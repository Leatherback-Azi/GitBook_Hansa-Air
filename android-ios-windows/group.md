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
                "userCount": 6
                "leader": "서승우",
                "firstPlace": "박상아",
                "firstPlaceStudyTime": "4321"
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

{% swagger baseUrl="SERVER_IP:PORT" path="/v1/user/data/group/detail/" method="post" summary="View Group detail" %}
{% swagger-description %}
View specfied group

\


특정 그룹 상세정보 보기
{% endswagger-description %}

{% swagger-parameter in="header" name="Content-Type" type="string" required="true" %}
application/x-www-form-urlencoded
{% endswagger-parameter %}

{% swagger-parameter in="body" name="GroupCode" type="string" required="true" %}
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

{% swagger-parameter in="query" name="GroupCode" type="string" required="true" %}
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

{% swagger baseUrl="SERVER_IP:PORT" path="/v1/user/data/group/detail/user/" method="delete" summary="Delete Group user" %}
{% swagger-description %}
Delete user from group

\


그룹에서 사용자 삭제하기
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" type="string" required="true" %}
Format - Token [token]
{% endswagger-parameter %}

{% swagger-parameter in="query" name="UserMail" required="true" type="string" %}
삭제할 유저의 E-mail
{% endswagger-parameter %}

{% swagger-parameter in="query" name="GroupCode" required="true" type="string" %}
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

{% swagger-response status="401" description="When Token in invalid
토큰이 유효하지 않을 때" %}
```
{
    "detail": "Invalid token." 
}
```
{% endswagger-response %}

{% swagger-response status="404" description="When can't find user
사용자를 찾지 못 하였을 때" %}
```
{
    "status": 200,
    "detail": "User not found"
    "data": {}
}
```
{% endswagger-response %}
{% endswagger %}
