---
title: Présentation du guide
description: Découvrez comment intégrer des données Adobe Commerce à Adobe Experience Platform à l’aide de l’extension  [!DNL Data Connection] .
exl-id: a8362e71-e21c-4b1d-8e3f-336e748e1018
recommendations: noCatalog
source-git-commit: b5727c90737ecfd237dd143801152f25600c3f97
workflow-type: tm+mt
source-wordcount: '1752'
ht-degree: 0%

---

# [!DNL Data Connection] Introduction

>[!IMPORTANT]
>
>Le connecteur Experience Platform a été renommé [!DNL Data Connection].

L’extension [!DNL Data Connection] connecte votre instance web Adobe Commerce à Adobe Experience Platform et à l’Edge Network. Pour les développeurs d’applications mobiles, vous utilisez le SDK Mobile Adobe Experience Platform avec Commerce pour capturer et envoyer des données Commerce à l’Experience Platform. [En savoir plus](./mobile-sdk-epc.md).

Votre boutique Commerce contient une mine de données. Les informations sur la manière dont vos acheteurs parcourent, affichent et finissent par acheter les produits de votre site peuvent vous révéler des opportunités pour créer une expérience d’achat plus personnalisée. Bien que ces données puissent informer les fonctionnalités Commerce natives telles que les règles de prix du panier et les blocs dynamiques, les données restent cloisonnées dans votre instance Commerce.

Adobe Experience Platform fournit une suite de technologies qui, lorsqu’elles sont hydratées avec les données de votre boutique Commerce, peuvent distribuer ces données par l’intermédiaire de l’Edge Network vers d’autres produits DX Adobes afin de déverrouiller les informations sur le comportement d’achat de votre acheteur. Grâce à ces informations détaillées, vous pouvez créer une expérience d’achat plus personnalisée sur tous les canaux.

L’image suivante montre comment vos données Commerce circulent de votre boutique vers d’autres produits DX Adobe lorsque l’extension [!DNL Data Connection] est installée et configurée.

![Flux de données vers le serveur Experience Platform ](assets/commerce-edge.png)

Dans l’image ci-dessus, vos données de comportement, de back-office et de profil client sont envoyées au serveur Edge Experience Platform à l’aide d’un SDK, d’une API et d’un connecteur source. Vous n’avez pas besoin de comprendre pleinement le fonctionnement de ces pièces, car l’extension gère la complexité du partage de données pour vous. Lorsque les données d’événement se trouvent à la périphérie, vous pouvez extraire ces données dans d’autres applications Experience Platform. Par exemple :

