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



# Troubleshooting for accessing {{site.data.keyword.Bluemix_notm}} 
{: #accessing}

Last updated: 13 September 2016
{: .last-updated} 

General problems with accessing {{site.data.keyword.Bluemix_notm}} might include a user that is unable to log in to {{site.data.keyword.Bluemix_notm}}, an account that is stuck in a pending state, and so on. However, in many cases, you can recover from these problems by following a few easy steps. 
{:shortdesc}




<!-- begin STAGING ONLY --> 

## Problem accessing external website
{: #ts_bmlinkid}

You cannot log in to {{site.data.keyword.Bluemix_notm}} by using your IBM intranet ID unless you link your intranet ID with your IBMid.


After you select **Sign in with your intranet ID** from the {{site.data.keyword.Bluemix_notm}} Sign in page, you might see the following error message:
{: tsSymptoms} 

`Problem Accessing External Website`



This problem occurs when you log in to {{site.data.keyword.Bluemix_notm}} by using an IBM intranet ID that is not linked to an IBMid. Your IBMid is the ID that you use to log in to www.ibm.com.
{: tsCauses}


As an IBM employee, before you are able to log in to {{site.data.keyword.Bluemix_notm}} by using your IBM intranet ID, you must link your intranet ID with your external IBMid. To link the two IDs, complete the following steps:
{: tsResolve} 

  1. On the [Central Sign-on](https://w3-03.sso.ibm.com/tools/cso/index.jsp){: new_window} page, click **My Sign-ons**.
  2. On the My Sign-ons page, click **Link IDs**, and enter your IBMid and password on the {{site.data.keyword.Bluemix_notm}} Sign in page. After that, your intranet ID and IBMid will be automatically linked.
  

<!-- end STAGING ONLY -->




## You have unsaved changes
{: #ts_unsaved_changes}


When you navigate on the app details page, you might be unable to perform any actions and might be prompted to save changes before you can proceed. 


When you try to check your app or services on the app details page, you keep getting the following error message:
{: tsSymptoms} 

`You have unsaved changes in page app_name. Save or cancel the changes.`


When you scroll your mouse over the **INSTANCES** or **MEMORY QUOTA** field on the runtime pane, the values change. This behavior is by design; however, the error message prompts you to save the memory or instance settings before you navigate away from the page. 
{: tsCauses}


Close the message window, and then click the **RESET** button in your runtime pane. 
{: tsResolve} 









## Unable to add users to an org
{: #ts_adduser}

You can invite more than one user to work under the same organization. You can invite users to your organization only if you are the account owner, or if you are both a manager and a member of the organization.
 

You cannot see the **Invite a New User** link in your **Manage Organizations** section. 
{: tsSymptoms}

 

Only the following {{site.data.keyword.Bluemix_notm}} users can invite users to an organization:
{: tsCauses}
  * The account owner of the organization
  * Organization managers who are also members, not collaborators, of the organization
  
In {{site.data.keyword.Bluemix_notm}}, you can be either a member or a collaborator of an organization:

<dl><dt>Collaborator</dt>
<dd>You are a collaborator of an organization if you already have a {{site.data.keyword.Bluemix_notm}} account, and someone else invites you to the organization.</dd>
<dt>Member</dt>
<dd>You are a member of an organization if you don't have a {{site.data.keyword.Bluemix_notm}} account, but then someone invites you to the organization and you sign up for {{site.data.keyword.Bluemix_notm}} from the invitation.</dd>
</dl>


You cannot invite users to your organization if you are a collaborator of the organization, even if you have been assigned as an organization manager.

**Note:** All organization managers, including those who are collaborators of an organization, can add, modify, and remove users that are already in the organization.

 

If you are unable to invite users to your organization and need a different role to do so, contact your organization manager to change your role. To identify your organization manager, complete the following steps:
{: tsResolve}

  1. Go to the {{site.data.keyword.Bluemix_notm}} Dashboard, click the {{site.data.keyword.avatar}} icon ![Avatar icon](images/account_support.svg) in the menu bar, and select **Manage Organizations**.
  2. Go to your organization, and view the information of organization manager on the **USERS** tab.  
  
If you are unable to invite users because you are a collaborator and not a member, you must delete your previous {{site.data.keyword.Bluemix_notm}} account and then be invited to join the account as a member of the organization. To delete your previous account and join the account as a member, complete the following steps: 

  1. Go to the [Bluemix Support Ticketing System](https://chinabluemix.itsm.unisysedge.cn/){: new_window} page to open a support ticket and request that your account be deleted. If you have data that is associated with your old account that you want to save and move to the new account, include this information in your email. 
  2. After your account is deleted, have a user with the organization manager role invite you to the organization as an organization manager. Then, sign up for {{site.data.keyword.Bluemix_notm}} from the invitation. 




## Batch registration of users is not supported
{: #ts_batchregistration}

When you register users for {{site.data.keyword.Bluemix_notm}}, you must register each user individually.
 

{{site.data.keyword.Bluemix_notm}} does not provide the capability to register multiple users at the same time.
{: tsSymptoms}
 

{{site.data.keyword.Bluemix_notm}} doesn't support batch registration of users. To register users for {{site.data.keyword.Bluemix_notm}}, you must register each user individually.
{: tsCauses}
 

To register multiple users for {{site.data.keyword.Bluemix_notm}}, you must complete the following steps for each user:
{: tsResolve}

  1. Click **SIGN UP** in the {{site.data.keyword.Bluemix_notm}} user interface.
  2. Complete the steps by following the wizard.

    

## {{site.data.keyword.Bluemix_notm}} page can't be loaded
{: #ts_err}

When you use the {{site.data.keyword.Bluemix_notm}} user interface, you might not be able to load a {{site.data.keyword.Bluemix_notm}} page. Instead, you might see error messages BXNUI0001E or BXNUI0016E.
 

You might see one of the following error messages when you use the {{site.data.keyword.Bluemix_notm}} user interface:
{: tsSymptoms}

`BXNUI0001E: The page wasn't loaded because Bluemix didn't detect whether a session exists.`


`BXNUI0016E: The apps and services weren't retrieved because a Bluemix page didn't load.`

 

You can complete one or more of the following actions as necessary:
{: tsResolve}

  * Refresh or restart your browser.
  * Log out of {{site.data.keyword.Bluemix_notm}} and log in again.
  * Use the private browsing mode of your browser. 
  * Clear the cookies and the cache of the browser.
  * Use a different browser. For information about the versions of the browsers that are supported by {{site.data.keyword.Bluemix_notm}}, see [{{site.data.keyword.Bluemix_notm}} Prerequisites](https://developer.ibm.com/bluemix/support/#prereqs){: new_window}.
  * If you have installed the cf command line interface, enter the `cf apps` command to see whether your application is running.
  
  
  
  
  

