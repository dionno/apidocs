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

This API allows you to view the details of a customer.

<span class="http-method http-get">GET</span> `  /api/customers/[id]`

<aside class="notice">
Use 'include' to embed additional details in the response.

List of includes go here
</aside>

>Example

```shell
curl -H "Authorization: nut-basic YVl6T1JtbkdpMHhwaXhCdTQ5b3l6ckpqR2ZGY2Z3Z1Eycnh2aGl0ZDphcGlkb2NzQGFwaWRvY3MuY29tOnBhc3N3b3Jk" -H "api-version: 3" -H "OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E" -X GET https://devapps.nutcache.com/webapi/customers
```

GET https://devapps.nutcache.com/webapi/customers/143222 HTTP/1.1
User-Agent: Fiddler
Host: devapps.nutcache.com
Authorization: nut-basic YVl6T1JtbkdpMHhwaXhCdTQ5b3l6ckpqR2ZGY2Z3Z1Eycnh2aGl0ZDphcGlkb2NzQGFwaWRvY3MuY29tOnBhc3N3b3Jk
OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E
api-version: 3

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
```

## List all Customers

Using this API, you'd be able to fetch a list of customers.

<span class="http-method http-get">GET</span> `/webapi/customers`

>Example

```shell
curl -H "Authorization: nut-basic YVl6T1JtbkdpMHhwaXhCdTQ5b3l6ckpqR2ZGY2Z3Z1Eycnh2aGl0ZDphcGlkb2NzQGFwaWRvY3MuY29tOnBhc3N3b3Jk" -H "api-version: 3" -H "OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E" -X GET https://devapps.nutcache.com/webapi/customers
```

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
```