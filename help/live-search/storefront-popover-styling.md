---
title: Styling Popover Elements
description: Technical notes about customizing the Live Search storefront popover.
exl-id: 033049f2-976e-4299-b026-333ac4b481a3
source-git-commit: 65126f10574801f7ea8d0a863e9bb512dca13f39
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---

# [!DNL Popover]

[[!DNL storefront popover]](storefront-popover.md)`name``price` [!DNL popover] [!DNL popover]

```css
.livesearch.popover-container {
    background-color: lavender;
}

.livesearch.view-all-footer {
    background-color: magenta;
}
```

## Container visibility

`.livesearch.popover-container``.search-autocomplete`  `.active` `.active`[!DNL popover]

```css
.search-autocomplete.active   /* visible */
.search-autocomplete          /* not visible */
```

[](https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/css-topics/css-overview.html)[](https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/bk-frontend-dev-guide.html)

## Class selectors

[!DNL popover]

* `.livesearch.popover-container`
* `.livesearch.view-all-footer`
* `.livesearch.suggestions-container`
* `.livesearch.suggestions-header`
* `.livesearch.suggestion`
* `.livesearch.products-container`
* `.livesearch.product-result`
* `.livesearch.product-name`
* `.livesearch.product-price`

### Container Class Selectors

`.livesearch.popover-container`

![[!DNL Popover]](assets/livesearch-popover-container.png)

`.livesearch.view-all-footer`

![](assets/livesearch-view-all-footer.png)

### Suggestion Class Selectors

`.livesearch.suggestions-container`![](assets/livesearch-suggestions-container.png)

`.livesearch.suggestions-header`![](assets/livesearch-suggestions-header.png)

`.livesearch.suggestion`![](assets/livesearch-suggestion.png)

### Product Class Selectors

`.livesearch.products-container`![](assets/livesearch-product-container.png)

`.livesearch.product-result`![](assets/livesearch-product-result.png)

`.livesearch.product-name`![](assets/livesearch-product-name.png)

`.livesearch.product-price`![](assets/livesearch-product-price.png)

## Working with a modified theme {#working-with-modified-theme}

[!DNL storefront popover][](https://devdocs.magento.com/guides/v2.3/frontend-dev-guide/themes/theme-overview.html)** `top.search``header-wrapper``Magento_Search`

```html
<referenceContainer name="header-wrapper">
   <block class="Magento\Framework\View\Element\Template" name="top.search" as="topSearch" template="Magento_Search::form.mini.phtml">
      <arguments>
         <argument name="configProvider" xsi:type="object">Magento\Search\ViewModel\ConfigProvider</argument>
      </arguments>
   </block>
</referenceContainer>
```

## [!DNL popover]

[!DNL popover][](https://docs.magento.com/user-guide/catalog/search-quick.html)

```bash
bin/magento module:disable Magento_LiveSearchStorefrontPopover
```
