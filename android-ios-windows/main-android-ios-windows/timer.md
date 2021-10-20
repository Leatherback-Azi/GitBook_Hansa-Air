---
description: 타이머와 관련된 API를 담고 있습니다.
---

# Timer

{% swagger baseUrl="SERVER_IP:PORT" path="/v1/user/timer/start/" method="post" summary="Start timer (타이머 시작하기)" %}
{% swagger-description %}
Start user's timer

\


사용자의 타이머를 시작하기
{% endswagger-description %}

{% swagger-parameter in="header" name="Content-Type" type="string" required="true" %}
application/x-www-form-urlencoded
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="string" required="true" %}
Format - Token [token]

\


형식 - Token [token]
{% endswagger-parameter %}

{% swagger-parameter in="body" name="title" type="string" required="true" %}
Subject Title

\


과목 이름
{% endswagger-parameter %}

{% swagger-response status="200" description="When timer successfully started
타이머가 성공적으로 시작 되었을 때" %}
```
{
    "status": 200,
    "detial": "OK",
    "data": {}
}
```
{% endswagger-response %}

{% swagger-response status="400" description="When some values are missing
값이 모두 들어오지 않았을 " %}
```
{
    "status": 400,
    "detail": "Some values are missing",
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

{% swagger-response status="409" description="When timer is already running
타이머가 이미 실행 중 일때" %}
```
{
    "status": 409,
    "detial": "Timer is already running",
    "data": {}
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="SERVER_IP:PORT" path="/v1/user/timer/stop/" method="post" summary="Stop timer (타이머 정지)" %}
{% swagger-description %}
Stop user's timer

\


사용자의 타이머를 정지하기
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" type="string" required="true" %}
Format - Token [token]

\


형식 - Token [token]
{% endswagger-parameter %}

{% swagger-response status="200" description="When timer successfully stopped
타이머가 정상적으로 정지 되었을 때" %}
```
{
    "status": 200,
    "detial": "OK",
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

{% swagger-response status="409" description="When timer is already stopped
타이머가 이미 정지된 상태일 때" %}
```
{
    "status": 409,
    "detial": "Timer is already stopped",
    "data": {}
}
```
{% endswagger-response %}
{% endswagger %}
