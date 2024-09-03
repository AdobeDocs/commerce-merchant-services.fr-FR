---
title: '[!DNL SaaS Data Export Extension] Notes de mise à jour'
description: Les dernières informations de mise à jour de [!DNL Data Export Extension] pour Adobe Commerce.
feature: Services, Release Notes
recommendations: noCatalog
exl-id: 0c7aeeda-e8a6-4740-b466-0661a6d2df07
source-git-commit: 915f6c5580f2976edde6609b8fd1c0ba4b09aade
workflow-type: tm+mt
source-wordcount: '670'
ht-degree: 0%

---

# Notes de mise à jour de l’extension [!DNL SaaS Data Export]

Ces notes de mise à jour décrivent les dernières versions de l’extension [!DNL SaaS data export]. La prise en charge de la version majeure actuelle est fournie. Les notes de mise à jour des versions antérieures sont fournies à titre de référence.

Les mises à jour sont les suivantes :

![New](../assets/new.svg) Nouvelles fonctionnalités
![ Correctifs et améliorations ](../assets/fix.svg)
![Bug](../assets/bug.svg) Problèmes connus


>[!NOTE]
>
>L’extension d’exportation de données SaaS est un ensemble de modules installés automatiquement avec Live Search, Product Recommendations et le service de catalogue. Vous pouvez vérifier la version installée sur votre système à l’aide du compositeur. Dans certains cas, vous souhaiterez peut-être mettre à niveau l’extension d’exportation des données sur votre système afin de récupérer des correctifs ou de nouvelles fonctionnalités sans mettre à jour la version du service Commerce.

## Version majeure actuelle

## Version 103.3.10

![Correction](../assets/fix.svg) Correction d’une filtration multi-vues de stockage pour le flux d’options personnalisées des produits. <!--MDEE-842-->
![Fix](../assets/fix.svg) Les flux non valides ne sont pas renvoyés tant que la valeur de hachage du flux n’a pas été modifiée.<!--MDEE-848-->

## Version 103.3.9

![Correctif](../assets/fix.svg) Lorsqu’une entité est supprimée, l’indicateur `deleted` est désormais propagé pour les flux de service de définition de la portée pour le site web (`scopesWebsite`) et le groupe de clients (`scopesCustomerGroup`).<!--MDEE-839-->

## Version 103.3.8

![Correctif](../assets/fix.svg) Les options de configuration désactivées ne sont plus exportées en tant qu’options actives.<!--MDEE-812-->
![Correctif](../assets/fix.svg) Les options et valeurs sont désormais mises à jour sur un produit configurable lorsque des modifications sont apportées à un produit enfant. <!--MDEE-835-->
![Nouveau](../assets/new.svg) Ajout de la possibilité d’inclure des données d’attributs système supplémentaires dans le flux d’attributs de produit.

## Version 103.3.7

![Fix](../assets/fix.svg) Suppression des dépendances inutiles du module InventoryDataExporter.
![Correctif](../assets/fix.svg) Modification des versions requises pour les modules d’inventaire inclus dans le module CatalogInventoryDataExporter afin de prendre en charge la version 2.4.4 d’Adobe Commerce.

## Version 103.3.6

![Fix](../assets/fix.svg) Correction des blocages qui se produisaient lors de la réindexation des flux en mode multi-thread. Les requêtes sont désormais séparées en opérations d’insertion et de mise à jour.
![Fix](../assets/fix.svg) Optimisation de la requête des prix pour les catalogues volumineux comportant de nombreux sites web.
![Nouveau](../assets/new.svg) Ajout d’une logique de nouvelle tentative pour exécuter à nouveau les transactions en échec lorsque des blocages se produisent.

## Version 103.3.5

![Correctif](../assets/fix.svg) Définissez la dépendance pour la dernière version d’exportation de données compatible pour le module commun SaaS.

![Fix](../assets/fix.svg) Remplacé l’instance `ScopeConfig` par `ServiceConfigInterface` pour prendre en charge différentes configurations de service.

## Version 103.3.4

![Correctif](../assets/fix.svg) Ajout de la prise en charge de la journalisation de l’audit de transfert de données en ajoutant un mécanisme pour distribuer un événement `data_sent_outside` chaque fois que des données sont transmises de l’instance Commerce à un service Commerce <!--MDEE-785-->

