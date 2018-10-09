# Timers

A Nutcache timer is a stopwatch used to record time spent on a task.

Using the API you can do the following with timer data.

| Attribute           | Type     | Description                        
|---------------------|----------|------------------------------------
| email_reminder_sent | True     | False  ?????                            
| guid                | string   | Unique identifier                  
| id                  | number   | Unique identifier                  
| max_end_time_utc    | datetime | ?????                              
| member              | number   | Member unique identifier.          
| minutes             | number   | Minutes                            
| project             | number   | Project unique identifier.         
| project_feature     | number   | Project feature unique identifier. 
| status              | string   | Unique identifier.                 
| time_start_local    | datetime | Timer start(local time)            
| time_start_utc      | datetime | Timer start(utc time)              
| type                | string   | Payload type.                      

## Viewing a Timer

This API allows you to view the details of a timer.

<span class="http-method http-get">GET</span> `  /api/timers/[id]`

<aside class="notice">
Use 'include' to embed additional details in the response.

List of includes go here
</aside>

>Example

```shell
curl -H "Authorization: Token token=sfg999666t673t7t82" -H "Content-Type: application/json"-X GET "https://domain.freshsales.io/api/leads/1"
```

>Response

```json
{
  "timers": [
    {
      "type": "timers",
      "id": 3546,
      "guid": "{d663bb56-53b1-477c-8736-56bac487cfc4}",
      "member": 9015,
      "time_start_local": "2018-09-07T11:55:00",
      "max_end_time_utc": "2018-09-08T04:00:04",
      "time_start_utc": "2018-09-07T15:55:47.377",
      "minutes": 0,
      "status": "Started",
      "email_reminder_sent": false,
      "project": 7224,
      "links": [
        {
          "href": "projects/7224",
          "rel": "projects",
          "type": "GET"
        },
        {
          "href": "members/9015",
          "rel": "members",
          "type": "GET"
        },
        {
          "href": "timers/3546",
          "rel": "self",
          "type": "GET"
        }
      ],
      "project_feature": null
    }
  ]
}
```

## List all Timers

Using this API, you'd be able to fetch a list of timers.

<span class="http-method http-get">GET</span> `/api/timers`

>Example

```shell
curl -H "Authorization: Token token=sfg999666t673t7t82" -H "Content-Type: application/json" -X GET "[https://domain.freshsales.io/api/leads/filters](https://domain.freshsales.io/api/leads/filters)"
```

>Response

```json
{
  "links": [
    {
      "href": "timers?limit=10&reference_id=3546&seek_direction=previous",
      "rel": "navigation-previous",
      "type": "GET"
    },
    {
      "href": "timers?limit=10&reference_id=3551&seek_direction=next",
      "rel": "navigation-next",
      "type": "GET"
    }
  ],
  "timers": [
    {
      "type": "timers",
      "id": 3546,
      "guid": "{aa8995ef-59e9-4173-ad5c-b923b46e20d7}",
      "member": 9015,
      "time_start_local": "2018-09-07T11:55:00",
      "max_end_time_utc": "2018-09-08T04:00:04",
      "time_start_utc": "2018-09-07T15:55:47.377",
      "minutes": 0,
      "status": "Started",
      "email_reminder_sent": false,
      "project": 7224,
      "links": [
        {
          "href": "projects/7224",
          "rel": "projects",
          "type": "GET"
        },
        {
          "href": "members/9015",
          "rel": "members",
          "type": "GET"
        },
        {
          "href": "timers/3546",
          "rel": "self",
          "type": "GET"
        }
      ],
      "project_feature": null
    },
    {
      "type": "timers",
      "id": 3547,
      "guid": "{f1cc59f9-2284-497f-bbe5-0b381ff73c9b}",
      "member": 9015,
      "time_start_local": "2018-09-07T11:56:00",
      "max_end_time_utc": "2018-09-08T04:00:04",
      "time_start_utc": "2018-09-07T15:56:06.517",
      "minutes": 0,
      "status": "Started",
      "email_reminder_sent": false,
      "project": 7224,
      "links": [
        {
          "href": "projects/7224",
          "rel": "projects",
          "type": "GET"
        },
        {
          "href": "members/9015",
          "rel": "members",
          "type": "GET"
        },
        {
          "href": "timers/3547",
          "rel": "self",
          "type": "GET"
        }
      ],
      "project_feature": null
    },
    {
      "type": "timers",
      "id": 3548,
      "guid": "{c18e8799-ba44-436f-9bc7-62144e0100fe}",
      "member": 9015,
      "time_start_local": "2018-09-07T11:56:00",
      "max_end_time_utc": "2018-09-08T04:00:04",
      "time_start_utc": "2018-09-07T15:56:10.407",
      "minutes": 0,
      "status": "Started",
      "email_reminder_sent": false,
      "project": 7224,
      "links": [
        {
          "href": "projects/7224",
          "rel": "projects",
          "type": "GET"
        },
        {
          "href": "members/9015",
          "rel": "members",
          "type": "GET"
        },
        {
          "href": "timers/3548",
          "rel": "self",
          "type": "GET"
        }
      ],
      "project_feature": null
    },
    {
      "type": "timers",
      "id": 3549,
      "guid": "{c1c136e5-6a21-4973-b135-c8c5e28541c1}",
      "member": 9015,
      "time_start_local": "2018-09-07T11:56:00",
      "max_end_time_utc": "2018-09-08T04:00:04",
      "time_start_utc": "2018-09-07T15:56:14.533",
      "minutes": 0,
      "status": "Started",
      "email_reminder_sent": false,
      "project": 7224,
      "links": [
        {
          "href": "projects/7224",
          "rel": "projects",
          "type": "GET"
        },
        {
          "href": "members/9015",
          "rel": "members",
          "type": "GET"
        },
        {
          "href": "timers/3549",
          "rel": "self",
          "type": "GET"
        }
      ],
      "project_feature": null
    },
    {
      "type": "timers",
      "id": 3550,
      "guid": "{9f8d4863-4db4-442e-a879-0ba0045ee5b2}",
      "member": 9015,
      "time_start_local": "2018-09-07T11:56:00",
      "max_end_time_utc": "2018-09-08T04:00:04",
      "time_start_utc": "2018-09-07T15:56:15.937",
      "minutes": 0,
      "status": "Started",
      "email_reminder_sent": false,
      "project": 7224,
      "links": [
        {
          "href": "projects/7224",
          "rel": "projects",
          "type": "GET"
        },
        {
          "href": "members/9015",
          "rel": "members",
          "type": "GET"
        },
        {
          "href": "timers/3550",
          "rel": "self",
          "type": "GET"
        }
      ],
      "project_feature": null
    },
    {
      "type": "timers",
      "id": 3551,
      "guid": "{56a51ace-f32f-4734-af65-8f01babf2c19}",
      "member": 9015,
      "time_start_local": "2018-09-07T11:56:00",
      "max_end_time_utc": "2018-09-08T04:00:04",
      "time_start_utc": "2018-09-07T15:56:16.72",
      "minutes": 0,
      "status": "Started",
      "email_reminder_sent": false,
      "project": 7224,
      "links": [
        {
          "href": "projects/7224",
          "rel": "projects",
          "type": "GET"
        },
        {
          "href": "members/9015",
          "rel": "members",
          "type": "GET"
        },
        {
          "href": "timers/3551",
          "rel": "self",
          "type": "GET"
        }
      ],
      "project_feature": null
    }
  ]
}
```