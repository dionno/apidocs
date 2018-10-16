# Time Entries

A time entry is a recording of the amount of time a member spent on a specific task.

Using the API you can do the following with time entry data.

| Attribute            | Type     | Description                                                                                                                               |
|----------------------|----------|-------------------------------------------------------------------------------------------------------------------------------------------|
| billable_minutes     | number   | Billable time entry in minutes (For projects that are billable).                                                                                                                 |
| creation_date        | datetime | When this entry has been logged; \ Read only; Can not be updated                                                                          |
| creation_userprofile | number   | Member that originally created the time entry; Read only; Can not be updated.                                                             |
| end_time             | datetime | A date time that represents the end of the time entry; Only available when time tracking mode is set to Start/End for the organization.   |
| guid                 | string   | Global Unique identifier.                                                                                                                        |
| id                   | number   | Unique identifier.                                                                                                                        |
| invoice              | number   | Invoice unique identifier.                                                                                                                |
| member               | number   | Member unique identifier.                                                                                                                 |
| minutes              | number   | Number of minutes logged.                                                                                                                 |
| note                 | string   | Note                                                                                                                                      |
| project              | number   | Project unique identifier.                                                                                                                |
| project_feature      | number   | Project Feature unique identifier.                                                                                                        |
| start_time           | datetime | A date time that represents the start of the time entry; Only available when time tracking mode is set to Start/End for the organization. |
| type                 | string   | Payload type(time_entries).                                                                                                                             |
| working_date         | datetime | A date time that represents the day for the time entry.                                                                                   |

## Viewing a Time Entry

>Example

```shell
curl -H 'Authorization: nut-basic YVl6T1JtbkdpMHhwaXhCdTQ5b3l6ckpqR2ZGY2Z3Z1Eycnh2aGl0ZDphcGlkb2NzQGFwaWRvY3MuY29tOnBhc3N3b3Jk' 
     -H 'api-version: 3' 
	 -H 'OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E' 
	 -X GET https://apps.nutcache.com/webapi/time_entries/1
```

>Response

```json
{
  "time_entries": [
    {
      "type": "time_entries",
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
          "href": "project_features/106963",
          "rel": "project_features",
          "type": "GET"
        },
        {
          "href": "members/9015",
          "rel": "members",
          "type": "GET"
        },
        {
          "href": "time_entries/201001",
          "rel": "self",
          "type": "GET"
        }
      ],
      "invoice": null
    }
  ]
}
```

This API allows you to view the details of a time entry.

<span class="http-method http-get">GET</span> `  /api/time_entries/[id]`

<aside class="notice">
Use 'include' to embed additional details in the response.
</aside>

## List all Time Entries

>Example

```shell
curl -H 'Authorization: nut-basic YVl6T1JtbkdpMHhwaXhCdTQ5b3l6ckpqR2ZGY2Z3Z1Eycnh2aGl0ZDphcGlkb2NzQGFwaWRvY3MuY29tOnBhc3N3b3Jk' 
     -H 'api-version: 3' 
	 -H 'OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E' 
	 -X GET https://apps.nutcache.com/webapi/time_entries
```

>Response

```json
{
  "links": [    
    {
      "href": "time_entries?limit=10&page=2",
      "rel": "navigation-next",
      "type": "GET"
    }
  ],
  "time_entries": [
    {
      "type": "time_entries",
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
          "href": "project_features/106963",
          "rel": "projectitems",
          "type": "GET"
        },
        {
          "href": "members/9015",
          "rel": "members",
          "type": "GET"
        },
        {
          "href": "time_entries/201001",
          "rel": "self",
          "type": "GET"
        }
      ],
      "invoice": null
    }
  ]
}
```

Using this API, you'd be able to fetch a list of time entries.

<span class="http-method http-get">GET</span> `/api/time_entries`

## Include (Time entries)

The following entity types can be included in this payload type

| Type             | Description                                 |
|------------------|---------------------------------------------|
| organizations    | The organisation containing this time entry |
| projects         | The project associated with this time entry |
| project_features | The task associated with this time entry    |
| members          | The member associated with this time entry  |
| invoices         | The invoice associated with this time entry |

## Updating Time Entry

This API allows existing time entries to be modified.</br>

<span class="http-method http-get">PUT</span> `  /api/time_entries/[id]`

The behavior and parameters of the API depend on the following:

>Example

```shell
curl -H 'Authorization: nut-basic YVl6T1JtbkdpMHhwaXhCdTQ5b3l6ckpqR2ZGY2Z3Z1Eycnh2aGl0ZDphcGlkb2NzQGFwaWRvY3MuY29tOnBhc3N3b3Jk' 
     -H 'api-version: 3' 
   	 -H 'OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E' 
	   -X PUT -d {"timeentries": [{"start_time":"2018-09-20T09:00", "end_time":"2018-09-20T21:45","note":"Modified from API 3",          "project_feature":106972,"member":9015,"project":6645,"invoice":""}]} https://apps.nutcache.com/webapi/time_entries/1
```

The start_time and end_time are used to calculate the time entry in minutes when the organization's time_tracking_type is 1=Start/End Time. Other wise these values are ignored.

The billable_minutes is updated when a project is billable otherwise this value is ignored

Invoiced time entries and not permitted

>Example

```shell
curl -H 'Authorization: nut-basic YVl6T1JtbkdpMHhwaXhCdTQ5b3l6ckpqR2ZGY2Z3Z1Eycnh2aGl0ZDphcGlkb2NzQGFwaWRvY3MuY29tOnBhc3N3b3Jk' 
     -H 'api-version: 3' 
   	 -H 'OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E' 
	   -X PUT -d {"timeentries": [{"start_time":"2018-09-20T09:00", "end_time":"2018-09-20T21:45","note":"Modified from API 3",          "project_feature":106972,"member":9015,"project":6645,"invoice":""}]} https://apps.nutcache.com/webapi/time_entries/1?notify=true
```

Time entries for a work_date that have been Approved/Rejected can also notify administrators of modification.

<span class="http-method http-get">GET</span> `/api/time_entries?notify=true`


## Creating Time Entry
