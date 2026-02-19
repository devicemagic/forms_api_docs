# Migrating from v3 to v4 Resources API

The v4 Resources API introduces asynchronous processing for resource creation and updates, improving scalability and reliability. This guide outlines the key changes and steps to migrate from v3 to v4.

## 1. Endpoint Changes

| Action                | v3 Endpoint                                      | v4 Endpoint                                                      |
|-----------------------|--------------------------------------------------|------------------------------------------------------------------|
| Create Resource       | `POST /api/v3/resources.json`                    | `POST /api/v4/resources.json`                                    |
| Update Resource       | `PUT /api/v3/resources/:resource_id.json`        | `PUT /api/v4/resources/:resource_id.json`                        |
| Check Update Status   | *(not available)*                                | `GET /api/v4/async_resource_updates/:async_resource_update_id`   |

## 2. Asynchronous Processing

- **v3:** Resource creation and updates are processed synchronously.
- **v4:** All create and update requests are processed asynchronously. The API immediately returns a status and an `async_resource_update_id` to poll for completion.

## 3. Request and Response Changes

### Request Body

- **v3:** Uses `content_type` in the file object.
- **v4:** Uses `mime_type` in the file object.

**v3 Example:**
```json
{
  "resource": {
    "description": "image resource",
    "file": {
      "file_name": "R2_D3.jpg",
      "file_data": "Base64...",
      "content_type": "image/jpeg"
    }
  }
}
```

**v4 Example:**
```json
{
  "resource": {
    "description": "image resource",
    "file": {
      "file_name": "R2_D3.jpg",
      "file_data": "Base64...",
      "mime_type": "image/jpeg"
    }
  }
}
```

### Response

- **v3:** Returns HTTP `201`/`200` for create/update endpoints with minimal response.
- **v4:** Returns HTTP `202` with an `async_resource_update_id`, current status, and a poll URL.

**v4 Example Response:**
```json
{
  "async_resource_update_id": "uuid",
  "status": "queued",
  "poll_url": "/api/v4/async_resource_updates/uuid",
  ...
}
```

## 4. Polling for Status

After creating or updating a resource in v4, use the `async_resource_update_id` to poll the status:

```
GET /api/v4/async_resource_updates/:async_resource_update_id
```

- Statuses: `queued`, `processing`, `completed`, `failed`
- On `completed`, the response includes the resource details.
- On `failed`, the response includes an error message.

## 5. Supported MIME Types

- v4 supports a subset of v3 MIME types. More specifically it does not yet support map overlay resources. Check the [`v4 documentation`](./resource_v4.md#supported-mime-types) for the full list. See supported 

## 6. Summary of Migration Steps

1. Update your endpoints to use `/api/v4/resources`.
2. Change the file object key from `content_type` to `mime_type`.
3. Handle asynchronous responses by polling the status endpoint.
4. Update error and completion handling logic to use the new status API.

---