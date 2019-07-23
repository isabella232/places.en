---
title: Getting started
seo-title: Getting started
description: Getting started with Experience Platform Location Services.
seo-description: Getting started with Experience Platform Location Services.
---

# Getting started {#getting-started}

Here are the tasks you need to complete before you can use Experience Platform Location Services.

## Get provisioned to use Experience Platform Location Services

Experience Platform Location Services requires special provisioning context with your regular Adobe Experience Platform provisioning context.

To get provisioned, complete the following tasks:

* In the Admin Console, ensure that your organization is provisioned with Experience Platform Location Services.   

  If you are not the Adobe administrator, contact the administrator to ensure the Experience Platform Location Services context in Admin Console.

* Ensure you are listed as a user under the Experience Platform Location Services and Launch product contexts in the Admin Console.  

   For more information, see [Adding a user to Experience Platform Launch and Experience Platform Location Services](/help/adding-a-user-to-launch-loc-services.md).

* Ensure your mobile app property is configured in Experience Platform Launch with the Places extension installed.   

  For more information, see [Places extension](/help/configure-places-in-the sdk/places-extension/places-extension.md). 

* If your company has multiple Adobe organizations, ensure that you always select the organization that is provisioned for Experience Platform Location Services.  

  This allows you to add your POIs and Libraries.

## Configure the Places extension and Places Monitor extension

For more information about configuring the Places extension and Monitor extension, see [Places extension](/help/configure-places-in-the sdk/places-extension/places-extension.md) and [Places Monitor extension](/help/configure-places-in-the sdk/places-monitor-extension/places-monitor-extension.md).

## Creating libraries and POIs

You can create libraries and POIs in one of the following ways:

* By using the web services. 

  For more information, see [Experience Platform Location Services web services](/help/loc-services-rest-apis/loc-services-web-services.md).

* By using the Experience Platform Location Services UI. 

  For more information, see [Experience Platform Location Services UI](/help/loc-services-database-management-1/loc-services-database-management.md). 

## Create an empty library in the Experience Platform Location Services database in the Experience Platform Location Services UI

1. Log into Adobe Experience Platform Location Services UI  

    The user interface helps you to visually add and manage the POIs and libraries. 
2. Click on the **Libraries** tab.
3. Click **Create Library**.
4. Type the name.
5. Click **Confirm**.

## Create a new POI in the library in the Experience Platform Location Services UI

A POI is a location or a point on a map that is of interest to you. It can include locations like cafes, restaurants, and so on.

1. Log in to [Adobe Experience Platform Location Services Services UI](https://places.adobe.com) with your Adobe ID.
2. In the map view, click **+ New POI**. 
3. Complete the following steps in the **Details** section:

   a. Type a name.

   b. Select a library.

   c. Enter or select a radius.

   d. Select the icon that you want to use for your POI.

   e. Select a color for your POI icon.

   f. Type a category.

4. Complete the following steps in the **Location** section:

   a. Type an address.

   b. Type the city.

   c. Type the name of the state.

   d. Type the name of the country.

   e. Select or enter a latitude or longitude.

   f. Click **Drop Pin on Map**.

5. Complete the following steps in the **Metadata** section:

   a. Click **Add Metadata.**

   b. Type the key name.

   c. Type the key value.

6. Click **Confirm**. 

## Get started with Experience Platform Location Services: a video

Here is a video that can help you get started with Adobe Experience Platform Location Services:

>[!VIDEO](https://www.youtube.com/watch?v=aV6i\_ayxWCw)