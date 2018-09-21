Nutcache API

# Introduction

To do!

[[TOC]]

# Getting Started

## Public Key

To use the Nutcache API, an owner must first generate a public key. This action can be done directly in Nutcache under the "My account -> My Profile" menu. From the My Profile dialog, select the “Manage Access Keys” tab and click the “+ Generate new key” to continue.

To do! Add screen captures

## Authentication

Authentication info must be provided along with your request within the Authorization header. The authentication is made of the public key, a username and password, all separated by a colon. The authentication info must be encoded in Base 64.

Authorization: nut-basic [Base64(*public-key*:*username*:*password*)]

## Schema

Blank Fields: Blank fields are made null instead of being omitted.

Timestamps:All timestamps are returned in the UTC format, YYYY-MM-DDTHH:MM:SSZ. For example, 2016-02-13T23:27:49ZDate Fields:Input for date fields is expected to be in one of the following formats:YYYY-MM-DD YYYY-MM-DDTHH:MM YYYY-MM-DDTHH:MMZ YYYY-MM-DDTHH:MM:SS YYYY-MM-DDTHH:MM:SSZ YYYY-MM-DDTHH:MM:SS±hh:mm YYYY-MM-DDTHH:MM:SS±hh YYYY-MM-DDTHH:MM:SS±hhmm If the time zone information is not present, it will be assumed to be in UTC.A few valid date fields - 2016-02-15T21:16:25Z ,    2012-12-24T12:56:15+05:30,    2010-03-23T12:00

## Organization Context

An organization context is required when making requests. To do this, simply include the organization GUID, which can be retrieved via the Organization API from the request header.

ie

curl -H "Authorization: YVl6T1JtbkdpMHhwaXhCdTQ5b3l6bUpqR29GY2Z3Z1Eycnh2aGl0dDpudXRjYWNoZTFAZ21haWwuY29tOkR5bmFjb20xMjM=" -H "api-version: 3" **-H "OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E"** -X GET https://devapps.nutcache.com/webapi/customers

## Embedding

You can request for additional entities using the "include" keyword up to one level. For example, you can embed an organization entity when requesting a list of projects.

curl -i -H 'Authorization: nut-basic YVl6T1JtbkdpMHhwaXhCdTQ5b3l6bUpqR29GY2Z3Z1Eycnh2aGl0dDpudXRjYWNoZTFAZ21haWwuY29tOkR5bmFjb20xMjM=' -H 'api-version: 3' -H 'CompanyGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E' -X GET https://devapps.nutcache.com/webapi/projects?**include=organizations**

Refer to each resource for more information on which entities can be included.

## Errors

API requests that result in errors will return an appropriate HTTP status code to help you identify the type of error and fix it. You can use the table below to understand what each code means. 

<table>
  <tr>
    <td>HTTP Status Code</td>
    <td>Text</td>
    <td>Description</td>
  </tr>
  <tr>
    <td>400</td>
    <td>Client or Validation Error</td>
    <td>Indicates that the request is not in the correct format.</td>
  </tr>
  <tr>
    <td>401</td>
    <td>Authentication Failure</td>
    <td>Indicates that the Authorization header is either missing or incorrect. You can learn more about the Authorization header here.</td>
  </tr>
  <tr>
    <td>403</td>
    <td>Access Denied</td>
    <td>This indicates that the user whose credentials were used in making this request was not authorized to perform this API call.</td>
  </tr>
  <tr>
    <td>404</td>
    <td>Requested Resource not Found</td>
    <td>This status code is returned when the request contains invalid ID/Nutcache domain in the URL or an invalid URL itself. For example, an API call to retrieve a project with an invalid ID will return a HTTP 404 status code to let you know that no such project exists.</td>
  </tr>
  <tr>
    <td>429</td>
    <td>Too Many Requests	</td>
    <td>This status code appears when the user has exceeded the API limit set per ??? per account. In Nutcache, this limit is ???? API requests per ???? per account.</td>
  </tr>
  <tr>
    <td>500</td>
    <td>Unexpected Server Error</td>
    <td>This indicates an error on Nutcache's side. Please email us at support@nutcache.com with your API script along with the response headers. We will reach out to you and fix this ASAP.</td>
  </tr>
</table>


## Pagination

API responses that return a list of objects, such as Projects, Customers or Time Entries are paginated. To scroll through the pages, add the parameter page to the query string. The page number starts with 1. By default, the number of objects returned per page is 10 and is limited to 100. For example, if you’d like to retrieve the Time Entries from 11 to 20 use,

### Sample Code

curl -i -H "Authorization: nut-basic YVl6T1JtbkdpMHhwaXhCdTQ5b3l6bUpqR29GY2Z3Z1Eycnh2aGl0dDpudXRjYWNoZTFAZ21haWwuY29tOkR5bmFjb20xMjM=" -H "api-version: 3" -H "OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E" -X GET "https://devapps.nutcache.com/webapi/customers?limit=10&page=2

href=customers?limit=10&page=2"

# Organizations

A Nutcache organization is an entity comprising multiple members with various roles and projects with varying constraints and goals.

Using the API, you can do the following with organization data.

<table>
  <tr>
    <td>Attribute</td>
    <td>Type</td>
    <td>Description</td>
  </tr>
  <tr>
    <td>active_user_count</td>
    <td>number</td>
    <td>Number of active members.</td>
  </tr>
  <tr>
    <td>address</td>
    <td>string</td>
    <td>Address</td>
  </tr>
  <tr>
    <td>city</td>
    <td>string</td>
    <td>Name of the city.</td>
  </tr>
  <tr>
    <td>country</td>
    <td>number</td>
    <td>Unique identifier for a country. 
include=countries</td>
  </tr>
  <tr>
    <td>currency</td>
    <td>number</td>
    <td>Unique identifier for a currency.
include=currencies</td>
  </tr>
  <tr>
    <td>date_format</td>
    <td>number</td>
    <td>Enum for date format set for the organization:
0 = ISO format (yyyy-MM-dd)
1 = US format w/ dash (MM-dd-yyyy)
2 = US format w/ slash (MM/dd/yyyy)
3 = International format w/ dash    
      (dd-MM-yyyy)
4 = International format w/ slash 
      (dd/MM/yyyy)
5 = International format w/ dots 
      (dd.MM.yyyy)</td>
  </tr>
  <tr>
    <td>email</td>
    <td>string</td>
    <td>Email contact.</td>
  </tr>
  <tr>
    <td>guid</td>
    <td>string</td>
    <td>Alternative unique identifier.</td>
  </tr>
  <tr>
    <td>id</td>
    <td>number</td>
    <td>Unique identifier.</td>
  </tr>
  <tr>
    <td>is_demo</td>
    <td>True|False</td>
    <td>Indicates if the organization is for demo purposes.</td>
  </tr>
  <tr>
    <td>is_owner</td>
    <td>True|False</td>
    <td>Indicates if the current user is the owner.</td>
  </tr>
  <tr>
    <td>last_activity_date</td>
    <td>datetime</td>
    <td>Last date/time this Organization was accessed.</td>
  </tr>
  <tr>
    <td>logo_url</td>
    <td>string</td>
    <td>URL for organization logo.</td>
  </tr>
  <tr>
    <td>name</td>
    <td>string</td>
    <td>Organization name.</td>
  </tr>
  <tr>
    <td>notification_count</td>
    <td>number</td>
    <td>Number of notifications.</td>
  </tr>
  <tr>
    <td>phone</td>
    <td>string</td>
    <td>Phone number.</td>
  </tr>
  <tr>
    <td>state</td>
    <td>state</td>
    <td>State
include=states</td>
  </tr>
  <tr>
    <td>status</td>
    <td>number</td>
    <td>0 = Active 1 = Inactive2 = Expired</td>
  </tr>
  <tr>
    <td>time_format</td>
    <td>number</td>
    <td>Enum for time format set for the organization:
