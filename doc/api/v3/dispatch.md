# Dispatces API v3


## JSON|XML GET all dispatch authors

* GET `/api/v3/dispatch_authors.(json|xml)` 

Returns an array of `authors` (all devices and users dispatches can be assigned to) with a **Author** object as value.

**Example JSON request:**

```
curl -u your_api_token:x \
https://api.devicemagic.com/api/v3/dispatch_authors.json
```

**Example XML request:**

```
curl -u your_api_token:x \
https://api.devicemagic.com/api/v3/dispatch_authors.xml
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

## JSON|XML GET index dispatch forms for a device

* GET `/api/v3/devices/:device_identifier/dispatches.json` 

### URI parameters

Key | Type | Description
--- | --- | ---
:device_identifier | string | Unique string identifier of a device

**Example request:**

```json
curl -u your_api_token:x \
  https://api.devicemagic.com/api/v3/devices/Android_123412b-1234-1234-1234-12341234/dispatches.json
```

**Example JSON response body:**

```json
{
  "dispatches": [
    {
      "id": 296,
      "name": "Test Dispatch form",
      "namespace": "http://www.devicemagic.com/xforms/1234-123-123?1234-123-123",
      "version": "1.01",
      "organization_id": 7,
      "device_id": 4,
      "description": "Test Dispatch form description",
      "parent_form_id": 270,
      "parent_form_version": "1.02",
      "created_at": "2020-03-12T14:47:22.000Z",
      "updated_at": "2020-03-12T14:47:22.000Z",
      "scheduled_at": "2020-02-10T21:04:40.000Z",
    },
  ]
}
```

**Example XML response body:**

```xml
<?xml version="1.0" encoding="UTF-8"?>
<dispatches type="array">
  <dispatch>
    <id type="integer">296</id>
    <name>Test Dispatch form</name>
    <namespace>http://www.devicemagic.com/xforms/1234-123-123?1234-123-123</namespace>
    <version>1.01</version>
    <organization-id type="integer">7</organization-id>
    <device-id type="integer">4</device-id>
    <description>Test Dispatch form description</description>
    <parent-form-id type="integer">198</parent-form-id>
    <parent-form-version>1.00</parent-form-version>
    <created-at type="dateTime">2020-03-13T13:48:58Z</created-at>
    <scheduled-at type="dateTime">2020-03-13T13:48:56Z</scheduled-at>
  </dispatch>
</dispatches>
```

## JSON|XML GET index dispatch forms for a user

* GET `/api/v3/users/:user_id/dispatches.json` 

### URI parameters

Key | Type | Description
--- | --- | ---
:user_id | string | Unique string identifier of a User

**Example request:**

```json
curl -u your_api_token:x \
  https://api.devicemagic.com/api/v3/users/1234/dispatches.json
```

**Example JSON response body:**

```json
{
  "dispatches": [
    {
      "id": 296,
      "name": "Test Dispatch form",
      "namespace": "http://www.devicemagic.com/xforms/1234-123-123?1234-123-123",
      "version": "1.01",
      "organization_id": 7,
      "device_id": 4,
      "description": "Test Dispatch form description",
      "parent_form_id": 270,
      "parent_form_version": "1.02",
      "created_at": "2020-03-12T14:47:22.000Z",
      "updated_at": "2020-03-12T14:47:22.000Z",
      "scheduled_at": "2020-02-10T21:04:40.000Z",
    },
  ]
}
```

**Example XML response body:**

```xml
<?xml version="1.0" encoding="UTF-8"?>
<dispatches type="array">
  <dispatch>
    <id type="integer">296</id>
    <name>Test Dispatch form</name>
    <namespace>http://www.devicemagic.com/xforms/1234-123-123?1234-123-123</namespace>
    <version>1.01</version>
    <organization-id type="integer">7</organization-id>
    <device-id type="integer">4</device-id>
    <description>Test Dispatch form description</description>
    <parent-form-id type="integer">198</parent-form-id>
    <parent-form-version>1.00</parent-form-version>
    <created-at type="dateTime">2020-03-13T13:48:58Z</created-at>
    <scheduled-at type="dateTime">2020-03-13T13:48:56Z</scheduled-at>
  </dispatch>
</dispatches>
```

## XML GET dispatch XML

* GET `/api/v3/dispatches/:dispatch_id` 

Returns the xml of the dispatch originally submitted by the mobile device.

### URI parameters

Key | Type | Description
--- | --- | ---
dispatch_id | integer |  The dispatch ID of the dispatch

**Example request:**

```
curl \
  -u your_api_token:x \
  https://api.devicemagic.com/api/v3/dispatches/123
```
The above request, with `your_api_token` in the `Authorization` header, will return a success status and all devices and users with webforms access

**Example response body:**

```xml
<?xml version="1.0" encoding="utf-8" standalone="yes"?>
<instance xmlns="http://www.devicemagic.com/xforms/12345678-abcd-1234-abcd-123456789" 
  xmlns:dm="http://mobileforms.devicemagic.com/xforms" 
  dispatchIdentifier="12345678-abcd-1234-abcd-123456789" 
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


## JSON POST create dispatch form for a device

* POST `/api/v3/devices/:device_identifier/dispatches.json` 

Returns a `HTTP 202 accepted` status.

### URI parameters

Key | Type | Description
--- | --- | ---
:device_identifier | string | Unique string identifier of a device

## JSON POST create dispatch for a user

* POST `/api/v3/users/:user_id/dispatches.json` 

Returns a `HTTP 202 accepted` status.

### URI parameters

Key | Type | Description
--- | --- | ---
:user_id | string | Unique string identifier of a User

### JSON dispatch form parameters

Key | Type | Description
--- | --- | ---
payload | object | Required. XML dispatch, the XML needs to be escaped using `\` and newline replaced with \r\n. There are two parameters that need to be passed in the XML, one is form_namespace (string, Unique namespace of the form template) and the other dispatch_identifier (string, Unique value UUID).

**Example request:**

```json
curl \
  -u your_api_token:x \
  -X POST \
  -d \
{"payload": "\u003c?xml version='1.0' encoding='UTF-8'?\u003e\n\u003cinstance xmlns='your_form_namespace_here' dispatchIdentifier='your_dispatch_identifier_here'\u003e\n\u003ca\u003e\n\u003cb\u003e88562-4446\u003c/b\u003e\n\u003c/a\u003e\n\u003c/instance\u003e"} \
  https://api.devicemagic.com/api/v3/devices/Android_123412b-1234-1234-1234-12341234/dispatches.json
```
The above request, with `your_api_token` in the `Authorization` header, will return a `HTTP 202 Accepted` status, response body 
will be empty.