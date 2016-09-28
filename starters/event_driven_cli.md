---

 

copyright:

  years: 2015，2016
lastupdated: "2016-02-02"
 

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:prereq: .prereq}
{:download: .download}
{:pre: .pre}
{:app_name: data-hd-keyref="app_name"}
{:app_key: data-hd-keyref="app_key"}
{:app_secret: data-hd-keyref="app_secret"}
{:app_url: data-hd-keyref="app_url"}
{:host: data-hd-keyref="host"}
{:org_name: data-hd-keyref="org_name"}
{:route: data-hd-keyref="route"}
{:space_name: data-hd-keyref="space_name"}
{:service_name: data-hd-keyref="service_name"}
{:service_instance_name: data-hd-keyref="service_instance_name"}
{:user_ID: data-hd-keyref="user_ID"}
{:auth_key: data-hd-keyref="auth_key"}

# Setting up the event-driven app command line interface
Last updated: 2 February 2016
{: .last-updated}

You can use the command line interface to set up your namespace and authorization key.
{:shortdesc}

To use the event-driven apps command line interface:

1. Install the command line interface. You can also [download the CLI](https://{DomainName}/whisk/cli/download){: new_window} and install it from your local filesystem, using [pip](https://pip.pypa.io/en/stable/){: new_window}.
 
  <pre class="pre">sudo pip install --upgrade https://<span class="keyword" data-hd-keyref="DomainName">DomainName</span>/whisk/cli/download</pre>

2. Set your event-driven apps namespace and authorization key. These are your settings. Copy and paste this line into your terminal.

  <pre class="pre">wsk property set --namespace <var class="keyword varname" data-hd-keyref="org_name">org_name</var>_<var class="keyword varname" data-hd-keyref="space_name">space_name</var> --auth <var class="keyword varname" data-hd-keyref="auth_key">authuorization_key</var></pre>

3. Verify your setup.

  <pre class="pre">wsk action invoke /whisk.system/samples/echo hello --blocking
{ "message": "hello" }
</pre>

4. For more information about the event-driven app command line interface, see [Event-driven app CLI](../cli/plugins/eventdrivenapps/index.html).
