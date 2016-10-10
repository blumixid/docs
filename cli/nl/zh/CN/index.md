---

 

copyright:

  years: 2015，2016

 

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}

# CLI 和开发工具
{: #cli}

上次更新时间：2016 年 9 月 13 日
{: .last-updated}

通过 {{site.data.keyword.Bluemix_short}}，您可以访问各种功能强大的工具，例如统一命令行界面和 CLI 插件。其中每个 CLI 下载都可用于支持您的 {{site.data.keyword.Bluemix_notm}} 体验。
{:shortdesc}

## ![](./images/CLI.svg) 命令行界面
{: #downloads}

下载并安装命令行界面以便为您的 {{site.data.keyword.Bluemix_notm}} 体验提供支持。下载并安装命令行界面以便为您的 {{site.data.keyword.Bluemix_notm}} 体验提供支持。 

Cloud Foundry cf 命令行工具是所有其他 {{site.data.keyword.Bluemix_notm}} CLI 工具的先决条件。{{site.data.keyword.Bluemix_notm}} 命令行工具提供了管理 {{site.data.keyword.Bluemix_notm}} 环境以及 Cloud Foundry 应用程序的延伸体验。
 

缺省情况下，这两种 CLI 工具均使用 443 端口。如果在 CLI 工具与 {{site.data.keyword.Bluemix_notm}} 环境之间有 HTTP 代理，那么必须使用实际 HTTP 代理 URL 和端口（如有）来配置 `http-proxy` 环境变量。请参阅 [Using the CLI with an HTTP Proxy Server](http://docs.cloudfoundry.org/cf-cli/http-proxy.html){: new_window} 以获取更多详细信息。

|  *Cloud Foundry：cf* | *{{site.data.keyword.Bluemix_notm}}：bx* |
|---------------------|---------------|
| [下载 CLI](https://github.com/cloudfoundry/cli/releases){: new_window}<br> [查看文档](./reference/cfcommands/index.html) | [下载 CLI](http://clis.ng.bluemix.net/)<br> [查看文档](./reference/bluemix_cli/index.html)| 


## ![](./images/CLI_Plugin.svg) 命令行界面插件

使用更多命令轻松扩展 {{site.data.keyword.Bluemix_notm}} 命令行界面。要访问 {{site.data.keyword.Bluemix_notm}} 命令行界面插件，请参阅 [ CLI 插件存储库](https://plugins.ng.bluemix.net/)。

### 扩展 {{site.data.keyword.Bluemix_notm}} 命令行界面：bx
{: cli_bluemix_ext}

1. 要从 {{site.data.keyword.Bluemix_notm}} 注册表安装 {{site.data.keyword.Bluemix_notm}} CLI 插件，请设置插件注册表端点：
```
bluemix plugin repo-add bluemix-bx-staging https://plugins.ng.bluemix.net
```
2. 运行以下命令来安装插件：
```
bluemix plugin install plugin_name -r bluemix-bx-staging
```

| *{{site.data.keyword.autoscaling}} CLI* | *目录管理器*  |
|-----|-----|
| 插件名称：auto-scaling<br> [查看文档](./plugins/auto-scaling/index.html) | 插件名称：catalog-manager<br> [查看文档](./plugins/catalogmanager/index.html) |



### 扩展 Cloud Foundry 命令行界面：cf
{: cli_cf_ext}

1. 要从 {{site.data.keyword.Bluemix_notm}} 注册表安装 cf CLI 插件，请设置插件注册表端点：
```
cf add-plugin-repo bluemix-cf-staging https://plugins.ng.bluemix.net
```
2. 运行以下命令来安装插件：
```
cf install-plugin plugin_name -r bluemix-cf-staging
```

| *管理控制台* | 
|-----------------|
|  插件名称：bluemix-admin<br> [查看文档](../cli/plugins/bluemix_admin/index.html) | 



<!-- View docs link for bluemix-admin plug-in cannot go live until December time frame. Check in with Michelle -->

