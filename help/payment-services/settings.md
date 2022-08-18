---
title: Paramètres des services de paiement
description: Après l’installation, vous pouvez configurer [!DNL Payment Services] dans la Maison.
role: Admin, User
level: Intermediate
exl-id: 108f2b24-39c1-4c87-8deb-d82ee1c24d55
source-git-commit: ecfe1448a0272fe5401090b322f4b69dffd1a8fa
workflow-type: tm+mt
source-wordcount: '1087'
ht-degree: 0%

---

# Paramètres

Vous pouvez personnaliser [!DNL Payment Services] à vos besoins avec des paramètres utiles dans la [!DNL Payment Services] Chez soi.

Pour configurer [!DNL Payment Services] pour [!DNL Adobe Commerce] et [!DNL Magento Open Source] click **[!UICONTROL Settings]**. Ces options de configuration s’appliquent uniquement à l’environnement défini dans la variable _[!UICONTROL Payment mode]_champ dans_[!UICONTROL Settings]_ > _[!UICONTROL General]_.

>[!IMPORTANT]
>
> Pour une configuration multi-magasin ou héritée, reportez-vous à la section [Configuration dans l’administrateur](configure-admin.md) rubrique.

## Activation des services de paiement

Vous pouvez activer [!DNL Payment Services] pour votre site web et activez les tests sandbox ou les paiements en direct, dans la variable [!UICONTROL General] .

1. Sur le _Administration_ barre latérale, accédez à **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   ![Vue d’accueil](assets/payment-services-menu-small.png)

1. Cliquez sur **[!UICONTROL Settings]**. Voir [Introduction à [!DNL Payment Services] Accueil](payments-home.md) pour plus d’informations.

   Le _[!UICONTROL General]_comprend les paramètres utilisés pour activer [!DNL Payment Services] comme mode de paiement.

1. Pour activer [!DNL Payment Services] comme mode de paiement pour votre boutique, dans la variable _[!UICONTROL General]_section, bascule (**[!UICONTROL Enable Payment Services as payment method]**) à `Yes`.

1. Si vous effectuez toujours des tests [!DNL Payment Services] pour votre boutique, définissez **Mode de paiement** to `Sandbox`. Si vous êtes prêt à activer les paiements en direct, définissez-le sur `Production`.

   >[!NOTE]
   >
   >Votre _[!UICONTROL Sandbox Merchant ID]_et_[!UICONTROL Production Merchant ID]_ sont générés automatiquement et présents dans leurs champs respectables lorsque vous avez terminé l’intégration pour l’environnement de test et/ou la production.

1. Cliquez sur **[!UICONTROL Save]**.

   Si vous essayez de quitter cette vue sans enregistrer vos modifications, un modal s’affiche pour vous inviter à ignorer les modifications, à continuer les modifications ou à les enregistrer.

1. Accédez à **[!UICONTROL System]** > **[!UICONTROL Cache Management]** et cliquez sur **[!UICONTROL Flush Cache]** pour actualiser tous les caches non valides.

