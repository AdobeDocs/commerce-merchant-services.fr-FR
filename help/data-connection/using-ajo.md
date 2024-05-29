---
title: Utiliser Adobe Journey Optimizer pour envoyer un email de panier abandonné
description: Découvrez comment utiliser Adobe Journey Optimizer pour envoyer un email de panier abandonné.
role: Admin, Developer
feature: Personalization, Integration
exl-id: 5e4e7c0a-c00b-4278-bd73-6b6f2fcbe770
source-git-commit: a94f75dfab1f88f02e217b0e021cc2dfc94244c7
workflow-type: tm+mt
source-wordcount: '1429'
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

### Que puis-je faire avec Adobe Commerce uniquement ?

Utiliser l’Adobe [!DNL Commerce] pour configurer des rappels d’email basés sur des règles, qui peuvent servir de panier ou parcourir les emails d’abandon. Découvrez comment ici.

### Que puis-je faire avec l&#39;Adobe ? [!DNL Commerce] et Experience Cloud ?

- **Adobe [!DNL Commerce] avec Adobe Journey Optimizer** - Utilisation d’Adobe [!DNL Commerce] avec Adobe Journey Optimizer permet d’utiliser [!DNL Commerce] données comme déclencheur pour un parcours d’abandon omnicanal. Vous pouvez personnaliser ce parcours en fonction des attributs du client, des articles qu’il a abandonnés, d’autres comportements d’achat et des comportements d’achat antérieurs.

- **Adobe Commerce, Adobe Journey Optimizer et Adobe Real-Time CDP** - L’ajout de Real-Time CDP vous permet d’affiner davantage vos campagnes d’abandon en fonction de profils client unifiés et d’audiences gérées de manière centralisée, basées sur des règles ou optimisées par l’IA. Par exemple, vous pouvez créer :

   - Une audience &quot;fortement convertisseurs&quot; ayant un faible taux d&#39;abandon
   - Une audience &quot;à haute considération&quot; qui a revu plusieurs fois certaines catégories
   - Une audience &quot;à fort potentiel&quot; qui a une forte dépense et une forte fidélité mais qui a récemment abandonné

### Qu’ont réalisé d’autres clients ?

Adobe [!DNL Commerce] les clients ont réalisé des impacts commerciaux significatifs en implémentant des campagnes d’abandon personnalisées à l’aide d’Adobe. [!DNL Commerce], ADOBE [!DNL Journey Optimizer], et Adobe [!DNL Real-Time CDP].

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

Ce cas d’utilisation spécifique se concentre sur la création d’un email de panier abandonné à l’aide des données de votre [!DNL Commerce] et l’envoyer à Adobe [!DNL Journey Optimizer].

### Qu’est-ce que Adobe Journey Optimizer ?

[Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/get-started.html) vous aide à personnaliser l’expérience commerciale de vos clients. Par exemple, vous pouvez utiliser Journey Optimizer pour créer et diffuser des campagnes marketing planifiées, telles que des promotions hebdomadaires pour un magasin de détail, ou générer un e-mail de panier abandonné si un client a ajouté un produit à un panier, mais qu’il n’a pas terminé le processus de passage en caisse.

Dans cette rubrique, vous apprenez à créer un email de panier abandonné en écoutant un `checkout` généré à partir de votre [!DNL Commerce] et de répondre à cet événement dans Journey Optimizer.

>[!IMPORTANT]
>
>Pour une démonstration, utilisez [!DNL Commerce] environnement de test afin de ne pas diluer vos données d’événement de production avec les données d’événement storefront et back-office que vous envoyez à Experience Platform.

### Conditions préalables

Avant de commencer, assurez-vous que :

