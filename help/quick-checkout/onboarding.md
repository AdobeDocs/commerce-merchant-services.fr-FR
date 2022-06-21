---
title: '"À l’intégration de [!DNL Quick Checkout] pour l’extension Adobe Commerce"'
description: '"Découvrez comment [!DNL Quick Checkout] pourrait bénéficier à votre instance Adobe Commerce et comment intégrer et configurer l’extension avec succès."'
exl-id: 8caf746c-e31b-4331-8b0d-ea0f1e545bdd
source-git-commit: a62c38adeb41812e91089716eb36c375b09595f4
workflow-type: tm+mt
source-wordcount: '570'
ht-degree: 0%

---

# [!DNL Quick Checkout] intégration

Pour commencer à utiliser la méthode [!DNL Quick Checkout] pour l’extension Adobe Commerce, vous devez suivre quelques étapes d’intégration afin de connecter votre instance à notre fonctionnalité de passage en caisse.

1. [Obtenir l’extension](#get-extension).
1. [Création d’un compte commercial de production ou d’environnement de test avec [!DNL Bolt]](#create-account-with-bolt). Fournissez toutes les informations requises pour vérifier votre identité.
1. [Fournissez les [!DNL API Key] et [!DNL Publishable Key] généré dans [!DNL Bolt]](#obtain-api-credentials).
1. [Configurez un fournisseur de paiement dans la variable [!DNL Bolt] account](#configure-payment-providers).
1. [Définir la liste déroulante Activer sur Oui](#enable-extension) pour activer l’extension.
1. [Définition des paramètres du service](#complete-admin-configuration) pour configurer la variable [!DNL Quick Checkout] extension .
1. [Cliquez sur le bouton Enregistrer la configuration .](#enable-live-quick-checkout) pour activer l’extension .

>[!NOTE]
>
> Si vous ne configurez pas votre [!DNL Bolt] comptes que vous ne pouvez pas configurer votre environnement de test ou vos environnements de production.

## Conditions préalables

Pour utiliser la variable [!DNL Quick Checkout], les éléments suivants doivent être disponibles pour [!DNL Bolt]:

- Prestataires de paiement pris en charge
- Compte Marchand et Production dans [!DNL Bolt]
- API et [!DNL Publishable key] généré dans [!DNL Bolt]

Reportez-vous à la section [conditions préalables](../quick-checkout/prerequisites.md) pour plus d’informations.

Voir [Informations d’identification de l’API](#obtain-api-credentials) pour savoir comment créer ou accéder à votre [!DNL API keys] pour votre instance.

## Obtenir l’extension

Voir [install](../quick-checkout/install.md) rubrique pour obtenir des informations détaillées sur l’obtention de l’extension.

## Créer un compte avec [!DNL Bolt]

Avant de configurer le [!DNL Quick Checkout] dans votre administrateur Adobe Commerce, vous devez créer une [sandbox](https://merchant-sandbox.bolt.com/register){target=&quot;_blank&quot;} et [production](https://merchant.bolt.com/register){target=&quot;_blank&quot;} comptes de commerce dans [!DNL Bolt]. Indiquez tous les détails requis pour créer un compte dans [!DNL Bolt].

Reportez-vous à la section [test et validation](../quick-checkout/testing.md) pour plus d’informations.

## Obtention des informations d’identification de l’API

Pour utiliser la variable [!DNL Quick Checkout] vous avez besoin de [!DNL Bolt] clés uniques. Procurez-vous les éléments suivants : [!DNL API keys] en accédant à **Développeurs** > **API** > **Clés** dans le **Tableau de bord des commerçants de Bolt**.

- [!DNL API key]: Clé privée utilisée par votre serveur principal pour interagir avec [!DNL Bolt] API.
- [!DNL Publishable key]: Clé utilisée par votre front-end pour interagir avec [!DNL Bolt] API.

Voir [[!DNL Bolt] détails de l’environnement](https://help.bolt.com/developers/references/environment-details/#about-keys)page {target=&quot;_blank&quot;} pour en savoir plus sur l’API et [!DNL Publishable keys] pour le [!DNL Quick Checkout] extension .

>[!CAUTION]
>
> Vous devez créer [!DNL API keys] pour les environnements de test et de production.

## Configurer les fournisseurs de paiement

Pour connecter votre fournisseur de services de paiement, procédez comme décrit dans la section [configuration du processeur](https://help.bolt.com/integrations/adobe-express-checkout/set-up/)Développeur {target=&quot;_blank&quot;} [!DNL Bolt] page.

## Activer l’extension

1. Sur le _Administration_ barre latérale, accédez à **Magasins** > _Paramètres_ > **Configuration**.
1. Dans le panneau de gauche, développez **Ventes** et sélectionnez **Passage en caisse**.

   ![Passage en caisse rapide](assets/admin-view.png)

1. Dans le [!DNL Quick Checkout] vue, définir **Activer** to `Yes`.
1. Sélectionnez la méthode (sandbox ou production) à utiliser.

   - Environnement de test à des fins de test et de développement
   - Production pour traiter les transactions avec le responsable du paiement en direct

1. Validation des informations d’identification après avoir fourni votre API unique et [!DNL Publishable keys].

>[!CAUTION]
>
> Vous devez fournir une API unique. [!DNL Publishable keys] avant d’activer l’extension, sinon les clients verront un formulaire de paiement et ne pourront pas passer de commande.

## Configuration complète de l’administrateur

1. Sur le _Administration_ barre latérale, accédez à **Magasins** > **Configuration** > **Passage en caisse** pour accéder à la page de configuration générale de l’administrateur de passage en caisse .
1. Dans le _Paramètres du service_ , fournissez tous les détails requis pour activer l’extension.
1. Définir _Action de paiement_ à l’une des options suivantes :

   - `Authorize`: Ne capturez pas automatiquement les transactions sur autorisation.
   - `Authorize and Capture`: Capturez automatiquement la transaction lors de l’autorisation.

Pour plus d’informations sur les options de passage en caisse standard d’Adobe Commerce, reportez-vous à la section [passage en caisse](https://docs.magento.com/user-guide/configuration/sales/checkout.html) rubrique.

## Activation du paiement rapide en direct

Pour activer la variable [!DNL Quick Checkout] pour l’extension Adobe Commerce :

1. Vérifiez que la variable [!UICONTROL Enable] La liste déroulante est définie sur **Oui** pour activer l’extension.
1. Cliquez sur **Enregistrer la configuration**.

## Obtenir de l’aide

Le processus d’intégration est conçu pour vous guider tout au long des étapes nécessaires à la configuration et à l’activation de la variable [!DNL Express Checkout] . Contactez l’équipe d’ingénieurs Adobe Commerce par l’intermédiaire de votre Slack désigné. [Canal Adobe de programmes bêta](http://adobe-beta-programs.slack.com/) canal pour obtenir de l’aide.

Voir [test et validation](../quick-checkout/testing.md) pour plus d’informations.
