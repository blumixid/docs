---

 

copyright:

  years: 2014, 2016

 

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}

# {{site.data.keyword.Bluemix_notm}} security
{: #security}
Last updated: 8 September 2016
{: .last-updated}

Designed with secure engineering practices, the {{site.data.keyword.Bluemix_notm}} platform has layered security controls across network and infrastructure. {{site.data.keyword.Bluemix_notm}} provides a group of security services that can be used by application developers to secure their mobile and web apps. These elements combine to make {{site.data.keyword.Bluemix_notm}} a platform with clear choices for secure application development.
{:shortdesc}

{{site.data.keyword.Bluemix_notm}} ensures security readiness by adhering to security policies that are driven by best practices in IBM for systems, networking, and secure engineering. These policies include practices such as source code scanning, dynamic scanning, threat modeling, and penetration testing. 

For {{site.data.keyword.Bluemix_notm}} Local, you own the physical security and provide the infrastructure by hosting {{site.data.keyword.Bluemix_notm}} Local in your own data center behind a company firewall. In addition, {{site.data.keyword.Bluemix_notm}} adds security capabilities at the Platform as a Service layer in different categories: platform, data, and application.

## Security of the {{site.data.keyword.Bluemix_notm}} platform
{: #platform-security}

{{site.data.keyword.Bluemix_notm}} provides functional, infrastructure, operational, and physical security for the core platform. However, {{site.data.keyword.Bluemix_notm}} Local is unique in that the customer provides the infrastructure and data center, and owns the physical security.

The {{site.data.keyword.Bluemix_notm}} environment is compliant with the most restrictive IBM information technology (IT) security standards, which meet or exceed the industry standards. These standards include the following:
Network, data encryption, and access control
 * Application ACLs, permissions, and penetration testing
 * Identification, authentication, and authorization
 * Information and data protection
 * Service integrity and availability
 * Vulnerability and fix management
 * Denial of service and systematic attacks detection
 * Security incident response

![Bluemix platform security overview](images/platform_sec.svg)

*Figure 1. {{site.data.keyword.Bluemix_notm}} platform security overview*

With {{site.data.keyword.Bluemix_notm}} Local, you host {{site.data.keyword.Bluemix_notm}} behind your company firewall and in your data center. Therefore, you are responsible for certain aspects of security. The following image details which parts of security are customer-owned and which parts of security are managed and maintained by IBM.

![Bluemix Local platform security overview](images/security_local_platform.svg)

*Figure 2. {{site.data.keyword.Bluemix_notm}} Local platform security overview*

IBM installs, remotely monitors, and manages {{site.data.keyword.Bluemix_notm}} Local in your data center through Relay, a delivery capability included with {{site.data.keyword.Bluemix_notm}} Local. Relay connects securely with certificates specific to each {{site.data.keyword.Bluemix_notm}} Local instance. For more information about {{site.data.keyword.Bluemix_notm}} Local and Relay, see [Bluemix Local](../local/index.html).

### Functional security

{{site.data.keyword.Bluemix_notm}} provides various functional security capabilities, including user authentication, access authorization, auditing of critical operations, and data protection.

<dl>
<dt>Authentication</dt>
<dd>Application developers are authenticated to {{site.data.keyword.Bluemix_notm}} by using the identity name.

For {{site.data.keyword.Bluemix_notm}} Dedicated and Local, authentication through LDAP is supported by default. On request, authentication through IBM web identity can be set up instead for {{site.data.keyword.Bluemix_notm}}.
</dd>

<dt>Authorization</dt>
<dd>{{site.data.keyword.Bluemix_notm}} uses Cloud Foundry mechanisms to ensure that each application developer has access only to the applications and service instances that they created. Authorization to {{site.data.keyword.Bluemix_notm}} services is based on OAuth. Access to all {{site.data.keyword.Bluemix_notm}} Platform internal endpoints are restricted to external users.</dd>

<dt>Auditing</dt>
<dd>Audit logs are created for all successful and unsuccessful authentication attempts of application developers. Audit logs are created also for privileged access to Linux systems that host the containers where {{site.data.keyword.Bluemix_notm}} applications run.</dd>

<dt>Data protection</dt>
<dd> All {{site.data.keyword.Bluemix_notm}} traffic goes through the IBM WebSphere® DataPower® SOA Appliances, which provide reverse proxy, SSL termination, and load balancing functions.
The following HTTP methods are allowed:
<ul>
<li>DELETE</li>
<li>GET</li>
<li>HEAD</li>
<li>OPTIONS</li>
<li>POST</li>
<li>PUT</li>
<li>TRACE</li>
</ul>
 HTTP inactivity times out at 2 minutes.</dd>
<dd>The following headers are populated by DataPower:
<dl>
<dt>$wsis</dt>
<dd>Set to true if client-side connection is secure (HTTPS), set to false otherwise.</dd>
<dt>$wssc</dt>
<dd>Set to one of the following schemes of client connection: https, http, ws, or wss.</dd>
<dt>$wssn</dt>
<dd>Set to host name that is sent by client.</dd>
<dt>$wssp</dt>
<dd>Set to server port that client connects to.</dd>
<dt>x-client-ip</dt>
<dd>Set to client IP address.</dd>
<dt>x-forwarded-proto</dt>
<dd>Set to one of the following schemes of client connection: https, http, ws, or wss.</dd>
</dl>
</dd>

<dt>Secure development practices</dt>
<dd> For {{site.data.keyword.Bluemix_notm}} Public and Dedicated, periodic security vulnerability scans are performed on various {{site.data.keyword.Bluemix_notm}} components. Threat modeling and penetration testing are performed to detect and address any potential vulnerabilities for all types of {{site.data.keyword.Bluemix_notm}} deployments.</dd>
</dl>

### Infrastructure security

{{site.data.keyword.Bluemix_notm}} builds upon Cloud Foundry to provide a robust foundation for running your applications. Within the architecture, several components are provided for security and isolation. In addition, change management and backup and recovery procedures are implemented to ensure integrity and availability.

<dl>
<dt>Environment segregation</dt>
<dd> For {{site.data.keyword.Bluemix_notm}} Public, development and production environments are segregated from each other to improve application stability and security.</dd>

<dt>Firewalls</dt>
<dd> Firewalls are in place to restrict access to the {{site.data.keyword.Bluemix_notm}} network. For {{site.data.keyword.Bluemix_notm}} Local, your company firewall segregates the rest of your network from your {{site.data.keyword.Bluemix_notm}} instance.</dd>

<dt>Intrusion protection</dt>
<dd>{{site.data.keyword.Bluemix_notm}} Public and Dedicated enable intrusion protection to discover threats so that they can be addressed. Intrusion protection policies are enabled on firewalls.</dd>

<dt>Secure application container management</dt>
<dd>Each {{site.data.keyword.Bluemix_notm}} application is isolated and runs in its own container that has specific resource limits for processor, memory, and disk.</dd>

<dt>Operating system security hardening</dt>
<dd>{{site.data.keyword.Bluemix_notm}} administrators perform network and operating system hardening regularly by using tools such as IBM Endpoint Manager.</dd>
</dl>

### Operational security

{{site.data.keyword.Bluemix_notm}} provides a robust operational security environment with the following controls.

<dl>
<dt>Vulnerability scan</dt>
<dd>{{site.data.keyword.Bluemix_notm}} uses the Tenable Network Security vulnerability scanning tool, Nessus, to detect any issues with network and host configurations so that the issues can be resolved.</dd>

<dt>Automated fix management</dt>
<dd>{{site.data.keyword.Bluemix_notm}} administrators ensure that fixes for operating systems are applied at appropriate frequencies. Automated fixes are enabled by using IBM Endpoint Manager.</dd>

<dt>Audit log consolidation and analysis</dt>
<dd>{{site.data.keyword.Bluemix_notm}} uses the IBMSecurity QRadar® tools to consolidate Linux logs to monitor privileged access on Linux systems. {{site.data.keyword.Bluemix_notm}} also uses IBM QRadar security information and event management (SIEM) to monitor successful and unsuccessful login attempts of application developers.</dd>

<dt>User access management</dt>
<dd>Within {{site.data.keyword.Bluemix_notm}}, Separation of Duties guidelines are followed to assign granular access privileges to users, and to ensure that users have only the access that is required to perform their jobs according to the principle of least privilege.

Within {{site.data.keyword.Bluemix_notm}} Dedicated and Local environments, assigned administrators can manage roles and permissions for {{site.data.keyword.Bluemix_notm}} users in their organization by using the Admin Console. See [Managing {{site.data.keyword.Bluemix_notm}}](../admin/adminpublic.html#mng) for details.
</dd>
</dl>


## Data security
{: #data-security}

With {{site.data.keyword.Bluemix_notm}}, securing your data against unauthorized access is a joint effort between {{site.data.keyword.Bluemix_notm}} and you.

Data that is associated with a running application can be in one of three states: data-in-transit, data-at-rest, and data-in-use.

<dl>
<dt>Data-in-transit</dt>
<dd>Data that is being transferred between nodes on a network.</dd>

<dt>Data-at-rest</dt>
<dd>Data that is stored.</dd>

<dt>Data-in-use</dt>
<dd>Data that is not currently stored, and is being acted upon at an endpoint.</dd>
</dl>

Each type of data needs to be considered when you plan for data security.

The {{site.data.keyword.Bluemix_notm}} platform secures data-in-transit by securing the end-user access to the application by using SSL, through the network until the data reaches IBM DataPower Gateway at the boundary of the {{site.data.keyword.Bluemix_notm}} internal network. IBM DataPower Gateway acts as a reverse proxy and provides SSL termination. From there to the application IPSEC is used to secure the data as it travels from the IBM DataPower Gateway to the application.

Security for both data-in-use and data-at-rest is your responsibility as you develop your application. You can take advantage of several data-related services available in the {{site.data.keyword.Bluemix_notm}} Catalog to help with these concerns.

## Security of {{site.data.keyword.Bluemix_notm}} applications
{: #application-security}

As an application developer, you must enable the security configurations, including application data protection, for your applications that run on {{site.data.keyword.Bluemix_notm}}.

You can use security capabilities that are provided by several {{site.data.keyword.Bluemix_notm}} services to secure your applications. All {{site.data.keyword.Bluemix_notm}} services that are produced by IBM follow IBM secure engineering development practices.

**Note:** Some of the services described here might not apply to {{site.data.keyword.Bluemix_notm}} Dedicated or Local instances.

### SSO service

IBM Single Sign On for {{site.data.keyword.Bluemix_notm}} is a policy-based authentication service that provides an easy to embed single sign-on capability for Node.js or Liberty for Java™ applications. To enable an application developer to embed single sign-on capability into an application, the administrator creates service instances and adds identity sources.

The Single Sign On service supports several identity sources where your users' credentials are stored:

<dl>
<dt>SAML Enterprise</dt>
<dd>A user registry with an exchange of SAML tokens that completes the authentication.</dd>

<dt>Cloud Directory</dt>
<dd>A user registry that is hosted in IBM Cloud.</dd>
</dl>

For more information, see [Getting started with Single Sign On](../services/SingleSignOn/index.html).

## {{site.data.keyword.Bluemix_notm}} security deployment
{: #security-deployment}

{{site.data.keyword.Bluemix_notm}} security deployment architecture includes different information flows for app users and developers to ensure secure access.

![Bluemix security deployment architecture](images/sec_deployment.svg)

*Figure 3. Bluemix security deployment architecture*

For {{site.data.keyword.Bluemix_notm}} *app users*, the **app user flow** is as follows:
 1. Through a firewall, with intrusion prevention and network security in place.
 2. Through the IBM DataPower Gateway with reverse proxy and SSL termination proxy.
 3. Through the network router.
 4. Reaches the application runtime in the droplet execution agent (DEA).

The {{site.data.keyword.Bluemix_notm}} *developer* follows two main flows: for login and for development and deployment.
 * The **developer login flow** includes the following:
    * For developers who are logging in to {{site.data.keyword.Bluemix_notm}} Public, the flow is through the IBM Single Sign On service.
    * For developers who are logging in to {{site.data.keyword.Bluemix_notm}} Dedicated or Local, the flow is through the enterprise LDAP.
 * The **development and deployment flow** is as follows:
    1. Through a firewall, with intrusion prevention and network security in place. This applies to {{site.data.keyword.Bluemix_notm}} Dedicated only.
    2. Through the IBM DataPower Gateway with reverse proxy and SSL termination proxy.
    3. Through the network router.
    4. Through authorization by using Cloud Foundry cloud controller, to ensure access to only apps and service instances that are created by the developer.

For {{site.data.keyword.Bluemix_notm}} Dedicated and {{site.data.keyword.Bluemix_notm}} Local *administrators*, the **administrator flow** is as follows:
 1. Through a firewall, with intrusion prevention and network security in place.
 2. Through the IBM DataPower Gateway with reverse proxy and SSL termination proxy.
 3. Through the network router.
 4. Reaches the Administration page in the {{site.data.keyword.Bluemix_notm}} user interface.

In addition to users described in these paths, an authorized security operations team performs various operational security tasks, such as the following:
 * Vulnerability scans. For {{site.data.keyword.Bluemix_notm}} Local, you own the physical security and any scans within your firewall.
 * User access management.
 * Operating system hardening by periodically applying fixes with IBM Endpoint Manager.
 * Management of risks with intrusion protection.
 * Security monitoring with QRadar.
 * Security reports available on the Administration page.
 

### Platform and service compliance
The following table displays which services in {{site.data.keyword.Bluemix_notm}} are compliant for each of the standards.

|{{site.data.keyword.Bluemix_notm}} components		|FISC		|ISO 27001	|PCI |SOC 2 Type 1		|
|:----------------------|:---------:|:---------:|:---------:|:---------:|
|{{site.data.keyword.Bluemix_notm}} platform		|Y			|Y	|Y	|Y	|
|{{site.data.keyword.autoscaling}}			|Y	|Y |Y	|			|
|{{site.data.keyword.cloudant}}				|Y |Y |	|Y	|
|{{site.data.keyword.jazzhub_short}}					|Y	|Y	|	|			|
|{{site.data.keyword.mql}}				|Y	|Y	|Y	|	 		|

*Table 1. Platform and service compliance*

# Related Links
{: #rellinks}

## Related Links
{: #general}

* [IBM SaaS security](http://www.ibm.com/cloud-computing/built-on-cloud/saas-security)
* [Getting started with Single Sign On](../services/SingleSignOn/index.html)