0 = ISO format (HH:mm) 
1 = AM/PM format (hh:mm tt)</td>
  </tr>
  <tr>
    <td>time_rounding</td>
    <td>number</td>
    <td>Enum for time rounding set for time entries in the organization:
0 = None
1 = Round to nearest
2 = Round up to nearest</td>
  </tr>
  <tr>
    <td>time_rounding_minutes</td>
    <td>number</td>
    <td>Number, in minutes, set to automatically round time entries, if time rounding is set.</td>
  </tr>
  <tr>
    <td>time_span_format</td>
    <td>number</td>
    <td>Enum for duration (time) format set for the organization:
0 = Decimal (e.g. 2.5)
1 = Short time (e.g. 2:30)</td>
  </tr>
  <tr>
    <td>time_tracking_type</td>
    <td>number</td>
    <td>Enum for time tracking mode set for the organization:
0 = Duration
1 = Start/End time</td>
  </tr>
  <tr>
    <td>type</td>
    <td>organizations</td>
    <td>Type of response</td>
  </tr>
  <tr>
    <td>website</td>
    <td>string</td>
    <td>Site identifier for the organization.</td>
  </tr>
  <tr>
    <td>zip_code</td>
    <td>string</td>
    <td>Zip code.</td>
  </tr>
</table>


## Viewing an Organization

This API allows you to view the details of an organization.

GET  /api/organizations/[id]

Use ‘include’ to embed additional details in the response.

List of includes go here

Countries, states, currencies

```shell

curl -H 'Authorization: nut-basic YVl6T1JtbkdpMHhwaXhCdTQ5b3l6bUpqR29GY2Z3Z1Eycnh2aGl0dDpudXRjYWNoZTFAZ21haWwuY29tOkR5bmFjb20xMjM=' -H 'api-version: 3' -X GET https://devapps.nutcache.com/webapi/organizations/6745

```

>The above command returns JSON structured like this:

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

Using this API, you’d be able to fetch a list of organizations.

```shell

curl -H 'Authorization: nut-basic YVl6T1JtbkdpMHhwaXhCdTQ5b3l6bUpqR29GY2Z3Z1Eycnh2aGl0dDpudXRjYWNoZTFAZ21haWwuY29tOkR5bmFjb20xMjM=' -H 'api-version: 3' -X GET https://devapps.nutcache.com/webapi/organizations

```

>The above command returns JSON structured like this:

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

# Projects

A Nutcache project is a planned work or activity that is to be completed over a period of time using Agile or Scrum methodology.

Using the API you can do the following with project data.

<table>
  <tr>
    <td>Attribute</td>
    <td>Type</td>
    <td>Description</td>
  </tr>
  <tr>
    <td>billing_approved_entries_only</td>
    <td>True|False</td>
    <td>????</td>
  </tr>
  <tr>
    <td>billing_invoice_method_fixed_fee</td>
    <td>number</td>
    <td>?????</td>
  </tr>
  <tr>
    <td>billing_invoice_method_hourly_rate</td>
    <td>number</td>
    <td>?????</td>
  </tr>
  <tr>
    <td>billing_method</td>
    <td>string</td>
    <td>Billing method.????bug returns string</td>
  </tr>
  <tr>
    <td>budget_approved_only</td>
    <td>True|False</td>
    <td></td>
  </tr>
  <tr>
    <td>budget_restrictive</td>
    <td>True|False</td>
    <td></td>
  </tr>
  <tr>
    <td>budget_scope</td>
    <td>string</td>
    <td></td>
  </tr>
  <tr>
    <td>budget_type</td>
    <td>string</td>
    <td></td>
  </tr>
  <tr>
    <td>code</td>
    <td>string</td>
    <td></td>
  </tr>
  <tr>
    <td>organization</td>
    <td>number</td>
    <td>Unique identifier for an organization.</td>
  </tr>
  <tr>
    <td>customer</td>
    <td>number</td>
    <td>Unique identifier for a customer.</td>
  </tr>
  <tr>
    <td>description</td>
    <td>string</td>
    <td>Project description.</td>
  </tr>
  <tr>
    <td>display_color</td>
    <td>string</td>
    <td>HTML color</td>
  </tr>
  <tr>
    <td>EffectiveBudgetAmount</td>
    <td>number</td>
    <td>??????</td>
  </tr>
  <tr>
    <td>EffectiveBudgetMinutes</td>
    <td>number</td>
    <td>??????</td>
  </tr>
  <tr>
    <td>end_date</td>
    <td>datetime</td>
    <td>Phone number.</td>
  </tr>
  <tr>
    <td>id</td>
    <td>number</td>
    <td>Unique identifier.</td>
  </tr>
  <tr>
    <td>primary_contact_email</td>
    <td>string</td>
    <td>Primary contact email.</td>
  </tr>
  <tr>
    <td>primary_contact_name</td>
    <td>string</td>
    <td>Primary contact name.</td>
  </tr>
  <tr>
    <td>primary_contact_phone</td>
    <td>string</td>
    <td>Primary contact phone</td>
  </tr>
  <tr>
    <td>project_budget</td>
    <td>number</td>
    <td>????</td>
  </tr>
  <tr>
    <td>project_type</td>
    <td>number</td>
    <td>Type of project.</td>
  </tr>
  <tr>
    <td>secondary_contact_email</td>
    <td>string</td>
    <td>Secondary contact email.</td>
  </tr>
  <tr>
    <td>secondary_contact_name</td>
    <td>string</td>
    <td>Secondary contact name.</td>
  </tr>
  <tr>
    <td>secondary_contact_phone</td>
    <td>string</td>
    <td>Secondary contact phone.</td>
  </tr>
  <tr>
    <td>start_date</td>
    <td>datetime</td>
    <td>Project start date.</td>
  </tr>
  <tr>
    <td>status</td>
    <td>number</td>
    <td>Project status(to enumerate)</td>
  </tr>
  <tr>
    <td>type</td>
    <td>string</td>
    <td>Payload type(projects)</td>
  </tr>
  <tr>
    <td>Vision</td>
    <td>string</td>
    <td>Project vision</td>
  </tr>
</table>


## Viewing a Project

This API allows you to view the details of a project.

GET  /api/projects/[id]

Use ‘include’ to embed additional details in the response.

List of includes go here

To do

### Sample code | Curl(to do)

curl -H 'Authorization: nut-basic YVl6T1JtbkdpMHhwaXhCdTQ5b3l6bUpqR29GY2Z3Z1Eycnh2aGl0dDpudXRjYWNoZTFAZ21haWwuY29tOkR5bmFjb20xMjM=' -H 'api-version: 3' -H 'OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E' -X GET https://devapps.nutcache.com/webapi/projects/6640

## Response

{

  "projects": [

    {

      "type": "projects",

      "id": 6640,

      "Organization": 1686,

      "code": "Agile sample project (non-billable)",

      "display_color": "#607d8b",

      "status": 1,

      "links": [

        {

          "href": "organizations/1686",

          "rel": "organizations",

          "type": "GET"

        },

        {

          "href": "customers/143222",

          "rel": "customers",

          "type": "GET"

        },

        {

          "href": "projects/6640",

          "rel": "self",

          "type": "GET"

        }

      ],

      "project_type": 0,

      "description": "Leverage the Agile approach to organize and manage your projects with boards.",

      "Vision": "&amp;nbsp;",

      "primary_contact_email": null,

      "primary_contact_name": null,

      "primary_contact_phone": null,

      "secondary_contact_email": null,

      "secondary_contact_name": null,

      "secondary_contact_phone": null,

      "start_date": "2018-01-22T00:00:00",

      "end_date": null,

      "budget_scope": "Global",

      "budget_type": "WorkedHours",

      "EffectiveBudgetAmount": 0,

      "EffectiveBudgetMinutes": 0,

      "budget_approved_only": false,

      "budget_restrictive": false,

      "billing_method": "NotBillable",

      "billing_invoice_method_fixed_fee": 0,

      "billing_invoice_method_hourly_rate": 0,

      "billing_approved_entries_only": false,

      "customer": 143222,

      "project_budget": null

    }

  ]

}

