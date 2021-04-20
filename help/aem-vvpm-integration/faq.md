---
title: Veeva Vault Integration FAQ
description: Veeva Vault Integration FAQ
exl-id: c308ebb3-7881-4094-9f35-c67a96fb5ab1
---
# Frequently Asked Questions 

**What metadata should be synced to Veeva?**

It is important to understand the metadata based on the content type (e.g. promotions) in the Veeva Portal. After reviewing the Veeva Portal, construct the content metadata schema in AEM to hold all the relevant metadata for each asset/page and configure the integration to map the metadata between the two systems. 

**Does the integration support the Veeva linked documents? If not, what relationship types are supported?**
    
No. See [Veeva documention](https://vaulthelp2.vod309.com/wordpress/admin-user-help/documents-admin-user-help/about-document-relationships/). The Linked document (reference relationship type) is one of the standard relationship types that can't be created or deleted via API due to them having a special Vault behaviour. Component, supporting documents and any other not in this list should be able to configure via AEM Veeva Cloud configuration.

**Does the integration support the AEM modular content?** 

Yes, the integration supports AEM Content Fragments and Experience Fragments.

**Does the integration support the Veeva modular content?** 

No, not at this time.

**Does the integration sync Veeva visual annotations to AEM?** 

No, not at this time. Visual annotations are only accessible via API as a PDF.

**How do we set permissions on VVPM documents synced by the integration?** 

The integration uses a service user to upload documents through the API.  Document defaulting and overriding rules (defaulting roles on documents) are supported only in the VVPM user interface, and not applied when using the API. The recommendation is to use DAC (Dynamic Access Control) for role assignments. DAC is enforced through all the touch points, including the API. [See documentation here.](http://vaulthelp2.vod309.com/wordpress/admin-user-help/ah-user-permissions-access-control/about-dynamic-access-control-for-documents/) 

**Does the integration support multiple VVPM instances?**

The integration uses a cloud configuration approach that allows mutliple Veeva endpoints to be configured from one AEM instance. 

**Does the integration support AEM publish?**

 No, this integration works only with AEM author. It is meant to facilitate MLR review cycles before the content is published. 
