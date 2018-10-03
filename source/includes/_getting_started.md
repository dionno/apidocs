# Getting Started


## Public Key

To use the Nutcache API, an owner must first generate a public key. This action can be done directly in Nutcache under the "My account -> My Profile" menu. From the My Profile dialog, select the "Manage Access Keys" tab and click the "+ Generate new key" to continue.

To do! Add screen captures


## Authentication

Authentication info must be provided along with your request within the Authorization header. The authentication is made of the public key, a username and password, all separated by a colon. The authentication info must be encoded in Base 64.

Authorization: nut-basic [Base64(_public-key_:_username_:_password_)]

## Organization Context

An organization context is required when making requests. To do this, simply include the organization GUID, which can be retrieved via the Organization API from the request header.

>Example

```shell
curl -H "Authorization: YVl6T1JtbkdpMHhwaXhCdTQ5b3l6bUpqR29GY2Z3Z1Eycnh2aGl0dDpudXRjYWNoZTFAZ21haWwuY29tOkR5bmFjb20xMjM="
	 -H "api-version: 3" **-H "OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E"**
	 -X GET https://devapps.nutcache.com/webapi/customers
```

## Schema

Blank Fields:  \
Blank fields are made null instead of being omitted.

Timestamps: \
All timestamps are returned in the UTC format, YYYY-MM-DDTHH:MM:SSZ. For example, 2016-02-13T23:27:49Z \
 \
Date Fields: \
Input for date fields is expected to be in one of the following formats: \
YYYY-MM-DD  \
YYYY-MM-DDTHH:MM  \
YYYY-MM-DDTHH:MMZ  \
YYYY-MM-DDTHH:MM:SS  \
YYYY-MM-DDTHH:MM:SSZ  \
YYYY-MM-DDTHH:MM:SS±hh:mm  \
YYYY-MM-DDTHH:MM:SS±hh  \
YYYY-MM-DDTHH:MM:SS±hhmm  \
If the time zone information is not present, it will be assumed to be in UTC. \
A few valid date fields - 2016-02-15T21:16:25Z ,    2012-12-24T12:56:15+05:30,    2010-03-23T12:00

## Embedding

You can request for additional entities using the "include" keyword up to one level. For example, you can embed an organization entity when requesting a list of projects.

>Example

```shell
curl -H 'Authorization: nut-basic YVl6T1JtbkdpMHhwaXhCdTQ5b3l6bUpqR29GY2Z3Z1Eycnh2aGl0dDpudXRjYWNoZTFAZ21haWwuY29tOkR5bmFjb20xMjM=' 
	 -H 'api-version: 3' -H 'CompanyGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E' 
	 -X GET https://devapps.nutcache.com/webapi/projects?**include=organizations**
```

<aside class="notice">
Refer to each resource for more information on which entities can be included.
</aside>

## Pagination

API responses that return a list of objects, such as Projects, Customers or Time Entries are paginated. To scroll through the pages, add the parameter page to the query string. The page number starts with 1. By default, the number of objects returned per page is 10 and is limited to 100. For example, if you'd like to retrieve the Time Entries from 11 to 20 use,

>Example

```shell
curl -i -H "Authorization: nut-basic YVl6T1JtbkdpMHhwaXhCdTQ5b3l6bUpqR29GY2Z3Z1Eycnh2aGl0dDpudXRjYWNoZTFAZ21haWwuY29tOkR5bmFjb20xMjM=" 
	 -H "api-version: 3" -H "OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E" 
	 -X GET "https://devapps.nutcache.com/webapi/customers?limit=10&page=2
```

## Rate Limit

A rate limit of 10 000 api calls per day. This limit is applied on an account wide basis irrespective of factors such as the number of agents or IP addresses used to make the calls.

If you go over these limits when using our HTTP based APIs, nutcache will start returning a HTTP 429 Too Many Requests error, and a Retry-After HTTP header containing the number of seconds until you can retry.

`HTTP/1.1 429 Too Many Requests`

`Retry-After: 30`


<aside class="warning">
There is a also a burst limit of 3 api calls per second and 100 per minute.
<aside>
