
# Invoices

A Nutcache invoice.

Using the API you can do the following with invoice data.

| Attribute                         | Type     	| Description                           	|
|-----------------------------------|-----------|---------------------------------------|
| balance      						| Decimal	|                     					|
| customer                          | number   	| Unique identifier for a customer.     |
| customer_address 					| string		|     		                            	|
| customer_city                     | string   	| 										|
| customer_email						| string  	| Project description.                  |
| customer_legal_notice             | string   	|                                       |
| customer_phone                    | string   	|                                    	|
| customer_phone_mobile             | string   	|                                       |
| customer_postal_zip_code          | string		| 										|
| customer_province_state           | string		| 										|
| description                      | string   | HTML color                             |
| due_date             | number   | ??????                                 |
| estimate              | number   | ??????                                 |
| invoice_date                           | datetime | Phone number.                          |
| notes                                 | number   | Unique identifier.                     |
| organization                      | number   	| Unique identifier for an organization.|
| paid_to_date					    | Decimal	| 										|
| purchase_order               | string   | Primary contact name.                  |
| responsible              | string   | Primary contact phone                  |
| status                     | number   | ????                                   |
| taxes_amount                       | number   | Type of project.                       |
| terms             | string   | Primary contact email.                 |
| total| string   | Secondary contact email.               |
| total_amount_before_taxes             | string   | Secondary contact name.                |

# Viewing an Invoice

This API allows you to view an invoice.

<span class="http-method http-get">GET</span> `  /api/invoices/[id]`

<aside class="notice">
Use 'include' to embed additional details in the response.

List of includes go here
</aside>

>Example

```shell
curl -H 'Authorization: nut-basic YVl6T1JtbkdpMHhwaXhCdTQ5b3l6bUpqR29GY2Z3Z1Eycnh2aGl0dDpudXRjYWNoZTFAZ21haWwuY29tOkR5bmFjb20xMjM=' -H 'api-version: 3' -H 'OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E' -X GET https://devapps.nutcache.com/webapi/invoices/6640
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

## List all Invoices

<span class="http-method http-get">GET</span> `  /api/invoces`

Using this API, you'd be able to fetch a list of invoices.

>Example

```shell
curl -H 'Authorization: nut-basic YVl6T1JtbkdpMHhwaXhCdTQ5b3l6bUpqR29GY2Z3Z1Eycnh2aGl0dDpudXRjYWNoZTFAZ21haWwuY29tOkR5bmFjb20xMjM=' -H 'api-version: 3' -H 'OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E' -X GET https://devapps.nutcache.com/webapi/invoices
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
