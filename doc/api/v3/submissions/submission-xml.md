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

# XML GET submission XMl

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
<instance xmlns="http://www.devicemagic.com/xforms/12345678-abcd-1234-abcd-123456789" xmlns:dm="http://mobileforms.devicemagic.com/xforms" submissionIdentifier="12345678-abcd-1234-abcd-123456789" submittingDevice="Android_12345678-abcd-1234-abcd-123456789" writeTime="2023-02-02T10:25:46.103-0500" formVersion="1.00" dm:submit_time="2023-02-25T19:08:40Z" dm:form="Test Form" dm:form_id="123" dm:form_version="1.00" dm:submitting_user="test@devicemagic.com" dm:submitting_device="Android_b0d2608b-a5da-4648-a68d-123456789" dm:submitting_user_id="User#123">
    <inputs>
        <Question1>Answer1</Question1>
        <Question2>Answer2</Question2>
    </inputs>
</instance>
```
