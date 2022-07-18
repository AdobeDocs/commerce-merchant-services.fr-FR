---
title: Paramètres des services de paiement
description: Après l’installation, vous pouvez configurer [!DNL Payment Services] dans la Maison.
role: Admin, User
level: Intermediate
exl-id: 108f2b24-39c1-4c87-8deb-d82ee1c24d55
source-git-commit: 7c02bb8dcb7b5daa68664bd12672ac389f84cfa1
workflow-type: tm+mt
source-wordcount: '688'
ht-degree: 0%

---

# Paramètres

Vous pouvez personnaliser [!DNL Payment Services] à vos besoins avec des paramètres utiles dans la [!DNL Payment Services] Chez soi.

Pour configurer [!DNL Payment Services] pour [!DNL Adobe Commerce] et [!DNL Magento Open Source] click **[!UICONTROL Settings]**. Ces options de configuration s’appliquent uniquement à l’environnement défini dans la variable _[!UICONTROL Payment mode]_dans Paramètres généraux.

Voir [[!UICONTROL General] section paramètres](#general-settings) pour plus d’informations.

>[!IMPORTANT]
>
> Pour une configuration multi-magasin ou héritée, reportez-vous à la section [Configuration dans l’administrateur](configure-admin.md) rubrique.

## Activation des services de paiement

Vous pouvez activer [!DNL Payment Services] pour votre site web et activez les tests sandbox ou les paiements en direct, dans la variable [!UICONTROL General] .

1. Sur le _Administration_ barre latérale, accédez à **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   ![Vue d’accueil](assets/payment-services-menu-small.png)

1. Cliquez sur **[!UICONTROL Settings]**. Voir [Introduction à [!DNL Payment Services] Accueil](payments-home.md) pour plus d’informations.

   Le _[!UICONTROL General]_comprend les paramètres utilisés pour activer [!DNL Payment Services] comme mode de paiement.

1. Pour activer [!DNL Payment Services] comme mode de paiement pour votre boutique, basculez (**[!UICONTROL Enable Payment Services as payment method]**) à `Yes`.

1. Si vous effectuez toujours des tests [!DNL Payment Services] pour votre boutique, définissez **Mode de paiement** to `Sandbox`. Si vous êtes prêt à activer les paiements en direct, définissez-le sur `Production`.

   >[!WARNING]
   >
   >Votre _[!UICONTROL Sandbox Merchant ID]_et_[!UICONTROL Production Merchant ID]_ sont générés automatiquement et présents dans leurs champs respectables lorsque vous avez terminé l’intégration pour l’environnement de test et/ou la production. Ne supprimez ou ne modifiez pas ces identifiants.

1. Sélectionnez la vue de magasin, dans la **[!UICONTROL Scope]** menu déroulant, pour lequel vous souhaitez activer un mode de paiement.
1. Pour modifier les paramètres par défaut des fonctions de paiement et de l’affichage du storefront, définissez les options supplémentaires nécessaires :

   - [Champs de carte de crédit](#credit-card-fields)
   - [Boutons de paiement](#payment-buttons)
   - [Style de bouton](#button-style)

1. Cliquez sur **[!UICONTROL Save]**.

   Si vous essayez de quitter cette vue sans enregistrer vos modifications, un modal s’affiche pour vous inviter à ignorer les modifications, à continuer les modifications ou à les enregistrer.

1. Accédez à **[!UICONTROL System]** > **[!UICONTROL Cache Management]** et cliquez sur **[!UICONTROL Flush Cache]** pour actualiser tous les caches non valides.

### Champs de carte de crédit

Le _[!UICONTROL Credit Card Fields]_ces paramètres offrent une option de paiement simple et sécurisée pour les modes de paiement par carte de crédit ou carte de débit.

Voir [Options de paiement](payments-options.md#paypal-smart-buttons) pour plus d’informations.

1. Pour modifier le nom du mode de paiement affiché lors de l’extraction, modifiez la valeur de la variable **[!UICONTROL Checkout title]** champ .
1. À [définir l’action de paiement ;](production.md#set-payment-services-as-payment-method), bascule **[!UICONTROL Payment action]** to `Authorize` ou `Authorize and Capture`.
1. Pour activer le mode de débogage, activez la fonction **[!UICONTROL Debug Mode]** sélecteur.

   Lorsque vous activez le mode de débogage, des informations de débogage supplémentaires sur le paiement par carte de crédit sont écrites dans la variable `var/log/payment.log` fichier . Ces informations peuvent vous donner plus d’informations sur un paiement spécifique pour faciliter la résolution des problèmes.

1. Cliquez sur **[!UICONTROL Save]**.

   Si vous essayez de quitter cette vue sans enregistrer vos modifications, un modal s’affiche pour vous inviter à ignorer les modifications, à continuer les modifications ou à les enregistrer.

1. Accédez à **[!UICONTROL System]** > **[!UICONTROL Cache Management]** et cliquez sur **[!UICONTROL Flush Cache]** pour actualiser tous les caches non valides.

### Boutons de paiement

Le [!DNL PayPal Smart Buttons] les options de paiement offrent un processus de paiement simple, rapide et sécurisé pour votre client. Voir [Options de paiement](payments-options.md#paypal-smart-buttons) pour plus d’informations.

Vous pouvez activer et configurer les boutons de paiement :

1. Pour modifier le nom du mode de paiement, comme indiqué lors de l’extraction, modifiez la valeur de la variable **[!UICONTROL Checkout Title]** champ .
1. À [définir l’action de paiement ;](production.md#set-payment-services-as-payment-method), bascule **[!UICONTROL Payment action]** to `Authorize` ou `Authorize and Capture`.
1. Utilisation des sélecteurs de basculement pour activer ou désactiver [!DNL PayPal smart button] fonctionnalités d’affichage :
   - **[!UICONTROL Show PayPal buttons on product detail page]**
   - **[!UICONTROL Show PayPal buttons on mini cart preview]**
   - **[!UICONTROL Show PayPal buttons on cart page]**
   - **[!UICONTROL Show PayPal Pay Later button]**
   - **[!UICONTROL Show Venmo button]**

1. Pour modifier la variable [Payer les messages plus tard](payments-options.md#pay-later-button), faites basculer le **[!UICONTROL Show PayPal Pay Later message]** .
1. Pour activer le mode de débogage, activez la fonction **[!UICONTROL Debug Mode]** sélecteur.

   Lorsque vous activez le mode de débogage, des informations de débogage supplémentaires sur le paiement PayPal sont écrites dans la variable `var/log/payment.log` fichier . Ces informations peuvent vous donner plus d’informations sur un paiement spécifique pour faciliter la résolution des problèmes.

1. Cliquez sur **[!UICONTROL Save]**.

   Si vous essayez de quitter cette vue sans enregistrer vos modifications, un modal s’affiche pour vous inviter à ignorer les modifications, à continuer les modifications ou à les enregistrer.

1. Accédez à **[!UICONTROL System]** > **[!UICONTROL Cache Management]** et cliquez sur **[!UICONTROL Flush Cache]** pour actualiser tous les caches non valides.

#### Style de bouton

Vous pouvez également configurer la variable _[!UICONTROL Button style]_options des boutons Paiement :

1. Pour modifier la variable **[!UICONTROL Layout]**, sélectionnez `Vertical` ou `Horizontal`.

   >[!NOTE]
   >
   > Si le style du bouton est configuré comme `Horizontal` et que votre boutique est configurée pour afficher plusieurs boutons de paiement, vous ne pouvez afficher que deux boutons sur la page produit, la page de passage en caisse et le mini-panier, ainsi qu’un bouton sur le panier.

1. Pour activer le tag dans une disposition horizontale, faites basculer le **[!UICONTROL Show tagline]** sélecteur.
1. Pour modifier la variable **[!UICONTROL Color]**, sélectionnez la couleur de votre choix.
1. Pour modifier la variable **[!UICONTROL Shape]**, sélectionnez `Pill` ou `Rect`.
1. Pour activer le sélecteur de hauteur de bouton, faites basculer le bouton **[!UICONTROL Responsive button height]** sélecteur.
1. Pour modifier la variable **[!UICONTROL Label]**, sélectionnez l’option de libellé de votre choix.
1. Cliquez sur **[!UICONTROL Save]**.

   Si vous essayez de quitter cette vue sans enregistrer vos modifications, un modal s’affiche pour vous inviter à ignorer les modifications, à continuer les modifications ou à les enregistrer.

1. Accédez à **[!UICONTROL System]** > **[!UICONTROL Cache Management]** et cliquez sur **[!UICONTROL Flush Cache]** pour actualiser tous les caches non valides.

Vous pouvez configurer [!DNL PayPal Smart Buttons] style dans l’administrateur ou [!DNL Payment Services Home]. Voir [Guide de style Boutons de PayPal](https://developer.paypal.com/docs/checkout/standard/customize/buttons-style-guide/) pour plus d’informations.
