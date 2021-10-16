---
description: 유저 관련 API를 기술합니다.
---

# User

{% swagger method="post" path="/v1/user/manage/signup/" baseUrl="SERVER_IP:PORT" summary="회원가입" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="Content-Type" required="true" %}
application/x-www-form-urlencoded
{% endswagger-parameter %}

{% swagger-parameter in="body" name="password" required="true" %}
비밀번호
{% endswagger-parameter %}

{% swagger-parameter in="body" name="id" type="" required="true" %}
유저ID - 중복 불가
{% endswagger-parameter %}

{% swagger-parameter in="body" name="username" required="true" %}
닉네임
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Successful" %}
성공적으로 계정이 생성 되었을 시

```javascript
{
    "status": 200,
    "detail": "OK",
    "data": {
        "token": "YOUR_TOKEN_HERE"
    }
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="Invalid Request" %}
일부 값이 주어지지 않았을 때

```javascript
{
    "status": 400,
    "detail": "Some Values are missing",
    "data": {}
}
```

이미 유저가 존재 할 때

```
{
    "status": 400,
    "detail": "User Already Exists",
    "data": {}
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="post" path="/v1/user/manage/signin/" baseUrl="SERVER_IP:PORT" summary="로그인" %}
{% swagger-description %}
토큰을 발급 받습니다.
{% endswagger-description %}

{% swagger-parameter in="header" name="Content-Type" required="true" %}
application/x-www-form-urlencoded
{% endswagger-parameter %}

{% swagger-parameter in="body" required="true" name="id" %}
유저 ID
{% endswagger-parameter %}

{% swagger-parameter in="body" name="password" required="true" %}
비밀번호
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Successful" %}
성공적으로 토큰을 발급 받았을 시

```javascript
{
    "status": 200,
    "detail": "OK",
    "data": {
        "token": "YOUR_TOKEN_HERE"
    }
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="Invalid Request" %}
id 또는 비밀번호가 틀렸을 시

```javascript
{
    "status": 400,
    "detail": "Invalid value",
    "data": {}
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="post" path="/v1/user/manage/signup/checkusername/" baseUrl="SERVER_IP:PORT" summary="유저 존재여부 확인" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="Content-Type" required="true" %}
application/x-www-form-urlencoded
{% endswagger-parameter %}

{% swagger-parameter in="body" name="id" required="true" %}
유저 ID
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Successful" %}
기존에 존재하는 유저가 없을 시

```javascript
{
    "status": 200,
    "detail": "No Exiting user",
    "data": {}
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="User Already Exists" %}
기존에 존재하는 유저가 있을 시

```javascript
{
    "status": 400,
    "detail": "There is Exiting user",
    "data": {}
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="/v1/user/manage/tokencheck/" baseUrl="SERVER_IP:PORT" summary="토큰 유효성 확인" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" required="true" %}
형식 - Token [token]
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Correct Token" %}
```javascript
{
    "status": 200,
    "detail": "Valid Token",
    "data": {}
}
```
{% endswagger-response %}

{% swagger-response status="401: Unauthorized" description="Invalid Token" %}
```javascript
{
    "detail": "Invalid token." 
}
```
{% endswagger-response %}
{% endswagger %}

