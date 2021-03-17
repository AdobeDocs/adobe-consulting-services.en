---
title: Veeva Vault Integration Setup
description: Veeva Vault Integration Setup
---

# Integration Setup

This guide will walk you through getting the connector up and running.

>[!IMPORTANT]
>
>For each system, these steps need to be performed by an **administrator**.
>
>Steps in this documentation will guide you through creating integrations/registrations that involve assigning permissions and/or admin access.  It is your responsibility to ensure these steps comply with your company policies before performing, and to perform them carefully.
>

## Install Integration Package

You will receive access the integration AEM package. There are two  options to install the connector: 

1. **Package Installation** - Straight forward and less involved. (Recommended)
2. **POM Installation** - More advanced, but can be useful when using CICD and upgrading the connector.

### Package Installation

To install the package, download it with the link provided. [Detailed instructions for installing an AEM package can be found by clicking here.](
https://experienceleague.adobe.com/docs/experience-manager-64/administering/contentmanagement/package-manager.html?lang=en#installing-packages) 

### POM Installation

To include the connector in your pom, follow these steps:

1. Add the followings to the `~/.m2/settings.xml` replacing `YOUR_USERNAME` with the username provided and `YOUR_PASSWORD` with the the password provided:

    ```
    <settings>
    ...
        <servers>
        ...
            <server>
                <id>repo.ea.adobe.net</id>
                <username>YOUR_USERNAME</username>
                <password>YOUR_PASSWORD</password>
                <filePermissions>BucketOwnerFullControl</filePermissions>
                <configuration>
                  <wagonProvider>s3</wagonProvider>
                </configuration>
            </server>
        ...
        </servers>
    ...
    </settings>
    ```

2. Add the following to the projects `pom.xml` file:

    ```
    <build>
    ...
        <extensions>
            ...
            <extension>
                <groupId>com.allogy.maven.wagon</groupId>
                <artifactId>maven-s3-wagon</artifactId>
                <version>1.2.0</version>
            </extension>
            ...
        </extensions>
    ...
    </build>
    ...
    <distributionManagement>
        <repository>
            <id>repo.ea.adobe.net</id>
            <url>s3://repo.ea.adobe.net/release</url>
            <releases>
                <enabled>true</enabled>
            </releases>
        </repository>
    </distributionManagement>
    ...
    ```

## Populate Cloud Configuration

Navigate to the cloud configuration and populate the configuration tabs.

[Navigate to Cloud Configuration](assets/cloud-config-navigation.png)

[Navigate to Veeva Configuration](assets/veeva-config-navigation.png)

### Configuration Tab

Fill out the following in the configuration tab:

[Configuration Tab](assets/configuration-tab.png)

1. Required. Title for Veeva Vault connector configuration. This can be an arbitrary value. (e.g. `Veeva Vault Configuration`)
2. Required. The domain url of the Veeva instance (e.g. `https://vvtechpartner-adobe-promomats.veevavault.com/`)
3. Required. ClientID required to call Veeva Vault API. This can be an arbitrary value and is mostly used for debugging. (e.g. `adobe-aem-vvtechpartner`)
4. Required. Veeva Vault username. See [Veeva User Creation](#veeva-user-creation).
5. Required. Veeva Vault password. See [Veeva User Creation](#veeva-user-creation).

### Adobe IO Tab

If the project needs to generate PDFs or images for pages, this tab is required. Fill out the following in the adobe io tab:

[Adobe IO Tab](assets/adobe-io-tab.png)

1. Required. The Adobe IO endpoint for creating PDF Images. (e.g. `https://ID_GOES_HERE.adobeioruntime.net/api/v1/web/aem-veeva-serverless-0.0.2/trigger-action.json`)
2. Required. The action name for page image generation. This value must be `aem-veeva-serverless-0.0.2/get-image-async`.
3. Required. The action name for html image generation. This value must be `aem-veeva-serverless-0.0.2/get-pdf-async`.
4. Required. The Adobe IO endpoint to get the state of the generation.(e.g. `https://ID_GOES_HERE.adobeioruntime.net/api/v1/web/aem-veeva-serverless-0.0.2/get-state-value`)
5. Required. AEM username to be used by Adobe IO. See [AEM User Creation](#aem-user-creation).
6. Required. AEM password to be used by Adobe IO. See [AEM User Creation](#aem-user-creation).
7. Optional. Default timeout is to let the page respond until a specified time after which AIO service stops trying to get a response. Default value is `30000`.
8. Optional. Delay is after page has responded with 200 to delay for all the images to render before taking a screenshot. Default value is `2000`.
9. Optional. Screenshot/PDF generated URL will be expired after configured value in seconds.
10. Optional. Adobe IO screenshot/PDF generation service is async. AEM service calls AIO status endpoint to get screenshot/PDF. This property will decide in milliseconds the pause between in each status call. Default value is `10000`.
11. Optional. Maximum retry count for status call to Adobe IO for getting screenshot/PDF. Default value is `10`.

### Advanced Tab

Fill out the following in the advanced tab:

[Advanced Tab](assets/advanced-tab.png)

1. Required for PDF/image generation. The filename pattern used when creating PDFs/images. `{name}` can be templated. (e.g. `{name}-screenshot`)
2. Required for PDF/image generation. The device types for which page screenshots are required. Valid types include `Desktop`, `Tab (iPad)`, and `Mobile (iPhone X)`.
3. Required for PDF/image generation. Screenshot type to create. Either `PDF` or `Image`.
4. Required for PDF/image generation. The PDF type to generate. Either `Print CSS Based PDF` or `Pixel Perfect Screenshot PDF`.
5. Required for PDF/image generation. The Image type to generate. Either `PNG` or `JPEG`.
6. Required. Workflow to run once Veeva Vault Approval trigger has come through.
7. Required. Workflow to run once Veeva Vault Reject trigger has come through.
8. Optional. Property name for Document Id in Veeva Vault. Default value is `id`.
9. Optional. Property name for Status in Veeva Vault. Default value is `status__v`.
10. Optional. Property name for Document Modified Date. Default value is `version_modified_date__v`.
11. Optional. Property name for document resource url. Default value will be `external_id__v`. If this field is already used, then create different field in Veeva and populate field name here.

### Page Tab

If syncing pages, fill out the following in the page tab:

[Page Tab](assets/page-tab.png)

1. Required. Map a property from AEM to Veeva.
    a. AEM property name. Selectable from AEM properties. 
    b. Veeva property name. Select a page tab. 
    c. Property type. Either `Text` or `Multiline Text`.

2. Required. Map a property from Veeva to AEM. **NOTE! The mapping of `status__v` to `veeva-status` must exist.**
    a. Veeva property name. Select a page tab.
    b. AEM property name. Selectable from AEM properties. 
    c. Property type. Either `Text` or `Multiline Text`.
    

### Asset Tab

If syncing assets, fill out the following in the asset tab:

[Asset Tab](assets/asset-tab.png)

1. Required. Map a property from AEM to Veeva.
    a. AEM property name. Selectable from AEM properties. 
    b. Veeva property name. Select a page tab. 
    c. Property type. Either `Text` or `Multiline Text`.

2. Required. Map a property from Veeva to AEM. **NOTE! The mapping of `status__v` to `veeva-status` must exist.**
    a. Veeva property name. Select a page tab.
    b. AEM property name. Selectable from AEM properties. 
    c. Property type. Either `Text` or `Multiline Text`.

## Additional Setup

### AEM User Creation

During PDF/Image generation, an AEM user needs to be created in order to get pages from AEM. Create and give permissions to a user by following these links:

* [Creating a user in AEM](https://experienceleague.adobe.com/docs/experience-manager-65/forms/administrator-help/setup-organize-users/adding-configuring-users.html?lang=en#create-a-user)
* [Adding permissions to a user in AEM](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security.html?lang=en#permissions-in-aem)


### Veeva User Creation

TODO: ADMIN -> Users and Groups -> Vault Users -> ensure Vault Owners
    
