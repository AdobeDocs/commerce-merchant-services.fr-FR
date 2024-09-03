---
title: '[!DNL Catalog Service] Notes de mise à jour'
description: Les dernières informations de mise à jour de [!DNL Catalog Service] pour Adobe Commerce.
exl-id: 9bf8e3f7-5b74-4755-867e-ac1c5000ff33
feature: Services, Catalog Service, Release Notes
source-git-commit: 58d5abf84a190b203661606c439beb088b7ee20d
workflow-type: tm+mt
source-wordcount: '765'
ht-degree: 0%

---

# Notes de mise à jour [!DNL Catalog Service]

Ces notes de mise à jour décrivent les dernières versions de [!DNL Catalog Service].
La prise en charge de la version majeure actuelle est fournie. Les notes de mise à jour des versions antérieures sont fournies à titre de référence.
Les mises à jour sont les suivantes :

![New](../assets/new.svg) Nouvelles fonctionnalités
![ Correctifs et améliorations ](../assets/fix.svg)
![Bug](../assets/bug.svg) Problèmes connus

## Version majeure actuelle

### Version 1.22

_13 août 2024_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) Ajout de la prise en charge de la récupération de toutes les variantes par SKU du produit. Voir la [référence de l’API Catalog Service](https://developer.adobe.com/commerce/services/graphql/catalog-service/). <!--DATA-6067-->


## Versions précédentes

+++ Versions précédentes

### Version 1.19

_23 mai 2024_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}


![Fix](../assets/fix.svg) <!--DATA-5033-->L’indicateur `InStock` pour les valeurs d’option prend désormais en compte l’état `enabled` de portée de la variante de produit.

![Correctif](../assets/fix.svg) <!--DATA-5888--> Ajoutez la prise en charge des prix des produits qui nécessitent des nombres élevés (jusqu’à 16 chiffres) et une précision décimale supérieure (jusqu’à 4 décimales). Pour appliquer les mises à jour de configuration des prix à votre catalogue existant, resynchronisez les données du catalogue à partir du [tableau de bord de Data Management](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard), ou à l’aide de l’[interface de ligne de commande Adobe Commerce](../landing/catalog-sync.md#command-line-interface).

#### Limites connues

Les fonctionnalités suivantes ne sont pas encore prises en charge :

* La taille maximale de la charge utile des attributs dynamiques est de 9 Mo.
* Le prix du produit Groupe peut être calculé à partir de prix simples.
* Dans un tableau d’images, seule la première image contient des rôles.

Résolvez les limites suivantes en utilisant le maillage d’API et l’API Core GraphQL :

* Prix publicitaire minimal
* Prix de niveau
* Produits groupés avec prix fixes

Pour plus d’informations et d’exemples, voir [Service de catalogue et Mesh API](mesh.md)

### Version 1.18

_11 avril 2024_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) Prise en charge de PHP 8.3.

![Nouveau](../assets/new.svg) Les requêtes [`products`](https://developer.adobe.com/commerce/services/graphql/catalog-service/products/) et [`refineProduct`](https://developer.adobe.com/commerce/services/graphql/catalog-service/refine-product/) renvoient désormais des données d’options personnalisables pour les produits simples et complexes.<!--DATA-5538-->

### Version 1.17

_22 février 2024_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) [[!DNL Data Management Dashboard]](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-dashboard.html) est désormais disponible. Ce tableau de bord repensé fournit des informations sur les flux de données pour [!DNL Product Recommendations], [!DNL Live Search] et [!DNL Catalog Service]. La prise en charge de cette fonctionnalité a été introduite dans la version 3.1.0 du métappackage `catalog-service`.

### Version 1.16

_13 février 2024_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouvelles](../assets/new.svg) Les vidéos de produit sont désormais prises en charge par l’API Catalog Service.
![Correctif](../assets/fix.svg) Les options en rupture de stock sont désormais affichées dans le widget PDP.

#### Limites connues

Ces fonctionnalités ne sont pas encore prises en charge :

* La taille maximale de la charge utile des attributs dynamiques est de 9 Mo.
* Prix du produit de groupe. Cette valeur peut être calculée avec des prix de produit simples.
* Dans un tableau d’images, seule la première image contient des rôles.

Les limites suivantes peuvent être résolues à l’aide du Mesh de l’API et de l’API Core GraphQL :

* Prix publicitaire minimal
* [Prix de niveau](mesh.md)

### Version 1.13

