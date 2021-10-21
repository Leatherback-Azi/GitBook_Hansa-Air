---
description: 커뮤니티 기능 중 게시물에 관한 API입니다.
---

# Post

{% swagger method="post" path="/v1/user/data/post/" baseUrl="SERVER_IP:PORT" summary="글 쓰기" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" required="true" %}
Token [token]
{% endswagger-parameter %}

{% swagger-parameter in="query" name="startDate" required="true" %}
YYYY-MM-DD
{% endswagger-parameter %}

{% swagger-parameter in="query" name="endDate" required="true" %}
YYYY-MM-DD
{% endswagger-parameter %}

{% swagger-parameter in="query" name="calendarType" required="true" %}
month, week, day
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
성공적으로 글이 생성되었을 때

```javascript
{
    "status": 200,
    "detial": "OK",
    "data": {
        "pk": 1
    }
}
```
{% endswagger-response %}

{% swagger-response status="401: Unauthorized" description="" %}
토큰이 유효하지 않을 때

```javascript
{
    "detail": "Invalid token."
}
```
{% endswagger-response %}
{% endswagger %}
