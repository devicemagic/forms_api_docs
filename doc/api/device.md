# Devices API

## JSON|XML GET all organization devices 

* GET `/api/v2/organizations/:organization_id/devices.(json|xml)` 

Returns a `JSON` or 'XML' object with a `devices` key containing an `Array` of **device** objects.

### URI Parameters

Key | Type | Description
--- | --- | ---
:organization_id | integer | Unique identifier of your oganization


### Example JSON response:

```json
{
  "devices": [
    {
      "id": 4,
      "identifier": "Android_12345678-1234-1234-1234-123412341234",
      "os_version": "9",
      "app_identifier": "com.devicemagic.androidx.forms",
      "app_version": "3.9.12-5",
      "organization_id": 7,
      "owner": "Test User",
      "description": null,
      "pending_approval": false,
      "groups": [
        {
          "name": "Default"
        }
      ],
      "custom_attributes": {
        "company_device": "true"
      }
    },
    {
      "id": 5,
      "identifier": "Android_87654321-1234-1234-1234-123412341234",
      "os_version": "10",
      "app_identifier": "com.devicemagic.androidx.forms",
      "app_version": "3.9.12-5",
      "organization_id": 7,
      "owner": "Test User 2",
      "description": null,
      "pending_approval": false,
      "groups": [
        {
          "name": "Default"
        }
      ],
      "custom_attributes": {}
    }
  ]
}
```

### Example XML response:

```xml
<devices type="array">
  <device>
    <id>4</id>
    <identifier>Android_12345678-1234-1234-1234-123412341234</identifier>
    <os_version>9</os_version>
    <app_identifier>com.devicemagic.androidx.forms</app_identifier>
    <app_version>3.9.12-5</app_version>
    <organization_id>7</organization_id>
    <owner>Test User</owner>
    <description></description>
    <pending_approval>false</pending_approval>
    <groups type="array">
      <name>Default</name>
    </groups>
    <custom_attributes type="array">
      <custom_attribute>
        <key>company device</key>
        <value>true</value>
      </custom_attribute>
    </custom_attributes>
  </device>
  <device>
    <id>5</id>
    <identifier>Android_87654321-1234-1234-1234-123412341234</identifier>
    <os_version>10</os_version>
    <app_identifier>com.devicemagic.androidx.forms</app_identifier>
    <app_version>3.9.12-5</app_version>
    <organization_id>7</organization_id>
    <owner>Test User 2</owner>
    <description/>
    <pending_approval>false</pending_approval>
    <groups type="array">
      <name>Default</name>
    </groups>
    <custom_attributes type="array"></custom_attributes>
  </device>
</devices>
```

**Device object**

Key | Type | Description
--- | --- | ---
id | integer | Unique id of the device
identifier | string | Unique identifier of the of the device
os_version | string | OS version of the device.
app_version | string | App version of **Device Magic** installed on the device
organization_id | integer | Unique identifier of the organization that the device belongs to
owner | string | Name of the owner of the device
description | string | Description of the device (can be `null`)
pending_approval | boolean | `true` If the device is pending approval, `false` when the device has been approved

**groups key array**

Key | Type | Description
--- | --- | ---
name | string | Name of a group this device belongs to

**custom_attributes key**

Key | Type | Description
--- | --- | ---
:any | string | String key/value pairs of custom device properties that may contain any name as a key

---

## JSON|XML GET organization device

* GET `/api/v2/organizations/:organization_id/devices/:device_id.(json|xml)`

Returns a `JSON` or `XML` representation of a **device** object

### URI Parameters

Key | Type | Description
--- | --- | ---
:organization_id | integer | Unique identifier of your oganization
:device_id | integer | Unique id of the device 


### Example JSON response:
```
{
  "id": 4,
  "identifier": "Android_12345678-1234-1234-1234-123412341234",
  "os_version": "9",
  "app_identifier": "com.devicemagic.androidx.forms",
  "app_version": "3.9.12-5",
  "organization_id": 7,
  "owner": "Test User",
  "description": "",
  "pending_approval": false,
  "groups": [
    {
      "name": "Default"
    }
  ],
  "custom_attributes": {
    "company_device": "true"
  }
}
```

### Example XML response:
```xml
<device>
  <id>4</id>
  <identifier>Android_9a4e1df8-1fd5-44c2-b67a-1dc0f2ee8752</identifier>
  <os_version>9</os_version>
  <app_identifier>com.devicemagic.androidx.forms</app_identifier>
  <app_version>3.9.12-5</app_version>
  <organization_id>7</organization_id>
  <owner>AshAndroid</owner>
  <description></description>
  <pending_approval>false</pending_approval>
  <groups type="array">
    <name>Default</name>
  </groups>
  <custom_attributes type="array">
    <custom_attribute>
      <key>is_awesome</key>
      <value>this is try</value>
    </custom_attribute>
  </custom_attributes>
</device>
```

---

## POST approving a device

* POST `/api/v2/organizations/:organization_id/devices/:device_id/approve`


### URI Parameters

Key | Type | Description
--- | --- | ---
:organization_id | integer | Unique identifier of your oganization
:device_id | integer | Unique id of the device 

---

## DELETE removing a device

* DELETE `/api/v2/organizations/:organization_id/devices/:device_id`


### URI Parameters

Key | Type | Description
--- | --- | ---
:organization_id | integer | Unique identifier of your oganization
:device_id | integer | Unique id of the device

---

## JSON|XML PUT update device

* PUT `/organizations/:organization_id/devices/:device_id.(json|xml)` 

Returns a `HTTP 202 accepted` status.

### URI query parameters

Key | Type |  Required | Description
--- | --- | --- | ---
:organization_id | integer | Unique identifier of your oganization
:device_id | integer | true | id of the device to update


**Example JSON PUT Request Body:**

```json
{  
    "device":{  
        "owner":"Andy Warhol",
        "description":"Eight Elvises",
        "groups":"Default,Unpublished",
        "custom_attributes":{
            "city": "Anchorage",
            "region": "Central"
        }
    }
}
```

**Example XML PUT Request Body:**

```json
<device>
    <owner>Andy Warhol</owner>
    <description>Eight Elvises</description>
    <groups>Default,Unpublished</groups>
</device>
```

If you leave out any elements in the payload, those properties of the device will be left unchanged.

When you specify groups, provide a comma-separated list of group names. Please don’t include spaces unless they’re actually part of the group name.