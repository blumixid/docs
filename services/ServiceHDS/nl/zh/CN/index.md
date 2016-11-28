---

copyright:
  years: 2016

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 混合数据库服务入门
{: #gettingstartedHDS}

最近修改: 10 月 2016
{: .last-updated}

混合数据库服务 (HDS)是IBM开发的多引擎混合数据库服务，同时支持JDBC、Mongo数据库接口、Rest接口对数据的访问，实现融合的数据存储与查询功能。同时，多引擎无缝集成使您能轻松应对物联网、互联网+转型以及现有系统云端迁移等各种场景。
{:shortdesc}

HDS对时间序列数据进行了专门的优化。时间序列数据通常产生于IoT（物联网）设备，例如计量传感器或温度传感器。基于统一JSON时间序列模型的IoT REST API给IoT应用提供了存储和查询时间序列传感数据的支持。

为了使用混合数据库服务，您需要使用IBM Bluemix Web 接口或 Cloud Foundry cf 命令行工具。因为无法从 Bluemix外部访问数据库，您需要 cf 工具来将您的应用程序部署到 Bluemix 云。请参考cf工具文档或者Bluemix文档生成您的混合数据库服务实例，并将其绑定到您的应用程序。

将混合数据库服务实例绑定到应用程序之后，系统会将连接混合数据库服务所需的信息和凭证添加到 VCAP_SERVICES 环境变量中（见下面的混合数据库服务的凭证例子）。

```
	{
	  "hybrid_data_service": 
	  [
	  {
		"name": "Hybrid_Data_Service-y9",
		"label": "hybrid_data_service",
		"plan": "small_plan",
		"credentials": 
		{
		  "json_url": "mongodb://iruyzsxu:6DQrw1PhIM@172.18.32.53:27017/d_1463109202675087",
		  "db": "d_1463109202675087",
		  "username": "iruyzsxu",
		  "sql_url": "jdbc:informix-sqli://172.18.32.53:9088/d_1463109202675087:INFORMIXSERVER=ifxserver;USER=iruyzsxu;PASSWORD=6DQrw1PhIM;DB_LOCALE=en_us.utf8",
		  "iot_url": "http://iruyzsxu:6DQrw1PhIM@172.18.32.53:8090/d_1463109202675087",
		  "rest_url": "http://iruyzsxu:6DQrw1PhIM@172.18.32.53:8080/d_1463109202675087",
		  "hostname": "172.18.32.53",
		  "password": "6DQrw1PhIM"
		}
	  }
	  ]       
	}
```
{: screen}

VCAP_SERVICES 环境变量包含以下项：

```
	hybrid_data_service：混合数据库服务的名称。
    name: 服务实例的名称。
    label: 服务的名称。
    plan: 服务套餐的名称。
    credentials: 访问该服务实例的凭证。
    hostname: 混合数据库服务的服务器的IP地址
	db: 数据库名称。
    username: 认证用户名。
	password: 认证密码。
    sql_url: Informix JDBC 驱动程序连接的连接 URL。
	json_url: MongoDB 连接的连接 URL。
    rest_url: REST API 连接的连接 URL。
	iot_url: IoT REST API 连接的连接 URL。
```
{: screen}

MongoDB 应用程序的以下代码片段显示了如何使用基本 Java 代码获取连接混合数据库服务的凭证信息（json_url):

```
	import com.mongodb.*;
	import com.mongodb.util.*;
	.....
	String VCAP_SERVICES = System.getenv("VCAP_SERVICES");
	if (VCAP_SERVICES != null) {
		BasicDBObject obj = (BasicDBObject) JSON.parse(VCAP_SERVICES);
		Set<String> keys = obj.keySet();
		for (String eachkey : keys) 
			if (eachkey.contains("hybrid_data_service")) 
				thekey = eachkey;
		BasicDBList list = (BasicDBList) obj.get(thekey);
		obj = (BasicDBObject) list.get("0");
		BasicDBObject credentialObj = (BasicDBObject) obj.get("credentials");
		databaseHost = (String) credentialObj.get("hostname");
		databaseName = (String) credentialObj.get("db");
		username = (String) credentialObj.get("username");
		password = (String) credentialObj.get("password");
		connectionUrl = (String) credentialObj.get("json_url");
	}
```
{: codeblock}

