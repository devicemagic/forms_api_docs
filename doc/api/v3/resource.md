# Resource API v3


## JSON|XML GET describe resource

* GET `/api/v3/resources/:resource_id/describe.(json|xml)` 

Returns a resource.

### URI query parameters

Key | Type |  Required | Description
--- | --- | --- | ---
resource_id | integer | true | id of the resuorce

**Example JSON request:**

```
curl -u your_api_token:x \
https://api.devicemagic.com/api/v3/resources/123/describe.json
```

**Example XML request:**

```
curl -u your_api_token:x \
https://api.devicemagic.com/api/v3/resources/123/describe.xml
```

The above request, with `your_api_token` in the `Authorization` header, will return a success status and all Authors with webform access

**Example JSON response body:**

```json
{
  "resource": {
    "id": 140222,
    "identifier": "dbfd3a10-249c-0133-5179-14109fd23119",
    "original_filename": "text_resource.xlsx",
    "version": 1,
    "description": "Equipment_List",
    "status": "Ready",
    "generated_content_summary": [
      {
        "table_name": "Equipment_List.Equipment_List",
        "original_sheet_name": "Equipment_List",
        "table_id": "5abae920-d3d6-013a-794d-6ae90a38da9d",
        "columns": [
          {
            "column_name": "Equipment",
            "column_number": 1,
            "column_id": "5abaf4c0-d3d6-013a-794d-6ae90a38da9d"
          },
          {
            "column_name": "Serial Number",
            "column_number": 2,
            "column_id": "5abafbf0-d3d6-013a-794d-6ae90a38da9d"
          }
        ]
      }
    ]
  }
}
```
**Example XML response body:**

```xml
<resource>
  <id>123</id>
  <identifier>dbfd3a10-249c-0133-5179-14109fd23119</identifier>
  <original_filename>Equipment_List.xlsx</original_filename>
  <version>1</version>
  <description>Equipment List</description>
  <status>Ready</status>
  <generated_content_summary>
    <tables>
      <table>
        <table_name>Equipment_List.Equipment_List</table_name>
        <table_id>5abae920-d3d6-013a-794d-6ae90a38da9d</table_id>
        <columns>
          <column>
            <column_name>Equipment</column_name>
            <column_number>1</column_number>
            <column_id>5abaf4c0-d3d6-013a-794d-6ae90a38da9d</column_id>
          </column>
          <column>
            <column_name>Serial Number</column_name>
            <column_number>2</column_number>
            <column_id>5abafbf0-d3d6-013a-794d-6ae90a38da9d</column_id>
          </column>
        </columns>
      </table>
    </tables>
  </generated_content_summary>
</resource>
```
---

## JSON POST create resource

* POST `/api/v3/resources.json` 

Returns a `HTTP 202 accepted` status.

### JSON resource parameters

Key | Type | Description
--- | --- | ---
description | string | The description of the resource
file | object | The data for the resource

### JSON File object

Key | Type | Description
--- | --- | ---
file_name | string | The name of the file
file_data  | binary | Base64 encoded file data
content_type | string | See supported [`mime types`](./doc/api/v3/resource.md#suported-mime-types) below

**Example request:**

```json
curl \
  -u your_api_token:x \
  -X POST \
  -d \
{"resource": {"description": "r3","file": {"file_name": "R2_D3.jpg","file_data": "TWFuIGlzIGRpc3Rpbmd1aXNoZWQsIG5vdC...","content_type": "image/jpeg"}}} \
  https://api.devicemagic.com/api/v3/resources.json
```
The above request, with `your_api_token` in the `Authorization` header, will return a `HTTP 202 Accepted` status, response body 
will be empty.

# Suported MIME types: #
* image/png
* image/jpeg
* application/xml
* text/xml
* text/plain
* application/vnd.device-magic.map-overlay.json
* application/pdf
* application/vnd.openxmlformats-officedocument.spreadsheetml.sheet
* application/vnd.openxmlformats-officedocument.wordprocessingml.document


## JSON PUT update resource

* PUT `/api/v3/resources/:resource_id.json` 

Returns a `HTTP 202 accepted` status.

### URI query parameters

Key | Type |  Required | Description
--- | --- | --- | ---
resource_id | integer | true | id of the resuorce

### JSON resource parameters

Key | Type | Description
--- | --- | ---
description | string | The description of the resource
file | object | The data for the resource

### JSON File object

Key | Type | Description
--- | --- | ---
file_name | string | The name of the file
file_data  | binary | Base64 encoded file data
content_type | string | See supported [`mime types`](./doc/api/v3/resource.md#suported-mime-types) above

**Example request:**

```json
curl \
  -u your_api_token:x \
  -X PUT \
  -d \
{"resource": {"description": "r3","file": {"file_name": "R2_D3.jpg","file_data": "TWFuIGlzIGRpc3Rpbmd1aXNoZWQsIG5vdC...","content_type": "image/jpeg"}}} \
  https://api.devicemagic.com/api/v3/resources/123.json
```
The above request, with `your_api_token` in the `Authorization` header, will return a `HTTP 202 Accepted` status, response body 
will be empty.
