# Timers

A Nutcache timer is a stopwatch used to record time spent on a task.

Using the API you can do the following with timer data.

| Attribute           | Type     | Description                        |
|---------------------|----------|------------------------------------|
| email_reminder_sent | boolean  | ?????                              |
| guid                | string   | Unique identifier                  |
| id                  | number   | Unique identifier                  |
| max_end_time_utc    | datetime | ?????                              |
| member              | number   | Member unique identifier.          |
| minutes             | number   | Minutes                            |
| project             | number   | Project unique identifier.         |
| project_feature     | number   | Project feature unique identifier. |
| status              | string   | Unique identifier.                 |
| time_start_local    | datetime | Timer start(local time)            |
| time_start_utc      | datetime | Timer start(utc time)              |
| type                | string   | Payload type.                      |  

## Viewing a Timer

This API allows you to view the details of a timer.

<span class="http-method http-get">GET</span> `  /api/timers/[id]`

<aside class="notice">
Use 'include' to embed additional details in the response.
</aside>

>Example

```shell
curl -H "Authorization: nut-basic YVl6T1JtbkdpMHhwaXhCdTQ5b3l6ckpqR2ZGY2Z3Z1Eycnh2aGl0ZDphcGlkb2NzQGFwaWRvY3MuY29tOnBhc3N3b3Jk" 
     -H "api-version: 3" 
	 -H "OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E" 
	 -X GET https://apps.nutcache.com/webapi/timers/3546
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
      "status": "1",
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
curl -H "Authorization: nut-basic YVl6T1JtbkdpMHhwaXhCdTQ5b3l6ckpqR2ZGY2Z3Z1Eycnh2aGl0ZDphcGlkb2NzQGFwaWRvY3MuY29tOnBhc3N3b3Jk" 
     -H "api-version: 3" 
	 -H "OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E" 
	 -X GET https://apps.nutcache.com/webapi/timers
```

>Response

```json
{
  "links": [
    {
      "href": "timers?limit=10&page=2",
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
      "status": "1",
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

## Include (Timers)

The following entity types can be included in this payload type

| Type             | Description                                      |
|------------------|--------------------------------------------------|
| projects         | The project associated with the timer            |
| project_features | The task associated with the timer               |
| sprint_stories   | The project board card associated with the timer |
| members          | The member associated with the timer             |