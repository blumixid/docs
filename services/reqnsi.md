---

copyright:
  years: 2015, 2016

---

{:new_window: target="_blank"}  
{:shortdesc: .shortdesc}


# Adding a service to your application
{: #add_service}

Last updated: 8 September 2016
{: .last-updated}

{{site.data.keyword.Bluemix_notm}} has a list of services and manages them on behalf of the developers. To add a service for your application to use, you must request an instance of this service and configure the application to interact with the service.

You can see all the services that are available in {{site.data.keyword.Bluemix_notm}} in the following ways:

* From the {{site.data.keyword.Bluemix_notm}} user interface. View the {{site.data.keyword.Bluemix_notm}} Catalog.
* From the cf command line interface. Use the **cf marketplace** command.
* From your own application. Use the [GET /v2/services Services API](http://apidocs.cloudfoundry.org/197/services/list_all_services.html){: new_window}.

You can select the service that you need when you develop applications. Upon your selection, {{site.data.keyword.Bluemix_notm}} interacts with the service and takes necessary steps to provision resources of the service. The provisioning process might be different for different types of services. For example, a database service creates a database, and a push notification service for mobile applications generates configuration information.

{{site.data.keyword.Bluemix_notm}} provides the resources of a service to your application by using a service instance. A service instance can be shared across web applications.

You can also use services that are hosted in other regions if those services are available in those regions. These services must be accessible from the internet and have API endpoints. You must manually code your application to use these services in the same way that you code external applications or third-party tools to use {{site.data.keyword.Bluemix_notm}} services. For more information, see [Enabling external applications and third-party tools to use {{site.data.keyword.Bluemix_notm}} services](#accser_external).




## Requesting a new service instance
{: #req_instance}

To request a new service instance, you must use the {{site.data.keyword.Bluemix_notm}} user interface or the cf command line interface.

**Note:** When you specify the service name, avoid using characters other than alphabetic or numeric characters, because results might be unpredictable.

If you use the {{site.data.keyword.Bluemix_notm}} user interface to request a service instance, complete the following steps:

1. In the {{site.data.keyword.Bluemix_notm}} **Catalog**, click the tile for the service that you want to add. The service details page opens.

2. In the Add Service pane, select an application that you want to bind this service instance to from the **App** list.

3. Type a name in the **Service name** field. A default service name is provided. You can change the name in the field, or leave it unchanged.

4. Complete additional fields or selections, and then click **CREATE**.

If you use the cf command line interface to request a service instance, complete the following steps:

1. Use the **cf marketplace** command to find the name and the plan of the service that you require.

2. Use the following command to create a service instance, where service_name is the name of the service, service_plan is the plan of the service, and service_instance is the name that you want to use for this service instance.

    ```
    cf create-service service_name service_plan service_instance
    ```

3. Use the following command to bind the service instance to an application, where appname is the name of the application, and service_instance is the name of the service instance.

    ```
    cf bind-service appname service_instance
    ```

You can bind a service instance to only those app instances that are in the same space or org. However, you can use service instances from other spaces or orgs in the same way that an external app does. Instead of creating a binding, use the credentials to directly configure your app instance. For more information about how external apps use {{site.data.keyword.Bluemix_notm}} services, see [Enabling external apps to use {{site.data.keyword.Bluemix_notm}} services](#accser_external){: new_window}.  
  
  


## Configuring your application to interact with a service
{: #config}

After you bind a service instance to your application, you must configure your application to interact with the service.

Each service might require a different mechanism for communicating with applications. These mechanisms are documented as part of the service definition for your information when you develop applications. For consistency, the mechanisms are required for your application to interact with the service.

* To interact with database services, use the information that {{site.data.keyword.Bluemix_notm}} provides such as the user ID, password, and the access URI for the application.
* To interact with mobile back-end services, use the information that {{site.data.keyword.Bluemix_notm}} provides such as the application identity (app ID), security information that is specific to the client, and the access URI for the application. The mobile services typically work in context with each other so that context information, such as the name of the application developer and the user that uses the application, can be shared across the set of services.
* To interact with web applications or server-side cloud code for mobile applications, use the information that {{site.data.keyword.Bluemix_notm}} provides such as the runtime credentials in the *VCAP_SERVICES* environment variable of the application. The value of the *VCAP_SERVICES* environment variable is the serialization of a JSON object. The variable contains the runtime data that is required to interact with the services that the application is bound to. The format of the data is different for different services. You might need to read the service documentation about what to expect and how to interpret each piece of information.

If a service that you bind to an application crashes, the application might stop running or have errors. {{site.data.keyword.Bluemix_notm}} does not automatically restart the application to recover from these problems. Consider coding your application to identify and recover from outages, exceptions, and connection failures. See the [Apps won't be automatically restarted](../troubleshoot/index.html#ts_topmenubar) troubleshooting topic for more information.

## Enabling external apps to use {{site.data.keyword.Bluemix_notm}} services
{: #accser_external}

You might have applications that were created and run outside of {{site.data.keyword.Bluemix_notm}}, or you might use third-party tools. If {{site.data.keyword.Bluemix_notm}} services provide endpoints that are accessible from the internet, you can use those services with your local apps or third-party tools.

To enable an external app or third-party tool to use a {{site.data.keyword.Bluemix_notm}} service, complete the following steps:

1. Request an instance of the service.
    1. On the Dashboard in the {{site.data.keyword.Bluemix_notm}} user interface, click **Use Services or APIs**. The Catalog displays.
    2. From the Catalog, select the service that you want by clicking the service tile. The service details page opens.
    3. In the Add Service window, keep the **App**: list selection as **Leave unbound**. This selection means that the service will not be connected to a {{site.data.keyword.Bluemix_notm}} app.
    4. Make any other selections as needed. Then, click **CREATE**. A service instance is created, and the service Dashboard displays.
2. In the service Dashboard, you can select **Service Credentials** to view or add credentials in JSON format. Use the API key that is displayed as the credentials to connect to the service instance.

Your application that runs outside of {{site.data.keyword.Bluemix_notm}} can now access the {{site.data.keyword.Bluemix_notm}} service.

**Note:** If you want to delete service instances or check the billing information, you must go back to your Dashboard in the user interface to manage the service instances.

## Creating a user-provided service instance
{: #user_provide_services}

You might have resources that are managed outside of {{site.data.keyword.Bluemix_notm}}. If you have credentials to access those external resources from the internet, you can create {{site.data.keyword.Bluemix_notm}} user-provided service instances to represent and communicate with your external resources.

To create a user-provided service instance and bind it to an application, complete the following steps:

1. Create a user-provided service instance by using either the **cf create-user-provided-service** or the **cf cups** command:
    * To create a general user-provided service instance, use the **-p** option, and separate the parameter names with commas. The cf command line interface then prompts you for each parameter in turn. For example:
        ```
        cf cups testups1 -p "host, port, dbname, username, password"
        host> pubsub01.example.com
        port> 1234
        dbname> sampledb01
        username> pubsubuser
        password> p@$$w0rd
        Creating user provided service testups1 in org my-org / space dev as user@sample.com...
        OK
        ```

    * To create a service instance that drains information to a third-party log management software, use the **-l** option, and specify the destination that the third-party log management software provides. For example:

        ```
        cf cups testups2 -l syslog://example.com
        Creating user provided service testups2 in org my-org / space dev as user@sample.com...
        OK
        ```

    If you want to update one or more parameters of the user-provided service instance, use either the **cf update-user-provided-service** or the **cf uups** command.

    * To update a general user-provided service instance, use the **-p** option, and specify the parameter keys and values in a json object. For example:

        ```
        cf uups testups1 -p "{\"username\":\"pubsubuser2\",\"password\":\"p@$$w0rd2\"}"
        Updating user provided service testups1 in org my-org / space dev as user@sample.com...
        OK
        ```

    * To create a service instance that drains information to a third-party log management software, use the -l option. For example:

        ```
        cf uups testups2 -l syslog://example2.com
        Updating user provided service testups2 in org my-org / space dev as user@sample.com...
        OK
        ```

2. Bind the service instance to your application by using the cf bind-service command. For example:

	```
	cf bind-service myapp testups1
	Binding service testups1 to app myapp in org my-org / space dev as user@sample.com...
	OK
	```

You can now configure your application to use the external resources. For information on how to configure your application to interact with a service, see [Configuring your application to interact with a service](#config){: new_window}.

		 
## Using services in another service
{: #s2s_binding}

Service access authorization provides a way for one service to access another service
directly. You can authorize and configure a service instance's access to other service instances on
the {{site.data.keyword.Bluemix_notm}} Dashboard.

To use a service instance from another service, complete the following steps:

1. On the {{site.data.keyword.Bluemix_notm}} Dashboard, click
the tile for the service that you want to access. The dashboard for the service is displayed.
2. In the navigation pane, click *Manage* to authorize the binding from other service instances by using the console of the service instance.
3. If you want to deny other services access to the service instance, click *Service Access Authorization* in the navigation pane and then use *Revoke* to remove the service binding.

# rellinks
{: #rellinks}

## general
{: #general}
* [Binding a service by using {{site.data.keyword.Bluemix_notm}} user interface](../cfapps/ee.html#ee_bindui)
* [Retrieving VCAP_SERVICES](../cli/vcapsvc.html)
