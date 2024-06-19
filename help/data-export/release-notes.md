---
title: "[!DNL SaaS Data Export Extension] Notes de mise à jour"
description: Les dernières informations de mise à jour pour [!DNL Data Export Extension] pour Adobe Commerce.
feature: Services, Release Notes
recommendations: noCatalog
source-git-commit: 8230756c203cb2b4bdb4949f116c398fcaab84ff
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# [!DNL SaaS Data Export] Notes de mise à jour d’extension

Ces notes de mise à jour décrivent les dernières versions des [!DNL SaaS data export] extension . La prise en charge de la version majeure actuelle est fournie. Les notes de mise à jour des versions antérieures sont fournies à titre de référence.

Les mises à jour sont les suivantes :

![Nouveau](../assets/new.svg) Nouvelles fonctionnalités
![Correction](../assets/fix.svg) Correctifs et améliorations
![Bogue](../assets/bug.svg) Problèmes connus


>[!NOTE]
>
>L’extension d’exportation de données SaaS est un ensemble de modules installés automatiquement avec Live Search, Product Recommendations et le service de catalogue. Vous pouvez vérifier la version installée sur votre système à l’aide du compositeur. Dans certains cas, vous souhaiterez peut-être mettre à niveau l’extension d’exportation des données sur votre système afin de récupérer des correctifs ou de nouvelles fonctionnalités sans mettre à jour la version du service Commerce.

## Version majeure actuelle

## Version 103.3.5

![Correction](../assets/fix.svg) Définissez la dépendance pour la dernière version d’exportation des données compatible pour le module commun SaaS.

![Correction](../assets/fix.svg) Remplacé `ScopeConfig` instance avec `ServiceConfigInterface` pour prendre en charge différentes configurations de service.

## Version 103.3.4

![Correction](../assets/fix.svg) Améliorez la journalisation de l’exportation des données SaaS Commerce en ajoutant des détails supplémentaires sur le processus de réindexation.

## Version 103.3.3

![Nouveau](../assets/new.svg) L’exportation de données SaaS met désormais en cache les attributs Entity-Attribute-Value (EAV) pour la requête de métadonnées d’attribut.

![Correction](../assets/fix.svg) Correction d’un problème en raison duquel la variable `InventoryStockStatus` le flux n’a pas été enregistré à la reprise si le produit a été supprimé.

## Version 103.3.2

![Correction](../assets/fix.svg) Correction d’un problème en raison duquel la variable `modifiedAt` était absent des flux d’entités supprimés.

## Version 103.3.1

![Correction](../assets/fix.svg) Correction d’un problème qui provoquait une erreur `Invalid Template File` message s’affichant lors de la réindexation des flux de produits lors de l’installation de Page Builder.

## Version 103.3.0

![Nouveau](../assets/new.svg) Migration des tables de flux d’exportation immédiate vers la structure unifiée :
`id`, `source_entity_id`, `feed_id`, `modified_at`, `is_deleted`, `status`, `feed_data`, `feed_hash`, `errors`

![Nouveau](../assets/new.svg) Flux de catalogue et d’inventaire migrés vers la solution d’exportation immédiate.

![Nouveau](../assets/new.svg) Changement du nom des tâches cron du flux d’exportation immédiate en `*_feed_resend_failed_items`.

![Nouveau](../assets/new.svg) Modification du flux d’exportation immédiat et des tables de logs.

![Correction](../assets/fix.svg) Définir `modified_at` dans les données de flux uniquement pour les flux qui en ont besoin.

![Correction](../assets/fix.svg) Modifiez la variable `productAttributes` requête pour récupérer uniquement les attributs de produit.

## Version 103.2.6

![Correction](../assets/fix.svg) Correction d’un problème qui empêchait la réindexation des flux lorsque les tables contenaient un préfixe.

## Version 103.2.5

![Correction](../assets/fix.svg) Optimisation de la requête Price.

## Version 103.2.4

![Correction](../assets/fix.svg) Correction d’un état Stock incorrect qui s’affichait pour un produit lorsque Commerce Inventory management était activé.

## Version 103.2.3

![Correction](../assets/fix.svg) Correction des prix spéciaux au niveau du site web.
![Correction](../assets/fix.svg) Ajout d’un mutex pour tous les flux qui sont traités.


## Version 103.2.2

![Correction](../assets/fix.svg) Amélioration de la stratégie de traitement par lot des flux pour les catalogues volumineux. Le tableau des lots est maintenant rempli avec un nombre limité d’identifiants afin de réduire l’utilisation de la mémoire.

![Correction](../assets/fix.svg) Suppression de la dépendance irréversible de CommerceInventoryDataExporter aux modules MSI.

![Correction](../assets/fix.svg) Amélioré `commerce-data-exporter` logs pour collecter plus d&#39;informations et les organiser par différentes étapes d&#39;export.

## Version 103.2.1

- Version mise à jour publiée.

## Version 103.2.0

- Ajout d’une synchronisation des données à plusieurs threads pour les produits et les prix.

