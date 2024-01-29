---
title: Présentation du guide
description: Découvrez comment intégrer des données Adobe Commerce à Adobe Experience Platform à l’aide du [!DNL Data Connection] extension .
exl-id: a8362e71-e21c-4b1d-8e3f-336e748e1018
recommendations: noCatalog
source-git-commit: b2ef02d6d1efbd1d2bc1d386517f050f56d5d864
workflow-type: tm+mt
source-wordcount: '1671'
ht-degree: 0%

---

# [!DNL Data Connection] Introduction

>[!IMPORTANT]
>
>Le connecteur Experience Platform a été renommé en [!DNL Data Connection].

La variable [!DNL Data Connection] L’extension connecte votre instance web Adobe Commerce à Adobe Experience Platform et au réseau Edge. Découvrez comment [intégrer](./mobile-sdk-epc.md) le SDK Adobe Experience Platform Mobile avec Commerce.

Votre boutique Commerce contient une mine de données. Les informations sur la manière dont vos acheteurs parcourent, affichent et finissent par acheter les produits de votre site peuvent vous révéler des opportunités pour créer une expérience d’achat plus personnalisée. Bien que ces données puissent informer les fonctionnalités commerciales natives telles que les règles de prix de panier et les blocs dynamiques, les données restent cloisonnées dans votre instance Commerce.

Adobe Experience Platform fournit une suite de technologies qui, lorsqu’elles sont hydratées avec les données de votre boutique de commerce, peuvent distribuer ces données par le biais du réseau Edge vers d’autres produits DX d’Adobe pour déverrouiller les informations sur le comportement d’achat de votre acheteur. Grâce à ces informations détaillées, vous pouvez créer une expérience d’achat plus personnalisée sur tous les canaux.

L’image suivante montre comment vos données Commerce passent de votre magasin à d’autres produits DX d’Adobe :

![Flux de données vers le serveur Experience Platform](assets/commerce-edge.png)

Dans l’image ci-dessus, vos données storefront et back-office sont envoyées au périphérique Experience Platform à l’aide d’un SDK, d’une API et d’un connecteur source. Vous n’avez pas besoin de comprendre pleinement le fonctionnement de ces pièces, car l’extension gère la complexité du partage de données pour vous. Lorsque les données d’événement se trouvent à la périphérie, vous pouvez extraire ces données dans d’autres applications Experience Platform. Par exemple :

