# Search

## Filtered Search

Filtered searches can be used to find entities that match specific search criteria.


## Usage

<span class="http-method http-post">POST</span> ` _entity_/**filtered**`


>Filter Construct

```json
{
  "**filter_rules**": [
    {
      "property": "_name_",
      "operator": "_operator_",
      "value": "_value_"
    }
  ]
}
```

>Filters can be and chained together as follows:

```json
{
  "filter_rules": [
    {
      "property": "_name_",
      "operator": "_operator_",
      "value": "_value_"
    },
    {
      "property": "_name_",
      "operator": "_operator_",
      "value": "_value_"
    }
  ]
}
```
>Example

```shell
curl -H 'Authorization: nut-basic YVl6T1JtbkdpMHhwaXhCdTQ5b3l6bUpqR29GY2Z3Z1Eycnh2aGl0dDpudXRjYWNoZTFAZ21haWwuY29tOkR5bmFjb20xMjM=' -H 'Content-Type:application/json' -H 'api-version: 3' -H 'OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E' -X POST https://devapps.nutcache.com/webapi/customers/filtered -d '{"filter_rules": [{"property": "name","operator": "ct","value": "Test"}]}'
```

## Filter Operators

<table>
  <tr>
   <td><strong>Operator</strong>
   </td>
   <td><strong>Description</strong>
   </td>
  </tr>
  <tr>
   <td>eq
   </td>
   <td>equals
   </td>
  </tr>
  <tr>
   <td>ne
   </td>
   <td>not equal
   </td>
  </tr>
  <tr>
   <td>gt
   </td>
   <td>greater than
   </td>
  </tr>
  <tr>
   <td>gte
   </td>
   <td>greater than or equal
   </td>
  </tr>
  <tr>
   <td>lt
   </td>
   <td>less than
   </td>
  </tr>
  <tr>
   <td>lte
   </td>
   <td>less than or equal
   </td>
  </tr>
  <tr>
   <td>ct
   </td>
   <td>contain
   </td>
  </tr>
  <tr>
   <td>sw
   </td>
   <td>starts with
   </td>
  </tr>
  <tr>
   <td>ew
   </td>
   <td>ends with
   </td>
  </tr>
</table>


## Sorting

Results from filtered searches can be sorted using filtered actions with sorting rules.


>Sorting Construct

```json
 "sorting_rules": [
    {
      "property": "description",
      "direction": "desc"
    },
    {
      "property": "code",
      "direction": "asc"
    }
  ]
```
  
Supported sort direction terms: \
 \
asc \
ASC \
ascending \
ASCENDING \
desc \
DESC \
descending \
DESCENDING