---
title: Notes techniques sur les facettes
description: Notes techniques sur l’utilisation des facettes de recherche en direct.
exl-id: 37982610-0ff7-48b7-b088-be7d2eff8a57
source-git-commit: 7402e97f53b71e488d860215487f4809572b7e6f
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Notes techniques sur les facettes

La facette est une méthode de filtrage haute performance qui utilise plusieurs dimensions de valeurs d’attributs statiques et dynamiques pouvant faire l’objet de recherches comme critères de recherche.

[!DNL Live Search] utilise la variable `productSearch` requête qui renvoie des facettes et d’autres données spécifiques à [!DNL Live Search]. Voir [`productSearch` query](https://devdocs.magento.com/live-search/product-search.html) pour des exemples de code.

## Agrégation des facettes

L’agrégation des facettes est effectuée comme suit si le storefront comporte trois facettes (catégories, couleur et prix) et que les filtres du nouvel acheteur sont appliqués aux trois éléments (couleur = bleu, prix compris entre 10,00 et 50,00 $, catégories = `promotions`).

* `categories` agrégation - Agrégats `categories`, s’applique `color` et `price` filtres, mais pas le filtre `categories` filtre.
* `color` agrégation - Agrégats `color`, s’applique `price` et `categories` filtres, mais pas le filtre `color` filtre.
* `price` agrégation - Agrégats `price`, s’applique `color` et `categories` filtres, mais pas le filtre `price` filtre.

## Valeurs d’attribut par défaut

Les attributs de produit suivants comportent certains [propriétés storefront](https://docs.magento.com/user-guide/stores/attributes-product.html) qui sont activés par défaut.

| Propriété | Propriété Storefront | Attribut |
|---|---|---|
| Triable | Utilisé pour le tri dans la liste des produits | `price` |
| Searchable | Utilisation dans la recherche | `price` <br />`sku`<br />`name` |
| FilterableInSearch | Utilisation dans la navigation par couches - Filtrable (avec résultats) | `price`<br />`visibility`<br />`category_name` |
