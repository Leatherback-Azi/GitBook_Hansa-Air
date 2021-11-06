# Rank

{% swagger method="get" path="/v1/user/data/rank/" baseUrl="SERVER_IP:PORT" summary="랭크 가져오기" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-response status="200: OK" description="" %}
```javascript
{
    "status": 200,
    "detail": "OK",
    "data": {
        "rank": [
            {
                "rank": 1,
                "username": "박상아",
                "totalStudyTime": 60000,
                "achievementRate": [
                    100,
                    176,
                    98,
                    0,
                    32,
                    68,
                    79
                ],
                "rank": 2,
                "username": "서승우",
                "totalStudyTime": 50000,
                "achievementRate": [
                    100,
                    176,
                    98,
                    0,
                    32,
                    68,
                    79
                ],
            }
        ]
    }
}
```
{% endswagger-response %}
{% endswagger %}
