# Currencies

A Nutcache currency ???.

Using the API you can do the following with currency data.

Attribute | Type | Description
----------|------|------------
code | string | Currency code.
decimal_count | number | Number of decimal places.
id | number | Unique identifier
name_dede | string | ?????
name_enus | string | Currency name in US english.
name_eses | string | Currency name in Spanish.
name_frca | string | Currency name in French / Canada
name_frfr | string | Currency name in French / France
name_itit | string | Currency name in Italian
name_plpl | string | Currency name in Polish
name_ptbr | string | Currency name in Portuguese
name_ruru | string | Currency name in Russian
type=currencies | string | Payload type.

## Viewing a Currency

This API allows you to view the details of a timer.

<span class="http-method http-get">GET</span> `  /api/currencies/[id]`

<aside class="notice">
Use 'include' to embed additional details in the response.

List of includes go here
</aside>

>Example

```shell
curl -H "Authorization: Token token=sfg999666t673t7t82" -H "Content-Type: application/json"-X GET "https://domain.freshsales.io/api/leads/1"
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
curl -H "Authorization: Token token=sfg999666t673t7t82" -H "Content-Type: application/json" -X GET "[https://domain.freshsales.io/api/leads/filters](https://domain.freshsales.io/api/leads/filters)"
```

>Response

```json
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
```