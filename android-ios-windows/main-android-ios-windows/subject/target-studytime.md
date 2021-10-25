---
description: 목표시간 설정 관련 API를 담고 있습니다.
---

# Target StudyTime

{% swagger method="post" path="/v1/user/data/subject/targettime/" baseUrl="SERVER_IP:PORT" summary="목표시간 설정" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="targetTime" required="true" %}

{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
성공적으로 값이 설정 되었을 때

```javascript
{
    "status": 200,
    "detail": "OK",
    "data": {}
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}
일부 값이 전달 되지 않았을 때

```javascript
{
    "status": 400,
    "detail": "Some values are missing",
    "data": {}
}
```
{% endswagger-response %}

{% swagger-response status="401: Unauthorized" description="" %}
토큰이 잘 못 되었을 때

```javascript
{
    "detail": "Invalid token."
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="/v1/user/data/subject/targettime/" baseUrl="SERVER_IP:PORT" summary="" %}
{% swagger-description %}

{% endswagger-description %}
{% endswagger %}
