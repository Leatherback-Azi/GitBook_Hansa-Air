---
description: 투두리스트 API
---

# TodoList

{% swagger baseUrl="SERVER_IP:PORT" path="/v1/user/data/subject/checklist/" method="get" summary="Get TodoList (투두리스트 가져오기)" %}
{% swagger-description %}
유저의 체크리스트를 가져옵니다.
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" type="string" required="true" %}
Format - Token [token]
{% endswagger-parameter %}

{% swagger-parameter in="query" name="date" type="string" required="true" %}
 조회할 날짜

\


Format - YYYY-MM-DD
{% endswagger-parameter %}

{% swagger-response status="200" description="When checklist successfully looked up
체크리스트가 성공적으로 조회 되었을 때" %}
```
{
    "status": 200,
    "detail": "OK",
    "data": {
        "date": "YYYY-MM-DD",
        "memo": "잠이 오네요",
        "subjects": [ 
            {
                "subject": "프실",
                "todoList": [
                    {
                        "isitDone": false,
                        "todo": "뭐하지"
                    }
                ]
            },
            {
                "subject": "한사랑공기",
                "todoList": [
                    {
                        "isitDone": false,
                        "todo": "TestMockServer 만들어서 AWS에 올리기"
                    }
                ]
            }
        ]
    }
}
```
{% endswagger-response %}

{% swagger-response status="400" description="When invalid date given
잘못된 날짜가 주어졌을 때" %}
```
{
    "status": 400,
    "detail": "invalid date given",
    "data": {}
}
```
{% endswagger-response %}

{% swagger-response status="401" description="When Token is invalid
토큰이 유효하지 않을 때" %}
```
{
    "detail": "Invalid token."
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="post" path="/v1/user/data/subject/checklist/" baseUrl="SERVER_IP:PORT" summary="Post/Modify TodoList (투두리스트 등록 및 수정하기)" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="Content-Type" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="subject" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="date" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="todo" required="true" %}

{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
성공적으로 등록 되었을 때

```javascript
{
    "status": 200,
    "detail": "OK",
    "data": {}
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}
잘못된 날짜가 주어졌을 때

```javascript
{
    "status": 400,
    "detail": "invalid date given",
    "data": {}
}
```

일부 값이 주어지지 않았을 때

```javascript
{
    "status": 400,
    "detail": "Some values are missing",
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

{% swagger method="post" path="/v1/user/data/subject/checklist/memo/" baseUrl="SERVER_IP:PORT" summary="Post/Modify Memo (메모 수정 또는 등록하기)" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="Conetent-Type" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="date" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="memo" required="true" %}

{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
성공적으로 등록 되었을 때

```javascript
{
    "status": 200,
    "detail": "OK",
    "data": {}
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}
잘못된 날짜가 주어졌을 때

```javascript
{
    "status": 400,
    "detail": "invalid date given",
    "data": {}
}
```

일부 값이 주어지지 않았을 때

```javascript
{
    "status": 400,
    "detail": "Some values are missing",
    "data": {}
}
```
{% endswagger-response %}

{% swagger-response status="401" description="" %}
토큰이 잘못 되었을 때

```javascript
{
    "detail": "Invalid token."
}
```
{% endswagger-response %}
{% endswagger %}
