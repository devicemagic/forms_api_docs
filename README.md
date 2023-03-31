# Device Magic API
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

  * [Destinations](./doc/api/destinations.md)

  * [Devices](./doc/api/device.md)
    * GET all organization devices
      * [GET `/api/v2/organizations/:organization_id/devices.(json|xml)`](./doc/api/device.md#jsonxml-get-all-organization-devices)
    * GET organization device
      * [GET `/api/v2/organizations/:organization_id/devices/:device_id.json`](./doc/api/device.md#jsonxml-get-organization-device)
    * POST approving a device
      * [POST `/api/organizations/[org_id]/devices`](./doc/api/device.md#post-approving-a-device)
    * DELETE removing a device
      * [DELETE `/api/organizations/[org_id]/devices/:device_id`](./doc/api/device.md#delete-removing-a-device)      
    * PUT update device
      * [PUT `/api/organizations/[org_id]/devices/:device_id`](./doc/api/device.md#jsonxml-put-update-device)
  * [Dispatch](./doc/api/dispatch.md)
    * GET all dispatch authors
      * [GET `/api/v3/dispatch_authors.(json|xml)`](./doc/api/dispatch.md#jsonxml-get-all-dispatch-authors)
    * GET index of dispatch forms for device or user
      * [GET `/api/v3/devices/:device_identifier/dispatches.(json|xml)`](./doc/api/dispatch.md#jsonxml-get-index-dispatch-forms-for-a-device)
      * [GET `/api/v3/users/:user/dispatches.(json|xml)`](./doc/api/dispatch.md#jsonxml-get-index-dispatch-forms-for-a-user)
    * GET organization dispatches
      * [GET `/api/v3/organization_dispatches.(json|xml)`](./doc/api/dispatch.md#jsonxml-get-organization-dispatches)
    * GET show
      * [GET `/api/v3/dispatches/:dispatch_id.(json|xml)`](./doc/api/dispatch.md#jsonxml-get-show-dispatch)
    * POST create dispatch form for a device or user
      * [POST `/api/v3/devices/:device_identifier/dispatches.json`](./doc/api/dispatch.md#jsonxml-post-create-dispatch-form-for-a-device)
      * [POST `/api/v3/users/:user/dispatches.json`](./doc/api/dispatch.md#jsonxml-post-create-dispatch-form-for-a-user)
    * PATCH update a dispatch form for a device or user
      * [PATCH `/api/v3/devices/:device_identifier/dispatches/:dispatch_id.json`](./doc/api/dispatch.md#jsonxml-patch-update-dispatch-form-for-a-device)
      * [PATCH `/api/v3/users/:user/dispatches/:dispatch_id.json`](./doc/api/dispatch.md#jsonxml-patch-update-dispatch-form-for-a-user)
    * DELETE destroy dispatch
      * [DELETE `/api/v3/dispatchs/:dispatch_id.json`](./doc/api/dispatch.md#json-delete-destroy-dispatch)
    * POST destroy all dispatch forms for a device or user
      * [POST `/api/v3/devices/:device_identifier/dispatches/destroy_all.json`](./doc/api/dispatch.md#json-post-destroy-all-dispatch-forms-for-a-device)
      * [POST `/api/v3/users/:user/dispatches/destroy_all.json`](./doc/api/dispatch.md#json-post-destroy-all-dispatch-forms-for-a-user)
  * [Groups](./doc/api/group.md)
    * GET all organization groups
      * [GET `/api/v2/organizations/:organization_id/groups.(json|xml)`](./doc/api/group.md#jsonxml-get-all-organization-groups)
    * POST create a group
      * [POST `/api/organizations/[org_id]/groups`](./doc/api/group.md#jsonxml-post-create-group)
    * PUT update a group
      * [PUT `/api/organizations/[org_id]/groups/:group_id`](./doc/api/group.md#jsonxml-put-update-group)
    * DELETE destroy a group
      * [DELETE `/api/organizations/[org_id]/groups/:group_id`](./doc/api/group.md#delete-destroy-group)      

  * [Resource](./doc/api/resource.md)
    * GET index resources
      * [GET `/api/resources`](./doc/api/resource.md#jsonxml-get-index-resources)
    * GET download a resource
      * [GET `/api/resources/:resource_id`](./doc/api/resource.md#get-download-resource)
    * GET describe a resource
      * [GET `/api/v3/resources/:resource_id/describe`](./doc/api/resource.md#jsonxml-get-describe-resource)
    * POST create a resource
      * [POST `/api/v3/resources`](./doc/api/resource.md#json-post-create-resource)
    * PUT update a resource
      * [PUT `/api/v3/resources/:resource_id`](./doc/api/resource.md#json-put-update-resource)
    * DELETE destroy a resource
      * [DELETE `/api/resources/:resource_id`](./doc/api/resource.md#delete-destroy-resource)      
  * [Submission](./doc/api/submission.md)
    * GET all submission authors
      * [GET `/api/v3/submission_authors.(json|xml)`](./doc/api/submission.md#jsonxml-get-all-submission-authors)
    * GET submission xml
      * [GET `/api/v3/submissions/:user_id`](./doc/api/submission.md#xml-get-submission-xml)
    * POST create submission from a form for a device or user
      * [POST `/api/v3/devices/:device_identifier/submissions.json`](./doc/api/submission.md#json-post-create-submission-from-a-form-for-a-device)
      * [POST `/api/v3/users/:user/submissions.json`](./doc/api/submission.md#json-post-create-submission-from-a-form-for-a-user)
  * [Submission Images](./doc/api/submission_image.md)
    * POST create submission image  
      * [POST `/api/v3/devices/:device_identifier/submissions_image`](./doc/api/submission_image.md#post-create-submission-image-for-a-device)
      * [POST `/api/v3/devices/:user/submissions_image`](./doc/api/submission_image.md#post-create-submission-image-for-a-user)
    * GET get image md5  
      * [GET `/api/v3/devices/:device_identifier/submissions.json`](./doc/api/submission_image.md#get-submission-image-md5-for-a-device)
      * [GET `/api/v3/devices/:user/submissions.json`](./doc/api/submission_image.md#get-submission-image-md5-for-a-user)

