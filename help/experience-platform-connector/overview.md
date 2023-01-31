---
title: Présentation du guide
description: Découvrez comment intégrer des données Adobe Commerce à Adobe Experience Platform à l’aide du connecteur Experience Platform.
exl-id: a8362e71-e21c-4b1d-8e3f-336e748e1018
source-git-commit: 092f2f4ab9d34466d66fe5b726bfff67a1309c6f
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# Présentation du connecteur Experience Platform

L’extension de connecteur Experience Platform permet aux marchands Adobe Commerce d’envoyer des données à Adobe Experience Platform Edge afin que d’autres produits Adobe Experience Cloud, tels qu’Adobe Analytics et Adobe Target, puissent utiliser ces données Commerce. En connectant vos données Commerce à d’autres produits dans Adobe Experience Cloud, vous pouvez effectuer des tâches, telles que analyser le comportement des utilisateurs sur votre site, effectuer des tests AB et créer des campagnes personnalisées.

[Événements Storefront](events.md) capturer les interactions d’acheteurs, telles que `View Page`, `View Product`, `Add to Cart`, etc. Les données capturées ne contiennent pas d’informations d’identification personnelle (PII). Tous les identifiants d’utilisateur, tels que les identifiants de cookie et les adresses IP, sont strictement anonymisés. [En savoir plus](https://www.adobe.com/privacy/experience-cloud.html).

Le connecteur Experience Platform apparaît dans l’Admin Commerce sous **Système** > Services > **Connecteur Experience Platform**.

![Vue d’administration de l’extension du connecteur Experience Platform](assets/epc-adminui.png)

## Conditions préalables {#prereqs}

Pour utiliser le connecteur Experience Platform, vous devez disposer des éléments suivants :

- Adobe Commerce 2.4.3 ou version ultérieure
- Adobe ID et ID d’organisation
- Droits sur d’autres produits DX Adobes

## Étapes d’intégration

1. [Installer](install.md) l’extension du connecteur Experience Platform.
1. [Se connecter](https://helpx.adobe.com/manage-account/using/access-adobe-id-account.html) à votre compte d’Adobe et [view](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html#concept_EA8AEE5B02CF46ACBDAD6A8508646255) ID d’organisation. L’ID d’organisation est l’ID associé à votre société Experience Cloud configurée. Cet identifiant est une chaîne alphanumérique de 24 caractères, suivie de (et doit inclure) `@AdobeOrg`.
1. [Connexion](connect-data.md) votre instance Adobe Commerce vers Adobe Experience Platform.
1. [Créer ou mettre à jour](update-xdm.md) votre schéma XDM avec des groupes de champs spécifiques à Commerce.
1. [Création d’un jeu de données](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) en fonction du schéma que vous avez créé ou mis à jour.
1. [Création d’un flux de données](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html) et sélectionnez le schéma XDM contenant les groupes de champs spécifiques à Commerce.

## Audience

Ce guide est destiné au commerçant Adobe Commerce qui souhaite connecter ses données Adobe Commerce à d’autres produits Adobe DX.

### Prise en charge des PWA Studio

Voir [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/aep/) documentation pour plus d’informations sur l’utilisation du connecteur Experience Platform dans un storefront de PWA Studio.

### Support AEM {#aem-support}

Voir [AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/content-and-commerce/integrations/aep.html) documentation pour savoir comment envoyer des données d’événement storefront d’une page de produit AEM rendue à l’Experience Platform à l’aide de CIF - Experience Platform Connector.

Si vous avez besoin d’informations ou si vous avez des questions qui ne sont pas abordées dans ce guide, utilisez les ressources suivantes :

- [Centre d’aide](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html){target="_blank"}
- [tickets d’assistance](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket){target="_blank"}: soumettez un ticket pour recevoir une aide supplémentaire.
