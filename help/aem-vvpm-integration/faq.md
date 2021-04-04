---
title: Veeva Vault Integration FAQ
description: Veeva Vault Integration FAQ
exl-id: c308ebb3-7881-4094-9f35-c67a96fb5ab1
---
# Frequently Asked Questions 

**What metadata should be synced to Veeva?**

It is important to understand the metadata based on the content type (e.g. promotions) in the Veeva Portal. 
After reviewing the Veeva Portal, construct the content metadata schema in AEM to hold all the relavant metadata 
for each asset/page and configure the integration to map the metadata between the two systems. 

**Does the integration support the Veeva linked documents? If not, what relationship types are supported?**
    
No. See [Veeva documention](https://vaulthelp2.vod309.com/wordpress/admin-user-help/documents-admin-user-help/about-document-relationships/).
The Linked document (reference relationship type) is one of the standard relationship types that can't be created 
or deleted via API due to them having a special Vault behaviour. Component, supporting documents and any other 
not in this list should be able to configure via AEM Veeva Cloud configuration.

**Does the integration support the Veeva modular content?** 

No, not at this time.
