---
title: "[!DNL Storefront Popover]"
description: "Le  [!DNL Live Search storefront popover] renvoie dynamiquement les produits suggérés et les miniatures."
exl-id: 88fdc3ed-b606-40de-94b7-435be09c4072
source-git-commit: e375404a50dd4972ab584f69d7953aba2c8f4566
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# [!DNL Storefront Popover]

Lorsque [!DNL Live Search] est [installé](install.md), un [!DNL popover] apparaît sur le storefront lorsque les clients saisissent dans la zone [Recherche](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#quick-search). Avec chaque caractère saisi, le [!DNL popover] est mis à jour avec les produits suggérés et les images miniatures des principaux résultats de recherche.

[!DNL Live Search] renvoie des résultats pour une requête de deux caractères ou plus. Pour une correspondance partielle, le nombre maximal de caractères par mot est de 20. Le nombre de caractères d’une requête &quot;Rechercher lorsque vous tapez&quot; n’est pas configurable.

Par défaut, [!DNL Live Search] prend en charge les [redirections de termes de recherche](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-terms.html).

![[!DNL Live Search popover]](assets/storefront-search-as-you-type.png)

>[!TIP]
>
>Découvrez comment définir les attributs de produit comme pouvant faire l’objet d’une recherche dans l’article [Configuration de la recherche en direct](workspace.md) .

## [!DNL Popover] taille de page

La taille de page de [!DNL popover] détermine le nombre de lignes de produits auto-complétés pouvant être renvoyées. Au cours de l’installation de la recherche en direct, la valeur `page_size` est remplacée par la valeur actuelle du paramètre [Recherche catalogue](https://experienceleague.adobe.com/docs/commerce-admin/config/catalog/catalog.html) - `Autocomplete Limit` .

Par défaut, la valeur Recherche catalogue - Limite de saisie automatique est définie sur huit lignes (ou lignes). Pour modifier la taille de page de [!DNL popover], procédez comme suit :

1. Sur la barre latérale *Admin*, accédez à **Magasins** > Paramètres > **Configuration**.
1. Dans le panneau de gauche, développez **Catalog** et sélectionnez **Catalog** dans la liste des paramètres.
1. Développez la section *Recherche catalogue* .
1. Définissez la **Limite d’achèvement automatique** sur le nombre de lignes que vous souhaitez autoriser dans le [!DNL popover].
1. Une fois l’opération terminée, cliquez sur **Enregistrer la configuration**.

## Exemple de style [!DNL Popover]

Vous pouvez personnaliser l’aspect du widget [!DNL Popover] pour qu’il corresponde aux directives de style et de marque de votre entreprise.

Le [!DNL storefront popover] affiche toujours le produit `name` et `price`, et la sélection des champs n’est pas configurable. Cependant, les éléments [!DNL popover] peuvent être stylisés à l’aide des classes [CSS](https://developer.adobe.com/commerce/frontend-core/guide/css/). Par exemple, les déclarations suivantes modifient la couleur d’arrière-plan du conteneur et du pied de page [!DNL popover].

```css
.livesearch.popover-container {
    background-color: lavender;
}

.livesearch.view-all-footer {
    background-color: magenta;
}
```

## Visibilité des conteneurs

Le composant parent de `.livesearch.popover-container` est `.search-autocomplete`.  La classe `.active` indique la visibilité du conteneur. La classe `.active` est ajoutée de manière conditionnelle lorsque [!DNL popover] est ouvert.

```css
.search-autocomplete.active   /* visible */
.search-autocomplete          /* not visible */
```

Pour plus d’informations sur le style des éléments storefront, reportez-vous à la section [Feuilles de style en cascade (CSS)](https://developer.adobe.com/commerce/frontend-core/guide/css/) du [Guide du développeur Frontend](https://developer.adobe.com/commerce/frontend-core/guide/).

## Sélecteurs de classe

Vous pouvez utiliser les sélecteurs de classe suivants pour mettre en forme le conteneur et les éléments de produit dans le [!DNL popover].

- `.livesearch.popover-container`
- `.livesearch.view-all-footer`
- `.livesearch.products-container`
- `.livesearch.product-result`
- `.livesearch.product-name`
- `.livesearch.product-price`

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

#### .livesearch product-link

![Résultat du produit](assets/livesearch-product-link.png)

## Utilisation d’un thème modifié {#working-with-modified-theme}

Vous pouvez utiliser le [!DNL storefront popover] avec un [thème](https://developer.adobe.com/commerce/frontend-core/guide/themes/) personnalisé qui hérite des fichiers requis de *Luma*. Le bloc `top.search` du module `header-wrapper` de `Magento_Search` ne doit pas être modifié.

```html
<referenceContainer name="header-wrapper">
   <block class="Magento\Framework\View\Element\Template" name="top.search" as="topSearch" template="Magento_Search::form.mini.phtml">
      <arguments>
         <argument name="configProvider" xsi:type="object">Magento\Search\ViewModel\ConfigProvider</argument>
      </arguments>
   </block>
</referenceContainer>
```

## Désactivation de l’ [!DNL popover]

Pour désactiver [!DNL popover] et restaurer la fonctionnalité [Recherche rapide](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#quick-search) standard, saisissez la commande suivante :

```bash
bin/magento module:disable Magento_LiveSearchStorefrontPopover
```

## Implémentations sans affichage

Pour ceux qui disposent d’implémentations sans interface utilisateur graphique, vous pouvez installer le [!DNL Live Search popover] à l’aide d’un [package npm](https://www.npmjs.com/package/@magento/ds-livesearch-storefront-utils).
