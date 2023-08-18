---
title: '[!DNL Store Fulfillment by Walmart Commerce Technologies] Notes de mise à jour'
description: "Consultez les notes de mise à jour pour plus d’informations sur toutes les [!DNL Store Fulfillment by Walmart Commerce Technologies] versions."
role: Admin, User, Leader
feature: Shipping/Delivery, Release Notes
exl-id: 04dcec10-fff8-483d-a2c1-4b58e063e0f0
source-git-commit: 78b09113e72382053b01d6016276bae3aa545fa3
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 2%

---

# Notes de mise à jour

Ces notes de mise à jour décrivent la version initiale de [!DNL Store Fulfillment Services by Walmart Commerce Technologies] et incluent :

![Nouveau](../assets/new.svg) Nouvelles fonctionnalités
![Correction d’un problème](../assets/fix.svg) Correctifs et améliorations
![Problème connu](../assets/bug.svg) Problèmes connus

## v1.5.0

*3 août 2023*

[!BADGE Compatibilité]{type=Informative tooltip="Compatibilité"}[Adobe Commerce 2.4.4 à 2.4.6](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html), y compris les versions de correctif de sécurité 2.4.6-p1, 2.4.5-p3 et 2.4.4-p4.

Cette version contient les mises à jour suivantes :

![Nouveau](../assets/fix.svg) Mise à jour de l’extension pour la prise en charge [Versions des correctifs de sécurité Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-operations/release/notes/security-patches/overview.html) 2.4.6-p1, 2.4.5-p3 et 2.4.4-p4.

![Nouveau](../assets/new.svg)<!-- WMTP-918 --> Ajout de la prise en charge de la fonction [Envoi asynchrone](sales-emails.md) option de configuration pour les courriers électroniques de vente. Les commerçants qui effectuent une mise à niveau vers la version 1.5.0 ont la possibilité d’envoyer des emails immédiatement (par défaut) ou de manière asynchrone.

![Nouveau](../assets/new.svg)<!-- WMTP-916--> Mise à jour de la [Configuration des sources](merchant-store-configuration.md) pour prendre en charge les formats de numéros de téléphone internationaux.

![Nouveau](../assets/new.svg) Ajout d’une logique pour empêcher les montants de remboursement de dépasser le montant restant ou le montant facturé.

![Nouveau](../assets/new.svg)<!-- WMTP-882 --> Remplacé `google.map.LatLng` avec des littéraux JSON pour prendre en charge la compatibilité avec les anciennes versions de [!DNL Google Maps].

![Correction d’un problème](../assets/fix.svg)<!-- WMTP- --> Mise à jour du script qui crée la variable `[!DNL Available for Store Pickup]` et `[!DNL Available for Home Delivery]` attributs de produit pour éviter les conflits de catégorie d’attributs.

![Correction d’un problème](../assets/fix.svg)<!-- WMTP-915 --> Correction d’un problème de compatibilité qui provoquait une boucle sans fin lors du chargement et de l’enregistrement de certaines entités.

![Correction d’un problème](../assets/fix.svg)<!-- WMTP-921 --> Correction d’un problème qui empêchait [!DNL Ship to Store] validation des guillemets à partir du déclenchement lorsqu’un élément est ajouté au panier à partir d’une page Détails du produit (PDP).

![Correction d’un problème](../assets/fix.svg)<!-- WMTP- 932 --> Correction d’un problème de passage en caisse qui permettait aux clients de sélectionner la méthode de livraison à domicile pour les articles non éligibles à la livraison à domicile.

![Correction d’un problème](../assets/fix.svg) Mises à jour d’installation :

- <!-- WMTP-880--> Correction d’un problème en raison duquel un code de site web incorrect était renvoyé lors de l’installation de la variable [!DNL Store Fulfillment] extension .

- <!-- WMTP-878--> Correction d’un problème pour les entiers SKU qui nécessitaient que le type de données soit transmis au type chaîne lors de l’installation.

![Correction d’un problème](../assets/fix.svg)<!-- WMTP-915--> Correction d’un échec provoqué par un code d’erreur Check-in manquant.

![Correction d’un problème](../assets/fix.svg)<!-- WMTP-932 --> Correction d’un bogue lié au rejet partiel lors des opérations de remise.

![Nouveau](../assets/new.svg)<!-- WMTP-953 --> Mise à jour du point de terminaison Annuler de l’API afin d’utiliser le paramètre d’état en tant qu’objet facultatif.

![Nouveau](../assets/new.svg)<!-- WMTP-960 --> Amélioration des détails de journalisation pour le point de terminaison de l’API de dépenses.

## v1.4.0

*13 avril 2023*

[!BADGE Compatibilité]{type=Informative tooltip="Compatibilité"}

![Nouveau](../assets/fix.svg) [!DNL Store Fulfillment] est maintenant [compatible avec [!DNL Adobe Commerce] 2.4.4 à 2.4.6](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).


## v1.3.0

*27 février 2023*

[!BADGE Compatibilité]{type=Informative tooltip="Compatibilité"}

Cette version contient les mises à jour suivantes :

![Nouveau](../assets/fix.svg)<!-- WMTP-795 --> Ajout de la possibilité de désactiver la solution d’exécution de magasin pour un site spécifique en modifiant la portée par défaut du paramètre Configuration du système de site web à global.

## v1.2.0

*27 septembre 2022*

[!BADGE Compatibilité]{type=Informative tooltip="Compatibilité"}

Cette version contient les mises à jour suivantes :

![Nouveau](../assets/fix.svg) [!DNL Store Fulfillment] est maintenant [compatible avec [!DNL Adobe Commerce] 2.4.4 à 2.4.5](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).


## v1.1.0

*15 juillet 2022*

[!BADGE Compatibilité]{type=Informative tooltip="Compatibilité"}

Stabilité : Disponibilité générale

![Nouveau](../assets/fix.svg)<!-- WMTP-731 --> Simplification de la [Configuration de l’expérience d’archivage](check-in-experience-setup.md) pour l’application d’aide à la boutique en ajoutant les sélections de modèle et de marque de voiture par défaut. Dans la version précédente, les vendeurs devaient configurer manuellement la marque de voiture et les sélections de modèles.

## v1.0.0

*4 mars 2022*

[!BADGE Compatibilité]{type=Informative tooltip="Compatibilité"}

Stabilité : Disponibilité générale

## Application d’assistance pour la boutique

Pour plus d’informations sur les nouvelles versions de l’application d’aide à la boutique, voir les informations de l’application dans la section [Apple App Store](https://apps.apple.com/us/app/store-assist-by-walmart/id1609281539){target="_blank"} or [Google Play store](https://play.google.com/store/apps/details?id=com.walmart.faas.storeassist){target="_blank"}.
