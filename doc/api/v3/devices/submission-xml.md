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