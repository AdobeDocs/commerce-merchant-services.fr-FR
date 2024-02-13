---
title: Service d’ingestion de flux
description: En savoir plus sur le service d’ingestion de flux pour Adobe Commerce
exl-id: bb5aec74-faca-42ec-9fdb-3261677d451e
source-git-commit: d3798efa038c35f71bb0bb6874d954a8e66c7467
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# Service d’ingestion de flux

Le service d’ingestion de flux permet aux clients disposant de catalogues volumineux et/ou complexes d’envoyer directement des données aux services Adobe Commerce.

Le service d’ingestion des flux réduit le temps nécessaire au traitement des modifications de produits (mises à jour des prix, ajout de nouveaux attributs) en contournant l’instance Adobe Commerce et en déplaçant les données de catalogue d’un ERP (Enterprise Resource Planning) tiers directement vers les services Adobe Commerce.

Ce service est destiné aux clients qui stockent et gèrent leur catalogue de produits dans un système externe à l’application Adobe Commerce principale. Il est fourni sous la forme d’une API, de sorte que les clients puissent l’intégrer à leurs systèmes existants, ce qui offre une plus grande flexibilité dans la manière dont il est déployé.

Les clients qui disposent de catalogues complexes et volumineux ou qui reçoivent de fréquentes mises à jour craignent que les nouvelles données ne prennent plus de temps que prévu pour apparaître dans le magasin en ligne. Puisque le service de catalogue sait quelles données il doit traiter ces mises à jour, il n’est pas nécessaire d’envoyer les données par l’intermédiaire du produit Commerce principal, mais elles doivent être transférées au service de catalogue. La suppression de cette étape intermédiaire est l’endroit où des gains d’efficacité sont constatés.

## Flux d’ingestion

Selon la configuration d’Adobe Commerce, le stockage des données et les flux de données peuvent emprunter différents chemins.

* Dans une instance Adobe Commerce standard, le catalogue de produits est stocké dans la base de données principale.
* Lors de l’utilisation des services Adobe Commerce, les données du catalogue sont copiées de la base de données principale vers le service et sont traitées et diffusées à partir de là.
* Lors du stockage de données de catalogue dans un système tiers (ERP, MDM, PIM), les données transitent par l’application Commerce principale, puis par les services Commerce.
* Avec le service d’ingestion de flux, les données de produit passent directement du système tiers à l’infrastructure de services de commerce.

![Service d’ingestion de flux](assets/feed-ingestion.png)

En contournant l’application Commerce principale et en déplaçant les données directement vers les services Commerce, les mises à jour de produit sont répercutées plus rapidement dans le magasin. Les données de catalogue principales, telles que les SKU, sont envoyées à l’application Commerce principale pour un traitement distinct.

## API

La variable [Documentation de l’API Feed Ingestion Service](https://developer.adobe.com/commerce/services/feed-ingestion) fournit des détails sur la mise en oeuvre du service.
