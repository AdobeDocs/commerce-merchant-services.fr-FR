---
title: Storefront Popover
description: The Live Search storefront popover dynamically returns suggested products and thumbnails.
exl-id: 88fdc3ed-b606-40de-94b7-435be09c4072
source-git-commit: 65126f10574801f7ea8d0a863e9bb512dca13f39
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# [!DNL Storefront Popover]

[!DNL Live Search][](install.md)[!DNL popover][](https://docs.magento.com/user-guide/catalog/search-quick.html) [!DNL popover]

[!DNL Live Search] For a partial match, the maximum number of characters per word is 20. The number of characters in a &quot;search as you type&quot; query is not configurable.

>[!NOTE]
>
>[!DNL Live Search][!DNL storefront popover]**** **[!DNL Commerce] [!DNL popover]** [ [!DNL Popover] ](storefront-popover-styling.md)

## Searchable attributes

[](https://docs.magento.com/user-guide/stores/attributes-product.html#storefront-properties)`searchable=true` To ensure relevancy, make attributes searchable only if they contain content that has a clear and concise meaning. `description` For example, if a person searches for &quot;shorts&quot; and there are shirts with a description that includes the term &quot;short sleeves&quot;, then the shirts will be included in the search results.

The following attributes are always searchable:

* `sku`
* `name`
* `categories`

[[!DNL Live Search popover]](assets/storefront-search-as-you-type.png)

## [!DNL Popover]

[!DNL popover] Previously, the page size was hardcoded as six lines. `page_size`** `page_size`[](https://docs.magento.com/user-guide/configuration/catalog/catalog.html#catalog-search)`Autocomplete Limit`

By default, the Catalog Search - Autocomplete Limit value is set to eight lines (or rows). [!DNL popover]

1. **********
1. ********
1. **
1. ****[!DNL popover]
1. ****
