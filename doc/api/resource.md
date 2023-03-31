# Resources API

## JSON|XML GET index resources

* GET `/api/v3/resources.(json|xml)` 

Returns a resource.

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

Returns the contesnts of the resource

---

## JSON|XML GET describe resource

* GET `/api/v3/resources/:resource_id/describe.(json|xml)` 

Returns a resource.

### URI query parameters

Key | Type |  Required | Description
--- | --- | --- | ---
resource_id | integer | true | id of the resource

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
content_type | string | See supported [`mime types`](./resource.md#suported-mime-types) below

**Example JSON POST Request Body:**

```json
{
    "resource": {
        "description": "r3",
        "file": {
            "file_name": "R2_D3.jpg",
            "file_data": "TWFuIGlzIGRpc3Rpbmd1aXNoZWQsIG5vdC...",
            "content_type": "image/jpeg"
        }
    }
}
```
The above request, with `your_api_token` in the `Authorization` header, will return a `HTTP 202 Accepted` status, response body 
will be empty.

---

## JSON PUT update resource

* PUT `/api/v3/resources/:resource_id.json` 

Returns a `HTTP 202 accepted` status.

### URI query parameters

Key | Type |  Required | Description
--- | --- | --- | ---
resource_id | integer | true | id of the resource

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
content_type | string | See supported [`mime types`](./resource.md#suported-mime-types) below

**Example JSON PUT Request Body:**

```json
{
    "resource": {
        "description": "r3",
        "file": {
            "file_name": "R2_D2_2.jpg",
            "file_data": "TWFuIGlzIGRpc3Rpbmd1aXNoZWQsIG5vdC...",
            "content_type": "image/jpeg"
        }
    }
}
```
The above request, with `your_api_token` in the `Authorization` header, will return a `HTTP 202 Accepted` status, response body 
will be empty.

## Suported MIME types: ##
* image/png
* image/jpeg
* application/xml
* text/xml
* text/plain
* application/vnd.device-magic.map-overlay.json
* application/pdf
* application/vnd.openxmlformats-officedocument.spreadsheetml.sheet
* application/vnd.openxmlformats-officedocument.wordprocessingml.document

---

## DELETE destroy resource

* DELETE `https://api.devicemagic.com/api/resources/:id` 

### URI query parameters

Key | Type |  Required | Description
--- | --- | --- | ---
id | integer | true | id of the 

**Example request:**

The above request, with `your_api_token` in the `Authorization` header

Returns a `HTTP 202 accepted` if the delete succeeded, and an HTTP error response otherwise.