Vous pouvez maintenant modifier les paramètres par défaut pour [options de paiement](#configure-payment-options) fonctions et affichage du storefront.

### Options de configuration générales

| Champ | Portée | Description |
|---|---|---|
| [!UICONTROL Enable] | site web | Activer ou désactiver [!DNL Payment Services] pour votre site web. Options : [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Payment mode] | vue de magasin | Définissez la méthode, ou l’environnement, de votre magasin. Options : [!UICONTROL Sandbox] / [!UICONTROL Production] |
| [!UICONTROL Sandbox Merchant ID] | vue de magasin | Votre ID de marchand d’environnement de test, qui est généré automatiquement lors de l’intégration des environnements de test. |
| [!UICONTROL Production Merchant ID] | vue de magasin | Votre identifiant commercial de production, qui est généré automatiquement lors de l’intégration des environnements de test. |

## Configuration des options de paiement

Maintenant que vous avez activé les services de paiement pour votre site web, vous pouvez modifier les paramètres par défaut des fonctions de paiement et de l’affichage du storefront.

### Champs de carte de crédit

Le _[!UICONTROL Credit Card Fields]_ces paramètres offrent une option de paiement simple et sécurisée pour les modes de paiement par carte de crédit ou carte de débit.

Voir [Options de paiement](payments-options.md#credit-card-fields) pour plus d’informations.

1. Sélectionnez la vue de magasin, dans la **[!UICONTROL Scope]** menu déroulant, pour lequel vous souhaitez activer un mode de paiement.
1. Pour modifier le nom du mode de paiement affiché lors de l’extraction, modifiez la valeur de la variable **[!UICONTROL Checkout title]** champ .
1. À [définir l’action de paiement ;](production.md#set-payment-services-as-payment-method), bascule **[!UICONTROL Payment action]** to `Authorize` ou `Authorize and Capture`.
1. Pour activer le mode de débogage, activez la fonction **[!UICONTROL Debug Mode]** sélecteur.
1. Cliquez sur **[!UICONTROL Save]**.

   Si vous essayez de quitter cette vue sans enregistrer vos modifications, un modal s’affiche pour vous inviter à ignorer les modifications, à continuer les modifications ou à les enregistrer.

1. Accédez à **[!UICONTROL System]** > **[!UICONTROL Cache Management]** et cliquez sur **[!UICONTROL Flush Cache]** pour actualiser tous les caches non valides.

#### Options de configuration

| Champ | Portée | Description |
|---|---|---|
| [!UICONTROL Title] | vue de magasin | Ajoutez le texte à afficher comme titre de cette option de paiement dans la vue Mode de paiement lors de l’extraction. Options : [!UICONTROL text field] |
| [!UICONTROL Payment Action] | site web | Le [action de paiement](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target=&quot;_blank&quot;} pour le mode de paiement spécifié. Options : [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Debug Mode] | site web | Activez ou désactivez le mode de débogage. Options : [!UICONTROL Yes] / [!UICONTROL No] |

### Boutons de paiement

Le [!DNL PayPal Smart Buttons] les options de paiement offrent un processus de paiement simple, rapide et sécurisé pour votre client. Voir [Options de paiement](payments-options.md#paypal-smart-buttons) pour plus d’informations.

Vous pouvez activer et configurer les options de paiement des boutons intelligents PayPal :

1. Sélectionnez la vue de magasin, dans la **[!UICONTROL Scope]** menu déroulant, pour lequel vous souhaitez activer un mode de paiement.
1. Pour modifier le nom du mode de paiement, comme indiqué lors de l’extraction, modifiez la valeur de la variable **[!UICONTROL Checkout Title]** champ .
1. À [définir l’action de paiement ;](production.md#set-payment-services-as-payment-method), bascule **[!UICONTROL Payment action]** to `Authorize` ou `Authorize and Capture`.
1. Utilisation des sélecteurs de basculement pour activer ou désactiver [!DNL PayPal smart button] fonctionnalités d’affichage :
   - **[!UICONTROL Show PayPal buttons on product detail page]**
   - **[!UICONTROL Show PayPal buttons in mini cart preview]**
   - **[!UICONTROL Show PayPal buttons on cart page]**
   - **[!UICONTROL Show PayPal Pay Later button]**
   - **[!UICONTROL Show PayPal Pay Later message]**
   - **[!UICONTROL Show Venmo button]**
   - **[!UICONTROL Show Apple Pay button]**

      >[!NOTE]
      >
      > Pour utiliser Apple Pay [Posséder un compte développeur Apple](test-validate.md#test-in-sandbox-environment) (avec une fausse carte de crédit et des informations de facturation) pour le tester. Lorsque vous êtes prêt à utiliser Apple Pay dans un environnement de test *ou* mode de production, après avoir effectué toute [test et validation](test-validate.md), contactez votre représentant commercial pour l’activer pour vos boutiques actives.

      Lorsque vous activez/désactivez la visibilité des boutons de paiement ou le message PayPal Pay Later, un aperçu visuel de cette configuration s’affiche au bas de la page Paramètres .

1. Pour activer le mode de débogage, activez la fonction **[!UICONTROL Debug Mode]** sélecteur.
1. Cliquez sur **[!UICONTROL Save]**.

   Si vous essayez de quitter cette vue sans enregistrer vos modifications, un modal s’affiche pour vous inviter à ignorer les modifications, à continuer les modifications ou à les enregistrer.

1. Accédez à **[!UICONTROL System]** > **[!UICONTROL Cache Management]** et cliquez sur **[!UICONTROL Flush Cache]** pour actualiser tous les caches non valides.

#### Options de configuration

| Champ | Portée | Description |
|---|---|---|
| [!UICONTROL Title] | vue de magasin | Ajoutez le texte à afficher comme titre pour cette option de paiement dans la vue Mode de paiement lors de l’extraction. Options : champ de texte |
| [!UICONTROL Payment Action] | site web | Le [action de paiement](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target=&quot;_blank&quot;} pour le mode de paiement spécifié. Options : [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Show PayPal buttons on product detail page] | vue de magasin | Activer ou désactiver [!DNL PayPal Smart Buttons] sur la page des détails du produit. Options : [!UICONTROL  Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal buttons in mini cart preview] | vue de magasin | Activer ou désactiver [!DNL PayPal Smart Buttons] dans l’aperçu du mini panier. Options : [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal buttons on cart page] | vue de magasin | Activer ou désactiver [!DNL PayPal Smart Buttons] sur la page du panier. Options : [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal Pay Later button] | vue de magasin | Activez ou désactivez l’aspect de l’option de paiement ultérieur lorsque des boutons de paiement s’affichent. Options : [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal Pay Later Message] | site web | Activez ou désactivez la messagerie Payer plus tard dans le panier, la page du produit, le mini-panier et pendant le flux de passage en caisse. Options : [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show Venmo button] | vue de magasin | Activez ou désactivez l’option de paiement Venmo lorsque les boutons de paiement s’affichent. Options : [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show Apple Pay button] | vue de magasin | Activez ou désactivez l’option Paiement Apple dans laquelle les boutons de paiement s’affichent. Options : [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Debug Mode] | site web | Activez ou désactivez le mode de débogage. Options : [!UICONTROL Yes] / [!UICONTROL No] |

### Style de bouton

Vous pouvez également configurer la variable _[!UICONTROL Button style]_options des boutons intelligents PayPal :

1. Pour modifier la variable **[!UICONTROL Layout]**, sélectionnez `Vertical` ou `Horizontal`.

   >[!NOTE]
   >
   > Si le style du bouton est configuré comme `Horizontal` et que votre boutique est configurée pour afficher plusieurs boutons intelligents PayPal, vous ne pouvez voir que deux boutons affichés sur la page produit, la page de passage en caisse et le mini-panier, et un bouton affiché dans le panier.

1. Pour activer le tag dans une disposition horizontale, faites basculer le **[!UICONTROL Show tagline]** sélecteur.
1. Pour modifier la variable **[!UICONTROL Color]**, sélectionnez la couleur de votre choix.
1. Pour modifier la variable **[!UICONTROL Shape]**, sélectionnez `Pill` ou `Rect`.
1. Pour activer le sélecteur de hauteur de bouton, faites basculer le bouton **[!UICONTROL Responsive button height]** sélecteur.
1. Pour modifier la variable **[!UICONTROL Label]**, sélectionnez l’option de libellé de votre choix.

   Lorsque vous modifiez les options de configuration pour la disposition, la couleur, la forme, la hauteur et le libellé, un aperçu visuel de cette configuration s’affiche au bas de la page Paramètres .

1. Cliquez sur **[!UICONTROL Save]**.

   Si vous essayez de quitter cette vue sans enregistrer vos modifications, un modal s’affiche pour vous inviter à ignorer les modifications, à continuer les modifications ou à les enregistrer.

1. Accédez à **[!UICONTROL System]** > **[!UICONTROL Cache Management]** et cliquez sur **[!UICONTROL Flush Cache]** pour actualiser tous les caches non valides.

Vous pouvez configurer [!DNL PayPal Smart Buttons] style [dans la configuration héritée de l’administrateur.](configure-admin.md#configure-paypal-smart-buttons) ou ici dans [!DNL Payment Services Home]. Voir [Guide de style Boutons de PayPal](https://developer.paypal.com/docs/checkout/standard/customize/buttons-style-guide/) pour plus d’informations sur les options.

#### Options de configuration

| Champ | Portée | Description |
|--- |--- |--- |
| [!UICONTROL Layout] | Affichage en magasin | Définissez le style de mise en page des boutons de paiement. Options : [!UICONTROL Vertical] / [!UICONTROL Horizontal] |
| [!UICONTROL Tagline] | Affichage en magasin | Activez/désactivez tagline. Options : [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Color] | Affichage en magasin | Définissez la couleur des boutons de paiement. Options : [!UICONTROL Blue] / [!UICONTROL Gold] / [!UICONTROL Silver] / [!UICONTROL White] / [!UICONTROL Black] |
| [!UICONTROL Shape] | Affichage en magasin | Définissez la forme des boutons de paiement. Options : [!UICONTROL Rectangular] / [!UICONTROL Pill] |
| [!UICONTROL Responsive Button Height] | Affichage en magasin | Définit si les boutons de paiement utilisent une hauteur par défaut. Options : [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Height] | Affichage en magasin | Définissez la hauteur des boutons de paiement. Valeur par défaut : none |
| [!UICONTROL Label] | Affichage en magasin | Définissez le libellé qui apparaît dans les boutons de paiement. Options : [!UICONTROL PayPal] / [!UICONTROL Checkout] / [!UICONTROL Buynow] / [!UICONTROL Pay] / [!UICONTROL Installment] |
