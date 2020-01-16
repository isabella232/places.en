---
title: Create a library
description: Create a library by using the Places REST API.
---

# Create a library {#create-a-library}

A POST method that lets you create a library.

## Request

```text
POST https://api-places.adobe.io/places/placesapi/v1/libraries
```

## Headers

```text
-H' Content-Type: application/json'  -H 'Authorization: Bearer <TOKEN>'  -H 'x-api-key: <API KEY>'  -H 'x-gw-ims-org-id: <ORGID>'  -H 'Accept-Language: en-US'
```

## Body

```text
{"name": "<LIBRARY_NAME>"}
```

## Sample Response

```text
{       "id": "449f08f3-eff5-4658-9329-2d9687af777e",       "name": "Facinating places",      "customerID": "777F20F55BACA09E0A495D8F@AdobeOrg",       "poiCount": 0  }
```

## CURL command

Use the following CURL command to test this API:

```text
curl -X POST 'https://api-places.adobe.io/places/placesapi/v1/libraries' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>' -d '{"name":"New Library Name"}' -H "Content-Type: application/json"
```

>[!IMPORTANT]
>
>Replace variables such as `<API KEY>`, `<TOKEN>`, and `<ORGID>` with actual values.

