# Errors

API requests that result in errors will return an appropriate HTTP code to help you identify the type of error and fix it. You can use the table below to understand what each code means. 

| Code | Text                         | Description                                                                                                                                                                                                                                                       |
|------|------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 400  | Client or Validation Error   | This indicates that the request is not in the correct format.                                                                                                                                                                                                     |
| 401  | Access Denied                | This indicates that the Authorization header is either missing or incorrect. You can learn more about the Authorization header [here](#authentication).                                                                                                           |
| 403  | Client or Validation Error   | This indicates that the user whose credentials were used in making this request was not authorized to perform this API call.                                                                                                                                      |
| 404  | Requested Resource not Found | This code is returned when the request contains invalid ID/Nutcache domain in the URL or an invalid URL itself. For example, an API call to retrieve a project with an invalid ID will return a HTTP 404 status code to let you know that no such project exists. |
| 429  | Too Many Requests            | This code appears when the user has exceeded the API rate limit. In Nutcache, this limit is set to 20000 API requests per day per API key.                                                                                                                        |
| 500  | Unexpected Server Error      | This indicates an error on Nutcache's side. Please email us at <a href="mailto:support@nutcache.com">support@nutcache.com</a> with any relevant information. We will reach out to you and fix this ASAP.                                                          |

