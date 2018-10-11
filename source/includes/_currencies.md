# Currencies

A Nutcache currency ???.

Using the API you can do the following with currency data.

| Attribute       | Type   | Description                      |
|-----------------|--------|----------------------------------|
| code            | string | Currency code.                   |
| decimal_count   | number | Number of decimal places.        |
| id              | number | Unique identifier                |
| name_dede       | string | ?????                            |
| name_enus       | string | Currency name in US english.     |
| name_eses       | string | Currency name in Spanish.        |
| name_frca       | string | Currency name in French / Canada |
| name_frfr       | string | Currency name in French / France |
| name_itit       | string | Currency name in Italian         |
| name_plpl       | string | Currency name in Polish          |
| name_ptbr       | string | Currency name in Portuguese      |
| name_ruru       | string | Currency name in Russian         |
| type=currencies | string | Payload type.                    |

## Viewing a Currency

This API allows you to view the details of a timer.

<span class="http-method http-get">GET</span> `  /api/currencies/[id]`

>Example

```shell
curl -H "Authorization: nut-basic YVl6T1JtbkdpMHhwaXhCdTQ5b3l6ckpqR2ZGY2Z3Z1Eycnh2aGl0ZDphcGlkb2NzQGFwaWRvY3MuY29tOnBhc3N3b3Jk" 
     -H "api-version: 3" 
	 -H "OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E" 
	 -X GET https://apps.nutcache.com/webapi/currencies/7
```

>Response

```json
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
```

## List all Currencies

Using this API, you'd be able to fetch a list of currencies.

<span class="http-method http-get">GET</span> `/api/currencies`

>Example

```shell
curl -H "Authorization: nut-basic YVl6T1JtbkdpMHhwaXhCdTQ5b3l6ckpqR2ZGY2Z3Z1Eycnh2aGl0ZDphcGlkb2NzQGFwaWRvY3MuY29tOnBhc3N3b3Jk" 
     -H "api-version: 3" 
	 -H "OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E" 
	 -X GET https://apps.nutcache.com/webapi/currencies
```

>Response

```json
{
  "links": [
    {
      "href": "currencies?limit=10&page=2",
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
    }
  ]
}
```