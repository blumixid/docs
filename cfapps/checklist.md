---

 

copyright:

  years: 2015，2016

 

---

{:shortdesc: .shortdesc} 
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

#Production-ready checklist
Last updated: 13 September 2016
{: .last-updated}

Before your app goes to production, you'll want to make sure that you check that it is ready for production to avoid outages or errors. 
{:shortdesc}

##Things to consider when developing your app
When you're developing your app, you should ensure that you are following good practices. Consider the following:
- Codebase - use revision control such as Git will make your life much easier and provide clarity around the codebase to be deployed to Bluemix. 
- Dependencies - Ensure all dependencies are declared
- Config - Always store config settings in environment variables
- Backing Services - Bluemix catalog includes numerous services (such as IBM Cloudant) on which you can build your app. 
- Build, release, run - Buildpacks for Bluemix will handle the building (e.g. installing npm dependencies), releasing, and running of your app. Other tasks such as building assets can be added as a postinstall script in your package.json file.
- Processes - Processes should be stateless and share-nothing. Bluemix requires one process named web, which is defined in a Procfile. Bluemix will automatically create a Procfile on deployment if one does not exist. Creating a Procfile is optional
- Port binding - Bluemix provides a VCAP_APP_PORT environment variable to your.  Configure your web server process to listen on this port number. Bluemix will then route HTTP requests from port 80 and from port 443 (for HTTPS requests) to this port.
- Concurrency - Bluemix apps scale horizontally by adding additional process instances to an application. The amount of memory allocated to each process and the number of processes to be created can be defined within the manifest.yml file.
- Disposability - Bluemix apps should have disposable processes which can be shut down gracefully with a SIGTERM or shut down suddenly in the case of an underlying system failure. Strive for a crash-only design for your app’s processes. This allows Bluemix to stop or start your processes as needed in order to handle crashes, scaling, or other scenarios.
- Dev/prod parity - Ensure your local development environment closely matches your production environment on Bluemix. There are several approaches to this including using Vagrant or Docker. 
- Logs - Bluemix has built in logging which can be used from the application dashboard 
- Admin processes - Does the app have any one-off admin processes?  Admin processes can be used for tasks such as running database migrations, running a REPL shell.
- Update app via blue green deployment, so it's easy to switch back if problems occur. To learn more about blue green deployments, see [Blue-green deployments](https://console.chinabluemix.net/docs/manageapps/updapps.html#blue_green){:new_window}.
- Use auto-scaling and/or implement throttling of user traffic to avoid overloading
- Stress test the app with load and multiple instances
- Test failure scenarios of services the app depends on (eg DB) -- eg does the app continue running properly after a blip of the DB 
- Monitor the user-facing availability of the app and configure alerting correspondingly
- Deploy across more than one region and implement regional failover

For more guidance on developing cloud apps, see: [Considerations for Designing and Running an Application in the Cloud](https://docs.cloudfoundry.org/devguide/deploy-apps/prepare-to-deploy.html){:new_window}.

##Making your apps Cloud-ready
{: #cloud-readyapps}

A cloud-ready application follows the cloud platform principles when the application is designed and built. A cloud-ready application can use the capabilities that are provided by the cloud platform.

If all of the following principles are observed in your application, the application is cloud-ready and can be deployed to {{site.data.keyword.Bluemix_notm}}. If a principle is violated in your application, you can usually modify your application to adhere to the principles.

* Do not code your application directly to a specific topology.

  In a non-cloud environment, the application might use a particular deployment topology. However, the application topology might change in cloud applications, because the cloud-ready applications and services allow immediate scalability changes. The scalability changes include dynamic scaling and manually resizing the number of instances of an application.

  Build your application to be as generic and stateless as possible to keep your application from being affected by scalability changes.

* Do not assume that the local file system is permanent.

  Because an application instance can be moved, deleted, or duplicated at any time on cloud, do not rely on the files that are written to the file system. If an application uses the local file system as a cache of frequently used information including application logs, the information is lost when the instance is shut down and restarted at a different location or a different VM.

  You can store information in a service, such as an SQL or NoSQL database instead of the local file system. In a dynamic cloud environment, it's also critical to have your logs available on a service that outlives the application instances where the logs are generated.

* Do not store session state in your application.

  The state of your system is defined by your databases and shared storage, and not by each individual running application instance. Statefulness of any sort limits the scalability of an application. Try to minimize the impact of session state by storing it in a centralized location on the server.

  If you can't eliminate session state entirely, push it out to a highly available store that is external to your application server. The stores include IBM WebSphere Extreme Scale, Redis, or Memcached, or an external database.

* Do not use specific infrastructure dependency.

  This is a general principle that has several manifestations. For example, do not assume that the services your application uses are allocated particular host names or IP addresses. Because the services might be relocated or regenerated in your cloud environment, the host names and IP addresses can also change.

  Extracting environment-specific dependencies into a set of property files is an improvement, but it is still inadequate. The best practice is to use an external service registry to resolve service endpoints, or delegate the entire routing function to a service bus or a load balancer with a virtual name.

* Do not use infrastructure APIs in your application.

  If you rely on a specific infrastructure API in your application, changing the infrastructure is more challenging, because an infrastructure API can refer to many different layers in your software stack.

  You can rely on existing open source or commercial products instead, and leave PaaS solutions in the PaaS layer to keep them out of your application code.

* Do not use obscure protocols.

  Do not use obscure protocols that require extra configuration for resiliency.

  Applications based on standard protocols are more resilient with the configuration items delegated to the platform. The standard protocols include HTTP, SSL, standard database, queuing, and web service connections.

* Do not rely on OS-specific features

  If you have already used OS-specific features, you can fix this issue by using compatibility libraries, for example, Cygwin and Mono. Cygwin is a compatibility library that provides a set of Linux tools in a Windows environment. Mono is a compatibility library that provides Windows .NET capabilities in Linux.

  Avoid the OS-specific dependencies; instead, use services that are provided by the middleware infrastructure or service providers.

* Do not manually install your application.

  Your application might be installed frequently on-demand on the dynamic cloud environment. The installation process must be scripted and reliable, and the configuration data must be externalized from the scripts.

  At a minimum, capture your application installation as a uniform set of scripts that are independent of the operating system. Keep your application installation small and portable to adapt to different automation techniques. Also, minimize the dependencies that are required by the application installation.

For more information about cloud-ready applications, see [The 12-factor application](http://12factor.net/){:new_window}.

##Monitoring your app health
After you have deployed your app, you can check the app health by running the `cf app APP_NAME` command. 
You can view the app state, memory usage, and CPU usage of all of your app instances.

In addition, running the `cf events APP_NAME` command let's you see instances of the app crashes.

Lastly, you can monitor all that your app depends on through the Bluemix Status page. For more information, see [Viewing Bluemix status](https://console.chinabluemix.net/docs/support/index.html#viewing-bluemix-status){:new_window}.

For more troubleshooting, including getting app logs, go to: [https://docs.cloudfoundry.org/devguide/deploy-apps/troubleshoot-app-health.html](https://docs.cloudfoundry.org/devguide/deploy-apps/troubleshoot-app-health.html).
