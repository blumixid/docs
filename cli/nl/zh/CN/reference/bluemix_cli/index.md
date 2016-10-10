---

 

copyright:

  years: 2015, 2016

 
---


{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# {{site.data.keyword.Bluemix_notm}} (bx) 命令
{: #bluemix_cli}

上次更新时间：2016 年 9 月 12 日
{: .last-updated}

版本：0.4.1

{{site.data.keyword.Bluemix_notm}} 命令行界面 (CLI) 提供了一组按名称空间分组的命令，供用户用于与 {{site.data.keyword.Bluemix_notm}} 进行交互。一些 {{site.data.keyword.Bluemix_notm}} 命令是现有 cf 命令的包装程序，而另一些为 {{site.data.keyword.Bluemix_notm}} 用户提供了扩展功能。以下信息列出了 {{site.data.keyword.Bluemix_notm}} CLI 支持的命令，并包含命令名称、选项、用法、先决条件、描述和示例。
{:shortdesc}
 
**注：***先决条件*列出使用命令前必须执行的操作。没有任何先决条件操作的命令会列出**无**。否则，先决条件可能会包含以下一个或多个操作：
<dl>
<dt>端点</dt>
<dd>使用命令前，必须通过 <code>bluemix api</code> 设置 API 端点。</dd>
<dt>登录</dt>
<dd>使用此命令之前，必须使用 <code>bluemix login</code> 命令登录。如果使用联合标识登录，请使用“--sso”选项对一次性密码进行验证。</dd>
<dt>目标</dt>
<dd>使用命令前，必须通过 <code>bluemix target</code> 命令设置组织和空间。</dd>
</dl>


## bluemix 命令索引
{: #bx_commands_index}

使用下表中的索引可查看常用 bluemix 命令：


<table summary="常规 bluemix 命令。">
 <thead>
 <th colspan="5">常规 bluemix 命令</th>
 </thead>
 <tbody> 
 <tr> 
 <td>[bluemix help](index.html#bluemix_help)</td> 
 <td>[bluemix api](index.html#bluemix_api)</td> 
 <td>[bluemix_login](index.html#bluemix_login)</td>
 <td>[bluemix logout](index.html#bluemix_logout)</td>
 <td>[bluemix target](index.html#bluemix_target)</td>
 </tr> 
 <tr> 
 <td>[bluemix info](index.html#bluemix_info) </td> 
 <td>[bluemix config](index.html#bluemix_config)</td> 
 <td>[bluemix list](index.html#bluemix_list)</td>
 <td>[bluemix scale](index.html#bluemix_scale)</td>
 <td>[bluemix curl](index.html#bluemix_curl)</td>
 </tr>
  </tbody> 
 </table> 
*表 1. 常规 bluemix 命令*



<table summary="可用于管理组织、空间和用户的 bluemix 命令">
 <thead>
 <th colspan="5">用于管理组织、空间和用户的命令</th>
 </thead>
 <tbody> 
 <tr> 
 <td>[bluemix iam orgs](index.html#bluemix_iam_orgs)</td>
 <td>[bluemix iam org](index.html#bluemix_iam_org)</td> 
 <td>[bluemix iam org-create](index.html#bluemix_iam_org_create)</td>
 <td>[bluemix iam org-replicate](index.html#bluemix_iam_org_replicate)</td>
 <td>[bluemix iam org-rename](index.html#bluemix_iam_org_rename)</td>
 </tr> 
 <tr> 
 <td>[bluemix iam org-delete](index.html#bluemix_iam_org_delete)</td>
 <td>[bluemix iam spaces](index.html#bluemix_iam_spaces)</td> 
 <td>[bluemix iam space](index.html#bluemix_iam_space)</td>
 <td>[bluemix iam space-create](index.html#bluemix_iam_space_create)</td>
 <td>[bluemix iam space-rename](index.html#bluemix_iam_space_rename)</td>
 </tr>
 <tr> 
 <td>[bluemix iam space-delete](index.html#bluemix_iam_space_delete)</td>
 <td>[bluemix iam account-users](index.html#bluemix_iam_account-users)</td> 
 <td>[bluemix iam account-user-invite](index.html#bluemix_iam_account-user-invite)</td>
 <td>[bluemix iam org-users](index.html#bluemix_iam_org_users)</td>
 <td>[bluemix iam org-role-set](index.html#bluemix_iam_org_role_set)</td>
 </tr>
 <tr> 
 <td>[bluemix iam org-role-unset](index.html#bluemix_iam_org_role_unset)</td>
 <td>[bluemix iam space-users](index.html#bluemix_iam_space_users)</td> 
 <td>[bluemix iam space-role-set](index.html#bluemix_iam_space_role_set)</td>
 <td>[bluemix iam space-role-unset](index.html#bluemix_iam_space_role_unset)</td>
 <td></td>
 </tr>
 </tbody> 
 </table> 
*表 2. 用于管理组织、空间和用户的命令*



<table summary="可用于管理 Cloud Foundry 应用程序的 bluemix 命令">
 <thead>
 <th colspan="5">用于管理 cf 应用程序的命令</th>
 </thead>
 <tbody> 
 <tr> 
 <td>[bluemix app push](index.html#bluemix_app_push)</td>
 <td>[bluemix app list](index.html#bluemix_app_list)</td>
<td>[bluemix app show](index.html#bluemix_app_show)</td> 
 <td>[bluemix app scale](index.html#bluemix_app_scale)</td>
 <td>[bluemix app delete](index.html#bluemix_app_delete)</td>
 </tr> 
 <tr> 
 <td>[bluemix app rename](index.html#bluemix_app_rename)</td>
 <td>[bluemix app start](index.html#bluemix_app_start)</td>
<td>[bluemix app stop](index.html#bluemix_app_stop)</td> 
 <td>[bluemix app restart](index.html#bluemix_app_restart)</td>
 <td>[bluemix app restage](index.html#bluemix_app_restage)</td>
 </tr>
 <tr> 
 <td>[bluemix app instance-restart](index.html#bluemix_app_instance_restart)</td>
 <td>[bluemix app events](index.html#bluemix_app_events)</td>
<td>[bluemix app files](index.html#bluemix_app_files)</td> 
 <td>[bluemix app logs](index.html#bluemix_app_logs)</td>
 <td>[bluemix app env](index.html#bluemix_app_env)</td>
 </tr>
 <tr> 
 <td>[bluemix app env-set](index.html#bluemix_app_env_set)</td>
 <td>[bluemix app env-unset](index.html#bluemix_app_env_unset)</td>
<td>[bluemix app stacks](index.html#bluemix_app_stacks)</td> 
 <td>[bluemix app stack](index.html#bluemix_app_stack)</td>
 <td>[bluemix app manifest-create](index.html#bluemix_app_manifest_create)</td>
 </tr>
  </tbody> 
 </table> 
*表 3. 用于管理 cf 应用程序的命令*


<table summary="可用于管理 Bluemix 服务的 bluemix 命令">
 <thead>
 <th colspan="5">用于管理 Bluemix 服务的命令</th>
 </thead>
 <tbody> 
 <tr> 
 <td>[bluemix service offerings](index.html#bluemix_service_offerings)</td>
 <td>[bluemix service list](index.html#bluemix_service_list)</td>
 <td>[bluemix service show](index.html#bluemix_service_show)</td> 
 <td>[bluemix service create](index.html#bluemix_service_create)</td>
 <td>[bluemix service update](index.html#bluemix_service_update)</td>
 </tr> 
 <tr> 
 <td>[bluemix service delete](index.html#bluemix_service_delete)</td>
 <td>[bluemix service rename](index.html#bluemix_service_rename)</td>
 <td>[bluemix service bind](index.html#bluemix_service_bind)</td> 
 <td>[bluemix service unbind](index.html#bluemix_service_unbind)</td>
 <td>[bluemix service key-create](index.html#bluemix_service_key_create)</td>
 </tr>
 <tr> 
 <td>[bluemix service key-delete](index.html#bluemix_service_key_delete)</td>
 <td>[bluemix service keys](index.html#bluemix_service_keys)</td>
 <td>[bluemix service key-show](index.html#bluemix_service_key_show)</td> 
 <td>[bluemix service user-provided-create](index.html#bluemix_service_user_provided_create)</td>
 <td>[bluemix service user-provided-update](index.html#bluemix_service_user_provided_update)</td>
 </tr>
  </tbody> 
 </table> 
*表 4. 用于管理 Bluemix 服务的命令*


<table summary="可用于管理 Bluemix 目录、插件、帐单和安全设置的 bluemix 命令">
<thead>
 <th colspan="5">用于管理 Bluemix 目录、插件、帐单和安全设置的命令</th>
 </thead>
 <tbody> 
 <tr> 
 <td>[bluemix catalog templates](index.html#bluemix_catalog_templates)</td>
 <td>[bluemix catalog template](index.html#bluemix_catalog_template)</td>
<td>[bluemix catalog template-run](index.html#bluemix_catalog_template_run)</td> 
 <td>[bluemix plugin repos](index.html#bluemix_plugin_repos)</td>
 <td>[bluemix plugin repo-add](index.html#bluemix_plugin_repo_add)</td> 
 </tr> 
 <tr> 
 <td>[bluemix plugin repo-remove](index.html#bluemix_plugin_repo_remove)</td> 
 <td>[bluemix plugin repo-plugins](index.html#bluemix_plugin_repo_plugins)</td>
 <td>[bluemix plugin list](index.html#bluemix_plugin_list)</td>
 <td>[bluemix plugin install](index.html#bluemix_plugin_install)</td>
 <td>[bluemix plugin uninstall](index.html#bluemix_plugin_uninstall)</td> 
 </tr> 
 <tr> 
 <td>[bluemix bss account-usage](index.html#bluemix_bss_account_usage)</td> 
 <td>[bluemix bss org-usage](index.html#bluemix_bss_org_usage)</td>
 <td>[bluemix bss orgs-usage-summary](index.html#bluemix_orgs_usage_summary)</td>
 <td>[bluemix security cert](index.html#bluemix_security_cert)</td> 
 <td>[bluemix security cert-add](index.html#bluemix_security_cert_add)</td>
 </tr>
 <tr>
 <td>[bluemix security cert-remove](index.html#bluemix_security_cert_remove)</td>
 <td></td>
 <td></td>
 </tr>
  </tbody> 
 </table> 
*表 5. 用于管理 Bluemix 目录、插件、帐单和安全设置的命令*



<table summary="可用于管理网络设置的 bluemix 命令">
 <thead>
 <th colspan="5">用于管理网络设置的命令</th>
 </thead>
 <tbody> 
 <tr> 
 <td>[bluemix network regions](index.html#bluemix_network_regions)</td>
 <td>[bluemix network region-set](index.html#bluemix_network_region_set)</td>
 <td>[bluemix network routes](index.html#bluemix_network_routes)</td>
 <td>[bluemix network route-check](index.html#bluemix_network_route_check)</td> 
 <td>[bluemix network route-map](index.html#bluemix_network_route_map)</td> 
 </tr> 
 <tr> 
 <td>[bluemix network route-unmap](index.html#bluemix_network_route_unmap)</td>
 <td>[bluemix network route-create](index.html#bluemix_network_route_create)</td>
 <td>[bluemix network route-delete](index.html#bluemix_network_route_delete)</td>
 <td>[bluemix network orphaned-routes-delete](index.html#bluemix_network_orphaned_routes_delete)</td> 
 <td>[bluemix network domains](index.html#bluemix_network_domains)</td> 
 </tr> 
 <tr> 
 <td>[bluemix network domain-create](index.html#bluemix_network_domain_create)</td>
 <td>[bluemix network domain-delete](index.html#bluemix_network_domain_delete)</td>
 <td>[bluemix network shared-domain-create](index.html#bluemix_network_shared_domain_create)</td>
 <td>[bluemix network shared-domain-delete](index.html#bluemix_network_shared_domain_delete)</td>
 <td></td>
 </tr>
  </tbody> 
 </table> 
*表 6. 用于管理网络设置的命令*



## bluemix help
{: #bluemix_help}
显示 {{site.data.keyword.Bluemix_notm}} CLI 第一级内置命令和受支持名称空间的一般帮助，或者显示特定内置命令或名称空间的帮助。

```
bluemix help [COMMAND|NAMESPACE]
```

<strong>先决条件</strong>：无

<strong>命令选项</strong>：

   <dl>
   <dt>COMMAND|NAMESPACE（可选）</dt>
   <dd>显示其帮助信息的命令或名称空间。如果未指定，将显示 {{site.data.keyword.Bluemix_notm}} CLI 的一般帮助。</dd>
   </dl>



<strong>示例</strong>：

显示 {{site.data.keyword.Bluemix_notm}} CLI 的一般帮助：

```
bluemix help
```

显示 `info` 命令的帮助信息：

```
bluemix help info
```

显示 `ic` 名称空间的帮助：

```
bluemix help ic
```

或 

```
bluemix ic help
```

显示 `ic` 名称空间下 `group-create` 命令的帮助信息：

```
bluemix ic help group-create
```


## bluemix api
{: #bluemix_api}
设置或查看 {{site.data.keyword.Bluemix_notm}} API 端点。此命令会对 `cf api` 命令打包。

```
bluemix api [API_ENDPOINT] [--unset]
```

<strong>先决条件</strong>：无

<strong>命令选项</strong>：
   <dl>
   <dt>API_ENDPOINT（可选）</dt>
   <dd>作为目标的 API 端点，例如 `https://api.chinabluemix.net`。如果未指定 *API_ENDPOINT* 和 `--unset` 选项，将显示当前 API 端点。</dd>
   <dt>--unset（可选）</dt>
   <dd>除去 API 端点设置。</dd>
    </dl>
<strong>示例</strong>：

将 API 端点设置为 api.chinabluemix.net。

```
bluemix api api.chinabluemix.net
```

查看当前 API 端点：

```
bluemix api
```

取消设置 API 端点：

```
bluemix api --unset
```


## bluemix login
{: #bluemix_login}

用户登录。此命令会对 `cf login` 命令打包。命令选项与 `cf login` 命令选项相同。

```
bluemix login [OPTIONS...]
```

<strong>先决条件</strong>：端点

<!-- staging comment for Atlas 45: might need prereq for federated ID/SSO option unless we expect them to just view the details from the cf login command -->

<strong>命令选项</strong>：
有关 `login` 命令支持的选项的信息，请参阅 `cf login` 命令用法信息，以了解用于管理应用程序的 cf 命令。

<strong>注</Strong>：
如果使用联合标识登录，请使用“--sso”选项对一次性密码进行验证。

## bluemix logout
{: #bluemix_logout}

注销用户。此命令会对 `cf logout` 命令打包。

```
bluemix logout
```

<strong>先决条件</strong>：无


## bluemix target
{: #bluemix_target}


设置或查看目标组织或空间。此命令会对 `cf target` 命令打包。

```
bluemix target [-o ORG_NAME] [-s SPACE_NAME]
```

<strong>先决条件</strong>：端点和登录

<strong>命令选项</strong>：
   <dl>
   <dt>-o <i>ORG_NAME</i>（可选）</dt>
   <dd>要作为目标的组织的名称。</dd>
   <dt>-s <i>SPACE_NAME</i>（可选）</dt>
   <dd>要作为目标的空间的名称。</dd>
   </dl>
如果 -o *ORG_NAME* 或 -s *SPACE_NAME* 均未指定，那么将显示当前组织和空间。
<strong>示例</strong>：

将当前组织设置为 `MyOrg`，将空间设置为 `MySpace`：

```
bluemix target -o MyOrg -s MySpace
```

查看当前组织和空间：

```
bluemix target
```


## bluemix info
{: #bluemix_info}

查看基本 {{site.data.keyword.Bluemix_notm}} 信息，包括当前区域、云控制器版本以及一些有用的端点，例如用于登录和交换访问令牌的端点。

```
bluemix info
```

<strong>先决条件</strong>：端点


## bluemix config
{: #bluemix_config}


将缺省值写入配置文件。

```
bluemix config --http-timeout TIMEOUT_IN_SECONDS | --trace (true|false|path/to/file) | --color (true|false) | --locale (LOCALE|CLEAR) | --check-version (true|false)
```

<strong>先决条件</strong>：无

<strong>命令选项</strong>：
   <dl>
   <dt>--http-timeout <i>TIMEOUT_IN_SECONDS</i></dt>
   <dd>HTTP 请求的超时值。缺省值为 60 秒。</dd>
   <dt>--trace true|false|<i>path-to-file</i></dt>
   <dd>跟踪对终端或指定文件的 HTTP 请求。</dd>
   <dt>--color true|false</dt>
   <dd>启用或禁用颜色输出。缺省情况下，会启用颜色输出。</dd>
   <dt>--locale <i>LOCALE|CLEAR</i></dt>
   <dd>设置缺省语言环境。如果 LOCALE 为 <i>CLEAR</i>，将删除先前的语言环境。</dd>
   <dt>--check-version true|false</dt>
   <dd>启用或禁用 CLI 版本检查。</dd>
   </dl>

一次只能指定其中一个选项。

<strong>示例</strong>：

将 HTTP 请求超时设置为 30 秒：

```
bluemix config --http-timeout 30
```

启用 HTTP 请求的跟踪输出：

```
bluemix config --trace true
```

跟踪对指定文件 */home/usera/my_trace* 的 HTTP 请求：

```
bluemix config --trace /home/usera/my_trace
```

禁用颜色输出：

```
bluemix config --color false
```

将语言环境设置为 zh_Hans：

```
bluemix config --locale zh_Hans
```

清除语言环境设置：

```
bluemix config --locale CLEAR
```


## bluemix list
{: #bluemix_list}

列出当前空间中的所有应用程序、容器、容器组和 VM 组。

```
bluemix list [apps|containers|container-groups|vm-groups]
```

<strong>先决条件</strong>：端点、登录和目标

<strong>命令选项</strong>：
   <dl>
   <dt>apps（可选）</dt>
   <dd>仅显示应用程序信息。</dd>
   <dt>containers（可选）</dt>
   <dd>仅显示容器信息。</dd>
   <dt>container-groups（可选）</dt>
   <dd>仅显示容器组信息。</dd>
   <dt>vm-groups（可选）</dt>
   <dd>仅显示 VM 组信息。</dd>
    </dl>
对于 `apps`、`containers`、`container-groups` 或 `vm-groups`，一次只能指定其中一个选项。如果未指定其中任何选项，那么将列出所有 cf 应用程序、容器、容器组和 VM 组。

<strong>示例</strong>：

列出所有 cf 应用程序：

```
bluemix list apps
```

列出所有容器实例：

```
bluemix list containers
```

列出所有应用程序、容器、容器组和 VM 组：

```
bluemix list
```


## bluemix scale
{: #bluemix_scale}

将 cf 应用程序或容器组向内扩展或向外扩展到指定的实例计数、磁盘配额和内存大小。

**注：**扩展容器组时，只能指定实例数。如果未指定任何选项，此命令将列出容器组的当前实例计数，以及 cf 应用程序的磁盘配额和内存大小。

```
bluemix scale CF_APP_NAME|CONTAINER_GROUP_NAME [-i INSTANCE_COUNT] [-k DISK_QUOTA] [-m MEMORY_SIZE]
```

<strong>先决条件</strong>：端点、登录和目标

<strong>命令选项</strong>：
   <dl>
   <dt><i>CF_APP_NAME</i>|<i>CONTAINER_GROUP_NAME</i>（必需）</dt>
   <dd>要扩展的 cf 应用程序或容器组的名称。</dd>
   <dt>-i <i>INSTANCE_COUNT</i>（可选）</dt>
   <dd>要扩展的 cf 应用程序或容器组的新实例数。对于要扩展的容器组，此选项是唯一有效的选项。</dd>
   <dt>-k <i>DISK_QUOTA</i>（可选）</dt>
   <dd>cf 应用程序的新磁盘限额。对于扩展容器组无效。</dd>
   <dt>-m <i>MEMORY_SIZE</i>（可选）</dt>
   <dd>cf 应用程序的新内存大小。对于扩展容器组无效。</dd>
    </dl>
<strong>示例</strong>：

显示 `my-container-group` 的当前实例数：

```
bluemix scale my-container-group
```

将 `my-container-group` 扩展到 2 个实例：

```
bluemix scale my-container-group -i 2
```

将 `my-java-app` 扩展到 3 个实例、8G 磁盘配额和 1024M 内存大小：

```
bluemix scale my-java-app -i 3 -k 8G -m 1024M
```


## bluemix curl
{: #bluemix_curl}

执行针对 {{site.data.keyword.Bluemix_notm}} 的原始 HTTP 请求。缺省情况下，*Content-Type* 设置为 *application/json*。此命令会向 {{site.data.keyword.Bluemix_notm}} 多云控制代理发送请求。有关受支持的路径，请参阅 [Cloud Foundry API 文档](http://apidocs.cloudfoundry.org/){: new_window}中的 API 路径定义。

```
bluemix curl PATH [OPTIONS...]
```

<strong>先决条件</strong>：端点和登录

<strong>命令选项</strong>：
   <dl>
   <dt><i>PATH</i>（必需）</dt>
   <dd>资源的 URL 路径。例如，/v2/apps。</dd>
   <dt><i>OPTIONS</i>（可选）</dt>
   <dd>`bluemix curl` 命令支持的选项与 `cf curl` 命令支持的那些选项相同。</dd>
   </dl>

<strong>示例</strong>：

查看当前帐户的所有组织的信息：

```
bluemix curl /v2/organizations
```


## bluemix iam orgs
{: #bluemix_iam_orgs}

列出所有组织

```
bluemix iam orgs [-r REGION --guid]
```

<strong>先决条件</strong>：端点和登录

<strong>命令选项</strong>：
   <dl>
   <dt>-r <i>REGION</i>（可选）</dt>
   <dd>显示其组织信息的区域。如果设置为“all”，将列出所有区域中的所有组织。</dd>
   <dt>--guid（可选）</dt>
   <dd>显示组织的 GUID。</dd>
   </dl>

<strong>示例</strong>：

列出区域 `us-south` 中的所有组织并显示 GUID

```
bluemix iam orgs -r us-south --guid
```

## bluemix iam org
{: #bluemix_iam_org}

显示指定组织的信息。

```
bluemix iam org ORG_NAME [--guid]
```

<strong>先决条件</strong>：端点和登录

<strong>命令选项</strong>：
   <dl>
   <dt>ORG_NAME（必需）</dt>
   <dd>组织的名称。</dd>
   <dt>--guid（可选）</dt>
   <dd>显示组织的 GUID。</dd>
   </dl>

<strong>示例</strong>：

显示组织 `IBM` 的信息并显示 GUID

```
bluemix iam org IBM --guid
```

## bluemix iam org-create
{: #bluemix_iam_org_create}

创建新组织。此操作只能由帐户所有者执行。

```
bluemix iam org-create ORG_NAME
```

<strong>先决条件</strong>：端点和登录

<strong>命令选项</strong>：
   <dl>
   <dt>ORG_NAME（必需）</dt>
   <dd>要创建的组织的名称。</dd>
   </dl>
   
<strong>示例</strong>：

创建名为 `IBM` 的组织。

```
bluemix iam org-create IBM
```


## bluemix iam org-replicate
{: #bluemix_iam_org_replicate}

将组织从当前区域复制到其他区域。

```
bluemix iam org-replicate ORG_NAME REGION_NAME
```

<strong>先决条件</strong>：端点和登录

<strong>命令选项</strong>：
   <dl>
   <dt>ORG_NAME（必需）</dt>
   <dd>要复制的现有组织的名称。</dd>
   <dt>REGION_NAME（必需）</dt>
   <dd>托管所复制组织的区域的名称。</dd>
   </dl>

<strong>示例</strong>：

将组织 `myorg` 复制到区域 `eu-gb`：

```
bluemix iam org-replicate myorg eu-gb
```


## bluemix iam org-rename
{: #bluemix_iam_org_rename}

重命名组织。此操作只能由组织管理员执行。

```
bluemix iam org-rename OLD_ORG_NAME NEW_ORG_NAME
```

<strong>先决条件</strong>：端点和登录

<strong>命令选项</strong>：
   <dl>
   <dt>OLD_ORG_NAME（必需）</dt>
   <dd>要重命名的组织的旧名称。</dd>
   <dt>NEW_ORG_NAME（必需）</dt>
   <dd>组织要重命名为的新名称。</dd>
   </dl>

## bluemix iam org-delete
{: #bluemix_iam_org_delete}

删除当前区域中的指定组织。

```
bluemix iam org-delete ORG_NAME [-f --all]
```

<strong>先决条件</strong>：端点和登录

<strong>命令选项</strong>：
   <dl>
   <dt>ORG_NAME（必需）</dt>
   <dd>要删除的现有组织的名称。</dd>
   <dt>-f（可选）</dt>
   <dd>强制删除而不确认。</dd>
   <dt>--all（可选）</dt>
   <dd>从所有区域删除组织。</dd>
   </dl>


## bluemix iam spaces
{: #bluemix_iam_spaces}

此命令的功能和选项与 `cf spaces` 命令的相同。


## bluemix iam space
{: #bluemix_iam_space}

此命令的功能和选项与 `cf space` 命令的相同。


## bluemix iam space-create
{: #bluemix_iam_space_create}

此命令的功能和选项与 `cf create-space` 命令的相同。


## bluemix iam space-rename
{: #bluemix_iam_space_rename}


此命令的功能和选项与 `cf rename-space` 命令的相同。


## bluemix iam space-delete
{: #bluemix_iam_space_delete}


此命令的功能和选项与 `cf delete-space` 命令的相同。


## bluemix iam account-users
{: #bluemix_iam_account-users}

显示与帐户关联的用户。此操作只能由帐户所有者执行。

```
bluemix iam account-users
```

## bluemix iam account-user-invite
{: #bluemix_iam_account-user-invite}


邀请用户加入已设置组织和空间角色的帐户。此操作只能由帐户所有者执行。

```
bluemix iam account-user-invite USER_NAME ORG_NAME ORG_ROLE SPACE_NAME SPACE_ROLE
```

<strong>先决条件</strong>：端点和登录


<strong>命令选项</strong>：

   <dl>
   <dt>USER_NAME（必需）</dt>
   <dd>要邀请的用户的名称。</dd>
   <dt>ORG_NAME（必需）</dt>
   <dd>要邀请此用户加入的组织的名称。</dd>
   <dt>ORG_ROLE（必需）</dt>
   <dd>要邀请此用户加入的组织角色的名称。例如：
<ul>
  <li>OrgManager：此角色可以邀请和管理用户，选择并更改套餐，以及设置花费限制。</li>
  <li>BillingManager：此角色可以创建和管理缴费帐户和付款信息。</li>
  <li>OrgAuditor：此角色具有对组织信息和报告的只读访问权。</li>
  </ul> </dd>
   <dt>SPACE_NAME（必需）</dt>
   <dd>要邀请此用户加入的空间的名称。</dd>
   <dt>SPACE_ROLE（必需）</dt>
   <dd>要邀请此用户加入的空间的名称。要邀请此用户加入的空间角色的名称。例如：
<ul>
<li>SpaceManager：此角色可以邀请和管理用户，以及启用给定空间的功能。</li>
<li>SpaceDeveloper：此角色可以创建和管理应用程序与服务，以及查看日志和报告。</li>
<li>SpaceAuditor：此角色可以查看空间的日志、报告和设置。</li>
</ul>
</dd>
</dl>

<strong>示例</strong>：

邀请用户 `Mary` 以 `OrgManager` 角色加入组织 `IBM`，并以 `SpaceAuditor` 角色加入空间 `Cloud`：

```
bluemix iam account-user-invite Mary IBM OrgManager Cloud SpaceAuditor
```

## bluemix iam org-users
{: #bluemix_iam_org_users}

按角色显示指定组织中的用户。

```
bluemix iam org-users ORG_NAME [-a]
```

<strong>先决条件</strong>：端点和登录

<strong>命令选项</strong>：
   <dl>
   <dt>ORG_NAME（必需）</dt>
   <dd>组织的名称。</dd>
   <dt>-a（可选）</dt>
   <dd>列出指定组织中的所有用户，但不按角色分组。</dd>
    </dl>


## bluemix iam org-role-set
{: #bluemix_iam_org_role_set}

向用户分配组织角色。此操作只能由组织管理员执行。

```
bluemix iam org-role-set USER_NAME ORG_NAME ORG_ROLE
```

<strong>先决条件</strong>：端点和登录

<strong>命令选项</strong>：


   <dl>
   <dt>USER_NAME（必需）</dt>
   <dd>要分配的用户的名称。</dd>
   <dt>ORG_NAME（必需）</dt>
   <dd>要将此用户分配到的组织的名称。</dd>
   <dt>ORG_ROLE（必需）</dt>
   <dd>要将此用户分配到的组织角色的名称。例如：
<ul>
   <li>OrgManager：此角色可以邀请和管理用户，选择并更改套餐，以及设置花费限制。</li>
   <li>BillingManager：此角色可以创建和管理缴费帐户和付款信息。</li>
   <li>OrgAuditor：此角色具有对组织信息和报告的只读访问权。</li>
   </ul>
   </dd>
    </dl>

<strong>示例</strong>：

将用户 `Mary` 以 `OrgManager` 角色分配给组织 `IBM`：

```
bluemix iam org-role-set Mary IBM OrgManager
```


## bluemix iam org-role-unset
{: #bluemix_iam_org_role_unset}

除去用户的组织角色。此操作只能由组织管理员执行。

```
bluemix iam org-role-unset USER_NAME ORG_NAME ORG_ROLE
```

<strong>先决条件</strong>：端点和登录

<strong>命令选项</strong>：
   <dl>
   <dt>USER_NAME（必需）</dt>
   <dd>要除去的用户的名称。</dd>
   <dt>ORG_NAME（必需）</dt>
   <dd>要将此用户从中除去的组织的名称。</dd>
   <dt>ORG_ROLE（必需）</dt>
   <dd>要将此用户从中除去的组织角色的名称。例如：
<ul>
   <li>OrgManager：此角色可以邀请和管理用户，选择并更改套餐，以及设置花费限制。</li>
   <li>BillingManager：此角色可以创建和管理缴费帐户和付款信息。</li>
   <li>OrgAuditor：此角色具有对组织信息和报告的只读访问权。</li>
   </ul>
   </dd>
    </dl>

<strong>示例</strong>：

从组织 `IBM` 中除去用户 `Mary` 的 `OrgManager` 角色：

```
bluemix iam org-role-unset Mary IBM OrgManager
```


## bluemix iam space-users
{: #bluemix_iam_space_users}

按角色显示指定空间中的用户。

```
bluemix iam space-users ORG_NAME SPACE_NAME
```

<strong>先决条件</strong>：端点和登录

<strong>命令选项</strong>：
   <dl>
   <dt>ORG_NAME（必需）</dt>
   <dd>组织的名称。</dd>
   <dt>SPACE_NAME（必需）</dt>
   <dd>空间的名称。</dd>
   </dl>


## bluemix iam space-role-set
{: #bluemix_iam_space_role_set}

向用户分配空间角色。此操作只能由空间管理员执行。

```
bluemix iam space-role-set USER_NAME ORG_NAME SPACE_NAME SPACE_ROLE
```

<strong>先决条件</strong>：端点和登录

<strong>命令选项</strong>：

   <dl>
   <dt>USER_NAME（必需）</dt>
   <dd>要分配的用户的名称。</dd>
   <dt>ORG_NAME（必需）</dt>
   <dd>要将此用户分配到的组织的名称。</dd>
   <dt>SPACE_NAME（必需）</dt>
   <dd>要将此用户分配到的空间的名称。</dd>
   <dt>SPACE_ROLE（必需）</dt>
   <dd>要将此用户分配到的空间角色的名称。例如：
<ul>
   <li>SpaceManager：此角色可以邀请和管理用户，以及启用给定空间的功能。</li>
   <li>SpaceDeveloper：此角色可以创建和管理应用程序与服务，以及查看日志和报告。</li>
   <li>SpaceAuditor：此角色可以查看空间的日志、报告和设置。</li>
   </ul></dd>
    </dl>

<strong>示例</strong>：

将用户 `Mary` 以 `SpaceManager` 角色分配给组织 `IBM` 和空间 `Cloud`：

```
bluemix iam space-role-set Mary IBM Cloud SpaceManager
```

## bluemix iam space-role-unset
{: #bluemix_iam_space_role_unset}

除去用户的空间角色。此操作只能由空间管理员执行。

```
bluemix iam space-role-unset USER_NAME ORG_NAME SPACE_NAME SPACE_ROLE
```

<strong>先决条件</strong>：端点和登录

<strong>命令选项</strong>：

   <dl>
   <dt>USER_NAME（必需）</dt>
   <dd>要除去的用户的名称。</dd>
   <dt>ORG_NAME（必需）</dt>
   <dd>要将此用户从中除去的组织的名称。</dd>
   <dt>SPACE_NAME（必需）</dt>
   <dd>要将此用户从中除去的空间的名称。</dd>
   <dt>SPACE_ROLE（必需）</dt>
   <dd>要将此用户从中除去的空间角色的名称。例如：
<ul>
   <li>SpaceManager：此角色可以邀请和管理用户，以及启用给定空间的功能。</li>
   <li>SpaceDeveloper：此角色可以创建和管理应用程序与服务，以及查看日志和报告。</li>
   <li>SpaceAuditor：此角色可以查看空间的日志、报告和设置。</li>
   </ul></dd>
    </dl>


<strong>示例</strong>：

从组织 `IBM` 和空间 `Cloud` 中除去用户 `Mary` 的 `SpaceManager` 角色：

```
bluemix iam space-role-unset Mary IBM Cloud SpaceManager
```


## bluemix app push
{: #bluemix_app_push}

此命令的功能和选项与 `cf push` 命令的相同。


## bluemix app list
{: #bluemix_app_list}

此命令的功能和选项与 `cf apps` 命令的相同。


## bluemix app show
{: #bluemix_app_show}

此命令的功能和选项与 `cf app` 命令的相同。


## bluemix app scale
{: #bluemix_app_scale}

此命令的功能和选项与 `cf scale` 命令的相同。


## bluemix app delete
{: #bluemix_app_delete}

此命令的功能和选项与 `cf delete` 命令的相同。


## bluemix app rename
{: #bluemix_app_rename}

此命令的功能和选项与 `cf rename` 命令的相同。


## bluemix app start
{: #bluemix_app_start}

此命令的功能和选项与 `cf start` 命令的相同。


## bluemix app stop
{: #bluemix_app_stop}

此命令的功能和选项与 `cf stop` 命令的相同。


## bluemix app restart
{: #bluemix_app_restart}

此命令的功能和选项与 `cf restart` 命令的相同。


## bluemix app restage
{: #bluemix_app_restage}


此命令的功能和选项与 `cf restage` 命令的相同。


## bluemix app instance-restart
{: #bluemix_app_instance_restart}


此命令的功能和选项与 `cf restart-app-instance` 命令的相同。


## bluemix app events
{: #bluemix_app_events}

此命令的功能和选项与 `cf events` 命令的相同。


## bluemix app files
{: #bluemix_app_files}

此命令的功能和选项与 `cf files` 命令的相同。


## bluemix app logs
{: #bluemix_app_logs}

此命令的功能和选项与 `cf logs` 命令的相同。


## bluemix app env
{: #bluemix_app_env}

此命令的功能和选项与 `cf env` 命令的相同。


## bluemix app env-set
{: #bluemix_app_env_set}

此命令的功能和选项与 `cf set-env` 命令的相同。


## bluemix app env-unset
{: #bluemix_app_env_unset}

此命令的功能和选项与 `cf unset-env` 命令的相同。


## bluemix app stacks
{: #bluemix_app_stacks}

此命令的功能和选项与 `cf stacks` 命令的相同。


## bluemix app stack
{: #bluemix_app_stack}

此命令的功能和选项与 `cf stack` 命令的相同。


## bluemix app manifest-create
{: #bluemix_app_manifest_create}

此命令的功能和选项与 `cf create-app-manifest` 命令的相同。


## bluemix service offerings
{: #bluemix_service_offerings}


此命令的功能和选项与 `cf marketplace` 命令的相同。


## bluemix service list
{: #bluemix_service_list}

此命令的功能和选项与 `cf services` 命令的相同。


## bluemix service show
{: #bluemix_service_show}

此命令的功能和选项与 `cf service` 命令的相同。


## bluemix service create
{: #bluemix_service_create}

此命令的功能和选项与 `cf create-service` 命令的相同。


## bluemix service update
{: #bluemix_service_update}

此命令的功能和选项与 `cf update-service` 命令的相同。


## bluemix service delete
{: #bluemix_service_delete}

此命令的功能和选项与 `cf delete-service` 命令的相同。


## bluemix service rename
{: #bluemix_service_rename}

此命令的功能和选项与 `cf rename-service` 命令的相同。


## bluemix service bind
{: #bluemix_service_bind}

此命令的功能和选项与 `cf bind-service` 命令的相同。


## bluemix service unbind
{: #bluemix_service_unbind}

此命令的功能和选项与 `cf unbind-service` 命令的相同。


## bluemix service key-create
{: #bluemix_service_key_create}

此命令的功能和选项与 `cf create-service-key` 命令的相同。


## bluemix service key-delete
{: #bluemix_service_key_delete}

此命令的功能和选项与 `cf delete-service-key` 命令的相同。


## bluemix service keys
{: #bluemix_service_keys}

此命令的功能和选项与 `cf service-keys` 命令的相同。


## bluemix service key-show
{: #bluemix_service_key_show}

此命令的功能和选项与 `cf service-key` 命令的相同。


## bluemix service user-provided-create
{: #bluemix_service_user_provided_create}

此命令的功能和选项与 `cf create-user-provided-service` 命令的相同。


## bluemix service user-provided-update
{: #bluemix_service_user_provided_update}

此命令的功能和选项与 `cf update-user-provided-service` 命令的相同。


## bluemix catalog templates
{: #bluemix_catalog_templates}

查看 Bluemix 上的样板模板。

```
bluemix catalog templates [-d]
```

<strong>先决条件</strong>：端点和登录

<strong>命令选项</strong>：

   <dl>
   <dt>-d（可选）</dt>
   <dd>如果指定了 <i>-d</i> 选项，那么还会显示每个模板的描述。否则，只显示每个模板的标识和名称。</dd>
   </dl>


## bluemix catalog template
{: #bluemix_catalog_template}

查看指定样板模板的详细信息。

```
bluemix catalog template TEMPLATE_ID
```

<strong>先决条件</strong>：端点和登录

<strong>命令选项</strong>：
   <dl>
   <dt>TEMPLATE_ID（必需）</dt>
   <dd>样板模板的标识。使用 <i>bluemix templates</i> 可查看所有模板的标识。</dd>
   </dl>


<strong>示例</strong>：

查看模板 `mobileBackendStarter` 的详细信息：

```
bluemix catalog template mobileBackendStarter
```


## bluemix catalog template-run
{: #bluemix_catalog_template_run}

使用指定 URL 和描述基于指定模板创建 cf 应用程序。缺省情况下，新应用程序将自动启动。

```
bluemix catalog template-run TEMPLATE_ID CF_APP_NAME [-u URL] [-d DESCRIPTION] [--no-start]
```

<strong>先决条件</strong>：端点、登录和目标

<strong>命令选项</strong>：
   <dl>
   <dt>TEMPLATE_ID（必需）</dt>
   <dd>创建应用程序时将基于的模板。使用 <i>bluemix templates</i> 可查看所有模板的标识。</dd>
   <dt>CF_APP_NAME（必需）</dt>
   <dd>要创建的 cf 应用程序的名称。</dd>
   <dt>-u <i>URL</i>（可选）</dt>
   <dd>应用程序的路径。如果未指定，Bluemix 将基于应用程序名称和缺省域自动设置路径。</dd>
   <dt>-d <i>DESCRIPTION</i>（可选）</dt>
   <dd>应用程序的描述。</dd>
   <dt>--no-start（可选）</dt>
   <dd>应用程序创建后不自动启动。如果未指定，应用程序创建后将自动启动。</dd>
   </dl>


<strong>示例</strong>：

基于 `javaHelloWorld` 模板创建 cf 应用程序 `my-app`：

```
bluemix catalog template-run javaHelloWorld my-app
```

基于 `rubyHelloWorld` 模板创建应用程序 `my-ruby-app`，路径为 `myrubyapp.chinabluemix.net`，描述为 `My first ruby app on {{site.data.keyword.Bluemix_notm}}.`：

```
bluemix catalog template-run rubyHelloWorld my-ruby-app -u myrubyapp.chinabluemix.net -d "My first ruby app on {{site.data.keyword.Bluemix_notm}}."
```

基于 `pythonHelloWorld` 模板创建应用程序 `my-python-app`，不带自动启动：

```
bluemix catalog template-run pythonHelloWorld my-python-app --no-start
```


## bluemix network regions
{: #bluemix_network_regions}

查看 {{site.data.keyword.Bluemix_notm}} 上所有区域的信息。

```
bluemix network regions
```

<strong>先决条件</strong>：端点


## bluemix network region-set
{: #bluemix_network_region_set}

切换到指定的区域。此命令会自动重定向到新区域中的相同组织和空间（如果可能）。如果用户已登录，该命令会提示用户选择新的组织和空间。API 端点会相应地更改。

```
bluemix network region-set REGION_NAME
```

<strong>先决条件</strong>：端点

<strong>命令选项</strong>：

   <dl>
   <dt>REGION_NAME（必需）</dt>
   <dd>您要切换到的区域的名称。可以使用 <i>bluemix network regions</i> 命令来查看所有区域名称。</dd>
    </dl>

<strong>示例</strong>：

将当前区域设置为 `eu-gb`：

```
bluemix network region-set eu-gb
```


## bluemix network routes
{: #bluemix_network_routes}

此命令的功能和选项与 `cf routes` 命令的相同。


## bluemix network route-check
{: #bluemix_network_route_check}

此命令的功能和选项与 `cf check-route` 命令的相同。


## bluemix network route-map
{: #bluemix_network_route_map}

将路径映射到具有指定域和主机名的现有 cf 应用程序或容器组。

```
bluemix network route-map CF_APP_NAME|CONTAINER_GROUP_NAME  DOMAIN  [-n HOST_NAME]
```

<strong>先决条件</strong>：端点、登录和目标

<strong>命令选项</strong>：

   <dl>
   <dt>CF_APP_NAME|CONTAINER_GROUP_NAME（必需）</dt>
   <dd>要使用路径映射到的 cf 应用程序或容器组的名称。</dd>
   <dt>DOMAIN（必需）</dt>
   <dd>路径的域。例如，mychinabluemix.net 或 chinabluemix.net。</dd>
   <dt>-n <i>HOST_NAME</i>（可选）</dt>
   <dd>路径的主机名。如果未提供，缺省情况下主机名将设置为应用程序名称或容器组名称。</dd>
   </dl>

<strong>示例</strong>：

使用指定的域将路径映射到 `my-app`：

```
bluemix network route-map my-app mychinabluemix.net
```

使用指定域和主机名将路径映射到“my-container-group”：

```
bluemix network route-map my-container-group chinabluemix.net -n abc
```


## bluemix network route-unmap
{: #bluemix_network_route_unmap}

取消来自现有 cf 应用程序或容器组中的指定路径映射。

```
bluemix network route-unmap CF_APP_NAME|CONTAINER_GROUP_NAME  DOMAIN  [-n HOST_NAME]
```

<strong>先决条件</strong>：端点、登录和目标

<strong>命令选项</strong>：

   <dl>
   <dt>CF_APP_NAME|CONTAINER_GROUP_NAME（必需）</dt>
   <dd>cf 应用程序或容器组的名称。</dd>
   <dt>DOMAIN（必需）</dt>
   <dd>路径的域（例如，mychinabluemix.net 或 chinabluemix.net）。</dd>
   <dt>-n <i>HOST_NAME</i>（可选）</dt>
   <dd>路径的主机名。如果未提供，缺省情况下主机名将设置为应用程序名称或容器组名称。</dd>
   </dl>

<strong>示例</strong>：

从 `my-app` 取消 `my-app.mychinabluemix.net` 的映射：

```
bluemix network route-unmap my-app mychianbluemix.net
```

从 `my-container-group` 取消 `abc.chinabluexmix.net` 的映射：

```
bluemix network route-unmap my-container-group chinabluemix.net -n abc
```


## bluemix network route-create
{: #bluemix_network_route_create}

此命令的功能和选项与 `cf create-route` 命令的相同。


## bluemix network route-delete
{: #bluemix_network_route_delete}

此命令的功能和选项与 `cf delete-route` 命令的相同。


## bluemix network orphaned-routes-delete
{: #bluemix_network_orphaned_routes_delete}

此命令的功能和选项与 `cf delete-orphaned-routes` 命令的相同。


## bluemix network domains
{: #bluemix_network_domains}

此命令的功能和选项与 `cf domains` 命令的相同。


## bluemix network domain-create
{: #bluemix_network_domain_create}

此命令的功能和选项与 `cf create-domain` 命令的相同。


## bluemix network domain-delete
{: #bluemix_network_domain_delete}

此命令的功能和选项与 `cf delete-domain` 命令的相同。


## bluemix network shared-domain-create
{: #bluemix_network_shared_domain_create}

此命令的功能和选项与 `cf create-shared-domain` 命令的相同。


## bluemix network shared-domain-delete
{: #bluemix_network_shared_domain_delete}

此命令的功能和选项与 `cf delete-shared-domain` 命令的相同。



## bluemix bss account-usage
{: #bluemix_bss_account_usage}

显示帐户的每月使用情况和成本。

```
bluemix bss account-usage [-d YYYY-MM] [--json]
```

<strong>先决条件</strong>：端点和登录

<strong>命令选项</strong>：

<dl>
  <dt>-d MONTH_DATE（可选）</dt>
  <dd>显示使用 YYYY-MM 格式指定的月份和日期的数据。如果未指定，那么会显示当月的使用情况。</dd>
  <dt>--json（可选）</dt>
  <dd>以 JSON 格式显示使用情况结果。</dd>
</dl>

<strong>示例</strong>：

显示 2016 年 6 月我的帐户的使用情况和成本报告：

```
bluemix bss account-usage -d 2016-06
```

## bluemix bss org-usage
{: #bluemix_bss_org_usage}

显示组织的每月使用情况详细信息。此操作只能由组织的记帐管理员执行。

```
bluemix bss org-usage ORG_NAME [-d YYYY-MM] [-r REGION_NAME] [--json]
```

<strong>先决条件</strong>：端点和登录

<strong>命令选项</strong>：

<dl>
  <dt>ORG_NAME（必需）</dt>
  <dd>组织的名称。</dd>
  <dt>-d MONTH_DATE（可选）</dt>
  <dd>显示使用 YYYY-MM 格式指定的月份和日期的数据。如果未指定，那么会显示当月的使用情况。</dd>
  <dt>-r REGION_NAME</dt>
  <dd>托管组织的区域的名称。如果设置为“all”，那么会显示所有区域中的组织使用情况。</dd>
  <dt>--json（可选）</dt>
  <dd>以 JSON 格式显示使用情况结果。</dd>
</dl>



## bluemix bss orgs-usage-summary
{: #bluemix_bss_orgs_usage_summary}

显示我的帐户中组织的每月使用情况摘要。

```
bluemix bss orgs-usage-summary [-d YYYY-MM] [-r REGION_NAME] [--json]
```

<strong>先决条件</strong>：端点和登录

<strong>命令选项</strong>：

<dl>
  <dt>-d MONTH_DATE（可选）</dt>
  <dd>显示使用 YYYY-MM 格式指定的月份和日期的数据。如果未指定，那么会显示当月的使用情况。</dd>
  <dt>-r REGION_NAME</dt>
  <dd>托管组织的区域的名称。如果设置为“all”，那么会显示所有区域中组织的使用情况摘要。</dd>
  <dt>--json（可选）</dt>
  <dd>以 JSON 格式显示使用情况结果。</dd>
</dl>



## bluemix security cert
{: #bluemix_security_cert}

列出域的证书信息。

```
bluemix security cert DOMAIN_NAME
```

<strong>先决条件</strong>：端点和登录

<strong>命令选项</strong>：
   
   <dl>
   <dt>DOMAIN_NAME（必需）</dt>
   <dd>托管证书的域。</dd>
   </dl>



<strong>示例</strong>：

查看域 `ibmcxo-eventconnect.com` 的证书信息：

```
bluemix security cert ibmcxo-eventconnect.com
```


## bluemix security cert-add
{: #bluemix_security_cert_add}

将证书添加到当前组织中的指定域。

```
bluemix security cert-add DOMAIN -k PRIVATE_KEY_FILE -c CERT_FILE [-p PASSWORD] [-i INTERMEDIATE_CERT_FILE] [--verify-client]
```

<strong>先决条件</strong>：端点、登录和目标

<strong>命令选项</strong>：
   <dl>
   <dt>DOMAIN（必需）</dt>
   <dd>将证书添加到其中的域。</dd>
   <dt>-k <i>PRIVATE_KEY_FILE</i>（必需）</dt>
   <dd>专用密钥文件路径。</dd>
   <dt>-c <i>CERT_FILE</i>（必需）</dt>
   <dd>证书文件路径。</dd>
   <dt>-p <i>PASSWORD</i>（可选）</dt>
   <dd>证书的密码。</dd>
   <dt>-i <i>INTERMEDIATE_CERT_FILE</i>（可选）</dt>
   <dd>中间证书文件路径。</dd>
   <dt>--verify-client（可选）</dt>
   <dd>是否启用客户机证书验证。</dd>
   </dl>


<strong>示例</strong>：

将证书添加到域 `ibmcxo-eventconnect.com`：

```
bluemix security cert-add ibmcxo-eventconnect.com -k key_file.key -c cert_file.crt -p 123 -i inter_cert.cert
```


## bluemix security cert-remove
{: #bluemix_security_cert_remove}

从当前组织中的指定域除去证书。

```
bluemix security cert-remove DOMAIN [-f]
```

<strong>先决条件</strong>：端点、登录和目标

<strong>命令选项</strong>：

   <dl>
   <dt>DOMAIN（必需）</dt>
   <dd>要从中除去证书的域。</dd>
   <dt>-f（可选）</dt>
   <dd>强制删除而不确认。</dd>
   </dl>



## bluemix plugin repos
{: #bluemix_plugin_repos}

列出 {{site.data.keyword.Bluemix_notm}} CLI 中注册的所有插件存储库。

```
bluemix plugin repos
```

<strong>先决条件</strong>：无


## bluemix plugin repo-add
{: #bluemix_plugin_repo_add}

将新的插件存储库添加到 {{site.data.keyword.Bluemix_notm}} CLI 中。

```
bluemix plugin repo-add REPO_NAME REPO_URL
```

<strong>先决条件</strong>：无

<strong>命令选项</strong>：

   <dl>
   <dt>REPO_NAME（必需）</dt>
   <dd>要添加的存储库的名称。可以为每个存储库定义您自己的名称。</dd>
   <dt>REPO_URL（必需）</dt>
   <dd>要添加的存储库的 URL。存储库 URL 必须包含协议（例如，http://plugins.ng.bluemix.net，而不是 plugins.ng.bluemix.net）。http://plugins.ng.bluemix.net 是 Bluemix CLI 的官方插件存储库。</dd>
    </dl>


<strong>示例</strong>：

将 Bluemix CLI 的官方插件存储库添加为 `bluemix-repo`：

```
bluemix plugin repo-add bluemix-repo http://plugins.ng.bluemix.net
```


## bluemix plugin repo-remove
{: #bluemix_plugin_repo_remove}

从 {{site.data.keyword.Bluemix_notm}} CLI 中除去插件存储库。

```
bluemix plugin repo-remove REPO_NAME
```

<strong>先决条件</strong>：无

<strong>命令选项</strong>：
   <dl>
   <dt>REPO_NAME（必需）</dt>
   <dd>要除去的存储库的名称。</dd>
   </dl>

<strong>示例</strong>：

从 {{site.data.keyword.Bluemix_notm}} CLI 中除去 `bluemix-repo` 存储库：

```
bluemix plugin repo-remove bluemix-repo
```


## bluemix plugin repo-plugins
{: #bluemix_plugin_repo_plugins}

列出所有添加的存储库或特定存储库中的所有可用插件。

```
bluemix plugin repo-plugins [-r REPO_NAME]
```

<strong>先决条件</strong>：无

<strong>命令选项</strong>：

   <dl>
   <dt>-r <i>REPO_NAME</i>（可选）</dt>
   <dd>仅列出指定存储库中的插件。</dd>
   </dl>

<strong>示例</strong>：

列出所有添加的存储库中的所有插件：

```
bluemix plugin repo-plugins
```

列出 `bluemix-repo` 存储库中的所有插件：

```
bluemix plugin repo-plugins -r bluemix-repo
```


## bluemix plugin list
{: #bluemix_plugin_list}

列出 {{site.data.keyword.Bluemix_notm}} CLI 中的所有已安装插件。

```
bluemix plugin list
```

<strong>先决条件</strong>：无


## bluemix plugin install
{: #bluemix_plugin_install}

从指定的路径或存储库将特定版本的插件安装到 {{site.data.keyword.Bluemix_notm}} CLI 中。

```
bluemix plugin install PLUGIN_PATH|PLUGIN_NAME [-r REPO_NAME] [-v VERSION]
```

<strong>先决条件</strong>：无

<strong>命令选项</strong>：

   <dl>
   <dt>PLUGIN_PATH|PLUGIN_NAME（必需）</dt>
   <dd>如果未指定 -r <i>REPO_NAME</i>，那么将从指定的本地路径或远程 URL 安装插件。</dd>
   <dt>-r <i>REPO_NAME</i>（可选）</dt>
   <dd>插件二进制文件所在的存储库的名称。</dd>
   <dt>-v <i>VERSION</i>（可选）</dt>
   <dd>要安装的插件的版本。如果未提供，将安装插件的最新版本。此选项仅对从存储库安装插件有效。</dd>
    </dl>

<strong>示例</strong>：

从本地文件安装插件：

```
bluemix plugin install /downloads/new_plugin
```

从远程 URL 安装插件：

```
bluemix plugin install http://plugins.ng.bluemix.net/downloads/new_plugin
```

从 `bluemix-repo` 存储库安装最新版本的 `IBM-Containers` 插件：

```
bluemix plugin install IBM-Containers -r bluemix-repo
```
从 `bluemix-repo` 存储库安装版本为 `0.5.800` 的 `IBM-Containers` 插件：

```
bluemix plugin install IBM-Containers -r bluemix-repo -v 0.5.800
```






## bluemix plugin uninstall
{: #bluemix_plugin_uninstall}

从 {{site.data.keyword.Bluemix_notm}} CLI 中卸载指定的插件。

```
bluemix plugin uninstall PLUGIN_NAME
```

<strong>先决条件</strong>：无

<strong>命令选项</strong>：

   <dl>
   <dt>PLUGIN_NAME（必需）</dt>
   <dd>要卸载的插件的名称。</dd>
    </dl>

<strong>示例</strong>：

卸载先前安装的 `IBM-Containers` 插件：

```
bluemix plugin uninstall IBM-Containers
```









# 相关链接
{: #rellinks}

## 相关链接
{: #general}

* [bx 工具](http://clis.ng.bluemix.net/ui/home.html){:new_window}

