---
title: Notes de mise à jour
description: Les dernières informations de mise à jour pour la variable [!DNL Data Connection] à partir d’Adobe Commerce.
exl-id: 7636664b-488a-46f7-8d19-a9faac126aec
feature: Personalization, Integration, Release Notes
source-git-commit: ace61fa579404962a9ca3eb97f61ed50bc43db52
workflow-type: tm+mt
source-wordcount: '807'
ht-degree: 0%

---

# Notes de mise à jour

>[!IMPORTANT]
>
>Le connecteur Experience Platform a été renommé en [!DNL Data Connection].

Ces notes de mise à jour contiennent des mises à jour des [!DNL Data Connection] et comprend :

![Nouveau](../assets/new.svg) - Nouvelles fonctionnalités
![Correction](../assets/fix.svg) - Correctifs et améliorations
![Bogue](../assets/bug.svg) - Problèmes connus

Pour les modifications et correctifs de fonctionnalités liés aux extensions utilisées par la variable [!DNL Data Connection] extension, voir **Mises à jour du service prises en charge**.

Voir [Versions à venir](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/schedule.html) pour en savoir plus sur les calendriers de publication et l’assistance.

Consultez la documentation destinée aux développeurs pour [connaître les versions de Commerce qui prennent en charge ce module ;](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).

## Mises à jour du service prises en charge

Ces notes de mise à jour décrivent les modifications et les correctifs liés aux extensions utilisées par les [!DNL Data Connection] extension .

Mises à jour du service +++prises en charge

_24 janvier 2024_

