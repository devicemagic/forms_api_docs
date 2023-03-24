# Submissions Image API v3


## POST create submission Image for a device

* POST `/api/v3/devices/:device_identifier/submission_images.json?image_identifier=:image_identifier&submission_identifer=:submission_identifer` 

Returns a `HTTP 202 accepted` status.

### URI parameters

Key | Type | Description
--- | --- | ---
:device_identifier | string | Unique string identifier of a device
:image_identifier | string | Unique string identifier to identiy the image being uploaded. Defined when the submission was uploaded
:submission_identifer | string | Unique string identifier to identiy the submission the image is for. Defined when the submission was uploaded

## POST create submission Image for a user

* POST `/api/v3/users/:user_id/submission_images.json?image_identifier=:image_identifier&submission_identifer=:submission_identifer` 

Returns a `HTTP 202 accepted` status.

### URI parameters

Key | Type | Description
--- | --- | ---
:user_id | string | Unique string identifier of a User
:image_identifier | string | Unique string identifier to identiy the image being uploaded. Defined when the submission was uploaded
:submission_identifer | string | Unique string identifier to identiy the submission the image is for. Defined when the submission was uploaded


**Example request:**

```json
curl \
  -u your_api_token:x \
  -X POST \
  -d \
<bindary data of the image> \
  https://api.devicemagic.com/api/v3/devices/Android_123412b-1234-1234-1234-12341234/submission_images.json?image_identifier=1234&submission_identifer=5678
```
The above request, with `your_api_token` in the `Authorization` header, will return a `HTTP 202 Accepted` status, response body 
will be empty.


## GET submission Image MD5

* GET `/api/v3/devices/:device_identifier/submission_images/:image_identifier/get_md5` 

Returns the MD5 hash of the image.

### URI parameters

Key | Type | Description
--- | --- | ---
:device_identifier | string | Unique string identifier of a device
:image_identifier | string | Unique string identifier to identiy the image being uploaded. Defined when the submission was uploaded

## POST create submission Image for a user

* GET `/api/v3/users/:user_id/submission_images/:image_identifier/get_md5` 

Returns the MD5 hash of the image.

### URI parameters

Key | Type | Description
--- | --- | ---
:user_id | string | Unique string identifier of a User
:image_identifier | string | Unique string identifier to identiy the image being uploaded. Defined when the submission was uploaded


**Example request:**

```json
curl \
  -u your_api_token:x \
  -X POST \
  -d \
<bindary data of the image> \
  https://api.devicemagic.com/api/v3/devices/Android_123412b-1234-1234-1234-12341234/submission_images/1234/get_md5
```
The above request, with `your_api_token` in the `Authorization` header, will return a `HTTP 202 Accepted` status, response body 
will be empty.