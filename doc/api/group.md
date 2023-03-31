# Group API

## JSON|XML GET all organization groups 

* GET `/api/v2/organizations/:organization_id/groups.(json|xml)` 

Returns a `JSON` object with a `groups` key containing an `Array` of **group** objects.

### URI Parameters

Key | Type | Description
--- | --- | ---
organization_id | integer | Unique identifier of your oganization

### Query Parameters

Key | Type | Description
--- | --- | ---
filter | string | Paramter to filter by group name. The parameter does not need to be a complete match to find the group(filter=Def brings 'Default' group)
tags | array | Array to find groups by tags. The group only needs to have one of the passed tags to be returned(tags[]=health and tags[]=food brings a group that only has the 'health' tag)
items | integer |  Allow the client to request a custom number of items per page. Defaults to 100
page | integer | Allow the client to request specific page for item results. Defaults to 1


**example:**

```
https://api.devicemagic.com/api/v2/organizations/7/groups.json?filter=Def&tags[]=health&tags[]=food&page=1
```

### Example JSON response:

```json
{
  "groups": [
    {
      "id": 3,
      "name": "Default",
      "device_ids": [
        4,
        7
      ],
      "form_ids": [
        9,
        13
      ],
      "tags": [
        "food",
        "health"
      ]
    },
    {
      "id": 4,
      "name": "Unpublished",
      "device_ids": [],
      "form_ids": [],
      "tags": [
        "food"
      ]
    }
  ]
}
```
### Example XML response:

```xml
<groups type="array">
  <group>
    <id>3</id>
    <name>Default</name>
    <device_ids type="array">
      <device_id>8</device_id>
    </device_ids>
    <form_ids type="array">
      <form_id>8</form_id>
      <form_id>10</form_id>
    </form_ids>
    <tags type="array">
      <name>food</name>
      <name>health</name>
    </tags>
  </group>
  <group>
    <id>4</id>
    <name>Unpublished</name>
    <device_ids type="array">
      <form_id>5</form_id>
    </device_ids>
    <form_ids type="array">
    </form_ids>
    <tags type="array">
      <name>food</name>
    </tags>
  </group>
</groups>
```

**Group object**

Key | Type | Description
--- | --- | ---
id | integer | Unique id of the group
name | string | Name of the group

**device ids array**

 Type | Description
 --- | ---
 integer | Ids of the devices this group belongs to

 **forms ids array**

 Type | Description
 --- | ---
 integer | Ids of the forms this group belongs to

 **tags name array**

 Type | Description
 --- | ---
 string | Names of the tags this group has

---

## JSON|XML POST create group

* POST `/organizations/:organization_id/groups.(json|xml)` 

Returns a `HTTP 202 accepted` status.

### JSON group parameters

Key | Type | Description
--- | --- | ---
organization_id | integer | Unique identifier of your oganization

**Example JSON POST Request Body:**

```json
[ "A First Group", "A Second Group" ]
```

**Example XML POST Request Body:**

```json
<groups>
    <group>
        <name>A First Group</name>
    </group>
    <group>
        <name>A Second Group</name>
    </group>
</groups>
```

---

## JSON PUT update group

* PUT `/organizations/:organization_id/groups/:group_id.(json|xml)` 

Returns a `HTTP 202 accepted` status.

### URI query parameters

Key | Type |  Required | Description
--- | --- | --- | ---
organization_id | integer | Unique identifier of your oganization
group_id | integer | true | id of the group to update

You can update the name, form_ids and device_ids.
If you do not want to update an attribute, just leave it out.


**Example JSON POST Request Body:**

```json
{
  "group": {
    "name": "An updated group name",
    "form_ids": [1,2],
    "device_ids": [4,5,12]
  }
}
```

**Example XML POST Request Body:**

```json
<group>
  <name>An updated group name</name>
  <form_ids>
    <form_id>1</form_id>
    <form_id>2</form_id>
  </form_ids>
  <device_ids>
    <device_id>4</device_id>
    <device_id>5</device_id>
    <device_id>12</device_id>
  </device_ids>
</group>
```
If your group was updated, the server will respond with a 200 OK.
If there was an error while updating, the server will respond with a 400 Bad Request and an error message in the body.

---

## DELETE destroy group

* DELETE `/organizations/:organization_id/groups/:group_id` 

### URI query parameters

Key | Type |  Required | Description
--- | --- | --- | ---
organization_id | integer | Unique identifier of your oganization
group_id | integer | true | id of the group to delete

Returns a `HTTP 202 accepted` if the delete succeeded, and an HTTP error response otherwise.
