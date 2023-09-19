---
title: "Style [!DNL Popover] Elements"
description: "Notes techniques sur la personnalisation de la variable [!DNL Live Search storefront popover]"
exl-id: 033049f2-976e-4299-b026-333ac4b481a3
source-git-commit: 75ff893bf5867ededa49807835676ddf9b19adc9
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%

---

# Style [!DNL Popover] Éléments

La variable [[!DNL storefront popover]](storefront-popover.md) affiche toujours le produit `name` et `price`et la sélection des champs n’est pas configurable. Cependant, [!DNL popover] Les éléments peuvent être stylisés à l’aide de classes CSS. Par exemple, les déclarations suivantes modifient la couleur d’arrière-plan de la variable [!DNL popover] conteneur et pied de page.

```css
.livesearch.popover-container {
    background-color: lavender;
}

.livesearch.view-all-footer {
    background-color: magenta;
}
```

## Visibilité des conteneurs

Le composant parent du `.livesearch.popover-container` is `.search-autocomplete`.  La variable `.active` indique la visibilité du conteneur. La variable `.active` est ajoutée de manière conditionnelle lorsque la variable [!DNL popover] est ouvert.

```css
.search-autocomplete.active   /* visible */
.search-autocomplete          /* not visible */
```

Pour plus d’informations sur le style des éléments storefront, reportez-vous à la section [Feuilles de style en cascade (CSS)](https://developer.adobe.com/commerce/frontend-core/guide/css/) dans le [Guide du développeur de Frontend](https://developer.adobe.com/commerce/frontend-core/guide/).

## Sélecteurs de classe

Les sélecteurs de classe suivants peuvent être utilisés pour mettre en forme le conteneur et les éléments de produit dans la variable [!DNL popover].

* `.livesearch.popover-container`
* `.livesearch.view-all-footer`
* `.livesearch.products-container`
* `.livesearch.product-result`
* `.livesearch.product-name`
* `.livesearch.product-price`

### Sélecteurs de classe de conteneur

#### .livesearch.popover-container

![[!DNL Popover] container](assets/livesearch-popover-container.png)

#### .livesearch.view-all-footer

![Afficher tout le pied de page](assets/livesearch-view-all-footer.png)

### Sélecteurs de classe de produits

#### .livesearch.products-container

![Conteneur de produits](assets/livesearch-product-container.png)

#### .livesearch.product-result

![Résultat du produit](assets/livesearch-product-result.png)

#### .livesearch.product-name

![Nom du produit](assets/livesearch-product-name.png)

#### .livesearch.product-price

![Prix du produit](assets/livesearch-product-price.png)

## Utilisation d’un thème modifié {#working-with-modified-theme}

La variable [!DNL storefront popover] peut être utilisé avec une [thème](https://developer.adobe.com/commerce/frontend-core/guide/themes/) qui hérite des fichiers requis de *Luma*. La variable `top.search` dans le `header-wrapper` de `Magento_Search` ne doit pas être modifié.

```html
<referenceContainer name="header-wrapper">
   <block class="Magento\Framework\View\Element\Template" name="top.search" as="topSearch" template="Magento_Search::form.mini.phtml">
      <arguments>
         <argument name="configProvider" xsi:type="object">Magento\Search\ViewModel\ConfigProvider</argument>
      </arguments>
   </block>
</referenceContainer>
```

## Désactivation de la variable [!DNL popover]

Pour désactiver la fonction [!DNL popover] et restaurer la norme [Recherche rapide](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#quick-search) , saisissez la commande suivante :

```bash
bin/magento module:disable Magento_LiveSearchStorefrontPopover
```
