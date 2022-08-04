---
title: Présentation du guide
description: Le connecteur Adobe Experience Platform pour Adobe Commerce connecte votre [!DNL Commerce] vers d’autres produits Adobe Experience Cloud.
exl-id: a8362e71-e21c-4b1d-8e3f-336e748e1018
source-git-commit: 15b7a8be65e5063606bb58755d0719b0ca54de37
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 0%

---

# Présentation du connecteur Experience Platform

L’extension de connecteur Experience Platform permet aux marchands Adobe Commerce d’envoyer des données à Adobe Experience Platform Edge afin que d’autres produits Adobe Experience Cloud, tels qu’Adobe Analytics et Adobe Target, puissent utiliser cette fonctionnalité. [!DNL Commerce] data. En connectant votre [!DNL Commerce] pour d’autres produits dans Adobe Experience Cloud, vous pouvez exécuter des tâches, telles que l’analyse du comportement des utilisateurs sur votre site, effectuer des tests AB et créer des campagnes personnalisées.

Les événements Storefront capturent les interactions d’acheteurs, telles que `View Page`, `View Product`, `Add to Cart`, etc. Les données capturées ne contiennent pas d’informations d’identification personnelle (PII). Tous les identifiants d’utilisateur, tels que les identifiants de cookie et les adresses IP, sont strictement anonymisés. [En savoir plus](https://www.adobe.com/privacy/experience-cloud.html). Consultez la liste complète des [événements storefront](events.md).

## Prérequis pour l’utilisation du connecteur Experience Platform {#prereqs}

Pour utiliser le connecteur Experience Platform, vous devez d&#39;abord :

- Remplissez les éléments suivants : [formulaire](https://forms.office.com/pages/responsepage.aspx?id=Wht7-jR7h0OUrtLBeN7O4VH_dtG9hJVAk_TqGkZC2DxUM1FSWkdJOE41UVpUWUw0M1JWV0RKS1VXQi4u) et Adobe vous donnera accès aux flux de données et à Adobe Experience Platform (si nécessaire).

Lorsque l’accès est accordé :

1. [Se connecter](https://helpx.adobe.com/manage-account/using/access-adobe-id-account.html) à votre compte d’Adobe.
1. Regardez votre [organization](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=en#concept_EA8AEE5B02CF46ACBDAD6A8508646255). L’ID d’organisation est l’ID associé à votre société Experience Cloud configurée. Cet identifiant est une chaîne alphanumérique de 24 caractères, suivie de (et doit inclure) `@AdobeOrg`.
1. Créez ou mettez à jour votre [Schéma XDM](update-xdm.md) avec des groupes de champs spécifiques à Commerce.
1. [Création d’un flux de données](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html?lang=en) et sélectionnez le schéma XDM contenant le schéma spécifique au commerce. **Groupes de champs**.

>[!NOTE]
>
> L’ID d’organisation et le flux de données sont utilisés pour connecter votre instance Adobe Commerce à Adobe Experience Platform.

## Étapes suivantes

- Installez le [Extension du connecteur Experience Platform](install.md).

   L’extension Experience Platform Connector est installée à partir de la ligne de commande du serveur et se connecte à votre installation Adobe Commerce en tant que [service](../landing/saas.md). Une fois le processus terminé, le connecteur Experience Platform s’affiche sur la **Système** sous **Services** dans le [!DNL Commerce] _Administration_.
- [Chargement de profils d’acheteur](profile.md) à Adobe Experience Platform afin que les données de storefront puissent être attribuées à des acheteurs spécifiques afin d’améliorer leur expérience d’achat.

## Audience

Ce guide est destiné au commerçant Adobe Commerce qui doit connecter ses données Adobe Commerce storefront à d’autres produits Adobe DX.

### Prise en charge des PWA Studio

Voir [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/aep/) documentation pour plus d’informations sur l’utilisation du connecteur Experience Platform dans un storefront de PWA Studio.

## Problèmes connus

Actuellement, le connecteur Experience Platform présente les problèmes connus suivants :

- Les événements de recherche ne sont pas pris en charge sur une édition Adobe Commerce Enterprise avec le module B2B installé.
- Les données de storefront prennent environ une heure pour aller d’Adobe Commerce aux différentes destinations après la connexion à Adobe Experience Platform Edge.

## Assistance

Si vous avez besoin d’informations ou si vous avez des questions qui ne sont pas abordées dans ce guide, publiez-les sur le canal de Slack suivant :

- `#beacon-ama`
