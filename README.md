# SMS Classification API

## Overview
This API allows you to classify SMS messages as spam or ham (non-spam).  It provides two endpoints: one for rendering results on an HTML GUI and another for direct API calls.

## Base URL
The base URL for all API endpoints is `localhost.8080`

## Authentication
Authentication is not required for accessing the API.

## Endpoints

### Render Results on HTML GUI

This endpoint renders the classification result on an HTML GUI.

1. Pull the image from the docker hub:  
```
docker pull jfiguracion94/sms-api:1.0.0
```
> *Note*: use the tag `1.0.0` when calling the docker image, leaving it blank will call the tag `latest`, which could lead to error
2. Run the docker command below on your local machine:  
```
docker run -p 8080:8080 jfiguracion94/sms-api:1.0.0
```
A successful run should look something like this:
![](https://github.com/TheLastMonolith/sms-spam-api-doc/blob/main/assets/docker-run.png)
> *Note*: you can add `-d` for detach mode, this will hide the terminal response
3. Open the application by going to `localhost.8080` in a browser.
4. Submit the SMS message through the text box form.
5. Once you click the predict button, it will show a text if it's a spam or ham.

![](https://github.com/TheLastMonolith/sms-spam-api-doc/blob/main/assets/spam-app.gif)

#### Request Parameters
No request parameters are required.

#### Request Example (home)
```
"GET / HTTP/1.1" 200 -
"GET /static/css/style.css HTTP/1.1" 200 -
```

#### Response Example (/predict)
The response is an HTML page containing the classification result once you click the **predict** button  
Example:
```
POST /predict HTTP/1.1" 200 -

{
  "prediction": "SPAM!"
}
```  
### Direct API Call
This endpoint allows for direct API calls to classify SMS messages
```
POST /predict_api
```
1. Run the docker image if you haven't started it yet.
```
docker run -p 8080:8080 jfiguracion94/sms-api:1.0.0
```
2. Open another terminal, `cd` to the same directory you saved the **app** folder.
3. Run `python request.py`
4. It will print the prediction of the input sms form the `request.py`
   
#### Request Example
```
{
  "sms" : "Congratulations! You have won a free trip to the Bahamas. Reply to claim your prize."
}
```

#### Response Example (/predict_api)
The response is an HTML page containing the classification result once you click the **predict** button  
Example:
```
POST /predict_api HTTP/1.1" 200 -

{
  "prediction": "SPAM!"
}
```
![](https://github.com/TheLastMonolith/sms-spam-api-doc/blob/main/assets/predict_api.png)

### Conclusion
This API provides two endpoints: one for rendering results on an HTML GUI and another for direct API calls. By sending a POST request to the appropriate endpoint, you can obtain the classification result in the response.

### Author  
Joseph Figuracion  
  
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/josephfiguracion/)
