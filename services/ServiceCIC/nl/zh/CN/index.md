---

copyright:
  years: 2016
lastupdated: "2016-10-11"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}


# 定制图片分类器 API 版本 v1.0

https://sv.chinabluemix.net/dlaas/api

{: #gettingstartedCIC}

本服务提供依用户需求而定制的图片分类器。通过本服务， 用户可以获得定制的训练模型并将该分类器部署为Web服务。用户只需定义图片类别并上传图片， 就会自动获得图片分类器。在模型训练的同时， 用户可以通过本服务特有的可视化服务， 观察训练的过程和各层所提取的特征，以便更好的理解深度学习。通过此服务， 用户可以零基础通过深度学习技术定制图片分类器。 
{:shortdesc}

## DLAPIs
{: #DLAPIs}

运行发布的APIs.

**/dlapis/{id}** 

* **GET**: 提供imageUrl, 运行API 例如: /dlapis/fbb78a52-ae41-4000-bbe5-ad0d116c4e9d?imageUrl=http://IP/path/fff287bc-412b-4b5d-9f8a-a3af27ca74d7.jpg

* **POST**: 上传图片, 运行API

### GET /dlapis/{id}
{: #getdlapi}

提供imageUrl, 运行API 例如: /dlapis/fbb78a52-ae41-4000-bbe5-ad0d116c4e9d?imageUrl=http://IP/path/fff287bc-412b-4b5d-9f8a-a3af27ca74d7.jpg

* ### Request
{: #request}

  * **URI 参数**

       --id: required (string)
   
       --Example:
 
 	       fbb78a52-ae41-4000-bbe5-ad0d116c4e9d

  * **Query 参数**

       --imageUrl: required (string)
   
       --Example:
   
            http://IP/path/fff287bc-412b-4b5d-9f8a-a3af27ca74d7.jpg

* ### Response
{: #response}

  * **HTTP status code 200**
  * **Body**
  
    **Type: application/json**
	
	**示例:**
    ```
	  the web api running result
      {
        result: "success",
        imageUrl: "http://IP/path/fff287bc-412b-4b5d-9f8a-a3af27ca74d7.jpg",
        classified:
       {
          store: "0.71855"
       }
      }
    ```
	{: screen}
	
### POST /dlapis/{id}
{: #postdlapi} 
     
上传图片, 运行API.

* ### Request
{: #postrequest}

  * **URI 参数**

       --id: required (string)
   
       --Example:  
	   
 	       fbb78a52-ae41-4000-bbe5-ad0d116c4e9d
		
  * **Body**
  
    **Type: multipart/form-data**
	
	**示例:**
	```
	// Post params
    Content-Disposition: form-data;
      [
        name="files"; filename="mytemp.jpg" Content-Type: image/jpeg => image binary data
      ]
    // HTML usage
    <form enctype="multipart/form-data" action="{baseUri}/dlapis/4c3259c3-e300-41a7-b031-d6fbf508cab7" method="POST">
         Choose a file to upload:
         <input name="files" type="file" /><br />
         <input type="submit" value="Upload File" />
    </form>
    // curl usage
    curl -i -X POST -H "Content-Type: multipart/form-data" -F "files=@mytemp.jpg" {baseUri}/dlapis/4c3259c3-e300-41a7-b031-d6fbf508cab7
	```
	{: codeblock}

* ### Response
{: #postresponse}

  * **HTTP status code 201**
  * **Body**
  
    **Type: application/json**
	
	**示例:**
    ```
	Web API 运行结果:
    {
      result: "success",
      imageUrl: "http://IP/path/fff287bc-412b-4b5d-9f8a-a3af27ca74d7.jpg",
      classified:
      {
        store: "0.71855"
      }
    }
	```
	{: screen}




