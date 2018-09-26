# Organizations

A Nutcache organization is an entity comprising multiple members with various roles and projects with varying constraints and goals.

Using the API, you can do the following with organization data.

<table>
  <tr>
   <td><strong>Attribute</strong>
   </td>
   <td><strong>Type</strong>
   </td>
   <td><strong>Description</strong>
   </td>
  </tr>
  <tr>
   <td>active_user_count
   </td>
   <td>number
   </td>
   <td>Number of active members.
   </td>
  </tr>
  <tr>
   <td>address
   </td>
   <td>string
   </td>
   <td>Address
   </td>
  </tr>
  <tr>
   <td>city
   </td>
   <td>string
   </td>
   <td>Name of the city.
   </td>
  </tr>
  <tr>
   <td>country
   </td>
   <td>number
   </td>
   <td>Unique identifier for a country. 
<p>
include=countries
   </td>
  </tr>
  <tr>
   <td>currency
   </td>
   <td>number
   </td>
   <td>Unique identifier for a currency.
<p>
include=currencies
   </td>
  </tr>
  <tr>
   <td>date_format
   </td>
   <td>number
   </td>
   <td>Enum for date format set for the organization:
<p>
0 = ISO format (yyyy-MM-dd)
<p>
1 = US format w/ dash (MM-dd-yyyy)
<p>
2 = US format w/ slash (MM/dd/yyyy)
<p>
3 = International format w/ dash    
<p>
      (dd-MM-yyyy)
<p>
4 = International format w/ slash 
<p>
      (dd/MM/yyyy)
<p>
5 = International format w/ dots 
<p>
      (dd.MM.yyyy)
   </td>
  </tr>
  <tr>
   <td>email
   </td>
   <td>string
   </td>
   <td>Email contact.
   </td>
  </tr>
  <tr>
   <td>guid
   </td>
   <td>string
   </td>
   <td>Alternative unique identifier.
   </td>
  </tr>
  <tr>
   <td>id
   </td>
   <td>number
   </td>
   <td>Unique identifier.
   </td>
  </tr>
  <tr>
   <td>is_demo
   </td>
   <td>True|False
   </td>
   <td>Indicates if the organization is for demo purposes.
   </td>
  </tr>
  <tr>
   <td>is_owner
   </td>
   <td>True|False
   </td>
   <td>Indicates if the current user is the owner.
   </td>
  </tr>
  <tr>
   <td>last_activity_date
   </td>
   <td>datetime
   </td>
   <td>Last date/time this Organization was accessed.
   </td>
  </tr>
  <tr>
   <td>logo_url
   </td>
   <td>string
   </td>
   <td>URL for organization logo.
   </td>
  </tr>
  <tr>
   <td>name
   </td>
   <td>string
   </td>
   <td>Organization name.
   </td>
  </tr>
  <tr>
   <td>notification_count
   </td>
   <td>number
   </td>
   <td>Number of notifications.
   </td>
  </tr>
  <tr>
   <td>phone
   </td>
   <td>string
   </td>
   <td>Phone number.
   </td>
  </tr>
  <tr>
   <td>state
   </td>
   <td>state
   </td>
   <td>State
<p>
include=states
   </td>
  </tr>
  <tr>
   <td>status
   </td>
   <td>number
   </td>
   <td>0 = Active  \
1 = Inactive \
2 = Expired
   </td>
  </tr>
  <tr>
   <td>time_format
   </td>
   <td>number
   </td>
   <td>Enum for time format set for the organization:
<p>
0 = ISO format (HH:mm) 
<p>
1 = AM/PM format (hh:mm tt)
   </td>
  </tr>
  <tr>
   <td>time_rounding
   </td>
   <td>number
   </td>
   <td>Enum for time rounding set for time entries in the organization:
<p>
0 = None
<p>
1 = Round to nearest
<p>
2 = Round up to nearest
   </td>
  </tr>
  <tr>
   <td>time_rounding_minutes
   </td>
   <td>number
   </td>
   <td>Number, in minutes, set to automatically round time entries, if time rounding is set.
   </td>
  </tr>
  <tr>
   <td>time_span_format
   </td>
   <td>number
   </td>
   <td>Enum for duration (time) format set for the organization:
<p>
0 = Decimal (e.g. 2.5)
<p>
1 = Short time (e.g. 2:30)
   </td>
  </tr>
  <tr>
   <td>time_tracking_type
   </td>
   <td>number
   </td>
   <td>Enum for time tracking mode set for the organization:
<p>
0 = Duration
<p>
1 = Start/End time
   </td>
  </tr>
  <tr>
   <td>type
   </td>
   <td>organizations
   </td>
   <td>Type of response
   </td>
  </tr>
  <tr>
   <td>website
   </td>
   <td>string
   </td>
   <td>Site identifier for the organization.
   </td>
  </tr>
  <tr>
   <td>zip_code
   </td>
   <td>string
   </td>
   <td>Zip code.
   </td>
  </tr>
</table>

## Viewing an Organization

This API allows you to view the details of an organization.

<span class="http-method http-get">GET</span> ` /api/organizations/<id>`

URL Parameters

