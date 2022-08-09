---
title: '"[!DNL Catalog Service] Notes de mise à jour"'
description: '"Informations les plus récentes sur la version [!DNL Catalog Service] pour Adobe Commerce."'
source-git-commit: 3959cc5d07f9a0da0ba772a4f3bc56adeb3c6bf3
workflow-type: tm+mt
source-wordcount: '146'
ht-degree: 2%

---


# [!DNL Catalog Service] Notes de mise à jour

{{catalog-service-beta}}

Ces notes de mise à jour décrivent les dernières versions de [!DNL Catalog Service] et incluent :

* ![Nouveau](../assets/new.svg) - Nouvelles fonctionnalités
* ![Correction](../assets/fix.svg) - Correctifs et améliorations
* ![Bogue](../assets/bug.svg) - Problèmes connus

## Version bêta

* ![Nouveau](../assets/new.svg) - Le `products` et `refineProduct` les requêtes renvoient les données suivantes :
   * Attributs de produit prédéfinis (système).
   * Attributs de produit dynamiques et filtrez-les par rôle (page d’affichage de produit/page de liste de produits).
   * Options du produit.
   * Images de produit et filtrez-les par rôle (PDP/PLP).
   * Un prix spécifique pour les produits simples et des plages de prix pour les produits configurables.
   * Prix des groupes clients et plages de prix. Ils renvoient un prix par défaut de secours aux acheteurs sans groupe de clients.
   * Types de produits qui utilisent la tarification spécifique aux clients B2B.

## Limites connues

* Le prix de niveau n’est pas pris en charge.
* Dans un tableau d’images, seule la première image contient des rôles.
* Les images des variantes ne sont pas récupérées.
* Les mises à jour ne sont pas reçues lorsque des produits ou des variantes sont supprimés du catalogue.
