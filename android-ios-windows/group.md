---
description: 그룹 관련 API를 기술하였습니다.
---

# Group

{% swagger baseUrl="SERVER_IP:PORT" path="/v1/user/data/group/" method="get" summary="Get List of User's Group" %}
{% swagger-description %}
Get user's group

\


유저가 속한 그룹의 리스트를 가져옵니다.

\



{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" type="string" required="true" %}
Format - Token [token]
{% endswagger-parameter %}

{% swagger-response status="200" description="When successfully got list" %}
```
{
    "status": 200,
    "detail": "OK",
    "data": {
        "groupList": [
            {
                "code": "G1AY56E7",
                "userCount": 6,
                "leader": "서승우",
                "leaderEmail": "yaz02110207@gmail.com",
                "firstPlace": "박상아",
                "firstPlaceStudyTime": 4321
            },
        ]
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

{% swagger baseUrl="SERVER_IP:PORT" path="/v1/user/data/group/" method="post" summary="Create User Group" %}
{% swagger-description %}
Create User's own group

\


그룹 생성하기
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" type="string" required="true" %}
Format - Token [token]
{% endswagger-parameter %}

{% swagger-response status="200" description="Successfully group created
성공적으로 그룹이 생성 되었을 때" %}
```
{
    "status": 200,
    "detail": "OK",
    "data": {
        "code": "GROUP_CODE"
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

{% swagger-response status="409" description="When User's group had already created
유저의 그룹이 이미 존재 할 때" %}
```
{
    "status": 409,
    "detail": "Group is already exists",
    "data": {}
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="delete" path="/v1/user/data/group/" baseUrl="SERVER_IP:PORT" summary="Delete User Group" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" type="String" required="true" %}
Token [token]
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
성공적으로 삭제 되었을 때

```javascript
{
    "status": 200,
    "detail": "OK",
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

{% swagger-response status="409: Conflict" description="" %}
그룹이 없거나 이미 삭제되었을 때

```javascript
{
    "status": 409,
    "detail": "There is no Group",
    "data": {}
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="SERVER_IP:PORT" path="/v1/user/data/group/detail/" method="post" summary="View Group detail" %}
{% swagger-description %}
View specfied group

\


특정 그룹 상세정보 보기
{% endswagger-description %}

{% swagger-parameter in="header" name="Content-Type" type="string" required="true" %}
application/x-www-form-urlencoded
{% endswagger-parameter %}

{% swagger-parameter in="body" name="groupCode" type="string" required="true" %}
Group's Code

\


그룹의 코드
{% endswagger-parameter %}

{% swagger-response status="200" description="Successful response
성공적으로 받아 왔을 때" %}
```
{
    "status": 200,
    "detail": "OK",
    "data": {
        "code": "G1AY56E7",
        "userList":[
            {
                "name": "박상아",
                "email": "USER'S_E-MAIL",
                "profileImg": "USER'S_PROFILE_IMG",
                "todayStudyTime": "4321",
                "isItOwner": false,
                "rank": 1
            },
            {
                "name": "서승우",
                "email": "USER'S_E-MAIL",
                "profileImg": "USER'S_PROFILE_IMG",
                "todayStudyTime": "3421",
                "isItOwner": true,
                "rank": 2
            },
        ]
    }
}
```
{% endswagger-response %}

{% swagger-response status="400" description="When invalid group code given
잘못된 그룹 코드가 주어졌을 때" %}
```
{
    "status": 400,
    "detail": "invalid group code",
    "data": {}
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="SERVER_IP:PORT" path="/v1/user/data/group/detail/user/" method="put" summary="Join Group" %}
{% swagger-description %}
Join group

\


그룹 참가하기
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" type="string" required="true" %}
Format - Token [token]
{% endswagger-parameter %}

{% swagger-parameter in="query" name="groupCode" type="string" required="true" %}
그룹 코드
{% endswagger-parameter %}

{% swagger-response status="200" description="When successfully joind to group
그룹에 성공적으로 참가하였을 때" %}
```
{
    "status": 200,
    "detail": "OK",
    "data": {
        "code": "GROUP_CODE"
    }
}
```
{% endswagger-response %}

{% swagger-response status="400" description="When invalid group code given
잘못된 그룹 코드가 주어졌을 때" %}
```
{
    "status": 400,
    "detail": "invalid group code",
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

{% swagger-response status="409" description="When user is already joind to that group
유저가 이미 해당 그룹에 참가 되어 있을 시" %}
```
{
    "status": 409,
    "detail": "Already joind group",
    "data": {}
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="delete" path="/v1/user/data/group/detail/user/" baseUrl="SERVER_IP:PORT" summary="Leave Group" %}
{% swagger-description %}
그룹에서 탈퇴하기
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" type="String" required="true" %}
Token [token]
{% endswagger-parameter %}

{% swagger-parameter in="query" name="groupCode" type="String" required="true" %}
그룹 코드
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
성공적으로 탈퇴 되었을 때

```javascript
{
    "status": 200,
    "detail": "OK",
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

{% swagger-response status="409: Conflict" description="" %}
해당 그룹이 없거나 해당 그룹에 참가된 상태가 아닐 때

```javascript
{
    "status": 409,
    "detail": "There is no Group",
    "data": {}
}
```

그룹장이 탈퇴하려 시도 할 때

```javascript
{
    "status": 409,
    "detail": "Cannot Exit",
    "data": {}
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="SERVER_IP:PORT" path="/v1/user/data/group/detail/user/manage/" method="delete" summary="Remove Group user" %}
{% swagger-description %}
Remove user from group

\


그룹에서 사용자 추방하기
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" type="string" required="true" %}
Format - Token [token]
{% endswagger-parameter %}

{% swagger-parameter in="query" name="userMail" required="true" type="string" %}
삭제할 유저의 E-mail
{% endswagger-parameter %}

{% swagger-parameter in="query" name="groupCode" required="true" type="string" %}
그룹 코드
{% endswagger-parameter %}

{% swagger-response status="200" description="When successfully user had deleted.
유저가 성공적으로 삭제 되었을 때" %}
```
{
    "status": 200,
    "detail": "OK",
    "data": {
        "code": "GROUP_CODE"
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

권한이 없을 때

```javascript
{
    "status": 401,
    "detail": "Unauthorized",
    "data": {}
}
```
{% endswagger-response %}

{% swagger-response status="404" description="사용자를 찾지 못 하였을 때" %}
그룹에서 사용자를 찾지 못 하였을 때

```
{
    "status": 200,
    "detail": "User not found"
    "data": {}
}
```
{% endswagger-response %}

{% swagger-response status="409: Conflict" description="" %}
해당 그룹이 없거나 해당 그룹에 참가된 상태가 아닐 때

```javascript
{
    "status": 409,
    "detail": "There is no Group",
    "data": {}
}
```

자기 자신을 추방하려 할 때

```javascript
{
    "status": 409,
    "detail": "Cannot Exit",
    "data": {}
}
```
{% endswagger-response %}
{% endswagger %}
