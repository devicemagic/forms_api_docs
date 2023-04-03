# Forms API

## JSON|XML GET list forms

* GET `/organizations/:organization_id/forms.(xml|json)` 

Returns a list of forms.

### URI Parameters

Key | Type | Description
--- | --- | ---
:organization_id | integer | Unique identifier of your oganization

**Example JSON response body:**

```json
{
  "forms": 
     [ {"id":2,
        "namespace":"http://www.devicemagic.com/xforms/4859c760-d9eb-012d-2595-123139016cf2", 
        "version":"1.04", 
        "description":"Description of form", 
        "group":"Unpublished"},
       {"id":1, 
        "namespace": "http://www.devicemagic.com/xforms/simple", 
        "version":"1.0", 
        "description":"Description of form", 
        "group":"Unpublished"}
     ]
}
```
**Example XML response body:**

```xml
<?xml version="1.0"?>
<forms>
  <form>
    <id>2</id>
    <name>Sample Form Two</name>
    <namespace>http://www.devicemagic.com/xforms/4859c760-d9eb-012d-2595-123139016cf2</namespace>
    <version>1.04</version>
    <description>Description of form</description>
    <group>Unpublished</group>
   </form>
   <form>
     <id>1</id>
     <name>Simple Form</name>
     <namespace>http://www.devicemagic.com/xforms/simple</namespace>
     <version>1.0</version>
     <description>Description of form</description>
     <group>Unpublished</group>
  </form>
</forms>
```
---

## JSON|XML GET Form Definition

* GET `/organizations/:organization_id/forms/:form_id.(xml|json)` 

Returns a form.

### URI query parameters

Key | Type | Description
--- | --- | ---
:organization_id | integer | Unique identifier of your oganization
:form_id | integer | id of the 
version | integer | (Optional) the verion of the form definition

Returns the contesnts of the form

**Example JSON response body:**

```json
{
  "type": "root",
  "children": [{
    "identifier": "Untitled_Question",
    "title": "Untitled Question",
    "autoIdentifier": true,
    "type": "text"
  }],
  "title": "Untitled Form",
  "namespace": "http://www.devicemagic.com/xforms/simple", 
  "version":"1.0", 
  "description":"Description of form", 
  "group":"Unpublished"
}
```

**Example XML response body:**

```xml
<?xml version="1.03"?>
<h:html xmlns:h="http://www.w3.org/1999/xhtml" xmlns:dm="http://www.devicemagic.com/XMLSchemaDataTypes" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:ev="http://www.w3.org/2001/xml-events" xmlns="http://www.w3.org/2002/xforms">
  <h:head>
    <h:title>Untitled Form</h:title>
    <model>
      <instance xmlns="http://www.devicemagic.com/xforms/ns">
        <inputs>
          <Untitled_Question/>
        </inputs>
      </instance>
    </model>
  </h:head>
  <h:body>
    <input ref="Untitled_Question">
      <label>Untitled Question</label>
    </input> 
  </h:body>
</h:html>
```
---

## JSON|XML POST create form

* POST `/organizations/:organization_id/forms.(xml|json)`  

Returns a `HTTP 201` status.

### JSON form parameters

Key | Type | Description
--- | --- | ---
:organization_id | integer | Unique identifier of your oganization

**Example JSON POST Request Body:**

```json
{
    "type": "root",
    "children": [
    {
        "identifier": "Free_Text_Question",
        "title": "Free Text Question",
        "autoIdentifier": true,
        "type": "text"
    },
    {
        "identifier": "Sketch_Question",
        "title": "Sketch Question",
        "autoIdentifier": true,
        "type": "sketch"
    } ],
    "title": "Dummy Form",
    "description": "Testing sample"
}   
```

**Example JSON response body:**

```json
{
    "id": 129,
    "namespace": "http://www.devicemagic.com/xforms/dummy_sample",
    "name": "Test Form"
}
```

**Example XML POST Request Body:**

