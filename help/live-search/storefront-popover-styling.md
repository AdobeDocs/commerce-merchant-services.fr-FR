---
title: "Style [!DNL Popover] Elements"
description: "Notes techniques sur la personnalisation de la variable [!DNL Live Search storefront popover]"
exl-id: 033049f2-976e-4299-b026-333ac4b481a3
source-git-commit: ba3d983372eb60d5cb42e503c3c26c693668a01e
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 0%

---

# Style [!DNL Popover] Éléments

Le [[!DNL storefront popover]](storefront-popover.md) affiche toujours le produit `name` et `price`et la sélection des champs n’est pas configurable. Cependant, [!DNL popover] Les éléments peuvent être stylisés à l’aide de classes CSS. Par exemple, les déclarations suivantes modifient la couleur d’arrière-plan de la variable [!DNL popover] conteneur et pied de page.

```css
.livesearch.popover-container {
    background-color: lavender;
}

.livesearch.view-all-footer {
    background-color: magenta;
}
```

## Visibilité des conteneurs

Le composant parent du `.livesearch.popover-container` is `.search-autocomplete`.  Le `.active` indique la visibilité du conteneur. Le `.active` est ajoutée de manière conditionnelle lorsque la variable [!DNL popover] est ouvert.

```css
.search-autocomplete.active   /* visible */
.search-autocomplete          /* not visible */
```

Pour plus d’informations sur le style des éléments storefront, reportez-vous à la section [Feuilles de style en cascade (CSS)](https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/css-topics/css-overview.html) dans le [Guide du développeur de Frontend](https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/bk-frontend-dev-guide.html).

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

Le [!DNL storefront popover] peut être utilisé avec une [thème](https://devdocs.magento.com/guides/v2.3/frontend-dev-guide/themes/theme-overview.html) qui hérite des fichiers requis de *Luma*. Le `top.search` dans le `header-wrapper` de `Magento_Search` ne doit pas être modifié.

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

Pour désactiver la fonction [!DNL popover] et restaurer la norme [Recherche rapide](https://docs.magento.com/user-guide/catalog/search-quick.html) , saisissez la commande suivante :

```bash
bin/magento module:disable Magento_LiveSearchStorefrontPopover
```
