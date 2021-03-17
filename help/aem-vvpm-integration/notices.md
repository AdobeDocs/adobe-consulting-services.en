---
title: Veeva Vault Integration Notices
description: Veeva Vault Integration Notices
---

# Best practices, Guardrails, and Notices

## Versions

This integration requires the following software versions:

* Adobe Experience Manager, 6.5.5+
* Veeva Vault PromoMats, 20R3.2+

## Data Privacy

This integration is designed to transfer end user data between Adobe Experience Manager and Veeva Vault PromoMats. 
This data can includes personal information if it is contained in your end user data.  As a data controller, your 
company is responsible for complying with any privacy laws and regulations applicable to your collection and use of personal data.

## Data Sync Frequency

Data is synced.....

## Integration Limitations

Consider the following limitations when using this integration:

* Only the following datatypes are supported when syncing metadata: "Text" and "Multiline Text".
* Veeva modules are not supported.

## Veeva Vault Limitations

Consider the following AEM limitations when using this integration:

* The number of documents are limited based on the Veeva license. See [License Limitations](#veeva-license-limitations).
* The number of API calls are limited based on the Veeva license. For more information see [API Limitations](https://developer.veevavault.com/docs/#what-are-rate-limits). See [License Limitations](#veeva-license-limitations).

### Veeva License Limitations 

You can monitor your instance limits by navigating to the VVPM general settings.

[Veeva Limits](assetseeva-limits.png)

## Adobe Experience Manager Limitations

Consider the following AEM limitations when using this integration:

* No more than 1000 assets or pages should be ingested into a single folder.
