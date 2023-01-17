# Device Magic API V2

The API expects all data to be UTF-8 encoded.
This is a REST-style API that uses JSON/XML with Basic Authentication.
All requests start with the `https://api.devicemagic.com/` base URL.

## Authentication

https://docs.devicemagic.com/en/articles/392931-authentication

## Response Codes
https://docs.devicemagic.com/en/articles/3334936-api-response-codes

* `2xx` Success
  * `200` Ok
  * `201` Created
  * `202` Accepted
  * `204` No Content
* `3xx` Redirection
  * `304` Not Modified
* `4xx` Client Error  
  * `400` Bad Request
  * `401` Unauthorized
  * `403` Forbidden
  * `404` Not Found
  * `422` Unprocessable Entity
* `5xx` Server Error
  * `500` Internal Server Error

## Endpoints
### JSON
  * Devices
    * [Submission v3](./doc/api/v3/devices/submission.md)
  * Users
    * [Submission v3](./doc/api/v3/users/submission.md)  

### XML
  * Devices
    * [Submission v3](./doc/api/v3/devices/submission.md)
  * Users
    * [Submission v3](./doc/api/v3/users/submission.md) 
    
