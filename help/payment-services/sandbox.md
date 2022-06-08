---
title: Configuration de l’environnement de test
description: Utilisez un compte sandbox PayPal à utiliser [!DNL Payment Services] en mode test.
exl-id: 99c14b4e-e6cf-48f9-9546-5c0d5c71464d
source-git-commit: e8d008d9a38cebde7772b7e3d70d2447631414fe
workflow-type: tm+mt
source-wordcount: '553'
ht-degree: 0%

---

# Configuration de l’environnement de test

Avant de commencer l’intégration à des environnements de test, vous devez vous inscrire à un compte Développeur PayPal gratuit et créer des comptes de commerçant (à utiliser pour l’intégration) et de commerçant (à utiliser pour tester votre passage en caisse). Si vous le souhaitez, vous pouvez créer plusieurs comptes de développeur.

Un compte sandbox PayPal vous permet d’utiliser des [!DNL Payment Services] en mode test. PayPal exige que vous utilisiez un compte de test d’environnement de test d’entreprise, un courrier électronique et un mot de passe générés par PayPal Developer Portal pour l’intégration à l’environnement de test. Ne créez pas un autre compte pendant le processus d’intégration des environnements de test.

Si vous avez créé un compte au cours du processus d’intégration PayPal des environnements de test, vous devez réinitialiser votre environnement de test d’intégration car vous ne pouvez pas vérifier votre adresse électronique.

Pour réinitialiser votre compte sandbox :

1. Cliquez sur **[!UICONTROL Reset sandbox]**. Voir [PayPal crée un compte sandbox d’entreprise](https://developer.paypal.com/docs/api-basics/sandbox/accounts/#create-a-business-sandbox-account) pour plus d’informations.
1. Cliquez sur **[!UICONTROL Sandbox onboarding]** et effectuez l’ensemble d’étapes suivant.

Pour finaliser l’intégration des environnements de test :

1. Accédez au [Page Compte de développeur PayPal](https://developer.paypal.com/developer/accounts/).
1. Cliquez sur **[!UICONTROL Log in to Home]** et connectez-vous avec vos informations d’identification existantes au compte des développeurs PayPal ou cliquez sur **S’inscrire** pour créer un compte.
1. Créez un compte sandbox PayPal :
   1. Accédez à _[!UICONTROL SANDBOX]_>**[!UICONTROL Accounts]**.
   1. Cliquez sur **[!UICONTROL Create account]**.
   1. Sélectionner **[!UICONTROL Business]** comme Type de compte, puis cliquez sur **[!UICONTROL Create]**.
   1. Dans le _[!UICONTROL Sandbox Accounts]_, cliquez sur les trois points de la section_[!UICONTROL Manage accounts]_ pour le compte sandbox que vous avez créé.
   1. Cliquez sur **[!UICONTROL View/edit account]**.

      ![PayPal - Afficher/modifier le compte sandbox](assets/onboarding-viewedit-sandbox.png)

   1. Copiez et enregistrez l’ID de message électronique et le mot de passe généré par le système pour une utilisation ultérieure.

1. Sur le _Administration_ barre latérale, accédez à **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Cliquez sur **[!UICONTROL Sandbox onboarding]**.

   Cette option est visible si vous n’avez pas encore terminé l’intégration à l’environnement de test pour [!DNL Payment Services].

   Un ID de marchand d’environnement de test est généré automatiquement et renseigné dans la variable [paramètres](settings.md). Ne modifiez pas ou ne modifiez pas cet identifiant.

   Une fenêtre PayPal s’affiche pour vous permettre de connecter un compte PayPal afin de commencer à accepter les paiements.

1. Saisissez l’adresse électronique de votre compte professionnel et votre pays ou région, puis cliquez sur **[!UICONTROL Next]**.

   ![PayPal - Connecter le compte PayPal pour les paiements](assets/paypal-connectacct.png)

1. Continuez à suivre le flux PayPal, à l’aide des informations d’identification de votre compte sandbox précédemment enregistrées.
1. Sur le _Administration_ barre latérale, accédez à **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   Le **[!UICONTROL Sandbox onboarding]** n’est plus visible et un texte &quot;Paiements en attente d’un environnement de test&quot; s’affiche.

Lorsque votre intégration à l’environnement de test PayPal est approuvée, une notification vous indique que votre système de paiement est actuellement en mode sandbox et qu’il ne traite pas les paiements en direct.

>[!IMPORTANT]
>
>Si vous révoquez le consentement de [!DNL Payment Services] pour [!DNL Adobe Commerce] et [!DNL Magento Open Source] pour le traitement de vos paiements (dans les paramètres de votre compte PayPal), les commandes de votre boutique ne peuvent pas être traitées par [!DNL Payment Services]. Sur votre page d’accueil des services de paiement, une alerte concernant le consentement révoqué s’affiche. Pour ignorer l’alerte, cliquez sur **[!UICONTROL Do not show again]**.

## Activer le numéro de téléphone de contact

Le numéro de téléphone de contact permet d&#39;obtenir les numéros de téléphone de contact que PayPal collecte auprès de vos clients. PayPal collecte toujours les numéros de téléphone des titulaires du compte PayPal afin de les aider à confirmer leur identité et à les contacter pour résoudre les problèmes sur leurs comptes, ou pour terminer leurs processus d&#39;exécution. Cependant, PayPal déconseille l&#39;utilisation des numéros de téléphone directement par le marchand, car cela peut avoir un impact négatif sur les ventes. Voir [PayPal reçoit les numéros de téléphone des contacts](https://developer.paypal.com/docs/admin/checkout-settings/#get-contact-telephone-numbers) pour plus d’informations.

Cette fonctionnalité est `off` par défaut. Lorsque vous l’activez, les administrateurs de magasin peuvent voir les numéros de téléphone lorsqu’un client effectue un flux de passage en caisse de marque en dehors de la page de passage en caisse.

>[!IMPORTANT]
>
>Ce paramètre ne s’applique pas aux autres flux de passage en caisse.

## Test dans l’environnement de test

Voir [Tester et valider](test-validate.md) pour plus d’informations.
