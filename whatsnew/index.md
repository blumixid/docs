---

 

copyright:

  years: 2015, 2016
 
lastupdated: "2016-11-21" 

---

{:shortdesc: .shortdesc} 
{:new_window: target="_blank"}
# What's new in {{site.data.keyword.Bluemix_notm}}


Stay up-to-date with the new features and services that are available in {{site.data.keyword.Bluemix}}, so that you get the most out of your {{site.data.keyword.Bluemix_notm}} experience. The updates are organized into these categories: [{{site.data.keyword.Bluemix_notm}} platform](index.html#platform_category), [{{site.data.keyword.Bluemix_local}} and {{site.data.keyword.Bluemix_dedicated}}](index.html#dedicatedandlocal), [Compute](index.html#compute_category), and [Services](index.html#services_category). 
{:shortdesc}

## {{site.data.keyword.Bluemix_notm}} platform
{: #platform_category}

### Set email notifications for your {{site.data.keyword.Bluemix}} account
*New as of: 12 July 2016*

You can now set platform notifications, in addition to the existing spending notification capability, for your {{site.data.keyword.Bluemix}} account. Choose to receive an email notification regarding platform-wide {{site.data.keyword.Bluemix}} incidents or planned {{site.data.keyword.Bluemix}} maintenance events. To learn more about how to set these notifications, see [Setting notifications](/docs/admin/account.html#notifications). And, remember, you can always see the latest status of incidents and planned maintenance events by visiting the [Status](http://www.{DomainName}/status){: new_window} page. 

### Check out the new user experience for the {{site.data.keyword.Bluemix_notm}} docs
### Experience the new {{site.data.keyword.Bluemix_notm}} 
New as of: 18 October 2016

While you've been busy making awesome applications, the {{site.data.keyword.Bluemix_notm}} team has been busy improving and tailoring the user interface just for you. You can expect a fast performance based on the new micro-services architecture, resources just a click away, a simplified catalog of services, improved metrics views, and a lot more. Learn more in the latest blog post: Say [Hello to the new {{site.data.keyword.Bluemix_notm}} Experience](https://www.ibm.com/blogs/bluemix/2016/10/say-hello-new-bluemix-experience/){: new_window}.

## {{site.data.keyword.Bluemix_notm}} Local and {{site.data.keyword.Bluemix_notm}} Dedicated
{: #dedicatedandlocal}

### October updates for the administration console
{: #octadminconsole}
*New as of: 31 October 2016*

With the latest updates and improvements from October, you can use the following new features:

* View metrics about your environment and applications by using API. See [API for metrics (experimental)](/docs/admin/index.html#envappmetricsapi) for more information.
* Find and set container quotas for an organization by using the {{site.data.keyword.Bluemix_notm}} admin CLI. See [Finding and setting container quotas for an organization](/docs/cli/plugins/bluemix_admin/index.html#containquotas) for more information.
* View more detailed information for each scheduled maintenance update for your environment, and then you can include these details when you create your maintenance update notifications.  

### September updates for the administration console
{: #septadminconsole}
New as of: 30 September 2016

With the latest updates and improvements from September, you can use the following new features:

* Configure webhook notifications to be sent when an event occurs or when the event is updated. See [Setting up notification subscriptions](/docs/admin/index.html#seteventsub) for more information.
* Subscribe to threshold notifications from the Subscriptions page. See [Setting up notification subscriptions](/docs/admin/index.html#seteventsub) for more information.
* View historical data for disk usage from the Resource Usage page. See [Memory, disk, and CPU details](/docs/admin/index.html#resourceusagedetails) for more information.
* View and change the maintenance windows for preapproved non-disruptive maintenance times for your system or schedule unavailable update windows of time in which your environment is not available for non-disruptive maintenance updates. See [Setting preapproved maintenance windows](/docs/admin/index.html#preapprovedmaintenance) and [Setting unavailable maintenance windows](/docs/admin/index.html#blockpreapprovedmaintenance) for more information.
* More easily view and use the System Information page with the latest layout improvements. 
* Issue a CLI command to enable managers in your organization to add users to your organization, without additional permissions. You can issue this command if you are an Admin superuser for that organization. See [Bluemix admin CLI](/docs/cli/plugins/bluemix_admin/index.html#clius_emau) for more information.
* Issue CLI commands to upload buildpacks to Bluemix. See [Bluemix admin CLI](/docs/cli/plugins/bluemix_admin/index.html##buildpacks) for more information. 
* Issue CLI commands to see resource usage and availability for memory, disk, and CPU as well as history for memory and disk usage. See [Viewing resource usage information](/docs/cli/plugins/bluemix_admin/index.html##cliresourceusage) for more information.

### August updates for the administration console
{: #augustadminconsole}
New as of: 30 August 2016

With the latest updates from August, you can expect the following updates, improvements, or new features:

* Billing managers of an organization can view the account usage data without being assigned any administration console permissions. For more information see [Account usage](/docs/admin/index.html#accountusage).
* When searching for users, you can filter your search based on name, permission type, organization, and organization role. You can filter your user search both in the CLI, with the `search-users` command, and in the user interface.  For more information, see [Managing users and permissions](/docs/admin/index.html#oc_useradmin) and [Bluemix admin CLI](/docs/cli/plugins/bluemix_admin/index.html).
* All users in your environment can view the latest scheduled disruptive maintenance events for your environment on the System Status page.
* Event subscriptions for maintenance and incidents now include notifications for all updates to the event. For example, if you have an email notification set up for a maintenance event and the date changes, your specified users for the notification are alerted of the change in event information.  For more information, see [Notifications and event subscriptions](/docs/admin/index.html#oc_eventsubscription).
* You can view resource utilization information for your memory and disk space, including the physical and physical limit, as well as the reserved and reserved limit.  You can also see historical information about your memory usage, including which organizations reserved the most memory in your environment. For more information, see [Resource usage](/docs/admin/index.html#resourceusage).

## Compute
{: #compute_category}

### ASP.NET Core buildpack v1.0.1 is now available
New as of: 13 October 2016 

The v1.0.1 buildpack adds support for ASP.Net Core v1.0.1. It also contains a number of bug fixes and small improvements. See the [ASP.NET Core runtime](/docs/runtimes/dotnet/index.html#dotnet) documentation for more information.

### IBM {{site.data.keyword.Bluemix_notm}} Runtime for Swift GA
New as of: 27 September 2016

The first GA release of the Runtime for Swift is now available in our cloud. For experienced enterprise clients, you will be pleased that this is an IBM-supported runtime for {{site.data.keyword.Bluemix_notm}} public, {{site.data.keyword.Bluemix_notm}} Dedicated and {{site.data.keyword.Bluemix_notm}} Local cloud deployments. It unlocks the value of the cloud for all Swift developers. Swift v3.0 is a major advancement in the Swift language, which supports the Swift Package Manager, enhanced APIs, and full Linux support. The bundled runtime integrates the latest IBM Swift buildpack with a sample application built with the IBM Kitura v1.0 open web framework.

For more information, see the [IBM {{site.data.keyword.Bluemix_notm}} Runtime for Swift](/docs/runtimes/swift/index.html) documentation and the [General Availability: IBM {{site.data.keyword.Bluemix_notm}} Runtime for Swift](https://developer.ibm.com/bluemix/2016/09/22/bluemix-runtime-for-swift/){: new_window} announcement.

### New Liberty for Java buildpack v3.3
New as of: 16 September 2016

The new Liberty for Java v3.3 buildpack provides updated Liberty runtime versions. The latest stable release is [16.0.0.3](http://www-01.ibm.com/support/docview.wss?uid=swg24042657){: new_window}, and the latest monthly release is 2016.9.0.0. The stable release is used by default. The buildpack also provides updated IBM JRE version 8 SR3 FP11 and contains other bug fixes. For more information on these updates, see the [latest updates](/docs/runtimes/liberty/updates.html) section.

### The ASP.NET Core buildpack v1.0 is now available
New as of: 31 August 2016

The ASP.NET Core buildpack is now generally available. The v1.0 buildpack adds support for running pre- and post-compile scripts to install front-end packages using NPM and Bower. The buildpack also contains a number of bug fixes and small improvements. For more information, see the [ASP.NET Core runtime](/docs/runtimes/dotnet/index.html#dotnet) documentation.

### New Liberty for Java buildpack v3.2
New as of: 29 August 2016

The new Liberty for Java v3.2 buildpack provides updated IBM JRE versions including 8 SR3 FP10 and 7.1 SR3 FP50. The monthly Liberty runtime version was also updated to the 2016.8.0.0 release. The v3.2 buildpack contains a number of small bug fixes. For more information on these updates, see the [latest updates](/docs/runtimes/liberty/updates.html) section.

## Services
{: #services_category}

#### {{site.data.keyword.mobilepushshort}} service is now available on {{site.data.keyword.Bluemix_notm}} Local

If you have a {{site.data.keyword.Bluemix_notm}} Local deployment, you can now leverage the {{site.data.keyword.mobilepushshort}} service in your own [{{site.data.keyword.Bluemix_notm}} Local](/docs/local/index.html#local) environment.

#### Improved {{site.data.keyword.mobilepushshort}} notification service console experience 

The {{site.data.keyword.mobilepushshort}} service console is now enhanced to align with the new {{site.data.keyword.Bluemix_notm}} user experience. See the catalog entry for [{{site.data.keyword.mobilepushshort}} ](https://new-console.ng.bluemix.net/catalog/services/push-notifications/){: new_window} to provision the service.

#### {{site.data.keyword.mobilepushshort}} service is now seamlessly integrated with the Mobile dashboard experience

You can now add push service to a project generated from the mobile dashboard and directly configure it from the dashboard. The push client SDK’s is included in the project and basic initialization code is generated. With this, you can now use push service from the mobile catalog of services or add to a project directly from the [mobile dashboard](https://new-console.ng.bluemix.net/mobile/projects/) experience.
#### Engage with users through web channel

With {{site.data.keyword.mobilepushshort}} service, you can now send notifications to your web apps on Chrome and Firefox browsers. You can engage with your web users either on desktop or mobile browser using a unified set of API’s even when the website is not open on the user’s mobile or desktop browser. Enhance engagement and retention to visitors of a web site by sending unicast, broadcast, or multicast (based on tags, platform, set of devices, or set of users) notifications. For more information, see [Enabling web applications to receive {{site.data.keyword.mobilepushshort}}](/docs/services/mobilepush/c_chrome_firefox_enable.html).

#### Leverage new notification features for the Android platform

Set the following notification features either from the console or SDK:

* Collapsible Message: A message can be replaced by a new message containing the same collapse key if it yet to be delivered to the device.
* Priority: Set high priority for message that GCM should attempt to deliver immediately.Messages with normal priority won’t open network connections on a sleeping device and their delivery might be delayed to conserve battery.
* Google Sync Notifications: Sync the messages across the same user’s registered devices. If the user handles the notification on one device than it would be dismissed on other devices.
* Specify the time-to-live parameter to set maximum lifespan of a message which corresponds to the maximum period of time for which FCM stores and attempts to deliver the message.
* Support for expandable notification styles like big picture, big text and inbox style notifications.
* Ability to set the visibility of the message as public or private affecting how the notification is displayed. A private option restricts public viewing.
* Ability to package custom sound files that needs to be played on the receipt of the notification.

#### {{site.data.keyword.mobilepushshort}} service SDK now supports Swift 3.0

You can now develop your notification based iOS applications with Swift 3.0. [Access the latest client SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push){: new_window}.
### {{site.data.keyword.dashdbshort_notm}} updates
New as of: 4 October 2016

#### Updated {{site.data.keyword.dashdbshort_notm}} drivers

The latest build level of the {{site.data.keyword.dashdbshort_notm}} drivers for Windows, Linux, and Mac OS is available from the **Connect** > **Download Tools** page. The new build levels include Windows 10 support and the latest fixes. For all supported operating systems, the build level s1607080700 replaces special_34028. For installation instructions, see [dashDB driver package](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_driver_package.html){: new_window}.

#### Validate SQL syntax in the SQL editor as you type

The Run SQL page has a new look and new options. You now have the choice to run a query for selected statements or to run the query from the cursor position. You can also validate the syntax as you enter the statements. To enable the validation, click **Options**, and turn on **Real-time validation**.

#### SQL compatibility

The following list describes the updates made to SQL compatibility in {{site.data.keyword.dashdbshort_notm}}:

* For integer input, the SQL SUM function now returns a BIGINT result and the AVG function now returns a DECIMAL(31,6) result.
* When operating in NPS compatibility mode, the AS clause of a CREATE TABLE statement can use the same syntax as the corresponding clause of a Netezza CREATE TABLE AS (CTAS) command.
* {{site.data.keyword.dashdbshort_notm}} no longer enforces partitioning key overlap with non-enforced constraints.
* When operating in NPS compatibility mode, an expression can refer to column aliases that are set in the select list.

For a cumulative list of updates for {{site.data.keyword.dashdbshort_notm}}, see [What's New in {{site.data.keyword.dashdbshort_notm}}](http://www-01.ibm.com/support/docview.wss?uid=swg21961758){: new_window}.
### {{site.data.keyword.dashdblong}} updates 
New as of: 16 August 2016

#### Manage data with {{site.data.keyword.dashdbshort}} support tools
The {{site.data.keyword.dashdbshort}} support tools package, also referred to as the dbtoolkit, contains a collection of scripts and utilities based on similar scripts delivered for the IBM PureData System for Analytics appliances and Netezza databases. You can use the dbtoolkit to migrate data from Netezza databases to {{site.data.keyword.dashdbshort}}, to connect to the {{site.data.keyword.dashdbshort}} database, and to run queries and reports on the migrated data.

To learn more about the dbtoolkit and to download the package, see [Manage data with dashDB Support Tools](https://developer.ibm.com/clouddataservices/docs/dashdb/get/Manage-data-with-dashDB-Support-Tools/){: new_window}.

#### Database Conversion Workbench (DCW) is available on Mac and no longer requires a Data Studio plug-in
DCW available on Mac no longer requires a Data Studio plug-in. DCW 4.0.0 is available in the dashDB web console from **Connect &gt; Download Tools**. For more information, see [Release Notes](https://www.ibm.com/developerworks/community/wikis/home?lang=en#!/wiki/W252c18693c7e_432e_ad40_03c3417db6b1/page/Release%20Notes){: new_window}.

#### {{site.data.keyword.dashdbshort}} managed service is HIPAA ready
The {{site.data.keyword.dashdbshort}} Enterprise 256.4, 256.12 and MPP.4 plans, when provisioned on IBM SoftLayer, have implemented required controls commensurate with the Health Insurance Portability and Accountability Act of 1996 (HIPAA) Security and Privacy Rule requirements. These include appropriate administrative, physical, and technical safeguards required of Business Associates in 45 CFR Part 160 and Subparts A and C of Part 164.

For information about how to order a HIPAA-ready {{site.data.keyword.dashdbshort}} system, contact your IBM Cloud Data Services sales representative, or send email to dashDB_Info@wwpdl.vnet.ibm.com.

#### New downloads available for InfoSphere Data Architect and Data Studio
To take advantage of the latest enhancements, download the updated versions of the software from the {{site.data.keyword.dashdbshort}} web console from **Connect &gt; Download Tools**.

* IBM InfoSphere Data Architect, version 9.1.3. For information about the enhancements, see [What's new in InfoSphere Data Architect versions 9.1.2 and 9.1.3](http://www.ibm.com/support/docview.wss?uid=swg21682045){: new_window}.
* IBM Data Studio, version 4.1.2. For information about the enhancements, see [What's New and Changed in IBM Data Studio Version 4.1.x](http://www.ibm.com/support/docview.wss?uid=swg27038173){: new_window}.

#### Random method of distribution now available when creating new tables
When you create a new table in a {{site.data.keyword.dashdbshort}} MPP database, you can now choose either a hash distribution or a random distribution. If you choose a random distribution, data is distributed evenly across the system. For more information, see [Creating tables in a {{site.data.keyword.dashdbshort}} MPP database](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/learn_how/creating_tables_mpp.html){: new_window}.

For a cumulative list of updates for {{site.data.keyword.dashdbshort}}, see [What's New in {{site.data.keyword.dashdbshort}}](http://www-01.ibm.com/support/docview.wss?uid=swg21961758){: new_window}.
### New changes in {{site.data.keyword.mobilepushshort}} service
New as of: 4 August 2016

#### User ID-based notifications
Do you wish to engage with specific users by sending push notifications by their user name or identifier rather than by device identifier? This is now possible with {{site.data.keyword.mobilepushshort}} service on {{site.data.keyword.Bluemix_notm}}. User ID-based notifications are notification messages that are targeted to a specific user. Many devices can be registered with one user.

During device registration you will need to provide a user ID and client secret. Client secret is allocated when the service is provisioned and can be obtained from the console. Use the regisgterDeviceWithUserId API to register the device for push notifications. From the console, send notifications to specific user Ids. For more information see, [Enabling user-based notifications](/docs/services/mobilepush/c_user_basednotifications.html).

#### Server-side Swift SDK
Are you a Swift user using Swift on client and server-side to build your applications? There is now a Swift server-side SDK for sending push notifications by using {{site.data.keyword.Bluemix_notm}} {{site.data.keyword.mobilepushshort}} services. Check out the [Swift server-side SDK](https://github.com/ibm-bluemix-mobile-services/bms-pushnotifications-serversdk-swift){: new_window}.

#### {{site.data.keyword.mobilepushshort}} as an unbound service
You can now access the {{site.data.keyword.mobilepushshort}} service from an application that runs outside {{site.data.keyword.Bluemix_notm}} as the service now supports unbound mode. Refer to the {{site.data.keyword.Bluemix_notm}} documentation on how to [enable external apps to use {{site.data.keyword.Bluemix_notm}} service](/docs/services/reqnsi.html#accser_external).

### Updates to IBM Eclipse Tools for {{site.data.keyword.Bluemix_notm}}

Finally, a new version of IBM Eclipse Tools for {{site.data.keyword.Bluemix_notm}} is now available for download. Some of the capabilities introduced in this update include the ability to map and unmap projects to cloud applications, service creation wizard improvements, support for {{site.data.keyword.Bluemix_notm}} Dedicated, and more!


