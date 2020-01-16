---
title: Bulk upload POIs
description: This section provides information about how to bulk upload your POIs.
---

# Bulk upload of POIs {#bulk-upload-pois}

A set of Python scripts have been created to simplify the batch import of POIs from a .csv file into a POI database by using the Web Service APIs. These scripts can be downloaded from this open source [git repo](https://github.com/adobe/places-scripts). 

Before you run these scripts, to access the web service APIs, see *Prerequisites for user access* in [Integration overview and prerequisites](/help/web-service-api/adobe-i-o-integration.md). 

Here is some information about the scripts:

>[!TIP]
>
>This information is also included in a readme file in the [git repo](https://github.com/adobe/places-scripts).

## CSV file

A sample .csv file, `places_sample.csv`, is part of this package and includes the required headers and a row of sample data. These headers are all lower case and correspond to the reserved metadata keys that are used in the Places database. Columns that you add to the .csv file will be added to the POI database in a separate metadata section for each POI as key/value pairs, and the header value is used as the key.

Here is a list of the columns and the values that you need to use:

* `lib_id`

  A valid library ID that is obtained from the POI database.

* `type`

  Point is currently the only valid value.

* `longitude`

  A value between -180 and 180.

* `latitude`

  A value between -85 and 85.

* `radius`

  A value between 10 and 20,000.

### Column values

The values of the following columns are used in the Places Service UI:

* color, which is used as the color of the pin that represents the location of the POI in the Places Service UI map.
  * The valid values are "", #3E76D0, #AA99E8, #DC2ABA, #FC685B, #FC962E, #F6C436, #BECE5D, #61B56B, and #3DC8DE, and "".
  * If the value is left blank, the Places Service UI uses blue as the default color.

    The values correspond to blue (#3E76D0), purple (#AA99E8), fuschia (#DC2ABA), orange (#FC685B), light orange (#FC962E), yellow (#F6C436), light green (#BECE5D), green (#61B56B), and light blue (#3DC8DE), respectively.
  
* icon, which is used as the icon on the pin that represents the location of the POI on the Places Service UI map.

  * The valid values are "", shop, hotelbed, car, airplane, train, ship, stadium, amusementpark, anchor, beaker, bell, bid, book, box, briefcase, browse, brush, building, calculator, camera, clock, education, flashlight, follow, game, female, male, gift, hammer, heart, home, key, launch, lightbulb, mailbox, money, pin, promote, ribbon, shoppingCart, star, target, teapot, thumbDown, thumbUp, trap, trophy, wrench.

    The icon values are listed in the order in which they appear in the following illustration:

    ![icons in the UI](/help/assets/UI_icons.png)

  * If the value is left blank, the UI uses star as the default icon.

* Columns that are not mentioned can be left blank.

## Running the Script

1. Download files from the [git repo](https://github.com/adobe/places-scripts) to your local directory.
1. In a text editor, open the `config.py` file and complete the following tasks:

   a. Edit the following variable values as strings:

      * `csv_file_path`

        This is the path to your `.csv`  file.

      * `access_code`

        This is your access code that was obtained from the call to Adobe IMS. For information about how to obtain this access code, see *Prerequisites for user access* in [Integration overview and prerequisites](/help/web-service-api/adobe-i-o-integration.md). 
 
      * `org_id`

        The Experience Cloud orgID into which the POIs are to be imported. For information about how to obtain the org ID, see *Prerequisites for user access* in [Integration overview and prerequisites](/help/web-service-api/adobe-i-o-integration.md).

      * `api_key`

        This is your Places REST API key obtained from your Adobe I/O Places Integration. For information about how to obtain the API key, see *Prerequisites for user access* in [Integration overview and prerequisites](/help/web-service-api/adobe-i-o-integration.md).

    b. Save your changes.

1. In a terminal window, navigate to the `…/places-scripts/import/` directory.
1. Enter `python ./places_import.py` and press the **[!UICONTROL enter]** (**[!UICONTROL return]**) key.


## Pre-import CSV checks

The script initially completes the following checks on the .csv file:

* Whether a `.csv` file was specified.
* Whether the file path is valid.
* Whether the reserved metadata headers are included.

  The reserved metadata headers are lib_id, name, description, type, longitude, latitude, radius, country, state, city, street, category, icon, and color.

  >[!TIP]
  >
  >The headers are all lower case and can be listed in any order.

* Verifies the values of the columns specified in the CSV file section.

If errors are found, the script prints out the errors and is aborted. If no errors are found, the script attempts to import the POIs in batches of 1000. If the batch is successfully imported, the script reports a status code of 200. If the batch is not successfully imported, errors are reported.

## Unit Tests

Unit tests are in the `tests.py` file, should be run before each pull request, and should all pass. Additional tests should be added with new code. To run the tests, navigate to the `…/places-scripts/import/` directory, and enter `python ./places_import.py` in terminal.
