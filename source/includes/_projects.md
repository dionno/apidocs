# Projects

A Nutcache project is a planned work or activity that is to be completed over a period of time using Agile or Scrum methodology.

Using the API you can do the following with project data.

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
   <td>billing_approved_entries_only
   </td>
   <td>True|False
   </td>
   <td>????
   </td>
  </tr>
  <tr>
   <td>billing_invoice_method_fixed_fee
   </td>
   <td>number
   </td>
   <td>?????
   </td>
  </tr>
  <tr>
   <td>billing_invoice_method_hourly_rate
   </td>
   <td>number
   </td>
   <td>?????
   </td>
  </tr>
  <tr>
   <td>billing_method
   </td>
   <td>string
   </td>
   <td>Billing method.????bug returns string
   </td>
  </tr>
  <tr>
   <td>budget_approved_only
   </td>
   <td>True|False
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>budget_restrictive
   </td>
   <td>True|False
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>budget_scope
   </td>
   <td>string
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>budget_type
   </td>
   <td>string
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>code
   </td>
   <td>string
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>organization
   </td>
   <td>number
   </td>
   <td>Unique identifier for an organization.
   </td>
  </tr>
  <tr>
   <td>customer
   </td>
   <td>number
   </td>
   <td>Unique identifier for a customer.
   </td>
  </tr>
  <tr>
   <td>description
   </td>
   <td>string
   </td>
   <td>Project description.
   </td>
  </tr>
  <tr>
   <td>display_color
   </td>
   <td>string
   </td>
   <td>HTML color
   </td>
  </tr>
  <tr>
   <td>EffectiveBudgetAmount
   </td>
   <td>number
   </td>
   <td>??????
   </td>
  </tr>
  <tr>
   <td>EffectiveBudgetMinutes
   </td>
   <td>number
   </td>
   <td>??????
   </td>
  </tr>
  <tr>
   <td>end_date
   </td>
   <td>datetime
   </td>
   <td>Phone number.
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
   <td>primary_contact_email
   </td>
   <td>string
   </td>
   <td>Primary contact email.
   </td>
  </tr>
  <tr>
   <td>primary_contact_name
   </td>
   <td>string
   </td>
   <td>Primary contact name.
   </td>
  </tr>
  <tr>
   <td>primary_contact_phone
   </td>
   <td>string
   </td>
   <td>Primary contact phone
   </td>
  </tr>
  <tr>
   <td>project_budget
   </td>
   <td>number
   </td>
   <td>????
   </td>
  </tr>
  <tr>
   <td>project_type
   </td>
   <td>number
   </td>
   <td>Type of project.
   </td>
  </tr>
  <tr>
   <td>secondary_contact_email
   </td>
   <td>string
   </td>
   <td>Secondary contact email.
   </td>
  </tr>
  <tr>
   <td>secondary_contact_name
   </td>
   <td>string
   </td>
   <td>Secondary contact name.
   </td>
  </tr>
  <tr>
   <td>secondary_contact_phone
   </td>
   <td>string
   </td>
   <td>Secondary contact phone.
   </td>
  </tr>
  <tr>
   <td>start_date
   </td>
   <td>datetime
   </td>
   <td>Project start date.
   </td>
  </tr>
  <tr>
   <td>status
   </td>
   <td>number
   </td>
   <td>Project status(to enumerate)
   </td>
  </tr>
  <tr>
   <td>type
   </td>
   <td>string
   </td>
   <td>Payload type(projects)
   </td>
  </tr>
  <tr>
   <td>Vision
   </td>
   <td>string
   </td>
   <td>Project vision
   </td>
  </tr>
</table>



## Viewing a Project

This API allows you to view the details of a project.

<span class="http-method http-get">GET</span> `  /api/projects/[id]`

Use 'include' to embed additional details in the response.

List of includes go here

To do

```shell
curl -H 'Authorization: nut-basic YVl6T1JtbkdpMHhwaXhCdTQ5b3l6bUpqR29GY2Z3Z1Eycnh2aGl0dDpudXRjYWNoZTFAZ21haWwuY29tOkR5bmFjb20xMjM=' -H 'api-version: 3' -H 'OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E' -X GET https://devapps.nutcache.com/webapi/projects/6640
```

> Response

```json
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
```

## List all Projects

<span class="http-method http-get">GET</span> `  /api/projects`

Using this API, you'd be able to fetch a list of projects.

```shell
curl -H 'Authorization: nut-basic YVl6T1JtbkdpMHhwaXhCdTQ5b3l6bUpqR29GY2Z3Z1Eycnh2aGl0dDpudXRjYWNoZTFAZ21haWwuY29tOkR5bmFjb20xMjM=' -H 'api-version: 3' -H 'OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E' -X GET https://devapps.nutcache.com/webapi/projects
```

>Response

```json
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
```