# Expenses

Describes the expenses on the company operation, including the amount, taxes, suppliers and other people associated with the expense.


| Attribute           | Type    | Description                                                                                                       |
|---------------------|---------|-------------------------------------------------------------------------------------------------------------------|
| id                  | Number  | Unique identifier                                                                                                 |
| type=expenses       | String  | Payload type                                                                                                      |
| expense_number      | String  | The expense’s identification. If not changed by the user, consists in a sequential number.                        |
| amount_after_taxes  | Number  | The total amount to pay, including the taxes.                                                                     |
| amount_before_taxes | Number  | The subtotal amount, without the taxes.                                                                           |
| amount_due          | Number  | The outstanding amount.                                                                                           |
| amount_paid         | Number  | The amount already paid.                                                                                          |
| billable            | Boolean | If the expense is billable.                                                                                       |
| organization        | Number  | Unique identifier for an organization.<br />include=organizations                                                 |
| description         | String  | The given expense description.                                                                                    |
| due_date            | Date    | The expense due date.                                                                                             |
| expense_category    | Number  | Unique identifier for the category.                                                                               |
| expense_date        | Date    | The date on which the expense was made.                                                                           |
| invoice             | Number  | Unique identifier of a related invoice, if any.<br />include=invoices                                             |
| project             | Number  | Unique identifier of a related project.<br />include=projects                                                     |
| status              | Number  | The expense status (to enumerate)                                                                                 |
| taxes_amount        | Number  | The total amount of taxes.                                                                                        |
| member              | Number  | Unique identifier of a related user, if any.<br />include=members                                                 |
| version             | Number  | The expense version. Used to identify changes made by different users.                                            |
| expense_tax_details | Array   | A collection of expense tax details. It’s present only when explicitly included.<br />include=expense_tax_details |


## Viewing an expense

>Example

```shell

curl -H 'Authorization: nut-basic YVl6T1JtbkdpMHhwaXhCdTQ5b3l6ckpqR2ZGY2Z3Z1Eycnh2aGl0ZDphcGlkb2NzQGFwaWRvY3MuY29tOnBhc3N3b3Jk' 
     -H 'api-version: 3' 
	 -H "OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E" 
	 -X GET https://apps.nutcache.com/webapi/expenses/231564

```

>Response

```json

{
	"expenses": [
		{
			"type": "expenses",
			"id": 231564,
			"expense_number": "0001",
			"amount_after_taxes": 1.0000,
			"amount_before_taxes": 1.0000,
			"amount_due": 1.0000,
			"amount_paid": 0.0000,
			"billable": false,
			"organization": 7338,
			"description": null,
			"due_date": "2018-07-26T00:00:00",
			"expense_category": null,
			"expense_date": "2018-07-26T00:00:00",
			"invoice": null,
			"project": null,
			"status": 0,
			"supplier": null,
			"taxes_amount": 0.0000,
			"member": 23637,
			"version": 0,
			"links": [{
					"href": "organizations/7338",
					"rel": "organizations",
					"type": "GET"
				}, {
					"href": "expenses/231564",
					"rel": "self",
					"type": "GET"
				}
			]
		}
	]
}


```

This API allows you to view the details of a expense:

<span class="http-method http-get">GET</span> ` /webapi/expenses/[id]`

URL Parameters:

| Parameter | Description                 |
|-----------|-----------------------------|
| id        | The expense id to retrieve. |

<aside class="notice">
Use 'include' to embed additional details in the response.
</aside>

## Listing expenses

>Example

```shell

curl -H 'Authorization: nut-basic YVl6T1JtbkdpMHhwaXhCdTQ5b3l6ckpqR2ZGY2Z3Z1Eycnh2aGl0ZDphcGlkb2NzQGFwaWRvY3MuY29tOnBhc3N3b3Jk' 
     -H 'api-version: 3' 
	 -H "OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E" 
	 -X GET https://apps.nutcache.com/webapi/expenses/

```

>Response

