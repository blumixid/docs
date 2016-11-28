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

# Getting started with NER
{: #gettingstarted}

<!-- Provide an appropriate ID above -->


中文命名实体识别API服务使用基于机器学习和规则匹配相结合的方法，
识别中文文本中的四种实体类型：人名、地名、机构名、其他类别专有名称。
提供页面交互访问和REST编程接口两种访问方式。

Chinese Named Entity Recognition service recognizes names of four types of entities: person, place, organization, and miscellaneous type. You can try it out now, or call the service through REST APIs.
{:shortdesc}

本服务提供了REST API。这个API使用的是POST方法，调用者指定application/json作为Request Header，并把需要分析的中文文本内容封装成在JSON的“main_content”字段中，然后将这个HTTP请求发送到。返回结构也采用JSON格式。

This service provides REST API. This API uses POST method, which requires the caller to set "application/json" as Request Header, pack the Chinese text to analyze into the "main_content" field of a JSON object, and then send the request via HTTP call. The output is also a JSON data; for its details, please refer to the following sections.

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
                 json.put("task", "ner");
                 OutputStream outputStream = httpConnection.getOutputStream();
                 outputStream.write(json.serialize().getBytes());
                 outputStream.flush();

                 // get the response, i.e., NER result
                 if (httpConnection.getResponseCode() != 200) {
                     throw new RuntimeException("Failed : HTTP error code : "
                     + httpConnection.getResponseCode());
                 }

                 BufferedReader responseBuffer = new BufferedReader(new InputStreamReader(
                        (httpConnection.getInputStream())));
                 String output;
                 System.out.println("NER result:\n");
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


	
	
	
## Tutorials and Samples
{: #samples}
* [NER function overview](https://sv.chinabluemix.net/bluepulse/ner/nerdoc.jsp){:new_window}

## API Reference
{: #api}
* [NER API](https://sv.chinabluemix.net/bluepulse/ner/nerapi.jsp){:new_window}

## Related Links
{: #general}
* [Try Me](https://sv.chinabluemix.net/bluepulse/ner/ner.jsp){:new_window}
