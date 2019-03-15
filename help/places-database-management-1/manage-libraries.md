# Manage libraries in the Places UI

A library is a collection of points of interest \(POI\). Up to 150K POIs can be in a library and there can be up to 100 libraries per Experience Cloud organization. 

There are various ways to organize your POIs into libraries depending what is most useful to your organization. Some customers may prefer to create a separate library for each mobile app, while others may choose to use libraries to group specific types of POIs such as coffee shops, parks, hotels, etc. For example, a major entertainment company might have a library that comprises their outdoor venues in one library, and another library that comprises retail stores. A city government might have a library that comprises all of the buildings in the city and another library that comprises all of the parks in the city. 

Libraries are defined by the following:

| Keys: | Description: |
| :--- | :--- |
| ID | a unique identifier assigned to the library at creation |
| Name | a friendly name given to a library |
| Rank | These rankings can be ignored if there are no overlapping geofences in your organization. If there are overlapping POIs, then you will want to put each of the geofences in separate libraries so they can be weighted relative to each other. A user can only be in one geofence at a time. The highest ranking of the geofences the user is in will determine his current geofence membership. If there geofences have the same library ranking, then the smallest geofence will be the user's current geofence. Please also note that the SDK is also aware of "Last entered" and "Last exited" POIs, so you have complete control of how you want your rules to fire based on user interaction with your POIs. |

## Create a library

1. Log into Adobe Places with your Adobe ID.
2. Click on the **Libraries** tab.
3. Click **Create Library**.
4. Type the name.
5. Click **Confirm**.

## Rename a library

1. Log in to Adobe Places with your Adobe ID.
2. Click the **Library** tab.
3. Click the edit \(pencil\) icon.
4. Enter the new name.
5. Click **Save**.

## Delete a library

1. Log in to Adobe Places with your Adobe ID.
2. Click the **Library** tab.
3. Click the delete \(trash can\) icon.
4. Click **Confirm**.