```xml
<h:html
  xmlns='http://www.w3.org/2002/xforms'
  xmlns:dm='http://www.devicemagic.com/XMLSchemaDataTypes'
  xmlns:ev='http://www.w3.org/2001/xml-events'
  xmlns:h='http://www.w3.org/1999/xhtml'
  xmlns:xsd='http://www.w3.org/2001/XMLSchema'>
  <h:head>
      <h:title>Dummy Form</h:title>
      <model>
          <instance xmlns='http://www.devicemagic.com/xforms/dummy_form'>
              <untitled_form_1>
                  <alpha/>
                  <bravo/>
              </untitled_form_1>
          </instance>
      </model>
  </h:head>
  <h:body>
      <input ref='alpha'>
          <label>Alpha</label>
      </input>
      <input ref='bravo'>
          <label>Bravo</label>
      </input>
  </h:body>
</h:html> 
```

**Example XML response body:**

```xml
<form>
    <id>42</id>
    <namespace>http://www.devicemagic.com/xforms/dummy_form</namespace>
    <name>Dummy Form</name>
</form>
```

---

## JSON|XML PUT update form

* PUT `/organizations/:organization_id/forms/:form_id.(xml|json)` 

Returns a `HTTP 202` status.

### URI query parameters

Key | Type | Description
--- | --- | ---
:organization_id | integer | Unique identifier of your oganization
:form_id | integer | id of the 

**Example JSON POST Request Body:**

```json
{
    "type": "root",
    "children": [
    {
        "identifier": "Free_Text_Question",
        "title": "Free Text Question",
        "autoIdentifier": true,
        "type": "text"
    },
    {
        "identifier": "Sketch_Question",
        "title": "Sketch Question",
        "autoIdentifier": true,
        "type": "sketch"
    } ],
    "title": "Dummy Form",
    "description": "Testing sample"
}   
```

**Example JSON response body:**

```json
{
    "id": 129,
    "namespace": "http://www.devicemagic.com/xforms/dummy_sample",
    "name": "Test Form",
    "version": "1.1"
}
```

**Example XML POST Request Body:**

```xml
<h:html
  xmlns='http://www.w3.org/2002/xforms'
  xmlns:dm='http://www.devicemagic.com/XMLSchemaDataTypes'
  xmlns:ev='http://www.w3.org/2001/xml-events'
  xmlns:h='http://www.w3.org/1999/xhtml'
  xmlns:xsd='http://www.w3.org/2001/XMLSchema'>
  <h:head>
      <h:title>Some Form</h:title>
      <model>
          <instance xmlns='http://www.devicemagic.com/xforms/dummy_form'>
              <untitled_form_1>
                  <alpha/>
                  <bravo/>
              </untitled_form_1>
          </instance>
      </model>
  </h:head>
  <h:body>
      <input ref='alpha'>
          <label>Alpha</label>
      </input>
      <input ref='bravo'>
          <label>Bravo</label>
      </input>
  </h:body>
</h:html>
```

**Example XML response body:**

```xml
<form>
    <id>42</id>
    <namespace>http://www.devicemagic.com/xforms/dummy_form</namespace>
    <name>Some Form</name>
    <version>1.1</version>
</form>
```

---

## DELETE destroy form

* DELETE `/organizations/:organization_id/forms/:form_id` 

You’ll receive a 200 OK if the delete succeeded.

### URI query parameters

Key | Type | Description
--- | --- | ---
:organization_id | integer | Unique identifier of your oganization
:form_id | integer | id of the 

---

## JSON|XML POST Updating a Form’s Group

* POST `/organizations/:organization_id/forms/:form_id/properties.(xml|json)` 

On success you’ll receive a 200 OK. If the request fails, check the response header ‘Message’ for the reason.

### URI query parameters

Key | Type | Description
--- | --- | ---
:organization_id | integer | Unique identifier of your oganization
:form_id | integer | id of the 


**Example JSON request body:**

```json
{
    "group": "Unpublished"
}
```

**Example XML request body:**

```xml
<form_properties>
    <group>Unpublished</group>
</form_properties>
```

Please note that the group name is case sensitive, and must exist within your organization.

---

## PUT Locking a form

* PUT `api/v3/forms/:form_id/lock` 

On success you’ll receive a 200 OK. If the request fails, check the response header ‘Message’ for the reason.

### URI query parameters

Key | Type | Description
--- | --- | ---
:form_id | integer | id of the 

---

## PUT Unocking a form

* PUT `api/v3/forms/:form_id/unlock` 

On success you’ll receive a 200 OK. If the request fails, check the response header ‘Message’ for the reason.

### URI query parameters

Key | Type | Description
--- | --- | ---
:form_id | integer | id of the 