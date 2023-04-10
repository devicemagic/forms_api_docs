# Submissions API

## JSON GET view submissions in Device Magic Database

* GET `api/forms/:form_id/device_magic_database.json` 

**Note**: Your form's Device Magic Database Destination needs to be active and have submissions in it, in order to view these submissions using the API.

### URI query parameters

Key | Type | Description
--- | --- | ---
:form_id | integer |  Unique identifier of the form
page | integer | Allow the client to request specific page for item results. Defaults to 1
per_page | integer |  Allow the client to request a custom number of items per page. Defaults to 30
from_date | date | Submissions made after date
to_date | date | Submissions made before date
submission_ids | list of strings | Comma seperated list of submission ids (note: ids not submission identifiers)
device_id | string | A device identifier to filter by
search | string | A free text search that matches against the text in the submission

**Example JSON response body:**

```json
{
  "per_page": 5,
  "current_page": 1,
  "total_pages": 2,
  "current_count": 5,
  "total_count": 7,
  "submissions": [{
    "form": {
      "id": 441,
      "name": "Simple Test Form",
      "version": "1.00"
    },
    "metadata": {
      "device_id": {
        "value": "iPhone_1",
        "type": "string"
      },
      "user_id": {
        "value": null,
        "type": "string"
      },
      "username": {
        "value": "Matty6s",
        "type": "string"
      },
      "submitted_at": {
        "value": "2016-05-04 11:25:49 +02:00",
        "type": "datetime"
      },
      "received_at": {
        "value": "2016-05-04 09:25:49 +00:00",
        "type": "datetime"
      },
      "submission_id": {
        "value": "233",
        "type": "integer"
      },
      "device_submission_identifier": {
        "value": "A8F925ED-52E0-4243-AD25-E0EDBB051A3F",
        "type": "integer"
      },
      "form_name": {
        "value": "Simple Test Form"
      },
      "form_namespace": {
        "value": "https://www.devicemagic.com/xforms/9be7df80-f407-0133-d8cb-14109fd23119"
      },
      "form_version": {
        "value": "1.00"
      },
      "device": {
        "value": {
          "a": null
        }
      }
    },
    "submission": {
      "Basic_Question": {
        "value": "Test answer 1",
        "type": "text"
      },
      "Date___Time_Question": {
        "value": "2016-05-03 09:25:42",
        "type": "datetime"
      }
    }
  }, {
    "form": {
      "id": 441,
      "name": "Simple Test Form",
      "version": "1.00"
    },
    "metadata": {
      "device_id": {
        "value": "iPhone_1",
        "type": "string"
      },
      "user_id": {
        "value": null,
        "type": "string"
      },
      "username": {
        "value": "Matty6s",
        "type": "string"
      },
      "submitted_at": {
        "value": "2016-05-04 11:26:04 +02:00",
        "type": "datetime"
      },
      "received_at": {
        "value": "2016-05-04 09:26:04 +00:00",
        "type": "datetime"
      },
      "submission_id": {
        "value": "234",
        "type": "integer"
      },
      "device_submission_identifier": {
        "value": "74F31AFF-2475-4EB2-A333-7BD43CF6CD93",
        "type": "integer"
      },
      "form_name": {
        "value": "Simple Test Form"
      },
      "form_namespace": {
        "value": "https://www.devicemagic.com/xforms/9be7df80-f407-0133-d8cb-14109fd23119"
      },
      "form_version": {
        "value": "1.00"
      },
      "device": {
        "value": {
          "a": null
        }
      }
    },
    "submission": {
      "Basic_Question": {
        "value": "Test answer 2",
        "type": "text"
      },
      "Date___Time_Question": {
        "value": "2016-05-04 11:25:58",
        "type": "datetime"
      }
    }
  }, {
    "form": {
      "id": 441,
      "name": "Simple Test Form",
      "version": "1.00"
    },
    "metadata": {
      "device_id": {
        "value": "iPhone_1",
        "type": "string"
      },
      "user_id": {
        "value": null,
        "type": "string"
      },
      "username": {
        "value": "Matty6s",
        "type": "string"
      },
      "submitted_at": {
        "value": "2016-05-04 11:26:15 +02:00",
        "type": "datetime"
      },
      "received_at": {
        "value": "2016-05-04 09:26:16 +00:00",
        "type": "datetime"
      },
      "submission_id": {
        "value": "235",
        "type": "integer"
      },
      "device_submission_identifier": {
        "value": "BBEDE777-893E-4075-8D92-A4764BC08953",
        "type": "integer"
      },
      "form_name": {
        "value": "Simple Test Form"
      },
      "form_namespace": {
        "value": "https://www.devicemagic.com/xforms/9be7df80-f407-0133-d8cb-14109fd23119"
      },
      "form_version": {
        "value": "1.00"
      },
      "device": {
        "value": {
          "a": null
        }
      }
    },
    "submission": {
      "Basic_Question": {
        "value": "Test answer 3",
        "type": "text"
      },
      "Date___Time_Question": {
        "value": "2016-05-04 11:26:11",
        "type": "datetime"
      }
    }
  }, {
    "form": {
      "id": 441,
      "name": "Simple Test Form",
      "version": "1.00"
    },
    "metadata": {
      "device_id": {
        "value": "iPhone_1",
        "type": "string"
      },
      "user_id": {
        "value": null,
        "type": "string"
      },
      "username": {
        "value": "Matty6s",
        "type": "string"
      },
      "submitted_at": {
        "value": "2016-05-04 11:26:35 +02:00",
        "type": "datetime"
      },
      "received_at": {
        "value": "2016-05-04 09:26:35 +00:00",
        "type": "datetime"
      },
      "submission_id": {
        "value": "236",
        "type": "integer"
      },
      "device_submission_identifier": {
        "value": "7688475F-1659-4E67-A5BE-915449D104E3",
        "type": "integer"
      },
      "form_name": {
        "value": "Simple Test Form"
      },
      "form_namespace": {
        "value": "https://www.devicemagic.com/xforms/9be7df80-f407-0133-d8cb-14109fd23119"
      },
      "form_version": {
        "value": "1.00"
      },
      "device": {
        "value": {
          "a": null
        }
      }
    },
    "submission": {
      "Basic_Question": {
        "value": "Test answer 4",
        "type": "text"
      },
      "Date___Time_Question": {
        "value": "2016-06-16 02:28:23",
        "type": "datetime"
      }
    }
  }, {
    "form": {
      "id": 441,
      "name": "Simple Test Form",
      "version": "1.00"
    },
    "metadata": {
      "device_id": {
        "value": "iPhone_1",
        "type": "string"
      },
      "user_id": {
        "value": null,
        "type": "string"
      },
      "username": {
        "value": "Matty6s",
        "type": "string"
      },
      "submitted_at": {
        "value": "2016-05-04 11:26:48 +02:00",
        "type": "datetime"
      },
      "received_at": {
        "value": "2016-05-04 09:26:48 +00:00",
        "type": "datetime"
      },
      "submission_id": {
        "value": "237",
        "type": "integer"
      },
      "device_submission_identifier": {
        "value": "9BAD6AA2-1D03-4E74-8962-8BC9FD80C57B",
        "type": "integer"
      },
      "form_name": {
        "value": "Simple Test Form"
      },
      "form_namespace": {
        "value": "https://www.devicemagic.com/xforms/9be7df80-f407-0133-d8cb-14109fd23119"
      },
      "form_version": {
        "value": "1.00"
      },
      "device": {
        "value": {
          "a": null
        }
      }
    },
    "submission": {
      "Basic_Question": {
        "value": "Test answer 5",
        "type": "text"
      },
      "Date___Time_Question": {
        "value": "2016-05-25 10:03:40",
        "type": "datetime"
      }
    }
  }]
}
```