<table>
  <tr>
   <td>Parameter
   </td>
   <td>Description
   </td>
  </tr>
  <tr>
   <td>id
   </td>
   <td>The organization id to retrieve.
   </td>
  </tr>
</table>

<aside class="notice">
Use 'include' to embed additional details in the response.

List of includes go here

Countries, states, currencies
</aside>

>Example

```shell

curl -H 'Authorization: nut-basic YVl6T1JtbkdpMHhwaXhCdTQ5b3l6bUpqR29GY2Z3Z1Eycnh2aGl0dDpudXRjYWNoZTFAZ21haWwuY29tOkR5bmFjb20xMjM=' -H 'api-version: 3' -X GET https://devapps.nutcache.com/webapi/organizations/6745

```

>Response

```json

{
  "organizations": [
    {
      "type": "organizations",
      "id": 1660,
      "guid": "7b1fb609-eba9-4b4d-91a8-b136cecaddaf",
      "name": "Green Bay Packers",
      "email": "1660@yopmail.com",
      "address": null,
      "city": null,
      "zip_code": null,
      "phone": null,
      "country": 4,
      "state": null,
      "currency": 3,
      "website": null,
      "logo_url": "https://storage.bhs1.cloud.ovh.net:443/v1/AUTH_5174164456074a2b81d0dfa449a372ef/logo_public_dev/logo-default.png?v=",
      "last_activity_date": "2018-01-11T18:59:50.07",
      "notification_count": 168,
      "is_owner": true,
      "is_demo": false,
      "date_format": 0,
      "time_format": 0,
      "time_span_format": 1,
      "time_rounding": 0,
      "time_rounding_minutes": 0,
      "time_tracking_type": 0,
      "active_user_count": 1,
      "links": [
        {
          "href": "countries/4",
          "rel": "countries",
          "type": "GET"
        },
        {
          "href": "currencies/3",
          "rel": "currencies",
          "type": "GET"
        },
        {
          "href": "organizations/1660",
          "rel": "self",
          "type": "GET"
        }
      ]
    }
  ]
}

```


## List all Organizations

Using this API, you'd be able to fetch a list of organizations.

>Example

```shell

`curl -H 'Authorization: nut-basic YVl6T1JtbkdpMHhwaXhCdTQ5b3l6bUpqR29GY2Z3Z1Eycnh2aGl0dDpudXRjYWNoZTFAZ21haWwuY29tOkR5bmFjb20xMjM=' -H 'api-version: 3' -X GET https://devapps.nutcache.com/webapi/organizations

```

>Response

```json

{
  "links": [
    {
      "href": "organizations?limit=10&page=1",
      "rel": "navigation-prev",
      "type": "GET"
    },
    {
      "href": "organizations?limit=10&page=3",
      "rel": "navigation-next",
      "type": "GET"
    }
  ],
  "organizations": [
    {
      "type": "organizations",
      "id": 1660,
      "guid": "7b1fb609-eba9-4b4d-91a8-b136cecaddaf",
      "name": "Green Bay Hackers",
      "email": "1660@yopmail.com",
      "address": null,
      "city": null,
      "zip_code": null,
      "phone": null,
      "country": 4,
      "state": null,
      "currency": 3,
      "website": null,
      "logo_url": "https://storage.bhs1.cloud.ovh.net:443/v1/AUTH_5174164456074a2b81d0dfa449a372ef/logo_public_dev/logo-default.png?v=",
      "last_activity_date": "2018-01-11T18:59:50.07",
      "notification_count": 167,
      "is_owner": true,
      "is_demo": false,
      "date_format": 0,
      "time_format": 0,
      "time_span_format": 1,
      "time_rounding": 0,
      "time_rounding_minutes": 0,
      "time_tracking_type": 0,
      "active_user_count": 1,
      "links": [
        {
          "href": "countries/4",
          "rel": "countries",
          "type": "GET"
        },
        {
          "href": "currencies/3",
          "rel": "currencies",
          "type": "GET"
        },
        {
          "href": "organizations/1660",
          "rel": "self",
          "type": "GET"
        }
      ]
    },
    {
      "type": "organizations",
      "id": 1686,
      "guid": "846e176e-7c4b-4bfd-a894-c98f2988927e",
      "name": "Justice League",
      "email": "nutcache1@gmail.com",
      "address": null,
      "city": null,
      "zip_code": null,
      "phone": null,
      "country": 2,
      "state": null,
      "currency": 2,
      "website": null,
      "logo_url": null,
      "last_activity_date": "2018-09-06T16:02:09.44",
      "notification_count": 167,
      "is_owner": true,
      "is_demo": false,
      "date_format": 0,
      "time_format": 0,
      "time_span_format": 1,
      "time_rounding": 0,
      "time_rounding_minutes": 0,
      "time_tracking_type": 0,
      "active_user_count": 14,
      "links": [
        {
          "href": "countries/2",
          "rel": "countries",
          "type": "GET"
        },
        {
          "href": "currencies/2",
          "rel": "currencies",
          "type": "GET"
        },
        {
          "href": "organizations/1686",
          "rel": "self",
          "type": "GET"
        }
      ]
    }
  ]
}

```