_12 octobre 2023_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![New](../assets/new.svg) Catalog Service prend en charge l’indicateur `inStock` pour les variantes de produits.
![Nouveau](../assets/new.svg) Les champs `urlKey` et `externalId` ont été ajoutés au schéma GraphQL.
![Nouveaux](../assets/new.svg) Les produits téléchargeables et les cartes-cadeaux sont désormais pris en charge.

### Version 1.12

_19 septembre 2023_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) Le service de catalogue utilise désormais l’ [indexation de prix SaaS](../price-index/price-indexing.md).
![Correctif](../assets/fix.svg) Cette version contient des correctifs et des améliorations du côté service.

### Version 1.11

_18 juillet 2023_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![New](../assets/new.svg) Catalog Service prend désormais en charge la requête GraphQL [`recommendations`](https://developer.adobe.com/commerce/services/graphql/recommendations/recommendations/) pour Product Recommendations.

### Version 1.10

_27 juin 2023_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) L’API Catalog Service prend désormais en charge `related products`.

### Version V1.7

_12 avril 2023_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![New](../assets/new.svg) Le service de catalogue nettoie désormais les variantes de produits supprimées.
![Correctif](../assets/fix.svg) Améliorations de l’évolutivité de l’infrastructure et des performances.

### Version V1.6

_28 mars 2023_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![New](../assets/new.svg) Ajout d’échantillons à la requête [`products`](https://developer.adobe.com/commerce/services/graphql/catalog-service/products/).
![New](../assets/new.svg) Ajout de la possibilité d’obtenir `entityId` à l’aide de [l’API Mesh](mesh.md).

### Version V1.5

_6 mars 2023_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) Ajout de la fonctionnalité [`categories`](https://developer.adobe.com/commerce/services/graphql/catalog-service/categories/) de GraphQL.
![Correctif](../assets/fix.svg) Amélioration des performances et de l’évolutivité des API.

### Version V1.4

_7 février 2023_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) Métapackage de service-catalogue publié pour simplifier les étapes d’installation.
Améliorations des performances et de l’évolutivité de l’API ![Fix](../assets/fix.svg).

### Version V1.3

_17 janvier 2023_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) Simplification et amélioration de l’expérience d’intégration.
![Nouveau](../assets/new.svg) De nouveaux points d’entrée sandbox client sont disponibles pour les tests de pré-production.
![Nouveau](../assets/new.svg) Ajout de la prise en charge des produits virtuels.
Améliorations des performances et de l’évolutivité de l’API ![Fix](../assets/fix.svg).

### Version V1.1

_18 novembre 2022_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) Le service de catalogue prend désormais en charge le [Mesh API](https://developer.adobe.com/graphql-mesh-gateway/) de l’Adobe.
![Correctif](../assets/fix.svg) Amélioration de l’évolutivité de l’API et des performances globales.

### Version V1.0

_4 octobre 2022_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) prend désormais en charge les produits regroupés et regroupés.
![Nouveau](../assets/new.svg) Ajout de remplacements de visibilité B2B. Les produits peuvent désormais faire l’objet de recherches et peuvent être ajoutés au panier pour des groupes de clients spécifiques.
![Fix](../assets/fix.svg) Le service est désormais plus stable et offre de meilleures performances.

### Version 0.3 - Beta+

_12 septembre 2022_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![New](../assets/new.svg) Images pour la prise en charge des variantes : les images de produit sont renvoyées en fonction des options sélectionnées
![Nouveaux ](../assets/new.svg) rôles pour la prise en charge des prix : permettent uniquement aux membres de groupes de clients spécifiques de voir le prix des produits
![Correctif](../assets/fix.svg) Amélioration de la stabilité et des performances du service
![Nouvelles](../assets/new.svg) Des mises à jour sont reçues lorsque des produits sont supprimés du catalogue.

### Version de Beta

_9 août 2022_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![New](../assets/new.svg) Les requêtes `products` et `refineProduct` renvoient les données suivantes :

* Attributs de produit prédéfinis (système).
* Attributs de produit dynamiques et filtrez-les par rôle (page d’affichage de produit/page de liste de produits).
* Options du produit.
* Images de produit et filtrez-les par rôle (PDP/PLP).
* Un prix spécifique pour les produits simples et des plages de prix pour les produits configurables.
* Prix des groupes clients et plages de prix. Ils renvoient un prix par défaut de secours aux acheteurs sans groupe de clients.
* Types de produits qui utilisent la tarification spécifique aux clients B2B.