## Version 103.3.3

![New](../assets/new.svg) L’exportation de données SaaS met désormais en cache les attributs Entity-Attribute-Value (EAV) pour la requête de métadonnées d’attribut.

![Correctif](../assets/fix.svg) Correction d’un problème en raison duquel le flux `InventoryStockStatus` n’était pas enregistré lors d’une nouvelle tentative si le produit était supprimé.

## Version 103.3.2

![Correctif](../assets/fix.svg) Correction d’un problème en raison duquel le champ `modifiedAt` manquait dans les flux d’entités supprimés.

## Version 103.3.1

![Correctif](../assets/fix.svg) Correction d’un problème en raison duquel un message `Invalid Template File` s’affichait lors de la réindexation des flux de produits lors de l’installation de Page Builder.

## Version 103.3.0

![New](../assets/new.svg) Migration immédiate des tables de flux d’exportation vers la structure unifiée :
`id`, `source_entity_id`, `feed_id`, `modified_at`, `is_deleted`, `status`, `feed_data`, `feed_hash`, `errors`

![Nouveau](../assets/new.svg) Flux de catalogue et d’inventaire migrés vers la solution d’exportation immédiate.

![Nouveau](../assets/new.svg) Modification du nom des tâches cron-jobs de flux d’exportation immédiate en `*_feed_resend_failed_items`.

![Nouveau](../assets/new.svg) Flux d’exportation immédiate renommés, identifiants d’affichage des indexeurs et modification des tables de logs.
- tables de flux (et identifiants de vue indexeur) :
   - `catalog_data_exporter_products` -> `cde_products_feed`
   - `catalog_data_exporter_product_attributes` -> `cde_product_attributes_feed`
   - `catalog_data_exporter_categories` -> `cde_categories_feed`
   - `catalog_data_exporter_product_prices` -> `cde_product_prices_feed`
   - `catalog_data_exporter_product_variants` -> `cde_product_variants_feed`
   - `inventory_data_exporter_stock_status` -> `inventory_data_exporter_stock_status_feed`
- change les noms des tables de logs : suit le même modèle de nommage que les tables de flux, mais modifier les noms des tables de logs ajoute un suffixe `_cl`.  Par exemple `catalog_data_exporter_products_cl`-> `cde-products_feed_cl`
Si vous disposez d’un code personnalisé qui référence l’une de ces entités, mettez à jour les références avec les nouveaux noms afin de vous assurer que votre code continue à fonctionner correctement.

![Correctif](../assets/fix.svg) Définissez le champ `modified_at` dans les données de flux uniquement pour les flux qui en ont besoin.

![Fix](../assets/fix.svg) Modifiez la requête `productAttributes` pour récupérer uniquement les attributs de produit.

## Version 103.2.6

![Correctif](../assets/fix.svg) Correction d’un problème qui empêchait la réindexation des flux lorsque les tables contenaient un préfixe.

## Version 103.2.5

![Fix](../assets/fix.svg) Optimisation de la requête Price.

## Version 103.2.4

![Correctif](../assets/fix.svg) Correction d’un état Stock incorrect qui s’affichait pour un produit lorsque Commerce Inventory management était activé.

## Version 103.2.3

![Correctif](../assets/fix.svg) Correction des prix spéciaux au niveau du site web.
![Correctif](../assets/fix.svg) Ajout d’un mutex pour tous les flux qui sont traités.


## Version 103.2.2

![Correctif](../assets/fix.svg) Amélioration de la stratégie de traitement par lot des flux pour les catalogues volumineux. Le tableau des lots est maintenant rempli avec un nombre limité d’identifiants afin de réduire l’utilisation de la mémoire.

![Fix](../assets/fix.svg) Suppression de la dépendance irréversible de CommerceInventoryDataExporter aux modules MSI.

![Correctif](../assets/fix.svg) Amélioration des `commerce-data-exporter` journaux pour collecter plus d’informations et les organiser par différentes étapes d’exportation.

## Version 103.2.1

- Version mise à jour publiée.

## Version 103.2.0

- Ajout d’une synchronisation des données à plusieurs threads pour les produits et les prix.
