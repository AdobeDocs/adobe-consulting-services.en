---
title: Veeva Vault Integration Overview
description: Veeva Vault Integration Overview
exl-id: 52cc7290-b7e1-4476-877f-48934e6daf68
---
# Get Started with Veeva Vault PromoMats and Adobe Experience Manager integration

This integration will manage your content, enforcing rights and compliance while also leveraging first in class experience delivery.  

This integration requires the following minimum software versions:

* Adobe Experience Manager, 6.5.5+
* Veeva Vault PromoMats, 20R3.2+

>[!IMPORTANT]
>
>Service users and appropriate permissions are required in both systems for the integration.
>

>[!IMPORTANT]
>
>This capability is not available out of the box as part of the product. The implementation requires Adobe Consulting maintenance contract. Please reach out to your Adobe representative to find out more.
>

## Principles and Features

This integration is designed to support two main use cases:

1. Content Approval - When new content has been created or existing content has been edited in AEM, the content must be approved for use in VVPM supporting the Medical, Legal, Regulatory (MLR) Approval process for Life Sciences.

2. Content Management - Provide visibility of asset utilization by establishing relationships in PromoMats between digital tactics (e.g. email, presentations, websites) and their elements (e.g. logos, photography, graphics) created in AEM for documents originating in AEM.

The benefits include:

* Maintaining a single source of truth for assets and content without duplication across digital repositories.
* Leveraging both Veeva Vault for rights and compliance management and AEM for best in class and asset and content creation/delivery.
* Helps automate moving content and metadata between AEM and Veeva Vault.
* Reduces manual effort in sending content to Veeva for Approval workflows.
* Each system is used for its strengths and the connector assists in moving content automatically between the systems to help speed up time to market.

What does the integration do?

* Supports sending AEM Site Pages, Assets, Content Fragments, and Experience Fragments to VVPM. AEM Pages, Content Fragments, and Experience Fragments can be sent as screenshot PDFs or images. AEM Assets binaries are sent as is.
* Supports manual and automated syncing of select metadata elements that are configurable from AEM to VVPM.
* Supports manual and automated syncing of select metadata elements that are configurable from VVPM to AEM. 
* Supports relationships between AEM Site Pages, Assets, Content Fragments, and Experience Fragments in VVPM to automate content relationships.
* Supports rendition generation for multiple device types.

>[!NOTE]
>
>Please see integration usage documentation for further details on configuration options.  
>

What does the connector NOT do?

* Does not replicate AEM processes and functionality in Veeva or vice-versa.
* Does not do MLR by itself. It assists in automation of sending content to Veeva to where MLR happens. 
* Not meant to be used to create an identical setup between AEM and Veeva. Not all content needs to move between the two platforms.


>[!IMPORTANT]
>
>This integration currently considers AEM as the source of truth for content synchronization.  
>

## Getting the Integration

In order to provision this integration, you will need to follow the steps below.

Please follow the flowchart and flowchart details below to request and configure the integration.

![Request Access](assets/integration-request.png)

Flowchart Details (maps to steps above):

* **Step 1** - It is assumed that you already have, or are in the process of procuring, a license for Veeva Vault PromoMats and for Adobe Experience Manager.
* **Step 2** - A new sales order (SO) that outlines a maintenance agreement with Adobe Consulting will need to be signed in order to take advantage of the integration.
* **Step 3** - Install, activate, and configure the integration package.

## Support

The follow describes how to contact and log an issue with the support team.

### Requesting Integration or Adobe Experience Manager Support

Support tickets can be logged with Adobe Customer Care. Your Adobe Experience Cloud administrator will need to log on to [Adobe Admin Console](https://adminconsole.adobe.com/), click on the support tab, and create a case. For any issues with integration, make sure to include the following information:

* **Process Title**: `AEM - Veeva Vault Integration`
* **Process Owner**: `Data Engineering`
* **Description**: `Description of the issue`
* **Point of Contact**: `The email address(es) for relavant AEM point of contacts for your organization.` 
* **AEM Instance URL**: `Place the Adobe Experience Manager instance url here.`
* **Veeva Instance URL**: `Place the Veeva Vault PromoMats instance url here.`
* **Customer ID**: `Provide the Customer ID included in the on-boarding email sent to your team. You can just put your company name here if the ID is not available`

### Requesting Veeva Vault PromoMats Support

Sometimes, the issue being experienced is a problem with the operation of the Veeva Vault PromoMats instance. If that is the case, your Veeva Vault PromoMats administrator might be directed to create a support ticket with [Veeva Support](http://support.veeva.com/). The status of the Veeva instance can be viewed by navigating to [Veeva Trust](http://trust.veeva.com/).