---

## JSON|XML GET all submission authors

* GET `/api/v3/submission_authors.(json|xml)` 

Returns an array of `authors` (all devices and users with webforms access) with a **Author** object as value.

### URI query parameters

Key | Type | Description
--- | --- | ---
items | integer | Optional. Allow the client to request a custom number of items per page. Defaults to 100
page | integer | Optional. Allow the client to request specific page for item results. Defaults to 1

**Example JSON request:**

```
curl -u your_api_token:x \
https://api.devicemagic.com/api/v3/submission_authors.json
```

**Example XML request:**

```
curl -u your_api_token:x \
https://api.devicemagic.com/api/v3/submission_authors.xml
```

The above request, with `your_api_token` in the `Authorization` header, will return a success status and all Authors with webform access

**Example JSON response body:**

```json
{
  "authors":[
    {
      "identifier":"iPhone_1234-123-86D82C7F7119",
      "type":"Device",
      "name":"Iphone",
      "email":null
    },
    {
      "identifier":3,
      "type":"User",
      "name":"Fanie",
      "email":"test6@devicemagic.com"
    }
  ]
}
```
**Example XML response body:**

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


---
## XML GET original submission XML

* GET `/api/v3/submissions/:submission_id` 

Returns the xml of the submission originally submitted by the mobile device.

