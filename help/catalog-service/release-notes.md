---
title: '''[!DNL Catalog Service] Notes de mise à jour d’'
description: Les dernières informations de mise à jour pour [!DNL Catalog Service] pour Adobe Commerce.
exl-id: 9bf8e3f7-5b74-4755-867e-ac1c5000ff33
feature: Services, Catalog Service, Release Notes
source-git-commit: a439df188f72d17a6a41fa248aa9957aaabd9e02
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---

# [!DNL Catalog Service] Notes de mise à jour

Ces notes de mise à jour décrivent les dernières versions de [!DNL Catalog Service].
La prise en charge de la version majeure actuelle est fournie. Les notes de mise à jour des versions antérieures sont fournies à titre de référence.
Les mises à jour sont les suivantes :

![Nouveau](../assets/new.svg) Nouvelles fonctionnalités
![Correction](../assets/fix.svg) Correctifs et améliorations
![Bogue](../assets/bug.svg) Problèmes connus

## Version majeure actuelle

### Version 1.17

_22 février 2023_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) La variable [[!DNL Data Management Dashboard]](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-dashboard.html) est désormais disponible. Ce tableau de bord restructuré fournit des informations sur les flux de données pour [!DNL Product Recommendations], [!DNL Live Search], et [!DNL Catalog Service]. La prise en charge de cette fonctionnalité a été introduite dans la version 3.1.0 du `catalog-service` métapackage.

## Versions précédentes

+++ Versions précédentes

### Version 1.16

_13 février 2023_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) Les vidéos de produit sont désormais prises en charge par l’API Catalog Service.
![Correction](../assets/fix.svg) Les produits groupés avec des prix fixes sont désormais pris en charge.
![Correction](../assets/fix.svg) Les options en rupture de stock s’affichent désormais dans le widget PDP.

#### Limites connues

Ces fonctionnalités ne sont pas encore prises en charge :

* La taille maximale de la charge utile des attributs dynamiques est de 9 Mo.
* Prix du produit de groupe. Peuvent être calculées avec des prix de produit simples.
* Dans un tableau d’images, seule la première image contient des rôles.

Les limites suivantes peuvent être résolues à l’aide du maillage de l’API et de l’API Core GraphQL :

* Prix publicitaire minimal
* [Prix de niveau](mesh.md)

### Version 1.13

_12 octobre 2023_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) Le service de catalogue prend en charge la variable `inStock` Indicateur pour les variantes de produits.
![Nouveau](../assets/new.svg) `urlKey` et `externalId` ont été ajoutés au schéma GraphQL.
![Nouveau](../assets/new.svg) Les produits téléchargeables et les cartes-cadeaux sont désormais pris en charge.

### Version 1.12

_19 septembre 2023_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) Le service de catalogue utilise désormais [Indexation des prix SaaS](../price-index/price-indexing.md).
![Correction](../assets/fix.svg) Cette version contient des correctifs et des améliorations du côté service.

### Version 1.11

_18 juillet 2023_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) Le service de catalogue prend désormais en charge la variable [`recommendations`](https://developer.adobe.com/commerce/services/graphql/recommendations/recommendations/) Requête GraphQL pour le Recommendations de produit.

### Version 1.10

_27 juin 2023_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) L’API Catalog Service prend désormais en charge les &quot;produits associés&quot;.

### Version V1.7

_12 avril 2023_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) Le service de catalogue nettoie désormais les variantes de produits supprimées.
![Correction](../assets/fix.svg) Évolutivité de l’infrastructure et améliorations des performances.

### Version V1.6

_28 mars 2023_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) Ajout d’échantillons aux [`products`](https://developer.adobe.com/commerce/services/graphql/catalog-service/products/) requête.
![Nouveau](../assets/new.svg) Ajout de la possibilité d’obtenir `entityId` using [Mesh de l’API](mesh.md).

### Version V1.5

_6 mars 2023_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) Ajout [`categories`](https://developer.adobe.com/commerce/services/graphql/schema/catalog-service/categories/) Fonctionnalité de GraphQL.
![Correction](../assets/fix.svg) Amélioration des performances et de l’évolutivité des API.

### Version V1.4

_7 février 2023_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) Mise en page du métaphorage du service de catalogue pour simplifier les étapes d’installation.
![Correction](../assets/fix.svg) Améliorations de l’évolutivité et des performances des API.

### Version V1.3

_17 janvier 2023_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) Simplification et amélioration de l’intégration.
![Nouveau](../assets/new.svg) De nouveaux points de terminaison d’environnement de test client sont disponibles pour les tests de pré-production.
![Nouveau](../assets/new.svg) Ajout de la prise en charge des produits virtuels
![Correction](../assets/fix.svg) Améliorations de l’évolutivité et des performances des API.

### Version V1.1

_18 novembre 2022_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) Le service de catalogue prend désormais en charge les Adobes [Mesh de l’API](https://developer.adobe.com/graphql-mesh-gateway/).
![Correction](../assets/fix.svg) Amélioration de l’évolutivité des API et des performances globales.

### Version V1.0

_4 octobre 2022_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) Prise en charge des produits regroupés et regroupés.
![Nouveau](../assets/new.svg) Ajout de remplacements de visibilité B2B. Les produits peuvent désormais faire l’objet de recherches et peuvent être ajoutés au panier pour des groupes de clients spécifiques.
![Correction](../assets/fix.svg) Le service est désormais plus stable et offre de meilleures performances.

### Version 0.3 - Bêta+

_12 septembre 2022_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) Prise en charge des images pour les variantes : les images de produit sont renvoyées en fonction des options sélectionnées.
![Nouveau](../assets/new.svg) Rôles de prise en charge des prix : permettent uniquement aux membres de groupes de clients spécifiques de voir le prix des produits.
![Correction](../assets/fix.svg) Stabilité et performances améliorées du service
![Nouveau](../assets/new.svg) Des mises à jour sont reçues lorsque des produits sont supprimés du catalogue.

### Version bêta

_9 août 2022_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) La variable `products` et `refineProduct` les requêtes renvoient les données suivantes :

* Attributs de produit prédéfinis (système).
* Attributs de produit dynamiques et filtrez-les par rôle (page d’affichage de produit/page de liste de produits).
* Options du produit.
* Images de produit et filtrez-les par rôle (PDP/PLP).
* Un prix spécifique pour les produits simples et des plages de prix pour les produits configurables.
* Prix des groupes clients et plages de prix. Ils renvoient un prix par défaut de secours aux acheteurs sans groupe de clients.
* Types de produits qui utilisent la tarification spécifique aux clients B2B.

+++
