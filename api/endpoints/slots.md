---
description: All API Endpoints Related to Slots
---

# Slots

{% swagger method="get" path="/api/v1/slots" baseUrl="https://example.com" summary="Get a List of Slots" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="query" name="beforeDate " type="String" required="false" %}
A UNIX Timestamp
{% endswagger-parameter %}

{% swagger-parameter in="query" name="afterDate" type="Strig" required="false" %}
A UNIX Timestamp
{% endswagger-parameter %}

{% swagger-parameter in="header" name="authorisation" type="String" required="true" %}
Authorisation Header that allowed you to access the RadioPanel API
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```javascript
{
    "_embedded": [
        {
            "uuid": "7a751c6b-7b77-40e9-b8a1-979fa625d330",
            "title": "New slot",
            "tenantUuid": "141bc871-f1e5-44b9-98f7-59fd1e31faea",
            "userUuid": "d7facb17-6012-48d3-b560-d039b5f043c7",
            "slotTypeUuid": "90731312-6a6e-4e75-8856-42a67f65b2f2",
            "start": 1604415600,
            "end": 1604419200,
            "recurring": false,
            "updatedAt": "2020-11-03T15:25:55.903Z",
            "createdAt": "2020-11-03T15:25:55.903Z",
            "slotType": {
                "uuid": "90731312-6a6e-4e75-8856-42a67f65b2f2",
                "name": "Podcast",
                "tenantUuid": "141bc871-f1e5-44b9-98f7-59fd1e31faea",
                "description": "Podcast show",
                "color": "#b80000",
                "updatedAt": "2020-06-25T18:08:44.779Z",
                "createdAt": "2020-06-25T18:08:44.779Z"
            },
            "user": {
                "uuid": "d7facb17-6012-48d3-b560-d039b5f043c7",
                "username": "Felikx",
                "avatar": "https://radiopanel.s3.nl-ams.scw.cloud/c9a65443-eed1-41ed-b9d2-743223b5ee75/bcab441c-88a4-4198-8d5d-cee0d6852a6c.png",
                "bio": "Radiopanel Developer",
                "email": "hidden",
                "password": "hidden",
                "updatedAt": "2020-05-16T13:42:38.142Z",
                "admin": true,
                "createdAt": "2020-05-16T13:42:38.142Z",
                "socials": {
                    "twitch": "",
                    "discord": "",
                    "twitter": "https://twitter.com/FelikxVanSaet",
                    "youtube": "",
                    "facebook": "",
                    "instagram": ""
                }
            }
        }
    ],
    "_page": {
        "totalEntities": 0
    }
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="post" path="/api/v1/slots/" baseUrl="https://example.com" summary="Book a Slot" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="body" type="String" name="title" required="true" %}
The title of the slot.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="slotTypeUuid" type="String" required="true" %}
The UUID of the slot type.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="userUuid" type="String" required="true" %}
The UUID of the user booking the slot.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="start" type="Integer" required="true" %}
A UNIX Timestamp
{% endswagger-parameter %}

{% swagger-parameter in="body" name="end" type="Integer" required="true" %}
A UNIX Timestamp
{% endswagger-parameter %}

{% swagger-parameter in="body" name="recurring" type="Boolean" required="true" %}
If the show is repeated weekly.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="customData" type="Object" required="true" %}
Key Value data for Custom Slot Data
{% endswagger-parameter %}

{% swagger-parameter in="header" name="authorisation" type="String" required="true" %}
Authorisation Header that allowed you to access the RadioPanel API
{% endswagger-parameter %}

{% swagger-response status="201: Created" description="" %}
```javascript
{
   "uuid":"d7facb17-6012-48d3-b560-d039b5f043c7",
   "title":"Show",
   "userUuid":"f11d7141-7d82-4e23-9183-4a55eabc6f73",
   "slotTypeUuid":"2375e486-6c83-41d0-b55d-5d5a14282dd0",
   "start":1644973200,
   "end":1644976800,
   "recurring":false,
   "customData":{
      
   },
   "updatedAt":"2022-02-16T10:14:43.070Z",
   "createdAt":"2022-02-16T10:14:43.070Z",
   "user":{
      "uuid":"f11d7141-7d82-4e23-9183-4a55eabc6f73",
      "username":"Felikx",
      "avatar":"https://radiopanel.s3.nl-ams.scw.cloud/c9a65443-eed1-41ed-b9d2-743223b5ee75/bcab441c-88a4-4198-8d5d-cee0d6852a6c.png",
      "authenticationMethodUuid":"28e29f82-91f7-4d0f-a907-91a9960f68b9",
      "bio":null,
      "email":"hidden",
      "password":"hidden",
      "updatedAt":"2022-02-15T11:56:16.847Z",
      "createdAt":"2022-02-15T11:56:16.847Z",
      "socials":{
         "twitch":"",
         "discord":"",
         "twitter":"",
         "youtube":"",
         "facebook":"",
         "instagram":""
      },
      }
   },
   "slotType":{
      "uuid":"2375e486-6c83-41d0-b55d-5d5a14282dd0",
      "name":"Regular Show",
      "description":"",
      "color":"#6bff9f",
      "updatedAt":"2022-02-15T12:07:02.398Z",
      "createdAt":"2022-02-15T12:07:02.398Z"
   }
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="/api/v1/slots/live" baseUrl="https://example.com" summary="Get the Live Slot" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="authorisation" type="String" required="true" %}
Authorisation Header that allowed you to access the RadioPanel API
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Slot Found" %}
```javascript
{
    "uuid": "7a751c6b-7b77-40e9-b8a1-979fa625d330",
    "title": "New slot",
    "tenantUuid": "141bc871-f1e5-44b9-98f7-59fd1e31faea",
    "userUuid": "d7facb17-6012-48d3-b560-d039b5f043c7",
    "slotTypeUuid": "90731312-6a6e-4e75-8856-42a67f65b2f2",
    "start": 1604415600,
    "end": 1604419200,
    "recurring": false,
    "updatedAt": "2020-11-03T15:25:55.903Z",
    "createdAt": "2020-11-03T15:25:55.903Z",
    "slotType": {
        "uuid": "90731312-6a6e-4e75-8856-42a67f65b2f2",
        "name": "Podcast",
        "tenantUuid": "141bc871-f1e5-44b9-98f7-59fd1e31faea",
        "description": "Podcast show",
        "color": "#b80000",
        "updatedAt": "2020-06-25T18:08:44.779Z",
        "createdAt": "2020-06-25T18:08:44.779Z"
    },
    "user": {
        "uuid": "d7facb17-6012-48d3-b560-d039b5f043c7",
        "username": "Felikx"
        "avatar": "https://radiopanel.s3.nl-ams.scw.cloud/c9a65443-eed1-41ed-b9d2-743223b5ee75/bcab441c-88a4-4198-8d5d-cee0d6852a6c.png",
        "bio": "Radiopanel Developer",
        "email": "hidden",
        "password": "hidden",
        "updatedAt": "2020-05-16T13:42:38.142Z",
        "admin": true,
        "createdAt": "2020-05-16T13:42:38.142Z",
        "socials": {
            "twitch": "",
            "discord": "",
            "twitter": "https://twitter.com/FelikxVanSaet",
            "youtube": "",
            "facebook": "",
            "instagram": ""
        }
    }
}
```
{% endswagger-response %}

