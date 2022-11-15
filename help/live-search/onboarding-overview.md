---
title: "Présentation de l’intégration"
description: "[!DNL Live Search] flux d’intégration, exigences du système, limites et limites"
exl-id: 45f6c1ae-544b-47ef-9feb-c1a05f93108a
source-git-commit: b4cdbc3b166a3aae5b4219196a86cb681744d435
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# Présentation de l’intégration

Pour commencer à utiliser [!DNL Live Search] pour Adobe Commerce, exécutez le processus d’intégration pour installer l’extension, configurer vos clés d’API et synchroniser votre catalogue.

## Flux d’intégration

![[!DNL Live Search] diagramme d’intégration](assets/onboarding-flow.svg)

## Conditions {#requirements}

* [Adobe Commerce](https://magento.com/products/magento-commerce) 2.4.x
* PHP 7.3 / 7.4 / 8.1
* [!DNL Composer]

### Plateformes prises en charge

* Adobe Commerce on prem (EE) : 2.4.x
* Adobe Commerce on Cloud (CEE) : 2.4.x

## Limites et seuils

À l’heure actuelle, la variable [!DNL Live Search] L’API de recherche/catégorie présente les limites et limites statiques suivantes prises en charge :

### Indexation

* Index jusqu’à 300 attributs de produit par vue de magasin.
* répertorie uniquement les produits de la base de données Adobe Commerce ;
* Les pages CMS ne sont pas indexées.

### Requête

* [!DNL Live Search] n’a pas accès à la taxonomie complète de l’arborescence des catégories, ce qui rend certains scénarios de recherche de navigation par couches hors de sa portée.
* [!DNL Live Search] utilise un point d’entrée GraphQL unique pour les requêtes afin de prendre en charge des fonctionnalités telles que les facettes intelligentes et la recherche par saisie. Bien que similaire au [API GraphQL du Magento](https://devdocs.magento.com/guides/v2.4/graphql), il existe quelques différences et certains champs peuvent ne pas être entièrement compatibles à l’heure actuelle.

### Règles

* Le nombre maximal de règles par vue de magasin est de 50.
* Le nombre maximal de conditions par règle est 10.
* Le nombre maximal d’événements par règle est de 25.

### Synonymes

* [!DNL Live Search] peut gérer jusqu’à 200 synonymes par vue de magasin.

### Version bêta de PWA

* La mise en oeuvre bêta actuelle du PWA de la recherche en direct nécessite plus de temps de traitement pour renvoyer les résultats de recherche que la recherche en direct avec le storefront Commerce natif.
* La version bêta de PWA pour [!DNL Live Search] ne prend pas en charge [gestion des événements](https://devdocs.magento.com/shared-services/storefront-events-sdk.html).
* Les attributs de produit suivants ne sont pas pris en charge par GraphQL lorsqu’ils sont utilisés en relation avec la version bêta de [PWA](https://developer.adobe.com/commerce/pwa-studio/): `description`, `name`, `short_description`

### Non pris en charge pour le moment

* Le [Recherche avancée](https://docs.magento.com/user-guide/catalog/search-advanced.html) module est désactivé lorsque [!DNL Live Search] est installé et le lien Recherche avancée dans le pied de page du storefront est supprimé.
* [Groupes de clients](https://docs.magento.com/user-guide/customers/customer-groups.html)
* [Groupes de prix personnalisés](https://docs.magento.com/user-guide/catalog/product-price-group.html)
* Plusieurs emplacements d’inventaire utilisés par [MCOM](https://docs.magento.com/user-guide/mcom.html) ou d’autres extensions OMS
* [Fonctionnalités intégrées B2B](https://business.adobe.com/products/magento/b2b-ecommerce.html)
* Les prix des produits ne sont pas inclus [taxe sur la valeur ajoutée](https://docs.magento.com/user-guide/tax/vat.html) (TVA).
* Les produits en rupture de stock apparaissent dans les résultats de recherche, quel que soit le [Options Stock](https://docs.magento.com/user-guide/catalog/inventory-options-global.html) configuration.
