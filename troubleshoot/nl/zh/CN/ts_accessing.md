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



# 有关访问 {{site.data.keyword.Bluemix_notm}} 的故障诊断 
{: #accessing}

上次更新时间：2016 年 9 月 13 日
{: .last-updated} 

访问 {{site.data.keyword.Bluemix_notm}} 的一般性问题可能包括用户无法登录到 {{site.data.keyword.Bluemix_notm}} 和帐户困于暂挂状态等。然而，在许多情况下，只需执行几个简单的步骤即可解决这些问题。
{:shortdesc}




<!-- begin STAGING ONLY --> 

## 访问外部 Web 站点时发生问题
{: #ts_bmlinkid}

您无法使用 IBM 内部网标识登录到 {{site.data.keyword.Bluemix_notm}}，除非您将内部网标识与 IBM 标识链接到一起。


从 {{site.data.keyword.Bluemix_notm}}“登录”页面选择**使用内部网标识登录**之后，可能会看到以下错误消息：
{: tsSymptoms} 

`访问外部 Web 站点时发生问题`



当您使用未与 IBM 标识相链接的 IBM 内部网标识登录到 {{site.data.keyword.Bluemix_notm}} 时会发生此问题。IBM 标识是用于登录 www.ibm.com 的标识。
{: tsCauses}


作为 IBM 员工，您必须将 IBM 内部网标识与外部 IBM 标识相链接，才能使用内部网标识登录到 {{site.data.keyword.Bluemix_notm}}。要链接这两个标识，请完成以下步骤：
{: tsResolve} 

  1. 在[中央登录](https://w3-03.sso.ibm.com/tools/cso/index.jsp){: new_window}页面中，单击**我的登录**。
  2. 在“我的登录”页面上，单击**链接标识**，然后在 {{site.data.keyword.Bluemix_notm}}“登录”页面上输入 IBM 标识和密码。之后，内部网标识与 IBM 标识即会自动链接在一起。
  

<!-- end STAGING ONLY -->




## 您有未保存的更改
{: #ts_unsaved_changes}


在应用程序详细信息页面上进行浏览时，可能无法执行任何操作，系统可能会提示您保存更改后才能继续。 


在应用程序详细信息页面上尝试检查应用程序或服务时，总是提示以下错误消息：
{: tsSymptoms} 

`您在页面 app_name 中有未保存的更改。请保存或取消这些更改。`


在运行时窗格中的**实例**或**内存配额**字段上滚动鼠标时，值会更改。这是故意这样设计的；但是，当您要离开该页面时，会有错误消息提示您保存内存或实例设置。
{: tsCauses}


关闭消息窗口，然后单击运行时窗格中的**重置**按钮。
{: tsResolve} 









## 无法向组织添加用户
{: #ts_adduser}

您可以邀请多个用户在同一组织下工作。只有帐户所有者或组织管理员兼组织成员，才能邀请用户加入组织。
 

在**管理组织**部分中看不到**邀请新用户**链接。 
{: tsSymptoms}

 

只有以下 {{site.data.keyword.Bluemix_notm}} 用户才能邀请用户加入组织：
{: tsCauses}
  * 组织的帐户所有者
  * 组织管理员兼组织成员，而不是组织的合作者
  
在 {{site.data.keyword.Bluemix_notm}} 中，您可以是组织的成员，也可以是组织的合作者：

<dl><dt>合作者</dt>
<dd>如果您已有 {{site.data.keyword.Bluemix_notm}} 帐户，并且有其他人邀请您加入组织，那么您就是组织的合作者。</dd>
<dt>成员</dt>
<dd>如果您没有 {{site.data.keyword.Bluemix_notm}} 帐户，但有人邀请您加入组织，并且您通过邀请注册了 {{site.data.keyword.Bluemix_notm}}，那么您就是组织的成员。</dd>
</dl>


如果您是组织的合作者，即使被指定为组织管理员，也不能邀请用户加入组织。

**注：**所有组织管理员（包括组织的合作者）都可以添加、修改和除去组织中的已有用户。

 

如果您无法邀请用户加入组织，并需要其他角色来完成此操作，请联系组织管理员来更改您的角色。要识别组织管理员，请完成以下步骤：
{: tsResolve}

  1. 转至 {{site.data.keyword.Bluemix_notm}}“仪表板”，单击菜单栏中的 {{site.data.keyword.avatar}} 图标 ![Avatar 图标](images/account_support.svg) ，然后选择**管理组织**。
  2. 转至您的组织，并查看**用户**选项卡上的组织管理员信息。  
  
如果由于您是合作者（并非成员）而无法邀请用户，那么您必须删除您先前的 {{site.data.keyword.Bluemix_notm}} 帐户，然后被邀请以组织成员身份加入帐户。要删除您先前的帐户并以成员身份加入帐户，请完成以下步骤： 

  1. 转至 [Bluemix 支持凭单系统](https://chinabluemix.itsm.unisysedge.cn/){: new_window}页面，以提交一个支持凭单，请求删除您的帐户。如果存在与旧帐户相关联的数据并且想要将其保存并移动到新帐户，请在您的电子邮件中包含此信息。 
  2. 在您的帐户被删除后，让具有组织管理员角色的用户以组织管理员身份邀请您加入组织。然后，通过邀请注册 {{site.data.keyword.Bluemix_notm}}。 




## 不支持用户批量注册
{: #ts_batchregistration}

在对 {{site.data.keyword.Bluemix_notm}} 注册用户时，必须单独注册每个用户。
 

{{site.data.keyword.Bluemix_notm}} 不提供同时注册多个用户的功能。
{: tsSymptoms}
 

{{site.data.keyword.Bluemix_notm}} 不支持用户批量注册。要对 {{site.data.keyword.Bluemix_notm}} 注册用户，必须单独注册每个用户。
{: tsCauses}
 

要对 {{site.data.keyword.Bluemix_notm}} 注册多个用户，必须为每个用户完成以下步骤：
{: tsResolve}

  1. 在 {{site.data.keyword.Bluemix_notm}} 用户界面中单击**注册**。
  2. 按照向导的提示完成每个步骤。

    

## 无法装入 {{site.data.keyword.Bluemix_notm}} 页面
{: #ts_err}

在使用 {{site.data.keyword.Bluemix_notm}} 用户界面时，您可能无法装入 {{site.data.keyword.Bluemix_notm}} 页面。相反，您可能会看到错误消息 BXNUI0001E 或 BXNUI0016E。
 

在使用 {{site.data.keyword.Bluemix_notm}} 用户界面时，您可能看到以下一条错误消息：
{: tsSymptoms}

`BXNUI0001E: 未装入页面，因为 Bluemix 未检测到是否存在会话。`


`BXNUI0016E: 未检索到应用程序和服务，因为未装入 Bluemix 页面。`

 

您可以根据需要完成以下一个或多个操作：
{: tsResolve}

  * 刷新或重新启动浏览器。
  * 注销 {{site.data.keyword.Bluemix_notm}}，并重新登录。
  * 使用浏览器的隐私浏览模式。 
  * 清除浏览器的 cookie 和高速缓存。
  * 使用其他浏览器。有关 {{site.data.keyword.Bluemix_notm}} 支持的浏览器版本的信息，请参阅 [{{site.data.keyword.Bluemix_notm}} 先决条件](https://developer.ibm.com/bluemix/support/#prereqs){: new_window}。
  * 如果安装了 cf 命令行界面，请输入 `cf apps` 命令以查看应用程序是否正在运行。
  
  
  
  
  