## List all Projects

Using this API, you’d be able to fetch a list of projects.

### Sample code | Curl

curl -H 'Authorization: nut-basic YVl6T1JtbkdpMHhwaXhCdTQ5b3l6bUpqR29GY2Z3Z1Eycnh2aGl0dDpudXRjYWNoZTFAZ21haWwuY29tOkR5bmFjb20xMjM=' -H 'api-version: 3' -H 'OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E' -X GET https://devapps.nutcache.com/webapi/projects

#### Response

{

  "links": [

    {

      "href": "projects?limit=10&reference_id=6640&seek_direction=previous",

      "rel": "navigation-previous",

      "type": "GET"

    },

    {

      "href": "projects?limit=10&reference_id=6691&seek_direction=next",

      "rel": "navigation-next",

      "type": "GET"

    }

  ],

  "projects": [

    {

      "type": "projects",

      "id": 6640,

      "Organization": 1686,

      "code": "Agile sample project (non-billable)",

      "display_color": "#607d8b",

      "status": 1,

      "links": [

        {

          "href": "organizations/1686",

          "rel": "organizations",

          "type": "GET"

        },

        {

          "href": "customers/143222",

          "rel": "customers",

          "type": "GET"

        },

        {

          "href": "projects/6640",

          "rel": "self",

          "type": "GET"

        }

      ],

      "project_type": 0,

      "description": "Leverage the Agile approach to organize and manage your projects with boards.",

      "Vision": "&amp;nbsp;",

      "primary_contact_email": null,

      "primary_contact_name": null,

      "primary_contact_phone": null,

      "secondary_contact_email": null,

      "secondary_contact_name": null,

      "secondary_contact_phone": null,

      "start_date": "2018-01-22T00:00:00",

      "end_date": null,

      "budget_scope": "Global",

      "budget_type": "WorkedHours",

      "EffectiveBudgetAmount": 0,

      "EffectiveBudgetMinutes": 0,

      "budget_approved_only": false,

      "budget_restrictive": false,

      "billing_method": "NotBillable",

      "billing_invoice_method_fixed_fee": 0,

      "billing_invoice_method_hourly_rate": 0,

      "billing_approved_entries_only": false,

      "customer": 143222,

      "project_budget": null

    },

    {

      "type": "projects",

      "id": 6641,

      "Organization": 1686,

      "code": "Scrum sample project (non-billable)",

      "display_color": "#fb8c00",

      "status": 1,

      "links": [

        {

          "href": "organizations/1686",

          "rel": "organizations",

          "type": "GET"

        },

        {

          "href": "customers/143222",

          "rel": "customers",

          "type": "GET"

        },

        {

          "href": "project_budgets/4280",

          "rel": "project_budgets",

          "type": "GET"

        },

        {

          "href": "projects/6641",

          "rel": "self",

          "type": "GET"

        }

      ],

      "project_type": 1,

      "description": "Manage your Scrum projects via a series of iterations called sprints.",

      "Vision": null,

      "primary_contact_email": null,

      "primary_contact_name": null,

      "primary_contact_phone": null,

      "secondary_contact_email": null,

      "secondary_contact_name": null,

      "secondary_contact_phone": null,

      "start_date": "2018-01-22T00:00:00",

      "end_date": null,

      "sprint_duration": 2,

      "budget_scope": "Global",

      "budget_type": "WorkedHours",

      "EffectiveBudgetAmount": 0,

      "EffectiveBudgetMinutes": 0,

      "budget_approved_only": false,

      "budget_restrictive": false,

      "billing_method": "NotBillable",

      "billing_invoice_method_fixed_fee": 0,

      "billing_invoice_method_hourly_rate": 0,

      "billing_approved_entries_only": false,

      "customer": 143222,

      "project_budget": 4280

    },

    {

      "type": "projects",

      "id": 6644,

      "Organization": 1686,

      "code": "Tax Test - non taxable client!",

      "display_color": "#ff5722",

      "status": 0,

      "links": [

        {

          "href": "organizations/1686",

          "rel": "organizations",

          "type": "GET"

        },

        {

          "href": "customers/143222",

          "rel": "customers",

          "type": "GET"

        },

        {

          "href": "projects/6644",

          "rel": "self",

          "type": "GET"

        }

      ],

      "project_type": 1,

      "description": null,

      "Vision": null,

      "primary_contact_email": null,

      "primary_contact_name": null,

      "primary_contact_phone": null,

      "secondary_contact_email": null,

      "secondary_contact_name": null,

      "secondary_contact_phone": null,

      "start_date": null,

      "end_date": null,

      "sprint_duration": 2,

      "budget_scope": "Global",

      "budget_type": "WorkedHours",

      "EffectiveBudgetAmount": 0,

      "EffectiveBudgetMinutes": 0,

      "budget_approved_only": false,

      "budget_restrictive": false,

      "billing_method": "TaskRate",

      "billing_invoice_method_fixed_fee": 0,

      "billing_invoice_method_hourly_rate": 0,

      "billing_approved_entries_only": false,

      "customer": 143222,

      "project_budget": null

    },

    {

      "type": "projects",

      "id": 6645,

      "Organization": 1686,

      "code": "Tax test - Ont Client",

      "display_color": "#303f9f",

      "status": 1,

      "links": [

        {

          "href": "organizations/1686",

          "rel": "organizations",

          "type": "GET"

        },

        {

          "href": "customers/143224",

          "rel": "customers",

          "type": "GET"

        },

        {

          "href": "projects/6645",

          "rel": "self",

          "type": "GET"

        }

      ],

      "project_type": 1,

      "description": null,

      "Vision": null,

      "primary_contact_email": null,

      "primary_contact_name": null,

      "primary_contact_phone": null,

      "secondary_contact_email": null,

      "secondary_contact_name": null,

      "secondary_contact_phone": null,

      "start_date": null,

      "end_date": null,

      "sprint_duration": 2,

      "budget_scope": "Global",

      "budget_type": "WorkedHours",

      "EffectiveBudgetAmount": 0,

      "EffectiveBudgetMinutes": 0,

      "budget_approved_only": false,

      "budget_restrictive": false,

      "billing_method": "TaskRate",

      "billing_invoice_method_fixed_fee": 0,

      "billing_invoice_method_hourly_rate": 0,

      "billing_approved_entries_only": false,

      "customer": 143224,

      "project_budget": null

    },

    {

      "type": "projects",

      "id": 6647,

      "Organization": 1686,

      "code": "Scrum sample project 2",

      "display_color": "#fb8c00",

      "status": 2,

      "links": [

        {

          "href": "organizations/1686",

          "rel": "organizations",

          "type": "GET"

        },

        {

          "href": "customers/143222",

          "rel": "customers",

          "type": "GET"

        },

        {

          "href": "project_budgets/4597",

          "rel": "project_budgets",

          "type": "GET"

        },

        {

          "href": "projects/6647",

          "rel": "self",

          "type": "GET"

        }

      ],

      "project_type": 1,

      "description": "Manage your scrum projects via a series of iterations called sprints.",

      "Vision": "&amp;nbsp;",

      "primary_contact_email": null,

      "primary_contact_name": null,

      "primary_contact_phone": null,

      "secondary_contact_email": null,

      "secondary_contact_name": null,

      "secondary_contact_phone": null,

      "start_date": null,

      "end_date": null,

      "sprint_duration": 2,

      "budget_scope": "Global",

      "budget_type": "WorkedHours",

      "EffectiveBudgetAmount": 0,

      "EffectiveBudgetMinutes": 0,

      "budget_approved_only": false,

      "budget_restrictive": false,

      "billing_method": "NotBillable",

      "billing_invoice_method_fixed_fee": 0,

      "billing_invoice_method_hourly_rate": 0,

      "billing_approved_entries_only": false,

      "customer": 143222,

      "project_budget": 4597

    },

    {

      "type": "projects",

      "id": 6648,

      "Organization": 1686,

      "code": "Scrum sample project 3",

      "display_color": "#fb8c00",

      "status": 0,

      "links": [

        {

          "href": "organizations/1686",

          "rel": "organizations",

          "type": "GET"

        },

        {

          "href": "customers/143222",

          "rel": "customers",

          "type": "GET"

        },

        {

          "href": "project_budgets/4598",

          "rel": "project_budgets",

          "type": "GET"

        },

        {

          "href": "projects/6648",

          "rel": "self",

          "type": "GET"

        }

      ],

      "project_type": 1,

      "description": "Manage your scrum projects via a series of iterations called sprints.",

      "Vision": null,

      "primary_contact_email": null,

      "primary_contact_name": null,

      "primary_contact_phone": null,

      "secondary_contact_email": null,

      "secondary_contact_name": null,

      "secondary_contact_phone": null,

      "start_date": null,

      "end_date": null,

      "sprint_duration": 2,

      "budget_scope": "PerMember",

      "budget_type": "WorkedHours",

      "EffectiveBudgetAmount": 0,

      "EffectiveBudgetMinutes": 0,

      "budget_approved_only": false,

      "budget_restrictive": false,

      "billing_method": "NotBillable",

      "billing_invoice_method_fixed_fee": 0,

      "billing_invoice_method_hourly_rate": 0,

      "billing_approved_entries_only": false,

      "customer": 143222,

      "project_budget": 4598

    },

    {

      "type": "projects",

      "id": 6649,

      "Organization": 1686,

      "code": "Scrum sample project 4",

      "display_color": "#fb8c00",

      "status": 0,

      "links": [

        {

          "href": "organizations/1686",

          "rel": "organizations",

          "type": "GET"

        },

        {

          "href": "customers/143222",

          "rel": "customers",

          "type": "GET"

        },

        {

          "href": "projects/6649",

          "rel": "self",

          "type": "GET"

        }

      ],

      "project_type": 1,

      "description": "Manage your Scrum projects via a series of iterations called sprints.",

      "Vision": null,

      "primary_contact_email": null,

      "primary_contact_name": null,

      "primary_contact_phone": null,

      "secondary_contact_email": null,

      "secondary_contact_name": null,

      "secondary_contact_phone": null,

      "start_date": null,

      "end_date": null,

      "sprint_duration": 2,

      "budget_scope": "Global",

      "budget_type": "WorkedHours",

      "EffectiveBudgetAmount": 0,

      "EffectiveBudgetMinutes": 0,

      "budget_approved_only": false,

      "budget_restrictive": false,

      "billing_method": "NotBillable",

      "billing_invoice_method_fixed_fee": 0,

      "billing_invoice_method_hourly_rate": 0,

      "billing_approved_entries_only": false,

      "customer": 143222,

      "project_budget": null

    },

    {

      "type": "projects",

      "id": 6650,

      "Organization": 1686,

      "code": "Scrum sample project 5",

      "display_color": "#fb8c00",

      "status": 0,

      "links": [

        {

          "href": "organizations/1686",

          "rel": "organizations",

          "type": "GET"

        },

        {

          "href": "customers/143222",

          "rel": "customers",

          "type": "GET"

        },

        {

          "href": "projects/6650",

          "rel": "self",

          "type": "GET"

        }

      ],

      "project_type": 1,

      "description": "Manage your Scrum projects via a series of iterations called sprints.",

      "Vision": null,

      "primary_contact_email": null,

      "primary_contact_name": null,

      "primary_contact_phone": null,

      "secondary_contact_email": null,

      "secondary_contact_name": null,

      "secondary_contact_phone": null,

      "start_date": null,

      "end_date": null,

      "sprint_duration": 2,

      "budget_scope": "Global",

      "budget_type": "WorkedHours",

      "EffectiveBudgetAmount": 0,

      "EffectiveBudgetMinutes": 0,

      "budget_approved_only": false,

      "budget_restrictive": false,

      "billing_method": "NotBillable",

      "billing_invoice_method_fixed_fee": 0,

      "billing_invoice_method_hourly_rate": 0,

      "billing_approved_entries_only": false,

      "customer": 143222,

      "project_budget": null

    },

    {

      "type": "projects",

      "id": 6667,

      "Organization": 1686,

      "code": "Label test destination",

      "display_color": "#ff5722",

      "status": 0,

      "links": [

        {

          "href": "organizations/1686",

          "rel": "organizations",

          "type": "GET"

        },

        {

          "href": "customers/143222",

          "rel": "customers",

          "type": "GET"

        },

        {

          "href": "projects/6667",

          "rel": "self",

          "type": "GET"

        }

      ],

      "project_type": 1,

      "description": null,

      "Vision": null,

      "primary_contact_email": null,

      "primary_contact_name": null,

      "primary_contact_phone": null,

      "secondary_contact_email": null,

      "secondary_contact_name": null,

      "secondary_contact_phone": null,

      "start_date": null,

      "end_date": null,

      "sprint_duration": 2,

      "budget_scope": "Global",

      "budget_type": "WorkedHours",

      "EffectiveBudgetAmount": 0,

      "EffectiveBudgetMinutes": 0,

      "budget_approved_only": false,

      "budget_restrictive": false,

      "billing_method": "TaskRate",

      "billing_invoice_method_fixed_fee": 0,

      "billing_invoice_method_hourly_rate": 0,

      "billing_approved_entries_only": false,

      "customer": 143222,

      "project_budget": null

    },

    {

      "type": "projects",

      "id": 6691,

      "Organization": 1686,

      "code": "Super Agile",

      "display_color": "#f44336",

      "status": 1,

      "links": [

        {

          "href": "organizations/1686",

          "rel": "organizations",

          "type": "GET"

        },

        {

          "href": "customers/143222",

          "rel": "customers",

          "type": "GET"

        },

        {

          "href": "project_budgets/4600",

          "rel": "project_budgets",

          "type": "GET"

        },

        {

          "href": "projects/6691",

          "rel": "self",

          "type": "GET"

        }

      ],

      "project_type": 0,

      "description": null,

      "Vision": null,

      "primary_contact_email": null,

      "primary_contact_name": null,

      "primary_contact_phone": null,

      "secondary_contact_email": null,

      "secondary_contact_name": null,

      "secondary_contact_phone": null,

      "start_date": null,

      "end_date": null,

      "budget_scope": "Global",

      "budget_type": "WorkedHours",

      "EffectiveBudgetAmount": 0,

      "EffectiveBudgetMinutes": 0,

      "budget_approved_only": false,

      "budget_restrictive": false,

      "billing_method": "TaskRate",

      "billing_invoice_method_fixed_fee": 0,

      "billing_invoice_method_hourly_rate": 0,

      "billing_approved_entries_only": false,

      "customer": 143222,

      "project_budget": 4600

    }

  ]

}

