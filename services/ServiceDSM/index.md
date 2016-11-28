---

copyright:
  years: 2016

lastupdated: "2016-10-15"

---
<!-- Copyright info at top of file: REQUIRED
    The copyright info is YAML content that must occur at the top of the MD file, before attributes are listed.
    It must be --- surrounded by 3 dashes ---
    The value "years" can contain just one year or a two years separated by a comma. (years: 2014, 2016)
    Indentation as per the previous template must be preserved.
-->

<!-- Common attributes used in the template are defined as follows: -->
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}


# Getting started with DSM
{: #gettingstarted}

<!-- Provide an appropriate ID above -->


中文深度舆情挖掘API服务从无结构的文本中提取和辨别主观评论性的内容。它从文章中辨别哪些句子描述事实，哪些有评论性，“谁”评论了“什么”，怎样评论的，评论了哪些方面。针对新闻和评论，中文深度舆情挖掘API服务按评论者的权威性以及评论本身的质量和可靠性，使用基于机器学习和规则匹配相结合的方法，对文章进行正面、负面、和中性的分类。该服务提供页面交互访问和REST编程接口两种访问方式。有关此服务的详细介绍和使用，请参阅功能介绍和API文档。

This is a service to provide Chinese Deep Sentiment Mining. You can try it out online or integrate this service into your codes through RESTful API calls. For documents about Chinese Deep Sentiment Mining functions and APIs, please refer to overview document and API reference.


{:shortdesc}

<!-- If overview content is required, do not include it here. Put it in a separate "## About" section below the task section. -->


This service provides REST API of POST method, which requires the caller to set "application/json" as Request Header, pack the Chinese text to analyze into the "main_content" field of a JSON object, and then send the request via HTTP call. The output is also a JSON data; for its details, please refer to the following sections.

A sample Java code snippet could be like this:

	```
            try {
                 URL targetUrl = new URL(targetURL);

                 // send a POST request
                 HttpURLConnection httpConnection = (HttpURLConnection) targetUrl.openConnection();
                 httpConnection.setDoOutput(true);
                 httpConnection.setRequestMethod("POST");
                 httpConnection.setRequestProperty("Content-Type", "text/xml");
                 JSONObject json = new JSONObject(); // com.ibm.json.java.JSONObject
                 json.put("main_content", inputChineseText);
                 json.put("task", "dsm");
                 OutputStream outputStream = httpConnection.getOutputStream();
                 outputStream.write(json.serialize().getBytes());
                 outputStream.flush();

                 // get the response, i.e., DSM result
                 if (httpConnection.getResponseCode() != 200) {
                     throw new RuntimeException("Failed : HTTP error code : "
                     + httpConnection.getResponseCode());
                 }

                 BufferedReader responseBuffer = new BufferedReader(new InputStreamReader(
                        (httpConnection.getInputStream())));
                 String output;
                 System.out.println("DSM result:\n");
                 while ((output = responseBuffer.readLine()) != null) {
                        System.out.println(output);
                 }
                 httpConnection.disconnect();
            } catch (MalformedURLException e) {
                 e.printStackTrace();
            } catch (IOException e) {
                 e.printStackTrace();
            }
	```
	{: codeblock}

Details of Output Data Schema is as below: 

o sentiment：文本的整体情感值：用正负数表示，正数表示舆情情感是正向的、积极的，类似于“好评”；负数表示舆情情感是负向的、消极的，类似于“差评”。数值越大，表示正负的倾向越明显。This is the overall sentiment polarity score represented by an integer number, either positive or negative. A positive value indicates positive and active sentiment, while a negative value means an negative sentiment. The bigger the value is, the stronger the polarity is.

o sentiment_cats：舆情类别，比如“食品安全:产品质量”、“食品饮料:产品:产品属性:口味”等。This is the field of categories of sentiment targets, e.g. "食品安全:产品质量", "食品饮料:产品:产品属性:口味", etc.

o aspect_0_als：最高级别的舆情类别，比如“食品安全”、“食品饮料”等。This is the field of the highest categories of sentiment targets, e.g., "食品安全", "食品饮料"等。

o aspect_1_als：次高级别的舆情类别，比如“食品安全:产品质量”、“食品饮料:产品”等。This is the field of the second highest categories of sentiment targets, e.g., "食品安全:产品质量", "食品饮料:产品", etc.

o aspect_2_als：第二级别的舆情类别，比如“食品饮料:产品:产品属性”等。

o aspect_3_als：第三级别的舆情类别，比如“食品饮料:产品:产品属性:口味”等。

o demand_aspects：需求分析结果，比如“奶源建设:工厂牧场运营”等。This is the field of demand analysis results.

o sentiment_objs：情感分析对象，比如“食品”、“管理”等。This field is the list of literal sentiment objects that appear in the original intpu text.

o opinion_words：文本中出现过的情感词，比如“完好”、“坏了”等。This field is the list of literal sentiment polarity words or terms that appear in the original input text.


## Tutorials and Samples
{: #samples}
* [DSM function overview](https://sv.chinabluemix.net/bluepulse/dsm/dsmdoc.jsp){:new_window}

## API Reference
{: #api}
* [DSM API](https://sv.chinabluemix.net/bluepulse/dsm/dsmapi.jsp){:new_window}

## Related Links
{: #general}
* [Try Me](https://sv.chinabluemix.net/bluepulse/dsm/dsm.jsp){:new_window}
