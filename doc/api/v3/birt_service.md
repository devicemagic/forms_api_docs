# BIRT Service API v3


## GET download submission image

* GET `/api/v3/download_submission_image` 

BIRT needs images to generate PDFs for destination deliveries

### URI query parameters

Key | Type |  Required | Description
--- | --- | --- | ---
uuid | integer | true |  id of the PDF Image

**Example request:**

```
curl -u your_api_token:x \
https://api.devicemagic.com/submission_image:uuid
```

The above request, with `your_api_token` in the `Authorization` header, will return a success status and all Authors with webform access

The response will be the binary data of the image
