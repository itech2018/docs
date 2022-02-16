---
description: Get banners for your radio's website.
---

# Banner List

{% swagger baseUrl="https://api.radiopanel.co" path="/api/v1/banners" method="get" summary="Get the banner list" %}
{% swagger-description %}
Get the list of banners
{% endswagger-description %}

{% swagger-parameter in="header" name="X-Tenant" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authentication" type="string" %}

{% endswagger-parameter %}

{% swagger-response status="200" description="Banner found and returned" %}
```
{
  "_embedded": [
    {
      "uuid": "1437e326-90d0-4172-a31c-65fe74cad3b3",
      "name": "radiopaneldiscord",
      "slug": "rpdisc",
      "link": "https://discord.gg/Mr9yZbxEZW",
      "tag": "sitebanners",
      "image": "https://radiopanel.s3.nl-ams.scw.cloud/141bc871-f1e5-44b9-98f7-59fd1e31faea/1437e326-90d0-4172-a31c-65fe74cad3b3.png",
      "tenantUuid": "141bc871-f1e5-44b9-98f7-59fd1e31faea",
      "updatedAt": "2020-12-08T10:24:22.488Z",
      "createdAt": "2020-12-08T10:24:22.488Z"
    }
  ],
  "_page": {
    "totalEntities": 1,
    "currentPage": 1,
    "itemsPerPage": 20
  }
}
```
{% endswagger-response %}

{% swagger-response status="204" description="No banners found" %}
```
{
  "_embedded": [

  ],
  "_page": {
    "totalEntities": 0,
    "currentPage": 1,
    "itemsPerPage": 20
  }
}
```
{% endswagger-response %}
{% endswagger %}
