---

 

copyright:

  years: 2015，2016

 

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}

# CLI and dev tools
{: #cli}

Last updated: 13 September 2016
{: .last-updated}

With {{site.data.keyword.Bluemix_short}}, you have access to powerful tools such as a unified command line interface and CLI plug-ins. Each of these CLI downloads are all available to support your {{site.data.keyword.Bluemix_notm}} experience.
{:shortdesc}

## ![](./images/CLI.svg) Command line interfaces
{: #downloads}

Download and install command line interfaces to support your {{site.data.keyword.Bluemix_notm}} experience. Download and install command line interfaces to support your {{site.data.keyword.Bluemix_notm}} experience. 

The Cloud Foundry cf command line tool is a prerequisite for all other {{site.data.keyword.Bluemix_notm}} CLI tools. {{site.data.keyword.Bluemix_notm}} command line tool provides extended experience to manage your {{site.data.keyword.Bluemix_notm}} environment besides Cloud Foundry applications. 

Both CLI tools use 443 port by default. If you have HTTP proxy between the CLI tools and {{site.data.keyword.Bluemix_notm}} environment, you must configure the  `http-proxy` environment variable with the actual HTTP proxy url and port if there is any. See [Using the CLI with an HTTP Proxy Server](http://docs.cloudfoundry.org/cf-cli/http-proxy.html){: new_window} for more details.

|  *Cloud Foundry: cf* | *{{site.data.keyword.Bluemix_notm}}: bx* |
|---------------------|---------------|
| [Download CLI](https://github.com/cloudfoundry/cli/releases){: new_window}  <br> [View Docs](./reference/cfcommands/index.html) | [Download CLI](http://clis.ng.bluemix.net/) <br> [View Docs](./reference/bluemix_cli/index.html)| 


## ![](./images/CLI_Plugin.svg) Command line interface plug-ins

Easily extend your {{site.data.keyword.Bluemix_notm}} command line interface with more commands. To access the {{site.data.keyword.Bluemix_notm}} command line interface plug-ins, see the [CLI Plug-in Repository](https://plugins.ng.bluemix.net/).

### Extend your {{site.data.keyword.Bluemix_notm}} command line interface: bx
{: cli_bluemix_ext}

1. To install {{site.data.keyword.Bluemix_notm}} CLI plug-ins from the {{site.data.keyword.Bluemix_notm}} registry, set the plug-in registry endpoint:
```
bluemix plugin repo-add bluemix-bx-staging https://plugins.ng.bluemix.net
```
2. Run the following command to install a plug-in:
```
bluemix plugin install plugin_name -r bluemix-bx-staging
```

| *{{site.data.keyword.autoscaling}} CLI* | *Catalog Manager*  |
|-----|-----|
| Plug-in name: auto-scaling <br> [View Docs](./plugins/auto-scaling/index.html) | Plug-in name: catalog-manager  <br> [View Docs](./plugins/catalogmanager/index.html) |



### Extend your Cloud Foundry command line interface: cf
{: cli_cf_ext}

1. To install cf CLI plug-ins from the {{site.data.keyword.Bluemix_notm}} registry, set the plug-in registry endpoint:
```
cf add-plugin-repo bluemix-cf-staging https://plugins.ng.bluemix.net
```
2. Run the following command to install a plug-in:
```
cf install-plugin plugin_name -r bluemix-cf-staging
```

| *Admin Console* | 
|-----------------|
|  Plug-in name: bluemix-admin <br> [View Docs](../cli/plugins/bluemix_admin/index.html) | 



<!-- View docs link for bluemix-admin plug-in cannot go live until December time frame. Check in with Michelle -->

