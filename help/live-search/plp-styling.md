---
title: Widget de page de liste de produits
description: Activation et définition du style de l’ [!DNL Live Search Product Listing Page Widget]
exl-id: f7346a06-a8c7-4a33-8437-ea4f61d9281f
source-git-commit: aa036228bb4040de5a8d4d159727fa0c4c6d99e1
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# Widget de page de liste de produits

[!DNL Live Search Product Listing Page Widget] (PLP) utilise la plateforme des services Commerce pour fournir une page de liste de produits performante, pouvant faire l’objet de recherches et pouvant être facettes. Cette rubrique décrit comment activer et mettre en forme le widget PLP.

## Activation du widget PLP

Lorsque le service [!DNL Live Search] est installé, la fonctionnalité de recherche par défaut est automatiquement convertie en [!DNL Live Search].

Le widget [!DNL Live Search] PLP est activé par défaut pour les nouvelles installations. Si vous effectuez une mise à niveau de [!DNL Live Search] et que le widget PLP a déjà été désactivé, il le restera.

>[!IMPORTANT]
>
>Lorsque l’option [!DNL Live Search Product Listing Page Widget] est activée, l’ordre de tri sur une page de liste de produits ne peut pas être modifié.

## Fonctionnalités des widgets

Le widget PLP fournit les fonctionnalités prêtes à l’emploi suivantes :

- Boutons Ajouter au panier - Disponible uniquement pour les produits simples.
- Plusieurs images par produit : l’image peut changer lorsqu’une autre couleur est sélectionnée pour un produit configurable.
- Prise en charge des échantillons de couleurs : notez que l’attribut de couleur doit être orthographié `color` pour que le code soit correctement validé.

### Personnalisation du widget

Outre les fonctionnalités prêtes à l’emploi du widget PLP, vous pouvez personnaliser davantage le widget pour inclure les fonctionnalités suivantes :

- Filtrage par attributs
- Prise en charge de plusieurs langues
- Curseurs de prix

Pour plus d’informations sur la personnalisation du widget PLP pour gérer les fonctionnalités ci-dessus, consultez le fichier Lisez-moi `storefront-product-listing-page` dans le [référentiel](https://github.com/adobe/storefront-product-listing-page/) suivant. Le fichier Lisez-moi de ce référentiel fournit un exemple de personnalisation du widget PLP et de déploiement de ces personnalisations sur votre site.

>[!WARNING]
>
>Si vous personnalisez le widget PLP à l’aide du code disponible dans le référentiel, vous êtes responsable de la maintenance et des mises à jour nécessaires. Toute nouvelle fonctionnalité de widget PLP qui Adobe des versions peut être incompatible avec votre mise en oeuvre personnalisée.

## Exemple de style

Vous pouvez personnaliser l’aspect du widget PLP pour qu’il corresponde à votre site à l’aide de [CSS](https://developer.adobe.com/commerce/frontend-core/guide/css/).

>[!NOTE]
>
>Les éléments avec des classes personnalisées dans un thème Adobe Commerce ne sont pas hérités. Ces éléments doivent être ciblés par leur classe spécifique pour correspondre aux classes personnalisées ; les classes d’action principales ne fonctionneront pas sur un bouton de widget. Les éléments ciblés génériques dans le CSS sont hérités ; `button` s’applique aux boutons de widget.

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

- `.ds-sdk-product-list` : div externe
- `.ds-sdk-product-list__grid` : div interne

![Pagination](assets/plp-css-product-list.png)

#### Pagination de la liste de produits

- `.ds-plp-pagination`

![Pagination](assets/plp-css-pagination.png)

- `.ds-plp-pagination_item`

![Élément de pagination](assets/plp-css-pagination-item.png)

- `.ds-plp-pagination_item--current`

![Élément actif de pagination](assets/plp-css-pagination-item-current.png)

### Widgets

- `.ds-widgets` : div externe
- `.ds-widgets__actions` : div interne gauche
- `.ds-widgets__results` : div interne du côté droit

![Résultats du widget](assets/plp-css-widgets.png)

### Menu déroulant Trier

- `.ds-sdk-sort-dropdown`

![Liste déroulante de tri](assets/plp-css-dropdown.png)

- `.ds-sdk-sort-dropdown__button`

![Bouton déroulant](assets/plp-css-dropdown-button.png)

- `.ds-sdk-sort-dropdown__items`

![Éléments de liste déroulante](assets/plp-css-dropdown-items.png)

- `.ds-sdk-sort-dropdown__items--item`

![Élément de liste déroulante](assets/plp-css-dropdown-item.png)

- `.ds-sdk-sort-dropdown__items--item-selected`

![Menu déroulant de l’élément sélectionné](assets/plp-css-dropdown-selected.png)

- `.ds-sdk-sort-dropdown__items--item-active`

![Liste déroulante de sélection active](assets/plp-css-dropdown-active.png)

### Facettes

- `.ds-plp-facets`
- `.ds-plp-facets__header`
- `.ds-plp-facets__header_title`
- `.ds-plp-facets__header__clear-all`

![Titre de l’en-tête de facettes](assets/plp-css-facets-title-clear.png){width="350"}

- `.ds-plp-facets__pills`
- `.ds-sdk-pill`

![Facet pills](assets/plp-css-facets-pill.png){width="350"}

- `.ds-sdk-pill__label`
- `.ds-sdk-pill__cta`

![Libellé des facettes](assets/plp-css-pill-label-cta.png){width="350"}

- `.ds-plp-facets__list`

![Liste des facettes](assets/plp-css-facets-list.png){width="350"}

- `.ds-sdk-input`
- `.ds-sdk-input__label`
- `.ds-sdk-product-item__product-swatch-group`
- `ds-sdk-product-item__product-swatch-item`
- `.ds-sdk-input_fieldset_show-more`

![Input](assets/plp-css-sdk-input.png)

- `.ds-sdk-labelled-input`

![Entrée étiquetée](assets/plp-css-labelled-input.png)

- `.ds-sdk-labelled-input__input`
- `.ds-sdk-labelled-input__label`

![Libellé d’entrée](assets/plp-css-labelled-input-label.png)

### Élément de produit

- `.ds-sdk-product-item`
- `.ds-sdk-product-item__image`
- `.ds-sdk-product-item__product-name`
- `.ds-sdk-product-item__product-options`
- `.ds-sdk-product-price`
   - `.ds-sdk-product-price--no-discount`
   - `.ds-sdk-product-price--grouped`
   - `.ds-sdk-product-price--bundle`
   - `.ds-sdk-product-price--discount`

![Produit](assets/plp-css-product.png)

### Chargement

- `.ds-sdk-loading`
- `.ds-sdk-loading__spinner`
- `.ds-sdk-loading__spinner-label`

![Indicateur de chargement](assets/plp-css-loading.png)

## Désactivation du widget PLP

Pour désactiver le widget PLP :

1. Accédez à **Magasins** > Paramètres > **Configuration** > **[!DNL Live Search]** > **Fonctionnalités Storefront** et définissez **Activer les widgets de liste de produits** sur &quot;Non&quot;.
1. Sélectionnez **Save Config** pour enregistrer le paramètre.
