---
title: Location Services REST APIs
seo-title: Location Services REST APIs
description: This topic is an introduction to the Location Services REST APIs.
seo-description: This topic is an introduction to the Location Services REST APIs.
---

# Places REST APIs

Places is the set of services that makes it easier for Adobe customers to hydrate the Adobe Cloud Platform and Adobe Experience Platform solutions with location data, delivering the right experience to the right person at the right time and the right place.

The Places services allows you to do the following:

* Manage Geofences
* Measure location of users even when app is in the background
* Use data in real-time when it matters

This guide explains how to use the REST APIs and the Places Database, which contains your org's point of interest \(POI\) data.

## Places REST API

The Places REST API let you work programmatically with your organization's POIs. These APIs allow you to create, update, and delete your libraries and the POIs in those libraries. These APIs use JavaScript Object Notation \(JSON\) standards to format the data that is sent and received. A principal advantage of JSON is that it helps make API queries easy to write, read, and parse by developers and machines.

Before you can use the Places API, ensure that the following requirements have been met:

1. Places is provisioned in your organization, and you have appropriate access as a user.  For more information, see [Organization requirements](/help/places-rest-apis/organizational-requirements.md).
2. After Places is provisioned in your organization, and you have access, create an Adobe Integration for Places.  For more information, see [Creating an Adobe I/O Integration](/help/places-rest-apis/adobe-i-o-integration/adobe-i-o-integration.md).

After these requirements are met, you can access to the Places REST API. For more information about information about the APIs available and how to use them, see [API Usage](/help/places-rest-apis/api-usage/api-usage.md).

To help you complete a batch import of your POIs from a `.csv` file into your organization's Places database, we created a set of Python scripts. You can download the zip file of these scripts [here](https://github.com/adobe/places-scripts). For instructions on how to use the scripts, see the included readme file.

