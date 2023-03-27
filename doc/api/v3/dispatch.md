# Dispatches API v3


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

## JSON|XML GET organization dispatches

* GET `/api/v3/organization_dispatches.(json|xml)` 


**Example request:**

```json
curl -u your_api_token:x \
  https://api.devicemagic.com/api/v3/organization_dispatches.json
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

## JSON|XML GET show dispatch

* GET `/api/v3/dispatches/:dispatch_id.(json|xml)?include_inputs=false` 

Returns the xml of the dispatch originally submitted by the mobile device.

### URI parameters

Key | Type | Description
--- | --- | ---
dispatch_id | integer |  The dispatch ID of the dispatch
include_inputs | boolean | Optional. A flag to include the field data for the dispatch 

**Example request:**

```
curl \
  -u your_api_token:x \
  https://api.devicemagic.com/api/v3/dispatches.json/123
```
The above request, with `your_api_token` in the `Authorization` header

**Example JSON response body:**

```json
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
}
```
**Example JSON response body with include_inputs=true:**

```json
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
  "inputs": {
    "Question1": "Answer1",
    "Question2": "Answer2",
  }
}
```

**Example XML response body:**

```xml
<?xml version="1.0" encoding="UTF-8"?>
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
```
**Example XML response body with include_inputs=true:**

```xml
<?xml version="1.0" encoding="UTF-8"?>
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
  <inputs>
    <Question1>Answer1</Question1>
    <Question2>Answer2</Question2>
  </inputs>
</dispatch>
```

## JSON|XML POST create dispatch form for a device

* POST `/api/v3/devices/:device_identifier/dispatches.(json|XML)` 

Returns a `HTTP 202 accepted` status.

### URI parameters

Key | Type | Description
--- | --- | ---
:device_identifier | string | Unique string identifier of a device

## JSON|XML POST create dispatch form for a user

* POST `/api/v3/users/:user_id/dispatches.(json|XML)` 

Returns a `HTTP 202 accepted` status.

**Example JSON payload:**
```xml
{
    "form_namespace": "http://www.devicemagic.com/xforms/a189a8b0-e816-0137-7257-2cde48001122",
    "form_name": "This is optional - you can change this element!",
    "form_description": "This is a sample Push Form",
    "location": "lat=35.7773663, long=-78.63876549999999",
    "address": "227 Fayetteville St Suite 802, Raleigh, NC 27601, USA",
    "scheduled_at": "2020-02-10T23:04:40+02:00",
    "payload": {
        "comments": "Easy, wasn't it?"
    }
}
```

**Example XML payload:**
```xml
<?xml version='1.0'?>
<oneshot xmlns='http://www.w3.org/2002/xforms' xmlns:dm='http://mobileforms.devicemagic.com/xforms' xmlns:h='http://www.w3.org/1999/xhtml' xmlns:xsd='http://www.w3.org/2001/XMLSchema'>
  <dm:form_name>This is optional - you can omit this element</dm:form_name>
  <dm:form_namespace>http://www.devicemagic.com/xforms/demo/2d3698c0-650c-012e-7e8e-12313b079c72</dm:form_namespace>
  <dm:form_description>This is a sample Push Form</dm:form_description>
  <dm:location>lat=35.7773663, long=-78.63876549999999</dm:location>
  <dm:address>227 Fayetteville St Suite 802, Raleigh, NC 27601, USA</dm:address>
  <dm:scheduled_at>2020-02-10T23:04:40+02:00</dm:scheduled_at>
  <comments>Easy, wasn't it?</comments>
</oneshot>
```

## JSON|XML PATCH update dispatch form for a device

* PATCH `/api/v3/devices/:device_identifier/dispatches.(json|XML)` 

Returns a `HTTP 202 accepted` status.

### URI parameters

Key | Type | Description
--- | --- | ---
:device_identifier | string | Unique string identifier of a device

## JSON|XML PATCH update dispatch form for a user

* PATCH `/api/v3/users/:user_id/dispatches.(json|XML)` 

Returns a `HTTP 202 accepted` status.

**Example JSON payload:**
```xml
{
    "form_namespace": "http://www.devicemagic.com/xforms/a189a8b0-e816-0137-7257-2cde48001122",
    "form_name": "This is optional - you can change this element!",
    "form_description": "This is a sample Push Form",
    "location": "lat=35.7773663, long=-78.63876549999999",
    "address": "227 Fayetteville St Suite 802, Raleigh, NC 27601, USA",
    "scheduled_at": "2020-02-10T23:04:40+02:00",
    "payload": {
        "comments": "Something new!"
    }
}
```

**Example XML payload:**
```xml
<?xml version='1.0'?>
<oneshot xmlns='http://www.w3.org/2002/xforms' xmlns:dm='http://mobileforms.devicemagic.com/xforms' xmlns:h='http://www.w3.org/1999/xhtml' xmlns:xsd='http://www.w3.org/2001/XMLSchema'>
  <dm:form_name>This is optional - you can omit this element</dm:form_name>
  <dm:form_namespace>http://www.devicemagic.com/xforms/demo/2d3698c0-650c-012e-7e8e-12313b079c72</dm:form_namespace>
  <dm:form_description>This is a sample Push Form</dm:form_description>
  <dm:location>lat=35.7773663, long=-78.63876549999999</dm:location>
  <dm:address>227 Fayetteville St Suite 802, Raleigh, NC 27601, USA</dm:address>
  <dm:scheduled_at>2020-02-10T23:04:40+02:00</dm:scheduled_at>
  <comments>Something new!</comments>
</oneshot>
```
