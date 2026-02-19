# V4 Resources API endpoints

## V4 JSON POST create resource

*   POST `/api/v4/resources.json`

Accepts a file for asynchronous processing and returns a `HTTP 202 Accepted` code. The response body contains an `async_resource_update_id` and a URL to poll for the status.

### JSON resource parameters

| Key         | Type   | Description                  |
| :---------- | :----- | :--------------------------- |
| description | string | The description of the resource |
| file        | object | The data for the resource    |

### JSON File object

| Key          | Type   | Description                                                  |
| :----------- | :----- | :----------------------------------------------------------- |
| file_name    | string | The name of the file                                         |
| file_data    | string | Base64 encoded file data                                     |
| mime_type | string | See supported [`mime types`](./resource_v4.md#supported-mime-types) below |

**Example JSON POST Request Body:**

```json
{
    "resource": {
        "description": "r3",
        "file": {
            "file_name": "R2_D3.jpg",
            "file_data": "TWFuIGlzIGRpc3Rpbmd1aXNoZWQsIG5vdC...",
            "mime_type": "image/jpeg"
        }
    }
}
```

**Example JSON Response Body:**

```json
{
  "async_resource_update_id": "1bddb14b-c65c-414a-9e1b-6ea99b599ba3",
  "status": "queued",
  "resource_version_when_queued": null,
  "poll_url": "/api/v4/async_resource_updates/1bddb14b-c65c-414a-9e1b-6ea99b599ba3",
  "created_at": "2026-02-09T14:19:59Z",
  "updated_at": "2026-02-09T14:19:59Z"
}
```

---

## V4 JSON PUT update resource

*   PUT `/api/v4/resources/:resource_id.json`

Accepts a file for asynchronous processing and returns a `HTTP 202 Accepted` code. The response body contains an `async_resource_update_id` and a URL to poll for the status.

### URI path parameters

| Key          | Type    | Required | Description        |
| :----------- | :------ | :------- | :----------------- |
| :resource_id | integer | true     | id of the resource |

### JSON resource parameters

| Key         | Type   | Description                  |
| :---------- | :----- | :--------------------------- |
| description | string | The description of the resource |
| file        | object | The data for the resource    |

### JSON File object

| Key          | Type   | Description                                                  |
| :----------- | :----- | :----------------------------------------------------------- |
| file_name    | string | The name of the file                                         |
| file_data    | string | Base64 encoded file data                                     |
| mime_type | string | See supported [`mime types`](./resource_v4.md#supported-mime-types) below |

**Example JSON PUT Request Body:**

```json
{
    "resource": {
        "description": "r3",
        "file": {
            "file_name": "R2_D2_2.jpg",
            "file_data": "TWFuIGlzIGRpc3Rpbmd1aXNoZWQsIG5vdC...",
            "mime_type": "image/jpeg"
        }
    }
}
```

**Example JSON Response Body:**

```json
{
  "async_resource_update_id": "1bddb14b-c65c-414a-9e1b-6ea99b599ba3",
  "status": "queued",
  "resource_version_when_queued": 1,
  "poll_url": "/api/v4/async_resource_updates/1bddb14b-c65c-414a-9e1b-6ea99b599ba3",
  "created_at": "2026-02-09T14:19:59Z",
  "updated_at": "2026-02-09T14:19:59Z"
}
```

---

## V4 JSON GET async resource update status

*   GET `/api/v4/async_resource_updates/:async_resource_update_id`

Returns the status of an async resource create/update request.

### URI query parameters

| Key          | Type   | Required | Description                               |
| :----------- | :----- | :------- | :---------------------------------------- |
| :async_resource_update_id  | string | true     | identifier of the async resource update request |

### Possible Statuses
*   `queued`: The request was successfully queued and is processing in the background.
*   `processing`: The request is still being processed.
*   `completed`: The request has completed successfully. The response will include the resource details.
*   `failed`: The request failed. The response will include an error message.

**Example JSON Response Body (Processing):**

```json
{
  "async_resource_update_id": "1bddb14b-c65c-414a-9e1b-6ea99b599ba3",
  "status": "processing",
  "resource_version_when_queued": 1,
  "poll_url": "/api/v4/async_resource_updates/1bddb14b-c65c-414a-9e1b-6ea99b599ba3",
  "created_at": "2026-02-09T14:19:59Z",
  "updated_at": "2026-02-09T14:19:59Z"
}
```

**Example JSON Response Body (Completed):**

```json
{
  "async_resource_update_id": "1bddb14b-c65c-414a-9e1b-6ea99b599ba3",
  "status": "completed",
  "resource_version_when_queued": 10,
  "resource_version_when_completed": 11,
  "resource": {
    "id": 7,
    "identifier": "59598680-e7f0-013e-f9dc-1e72db44c400",
    "original_filename": "R2_D3.jpg",
    "version": 11,
    "description":"r3"
    },
  "created_at": "2026-02-09T14:19:59Z",
  "updated_at": "2026-02-09T14:20:03Z"
  }
```

**Example JSON Response Body (Failed):**

```json
{
  "async_resource_update_id": "a1b2c3d4-e5f6-7890-1234-567890abcdef",
  "status": "failed",
  "resource_version_when_queued": 10,
  "error": "An error occurred while processing this resource update. Please retry the upload. If this issue persists, contact Support.",
  "created_at": "2026-02-09T14:19:59Z",
  "updated_at": "2026-02-09T14:20:03Z"
}
```

## Supported MIME types: ##
* image/png
* image/jpeg
* application/xml
* text/xml
* text/plain
* application/pdf
* application/vnd.openxmlformats-officedocument.spreadsheetml.sheet
* application/vnd.openxmlformats-officedocument.wordprocessingml.document