# Customers

An individual or party with whom you conduct business.

Using the API’s you can do the following with project data.

<table>
  <tr>
    <td>Attribute</td>
    <td>Type</td>
    <td>Description</td>
  </tr>
  <tr>
    <td>address</td>
    <td>string</td>
    <td>Address</td>
  </tr>
  <tr>
    <td>city</td>
    <td>string</td>
    <td>City</td>
  </tr>
  <tr>
    <td>communication_culture_code</td>
    <td>string</td>
    <td>Communication culture code</td>
  </tr>
  <tr>
    <td>Organization</td>
    <td>number</td>
    <td>Unique identifier for organization.</td>
  </tr>
  <tr>
    <td>contact</td>
    <td>string</td>
    <td>Contact</td>
  </tr>
  <tr>
    <td>country</td>
    <td>number</td>
    <td>Unique identifier for country.</td>
  </tr>
  <tr>
    <td>email</td>
    <td>string</td>
    <td>Email address</td>
  </tr>
  <tr>
    <td>id</td>
    <td>number</td>
    <td>Unique identifier.</td>
  </tr>
  <tr>
    <td>legal_notice</td>
    <td>string</td>
    <td>Legal notice</td>
  </tr>
  <tr>
    <td>mobile_phone</td>
    <td>string</td>
    <td>Mobile phone number.</td>
  </tr>
  <tr>
    <td>name</td>
    <td>string</td>
    <td>Name</td>
  </tr>
  <tr>
    <td>notes</td>
    <td>string</td>
    <td>Notes</td>
  </tr>
  <tr>
    <td>phone</td>
    <td>string</td>
    <td>Phone</td>
  </tr>
  <tr>
    <td>state</td>
    <td>string</td>
    <td>State</td>
  </tr>
  <tr>
    <td>Status</td>
    <td>number</td>
    <td>Status</td>
  </tr>
  <tr>
    <td>tax</td>
    <td>number</td>
    <td>Tax</td>
  </tr>
  <tr>
    <td>type</td>
    <td>string</td>
    <td>Payload type.</td>
  </tr>
  <tr>
    <td>zip_code</td>
    <td>string</td>
    <td>Zip code.</td>
  </tr>
