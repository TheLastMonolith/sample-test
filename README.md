# SMS Classification API

## Overview
This API allows you to classify SMS messages as spam or ham (non-spam). It provides one endpoint for rendering results on an HTML GUI.

## Base URL
The base URL for all API endpoints is `localhost.8080`

## Authentication
Authentication is not required for accessing the API.

## Endpoints

### Render Results on HTML GUI

This endpoint renders the classification result on an HTML GUI.

#### Request Parameters
No request parameters are required.

#### Request Example
1. Pull the image from the docker hub:  
```
docker pull jfiguracion94/sms-spam-app
```
2. Run the docker command below on your local machine:  
```
docker run -p 8080:8080 -d jfiguracion94/sms-spam-app
```
3. Open the application by going to `localhost.8080` in a browser.
4. Submit the SMS message through the text box form.
Example:
```
POST localhost:8080/predict OK
Content-Type: application/json

{
  "sms": "Get a free gift now! Call +871297"
}
```

#### Response
The response is an HTML page containing the classification result once you click the **predict** button  
Example:
```
POST localhost:8080/predict OK
Content-Type: application/json

{
  "prediction": "SPAM!"
}
```  

### Conclusion
This API provides am endpoint that allows for rendering results on an HTML GUI. By sending a POST request to the appropriate endpoint, you can obtain the classification result in the response.
