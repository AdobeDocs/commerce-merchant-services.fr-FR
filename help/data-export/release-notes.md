---
title: '[!DNL SaaS Data Export Extension] Notes de mise à jour'
description: Les dernières informations de mise à jour de [!DNL Data Export Extension] pour Adobe Commerce.
feature: Services, Release Notes
recommendations: noCatalog
exl-id: 0c7aeeda-e8a6-4740-b466-0661a6d2df07
source-git-commit: 051e558f9aa9760c2d6e993713e49a5997270f1b
workflow-type: tm+mt
source-wordcount: '498'
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

![Correctif](../assets/fix.svg) Améliorer la journalisation de l’exportation des données SaaS Commerce en ajoutant plus de détails sur le processus de réindexation.

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

![Nouveau](../assets/new.svg) Modification du flux d’exportation immédiat et modification des tables de logs.

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
