---

 

copyright:

  years: 2015, 2016

 

---

{:shortdesc: .shortdesc} 
{:new_window: target="_blank"}
# What's new in {{site.data.keyword.Bluemix_notm}}
Last updated: 16 August 2016
{: .last-updated}

Stay up-to-date with the new features and services that are available in {{site.data.keyword.Bluemix}}, so that you get the most out of your {{site.data.keyword.Bluemix_notm}} experience. The updates are organized into these categories: [{{site.data.keyword.Bluemix_notm}} platform](index.html#platform_category), [{{site.data.keyword.Bluemix_local}} and {{site.data.keyword.Bluemix_dedicated}}](index.html#dedicatedandlocal), [Compute](index.html#compute_category), and [Services](index.html#services_category). 
{:shortdesc}

## {{site.data.keyword.Bluemix_notm}} platform
{: #platform_category}

### Set email notifications for your {{site.data.keyword.Bluemix}} account
*New as of: 12 July 2016*

You can now set platform notifications, in addition to the existing spending notification capability, for your {{site.data.keyword.Bluemix}} account. Choose to receive an email notification regarding platform-wide {{site.data.keyword.Bluemix}} incidents or planned {{site.data.keyword.Bluemix}} maintenance events. To learn more about how to set these notifications, see [Setting notifications](../admin/account.html#notifications). And, remember, you can always see the latest status of incidents and planned maintenance events by visiting the [Status](http://ibm.biz/bluemixstatus){: new_window} page. 

### Check out the new user experience for the {{site.data.keyword.Bluemix_notm}} docs
*New as of: 27 June 2016*

The {{site.data.keyword.Bluemix_notm}} team has been working on an improved design that starts to break the traditional help system barriers, which hopefully provides you a better learning experience. [Check it out](https://console.{DomainName}/docs) now, or read more about the updates in the blog: [{{site.data.keyword.Bluemix_notm}} docs get a facelift](https://developer.ibm.com/bluemix/2016/06/27/bluemix-docs-get-facelift/){: new_window}.

### Streamlined account management experience is now available
*New as of: 16 May 2016*

Managing one or multiple {{site.data.keyword.Bluemix_notm}} accounts just got easier! With the new global account management feature, you have a single place to view and manage all of your orgs, spaces, and team members that are a part of your {{site.data.keyword.Bluemix_notm}} account. Viewing orgs across multiple regions and all of the team members within each org and space can be accomplished in just a few clicks.

From **{{site.data.keyword.avatar}}** &gt; **Account**, you can quickly complete the following tasks:

* See and manage all accounts that you are a member of
* See all team members within your account in a single view
* Remove any person from your account
* See and manage all of the orgs and spaces, even across all of the regions, including setting team member access 
* Invite one or multiple team members at once to your orgs and spaces
* Manage org and space access for pending team members, and resend or cancel pending inviatations as needed
* Change your profile settings, including the option to add a picture


For more details about the latest account management updates in {{site.data.keyword.Bluemix_notm}}, see [Announcing: Gobal Account Management](https://developer.ibm.com/bluemix/2016/05/16/announcing-global-account-management-in-bluemix/){: new_window}.


### A tour of the new {{site.data.keyword.Bluemix_notm}} user interface
*New as of: 13 April 2016*

You can learn more about the new user interface in the new video posted on the [Try the new Bluemix user experience](https://developer.ibm.com/bluemix/2016/04/13/try-the-new-bluemix-user-experience/){: new_window}. blog post. Try it out today by clicking **Try the new experience** in the header bar. 

### Check out the new user experience for {{site.data.keyword.Bluemix_notm}}
*New as of: 1 March 2016*

{{site.data.keyword.Bluemix_notm}} has been listening to your feedback on the user interface (UI) and has used it to design a brand new user experience that streamlines many workflows. The new experience is available for your immediate use. When you visit the {{site.data.keyword.Bluemix_notm}} UI, you can choose to use the new experience by clicking **Try the new {{site.data.keyword.Bluemix_notm}}** link in the header bar. And, you can use the Feedback tool to submit feedback at any time.

For more information about what has changed with the new look and feel, see [The new {{site.data.keyword.Bluemix_notm}} look](https://developer.ibm.com/bluemix/2016/03/01/try-the-new-bluemix-look/){: new_window}.

### Anyone can contribute to {{site.data.keyword.Bluemix_notm}} documentation
*New as of: 13 January 2016*

The {{site.data.keyword.Bluemix_notm}} team is now sourcing content in Markdown and storing the content in GitHub. If you are using the docs, and you identify an area in which you can contribute an improvement by adding an example or best practice from your own experience, then simply click the **Edit in GitHub** link on the page. When you click the link, you are directed to the source file in GitHub, and you can fork the project to suggest fixes or enhancements. For more information about how to contribute to the docs, see [When it comes to docs, anyone can contribute in {{site.data.keyword.Bluemix_notm}}](https://developer.ibm.com/bluemix/2016/01/13/bluemix-docs-now-open-source-on-github/){: new_window}.

## {{site.data.keyword.Bluemix_notm}} Local and {{site.data.keyword.Bluemix_notm}} Dedicated
{: #dedicatedandlocal}

### July updates for the administration console
*New as of: 9 August 2016*

With the latest updates from July, you can expect the following updates, improvements, or new features:

* As an Admin Console administrator, you can set preferred preapproved maintenance windows for non-disruptive updates to be applied. The preferred windows that are set are used by the {{site.data.keyword.Bluemix_notm}} deployment team when scheduling the updates for your environment. For more information see, [Setting preapproved maintenance windows](../admin/index.html#preapprovedmaintenance).
* As an Admin Console administrator, you can reschedule an already scheduled maintenance update deployment as long as the deployment start and date time is at least 24 hours away. Open the details view for any scheduled deployment to find the reschedule deployment link.
* As an Admin Console administrator, there is a new option available when setting up email or webhook subscriptions. Previously, all event subscriptions sent notifications for every region that the alert applied to. Now, on the event subscription form, you can choose to **Combine notifications** for all regions into a single alert.
* As an Admin Console administrator, you can choose to use an API command to enable organization managers, who do not have administration console admin permissions or users permissions, to invite new users into their organization who do not already exist in the {{site.data.keyword.Bluemix_notm}} environment. For more information, see [Managing users with the Admin REST API](../admin/index.html#usingadminapi).
* As an environment administrator, you can use the [Bluemix Admin CLI](../cli/plugins/bluemix_admin/index.html) to work with application security groups to control network traffic for apps that are tied to specific spaces or application group sets.


### Managing system updates
*New as of: 1 June 2016*

From the **System Information** tile in the administration console, as an administration, you can now manage your local or dedicated environment's maintenance updates by setting available and unavailable date windows for the {{site.data.keyword.Bluemix_notm}} deployment team to use when scheduling your deployments. By using the new system updates process, you now have visibility and control over the scheduling and deployment of maintenance updates for your {{site.data.keyword.Bluemix_notm}} environment.

The new system updates process splits maintenance updates into two categories: non-disruptive and disruptive. A non-disruptive update does not affect your environment, your running applications, or your users' access to your applications, while a disruptive update might affect the listed components. Based on the update category type, the {{site.data.keyword.Bluemix_notm}} deployment team either schedules the update during your already set and approved update windows (non-disruptive), or you are prompted for approval through the administration console for scheduling the deployment date and time (disruptive).

To get started with the new system update process, review the differences between non-disruptive and disruptive updates in the [Maintenance updates](../admin/index.html#oc_schedulemaintenance) section of the documentation. Then, you can work on [Setting preapproved maintenance windows](../admin/index.html#preapprovedmaintenance), so that the deployment team can start scheduling non-disruptive updates right away. Finally, you can review [Scheduling and approving updates](../admin/index.html#scheduleandapprove) to understand more about the deployment scheduling process for disruptive updates.

### Setting up notifications for incidents and maintenance events
*New as of: 1 June 2016*

With the new subscriptions feature, you can extend the functionality of the notifications that are sent to the Administration page and the Status page by using event subscriptions to set up alerts in a custom email message, or you can use the webhooks functionality to integrate alerts with a tool of your choice. For example, if you select the webhooks option, your notifications can be routed directly to a destination of your choice, such as a phone number (by SMS message) or Slack post. The alert notifications for both methods can be customized for maintenance updates or critical incident alerts, and the information that is included in the body of each notification can be tailored for your needs.

To learn more about setting up your custom incident or maintenance alerts, see [Notifications and event subscriptions](../admin/index.html#oc_eventsubscription).


## Compute
{: #compute_category}

<!-- Updates for this category include bare metal (preconfigured), openstack VMs, containers, CF apps (runtimes, buildpacks, cf items) and whisk -->

### New Liberty for Java buildpack v3.1
*New as of: 22 July 2016*

The new Liberty for Java v3.1 provides enhanced application management functionality that supports federated authentication. It also adds support for the [Dynatrace Ruxit](http://www.dynatrace.com/en/ruxit/){: new_window} application monitoring agent. It provides an updated data collector for the [Monitoring and Analytics service](../services/monana/index.html) and updated agent for the [Auto-Scaling service](../services/Auto-Scaling/index.html). The monthly Liberty runtime version was updated to the 2016.7.0.0 release. For more infromation about the release, see [Beta: WebSphere Liberty and tools (July 2016)](https://developer.ibm.com/wasdev/blog/2016/06/30/beta-websphere-liberty-and-tools-july-2016/){: new_window}.

### New SDK for Node.js buildpack v3.6
*New as of: 22 July 2016* 

The new SDK for Node.js v3.6 provides enhanced application management functionality that supports federated authentication. It provides an updated data collector for the [Monitoring and Analytics service](../services/monana/index.html). The SDK for Node.js runtime versions provided are 0.10.45, 0.10.46, 0.12.14, 0.12.15, 4.4.6, 4.4.7, 6.2.1, and 6.2.2, with 4.4.7 being the default.

### Upgrade to the ASP.NET Core buildpack
*New as of: 12 July 2016*

This buildpack makes the .NET Core V1.0 and .NET Core SDK V1.0 Preview 2 available in {{site.data.keyword.Bluemix_notm}}. Existing RC2 apps will continue to work with this buildpack as long as you specify the correct SDK version in your global.json file.

### Updates to {{site.data.keyword.appserver_full}}
*New as of: 24 June 2016*

The {{site.data.keyword.appserver_short}} team has the added ability for clients to to choose between V8.5 and V9.0 when you create a new `Traditional ND` or `Traditional WebSphere` instance. The team also upgraded the {{site.data.keyword.appserver_short}} for {{site.data.keyword.Bluemix_notm}} binaries so that new instances of {{site.data.keyword.appserver_short}} Liberty (Core and ND Plans) will have fixpack 16.0.0.2 installed. Additionally, [several security vulnerabilities](http://www-01.ibm.com/support/docview.wss?uid=swg21984977){: new_window} that affect {{site.data.keyword.appserver_short}} for {{site.data.keyword.Bluemix_notm}} have been addressed. For more information on these updates, see the [latest updates](../services/ApplicationServeronCloud/latestUpdates.html) section.

### Liberty buildpack v3.0 update
*New as of: 20 June 2016*

Liberty buildpack v3.0 with the latest version of [WebSphere Liberty](http://www-01.ibm.com/common/ssi/ShowDoc.wss?docURL=/common/ssi/rep_ca/4/897/ENUS216-264/index.html&lang=en&request_locale=en){: new_window} is now deployed in {{site.data.keyword.Bluemix_notm}}. The new Liberty runtime will be part of the upcoming WebSphere Application Server V9 release. With the v3.0 buildpack, the new runtime is available for {{site.data.keyword.Bluemix_notm}} applications first and is available a week ahead of the official release date! For more information, see [Buildpack defaults](../runtimes/liberty/buildpackDefaults.html).

### ASP.NET Core buildpack beta is now available
*New as of: 16 June 2016*

The ASP.NET Core buildpack, formerly known as the ASP.NET 5 buildpack, is now available as a beta buildpack. The ASP.NET Core buildpack v0.8.1 is compatible with RC2 of the .NET Core runtime and libraries.

### Liberty for Java buildpack 2.9 and {{site.data.keyword.sdk4node}} buildpack 3.4 are available
*New as of: 1 June 2016*

The Liberty for Java buildpack v2.9 provides an updated version of the WebSphere Liberty runtime, several defect fixes, and other small improvements. The SDK for Node.js buildpack v3.4 includes defect fixes and the following IBM SDK for Node.js runtimes: 0.10.45, 0.12.14, 4.4.4, 6.0.0, and 6.0.1. Version 4.4.4 is the default.

### Liberty for Java buildpack 2.8 and {{site.data.keyword.sdk4node}} buildpack 3.3 are available
*New as of: 9 May 2016*

The Liberty for Java buildpack version 2.8 and the {{site.data.keyword.sdk4node}} buildpack version 3.3 are now deployed in {{site.data.keyword.Bluemix_notm}} including new features and multiple defect fixes. The Liberty for Java buildpack version 2.8 includes the updated WebSphere Liberty runtime, the latest IBM SDK for Java 7.1 SR3 FP40 and 8.0 SR3, and the initial AppDynamic integration. The {{site.data.keyword.sdk4node}} buildpack version 3.3 includes new Node.js runtime 4.4.0, 4.4.1, 4.4.2, 4.4.3, 0.12.13 and 0.10.44, which contains multiple security fixes. The updated version also brings FIPS-enabled mode support for Node.js 4.3.1 and later.


### The {{site.data.keyword.sdk4node}} v3.2 buildpack is available
*New as of: 25 March 2016*

The {{site.data.keyword.sdk4node}} v3.2 buildpack includes several security fixes. For information about the fixes, see the [Security Bulletin](http://www.ibm.com/support/docview.wss?uid=swg21979050){: new_window}. The update does not impact staged applications, and it will be picked up only when your application is repushed or restaged.

Use the blue-green deployment technique to test your application with the updated buildpacks before you use it for production. For more information about the blue-green deployment technique, see [Updating apps](../manageapps/updapps.html#blue_green).

### The Liberty for Java v2.7 buildpack is available
*New as of: 25 March 2016*

The Liberty for Java buildpack v2.7 includes the latest WebSphere Liberty runtime and IBM SDK for Java, as well as a few other updates including the updated the DB2 JDBC driver to 4.19.49.


### {{site.data.keyword.sdk4node}} v3.1 buildpack is now available
*New as of: 16 March 2016*

The {{site.data.keyword.sdk4node}} buildpack v3.1 updates the the default Node.js runtime from 4.2.4 to 4.3.0. The new buildpack also includes versions 0.10.42, 0.12.10, and 4.2.6. The update does not impact staged applications and will be picked up only when your application is repushed or restaged. 

Use the blue-green deployment technique to test your application with the updated buildpacks before you use it for production. For more information about the blue-green deployment technique, see [Updating apps] (../manageapps/updapps.html#blue_green).


### The Liberty for Java v2.6 buildpack is now available
*New as of: 16 March 2016*

The Liberty for Java buildpack v2.6 makes it easy to use the [Dynatrace](http://www.dynatrace.com/en/index.html) and [DynamicPULSE](http://www.fujitsu.com/jp/group/fsweb/products/dynamic-pulse/) services. The update does not impact staged applications, and the update will be picked up only when your application is repushed or restaged. 

Use the blue-green deployment technique to test your application with the updated buildpacks before you use it for production. For more information on the blue-green deployment technique, see [Updating apps](../manageapps/updapps.html#blue_green).

### {{site.data.keyword.Bluemix_notm}} CLI v0.3.0 is available
*New as of: 25 February 2016*

{{site.data.keyword.Bluemix_notm}} is pleased to announce that the {{site.data.keyword.Bluemix_notm}} CLI (Command Line Interface) v0.3.0 is now generally available for [download](http://clis.ng.bluemix.net/ui/home.html){: new_window}. The {{site.data.keyword.Bluemix_notm}} CLI provides a unified way for you to  manage your applications, containers, virtual servers, and services. Plug-ins are also available to extend your CLI capability. To learn more about everything you can do with the CLI and available options, see [Use {{site.data.keyword.Bluemix_notm}} CLI to manage your applications, containers, virtual servers and services](https://developer.ibm.com/bluemix/2016/02/25/bluemix-cli/){: new_window}.


### {{site.data.keyword.openwhisk}} experimental compute service is now available
*New as of: 22 Februrary 2016*

{{site.data.keyword.openwhisk}} is a distributed, event-driven compute service. {{site.data.keyword.openwhisk_short}} executes application logic in response to events or direct invocations from web or mobile apps over HTTP. Events can be provided from {{site.data.keyword.Bluemix_notm}} services like Cloudant, and from external sources. As developers, you can focus on writing application logic and creating actions that are executed on demand. The rate of executing actions always matches the event rate, resulting in inherent scaling and resiliency, and optimal utilization. You pay for only what you use, and you don't have to manage a server.

To learn more about {{site.data.keyword.openwhisk_short}}, see [Getting started with {{site.data.keyword.openwhisk_short}}](../openwhisk/index.html).

## Services
{: #services_category}

### New changes in {{site.data.keyword.mobilepushshort}} service
New as of: 4 August 2016

#### User ID-based notifications
Do you wish to engage with specific users by sending push notifications by their user name or identifier rather than by device identifier? This is now possible with {{site.data.keyword.mobilepushshort}} service on {{site.data.keyword.Bluemix_notm}}. User ID-based notifications are notification messages that are targeted to a specific user. Many devices can be registered with one user.

During device registration you will need to provide a user ID and client secret. Client secret is allocated when the service is provisioned and can be obtained from the console. Use the regisgterDeviceWithUserId API to register the device for push notifications. From the console, send notifications to specific user Ids. For more information see, [Enabling user-based notifications](../services/mobilepush/c_user_basednotifications.html).

#### Server-side Swift SDK
Are you a Swift user using Swift on client and server-side to build your applications? There is now a Swift server-side SDK for sending push notifications by using {{site.data.keyword.Bluemix_notm}} {{site.data.keyword.mobilepushshort}} services. Check out the [Swift server-side SDK](https://github.com/ibm-bluemix-mobile-services/bms-pushnotifications-serversdk-swift){: new_window}.

#### {{site.data.keyword.mobilepushshort}} as an unbound service
You can now access the {{site.data.keyword.mobilepushshort}} service from an application that runs outside {{site.data.keyword.Bluemix_notm}} as the service now supports unbound mode. Refer to the {{site.data.keyword.Bluemix_notm}} documentation on how to [enable external apps to use {{site.data.keyword.Bluemix_notm}} service](../services/reqnsi.html#accser_external).

### Updates to IBM Eclipse Tools for {{site.data.keyword.Bluemix_notm}}

Finally, a new version of IBM Eclipse Tools for {{site.data.keyword.Bluemix_notm}} is now available for download. Some of the capabilities introduced in this update include the ability to map and unmap projects to cloud applications, service creation wizard improvements, support for {{site.data.keyword.Bluemix_notm}} Dedicated, and more!


