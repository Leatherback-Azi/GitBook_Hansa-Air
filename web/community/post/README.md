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

{% swagger-response status="400: Bad Request" description="" %}
일부 값이 전달되지 않았을 때

```javascript
{
    "status": 400,
    "detial": "Some Values are missing",
    "data": {}
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

{% swagger method="delete" path="/v1/user/data/post/" baseUrl="SERVER_IP:PORT" summary="글 삭제" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" required="true" %}
Token [token]
{% endswagger-parameter %}

{% swagger-parameter in="query" name="pk" required="true" %}
게시물 idx(pk)
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
성공적으로 글이 삭제 되었을 때

```javascript
{
    "status": 200,
    "detial": "OK",
    "data": {}
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}
존재하는 글이 없을 때

```javascript
{
    "status": 400,
    "detial": "No Exiting Post",
    "data": {}
}
```

일부 값이 전달되지 않았을 때

```javascript
{
    "status": 400,
    "detial": "Some Values are missing",
    "data": {}
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

삭제 권한이 없는 글일 때

```javascript
{
    "status": 401,
    "detial": "No Permission to Delete",
    "data": {}
}
```
{% endswagger-response %}
{% endswagger %}
