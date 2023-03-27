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
  * [BIRT Service](./doc/api/v3/birt_service.md)
    * GET download submission image
      * [GET `/api/v3/download_submission_image`](./doc/api/v3/birt_service.md#get-download-submission-image)
  * [Dispatch](./doc/api/v3/dispatch.md)
    * GET all dispatch authors
      * [GET `/api/v3/dispatch_authors.(json|xml)`](./doc/api/v3/dispatch.md#jsonxml-get-all-dispatch-authors)
    * GET index of dispatch forms for device or user
      * [GET `/api/v3/devices/:device_identifier/dispatches.(json|xml)`](./doc/api/v3/dispatch.md#jsonxml-get-index-dispatch-forms-for-a-device)
      * [GET `/api/v3/users/:user/dispatches.(json|xml)`](./doc/api/v3/dispatch.md#jsonxml-get-index-dispatch-forms-for-a-user)
    * GET organization dispatches
      * [GET `/api/v3/organization_dispatches.(json|xml)`](./doc/api/v3/dispatch.md#jsonxml-get-organization-dispatches)
    * GET show
      * [GET `/api/v3/dispatches/:dispatch_id.(json|xml)`](./doc/api/v3/dispatch.md#jsonxml-get-show-dispatch)
    * POST create dispatch form for a device or user
      * [POST `/api/v3/devices/:device_identifier/dispatches.json`](./doc/api/v3/dispatch.md#jsonxml-post-create-dispatch-form-for-a-device)
      * [POST `/api/v3/users/:user/dispatches.json`](./doc/api/v3/dispatch.md#jsonxml-post-create-dispatch-form-for-a-user)
    * PATCH update a dispatch form for a device or user
      * [PATCH `/api/v3/devices/:device_identifier/dispatches/:dispatch_id.json`](./doc/api/v3/dispatch.md#jsonxml-patch-update-dispatch-form-for-a-device)
      * [PATCH `/api/v3/users/:user/dispatches/:dispatch_id.json`](./doc/api/v3/dispatch.md#jsonxml-patch-update-dispatch-form-for-a-user)



    * DELETE destroy
      * [DELETE `/api/v3/dispatchs/:dispatch_id.json`](./doc/api/v3/dispatch.md#json-delete-destroy-dispatch)
    * POST destroy all
      * [POST `/api/v3/dispatchs/destroy_all.json`](./doc/api/v3/dispatch.md#json-post-destroy_all)



  * [Resource](./doc/api/v3/resource.md)
    * GET describe
      * [GET `/api/v3/resources/describe`](./doc/api/v3/resource.md#jsonxml-get-describe-resource)
    * POST create
      * [POST `/api/v3/resources`](./doc/api/v3/resource.md#json-post-create-resource)
    * PUT update
      * [PUT `/api/v3/resources`](./doc/api/v3/resource.md#json-put-update-resource)
  * [Submission](./doc/api/v3/submission.md)
    * GET all submission authors
      * [GET `/api/v3/submission_authors.(json|xml)`](./doc/api/v3/submission.md#jsonxml-get-all-submission-authors)
    * GET submission xml
      * [GET `/api/v3/submissions/:user_id`](./doc/api/v3/submission.md#xml-get-submission-xml)
    * POST create submission from a form for a device or user
      * [POST `/api/v3/devices/:device_identifier/submissions.json`](./doc/api/v3/submission.md#json-post-create-submission-from-a-form-for-a-device)
      * [POST `/api/v3/users/:user/submissions.json`](./doc/api/v3/submission.md#json-post-create-submission-from-a-form-for-a-user)
  * [Submission Images](./doc/api/v3/submission_image.md)
    * POST create submission image  
      * [POST `/api/v3/devices/:device_identifier/submissions_image`](./doc/api/v3/submission_image.md#post-create-submission-image-for-a-device)
      * [POST `/api/v3/devices/:user/submissions_image`](./doc/api/v3/submission_image.md#post-create-submission-image-for-a-user)
    * GET get image md5  
      * [GET `/api/v3/devices/:device_identifier/submissions.json`](./doc/api/v3/submission_image.md#get-submission-image-md5-for-a-device)
      * [GET `/api/v3/devices/:user/submissions.json`](./doc/api/v3/submission_image.md#get-submission-image-md5-for-a-user)

