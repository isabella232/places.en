---
title: Adobe I/O integration overview
seo-title: Adobe I/O integration overview
description: Information about creating an Adobe I/O integration.
seo-description: Information about creating a Adobe I/O integration.
---

# Integration overview and prerequisites {#integration-prereqs}

This information shows you how to create an Adobe I/O and a Places integration.

## Prerequisites for user access

Verify with your organization's System administrator that the following tasks have been completed:

* Places Core Service appears in your organization's admin console. 
* You have been added to the organization. 
* You have been added as a User to Places Core Service in your organization. 

  For more information, see *Add a user or a developer to your Location Service and Experience Platform Launch profiles* in [Frequently asked questions](/help/places-faqs.md).

* You have been added as a Developer to Places Core Service in your organization.  

  For more information on adding developers see *Add a user or a developer to your Location Service and Experience Platform Launch profiles* in [Frequently asked questions](/help/places-faqs.md).

  For more information about the developer role, see [Manage developers](https://helpx.adobe.com/enterprise/using/manage-developers.html).

### REST API requests 

Each request to the Places REST API requires the following items:

* An organization ID
* An API key
* A bearer token

An integration with Adobe I/O provides these items and a way to request the bearer token by using a JSON Web Token (JWT). 

* For more information about JWTs, see [Introduction to JSON Web Tokens](https://jwt.io/introduction/).
* To create an integration for Places, see the *Creating a Places integration* section below.
* To understand API key integration, generating a JWT, and public key certificates, see [Adobe I/O Authentication Overview](https://www.adobe.io/apis/cloudplatform/console/authentication/gettingstarted.html).

>[!IMPORTANT]
>
>If you cannot log in to the Adobe I/O console, or if Experience Platform Location Service is not an option on the *Create Integrations page*, see *Organization requirements* in [Web services API overview](/help/web-service-api/places-web-services.md).

## Create a Places integration

To create an Places integration, complete the following tasks:

### Generate a public and private key pair

To create a Places integration, you need a public and a private key pair. These pairs can be purchased, or you can generate your own self-signed keys.

To generate your own self-signed keys:

1. In a terminal window, copy and paste each of the following lines and press **[!UICONTROL Enter]** after pasting each line:

   ```text
      mkdir keys
      cd keys
      openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout places_integration_test_private.key -out    places_integration_test_public.crt
   ```

   >[!IMPORTANT]
   >
   >We recommend that you name your keys for easy reference and store them in a folder. If you create multiple integrations, you can easily identify and manage which keys belong to which integration.

1. Type the information that is requested by OpenSSL:

   ```text
   Country Name (2 letter code:  // Example: US
   State or Province Name (full name):  // Example: California
   Locality Name (eg, city):  // Example: San Jose
   Organization Name (eg, company):  // Example: Places
   Organizational Unit Name (eg, section):  // Example: Engineering
   Common Name (eg, fully qualified host name):  // Example: places.com
   Email Address:  // Example:  poi@places.com
   ```

   For more information about OpenSSL, see [OpenSSL](https://www.openssl.org/).

    >[!IMPORTANT]
    >
    >The information that you provide is incorporated into the keys.

1. Navigate to the directory where the `.key` and `.crt` files are located. 

    For example, in iOS, go to **[!UICONTROL Macintosh HD]** > **[!UICONTROL users]** > **[!UICONTROL (your user name)]** > **[!UICONTROL Keys]**.

The following video guides you through the process of generating the key pair:

![integration video](/help/assets/places_integration_video.gif)

### Create a Places integration in the Adobe I/O console

To create a Places integration:

1. Go to [https://console.adobe.io](https://console.adobe.io) and sign in with your Adobe ID.
1. in the **Quick Start** section, click on **Create integration**.
1. Select **[!UICONTROL Access an API]** and click **[!UICONTROL Continue]**.

    **[!UICONTROL Access an API]** is the default location.

1. If you have access to more than one Experience Cloud organization, select the organization from the drop-down list on the top right.
1. Under **[!UICONTROL Experience Cloud]**, select **[!UICONTROL Places]** as the Adobe service to which you want to integrate and click **[!UICONTROL Continue]**.
1. Select **[!UICONTROL New integration]** and click **[!UICONTROL Continue]**.
1. On the Create a new integration screen, enter a name and description. 
1. Drag and drop your `xxxx_public.crt` file, that you created above, to the **[!UICONTROL Public keys certificates]** drop zone.
1. Select a product profile.

    If you are unsure of which profile to select, contact your system administrator.
10. At the bottom of the page, click **[!UICONTROL Create integration]**.
11. After a few seconds, in the *Integration created* screen, verify that the following message appears:

    `Your integration has been created.`

12. The integration details page appears with the name of the integration at the top.

    The **[!UICONTROL Overview]** tab appears by default and displays the API key, your organization ID, the technical account ID, and other details about your integrations.

### Record the organization ID and the API key

1. On the integration details page, click the **[!UICONTROL Services]** tab and confirm that **[!UICONTROL Places]** is displayed under **[!UICONTROL Configured Services]**.
1. On the **[!UICONTROL Overview]** tab, locate and record the API Key (Client ID) and the Organization ID.

   These IDs are needed for each Places REST API request.

![](/help/assets/places_orgid_api-key.png)

### Generate a JWT token

On the integration details page, click the **[!UICONTROL JWT]** tab so that you can test your integration by generating a JWT and providing the exchange URL.

To generate a JWT token:

1. In a text editor, open your `private.key` file created that you created above.
1. On the **[!UICONTROL JWT]** tab, copy the contents of the key and paste it in the **[!UICONTROL Paste private key]** field. 
1. Click **[!UICONTROL Generate JWT]**.
1. In the **[!UICONTROL Sample CURL command]** section, click **[!UICONTROL Copy]** and paste the contents in your command prompt or terminal window.
1. Run the command by pressing **[!UICONTROL Enter]** on your keyboard.
1. Locate the `"token_type": "bearer"` and the `"access_token"` value.  

    The value of the bearer access token is what you will use in your Places API requests.  

>[!IMPORTANT]
>
>Adobe access tokens are valid **only** for 24 hours, so save the sample CURL command (step 5). If the access token is no longer valid, you need to regenerate the token.