</table>


## Viewing a Customer

This API allows you to view the details of a customer.

GET  /api/customers/[id]

Use ‘include’ to embed additional details in the response.

List of includes go here

To do

### Sample code | Curl(to do)

<table>
  <tr>
    <td>curl -H "Authorization: nut-basic YVl6T1JtbkdpMHhwaXhCdTQ5b3l6bUpqR29GY2Z3Z1Eycnh2aGl0dDpudXRjYWNoZTFAZ21haWwuY29tOkR5bmFjb20xMjM=" -H "api-version: 3" -H "OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E" -X GET https://devapps.nutcache.com/webapi/customers

GET https://devapps.nutcache.com/webapi/customers/143222 HTTP/1.1
User-Agent: Fiddler
Host: devapps.nutcache.com
Authorization: nut-basic pHIREh3p2PquBMmwQIqWX34EEU6MxRwL5t2BaKau:nutcache1@gmail.com:Dynacom123
OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E
api-version: 3

</td>
  </tr>
</table>


#### Response

{

  "customers": [

    {

      "type": "customers",

      "id": 143222,

      "Organization": 1686,

      "name": "Sample client",

      "status": 0,

      "links": [

        {

          "href": "organizations/1686",

          "rel": "organizations",

          "type": "GET"

        },

        {

          "href": "countries/40",

          "rel": "countries",

          "type": "GET"

        },

        {

          "href": "customers/143222",

          "rel": "self",

          "type": "GET"

        }

      ],

      "email": "143222@yopmail.com",

      "contact": "Sample contact name",

      "address": null,

      "city": null,

      "zip_code": null,

      "phone": "123-456-7890",

      "mobile_phone": null,

      "country": 40,

      "state": null,

      "legal_notice": null,

      "communication_culture_code": null,

      "Notes": null,

      "tax": null

    }

  ]

}

## List all Customers

Using this API, you’d be able to fetch a list of customers.

Sample code | Curlcurl -H "Authorization: nut-basic YVl6T1JtbkdpMHhwaXhCdTQ5b3l6bUpqR29GY2Z3Z1Eycnh2aGl0dDpudXRjYWNoZTFAZ21haWwuY29tOkR5bmFjb20xMjM=" -H "api-version: 3" -H "OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E" -X GET https://devapps.nutcache.com/webapi/customers

GET https://devapps.nutcache.com/webapi/customers/ HTTP/1.1

User-Agent: Fiddler

Host: devapps.nutcache.com

Authorization: nut-basic pHIREh3p2PquBMmwQIqWX34EEU6MxRwL5t2BaKau:nutcache1@gmail.com:Dynacom123

OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E

api-version: 3

#### Response

{

  "links": [

    {

      "href": "customers?limit=10&reference_id=143222&seek_direction=previous",

      "rel": "navigation-previous",

      "type": "GET"

    },

    {

      "href": "customers?limit=10&reference_id=153745&seek_direction=next",

      "rel": "navigation-next",

      "type": "GET"

    }

  ],

  "customers": [

    {

      "type": "customers",

      "id": 143222,

      "Organization": 1686,

      "name": "Sample client",

      "status": 0,

      "links": [

        {

          "href": "organizations/1686",

          "rel": "organizations",

          "type": "GET"

        },

        {

          "href": "countries/40",

          "rel": "countries",

          "type": "GET"

        },

        {

          "href": "customers/143222",

          "rel": "self",

          "type": "GET"

        }

      ],

      "email": "143222@yopmail.com",

      "contact": "Sample contact name",

      "address": null,

      "city": null,

      "zip_code": null,

      "phone": "123-456-7890",

      "mobile_phone": null,

      "country": 40,

      "state": null,

      "legal_notice": null,

      "communication_culture_code": null,

      "Notes": null,

      "tax": null

    },

    {

      "type": "customers",

      "id": 143224,

      "Organization": 1686,

      "name": "Taxable Ont Client",

      "status": 0,

      "links": [

        {

          "href": "organizations/1686",

          "rel": "organizations",

          "type": "GET"

        },

        {

          "href": "taxes/375",

          "rel": "taxes",

          "type": "GET"

        },

        {

          "href": "customers/143224",

          "rel": "self",

          "type": "GET"

        }

      ],

      "email": "143224@yopmail.com",

      "contact": null,

      "address": null,

      "city": null,

      "zip_code": null,

      "phone": null,

      "mobile_phone": null,

      "country": null,

      "state": null,

      "legal_notice": null,

      "communication_culture_code": null,

      "Notes": null,

      "tax": 375

    },

    {

      "type": "customers",

      "id": 143225,

      "Organization": 1686,

      "name": "Taxable QC Client",

      "status": 0,

      "links": [

        {

          "href": "organizations/1686",

          "rel": "organizations",

          "type": "GET"

        },

        {

          "href": "taxes/376",

          "rel": "taxes",

          "type": "GET"

        },

        {

          "href": "customers/143225",

          "rel": "self",

          "type": "GET"

        }

      ],

      "email": "143225@yopmail.com",

      "contact": null,

      "address": null,

      "city": null,

      "zip_code": null,

      "phone": null,

      "mobile_phone": null,

      "country": null,

      "state": null,

      "legal_notice": null,

      "communication_culture_code": null,

      "Notes": null,

      "tax": 376

    },

    {

      "type": "customers",

      "id": 147033,

      "Organization": 1686,

      "name": "Test Client",

      "status": 0,

      "links": [

        {

          "href": "organizations/1686",

          "rel": "organizations",

          "type": "GET"

        },

        {

          "href": "customers/147033",

          "rel": "self",

          "type": "GET"

        }

      ],

      "email": "147033@yopmail.com",

      "contact": null,

      "address": null,

      "city": null,

      "zip_code": null,

      "phone": null,

      "mobile_phone": null,

      "country": null,

      "state": null,

      "legal_notice": null,

      "communication_culture_code": null,

      "Notes": null,

      "tax": null

    },

    {

      "type": "customers",

      "id": 147504,

      "Organization": 1686,

      "name": "Client inactif",

      "status": 1,

      "links": [

        {

          "href": "organizations/1686",

          "rel": "organizations",

          "type": "GET"

        },

        {

          "href": "customers/147504",

          "rel": "self",

          "type": "GET"

        }

      ],

      "email": "147504@yopmail.com",

      "contact": "Clientinactif@yopmail.com",

      "address": "Clientinactif@yopmail.com",

      "city": null,

      "zip_code": null,

      "phone": null,

      "mobile_phone": null,

      "country": null,

      "state": null,

      "legal_notice": null,

      "communication_culture_code": null,

      "Notes": null,

      "tax": null

    },

    {

      "type": "customers",

      "id": 149643,

      "Organization": 1686,

      "name": "client android",

      "status": 0,

      "links": [

        {

          "href": "organizations/1686",

          "rel": "organizations",

          "type": "GET"

        },

        {

          "href": "countries/2",

          "rel": "countries",

          "type": "GET"

        },

        {

          "href": "customers/149643",

          "rel": "self",

          "type": "GET"

        }

      ],

      "email": "149643@yopmail.com",

      "contact": "",

      "address": null,

      "city": null,

      "zip_code": null,

      "phone": "",

      "mobile_phone": null,

      "country": 2,

      "state": null,

      "legal_notice": null,

      "communication_culture_code": null,

      "Notes": null,

      "tax": null

    },

    {

      "type": "customers",

      "id": 153744,

      "Organization": 1686,

      "name": "Aquaman client",

      "status": 0,

      "links": [

        {

          "href": "organizations/1686",

          "rel": "organizations",

          "type": "GET"

        },

        {

          "href": "countries/2",

          "rel": "countries",

          "type": "GET"

        },

        {

          "href": "customers/153744",

          "rel": "self",

          "type": "GET"

        }

      ],

      "email": null,

      "contact": null,

      "address": null,

      "city": null,

      "zip_code": null,

      "phone": null,

      "mobile_phone": null,

      "country": 2,

      "state": null,

      "legal_notice": null,

      "communication_culture_code": null,

      "Notes": null,

      "tax": null

    },

    {

      "type": "customers",

      "id": 153745,

      "Organization": 1686,

      "name": "Surprise!",

      "status": 0,

      "links": [

        {

          "href": "organizations/1686",

          "rel": "organizations",

          "type": "GET"

        },

        {

          "href": "customers/153745",

          "rel": "self",

          "type": "GET"

        }

      ],

      "email": null,

      "contact": null,

      "address": null,

      "city": null,

      "zip_code": null,

      "phone": null,

      "mobile_phone": null,

      "country": null,

      "state": null,

      "legal_notice": null,

      "communication_culture_code": null,

      "Notes": null,

      "tax": null

    }

  ]

}

