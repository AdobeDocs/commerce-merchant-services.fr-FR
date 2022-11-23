---
title: "Remarques techniques sur les facettes"
description: "Remarques techniques sur l’utilisation de [!DNL Live Search] facettes."
exl-id: 37982610-0ff7-48b7-b088-be7d2eff8a57
source-git-commit: 1a55f2fb3d56183e5e73d172ebdc40f340e4d520
workflow-type: tm+mt
source-wordcount: '117'
ht-degree: 0%

---

# Notes techniques sur les facettes

La facette est une méthode de filtrage haute performance qui utilise plusieurs dimensions de valeurs d’attributs statiques et dynamiques pouvant faire l’objet de recherches comme critères de recherche.

[!DNL Live Search] utilise la variable `productSearch` requête qui renvoie des facettes et d’autres données spécifiques à [!DNL Live Search]. Voir [`productSearch` query](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/) pour des exemples de code.

## Agrégation des facettes

L’agrégation des facettes est effectuée comme suit si le storefront comporte trois facettes (catégories, couleur et prix) et que les filtres du nouvel acheteur sont appliqués aux trois éléments (couleur = bleu, prix compris entre 10,00 et 50,00 $, catégories = `promotions`).

* `categories` agrégation - Agrégats `categories`, s’applique `color` et `price` filtres, mais pas le filtre `categories` filtre.
* `color` agrégation - Agrégats `color`, s’applique `price` et `categories` filtres, mais pas le filtre `color` filtre.
* `price` agrégation - Agrégats `price`, s’applique `color` et `categories` filtres, mais pas le filtre `price` filtre.
