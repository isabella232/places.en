---
title: Places web services overview 
seo-title: Places web services overview 
description: Places is the set of services that makes it easier for Adobe customers to hydrate the Adobe Experience Cloud and Adobe Experience Platform solutions with location data and the right experience to the right person at the right time and in the right place.
seo-description: Places is the set of services that makes it easier for Adobe customers to hydrate the Adobe Experience Cloud and Adobe Experience Platform solutions with location data and the right experience to the right person at the right time and in the right place.
---

# Places web services overview {#places-web-services-api}

Places is the set of services that makes it easier for Adobe customers to hydrate the Adobe Cloud Platform and Adobe Experience Platform solutions with location data and the right experience to the right person at the right time and in the right place.

The Places allows you to do the following:

* Manage geofences
* Measure the location of users even when app is in the background
* Use data in real-time when it matters

This section provides information about how to use the REST APIs and the  Places database, which contains your org's POI data.

## Places REST API

The Places REST API let you work programmatically with your organization's POIs. These APIs allow you to create, update, and delete your libraries and the POIs in those libraries. These APIs use JavaScript Object Notation (JSON) standards to format the data that is sent and received. A principal advantage of JSON is that it makes API queries easy to write, read, and parse by developers and machines.

Before you can use the Places API, ensure that the following requirements have been met:

* Places is provisioned in your organization, and you have appropriate access as a user.

  For more information, see the *Organization requirements* section below.

* After Places is provisioned in your organization, and you have access, create an Adobe integration for Places. 

  For more information, see *Creating Places integration* in [Adobe I/O integration overview](/help/places-web-service-api/adobe-i-o-integration.md).

Additional information:

* For more information about information about the available APIs and how to use them, see [Manage libraries](/help/places-web-service-api/api-usage/manage-libraries/manage-libraries.md) and [Manage POIs](/help/places-web-service-api/api-usage/manage-pois/manage-pois.md). 
* For more information about the headers and parameters in these APIs, see [Headers and parameters](/help/places-web-service-api/api-usage/headers-and-parameters.md).

## Organizational requirements {#org-requirements}

To access the Places REST APIs, verify with your system administrator that the following tasks have been completed:

* Places has been provisioned and appears in the organization. 
* You have been added to the organization. 
* You have been added to Places in your organization.

    For more information, see *Adding a user to Places and Experience Platform Launch* in [Places FAQs](/help/places-faqs.md).

* You have been added as a Places developer to your organization. 

  For more information about the developer role, see [Manage developers](https://helpx.adobe.com/enterprise/using/manage-developers.html).