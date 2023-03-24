# Device Submission forms API v3


## JSON|XML GET all submission authors

* GET `/api/v3/submission_authors.(json|xml)` 

Returns an array of `authors` (all devices and users with webforms access) with a **Author** object as value.

### URI query parameters

Key | Type |  Required | Description
--- | --- | --- | ---
items | integer | false |  Allow the client to request a custom number of items per page. Defaults to 100
page | integer | false | Allow the client to request specific page for item results. Defaults to 1

**Example JSON request:**

```
curl -u your_api_token:x \
https://api.devicemagic.com/api/v3/submission_authors.json
```

**Example XML request:**

```
curl -u your_api_token:x \
https://api.devicemagic.com/api/v3/submission_authors.xml
```

The above request, with `your_api_token` in the `Authorization` header, will return a success status and all Authors with webform access

**Example JSON response body:**

```json
{
  "authors":[
    {
      "identifier":"iPhone_1234-123-86D82C7F7119",
      "type":"Device",
      "name":"Iphone",
      "email":null
    },
    {
      "identifier":3,
      "type":"User",
      "name":"Fanie",
      "email":"test6@devicemagic.com"
    }
  ]
}
```
**Example XML response body:**

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
## XML GET submission XML

* GET `/api/v3/submissions/:submission_id` 

Returns the xml of the submission originally submitted by the mobile device.

### URI parameters

Key | Type | Description
--- | --- | ---
submission_id | integer |  The submission ID of the submission

**Example request:**

```
curl \
  -u your_api_token:x \
  https://api.devicemagic.com/api/v3/submissions/123
```
The above request, with `your_api_token` in the `Authorization` header, will return a success status and all devices and users with webforms access

**Example response body:**

```xml
<?xml version="1.0" encoding="utf-8" standalone="yes"?>
<instance xmlns="http://www.devicemagic.com/xforms/12345678-abcd-1234-abcd-123456789" 
  xmlns:dm="http://mobileforms.devicemagic.com/xforms" 
  submissionIdentifier="12345678-abcd-1234-abcd-123456789" 
  submittingDevice="Android_12345678-abcd-1234-abcd-123456789" 
  writeTime="2023-02-02T10:25:46.103-0500" formVersion="1.00" 
  dm:submit_time="2023-02-25T19:08:40Z" dm:form="Test Form" 
  dm:form_id="123" dm:form_version="1.00" 
  dm:submitting_user="test@devicemagic.com" 
  dm:submitting_device="Android_b0d2608b-a5da-4648-a68d-123456789" 
  dm:submitting_user_id="User#123">
    <inputs>
        <Question1>Answer1</Question1>
        <Question2>Answer2</Question2>
    </inputs>
</instance>
```
---

## JSON POST create submission from a form or dispatch for device

* POST `/api/v3/devices/:device_identifier/submissions.json` 

Returns a `HTTP 202 accepted` status.

### URI parameters

Key | Type | Description
--- | --- | ---
:device_identifier | string | Unique string identifier of a device

## JSON POST create submission from a form or dispatch for user

* POST `/api/v3/users/:user_id/submissions.json` 

Returns a `HTTP 202 accepted` status.

### URI parameters

Key | Type | Description
--- | --- | ---
:user_id | string | Unique string identifier of a User

### JSON submission form parameters

Key | Type | Description
--- | --- | ---
payload | object | Required. XML submission, the XML needs to be escaped using `\` and newline replaced with \r\n. There are two parameters that need to be passed in the XML, one is form_namespace (string, Unique namespace of the form template) and the other submission_identifier (string, Unique value UUID).

**Example request:**

```json
curl \
  -u your_api_token:x \
  -X POST \
  -d \
{"payload": "\u003c?xml version='1.0' encoding='UTF-8'?\u003e\n\u003cinstance xmlns='your_form_namespace_here' submissionIdentifier='your_submission_identifier_here'\u003e\n\u003ca\u003e\n\u003cb\u003e88562-4446\u003c/b\u003e\n\u003c/a\u003e\n\u003c/instance\u003e"} \
  https://api.devicemagic.com/api/v3/devices/Android_123412b-1234-1234-1234-12341234/submissions.json
```
The above request, with `your_api_token` in the `Authorization` header, will return a `HTTP 202 Accepted` status, response body 
will be empty.