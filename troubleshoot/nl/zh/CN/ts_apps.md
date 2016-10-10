---

copyright:
  years: 2015, 2016

---

{:tsSymptoms: .tsSymptoms} 
{:tsCauses: .tsCauses} 
{:tsResolve: .tsResolve} 
{:new_window: target="_blank"}  
{:shortdesc: .shortdesc}
{:codeblock: .codeblock} 





# 有关管理应用程序的故障诊断
{: #managingapps}

上次更新时间：2016 年 9 月 13 日
{: .last-updated} 

有关管理应用程序的一般性问题可能包括：无法更新应用程序；未显示双字节字符。然而，在许多情况下，只需执行几个简单的步骤即可解决这些问题。
{:shortdesc}





## 无法将应用程序切换到调试方式
{: #ts_debug}

如果 Java 虚拟机 (JVM) 版本为 8 或更低版本，那么可能无法启用调试方式。 


选择**启用应用程序调试**后，工具会尝试将应用程序切换到调试方式。然后，Eclipse 工作台会启动调试会话。工具成功启用调试方式时，Web 应用程序状态会依次显示 `Updating mode`、`Developing` 和 `Debugging`。
{: tsSymptoms}

但是，工具启用调试方式失败时，Web 应用程序状态只会依次显示 `Updating mode` 和 `Developing`，而不会显示 `Debugging`。工具还可能会在“控制台”视图中显示以下错误消息：

```
bluemixMgmgClient - ???? [pool-1-thread-1] .... ERROR --- ClientProxyImpl: Cannot create the websocket connections for MyWebProj
com.ibm.ws.cloudoe.management.client.exception.ApplicationManagementException: javax.websocket.DeploymentException: The HTTP request to initiate the  WebSocket connection failed
at com.ibm.ws.cloudoe.management.client.impl.ClientProxyImpl.onNewClientSocket(ClientProxyImpl.java:161)
at com.ibm.ws.cloudoe.management.client.impl.ClientProxyImpl$RunServerTask.run(ClientProxyImpl.java:267)
at java.util.concurrent.Executors$RunnableAdapter.call(Executors.java:522)
at java.util.concurrent.FutureTask.run(FutureTask.java:277)
at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1153)
at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:628)
at java.lang.Thread.run(Thread.java:785)
Caused by: javax.websocket.DeploymentException: The HTTP request to initiate the WebSocket connection failed
at  org.apache.tomcat.websocket.WsWebSocketContainer.connectToServer(WsWebSocketContainer.java:315)
at  com.ibm.ws.cloudoe.management.client.impl.ClientProxyImpl.onNewClientSocket(ClientProxyImpl.java:158)
... 6 more
Caused by: java.util.concurrent.TimeoutException
at org.apache.tomcat.websocket.AsyncChannelWrapperSecure$WrapperFuture.get(AsyncChannelWrapperSecure.java:505)
at org.apache.tomcat.websocket.WsWebSocketContainer.processResponse(WsWebSocketContainer.java:542)
at org.apache.tomcat.websocket.WsWebSocketContainer.connectToServer(WsWebSocketContainer.java:296)
... 7 more
[2016-01-15 13:33:51.075] bluemixMgmgClient - ????  [pool-1-thread-1] .... ERROR --- ClientProxyImpl: Cannot create the  websocket connections for MyWebProj
com.ibm.ws.cloudoe.management.client.exception.ApplicationManagementException: javax.websocket.DeploymentException: The HTTP request to initiate the  WebSocket connection failed
at com.ibm.ws.cloudoe.management.client.impl.ClientProxyImpl.onNewClientSocket(ClientProxyImpl.java:161)
at com.ibm.ws.cloudoe.management.client.impl.ClientProxyImpl$RunServerTask.run(ClientProxyImpl.java:267)
at java.util.concurrent.Executors$RunnableAdapter.call(Executors.java:522)
at java.util.concurrent.FutureTask.run(FutureTask.java:277)
at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1153)
at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:628)
at java.lang.Thread.run(Thread.java:785)
Caused by: javax.websocket.DeploymentException: The HTTP request to initiate the WebSocket connection failed
at org.apache.tomcat.websocket.WsWebSocketContainer.connectToServer(WsWebSocketContainer.java:315)
at com.ibm.ws.cloudoe.management.client.impl.ClientProxyImpl.onNewClientSocket(ClientProxyImpl.java:158)
... 6 more
Caused by: java.util.concurrent.TimeoutException
at org.apache.tomcat.websocket.AsyncChannelWrapperSecure$WrapperFuture.get(AsyncChannelWrapperSecure.java:505)
at org.apache.tomcat.websocket.WsWebSocketContainer.processResponse(WsWebSocketContainer.java:542)
at org.apache.tomcat.websocket.WsWebSocketContainer.connectToServer(WsWebSocketContainer.java:296)
... 7 more
```
 

以下 Java 虚拟机 (JVM) 版本无法建立调试会话：IBM JVM 7、IBM JVM 8 以及早于 Oracle JVM 8 的版本。
{: tsCauses}

如果工作台 JVM 是上述其中一个版本，那么在创建调试会话时可能会发生问题。工作台 JVM 版本通常是本地计算机的系统 JVM。系统 JVM 与运行中 Bluemix Java 应用程序的 JVM 不同。Bluemix Java 应用程序几乎总是在 IBM JVM 上运行，但有时会在 OpenJDK JVM 上运行。
  

要检查 IBM Eclipse Tools for Bluemix 运行的 Java 版本，请完成以下步骤：
{: tsResolve}

  1. 在 IBM Eclipse Tools for Bluemix 中，选择**帮助** > **关于 Eclipse** > **安装详细信息** > **配置**。
  2. 从列表中找到 `eclipse.vm` 属性。以下行是 `eclipse.vm` 属性的示例：
	
	```
	eclipse.vm=C:\Program Files\IBM\ibm-java-sdk-80-win-x86_64\bin\..\jre\bin\j9vm\jvm.dll
	```

  3. 在命令行中，从 Java 安装的 `bin` 目录输入 `java -version`。这将显示 IBM JVM 版本信息。

如果工作台 JVM 为 IBM JVM 7 或 8，或者为早于 Oracle JVM 8 的版本，请完成以下步骤来切换到 Oracle JVM 8：

  1. 下载并安装 Oracle JVM 8；请参阅 [Java SE Downloads](http://www.oracle.com/technetwork/java/javase/downloads/index.html){: new_window} 以获取详细信息。
  2. 重新启动 Eclipse。
  3. 检查 `eclipse.vm` 属性是否指向 Oracle JVM 8 的新安装。

  
## 无法复用已删除应用程序的名称
{: #ts_reuse_appname}
  
删除应用程序之后，您仅可以在删除应用程序路径之后复用应用程序名称。 

尝试复用应用程序名称时，您会收到以下消息：
{: tsSymptoms}

`名称已经由其他应用程序使用。`

删除应用程序时，不会自动删除其作为应用程序 URL 的路径。因此无法对其进行复用。您必须转至创建应用程序的空间，来删除路径，以便可以对其进行复用。
{: tsCauses}

执行以下步骤以删除未用的路径：
{: tsResolve}

  1. 通过输入以下命令，检查路径是否属于当前空间： 
     ```
	 cf routes
	 ```
  2. 如果路径不属于当前空间，请通过输入以下命令，切换到其所属的空间或组织： 
     ```
	 cf target -o org_name -s space_name
	 ```
  3. 通过输入以下命令，删除应用程序路径：
     ```
	 cf delete-route domain_name -n host_name
	 ```
	 例如： 	
```
	 cf delete-route mychinabluemix.net -n app001
	 ```


	 
	 

## 无法在组织中检索空间
{: #ts_retrieve_space}
如果当前组织没有与其相关联的空间，那么您无法创建应用程序或服务。

尝试在 Bluemix 中创建应用程序时，您会看到以下错误消息：
{: tsSymptoms}

`BXNUI0515E：尝试在组织中检索空间失败，因为发生了网络连接问题。`

通常当您第一次尝试在未创建空间的情况下通过目录创建应用程序或服务时，会发生此错误。
{: tsCauses}

请确保在当前组织中已创建空间。要创建空间，请使用以下某种方法： 
{: tsResolve}

  * 单击 {{site.data.keyword.avatar}} 图标 ![Avatar 图标](images/account_support.svg)，以打开“帐户和支持”窗口小部件，选择要在其中创建空间的组织，然后单击**创建空间**。
  * 在 cf 命令行界面中，键入 `cf create-space <space_name> -o <organization_name>`。

请重试。如果再次看到此消息，请转至 [Bluemix 状态](https://status.chinabluemix.net/){: new_window}页面，查看服务或组件是否存在问题。



## 无法执行请求的操作
{: #ts_authority}

没有相应的访问权限，您可能无法完成操作。

 

尝试对服务实例或应用程序实例执行操作时，无法完成请求的操作，并看到以下其中一条错误消息：
{: tsSymptoms}

`BXNUI0514E: 您不是 <orgName> 组织中任何空间的开发者。`


`服务器错误，状态码：403，错误代码：10003，消息：您无权执行请求的操作。`

 

您没有执行操作所需的相应级别的权限。
{: tsCauses}

  
要获取相应级别的权限，请使用以下其中一种方法：
{: tsResolve}
 * 选择您具有其开发者角色的另一个组织和空间。 
 * 请求组织管理员将您的角色更改为开发者，或者创建空间，然后为您分配开发者角色。有关详细信息，请参阅[管理组织和空间](../admin/orgs_spaces.html){: new_window}。
 



## 由于授权错误而无法访问 {{site.data.keyword.Bluemix_notm}} 服务
{: #ts_vcap}

应用程序访问 {{site.data.keyword.Bluemix_notm}} 服务时，如果服务凭证是硬编码到应用程序中的，那么可能会发生授权错误。 

将应用程序配置为与 {{site.data.keyword.Bluemix_notm}} 服务通信后，将应用程序部署到 {{site.data.keyword.Bluemix_notm}}。但是，无法使用应用程序来访问 {{site.data.keyword.Bluemix_notm}} 服务，并且会收到授权错误。
{: tsSymptoms}

硬编码到应用程序中的凭证可能不正确。每次重新创建服务时，用于访问该服务的凭证都会改变。
{: tsCauses}


不要将凭证硬编码到应用程序中，请改用 VCAP_SERVICES 环境变量中的连接参数。具体如何使用 VCAP_SERVICES 环境变量中的连接参数取决于程序语言。例如，对于 Node.js 应用程序，可以使用以下命令：
{: tsResolve}

```
process.env.VCAP_SERVICES
```
有关可在其他程序语言中使用的命令的更多信息，请参阅 [Java](http://docs.run.pivotal.io/buildpacks/java/java-tips.html#env-var){: new_window} 和 [Ruby](http://docs.run.pivotal.io/buildpacks/ruby/ruby-tips.html#env-var){: new_window}。









## 收到 502 无效网关错误
{: #ts_502_error}

如果在与 {{site.data.keyword.Bluemix_notm}} 上的应用程序进行交互时收到“502 无效网关”错误，请检查 {{site.data.keyword.Bluemix_notm}} 状态页面，然后采取相应的措施。

 

您收到以“502 无效网关”开头的错误消息。例如，您可能会看到 `502 无效网关：注册的端点未能处理请求。`
{: tsSymptoms}

 

通常会在以下情况下发生“无效网关”错误：您访问某个 Web 站点，该站点使用代理服务器来存储和中继来自托管该站点的主服务器中的数据。主服务器和代理服务器之间可能未正确连接，因此您会在浏览器窗口中看到 HTTP 状态码 502。此状态码指示该站点的主服务器未收到代理服务器所期望的 HTTP 实施。
{: tsCauses}

其他导致“无效网关”错误的不太常见的原因包括：因特网服务提供商 (ISP) 信息遗失、防火墙配置错误以及浏览器高速缓存错误。 

 

如果您怀疑 {{site.data.keyword.Bluemix_notm}} 服务关闭，请先检查 [{{site.data.keyword.Bluemix_notm}} 状态](https://status.chinabluemix.net/){: new_window}页面。如果服务状态正常，请尝试执行以下步骤来解决问题： 
{: tsResolve}

  * 重试操作：
    * 通过按键盘上的 F5 或单击刷新按钮，重新装入页面。如果此步骤无效，请清除浏览器的高速缓存和 cookie，然后再重新装入。
	* 使用其他浏览器。
	* 重新引导您的路由器、调制解调器和计算机。重新引导这些设备可以清理导致 502 错误的各种错误。 
  * 稍等，然后重试。在某些情况下，您的因特网服务提供商或 {{site.data.keyword.Bluemix_notm}} 服务可能会发生临时问题。您可以一直等到临时问题得到解决为止。
  * 如果问题持续存在，请联系 {{site.data.keyword.Bluemix_notm}} 支持。有关更多信息，请参阅[联系 {{site.data.keyword.Bluemix_notm}} 支持](../support/index.html#contacting-bluemix-support){: new_window}。 




## 超出磁盘配额
{: #ts_disk_quota}

如果磁盘空间不足，可以手动修改磁盘配额来获取更多的磁盘空间。

  

磁盘空间不足时，可能会看到一条消息，指示超过磁盘配额。为了解决该问题，您可能尝试了通过扩展应用程序实例来获取更多的磁盘空间。例如，您可能更改了应用程序详细信息页面上的内存配额，将大小从 256 MB 扩展到 1256 MB。但是，由于磁盘配额依然未变，所以您并没有获得更多的磁盘空间。 
{: tsSymptoms}


为应用程序分配的缺省磁盘配额为 1 GB。如果您需要更多的磁盘空间，必须手动指定磁盘配额。 
{: tsCauses}

 
使用以下某个方法可指定磁盘配额。可指定的最大磁盘配额为 2 GB。如果 2 GB 仍不够，请尝试外部服务。
{: tsResolve}

  * 在 manifest.yml 文件中，添加以下项：
    ```
	disk_quota: <disk_quota>
	```
  * 在用于将应用程序推送到 {{site.data.keyword.Bluemix_notm}} 的 `cf push` 命令中使用 **-k** 选项：
    ```
	cf push appname -p app_path -k <disk_quota>
	```

	
	



## Android 应用程序收不到 {{site.data.keyword.mobilepushshort}}
{: #ts_push}

在无法访问 Google 的某些地区，Android 应用程序收不到您通过 IBM {{site.data.keyword.mobilepushshort}} 服务发送出来的通知。在此情况下，可以使用第三方服务作为一种变通方法。

为 Bluemix 应用程序绑定 {{site.data.keyword.mobilepushshort}} 服务，并将消息发送给已注册的设备。但在某些地区，在 Android 平台上开发的应用程序收不到您的通知。
{: tsSymptoms}

IBM {{site.data.keyword.mobilepushshort}} 服务使用 Google 云消息传递 (GCM) 服务将通知分派到在 Android 平台上开发的移动应用程序。要使 Android 应用程序能够接收通知，移动应用程序必须可以访问 Google 云消息传递 (GCM) 服务。在 Android 应用程序无法访问 GCM 服务的区域，Android 应用程序收不到 {{site.data.keyword.mobilepushshort}}。
{: tsCauses}

 
使用不依赖于 GCM 服务的第三方服务作为一种变通方法，例如 [Pushy](https://pushy.me){: new_window}、[igetui](http://www.getui.com/){: new_window} 和 [jpush](https://www.jpush.cn/){: new_window}。
{: tsResolve}


  
## 无法在 {{site.data.keyword.Bluemix_notm}} 上运行可执行文件
{: #ts_executable}

如果可执行文件是在不同环境中开发的，那么可能无法在 {{site.data.keyword.Bluemix_notm}} 上运行这些可执行文件。 

 

如果可执行文件是在不同环境中开发的，那么无法在 {{site.data.keyword.Bluemix_notm}} 上运行这些可执行文件。
{: tsSymptoms}

 

如果要推送到 {{site.data.keyword.Bluemix_notm}} 的内容已经是可执行文件，那么该内容是先前构建的，不需要在 {{site.data.keyword.Bluemix_notm}} 上进行构建。在此情况下，无需任何 buildpack，可执行文件就可以在 {{site.data.keyword.Bluemix_notm}} 上运行。但是，必须向 {{site.data.keyword.Bluemix_notm}} 明确指示不需要 buildpack。
{: tsCauses}

 

当您将可执行文件推送到 {{site.data.keyword.Bluemix_notm}} 时，必须指定 null-buildpack，它指示不需要 buildpack。指定 null-buildpack 的方法是使用带 **-b** 选项的 `cf push` 命令：
{: tsResolve}

```
cf push appname -p app_path -c <start_command> -b <null-buildpack>
```
例如：
```
cf push appname -p app_path -c ./RunMeNow -b https://github.com/ryandotsmith/null-buildpack
```



	  
## 应用程序不会自动重新启动
{: #ts_apps_not_auto_restarted}


当绑定到应用程序的服务停止工作时，该应用程序不会自动重新启动。	  
	  
 

当绑定到应用程序的服务崩溃时，应用程序可能会发生如中断、异常和连接失败等问题。 {{site.data.keyword.Bluemix_notm}} 不会自动重新启动应用程序，以便从这些问题中进行恢复。
{: tsSymptoms}



此行为是 Cloud Foundry 故意为之。
{: tsCauses} 

 

您可以通过在命令行界面中键入以下命令来手动重新启动应用程序：
{: tsResolve}

```
cf push appname -p app_path
  ```
此外，还可以对应用程序进行编码，以识别如中断、异常和连接失败等问题，并从这些问题中进行恢复。

    
  

  
  
## 在 {{site.data.keyword.Bluemix_notm}} 上找不到组织
{: #ts_orgs}

在 {{site.data.keyword.Bluemix_notm}} 区域上工作时，可能在 {{site.data.keyword.Bluemix_notm}} 上找不到组织。
  
 

您可以成功登录到 {{site.data.keyword.Bluemix_notm}} 用户界面，但不能使用 cf 命令行界面来推送应用程序。
{: tsSymptoms}

尝试使用 cf 命令行界面将应用程序推送到 {{site.data.keyword.Bluemix_notm}} 时，您会看到以下某个错误消息（消息中指定了组织名称）： 

`查找组织时出错`

`找不到组织`



发生此问题的原因是您要使用的区域的 API 端点未指定，且您要查找的组织可能位于其他区域中。
{: tsCauses} 

   
  
如果使用 cf 命令行界面将应用程序推送到 {{site.data.keyword.Bluemix_notm}}，请输入 cf api 命令并指定区域的 API 端点。例如，输入以下命令以连接到 {{site.data.keyword.Bluemix_notm}} 中国：
{: tsResolve}

```
cf api https://api.chinabluemix.net
```

  
  


## 无法创建应用程序路径
{: #ts_hostistaken}

将应用程序部署到 {{site.data.keyword.Bluemix_notm}} 时，如果您所指定的主机名已在使用，那么无法创建该应用程序的路径。



将应用程序部署到 {{site.data.keyword.Bluemix_notm}} 时，您会看到以下错误消息： 
{: tsSymptoms} 

`正在创建路径 hostname.domainname ... 失败 服务器错误，状态码：400，错误代码：210003，消息：所采用的主机为：hostname`



如果您所指定的主机名已在使用，那么会发生此问题。
{: tsCauses} 


  
您所指定的主机名在您所使用的域中必须是唯一的。要指定不同的主机名，请使用以下某个方法：
{: tsResolve} 

  * 如果通过使用 `manifest.yml` 文件来部署应用程序，请在 host 选项中指定主机名。	 
    ```
    host: host_name	
	```
  * 如果从命令提示符部署应用程序，请使用带有 **-n** 选项的 `cf push` 命令。 
    ```
    cf push appname -p app_path -n host_name
    ```


## 无法使用 cf push 命令推送 WAR 应用程序
{: #ts_cf_war}

如果未正确指定应用程序位置，那么可能无法使用 cf push 命令来将归档的 Web 应用程序推送到 {{site.data.keyword.Bluemix_notm}}。
	


使用 `cf push` 命令将 WAR 应用程序上传到 {{site.data.keyword.Bluemix_notm}} 时，您会看到错误消息：`编译打包错误：由于编译打包失败，无法获取实例。`
{: tsSymptoms} 

 

如果未指定 WAR 文件，或者未指定 WAR 文件的路径，那么可能会发生此问题。 
{: tsCauses}

 	
	
使用 **-p** 选项来指定 WAR 文件或将路径添加到 WAR 文件。例如：
{: tsResolve}

```
cf push MyUniqueAppName01 -p app.war
```

```
cf push MyUniqueAppName02 -p "./app.war"
```
有关 `cf push` 命令的更多信息，请输入 `cf push -h`。



## 将 Liberty 应用程序推送到 {{site.data.keyword.Bluemix_notm}} 时未正确显示双字节字符
{: #ts_doublebytes}

如果没有为 servlet 或 JSP 文件正确配置 Unicode 支持，那么可能未正确显示双字节字符。

 

将 Liberty 应用程序推送到 {{site.data.keyword.Bluemix_notm}} 时，未正确显示在应用程序内指定的双字节字符。
{: tsSymptoms}

 

如果没有为 servlet 或 JSP 文件正确配置 Unicode 支持，那么可能发生该问题。
{: tsCauses}


您可以在 servlet 或 JSP 文件内使用以下代码：
{: tsResolve} 

  * 在 servlet 源文件中， 
    ```
	response.setContentType("text/html; charset=UTF-8");
	```
  * 在 JSP 中， 
    ```
	<meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
	```
	
	
	

## 无法部署 Node.js 应用程序
{: #ts_nodejs_deploy}

您在更新 Node.js 应用程序或将 Node.js 应用程序部署到 {{site.data.keyword.Bluemix_notm}} 时可能会遇到问题。



您在更新 Node.js 应用程序或将 Node.js 应用程序部署到 {{site.data.keyword.Bluemix_notm}} 时，可能会看到以下其中一条错误消息：
{: tsSymptoms} 

`任何可用 buildpack 均未成功检测到应用程序。`


`实例（索引 0）未能开始接受连接。`


`由于编译打包失败，无法获取实例。`


 

以下原因可能导致问题：
{: tsCauses}
 
  * 未指定启动命令。
  * 部署 Node.js 应用程序所需的文件在应用程序中缺少，或者放置在除根目录外的文件夹中。
  


	
根据导致问题的原因，采取以下操作：
{: tsResolve} 

  * 通过以下其中一种方法来指定启动命令： 
      * 使用命令行界面。例如： 
        ```
		cf push MyUniqueNodejs01 -p app_path -c "node app.js"
		```
	  * 使用 [package.json](https://docs.npmjs.com/json){: new_window} 文件。例如：
	    ```
		{
      ...
  	   "scripts": {
	 		 "start": "node app.js"
 	   }
	}
	    ```
	  * 使用 `manifest.yml` 文件。例如： 
	    ```
		applications:
  name: MyUniqueNodejs01
  ...
  command: node app.js
  ...
        ```

  * 确保 `package.json` 文件在 Node.js 应用程序中存在，才能启用用来识别应用程序的 Node.js buildpack。此外，您必须将此文件放置在应用程序的根目录中。	
    以下示例显示简单的 `package.json` 文件：   
	```
	{
        "name": "MyUniqueNodejs01",
        "version": "0.0.1",
        "description": "A sample package.json file",
        "dependencies": {
                "express": "3.4.x",
                "jade": "1.1.x"
        },
        "engines": {
                "node": "0.10.x"
        },
        "scripts": {
                  "start": "node app.js"
        }
 }
    ```
	
有关 Node.js 应用程序的更多提示，请参阅 [Tips for Node.js Applications](http://docs.cloudfoundry.org/buildpacks/node/node-tips.html){: new_window}。	




	
## 使用定制 buildpack 无法编译打包应用程序
{: #ts_bp_compilation}

如果 buildpack 内的脚本为“不可执行”，那么可能无法使用定制 buildpack 将应用程序部署到 {{site.data.keyword.Bluemix_notm}}。



使用定制 buildpack 将应用程序部署到 {{site.data.keyword.Bluemix_notm}} 时，您会看到错误消息：`应用程序未能编译打包，因此没有要显示的实例。`
{: tsSymptoms} 


如果脚本（如检测脚本、编译脚本和发布检测）不可执行，那么可能发生此问题。
{: tsCauses}

 

您可以使用 [git update](http://git-scm.com/docs/git-update-index){: new_window} 命令将每个脚本的许可权更改为“可执行”。例如，可以键入 `git update --chmod=+x script.sh`。
{: tsResolve}
	
	



## 无法推送 Meteor 应用程序
{: #ts_meteor}

如果未正确指定 buildpack，那么可能无法将 Meteor 应用程序推送到 {{site.data.keyword.Bluemix_notm}}。

 

将 Meteor 应用程序部署到 {{site.data.keyword.Bluemix_notm}} 时，您可能会看到错误消息：`应用程序未能编译打包，因此没有要显示的实例。`
{: tsSymptoms}


发生此问题的原因是没有可用于 Meteor 应用程序的内置 buildpack。必须使用定制 buildpack。
{: tsCauses} 


 

要对 Meteor 应用程序使用定制 buildpack，请使用以下其中一种方法：
{: tsResolve}

  * 如果使用 `manifest.yml` 文件来部署应用程序，请使用 buildpack 选项来指定定制 buildpack 的 URL 或名称。例如：
  ```
buildpack: https://github.com/Sing-Li/bluemix-bp-meteor 
  ```
  * 如果从命令提示符部署应用程序，请使用 `cf push` 命令并通过 **-b** 选项来指定定制 buildpack。例如：
    ```
	cf push appname -p app_path -b https://github.com/Sing-Li/bluemix-bp-meteor 
	```
	
  




