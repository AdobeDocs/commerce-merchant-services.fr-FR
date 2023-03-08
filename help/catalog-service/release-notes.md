---
title: '''[!DNL Catalog Service] Notes de mise à jour de'
description: Les dernières informations de mise à jour pour [!DNL Catalog Service] pour Adobe Commerce.
exl-id: 9bf8e3f7-5b74-4755-867e-ac1c5000ff33
source-git-commit: 40cf5c5dc6242b5efe3822b9c574fe5b219cfcd8
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# [!DNL Catalog Service] Notes de mise à jour

Ces notes de mise à jour décrivent les dernières versions de [!DNL Catalog Service] et incluent :

![Nouveau](../assets/new.svg) Nouvelles fonctionnalités
![Correction](../assets/fix.svg) Correctifs et améliorations
![Bogue](../assets/bug.svg) Problèmes connus

## Version majeure actuelle

### Version V1.5

_6 mars 2023_

[!BADGE Compatibilité]{type=Informative tooltip="Compatibilité"}

![Nouveau](../assets/new.svg) Ajout [`categories`](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/categories/) Fonctionnalité de GraphQL.
![Correction](../assets/fix.svg) Amélioration des performances et de l’évolutivité des API.

#### Limites connues

Ces fonctionnalités ne sont pas encore prises en charge :

* Produits groupés avec prix fixe
* Aucune mise à jour n’est reçue lorsque les variantes sont supprimées du catalogue.
* La taille maximale de la charge utile des attributs dynamiques est de 9 Mo.
* Prix du produit de groupe. Peuvent être calculées avec des prix de produit simples.
* Dans un tableau d’images, seule la première image contient des rôles.
* Échantillons de couleurs
* Chargement de la page Détails du produit via l’URL du produit.

Les restrictions suivantes peuvent être résolues à l’aide de l’API Core GraphQL :

* Prix publicitaire minimal
* Prix de niveau
* Produits téléchargeables et cartes-cadeaux

### Version V1.4

_7 février 2023_

[!BADGE Compatibilité]{type=Informative tooltip="Compatibilité"}

![Nouveau](../assets/new.svg) Mise en page du métaphorage du service de catalogue pour simplifier les étapes d’installation.
![Correction](../assets/fix.svg) Améliorations de l’évolutivité et des performances des API.

### Version V1.3

_17 janvier 2023_

[!BADGE Compatibilité]{type=Informative tooltip="Compatibilité"}

![Nouveau](../assets/new.svg) Simplification et amélioration de l’expérience d’intégration.
![Nouveau](../assets/new.svg) De nouveaux points de terminaison d’environnement de test client sont disponibles pour les tests de pré-production.
![Nouveau](../assets/new.svg) Ajout de la prise en charge des produits virtuels.
![Correction](../assets/fix.svg) Améliorations de l’évolutivité et des performances des API.

### Version V1.1

_18 novembre 2022_

[!BADGE Compatibilité]{type=Informative tooltip="Compatibilité"}

![Nouveau](../assets/new.svg) Le service de catalogue prend désormais en charge les Adobes [Mesh de l’API](https://developer.adobe.com/graphql-mesh-gateway/).
![Correction](../assets/fix.svg) Nous avons amélioré l’évolutivité des API et les performances globales.

### Version V1.0

_4 octobre 2022_

[!BADGE Compatibilité]{type=Informative tooltip="Compatibilité"}

![Nouveau](../assets/new.svg) Prise en charge des produits regroupés et regroupés.
![Nouveau](../assets/new.svg) Ajout de remplacements de visibilité B2B. Les produits peuvent désormais faire l’objet de recherches et peuvent être ajoutés au panier pour des groupes de clients spécifiques.
![Correction](../assets/fix.svg) Le service est désormais plus stable et offre de meilleures performances.

## Versions précédentes

+++Versions bêta

### Version 0.3 - Bêta+

_12 septembre 2022_

[!BADGE Compatibilité]{type=Informative tooltip="Compatibilité"}

![Nouveau](../assets/new.svg) Prise en charge des images pour les variantes : les images de produit sont renvoyées en fonction des options sélectionnées.
![Nouveau](../assets/new.svg) Les rôles pour les prix prennent en charge : autoriser uniquement les membres de groupes de clients spécifiques à voir le prix des produits ;
![Correction](../assets/fix.svg) Amélioration de la stabilité et des performances du service
![Nouveau](../assets/new.svg) Des mises à jour sont reçues lorsque des produits sont supprimés du catalogue.

### Version bêta

_9 août 2022_

[!BADGE Compatibilité]{type=Informative tooltip="Compatibilité"}

![Nouveau](../assets/new.svg) Le `products` et `refineProduct` les requêtes renvoient les données suivantes :

* Attributs de produit prédéfinis (système).
* Attributs de produit dynamiques et filtrez-les par rôle (page d’affichage de produit/page de liste de produits).
* Options du produit.
* Images de produit et filtrez-les par rôle (PDP/PLP).
* Un prix spécifique pour les produits simples et des plages de prix pour les produits configurables.
* Prix des groupes clients et plages de prix. Ils renvoient un prix par défaut de secours aux acheteurs sans groupe de clients.
* Types de produits qui utilisent la tarification spécifique aux clients B2B.

+++
