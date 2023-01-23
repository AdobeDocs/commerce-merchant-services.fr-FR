---
title: Notes de mise à jour
description: Informations les plus récentes sur le connecteur Adobe Experience Platform depuis Adobe Commerce.
exl-id: 7636664b-488a-46f7-8d19-a9faac126aec
source-git-commit: 975854dbdae32e5e51bb57593cf122627d01571f
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 2%

---

# Notes de mise à jour

Ces notes de mise à jour contiennent des mises à jour du connecteur Experience Platform et incluent :

* ![Nouveau](../assets/new.svg) - Nouvelles fonctionnalités
* ![Correction](../assets/fix.svg) - Correctifs et améliorations
* ![Bogue](../assets/bug.svg) - Problèmes connus

Pour les modifications et correctifs de fonctionnalités liés aux extensions utilisées par le connecteur Experience Platform, voir **Mises à jour du service prises en charge**.

Voir [Versions à venir](https://experienceleague.adobe.com/docs/commerce-operations/release/schedule.html) pour en savoir plus sur les calendriers de publication et l’assistance.

Voir [Disponibilité](https://experienceleague.adobe.com/docs/commerce-operations/release/availability.html) pour en savoir plus sur la compatibilité des produits.

## Mises à jour du service prises en charge

Ces notes de mise à jour décrivent les modifications et correctifs de fonctionnalités liés aux extensions utilisées par le connecteur Experience Platform.

Mises à jour du service +++prises en charge

_12 octobre 2022_

* ![Nouveau](../assets/new.svg) - Ajout de deux [événements storefront](events.md): `openCart` et `removeFromCart` au SDK et au collecteur d’Adobe Commerce Storefront Events
* ![Nouveau](../assets/new.svg) - Ajout de la prise en charge d’un [AEM storefront](overview.md#aem-support)

+++

## 2.1.0

_17 janvier 2023_

* ![Nouveau](../assets/new.svg) - Mise à jour de la [Administrateur des connecteurs Experience Platform](connect-data.md) vous pouvez donc spécifier votre propre SDK Web AEP (allié). Ajout également d’une option permettant aux commerçants inscrits à notre programme bêta de back-office d’envoyer [données d’événement back office](connect-data.md#data-collection) au bord. Ces événements contiennent [informations sur l’état de la commande](events.md#beta-order-status-events) sur une commande, par exemple si une commande a été passée, annulée, remboursée ou expédiée. Si vous souhaitez participer au programme bêta back-office, contactez [drios@adobe.com](mailto:drios@adobe.com).
* ![Correction](../assets/fix.svg) Remplacé par l’utilisation de `identityMap` au lieu de `personID` lors de la définition de l’identité Principale pour toutes les données transmises à la périphérie.

## 2.0.1

_10 novembre 2022_

* ![Correction d’un problème](../assets/fix.svg) - Désormais, le contexte Adobe Experience Platform est défini uniquement après le chargement du collecteur d’événements Storefront et du SDK d’événements Storefront.

## 2.0.0

_12 octobre 2022_

* ![Nouveau](../assets/new.svg) - Ajout de la possibilité de spécifier votre propre SDK Web AEP lorsque [connexion](connect-data.md) votre instance Adobe Commerce à l’Experience Platform
* ![Correction](../assets/fix.svg) - Mise à jour de l’exigence de portée de la banque de données afin que les identifiants de la banque de données soient définis sur le site web plutôt que sur la vue d’ensemble

## 1.0.0

_9 août 2022_

* ![Nouveau](../assets/new.svg) - Version de disponibilité générale

## Documentation

Pour en savoir plus :

* [Documentation destinée aux développeurs Adobe Commerce](https://devdocs.magento.com/)
* [Guide de l’utilisateur d’Adobe Commerce](https://docs.magento.com/user-guide/)
