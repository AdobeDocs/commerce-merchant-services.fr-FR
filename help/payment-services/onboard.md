---
title: Onboard [!DNL Payment Services]
description: Connexion de votre instance à [!DNL Payment Services] en suivant quelques étapes d’intégration.
role: User
level: Intermediate
exl-id: 1ee8c660-0941-4378-a1d7-ae45de3de211
feature: Payments, Checkout, Integration
source-git-commit: 6ba5a283d9138b4c1be11b80486826304c63247f
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# Onboard [!DNL Payment Services]

Pour commencer à utiliser [!DNL Payment Services] pour [!DNL Adobe Commerce] et [!DNL Magento Open Source], vous devez effectuer quelques étapes d’intégration pour connecter votre instance à la fonctionnalité de paiements.

## Flux d’intégration

![Flux d’intégration](assets/onboarding-diagram.svg){width="600" zoomable="yes"}

Ce diagramme de flux d’intégration affiche le processus général d’intégration. [!DNL Payment Services].

Une fois l’intégration terminée pour l’environnement de test ou les paiements en direct, les rapports financiers sont accessibles à partir de [!DNL Payment Services] dans Admin.

Si les paiements en environnement de test et en direct sont intégrés et activés, vous pouvez facilement basculer entre ces modes à partir de la [!DNL Payment Services] Chez soi.

## Conditions préalables

Pour utiliser [!DNL Payment Services], les éléments suivants doivent être disponibles pour votre instance :

* Module Services Connector
* Module d’ID de services
* Clés API

Les modules Connecteur de services et Identifiant de services sont automatiquement installés pendant la [installation de [!DNL Payment Services]](install.md). Une fois l’installation terminée, une nouvelle section s’affiche dans les paramètres de configuration (**[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**) lorsque vous développez **[!UICONTROL Services]**—**[!UICONTROL Commerce Services Connector]**.

Pour savoir comment créer des clés d’API ou y accéder, voir [Informations d’identification API](#obtain-api-credentials).

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

* [Résolution des problèmes [!DNL Payment Services] installation](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-install.html?lang=en)
* [Compte sandbox PayPal non vérifié](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-paypal-acct.html)
* [Retardé [!DNL Payment Services] données de rapport](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-report-info-delayed.html)
* [Échec du test de la carte de crédit avec PayPal lors du traitement des paiements dans un environnement Sandbox](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-cc-sandbox-failure.html?lang=en)
