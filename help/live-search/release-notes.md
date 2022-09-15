---
title: "[!DNL Live Search] Notes de mise à jour"
description: "Informations les plus récentes sur la version [!DNL Live Search] d’Adobe Commerce."
exl-id: 2a581e43-35f5-48ce-9752-844430ccdebf
source-git-commit: 07d8a80cc8afe34cd0363a7705465b5565f5c196
workflow-type: tm+mt
source-wordcount: '886'
ht-degree: 1%

---

# [!DNL Live Search] Notes de mise à jour

Ces notes de mise à jour décrivent les dernières versions de [!DNL Live Search] et incluent :

* ![Nouveau](../assets/new.svg) - Nouvelles fonctionnalités
* ![Correction](../assets/fix.svg) - Correctifs et améliorations
* ![Bogue](../assets/bug.svg) - Problèmes connus

## [!DNL Live Search] 2.0.3

* Compatible avec Adobe Commerce (EE) : 2.4.x
* Compatible avec Adobe Commerce for Cloud (CEE) : 2.4.x
* Stabilité : Stable

* ![Nouveau](../assets/new.svg) - La recherche en direct prend désormais en charge les fonctionnalités B2B en respectant les autorisations de catégorie, les catalogues partagés et la tarification spécifique aux groupes de clients.

Les commerçants doivent mettre à niveau l’extension Live Search >= 2.0.3 pour accéder à ces fonctionnalités.

Nous conseillons aux utilisateurs de mettre à niveau et de tester avant de passer en production. Envisagez de mettre à niveau l’environnement de production pendant les heures creuses après avoir vérifié les résultats de l’environnement de test.

>[!NOTE]
>
>La prise en charge B2B sera ajoutée par étapes à partir du 9 août sur les services principaux, avec une migration prévue pour la fin du mois d’août. Si l’extension Live Search n’est pas mise à niveau, votre vitrine continuera à fonctionner normalement, mais sans fonctionnalités B2B.

### Limites connues/bogues :

* ![Bogue](../assets/bug.svg) - Les suggestions sont issues de produits qui ne peuvent pas être affichés pour le groupe de clients.
* ![Bogue](../assets/bug.svg) - Les produits ne s’affichent pas s’ils ne sont pas ajoutés au &quot;catalogue partagé par défaut&quot;.
* La version B2B avec la recherche en direct pour le PWA Studio ne sera pas disponible tant que PWA Studio n’y aura pas ajouté la prise en charge.
* Les remplacements de produits et le flux d’attributs de produit peuvent présenter des problèmes de synchronisation nécessitant l’exécution des administrateurs. `bin/magento indexer:reset` et `bin/magento indexer:reindex` pour effectuer une synchronisation correcte.
* Si vous activez ou désactivez les fonctionnalités Autorisations du catalogue/Catalogue partagé/B2B, la variable `productOverrides` les indexeurs ne sont pas mis à jour et sont incorrectement marqués comme &quot;valides&quot;. Utilisation `bin/magento saas:resync --feed=productOverrides` pour résoudre le problème.

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
