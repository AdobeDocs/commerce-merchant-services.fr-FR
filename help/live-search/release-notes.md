---
title: "[!DNL Live Search] Notes de mise à jour"
description: "Informations les plus récentes sur la version [!DNL Live Search] d’Adobe Commerce."
exl-id: 2a581e43-35f5-48ce-9752-844430ccdebf
source-git-commit: 4566727b4e672033997491bcaf075c48e2a55cc8
workflow-type: tm+mt
source-wordcount: '1004'
ht-degree: 1%

---

# [!DNL Live Search] Notes de mise à jour

Ces notes de mise à jour décrivent les dernières versions de [!DNL Live Search] et incluent :

* ![Nouveau](../assets/new.svg) - Nouvelles fonctionnalités
* ![Correction](../assets/fix.svg) - Correctifs et améliorations
* ![Bogue](../assets/bug.svg) - Problèmes connus

## [!DNL Live Search] 2.0.5 {#205}

* Compatible avec Adobe Commerce (EE) : 2.4.x
* Compatible avec Adobe Commerce for Cloud (CEE) : 2.4.x
* Stabilité : Stable

* ![Correction](../assets/fix.svg) - La recherche en direct renvoie une erreur lorsque les ressources du SDK n’étaient pas disponibles en raison de problèmes de réseau. Ce bogue a maintenant été corrigé.

Les commerçants doivent mettre à niveau l’extension Live Search >= 2.0.5 pour accéder à ces fonctionnalités.

Il est recommandé de mettre à niveau et de tester avant de passer en production. Envisagez de mettre à niveau l’environnement de production pendant les heures creuses après avoir vérifié les résultats de l’environnement de test.

## [!DNL Live Search] 2.0.4 {#204}

* Compatible avec Adobe Commerce (EE) : 2.4.x
* Compatible avec Adobe Commerce for Cloud (CEE) : 2.4.x
* Stabilité : Stable

* ![Nouveau](../assets/new.svg) - La recherche en direct prend désormais en charge le filtrage par le paramètre &quot;Produits d’affichage en rupture de stock&quot; dans l’administrateur. Si &quot;Produits en rupture de stock&quot; est défini sur false, `inStock = true` est ajouté au filtre.
* ![Correction](../assets/fix.svg) - Pour améliorer les performances, le bloc &quot;Suggestions&quot; a été supprimé de la fenêtre contextuelle Recherche en direct . Les données sont toujours transmises par GraphQL, au cas où vous souhaitez remplacer la fonctionnalité.
* ![Correction](../assets/fix.svg) - `categories` et `categoryPath` ont remplacé `categoryIds` pour le filtrage par catégorie. En savoir plus dans la section [productSearch](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/) rubrique.
* ![Correction](../assets/fix.svg) - Auparavant, un utilisateur lié à une entreprise B2B recevait un code de groupe client incorrect lors des recherches. La fonction de recherche en direct renvoie désormais la valeur correcte.
* ![Correction](../assets/fix.svg) - Auparavant, la recherche en direct renvoyait une erreur lors de la recherche d’un terme qui n’existe pas. Ce bogue est maintenant corrigé.

Les commerçants doivent mettre à niveau l’extension Live Search >= 2.0.4 pour accéder à ces fonctionnalités.

Nous conseillons aux utilisateurs de mettre à niveau et de tester avant de passer en production. Envisagez de mettre à niveau l’environnement de production pendant les heures creuses après avoir vérifié les résultats de l’environnement de test.

## [!DNL Live Search] 2.0.3 {#203}

* Compatible avec Adobe Commerce (EE) : 2.4.x
* Compatible avec Adobe Commerce for Cloud (CEE) : 2.4.x
* Stabilité : Stable

* ![Nouveau](../assets/new.svg) - La recherche en direct prend désormais en charge les fonctionnalités B2B en respectant les autorisations de catégorie, les catalogues partagés et la tarification spécifique aux groupes de clients.

Les commerçants doivent mettre à niveau l’extension Live Search >= 2.0.3 pour accéder à ces fonctionnalités.

Nous conseillons aux utilisateurs de mettre à niveau et de tester avant de passer en production. Envisagez de mettre à niveau l’environnement de production pendant les heures creuses après avoir vérifié les résultats de l’environnement de test.

## [!DNL Live Search] 2.0 {#20}

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
* ![Bogue](../assets/bug.svg) - Les attributs de produit suivants ne sont pas pris en charge par [API Magento GraphQL](https://developer.adobe.com/commerce/webapi/graphql/) lorsqu’elle est utilisée en rapport avec la version bêta de PWA : `description`, `name`, `short_description`
* ![Bogue](../assets/bug.svg) - La version bêta de PWA pour [!DNL Live Search] ne prend pas en charge [gestion des événements](https://devdocs.magento.com/shared-services/storefront-events-sdk.html).

## [!DNL Live Search] 1.3.1 {#131}

* Compatible avec Adobe Commerce (EE) : 2.4.x
* Compatible avec Adobe Commerce for Cloud (CEE) : 2.4.x
* Stabilité : Stable

* ![Correction](../assets/fix.svg) - [Attribut de prix personnalisé](https://docs.magento.com/user-guide/stores/attributes-input-types.html) ne renvoie plus d’erreur lorsqu’elle est configurée en tant que [facette]({% lien live-search/facets-add.md %}).
* ![Correction](../assets/fix.svg) - Correction d’un problème en raison duquel une erreur se produisait lorsqu’aucune [symbole de devise](https://docs.magento.com/user-guide/stores/currency-symbols.html) (`data-currency-symbol`) est disponible.
* ![Correction](../assets/fix.svg) - [[!DNL Storefront popover]](storefront-popover.md) affiche désormais la variable [Prix spécial](https://docs.magento.com/user-guide/catalog/product-price-special.html) (prix final minimum) le cas échéant.

## [!DNL Live Search] 1.3.0 {#130}

* Compatible avec Adobe Commerce (EE) : 2.4.x
* Compatible avec Adobe Commerce for Cloud (CEE) : 2.4.x
* Stabilité : Stable

* ![Nouveau](../assets/new.svg) - [Performances](performance.md) le tableau de bord des rapports fournit des informations sur les termes de recherche que les acheteurs utilisent.
* ![Nouveau](../assets/new.svg) - [!DNL Live Search] [SDK des événements Storefront](https://devdocs.magento.com/shared-services/storefront-events-sdk.html) permet d’accéder à une couche de données commune avec des services de publication et d’abonnement d’événements, ainsi que des mesures.
* ![Correction](../assets/fix.svg) - Le [[!DNL Storefront popover]](storefront-popover.md) comporte une nouvelle `active` pour la classe `.search-autocomplete` conteneur contrôlant la visibilité.
* ![Correction](../assets/fix.svg) - Sur le storefront, le [Termes de recherche](https://docs.magento.com/user-guide/marketing/search-terms-popular.html) lien de pied de page supprimé et son cache désactivé pour [!DNL Live Search] installations.
* ![Bogue](../assets/bug.svg) - Le correctif pour l’adaptateur de recherche gère les produits en double.
* ![Bogue](../assets/bug.svg) - [!DNL Live Search] prend en charge [source unique](https://docs.magento.com/user-guide/catalog/inventory-sources.html) emplacements d’inventaire (physiques) avec plusieurs emplacements (virtuels) [stocks](https://docs.magento.com/user-guide/catalog/inventory-stock.html). Pour l’instant, plusieurs sources d’inventaire ne sont pas prises en charge.

## [!DNL Live Search] 1.2.0 {#120}

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

## [!DNL Live Search] 1.1.0 {#110}

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
