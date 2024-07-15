---
title: '[!DNL Store Fulfillment by Walmart Commerce Technologies] Notes de mise à jour'
description: "Consultez les notes de mise à jour pour plus d’informations sur toutes les  [!DNL Store Fulfillment by Walmart Commerce Technologies] versions."
role: Admin, User, Leader
feature: Shipping/Delivery, Release Notes
exl-id: 04dcec10-fff8-483d-a2c1-4b58e063e0f0
source-git-commit: db1d5523f48f5686c2a28c7dfb7b1175238b37cf
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# Notes de mise à jour

Ces notes de mise à jour décrivent la version initiale de [!DNL Store Fulfillment Services by Walmart Commerce Technologies] et incluent :

![New](../assets/new.svg) Nouvelles fonctionnalités
![Problème corrigé](../assets/fix.svg) Correctifs et améliorations
![Problème connu](../assets/bug.svg) Problèmes connus

Voir [Versions à venir](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/schedule.html) pour en savoir plus sur les calendriers de publication et l’assistance.

Voir [Disponibilité du produit](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html) pour savoir quelles versions d’Adobe Commerce prennent en charge cette extension.

## v1.5.0

*3 août 2023*

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}[Adobe Commerce 2.4.4 à 2.4.6](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html), y compris les versions de correctif de sécurité 2.4.6-p1, 2.4.5-p3 et 2.4.4-p4

Cette version contient les mises à jour suivantes :

![Nouveau](../assets/fix.svg) Mise à jour de l’extension pour la prise en charge des [versions de correctif de sécurité Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-operations/release/notes/security-patches/overview.html) 2.4.6-p1, 2.4.5-p3 et 2.4.4-p4.

![Nouveau](../assets/new.svg)<!-- WMTP-918 --> Ajout de la prise en charge de l’option de configuration [Envoi asynchrone](sales-emails.md) pour les courriers électroniques de vente. Les commerçants qui effectuent une mise à niveau vers la version 1.5.0 ont la possibilité d’envoyer des emails immédiatement (par défaut) ou de manière asynchrone.

![Nouveau](../assets/new.svg)<!-- WMTP-916--> Mise à jour de la [configuration des sources](merchant-store-configuration.md) pour la prise en charge des formats de numéros de téléphone internationaux.

![New](../assets/new.svg) Ajout d’une logique pour empêcher les montants de remboursement de dépasser le montant restant ou facturé.

![New](../assets/new.svg)<!-- WMTP-882 --> L’objet `google.map.LatLng` a été remplacé par des littéraux JSON pour prendre en charge la compatibilité avec les anciennes versions de [!DNL Google Maps].

![ Correction d’un problème ](../assets/fix.svg)<!-- WMTP- --> Mise à jour du script qui crée les attributs de produit `[!DNL Available for Store Pickup]` et `[!DNL Available for Home Delivery]` pour éviter les conflits de catégorie d’attributs.

![ Correction d’un problème de compatibilité qui provoquait une boucle sans fin lors du chargement et de l’enregistrement de certaines entités.](../assets/fix.svg)<!-- WMTP-915 -->

![ Correction d’un problème ](../assets/fix.svg)<!-- WMTP-921 --> qui empêchait le déclenchement de la validation des guillemets [!DNL Ship to Store] lorsqu’un élément était ajouté au panier à partir d’une page des détails du produit (PDP).

![ Correction d’un problème ](../assets/fix.svg)<!-- WMTP- 932 --> qui permettait aux clients de sélectionner la méthode de remise à domicile pour les éléments qui ne pouvaient pas être livrés à domicile.

![Problème corrigé](../assets/fix.svg) Mises à jour de l’installation :

- <!-- WMTP-880--> Correction d’un problème en raison duquel un code de site web incorrect était renvoyé lors de l’installation de l’extension [!DNL Store Fulfillment].

- <!-- WMTP-878--> Correction d’un problème pour les entiers SKU qui nécessitaient que le type de données soit transmis au type chaîne lors de l’installation.

![Correction d’un problème](../assets/fix.svg)<!-- WMTP-915--> Correction d’un échec provoqué par un code d’erreur d’archivage manquant.

![Correction d’un problème](../assets/fix.svg)<!-- WMTP-932 --> Correction d’un bogue lié au rejet partiel lors des opérations de remise.

![New](../assets/new.svg)<!-- WMTP-953 --> Mise à jour du point de terminaison Annuler de l’API pour utiliser le paramètre d’état comme objet facultatif.

![Nouveau](../assets/new.svg)<!-- WMTP-960 --> Amélioration des détails de journalisation pour le point de terminaison de l’API de dépenses.

## v1.4.0

*13 avril 2023*

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![New](../assets/fix.svg) [!DNL Store Fulfillment] est désormais [compatible avec [!DNL Adobe Commerce] 2.4.4 à 2.4.6](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).


## v1.3.0

*27 février 2023*

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

Cette version contient les mises à jour suivantes :

![Nouveau](../assets/fix.svg)<!-- WMTP-795 --> Ajout de la fonctionnalité de désactivation de la solution d’exécution de magasin pour un site spécifique en modifiant la portée par défaut du paramètre Configuration du système de site web à global.

## v1.2.0

*27 septembre 2022*

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

Cette version contient les mises à jour suivantes :

![New](../assets/fix.svg) [!DNL Store Fulfillment] est désormais [compatible avec [!DNL Adobe Commerce] 2.4.4 à 2.4.5](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).


## v1.1.0

*15 juillet 2022*

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

Stabilité : Disponibilité générale

![Nouveau](../assets/fix.svg)<!-- WMTP-731 --> a simplifié la [configuration de l’expérience d’archivage](check-in-experience-setup.md) pour l’application d’assistance en magasin en ajoutant les sélections de maquette et de modèle de voiture par défaut. Dans la version précédente, les vendeurs devaient configurer manuellement la marque de voiture et les sélections de modèles.

## v1.0.0

*4 mars 2022*

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

Stabilité : Disponibilité générale

## Application d’assistance pour la boutique

Pour plus d’informations sur les nouvelles versions de l’application d’aide à la boutique, voir les informations de l’application dans la [boutique Apple App Store](https://apps.apple.com/us/app/store-assist-by-walmart/id1609281539){target="_blank"} ou la [boutique Google Play](https://play.google.com/store/apps/details?id=com.walmart.faas.storeassist){target="_blank"}.
