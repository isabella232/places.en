# Create a library

A POST method that lets you create a library.

## Request <a id="request"></a>

```text
POST https://api-places.adobe.io/places/placesapi/v1/libraries
```

## Headers <a id="headers"></a>

```text
-H' Content-Type: application/json'  -H 'Authorization: Bearer <TOKEN>'  -H 'x-api-key: <API KEY>'  -H 'x-gw-ims-org-id: <ORGID>'  -H 'Accept-Language: en-US'
```

## Body <a id="body"></a>

```text
{"name": "<LIBRARY_NAME>"}
```

## Sample Response <a id="sample-response"></a>

```text
{       "id": "449f08f3-eff5-4658-9329-2d9687af777e",       "name": "Facinating places",      "customerID": "777F20F55BACA09E0A495D8F@AdobeOrg",       "poiCount": 0  }
```

## CURL command <a id="curl-command"></a>

Use the following CURL command to test this API:

```text
curl -X POST 'https://api-places.adobe.io/places/placesapi/v1/libraries' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>' -d '{"name":"New Library Name"}' -H "Content-Type: application/json"
```

**Important**: Replace variables such as `<API KEY>`, `<TOKEN>`, and `<ORGID>` with actual values.

