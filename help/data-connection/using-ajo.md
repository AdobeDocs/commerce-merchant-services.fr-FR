---
title: Utiliser Adobe Journey Optimizer pour envoyer un email de panier abandonné
description: Découvrez comment utiliser Adobe Journey Optimizer pour envoyer un email de panier abandonné.
role: Admin, Developer
feature: Personalization, Integration
exl-id: 5e4e7c0a-c00b-4278-bd73-6b6f2fcbe770
source-git-commit: 6500aaa373d8e9abf88d1ca45dc2742c83bfeca3
workflow-type: tm+mt
source-wordcount: '1262'
ht-degree: 0%

---

# Utilisation de Adobe Journey Optimizer pour envoyer un courrier électronique au panier abandonné

Découvrez comment diffuser un email ou une notification de réengagement personnalisé si une session de panier ou de navigateur a été abandonnée. Dans cet article, vous utilisez les données générées par des clients qui ont consulté un certain nombre de produits et de catégories, qui ont interagi avec un produit ou qui ont passé du temps sur une page.

## Quelles données dois-je envisager d’utiliser ?

Créez un panier abandonné, parcourez les e-mails ou les notifications à l’aide des données provenant des événements storefront et back-office.

| Types de données | Données Storefront (Événements comportementaux) | Données du back-office (événements côté serveur) |
|---|---|---|
| **Définition** | Clics ou actions des clients sur votre site. | Informations sur le cycle de vie et détails de chaque commande (passé et actuel). |
| **Événements capturés par Adobe Commerce** | [pageView](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/event-forwarding/events#pageview)<br>[productPageView](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/event-forwarding/events)<br>[addToCart](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/event-forwarding/events#addtocart)<br>[openCart](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/event-forwarding/events#opencart)<br>[startCheckout](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/event-forwarding/events#startcheckout)<br>[completeCheckout](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/event-forwarding/events#completecheckout) | [orderPlaced](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/event-forwarding/events-backoffice#orderplaced)<br>[Historique des commandes](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/fundamentals/connect-data#send-historical-order-data) |

### Qu’ont réalisé d’autres clients ?

Les clients d’Adobe [!DNL Commerce] ont eu des répercussions importantes sur l’entreprise en mettant en oeuvre des campagnes d’abandon personnalisées à l’aide de l’Adobe [!DNL Commerce], de l’Adobe [!DNL Journey Optimizer] et de l’Adobe [!DNL Real-Time CDP].

Un détaillant mondial de vêtements multimarques a obtenu les résultats suivants :

- Conversion 1.9x en clic depuis les nouvelles campagnes
- Augmentation de 57 % des recettes provenant des parcours d’abandon de canal
- Augmentation de 41 % du taux de conversion des campagnes de réengagement
- Plus de 1 000 nouveaux acheteurs engagés par semaine

Une entreprise mondiale de boissons a réussi :

- Taux d’ouverture des emails de réengagement de 36 %
- Effet élévateur de 21 % dans les taux de clics publicitaires
- Effet élévateur de 8,5 % du taux de conversion
- 89 % des personnes ayant abandonné leur engagement

## Commençons

Ce cas d’utilisation spécifique se concentre sur la création d’un email de panier abandonné à l’aide des données de votre instance [!DNL Commerce] et de l’envoyer à l’Adobe [!DNL Journey Optimizer].

### Qu’est-ce que Adobe Journey Optimizer ?

[Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/get-started.html) vous aide à personnaliser l’expérience commerciale de vos acheteurs. Par exemple, vous pouvez utiliser Journey Optimizer pour créer et diffuser des campagnes marketing planifiées, telles que des promotions hebdomadaires pour un magasin de détail, ou générer un e-mail de panier abandonné si un client a ajouté un produit à un panier, mais qu’il n’a pas terminé le processus de passage en caisse.

Dans cette rubrique, vous apprenez à créer un email de panier abandonné en écoutant un événement `checkout` généré à partir de votre instance [!DNL Commerce] et en répondant à cet événement dans Journey Optimizer.

>[!IMPORTANT]
>
>À des fins de démonstration, utilisez votre environnement de test [!DNL Commerce] afin de ne pas diluer vos données d’événement de production avec les données d’événement storefront et back-office que vous envoyez à l’Experience Platform.

### Conditions préalables

Avant de commencer, assurez-vous que :

- Vous êtes configuré pour utiliser l’Adobe [!DNL Journey Optimizer]. Si vous n’en êtes pas sûr, contactez votre intégrateur de systèmes ou l’équipe de développement qui gère les projets et les environnements.
- Vous [ avez ](install.md) installé et [configuré](connect-data.md) l’extension [!DNL Data Connection] dans [!DNL Commerce].
- Vous [avez confirmé](connect-data.md#confirm-that-event-data-is-collected) que vos données d’événement [!DNL Commerce] arrivent sur le bord Experience Platform.

## Étape 1 : Création d’un utilisateur dans votre environnement de test [!DNL Commerce]

Créez un utilisateur dans votre environnement de test et vérifiez que les informations de ce compte d’utilisateur s’affichent dans Experience Platform. Assurez-vous que l’email que vous avez spécifié est valide, car il est utilisé ultérieurement dans cette section pour envoyer l’email du panier abandonné.

1. Connectez-vous ou créez un compte dans votre environnement de test [!DNL Commerce].

   ![Connectez-vous à votre compte de test](assets/sign-in-account.png){width="700" zoomable="yes"}

   Une fois l’extension [!DNL Data Connection] installée et configurée, ces informations de compte sont envoyées à l’Experience Platform en tant que profil.

1. Vérifiez que les informations de votre compte utilisateur apparaissent dans la section **[!UICONTROL Profile]** de l’Experience Platform.

   Accédez à **[!UICONTROL Profiles]** dans Adobe Experience Platform. Cliquez sur **[!UICONTROL Detail]** dans le profil pour afficher le profil que vous avez créé.

   ![Confirmer le profil](assets/check-event-profile.png){width="700" zoomable="yes"}

## Étape 2 : affichage des événements dans Journey Optimizer

Dans votre environnement de test [!DNL Commerce], déclenchez des événements sur votre vitrine en affichant des pages de produits, en ajoutant des éléments à un panier et en exécutant diverses autres activités qu’un acheteur devrait exécuter. Vérifiez ensuite que ces événements arrivent à Journey Optimizer.

1. Lancez [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/user-interface.html).
1. Sélectionnez **[!UICONTROL Profiles]**.
1. Définissez **[!UICONTROL Identity namespace]** sur `Email`.
1. Définissez le **[!UICONTROL Identity value]** sur votre adresse électronique.
1. Sélectionnez votre profil, puis sélectionnez l’onglet **[!UICONTROL Events]** .

   ![Vérifier les détails de l’événement](assets/check-event-details.png){width="700" zoomable="yes"}

   Recherchez l’événement `commerce.checkouts` et examinez la charge utile de l’événement :

   ```json
   "personID": "84281643067178465783746543501073369488", 
   "eventType": "commerce.checkouts", 
   "_id": "4b41703f-e42e-485b-8d63-7001e3580856-0", 
   "commerce": { 
       "cart": {}, 
       "checkouts": { 
           "value": 1 
       } 
   ```

   Comme vous pouvez le constater, la payload d’événement complète contient des données d’événement riches. Dans la section suivante, vous allez configurer des événements dans Journey Optimizer pour écouter l’événement `commerce.checkouts` généré à partir de votre vitrine [!DNL Commerce] et y répondre.

## Étape 3 : configuration des événements dans Journey Optimizer

Configurez deux événements dans Journey Optimizer : l’un écoute l’événement `commerce.checkouts` de Commerce, l’autre est un événement de délai d’expiration de base qui attend un certain temps avant de déclencher un courrier électronique de panier abandonné.

### Créer un événement d’écouteur

1. Lancez [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/user-interface.html).

1. Cliquez sur **[!UICONTROL Configurations]** sous la section **[!UICONTROL Administration]** du volet de gauche.

1. Dans la mosaïque **[!UICONTROL Events]**, cliquez sur **[!UICONTROL Manage]**.

   ![Configuration d’événement Journey Optimizer](assets/ajo-config.png){width="700" zoomable="yes"}

1. Sur la page **[!UICONTROL Events]**, cliquez sur **[!UICONTROL Create Event]**.

1. Dans le volet de navigation de droite, configurez votre événement comme suit :

   1. Définissez le **[!UICONTROL Name]** sur : `firstname_lastname_checkout`.
   1. Définissez **[!UICONTROL Type]** sur **[!UICONTROL Unitary]**.
   1. Définissez **[!UICONTROL Event id typ]e** sur **[!UICONTROL Rule based]**.
   1. Définissez **[!UICONTROL Schema]** sur votre [!DNL Commerce] [schéma](update-xdm.md).
   1. Sélectionnez **[!UICONTROL Fields]** pour ouvrir la page **[!UICONTROL Fields]**. Sélectionnez ensuite les champs utiles à cet événement. Par exemple, sélectionnez tous les champs sous **[!UICONTROL Product list items]**, **[!UICONTROL Commerce]**, **[!UICONTROL eventType]** et **[!UICONTROL Web]**.
   1. Cliquez sur **[!UICONTROL OK]** pour enregistrer les champs sélectionnés.
   1. Cliquez à l’intérieur du champ **[!UICONTROL Event id condition]** . Ensuite, créez une condition : `eventType` est égal à `commerce.checkouts` ET `personalEmail.address` est égal à l’adresse électronique que vous avez utilisée lors de la création du profil dans la section précédente.

      ![Condition du jeu de Journey Optimizer](assets/ajo-set-condition.png){width="700" zoomable="yes"}

   1. Cliquez sur **[!UICONTROL OK]**.
   1. Cliquez sur **[!UICONTROL Save]** pour enregistrer votre événement.

### Création d’un événement de délai d’expiration

1. Créez un événement dans Journey Optimizer comme vous le faisiez auparavant.

1. Dans le volet de navigation de droite, configurez votre événement comme suit :

   1. Définissez le **[!UICONTROL Name]** sur : `firstname_lastname_timeout`.
   1. Définissez **[!UICONTROL Type]** sur **[!UICONTROL Unitary]**.
   1. Définissez **[!UICONTROL Event id type]** sur **[!UICONTROL Rule based]**.
   1. Définissez **[!UICONTROL Schema]** sur votre [!DNL Commerce] [schéma](update-xdm.md).
   1. Définissez les **[!UICONTROL Schema]**, **[!UICONTROL Fields]** et **[!UICONTROL Event id condition]** sur la même valeur que ci-dessus.
   1. Cliquez sur **[!UICONTROL Save]** pour enregistrer votre événement.

Une fois ces deux événements configurés, créez un parcours qui envoie un email de panier abandonné.

## Étape 4 : création d’un parcours de passage en caisse

Créez un parcours qui écoute l’événement `commerce.checkouts`, puis envoie un courrier électronique de panier abandonné après un délai spécifié.

1. Dans Journey Optimizer, sélectionnez **[!UICONTROL Journeys]** sous **J[!UICONTROL OURNEY MANAGEMENT]**.
1. Cliquez sur **[!UICONTROL Create Journey]**.
1. Indiquez le nom de votre parcours.
1. Cliquez sur **[!UICONTROL OK]** pour enregistrer le parcours.
1. Dans le volet de navigation de gauche, sous la section **[!UICONTROL EVENTS]**, recherchez l’événement de passage en caisse que vous avez précédemment créé : `firstname_lastname_checkout` et faites-le glisser et déposez-le sur la zone de travail.

   >[!TIP]
   >
   >Double-cliquez sur l’événement pour l’ajouter automatiquement à la zone de travail.

1. Recherchez l’événement de délai d’expiration et ajoutez-le à la zone de travail.
1. Double-cliquez sur l’événement de dépassement de délai.

   1. Dans la section **[!UICONTROL Timeout]** , cochez la case **[!UICONTROL Define the event time]** .
   1. Dans le champ **[!UICONTROL Wait for]** , saisissez `1` et `Minute`.
   1. Cochez la case **[!UICONTROL Set a timeout path]** .

   Avec cette configuration de délai d’expiration, un acheteur qui effectue un passage en caisse mais ne termine pas la commande en une minute déclenche cette branche de délai d’expiration. Dans un environnement de production réel, vous le définiriez sur une plus longue période, par exemple 24 heures.

1. Dans le volet de navigation de gauche sous **[!UICONTROL ACTIONS]**, ajoutez l’action **[!UICONTROL Email]** à la branche de dépassement de délai. Votre parcours doit se présenter comme suit :

   ![Canevas Journey Optimizer](assets/ajo-canvas.png){width="700" zoomable="yes"}

### Créer un email de panier abandonné

Créez un email de panier abandonné qui est envoyé lorsqu’un panier abandonné est détecté.

1. Dans le parcours que vous avez créé ci-dessus, double-cliquez sur l’icône **[!UICONTROL Email]** sur la zone de travail.

1. Suivez les [étapes](https://experienceleague.adobe.com/docs/journey-optimizer/using/content-management/personalization/personalization-use-cases/personalization-use-case-helper-functions.html#configure-email) du guide Journey Optimizer pour créer l’email de panier abandonné.

Vous disposez désormais d’un parcours dans Journey Optimizer qui écoute l’événement `commerce.checkouts` de votre boutique [!DNL Commerce] et d’un courrier électronique de panier abandonné envoyé après un certain temps. La section suivante montre comment tester le parcours.

## Étape 5 : déclencher l’événement de passage en caisse en temps réel

Dans cette section, vous testez l’événement en temps réel.

1. Dans Journey Optimizer, activez le mode Test.

   ![Activer le mode test](assets/ajo-enable-test.png){width="700" zoomable="yes"}

1. Pour tester ce parcours en temps réel, ouvrez un autre onglet du navigateur et accédez au site web [!DNL Commerce] dans votre environnement de test.

   1. Ajoutez un produit à votre panier.
   1. Accédez à la page de passage en caisse.
   1. Depuis la page de passage en caisse, abandonnez le panier en revenant à la page principale ou en fermant votre onglet.

      Le parcours est maintenant déclenché. Pour confirmer, ouvrez l’onglet contenant votre parcours dans Journey Optimizer. Vous devriez voir une flèche verte qui indique le chemin emprunté par votre utilisateur.

1. Recherchez le courrier électronique dans votre boîte de réception.
