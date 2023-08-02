---
title: "Quick Tour"
description: "Visitez rapidement le [!DNL Live Search] de la vitrine."
exl-id: bcb19506-6617-4c8a-83df-9d961f81e9e8
source-git-commit: 9cf48f6f900385a5cb772adee8834ec9cfe5ee13
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---

# Présentation rapide

En mettant l&#39;accent sur la rapidité, la pertinence et la facilité d&#39;utilisation, [!DNL Live Search] est un outil de transformation pour les acheteurs comme pour les marchands. Suivez-le pour une visite rapide de [!DNL Live Search] de la vitrine.

## Recherche en cours de frappe

[!DNL Live Search] répond avec des produits suggérés et une miniature des principaux résultats de recherche dans une [fenêtre contextuelle](storefront-popover.md) comme les clients saisissent des requêtes dans la variable [Rechercher](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#quick-search) de la boîte. La variable [détail du produit](https://experienceleague.adobe.com/docs/commerce-admin/start/storefront/storefront.html#product-page) s’affiche lorsque les acheteurs cliquent sur un produit proposé ou présenté. A _Afficher tout_ dans le pied de page de la fenêtre contextuelle affiche la page des résultats de la recherche.

[!DNL Live Search] renvoie &quot;search as you type&quot; (rechercher en cours de frappe) pour une requête de deux caractères ou plus. Pour une correspondance partielle, le nombre maximal de caractères par mot est de 20. Le nombre de caractères dans la requête n’est pas configurable. Les champs suivants sont inclus dans la fenêtre contextuelle : `name`, `sku`, et `category_ids`.

![Exemple de storefront : effectuez une recherche lorsque vous tapez](assets/storefront-search-as-you-type.png)

## Afficher tous les résultats de recherche

Pour répertorier tous les produits renvoyés par la requête &quot;rechercher lorsque vous tapez&quot;, cliquez sur _Afficher tout_ dans le pied de page de la fenêtre contextuelle.

![Exemple de storefront - facettes de prix](assets/storefront-view-all-search-results.png)

## Recherche filtrée avec facettes

La recherche filtrée utilise plusieurs dimensions de valeurs d’attribut, ou [facettes](facets.md), comme critères de recherche. La sélection des filtres est définie par le commerçant et change en fonction des produits renvoyés, les facettes les plus couramment utilisées étant collées en haut de la liste.

Utilisez les facettes comme paramètres d’URL :`http://yourwebsite.com?color=red`et la recherche en direct filtrent les résultats en fonction de ces valeurs d’attribut.

## Synonymes

[Synonymes](synonyms.md) développez la portée et accentuez le focus des requêtes en incluant des mots que les acheteurs peuvent utiliser qui diffèrent de ceux du catalogue. Vous pouvez affiner le dictionnaire de synonyme pour que les acheteurs restent actifs et sur le chemin de l’achat.

## Règles de marchandisage

Marchandisage [rules](rules.md) façonnez l’expérience d’achat avec des instructions if-then ajoutant une logique et des événements à rechercher. Vous pouvez facilement booster ou enterrer des produits pour une promotion, une saison ou toute autre période.