### URI parameters

Key | Type | Description
--- | --- | ---
submission_id | integer |  The submission ID of the submission

**Example request:**

```
curl \
  -u your_api_token:x \
  https://api.devicemagic.com/api/v3/submissions/123
```
The above request, with `your_api_token` in the `Authorization` header

**Example response body:**

```xml
<?xml version="1.0" encoding="utf-8" standalone="yes"?>
<instance xmlns="http://www.devicemagic.com/xforms/12345678-abcd-1234-abcd-123456789" 
  xmlns:dm="http://mobileforms.devicemagic.com/xforms" 
  submissionIdentifier="12345678-abcd-1234-abcd-123456789" 
  submittingDevice="Android_12345678-abcd-1234-abcd-123456789" 
  writeTime="2023-02-02T10:25:46.103-0500" formVersion="1.00" 
  dm:submit_time="2023-02-25T19:08:40Z" dm:form="Test Form" 
  dm:form_id="123" dm:form_version="1.00" 
  dm:submitting_user="test@devicemagic.com" 
  dm:submitting_device="Android_b0d2608b-a5da-4648-a68d-123456789" 
  dm:submitting_user_id="User#123">
    <inputs>
        <Question1>Answer1</Question1>
        <Question2>Answer2</Question2>
    </inputs>
</instance>
```
---

## JSON POST create submission from a form for a device

* POST `/api/v3/devices/:device_identifier/submissions.json` 

Returns a `HTTP 202 accepted` status.

### URI parameters

Key | Type | Description
--- | --- | ---
:device_identifier | string | Unique string identifier of a device

## JSON POST create submission from a form for a user

* POST `/api/v3/users/:user_id/submissions.json` 

Returns a `HTTP 202 accepted` status.

### URI parameters

Key | Type | Description
--- | --- | ---
:user_id | string | Unique string identifier of a User

### JSON submission form parameters

Key | Type | Description
--- | --- | ---
payload | object | Required. XML submission, the XML needs to be escaped using `\` and newline replaced with \r\n. There are two parameters that need to be passed in the XML, one is form_namespace (string, Unique namespace of the form template) and the other submission_identifier (string, Unique value UUID).

**Example request:**

```json
curl \
  -u your_api_token:x \
  -X POST \
  -d \
{"payload": "\u003c?xml version='1.0' encoding='UTF-8'?\u003e\n\u003cinstance xmlns='your_form_namespace_here' submissionIdentifier='your_submission_identifier_here'\u003e\n\u003ca\u003e\n\u003cb\u003e88562-4446\u003c/b\u003e\n\u003c/a\u003e\n\u003c/instance\u003e"} \
  https://api.devicemagic.com/api/v3/devices/Android_123412b-1234-1234-1234-12341234/submissions.json
```
The above request, with `your_api_token` in the `Authorization` header, will return a `HTTP 202 Accepted` status, response body 
will be empty.