```json

{
	"links": [],
	"expenses": [
		{
			"type": "expenses",
			"id": 231564,
			"expense_number": "0001",
			"amount_after_taxes": 1.0000,
			"amount_before_taxes": 1.0000,
			"amount_due": 1.0000,
			"amount_paid": 0.0000,
			"billable": false,
			"organization": 7338,
			"description": null,
			"due_date": "2018-07-26T00:00:00",
			"expense_category": null,
			"expense_date": "2018-07-26T00:00:00",
			"invoice": null,
			"project": null,
			"status": 0,
			"supplier": null,
			"taxes_amount": 0.0000,
			"member": 23637,
			"version": 0,
			"links": [{
					"href": "organizations/7338",
					"rel": "organizations",
					"type": "GET"
				}, {
					"href": "expenses/231564",
					"rel": "self",
					"type": "GET"
				}
			]
		}, {
			"type": "expenses",
			"id": 231565,
			"expense_number": "0003",
			"amount_after_taxes": 1560.0000,
			"amount_before_taxes": 1560.0000,
			"amount_due": 1545.0000,
			"amount_paid": 15.0000,
			"billable": true,
			"organization": 7338,
			"description": null,
			"due_date": "2018-07-31T00:00:00",
			"expense_category": 26092,
			"expense_date": "2018-07-31T00:00:00",
			"invoice": null,
			"project": 17276,
			"status": 1,
			"supplier": 1166,
			"taxes_amount": 0.0000,
			"member": 23637,
			"version": 0,
			"links": [{
					"href": "organizations/7338",
					"rel": "organizations",
					"type": "GET"
				}, {
					"href": "projects/17276",
					"rel": "projects",
					"type": "GET"
				}, {
					"href": "expenses/231565",
					"rel": "self",
					"type": "GET"
				}
			]
		}, {
			"type": "expenses",
			"id": 231566,
			"expense_number": "0004",
			"amount_after_taxes": 11.2500,
			"amount_before_taxes": 10.0000,
			"amount_due": 0.0000,
			"amount_paid": 11.2500,
			"billable": true,
			"organization": 7338,
			"description": "Some expense",
			"due_date": "2018-08-02T00:00:00",
			"expense_category": 26092,
			"expense_date": "2018-08-02T00:00:00",
			"invoice": null,
			"project": 17274,
			"status": 2,
			"supplier": 1166,
			"taxes_amount": 1.2500,
			"member": 23632,
			"version": 1,
			"links": [{
					"href": "organizations/7338",
					"rel": "organizations",
					"type": "GET"
				}, {
					"href": "projects/17274",
					"rel": "projects",
					"type": "GET"
				}, {
					"href": "expenses/231566",
					"rel": "self",
					"type": "GET"
				}
			]
		}
	]
}


```

To get a list containing all expenses, do a GET request, omitting the expense ID.

<span class="http-method http-get">GET</span> ` /webapi/expenses/`

<aside class="notice">
Use 'include' to embed additional details in the response.
</aside>

## Expense Taxes

>Example

```shell

curl -H 'Authorization: nut-basic YVl6T1JtbkdpMHhwaXhCdTQ5b3l6ckpqR2ZGY2Z3Z1Eycnh2aGl0ZDphcGlkb2NzQGFwaWRvY3MuY29tOnBhc3N3b3Jk' 
     -H 'api-version: 3' 
	 -H "OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E" 
	 -X GET https://apps.nutcache.com/webapi/expenses/234300/expense_taxes

```

>Response

```json

{
	"links": [],
	"expense_taxes": [
		{
			"type": "expense_taxes",
			"expense": 234300,
			"id": 229010,
			"tax_amount": 2.0000,
			"tax_code": "component a",
			"links": [
				{
					"href": "expenses/234300",
					"rel": "expenses",
					"type": "GET"
				}, {
					"href": "expense_taxes/229010",
					"rel": "self",
					"type": "GET"
				}
			]
		}, {
			"type": "expense_taxes",
			"expense": 234300,
			"id": 229011,
			"tax_amount": 3.0000,
			"tax_code": "Manual tax",
			"links": [
				{
					"href": "expenses/234300",
					"rel": "expenses",
					"type": "GET"
				}, {
					"href": "expense_taxes/229011",
					"rel": "self",
					"type": "GET"
				}
			]
		}
	]
}


```

You can get a detailed list of taxes contained in an expense, using the following path:

<span class="http-method http-get">GET</span> ` /webapi/expenses/[id]/expense_taxes`

| Attribute          | Type   | Description                          |
|--------------------|--------|--------------------------------------|
| id                 | Number | Unique identifier                    |
| type=expense_taxes | String | Payload type                         |
| expense            | Number | Unique identifier of parent expense. |
| tax_amount         | Number | The amount to be paid on this tax.   |
| tax_code           | String | The name or code for this tax.       |

<aside class="notice">
The taxes for an expense can also be filtered using filtered searches.
</aside>
