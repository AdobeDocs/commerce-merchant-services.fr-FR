---
title: Service d’ingestion de flux
description: En savoir plus sur le service d’ingestion de flux pour Adobe Commerce
source-git-commit: 12b1e89924a2eb89494bcb884fc3bc14e87b2b1c
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---


# Service d’ingestion de flux

>[!NOTE]
>
>Le service d’ingestion de flux est actuellement en version bêta privée. Il n’est pas encore disponible pour une utilisation générale.

Le service d’ingestion des flux réduit le temps nécessaire au traitement des modifications de produits (mises à jour des prix, ajout de nouveaux attributs) en contournant l’instance Adobe Commerce et en déplaçant les données de catalogue d’un ERP (Enterprise Resource Planning) tiers directement vers les services Adobe Commerce.

Ce service est destiné aux clients qui stockent et gèrent leur catalogue de produits dans un système externe à l’application Adobe Commerce principale.

Les clients qui disposent de catalogues complexes et volumineux ou qui reçoivent de fréquentes mises à jour craignent que les nouvelles données ne prennent plus de temps que prévu pour apparaître dans le magasin en ligne. Puisque le service de catalogue sait quelles données il doit traiter ces mises à jour, il n’est pas nécessaire d’envoyer les données par l’intermédiaire du produit Commerce principal, mais elles doivent être transférées au service de catalogue. La suppression de cette étape intermédiaire est l’endroit où des gains d’efficacité sont constatés.

## Flux d’ingestion

Selon la configuration d’Adobe Commerce, le stockage des données et les flux de données peuvent emprunter différents chemins.

* Dans une instance Adobe Commerce standard, le catalogue de produits est stocké dans la base de données principale.
* Lors de l’utilisation des services Adobe Commerce, les données du catalogue sont copiées de la base de données principale vers le service et sont traitées et diffusées à partir de là.
* Lors du stockage de données de catalogue dans un système tiers (ERP, MDM, PIM), les données transitent par l’application Commerce principale, puis par les services Commerce.
* Avec le service d’ingestion de flux, les données de produit passent directement du système tiers à l’infrastructure de services de commerce.

![Service d’ingestion de flux](assets/feed-ingestion.png)

En contournant l’application Commerce principale et en déplaçant les données directement vers les services Commerce, les mises à jour de produit sont répercutées plus rapidement dans le magasin. Les données de catalogue principales, telles que les SKU, sont envoyées à l’application Commerce principale pour un traitement distinct.

## Rejoindre la version bêta

Le service d’ingestion de flux est conçu pour :

* Clients de moyenne entreprise avec implémentations sans interface utilisateur
* Clients disposant de catalogues volumineux et complexes
* Clients n’utilisant pas l’administrateur Adobe Commerce pour gérer les données de catalogue, mais utilisant un système ERP ou tiers pour gérer les données de catalogue

Si vous souhaitez rejoindre le programme bêta, contactez l’équipe à l’adresse sagonzal@adobe.com.