## 使用JDBC, MongoDB 接口 和 Rest 接口访问混合数据库服务示例
{: #samplesaccessHDS}

本节通过简单的Java程序来介绍使用IBM Informix JDBC API，MongoDB的API，REST API和支持物联网数据的IoT REST API来连接，操作混合数据库服务。

其主要步骤为：
1. 从VCAP_SERVICES 环境变量中获得的凭证信息所对应的url  
2. 通过API进行连接
3. 操作混合数据库
4. 关闭连接

注：

凭证信息是从VCAP_SERVICES 环境变量中获得并把它放到credentialObj中（参考上面的程序片段）。
	
### IBM Informix JDBC API示例（创建表）

```
	public class HSD_JDBC_Test {
     public static void main(String[] args) throws IOException, JSONException, SQLException { 
       //obtain credentialObj from VCAP_SERVICES
       BasicDBObject credentialObj = ......

       //Get JDBC url string
       String URL = credentialObj.getString("sql_url");
       System.out.print("url = " + URL + "\n");
     
       //Connect
       Connection conn = DriverManager.getConnection(URL);
       System.out.print("success to connect to the HDS by JDBC!\n");
       conn.setAutoCommit(true);
     
       //Try to create a table
       Statement st = conn.createStatement();
       String sql = "create table if not exists testtable(id int, str char(50))";
       st.execute(sql);
       st.close();
       System.out.print("success to run : " + sql + "\n");
     
       //Close connection
       conn.close();
       System.out.print("Demo ends.\n");
     }
	}
```
{: codeblock}
	
### MongoDB API示例（查询返回Collection名称的列表）

```
	public class HDS_Mongo_Test {
     public static void main(String[] args) throws IOException, JSONException {
       //obtain credentialObj from VCAP_SERVICES
       BasicDBObject credentialObj = ......

       //Get MongoDB url string
       String URI = credentialObj.getString("json_url");
       String DBNAME = credentialObj.getString("db");
       System.out.print("url = " + URI + "\n");
     
       //Connect
       MongoClientURI mongoURI = new MongoClientURI(URI);
       MongoClient mongo = new MongoClient(mongoURI);
       DB db =mongo.getDB(DBNAME);
       System.out.print("success to connect to the HDS by Mongo!\n");
     
       //Try to query all collections' name
       Set<String> colls = db.getCollectionNames();
       System.out.println("There are "+ colls.size() + " collections:");
       for (String s : colls) {
       System.out.println("Collection Name:"+s);
       }
     
       //Close connection
       mongo.close();
       System.out.print("Demo ends.");
     }
	}
```
{: codeblock}


### REST API示例（查询返回Collection名称的列表）

```
	public class HDS_REST_Test {
      public static void main(String[] args) throws IOException, JSONException {
       //obtain credentialObj from VCAP_SERVICES
       BasicDBObject credentialObj = ......
       
       //Get REST url string
       String URI = credentialObj.getString("rest_url");
       System.out.print("url = " + URI + "\n");
       //Set authorization information
       String USRERNAME = credentialObj.getString("username");
       String PASSWORD = credentialObj.getString("password");
       byte[] token = (USRERNAME + ":" + PASSWORD).getBytes("utf-8");
       String authorization = "Basic " + new String(Base64.encodeBase64(token), "utf-8");
       //Connect - query all collections' name
       URL restServiceURL = new URL(URI);
       HttpURLConnection httpConnection = (HttpURLConnection) restServiceURL.openConnection();
       System.out.print("success to connect to the HDS by REST!\n");
       //Set methods and proterties of request
       httpConnection.setRequestMethod("GET");
       httpConnection.setRequestProperty("Authorization", authorization);
       httpConnection.setRequestProperty("Accept", "application/json");
       //Judge whether the response is correct
       if(httpConnection.getResponseCode() == 200){
         System.out.print("success to authorizate...\n");
       }
       //Get response
       BufferedReader responseBuffer = new BufferedReader(new InputStreamReader((httpConnection.getInputStream())));
       System.out.println("Response from Server:");
       String output;
       while ((output = responseBuffer.readLine()) != null) {
         System.out.println(output);
       }
       //Close connection
       httpConnection.disconnect();
       System.out.print("Demo ends.\n");
     }
    }
```
{: codeblock}

### IoT REST API示例（查询所有设备的所有信息和数据）

```
	public class HDS_IOT_Test {
     public static void main(String[] args) throws IOException, JSONException {
       //obtain credentialObj from VCAP_SERVICES
       BasicDBObject credentialObj = ......
       
       //Get IoT REST url string
       String URI = credentialObj.getString("iot_url");
       System.out.print("url = " + URI + "\n");
       //Set authorization information
       String USRERNAME = credentialObj.getString("username");
       String PASSWORD = credentialObj.getString("password");
       byte[] token = (USRERNAME + ":" + PASSWORD).getBytes("utf-8");
       String authorization = "Basic " + new String(Base64.encodeBase64(token), "utf-8");
       //Connect - query all collections' name
       URL restServiceURL = new URL(URI);
       HttpURLConnection httpConnection = (HttpURLConnection) restServiceURL.openConnection();
       System.out.print("success to connect to the HDS by IoT REST!\n");
       //Set methods and proterties of request
       httpConnection.setRequestMethod("GET");
       httpConnection.setRequestProperty("Authorization", authorization);
       httpConnection.setRequestProperty("Accept", "application/json");
       //Judge whether the response is correct
       if(httpConnection.getResponseCode() == 200){
         System.out.print("success to authorizate...\n");
       }
       //Get response
       BufferedReader responseBuffer = new BufferedReader(new InputStreamReader((httpConnection.getInputStream())));
       System.out.println("Response from Server:");
       String output;
       while ((output = responseBuffer.readLine()) != null) {
         System.out.println(output);
       }
       //Close connection
       httpConnection.disconnect();
       System.out.print("Demo ends.\n");
     }
    }
```
{: codeblock}	
	
# API文档
{: #apiHDS}

## 混合数据库服务的REST API
{: #restapiHDS}

REST API提供了一种强大而灵活的方式访问HDS的数据库。通过REST API，您可以查询JSON/BSON文档的集合、传统的关系型表和时间序列数据。

REST API支持GET、PUT、POST和DELETE的HTTP方法，查询条件语句借鉴MongoDB的语法。

在混合数据库服务中，使用Credentials凭据的rest_url来作为请求地址。

REST API的完整文档请参考 ["REST API in IBM Knowledge Center"](http://www-01.ibm.com/support/knowledgecenter/SSGU8G_12.1.0/com.ibm.json.doc/ids_json_043.html){:new_window}.

- GET

    GET rest_url  返回集合列表。

    GET rest_url/collectionName  返回某个集合的所有数据。

    GET rest_url/collectionName?queryParameters  查询满足条件的集合数据，支持的查询参数有batchSize, query, fields, sort。

- PUT

    PUT rest_url/collectionName?queryParameters  插入或者修改集合数据。

- POST

    POST rest_url  创建一个集合。

    POST rest_url/collectionName  创建一个文档。

- DELETE

    DELETE rest_url/collectionName  删除一个集合。

    DELETE rest_url/collectionName?queryParameters  从指定集合中删除满足查询的文档。
	
## 混合数据库服务的IoT REST API
{: #iotrestapiHDS}

IoT REST API是一个基于物联网设备而设计的、简单易用的REST API，用于存储和管理物联网设备的时间序列数据。例如用来存储传感器的时间序列数据。

IoT REST API是基于三个事先创建的表（iot_device, iot_devicedata, iot_devicedata_ts)来实现的, 在创建的数据库时，系统会自动创建这三个表。客户在使用数据库时，不要对这三个表进行任何操作，否则IoT REST API可能无法正确运行。

IoT REST API有一个预定义的设备的数据模式，包括5个属性：

```
    id：设备自带的UUID，即通用唯一识别码。
    key：用户自定义的设备ID，必须满足唯一约束。
    description：设备的描述信息。
    metadata：JSON文档，描述该设备的基本属性，可以包括制造商、型号和位置等信息。这个JSON文档文件不能包含子文档或数组，即它必须是一维的。
    data：该设备生成的时间序列数据。在“data”这个字段的时间采用常见的时间格式yyyy-MM-dd HH:mm:ss 或者yyyy-MM-dd HH:mm:ss.SSS 来表示
```
{: screen} 

例子:

```
	{
	   "id": "7c1c1197-c011-4169-a0d1-97685b96054b",
	   "key": "building.1.floor.2.sensor",
	   "description": "sensor to get temperature, pressure, et cetera",
	   "metadata": {
				   "building": "1",,
				   "floor": "2"
	   },
	   "data": [
			{
			"t": "2014-01-08T00:00:00.000",
			"temperature": 33,
			"humidity": 45
			},
			{
			"t": "2014-01-08T01:00:00.000",
			"temperature": 34,
			"humidity": 50
			}
	   ]
	}
```
{: screen} 

你可以用IoT REST API查询设备的时间序列数据。IoT REST API支持GET、PUT、POST、DELETE等HTTP方法，查询条件语句借鉴MongoDB的语法。

在HDS中使用Credentials凭据中的iot_url进行IoT REST操作。

- GET

    GET iot_url   返回所有设备的信息。

    GET iot_url?  返回满足条件的设备信息。

- PUT

    PUT iot_url   插入或者修改设备的时间序列数据。


- POST

    POST iot_url  创建一个设备，设备信息需要包含id和key，description 和 metadata是可选的。

- DELETE

    DELETE iot_url? 根据约束条件删除设备。
	
## IOT REST API的使用例子
{: #iotrestapiExamples}

### 注册一个设备

使用 'POST iot_url' 方法来注册设备。POST 的数据是一种结构化的 JSON 文档，用于描述要注册的设备。此 JSON 文档必须包含前面介绍的JSON时间序列数据模型中的id和key，id和key必须是唯一的，description和metadata是可选的，如果在注册时没有提供id，系统会自动生成一个唯一id并且在response中返回。 

所有的IoT REST API 都需要验证用户名和密码，使用Basic Auth方法鉴权。

注册例子:

注册温度传感器设备，设置ID和描述信息，给出元数据描述信息，例子中`http://dgzbbwwa:4raD5M9JIB@172.18.32.53:8090/d_1461161444275608`是`iot_url`


	HTTP Request:

```
		POST http://dgzbbwwa:4raD5M9JIB@172.18.32.53:8090/d_1461161444275608
		HEADER:
			Content-type: application/json; charset=UTF-8
			Authorization: authorizationString
			Accept: application/json
		POST BODY:
		{
			"id": "H1xxlXyT",
			"key": "IBMabcdefghi845dd7dev005abcdefgh",
			"description": "sensor to get temperature and pressure",
			"metadata": {  
				"name":"test1",
				"typename":"tester",
				"version":"1.0",
				"manufacturedate":"12/22/2015",
				"registerdate":"12/22/2015"
		   }
		}
```
{: screen} 

	HTTP Response:
```
		{"id": "H1xxlXyT", "ok": true}
```
{: screen}


### 查询设备数据

使用 'GET iot_url?' 来查询设备数据，支持的查询的http参数如下:

```
		id	        用于查询数据的设备的id.
		key	        用于查询数据的设备的key.
		start	    用于查询数据的开始时间.此时间使用ISO_8601格式，或者长整数(毫秒数).
		end	        用于查询数据的结束时间.此时间使用ISO_8601格式，或者长整数(毫秒数).
		metadata	使用metadata来过滤设备的JSON文档.
		fields	    在返回结果中被包含的字段.
		dataFormat  在返回结果中被包含的时间戳的显示格式.
```
{: screen} 
 
IoT REST API支持如下几种时间戳格式:

- 毫秒数(当前时间与1970年1月1日的毫秒数)

> 正则表达式:"^(\+|-)?\d+L$"

> 示例:
123456789L
+123L

- Year 

> 正则表达式:"^\d{4}$"

> 示例: 
2015

- Year-Month

> 正则表达式:"^\d{4}$"

> 示例: 
2015


- Year-Month-Day

> 示例:
2016-05-30

- Year-Month-Day Hour:Minute

> 示例:
2016-05-30 12:00

- Year-Month-Day Hour:Minute:Second

> 示例:
2016-05-30 12:00:00

- Year-Month-Day Hour:Minute:Second.Fraction

> 示例:
2016-05-30 12:00:00.000

在查询请求中，查询参数start和end的值需要遵循上面时间戳格式。
而查询参数dataFormat 用来描述在返回结果中被包含的时间戳的显示格式，它常用的取值有yyyy-MM-dd HH:mm:ss 或者yyyy-MM-dd HH:mm:ss.SSS 两种。

为了统一返回的查询JSON文档，我们使用了JSONArray来存放查询结果，在JSONArray里面的每一个元素代表一个设备的所有数据（数据的格式就是按照上面描述JSON时间序列数据模型的格式来组织的）。

查询例子:

**查询所有设备**

使用 'GET iot_url' 查询所有设备。

	HTTP Request:
	
```	
		GET http://dgzbbwwa:4raD5M9JIB@172.18.32.53:8090/d_1461161444275608
```
{: screen}
	
	HTTP Reponse: 返回所有设备的数据

**按ID查询设备**

使用 'GET iot_url?id=xxx' 按ID查询设备。
	
	HTTP Request:
	
```
		GET  http://mdlssbmm:Fq388kXB8N@172.16.11.67:8090/d_1463034061959174?id=H1xxlXyT&dateFormat=yyyy-MM-dd HH:mm:ss.SSS
		HEADER:
			Authorization: authorizationString
			Accept: application/json
```
{: screen}
	
	HTTP Reponse:  返回该id对应的设备的数据，时间格式按照yyyy-MM-dd HH:mm:ss.SSS方式显示
	
```
		[
		{"id":"H1xxlXyT",
		 "key":"IBMabcdefghi845dd7dev005abcdefgh",
		 "metadata":{"name":"test1",
		   "typename":"tester",
		   "version":"1.0",
		   "manufacturedate":"12/22/2015",
		   "registerdate":"12/22/2015"
		 },
		 "description":"sensor to get temperature and pressure",
		 "data":
		   [
		   {"t":"2015-01-01 01:00:00.000","temperature":33,"humidity":50},
		   {"t":"2015-01-01 01:15:00.000","temperature":34,"humidity":51},
		   {"t":"2015-01-01 01:45:00.000","temperature":35,"humidity":52}
		   ]
		}
		]
```
{: screen}
	
**按key查询设备**

使用 'GET iot_url?key=xxx' 按key查询设备。
	
	HTTP Request:
	
```
		GET http://dgzbbwwa:4raD5M9JIB@172.18.32.53:8090/d_1461161444275608?key=IBMabcdefghi845dd7dev005abcdefgh&dateFormat=yyyy-MM-dd HH:mm:ss.SSS
		HEADER:
			Authorization: authorizationString
			Accept: application/json
```
{: screen}
	
	HTTP Response:	
	
```
		[
		{"id":"H1xxlXyT",
		 "key":"IBMabcdefghi845dd7dev005abcdefgh",
		 "metadata":{"name":"test1",
		   "typename":"tester",
		   "version":"1.0",
		   "manufacturedate":"12/22/2015",
		   "registerdate":"12/22/2015"
		 },
		 "description":"sensor to get temperature and pressure",
		 "data":
		   [
		   {"t":"2015-01-01 01:00:00.000","temperature":33,"humidity":50},
		   {"t":"2015-01-01 01:15:00.000","temperature":34,"humidity":51},
		   {"t":"2015-01-01 01:45:00.000","temperature":35,"humidity":52}
		   ]
		}
		]
```
{: screen}
	
**查询与元数据过滤器匹配的设备**

使用 'GET iot_url?metadata={xxx:xxx}' 查询与元数据过滤器匹配的设备。
	
	HTTP Request:
	
```
		GET http://dgzbbwwa:4raD5M9JIB@172.18.32.53:8090/d_1461161444275608?metadata={typename:"tester"}
		HEADER:
			Authorization: authorizationString
			Accept: application/json
```
{: screen}
	
	HTTP Response: 返回所有的typename是tester的设备的数据
	
```
		[
		{"id":"H1xxlXyT",
		 "key":"IBMabcdefghi845dd7dev005abcdefgh",
		 "metadata":{"name":"test1",
		   "typename":"tester",
		   "version":"1.0",
		   "manufacturedate":"12/22/2015",
		   "registerdate":"12/22/2015"
		 },
		 "description":"sensor to get temperature and pressure",
		 "data":
		   [
		   {"t":"2015-01-01 01:00:00.000","temperature":33,"humidity":50},
		   {"t":"2015-01-01 01:15:00.000","temperature":34,"humidity":51},
		   {"t":"2015-01-01 01:45:00.000","temperature":35,"humidity":52}
		   ]
		}
		]
```
{: screen}

**根据时间间隔查询设备数据**

使用 'GET iot_url?start=xxx&end=xxx' 根据时间间隔查询设备数据。

	HTTP Request:
	
```   
		GET http://dgzbbwwa:4raD5M9JIB@172.18.32.53:8090/d_1461161444275608?id=H1xxlXyT&start=2016-01-08&end=2016-01-09&dateFormat=yyyy-MM-dd HH:mm:ss.SSS
		HEADER:
			Authorization: authorizationString
			Accept: application/json
```
{: screen}
	
	HTTP Reponse: 返回该id的设备在1月8号(开始时间是2016-01-08 00:00:00， 结束时间是2016-01-09 00:00:00)的数据，时间的格式按dataFormat要求显示。    
    如果只提供开始时间而没有提供结束时间，则返回该设备从开始时间开始的所有数据。return device dataset between 2016-01-08 00:00:00 and 2016-01-09 00:00:00 with timestamp's format 'yyyy-MM-dd HH:mm:ss.SSS'.
	
```
		[
		{"id":"H1xxlXyT",
		 "key":"IBMabcdefghi845dd7dev005abcdefgh",
		 "metadata":{"name":"test1",
		   "typename":"tester",
		   "version":"1.0",
		   "manufacturedate":"12/22/2015",
		   "registerdate":"12/22/2015"
		 },
		 "description":"sensor to get temperature and pressure",
		 "data":
		   [
		   {"t":"2015-01-01 01:00:00.000","temperature":33,"humidity":50},
		   {"t":"2015-01-01 01:15:00.000","temperature":34,"humidity":51},
		   {"t":"2015-01-01 01:45:00.000","temperature":35,"humidity":52}
		   ]
		}
		]
```
{: screen}

**查询设备数据的字段子集**

使用 'GET iot_url?fields={xxx:1}' 查询设备数据的字段子集

	HTTP Request:
	
```    
		GET 
		http://dgzbbwwa:4raD5M9JIB@172.18.32.53:8090/d_1461161444275608?id=H1xxlXyT&fields={temperature:1}
		HEADER:
			Authorization: authorizationString
			Accept: application/json
```
{: screen}
	
	HTTP Response: 返回该id的设备只包含temperature这个属性的数据。
	
```
		[
		{"id":"H1xxlXyT",
		 "key":"IBMabcdefghi845dd7dev005abcdefgh",
		 "metadata":{"name":"test1",
		   "typename":"tester",
		   "version":"1.0",
		   "manufacturedate":"12/22/2015",
		   "registerdate":"12/22/2015"
		 },
		 "description":"sensor to get temperature and pressure",
		 "data":
		   [
		   {"t":"2015-01-01 01:00:00.000","temperature":33},
		   {"t":"2015-01-01 01:15:00.000","temperature":34},
		   {"t":"2015-01-01 01:45:00.000","temperature":35}
		   ]
		}
		]
```
{: screen}

### 插入或者修改一个设备的时间序列数据

使用 'PUT iot_url?id=xxx' 插入或者修改一个设备的时间序列数据。当给定的时间点没有数据时，则插入该时间点的数据，否则更新数据。

插入或者修改例子:
	
	HTTP Request:
	
```    
		PUT http://dgzbbwwa:4raD5M9JIB@172.18.32.53:8090/d_1461161444275608?id= H1xxlXyT
		HEADER:
			Content-type: application/json; charset=UTF-8
			Authorization: authorizationString
		   Accept: application/json
		PUT BODY:
		[
		  {"t":"2015-01-01 01:00:00" , "temperature": 33, "humidity":50}, 
		  {"t":"2015-01-01 01:15:00" , "temperature": 34, "humidity":51},
		  {"t":"2015-01-01 01:45:00" , "temperature": 35, "humidity":52}
		]
```
{: screen}
	
	HTTP Response: 返回插入或修改的确认信息。
	
```
		{"n":3,"ok":true}
```
{: screen}
	
### 删除一个设备的数据

使用 'DELETE iot_url?id=xxx' 删除一个设备的数据。使用该删除接口的时候一定要谨慎。

删除例子:
	
	HTTP Request:
	
```    
		DELETE http://dgzbbwwa:4raD5M9JIB@172.18.32.53:8090/d_1461161444275608?id= H1xxlXyT
		HEADER:
			Authorization: authorizationString
			Accept: application/json
```
{: screen}
	
	HTTP Response: 返回删除的确认信息。
	
```	
		{"n":1,"ok":true}
```
{: screen}
		
# 服务实例的网页
{: #siHDSweb}

## Mongo网页
{: #mongoPage}

Mongo页面提供对mongo数据集合的查询、插入、删除、导入、导出等功能。

**导入**

在左侧操作栏点击`导入`，选择要导入的集合名称和本地需要上传的数据文件，点击`提交`即可导入本地数据到该集合。注意目前仅支持json格式的本地文件，且此文件格式应该是使用mongo客户端`mongoexport`导出的格式。

**导出**

支持将数据导出为json格式的文件。和`导入`类似，选择要导出的集合，点击`导出`即可下载数据文件到本地。

**创建新集合**

输入新集合名，点击`提交`即可。

**集合的数据操作**

在mongo页面我们支持对集合中文档的`查询`，`插入`，`删除`功能，对关系表中数据仅支持`查询`功能。

## SQL页面
{: #sqlPage}

SQL页面提供对关系型数据库表的查询、插入、删除、统计等功能。

**创建表**

在左边`动作`栏中选择`创建表`，在右边会出现相应的输入框。

首先输入表名，在表中每一栏中，输入列名，选择列类型（varchar和char类型必须输入长度），选择是否为主键，是否可空，以及设置默认值。点击“+”可以新增一列。当表设计好之后，点击`创建表`即可。

**删除表**

点击"SQL"标签，页面显示为SQL主页面，选择需要删除的表，然后点击下方`删除`按钮，弹出的确认框选择确认，即可删除该表。

**SQL查询**

SQL页面提供了对SQL语句的支持。在`动作`栏点击`SQL执行`，会出现SQL的输入框，输入SQL语句，点击`提交`即可。

**使用SQL查询集合中的文档**

使用SQL语句查询一个集合中的文档，查询的SQL语句类似"select data::json from collectionName“，其中collectionName是集合名。