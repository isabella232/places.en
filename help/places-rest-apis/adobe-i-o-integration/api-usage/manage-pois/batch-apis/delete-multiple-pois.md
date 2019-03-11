# Delete multiple POIs

A POST method that lets you delete multiple POIs.

## Request <a id="request"></a>

```text
POST https://api-places.adobe.io/places/placesapi/v1/pois/batchDelete
```

## Headers <a id="headers"></a>

```text
-H' Content-Type: application/json'  -H 'Authorization: Bearer <TOKEN>'  -H 'x-api-key: <API KEY>'  -H 'x-gw-ims-org-id: <ORGID>'  -H 'Accept-Language: en-US'
```

## Body <a id="body"></a>

```text
{  "ids": [    "<POIID>",    "<POIID>",    .    .    .    "<POIID>",    "<POIID>"  ]}
```

## Sample Response <a id="sample-response"></a>

```text
If successful a Status of "204 No Content" is returned.
```

## CURL command <a id="curl-command"></a>

Use the following CURL command to test this API:

```text
curl -X POST 'https://api-places.adobe.io/places/placesapi/v1/pois/batchDelete' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>' --data-binary "@<PATHTOBATCHDELETEJSONFILE>" -H "Content-Type: application/json"
```

**Important**: Replace `<API KEY>`, `<TOKEN>`, `<ORGID>`, and `<PATHTOBATCHDELETEJSONFILE>` with real values.

## Sample JSON file <a id="sample-json-file"></a>

Here is the sample JSON file for the `batchDelete` API:

```text
{​"ids":["31a49d5c-c6ad-46ae-b88d-a6912a8a6b2f","6a78a729-7973-4373-9199-36da18cc5b8c","74eaa3da-2464-4298-9b6d-5376fa7ea00f"]​}
```

[  
](https://launch.gitbook.io/places-developer-by-adobe-documentation/api-usage/poi-management/batch-apis/post-poi-batch-update)

