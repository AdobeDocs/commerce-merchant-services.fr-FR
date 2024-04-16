---
title: Widget de page de liste de produits
description: Activation et définition de style de la variable [!DNL Live Search Product Listing Page Widget]
exl-id: f7346a06-a8c7-4a33-8437-ea4f61d9281f
source-git-commit: d4511219a0244dca7db896419daba1e6694d80de
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---

# Widget de page de liste de produits

La variable [!DNL Live Search Product Listing Page Widget] (PLP) utilise la plateforme Commerce Services pour fournir une page de liste de produits performante, indexable et facettable. Cette rubrique décrit comment activer et mettre en forme le widget PLP.

## Activation du widget PLP

Lorsque la variable [!DNL Live Search] est installé, la fonctionnalité de recherche par défaut est convertie en [!DNL Live Search] automatiquement.

La variable [!DNL Live Search] Le widget PLP est activé par défaut pour les nouvelles installations. Si vous effectuez une mise à niveau [!DNL Live Search] et le widget PLP a déjà été désactivé, il le restera.

>[!IMPORTANT]
>
>Lorsque la variable [!DNL Live Search Product Listing Page Widget] est activée, la direction de l’ordre de tri sur une page de liste de produits ne peut pas être modifiée.

## Désactivation du widget PLP

Pour désactiver le widget PLP :

1. Accédez à **Magasins** > Paramètres > **Configuration** > **[!DNL Live Search]** > **Fonctionnalités de Storefront** et défini **Activation des widgets de liste de produits** à &quot;Non&quot;.
1. Sélectionner **Enregistrer la configuration** pour enregistrer le paramètre.

## Fonctionnalités des widgets

Le widget PLP fournit toute une gamme de fonctionnalités attendues dans une page de produits pouvant faire l’objet d’une recherche. Il s’agit notamment :

* Filtrage par attributs
* Prise en charge des échantillons de couleurs
* Fonction Ajouter au panier
* Prise en charge de plusieurs langues
* Curseurs de prix

## Exemple de style

Vous pouvez personnaliser l’aspect du widget PLP pour qu’il corresponde à votre site à l’aide de [CSS](https://developer.adobe.com/commerce/frontend-core/guide/css/).

>[!NOTE]
>
>Les éléments avec des classes personnalisées dans un thème Adobe Commerce ne sont pas hérités. Ces éléments doivent être ciblés par leur classe spécifique pour correspondre aux classes personnalisées ; les classes d’action principales ne fonctionneront pas sur un bouton de widget.
>Les éléments ciblés génériques dans le CSS sont hérités ; `button` s’applique aux boutons de widget.

Les divisions en surbrillance contiennent la classe cible `ds-sdk-product-item__product-name`.

![Pagination](assets/plp-css-example.png)

Personnalisez le nom du produit en ajoutant une règle pour le mettre en majuscules.

```css
.ds-sdk-product-item__product-name {
 text-transform: uppercase;
}
```

![Pagination](assets/plp-css-example-after.png)

## Classes CSS

### Liste de produits

* `.ds-sdk-product-list`: div externe
* `.ds-sdk-product-list__grid`: div interne

![Pagination](assets/plp-css-product-list.png)

#### Pagination de la liste de produits

* `.ds-plp-pagination`

![Pagination](assets/plp-css-pagination.png)

* `.ds-plp-pagination_item`

![Élément de pagination](assets/plp-css-pagination-item.png)

* `.ds-plp-pagination_item--current`

![Pagination de l’élément actif](assets/plp-css-pagination-item-current.png)

### Widgets

* `.ds-widgets`: div externe
* `.ds-widgets__actions`: div interne du côté gauche
* `.ds-widgets__results`: div interne du côté droit

![Résultats du widget](assets/plp-css-widgets.png)

### Menu déroulant Trier

* `.ds-sdk-sort-dropdown`

![Menu déroulant Trier](assets/plp-css-dropdown.png)

* `.ds-sdk-sort-dropdown__button`

![Bouton Liste déroulante](assets/plp-css-dropdown-button.png)

* `.ds-sdk-sort-dropdown__items`

![Éléments déroulants](assets/plp-css-dropdown-items.png)

* `.ds-sdk-sort-dropdown__items--item`

![Élément de liste déroulante](assets/plp-css-dropdown-item.png)

* `.ds-sdk-sort-dropdown__items--item-selected`

![Menu déroulant de l’élément sélectionné](assets/plp-css-dropdown-selected.png)

* `.ds-sdk-sort-dropdown__items--item-active`

![Liste déroulante de sélection active](assets/plp-css-dropdown-active.png)

### Facettes

* `.ds-plp-facets`
* `.ds-plp-facets__header`
* `.ds-plp-facets__header_title`
* `.ds-plp-facets__header__clear-all`

![Titre de l’en-tête Facettes](assets/plp-css-facets-title-clear.png){width="350"}

* `.ds-plp-facets__pills`
* `.ds-sdk-pill`

![Facettes](assets/plp-css-facets-pill.png){width="350"}

* `.ds-sdk-pill__label`
* `.ds-sdk-pill__cta`

![Libellé des facettes](assets/plp-css-pill-label-cta.png){width="350"}

* `.ds-plp-facets__list`

![Liste des facettes](assets/plp-css-facets-list.png){width="350"}

* `.ds-sdk-input`
* `.ds-sdk-input__label`
* `.ds-sdk-product-item__product-swatch-group`
* `ds-sdk-product-item__product-swatch-item`
* `.ds-sdk-input_fieldset_show-more`

![Entrée](assets/plp-css-sdk-input.png)

* `.ds-sdk-labelled-input`

![Entrée étiquetée](assets/plp-css-labelled-input.png)

* `.ds-sdk-labelled-input__input`
* `.ds-sdk-labelled-input__label`

![Libellé d&#39;entrée](assets/plp-css-labelled-input-label.png)

### Élément de produit

* `.ds-sdk-product-item`
* `.ds-sdk-product-item__image`
* `.ds-sdk-product-item__product-name`
* `.ds-sdk-product-item__product-options`
* `.ds-sdk-product-price`
   * `.ds-sdk-product-price--no-discount`
   * `.ds-sdk-product-price--grouped`
   * `.ds-sdk-product-price--bundle`
   * `.ds-sdk-product-price--discount`

![Produit](assets/plp-css-product.png)

### Chargement

* `.ds-sdk-loading`
* `.ds-sdk-loading__spinner`
* `.ds-sdk-loading__spinner-label`

![Indicateur de chargement](assets/plp-css-loading.png)
