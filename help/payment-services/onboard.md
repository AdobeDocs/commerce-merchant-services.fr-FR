---
title: Onboard [!DNL Payment Services]
description: Connexion de votre instance à [!DNL Payment Services] en suivant quelques étapes d’intégration.
role: User
level: Intermediate
exl-id: 1ee8c660-0941-4378-a1d7-ae45de3de211
source-git-commit: bfb2b6632fe494d6e392c214f5e3f5a11930c0b2
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# Onboard [!DNL Payment Services]

Pour commencer à utiliser [!DNL Payment Services] pour Adobe Commerce et Magento Open Source, vous devez suivre quelques étapes d’intégration pour connecter votre instance à la fonctionnalité de paiements.

## Flux d’intégration

![Flux d’intégration](assets/onboarding-diagram.svg)

Ce diagramme de flux d’intégration affiche le processus général d’intégration. [!DNL Payment Services].

Une fois l’intégration terminée pour les environnements de test ou les paiements en direct, les rapports financiers sont accessibles à partir de [!DNL Payment Services] dans Admin.

Si les paiements en environnement de test et en direct sont intégrés et activés, vous pouvez facilement basculer entre ces modes à partir de la variable [!DNL Payment Services] accueil.

## Conditions préalables

Pour utiliser [!DNL Payment Services], les éléments suivants doivent être disponibles pour votre instance :

* Module Services Connector
* Module d’ID de services
* Clés API

Les modules Connecteur de services et Identifiant de services sont automatiquement installés pendant la [installation de [!DNL Payment Services]](install.md). Une fois l’installation terminée, une nouvelle section s’affiche dans les paramètres de configuration (**[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**) lorsque vous développez **[!UICONTROL Services]**—**[!UICONTROL Commerce Services Connector]**.

Pour savoir comment créer des clés d’API ou y accéder, voir [Informations d’identification de l’API](#obtain-api-credentials).

## Étapes d’intégration

1. [Installez le [!DNL Payment Services] extension](install.md#get-payment-services).
1. [Obtention des informations d’identification de l’API](connect.md#obtain-api-credentials).
1. [Connexion à votre instance](connect.md#configure-commerce-services) vers Commerce Services. Cette connexion ne doit être effectuée qu’une seule fois par instance Commerce.
1. [Configuration du service sandbox](sandbox.md#enable-sandbox-testing) (ou, à titre de variante, passez à la [activation des paiements en direct](sandbox.md#enable-live-payments) si vous avez testé la fonctionnalité dans un autre environnement) avec un compte de traitement des paiements PayPal de test.
1. [Définir [!DNL Payment Services] comme mode de paiement](production.md#set-payment-services-as-payment-method), en mode sandbox, pour commencer le traitement des paiements de test.
1. [Droit relatif aux paiements](production.md#request-payments-entitlement-from-adobe) pour activer l’intégration en direct.
1. [Intégration complète de commerce](production.md#complete-merchant-onboarding) pour activer les paiements en direct pour vos sites web Commerce.
1. [Obtenez votre [!DNL Payment Services] Identifiant du marchand](production.md#configure-pricing-tier) et passez-le à Sales pour configurer le niveau de tarification approprié.
1. [Activer [!DNL Payment Services] en mode réel](production.md#enable-live-payments) pour commencer à traiter les paiements en direct.
1. Tester les paiements, dans les deux [sandbox](sandbox.md#test-in-sandbox-environment) et [production](production.md#test-in-production) des environnements.

>[!NOTE]
>
>Si vous ne configurez pas vos services de commerce dans l’Admin (étape 3), vous ne pouvez pas configurer d’environnement de test ni de paiements en direct.

## Dépannage

* [Résolution des problèmes [!DNL Payment Services] installation](https://support.magento.com/hc/en-us/articles/4406603542541)
* [Compte sandbox PayPal non vérifié](https://support.magento.com/hc/en-us/articles/4406954952461)
* [Retardé [!DNL Payment Services] données de rapport](https://support.magento.com/hc/en-us/articles/4406114741517)
* [Échec du test de la carte de crédit avec PayPal lors du traitement des paiements dans un environnement Sandbox](https://support.magento.com/hc/en-us/articles/5201041963917)
