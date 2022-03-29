---
title: Présentation de l’intégration
description: Flux d’intégration de la recherche en direct, configuration système requise, limites et limites
source-git-commit: 6220824c6032a33a760fe5c2bb5d2346e00a074b
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# Présentation de l’intégration

Pour commencer à utiliser Live Search pour Adobe Commerce, vous devez suivre quelques étapes d’intégration afin d’installer l’extension, de configurer vos clés d’API et de synchroniser votre catalogue.

## Flux d’intégration

![Diagramme d’intégration de Live Search](assets/onboarding-flow.svg)

## Conditions {#requirements}

* [Adobe Commerce](https://magento.com/products/magento-commerce) 2.4.x
* PHP 7.3 / 7.4
* [!DNL Composer]

### Plateformes prises en charge

* Adobe Commerce on prem (EE) : 2.4.x
* Adobe Commerce on Cloud (CEE) : 2.4.x

## Limites et seuils

Actuellement, l’API de recherche/catégorie de recherche en direct comporte les limites et limites statiques suivantes prises en charge :

### Indexation

* Index jusqu’à 300 attributs de produit par vue de magasin
* répertorie uniquement les produits de la base de données Adobe Commerce ;
* N’indexe pas les pages CMS

### Limites de requête

* La recherche en direct n’a pas accès à la taxonomie complète de l’arborescence des catégories, ce qui rend certains scénarios de recherche de navigation par couches hors de sa portée.
* La recherche en direct utilise un point d’entrée GraphQL unique pour les requêtes afin de prendre en charge des fonctionnalités telles que les facettes intelligentes et la recherche par saisie. Bien que similaire au [API GraphQL du Magento](https://devdocs.magento.com/guides/v2.4/graphql), il existe quelques différences et certains champs peuvent ne pas être entièrement compatibles à l’heure actuelle.

### Version bêta de PWA

* La version bêta de PWA pour Live Search ne prend pas en charge [gestion des événements](https://devdocs.magento.com/shared-services/storefront-events-sdk.html).
* Les attributs de produit suivants ne sont pas pris en charge par GraphQL lorsqu’ils sont utilisés en relation avec la version bêta de [PWA](https://developer.adobe.com/commerce/pwa-studio/): `description`, `name`, `short_description`

### Non pris en charge pour le moment

* Le [Recherche avancée](https://docs.magento.com/user-guide/catalog/search-advanced.html) est désactivé lorsque la recherche en direct est installée et que le lien Recherche avancée dans le pied de page du storefront est supprimé.
* [Groupes de clients](https://docs.magento.com/user-guide/customers/customer-groups.html)
* [Groupes de prix personnalisés](https://docs.magento.com/user-guide/catalog/product-price-group.html)
* Plusieurs emplacements d’inventaire utilisés par [MCOM](https://docs.magento.com/user-guide/mcom.html) ou d’autres extensions OMS
* [Fonctionnalités intégrées B2B](https://business.adobe.com/products/magento/b2b-ecommerce.html)
