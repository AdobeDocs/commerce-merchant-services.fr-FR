---
title: Notes de mise à jour
description: Informations les plus récentes sur l’extension  [!DNL Data Connection] d’Adobe Commerce.
exl-id: 7636664b-488a-46f7-8d19-a9faac126aec
feature: Personalization, Integration, Release Notes
source-git-commit: f894a1a192f648df01e1f869bec9c8a4c66803e1
workflow-type: tm+mt
source-wordcount: '951'
ht-degree: 0%

---

# Notes de mise à jour

>[!IMPORTANT]
>
>Le connecteur Experience Platform a été renommé [!DNL Data Connection].

Ces notes de mise à jour contiennent des mises à jour de l’extension [!DNL Data Connection] et incluent :

![New](../assets/new.svg) - Nouvelles fonctionnalités
![Correctif](../assets/fix.svg) - Correctifs et améliorations
![Bug](../assets/bug.svg) - Problèmes connus

Pour les modifications et correctifs de fonctionnalités liés aux extensions utilisées par l’extension [!DNL Data Connection], voir **Mises à jour de service prises en charge**.

Voir [Versions à venir](https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/schedule) pour en savoir plus sur les calendriers de publication et l’assistance.

Consultez la documentation destinée aux développeurs pour [découvrir les versions de Commerce qui prennent en charge ce module](https://experienceleague.adobe.com/en/docs/commerce-operations/release/product-availability).

## Mises à jour du service prises en charge

Ces notes de mise à jour décrivent les modifications et correctifs de fonctionnalités liés aux extensions utilisées par l’extension [!DNL Data Connection].

Mises à jour du service +++prises en charge

_2 août 2024_

![Fix](../assets/fix.svg) - Correction du montant total des paiements lorsque le total de la commande est configuré pour inclure les taxes.
![Nouveau](../assets/new.svg) - Ajout d’un champ `taxAmount` pour commander des événements d’achat.
![Nouveau](../assets/new.svg) - Possibilité d’ajouter des données personnalisées aux événements. Voir ce qui suit pour un [exemple](https://github.com/adobe/commerce-events/blob/main/examples/events/custom-event-override.md).

_24 janvier 2024_

![New](../assets/new.svg) - Mise à jour de l’extension `data-services-b2b` afin d’inclure un nouvel événement de demande appelé [deleteRequestList](events.md#deleterequisitionlist) pour les marchands B2B.

_16 novembre 2023_

![Correctif](../assets/fix.svg) - Correction d’un problème en raison duquel un message d’erreur s’affichait incorrectement lors de la commande portant plusieurs adresses de livraison.
![Correctif](../assets/fix.svg) - Correction d’un problème dans l’événement [productPageView](events.md#productpageview) en raison duquel le champ d’événement `productListItems.priceTotal` ne convertissait pas le prix après avoir permuté la devise en mode magasin.
![Correctif](../assets/fix.svg) - Correction d’un problème dans le champ d’événement `productListItems` en raison duquel le code de devise n’était pas mis à jour lorsque le marchand activait la vue de magasin.

_10 octobre 2023_

![New](../assets/new.svg) - Ajout de nouveaux événements d’état de commande : [Commande facturée](events-backoffice.md#orderinvoiced), [Retour à la commande initié](events-backoffice.md#orderitemsreturninitiated) et [Retour à la commande terminé](events-backoffice.md#orderitemreturncompleted).
![Correctif](../assets/fix.svg) - Correction d’un problème en raison duquel les modifications de configuration de devise n’étaient pas répercutées dans les événements après l’actualisation du cache.
![Fix](../assets/fix.svg) - Correction d’une erreur lorsque le message de confirmation de commande n’apparaissait pas si le placement de commande asynchrone était activé.
![New](../assets/new.svg) - Ajout de données à l’événement [addToRequestList](events.md#addtorequisitionlist) pour les produits simples sur la page d’affichage de catégorie.
![Fix](../assets/fix.svg) - Correction d’un problème dans les données `selectedOptions` de l’événement [addToRequestList](events.md#addtorequisitionlist) lorsque des produits sont ajoutés à partir de la page de confirmation de commande.
![New](../assets/new.svg) - Ajout de données de produit à l’événement [addToRequestList](events.md#addtorequisitionlist) lorsque des produits sont ajoutés à la liste des demandes à partir de la page de vue Catégorie.
![New](../assets/new.svg) - Ajout de l’événement [addToRequestList](events.md#addtorequisitionlist) lors de l’ajout de produits configurables à la liste des demandes à partir de la page Product view.
![New](../assets/new.svg) - Ajout des événements [addToRequestList](events.md#addtorequisitionlist) et [removeFromRequestList](events.md#removefromrequisitionlist) lorsque la quantité de produit est augmentée et/ou réduite à partir d’une liste de demandes.

_10 juin 2023_

![Correctif](../assets/fix.svg) - Correction d’un problème en raison duquel `orderId` ne transmettait pas le contexte en raison de préfixes dans l’identifiant de commande Commerce.
![Correctif](../assets/fix.svg) - Mise à jour des configurations de la stratégie de sécurité du contenu.

_30 mars 2023_

![New](../assets/new.svg) - Ajout d’une extension appelée `data-services-b2b` qui inclut [ événements de liste de demandes](events.md#b2b-events) pour les marchands B2B.
![New](../assets/new.svg) - Ajout du champ `uniqueIdentifier` aux événements [search](events.md#search-events). Ce nouveau champ permet aux commerçants de croiser les références des requêtes de recherche et des réponses de recherche.

_12 octobre 2022_

![Nouveau](../assets/new.svg) - Ajout de deux [ événements storefront ](events.md), `openCart` et `removeFromCart` au SDK et au collecteur des événements Storefront Adobe Commerce.
![Nouveau](../assets/new.svg) - Ajout de la prise en charge d’une [AEM storefront](overview.md#aem-support).

+++

## 3.1.4

_9 août 2024_

[!BADGE Compatibilité]{type=Informative tooltip="Compatibilité"}

![Fix](../assets/fix.svg) - Mise à jour du métapaquet `experience-platform-connector` pour supprimer les autres exportateurs et indexeurs de données inutilisés.

## 3.1.3

_22 juillet 2024_

[!BADGE Compatibilité]{type=Informative tooltip="Compatibilité"}

![Fix](../assets/fix.svg) - Mise à jour du métapaquet `experience-platform-connector` pour supprimer les exportateurs et les indexeurs de données inutilisés.

## 3.1.2

_5 juin 2024_

[!BADGE Compatibilité]{type=Informative tooltip="Compatibilité"}

![Fix](../assets/fix.svg) - Correction d’un problème en raison duquel un format de date incorrect était utilisé lors du lancement d’une [synchronisation historique](connect-data.md#specify-order-history-date-range).
![Fix](../assets/fix.svg) - Correction d’un problème en raison duquel l’événement [startCheckout](events.md#startcheckout) n’était pas envoyé sur Adobe Commerce 2.4.7.

## 3.1.1

_4 avril 2024_

[!BADGE Compatibilité]{type=Informative tooltip="Compatibilité"}

![Nouveau](../assets/new.svg) - Ajout de la prise en charge de PHP 8.3 pour toutes les extensions [!DNL Data Connection].
![Nouveau](../assets/new.svg) - Ajout d’un article expliquant comment [intégrer](mobile-sdk-epc.md) le SDK Adobe Experience Platform Mobile avec Commerce.

## 3.2.0-beta2

_4 mars 2024_

[!BADGE Compatibilité]{type=Informative tooltip="Compatibilité"}

![Nouveau](../assets/new.svg) - Si vous participez à la version bêta, assurez-vous que votre fichier `composer.json` comporte les éléments suivants au niveau racine : ` "minimum-stability": "beta"`. Ajoutez également `composer require "magento/customers-connector: ^1.2.0"` pour envoyer des profils client de votre instance Commerce vers SaaS.
![Nouveau](../assets/new.svg) - Possibilité d’[ ajouter des attributs personnalisés](update-xdm.md#update-schema-with-time-series-behavioral-and-back-office-event-data).
![Nouveau](../assets/new.svg) - Possibilité de [ collecter et envoyer des enregistrements de profil ](connect-data.md#send-customer-profile-data) et des données à l’Experience Platform.

## 3.1.0

_16 novembre 2023_

[!BADGE Compatibilité]{type=Informative tooltip="Compatibilité"}

![Nouveau](../assets/new.svg) - Le connecteur Experience Platform a été renommé [!DNL Data Connection].
![Fix](../assets/fix.svg) - Possibilité de consigner la réponse d’erreur si Adobe IMS ne parvient pas à générer le jeton d’accès.
![Fix](../assets/fix.svg) - Ajout d’un message de notification si vous tentez de synchroniser les commandes historiques mais que vous n’avez pas spécifié les informations d’identification du compte.

## 3.0.0

_10 octobre 2023_

[!BADGE Compatibilité]{type=Informative tooltip="Compatibilité"}

Il s’agit d’une version majeure. [Modifiez](install.md#update-the-data-connection) le fichier racine du compositeur.json de votre projet.

![Nouveau](../assets/new.svg) - Disponibilité générale pour [envoyer les données d’ordre historique](connect-data.md#send-historical-order-data) et état à l’Experience Platform.
![Nouveau](../assets/new.svg) - Ajout de la prise en charge d’OAuth 2.0 lorsque vous [configurez](connect-data.md#connect-commerce-data-to-adobe-experience-platform) l’extension [!DNL Data Connection].
![Nouveau](../assets/new.svg) - Prise en charge terminée pour Adobe Commerce 2.4.3.

## 2.3.0

_27 juin 2023_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) - Possibilité de [désactiver l’envoi d’événements storefront](connect-data.md#data-collection) à l’Experience Platform.
![Correctif](../assets/fix.svg) - Mise à jour des configurations de la stratégie de sécurité du contenu.
![Fix](../assets/fix.svg) - Correction de la prise en charge des événements back-office sur la version Commerce 2.4.7.
![New](../assets/new.svg) - Ajout d’un message de notification sur l’invalidation du cache lorsque vous enregistrez les modifications apportées au formulaire d’extension [!DNL Data Connection].

## 3.0.0-beta1 (interne uniquement)

_13 juin 2023_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) - (Beta) Possibilité d’ [envoyer des données d’ordre historique](connect-data.md#beta-send-historical-order-data) et l’état à l’Experience Platform.

## 2.2.0

_30 mars 2023_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![New](../assets/new.svg) - Regroupement des dépendances `commerce-data-export` et `saas-export` avec l’extension `experience-platform-connector`. Auparavant, vous deviez installer ces dépendances séparément. Ces dépendances, ainsi que la configuration du commerce, permettent le traitement côté serveur des [événements back-office](events-backoffice.md).
![New](../assets/new.svg) - Ajout d’un nouvel événement back-office appelé [`orderShipmentCompleted`](events-backoffice.md#ordershipmentcompleted).

## 2.1.1

_28 février 2023_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) - Ajout de la prise en charge de PHP 8.2 pour toutes les extensions [!DNL Data Connection].

## 2.1.0

_17 janvier 2023_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) - Mise à jour de l’ [[!DNL Data Connection] extension Admin](connect-data.md) afin que vous puissiez spécifier votre propre SDK Web AEP (alliage).
![Correctif](../assets/fix.svg) Remplacé par `identityMap` au lieu de `personID` lors de la définition de l’identité principale pour toutes les données transmises à la périphérie.

## 2.0.1

_10 novembre 2022_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Fix](../assets/fix.svg) - Désormais, le contexte Adobe Experience Platform est défini uniquement après le chargement du collecteur d’événements Storefront et du SDK d’événements Storefront.

## 2.0.0

_12 octobre 2022_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) - Possibilité de spécifier votre propre SDK Web AEP lors de la [connexion](connect-data.md) de votre instance Adobe Commerce à l’Experience Platform.
![Correctif](../assets/fix.svg) - Mise à jour de l’exigence de portée de la banque de données afin que les identifiants de la banque de données soient définis sur le site web plutôt que sur l’aperçu du magasin.

## 1.0.0

_9 août 2022_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) - Disponibilité générale
