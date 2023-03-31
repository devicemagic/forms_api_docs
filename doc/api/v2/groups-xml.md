# XML GET all organization groups 

* GET `/api/v2/organizations/:organization_id/groups.xml` 

Returns a `XML` object with a `groups` key containing an `Array` of **group** objects.

### URI Parameters

Key | Type | Description
--- | --- | ---
:organization_id | integer | Unique identifier of your organization

### Query Parameters

Key | Type | Description
--- | --- | ---
filter | string | Paramter to filter by group name. The parameter does not need to be a complete match to find the group(filter=Def brings 'Default' group)
tags | array | Array to find groups by tags. The group only needs to have one of the passed tags to be returned(tags[]=health and tags[]=food brings a group that only has the 'health' tag)
items | integer |  Allow the client to request a custom number of items per page. Defaults to 100
page | integer | Allow the client to request specific page for item results. Defaults to 1

**example:**

```
curl -u your_api_token:x \
https://api.devicemagic.com/api/v2/organizations/7/groups.xml?filter=Def&tags[]=health&tags[]=food&page=1
```
The above request, with `api_token` in the `Authorization` header, will return a list of all groups belonging to organization with id `7`.

### Example response:

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