# Time Entries

A time entry is a recording of the amount of time a member spent on a specific task.

Using the API you can do the following with time entry data.

<table>
  <tr>
    <td>Attribute</td>
    <td>Type</td>
    <td>Description</td>
  </tr>
  <tr>
    <td>billable_minutes</td>
    <td>number</td>
    <td>Number of active members.</td>
  </tr>
  <tr>
    <td>creation_date</td>
    <td>datetime</td>
    <td>When this entry has been logged.</td>
  </tr>
  <tr>
    <td>creation_userprofile</td>
    <td>number</td>
    <td>?????</td>
  </tr>
  <tr>
    <td>end_time</td>
    <td>number</td>
    <td>????????</td>
  </tr>
  <tr>
    <td>guid</td>
    <td>string</td>
    <td>Unique identifier.</td>
  </tr>
  <tr>
    <td>id</td>
    <td>number</td>
    <td>Unique identifier.</td>
  </tr>
  <tr>
    <td>invoice</td>
    <td>number</td>
    <td>Invoice unique identifier.</td>
  </tr>
  <tr>
    <td>member</td>
    <td>number</td>
    <td>Member unique identifier.</td>
  </tr>
  <tr>
    <td>minutes</td>
    <td>number</td>
    <td>Number of minutes logged.</td>
  </tr>
  <tr>
    <td>note</td>
    <td>string</td>
    <td>Note</td>
  </tr>
  <tr>
    <td>project</td>
    <td>number</td>
    <td>Project unique identifier.</td>
  </tr>
  <tr>
    <td>project_feature</td>
    <td>number</td>
    <td>Project Feature unique identifier.</td>
  </tr>
  <tr>
    <td>start_time</td>
    <td>datetime</td>
    <td>??????</td>
  </tr>
  <tr>
    <td>type</td>
    <td>string</td>
    <td>Payload type.</td>
  </tr>
  <tr>
    <td>working_date</td>
    <td>datetime</td>
    <td></td>
  </tr>
</table>


## Viewing a Time Entry

This API allows you to view the details of a time entry.

GET  /api/timeentries/[id]

Use ‘include’ to embed additional details in the response.

List of includes go here

To do

### Sample code | Curl(to do)

<table>
  <tr>
    <td>curl -H "Authorization: Token token=sfg999666t673t7t82" -H "Content-Type: application/json"-X GET "https://domain.freshsales.io/api/leads/1"

GET https://devapps.nutcache.com/webapi/timeentries HTTP/1.1
User-Agent: Fiddler
Host: devapps.nutcache.com
Authorization: nut-basic pHIREh3p2PquBMmwQIqWX34EEU6MxRwL5t2BaKau:nutcache1@gmail.com:Dynacom123
OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E
api-version: 3

</td>
  </tr>
</table>


#### Response

