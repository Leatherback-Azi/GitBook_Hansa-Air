---
description: 유저 관리/로그인/회원가입
---

# User

{% swagger baseUrl="SERVER_IP:PORT" path="/v1/user/manage/signin/" method="post" summary="Sign Up/Sign In - Request E-mail Auth (회원가입/로그인, 이메일 인증 요청)" %}
{% swagger-description %}
Request to send Auth Email, SignUp

\


회원가입, 인증 메일 전송을 요청합니다.
{% endswagger-description %}

{% swagger-parameter in="header" name="Content-Type" type="string" required="true" %}
application/x-www-form-urlencoded
{% endswagger-parameter %}

{% swagger-parameter in="body" name="email" type="string" required="true" %}
User's E-mail

\


유저 이메일
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
When E-mail successfully sent - New Account

이메일 전송에 성공 했을 때 - 새로운 계정

```
{
    "status": 200,
    "detail": "OK",
    "data": {
        "isEmailExist": false,        
        "emailSent": true           
    }
}
```

When E-mail successfully sent - Exiting Account

이메일 전송에 성공 했을 때 - 존재하는 계정

```json
{
    "status": 200,
    "detail": "OK",
    "data": {
        "isEmailExist": true,        
        "emailSent": true           
    }
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}
When faild to send E-mail

이메일 전송에 실패 했을 때

```json
{
    "status": 400,
    "detail": "Faild to send E-mail",
    "data": {}
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="SERVER_IP:PORT" path="/v1/user/manage/signin/" method="put" summary="Sign Up/Sign In - Auth via E-mail auth code (회원가입/로그인, 이메일 인증 코드로 인증하기)" %}
{% swagger-description %}
Send auth code to sign up and get Token.

\


(인증 코드를 보내고 회원가입 및 토큰을 받습니다.)
{% endswagger-description %}

{% swagger-parameter in="header" name="Content-Type" type="string" required="true" %}
application/x-www-form-urlencoded
{% endswagger-parameter %}

{% swagger-parameter in="body" name="auth" type="string" required="true" %}
auth code which sent to e-mail

\


이메일로 보내진 인증 코드
{% endswagger-parameter %}

{% swagger-parameter in="body" name="email" type="string" required="true" %}
user's e-mail to auth

\


인증할 유저의 이메일
{% endswagger-parameter %}

{% swagger-response status="200" description="When auth code is correct
인증 코드가 맞았을 때" %}
```
{
    "status": 200,
    "detail": "OK",
    "data": {
        "token": "YOUR_TOKEN_HERE"
    }
}
```
{% endswagger-response %}

{% swagger-response status="401" description="When auth code is incorrect
인증 코드가 틀렸을 때" %}
```
{
    "status": 401,
    "detail": "invalid auth code",
    "data": {
        "token": ""
    }
}
```
{% endswagger-response %}

{% swagger-response status="410" description="When time limit exceeded (5min)
5분 시간 제한이 초과 되었을 때" %}
```
{
    "status": 410,
    "detail": "time limit exceeded (5min)",
    "data": {
        "token": ""
    }
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="SERVER_IP:PORT" path="/v1/user/info/manage/basic/name/" method="put" summary="Modify User -  name (유저 이름 수정)" %}
{% swagger-description %}
Modify user's name

\


유저의 이름 수정
{% endswagger-description %}

{% swagger-parameter in="header" name="Content-Type" type="string" required="true" %}
application/x-www-form-urlencoded
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="string" required="true" %}
Format - Token [token]

\


형식 - Token [token]
{% endswagger-parameter %}

{% swagger-parameter in="body" name="name" type="string" %}
User's new name (Korean, up to 7 chars, no spaces)

\


유저의 새로운 이름 (한국어, 7자 이하, 공백 없음)
{% endswagger-parameter %}

{% swagger-response status="200" description="When username successfully edited
유저 이름이 성공적으로 수정 되었을 때" %}
```
{
    "status": 200,
    "detail": "OK",
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

{% swagger baseUrl="SERVER_IP:PORT" path="/v1/user/info/manage/basic/email/" method="post" summary="Modify User - E-mail request (유저 이메일 수정 요청)" %}
{% swagger-description %}
Modify user's e-mail

\


유저의 이메일 수정
{% endswagger-description %}

{% swagger-parameter in="header" name="Content-Type" type="string" required="true" %}
application/x-www-form-urlencoded
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="string" required="true" %}
Format - Token [token]

\


형식 - Token [token]
{% endswagger-parameter %}

{% swagger-parameter in="body" name="email" type="string" required="true" %}
User's new e-mail

\


유저의 새로운 이메일
{% endswagger-parameter %}

{% swagger-response status="200" description="OK" %}
이미 존재하는 이메일이 없고, 성공적으로 이메일이 전송 되었을 때

```
{
    "status": 200,
    "detail": "OK",
    "data": {
        "isEmailExist": false,        
        "emailSent": true           
    }
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}
같은 메일이 이미 존재 할 때

```javascript
{
    "status": 400,
    "detail": "Given email already Exists",
    "data": {
        "isEmailExist": true,        
        "emailSent": false       
    }
}
```
{% endswagger-response %}

{% swagger-response status="401" description="Unauthorized" %}
잘못 된 토큰이 전달 되었을 때

```
{
    "detail": "Invalid token." 
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="put" path="/v1/user/info/manage/basic/email/" baseUrl="SERVER_IP:PORT" summary="Modify User -  Auth via E-mail code (이메일 코드로 인증하기)" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="Content-Type" required="true" %}
application/x-www-form-urlencoded
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" required="true" %}
Token [token]
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
인증 코드가 맞았을 때

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

{% swagger-response status="401: Unauthorized" description="" %}
인증 코드가 틀렸을 때

```javascript
{
    "status": 401,
    "detail": "invalid auth code",
    "data": {
        "token": ""
    }
}
```

토큰이 유효하지 않을 때

```json
{
    "detail": "Invalid token."
}
```
{% endswagger-response %}

{% swagger-response status="410: Gone" description="" %}
5분 시간 제한이 초과 되었을 때

```javascript
{
    "status": 410,
    "detail": "time limit exceeded (5min)",
    "data": {
        "token": ""
    }
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="SERVER_IP:PORT" path="/v1/user/info/basic/" method="get" summary="Get user info - Basic (유저 기본 정보 받아오기)" %}
{% swagger-description %}
Get user's basic info (e-mail, name)

\


유저 기본 정보 가져오기 (e-mail, name)
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" type="string" required="true" %}
Format - Token [token]

\


형식 - Token [token]
{% endswagger-parameter %}

{% swagger-response status="200" description="When Token is valid
토큰이 유효할 때" %}
```
{
    "status": 200,
    "detail": "OK",
    "data": {
        "email": "USER'S_E-MAIL",
        "name": "USER'S_NAME"
    }
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
