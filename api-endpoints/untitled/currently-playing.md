# Currently Playing

{% swagger baseUrl="https://api.radiopanel.co" path="/api/v1/song-history/now-playing" method="get" summary="Currently Playing" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="x-tenant" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="header" name="authorization" type="string" %}

{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
    "createdAt": "2020-11-03T15:11:16.911Z",
    "song": {
        "uuid": "e9a1acfc-50dc-4dfe-a7cf-41ead2a88be0",
        "externalId": "98c452a7fb176c539ba786c4e520e50d",
        "title": "Pretty Shining People",
        "artist": "George Ezra",
        "album": "Staying at Tamara's",
        "originalTitle": "George Ezra - Pretty Shining People",
        "previewUrl": "https://p.scdn.co/mp3-preview/622a416ab31a2a1e751bff3ad8ec0e04d45172cc?cid=8cc80ab9c4f846b699befef45cf9dd02",
        "durationMs": 212446,
        "releaseDate": "2018-03-23T00:00:00.000Z",
        "graphic": {
            "large": "https://i.scdn.co/image/ab67616d0000b273103045cd1c29dd16a469f808",
            "small": "https://i.scdn.co/image/ab67616d00004851103045cd1c29dd16a469f808",
            "medium": "https://i.scdn.co/image/ab67616d00001e02103045cd1c29dd16a469f808"
        },
    }
}
```
{% endswagger-response %}
{% endswagger %}
