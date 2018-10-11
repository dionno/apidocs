
# Invoices

A Nutcache invoice.

Using the API you can do the following with invoice data.

| Attribute                 | Type     | Description                            |
|---------------------------|----------|----------------------------------------|
| balance                   | decimal  |                                        |
| customer                  | number   | Unique identifier for a customer.      |
| customer_address          | string   |                                        |
| customer_city             | string   |                                        |
| customer_email            | string   |                                        |
| customer_legal_notice     | string   |                                        |
| customer_phone            | string   |                                        |
| customer_phone_mobile     | string   |                                        |
| customer_postal_zip_code  | string   |                                        |
| customer_province_state   | string   |                                        |
| description               | string   | Invoice description.                   |
| due_date                  | datetime |                                        |
| estimate                  | decimal  |                                        |
| id                        | number   | Unique identifier for an invoice.      |
| invoice_date              | datetime |                                        |
| invoice_number            | string   |                                        |
| notes                     | string   |                                        |
| organization              | number   | Unique identifier for an organization. |
| paid_to_date              | decimal  |                                        |
| purchase_order            | string   |                                        |
| responsible               | string   |                                        |
| status                    | number   |                                        |
| taxes_amount              | decimal  |                                        |
| terms                     | string   |                                        |
| total                     | decimal  |                                        |
| total_amount_before_taxes | decimal  |                                        |


## Viewing an Invoice

This API allows you to view an invoice.

<span class="http-method http-get">GET</span> `  /api/invoices/[id]`

<aside class="notice">
Use 'include' to embed additional details in the response.

List of includes go here
</aside>

>Example

```shell
curl -H 'Authorization: nut-basic YVl6T1JtbkdpMHhwaXhCdTQ5b3l6ckpqR2ZGY2Z3Z1Eycnh2aGl0ZDphcGlkb2NzQGFwaWRvY3MuY29tOnBhc3N3b3Jk' -H 'api-version: 3' -H 'OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E' -X GET https://devapps.nutcache.com/webapi/invoices/9287
```

> Response

```json
{
 	"invoices": [
		{
			"type":"invoices",
			"id":9287,
			"invoice_number":"0005",
			"customer_name":"Sample client",
			"balance":1225.7900,
			"paid_to_date":100.0000,
			"organization":1686,
			"customer":143222,
			"customer_address":null,
			"customer_city":null,
			"customer_contact":"Sample contact name",
			"customer_country":"Canada",
			"customer_email":"143222@yopmail.com",
			"customer_legal_notice":null,
			"customer_phone":"123-456-7890",
			"customer_phone_mobile":null,
			"customer_postal_zip_code":null,
			"customer_province_state":null,
			"custom_title":null,
			"description":null,
			"due_date":"2018-04-18T00:00:00",
			"estimate":null,
			"invoice_date":"2018-04-18T00:00:00",
			"notes":null,
			"terms":null,
			"purchase_order":null,
			"responsible":9015,
			"status":3,
			"taxes_amount":13.7900,
			"total":1325.7900,
			"total_amount_before_taxes":1312.0000,
			"links":[
				{
				"href":"organizations/1686",
				"rel":"organizations",
				"type":"GET"
				},
				{
				"href":"customers/143222",
				"rel":"customers",
				"type":"GET"
				},
				{
				"href":"invoices/9287",
				"rel":"self",
				"type":"GET"
				}
			]
		}
	]
}
```
## List all invoices

Using this API, you'd be able to fetch a list of invoices.

<span class="http-method http-get">GET</span> `  /api/invoices/`

>Example

```shell
curl -H 'Authorization: nut-basic YVl6T1JtbkdpMHhwaXhCdTQ5b3l6ckpqR2ZGY2Z3Z1Eycnh2aGl0ZDphcGlkb2NzQGFwaWRvY3MuY29tOnBhc3N3b3Jk' -H 'api-version: 3' -H 'OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E' -X GET https://devapps.nutcache.com/webapi/invoices
```

>Response

```json
{
  "links": [    
    {
      "href": "projects?limit=10&page=2",
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
