---
title: Création d’une audience dans Real-Time CDP à l’aide de données d’événement  [!DNL Commerce]
description: Découvrez comment utiliser les données d'événement  [!DNL Commerce] pour créer une audience dans Real-Time CDP
role: Admin, Developer
feature: Personalization, Integration
exl-id: b637f40b-0d35-4c41-a4eb-563085966dc0
source-git-commit: fc6d33dcd069b5351b3e953daa14ca0014ee093d
workflow-type: tm+mt
source-wordcount: '1040'
ht-degree: 0%

---

# Création d’audiences dans Real-Time CDP à l’aide des données d’événement [!DNL Commerce]

Utilisez les données d’événement capturées dans votre boutique [!DNL Commerce] pour créer des audiences dans Real-Time CDP. Les données capturées sont basées sur le comportement de navigation, les achats passés, les attributs de profil, les propensions à convertir ou à générer, l’état de fidélité, la valeur client élevée et faible, etc.

## Quelles données dois-je envisager d’utiliser ?

Créez des audiences dans Real-Time CDP à l’aide de données issues d’événements storefront, back-office et de profil.

| Types de données | Données Storefront (Événements comportementaux) | Données du back-office (événements côté serveur) | Données de profil et de segment du client |
|---|---|---|---|
| **Définition** | Clics ou actions des clients sur votre site. | Informations sur le cycle de vie et détails de chaque commande (passé et actuel). | Qui sont vos acheteurs et à quels segments sont-ils qualifiés ? |
| **Événements capturés par Adobe Commerce** | [productPageView](events.md#productpageview)<br>[addToCart](events.md#addtocart) | [placeOrder](events.md#completecheckout)<br>[orderplace](events-backoffice.md#orderplaced)<br>[orderLineItemRefunding](events-backoffice.md#orderlineitemrefunded)<br>[order Canceled](events-backoffice.md#ordercancelled)<br>[historique des commandes](connect-data.md#send-historical-order-data) | [createAccount](events.md#createaccount)<br>[editAccount](events.md#editaccount)<br>[Enregistrement de profil](events-profilerecord.md) |

## Qu’ont réalisé d’autres clients ?

Les clients d’Adobe [!DNL Commerce] ont eu des répercussions importantes sur l’entreprise en activant les audiences créées dans Real-Time CDP et en les déployant sur leur instance [!DNL Commerce].

Un détaillant mondial de vêtements multimarques a obtenu les résultats suivants :

- Une source de vérité avec 10 millions de profils client unifiés
- Création de plus de 40 audiences uniques de &quot;clients à haut niveau d’intention&quot; pour interagir entre les canaux

Une société mondiale de boissons a collecté :

- 98 millions de profils client provenant de plus de 100 pays

## Commençons

Dans cet article, vous apprendrez à :

- Créez une audience dans Real-Time CDP en fonction des données [!DNL Commerce] collectées par les événements
- Activez cette audience pour votre boutique [!DNL Commerce].
- Utiliser l’audience de [!DNL Commerce] pour informer une règle de prix de panier

>[!IMPORTANT]
>
>Effectuez les tâches décrites dans cet article en utilisant votre environnement de test [!DNL Commerce]. Cela permet de s’assurer que les données d’événement storefront et back-office que vous envoyez à Experience Platform ne diluent pas vos données d’événement de production.

### Conditions préalables

Avant de commencer, assurez-vous que :

- Vous êtes configuré pour utiliser Real-Time CDP. Si vous n’en êtes pas sûr, contactez votre intégrateur de systèmes ou l’équipe de développement qui gère les projets et les environnements.
- Vous [ avez ](install.md) installé et [configuré](connect-data.md) l’extension [!DNL Data Connection] dans [!DNL Commerce].
- Vous [avez confirmé](connect-data.md#confirm-that-event-data-is-collected) que vos données d’événement [!DNL Commerce] arrivent sur le bord Experience Platform.

### 1. Création d’une audience

Une audience est un ensemble de clients qui partagent un comportement ou des caractéristiques similaires. Dans cet exercice, vous créez une audience qui qualifie les personnes intéressées par un produit particulier de votre boutique.

Pour simplifier cet exercice, vous utilisez les données d’événement de l’événement [productPageView](events.md#productpageview) . Cet événement capture les détails du produit consulté, tels que le nom, le SKU, le prix, etc. du produit.

Utilisez ces données d’événement pour indiquer que l’audience inclut des personnes qui ont au moins un événement &quot;Consultations produits&quot; où le SKU (identifiant du produit) est égal à un produit spécifique sur votre site et où l’événement se produit au cours du dernier jour. &#x200B;

1. Ouvrez Experience Platform et sélectionnez **[!UICONTROL Audiences]** dans le menu de navigation de gauche.

   ![Tableau de bord d’audience](assets/audience-left-rail.png)

1. Cliquez sur **[!UICONTROL Create Audience]**.

   ![Créer une audience](assets/browse-create-audience.png)

   L’espace de travail **Créateur de segments** s’affiche.

1. Dans l’espace de travail **Créateur de segments**, sélectionnez la méthode de création **Créer une règle**.

   ![Créer la règle](assets/build-rule.png)

   L’espace de travail **Créateur de segments** vous permet de définir les règles et conditions de votre audience. &#x200B; Ces règles et conditions sont basées sur les données d’événement et de profil de votre magasin Commerce et définissent les critères qui déterminent si un utilisateur est admissible pour l’audience. Vous pouvez par exemple créer une règle qui inclut les utilisateurs qui ont consulté un produit spécifique ou ceux qui ont effectué un achat au cours d’une période donnée. En savoir plus sur le [créateur de segments](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder) et les règles et conditions.

1. Sélectionnez l’onglet [Événements](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder#events) .

   ![Onglet Événements](assets/audience-events-tab.png)

1. Recherchez le type d’événement &quot;Consultations produits&quot;. Ensuite, faites-le glisser et déposez-le dans l’espace de travail **Créateur de segments**.

1. Revenez à l’onglet **Events** et recherchez &quot;SKU&quot;, qui est un champ de données sous le champ `productListItems` . Faites-le glisser et déposez-le dans l’espace de travail **Créateur de segments** au-dessus de l’événement **Consultation produit**.

   La section **Règles d’événement** s’affiche où vous pouvez spécifier le produit spécifique dont vous souhaitez créer votre audience.

   ![Sélectionner un SKU](assets/audience-addsku.png)

1. Définissez l’intervalle sur un jour en cliquant sur **Any Time** et en sélectionnant *In last* avec la valeur *1*.

   Lors de la création d’une audience, vous pouvez spécifier un intervalle de temps pour capturer l’activité récente. La définition d’un intervalle de temps vous permet de cibler les utilisateurs en fonction de leurs interactions ou comportements récents au cours d’une période spécifique.

1. Dans la section **Propriétés de l’audience** située à droite de l’espace de travail, définissez les propriétés de l’audience en fournissant un nom, une description et une méthode d’évaluation pour l’audience.

1. Pour enregistrer l’audience, cliquez sur **[!UICONTROL Save and Close]**.

   Les détails de votre audience s’affichent sur le tableau de bord **Audience**.

### 2. Activez l’audience vers la destination [!DNL Commerce]

Vous rendez une audience disponible dans [!DNL Commerce] en l’activant pour la destination [!DNL Commerce].

>[!IMPORTANT]
>
>Si vous n&#39;avez pas déjà défini [!DNL Commerce] comme destination disponible pour la réception des données, consultez la rubrique [Adobe [!DNL Commerce] Connexion](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/personalization/adobe-commerce) .

1. Dans l&#39;onglet **Détails** de votre audience, cliquez sur **Activer à la destination**.

1. Sélectionnez votre destination [!DNL Commerce]. Cliquez ensuite sur **Suivant**.

1. Terminez le processus d’activation en cliquant sur **[!UICONTROL Finish]**.

## 3. Afficher l’audience dans le tableau de bord des audiences

Dans [!DNL Commerce], vous pouvez afficher toutes les audiences [actives](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-edge-personalization-destinations) qui peuvent être personnalisées pour votre instance [!DNL Commerce] à l’aide du tableau de bord **Audiences Real-Time CDP**.

Pour accéder au tableau de bord **Audiences Real-Time CDP**, accédez à la barre latérale _Admin_, puis accédez à **[!UICONTROL Customers]** > **[!UICONTROL Real-time CDP Audience]**.

Dans le tableau de bord, recherchez l’audience que vous avez créée. Notez qu’il n’est pas utilisé dans une règle de prix de panier ou un bloc dynamique. Dans la section suivante, vous associez l’audience à une règle de prix de panier.

![Tableau de bord des audiences Real-Time CDP](assets/real-time-cdp-dashboard.png)

### 4. Créez une règle de prix de panier basée sur l’audience

Cette section vous explique comment créer une règle de prix de panier basée sur votre nouvelle audience.

1. Vérifiez que la nouvelle audience s’affiche dans le tableau de bord **Audiences Real-Time CDP**.
1. [Créez une règle de prix de panier](https://experienceleague.adobe.com/en/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-create).
1. [Définissez la condition](https://experienceleague.adobe.com/en/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-create#use-real-time-cdp-audiences-to-set-a-condition) de la règle de prix du panier à l’aide de votre nouvelle audience.
1. [Définissez l’action](https://experienceleague.adobe.com/en/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-create#step-3-define-the-actions) que vous souhaitez réaliser lorsque le produit est ajouté au panier.
1. Continuez à configurer la règle de prix du panier.
1. Accédez à la vue du client de votre instance sandbox.
1. Ajoutez le produit que vous avez basé l’audience de dans le panier. Notez que la règle de prix du panier est activée.

## Terminer

Dans cet exercice, vous avez créé une audience dans Real-Time CDP et l’avez activée sur la destination [!DNL Commerce]. Ensuite, dans l’administrateur [!DNL Commerce], vous avez créé une règle de prix de panier basée sur cette audience et activé la règle dans votre environnement de test.
