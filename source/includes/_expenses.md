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
