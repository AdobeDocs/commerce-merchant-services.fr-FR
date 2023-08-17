---
title: "Présentation de l’intégration"
description: "[!DNL Live Search] flux d’intégration, exigences système, limites et limites"
exl-id: 45f6c1ae-544b-47ef-9feb-c1a05f93108a
recommendations: noCatalog
source-git-commit: 9ae4aff1851e9ce9920c4fbf11d2616d6f0f6307
workflow-type: tm+mt
source-wordcount: '545'
ht-degree: 0%

---

# Présentation de l’intégration

Pour commencer à utiliser [!DNL Live Search] pour Adobe Commerce, exécutez le processus d’intégration pour installer l’extension, configurer vos clés d’API et synchroniser votre catalogue.

## Flux d’intégration

![[!DNL Live Search] diagramme d’intégration](assets/onboarding-flow.svg)

## Conditions {#requirements}

* [Adobe Commerce](https://business.adobe.com/products/magento/magento-commerce.html) 2.4.4+
* PHP 8.1 / 8.2
* [!DNL Composer]

### Plateformes prises en charge

* Adobe Commerce on-premise (EE) : 2.4.4+
* Adobe Commerce on Cloud (CEE) : 2.4.4+

## Limites et seuils

Actuellement, la variable [!DNL Live Search] L’API de recherche/catégorie présente les limites et limites statiques suivantes prises en charge :

### Indexation

* Index jusqu’à 300 attributs de produit par vue de magasin.
* répertorie uniquement les produits de la base de données Adobe Commerce ;
* Les produits doivent se trouver dans le catalogue partagé par défaut.
* Les pages CMS ne sont pas indexées.

### Requête

* [!DNL Live Search] n’a pas accès à la taxonomie complète de l’arborescence des catégories, ce qui rend certains scénarios de recherche de navigation par couches hors de sa portée.
* [!DNL Live Search] utilise un point de terminaison GraphQL unique pour les requêtes afin de prendre en charge des fonctionnalités telles que les facettes dynamiques et la recherche par saisie. Bien que similaire à la variable [API GRAPHQL](https://developer.adobe.com/commerce/webapi/graphql/), il existe quelques différences et certains champs peuvent ne pas être entièrement compatibles.

Pour restreindre les groupes de clients à l’aide des autorisations du catalogue :

* Les produits doivent être affectés à la catégorie Racine .
* Le groupe de clients &quot;Non connecté&quot; doit disposer des autorisations de navigation &quot;Autoriser&quot;.
* Pour limiter les produits au groupe de clients Non connecté , accédez à chaque catégorie et définissez des autorisations pour chaque groupe de clients.

### Règles

* Le nombre maximal de règles par vue de magasin est de 50.
* Le nombre maximal de conditions par règle est 10.
* Le nombre maximal d’événements par règle est de 25.

### Synonymes

* [!DNL Live Search] peut gérer jusqu’à 200 synonymes par vue de magasin.

## Indexateur de prix

Les clients Live Search peuvent utiliser la nouvelle [Indexeur de prix SaaS](../price-index/index.md), qui accélère les mises à jour des changements de prix et le temps de synchronisation.

### Prise en charge des PWA

[!DNL Live Search] fonctionne avec PWA Studio, mais les utilisateurs peuvent voir de légères différences par rapport aux autres mises en oeuvre de Commerce. Les fonctionnalités de base telles que la recherche et la liste de produits fonctionnent dans Venia, mais certaines permutations de Graphql peuvent ne pas fonctionner correctement. Il peut également y avoir des différences de performances.

* L’implémentation actuelle du PWA de [!DNL Live Search] nécessite plus de temps de traitement pour renvoyer les résultats de recherche que [!DNL Live Search] avec le storefront natif Commerce.
* [!DNL Live Search] dans PWA ne prend pas en charge [gestion des événements](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/). Le marchandisage intelligent ne fonctionnera pas à cause de cela.
* Filtrage directement sur `description`, `name`, `short_description` n’est pas pris en charge par GraphQL lorsqu’il est utilisé avec [PWA](https://developer.adobe.com/commerce/pwa-studio/), mais ils sont renvoyés avec un filtre plus général.

Pour utiliser [!DNL Live Search] avec PWA Studio, les intégrateurs doivent également :

1. Installer [livesearch-storefront-utils](https://www.npmjs.com/package/@magento/ds-livesearch-storefront-utils).
1. Définissez la variable `environmentId` dans le `storeDetails` .

   ```javascript
   const storeDetails: StoreDetailsProps = {
       environmentId: <Storefront_ID>,
       websiteCode: "base",
       storeCode: "main_website_store",
       storeViewCode: "default",
       searchUnitId: searchUnitId,
       config: {
           minQueryLength: 5,
           pageSize: 8,
           currencySymbol: "$",
           },
       };
   ```

### Non pris en charge actuellement

* La variable [Recherche avancée](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#advanced-search) module est désactivé lorsque [!DNL Live Search] est installé et le lien Recherche avancée dans le pied de page du storefront est supprimé.
* Plusieurs emplacements d’inventaire utilisés par [MCOM](https://experienceleague.adobe.com/docs/commerce-admin/systems/integrations/mcom.html) ou d’autres extensions OMS
* Les prix des produits ne sont pas inclus [taxe sur la valeur ajoutée](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/taxes/vat.html) (TVA).
* [Prix de niveau](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/product-price-tier.html) n’est pas pris en charge dans la fenêtre contextuelle de recherche en direct et le widget de page de liste de produits.

## Cookies

[!DNL Live Search] collecte des données d’interaction utilisateur dans le cadre de ses fonctionnalités de base et utilise des cookies pour stocker ces données. Lors de la collecte de toute information utilisateur, l’utilisateur doit accepter de stocker les cookies. [!DNL Live Search] et [!DNL Product Recommendations] partagez le flux de données et, par conséquent, le même mécanisme de cookie. En savoir plus à ce sujet dans [Gérer les restrictions de cookie](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/setting-cookie.html).
