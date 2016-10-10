---

 

copyright:

  years: 2015，2016

 

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

# 设置事件驱动型应用程序命令行界面
上次更新时间：2016 年 2 月 2 日
{: .last-updated}

可以使用命令行界面来设置名称空间和授权密钥。{:shortdesc}

要使用事件驱动型应用程序命令行界面，请执行以下操作：

1. 安装命令行界面。您还可以[下载 CLI](https://{DomainName}/whisk/cli/download){: new_window}，然后使用 [pip](https://pip.pypa.io/en/stable/){: new_window} 从本地文件系统安装 CLI。
 
  <pre class="pre">sudo pip install --upgrade https://<span class="keyword" data-hd-keyref="DomainName">DomainName</span>/whisk/cli/download</pre>

2. 设置事件驱动型应用程序名称空间和授权密钥。下面是您的设置。将此行复制并粘贴到您的终端中。

  <pre class="pre">wsk property set --namespace <var class="keyword varname" data-hd-keyref="org_name">org_name</var>_<var class="keyword varname" data-hd-keyref="space_name">space_name</var> --auth <var class="keyword varname" data-hd-keyref="auth_key">authuorization_key</var></pre>

3. 验证您的设置。

  <pre class="pre">wsk action invoke /whisk.system/samples/echo hello --blocking
{ "message": "hello" }
</pre>

4. 有关事件驱动型应用程序命令行界面的更多信息，请参阅[事件驱动型应用程序 CLI](../cli/plugins/eventdrivenapps/index.html)。
