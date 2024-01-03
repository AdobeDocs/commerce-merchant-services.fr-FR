---
title: "Présentation technique"
description: "[!DNL Live Search] flux d’intégration, exigences système, limites et limites"
exl-id: 45f6c1ae-544b-47ef-9feb-c1a05f93108a
recommendations: noCatalog
source-git-commit: 9b46ee98d0459b6a4cce2da51ac6308a1102ef30
workflow-type: tm+mt
source-wordcount: '691'
ht-degree: 0%

---

# Présentation technique

Cette rubrique passe en revue les exigences techniques et les conseils d’installation et d’optimisation [!DNL Live Search] pour Adobe Commerce.

## Conditions {#requirements}

* [Adobe Commerce](https://business.adobe.com/products/magento/magento-commerce.html) 2.4.4+
* PHP 8.1 / 8.2
* [!DNL Composer]

### Plateformes prises en charge

* Adobe Commerce on-premise (EE) : 2.4.4+
* Adobe Commerce on Cloud (CEE) : 2.4.4+

## Point d’entrée

[!DNL Live Search] communique par le biais du point de terminaison à l’adresse `https://catalog-service.adobe.io/graphql`.

>[!NOTE]
>
>As [!DNL Live Search] n&#39;a pas accès à la base de données complète des produits, [!DNL Live Search] GraphQL et Commerce core GraphQL n’auront pas une parité complète.

## Limites et seuils

Actuellement, la variable [!DNL Live Search] L’API de recherche/catégorie présente les limites et limites statiques suivantes prises en charge :

### Indexation

* [Index](indexing.md) jusqu’à 300 attributs de produit par consultation de magasin.
* répertorie uniquement les produits de la base de données Adobe Commerce ;
* Les pages CMS ne sont pas indexées.

### Requête

* [!DNL Live Search] n’a pas accès à la taxonomie complète de l’arborescence des catégories, ce qui rend certains scénarios de recherche de navigation par couches hors de sa portée.
* [!DNL Live Search] utilise un point de terminaison GraphQL unique pour les requêtes afin de prendre en charge des fonctionnalités telles que les facettes dynamiques et la recherche par saisie. Bien que similaire à la variable [API GRAPHQL](https://developer.adobe.com/commerce/webapi/graphql/), il existe quelques différences et certains champs peuvent ne pas être entièrement compatibles.

Pour restreindre les groupes de clients à l’aide des autorisations du catalogue :

* Les produits doivent être affectés à la catégorie Racine .
* Le groupe de clients &quot;Non connecté&quot; doit disposer des autorisations de navigation &quot;Autoriser&quot;.
* Pour limiter les produits au groupe de clients Non connecté , accédez à chaque catégorie et définissez des autorisations pour chaque groupe de clients.

### Règles

* Nombre maximal de marchandisage de recherche [rules](rules.md) la vue de magasin est de 50.
* Le marchandisage des catégories peut comporter une règle par catégorie.
* Le nombre maximal de conditions par règle est 10.
* Le nombre maximal d’événements par règle est de 25.

### Synonymes

* [!DNL Live Search] peut gérer jusqu’à 200 [synonyms](synonyms.md) par vue de magasin.

## Prise en charge linguistique

[!DNL Live Search] Les widgets prennent en charge les langues suivantes :

* en_US (par défaut)
* de_DE
* es_MX
* fr_FR
* it_IT
* ja_JA
* nl_NL
* no_NO
* pt_PT

Si le widget détecte que le paramètre de langue d’administrateur Commerce (_Magasins_ > Paramètres > _Configuration_ > _Général_ > Options de pays) correspond à une langue prise en charge. Par défaut, cette langue est utilisée. Sinon, les widgets sont définis par défaut sur Anglais.

Les administrateurs peuvent également définir la langue de la variable [index de recherche](settings.md#language), pour améliorer les résultats de la recherche.

## Marchandisage des catégories

[Marchandisage des catégories](category-merch.md) vous permet de configurer [!DNL Live Search] pour travailler au niveau de la catégorie de produits.

Cette vidéo présente le marchandisage par catégorie.

>[!VIDEO](https://video.tv.adobe.com/v/3424617)

## Référentiel de code de widget

Le widget Page de liste de produits et le widget Fenêtre contextuelle de recherche peuvent tous deux être téléchargés à partir de leur référentiel github.

Cela permet aux développeurs de personnaliser entièrement les fonctionnalités et le style. Ces utilisateurs hébergent le code eux-mêmes tout en tirant parti de la fonction [!DNL Live Search] service.

* [Widget PLP](https://github.com/adobe/storefront-product-listing-page)
* [Barre de recherche](https://github.com/adobe/storefront-search-as-you-type)

## Inventory management

[!DNL Live Search] prend [Inventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/introduction.html) Fonctionnalités dans Commerce (anciennement appelées inventaire multi-source ou MSI). Pour activer la prise en charge complète, vous devez [update](install.md#update) le module de dépendance ; `commerce-data-export` vers la version 102.2.0+.

[!DNL Live Search] renvoie une valeur booléenne indiquant si un produit est disponible dans Inventory management, mais ne contient pas d’informations sur la source qui possède le stock.

## Indexateur de prix

Les clients Live Search peuvent utiliser la nouvelle [Indexeur de prix SaaS](../price-index/index.md), qui accélère les mises à jour des changements de prix et le temps de synchronisation.

## Prise en charge des PWA

[!DNL Live Search] fonctionne avec PWA Studio, mais les utilisateurs peuvent voir de légères différences par rapport aux autres mises en oeuvre de Commerce. Les fonctionnalités de base telles que la recherche et la liste de produits fonctionnent dans Venia, mais certaines permutations de Graphql peuvent ne pas fonctionner correctement. Il peut également y avoir des différences de performances.

* L’implémentation actuelle du PWA de [!DNL Live Search] nécessite plus de temps de traitement pour renvoyer les résultats de recherche que [!DNL Live Search] avec le storefront natif Commerce.
* [!DNL Live Search] dans PWA ne prend pas en charge [gestion des événements](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/). Par conséquent, les rapports de recherche et le marchandisage intelligent fonctionneront.
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

## Non pris en charge actuellement

* La variable [Recherche avancée](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#advanced-search) module est désactivé lorsque [!DNL Live Search] est installé et le lien Recherche avancée dans le pied de page du storefront est supprimé.
* [Tarifs de niveau](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/product-price-tier.html) et [Tarifs spéciaux](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/product-price-special.html) ne sont pas pris en charge dans la variable [!DNL Live Search] Widget de page de liste de produits et de fenêtre contextuelle.

## Cookies

[!DNL Live Search] collecte des données d’interaction utilisateur dans le cadre de ses fonctionnalités de base et utilise des cookies pour stocker ces données. Lors de la collecte de toute information utilisateur, l’utilisateur doit accepter de stocker les cookies. [!DNL Live Search] et [!DNL Product Recommendations] partagez le flux de données et, par conséquent, le même mécanisme de cookie. En savoir plus à ce sujet dans [Gérer les restrictions de cookie](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/setting-cookie.html).