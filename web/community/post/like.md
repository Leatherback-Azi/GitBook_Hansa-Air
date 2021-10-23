# Like

{% swagger method="post" path="/v1/user/data/post/like/" baseUrl="SERVER_IP:PORT" summary="좋아요 누르기/취소하기" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="query" name="pk" %}

{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
좋아요가 추가 되었을 시

```javascript
{
    "status": 200,
    "detial": "OK",
    "data": {
        "isChecked": true,
    }
}
```

좋아요가 취소 되었을 시

```javascript
{
    "status": 200,
    "detial": "OK",
    "data": {
        "isChecked": false,
    }
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}
해당 글이 존재하지 않을 때

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
토큰이 잘못 되었을 때

```javascript
{
    "detail": "Invalid token."
}
```
{% endswagger-response %}
{% endswagger %}
