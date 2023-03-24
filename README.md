# Device Magic API V3

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
  * [Submission v3](./doc/api/v3/submissions/submission.md)
    * JSON
      * [Submission v3](./doc/api/v3/submissions/submission-json.md)
    * XML
      * [Submission v3](./doc/api/v3/submissions/submission-xml.md)
    
