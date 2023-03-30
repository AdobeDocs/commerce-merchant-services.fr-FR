---
title: Notes de mise à jour
description: Informations les plus récentes sur le connecteur Adobe Experience Platform depuis Adobe Commerce.
exl-id: 7636664b-488a-46f7-8d19-a9faac126aec
source-git-commit: 735fd14fad22826b04320644e120d296de19a211
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 1%

---

# Notes de mise à jour

Ces notes de mise à jour contiennent des mises à jour du connecteur Experience Platform et incluent :

* ![Nouveau](../assets/new.svg) - Nouvelles fonctionnalités
* ![Correction](../assets/fix.svg) - Correctifs et améliorations
* ![Bogue](../assets/bug.svg) - Problèmes connus

Pour les modifications et correctifs de fonctionnalités liés aux extensions utilisées par le connecteur Experience Platform, voir **Mises à jour du service prises en charge**.

Voir [Versions à venir](https://experienceleague.adobe.com/docs/commerce-operations/release/schedule.html) pour en savoir plus sur les calendriers de publication et l’assistance.

Consultez la documentation destinée aux développeurs pour [en savoir plus sur la compatibilité des produits](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).

## Mises à jour du service prises en charge

Ces notes de mise à jour décrivent les modifications et correctifs de fonctionnalités liés aux extensions utilisées par le connecteur Experience Platform.

Mises à jour du service +++prises en charge

_30 mars 2023_

* ![Nouveau](../assets/new.svg) - Ajout d’une nouvelle extension appelée `data-services-b2b` inclut [événements de liste de demandes](events.md#b2b-events) pour les marchands B2B
* ![Nouveau](../assets/new.svg) - Ajout de la fonction `uniqueIdentifier` champ à [search](events.md#search-events) événements . Ce nouveau champ permet aux marchands de croiser les requêtes de recherche correspondant aux réponses de recherche.

_12 octobre 2022_

* ![Nouveau](../assets/new.svg) - Ajout de deux [événements storefront](events.md): `openCart` et `removeFromCart` au SDK et au collecteur d’Adobe Commerce Storefront Events
* ![Nouveau](../assets/new.svg) - Ajout de la prise en charge d’un [AEM storefront](overview.md#aem-support)

+++

## 2.2.0

_30 mars 2023_

* ![Nouveau](../assets/new.svg) - Regroupé le `commerce-data-export` et `saas-export` dépendances avec la variable `experience-platform-connector` extension . Auparavant, vous deviez installer ces dépendances séparément. Ces dépendances, ainsi que la configuration du commerce, permettent le traitement côté serveur de [événements back office](events.md#back-office-events).
* ![Nouveau](../assets/new.svg) - Ajout d’un nouvel événement back-office appelé [`orderShipmentCompleted`](events.md#ordershipmentcompleted).

## 2.1.1

_28 février 2023_

* ![Nouveau](../assets/new.svg) - Ajout de la prise en charge de PHP 8.2 pour tous les modules de connecteur Experience Platform

## 2.1.0

_17 janvier 2023_

* ![Nouveau](../assets/new.svg) - Mise à jour de la [Administrateur des connecteurs Experience Platform](connect-data.md) vous pouvez donc spécifier votre propre SDK Web AEP (allié). Ajout également d’une option permettant aux commerçants inscrits à notre programme bêta de back-office d’envoyer [données d’événement back office](connect-data.md#data-collection) au bord. Ces événements contiennent [informations sur l’état de la commande](events.md#beta-order-status-events) sur une commande, par exemple si une commande a été passée, annulée, remboursée ou expédiée.
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
