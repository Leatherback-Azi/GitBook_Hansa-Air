---
description: 주간 통계
---

# Weekly Stats

{% swagger baseUrl="SERVER_IP:PORT" path="/v1/user/data/stats/" method="post" summary="Get Stats of period" %}
{% swagger-description %}
get stats between of given dates including that days

\


주어진 날짜 사이의 날짜와 주어진 날짜의 통계를 받아옵니다.
{% endswagger-description %}

{% swagger-parameter in="header" name="Content-Type" type="string" required="true" %}
application/x-www-form-urlencoded
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="string" required="true" %}
Format - Token [token]

\


형식 - Token [token]
{% endswagger-parameter %}

{% swagger-parameter in="body" name="startDate" type="string" required="true" %}
start date of stats

\


통계 시작일
{% endswagger-parameter %}

{% swagger-parameter in="body" name="endDate" type="string" required="true" %}
end date of stats

\


통계 마감일
{% endswagger-parameter %}

{% swagger-response status="200" description="Search completed검색 성공" %}
```
{
    "status": 200,
    "detail": "OK",
    "data": {
        "totalTime": 28051,
        "goals": 40000,
        "stats": [
            {
                "date": "2021-03-07",
                "totalStudyTime": 4312,
                "subject": [
                    {
                        "title": "수학",
                        "time": 3,
                        "color": "#5F79D3"
                    },
                    {
                        "title": "국어",
                        "time": 10,
                        "color": "#FFFFF0"
                    }
                ],
                "goal": 10000
            },
            {
                "date": "2021-03-08",
                "totalStudyTime": 2734,
                "subject": [
                    {
                        "title": "수학",
                        "time": 3,
                        "color": "#5F79D3"
                    },
                    {
                        "title": "국어",
                        "time": 10,
                        "color": "#FFFFF0"
                    }
                ],
                "goal": 10000
            },
            {
                "date": "2021-03-07",
                "totalStudyTime": 0,
                "subject: []
            },
            {
                "date": "2021-03-08",
                "totalStudyTime": 0,
                "subject: []
            },
            {
                "date": "2021-03-09",
                "totalStudyTime": 0,
                "subject: []
            },
            {
                "date": "2021-03-10",
                "totalStudyTime": 0,
                "subject: []
            },
            {
                "date": "2021-03-11",
                "totalStudyTime": 0,
                "subject: []
            },
            {            
                "date": "2021-03-12",
                "totalStudyTime": 7865,
                "subject": [
                    {
                        "title": "수학",
                        "time": 3,
                        "color": "#5F79D3"
                    },
                    {
                        "title": "국어",
                        "time": 10,
                        "color": "#FFFFF0"
                    }
                ],
                "goal": 10000
            },
            {
                "date": "2021-03-13",
                "totalStudyTime": 13140,
                "subject": [
                    {
                        "title": "수학",
                        "time": 3,
                        "color": "#5F79D3"
                    },
                    {
                        "title": "국어",
                        "time": 10,
                        "color": "#FFFFF0"
                    }
                ],
                "goal": 10000
            }
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
