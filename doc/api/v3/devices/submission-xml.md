# XML GET all submission authors

* GET `/api/v3/submission_authors.xml` 

Returns an array of all `users` and `devices` with webforms access with a **Author** object as value.

### URI parameters

Key | Type | Description
--- | --- | ---
items | integer |  Allow the client to request a custom number of items per page. Defaults to 100
page | integer | Allow the client to request specific page for item results. Defaults to 1

**Example request:**

```
curl \
  -u your_api_token:x \
  https://api.devicemagic.com/api/v3/submission_authors.xml
```
The above request, with `your_api_token` in the `Authorization` header, will return a success status and all devices and users with webforms access

**Example response body:**

```xml
<?xml version="1.0" encoding="UTF-8"?>
<authors type="array">
  <author>
    <identifier>iPhone_65AD03C2-FA00-1234-1234-86D82C7F7119</identifier>
    <type>Device</type>
    <name>Iphone</name>
    <email/>
  </author>
  <author>
    <identifier>5</identifier>
    <type>User</type>
    <name>Frikkie</name>
    <email>testuser@devicemagic.com</email>
  </author>
</authors>
```
**Authors object**

Key | Type | Description
--- | --- | ---
identifier | string | Unique id a user or device
type | string | Type of author. Can be either 'Device' or 'User'
name | string | Name of the author
email | string | Email address of the author, available when the type is User

---

# XML POST create submission from a form or dispatch for device

* POST `/api/v3/devices/:device_identifier/submissions.xml` 

Returns a `HTTP 202 accepted` status 

### URI parameters

Key | Type | Description
--- | --- | ---
:device_identifier | string | Unique string identifier of a device

### Body is still json

Key | Type | Description
--- | --- | ---
form_namespace | string | Required. Unique namespace of the form template
submission_identifier | string | Required. Unique value (UUID). It needs to be changed or the submission will fail.
payload | object | Required. XML submission, the XML needs to be escaped using `\` and newline replaced with \r\n.

**Example request:**

```json
curl \
-u your_api_token:x \
-X POST \
-d \
{"payload": "\u003c?xml version='1.0' encoding='UTF-8'?\u003e\n\u003cinstance xmlns='your_form_namespace_here' submissionIdentifier='your_submission_identifier_here'\u003e\n\u003ca\u003e\n\u003cb\u003e88562-4446\u003c/b\u003e\n\u003c/a\u003e\n\u003c/instance\u003e"} \
https://api.devicemagic.com/api/v3/devices/Android_123412b-1234-1234-1234-12341234/submissions.xml
```
The above request, with `your_api_token` in the `Authorization` header, will return a `HTTP 202 Accepted` status, response body
will be empty.