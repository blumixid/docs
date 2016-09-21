---

 

copyright:

  years: 2015，2016

 

---

{:shortdesc: .shortdesc} 
{:new_window: target="_blank"}

# Creating Cloud Foundry apps
Last updated: 12 September 2016
{: .last-updated}

With {{site.data.keyword.Bluemix_notm}}, you can create your app in the {{site.data.keyword.Bluemix_notm}} user interface. After it's created, you can decide to continue to use the UI, use the cf command line interface to develop, track, plan, and deploy your app.
{:shortdesc}

When you create an app in {{site.data.keyword.Bluemix_notm}}, you begin with a starter. A *starter* is a template that includes predefined services and application code that is configured with a particular buildpack. There are two types of starters: boilerplates and runtimes.

A *boilerplate* is a container for an application and its associated runtime environment and predefined services for a particular domain. For example, the Mobile Cloud boilerplate includes a Node.js runtime, as well as the Mobile Data, Mobile Application Security, and Push services. It also includes an SDK and sample applications to get started developing mobile apps that access these services.

A *runtime* is the set of resources that is used to run an application. {{site.data.keyword.Bluemix_notm}} provides runtime environments as containers for different types of applications. The runtime environments are integrated as buildpacks into {{site.data.keyword.Bluemix_notm}}, are automatically configured for use, and require little to no maintenance.

To get started creating your application, take the following steps:
  1. Go to the Dashboard in the {{site.data.keyword.Bluemix_notm}} user interface.
  2. Click **CREATE AN APP**.
  3. Click **WEB** and follow the guided experience to choose a starter, specify a name, and select how you want to code.
  4. When you are finished with the guided experience, click **VIEW APP OVERVIEW**. The Overview for your app is displayed on the Dashboard.
  5. You can add a service to your app by clicking **ADD A SERVICE OR API** on the app Overview in the Bluemix user interface. Browse and select services from the catalog, or, scroll to the end of the catalog and click **{{site.data.keyword.Bluemix_notm}} Experimental Services** to browse experimental services. Or, you can use the cf command line interface. See Options for working with apps.
  

**Note:** If a service that you bind to an app crashes, the app might stop running or have errors. {{site.data.keyword.Bluemix_notm}} does not automatically restart the app to recover from these problems. Consider coding your app to identify and recover from outages, exceptions, and connection failures. See the Apps are not automatically restarted troubleshooting topic for more information.

## Options for working with apps

After your app is created, you have a few options for continuing to add services to your app and to build and deploy your app:

<dl><dt>cf command line interface</dt>
<dd>Use the cf command line interface to update your application, create a service instance, or bind the service to your application. You can also use the cloud-cli command line interface to create, update, and delete service offerings.</dd>
<dt>{{site.data.keyword.Bluemix_notm}} user interface</dt>
<dd>Use the {{site.data.keyword.Bluemix_notm}} user interface to build your application, including picking which services and runtimes to combine to solve your business problem.</dd>
</dl>

