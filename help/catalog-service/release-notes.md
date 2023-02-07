---
title: '''[!DNL Catalog Service] Notes de mise à jour de'
description: Les dernières informations de mise à jour pour [!DNL Catalog Service] pour Adobe Commerce.
exl-id: 9bf8e3f7-5b74-4755-867e-ac1c5000ff33
source-git-commit: 67f9e5ce69930f3298427a103f9160f925d2ae0d
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# [!DNL Catalog Service] Notes de mise à jour

Ces notes de mise à jour décrivent les dernières versions de [!DNL Catalog Service] et incluent :

* ![Nouveau](../assets/new.svg) Nouvelles fonctionnalités
* ![Correction](../assets/fix.svg) Correctifs et améliorations
* ![Bogue](../assets/bug.svg) Problèmes connus

## Version V1.4

Date de publication : 2023-2-7 Compatible avec Adobe Commerce (EE) : 2.4.x Compatible avec Adobe Commerce for Cloud (CEE) : 2.4.x Stabilité : Disponibilité générale

![Nouveau](../assets/new.svg) Mise en page du métaphorage du service de catalogue pour simplifier les étapes d’installation.
![Correction](../assets/fix.svg) Améliorations de l’évolutivité et des performances des API.


### Limites connues

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
* Catégories (`categories` et `categoryList`)

## Version V1.3

Date de publication : 2023-1-17 Compatible avec Adobe Commerce (EE) : 2.4.x Compatible avec Adobe Commerce for Cloud (CEE) : 2.4.x Stabilité : Disponibilité générale

![Nouveau](../assets/new.svg) Simplification et amélioration de l’expérience d’intégration.
![Nouveau](../assets/new.svg) De nouveaux points de terminaison d’environnement de test client sont disponibles pour les tests de pré-production.
![Nouveau](../assets/new.svg) Ajout de la prise en charge des produits virtuels.
![Correction](../assets/fix.svg) Améliorations de l’évolutivité et des performances des API.

### Limites connues

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
* Catégories (`categories` et `categoryList`)

## Version V1.1

Date de publication : 2022-11-18 Compatible avec Adobe Commerce (EE) : 2.4.x Compatible avec Adobe Commerce for Cloud (CEE) : 2.4.x Stabilité : Disponibilité générale

![Nouveau](../assets/new.svg) Le service de catalogue prend désormais en charge les Adobes [Mesh de l’API](https://developer.adobe.com/graphql-mesh-gateway/).
![Correction](../assets/fix.svg) Nous avons amélioré l’évolutivité des API et les performances globales.

### Limites connues

Ces fonctionnalités ne sont pas encore prises en charge :

* Produits groupés avec prix fixe
* Aucune mise à jour n’est reçue lorsque les variantes sont supprimées du catalogue.
* La taille maximale de la charge utile des attributs dynamiques est de 9 Mo.
* Prix du produit de groupe. Peuvent être calculées avec des prix de produit simples.
* Dans un tableau d’images, seule la première image contient des rôles.
* Échantillons de couleurs
* Chargement de la page Détails du produit via l’URL du produit.

Les restrictions suivantes peuvent être résolues à l’aide de l’API GraphQL :

* Prix publicitaire minimal
* Prix de niveau
* Produits téléchargeables et cartes-cadeaux
* Catégories (`categories` et `categoryList`)

## Version V1.0

Date de publication : 2022-10-04 Compatible avec Adobe Commerce (EE) : 2.4.x Compatible avec Adobe Commerce for Cloud (CEE) : 2.4.x Stabilité : Disponibilité générale

![Nouveau](../assets/new.svg) Prise en charge des produits regroupés et regroupés.
![Nouveau](../assets/new.svg) Ajout de remplacements de visibilité B2B. Les produits peuvent désormais faire l’objet de recherches et peuvent être ajoutés au panier pour des groupes de clients spécifiques.
![Correction](../assets/fix.svg) Le service est désormais plus stable et offre de meilleures performances.

### Limites connues

Ces fonctionnalités ne sont pas encore prises en charge :

* Prix de niveau
* Les mises à jour ne sont pas reçues lorsque des variantes sont supprimées du catalogue.
* La taille maximale de la charge utile des attributs dynamiques est &lt;9 Mo
* Prix fixe pour les produits groupés
* Prix total des produits groupés
* Prise en charge des types de produits de cartes-cadeaux, virtuelles et téléchargeables
* Prix publicitaire minimal (MAP)

## Version 0.3 - Bêta+

Date de publication : 2022-09-12 Compatible avec Adobe Commerce (EE) : 2.4.x Compatible avec Adobe Commerce for Cloud (CEE) : 2.4.x Stabilité : Beta

![Nouveau](../assets/new.svg) Prise en charge des images pour les variantes : les images de produit sont renvoyées en fonction des options sélectionnées.
![Nouveau](../assets/new.svg) Les rôles pour les prix prennent en charge : autoriser uniquement les membres de groupes de clients spécifiques à voir le prix des produits ;
![Correction](../assets/fix.svg) Amélioration de la stabilité et des performances du service
![Nouveau](../assets/new.svg) Des mises à jour sont reçues lorsque des produits sont supprimés du catalogue.

### Limites connues

Ces fonctionnalités ne sont pas encore prises en charge :

* Prix de niveau
* Lot et produits regroupés
* Aucune mise à jour n’est reçue lorsque des variantes sont supprimées du catalogue.
* La visibilité B2B remplace : les produits peuvent faire l’objet de recherches ou être ajoutés au panier pour des groupes de clients spécifiques ;

## Version bêta

Date de publication : 2022-08-09 Compatible avec Adobe Commerce (EE) : 2.4.x Compatible avec Adobe Commerce for Cloud (CEE) : 2.4.x Stabilité : Beta

![Nouveau](../assets/new.svg) Le `products` et `refineProduct` les requêtes renvoient les données suivantes :

* Attributs de produit prédéfinis (système).
* Attributs de produit dynamiques et filtrez-les par rôle (page d’affichage de produit/page de liste de produits).
* Options du produit.
* Images de produit et filtrez-les par rôle (PDP/PLP).
* Un prix spécifique pour les produits simples et des plages de prix pour les produits configurables.
* Prix des groupes clients et plages de prix. Ils renvoient un prix par défaut de secours aux acheteurs sans groupe de clients.
* Types de produits qui utilisent la tarification spécifique aux clients B2B.

### Limites connues

* Les produits groupés et groupés ne sont pas pris en charge.
* Le prix de niveau n’est pas pris en charge.
* Dans un tableau d’images, seule la première image contient des rôles.
* Les images des variantes ne sont pas récupérées.
* Les mises à jour ne sont pas reçues lorsque des produits ou des variantes sont supprimés du catalogue.
