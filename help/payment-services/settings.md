---
title: Paramètres des services de paiement
description: Après l’installation, vous pouvez configurer [!DNL Payment Services] dans la Maison.
role: Admin, User
level: Intermediate
source-git-commit: 9596815e31402f23b399b223f3221074331c1773
workflow-type: tm+mt
source-wordcount: '640'
ht-degree: 0%

---

# Configuration dans la vue Accueil

Vous pouvez personnaliser [!DNL Payment Services] à vos besoins avec des paramètres utiles dans la vue Accueil.

Pour configurer [!DNL Payment Services] pour [!DNL Adobe Commerce] et [!DNL Magento Open Source] click **[!UICONTROL Settings]**. Ces options de configuration s’appliquent uniquement à l’environnement défini dans la variable _[!UICONTROL Payment mode]_dans les Paramètres généraux.

Voir [[!UICONTROL General] section paramètres](#general-settings) pour plus d’informations.

>[!IMPORTANT]
>
> Pour une configuration multi-magasin ou héritée, reportez-vous à la section [Configuration dans l’administrateur](configure-admin.md) rubrique.

## Configuration des services de paiement

Vous pouvez activer [!DNL Payment Services] pour votre site web et activez les tests sandbox ou les paiements en direct dans la variable [!UICONTROL General] paramètres .

1. Sur le _Administration_ barre latérale, accédez à **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   ![Vue d’accueil](assets/payment-services-menu-small.png)

1. Dans la vue Accueil, cliquez sur **[!UICONTROL Settings]**. Voir [Accueil](payments-home.md) pour plus d’informations.

   Le _[!UICONTROL General]_comprend les options de configuration utilisées pour définir [!DNL Payment Services] comme mode de paiement.

1. Pour l’option de basculement en haut de l’écran (**[!UICONTROL Enable Payment Services as payment method]**), définissez-le sur `Yes` pour activer [!DNL Payment Services] pour votre site web.

1. Pour **Mode de paiement**, définissez-le sur `Sandbox` si vous effectuez toujours des tests [!DNL Payment Services] pour votre boutique ou `Production` si vous êtes prêt à activer les paiements en direct.

   >[!WARNING]
   >
   >Votre _[!UICONTROL Sandbox Merchant ID]_et_[!UICONTROL Production Merchant ID]_ sont générés automatiquement et présents dans leurs champs respectables lorsque vous avez terminé l’intégration à l’environnement de test et/ou à la production. Ne supprimez ou ne modifiez pas ces identifiants.

1. Pour modifier les paramètres par défaut des fonctions de paiement et de l’affichage du storefront, définissez les options supplémentaires nécessaires :

   - [Champs de carte de crédit](#credit-card-fields)
   - [Boutons intelligents PayPal](#paypal-smart-buttons)
   - [Style de bouton](#button-style)

1. Pour enregistrer vos modifications, cliquez sur **[!UICONTROL Save]** en haut à droite de la page.

   Si vous essayez de quitter cette vue sans enregistrer vos modifications, un modal s’affiche pour vous inviter à ignorer les modifications, à continuer les modifications ou à les enregistrer.

1. Accédez à **[!UICONTROL System]** > **[!UICONTROL Cache Management]** et cliquez sur **[!UICONTROL Flush Cache]** pour actualiser tous les caches non valides.

### Champs de carte de crédit

Le _[!UICONTROL Credit Card Fields]_les options de paiement offrent un passage en caisse simple et sécurisé pour les modes de paiement par carte de crédit ou carte de débit.

Voir [Options de paiement](payments-options.md#paypal-smart-buttons) pour plus d’informations.

1. Pour **[!UICONTROL Checkout title]**, saisissez du texte (si nécessaire) pour modifier le nom du mode de paiement affiché lors de l’extraction.
1. À [définir l’action de paiement ;](production.md#set-payment-services-as-payment-method), définit **[!UICONTROL Payment action]** to `Authorize` ou `Authorize and Capture`.
1. Pour **[!UICONTROL Debug Mode]**, faites basculer le sélecteur pour activer le mode de débogage.
1. Pour enregistrer vos modifications, cliquez sur **[!UICONTROL Save]** en haut à droite de la page.

   Si vous essayez de quitter cette vue sans enregistrer vos modifications, un modal s’affiche pour vous inviter à ignorer les modifications, à continuer les modifications ou à les enregistrer.

1. Accédez à **[!UICONTROL System]** > **[!UICONTROL Cache Management]** et cliquez sur **[!UICONTROL Flush Cache]** pour actualiser tous les caches non valides.

### Boutons intelligents PayPal

Le [!DNL PayPal Smart Buttons] les options de paiement offrent un processus de paiement simple, rapide et sécurisé pour votre client. Voir [Options de paiement](payments-options.md#paypal-smart-buttons) pour plus d’informations.

Vous pouvez activer les options de paiement des boutons intelligents PayPal dans Accueil :

1. Pour modifier le nom du mode de paiement, comme indiqué lors de l’extraction, modifiez la valeur de la variable **[!UICONTROL Checkout Title]** champ .
1. À [définir l’action de paiement ;](production.md#set-payment-services-as-payment-method), définit **[!UICONTROL Payment action]** to `Authorize` ou `Authorize and Capture`.
1. Utilisation des sélecteurs de basculement pour activer ou désactiver [!DNL PayPal smart button] fonctionnalités d’affichage :
   - **[!UICONTROL Show buttons on product detail page]**
   - **[!UICONTROL Show buttons in mini cart preview]**
   - **[!UICONTROL Show buttons on cart page]**
   - **[!UICONTROL Show Venmo button]**.
   - **[!UICONTROL PayPal Pay Later enabled]** pour activer l’option d’affichage du bouton lors de l’extraction.

1. Pour modifier la variable [Payer les messages plus tard](payments-options.md#pay-later-button) (si vous le souhaitez), activez la variable **[!UICONTROL Display Pay Later message]** .
1. Pour activer le mode de débogage, cliquez sur **[!UICONTROL Debug Mode]**,
1. Pour enregistrer vos modifications, cliquez sur **[!UICONTROL Save]** en haut à droite de la page.

   Si vous essayez de quitter cette vue sans enregistrer vos modifications, un modal s’affiche pour vous inviter à ignorer les modifications, à continuer les modifications ou à les enregistrer.

1. Accédez à **[!UICONTROL System]** > **[!UICONTROL Cache Management]** et cliquez sur **[!UICONTROL Flush Cache]** pour actualiser tous les caches non valides.

### Style de bouton

Vous pouvez également configurer la variable _[!UICONTROL Button style]_options des boutons intelligents PayPal dans la page d’accueil :

1. Pour modifier la variable **[!UICONTROL Layout]**, sélectionnez `Vertical` ou `Horizontal`.
1. Pour activer le tag dans une disposition horizontale, cliquez sur **[!UICONTROL Show tagline]**.
1. Pour modifier la variable **[!UICONTROL Color]**, sélectionnez la couleur de votre choix.
1. Pour modifier la variable **[!UICONTROL Shape]**, sélectionnez `Pill` ou `Rect`.
1. Pour activer le sélecteur de hauteur de bouton, cliquez sur **[!UICONTROL Responsive button height]**.
1. Pour modifier la variable **[!UICONTROL Label]**, sélectionnez l’option de libellé de votre choix.
1. Pour enregistrer vos modifications, cliquez sur **[!UICONTROL Save]** en haut à droite de la page.

   Si vous essayez de quitter cette vue sans enregistrer vos modifications, un modal s’affiche pour vous inviter à ignorer les modifications, à continuer les modifications ou à les enregistrer.

1. Accédez à **[!UICONTROL System]** > **[!UICONTROL Cache Management]** et cliquez sur **[!UICONTROL Flush Cache]** pour actualiser tous les caches non valides.

Vous pouvez configurer [!DNL PayPal Smart Buttons] style dans l’Admin ou la page d’accueil. Voir [Guide de style Boutons de PayPal](https://developer.paypal.com/docs/checkout/standard/customize/buttons-style-guide/) pour plus d’informations.