- Vous êtes configuré pour utiliser Adobe [!DNL Journey Optimizer]. Si vous n’en êtes pas sûr, contactez votre intégrateur de systèmes ou l’équipe de développement qui gère les projets et les environnements.
- You [installé](install.md) et [configuré](connect-data.md) la valeur [!DNL Data Connection] extension dans [!DNL Commerce].
- You [confirm](connect-data.md#confirm-that-event-data-is-collected) que votre [!DNL Commerce] les données d’événement arrivent à la périphérie Experience Platform.

## Étape 1 : créer un utilisateur dans votre [!DNL Commerce] environnement de test

Créez un utilisateur dans votre environnement de test et vérifiez que les informations de ce compte d’utilisateur s’affichent dans Experience Platform. Assurez-vous que l’email que vous avez spécifié est valide, car il est utilisé ultérieurement dans cette section pour envoyer l’email du panier abandonné.

1. Connectez-vous ou créez un compte dans votre [!DNL Commerce] environnement de test.

   ![Connexion à votre compte de test](assets/sign-in-account.png){width="700" zoomable="yes"}

   Avec la variable [!DNL Data Connection] installé et configuré, ces informations de compte sont envoyées à l’Experience Platform en tant que profil.

1. Vérifiez que les informations de votre compte d’utilisateur s’affichent dans la variable **[!UICONTROL Profile]** de l’Experience Platform.

   Accédez à **[!UICONTROL Profiles]** dans Adobe Experience Platform. Cliquez sur **[!UICONTROL Detail]** dans le profil pour afficher le profil que vous avez créé.

   ![Confirmer le profil](assets/check-event-profile.png){width="700" zoomable="yes"}

## Étape 2 : affichage des événements dans Journey Optimizer

Dans votre [!DNL Commerce] environnement de test, déclenchez des événements sur votre storefront en affichant des pages de produits, en ajoutant des éléments à un panier et en exécutant diverses autres activités qu’un acheteur doit exécuter. Vérifiez ensuite que ces événements arrivent à Journey Optimizer.

1. Launch [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/user-interface.html).
1. Sélectionner **[!UICONTROL Profiles]**.
1. Définir **[!UICONTROL Identity namespace]** to `Email`.
1. Définissez la variable **[!UICONTROL Identity value]** à votre adresse électronique.
1. Sélectionnez votre profil, puis cliquez sur le bouton **[!UICONTROL Events]** .

   ![Vérification des détails de l’événement](assets/check-event-details.png){width="700" zoomable="yes"}

   Recherchez le `commerce.checkouts` et examinez la payload de l’événement :

       &quot;json
       &quot;personID&quot;: &quot;84281643067178465783746543501073369488&quot;,
       &quot;eventType&quot;: &quot;commerce.checkouts&quot;,
       &quot;_id&quot;: &quot;4b41703f-e42e-485b-8d63-7001e3580856-0&quot;,
       &quot;commerce&quot;: {
       &quot;cart&quot;: {},
       &quot;checkouts&quot;: {
       &quot;value&quot;: 1
       }
       &quot;
   
   Comme vous pouvez le constater, la payload d’événement complète contient des données d’événement riches. Dans la section suivante, vous allez configurer les événements dans Journey Optimizer pour qu’ils écoutent les événements et y répondent. `commerce.checkouts` généré à partir de votre [!DNL Commerce] storefront.

## Étape 3 : configuration des événements dans Journey Optimizer

Configurez deux événements dans Journey Optimizer : un événement écoute les événements `commerce.checkouts` de Commerce, et l’autre est un événement de délai d’expiration de base qui attend un certain temps avant de déclencher un courrier électronique de panier abandonné.

### Créer un événement d’écouteur

1. Launch [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/user-interface.html).

1. Cliquez sur **[!UICONTROL Configurations]** sous le **[!UICONTROL Administration]** du volet de gauche.

1. Dans le **[!UICONTROL Events]** mosaïque, cliquez **[!UICONTROL Manage]**.

   ![Configuration des événements Journey Optimizer](assets/ajo-config.png){width="700" zoomable="yes"}

1. Sur le **[!UICONTROL Events]** page, cliquez sur **[!UICONTROL Create Event]**.

1. Dans le volet de navigation de droite, configurez votre événement comme suit :

   1. Définissez la variable **[!UICONTROL Name]** à : `firstname_lastname_checkout`.
   1. Définir **[!UICONTROL Type]** to **[!UICONTROL Unitary]**.
   1. Définir **[!UICONTROL Event id typ]e** to **[!UICONTROL Rule based]**.
   1. Définir **[!UICONTROL Schema]** à votre [!DNL Commerce] [schema](update-xdm.md).
   1. Sélectionner **[!UICONTROL Fields]** pour ouvrir le **[!UICONTROL Fields]** page. Sélectionnez ensuite les champs utiles à cet événement. Par exemple, sélectionnez tous les champs sous le **[!UICONTROL Product list items]**, **[!UICONTROL Commerce]**, **[!UICONTROL eventType]**, et **[!UICONTROL Web]**.
   1. Cliquez sur **[!UICONTROL OK]** pour enregistrer les champs sélectionnés.
   1. Cliquez dans le **[!UICONTROL Event id condition]** champ . Créez ensuite une condition : `eventType` est égal à `commerce.checkouts` ET `personalEmail.address` est égal à l’adresse électronique que vous avez utilisée lors de la création du profil dans la section précédente.

      ![Condition du jeu de Journey Optimizer](assets/ajo-set-condition.png){width="700" zoomable="yes"}

   1. Cliquez sur **[!UICONTROL OK]**.
   1. Cliquez sur **[!UICONTROL Save]** pour enregistrer votre événement.

### Création d’un événement de délai d’expiration

1. Créez un événement dans Journey Optimizer comme vous le faisiez auparavant.

1. Dans le volet de navigation de droite, configurez votre événement comme suit :

   1. Définissez la variable **[!UICONTROL Name]** à : `firstname_lastname_timeout`.
   1. Définir **[!UICONTROL Type]** to **[!UICONTROL Unitary]**.
   1. Définir **[!UICONTROL Event id type]** to **[!UICONTROL Rule based]**.
   1. Définir **[!UICONTROL Schema]** à votre [!DNL Commerce] [schema](update-xdm.md).
   1. Définissez la variable **[!UICONTROL Schema]**, **[!UICONTROL Fields]**, et **[!UICONTROL Event id condition]** comme ci-dessus.
   1. Cliquez sur **[!UICONTROL Save]** pour enregistrer votre événement.

Une fois ces deux événements configurés, créez un parcours qui envoie un email de panier abandonné.

## Étape 4 : création d’un parcours de passage en caisse

Créez un parcours qui écoute les `commerce.checkouts` puis envoie un courrier électronique au panier abandonné après un délai spécifié.

1. Dans Journey Optimizer, sélectionnez **[!UICONTROL Journeys]** under **J[!UICONTROL OURNEY MANAGEMENT]**.
1. Cliquez sur **[!UICONTROL Create Journey]**.
1. Indiquez le nom de votre parcours.
1. Cliquez sur **[!UICONTROL OK]** pour enregistrer le parcours.
1. Dans le volet de navigation de gauche, sous **[!UICONTROL EVENTS]** , recherchez l’événement de passage en caisse que vous avez créé précédemment : `firstname_lastname_checkout` et faites-le glisser et déposez-le sur la zone de travail.

   >[!TIP]
   >
   >Double-cliquez sur l’événement pour l’ajouter automatiquement à la zone de travail.

1. Recherchez l’événement de délai d’expiration et ajoutez-le à la zone de travail.
1. Double-cliquez sur l’événement de dépassement de délai.

   1. Dans le **[!UICONTROL Timeout]** , sélectionnez **[!UICONTROL Define the event time]** .
   1. Dans le **[!UICONTROL Wait for]** entrée de champ `1` et `Minute`.
   1. Sélectionnez la variable **[!UICONTROL Set a timeout path]** .

   Avec cette configuration de délai d’expiration, un acheteur qui effectue un passage en caisse mais ne termine pas la commande en une minute déclenche cette branche de délai d’expiration. Dans un environnement de production réel, vous le définiriez sur une plus longue période, par exemple 24 heures.

1. Dans la navigation de gauche sous **[!UICONTROL ACTIONS]**, ajoutez le **[!UICONTROL Email]** à la branche timeout. Votre parcours doit se présenter comme suit :

   ![Canevas Journey Optimizer](assets/ajo-canvas.png){width="700" zoomable="yes"}

### Créer un email de panier abandonné

Créez un email de panier abandonné qui est envoyé lorsqu’un panier abandonné est détecté.

1. Dans le parcours que vous avez créé ci-dessus, double-cliquez sur le **[!UICONTROL Email]** sur la zone de travail.

1. Suivez la [étapes](https://experienceleague.adobe.com/docs/journey-optimizer/using/content-management/personalization/personalization-use-cases/personalization-use-case-helper-functions.html#configure-email) dans le guide Journey Optimizer pour créer l’email du panier abandonné.

Vous disposez maintenant d’un parcours dans Journey Optimizer qui écoute le `commerce.checkouts` de votre [!DNL Commerce] boutique et un email de panier abandonné envoyé après un certain temps. La section suivante montre comment tester le parcours.

## Étape 5 : déclencher l’événement de passage en caisse en temps réel

Dans cette section, vous testez l’événement en temps réel.

1. Dans Journey Optimizer, activez le mode Test.

   ![Activation du mode test](assets/ajo-enable-test.png){width="700" zoomable="yes"}

1. Pour tester ce parcours en temps réel, ouvrez un autre onglet du navigateur et accédez au [!DNL Commerce] site web dans votre environnement de test.

   1. Ajoutez un produit à votre panier.
   1. Accédez à la page de passage en caisse.
   1. Depuis la page de passage en caisse, abandonnez le panier en revenant à la page principale ou en fermant votre onglet.

      Le parcours est maintenant déclenché. Pour confirmer, ouvrez l’onglet contenant votre parcours dans Journey Optimizer. Vous devriez voir une flèche verte qui indique le chemin emprunté par votre utilisateur.

1. Recherchez le courrier électronique dans votre boîte de réception.
