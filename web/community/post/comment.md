---
description: 댓글 관련 API를 기술합니다
---

# Comment

{% swagger method="post" path="/v1/user/data/post/comment/" baseUrl="SERVER_IP:PORT" summary="댓글 등록" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="content" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="idx" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-Type" required="true" %}

{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
성공적으로 댓글이 등록 되었을 때

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
토큰이 잘못되었을 때

```javascript
{
    "detail": "Invalid token."
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="delete" path="/v1/user/data/post/comment/" baseUrl="SERVER_IP:PORT" summary="댓글 삭제" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" %}

{% endswagger-parameter %}

{% swagger-parameter in="query" name="pk" %}

{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
성공적으로 댓글이 삭제 되었을 때

```javascript
{
    "status": 200,
    "detial": "OK",
    "data": {}
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}
존재하는 댓글이 없을 때

```javascript
{
    "status": 400,
    "detial": "No Exiting comment",
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
잘못된 토큰일 때

```javascript
{
    "detail": "Invalid token."
}
```

삭제 권한이 없을 때

```javascript
{
    "status": 401,
    "detial": "No Permission to Delete",
    "data": {}
}
```
{% endswagger-response %}
{% endswagger %}