| Application | Objectif | Cas d’utilisation |
|---|---|---|
| [Adobe [!DNL Real-Time CDP]](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/intro/rtcdp-intro/overview.html?lang=fr) | Service de gestion des profils et de segmentation | **Segmentation de l’historique des achats** : les vendeurs peuvent identifier les clients qui achètent un article selon une période spécifique (mensuelle, trimestrielle, annuelle, etc.). Les vendeurs peuvent ensuite créer des segments pour ces clients et les cibler pour les promotions, les campagnes et en tant que données _top de l’entonnoir_ pour les pistes des services d’abonnement.<br> **Segmentation par catégorie** : les vendeurs peuvent voir quelle catégorie de produits a été achetée.<br> **Segmentation basée sur les offres** : les vendeurs peuvent identifier les clients qui renvoient régulièrement des produits. Les offres et les remises qui leur sont accordées peuvent désormais être plus intelligentes. Par exemple, la livraison gratuite peut être supprimée pour un client qui renvoie tout le temps des produits.<br> **Ciblage de sosiles** : une _audience sosiles_ est une méthodologie utilisée par un commerçant pour que ses promotions atteignent de nouvelles personnes susceptibles de s’intéresser à leur activité car elles partagent des caractéristiques similaires avec vos clients existants. Les segments Lookalike peuvent être créés en fonction des données comportementales et transactionnelles.<br> **Propensité de la clientèle** : les changements de comportement des clients peuvent être identifiés à la suite des profils client plus profonds qui peuvent être créés à partir des données transactionnelles. Il y aura une confiance plus élevée dans le score de propension, car il y aura plus de données circulant dans les calculs, comme les retours de produits et les configurations de produits.<br> **Vente croisée** : un commerçant peut identifier de fortes opportunités de vente croisée et de vente incitative à partir des informations granulaires capturées dans Commerce. |
| [Client [!DNL Journey Analytics]](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-overview/cja-overview.html) | Analyse approfondie du parcours Commerce complet | **Tendances saisonnières** : un commerçant peut identifier des tendances saisonnières, ce qui l’aide à se préparer au changement périodique de la demande pour des produits particuliers. En outre, les marchands peuvent identifier les changements de popularité globale de n’importe quel produit au fil des années.<br> **Analyse de conversion** : en sachant quand un produit a été acheté, ainsi que l’accès aux événements d’impression du storefront, les marchands peuvent générer un profil riche du client pour effectuer une analyse de conversion. |
| [Adobe [!DNL Analytics]](https://experienceleague.adobe.com/docs/analytics/analyze/admin-overview/analytics-overview.html) | Analyse approfondie du comportement des clients et des performances de campagne | **Renvoie des commandes** : les vendeurs peuvent identifier les clients et les segments de clients plus importants qui ont un modèle de retour de produits. Cela permet aux commerçants d’améliorer leur stratégie de commerce en comprenant à quoi ressemble leur comportement de base de clients.<br> **Adresse de la commande** : en fonction de l’adresse de livraison, un commerçant peut comprendre si les commandes sont passées par les clients eux-mêmes ou si elles le sont pour une autre personne ou entité.<br> **Tendances de saisonnalité** : un commerçant peut identifier des tendances saisonnières, ce qui l’aide à se préparer au changement périodique de la demande pour des produits particuliers. En outre, les marchands peuvent identifier les changements de popularité globale de n’importe quel produit au fil des années.<br> **Analyse de conversion** : en sachant quand un produit a été acheté, ainsi que l’accès aux événements d’impression du storefront, les marchands peuvent générer un profil riche du client pour effectuer une analyse de conversion. **Remarque** Adobe Analytics prend uniquement en charge les données d’événement comportemental (storefront). Adobe Analytics ne prend pas en charge les données d’événement transactionnel (backoffice). |
| [Adobe [!DNL Journey Optimizer]](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/get-started.html) | Orchestration des campagnes sur plusieurs canaux | **parcours basés sur le comportement** : les vendeurs peuvent cibler un client qui a acheté un téléphone mobile il y a deux ans en suggérant qu’il achète le nouveau modèle. Les commerçants peuvent créer des campagnes et des promotions personnalisées pour ces clients et utiliser les fonctionnalités d’email et de SMS pour atteindre ces clients. En outre, les marchands peuvent utiliser l’ordre historique et les données comportementales pour identifier les tendances. Par exemple, un client qui a acheté un article avec une configuration particulière dans le passé et qui cherche à nouveau à acheter le même produit peut voir son parcours d’achat amélioré en lui donnant visibilité et accès aux mêmes configurations de produit.<br> **Personalization** : avec accès aux informations de profil client, [!DNL Journey Optimizer] peut déverrouiller des parcours hautement personnalisés permettant aux marchands de contacter les clients sur plusieurs canaux différents.<br> **Nouveau profil créé** : les e-mails de bienvenue et les activités promotionnelles peuvent encourager et influencer les nouveaux clients dans leurs parcours d’achats.<br> **Profil supprimé** : les vendeurs peuvent choisir d’arrêter l’envoi d’emails promotionnels aux clients qui ont fermé leur compte. Les commerçants peuvent également créer des campagnes pour reconquérir les clients perdus. |

## Récupération des données Experience Platform dans Commerce

L’envoi de vos données Commerce à l’Experience Platform à l’aide de l’extension [!DNL Data Connection] est l’un des côtés des fonctionnalités de partage de données Commerce. L’autre côté, qui est une extension facultative, est appelée [Audience Activation](https://experienceleague.adobe.com/docs/commerce-admin/customers/audience-activation.html). Cette extension vous permet de créer des audiences dans Real-Time CDP et de les déployer dans votre boutique Commerce afin d’informer les règles de prix du panier, les règles de produit associées et les blocs dynamiques.

À un haut niveau, le flux de données de votre boutique Commerce vers l’Experience Platform et de retour par l’extension d’Audience Activation ressemble à ce qui suit :

![[!DNL Data Connection] flow](assets/data-connection.png)

Une fois que vous avez configuré la connexion entre Commerce à l’Experience Platform et l’Experience Platform à Commerce, les données continuent à circuler. Vous n’avez pas besoin de vous reconnecter, sauf si une mise à niveau vous l’exige.

## Concepts

Le partage de données entre ces deux systèmes nécessite de comprendre plusieurs concepts.

* **Data** - Les données qui sont partagées avec l’Experience Platform sont des données collectées à partir des événements du navigateur sur votre vitrine, des événements du back-office sur le serveur et des données d’enregistrement de profil. Les événements Storefront sont capturés à partir des interactions des clients sur le site et incluent des événements tels que [`addToCart`](events.md#addtocart), [`pageView`](events.md#pageview), [`createAccount`](events.md#createaccount), [`editAccount`](events.md#editaccount), [`startCheckout`](events.md#startcheckout), [`completeCheckout`](events.md#completecheckout), [`signIn`](events.md#signin), [`signOut`](events.md#signout), etc. Voir [storefront events](events.md#storefront-events) pour obtenir la liste complète des événements storefront. Les événements côté serveur ou back-office incluent des informations [order status](events-backoffice.md#order-status), telles que [`orderPlaced`](events-backoffice.md#orderplaced), [`orderReturned`](events-backoffice.md#orderitemreturncompleted), [`orderShipped`](events-backoffice.md#ordershipmentcompleted), [`orderCancelled`](events-backoffice.md#ordercancelled), etc. Pour obtenir la liste complète des événements back-office, reportez-vous à la section [événements back-office](events-backoffice.md) . Les données d’enregistrement de profil contiennent des informations lorsqu’un nouveau profil est créé, mis à jour ou supprimé. Voir [données d’enregistrement de profil](events-profilerecord.md) pour en savoir plus.

* **Experience Platform et Edge Network** - L’entrepôt de données pour la plupart des produits DX Adobes. Les données envoyées à l’Experience Platform sont ensuite propagées aux produits DX Adobe par l’intermédiaire de l’Edge Network Experience Platform. Par exemple, vous pouvez lancer Journey Optimizer, récupérer vos données d’événement Commerce spécifiques à partir de la périphérie et créer un courrier électronique de panier abandonné dans Journey Optimizer. Journey Optimizer peut alors envoyer cet email s’il existe des paniers abandonnés dans votre boutique Commerce. En savoir plus sur [Experience Platform et Edge Network](https://experienceleague.adobe.com/docs/platform-learn/data-collection/web-sdk/overview.html).

* **Schéma** - Le schéma décrit la structure des données envoyées. Avant que l’Experience Platform puisse ingérer vos données Commerce, vous devez composer un schéma pour décrire la structure des données et fournir des contraintes au type de données pouvant être contenues dans chaque champ. Les schémas se composent d’une classe de base et de zéro ou plusieurs groupes de champs de schéma. Le schéma utilise la structure XDM, que tous les produits DX d’Adobe peuvent lire. Ainsi, lorsque vous envoyez vos données à l’Experience Platform, vous pouvez vous assurer que vos données sont bien comprises dans tous les produits DX. En savoir plus sur les [schémas](https://experienceleague.adobe.com/docs/experience-platform/xdm/home.html).

* **Jeu de données** - Une structure de stockage et de gestion pour une collecte de données, généralement un tableau contenant un schéma (des colonnes) et des champs (des lignes). Les jeux de données contiennent également des métadonnées qui décrivent divers aspects des données qu’ils stockent. Toutes les données correctement ingérées dans Adobe Experience Platform sont contenues dans des jeux de données. En savoir plus sur les [jeux de données](https://experienceleague.adobe.com/docs/experience-platform/catalog/datasets/overview.html).

* **Datastream** - ID qui permet aux données de passer de Adobe Experience Platform à d’autres produits DX d’Adobe. Cet identifiant doit être associé à un site web spécifique dans votre instance Adobe Commerce spécifique. Lorsque vous créez ce flux de données, spécifiez le schéma XDM que vous avez créé ci-dessus. En savoir plus sur [datastreams](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html).

## Architecture prise en charge

L’extension [!DNL Data Connection] est disponible sur les architectures suivantes :

* PHP/Luma
* [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/aep/)
* [AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/content-and-commerce/integrations/aep.html)

>[!BEGINSHADEBOX]

## Conditions préalables

Pour utiliser l’extension [!DNL Data Connection], vous devez disposer des éléments suivants :

* Adobe Commerce 2.4.4 ou version ultérieure
* Adobe ID et ID d’organisation
* [Adobe de la couche de données client (ACDL)](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/client/client-data-layer/overview.html), nécessaire pour collecter les données d’événement du storefront
* Droits pour d’autres produits DX d’Adobe.

>[!ENDSHADEBOX]

## Étapes d’intégration

À un niveau élevé, l’activation de l’extension [!DNL Data Connection] implique les étapes suivantes :

1. [Installez ](install.md) l’extension [!DNL Data Connection].
1. [Connectez-vous](https://helpx.adobe.com/manage-account/using/access-adobe-id-account.html) à votre compte d’Adobe et [affichez pour confirmer](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html#concept_EA8AEE5B02CF46ACBDAD6A8508646255) votre ID d’organisation. L’ID d’organisation est l’ID associé à votre société Experience Cloud configurée. Cet identifiant est une chaîne alphanumérique de 24 caractères, suivie de (et doit inclure) `@AdobeOrg`.
1. Assurez-vous que vous disposez de l’autorisation [pour la collecte de données dans Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/collection/permissions.html).
1. Examinez les [types de données](data-ingestion.md) que vous pouvez collecter et envoyer.
1. Créez ou mettez à jour votre [schéma d’événement de série temporelle](update-xdm.md) ou [ schéma de données d’enregistrement de profil](profile-data.md) avec des groupes de champs spécifiques à Commerce.
1. [Créez un jeu de données](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) basé sur le schéma que vous avez créé ou mis à jour. Ce jeu de données contient les données Commerce envoyées à l’Edge Experience Platform.
1. [ Créez un flux de données ](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) et sélectionnez le schéma XDM contenant les groupes de champs spécifiques à Commerce.
1. [Connexion aux services Commerce](../landing/saas.md).
1. [Connectez-vous à Adobe Experience Platform](connect-data.md).

Le reste de ce guide vous guide tout au long de ces étapes afin que vous puissiez vous familiariser rapidement et commencer à utiliser la puissance des produits DX d’Adobe dans votre boutique Commerce.

>[!NOTE]
>
>Pour les développeurs mobiles, découvrez comment [intégrer](./mobile-sdk-epc.md) le SDK Mobile Adobe Experience Platform avec Commerce.

## Audience

Ce guide est destiné au commerçant Adobe Commerce qui souhaite enrichir et personnaliser sa boutique Commerce afin d’améliorer l’expérience d’achat de ses clients.

## Assistance

Si vous avez besoin d’informations ou si vous avez des questions qui ne sont pas abordées dans ce guide, utilisez les ressources suivantes :

* [Centre d’aide](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html){target="_blank"}
* [tickets d’assistance](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket){target="_blank"} : envoyez un ticket pour recevoir une aide supplémentaire.
