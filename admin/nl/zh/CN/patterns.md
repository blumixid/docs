---



copyright:

  years: 2015, 2016



---

{:new_window: target="_blank"} 
{:shortdesc: .shortdesc} 
{:screen:.screen} 
{:codeblock:.codeblock}

# 设计云环境
{: #patterns}
上次更新时间：2016 年 6 月 15 日
{: .last-updated}

设计混合云解决方案时，必须考虑安全和操作需求、国家或地区规范、市场监管指令以及公司政策。{{site.data.keyword.Bluemix_notm}} 是一种开放标准的云平台，用于构建、运行和管理应用程序和服务；该平台提供了三种类型的云环境，帮助您构造混合云环境：
* [{{site.data.keyword.Bluemix_notm}} Public](../public/index.html#public "{{site.data.keyword.Bluemix_notm}} Public") 是一种由不同公司和用户共享基础架构资源的云环境。 
* [{{site.data.keyword.Bluemix_notm}} Dedicated](../dedicated/index.html#dedicated "{{site.data.keyword.Bluemix_notm}} Dedicated") 是一种位于您自己的专用基础架构中的云环境，它可以安全地连接到 {{site.data.keyword.Bluemix_notm}} Public 云和您自己的网络。
* [{{site.data.keyword.Bluemix_notm}} Local](../local/index.html#local "{{site.data.keyword.Bluemix_notm}} Local") 是一种位于您公司防火墙后的云，可用于保护最敏感的工作负载，并安全连接到 {{site.data.keyword.Bluemix_notm}} Public 和 {{site.data.keyword.Bluemix_notm}} Dedicated。

要设计使用 {{site.data.keyword.Bluemix_notm}} Public、{{site.data.keyword.Bluemix_notm}} Dedicated 、{{site.data.keyword.Bluemix_notm}} Local 或上述各项任意组合的云环境，可以使用以下任一模式：
* [单组织模式](#single)
* [多组织模式](#multi)

如果需要一组相同的用户来访问在组织中任意位置（即 {{site.data.keyword.Bluemix_notm}} Public、{{site.data.keyword.Bluemix_notm}} Dedicated 或 {{site.data.keyword.Bluemix_notm}} Local 中）可用的资源，请考虑使用单组织模式。

如果需要 {{site.data.keyword.Bluemix_notm}} Public、{{site.data.keyword.Bluemix_notm}} Dedicated 或 {{site.data.keyword.Bluemix_notm}} Local 内的不同环境之间相隔离，请考虑使用多组织模式。 

{:shortdesc}

## 单组织模式
{: #single}

单组织模式基于以下原则：

1. 由公司不同区域共享基础架构资源的云体系结构。
2. 隔离应用程序和/或项目。
3. 按角色授予管理资源的权限。

设计单组织体系结构时，可在 {{site.data.keyword.Bluemix_notm}} Public、{{site.data.keyword.Bluemix_notm}} Dedicated 或 {{site.data.keyword.Bluemix_notm}} Local 中创建一个帐户，并定义一个组织。然后，可以基于不同的业务线 (LoB)、交付阶段、特定项目、应用程序、用户许可权或以上各项的组合来定义多个空间。 

为 {{site.data.keyword.Bluemix_notm}} Public、{{site.data.keyword.Bluemix_notm}} Dedicated 或 {{site.data.keyword.Bluemix_notm}} Local 云设计组织体系结构时，请考虑以下信息：

1. 要定义一个组织，请参阅[定义单个组织的指导信息](#singleorg)
2. 要定义多个空间，请参阅[定义多个空间的指导信息](#singlespace)
3. 要基于 Bluemix 角色授予用户许可权，请参阅[为用户分配角色的指导信息](#roles)。


## 多组织模式
{: #multi}

多组织模式基于以下原则：

1. 不由公司不同区域共享基础架构资源的云体系结构。
2. 隔离应用程序和/或项目。
3. 按角色授予管理资源的权限。

设计多组织体系结构时，可在 {{site.data.keyword.Bluemix_notm}} Public、{{site.data.keyword.Bluemix_notm}} Dedicated 或 {{site.data.keyword.Bluemix_notm}} Local 中创建一个帐户。接着，可对应不同的业务线 (LoB)、交付阶段、特定项目、用户许可权或以上各项的组合来定义组织。随后，可以基于公司中同一部门交付的应用程序或项目来定义多个空间。为 {{site.data.keyword.Bluemix_notm}} Public、{{site.data.keyword.Bluemix_notm}} Dedicated 或 {{site.data.keyword.Bluemix_notm}} Local 云设计组织体系结构时，请考虑以下信息：

1. 要定义多个组织，请参阅[定义多个组织的指导信息](#multiorg)
2. 要定义多个空间，请参阅[定义多个空间的指导信息](#multispace)
3. 要基于 Bluemix 角色授予用户许可权，请参阅[为用户分配角色的指导信息](#roles)。

## 组织
{: #org}

{: #singleorg}
采用单组织体系结构时，该组织会包含用于开发、管理和部署云应用程序的所有云资源、服务和应用程序。在 {{site.data.keyword.Bluemix_notm}} Public 中，组织提供帐户之间的隔离，并且组织在所有区域可用。

 ![显示 {{site.data.keyword.Bluemix_notm}} 中单组织体系结构的图](../admin/images/multi_F3.gif "显示 {{site.data.keyword.Bluemix_notm}} 中单组织体系结构的图")

 *图 3. {{site.data.keyword.Bluemix_notm}} Public、{{site.data.keyword.Bluemix_notm}} Dedicated 和 {{site.data.keyword.Bluemix_notm}} Local 的单组织体系结构示例*

{: #multiorg}
采用多组织体系结构时，组织将提供第一级隔离和抽取，可用于控制和定义可以执行的操作以及执行者。根据不同的业务线 (LoB)、交付阶段、用户的 IT 角色、特定项目或以上各项的组合来设计每个组织。  

需要的组织数量取决于多个因素：
*	在组织内管理配额和控制成本所需的详细程度级别。
*	必须在不同环境中强制实施的安全等级。
*	根据公司、国家或地区以及行业要求确定的组织位置。例如，您可能希望在位于您所在地理位置中某个区域的专用云中运行所有应用程序。

以下场景显示了在云环境中定义 {{site.data.keyword.Bluemix_notm}} 组织数量时可采用的不同方法：
* 场景 1：按交付阶段隔离用户

  描述：您有几组不同的用户，分别需要在开发环境、测试环境和生产环境中工作。 
  
  解决方案：可以根据 IT 工作类型创建多个组织，例如针对开发、测试和生产分别创建一个组织。

  ![显示在 {{site.data.keyword.Bluemix_notm}} Public 中按交付阶段隔离用户的图](../admin/images/multi_F1.gif "显示在 {{site.data.keyword.Bluemix_notm}} Public 中按交付阶段隔离用户的图")
 
  *图 1. 与 {{site.data.keyword.Bluemix_notm}} Public 中的交付阶段对应的多组织体系结构示例*

* 场景 2：基于用户类型（内部用户和外部用户）隔离
  
  描述：您的公司与不同的合作伙伴进行合作。您需要对内部用户和外部用户使用不同的应用程序。
  
  解决方案：可以创建多个组织来开发、测试和运行内部使用的应用程序。此外，可以为每个合作伙伴创建一个或多个组织。

* 场景 3：按项目隔离
  
  描述：您的公司运行编程马拉松来确定新服务。  
  
  解决方案：可以为每个编程马拉松定义一个组织，并将组织用作沙箱。在运行编程马拉松后，可以将沙箱组织升级成为帐户中的额外组织。

* 场景 4：按 LoB 和交付阶段隔离用户

  描述：公司规则要求开发、测试和生产用户必须不同。此外，每个 LoB 的应用程序都必须由不同的用户进行开发、管理和部署。必须强制实施安全性，以便用户只能访问与其业务部分相关的应用程序。 
  
  解决方案：可以先按 LoB 再按环境类型来创建组织，例如可以针对记帐部门的应用程序开发创建一个组织，针对记帐应用程序测试创建一个组织，针对生产中的记帐应用程序创建一个组织。

  ![显示在 {{site.data.keyword.Bluemix_notm}} Dedicated 中按 LoB 和交付阶段隔离用户的图](../admin/images/multi_F2.gif "显示在 {{site.data.keyword.Bluemix_notm}} Dedicated 中按 LoB 和交付阶段隔离用户的图")
  
   *图 2. 与 {{site.data.keyword.Bluemix_notm}} Dedicated 中的 LoB 和交付阶段对应的多组织体系结构示例*

要为云组织定义组织列表时，请考虑以下指导信息：
* 定义并强制实施命名约定。例如，定义命名约定，使组织的名称包含有关业务领域、云类型（{{site.data.keyword.Bluemix_notm}} Public、{{site.data.keyword.Bluemix_notm}} Local 或 {{site.data.keyword.Bluemix_notm}} Dedicated）和 IT 角色（开发、测试或生产）的信息。对于位于 {{site.data.keyword.Bluemix_notm}} Public 中的组织，可能还要添加有关区域的信息。 
* 定义应用于组织的限制。例如，定义将在该组织中工作的用户的角色。 
* 确定组织的管理者。
* 确定分配给此组织的业务领域。

## 空间
{: #spaces}

在组织内，空间提供了额外的隔离和抽取级别。 

空间是组织中的保留区域，在其中用户可以开发和运行应用程序与服务。可以在一个组织中创建任意数量的空间。您可以控制有权访问空间的用户。有关管理空间的更多信息，请参阅[空间](../admin/orgs_spaces.html#spaceinfo "空间")。

{: #singlespace}
采用单组织体系结构时，隔离和抽取级别由在组织内定义的空间提供。定义空间时，请考虑以下指导信息：
* 定义一个空间来托管只需在组织中供应和配置一次的服务。 
* 基于交付生命周期定义多个空间。例如，可以为正在开发的应用程序定义一个或多个空间，为处于测试阶段的应用程序定义一个或多个空间，为处于生产阶段的应用程序定义一个或多个空间。
* 如果按交付生命周期无法进行充分隔离，那么可以通过为每个 LoB 和交付阶段定义一个或多个空间来实现更充分地隔离。
* 如果需要按不同组的用户进行隔离，请为每组用户定义一个空间。例如，开发人员不能既创建应用程序，又对其进行测试。需要由另一组用户对应用程序进行测试。在此场景中，您将创建两个空间，一个空间用于应用程序开发者，另一个空间用于应用程序测试者。然后，为每组用户授予对正确空间的访问权。

{: #multispace}
采用多组织体系结构时，可以按交付生命周期的阶段和/或按业务线来隔离每个组织。随后，可以基于公司中同一部门交付的应用程序数或项目数来定义多个空间。计划组织中的空间时，请考虑以下指导信息：

* 为每个应用程序定义一个空间、为每组相关应用程序定义一个空间，或为特定项目定义一个空间。 
* 如果需要按不同组的用户进行隔离，请为每组用户定义一个空间。
  

要为云组织定义空间列表时，请考虑以下指导信息：
* 定义并强制实施命名约定。例如，定义命名约定，使空间名称包含有关组织位置和云类型（{{site.data.keyword.Bluemix_notm}} Public、{{site.data.keyword.Bluemix_notm}} Local 或 {{site.data.keyword.Bluemix_notm}} Dedicated）的信息。
* 定义应用于空间的限制。例如，定义可以在每个空间中开发、管理和部署的应用程序类型。 
* 确定空间的管理员。

## 配额
{: #quota}

在 {{site.data.keyword.Bluemix_notm}} 中创建组织时，可供应基础架构资源（包含内存、IP、CPU 和存储器等资源）。
*	对于 {{site.data.keyword.Bluemix_notm}} Public，将为组织分配最少的一组资源。根据帐户类型，将有不同的资源分配。这些资源将定义分配给组织的配额。 
*	对于 {{site.data.keyword.Bluemix_notm}} Dedicated，您可向 IBM 请求一组资源，然后在 {{site.data.keyword.Bluemix_notm}} Dedicated 云环境中的不同组织之间分布这些资源。 
*	对于 {{site.data.keyword.Bluemix_notm}} Local，您可提供资源，然后在 {{site.data.keyword.Bluemix_notm}} Local 云环境中的各组织之间分布这些资源。

对于 {{site.data.keyword.Bluemix_notm}} Public 和 {{site.data.keyword.Bluemix_notm}} Dedicated，可以向 IBM 请求额外的资源。对于 {{site.data.keyword.Bluemix_notm}} Local，由您负责提供在本地云中运行业务可能需要的任何资源。

分配给组织的配额表示在组织内可用的资源。您可管理配额并决定如何在组织中分布这些资源。

您可按空间或按计算基础架构来监视和管理帐户配额。组织的空间中供应的任何资源都会使用组织的配额。 
* 有关如何在 {{site.data.keyword.Bluemix_notm}} Public 中查看和管理组织配额的更多信息，请参阅[管理配额](../admin/orgs_spaces.html#managequota "管理配额")。 
* 有关如何在 {{site.data.keyword.Bluemix_notm}} Dedicated 或 {{site.data.keyword.Bluemix_notm}} Local 中查看和管理组织配额的更多信息，请参阅[查看使用情况和报告](../admin/index.html?pos=2#oc_resource "查看使用情况和报告")。

在多组织体系结构中，可基于不同的业务线 (LoB)、交付阶段、特定项目、用户许可权或以上各项的组合来定义组织数量。例如，如果按 LoB 和交付阶段定义组织的详细程度级别，并按项目定义空间数，那么可以确定用于 LoB 负责的项目开发、测试和生产的资源。您还可以通过查看空间配额来监视分配给每个项目的资源。在单组织体系结构中，要获取相同的详细信息级别，用于定义空间的标准应该考虑按 LoB、交付阶段和项目进行隔离。每个空间的命名约定应该有利于识别项目，包括有关 LoB、交付生命周期中的阶段以及项目的信息。 

不管是采用多组织体系结构还是单组织体系结构，都请使用空间命名约定，以便轻松识别和显示所需的配额分配。   

## 用户和角色
{: #roles}

可以授予 {{site.data.keyword.Bluemix_notm}} 帐户中的用户多个角色。这些角色定义用户管理帐户和组织资源的许可权：
* 可以向组织成员授予[用户角色](../admin/users_roles.html#userrolesinfo "用户角色")。这些角色定义组织内的访问权级别，以及谁可以访问空间及其资源。例如，可以授予用户对不同空间的不同许可权。
* 仅在 {{site.data.keyword.Bluemix_notm}} Dedicated 和 {{site.data.keyword.Bluemix_notm}} Local 中，可以授予帐户成员[管理角色](../admin/index.html#oc_useradmin "管理角色")来管理系统信息、帐户资源使用情况、报告和日志、目录服务、用户以及每个组织的资源使用情况。

不管是设计多组织体系结构还是单组织体系结构，帐户所有者都是云环境的超级用户。

帐户所有者的核心任务包含：
* 管理全局帐户的资源。
* 创建组织。
* 将用户添加为帐户的团队成员。 

要将用户添加到帐户，请使用用户的电子邮件地址或电子邮件地址列表。在 {{site.data.keyword.Bluemix_notm}} Dedicated 和 {{site.data.keyword.Bluemix_notm}} Local 中，还可以使用公司的 LDAP 来添加用户和/或用户组，或者从文件导入用户。有关更多信息，请参阅[管理用户和许可权](../admin/index.html#oc_useradmin "管理用户和许可权")。

帐户所有者的其他任务包含：
* 通过为一个或多个用户分配**管理者**角色，将这些用户添加为组织管理者。请考虑至少将 2 个用户添加为组织管理者。第一个用户充当组织的主管理者。第二个用户充当副管理者，以备主管理者不在时负责工作。 
* 在 {{site.data.keyword.Bluemix_notm}} Public 中，根据[帐户类型](../pricing/index.html#pay-accounts "帐户类型")设置花费通知。首先，帐户所有者定义用于在成本达到特定限制时向其发出警报的阈值。然后，[配置电子邮件通知](../admin/account.html#notifications "配置电子邮件通知")。帐户管理者可以将电子邮件中的信息用作警报通知，并可根据提供的信息执行操作，例如升级帐户。**注：**只有帐户所有者一个人可以接收花费通知电子邮件。 
* 在 {{site.data.keyword.Bluemix_notm}} Dedicated 或 {{site.data.keyword.Bluemix_notm}} Local 中， 
  * 通过为一个或多个用户分配**管理**角色，将这些用户添加为帐户管理员。请考虑至少添加 2 个用户。第一个用户充当帐户的主管理员。第二个用户充当副管理员。
  * 定义帐户通知，以通知有关维护更新或严重事件警报的信息。可以将这些通知配置为发送电子邮件或短信。

### 用户角色 

用户角色定义可以分配给组织中用户的许可权，并定义用户在组织以及每个空间中具有的访问权级别。 

在多组织体系结构或单组织体系结构中，定义用户以及每个用户执行其工作所需的许可权：
1. 确定需要访问组织的用户组。
2. 为组织中和组织的每个空间中的每个用户定义许可权。
3. 选择用于授予用户所需许可权的角色。
   * [组织的管理者角色](#manager)
   * 组织的审计员角色 (#orgauditor)
   * [组织的记帐角色](#orgbilling)
   * [空间管理者](#spmanager)
   * [空间开发者](#dev)
   * [空间审计员](#spauditor)

{: #manager}
组织的主管理者负责创建空间，在空间中分配配额，邀请用户并选择授予用户角色，以及定义定制域。以下列表概述了组织管理者的任务：
1. 创建已确定的空间。请考虑采用并强制实施命名约定。 
2. 根据将在每个空间中运行的应用程序的类型，在空间之间分配配额。
3. 邀请用户加入组织。 
4. 对每个空间，至少为一个用户授予**空间管理者**角色。
5. 为一组用户授予**组织记帐**角色。
6. 为一组用户授予**组织审计员**角色和**空间审计员**角色。 
7. 定义域。

{: #orgauditor}
被授予**组织审计员**角色的用户可以监视组织中所有空间的配额和用户。 
* 采用多组织体系结构时，请考虑在属于该帐户的每个组织中向同一组用户授予审计员角色。然后，这些用户可以监视云环境中所有组织中的配额，并获得帐户的全局视图。 
* 采用单组织体系结构时，请确定负责监视配额使用情况的用户。

{: #orgbilling}
被授予**组织记帐**角色的用户可以监视组织的成本。 
* 采用多组织体系结构时，请考虑在属于该帐户的每个组织中向同一组用户授予记帐角色。然后，这些用户可以监视每个组织的花费成本，并获得帐户的全局视图。 
* 在单组织体系结构中，确定负责监视成本的用户。

{: #spmanager}
空间管理者负责在其管理和控制的空间内执行的所有工作。空间管理者负责： 
* 监视已分配给空间的配额。 
* 向组织管理者请求更多资源。
* 向组织管理者通知不需要的资源。 
* 通过**开发者**角色将用户添加到空间。
* （可选）将“**空间管理者”角色分配给某个用户，以便此用户可以充当副空间管理者，在主空间管理者不在时负责工作。

{: #dev}
在 {{site.data.keyword.Bluemix_notm}} Public 中，开发者是被授予空间访问权并且分配有**开发者**角色的用户。这些用户可以在空间内执行以下任何任务：
* 管理 CF 应用程序。
* 供应和配置 {{site.data.keyword.Bluemix_notm}} 服务。 
* 将域与应用程序相关联。

在 {{site.data.keyword.Bluemix_notm}} Dedicated 和 {{site.data.keyword.Bluemix_notm}} Local 中，开发者也是被授予空间访问权并且分配有**开发者**角色的用户。这些用户可以在空间内执行以下任何任务：
* 管理 CF 应用程序。
* 供应和配置 {{site.data.keyword.Bluemix_notm}} 服务。 
* 将域与应用程序相关联。

{: #spauditor}
请考虑将每个空间中的**审计**角色授予已授予**组织审计员**角色的用户。您可能还需要将此角色授予一组特定的用户。

### 管理角色 

[管理角色](../admin/index.html#oc_useradmin "管理角色")定义可以授予用户管理 {{site.data.keyword.Bluemix_notm}} Dedicated 或 {{site.data.keyword.Bluemix_notm}} Local 帐户的许可权。您可以授予读或写许可权，以允许用户查看系统信息、帐户资源使用情况、报告和日志、目录服务、用户以及每个组织的资源使用情况。 

在多组织体系结构或单组织体系结构中，定义用户以及每个用户管理帐户所需的许可权：

1. 确定计划授予其管理许可权的一组用户，这组用户将属于管理云团队。请在此团队的成员中包含组织管理者。
2. 为帐户中的这些用户定义许可权。在团队中各用户之间划分许可权来管理目录和报告。
3. 为每个用户选择一个或多个角色，以匹配管理帐户所需的许可权：
   * 管理角色：向此帐户中 2 个以上的用户授予此角色。具有此角色的用户有权管理整个组织。
   * 用户角色：可以将此角色配置为具有读或写许可权。向组织的管理者授予具有写许可权的此角色，允许管理者向帐户及其组织添加用户。向可能需要访问并查看帐户成员列表的组织管理者授予具有读许可权的此角色。
   * 目录角色：可以将此角色配置为具有读或写许可权。向一组用户授予具有写许可权的此角色，允许这些用户定义和管理用户可以在 Bluemix 目录中看到哪些 Bluemix 服务和入门模板。向组织管理者授予具有读许可权的此角色。
   * 报告角色：可以将此角色配置为具有读或写许可权。向一组用户授予具有写许可权的此角色，允许这些用户查看和添加报告，其他具有读许可权的用户可以下载这些报告。向管理团队中的所有成员授予读许可权。
   * 登录角色：向管理团队中的所有成员授予此角色。您还可以向帐户中需要访问并查看帐户通知和系统信息的其他用户授予此角色。












