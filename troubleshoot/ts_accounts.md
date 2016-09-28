---

copyright:
  years: 2015, 2016
lastupdated: "2016-09-13"

---

{:tsSymptoms: .tsSymptoms} 
{:tsCauses: .tsCauses} 
{:tsResolve: .tsResolve} 
{:new_window: target="_blank"}  
{:shortdesc: .shortdesc}
{:codeblock: .codeblock} 





# Troubleshooting for managing accounts
{: #managingaccounts}

Last updated: 13 September 2016
{: .last-updated}

You might experience problems when you manage your account, such as different apps share the same domain name, administrators can't view all organizations. However, in many cases, you can recover from these problems by following a few easy steps.
{:shortdesc}


## Account is inactive
{: #ts_accnt_inactive}

You are unable to create an app in {{site.data.keyword.Bluemix_notm}} if your account is inactive. You must contact the support team to fix this problem.



When you try to create an app in {{site.data.keyword.Bluemix_notm}}, you see the following error message:
{: tsSymptoms} 

`BXNUI0096E: The app wasn't created. Your account is inactive because it was canceled or suspended.`


The status of your {{site.data.keyword.Bluemix_notm}} account becomes inactive when the account is cancelled or suspended.
{: tsCauses}

 

To reactivate your account, you can submit a ticket from the [Bluemix Support Ticketing System](https://chinabluemix.itsm.unisysedge.cn/){: new_window} page. In the ticket, you must include the following information:
{: tsResolve}

  * The ID that you use to log in to {{site.data.keyword.Bluemix_notm}}.
  * The name of the organization in which your app is being created. This information can help the support team determine whether you are assigned the correct roles or membership within your organization.



## No space is associated with your current org
{: #ts_no_space}

You are unable to create an application if no space is associated with your current organization.



When you try to create an app in {{site.data.keyword.Bluemix_notm}}, you see the following error message:
{: tsSymptoms} 


`BXNUI0097E: Before you can add an app, at least one space must be associated with your organization and region. On the Dashboard, click Create a Space. When the space is created, try again.`



Apps in {{site.data.keyword.Bluemix_notm}} must be created within a space under your organization.
{: tsCauses} 

 

To create a space, use one of the following methods: 
{: tsResolve}
 
  * On the {{site.data.keyword.Bluemix_notm}} Dashboard, select the organization in which you want to create the space, then click **Create a Space**.
  * In the cf command line interface, type `cf create-space <space_name> -o <organization_name>`.
  
  
  
  
## Apps share same domain name
{: #ts_domain_diff}

You might notice that several applications share the same URL in {{site.data.keyword.Bluemix_notm}}.

 

This problem might happen when you assign the same URL route for different applications within a space.
{: tsCauses}

For example, you push the myApp1 application to {{site.data.keyword.Bluemix_notm}} and set the domain to "mynewapp.{DomainName}". Then, you push another myApp2 application to the same space and set one of its URL routes to "mynewapp.{DomainName}". The route is now mapped to both applications.

 

This is supported behavior of the {{site.data.keyword.Bluemix_notm}} and you can use this practice to achieve zero downtime for your application upgrade. For more information, see Blue-green deployments.
{: tsResolve}
  
	




