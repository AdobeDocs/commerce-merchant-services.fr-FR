---
title: Présentation de l’intégration pour les services d’exécution de magasin
description: '"[!DNL Live Search] flux d’intégration, exigences système, limites et limites"'
role: User, Admin
level: Intermediate
source-git-commit: 4ea03b3be11056526adc42d875b1e26a24736d15
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# Présentation de l’intégration pour l’exécution du magasin

Prise en main d’ [!DNL Store Fulfillment for Adobe Commerce by Walmart Commerce Technologies] en configurant, configurant et activant les composants suivants :

- **Extension d’exécution de magasin**- Installez et configurez cette extension tierce sur votre instance Adobe Commerce. Une fois l’installation terminée, vous pouvez configurer et gérer la solution Store Fulfillment à partir de l’Admin pour la prise en charge. [!DNL buy online, pickup in store] Scénarios BOPIS dans le storefront Commerce.

   ![[!DNL Store Fulfillment Service] configuration dans la vue Admin](assets/store-fulfillment-admin-home.png)

- **Compte d’exécution de la boutique**-Au cours du processus d’activation, un gestionnaire de compte crée votre compte d’exécution Boutique et vous fournit les informations et les informations d’identification du compte. Ces informations d’identification sont requises pour activer la connexion entre Adobe Commerce et la solution d’exécution de magasin.

- **Application d’assistance pour la boutique**: fournit des associés de magasin à un workflow d’exécution de magasin de bout en bout pour gérer les commandes BOPIS des appareils mobiles. Store Associates peut télécharger et installer Walmart [!DNL Store Assist] pour les appareils iOS et Android. Le processus d’intégration des applications est géré par le Walmart Commerce Technology Client Center en tant que processus distinct. Cependant, [certains paramètres de configuration de l’application](user-setup.md) sont terminées à partir de l’administrateur Adobe Commerce.

   | Application d’aide à la boutique - Vue de prise en main | Application d’assistance de la boutique - Mode Modules |
   |-------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------|
   | ![[!DNL Store Assist App Getting Started] Affichage sur appareil mobile](assets/store-assist-get-started-small.png) | ![[!DNL Store Assist App Orders view] sur appareil mobile](assets/store-assist-orders-small.png) |




## Etapes de configuration

- **Inscrivez-vous à[!DNL Store Fulfillment for Adobe Commerce by Walmart Commerce Technologies]**- Remplissez le formulaire d’inscription sur [business.adobe.com](https://business.adobe.com/resources/store-fulfillment.html)ou contactez votre gestionnaire de compte Adobe Commerce pour obtenir de l’aide.

- **Lancement de la demande d’approvisionnement pour l’exécution du magasin**- Remplissez le formulaire de prise fourni par votre gestionnaire de compte pour fournir les informations nécessaires au démarrage du processus d’approvisionnement.

- **Obtention des informations d’identification de votre compte d’exécution de magasin**- Une fois votre compte d’exécution de magasin créé pour vous, vous recevez les informations d’identification requises pour intégrer la solution d’exécution de magasin à Adobe Commerce.

- **[Téléchargez le code source pour installer le [!DNL Store Fulfillment] extension](install.md)**

## Étapes d’intégration

1. [Installation de l’extension Store Fulfillment pour Adobe Commerce](install.md).

1. Depuis l’administrateur, [activer la solution](enable-general.md).

1. [Configuration de l’extension d’exécution de magasin à partir de l’administrateur Adobe Commerce](service-config-settings-overview.md).

1. [Connectez-vous au [!DNL Store Fulfillment] à l’aide des informations d’identification d’exécution de magasin qui vous ont été fournies.](connect-set-up-service.md)

1. [Création d’utilisateurs et de rôles pour l’application d’aide à la boutique](user-setup.md)

1. [Téléchargez le fichier de Walmart [!DNL Store Assist] sur l’appareil de votre choix. L’application est disponible à la fois sur la boutique d’applications (iOS) et la boutique de lecture (Android).](app-setup.md)

Une fois que vous avez installé, configuré, intégré et que vous avez accès à la variable [!DNL Store Assist] application, vous pouvez [commencer à créer des commandes et des tests ;](test-and-deploy.md).