{

  "timeentries": [

    {

      "type": "timeentries",

      "id": 201001,

      "guid": "{71094532-926e-41a1-bda5-3ce0bcb40180}",

      "billable_minutes": 0,

      "creation_date": "2018-03-06T22:01:09.25",

      "creation_userprofile": 2814,

      "start_time": null,

      "end_time": null,

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

## List all Time Entries

Using this API, you’d be able to fetch a list of time entries.

Sample code | Curlcurl -H "Authorization: Token token=sfg999666t673t7t82" -H "Content-Type: application/json" -X GET "[https://domain.freshsales.io/api/leads/filters](https://domain.freshsales.io/api/leads/filters)"

GET https://devapps.nutcache.com/webapi/timeentries HTTP/1.1

User-Agent: Fiddler

Host: devapps.nutcache.com

Authorization: nut-basic pHIREh3p2PquBMmwQIqWX34EEU6MxRwL5t2BaKau:nutcache1@gmail.com:Dynacom123

OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E

api-version: 3

Response

{

  "links": [

    {

      "href": "timeentries?limit=10&reference_id=201001&seek_direction=previous",

      "rel": "navigation-previous",

      "type": "GET"

    },

    {

      "href": "timeentries?limit=10&reference_id=206770&seek_direction=next",

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

      "start_time": null,

      "end_time": null,

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

      "start_time": null,

      "end_time": null,

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

      "start_time": null,

      "end_time": null,

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

      "start_time": null,

      "end_time": null,

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

      "start_time": null,

      "end_time": null,

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

      "start_time": null,

      "end_time": null,

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

      "start_time": null,

      "end_time": null,

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

      "start_time": null,

      "end_time": null,

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

      "start_time": null,

      "end_time": null,

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

      "start_time": null,

      "end_time": null,

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

# Timers

A Nutcache timer is a stopwatch used to record time spent on a task.

Using the API you can do the following with timer data.

<table>
  <tr>
    <td>Attribute</td>
    <td>Type</td>
    <td>Description</td>
  </tr>
  <tr>
    <td>email_reminder_sent</td>
    <td>True|False</td>
    <td>????</td>
  </tr>
  <tr>
    <td>guid</td>
    <td>string</td>
    <td>Unique identifier</td>
  </tr>
  <tr>
    <td>id</td>
    <td>number</td>
    <td>Unique identifier</td>
  </tr>
  <tr>
    <td>max_end_time_utc</td>
    <td>datetime</td>
    <td>?????</td>
  </tr>
  <tr>
    <td>member</td>
    <td>number</td>
    <td>Member unique identifier.</td>
  </tr>
  <tr>
    <td>minutes</td>
    <td>number</td>
    <td>Minutes</td>
  </tr>
  <tr>
    <td>project</td>
    <td>number</td>
    <td>Project unique identifier.</td>
  </tr>
  <tr>
    <td>project_feature</td>
    <td>number</td>
    <td>Project feature unique identifier.</td>
  </tr>
  <tr>
    <td>status</td>
    <td>string</td>
    <td>Unique identifier.</td>
  </tr>
  <tr>
    <td>time_start_local</td>
    <td>datetime</td>
    <td>Timer start(local time)</td>
  </tr>
  <tr>
    <td>time_start_utc</td>
    <td>datetime</td>
    <td>Timer start(utc time)</td>
  </tr>
  <tr>
    <td>type</td>
    <td>string</td>
    <td>Payload type.</td>
  </tr>
</table>


## Viewing a Timer

This API allows you to view the details of a timer.

GET  /api/timers/[id]

Use ‘include’ to embed additional details in the response.

List of includes go here

To do

### Sample code | Curl(to do)

<table>
  <tr>
    <td>curl -H "Authorization: Token token=sfg999666t673t7t82" -H "Content-Type: application/json"-X GET "https://domain.freshsales.io/api/leads/1"

GET https://devapps.nutcache.com/webapi/timers/3546 HTTP/1.1
User-Agent: Fiddler
Host: devapps.nutcache.com
Authorization: nut-basic pHIREh3p2PquBMmwQIqWX34EEU6MxRwL5t2BaKau:nutcache1@gmail.com:Dynacom123
OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E
api-version: 3
</td>
  </tr>
</table>


#### Response

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

## List all Timers

Using this API, you’d be able to fetch a list of timers.

Sample code | Curlcurl -H "Authorization: Token token=sfg999666t673t7t82" -H "Content-Type: application/json" -X GET "[https://domain.freshsales.io/api/leads/filters](https://domain.freshsales.io/api/leads/filters)"

GET https://devapps.nutcache.com/webapi/timers HTTP/1.1

User-Agent: Fiddler

Host: devapps.nutcache.com

Authorization: nut-basic pHIREh3p2PquBMmwQIqWX34EEU6MxRwL5t2BaKau:nutcache1@gmail.com:Dynacom123

OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E

api-version: 3

### Response

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

# Currencies

A Nutcache currency ???.

Using the API you can do the following with currency data.

<table>
  <tr>
    <td>Attribute</td>
    <td>Type</td>
    <td>Description</td>
  </tr>
  <tr>
    <td>code</td>
    <td>string</td>
    <td>Currency code.</td>
  </tr>
  <tr>
    <td>decimal_count</td>
    <td>number</td>
    <td>Number of decimal places.</td>
  </tr>
  <tr>
    <td>id</td>
    <td>number</td>
    <td>Unique identifier</td>
  </tr>
  <tr>
    <td>name_dede</td>
    <td>string</td>
    <td>?????</td>
  </tr>
  <tr>
    <td>name_enus</td>
    <td>string</td>
    <td>Currency name in US english.</td>
  </tr>
  <tr>
    <td>name_eses</td>
    <td>string</td>
    <td>Currency name in Spanish.</td>
  </tr>
  <tr>
    <td>name_frca</td>
    <td>string</td>
    <td>Currency name in French / Canada</td>
  </tr>
  <tr>
    <td>name_frfr</td>
    <td>string</td>
    <td>Currency name in French / France</td>
  </tr>
  <tr>
    <td>name_itit</td>
    <td>string</td>
    <td>Currency name in Italian</td>
  </tr>
  <tr>
    <td>name_plpl</td>
    <td>string</td>
    <td>Currency name in Polish</td>
  </tr>
  <tr>
    <td>name_ptbr</td>
    <td>string</td>
    <td>Currency name in Portuguese</td>
  </tr>
  <tr>
    <td>name_ruru</td>
    <td>string</td>
    <td>Currency name in Russian</td>
  </tr>
  <tr>
    <td>type=currencies</td>
    <td>string</td>
    <td>Payload type.</td>
  </tr>
</table>


## Viewing a Currency

This API allows you to view the details of a timer.

GET  /api/currencies/[id]

Use ‘include’ to embed additional details in the response.

List of includes go here

To do

### Sample code | Curl(to do)

<table>
  <tr>
    <td>curl -H "Authorization: Token token=sfg999666t673t7t82" -H "Content-Type: application/json"-X GET "https://domain.freshsales.io/api/leads/1"

GET https://devapps.nutcache.com/webapi/timers/7 HTTP/1.1
User-Agent: Fiddler
Host: devapps.nutcache.com
Authorization: nut-basic pHIREh3p2PquBMmwQIqWX34EEU6MxRwL5t2BaKau:nutcache1@gmail.com:Dynacom123
OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E
api-version: 3
</td>
  </tr>
</table>


#### Response

{

  "currencies": [

    {

      "type": "currencies",

      "id": 7,

      "code": "ARS",

      "decimal_count": 2,

      "name_enus": "Peso - Argentina",

      "name_frfr": "Peso - Argentine",

      "name_frca": "Peso - Argentine",

      "name_ruru": "Песо - Аргентина",

      "name_ptbr": "Peso - Argentina",

      "name_plpl": "peso argentyńskie– Argentyna",

      "name_itit": "Peso - Argentina",

      "name_eses": "Peso - Argentina",

      "name_esus": "Peso - Argentina",

      "name_dede": "Peso – Argentinien",

      "links": [

        {

          "href": "currencies/7",

          "rel": "self",

          "type": "GET"

        }

      ]

    }

  ]

}

## List all Currencies

Using this API, you’d be able to fetch a list of currencies.

Sample code | Curlcurl -H "Authorization: Token token=sfg999666t673t7t82" -H "Content-Type: application/json" -X GET "[https://domain.freshsales.io/api/leads/filters](https://domain.freshsales.io/api/leads/filters)"

GET https://devapps.nutcache.com/webapi/currencies HTTP/1.1

User-Agent: Fiddler

Host: devapps.nutcache.com

Authorization: nut-basic pHIREh3p2PquBMmwQIqWX34EEU6MxRwL5t2BaKau:nutcache1@gmail.com:Dynacom123

OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E

api-version: 3

### Response

{

  "links": [

    {

      "href": "currencies?limit=10&reference_id=1&seek_direction=previous",

      "rel": "navigation-previous",

      "type": "GET"

    },

    {

      "href": "currencies?limit=10&reference_id=10&seek_direction=next",

      "rel": "navigation-next",

      "type": "GET"

    }

  ],

  "currencies": [

    {

      "type": "currencies",

      "id": 1,

      "code": "AED",

      "decimal_count": 2,

      "name_enus": "Dirham - United Arab Emirates",

      "name_frfr": "Dirham - Émirats arabes unis",

      "name_frca": "Dirham - Émirats arabes unis",

      "name_ruru": "Дирхам - Объединенные Арабские Эмираты",

      "name_ptbr": "Dirham - Emirados Árabes Unidos",

      "name_plpl": "dirham ZEA – Zjednoczone Emiraty Arabskie",

      "name_itit": "Dirham - Emirati Arabi Uniti",

      "name_eses": "Dirham - Emiratos Árabes Unidos",

      "name_esus": "Dirham - Emiratos Árabes Unidos",

      "name_dede": "Dirhem – Vereinigte Arabische Emirate",

      "links": [

        {

          "href": "currencies/1",

          "rel": "self",

          "type": "GET"

        }

      ]

    },

    {

      "type": "currencies",

      "id": 2,

      "code": "AFN",

      "decimal_count": 2,

      "name_enus": "Afghani - Afghanistan",

      "name_frfr": "Afghani - Afghanistan",

      "name_frca": "Afghani - Afghanistan",

      "name_ruru": "Афгани - Афганистан",

      "name_ptbr": "Afegane - Afeganistão",

      "name_plpl": "afgani – Afganistan",

      "name_itit": "Afghani - Afghanistan",

      "name_eses": "Afgani - Afganistán",

      "name_esus": "Afgani - Afganistán",

      "name_dede": "Afghani – Afghanistan",

      "links": [

        {

          "href": "currencies/2",

          "rel": "self",

          "type": "GET"

        }

      ]

    },

    {

      "type": "currencies",

      "id": 3,

      "code": "ALL",

      "decimal_count": 2,

      "name_enus": "Lek - Albania",

      "name_frfr": "Lek - Albanie",

      "name_frca": "Lek - Albanie",

      "name_ruru": "Лек - Албания",

      "name_ptbr": "Lek - Albânia",

      "name_plpl": "lek – Albania",

      "name_itit": "Lek - Albania",

      "name_eses": "Lek - Albania",

      "name_esus": "Lek - Albania",

      "name_dede": "Alle",

      "links": [

        {

          "href": "currencies/3",

          "rel": "self",

          "type": "GET"

        }

      ]

    },

    {

      "type": "currencies",

      "id": 4,

      "code": "AMD",

      "decimal_count": 2,

      "name_enus": "Dram - Armenia",

      "name_frfr": "Dram - Arménie",

      "name_frca": "Dram - Arménie",

      "name_ruru": "Драм - Армения",

      "name_ptbr": "Dram - Armênia",

      "name_plpl": "dram armeński – Armenia",

      "name_itit": "Dram - Armenia",

      "name_eses": "Dram - Armenia",

      "name_esus": "Dram - Armenia",

      "name_dede": "Dram – Armenien",

      "links": [

        {

          "href": "currencies/4",

          "rel": "self",

          "type": "GET"

        }

      ]

    },

    {

      "type": "currencies",

      "id": 5,

      "code": "ANG",

      "decimal_count": 2,

      "name_enus": "Guilder - Netherlands Antilles",

      "name_frfr": "Florin - Antilles néerlandaises",

      "name_frca": "Florin - Antilles néerlandaises",

      "name_ruru": "Гульден - Нидерландские Антильские острова",

      "name_ptbr": "Florim - Antilhas Holandesas",

      "name_plpl": "gulden Antyli Holenderskich – Antyle Holenderskie",

      "name_itit": "Fiorino - Antille Olandesi",

      "name_eses": "Florín - Antillas Neerlandesas",

      "name_esus": "Florín - Antillas Neerlandesas",

      "name_dede": "Antillen-Gulden – Niederländische Antillen",

      "links": [

        {

          "href": "currencies/5",

          "rel": "self",

          "type": "GET"

        }

      ]

    },

    {

      "type": "currencies",

      "id": 6,

      "code": "AOA",

      "decimal_count": 2,

      "name_enus": "Kwanza - Angola",

      "name_frfr": "Kwanza - Angola",

      "name_frca": "Kwanza - Angola",

      "name_ruru": "Кванза - Ангола",

      "name_ptbr": "Kwanza - Angola",

      "name_plpl": "kwanza – Angola",

      "name_itit": "Kwanza - Angola",

      "name_eses": "Kwanza - Angola",

      "name_esus": "Kwanza - Angola",

      "name_dede": "Kwanza – Angola",

      "links": [

        {

          "href": "currencies/6",

          "rel": "self",

          "type": "GET"

        }

      ]

    },

    {

      "type": "currencies",

      "id": 7,

      "code": "ARS",

      "decimal_count": 2,

      "name_enus": "Peso - Argentina",

      "name_frfr": "Peso - Argentine",

      "name_frca": "Peso - Argentine",

      "name_ruru": "Песо - Аргентина",

      "name_ptbr": "Peso - Argentina",

      "name_plpl": "peso argentyńskie– Argentyna",

      "name_itit": "Peso - Argentina",

      "name_eses": "Peso - Argentina",

      "name_esus": "Peso - Argentina",

      "name_dede": "Peso – Argentinien",

      "links": [

        {

          "href": "currencies/7",

          "rel": "self",

          "type": "GET"

        }

      ]

    },

    {

      "type": "currencies",

      "id": 8,

      "code": "AUD",

      "decimal_count": 2,

      "name_enus": "Dollar - Australia",

      "name_frfr": "Dollar - Australie",

      "name_frca": "Dollar - Australie",

      "name_ruru": "Доллар - Австралия",

      "name_ptbr": "Dólar - Austrália",

      "name_plpl": "dolar australijski – Australia",

      "name_itit": "Dollaro - Australia",

      "name_eses": "Dólar - Australia",

      "name_esus": "Dólar - Australia",

      "name_dede": "Australischer Dollar – Australien",

      "links": [

        {

          "href": "currencies/8",

          "rel": "self",

          "type": "GET"

        }

      ]

    },

    {

      "type": "currencies",

      "id": 9,

      "code": "AWG",

      "decimal_count": 2,

      "name_enus": "Guilder - Aruba",

      "name_frfr": "Florin - Aruba",

      "name_frca": "Florin - Aruba",

      "name_ruru": "Гульден - Аруба",

      "name_ptbr": "Florim - Aruba",

      "name_plpl": "gulden arubański – Aruba",

      "name_itit": "Fiorino - Aruba",

      "name_eses": "Florín - Aruba",

      "name_esus": "Florín - Aruba",

      "name_dede": "Aruba-Florin – Aruba",

      "links": [

        {

          "href": "currencies/9",

          "rel": "self",

          "type": "GET"

        }

      ]

    },

    {

      "type": "currencies",

      "id": 10,

      "code": "AZN",

      "decimal_count": 2,

      "name_enus": "Manat - Azerbaijan",

      "name_frfr": "Manat - Azerbaïdjan",

      "name_frca": "Manat - Azerbaïdjan",

      "name_ruru": "Манат - Азербайджан",

      "name_ptbr": "Manat - Azerbaijão",

      "name_plpl": "manat azerbejdżański– Azerbejdżan",

      "name_itit": "Manat - Azerbaigian",

      "name_eses": "Manat - Azerbaiyán",

      "name_esus": "Manat - Azerbaiyán",

      "name_dede": "Aserbaidschan-Manat – Aserbeidschan",

      "links": [

        {

          "href": "currencies/10",

          "rel": "self",

          "type": "GET"

        }

      ]

    }

  ]

}

# Search

## Filtered Search

Filtered searches can be used to find entities that match specific search criteria.

## Usage

POST *entity*/**filtered**

## Filter Construct

{

  "**filter_rules**": [

    {

      "property": "*name*",

      "operator": "*operator*",

      "value": "*value*"

    }

  ]

}

Filters can be and chained together as follows:{

  "filter_rules": [

    {

      "property": "*name*",

      "operator": "*operator*",

      "value": "*value*"

    },

    {

      "property": "*name*",

      "operator": "*operator*",

      "value": "*value*"

    }

  ]

}

### Sample Code

curl -H 'Authorization: nut-basic YVl6T1JtbkdpMHhwaXhCdTQ5b3l6bUpqR29GY2Z3Z1Eycnh2aGl0dDpudXRjYWNoZTFAZ21haWwuY29tOkR5bmFjb20xMjM=' -H 'Content-Type:application/json' -H 'api-version: 3' -H 'OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E' -X POST https://devapps.nutcache.com/webapi/customers/filtered -d '{"filter_rules": [{"property": "name","operator": "ct","value": "Test"}]}'

## Filter Operators

<table>
  <tr>
    <td>Operator</td>
    <td>Description</td>
  </tr>
  <tr>
    <td>eq</td>
    <td>equals</td>
  </tr>
  <tr>
    <td>ne</td>
    <td>not equal</td>
  </tr>
  <tr>
    <td>gt</td>
    <td>greater than</td>
  </tr>
  <tr>
    <td>gte</td>
    <td>greater than or equal</td>
  </tr>
  <tr>
    <td>lt</td>
    <td>less than</td>
  </tr>
  <tr>
    <td>lte</td>
    <td>less than or equal</td>
  </tr>
  <tr>
    <td>ct</td>
    <td>contain</td>
  </tr>
  <tr>
    <td>sw</td>
    <td>starts with</td>
  </tr>
  <tr>
    <td>ew</td>
    <td>ends with</td>
  </tr>
</table>


## Sorting

Results from filtered searches can be sorted using filtered actions with sorting rules.

## Sorting Construct

 "sorting_rules": [

    {

      "property": "description",

      "direction": "desc"

    },

    {

      "property": "code",

      "direction": "asc"

    }

  ]

Supported sort direction terms:ascASCascendingASCENDINGdescDESCdescendingDESCENDING

To do 

Project members

[https://nutcache.github.io/apidocs](https://nutcache.github.io/apidocs)

Replace devapps with correct name

Time entry

Depends on organisation setting Time Tracking mode

Depends on if project is billable.

Start and Endtime is timespan only

