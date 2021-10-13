---
description: 과목과 관련된 API를 담고 있습니다.
---

# Subject

{% swagger baseUrl="SERVER_IP:PORT" path="/v1/user/data/subject/" method="get" summary="Get subject list, info by date (과목 리스트, 정보 가져오기)" %}
{% swagger-description %}
Get user's subjects

\


사용자의 과목 리스트 가져오기
{% endswagger-description %}

{% swagger-parameter in="header" name="Content-Type" type="string" required="true" %}
application/x-www-form-urlencoded
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="string" required="true" %}
Format - Token [token]
{% endswagger-parameter %}

{% swagger-parameter in="body" name="date" type="string" %}
Formet - YYYY-MM-DD

\


if empty, returns today's info

\


(비었을 시, 오늘 정보를 return 함.)
{% endswagger-parameter %}

{% swagger-response status="200" description="When subject successfully looked up
과목이 성공적으로 조회 되었을 " %}
```
{
    "status": 200,
    "detail": "OK",
    "data": {
        "subject": [
            {
                "title": "수학",
                "time": 3,
                "color": "#ffffff"
            },
            {
                "title": "국어",
                "time": 10,
                "color": "#000000"
            }
        ],
        "goal": 10
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
토큰이 유효하지 않을 " %}
```
{
    "detail": "Invalid token."
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="SERVER_IP:PORT" path="/v1/user/data/subject/manage/" method="post" summary="Make Subject (과목 만들기)" %}
{% swagger-description %}
Make user's custom subject

\


사용자의 커스텀 과목을 만들기
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
Name of subject

\


과목 이름
{% endswagger-parameter %}

{% swagger-parameter in="body" name="color" type="string" required="true" %}
Color of subject

\


과목의 색
{% endswagger-parameter %}

{% swagger-response status="200" description="When subject successfully made
과목이 성공적으로 생성 되었을 때" %}
```
{
    "status": 200,
    "detail": "OK",
    "data": {}
}
```
{% endswagger-response %}

{% swagger-response status="400" description="When some values are missing
값이 모두 들어오지 않았을 때" %}
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
{% endswagger %}

{% swagger baseUrl="SERVER_IP:PORT" path="/v1/user/data/subject/manage/" method="delete" summary="Alter Subject (과목 삭제)" %}
{% swagger-description %}
Delete specified subject

\


사용자의 지정된 과목을 삭제하기
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
Subject name

\


과목 이름
{% endswagger-parameter %}

{% swagger-response status="200" description="When the subject to be deleted exists삭제 하려는 과목이 존재 할 때" %}
```
{
    "status": 200,
    "detail": "OK",
    "data": {}
}
```
{% endswagger-response %}

{% swagger-response status="400" description="When the subject to be deleted dosen't exists (in [subjectTitle], requested subject will be here)
삭제 하려는 과목이 존재 하지 않을 때 ([subjectTitle]에는 입력 받은 과목명이 들어 갑니다.)" %}
```
{
    "status": 400,
    "detail": "Subject [subjectTitle] is not exists",
    "data": {}
}
```
{% endswagger-response %}

{% swagger-response status="401" description="When Token is invalid
토큰이 유효하지 않을 " %}
```
{
    "detail": "Invalid token."
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="SERVER_IP:PORT" path="/v1/user/data/subject/manage/" method="put" summary="Modify Subject (과목 수정)" %}
{% swagger-description %}
Modify specified subject

\


사용자의 지정된 과목을 수정하기
{% endswagger-description %}

{% swagger-parameter in="header" name="Content-Type" type="string" required="true" %}
application/x-www-form-urlencoded
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="string" required="true" %}
Format - Token [token]

\


형식 - Token [token]
{% endswagger-parameter %}

{% swagger-parameter in="body" name="title_new" type="string" %}
New name of subject

\


과목의 새 이름
{% endswagger-parameter %}

{% swagger-parameter in="body" name="title" type="string" required="true" %}
Name of subject

\


과목 이름
{% endswagger-parameter %}

{% swagger-parameter in="body" name="color" type="string" %}
Color of subject

\


과목의 색깔
{% endswagger-parameter %}

{% swagger-response status="200" description="Subject completely modifyed
과목이 성공적으로 수정 되었을 때" %}
```
{
    "status": 200,
    "detail": "OK",
    "data": {}
}
```
{% endswagger-response %}

{% swagger-response status="400" description="When the subject to be deleted dosen't exists (in [subjectTitle], request subject will be here)
삭제 하려는 과목이 존재하지 않을 때 ([subjectTitle]에는 입력 받은 과목명이 들어 갑니다.)" %}
```
{
    "status": 400,
    "detail": "Subject [subjectTitle] is not exists",
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
