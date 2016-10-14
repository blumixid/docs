---

copyright:
  years: 2016
lastupdated: "2016-10-11"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}


# Customized Image Classifier API version v1.0

https://sv.chinabluemix.net/dlaas/api

{: #gettingstartedCIC}

The CIC service provides the image classifier based on users' specific requirements. Through this service, users can get their specified training models and deploy the image classifiers as web service. Users just need to define their images' categories and upload corresponding images. They will get their customized image classifier automatically. This service makes users to create image classifiers through deep learning techniques with zero entry.
{:shortdesc}

## DLAPIs
{: #DLAPIs}

Run the published APIs.

**/dlapis/{id}** 

* **GET**: Run API by providing imageUrl Sample: /dlapis/fbb78a52-ae41-4000-bbe5-ad0d116c4e9d?imageUrl=http://IP/path/fff287bc-412b-4b5d-9f8a-a3af27ca74d7.jpg

* **POST**: Run API by uploading an image

### GET /dlapis/{id}
{: #getdlapi}

Run API by providing imageUrl Sample: /dlapis/fbb78a52-ae41-4000-bbe5-ad0d116c4e9d?imageUrl=http://IP/path/fff287bc-412b-4b5d-9f8a-a3af27ca74d7.jpg

* ### Request
{: #request}

  * **URI Parameters**

       --id: required (string)
   
       --Example:
 
 	       fbb78a52-ae41-4000-bbe5-ad0d116c4e9d

  * **Query Parameters**

       --imageUrl: required (string)
   
       --Example:
   
            http://IP/path/fff287bc-412b-4b5d-9f8a-a3af27ca74d7.jpg

* ### Response
{: #response}

  * **HTTP status code 200**
  * **Body**
  
    **Type: application/json**
	
	**Example:**
    ```
	  the web api running result
      {
        result: "success",
        imageUrl: "http://IP/path/fff287bc-412b-4b5d-9f8a-a3af27ca74d7.jpg",
        classified:
       {
          store: "0.71855"
       }
      }
    ```
	{: screen}
	
### POST /dlapis/{id}
{: #postdlapi} 
     
Run API by uploading an image

* ### Request
{: #postrequest}

  * **URI Parameters**

       --id: required (string)
   
       --Example:  
	   
 	       fbb78a52-ae41-4000-bbe5-ad0d116c4e9d
		
  * **Body**
  
    **Type: multipart/form-data**
	
	**Example:**
	```
	// Post params
    Content-Disposition: form-data;
      [
        name="files"; filename="mytemp.jpg" Content-Type: image/jpeg => image binary data
      ]
    // HTML usage
    <form enctype="multipart/form-data" action="{baseUri}/dlapis/4c3259c3-e300-41a7-b031-d6fbf508cab7" method="POST">
         Choose a file to upload:
         <input name="files" type="file" /><br />
         <input type="submit" value="Upload File" />
    </form>
    // curl usage
    curl -i -X POST -H "Content-Type: multipart/form-data" -F "files=@mytemp.jpg" {baseUri}/dlapis/4c3259c3-e300-41a7-b031-d6fbf508cab7
	```
	{: codeblock}

* ### Response
{: #postresponse}

  * **HTTP status code 201**
  * **Body**
  
    **Type: application/json**
	
	**Example:**
    ```
	the web api running result
    {
      result: "success",
      imageUrl: "http://IP/path/fff287bc-412b-4b5d-9f8a-a3af27ca74d7.jpg",
      classified:
      {
        store: "0.71855"
      }
    }
	```
	{: screen}