![Nouveau](../assets/new.svg) - Mise à jour de la `data-services-b2b` pour inclure un nouvel événement de demande appelé [deleteRequestList](events.md#deleterequisitionlist) pour les commerçants B2B.

_16 novembre 2023_

![Correction](../assets/fix.svg) - Correction d’un problème en raison duquel un message d’erreur s’affichait incorrectement lors de la commande comportant plusieurs adresses de livraison.
![Correction](../assets/fix.svg) - Correction d’un problème dans la variable [productPageView](events.md#productpageview) où la variable `productListItems.priceTotal` le champ d’événement ne convertissait pas le prix après avoir modifié la devise dans la vue de magasin.
![Correction](../assets/fix.svg) - Correction d’un problème dans la variable `productListItems` champ d’événement où le code de devise n’était pas mis à jour lorsque le marchand a basculé vers la vue magasin.

_10 octobre 2023_

![Nouveau](../assets/new.svg) - Ajout de nouveaux événements d’état de commande : [Commande facturée](events-backoffice.md#orderinvoiced), [Retour à la ligne de commande initié](events-backoffice.md#orderitemsreturninitiated), et [Retour à la ligne de commande terminé](events-backoffice.md#orderitemreturncompleted).
![Correction](../assets/fix.svg) - Correction d’un problème en raison duquel les modifications de configuration de devise n’étaient pas répercutées dans les événements après l’actualisation du cache.
![Correction](../assets/fix.svg) - Correction d’une erreur lorsque le message de confirmation de commande n’apparaissait pas si le placement de commande asynchrone était activé.
![Nouveau](../assets/new.svg) - Ajout de données à [addToRequestList](events.md#addtorequisitionlist) pour les produits simples sur la page d’affichage Catégorie.
![Correction](../assets/fix.svg) - Correction d’un problème dans la variable `selectedOptions` des données de la variable [addToRequestList](events.md#addtorequisitionlist) lorsque des produits sont ajoutés à partir de la page de confirmation de commande.
![Nouveau](../assets/new.svg) - Ajout de données de produit à [addToRequestList](events.md#addtorequisitionlist) lorsque des produits sont ajoutés à la liste des demandes à partir de la page d’affichage Catégorie .
![Nouveau](../assets/new.svg) - Ajout [addToRequestList](events.md#addtorequisitionlist) lorsque des produits configurables sont ajoutés à la liste des demandes à partir de la page d’affichage des produits.
![Nouveau](../assets/new.svg) - Ajout [addToRequestList](events.md#addtorequisitionlist) et [removeFromRequestList](events.md#removefromrequisitionlist) événements lorsque la quantité de produits est augmentée et/ou réduite à partir d’une liste de demandes.

_10 juin 2023_

![Correction](../assets/fix.svg) - Correction d’un problème lors de la `orderId` n’a pas été transmis dans le contexte en raison de préfixes dans l’identifiant de commande Commerce.
![Correction](../assets/fix.svg) - Mise à jour des configurations des stratégies de sécurité du contenu.

_30 mars 2023_

![Nouveau](../assets/new.svg) - Ajout d’une extension appelée `data-services-b2b` inclut [événements de liste de demandes](events.md#b2b-events) pour les commerçants B2B.
![Nouveau](../assets/new.svg) - Ajout de la fonction `uniqueIdentifier` champ à [search](events.md#search-events) événements . Ce nouveau champ permet aux commerçants de croiser les références des requêtes de recherche et des réponses de recherche.

_12 octobre 2022_

![Nouveau](../assets/new.svg) - Ajout de deux [événements storefront](events.md), `openCart` et `removeFromCart`, au SDK et au collecteur des événements Storefront d’Adobe Commerce.
![Nouveau](../assets/new.svg) - Ajout de la prise en charge d’un [AEM storefront](overview.md#aem-support).

+++

## 3.1.1

_19 mars 2024_

[!BADGE Compatibilité]{type=Informative tooltip="Compatibilité"}

![Nouveau](../assets/new.svg) Ajout de la prise en charge de PHP 8.3

## 3.2.0-beta2

_4 mars 2024_

[!BADGE Compatibilité]{type=Informative tooltip="Compatibilité"}

![Nouveau](../assets/new.svg) - Si vous participez à la version bêta, assurez-vous que votre `composer.json` se présente comme suit au niveau racine : ` "minimum-stability": "beta"`.
![Nouveau](../assets/new.svg) - Ajout de la capacité à [ajout d’attributs personnalisés](update-xdm.md#update-schema-with-time-series-behavioral-and-back-office-event-data).
![Nouveau](../assets/new.svg) - Ajout de la capacité à [collecter et envoyer des enregistrements de profil ;](connect-data.md#send-customer-profile-data) et les données à Experience Platform.

## 3.1.0

_16 novembre 2023_

[!BADGE Compatibilité]{type=Informative tooltip="Compatibilité"}

![Nouveau](../assets/new.svg) - Le connecteur Experience Platform a été renommé en [!DNL Data Connection].
![Correction](../assets/new.svg) - Ajout de la possibilité de consigner la réponse d’erreur si Adobe IMS ne parvient pas à générer le jeton d’accès.
![Correction](../assets/new.svg) - Ajout d’un message de notification si vous tentez de synchroniser les commandes historiques mais que vous n’avez pas spécifié d’informations d’identification de compte.

## 3.0.0

_10 octobre 2023_

[!BADGE Compatibilité]{type=Informative tooltip="Compatibilité"}

Il s’agit d’une version majeure. [Modifier](install.md#update-the-data-connection) le fichier racine compositeur.json de votre projet.

![Nouveau](../assets/new.svg) - Disponibilité générale de [envoyer l’ordre historique](connect-data.md#send-historical-order-data) données et état de l’Experience Platform.
![Nouveau](../assets/new.svg) - Ajout de la prise en charge d’OAuth 2.0 lorsque vous [configure](connect-data.md#connect-commerce-data-to-adobe-experience-platform) la valeur [!DNL Data Connection] extension .
![Nouveau](../assets/new.svg) - Fin de la prise en charge d’Adobe Commerce 2.4.3.

## 2.3.0

_27 juin 2023_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) - Ajout de la capacité à [désactiver l’envoi des événements storefront](connect-data.md#data-collection) à l’Experience Platform.
![Correction](../assets/fix.svg) - Mise à jour des configurations des stratégies de sécurité du contenu.
![Correction](../assets/fix.svg) - Correction de la prise en charge des événements back-office sur la version Commerce 2.4.7.
![Nouveau](../assets/new.svg) - Ajout d’un message de notification sur l’invalidation du cache lorsque vous enregistrez les modifications apportées à la variable [!DNL Data Connection] formulaire d’extension.


## 3.0.0-beta1 (interne uniquement)

_13 juin 2023_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) - (Version bêta) Ajout de la capacité à [envoyer l’ordre historique](connect-data.md#beta-send-historical-order-data) données et état de l’Experience Platform.

## 2.2.0

_30 mars 2023_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) - Regroupé le `commerce-data-export` et `saas-export` dépendances avec la variable `experience-platform-connector` extension . Auparavant, vous deviez installer ces dépendances séparément. Ces dépendances, ainsi que la configuration du commerce, permettent le traitement côté serveur de [événements back office](events-backoffice.md).
![Nouveau](../assets/new.svg) - Ajout d’un nouvel événement back-office appelé [`orderShipmentCompleted`](events-backoffice.md#ordershipmentcompleted).

## 2.1.1

_28 février 2023_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) - Prise en charge de PHP 8.2 pour tous [!DNL Data Connection] extensions.

## 2.1.0

_17 janvier 2023_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) - Mise à jour de la [[!DNL Data Connection] administration des extensions](connect-data.md) vous pouvez donc spécifier votre propre SDK Web AEP (allié).
![Correction](../assets/fix.svg) Remplacé par l’utilisation `identityMap` au lieu de `personID` lors de la définition de l’identité principale pour toutes les données transmises à la périphérie.

## 2.0.1

_10 novembre 2022_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Correction](../assets/fix.svg) - Désormais, le contexte Adobe Experience Platform est défini uniquement après le chargement du collecteur d’événements Storefront et du SDK d’événements Storefront.

## 2.0.0

_12 octobre 2022_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) - Ajout de la possibilité de spécifier votre propre SDK Web AEP lorsque [connexion](connect-data.md) votre instance Adobe Commerce à l’Experience Platform.
![Correction](../assets/fix.svg) - Mise à jour de l’exigence de portée de la banque de données afin que les identifiants de la banque de données puissent être définis sur le site web plutôt que sur l’aperçu.

## 1.0.0

_9 août 2022_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) - Disponibilité générale
