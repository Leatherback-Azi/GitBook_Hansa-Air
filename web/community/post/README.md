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
    "detail": "OK",
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
    "detail": "Some Values are missing",
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
    "detail": "OK",
    "data": {}
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}
존재하는 글이 없을 때

```javascript
{
    "status": 400,
    "detail": "No Exiting Post",
    "data": {}
}
```

일부 값이 전달되지 않았을 때

```javascript
{
    "status": 400,
    "detail": "Some Values are missing",
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
    "detail": "No Permission to Delete",
    "data": {}
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="/v1/user/data/post/" baseUrl="SERVER_IP:PORT" summary="글 조회" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="query" name="pk" %}

{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
글 조회에 성공했을 시 (pk값이 주어졌을 때)

```javascript
{
    "status": 200,
    "detail": "OK",
    "data": {
        "username": "박상아",
        "userImage": "PROFILE_IMG_URL",
        "postDate": "2021-10-14",
        "startDate": "2021-10-07",
        "endDate": "2021-10-14",
        "achievementRate": [
            100,
            176,
            98,
            0,
            32,
            68,
            79
        ],
        "calendarType": "week",  // month, week, day
        "like": 36,
        "idx": 2
    }
}
```

글 리스트 가져오기에 성공 했을 때 (pk값 없을 때)

```javascript
{
    "status": 200,
    "detail": "OK",
    "data": {
        "post":[
            {
                "username": "서승우",
                "userImage": "PROFILE_IMG_URL",
                "postDate": "2021-10-14",
                "startDate": "2021-10-07",
                "endDate": "2021-10-14",
                "achievementRate": [
                    100,
                    176,
                    98,
                    0,
                    32,
                    68,
                    79
                ],
                "calendarType": "week",  // month, week, day
                "like": 36,
                "idx": 1
            },
            {
                "username": "박상아",
                "userImage": "PROFILE_IMG_URL",
                "postDate": "2021-10-14",
                "startDate": "2021-10-07",
                "endDate": "2021-10-14",
                "achievementRate": [
                    100,
                    176,
                    98,
                    0,
                    32,
                    68,
                    79
                ],
                "calendarType": "week",  // month, week, day
                "like": 36,
                "idx": 2
            }
        ]
    }
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}
주어진 pk 값의 글이 없을 때

```javascript
{
    "status": 400,
    "detail": "There is no exiting post",
    "data": {}
}
```
{% endswagger-response %}
{% endswagger %}
