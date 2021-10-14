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
        "totalTime": 3000,
        "goals": 95,
        "stats": [
            {
                "date": "2021-03-07",
                "totalStudyTime": 40312,     // 총 공부시간
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
                "goal": 10000                   // 목표시간
            },
            {
                "date": "2021-03-08",
                "totalStudyTime": 40312,     // 총 공부시간
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
                "goal": 10000                   // 목표시간
            },
            {
                "date": "2021-03-12",
                "totalStudyTime": 40312,     // 총 공부시간
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
                "goal": 10000                   // 목표시간
            },
            {
                "date": "2021-03-13",
                "totalStudyTime": 40312,     // 총 공부시간
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
                "goal": 10000                   // 목표시간
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
