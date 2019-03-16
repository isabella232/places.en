---
title: Headers and parameters
seo-title: Getting started
description: Headers and parameters that are available in the Places REST APIs.
seo-description: Headers and parameters that are available in the Places REST APIs.
---

# Headers and parameters {#headers-and-parameters}

Here are the details about the headers and parameters that are available in the Places REST API:

## Supported headers

| Header | Description | Method | Example |
| :--- | :--- | :--- | :--- |
| `Authorization` | Your bearer token | All |  |
| `x-api-key` | Your API key | All | `19776964b4cde49e08d8f62e5824f777b` |
| `x-gw-ims-org-id` | Your org ID | All | `18FB61145BAC2FFB0A494777@AdobeOrg` |
| `Content-Type` | Format of content sent or received | PUT, POST | `application/json` |
| `Accept-Language` | Language used for error messages | Optional | `en-US` |

## Library parameters

| Parameter | Description | Type | Limit | Request or Response | Example |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `id` | ID of library | assigned | n/a | Response | `"id": "b2488788-2d2a-462b-b1a2-305272777dda"` |
| `name` | Name of the library | string | 256 characters | both, required in request | `"name": "Amazing Places"` |
| `orgID` | Experience cloud orgID of the organization | assigned | n/a | Response | `"orgID": "777F20F55BACA09E0A495D8F@AdobeOrg"` |
| `poiCount` | Number of POIs in library | integer | 150,000 max | Response | `"poiCount": 25149` |
| `metadataDescriptors` | Count for each unique POI metadata key value pair | mixed | n/a | Response |  |
| `poiCountInCities` | Count for each unique POI city value | mixed | n/a | Response |  |

## POI parameters

| Parameter | Description | Type | Limit | Request or Response | Example |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `data` | Poi data | Array of POI details | n/a | both |  |
| `id` | ID of POI | assigned | n/a | response | `"id": "1455462b-7f9c-4220-9f42-5bbce777a0d1"` |
| `name` | Name of the POI | string | 512 characters | both, optional\* | `"name": "My Favorite Place"` |
| `description` | Description of the POI | string | 512 characters | both, optional\* | `"description": "This is a very good place."` |
| `location` | Array of type and coordinates of POI | array\(mixed\) | n/a | both | `"location": {"type": "Point", "coordinates": [-122.201007, 37.604713]` |
| `type` | Type of POI | string | only "Point" currently supported | both, required in request | `"type": "Point"` |
| `coordinates` | Array of longitude and latitude of POI | array\(float\) | longitude: -180 to 180, latitude -85 to 85 | both, required in request | `"coordinates": [-122.201007, 37.604713]` |
| `radius` | Size of circular geofence around POI | float | 10 - 2000 meters | both, required in request | `"radius": 100` |
| `country` | Country for the POI | string | 32 characters | both, optional**\*** | `"country": "United States"` |
| `state` | State for the POI | string | 32 characters | both, optional**\*** | `"state": "California"` |
| `city` | City for the POI | string | 32 characters | both, optional**\*** | `"city": "San Jose"` |
| `street` | Street address for the POI | string | 256 characters | both, optional**\*** | `"street": "122 Woz Way"` |
| `category` | Category for the POI | string | 100 characters | both, optional**\*** | `"category": "cafe"` |
| `icon` | Icon for the POI | string | 50 characters | both, optional**\*** | `"icon": "star"` |
| `color` | Color for the POI | string | 8 characters | both, optional**\*** | `"color": "blue"` |
| `metadata` | Array of key/value pairs for the POI | array\(string\) | key: 256 characters, value: 256 characters, maximum of 10 pairs | both, optional**\*** | `"metadata": {"region": "Equator"}` |
| `lib_id` | ID of the library the POI is in | n/a | n/a | both, required | `"lib_id": "ac7a0b25-c6c2-43ba-bbc6-2b1777b80fe9"` |

\* If the parameter value is not included, the value is set to `empty` in database. If the existing key/value pair is not included, the key/value pair is removed for that POI in the database.

