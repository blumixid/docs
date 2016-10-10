---

copyright:
  years: 2016

---


{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

<!-- audience blue staging only begin comment -->


## 在 Dedicated 中对 Cloud Foundry 应用程序进行监视和日志记录
{: #dedicated_apps_ml_ov}

上次更新时间：2016 年 5 月 24 日
{: .last-updated}

在 {{site.data.keyword.Bluemix_notm}} Dedicated 中，Cloud Foundry 应用程序随附内置日志记录功能。可以在 {{site.data.keyword.Bluemix_notm}}“仪表板”上查看从应用程序收集的数据。
{:shortdesc}

### 在 Dedicated 中对 Cloud Foundry 应用程序进行日志记录
{: #dedicated_apps_ml_logs}

*上次更新时间：2016 年 5 月 24 日*
{: .last-updated}

Cloud Foundry 应用程序日志由 Cloud Foundry loggregator 从应用程序外部进行监视和转发，而不必在应用程序内部安装代理程序。
{:shortdesc}

### 在 Dedicated 中查看 Cloud Foundry 应用程序的日志
{: #dedicated_apps_ml_logs_dash}

*上次更新时间：2016 年 5 月 24 日*
{: .last-updated}

可以查看在 {{site.data.keyword.Bluemix_notm}} 上运行的应用程序的日志。
{:shortdesc}

1. 要查看应用程序日志，请执行以下步骤。
2. 打开 {{site.data.keyword.Bluemix_notm}}“仪表板”。
3. 选择应用程序。
4. 单击**日志**。这将显示“日志记录”选项卡。
5. 单击**高级视图**按钮。

在**日志**视图中，可以查看运行的应用程序的日志。还可以基于日志类型和通道进行过滤。

**限制：**日志数据最长可用时间为 30 天。超过 30 天后，日志数据会滚动式覆盖（先进先出）。

要获取数据的更多视图，可通过**高级视图**打开 Kibana，这是一个可视化工具，使用日志和带时间戳记的数据来创建定制可视化。有关使用高级视图的更多信息，请参阅 [Kibana](https://www.elastic.co/guide/en/kibana/current/index.html) 文档。

### 定制用于日志的 Kibana 仪表板
{: #dedicated_apps_ml_logs_custom}

创建定制仪表板以显示在空间中运行的应用程序的日志。

开始之前，请登录到 Kibana 用户界面。
1. 打开 `https://logmet.<customer_name>.chinabluemix.net`。
2. 输入您的 {{site.data.keyword.Bluemix_notm}} 标识、密码、空间和组织。
3. 选择 **Kibana**。
4. 单击**登录**。

（可选）要保存缺省值或样本仪表板以进行定制，请执行以下步骤。

1. 打开缺省仪表板或以下某个样本仪表板。
  - [https://logmet.<span class="keyword" data-hd-keyref="DomainName">DomainName</span>/kibana/#/dashboard/file/blank.json](https://logmet.chinabluemix.net/kibana/#/dashboard/file/blank.json)
  - [https://logmet.<span class="keyword" data-hd-keyref="DomainName">DomainName</span>/kibana/#/dashboard/file/guided.json](https://logmet.chinabluemix.net/kibana/#/dashboard/file/guided.json)
  - [https://logmet.<span class="keyword" data-hd-keyref="DomainName">DomainName</span>/kibana/#/dashboard/script/logstash.js](https://logmet.{DomainName}/kibana/#/dashboard/script/logstash.js)
  - [https://logmet.<span class="keyword" data-hd-keyref="DomainName">DomainName</span>/kibana/#/dashboard/file/logstash.json](https://logmet.{DomainName}/kibana/#/dashboard/file/logstash.json)
  - [https://logmet.<span class="keyword" data-hd-keyref="DomainName">DomainName</span>/kibana/#/dashboard/file/noted.json](https://logmet.{DomainName}/kibana/#/dashboard/file/noted.json)
2. 将该仪表板另存为新仪表板。
    1. 在工具栏中，单击**保存**图标。
    2. 输入仪表板的名称。
    3. 在“名称”字段旁边，单击**保存**图标。
3. 如果未看到任何日志，请调整顶部的时间选取器。

尝试以下常用方法来定制用于显示日志信息的仪表板：
- [通过现有表创建图表](#creating_chart_existing_table)
- [通过查询创建图表](#creating_chart_query)

#### 通过现有表创建图表
{: #creating_chart_existing_table}

通过缺省仪表板中“所有事件”列表中的字段，创建条形图、饼图或表。

此任务使用 `default.json` 仪表板中的元素来创建其他元素。
1. 在表中，展开**字段**部分。
2. 可选：选中要在“所有活动”列表中显示的字段旁边的复选框。
3. 要从哪个字段创建图形，即单击其名称。例如，选择 **group_id** 可创建用于根据每个容器组的组标识收集日志的图形。
4. 在**术语**菜单中，选择**条形图**、**饼图**或**表**。这将显示图形。
5. 将图形拖至仪表板以保存该图形。
6. 可选：单击**配置**图标以更改图形的配置。例如，可单击**面板**选项卡，然后在**排除术语**字段中，输入 0000。此过程会将应用程序分组到名为“其他值”的类别中。

#### 通过查询创建图表
{: #creating_chart_query}

首先，创建颜色编码的查询，然后基于消息类型对消息分组。接着，基于这些查询将消息显示到图表中。

1. 针对要在仪表板中显示的信息创建查询。
  1. 在“查询”部分中，单击彩色圆圈。
  2. 选择查询的类型。例如，可选择 **Lucene**。
  3. 为查询选择颜色。此颜色将显示在面板中以表示此查询。例如，要描述错误消息，可选择红色。在使用此查询的饼图中，错误消息会显示为红色。
  4. 输入查询。对于 Lucene 查询，可能需要输入字段名称、冒号以及可能会显示在该字段中的值。例如，要显示错误消息，可输入消息：\*error\*。此查询会将其中包含单词 error 的消息分组在一起。
  5. 可选：单击**锁定**。稍后创建面板时，可以只包含锁定的查询。
  6. 可选：重复这些步骤以创建参考消息显示为绿色的查询和警告消息显示为黄色的查询。![参考消息示例](../manageapps/containers/images/container_queries_messages.png)
  7. 保存对仪表板的更改。
2. 创建使用查询的面板。
  1. 滚动到仪表板末尾，并单击**添加行**。
  2. 输入行的名称。此名称不会显示在仪表板中。此名称显示在仪表板配置页面中，在此页面中可以对行重新排序。
  3. 单击**创建行**。
  4. 按所需顺序排列行，然后单击**保存**。
  5. 在新行中，单击**向行添加面板**。
  6. 选择面板类型。对于**日志**，常用的是**表**、**直方图**、**命中**和**术语**。表可能是最常用的日志显示方法，这样将显示每个日志的所有详细信息，而不是一组日志的表示。但对于消息类型示例，会使用**命中**，以便可以显示用颜色编码表示的消息类型。
  7. 输入面板的标题。此名称会显示在仪表板中。示例消息类型
  8. 选择样式以及所需的其他任何显示定制项。示例：**饼图**和**倾斜**
  9. 对于查询，选择**已锁定**。
  10. 单击**保存**。![饼图示例](../manageapps/containers/images/container_pie_messages.png)
3. 保存对仪表板的更改。

有关定制 Kibana 仪表板的更多信息，请参阅[此博客帖子](https://developer.ibm.com/bluemix/2015/09/29/creating-custom-kibana-dashboard-in-bluemix/)或 [Kibana 文档](https://www.elastic.co/guide/en/kibana/current/index.html)。

<!-- audience blue staging only end comment -->