{% swagger-response status="204: No Content" description="Slot Not Found" %}
```javascript
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="/api/v1/slots/" baseUrl="" summary="Get the Next Available Slot" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="authorisation" type="String" required="true" %}
Authorisation Header that allowed you to access the RadioPanel API
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```javascript
{
    "uuid": "7a751c6b-7b77-40e9-b8a1-979fa625d330",
    "title": "New slot",
    "tenantUuid": "141bc871-f1e5-44b9-98f7-59fd1e31faea",
    "userUuid": "d7facb17-6012-48d3-b560-d039b5f043c7",
    "slotTypeUuid": "90731312-6a6e-4e75-8856-42a67f65b2f2",
    "start": 1604415600,
    "end": 1604419200,
    "recurring": false,
    "updatedAt": "2020-11-03T15:25:55.903Z",
    "createdAt": "2020-11-03T15:25:55.903Z",
    "slotType": {
        "uuid": "90731312-6a6e-4e75-8856-42a67f65b2f2",
        "name": "Podcast",
        "tenantUuid": "141bc871-f1e5-44b9-98f7-59fd1e31faea",
        "description": "Podcast show",
        "color": "#b80000",
        "updatedAt": "2020-06-25T18:08:44.779Z",
        "createdAt": "2020-06-25T18:08:44.779Z"
    },
    "user": {
        "uuid": "d7facb17-6012-48d3-b560-d039b5f043c7",
        "username": "Felikx",
        "avatar": "https://radiopanel.s3.nl-ams.scw.cloud/c9a65443-eed1-41ed-b9d2-743223b5ee75/bcab441c-88a4-4198-8d5d-cee0d6852a6c.png",
        "bio": "Radiopanel Developer",
        "email": "hidden",
        "password": "hidden",
        "updatedAt": "2020-05-16T13:42:38.142Z",
        "admin": true,
        "createdAt": "2020-05-16T13:42:38.142Z",
        "socials": {
            "twitch": "",
            "discord": "",
            "twitter": "https://twitter.com/FelikxVanSaet",
            "youtube": "",
            "facebook": "",
            "instagram": ""
        }
    }
}
```
{% endswagger-response %}

{% swagger-response status="204: No Content" description="Slot Not Found" %}
```javascript
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="/api/v1/slots/later" baseUrl="https://example.com" summary="Get the Next Available Slot after Next" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="authorisation" type="String" required="true" %}
Authorisation Header that allowed you to access the RadioPanel API
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```javascript
{
    "uuid": "7a751c6b-7b77-40e9-b8a1-979fa625d330",
    "title": "New slot",
    "tenantUuid": "141bc871-f1e5-44b9-98f7-59fd1e31faea",
    "userUuid": "d7facb17-6012-48d3-b560-d039b5f043c7",
    "slotTypeUuid": "90731312-6a6e-4e75-8856-42a67f65b2f2",
    "start": 1604415600,
    "end": 1604419200,
    "recurring": false,
    "updatedAt": "2020-11-03T15:25:55.903Z",
    "createdAt": "2020-11-03T15:25:55.903Z",
    "slotType": {
        "uuid": "90731312-6a6e-4e75-8856-42a67f65b2f2",
        "name": "Podcast",
        "tenantUuid": "141bc871-f1e5-44b9-98f7-59fd1e31faea",
        "description": "Podcast show",
        "color": "#b80000",
        "updatedAt": "2020-06-25T18:08:44.779Z",
        "createdAt": "2020-06-25T18:08:44.779Z"
    },
    "user": {
        "uuid": "d7facb17-6012-48d3-b560-d039b5f043c7",
        "username": "Felikx",
        "avatar": "https://radiopanel.s3.nl-ams.scw.cloud/c9a65443-eed1-41ed-b9d2-743223b5ee75/bcab441c-88a4-4198-8d5d-cee0d6852a6c.png",
        "bio": "Radiopanel Developer",
        "email": "hidden",
        "password": "hidden",
        "updatedAt": "2020-05-16T13:42:38.142Z",
        "admin": true,
        "createdAt": "2020-05-16T13:42:38.142Z",
        "socials": {
            "twitch": "",
            "discord": "",
            "twitter": "https://twitter.com/FelikxVanSaet",
            "youtube": "",
            "facebook": "",
            "instagram": ""
        }
    }
}
```
{% endswagger-response %}

{% swagger-response status="204: No Content" description="Slot Not Found" %}
```javascript
```
{% endswagger-response %}
{% endswagger %}
