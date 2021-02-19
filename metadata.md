---
product: adobe experience manager
solution: Experience Manager
type: Documentation
git-repo: https://github.com/AdobeDocs/adobe-consulting-services.en
index: y
---

# Metadata for internal use

Metadata in the GitHub authoring system is hierarchical and is defined the the following increasing levels of precedent.

1. metadata.md
1. ToC
1. Article

Metadata defined in the metadata.md file apply to the entire repo, but can be overridden at the ToC and article levels. Any overriding of the metadata should be done at the lowest level possible.

metadata.md

* `product`
* `git-repo`
* `index: y`

ToCs

* `sub-product`
* `user-guide-title`

Article

* `title`
* `description`

Additional information about the metadata can be found in the [internal authoring guide](https://experienceleague.adobe.com/docs/authoring-guide-exl/using/authoring/metadata.html).
