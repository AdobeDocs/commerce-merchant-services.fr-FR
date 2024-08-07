---
title: Configuration de l’environnement de test
description: Utilisez un compte sandbox PayPal pour utiliser  [!DNL Payment Services]  en mode test.
exl-id: 99c14b4e-e6cf-48f9-9546-5c0d5c71464d
feature: Payments, Checkout, Configuration, Install
source-git-commit: 5481b19f95908b441e12c4700c51649921dabb08
workflow-type: tm+mt
source-wordcount: '614'
ht-degree: 0%

---

# Configuration de l’environnement de test

Avant de commencer l’intégration à des environnements de test, vous devez vous inscrire à un compte Développeur PayPal gratuit et créer des comptes de commerçant (à utiliser pour l’intégration) et de commerçant (à utiliser pour tester votre passage en caisse). Si vous le souhaitez, vous pouvez créer plusieurs comptes de développeur.

Un compte sandbox PayPal vous permet d’utiliser [!DNL Payment Services] en mode test. PayPal exige que vous utilisiez un compte de test d’environnement de test d’entreprise, un courrier électronique et un mot de passe générés par PayPal Developer Portal pour l’intégration à l’environnement de test. *Ne créez pas un autre compte pendant le processus d&#39;intégration des environnements de test.*

## Intégration à des environnements de test

Pour finaliser l’intégration des environnements de test :

1. Accédez à la [page du compte de développeur PayPal](https://developer.paypal.com/developer/accounts/).
1. Cliquez sur **[!UICONTROL Log in to Dashboard]** et connectez-vous à votre compte de test de sandbox professionnel généré par PayPal Developer Portal existant ou cliquez sur **S’inscrire** pour créer un compte.
1. Créez un compte sandbox PayPal :
   1. Accédez à _[!UICONTROL Testing Tools]_>**[!UICONTROL Sandbox Accounts]**.
   1. Cliquez sur **[!UICONTROL Create account]**.

      Si vous avez créé un compte sandbox PayPal pendant le processus d’intégration de l’environnement de test PayPal, vous devez [réinitialiser votre environnement de test d’intégration](#reset-your-sandbox-account) car vous ne pouvez pas vérifier votre adresse électronique.

   1. Sélectionnez **[!UICONTROL Business]** comme Type de compte et cliquez sur **[!UICONTROL Create]**.
   1. Dans la section _[!UICONTROL Sandbox Accounts]_, cliquez sur les trois points de la colonne_[!UICONTROL Manage accounts]_ correspondant au compte sandbox que vous avez créé.
   1. Cliquez sur **[!UICONTROL View/edit account]**.

      ![PayPal - Afficher/modifier le compte sandbox](assets/onboarding-viewedit-sandbox.png){width="300" zoomable="yes"}

   1. Copiez et enregistrez l’ID de message électronique et le mot de passe généré par le système pour une utilisation ultérieure.

1. Sur la barre latérale _Admin_, accédez à **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Cliquez sur **[!UICONTROL Sandbox onboarding]**.

   Cette option est visible si vous n’avez pas encore terminé l’intégration des environnements de test pour [!DNL Payment Services].

   Un ID de commerce sandbox est généré automatiquement et renseigné dans [settings](settings.md). Ne modifiez pas ou ne modifiez pas cet identifiant.

   Une fenêtre PayPal s’affiche pour vous permettre de connecter un compte PayPal afin de commencer à accepter les paiements.

1. Saisissez l’adresse électronique et le mot de passe du compte sandbox PayPal que vous avez généré à l’étape 3 (et non les informations de votre compte professionnel PayPal) et votre pays ou région.
1. Cliquez sur **[!UICONTROL Next]**.

   ![PayPal - Connecter le compte PayPal pour les paiements](assets/paypal-connectacct.png){width="300" zoomable="yes"}

1. Continuez à suivre le flux PayPal, à l’aide des informations d’identification de votre compte sandbox précédemment enregistrées.
1. Sur la barre latérale _Admin_, accédez à **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   Le bouton **[!UICONTROL Sandbox onboarding]** n’est plus visible et un texte &quot;Paiements Sandbox en attente&quot; s’affiche.

Lorsque votre intégration à l’environnement de test PayPal est approuvée, une notification vous indique que votre système de paiement est actuellement en mode sandbox et qu’il ne traite pas les paiements en direct.

>[!IMPORTANT]
>
>Si vous révoquez le consentement à [!DNL Payment Services] pour [!DNL Adobe Commerce] et [!DNL Magento Open Source] pour le traitement de vos paiements (dans les paramètres de votre compte PayPal), les commandes de votre boutique ne peuvent pas être traitées par [!DNL Payment Services]. Sur votre page d’accueil des services de paiement, une alerte concernant le consentement révoqué s’affiche. Pour ignorer l’alerte, cliquez sur **[!UICONTROL Do not show again]**.

### Réinitialisation de votre compte sandbox

Si vous avez créé un compte sandbox PayPal pendant le processus d’intégration de l’environnement de test PayPal, vous devez réinitialiser votre environnement de test d’intégration car vous ne pouvez pas vérifier votre adresse électronique.

Pour réinitialiser votre compte sandbox :

1. Cliquez sur **[!UICONTROL Reset sandbox]**. [ Créez un compte de sandbox d’entreprise PayPal ](https://developer.paypal.com/docs/api-basics/sandbox/accounts/#create-a-business-sandbox-account).
1. Cliquez sur **[!UICONTROL Sandbox onboarding]** et effectuez l’ensemble d’étapes suivant.

## Activer le numéro de téléphone de contact

Le numéro de téléphone de contact permet d&#39;obtenir les numéros de téléphone de contact que PayPal collecte auprès de vos clients. PayPal collecte toujours les numéros de téléphone des titulaires du compte PayPal afin de les aider à confirmer leur identité et à les contacter pour résoudre les problèmes sur leurs comptes, ou pour terminer leurs processus d&#39;exécution. Cependant, PayPal déconseille l&#39;utilisation des numéros de téléphone directement par le marchand, car cela peut avoir un impact négatif sur les ventes. Pour plus d’informations, consultez la documentation [PayPal obtenir les numéros de téléphone de contact](https://www.sandbox.paypal.com/businessmanage/preferences/website) .

Cette fonctionnalité est `off` par défaut. Lorsque vous l’activez, les administrateurs de magasin peuvent voir les numéros de téléphone lorsqu’un client effectue un flux de passage en caisse de marque en dehors de la page de passage en caisse.

>[!IMPORTANT]
>
>Ce paramètre ne s’applique pas aux autres flux de passage en caisse.

## Test dans l’environnement de test

Il est vivement recommandé d’utiliser des jeux de données de test pour les environnements d’intégration et d’évaluation, ainsi que pour tester les paiements en production, avec de vraies cartes de crédit et des banques, avant d’exposer cette fonctionnalité aux acheteurs.

Voir [Test et validation](test-validate.md) pour plus d’informations.
