# Submissions Image API


## POST create submission Image for a device

* POST `/api/v3/devices/:device_identifier/submission_images.json?image_identifier=:image_identifier&submission_identifer=:submission_identifer` 

Returns a `HTTP 202 accepted` status.

### URI parameters

Key | Type | Description
--- | --- | ---
:device_identifier | string | Unique string identifier of a device
:image_identifier | string | Unique string identifier to identiy the image being uploaded. Defined when the submission was uploaded
:submission_identifer | string | Unique string identifier to identiy the submission the image is for. Defined when the submission was uploaded

---

## POST create submission Image for a user

* POST `/api/v3/users/:user_id/submission_images.json?image_identifier=:image_identifier&submission_identifer=:submission_identifer` 

Returns a `HTTP 202 accepted` status.

### URI parameters

Key | Type | Description
--- | --- | ---
:user_id | string | Unique string identifier of a User
:image_identifier | string | Unique string identifier to identiy the image being uploaded. Defined when the submission was uploaded
:submission_identifer | string | Unique string identifier to identiy the submission the image is for. Defined when the submission was uploaded

---

## GET submission Image MD5 for a device

* GET `/api/v3/devices/:device_identifier/submission_images/:image_identifier/get_md5` 

Returns the MD5 hash of the image.

### URI parameters

Key | Type | Description
--- | --- | ---
:device_identifier | string | Unique string identifier of a device
:image_identifier | string | Unique string identifier to identiy the image being uploaded. Defined when the submission was uploaded

---

## GET submission Image MD5 for a user

* GET `/api/v3/users/:user_id/submission_images/:image_identifier/get_md5` 

Returns the MD5 hash of the image.

### URI parameters

Key | Type | Description
--- | --- | ---
:user_id | string | Unique string identifier of a User
:image_identifier | string | Unique string identifier to identiy the image being uploaded. Defined when the submission was uploaded
