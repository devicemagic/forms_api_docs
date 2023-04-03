# Dispatches API


## JSON|XML GET all dispatch authors

* GET `/api/v3/dispatch_authors.(json|xml)` 

Returns an array of `authors` (all devices and users dispatches can be assigned to) with a **Author** object as value.

### URI query parameters

Key | Type | Description
--- | --- | ---
items | integer |  Allow the client to request a custom number of items per page. Defaults to 100
page | integer | Allow the client to request specific page for item results. Defaults to 1

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

Returns an array of [**Dispatch**](./dispatch.md#dispatch-object) objects assigned to a device within

### URI parameters

Key | Type | Description
--- | --- | ---
:device_identifier | string | Unique string identifier of a device

### URI query parameters

Key | Type | Description
--- | --- | ---
items | integer |  Allow the client to request a custom number of items per page. Defaults to 100
page | integer | Allow the client to request specific page for item results. Defaults to 1

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

---

## JSON|XML GET index dispatch forms for a user

* GET `/api/v3/users/:user_id/dispatches.json` 
Returns an array of **Dispatch** objects assigned to a user


### URI parameters

Key | Type | Description
--- | --- | ---
:user_id | string | Unique string identifier of a User

### URI query parameters

Key | Type | Description
--- | --- | ---
items | integer |  Allow the client to request a custom number of items per page. Defaults to 100
page | integer | Allow the client to request specific page for item results. Defaults to 1

**Example request:**

```json
curl -u your_api_token:x \
  https://api.devicemagic.com/api/v3/users/1234/dispatches.json
```

The above request, with `your_api_token` in the `Authorization` header, will return a success status and return all Dispatch forms belonging to a user with identifier `1234`

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
---

## JSON|XML GET organization dispatches

* GET `/api/v3/organization_dispatches.(json|xml)` 

Returns an array of objects each containing a `dispatches` key with a **Dispatch** object as value.

### URI query parameters

Key | Type | Description
--- | --- | ---
items | integer |  Allow the client to request a custom number of items per page. Defaults to 100
page | integer | Allow the client to request specific page for item results. Defaults to 1

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

---

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
  https://api.devicemagic.com/api/v3/dispatches/123.json
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

---

## JSON|XML POST create dispatch form for a device

* POST `/api/v3/devices/:device_identifier/dispatches.(json|XML)` 

Returns a `HTTP 202 accepted` status and a `JSON` summary representation of the new Dispatch **form** object in the response body.

### URI parameters

Key | Type | Description
--- | --- | ---
:device_identifier | string | Unique string identifier of a device

## JSON|XML POST create dispatch form for a user

* POST `/api/v3/users/:user_id/dispatches.(json|XML)` 

### URI parameters

Key | Type | Description
--- | --- | ---
:user_id | string | Unique string identifier of a User

Returns a `HTTP 202 accepted` status and a `JSON` summary representation of the new Dispatch **form** object in the response body.

### Dispatch form parameters

Key | Type | Description
--- | --- | ---
form_name | string | Optional. Name of the Dispatch form
form_namespace | string | Required. Unique namespace of the form template the Dispatch will be built from
form_description | string | Optional. Description of the Dispatch form
location | string | Optional. Lat/Long used to display the dispatch on devices, only when it is within this vicinity
geofence_radius | string | Optional. Radius in meters or feet a device needs to be from the location before the form may be edited.
address | string | Optional. Name of a place, should be used with `dm:location` property's Lat/long
scheduled_at | string | Optional. Timestamp in ISO 8601 format to specify when devices should receive a dispatch
payload | object | Required but may be empty. Keys/Values containing the pre-populated Dispatch form question and answers

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

---

## JSON|XML PATCH update dispatch form for a device

* PATCH `/api/v3/devices/:device_identifier/dispatches/:id.(json|XML)` 

Returns a `HTTP 202 accepted` status.

### URI parameters

Key | Type | Description
--- | --- | ---
:device_identifier | string | Unique string identifier of a device
:id | integer | Unique id of a Dispatch form

## JSON|XML PATCH update dispatch form for a user

* PATCH `/api/v3/users/:user_id/dispatches/:id.(json|XML)` 

### URI parameters

Key | Type | Description
--- | --- | ---
:user_id | string | Unique string identifier of a User
:id | integer | Unique id of a Dispatch form

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
---

# JSON DELETE Dispatch form for device

* DELETE `/api/v3/devices/:device_identifier/dispatches/:id.json` 

Returns a `HTTP 200 Ok` status and an empty response body.

### URI parameters

Key | Type | Description
--- | --- | ---
:device_identifier | string | Unique string identifier of a device
:id | integer | Unique id of a Dispatch form

**Example request:**

```
curl \
  -u your_api_token:x \
  -X DELETE \
  https://api.devicemagic.com/api/v3/devices/Android_123412b-1234-1234-1234-12341234/dispatches/302.json
```
The above request, with `your_api_token` in the `Authorization` header, will return a `HTTP 200 OK` status and an empty body afer Dispatch form id `302` belonging to a device with string identifier `Android_123412b-1234-1234-1234-12341234` has been deleted

---

# JSON DELETE Dispatch form for user

* DELETE `/api/v3/users/:user_id/dispatches/:id.json` 

Returns a `HTTP 200 Ok` status and an empty response body.

### URI parameters

Key | Type | Description
--- | --- | ---
:user_id | string | Unique string identifier of a user
:id | integer | Unique id of a Dispatch form

**Example request:**

```
curl \
  -u your_api_token:x \
  -X DELETE \
  https://api.devicemagic.com/api/v3/users/1234/dispatches/302.json
```
The above request, with `your_api_token` in the `Authorization` header, will return a `HTTP 200 OK` status and an empty body afer Dispatch form id `302` belonging to a device with string identifier `Android_123412b-1234-1234-1234-12341234` has been deleted

---

## JSON POST destroy all Dispatch forms for a device

* POST `/api/v3/devices/:device_identifier/dispatches/destroy_all.json` 

Returns a `HTTP 200 OK` status with an `empty` body, when all Dispatch forms belonging to the device are destroyed.

### URI parameters

Key | Type | Description
--- | --- | ---
:device_identifier | string | Unique string identifier of a device

**Example request:**

```
curl \
  -u your_api_token:x \
  -X POST \
  https://api.devicemagic.com/api/v3/devices/Android_123412b-1234-1234-1234-12341234/dispatches/destroy_all.json
```
The above request, with `your_api_token` in the `Authorization` header, will return a success status indicating all Dispatch forms belonging to device with string identifier `Android_123412b-1234-1234-1234-12341234` are destroyed.

---

## JSON POST destroy all dispatch forms for a user

* POST `/api/v3/users/:user_id/dispatches/destroy_all.json` 

### URI parameters

Key | Type | Description
--- | --- | ---
:user_id | string | Unique string identifier of a User

Returns a `HTTP 200 OK` status with an `empty` body, when all Dispatch forms belonging to the device are destroyed.

**Example request:**

```
curl \
  -u your_api_token:x \
  -X POST \
  https://api.devicemagic.com/api/v3/users/1234/dispatches/destroy_all.json
```
The above request, with `your_api_token` in the `Authorization` header, will return a success status indicating all Dispatch forms belonging to user with identifier `1234` are destroyed.

---
## Dispatch object

Key | Type | Description
--- | --- | ---
id | integer | Unique id of the form
name | string | Name of the form
namespace | string | Unique namespace of the form
version | string | Dispatch form version
organization_id | integer | Unique identifier of the organization that the form belongs to
author_identifier | string | ID of the device/user that will submit this Dispatch form
author_type | string | Type of resource that will be dispatched to, either 'User' or 'Device'
description | string | Description of the form
parent_form_id | integer | ID of the regular form that this Dispatch form was created from
parent_form_version | string | Version of the regular form that this Dispatch form was created from
created_at | timestamp | Time that the Dispatch form was created
updated_at | timestamp | Time that the form was last changed
scheduled_at | timestamp | Time that the dispatch form is set to become visible by devices