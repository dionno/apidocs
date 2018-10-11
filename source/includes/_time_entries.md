# Time Entries

A time entry is a recording of the amount of time a member spent on a specific task.

Using the API you can do the following with time entry data.

| Attribute            | Type     | Description                                                                                                                               |
|----------------------|----------|-------------------------------------------------------------------------------------------------------------------------------------------|
| billable_minutes     | number   | Number of active members.                                                                                                                 |
| creation_date        | datetime | When this entry has been logged; \ Read only; Can not be updated                                                                          |
| creation_userprofile | number   | Member that created originally the time entry; Read only; Can not be updated.                                                             |
| end_time             | datetime | A date time that represents the end of the time entry; Only available when time tracking mode is set to Start/End for the organization.   |
| guid                 | string   | Unique identifier.                                                                                                                        |
| id                   | number   | Unique identifier.                                                                                                                        |
| invoice              | number   | Invoice unique identifier.                                                                                                                |
| member               | number   | Member unique identifier.                                                                                                                 |
| minutes              | number   | Number of minutes logged.                                                                                                                 |
| note                 | string   | Note                                                                                                                                      |
| project              | number   | Project unique identifier.                                                                                                                |
| project_feature      | number   | Project Feature unique identifier.                                                                                                        |
| start_time           | datetime | A date time that represents the start of the time entry; Only available when time tracking mode is set to Start/End for the organization. |
| type                 | string   | Payload type.                                                                                                                             |
| working_date         | datetime | A date time that represents the day for the time entry.                                                                                   |

## Viewing a Time Entry

This API allows you to view the details of a time entry.

<span class="http-method http-get">GET</span> `  /api/timeentries/[id]`

<aside class="notice">
Use 'include' to embed additional details in the response.
</aside>

>Example

```shell
curl -H "Authorization: Token token=sfg999666t673t7t82" -H "Content-Type: application/json"-X GET "https://domain.freshsales.io/api/leads/1"
```

>Response

```json
{
  "timeentries": [
    {
      "type": "timeentries",
      "id": 201001,
      "guid": "{71094532-926e-41a1-bda5-3ce0bcb40180}",
      "billable_minutes": 0,
      "creation_date": "2018-03-06T22:01:09.25",
      "creation_userprofile": 2814,
      "working_date": "2018-03-07T00:00:00",
      "minutes": 480,
      "note": null,
      "project_feature": 106963,
      "member": 9015,
      "project": 6641,
      "links": [
        {
          "href": "projects/6641",
          "rel": "projects",
          "type": "GET"
        },
        {
          "href": "projectitems/106963",
          "rel": "projectitems",
          "type": "GET"
        },
        {
          "href": "members/9015",
          "rel": "members",
          "type": "GET"
        },
        {
          "href": "timeentries/201001",
          "rel": "self",
          "type": "GET"
        }
      ],
      "invoice": null
    }
  ]
}
```

## List all Time Entries

Using this API, you'd be able to fetch a list of time entries.

<span class="http-method http-get">GET</span> `/api/timeentries`

>Example

```shell
curl -H "Authorization: Token token=sfg999666t673t7t82" -H "Content-Type: application/json" -X GET "[https://domain.freshsales.io/api/leads/filters](https://domain.freshsales.io/api/leads/filters)"
```

>Response

