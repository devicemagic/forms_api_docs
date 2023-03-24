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
    * GET all submission authors
      * [GET `/api/v3/submission_authors.json`](./submission.md#json-get-all-submission-authors)
    * GET submission xml
      * [GET `/api/v3/submissions/:user_id`](./submission.md#xml-get-submission-xml)
    * POST create submission from a form or dispatch for device
      * [POST `/api/v3/devices/:device_identifier/submissions.json`](./submission.md#json-post-create-submission-from-a-form-or-dispatch-for-device)
      * [POST `/api/v3/devices/:user/submissions.json`](./submission.md#json-post-create-submission-from-a-form-or-dispatch-for-user)
