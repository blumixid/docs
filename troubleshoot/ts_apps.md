---

copyright:
  years: 2015, 2016
lastupdated: "2016-11-21"

---

{:tsSymptoms: .tsSymptoms} 
{:tsCauses: .tsCauses} 
{:tsResolve: .tsResolve} 
{:new_window: target="_blank"}  
{:shortdesc: .shortdesc}
{:codeblock: .codeblock} 





# Troubleshooting for managing apps
{: #managingapps}

General problems with managing applications might include applications can't be updated, double-byte characters aren't displayed. However, in many cases, you can recover from these problems by following a few easy steps.
{:shortdesc}





## Unable to switch apps into debug mode
{: #ts_debug}

You might not be able to enable the debug mode if the Java virtual machine (JVM) version is 8 or lower. 


After you select **Enable application debug**, the tools attempt to switch the application into the debug mode. Then, the Eclipse workbench begins a debug session. When the tools successfully enable debug mode, the web application status displays `Updating mode`, `Developing`, and `Debugging`. 
{: tsSymptoms}

However, when the tools fail to enable the debug mode, the web application status displays `Updating mode` and `Developing` only, and does not display `Debugging`. The tools might also display the following error message in the Console view:

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
 

The following Java virtual machine (JVM) versions cannot establish a debug session: IBM JVM 7, IBM JVM 8, and previous versions of Oracle JVM 8.
{: tsCauses}

If your workbench JVM is one of these versions, then you might have issues when you create a debug session. Your workbench JVM version is typically the system JVM of your local computer. Your system JVM is not the same as the JVM of your running Bluemix Java application. The Bluemix Java application almost always runs on IBM JVM, and sometimes runs on OpenJDK JVM.
  

To check the version of Java that IBM Eclipse Tools for Bluemix runs, complete the following steps:
{: tsResolve}

  1. In IBM Eclipse Tools for Bluemix, select **Help** > **About Eclipse** > **Installation Details** > **Configuration**.
  2. Find the `eclipse.vm` property from the list. The following line is an example of an `eclipse.vm` property:
	
	```
	eclipse.vm=C:\Program Files\IBM\ibm-java-sdk-80-win-x86_64\bin\..\jre\bin\j9vm\jvm.dll
	```

  3. At the command line, enter `java -version` from the `bin` directory of your Java installation. Your IBM JVM version information is displayed.

If your workbench JVM is IBM JVM 7 or 8, or a previous version of Oracle JVM 8, complete the following steps to switch to Oracle JVM 8:

  1. Download and then install Oracle JVM 8, see [Java SE Downloads](http://www.oracle.com/technetwork/java/javase/downloads/index.html){: new_window} for details.
  2. Restart Eclipse.
  3. Check whether the `eclipse.vm` property points to your new installation of Oracle JVM 8.

  
## Unable to reuse names of deleted apps
{: #ts_reuse_appname}
  
After you delete an app, you can reuse the app name only after you delete the app route. 

When you try to reuse the app name, you receive the following message:
{: tsSymptoms}

`The name is already used by another app.`

When an app is deleted, its route, which is the URL for the app, isn't automatically deleted. Therefore, it's not available for reuse. You must go to the space where the app was created to delete the route so that it can be reused.
{: tsCauses}

Take the following steps to delete the unused route: 
{: tsResolve}

  1. Check whether the route belongs to the current space by entering the following command: 
     ```
	 cf routes
	 ```
  2. If the route does not belong to the current space, switch to the space or org that it belongs to by entering the following command: 
     ```
	 cf target -o org_name -s space_name
	 ```
  3. Delete the app route by entering the following command:
     ```
	 cf delete-route domain_name -n host_name
	 ```
	 For example:
	 ```
	 cf delete-route mychinabluemix.net -n app001
	 ```


	 
	 

## Unable to retrieve spaces in the org
{: #ts_retrieve_space}
You can't create an app or a service if your current organization does not have a space associated with it.

When you try to create an app in Bluemix, you see the following error message:
{: tsSymptoms}

`BXNUI0515E: The attempt to retrieve the spaces in the org failed because of a network connection problem.`

This error often is received the first time you try to create an app or a service from the Catalog when a space is not created yet. 
{: tsCauses}

Ensure that you created a space in your current organization.  To create a space, use one of the following methods:
{: tsResolve}

  * Click the {{site.data.keyword.avatar}} icon ![Avatar icon](images/account_support.svg) to open the Account and Support widget, select the organization that you want to create the space in, and then click **Create a Space**.
  * In the cf command line interface, type `cf create-space <space_name> -o <organization_name>`.

Try again. If you see this message again, go to the [Bluemix status](https://status.chinabluemix.net/){: new_window} page to check whether a service or component has an issue.



## Unable to perform requested actions
{: #ts_authority}

You might not be able to complete actions without appropriate access authority.

 

When you try to perform actions for a service instance or an app instance, you can't complete the requested actions and see one of the following error messages: 
{: tsSymptoms}

`BXNUI0514E: You are not a developer for any of the spaces in the <orgName> organization.`


`Server error, status code: 403, error code: 10003, message: You are not authorized to perform the requested action.`

 

You do not have the appropriate level of authority that is required to perform the actions. 
{: tsCauses}

  
To obtain the appropriate authority level, use one of the following methods: 
{: tsResolve}
 * Select another organization and space for which you have the developer role. 
 * Ask the org manager to change your role to developer or to create a space and then assign you a developer role. See [Managing organizations and spaces](/docs/admin/orgs_spaces.html){: new_window} for details.
 



## Unable to access {{site.data.keyword.Bluemix_notm}} services because of authorization errors
{: #ts_vcap}

Authorization errors might occur when your app accesses a {{site.data.keyword.Bluemix_notm}} service if the service credentials are hardcoded in your app. 

After you configure your app to communicate with a {{site.data.keyword.Bluemix_notm}} service, you deploy the app to {{site.data.keyword.Bluemix_notm}}. However, you can't use the app to access the {{site.data.keyword.Bluemix_notm}} service and receive an authorization error.
{: tsSymptoms}

The hardcoded credentials in the app might not be correct. Every time that the service is recreated, the credentials to access it change.
{: tsCauses}


Instead of hardcoding the credentials in your app, use connection parameters from the VCAP_SERVICES environment variable. The methods to use connection parameters from the VCAP_SERVICES environment variable vary depending on program languages. For example, for Node.js apps, you can use the following command: 
{: tsResolve}

```
process.env.VCAP_SERVICES
```
For more information about the commands that you can use in other program languages, see [Java](http://docs.run.pivotal.io/buildpacks/java/java-tips.html#env-var){: new_window} and [Ruby](http://docs.run.pivotal.io/buildpacks/ruby/ruby-tips.html#env-var){: new_window}. 
 

 
 





## 502 Bad Gateway errors are received
{: #ts_502_error}

If you receive 502 Bad Gateway errors when you interact with apps on {{site.data.keyword.Bluemix_notm}}, check the {{site.data.keyword.Bluemix_notm}} status page, and then take actions accordingly.

 

You receive error messages that start with 502 Bad Gateway. For example, you might see `502 Bad Gateway: Registered endpoint failed to handle the request.`
{: tsSymptoms}

 

A Bad Gateway error usually happens when you visit a website that uses a proxy server to store and relay the data from the main server that hosts the site. The main server and the proxy server might not properly connect, therefore you see the HTTP status code 502 in your browser window. This status code indicates that the site's main server did not receive the HTTP implementation that it expected from the proxy server.
{: tsCauses}

Other less common causes of a Bad Gateway error are Internet service provider (ISP) dropouts, bad firewall configurations, and browser cache errors. 

 

If you suspect that a {{site.data.keyword.Bluemix_notm}} service is down, first check the [{{site.data.keyword.Bluemix_notm}} status](https://status.chinabluemix.net/){: new_window} page. If the service status is normal, try the following steps to solve the problem: 
{: tsResolve}

  * Retry the action:
    * Reload the page by pressing F5 on your keyboard, or by clicking the refresh button. If this step does not work, clear your browser's cache and cookies, and then reload again.
	* Use a different browser.
	* Reboot your router, your modem, and your computer. Rebooting these devices can clear up various errors that lead to the error 502. 
  * Wait and try again later. In some instances, temporary problems might occur with your Internet service provider or the {{site.data.keyword.Bluemix_notm}} services. You can wait until the temporary problems are solved.
  * If the problem still exists, contact {{site.data.keyword.Bluemix_notm}} support. See [Contacting {{site.data.keyword.Bluemix_notm}} Support](/docs/support/index.html#contacting-bluemix-support){: new_window} for more information. 




## Disk quota is exceeded
{: #ts_disk_quota}

If you run out of disk space, you can manually modify the disk quota to get more disk space.

  

When you run out of disk space, you might see a message that states that the disk quota is exceeded. To resolve the problem, you might have tried scaling up your app instance to get more disk space. For example, you might scale from 256 MB to 1256 MB by changing the memory quota on the app details page. However, because the disk quota remained the same, you did not get more disk space. 
{: tsSymptoms}


The default disk quota that is allocated for an app is 1 GB. If you need more disk space, you must manually specify the disk quota. 
{: tsCauses}

 
Use one of the following methods to specify your disk quota. The maximum disk quota that you can specify is 2 GB. If 2 GB is still not enough, try an external service.
{: tsResolve}

  * In the manifest.yml file, add the following item:
    ```
	disk_quota: <disk_quota>
	```
  * Use the **-k** option with the `cf push` command when you push your app to {{site.data.keyword.Bluemix_notm}}:
    ```
	cf push appname -p app_path -k <disk_quota>
	```

	
	



## Android apps can't receive {{site.data.keyword.mobilepushshort}}
{: #ts_push}

Android apps in certain regions where Google is not accessible can't receive notifications that you send out through the IBM {{site.data.keyword.mobilepushshort}} service. In this case, you can use third-party services as a workaround.

You bind a {{site.data.keyword.mobilepushshort}} service for your Bluemix app and send a message to the registered devices. However, apps that are developed on the Android platform can't receive your notifications in certain regions. 
{: tsSymptoms}

IBM {{site.data.keyword.mobilepushshort}} service uses the Google Cloud Messaging (GCM) service to dispatch notifications to mobile apps that are developed on the Android platform. To enable the Android apps to receive notifications, Google Cloud Messaging (GCM) service must be accessible by the mobile apps. In regions where the GCM service cannot be reached by the Android apps, the Android apps are not able to receive {{site.data.keyword.mobilepushshort}}.
{: tsCauses}

 
Use third-party services that do not rely on the GCM service as a workaround, for example, [Pushy](https://pushy.me){: new_window}, [igetui](http://www.getui.com/){: new_window}, and [jpush](https://www.jpush.cn/){: new_window}.
{: tsResolve}


  
## Executables can't be run on {{site.data.keyword.Bluemix_notm}}
{: #ts_executable}

You might be unable to run executables on {{site.data.keyword.Bluemix_notm}} when those executables were developed and built in a different environment. 

 

You are unable to run executables on {{site.data.keyword.Bluemix_notm}} when those executables were developed and built in a different environment.
{: tsSymptoms}

 

If the content that you want to push to {{site.data.keyword.Bluemix_notm}} is already an executable, the content was previously built and doesn't need to be built on {{site.data.keyword.Bluemix_notm}}. In this case, no buildpack is required for the executable to be run on {{site.data.keyword.Bluemix_notm}}. However, you must explicitly indicate to {{site.data.keyword.Bluemix_notm}} that no buildpack is required.
{: tsCauses}

 

When you push the executable to {{site.data.keyword.Bluemix_notm}}, you must specify a null-buildpack, which indicates that no buildpack is required. Specify a null-buildpack by using the **-b** option with the `cf push` command:
{: tsResolve}

```
cf push appname -p app_path -c <start_command> -b <null-buildpack>
```
For example:
```
cf push appname -p app_path -c ./RunMeNow -b https://github.com/ryandotsmith/null-buildpack
```



	  
## Apps are not automatically restarted
{: #ts_apps_not_auto_restarted}


An app is not automatically restarted when a service that you bind to the app stops working.	  
	  
 

When a service that you bind to an app crashes, problems such as outages, exceptions, and connection failures might occur on the app. {{site.data.keyword.Bluemix_notm}} does not automatically restart the app to recover from these problems.
{: tsSymptoms}



This behavior is by design of Cloud Foundry.
{: tsCauses} 

 

You can manually restart the app by typing the following command in the command line interface:
{: tsResolve}

```
cf push appname -p app_path
```
In addition, you can code the app to identify and recover from problems such as outages, exceptions, and connection failures. 

	    
  

  
  
## Orgs can't be found on {{site.data.keyword.Bluemix_notm}}
{: #ts_orgs}

You might not be able to locate your organization on {{site.data.keyword.Bluemix_notm}} when working on a {{site.data.keyword.Bluemix_notm}} region.
  
 

You can log in to the {{site.data.keyword.Bluemix_notm}} console successfully, but you cannot push apps by using the cf command line interface.
{: tsSymptoms}

When you try to push an application to {{site.data.keyword.Bluemix_notm}} by using the cf command line interface, you see one of the following error messages with the organization name specified in the message: 

`Error finding org`

`Organization not found`



This problem occurs because the API endpoint of the region that you want to work with is not specified, and the organization you're looking for might be in a different region.
{: tsCauses} 

   
  
If you are pushing your application to {{site.data.keyword.Bluemix_notm}} by using the cf command line interface, enter the cf api command and specify the API endpoint of the region. For example, enter the following command to connect to the {{site.data.keyword.Bluemix_notm}} China:
{: tsResolve}

```
cf api https://api.chinabluemix.net
```

  
  


## App routes can't be created
{: #ts_hostistaken}

When you deploy an app to {{site.data.keyword.Bluemix_notm}}, the route of the app can't be created if the host name that you specified is already being used.



When you deploy an app to {{site.data.keyword.Bluemix_notm}}, you see the following error message: 
{: tsSymptoms} 

`Creating route hostname.domainname ... FAILED Server error, status code: 400, error code: 210003, message: The host is taken: hostname`



This problem occurs if the host name that you specified is already being used.
{: tsCauses} 


  
The host name that you specify must be unique within the domain that you are using. To specify a different host name, use one of the following methods:
{: tsResolve} 

  * If you deploy your application by using the `manifest.yml` file, specify the host name in the host option.	 
    ```
    host: host_name	
	```
  * If you deploy your application from the command prompt, use the `cf push` command with the **-n** option. 
    ```
    cf push appname -p app_path -n host_name
    ```


## WAR apps can't be pushed by using the cf push command
{: #ts_cf_war}

You might not be able to use the cf push command to deploy an archived web app to {{site.data.keyword.Bluemix_notm}} if the app location is not specified correctly.
	


When you upload a WAR app to {{site.data.keyword.Bluemix_notm}} by using the `cf push` command, you see the error message, `Staging error: cannot get instances since staging failed.`
{: tsSymptoms} 

 

This problem might happen if the WAR file is not specified, or if the path to the WAR file is not specified. 
{: tsCauses}

 	
	
Use the **-p** option to specify a WAR file or add the path to the WAR file. For example:
{: tsResolve}

```
cf push MyUniqueAppName01 -p app.war
```

```
cf push MyUniqueAppName02 -p "./app.war"
```
For more information about the `cf push` command, enter `cf push -h`. 	





## Double-byte characters aren't displayed properly when Liberty applications are pushed to {{site.data.keyword.Bluemix_notm}}
{: #ts_doublebytes}

Double-byte characters might not be displayed properly if Unicode support is not configured properly for the servlet or JSP files.

 

When a Liberty application is pushed to the {{site.data.keyword.Bluemix_notm}}, the double-byte characters that are specified within the app are not displayed properly.
{: tsSymptoms}

 

The problem might occur if Unicode support is not configured properly for the servlet or JSP files.
{: tsCauses}


You can use the following code within your servlet or JSP file:
{: tsResolve} 

  * In the servlet source file 
    ```
	response.setContentType("text/html; charset=UTF-8");
	```
  * In the JSP 
    ```
	<meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
	```
	
	
	

## Node.js apps can't be deployed
{: #ts_nodejs_deploy}

You might run into problems when you update a Node.js app or deploy a Node.js app to {{site.data.keyword.Bluemix_notm}}.



When you update a Node.js app or deploy your Node.js app to {{site.data.keyword.Bluemix_notm}}, you might see one of the following error messages:
{: tsSymptoms} 

`An app was not successfully detected by any available buildpack.`


`Instance (index 0) failed to start accepting connections.`


`Cannot get instances since staging failed.`


 

The following reasons are possible causes of the problem:
{: tsCauses}
 
  * The start command is not specified.
  * Files that are required to deploy a Node.js app are either missing from the app or placed in a folder other than the root directory.
  


	
Take the following actions based on the cause that leads to the problem:
{: tsResolve} 

  * Specify the start command by one of the following methods: 
      * Use the cf command line interface. For example: 
        ```
		cf push MyUniqueNodejs01 -p app_path -c "node app.js"
		```
	  * Use the [package.json](https://docs.npmjs.com/json){: new_window} file. For example:
	    ```
		{
      ...
  	   "scripts": {
	 		 "start": "node app.js"
 	   }
	}
	    ```
	  * Use the `manifest.yml` file. For example: 
	    ```
		applications:
  name: MyUniqueNodejs01
  ...
  command: node app.js
  ...
        ```

  * Ensure that a `package.json` file exists in your Node.js app to enable the Node.js buildpack to recognize the app. In addition, you must put this file in the root directory of your app.	
    The following example shows a simple `package.json` file:  
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
	
For more tips about Node.js apps, see [Tips for Node.js Applications](http://docs.cloudfoundry.org/buildpacks/node/node-tips.html){: new_window}.	




	
## Apps can't be staged by using custom buildpacks
{: #ts_bp_compilation}

You might not be able to deploy an app to {{site.data.keyword.Bluemix_notm}} by using a custom buildpack if the scripts within the buildpack are not executable.



When you deploy an app to {{site.data.keyword.Bluemix_notm}} by using a custom buildpack, you see the error message, `The application failed to stage, so there are no instances to display.`
{: tsSymptoms} 


This problem might happen if scripts, such as the detect script, the compile script, and the release script, are not executable.
{: tsCauses}

 

You can use the [git update](http://git-scm.com/docs/git-update-index){: new_window} command to change the permission of each script to executable. For example, you can type `git update --chmod=+x script.sh`.
{: tsResolve}
	
	



## Meteor apps can't be pushed
{: #ts_meteor}

You might not be able to push a Meteor application to {{site.data.keyword.Bluemix_notm}} if the buildpack is not specified correctly.

 

When you deploy a Meteor app to {{site.data.keyword.Bluemix_notm}}, you might see the error message, `The application failed to stage, so there are no instances to display.`
{: tsSymptoms}


This problem occurs because no built-in buildpack is provided for Meteor apps. You must use a custom buildpack.
{: tsCauses} 


 

To use a custom buildpack for Meteor apps, use one of the following methods:
{: tsResolve}

  * If you deploy your app by using the `manifest.yml` file, specify the URL or the name of your custom buildpack by using the buildpack option. For example:
  ```
  buildpack: https://github.com/Sing-Li/bluemix-bp-meteor 
  ```
  * If you deploy your application from the command prompt, use the `cf push` command and specify your custom buildpack by using the **-b** option. For example:
    ```
	cf push appname -p app_path -b https://github.com/Sing-Li/bluemix-bp-meteor 
	```
	
  




# Troubleshooting for runtimes
{: #runtimes}

You might experience problems when you useBluemix runtimes. However, in many cases, you can recover from these problems by following a few easy steps.
{:shortdesc}


## Obsolete buildpack used when an app is pushed
{: #ts_loading_bp}


You might not be able to use the latest buildpack components when you push an app. You can use buildpacks that have built-in mechanisms to prevent loading obsolete components, or you can delete the contents in your app's cache directory before you push or restage the app. 

 

When you push or restage an app after the buildpack is updated, the latest buildpack components are not loaded automatically. As a result, your app uses the obsolete buildpack components from the cache. Updates that have been applied to the buildpack since the last time you pushed the app are not implemented. 
{: tsSymptoms}



Some buildpacks are not configured to automatically download all updated components from the internet to ensure that you always use the latest version.
{: tsCauses} 

 

You can use buildpacks that have built-in mechanisms to avoid loading obsolete components. The following buildpacks are two examples: 
{: tsResolve}

  * [Cloud Foundry Java buildpack](https://github.com/cloudfoundry/java-buildpack){: new_window}. This buildpack has a built-in mechanism to ensure that the latest version of the buildpack is used. For more information about how this mechanism works, see [extending-caches.md](https://github.com/cloudfoundry/java-buildpack/blob/master/docs/extending-caches.md){: new_window}. 
  * [Cloud Foundry Node.js buildpack](https://github.com/cloudfoundry/nodejs-buildpack){: new_window}. This buildpack has similar functionality by using environment variables. To enable the Node.js buildpack to download node modules from the internet every time, type the following command in the cf command line interface: 	
  ```
  set NODE_MODULES_CACHE=false
  ```
If the buildpack that you are using does not provide a mechanism to load the latest components automatically, you can manually delete the contents in the cache directory and push your app again by taking the following steps:
  1. Check out a branch of a null buildpack, for example, https://github.com/ryandotsmith/null-buildpack. For information about how to check out a branch, see [Git Basics - Getting a Git Repository](http://www.git-scm.com/book/en/v2/Git-Basics-Getting-a-Git-Repository){: new_window}.  
  2. Add the following line to the `null-buildpack/bin/compile` file and commit the changes. For information about how to commit changes, see [Git Basics - Recording Changes to the Repository](http://www.git-scm.com/book/en/v2/Git-Basics-Recording-Changes-to-the-Repository){: new_window}.
  ```
  rm -rfv $2/*
  ```
  3. Push your app with the null buildpack that was modified to delete the cache by using the following command. After you complete this step, all contents in the cache directory of your app are deleted.
  ```
  cf push appname -p app_path -b <modified_null_buildpack>
  ```
  4. Push your app with the latest buildpack that you want to use by using the following command: 
  ```
  cf push appname -p app_path -b <latest_buildpack>
  ```
  
	


## NOTICE messages from the PHP buildpack
{: #ts_phplog}

You might see messages that contain NOTICE from the logs. You can stop the logging of these messages by changing the logging level.	
	
 

When you push an application to Bluemix by using a PHP buildpack, you might see messages that contain `NOTICE`:
{: tsSymptoms}

```
2015-01-26T15:00:59.70+0100 [App/0] ERR [26-Jan-2015 14:00:59] NOTICE: [pool www] 'user' directive is ignored when FPM is not running as root
2015-01-26T15:01:00.63+0100 [App/0] ERR [26-Jan-2015 14:00:59] NOTICE: [pool www] 'user' directive is ignored when FPM is not running as root
2015-01-26T15:01:00.63+0100 [App/0] ERR [26-Jan-2015 14:00:59] NOTICE: fpm is running, pid 93
2015-01-26T15:01:00.63+0100 [App/0] ERR [26-Jan-2015 14:00:59] NOTICE: ready to handle connections
```



In the PHP buildpack, the error_log parameter is used to define the logging level. By default, the value of the `error_log` parameter is **stderr notice**. The following example shows the default logging level configuration in the `nginx-defaults.conf` file of the PHP buildpack that is provided by Cloud Foundry. For more information, see [cloudfoundry/php-buildpack](https://github.com/cloudfoundry/php-buildpack/blob/ff71ea41d00c1226d339e83cf2c7d6dda6c590ef/defaults/config/nginx/1.5.x/nginx-defaults.conf){: new_window}.
{: tsCauses} 

```
daemon off;
error_log stderr notice;
pid @{HOME}/nginx/logs/nginx.pid;
```

 	
	
The `NOTICE` messages are informational and do not necessarily indicate that a problem has occurred. You can stop the logging of these messages by changing the logging level from stderr notice to stderr error in the nginx-defaults.conf file of your buildpack. For example: 	
{: tsResolve}

```
daemon off;
error_log stderr error;
pid @{HOME}/nginx/logs/nginx.pid;
```
For more information about how to change the default logging configuration, see [error_log](http://nginx.org/en/docs/ngx_core_module.html#error_log){: new_window}.
	

## Unable to import a third-party Python library into {{site.data.keyword.Bluemix_notm}}
{: #ts_importpylib}

You might not be able to import a third-party Python library into {{site.data.keyword.Bluemix_notm}}. You can solve the problem by adding configuration files into the root directory of your python application.


When you try to import a third-party Python library, such as the `web.py` library, the `cf push` command fails.
{: tsSymptoms}


 

This problem occurs when configuration information for the Python application is missing.
{: tsCauses}


 

To solve the problem, add a `requirements.txt` file and a `Procfile` file into the root directory of your Python app. The following information assumes that you are importing the web.py library:
{: tsResolve}

  1. Add a `requirements.txt` file into the root directory of your Python app.
     The `requirements.txt` file specifies the library packages that are required for your Python application and the version of the packages. The following example shows the content of the `requirements.txt` file, where `web.py==0.37` indicates the version of the `web.py` library that will be downloaded is 0.37, and `wsgiref==0.1.2` indicates the version of the web server gateway interface that is required by the web.py library is 0.1.2.
	 ```
	 web.py==0.37
     wsgiref==0.1.2
	 ```
	For more information about how to configure the `requirements.txt` file, see [Requirements files](https://pip.readthedocs.org/en/1.1/requirements.html). 
	 
  2. Add a `Procfile` file into the root directory of your Python application.
	The `Procfile` file must contain the start command for your Python application. In the following command, *yourappname* is the name of your Python application, and *PORT* is the port number that your Python application must use to receive requests from users of the app. *$PORT* is optional. If you do not specify PORT in the start command, the port number under the `VCAP_APP_PORT` environment variable that is inside the app is used instead. 
	```
	web: python <yourappname>.py $PORT
	```
You are now able to import the third-party Python library into {{site.data.keyword.Bluemix_notm}}.	



## The Actions button on the Instance Details page is disabled
{: #ts_actionsbutton}



The Actions button on the Instance Details page is disabled.
{: tsSymptoms} 

 

This problem occurs because of the following reasons:
{: tsCauses}

  * The application is not a Java web application. Runtime Management Utilities (RMU) supports only web applications that are deployed with Liberty buildpacks.
  * The application is not deployed with the embedded Liberty buildpack.
  * The application was deployed with an early version of Liberty buildpack.



If the problem is caused by an early version of Liberty buildpack, redeploy the application in {{site.data.keyword.Bluemix_notm}}. Otherwise, you can provide the following client application log files to the support team:
{: tsResolve} 

  * logs/messages.log
  * logs/stdout.log
  * logs/stderr.log
  

  
  
## Credentials are required when opening trace or dump window
{: #ts_username}


 

A user name and password are required when opening the trace and dump window.
{: tsSymptoms}

 

This problem occurs because of the login session timeout.
{: tsCauses}

 

The solution is to reenter the user name and password.
{: tsResolve}




## Error occurs when trace or dump operations are running
{: #ts_target}

 

An error message is displayed while the trace or dump operations are running. The message indicates that a target instance for an app is not in the running state:	
{: tsSymptoms}

```
Instance 0: Trace specification is set successfully
Instance 2: Trace specification is set successfully
Instance 1: Target instance 1 for app abcd is not in the running state.
Instance 3: Trace specification is set successfully
Instance 4: Trace specification is set successfully
```



This problem occurs because of the following reasons:
{: tsCauses} 

  * The trace or dump management capabilities are only for application instances that are running. Trace or dump operations cannot be used on application instances that are stopped, starting, or crashed.
  * The status of the application instance is changing when the trace or dump dialog is opened. 
  


The solution is to close the window, and then reopen it again.
{: tsResolve} 



## Instances have different traceSpecification configuration
{: #ts_different_config}

 

For different instances of one application, you might see different traceSpecification configuration.
{: tsSymptoms}

 

This problem occurs because of the following reasons:
{: tsCauses}

  * You might have changed the configuration for one or more instances previously. If you change the traceSpecification configuration for one instance, it does not apply to other instances of the same application. For example, you application uses log4j and you have 2 instances for this application. You can change the log level of instance 0 from info to debug, but the log level of instance 1 remains info. 
  * The application scales out and has new instances. RMU does not apply the traceSpecification configuration of the existing instance to the new, scaled out instance. The new instance uses the default configuration. For example, your application uses log4j and it has one instance. You can change the log level of this instance from info to debug. After you make this change, if you scale out your application into two instances, the log level of the new instance is info, rather than debug.
  


This behavior is expected.
{: tsResolve} 





## Disk quota exceeded
{: #ts_diskquota}

You might see, in your app log, that your disk quota is exceeded.

 

You see the `Disk quota exceeded` error message in the log of your app.
{: tsSymptoms}



This problem is caused by one of the following reasons: 
{: tsCauses} 

  * The dump files are generated with the running application instances, and the files use up the allocated disk quota. By default, the disk quota for one application instance is 1 GB. You can check your disk usage by clicking **Dashboard > Application > App Runtime**. The following example shows the runtime information, including disk usage, for two instances of an application:
    ```
    Instance	State	CPU	Memory Usage	Disk Usage

	0		Running	1.0%	344.8MB/512MB	236.8MB/1GB
	2		Running	2.3%	361.2MB/512MB	235.7MB/1GB
    ```
  * The disk quota is limited by the current organization quota.
  
  


You can resolve this issue by using one of the following methods:
{: tsResolve} 

  * Delete dump files after they are downloaded.
  * Redeploy the application with a bigger disk quota by including the following entry in the deployment manifest:
    ```
	disk_quota: 2048
	```
