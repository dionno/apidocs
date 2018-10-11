
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
</aside>

>Example

```shell
curl -H 'Authorization: nut-basic YVl6T1JtbkdpMHhwaXhCdTQ5b3l6ckpqR2ZGY2Z3Z1Eycnh2aGl0ZDphcGlkb2NzQGFwaWRvY3MuY29tOnBhc3N3b3Jk' -H 'api-version: 3' -H 'OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E' -X GET https://apps.nutcache.com/webapi/invoices/9287
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
			"customer_email":"143222@example.com",
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
curl -H 'Authorization: nut-basic YVl6T1JtbkdpMHhwaXhCdTQ5b3l6ckpqR2ZGY2Z3Z1Eycnh2aGl0ZDphcGlkb2NzQGFwaWRvY3MuY29tOnBhc3N3b3Jk' -H 'api-version: 3' -H 'OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E' -X GET https://apps.nutcache.com/webapi/invoices
```

>Response

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
			"customer_email":"143222@example.com",
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

## Include (Invoices)

The following entity types can be included in this payload type

| Type            | Description                               |
|-----------------|-------------------------------------------|
| organizations   | The organization containing this invoice  |
| customers       | The customer associated with this invoice |
| members         | The responsible member for this invoice   |
| invoice_details | The invoice's detail rows                 |
| invoice_taxes   | The taxes summary of this invoice         |