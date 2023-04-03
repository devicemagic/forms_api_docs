# Destinations API

Components
Destinations are made up of a Format, a Transport and optionally a Binary Transport. These are used when creating and updating destinations.

To view a full list of available formats, transports, binary transports and the available parameters for each please use the link below:
[Destination Components Documentation](https://docs.devicemagic.com/en/articles/392937-destinations-api-components)

 
## JSON GET View Destinations on a Form

* GET `/api/forms/:form_id/destinations.json`

Returns an overview of all the destinations forms belonging to a form.

### URI query parameters

Key | Type | Description
--- | --- | ---
:form_id | integer |  Unique identifier of the form
 
**Example JSON response body:**

```json
{
    "destinations": [
        {
            "id": 1,
            "description": null,
            "active": true,
            "format_type": "text_format",
            "format_id": 1,
            "transport_type": "email_transport",
            "transport_id": 1,
            "binary_transport_type": null,
            "binary_transport_id": null,
            "created_at": "2015-07-23T12:21:19.000Z",
            "updated_at": "2015-07-23T12:21:19.000Z"
        },
        {
            "id": 2,
            "description": null,
            "active": true,
            "format_type": "text_format",
            "format_id": 2,
            "transport_type": "email_transport",
            "transport_id": 2,
            "binary_transport_type": null,
            "binary_transport_id": null,
            "created_at": "2015-07-23T12:21:19.000Z",
            "updated_at": "2015-07-23T12:21:19.000Z"
        }
    ]
}
```

---

## JSON GET View Destination details

* GET `/api/forms/:form_id/destinations/:destination_id.json`

Returns an overview of all the destinations forms belonging to a form.

### URI query parameters

Key | Type | Description
--- | --- | ---
:form_id | integer |  Unique identifier of the form
:destination_id | integer |  Unique identifier of the destination
 
**Example JSON response body:**

```json
{
    "destination": {
        "id": 1,
        "description": null,
        "active": true,
        "format_type": "text_format",
        "format_id": 1,
        "transport_type": "email_transport",
        "transport_id": 1,
        "binary_transport_type": null,
        "binary_transport_id": null,
        "created_at": "2015-07-23T12:22:31.000Z",
        "updated_at": "2015-07-23T12:22:31.000Z",
        "text_format": {
            "id": 1,
            "include_images": null,
            "created_at": "2015-07-23T12:22:31.000Z",
            "updated_at": "2015-07-23T12:22:31.000Z",
            "template": null,
            "text_intro": null,
            "custom_text_content": null,
            "render_template_as_html": null,
            "location_in_coordinate_format": null,
            "include_answer_attributes": null
        },
        "email_transport": {
            "id": 1,
            "smtp_address": null,
            "smtp_port": null,
            "from_domain": null,
            "username": null,
            "password": null,
            "auth_scheme": null,
            "from_address": null,
            "from_name": null,
            "to_addresses": "bob@lol.com",
            "to_address_form_field": null,
            "subject_template": null,
            "body_template": null,
            "created_at": "2015-07-23T12:22:31.000Z",
            "updated_at": "2015-07-23T12:22:31.000Z",
            "use_tls": null,
            "via_custom_smtp": null,
            "custom_email_content": null,
            "to_address_device_attribute": null,
            "encryption": 0,
            "skip_bounce_list_check": null,
            "allow_no_email": null
        }
    }
}
```

---


## JSON POST create a destination

* POST `/api/forms/:form_id/destinations.json`

If the creation is successful you will get the destination details returned in the same format as "View destination details" above.

### URI query parameters

Key | Type | Description
--- | --- | ---
:form_id | integer |  Unique identifier of the form

### Destination form parameters

Key | Type | Description
--- | --- | ---
description | string | Description of the destination
format_selection | string | The format of the data sent by the destination
transport_selection | string | The services the destination sends to
binary_transport_selection | string | Optional. The services images, signatures and sketches are sent to

Then you need to provide the parameters for the format / transports you selected.

An example post:

**Example JSON request body:**

```
{
    "destination": {
      "description": "Some description",
      "format_selection": "text_format",
      "transport_selection": "email_transport"
    },
    "email_transport": {
      "to_addresses": "test@test.com;test2@test.com" 
    }
}  
``` 
In the above example I don't need to specify any settings for the "text_format" so I don't send any parameters through for it.

**Example JSON request body with a binary_transport:**

 
```
{
  "destination": {
    "description": "Some description",
    "format_selection": "word_format",
    "transport_selection": "http_transport",
    "binary_transport_selection": "binary_google_drive_transport"
  },
  "word_format": {
    "file_name_template": "My_Doc"
  },
  "http_transport": {
    "uri": "test.com" 
  },
  "binary_google_drive_transport": {
    "google_account_email": "myemail@gmail.com"
  }
}
```

To view a full list of available formats, transports, binary transports and the available parameters for each please use the link below:
[Destination Components Documentation](https://docs.devicemagic.com/en/articles/392937-destinations-api-components)

--- 

## JSON PUT update a destination

* PUT `/api/forms/:form_id/destinations/:destination_id.json`

For the update, send through all required parameters. Note, you cannot change the components of the destination. For example, a destination in text_format can't be changed to pdf_format. Instead, create a new destination.

### URI query parameters

Key | Type | Description
--- | --- | ---
:form_id | integer |  Unique identifier of the form
:destination_id | integer |  Unique identifier of the destination

**Example JSON request body:**

```
{
    "destination": {
      "description": "Brand new description",
    },
    "email_transport": {
      "to_addresses": "some_other_address@test.com" 
    },
    "text_format": {
      "location_in_coordinate_format": true
    }
}
```
You do not need to specify the format_selection, transport_selection or binary_transport_selection as we know what to look for from the destination.

---

## DELETE Destroying a Destination

* DELETE `/api/forms/:form_id/destinations/:destination_id.json`
You’ll receive a 200 OK if the delete succeeded, and an HTTP error response otherwise.

### URI query parameters

Key | Type | Description
--- | --- | ---
:form_id | integer |  Unique identifier of the form
:destination_id | integer |  Unique identifier of the destination