| Application | Objectif | Cas d’utilisation |
|---|---|---|
| [Adobe [!DNL Real-Time CDP]](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/overview.html) | Service de gestion des profils et de segmentation | **Segmentation de l’historique des achats**: les marchands peuvent identifier les clients qui achètent un article selon une période donnée (mensuelle, trimestrielle, annuelle, etc.). Les vendeurs peuvent alors créer des segments pour ces clients et les cibler pour des promotions, des campagnes et comme _haut de l’entonnoir_ données pour les prospects pour les services d’abonnement.<br> **Segmentation basée sur les catégories**: les marchands peuvent voir quelle catégorie de produits ont été achetés.<br> **Segmentation basée sur les offres**: les marchands peuvent identifier les clients qui renvoient régulièrement des produits. Les offres et les remises qui leur sont accordées peuvent désormais être plus intelligentes. Par exemple, la livraison gratuite peut être supprimée pour un client qui renvoie tout le temps des produits.<br> **Ciblage analogue**: A _Audience Lookalike_ est une méthodologie utilisée par un commerçant pour ses promotions afin d’atteindre de nouvelles personnes susceptibles de s’intéresser à leur activité car elles partagent des caractéristiques similaires à celles de vos clients existants. Les segments Lookalike peuvent être créés en fonction des données comportementales et transactionnelles.<br> **Propension du client**: les changements de comportement des clients peuvent être identifiés à la suite des profils client plus profonds qui peuvent être créés à partir des données transactionnelles. La confiance dans le score de propension sera plus élevée, car les données entrant dans les calculs, telles que les retours de produits et les configurations de produits, seront plus nombreuses.<br> **Vente croisée**: un marchand peut identifier de fortes opportunités de ventes croisées et de ventes consécutives à partir des informations granulaires capturées dans Commerce. |
| [Client [!DNL Journey Analytics]](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-overview/cja-overview.html) | Analyse approfondie de l’parcours Commerce complet | **Tendances saisonnières**: un commerçant peut identifier les tendances saisonnières, ce qui l’aide à se préparer au changement périodique de la demande pour des produits particuliers. En outre, les marchands peuvent identifier les changements de popularité globale de n’importe quel produit au fil des ans.<br> **Analyse des conversions**: en sachant quand un produit a été acheté, ainsi que l’accès aux événements d’impression du storefront, les marchands peuvent générer un profil riche du client pour effectuer une analyse de conversion. |
| [Adobe [!DNL Analytics]](https://experienceleague.adobe.com/docs/analytics/analyze/admin-overview/analytics-overview.html) | Analyse approfondie du comportement des clients et des performances de campagne | **Retours de commande**: les marchands peuvent identifier les clients et les segments de clients plus importants qui ont un modèle de renvoi de produits. Cela permet aux commerçants d’améliorer leur stratégie commerciale tout en comprenant à quoi ressemble leur comportement de base de clients.<br> **Adresse de commande**: en fonction de l’adresse de livraison, un marchand peut déterminer si les commandes sont passées par les clients eux-mêmes ou si elles sont destinées à une autre personne ou entité.<br> **Tendances saisonnières**: un commerçant peut identifier les tendances saisonnières, ce qui l’aide à se préparer au changement périodique de la demande pour des produits particuliers. En outre, les marchands peuvent identifier les changements de popularité globale de n’importe quel produit au fil des ans.<br> **Analyse des conversions**: en sachant quand un produit a été acheté, ainsi que l’accès aux événements d’impression du storefront, les marchands peuvent générer un profil riche du client pour effectuer une analyse de conversion. **Remarque** Adobe Analytics ne prend en charge que les données d’événement comportemental (storefront). Adobe Analytics ne prend pas en charge les données d’événement transactionnel (backoffice). |
| [Adobe [!DNL Journey Optimizer]](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/get-started.html) | Orchestration des campagnes sur plusieurs canaux | **Parcours basés sur le comportement**: les commerçants peuvent cibler un client qui a acheté un téléphone mobile il y a deux ans en suggérant d’acheter le nouveau modèle. Les commerçants peuvent créer des campagnes et des promotions personnalisées pour ces clients et utiliser les fonctionnalités d’email et de SMS pour atteindre ces clients. En outre, les marchands peuvent utiliser l’ordre historique et les données comportementales pour identifier les tendances. Par exemple, un client qui a acheté un article avec une configuration particulière dans le passé et qui envisage maintenant d’acheter le même produit à nouveau, peut voir son parcours d’achat amélioré en lui donnant visibilité et accès aux mêmes configurations de produit.<br> **Personnalisation**: avec accès aux informations de profil du client, [!DNL Journey Optimizer] peut déverrouiller des parcours hautement personnalisés permettant aux commerçants de contacter les clients sur plusieurs canaux différents.<br> **Nouveau profil créé**: les e-mails de bienvenue et les activités promotionnelles peuvent encourager et influencer les nouveaux clients dans leurs parcours d’achats.<br> **Profil supprimé**: les vendeurs peuvent choisir d’arrêter l’envoi d’emails promotionnels aux clients qui ont fermé leur compte. Les commerçants peuvent également créer des campagnes pour reconquérir les clients perdus. |

## Récupérer les données Experience Platform dans Commerce

Envoi de données Commerce à l’Experience Platform à l’aide de la variable [!DNL Data Connection] est l’un des aspects des fonctionnalités de partage de données de Commerce. L’autre côté, qui est une extension facultative, est appelée [Audience Activation](https://experienceleague.adobe.com/docs/commerce-admin/customers/audience-activation.html). Cette extension vous permet de créer des audiences dans Real-Time CDP et de déployer ces audiences dans votre boutique Commerce afin d’informer les règles de prix du panier et les blocs dynamiques.

À un niveau élevé, le flux de données de votre boutique Commerce vers l’Experience Platform et de retour par l’extension d’Audience Activation ressemble à ce qui suit :

![[!DNL Data Connection] flow](assets/data-connection.png)

Une fois que vous avez configuré la connexion entre Commerce et Experience Platform et Experience Platform à Commerce, les données continuent à circuler. Vous n’avez pas besoin de vous reconnecter, sauf si une mise à niveau vous l’exige.

## Concepts

Le partage de données entre ces deux systèmes nécessite de comprendre plusieurs concepts.

* **Données** - Les données qui sont partagées avec l’Experience Platform sont des données collectées à partir des événements du navigateur sur votre vitrine et des événements du back-office sur le serveur. Les événements de storefront sont capturés à partir des interactions des clients sur le site et incluent des événements tels que [`addToCart`](events.md#addtocart), [`pageView`](events.md#pageview), [`createAccount`](events.md#createaccount), [`editAccount`](events.md#editaccount), [`startCheckout`](events.md#startcheckout), [`completeCheckout`](events.md#completecheckout), [`signIn`](events.md#signin), [`signOut`](events.md#signout), etc. Voir [événements storefront](events.md#storefront-events) pour obtenir la liste complète des événements storefront. Événements côté serveur ou back-office, y compris [état de la commande](events.md#back-office-events) des informations, telles que [`orderPlaced`](events.md#orderplaced), [`orderReturned`](events.md#orderitemreturncompleted), [`orderShipped`](events.md#ordershipmentcompleted), [`orderCancelled`](events.md#ordercancelled), etc. Voir [événements back office](events.md#back-office-events) pour obtenir la liste complète des événements back-office.

* **Experience Platform et réseau Edge** - entrepôt de données pour la plupart des produits DX Adobes. Les données envoyées à l’Experience Platform sont ensuite propagées aux produits DX Adobes par le biais du réseau Edge Experience Platform. Par exemple, vous pouvez lancer Journey Optimizer, récupérer vos données d’événement Commerce spécifiques à partir de la périphérie et créer un courrier électronique de panier abandonné dans Journey Optimizer. Journey Optimizer peut alors envoyer cet email s’il existe des paniers abandonnés dans votre boutique de commerce. En savoir plus sur les [Experience Platform et réseau Edge](https://experienceleague.adobe.com/docs/platform-learn/data-collection/web-sdk/overview.html).

* **Schéma** - Le schéma est ce qui décrit la structure des données envoyées. Avant que l’Experience Platform puisse ingérer vos données Commerce, vous devez composer un schéma pour décrire la structure des données et fournir des contraintes au type de données pouvant être contenues dans chaque champ. Les schémas se composent d’une classe de base et de zéro ou plusieurs groupes de champs de schéma. Le schéma utilise la structure XDM, que tous les produits DX d’Adobe peuvent lire. Ainsi, lorsque vous envoyez vos données à l’Experience Platform, vous pouvez vous assurer que vos données sont bien comprises dans tous les produits DX. En savoir plus sur [schémas](https://experienceleague.adobe.com/docs/experience-platform/xdm/home.html).

* **Jeu de données** - Une structure de stockage et de gestion pour une collecte de données, généralement un tableau contenant un schéma (des colonnes) et des champs (des lignes). Les jeux de données contiennent également des métadonnées qui décrivent divers aspects des données qu’ils stockent. Toutes les données correctement ingérées dans Adobe Experience Platform sont contenues dans des jeux de données. En savoir plus sur [jeux de données](https://experienceleague.adobe.com/docs/experience-platform/catalog/datasets/overview.html).

* **Datastream** - Identifiant qui permet aux données de passer de Adobe Experience Platform à d’autres produits DX Adobe. Cet identifiant doit être associé à un site web spécifique dans votre instance Adobe Commerce spécifique. Lorsque vous créez ce flux de données, spécifiez le schéma XDM que vous avez créé ci-dessus. En savoir plus sur [datastreams](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html).

## Architecture prise en charge

La variable [!DNL Data Connection] est disponible sur les architectures suivantes :

* PHP/Luma
* [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/aep/)
* [AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/content-and-commerce/integrations/aep.html)

## Conditions préalables

Pour utiliser la variable [!DNL Data Connection] , vous devez disposer des éléments suivants :

* Adobe Commerce 2.4.4 ou version ultérieure
* Adobe ID et ID d’organisation
* [Adobe de la couche de données client (ACDL)](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/client/client-data-layer/overview.html), qui est nécessaire pour collecter les données d’événement storefront
* Droits pour d’autres produits DX d’Adobe.

## Étapes d’intégration

À un niveau élevé, activez la variable [!DNL Data Connection] l’extension comprend les étapes suivantes :

1. [Installer](install.md) la valeur [!DNL Data Connection] extension .
1. [Se connecter](https://helpx.adobe.com/manage-account/using/access-adobe-id-account.html) à votre compte d’Adobe et [afficher pour confirmer](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html#concept_EA8AEE5B02CF46ACBDAD6A8508646255) ID d’organisation. L’ID d’organisation est l’ID associé à votre société Experience Cloud configurée. Cet identifiant est une chaîne alphanumérique de 24 caractères, suivie de (et doit inclure) `@AdobeOrg`.
1. [Créer ou mettre à jour](update-xdm.md) votre schéma XDM avec des groupes de champs spécifiques à Commerce.
1. [Création d’un jeu de données](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) en fonction du schéma que vous avez créé ou mis à jour. Ce jeu de données contient les données Commerce que vous envoyez.
1. [Création d’un flux de données](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) et sélectionnez le schéma XDM contenant les groupes de champs spécifiques à Commerce.
1. [Connexion à Commerce Services](../landing/saas.md).
1. [Connexion à Adobe Experience Platform](connect-data.md).

Le reste de ce guide vous guide tout au long de ces étapes afin que vous puissiez vous familiariser rapidement et commencer à utiliser la puissance des produits DX d’Adobe dans votre boutique de commerce.

>[!NOTE]
>
>Pour les développeurs mobiles, découvrez comment [intégrer](./mobile-sdk-epc.md) le SDK Adobe Experience Platform Mobile avec Commerce.

## Audience

Ce guide est destiné au commerçant Adobe Commerce qui souhaite enrichir et personnaliser sa boutique Commerce afin d’améliorer l’expérience d’achat de ses clients.

## Assistance

Si vous avez besoin d’informations ou si vous avez des questions qui ne sont pas abordées dans ce guide, utilisez les ressources suivantes :

* [Centre d’aide](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html){target="_blank"}
* [tickets d’assistance](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket){target="_blank"}: soumettez un ticket pour recevoir de l’aide supplémentaire.
