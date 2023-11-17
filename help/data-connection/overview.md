---
title: Présentation du guide
description: Découvrez comment intégrer des données Adobe Commerce à Adobe Experience Platform à l’aide du [!DNL Data Connection] extension .
exl-id: a8362e71-e21c-4b1d-8e3f-336e748e1018
recommendations: noCatalog
source-git-commit: 4a5877d6e1a5c7d840e36f4913306b0c440bbac5
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 0%

---

# [!DNL Data Connection] aperçu

>[!IMPORTANT]
>
>Le connecteur Experience Platform a été renommé en [!DNL Data Connection].

La variable [!DNL Data Connection] l’extension permet aux marchands Adobe Commerce d’envoyer [storefront](events.md#storefront-events) et [back office](events.md#back-office-events) données vers Adobe Experience Platform Edge afin que d’autres produits Adobe Experience Cloud, tels qu’Adobe Analytics et Adobe Journey Optimizer, puissent utiliser ces données Commerce. En connectant vos données Commerce à d’autres produits dans Adobe Experience Cloud, vous pouvez exécuter des tâches telles que l’analyse du comportement des utilisateurs sur votre site, effectuer des tests AB et créer des campagnes personnalisées.

[Événements Storefront](events.md#storefront-events) capturer les interactions d’acheteurs, telles que `View Page`, `View Product`, `Add to Cart`, et [liste des demandes](events.md#b2b-events) informations (pour les commerçants B2B). [Retour au bureau](events.md#back-office-events) les événements capturent des informations sur l’état d’une commande, par exemple si une commande a été passée, annulée, remboursée, expédiée ou terminée. Les données capturées ne contiennent pas d’informations d’identification personnelle (PII). Tous les identifiants d’utilisateur, tels que les identifiants de cookie et les adresses IP, sont strictement anonymisés. [En savoir plus](https://www.adobe.com/privacy/experience-cloud.html).

La variable [!DNL Data Connection] l’extension apparaît dans l’Admin Commerce sous **Système** > Services > **[!DNL Data Connection]**.

![[!DNL Data Connection] vue d’administration de l’extension](assets/epc-adminui.png)

## Conditions préalables {#prereqs}

Pour utiliser la variable [!DNL Data Connection] , vous devez disposer des éléments suivants :

- Adobe Commerce 2.4.3 ou version ultérieure
- Adobe ID et ID d’organisation
- [Adobe de la couche de données client (ACDL)](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/client/client-data-layer/overview.html). La collecte de données ACDL est requise pour collecter les données d’événement de vitrine.
- Droits sur d’autres produits DX Adobes

## Étapes d’intégration

1. [Installer](install.md) la valeur [!DNL Data Connection] extension .
1. [Se connecter](https://helpx.adobe.com/manage-account/using/access-adobe-id-account.html) à votre compte d’Adobe et [afficher pour confirmer](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html#concept_EA8AEE5B02CF46ACBDAD6A8508646255) ID d’organisation. L’ID d’organisation est l’ID associé à votre société Experience Cloud configurée. Cet identifiant est une chaîne alphanumérique de 24 caractères, suivie de (et doit inclure) `@AdobeOrg`.
1. [Créer ou mettre à jour](update-xdm.md) votre schéma XDM avec des groupes de champs spécifiques à Commerce.
1. [Création d’un jeu de données](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) en fonction du schéma que vous avez créé ou mis à jour. Ce jeu de données contient les données Commerce que vous envoyez.
1. [Création d’un flux de données](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) et sélectionnez le schéma XDM contenant les groupes de champs spécifiques à Commerce.
1. [Connexion à Commerce Services](../landing/saas.md).
1. [Connexion à Adobe Experience Platform](connect-data.md).

## Audience

Ce guide est destiné au commerçant Adobe Commerce qui souhaite connecter ses données Adobe Commerce à d’autres produits Adobe DX.

### Prise en charge des PWA Studio

Voir [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/aep/) documentation pour plus d’informations sur l’utilisation de la variable [!DNL Data Connection] dans un storefront PWA Studio.

### Prise en charge AEM {#aem-support}

Voir [AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/content-and-commerce/integrations/aep.html) documentation pour savoir comment envoyer des données d’événement storefront d’une page de produit AEM rendue à l’Experience Platform à l’aide de CIF - [!DNL Data Connection] extension .

Si vous avez besoin d’informations ou si vous avez des questions qui ne sont pas abordées dans ce guide, utilisez les ressources suivantes :

- [Centre d’aide](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html){target="_blank"}
- [tickets d’assistance](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket){target="_blank"}: soumettez un ticket pour recevoir de l’aide supplémentaire.