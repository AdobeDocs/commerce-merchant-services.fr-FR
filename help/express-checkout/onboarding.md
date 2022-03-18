---
title: À l’intégration de [!DNL Express Checkout] pour l’extension Adobe Commerce
description: Découvrez comment [!DNL Express Checkout] pourrait bénéficier à votre instance Adobe Commerce et comment intégrer et configurer l’extension avec succès.
exl-id: 8caf746c-e31b-4331-8b0d-ea0f1e545bdd
source-git-commit: d8302d2d652b4e2380cc862183e58cbd2cca831b
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# [!DNL Express Checkout] intégration

>[!IMPORTANT]
>
> Cette fonctionnalité est réservée aux utilisateurs du Programme des Adopteurs Anticipés (EAP) et n’est pas encore accessible à tous les clients. Actuellement limitée aux clients américains. Contactez l’assistance d’Adobe Commerce pour toute question ou assistance.

Pour commencer à utiliser la méthode [!DNL Express Checkout] pour l’extension Adobe Commerce, vous devez suivre quelques étapes d’intégration afin de connecter votre instance à notre fonctionnalité de passage en caisse.

1. [Obtenir l’extension](#get-extension).
1. [Création d’un compte marchand de production ou d’environnement de test avec Bolt](#create-account-with-bolt). Fournissez toutes les informations requises pour vérifier votre identité.
1. [Fournir la clé API unique et la clé publiable générées dans Bolt](#obtain-api-credentials).
1. [Configurer un fournisseur de paiement dans le compte Bolt](#configure-payment-providers).
1. [Définir la liste déroulante Activer sur Oui](#enable-extension) pour activer l’extension.
1. [Définition des paramètres du service](#complete-admin-configuration) pour configurer la variable [!DNL Express Checkout] extension .
1. [Cliquez sur le bouton Enregistrer la configuration .](#enable-live-express-checkout) pour activer l’extension .

>[!NOTE]
>
> Si vous ne configurez pas vos comptes Bolt (étape 2 ci-dessus), vous ne pouvez pas configurer votre environnement de test ou vos environnements de production.

## Conditions préalables

Pour utiliser la variable [!DNL Express Checkout], les éléments suivants doivent être disponibles pour Bolt :

- Prestataires de paiement pris en charge
- Compte Marchand et Production en Bourse
- API et clé publiable générées dans Bolt

Reportez-vous à la section [conditions préalables](../express-checkout/prerequisites.md) pour plus d’informations.

Voir [Informations d’identification de l’API](#obtain-api-credentials) pour savoir comment créer ou accéder à vos clés d’API pour votre instance.

## Obtenir l’extension

Voir [install](../express-checkout/install.md) rubrique pour obtenir des informations détaillées sur l’obtention de l’extension.

## Créer un compte avec Bolt

Avant de configurer le [!DNL Express Checkout] dans votre administrateur Adobe Commerce, vous devez créer une [production](https://merchant.bolt.com/register){target=&quot;_blank&quot;} et [sandbox](https://merchant-sandbox.bolt.com/register)Compte marchand {target=&quot;_blank&quot;} dans Bolt. Fournissez tous les détails requis pour créer un compte dans Bolt.

Reportez-vous à la section [test et validation](../express-checkout/testing.md) pour plus d’informations.

## Obtention des informations d’identification de l’API

Pour utiliser la variable [!DNL Express Checkout] vous avez besoin de clés uniques Bolt. Obtenez les clés d’API suivantes en accédant à **Développeurs** > **API** > **Clés** dans le **Tableau de bord des commerçants de Bolt**.

- Clé API : Clé privée utilisée par votre serveur principal pour interagir avec les API Bolt.
- Clé publiable : Clé utilisée par votre serveur frontal pour interagir avec les API Bolt.

Voir [Détails de l’environnement de blocage](https://help.bolt.com/developers/references/environment-details/#about-keys)Page {target=&quot;_blank&quot;} pour en savoir plus sur l’API et les clés publiables pour [!DNL Express Checkout] extension .

>[!CAUTION]
>
> Vous devez créer des clés d’API pour les environnements de test et les environnements de production.

## Configurer les fournisseurs de paiement

Pour connecter votre fournisseur de services de paiement, procédez comme décrit dans la section [configuration du processeur](https://help.bolt.com/integrations/adobe-express-checkout/set-up/)La page Bolt du développeur {target=&quot;_blank&quot;}.

## Activer l’extension

1. Sur le _Administration_ barre latérale, accédez à **Magasins** > **Configuration** > **Passage en caisse** pour accéder à la page de configuration Admin de passage en caisse .

![Extraction express](../assets/admin-view.png)

1. Dans le [!DNL Express Checkout] vue, définir **Activer** to `Yes`.
1. Sélectionnez la méthode (Production ou Sandbox) à utiliser.
1. Validez les informations d’identification après avoir fourni votre API unique et vos clés publiables.

>[!CAUTION]
>
> Vous devez fournir une API unique et des clés publiables avant d’activer l’extension. Sinon, les clients verront un formulaire de paiement et ne pourront pas passer de commande.

## Configuration complète de l’administrateur

1. Sur le _Administration_ barre latérale, accédez à **Magasins** > **Configuration** > **Passage en caisse** pour accéder à la page de configuration générale de l’administrateur de passage en caisse .
1. Dans le _Paramètres du service_ , fournissez tous les détails requis pour activer l’extension.
1. Définir _Action de paiement_ comme :

   - Autoriser : Ne capturez pas automatiquement les transactions sur autorisation.
   - Autoriser et capturer : Capturez automatiquement la transaction lors de l’autorisation.

Pour plus d’informations sur les options de passage en caisse standard d’Adobe Commerce, reportez-vous à la section [passage en caisse](https://docs.magento.com/user-guide/configuration/sales/checkout.html) rubrique.

## Activer le paiement express en direct

Pour activer la variable [!DNL Express Checkout] pour l’extension Adobe Commerce :

1. Cliquez sur **Enregistrer la configuration**.

## Obtenir de l’aide

Le processus d’intégration est conçu pour vous guider tout au long des étapes requises pour configurer et activer toutes les [!DNL Express Checkout] . Contactez l’assistance d’Adobe Commerce pour toute question ou assistance.

Reportez-vous à la section [test et validation](../express-checkout/testing.md) pour plus d’informations.
