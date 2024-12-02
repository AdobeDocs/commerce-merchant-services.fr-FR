---
title: Présentation de l’intégration pour les services d’exécution de magasin
description: '[!DNL Live Search] Flux d’intégration, configuration requise, limites et limites.'
role: Admin, Leader
level: Intermediate
feature: Shipping/Delivery, Install
exl-id: f8e403ac-9bbd-4ea2-b209-9b1a8d1e32a2
source-git-commit: 36b57648e156ead801764f3ee4e5e6a0f3245fe6
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# Présentation de l’intégration pour l’exécution du magasin

Commencez avec [!DNL Store Fulfillment for Adobe Commerce by Walmart Commerce Technologies] en configurant, configurant et activant les composants suivants :

- **Store Fulfillment extension** - Installez et configurez cette extension tierce sur votre instance Adobe Commerce. Après l’installation, vous pouvez configurer et gérer la solution Store Fulfillment à partir de l’administrateur pour prendre en charge les scénarios [!DNL buys online, pickup in store] (BOPIS) dans le storefront Commerce.

  ![[!DNL Store Fulfillment Service] configuration dans la vue d’administration](assets/store-fulfillment-admin-home.png)

- **Compte d’exécution de magasin** : au cours du processus d’activation, un gestionnaire de compte crée votre compte d’exécution de magasin et vous fournit les informations et les informations d’identification du compte. Ces informations d’identification sont requises pour activer la connexion entre Adobe Commerce et la solution d’exécution de magasin.

- **Application d’assistance en magasin** : fournit des associés de magasin à un workflow d’exécution de magasin de bout en bout pour gérer les commandes BOPIS à partir d’appareils mobiles. Store Associates peut télécharger et installer [!DNL Store Assist] de Walmart pour les appareils iOS et Android™. Le processus d’intégration des applications est géré par le Centre client Walmart Commerce Technologies en tant que processus distinct. Cependant, [certains paramètres de configuration d’application](user-setup.md) sont renseignés à partir de l’administrateur Adobe Commerce.

  | Application d’aide à la boutique - Vue de démarrage | Application d’assistance de la boutique - Mode Modules |
  |-------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------|
  | ![[!DNL Store Assist App Getting Started] vue sur appareil mobile](assets/store-assist-get-started-small.png) | ![[!DNL Store Assist App Orders view] sur appareil mobile](assets/store-assist-orders-small.png) |

## Etapes de configuration

- **Inscrivez-vous à[!DNL Store Fulfillment for Adobe Commerce by Walmart Commerce Technologies]** : remplissez le formulaire d’inscription sur [business.adobe.com](https://business.adobe.com/resources/store-fulfillment.html) ou contactez votre gestionnaire de compte Adobe Commerce pour obtenir de l’aide.

- **Lancer la demande d’approvisionnement pour l’exécution du magasin** : remplissez le formulaire d’ingestion fourni par votre gestionnaire de compte pour fournir les informations nécessaires au démarrage du processus d’approvisionnement.

- **Obtenir les informations d’identification de votre compte d’exécution de magasin** : une fois votre compte d’exécution de magasin créé pour vous, vous recevez les informations d’identification requises pour intégrer la solution d’exécution de magasin à Adobe Commerce.

- **[Téléchargez le code source pour installer l&#39; [!DNL Store Fulfillment] extension](install.md)**

## Étapes d’intégration

1. [Installez l’extension Store Fulfillment pour Adobe Commerce](install.md).

1. Depuis l’administrateur, [activez la solution](enable-general.md).

1. [Configurez l’extension d’exécution de magasin à partir de l’administrateur Adobe Commerce](service-config-settings-overview.md).

1. [ Connectez-vous au service  [!DNL Store Fulfillment]  à l’aide des informations d’identification d’exécution de magasin qui vous ont été fournies ](connect-set-up-service.md).

1. [ Créez des utilisateurs et des rôles pour l’application d’assistance de la boutique ](user-setup.md).

1. [Téléchargez l&#39;application  [!DNL Store Assist]  de Walmart sur l&#39;appareil de votre choix. L’application est disponible sur les boutiques Apple app (iOS) et Google Play (Android™)](app-setup.md).

Une fois que vous avez installé, configuré et intégré avec succès et que vous avez accès à l’application [!DNL Store Assist], vous pouvez [ commencer à créer des commandes et des tests](test-and-deploy.md).
