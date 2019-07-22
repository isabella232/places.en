---
title: Manage POIs in the Experience Platform Location Services UI
seo-title: Manage POIs in the Experience Platform Location Services UI
description: Use the Places UI to manage your POIs.
seo-description: Use the Places UI to manage your POIs.
---

# Manage POIs in the Places UI

POIs and libraries are created and managed in the Experience Platform Location Services database by using the Experience Platform Location Services UI.

## Defining a geofence POI

Geofences are a type of POI and are defined in the database based by the following keys:

| Keys | Description | Required? |
| :--- | :--- | :--- |
| ID | Unique identifier assigned to each POI | Yes |
| Name | Friendly Name given to the POI | Yes |
| Library | Each POI must be assigned a library for organization | Yes |
| Icon | Assist with visualizations of the POIs | Yes \(assigned default\) |
| Color | Assist with visualizations of the POIs | Yes \(assigned default\) |
| Category | Assign a common framework of categories that are common across all POIs in all libraries | No |
| Address | Street address | No |
| City | city of POI | No |
| State/Region | state or region of POI | No |
| Country | country of POI | No |
| Latitude | Latitude coordinate for center of POI | Yes |
| Longitude | Longitude coordinate for center of POI | Yes |
| Metadata | custom key + value pairs that can be assigned to POIs. This metadata streamlines future workflows by allowing you to group POIs across libraries for each to use rules and filters in downstream workflows such as send a push notification whenever someone enter a POI with Type = Competitor. | No |

## Create a POI

A point of interest (POI) is a location or a point on a map that is of interest to you. It can include locations like cafes, restaurants, and so on. 

1. Log into Adobe Experience Platform Location Services with your Adobe ID.
2. In the top left side, click **[!UICONTROL Map]**.
3. In the map view, on the lower right side, click **[!UICONTROL New POI]**. 
4. Expand the **[!UICONTROL Details]** section.
5. Type a name.
6. Select a library.
7. Enter or select a radius. 
8. Select the icon that you want to use for your POI.
9. Select a color for your POI icon.
10. Type a category.
11. Expand the **[!UICONTROL Location]** section.
12. Type an address.
13. Type the city.
14. Type the name of the state.
15. Type the name of the country.
16. Select or enter a latitude or longitude.
17. Click **[!UICONTROL Drop Pin on Map]**.
18. Expand the **Metadata** section and click **[!UICONTROL Add Metadata]**.
19. Type the key name.
20. Type the key value.
21. Click **[!UICONTROL Confirm]**.

## Edit a POI

1. Log into Experience Platform Location Services using your Adobe ID.
2. On the **[!UICONTROL Libraries]** tab, click **[!UICONTROL View POIs]**. 
3. In the list, click the POI that you want to edit.
4. Click **[!UICONTROL Confirm]**.

## Delete a POI

1. Log into Experience Platform Location Services using your Adobe ID.
2. On the **[!UICONTROL Libraries]** tab, click **[!UICONTROL View POIs]**. 
3. In the list, click the POI that you want to delete.
4. Expand the **[!UICONTROL Advanced]** section.
5. Click **[!UICONTROL Delete POI]**.
6. Click **[!UICONTROL Confirm]**.

