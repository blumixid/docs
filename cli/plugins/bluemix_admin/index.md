---



copyright:

  years: 2015, 2016
lastupdated: "2016-11-21"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}

# {{site.data.keyword.Bluemix_notm}} admin CLI
{: #bluemixadmincli}



You can manage users for your
{{site.data.keyword.Bluemix_notm}} Local or {{site.data.keyword.Bluemix_notm}} Dedicated environment by
using the Cloud Foundry command line interface with the
{{site.data.keyword.Bluemix_notm}} Admin CLI plug-in. For
example, you can add users from an LDAP registry. If you are looking for information about managing your {{site.data.keyword.Bluemix_notm}} Public account, see [Administering](/docs/admin/adminpublic.html#administer).

Before you begin, install the cf command line interface. The
{{site.data.keyword.Bluemix_notm}} Admin CLI plug-in
requires cf version 6.11.2 or later. [Download Cloud Foundry command line interface](https://github.com/cloudfoundry/cli/releases){: new_window}

**Restriction:** The Cloud Foundry command line interface is not supported by
Cygwin. Use the Cloud Foundry command line interface in a command line window other than the Cygwin
command line window.

## Adding the {{site.data.keyword.Bluemix_notm}} Admin CLI plug-in

After the cf command line interface is installed, you can add the
{{site.data.keyword.Bluemix_notm}} admin CLI
plug-in.

**Note**: If you have previously installed the {{site.data.keyword.Bluemix_notm}} Admin plug-in, you might need to uninstall the plug-in, delete the repository, and then re-install to get the latest updates.

Complete the following steps to add the repository and install the plug-in:

<ol>
<li>To add the {{site.data.keyword.Bluemix_notm}} admin plug-in repository, run the following command:<br/><br/>
<code>
cf add-plugin-repo BluemixAdmin https://console.&lt;subdomain&gt;.chinabluemix.net/cli
</code><br/><br/>
<dl class="parml">
<dt class="pt dlterm">&lt;subdomain&gt;</dt>
<dd class="pd">Subdomain of the URL for your {{site.data.keyword.Bluemix_notm}} instance. For example, <code>https://console.mycompany.chinabluemix.net/cli</code></dd>
</dl>
</li>
<li>To install the {{site.data.keyword.Bluemix_notm}} Admin CLI plug-in, run the following command:<br/><br/>
<code>
cf install-plugin bluemix-admin-cli -r BluemixAdmin
</code>
</li>
</ol>

If you need to uninstall the plug-in, you can use the following commands, then you can add the updated repository and install the latest plug-in:

* Uninstall the plug-in: `cf uninstall-plugin-repo bluemix-admin-cli`
* Remove the plugin repository: `cf remove-plugin-repo BluemixAdmin`


## Using the {{site.data.keyword.Bluemix_notm}} Admin CLI plug-in

You can use the {{site.data.keyword.Bluemix_notm}} Admin CLI plug-in to add or remove users, assign or unassign users from orgs, and to perform other management tasks. Special characters, such as spaces, plus signs (+), and ampersands (&) are not supported when you create org names, space names, and application security groups. Try using mixed capitalization or underscores to create unique names.

To see a list of commands, run the following
command:

```
cf plugins
```
{: codeblock}

For additional help for a command, use the `-help` option.

### Connecting and logging in to {{site.data.keyword.Bluemix_notm}}

Before you can use the Admin CLI plug-in to manage users, you must connect and log in, if
you are not already.

<ol>
<li>To connect to the {{site.data.keyword.Bluemix_notm}} API endpoint, run the following command:<br/><br/>
<code>
cf ba api https://console.&lt;subdomain&gt;.chinabluemix.net
</code>
<dl class="parml">
<dt class="pt dlterm">&lt;subdomain&gt;</dt>
<dd class="pd">Subdomain of the URL for your {{site.data.keyword.Bluemix_notm}} instance.<br />
</dd>
</dl>
<p>You can check the Admin Console Resources and Information page for the
correct URL. The URL is shown in the API Information section in the **API URL**
field.</p>
</li>
<li>Log in to {{site.data.keyword.Bluemix_notm}} with the following command:<br/><br/>
<code>
cf login
</code>
</li>
</ol>

### Adding a user

You can add a user to your
{{site.data.keyword.Bluemix_notm}} environment from the
user registry for your environment. Enter the following command:

```
cf ba add-user <user_name> <organization>
```
{: codeblock}

**Note**: To add a user to a specific organization, you must be the manager of the organization, or you must have **Admin** (available alternative is **Superuser**) or **User** permission with **Write** access.

<dl class="parml">
<dt class="pt dlterm">&lt;user_name&gt;</dt>
<dd class="pd">The name of the user in the LDAP registry.</dd>
<dt class="pt dlterm">&lt;organization&gt;</dt>
<dd class="pd">The name or GUID of the {{site.data.keyword.Bluemix_notm}} org to add the user to.</dd>
</dl>

**Tip:** You can also use **ba au** as an alias for the longer
**ba add-user** command name.

<!-- staging-only commands start. Live for interconnect -->

### Search for a user

You can search for a user. Enter the following command in conjunction with the optional search filter parameters as needed (name, permission, organization, and role):

```
cf ba search-users -name=<user_name_value> -permission=<permission_value> -organization=<organization_value> -role=<role_value>
```
{: codeblock}

<dl class="parml">

<dt class="pt dlterm">&lt;user_name_value&gt;</dt>
<dd class="pd">The name of the user in {{site.data.keyword.Bluemix_notm}}. </dd>
<dt class="pt dlterm">&lt;permission_value&gt;</dt>
<dd class="pd">The permission assigned to the user. For example, superuser, basic, catalog, user, and reports. For more information about assigned user permissions, see [Permissions](/docs/admin/index.html#permissions). You cannot use this parameter with the organization parameter in the same query. </dd>
<dt class="pt dlterm">&lt;organization_value&gt;</dt>
<dd class="pd">The organization name that the user belongs to. You cannot use this parameter with the organization parameter in the same query.</dd>
<dt class="pt dlterm">&lt;role_value&gt;</dt>
<dd class="pd">The organization role assigned to the user. For example, manager, billing manager, or auditor for the organization. You must specify the organization with this parameter. For more information about roles, see [User roles](/docs/admin/users_roles.html#userrolesinfo).</dd>

</dl>

**Tip:** You can also use **ba su** as an alias for the longer
**ba search-users** command name.

### Set permissions for a user

You can set permissions for a specified user. Enter the following command:

```
cf ba set-permissions <user_name> <permission> <access>
```
{: codeblock}

**Note**: You can set one permission at a time.

<dl class="parml">
<dt class="pt dlterm">&lt;user_name&gt;</dt>
<dd class="pd">The name of the user in {{site.data.keyword.Bluemix_notm}}.</dd>
<dt class="pt dlterm">&lt;permission&gt;</dt>
<dd class="pd">Set the permissions for the user: Admin (available alternative is Superuser), Login (available alternative is Basic), Catalog (read or write access), Reports (read or write access), or Users (read or write access).</dd>
<dt class="pt dlterm">&lt;access&gt;</dt>
<dd class="pd">For Catalog, Reports, or Users permissions, you must also set the level of access as <code>read</code> or <code>write</code>.</dd>
</dl>

**Tip:** You can also use **ba sp** as an alias for the longer
**ba set-permissions** command name.

<!-- staging-only commands end -->

### Removing a user

You can remove a user from your
{{site.data.keyword.Bluemix_notm}} environment by
entering the following command:

```
cf ba remove-user <user_name>
```
{: codeblock}

<dl class="parml">

<dt class="pt dlterm">&lt;user_name&gt;</dt>
<dd class="pd">The name of the user in {{site.data.keyword.Bluemix_notm}}.</dd>

</dl>

**Tip:** You can also use **ba ru** as an alias for the longer
**ba remove-user** command name.

### Adding and deleting an organization

You can add and delete an organization.

* To add an organization, enter the following command:

```
cf ba create-organization <organization> <manager>
```
{: codeblock}

<dl class="parml">
<dt class="pt dlterm">&lt;organization&gt;</dt>
<dd class="pd">The name or GUID of the {{site.data.keyword.Bluemix_notm}} org to add.</dd>
<dt class="pt dlterm">&lt;manager&gt;</dt>
<dd class="pd">The user name of the manager for the org.</dd>
</dl>

**Tip:** You can also use **ba co** as an alias for the longer
**ba create-organization** command name.

* To delete an organization, enter the following command:

```
cf ba delete-organization <organization>
```
{: codeblock}

<dl class="parml">
<dt class="pt dlterm">&lt;organization&gt;</dt>
<dd class="pd">The name or GUID of the {{site.data.keyword.Bluemix_notm}} org to delete.</dd>
</dl>

**Tip:** You can also use **ba do** as an alias for the longer
**ba delete-organization** command name.

### Assigning a user to an organization

You can assign a user in your
{{site.data.keyword.Bluemix_notm}} environment to a
particular organization. Enter the following command:

```
cf ba set-org <user_name> <organization> [<role>]
```
{: codeblock}

<dl class="parml">
<dt class="pt dlterm">&lt;user_name&gt;</dt>
<dd class="pd">The name of the user in {{site.data.keyword.Bluemix_notm}}.</dd>
<dt class="pt dlterm">&lt;organization&gt;</dt>
<dd class="pd">The name or GUID of the {{site.data.keyword.Bluemix_notm}} org to assign the user to.</dd>
<dt class="pt dlterm">&lt;role&gt;</dt>
<dd class="pd">See [Roles](/docs/admin/users_roles.html) for
{{site.data.keyword.Bluemix_notm}} user roles and
descriptions.</dd>
</dl>

**Tip:** You can also use **ba so** as an alias for the longer
**ba set-org** command name.

### Unassigning a user from an organization

You can unassign a user in your
{{site.data.keyword.Bluemix_notm}} environment from a
particular organization. Enter the following command:

```
cf ba unset-org <user_name> <organization> [<role>]
```
{: codeblock}

<dl class="parml">
<dt class="pt dlterm">&lt;user_name&gt;</dt>
<dd class="pd">The name of the user in {{site.data.keyword.Bluemix_notm}}.</dd>
<dt class="pt dlterm">&lt;organization&gt;</dt>
<dd class="pd">The name or GUID of the {{site.data.keyword.Bluemix_notm}} org to assign the user to.</dd>
<dt class="pt dlterm">&lt;role&gt;</dt>
<dd class="pd">See [Roles](/docs/admin/users_roles.html) for
{{site.data.keyword.Bluemix_notm}} user roles and
descriptions.</dd>
</dl>

**Tip:** You can also use **ba uo** as an alias for the longer
**ba unset-org** command name.

### Roles

<dl class="parml">
<dt class="pt dlterm">OrgManager</dt>
<dd class="pd">Organization manager. An org manager has authority to do the following actions:
<ul>
<li>Create or delete spaces within the organization.</li>
<li>Invite users to the organization and manage users.</li>
<li>Manage domains of the organization.</li>
</ul>
</dd>
<dt class="pt dlterm">BillingManager</dt>
<dd class="pd">Billing manager. A billing manager can view runtime and service usage information for the
organization.</dd>
<dt class="pt dlterm">OrgAuditor</dt>
<dd class="pd">Organization auditor. An organization auditor can view application and service content in the
space.</dd>
</dl>

### Setting a quota for an organization

You can set the usage quota for a particular organization.

```
cf ba set-quota <organization> <plan>
```
{: codeblock}

<dl class="parml">
<dt class="pt dlterm">&lt;organization&gt;</dt>
<dd class="pd">The name or GUID of the {{site.data.keyword.Bluemix_notm}} org to set the quota for.</dd>
<dt class="pt dlterm">&lt;plan&gt;</dt>
<dd class="pd">The quota plan for an organization.</dd>
</dl>

**Tip:** You can also use **ba sq** as an alias for the longer
**ba set-quota** command name.

### Adding, deleting, and retrieving reports

You can add, delete, and retrieve security reports.
* To add a report, enter the following command:

```
cf ba add-report <category> <date> <PDF|TXT|LOG> <RTF>
```
{: codeblock}

**Note**: If you have write access for the reports permission, you can create a new category and add a report in any of the accepted formats for your users. Enter the new category name for the `category` parameter, or add your new report to an existing category.

<dl class="parml">
<dt class="pt dlterm">&lt;category&gt;</dt>
<dd class="pd">The category for the report. If there is a space in the name, use quotation marks around the
name.</dd>
<dt class="pt dlterm">&lt;date&gt;</dt>
<dd class="pd">The report date in the format <samp class="ph codeph">YYYYMMDD</samp>.</dd>
<dt class="pt dlterm">&lt;PDF|TXT|LOG&gt;</dt>
<dd class="pd">The path for the report PDF, text file, or log file to upload.</dd>
<dt class="pt dlterm">&lt;RTF&gt;</dt>
<dd class="pd">An option to include a Rich Text Format (RTF) version of the PDF. This option applies only if
you included a path to the report PDF. The RTF version is used for indexing and searching.</dd>
</dl>

**Tip:** You can also use **ba ar** as an alias for the longer
**ba add-report** command name.

* To delete a report, enter the following command:

```
cf ba delete-report <category> <date> <name>
```
{: codeblock}

<dl class="parml">
<dt class="pt dlterm">&lt;category&gt;</dt>
<dd class="pd">The category for the report. If there is a space in the name, use quotation marks around the
name.</dd>
<dt class="pt dlterm">&lt;date&gt;</dt>
<dd class="pd">The report date in the format <samp class="ph codeph">YYYYMMDD</samp>.</dd>
<dt class="pt dlterm">&lt;name&gt;</dt>
<dd class="pd">The name of the report.</dd>
</dl>

**Tip:** You can also use **ba dr** as an alias for the longer
**ba delete-report** command name.

* To retrieve a report, enter the following command:

```
cf ba retrieve-report <category> <date> <name>
```
{: codeblock}

<dl class="parml">
<dt class="pt dlterm">&lt;category&gt;</dt>
<dd class="pd">The category for the report. If there is a space in the name, use quotation marks around the
name.</dd>
<dt class="pt dlterm">&lt;date&gt;</dt>
<dd class="pd">The report date in the format <samp class="ph codeph">YYYYMMDD</samp>.</dd>
<dt class="pt dlterm">&lt;name&gt;</dt>
<dd class="pd">The name of the report.</dd>
</dl>

**Tip:** You can also use **ba rr** as an alias for the longer **ba retrieve-report** command name.

### Enabling and disabling services for all organizations

You can enable or disable a service from being displayed in the
{{site.data.keyword.Bluemix_notm}} Catalog for all organizations.

* To enable a service to be visible in the
{{site.data.keyword.Bluemix_notm}} Catalog for all
organizations, enter the following command:

```
cf ba enable-service-plan <plan_identifier>
```
{: codeblock}

<dl class="parml">
<dt class="pt dlterm">&lt;plan_identifier&gt;</dt>
<dd class="pd">The name or GUID of the service plan that you want to enable. If you enter a non-unique service plan name, for example "Standard" or "Basic," you are prompted with service plans that  to choose from. To identify a service plan name,  select the service category from the homepage, then select **Add** to view the services for that category. Click the service name to open the details view, then you can view the names of the service plans that are available for that service. </dd>
</dl>

**Tip:** You can also use **ba esp** as an alias for the longer
**ba enable-service-plan** command name.

* To disable a service from being visible in the
{{site.data.keyword.Bluemix_notm}} Catalog for all
organizations, enter the following command:

```
cf ba disable-service-plan <plan_identifier>
```
{: codeblock}

<dl class="parml">
<dt class="pt dlterm">&lt;plan_identifier&gt;</dt>
<dd class="pd">The name or GUID of the service plan that you want to enable. If you enter a non-unique service plan name, for example "Standard" or "Basic," you are prompted with service plans that  to choose from. To identify a service plan name, select the service category from the homepage, then select **Add** to view the services for that category. Click the service name to open the details view, then you can view the names of the service plans that are available for that service.</dd>
</dl>

**Tip:** You can also use **ba dsp** as an alias for the longer
**ba disable-service-plan** command name.

### Adding, removing, and editing service visibility for organizations

You can add or remove an organization from the list of organizations that can see a
specific service in the {{site.data.keyword.Bluemix_notm}} Catalog. You can also edit and replace the list of services that specific
organizations can see in the {{site.data.keyword.Bluemix_notm}} Catalog.

* To allow an organization to view a specific service in the
{{site.data.keyword.Bluemix_notm}} Catalog, enter the
following command:

```
cf ba add-service-plan-visibility <plan_identifier> <organization>
```
{: codeblock}

<dl class="parml">
<dt class="pt dlterm">&lt;plan_identifier&gt;</dt>
<dd class="pd">The name or GUID of the service plan that you want to enable. If you enter a non-unique service plan name, for example "Standard" or "Basic," you are prompted with service plans that  to choose from. To identify a service plan name, select the service category from the homepage, then select **Add** to view the services for that category. Click the service name to open the details view, then you can view the names of the service plans that are available for that service.</dd>
<dt class="pt dlterm">&lt;organization&gt;</dt>
<dd class="pd">The name or GUID of the {{site.data.keyword.Bluemix_notm}} org to add to the service's visibility list.</dd>
</dl>

**Tip:** You can also use **ba aspv** as an alias for the longer
**ba add-service-plan-visibility** command name.

* To remove the visibility of a service in the
{{site.data.keyword.Bluemix_notm}} Catalog for an
organization, enter the following command:

```
cf ba remove-service-plan-visibility <plan_identifier> <organization>
```
{: codeblock}

<dl class="parml">
<dt class="pt dlterm">&lt;plan_identifier&gt;</dt>
<dd class="pd">TThe name or GUID of the service plan that you want to enable. If you enter a non-unique service plan name, for example "Standard" or "Basic," you are prompted with service plans that  to choose from. To identify a service plan name, select the service category from the homepage, then select **Add** to view the services for that category. Click the service name to open the details view, then you can view the names of the service plans that are available for that service.</dd>
<dt class="pt dlterm">&lt;organization&gt;</dt>
<dd class="pd">The name or GUID of the {{site.data.keyword.Bluemix_notm}} org to remove from the service's visibility list.</dd>
</dl>

**Tip:** You can also use **ba rspv** as an alias for the longer
**ba remove-service-plan-visibility** command name.

* To replace all existing visible services for an organization or multiple organizations, use the
following command:

```
cf ba edit-service-plan-visibilities <plan_identifier> <organization_1> <optional_organization_2>
```
{: codeblock}

**Note:** This
command replaces existing visible services for the specified organizations with the service that you
specify in the command.

<dl class="parml">
<dt class="pt dlterm">&lt;plan_identifier&gt;</dt>
<dd class="pd">The name or GUID of the service plan that you want to enable. If you enter a non-unique service plan name, for example "Standard" or "Basic," you are prompted with service plans that  to choose from. To identify a service plan name, select the service category from the homepage, then select **Add** to view the services for that category. Click the service name to open the details view, then you can view the names of the service plans that are available for that service.</dd>
<dt class="pt dlterm">&lt;organization&gt;</dt>
<dd class="pd">The name or GUID of the {{site.data.keyword.Bluemix_notm}} org to add visibility for. You can enable visibility of the service for more than
one organization by entering additional organization names or GUIDs in the command.</dd>
</dl>

**Tip:** You can also use **ba espv** as an alias for the longer
**ba edit-service-plan-visibility** command name.

### Working with service brokers

Use the following commands to list all service brokers, add or delete a service broker, or to update a service broker.

* You can list a service brokers by
entering the following command:

```
cf ba service-brokers <broker_name>
```
{: codeblock}

**Note**: To list all service brokers, enter the command without the `broker_name` parameter.

<dl class="parml">
<dt class="pt dlterm">&lt;broker_name&gt;</dt>
<dd class="pd">Optional: The name of the custom service broker. Use this parameter, if you want to get information for a specific service broker.</dd>
</dl>

**Tip:** You can also use **ba sb** as an alias for the longer
**ba service-brokers** command name.

* You can add a service broker, so that you can add a custom service to your  
{{site.data.keyword.Bluemix_notm}} Catalog by
entering the following command:

```
cf ba add-service-broker <broker_name> <user_name> <password> <broker_url>
```
{: codeblock}

<dl class="parml">
<dt class="pt dlterm">&lt;broker_name&gt;</dt>
<dd class="pd">The name of the custom service broker.</dd>
<dt class="pt dlterm">&lt;user_name&gt;</dt>
<dd class="pd">The user name for the account that has access to the service broker.</dd>
<dt class="pt dlterm">&lt;password&gt;</dt>
<dd class="pd">The password for the account that has access to the service broker.</dd>
<dt class="pt dlterm">&lt;broker_url&gt;</dt>
<dd class="pd">The URL for the service broker.</dd>
</dl>

**Tip:** You can also use **ba asb** as an alias for the longer
**ba add-service-broker** command name.

* You can delete a service broker, to remove the custom service from your   
{{site.data.keyword.Bluemix_notm}} Catalog by
entering the following command:

```
cf ba delete-service-broker <service_broker>
```
{: codeblock}

<dl class="parml">
<dt class="pt dlterm">&lt;service_broker&gt;</dt>
<dd class="pd">The name or guid of the custom service broker.</dd>
</dl>

**Tip:** You can also use **ba dsb** as an alias for the longer
**ba delete-service-broker** command name.

* You can update a service broker by
entering the following command:

`cf ba update-service-broker <broker_name> <user_name> <password> <broker_url>`
{: codeblock}

<dl class="parml">
<dt class="pt dlterm">&lt;broker_name&gt;</dt>
<dd class="pd">The name of the custom service broker.</dd>
<dt class="pt dlterm">&lt;user_name&gt;</dt>
<dd class="pd">The user name for the account that has access to the service broker.</dd>
<dt class="pt dlterm">&lt;password&gt;</dt>
<dd class="pd">The password for the account that has access to the service broker.</dd>
<dt class="pt dlterm">&lt;broker_url&gt;</dt>
<dd class="pd">The URL for the service broker.</dd>
</dl>

**Tip:** You can also use **ba usb** as an alias for the longer
**ba update-service-broker** command name.


### Working with application security groups

To work with application security groups (ASGs), you must be a full access administrator for the local or dedicated environment. All users of the environment can list the available ASGs for the organization that is being targeted with the command. However, to create, update, or bind ASGs, you must be an administrator for the {{site.data.keyword.Bluemix_notm}} environment.

ASGs function as virtual firewalls that control outbound traffic from the applications in your {{site.data.keyword.Bluemix_notm}} environment. Each ASG consists of a list of rules that allow specific traffic and communication to and from the outside network. You can bind one or more ASGs to a specific security group set, for example a group set that is used for applying global access, or you can bind to spaces within an organization in your {{site.data.keyword.Bluemix_notm}} environment.

{{site.data.keyword.Bluemix_notm}} is initially set up with all access to the outside network restricted. Two IBM-created  security groups, `public_networks` and `dns`, enable global access to the outside network when you bind these groups to default Cloud Foundry security group sets. The two security group sets in Cloud Foundry that are used to apply global access are the **Default Staging** and **Default Running** group sets. These group sets apply the rules for allowing traffic to all running apps or all staging apps. If you do not want to bind to these two security group sets, you can unbind from the Cloud Foundry group sets, and then bind the security group to a specific space. For more information, see [Binding Application Security Groups](https://docs.cloudfoundry.org/adminguide/app-sec-groups.html#binding-groups){: new_window}.

**Note**: The following commands that enable you to work with security groups are based on the Cloud Foundry 1.6 version.

#### Listing, creating, updating, and deleting security groups

For more information about creating security groups and the rules that define outgoing traffic, see [Creating Application Security Groups](https://docs.cloudfoundry.org/adminguide/app-sec-groups.html#creating-groups){: new_window}.

* You can list all security groups by
entering the following command:

```
cf ba security-groups
```
{: codeblock}

**Tip:** You can also use **ba sgs** as an alias for the longer
**ba security-groups** command name.

* You can display a specific security-group details by
entering the following command:

```
cf ba security-groups <security-group>
```
{: codeblock}

<dl class="parml">
<dt class="pt dlterm">&lt;Security group&gt;</dt>
<dd class="pd">Name of the security group</dd>
</dl>

**Tip:** You can also use **ba sg** as an alias for the longer
**ba security-groups** command name with the `security-group` parameter.


* You can create a security group by
entering the following command. Each security group that you create has the prefix `adminconsole_` added to the name to distinguish it from the IBM-created security groups.

```
cf ba create-security-group <security-group> <path-to-rules-file>
```
{: codeblock}

<dl class="parml">
<dt class="pt dlterm">&lt;Security group&gt;</dt>
<dd class="pd">Name of your security group</dd>
<dt class="pt dlterm">&lt;Path to rules file&gt;</dt>
<dd class="pd">Absolute or relative path to a rules file</dd>
</dl>

**Tip:** You can also use **ba csg** as an alias for the longer
**ba create-security-group** command name.

* You can update a security group by
entering the following command:

```
cf ba update-security-group <security-group> <path-to-rules-file>
```
{: codeblock}

<dl class="parml">
<dt class="pt dlterm">&lt;Security group&gt;</dt>
<dd class="pd">Name of your security group</dd>
<dt class="pt dlterm">&lt;Path to rules file&gt;</dt>
<dd class="pd">Absolute or relative path to a rules file</dd>
</dl>

**Tip:** You can also use **ba usg** as an alias for the longer
**ba update-security-group** command name.

* You can delete a security group by
entering the following command:

```
cf ba delete-security-group <security-group>
```
{: codeblock}

<dl class="parml">
<dt class="pt dlterm">&lt;Security group&gt;</dt>
<dd class="pd">Name of your security group</dd>
</dl>

**Tip:** You can also use **ba dsg** as an alias for the longer
**ba delete-security-group** command name.


#### Binding, unbinding, and listing bound security groups

For more information about binding and unbinding security groups, see [Binding Application Security Groups](https://docs.cloudfoundry.org/adminguide/app-sec-groups.html#binding-groups){: new_window} and [Unbinding Application Security Groups](https://docs.cloudfoundry.org/adminguide/app-sec-groups.html#unbinding-groups){: new_window}.

* You can bind to thetheDefault Staging security group set by
entering the following command:

```
cf ba bind-staging-security-group <security-group>
```
{: codeblock}

<dl class="parml">
<dt class="pt dlterm">&lt;Security group&gt;</dt>
<dd class="pd">Name of your security group</dd>
</dl>

**Tip:** You can also use **ba bssg** as an alias for the longer
**ba bind-staging-security-group** command name.

* You can bind to the Default Running security group set by
entering the following command:

```
cf ba bind-running-security-group <security-group>
```
{: codeblock}

<dl class="parml">
<dt class="pt dlterm">&lt;Security group&gt;</dt>
<dd class="pd">Name of your security group</dd>
</dl>

**Tip:** You can also use **ba brsg** as an alias for the longer
**ba bind-running-security-group** command name.

* You can unbind to a Default Staging security group set by
entering the following command:

```
cf ba cf ba unbind-staging-security-group <security-group>
```
{: codeblock}

<dl class="parml">
<dt class="pt dlterm">&lt;Security group&gt;</dt>
<dd class="pd">Name of your security group</dd>
</dl>

**Tip:** You can also use **ba ussg** as an alias for the longer
**ba unbind-staging-security-group** command name.

* You can unbind to a Default Running security group set by
entering the following command:

```
cf ba unbind-running-security-group <security-group>
```
{: codeblock}

<dl class="parml">
<dt class="pt dlterm">&lt;Security group&gt;</dt>
<dd class="pd">Name of your security group</dd>
</dl>

**Tip:** You can also use **ba brsg** as an alias for the longer
**ba bind-running-security-group** command name.

* You can bind a security group to a space by
entering the following command:

```
cf ba bind-security-group <security-group> <org> <space>
```
{: codeblock}

<dl class="parml">
<dt class="pt dlterm">&lt;Security group&gt;</dt>
<dd class="pd">Name of your security group</dd>
<dt class="pt dlterm">&lt;Org&gt;</dt>
<dd class="pd">Name of the organization to bind the security group to</dd>
<dt class="pt dlterm">&lt;Space&gt;</dt>
<dd class="pd">Name of the space within the organization to bind the security group to</dd>
</dl>

**Tip:** You can also use **ba bsg** as an alias for the longer
**ba bind-security-group** command name.

* You can unbind a security group to a space by
entering the following command:

```
cf ba unbind-security-group <security-group> <org> <space>
```
{: codeblock}

<dl class="parml">
<dt class="pt dlterm">&lt;Security group&gt;</dt>
<dd class="pd">Name of your security group</dd>
<dt class="pt dlterm">&lt;Org&gt;</dt>
<dd class="pd">Name of the organization to bind the security group to</dd>
<dt class="pt dlterm">&lt;Space&gt;</dt>
<dd class="pd">Name of the space within the organization to bind the security group to</dd>
</dl>

**Tip:** You can also use **ba usg** as an alias for the longer
**ba unbind-staging-security-group** command name.

