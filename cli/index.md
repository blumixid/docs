---

 

copyright:

  years: 2015，2016
lastupdated: "2016-11-21"
 

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}

# CLI and dev tools
{: #cli}



With {{site.data.keyword.Bluemix_short}}, you have access to powerful tools such as a unified command line interface and CLI plug-ins. Each of these CLI downloads are all available to support your {{site.data.keyword.Bluemix_notm}} experience.
{:shortdesc}

## ![](./images/CLI.svg) Command line interfaces
{: #downloads}

Download and install command line interfaces to support your {{site.data.keyword.Bluemix_notm}} experience. 

The Cloud Foundry cf command line tool is a prerequisite for all {{site.data.keyword.Bluemix_notm}} CLI tools. {{site.data.keyword.Bluemix_notm}} command line tool provides extended experience to manage your {{site.data.keyword.Bluemix_notm}} environment besides Cloud Foundry applications.

Both CLI tools use 443 port by default. If you have HTTP proxy between the CLI tools and {{site.data.keyword.Bluemix_notm}} environment, you must configure the  `http-proxy` environment variable with the actual HTTP proxy url and port if there is any. See [Using the CLI with an HTTP Proxy Server](http://docs.cloudfoundry.org/cf-cli/http-proxy.html){: new_window} for more details.

| *{{site.data.keyword.Bluemix_notm}}: bx* | *Cloud Foundry: cf* |
|---------------------|---------------|
| [Download CLI](http://clis.ng.bluemix.net/) <br> [View Docs](./reference/bluemix_cli/index.html)|  [Download CLI](https://github.com/cloudfoundry/cli/releases){: new_window}  <br> [View Docs](./reference/cfcommands/index.html) |


## ![](./images/CLI_Plugin.svg) Command line interface plug-ins


Easily extend your {{site.data.keyword.Bluemix_notm}} command line interface with more commands. To access the {{site.data.keyword.Bluemix_notm}} command line interface plug-ins, see the [CLI Plug-in Repository](https://plugins.ng.bluemix.net/).

### Extend your {{site.data.keyword.Bluemix_notm}} command line interface: bx
{: cli_bluemix_ext}

After you install the {{site.data.keyword.Bluemix_notm}} cli tool, the [CLI Plug-in Repository](https://plugins.ng.bluemix.net/) is pre-configured with a repository alias `Bluemix` by default. You can install available plug-ins directly.

```
bluemix plugin install plugin_name -r Bluemix
```
| *{{site.data.keyword.autoscaling}} CLI* | *Catalog Manager*  |
|-----|-----|
| Plug-in name: auto-scaling <br> [View Docs](./plugins/auto-scaling/index.html) | Plug-in name: catalog-manager  <br> [View Docs](./plugins/catalogmanager/index.html) |

You can also add plug-ins from other repositories that complies with the {{site.data.keyword.Bluemix_notm}} cli architecture.

1. To install {{site.data.keyword.Bluemix_notm}} CLI plug-ins from another repository, set the plug-in registry endpoint:
```
bluemix plugin repo-add bluemix-other-repo [repo_url]
```
where `repo_url` is the https url of the plugin repository.

2. Run the following command to install a plug-in:
```
bluemix plugin install plugin_name -r bluemix-other-repo
```





### Extend your Cloud Foundry command line interface: cf
{: cli_cf_ext}

1. To install cf CLI plug-ins from the {{site.data.keyword.Bluemix_notm}} registry, set the plug-in registry endpoint:
```
cf add-plugin-repo bluemix-cf https://plugins.ng.bluemix.net
```
2. Run the following command to install a plug-in:
```
cf install-plugin plugin_name -r bluemix-cf
```

| *Admin Console* | 
|-----------------|
|  Plug-in name: bluemix-admin <br> [View Docs](/docs/cli/plugins/bluemix_admin/index.html) | 



<!-- View docs link for bluemix-admin plug-in cannot go live until December time frame. Check in with Michelle -->

