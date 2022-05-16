---
title: '"[!DNL Live Search] Notes de mise à jour"'
description: '"Informations les plus récentes sur la version [!DNL Live Search] d’Adobe Commerce."'
exl-id: 2a581e43-35f5-48ce-9752-844430ccdebf
source-git-commit: bffbede99865e9085f60392e474065a454446370
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# [!DNL Live Search] Notes de mise à jour

Ces notes de mise à jour décrivent les dernières versions de [!DNL Live Search] et incluent :

* ![Nouveau](../assets/new.svg) - Nouvelles fonctionnalités
* ![Correction](../assets/fix.svg) - Correctifs et améliorations
* ![Bogue](../assets/bug.svg) - Problèmes connus

## [!DNL Live Search] 2,0

* Compatible avec Adobe Commerce (EE) : 2.4.x
* Compatible avec Adobe Commerce for Cloud (CEE) : 2.4.x
* Stabilité : Stable

Existant [!DNL Live Search] Les installations doivent être mises à niveau vers [!DNL Live Search] 2.0.0 pour tirer parti des nouvelles fonctionnalités, correctifs et améliorations suivants :

* ![Nouveau](../assets/new.svg) - [!DNL Live Search] prend désormais en charge PHP 8.1 pour les installations exécutant Adobe Commerce 2.4.4.
* ![Nouveau](../assets/new.svg) - Le `Magento_ElasticsearchCatalogPermissionsGraphQl` module est ajouté à la liste des modules désactivés lors de l’installation.
* ![Nouveau](../assets/new.svg) - Le nombre de lignes disponibles dans la variable [[!DNL storefront popover]](quick-tour.md) peut être configuré à partir du *Administration*.
* ![Nouveau](../assets/new.svg) - Bêta [PWA](https://developer.adobe.com/commerce/pwa-studio/) compatibilité pour [!DNL Live Search].
* ![Nouveau](../assets/new.svg) - Le [!DNL Live Search] le processus d’installation est mis à jour avec des modifications avancées des processus.
* ![Correction](../assets/fix.svg) - [Recherche avancée](https://docs.magento.com/user-guide/catalog/search-advanced.html) lien supprimé du pied de page du storefront.
* ![Bogue](../assets/bug.svg) - Les attributs de produit suivants ne sont pas pris en charge par [API GraphQL du Magento](https://devdocs.magento.com/guides/v2.4/graphql) lorsqu’elle est utilisée en rapport avec la version bêta de PWA : `description`, `name`, `short_description`
* ![Bogue](../assets/bug.svg) - La version bêta de PWA pour [!DNL Live Search] ne prend pas en charge [gestion des événements](https://devdocs.magento.com/shared-services/storefront-events-sdk.html).

## [!DNL Live Search] 1.3.1

* Compatible avec Adobe Commerce (EE) : 2.4.x
* Compatible avec Adobe Commerce for Cloud (CEE) : 2.4.x
* Stabilité : Stable

* ![Correction](../assets/fix.svg) - [Attribut de prix personnalisé](https://docs.magento.com/user-guide/stores/attributes-input-types.html) ne renvoie plus d’erreur lorsqu’elle est configurée en tant que [facette]({% lien live-search/facets-add.md %}).
* ![Correction](../assets/fix.svg) - Correction d’un problème en raison duquel une erreur se produisait lorsqu’aucune [symbole de devise](https://docs.magento.com/user-guide/stores/currency-symbols.html) (`data-currency-symbol`) est disponible.
* ![Correction](../assets/fix.svg) - [[!DNL Storefront popover]](storefront-popover.md) affiche désormais la variable [Prix spécial](https://docs.magento.com/user-guide/catalog/product-price-special.html) (prix final minimum) le cas échéant.

## [!DNL Live Search] 1.3.0

* Compatible avec Adobe Commerce (EE) : 2.4.x
* Compatible avec Adobe Commerce for Cloud (CEE) : 2.4.x
* Stabilité : Stable

* ![Nouveau](../assets/new.svg) - [Performances](performance.md) le tableau de bord des rapports fournit des informations sur les termes de recherche que les acheteurs utilisent.
* ![Nouveau](../assets/new.svg) - [!DNL Live Search] [SDK des événements Storefront](https://devdocs.magento.com/shared-services/storefront-events-sdk.html) permet d’accéder à une couche de données commune avec des services de publication et d’abonnement d’événements, ainsi que des mesures.
* ![Correction](../assets/fix.svg) - Le [[!DNL Storefront Popover]](https://devdocs.magento.com/live-search/storefront-popover.html) comporte une nouvelle `active` pour la classe `.search-autocomplete` conteneur contrôlant la visibilité.
* ![Correction](../assets/fix.svg) - Sur le storefront, le [Termes de recherche](https://docs.magento.com/user-guide/marketing/search-terms-popular.html) lien de pied de page supprimé et son cache désactivé pour [!DNL Live Search] installations.
* ![Bogue](../assets/bug.svg) - Le correctif pour l’adaptateur de recherche gère les produits en double.
* ![Bogue](../assets/bug.svg) - [!DNL Live Search] prend en charge [source unique](https://docs.magento.com/user-guide/catalog/inventory-sources.html) emplacements d’inventaire (physiques) avec plusieurs emplacements (virtuels) [stocks](https://docs.magento.com/user-guide/catalog/inventory-stock.html). Pour l’instant, plusieurs sources d’inventaire ne sont pas prises en charge.

## [!DNL Live Search] 1.2.0

* Compatible avec Adobe Commerce (EE) : 2.4.x
* Compatible avec Adobe Commerce for Cloud (CEE) : 2.4.x
* Stabilité : Stable

* ![Nouveau](../assets/new.svg) - [[!DNL Storefront popover]](storefront-popover.md) affiche les produits suggérés et les images miniatures des principaux résultats de recherche sous la forme de requêtes de type shoppers dans la zone de recherche.
* ![Nouveau](../assets/new.svg) - Commerce *Administration* la session reste ouverte pendant les longues périodes d’inactivité du clavier ;
* ![Nouveau](../assets/new.svg) - [!DNL Live Search] est activé automatiquement après l’intégration
* ![Correction](../assets/fix.svg) - Le temps d’indexation initial est inférieur à une heure
* ![Correction](../assets/fix.svg) - Mises à jour incrémentielles des produits quasiment en temps réel (après installation et configuration)
* ![Correction](../assets/fix.svg) - Colonnes triables dans l’éditeur de synchronisation
* ![Correction](../assets/fix.svg) - [!DNL Live Search] ne renvoie plus d’erreur si les critères de recherche contiennent une valeur d’ordre de tri vide
* ![Correction](../assets/fix.svg) - Le filtrage de plage ne rompt plus si les codes d’attribut contiennent des chaînes &quot;to&quot; ou &quot;from&quot;

## [!DNL Live Search] 1.1.0

* Compatible avec Adobe Commerce (EE) : 2.4.x
* Compatible avec Adobe Commerce for Cloud (CEE) : 2.4.x
* Stabilité : Stable

* ![Bogue](../assets/bug.svg) - Le [!DNL Live Search] ne prend en charge que les [monnaie de base](https://docs.magento.com/user-guide/stores/currency-configuration.html) de l’installation d’Adobe Commerce.
* ![Bogue](../assets/bug.svg) - Lors de l’ajout d’une facette, le flux d’attributs de produit ne se met pas à jour correctement lorsqu’il est défini sur `Update on Save`. Pour éviter ce problème, accédez à [Gestion des index](https://docs.magento.com/user-guide/system/index-management.html) et définissez le flux Attributs du produit sur `Update by Schedule`.
* ![Bogue](../assets/bug.svg) - [!DNL Live Search] les synonymes sont définis par vue de magasin, mais sont actuellement stockés par site web et identifiés par une combinaison de `environmentId` + `storeViewCode`. Par conséquent, tous les sites web et toutes les vues de magasin dans l’installation Adobe Commerce partagent le même ensemble de synonymes. Le dernier ensemble de synonymes créé pour la vue de magasin est prioritaire.
* ![Bogue](../assets/bug.svg) - Si un terme de synonyme contient plusieurs mots, chaque mot est traité comme un synonyme distinct. Par exemple, si vous définissez &quot;pièce temporelle&quot; comme un synonyme de &quot;montre&quot;, &quot;heure&quot; et &quot;pièce&quot; sont tous deux traités comme des synonymes de montre.

## Documentation

Pour en savoir plus :

* [Documentation destinée aux développeurs Adobe Commerce](https://devdocs.magento.com/)
* [Guide de l’utilisateur d’Adobe Commerce](https://docs.magento.com/user-guide/)
* [[!DNL Live Search] sur Marketplace](https://marketplace.magento.com/magento-live-search.html)
