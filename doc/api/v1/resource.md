# Resources API v1


## JSON|XML GET index resources

* GET `/api/v3/resources.(json|xml)` 

Returns a resource.

**Example JSON request:**

```
curl -u your_api_token:x \
https://api.devicemagic.com/api/resources.json
```

**Example XML request:**

```
curl -u your_api_token:x \
https://api.devicemagic.com/api/resources.xml
```

The above request, with `your_api_token` in the `Authorization` header

**Example JSON response body:**

```json
{
    "resources": [
        {
            "id": 1,
            "original_filename": "R2-D2.jpg",
            "version": 0,
            "description": "r1"
        },
        {
            "id": 2,
            "original_filename": "R2-D2.jpg",
            "version": 0,
            "description": "r2"
        }
    ]
}
```
**Example XML response body:**

```xml
<resources>
    <resource>
        <id>1</id>
        <original_filename>R2-D2.jpg</original_filename>
        <version>0</version>
        <description>r1</description>
    </resource>
    <resource>
        <id>2</id>
        <original_filename>R2-D2.jpg</original_filename>
        <version>0</version>
        <description>r2</description>
    </resource>    
</resources>
```
---

## GET download resource

* GET `https://api.devicemagic.com/api/resources/:id` 

Returns a resource.

### URI query parameters

Key | Type |  Required | Description
--- | --- | --- | ---
id | integer | true | id of the 

**Example request:**

```
curl -u your_api_token:x \
https://api.devicemagic.com/api/resources/123
```

The above request, with `your_api_token` in the `Authorization` header

Returns the contesnts of the resource

---

## DELETE destropy resource

* GET `https://api.devicemagic.com/api/resources/:id` 

Returns a resource.

### URI query parameters

Key | Type |  Required | Description
--- | --- | --- | ---
id | integer | true | id of the 

**Example request:**

```
curl -u your_api_token:x \
-X DELETE \
https://api.devicemagic.com/api/resources/123
```

The above request, with `your_api_token` in the `Authorization` header

Returns a `HTTP 202 accepted` if the delete succeeded, and an HTTP error response otherwise.
