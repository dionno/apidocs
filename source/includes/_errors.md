# Errors

<aside class="notice">
This error section is stored in a separate file in <code>includes/_errors.md</code>. Slate allows you to optionally separate out your docs into many files...just save them to the <code>includes</code> folder and add them to the top of your <code>index.md</code>'s frontmatter. Files are included in the order listed.
</aside>

API requests that result in errors will return an appropriate HTTP status code to help you identify the type of error and fix it. You can use the table below to understand what each code means. 

HTTP Status Code | Text | Description
----------------- | ---------------- | -----------
400 | Client or Validation Error | Indicates that the request is not in the correct format.
401 | Access Denied | Indicates that the Authorization header is either missing or incorrect. You can learn more about the Authorization header 
403 | Client or Validation Error | This indicates that the user whose credentials were used in making this request was not authorized to perform this API call.
404 | Requested Resource not Found | This status code is returned when the request contains invalid ID/Nutcache domain in the URL or an invalid URL itself. For example, an API call to retrieve a project with an invalid ID will return a HTTP 404 status code to let you know that no such project exists.
429 | Too Many Requests | This status code appears when the user has exceeded the API limit set per ??? per account. In Nutcache, this limit is ???? API requests per ???? per account.
500 | Unexpected Server Error | This indicates an error on Nutcache's side. Please email us at <a href="mailto:support@nutcache.com">support@nutcache.com</a> with your API script along with the response headers. We will reach out to you and fix this ASAP.
