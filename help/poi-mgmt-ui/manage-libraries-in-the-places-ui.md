---
title: Manage libraries in the Places UI
seo-title: Manage libraries in the Places UI
description: Manage your libraries by using the Places UI.
seo-description: Manage your libraries by using the Places UI.
---

# Manage libraries {#manage-libraries-places-ui}

A library is a collection of POIs. You can have up to 150,000 POIs in a library, and there can be up to 100 libraries per Experience Cloud organization.  

There are various ways to organize your POIs into libraries depending what is most useful to your organization. Some customers might prefer to create a separate library for each mobile app, while other customers might use libraries to group specific types of POIs such as coffee shops, parks, hotels, and so on. For example, a major entertainment company might have a library that comprises their outdoor venues in one library and their retail stores in another library. A city government might have a library that comprises all of the buildings in the city and another library that comprises all of the parks in the city.  

Libraries are defined by the following:

| Keys: | Description: |
| :--- | :--- |
| ID | a unique identifier assigned to the library at creation |
| Name | a friendly name given to a library |
| Rank | These rankings can be ignored if there are no overlapping geofences in your organization. If there are overlapping POIs, we recommend that you put each of the geofences in separate libraries, so they can be weighted relative to each other. A user can only be in one geofence at a time. <br><br>The highest ranking of the geofences a user is in determines his or her current geofence membership. If there geofences have the same library ranking, the smallest geofence is the user's current geofence. <br><br>The SDK is also aware of *Last entered* and *Last exited* POIs, so you have complete control of how you want your rules to fire based on user interaction with your POIs. |

## Create a library

1. Log into Places with your Adobe ID.
2. In the top right side, click **[!UICONTROL ...]**  > **[!UICONTROL Manage Libraries]**. 
3. Click **[!UICONTROL New]**.
4. Type the name.
5. Click **[!UICONTROL Confirm]**.

## Change the rank of a library in the Places UI

1. Log in to Places with your Adobe ID.
2. In the top right side, click **[!UICONTROL ...]**  > **[!UICONTROL Manage Libraries]**.
3. Click the icon to the left of the library name and drag the library to the new rank. 

## Rename a library

1. Log in to Places with your Adobe ID.
2. In the top right side, click **[!UICONTROL ...]** > **[!UICONTROL Manage Libraries]**.
3. Locate the library that you want to delete.
4. Click **[!UICONTROL ...]** and select **[!UICONTROL Rename]**.
5. Update the name and click **[!UICONTROL Save]**.

## Delete a library

1. Log in to Places with your Adobe ID.
2. In the top right side, click **[!UICONTROL ...]** > **[!UICONTROL Manage Libraries]**.
3. Locate the library that you want to delete.
4. Click **[!UICONTROL ...]** and select **[!UICONTROL Delete]**.

