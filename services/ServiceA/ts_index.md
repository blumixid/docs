---

copyright:
  years: 2016
lastupdated: "YYYY-MM-DD"

---
<!-- Copyright info at top of file: REQUIRED
    The copyright info is YAML content that must occur at the top of the MD file, before attributes are listed.
    It must be --- surrounded by 3 dashes ---
    The value "years" can contain just one year or a two years separated by a comma. (years: 2014, 2016)
    Indentation as per the previous template must be preserved.
-->

<!-- Common attributes used in the template are defined as follows: -->
{:tsSymptoms: .tsSymptoms} 
{:tsCauses: .tsCauses} 
{:tsResolve: .tsResolve} 
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}

# service_short_name troubleshooting
{: #ts}
<!-- Provide an appropriate ID above -->


<!-- This is the template for troubleshooting topics.  -->

<!-- The short description section should include the service long name and "Bluemix" for search optimization. Example short description: -->

Here are the answers to common troubleshooting questions about using <service_name> on {{site.data.keyword.Bluemix_notm}}.
{:shortdesc}


<!-- Example problem statement title: "Cannot add Git repository" -->

## <problem_statement>
{: #problem}

<!-- This is the template for a problem topic.  -->

<!-- The short description section contains a brief description of problem. For example:  -->

After you create an app on the Dashboard, you click *ADD GIT* to create a Git repository, but you cannot proceed.
{:shortdesc}

<!-- The symptoms section contains a description of problem symptoms. For example:  -->
When you click ADD GIT, a window opens and one of these issues occur:
- The window hangs with a blank screen.
- A message states that a problem exists with 3rd party cookies.
{: tsSymptoms}

<!-- The causes section contains a brief explanation of what causes the problem. For example:  -->
Your browser might be configured to prevent a cookie from being set. That cookie must be set from the IBM Bluemix DevOps Services site in the hub.jazz.net internet domain from within the context of the Bluemix console.
{: tsCauses}

<!-- The resolve section contains steps to resolve the problem. For example:  -->
You can fix this problem in one of three ways:
- Follow the instructions that are in the window that opens from the Bluemix console. Click the button. Another browser window opens temporarily. In that window, DevOps Services sets the authentication cookie.
- In another browser tab, go to https://hub.jazz.net and log in. Return to the Bluemix console and refresh the page. Click ADD GIT again.
- Change your browser settings to enable 3rd party cookies and click ADD GIT again. 
{: tsResolve}

## <service_name> error messages
{: #errormsgs}

You might see these error messages when using the <service_name> service on Bluemix.
{:shortdesc}

### errorID
**message description**

Message explanation (optional)

Recovery

### BXNUI0001E
**The page wasn't loaded because Bluemix didn't detect whether a session exists.** 

For instructions to fix this problem, see this [troubleshooting topic](https://www.{DomainName}/docs/troubleshoot/accessing.html#tr_err){: new_window}.

<!-- Add a heading and content for how to get help and support. Use this template for beta and GA services:  -->
## Getting help and support for <service_short_name> 
{: #gettinghelp}

If you have problems or questions when using service_name, you can check {{site.data.keyword.Bluemix_notm}}, or get help by searching for information or by asking questions through a forum. You can also open a support ticket. 

* You can check whether {{site.data.keyword.Bluemix_notm}} is available by going to the [Bluemix status page](https://console.chinabluemix.net/status){:new_window}.

* You can review the forums to see whether other users ran into the same problem. When using the forums to ask a question, tag your question so that it is seen by the {{site.data.keyword.Bluemix_notm}} development teams.
* For questions about the service and getting started instructions, use the [IBM developerWorks dW Answers](https://developer.ibm.com/cn_answers/topics/<service_name>/?smartspace=bluemix){:new_window} forum. Include the  "<service_keyword>" and "bluemix" tags.

See [Getting help](https://www.{DomainName}/docs/support/index.html#getting-help) for more details about using the forums.

* If you still can't resolve the problem, you can open a support ticket. For information about opening an Bluemix support ticket, or about support levels and ticket severities, see [Contacting support](https://www.{DomainName}/docs/support/index.html#contacting-support).

