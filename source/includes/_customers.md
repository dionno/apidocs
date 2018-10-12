# Customers

An individual or party with whom you conduct business.

Using the API's you can do the following with project data.

| Attribute                  | Type   | Description                         |
|----------------------------|--------|-------------------------------------|
| address                    | string | Address                             |
| city                       | string | City                                |
| communication_culture_code | string | Communication culture code          |
| Organization               | number | Unique identifier for organization. |
| contact                    | string | Contact                             |
| country                    | number | Unique identifier for country.      |
| email                      | string | Email address                       |
| id                         | number | Unique identifier.                  |
| legal_notice               | string | Legal notice                        |
| mobile_phone               | string | Mobile phone number.                |
| name                       | string | Name                                |
| notes                      | string | Notes                               |
| phone                      | string | Phone                               |
| state                      | string | State                               |
| Status                     | number | Status                              |
| tax                        | number | Tax                                 |
| type                       | string | Payload type.                       |
| zip_code                   | string | Zip code.                           |

## Viewing a Customer

>Example

```shell
curl -H "Authorization: nut-basic YVl6T1JtbkdpMHhwaXhCdTQ5b3l6ckpqR2ZGY2Z3Z1Eycnh2aGl0ZDphcGlkb2NzQGFwaWRvY3MuY29tOnBhc3N3b3Jk" 
     -H "api-version: 3" 
	 -H "OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E" 
	 -X GET https://apps.nutcache.com/webapi/customers
```

This API allows you to view the details of a customer.

<span class="http-method http-get">GET</span> `  /api/customers/[id]`

<aside class="notice">
Use 'include' to embed additional details in the response.
</aside>

>Response

```json
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
      "email": "143222@example.com",
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
```

## List all Customers

>Example

```shell
curl -H "Authorization: nut-basic YVl6T1JtbkdpMHhwaXhCdTQ5b3l6ckpqR2ZGY2Z3Z1Eycnh2aGl0ZDphcGlkb2NzQGFwaWRvY3MuY29tOnBhc3N3b3Jk" 
     -H "api-version: 3" 
	 -H "OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E" 
	 -X GET https://apps.nutcache.com/webapi/customers
```

Using this API, you'd be able to fetch a list of customers.

<span class="http-method http-get">GET</span> `/webapi/customers`

>Response

```json
{
  "links": [
    {
      "href": "customers?limit=10&page=2",
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
      "email": "143222@example.com",
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
}
```

## Include (Customers)

The following entity types can be included in this payload type

| Type          | Description                               |
|---------------|-------------------------------------------|
| organizations | The organization containing the customer  |
| taxes         | The taxes associated with this customer   |
| countries     | The country associated with this customer |
| states        | The state associated with this customer   |