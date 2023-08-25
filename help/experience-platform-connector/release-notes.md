---
title: Notes de mise à jour
description: Informations les plus récentes sur le connecteur Adobe Experience Platform depuis Adobe Commerce.
exl-id: 7636664b-488a-46f7-8d19-a9faac126aec
feature: Personalization, Integration, Release Notes
source-git-commit: 9717de31ee5545a33462776f3b2bc529ec9e08f2
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 2%

---

# Notes de mise à jour

Ces notes de mise à jour contiennent des mises à jour du connecteur Experience Platform et incluent :

* ![Nouveau](../assets/new.svg) - Nouvelles fonctionnalités
* ![Correction](../assets/fix.svg) - Correctifs et améliorations
* ![Bogue](../assets/bug.svg) - Problèmes connus

Pour les modifications et correctifs de fonctionnalités liés aux extensions utilisées par le connecteur Experience Platform, voir **Mises à jour du service prises en charge**.

Voir [Versions à venir](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/schedule.html) pour en savoir plus sur les calendriers de publication et l’assistance.

Consultez la documentation destinée aux développeurs pour [découvrez la compatibilité des produits](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).

## Mises à jour du service prises en charge

Ces notes de mise à jour décrivent les modifications et correctifs de fonctionnalités liés aux extensions utilisées par le connecteur Experience Platform.

Mises à jour du service +++prises en charge

_10 juin 2023_

* ![Correction](../assets/fix.svg) - Correction d’un problème lors de la `orderId` ne transmettait pas le contexte en raison de préfixes dans l’identifiant de commande Commerce.
* ![Correction](../assets/fix.svg) - Mise à jour des configurations des stratégies de sécurité du contenu.

_30 mars 2023_

* ![Nouveau](../assets/new.svg) - Ajout d’une nouvelle extension appelée `data-services-b2b` inclut [événements de liste de demandes](events.md#b2b-events) pour les commerçants B2B.
* ![Nouveau](../assets/new.svg) - Ajout de la fonction `uniqueIdentifier` champ à [search](events.md#search-events) événements . Ce nouveau champ permet aux marchands de croiser les requêtes de recherche correspondant aux réponses de recherche.

_12 octobre 2022_

* ![Nouveau](../assets/new.svg) - Ajout de deux [événements storefront](events.md): `openCart` et `removeFromCart` vers le SDK et le collecteur des événements Storefront d’Adobe Commerce.
* ![Nouveau](../assets/new.svg) - Ajout de la prise en charge d’un [AEM storefront](overview.md#aem-support).

+++

## 2.3.0

_27 juin 2023_

[!BADGE Compatibilité]{type=Informative tooltip="Compatibilité"}

* ![Nouveau](../assets/new.svg) - Ajout de la capacité à [désactiver l’envoi des événements storefront](connect-data.md#data-collection) à l’Experience Platform.
* ![Correction](../assets/fix.svg) - Mise à jour des configurations des stratégies de sécurité du contenu.
* ![Correction](../assets/fix.svg) - Correction de la prise en charge des événements back-office sur la version Commerce 2.4.7.
* ![Nouveau](../assets/new.svg) - Ajout d’un message de notification sur l’invalidation du cache lors de l’enregistrement des modifications dans le formulaire Connecteur Experience Platform.


## 3.0.0-beta1 (interne uniquement)

_13 juin 2023_

[!BADGE Compatibilité]{type=Informative tooltip="Compatibilité"}

* ![Nouveau](../assets/new.svg) - (Version bêta) Ajout de la capacité à [envoyer l’ordre historique](connect-data.md#beta-send-historical-order-data) données et état de l’Experience Platform. Cette fonctionnalité est disponible uniquement pour les utilisateurs bêta. Vous pouvez rejoindre la version bêta en envoyant un courrier électronique à l’adresse suivante : `dataconnection@adobe.com`.

## 2.2.0

_30 mars 2023_

[!BADGE Compatibilité]{type=Informative tooltip="Compatibilité"}

* ![Nouveau](../assets/new.svg) - Regroupé le `commerce-data-export` et `saas-export` dépendances avec la variable `experience-platform-connector` extension . Auparavant, vous deviez installer ces dépendances séparément. Ces dépendances, ainsi que la configuration du commerce, permettent le traitement côté serveur de [événements back office](events.md#back-office-events).
* ![Nouveau](../assets/new.svg) - Ajout d’un nouvel événement back-office appelé [`orderShipmentCompleted`](events.md#ordershipmentcompleted).

## 2.1.1

_28 février 2023_

[!BADGE Compatibilité]{type=Informative tooltip="Compatibilité"}

* ![Nouveau](../assets/new.svg) - Ajout de la prise en charge de PHP 8.2 pour toutes les extensions de connecteur Experience Platform.

## 2.1.0

_17 janvier 2023_

[!BADGE Compatibilité]{type=Informative tooltip="Compatibilité"}

* ![Nouveau](../assets/new.svg) - Mise à jour de la [Administrateur des connecteurs Experience Platform](connect-data.md) vous pouvez donc spécifier votre propre SDK Web AEP (allié).
* ![Correction](../assets/fix.svg) Remplacé par l’utilisation `identityMap` au lieu de `personID` lors de la définition de l’identité principale pour toutes les données transmises à la périphérie.

## 2.0.1

_10 novembre 2022_

[!BADGE Compatibilité]{type=Informative tooltip="Compatibilité"}

* ![Correction d’un problème](../assets/fix.svg) - Désormais, le contexte Adobe Experience Platform est défini uniquement après le chargement du collecteur d’événements Storefront et du SDK d’événements Storefront.

## 2.0.0

_12 octobre 2022_

[!BADGE Compatibilité]{type=Informative tooltip="Compatibilité"}

* ![Nouveau](../assets/new.svg) - Ajout de la possibilité de spécifier votre propre SDK Web AEP lorsque [connexion](connect-data.md) votre instance Adobe Commerce à l’Experience Platform.
* ![Correction](../assets/fix.svg) - Mise à jour de l’exigence de portée de la banque de données afin que les identifiants de la banque de données puissent être définis sur le site web plutôt que sur l’aperçu.

## 1.0.0

_9 août 2022_

[!BADGE Compatibilité]{type=Informative tooltip="Compatibilité"}

* ![Nouveau](../assets/new.svg) - Disponibilité générale