```json
{
  "links": [    
    {
      "href": "timeentries?limit=10&page=2",
      "rel": "navigation-next",
      "type": "GET"
    }
  ],
  "timeentries": [
    {
      "type": "timeentries",
      "id": 201001,
      "guid": "{66700be6-2d82-4fde-bd69-cd2a1161e0d4}",
      "billable_minutes": 0,
      "creation_date": "2018-03-06T22:01:09.25",
      "creation_userprofile": null,
      "working_date": "2018-03-07T00:00:00",
      "minutes": 480,
      "note": null,
      "project_feature": 106963,
      "member": 9015,
      "project": 6641,
      "links": [
        {
          "href": "projects/6641",
          "rel": "projects",
          "type": "GET"
        },
        {
          "href": "projectitems/106963",
          "rel": "projectitems",
          "type": "GET"
        },
        {
          "href": "members/9015",
          "rel": "members",
          "type": "GET"
        },
        {
          "href": "timeentries/201001",
          "rel": "self",
          "type": "GET"
        }
      ],
      "invoice": null
    },
    {
      "type": "timeentries",
      "id": 201002,
      "guid": "{9b6f6be9-881f-4b94-b500-2e03c9f8cf8e}",
      "billable_minutes": 0,
      "creation_date": "2018-03-06T22:07:02.793",
      "creation_userprofile": null,
      "working_date": "2018-03-05T00:00:00",
      "minutes": 480,
      "note": null,
      "project_feature": 106963,
      "member": 9015,
      "project": 6641,
      "links": [
        {
          "href": "projects/6641",
          "rel": "projects",
          "type": "GET"
        },
        {
          "href": "projectitems/106963",
          "rel": "projectitems",
          "type": "GET"
        },
        {
          "href": "members/9015",
          "rel": "members",
          "type": "GET"
        },
        {
          "href": "timeentries/201002",
          "rel": "self",
          "type": "GET"
        }
      ],
      "invoice": null
    },
    {
      "type": "timeentries",
      "id": 201003,
      "guid": "{c7dd6c43-3e77-4c92-8e4c-917e5c4a247b}",
      "billable_minutes": 0,
      "creation_date": "2018-03-06T22:07:15.97",
      "creation_userprofile": null,
      "working_date": "2018-03-05T00:00:00",
      "minutes": 480,
      "note": null,
      "project_feature": 106963,
      "member": 9015,
      "project": 6641,
      "links": [
        {
          "href": "projects/6641",
          "rel": "projects",
          "type": "GET"
        },
        {
          "href": "projectitems/106963",
          "rel": "projectitems",
          "type": "GET"
        },
        {
          "href": "members/9015",
          "rel": "members",
          "type": "GET"
        },
        {
          "href": "timeentries/201003",
          "rel": "self",
          "type": "GET"
        }
      ],
      "invoice": null
    },
    {
      "type": "timeentries",
      "id": 201186,
      "guid": "{947fe429-66ee-4530-886f-4f2f53add355}",
      "billable_minutes": 720,
      "creation_date": "2018-04-24T12:20:06.683",
      "creation_userprofile": null,
      "working_date": "2018-04-10T00:00:00",
      "minutes": 720,
      "note": null,
      "project_feature": 107871,
      "member": 9015,
      "project": 7289,
      "links": [
        {
          "href": "projects/7289",
          "rel": "projects",
          "type": "GET"
        },
        {
          "href": "projectitems/107871",
          "rel": "projectitems",
          "type": "GET"
        },
        {
          "href": "members/9015",
          "rel": "members",
          "type": "GET"
        },
        {
          "href": "timeentries/201186",
          "rel": "self",
          "type": "GET"
        }
      ],
      "invoice": null
    },
    {
      "type": "timeentries",
      "id": 201187,
      "guid": "{65cefc03-c6cd-4af4-a43e-cd78f8b2a4ef}",
      "billable_minutes": 120,
      "creation_date": "2018-04-24T12:21:03.967",
      "creation_userprofile": null,
      "working_date": "2018-04-10T00:00:00",
      "minutes": 120,
      "note": null,
      "project_feature": 107872,
      "member": 9015,
      "project": 7289,
      "links": [
        {
          "href": "projects/7289",
          "rel": "projects",
          "type": "GET"
        },
        {
          "href": "projectitems/107872",
          "rel": "projectitems",
          "type": "GET"
        },
        {
          "href": "members/9015",
          "rel": "members",
          "type": "GET"
        },
        {
          "href": "timeentries/201187",
          "rel": "self",
          "type": "GET"
        }
      ],
      "invoice": null
    },
    {
      "type": "timeentries",
      "id": 201331,
      "guid": "{6048aabb-d28f-4f26-8954-274c2570edf4}",
      "billable_minutes": 1200,
      "creation_date": "2018-05-17T13:53:24.027",
      "creation_userprofile": null,
      "working_date": "2018-04-11T00:00:00",
      "minutes": 1200,
      "note": null,
      "project_feature": 107872,
      "member": 9280,
      "project": 7289,
      "links": [
        {
          "href": "projects/7289",
          "rel": "projects",
          "type": "GET"
        },
        {
          "href": "projectitems/107872",
          "rel": "projectitems",
          "type": "GET"
        },
        {
          "href": "members/9280",
          "rel": "members",
          "type": "GET"
        },
        {
          "href": "timeentries/201331",
          "rel": "self",
          "type": "GET"
        }
      ],
      "invoice": null
    },
    {
      "type": "timeentries",
      "id": 201332,
      "guid": "{136934bf-ef97-493c-8e45-81fb10d88f2a}",
      "billable_minutes": 720,
      "creation_date": "2018-05-17T13:53:41.87",
      "creation_userprofile": null,
      "working_date": "2018-04-12T00:00:00",
      "minutes": 720,
      "note": "Testing notes!",
      "project_feature": 107872,
      "member": 9225,
      "project": 7289,
      "links": [
        {
          "href": "projects/7289",
          "rel": "projects",
          "type": "GET"
        },
        {
          "href": "projectitems/107872",
          "rel": "projectitems",
          "type": "GET"
        },
        {
          "href": "members/9225",
          "rel": "members",
          "type": "GET"
        },
        {
          "href": "timeentries/201332",
          "rel": "self",
          "type": "GET"
        }
      ],
      "invoice": null
    },
    {
      "type": "timeentries",
      "id": 201333,
      "guid": "{035519de-aa2e-4348-a003-8eb6ecaea174}",
      "billable_minutes": 0,
      "creation_date": "2018-05-28T16:16:57.227",
      "creation_userprofile": null,
      "working_date": "2018-05-28T00:00:00",
      "minutes": 240,
      "note": null,
      "project_feature": 111911,
      "member": 9231,
      "project": 7289,
      "links": [
        {
          "href": "projects/7289",
          "rel": "projects",
          "type": "GET"
        },
        {
          "href": "projectitems/111911",
          "rel": "projectitems",
          "type": "GET"
        },
        {
          "href": "members/9231",
          "rel": "members",
          "type": "GET"
        },
        {
          "href": "timeentries/201333",
          "rel": "self",
          "type": "GET"
        }
      ],
      "invoice": null
    },
    {
      "type": "timeentries",
      "id": 203423,
      "guid": "{64f09e77-67e3-42fa-8292-6f6baf2064a7}",
      "billable_minutes": 0,
      "creation_date": "2018-07-09T13:03:56.833",
      "creation_userprofile": null,
      "working_date": "2018-07-09T00:00:00",
      "minutes": 1,
      "note": "hello",
      "project_feature": 119685,
      "member": 9015,
      "project": 7224,
      "links": [
        {
          "href": "projects/7224",
          "rel": "projects",
          "type": "GET"
        },
        {
          "href": "projectitems/119685",
          "rel": "projectitems",
          "type": "GET"
        },
        {
          "href": "members/9015",
          "rel": "members",
          "type": "GET"
        },
        {
          "href": "timeentries/203423",
          "rel": "self",
          "type": "GET"
        }
      ],
      "invoice": null
    },
    {
      "type": "timeentries",
      "id": 206770,
      "guid": "{33be84f1-34e3-43b8-8c11-59c1ea11eb00}",
      "billable_minutes": 3,
      "creation_date": "2018-08-20T13:56:25.207",
      "creation_userprofile": null,
      "working_date": "2018-08-20T00:00:00",
      "minutes": 3,
      "note": null,
      "project_feature": 119685,
      "member": 9015,
      "project": 7224,
      "links": [
        {
          "href": "projects/7224",
          "rel": "projects",
          "type": "GET"
        },
        {
          "href": "projectitems/119685",
          "rel": "projectitems",
          "type": "GET"
        },
        {
          "href": "members/9015",
          "rel": "members",
          "type": "GET"
        },
        {
          "href": "timeentries/206770",
          "rel": "self",
          "type": "GET"
        }
      ],
      "invoice": null
    }
  ]
}
```

## Updating Time Entry

Time entry \
Depends on organisation setting Time Tracking mode \
Depends on if project is billable. \
Start and Endtime is timespan only \

## Creating Time Entry

## Include (Time entries)

The following entity types can be included in this payload type

| Type             | Description                                 |
|------------------|---------------------------------------------|
| organizations    | The organisation containing this time entry |
| projects         | The project associated with this time entry |
| project_features | The task associated with this time entry    |
| members          | The member associated with this time entry  |
| invoices         | The invoice associated with this time entry |