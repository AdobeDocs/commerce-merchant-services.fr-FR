---
title: Configuration des services de paiement hérités
description: Après l’installation, vous pouvez configurer [!DNL Payment Services] dans la configuration du magasin.
role: Admin, User
level: Intermediate
exl-id: e1a3269d-bdf9-4b0f-972f-e8a0ef469503
feature: Payments, Checkout, Configuration
source-git-commit: 90bfa7099924feb308397960cff76bdf177bbe49
workflow-type: tm+mt
source-wordcount: '954'
ht-degree: 0%

---

# Hérité [!DNL Payment Services] Configuration

Vous pouvez personnaliser [!DNL Payment Services] à vos besoins avec des options de configuration utiles dans l’Admin.

Lorsque vous configurez [!DNL Payment Services] pour [!DNL Adobe Commerce] et [!DNL Magento Open Source] dans l’Admin, ces configurations s’appliquent uniquement à l’environnement défini dans la variable _[!UICONTROL Method]_champ de_[!UICONTROL General Configuration]_. Les modifications que vous apportez dans les champs de configuration ne sont pas liées au changement de _[!UICONTROL Method]_selection : si vous changez de méthode, vos sélections ne sont pas réinitialisées.

## Configuration générale

Vous pouvez activer [!DNL Payment Services] pour votre magasin et activez le test sandbox ou les paiements en direct dans la variable _[!UICONTROL General Configuration]_.

1. Sur le _Administration_ barre latérale, accédez à **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Dans le panneau de gauche, développez **[!UICONTROL Sales]** et choisissez **[!UICONTROL Payment Methods]**.

   ![Affichage des méthodes](assets/methods-view.png)

1. Développez l’objet _[!UICONTROL Recommended Solutions]_.
1. Dans le _[!UICONTROL [!DNL Payment Services]]_, développez la section_[!UICONTROL General Configuration]_ .
1. Pour **Activer**, définissez-le sur `Yes` pour activer [!DNL Payment Services] pour votre magasin.
1. Pour **Méthode**, définissez-le sur `Sandbox` si vous effectuez toujours des tests [!DNL Payment Services] pour votre boutique ou `Production` si vous êtes prêt à activer les paiements en direct.

   >[!WARNING]
   >
   >Votre _[!UICONTROL Sandbox Merchant ID]_et_[!UICONTROL Production Merchant ID]_ sont générés automatiquement et présents dans leurs champs respectables lorsque vous avez terminé l’intégration à l’environnement de test et/ou à la production. Ne supprimez ou ne modifiez pas ces identifiants.

1. Cliquez sur **[!UICONTROL Save Config]** pour enregistrer vos modifications.
1. Accédez à **[!UICONTROL System]** > **[!UICONTROL Cache Management]**, puis cliquez sur **[!UICONTROL Flush Cache]** pour actualiser tous les caches non valides.

### Options de configuration

| Champ | Portée | Description |
|---|---|---|
| [!UICONTROL Enable] | site web | Activer ou désactiver [!DNL Payment Services] pour votre site web. Options : [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Method] | vue de magasin | Définissez la méthode, ou l’environnement, de votre magasin. Options : [!UICONTROL Sandbox] / [!UICONTROL Production] |
| [!UICONTROL Sandbox Merchant ID] | vue de magasin | Votre ID de marchand d’environnement de test, qui est généré automatiquement lors de l’intégration des environnements de test. Ne modifiez pas ou ne modifiez pas cet identifiant. |
| [!UICONTROL Production Merchant ID] | vue de magasin | Votre identifiant commercial de production, qui est généré automatiquement lors de l’intégration des environnements de test. Ne modifiez pas ou ne modifiez pas cet identifiant. |

## [!UICONTROL Credit Card Fields]

La variable [!UICONTROL Credit Card Fields] les options de paiement offrent un passage en caisse simple et sécurisé pour les modes de paiement par carte de crédit ou carte de débit.

Voir [Options de paiement](payments-options.md#paypal-smart-buttons) pour plus d’informations.

### Configuration des champs de carte de crédit

1. Sur le _Administration_ barre latérale, accédez à **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Dans le panneau de gauche, développez **[!UICONTROL Sales]** et choisissez **[!UICONTROL Payment Methods]**.
1. Développez l’objet _[!UICONTROL Recommended Solutions]_.
1. Dans le _[!UICONTROL Payment Services]_, développez la section_[!UICONTROL Credit Card Fields]_ .
1. Pour **[!UICONTROL Title]**, saisissez du texte (si nécessaire) pour modifier le nom du mode de paiement, comme indiqué lors du passage en caisse.
1. À [définir l’action de paiement ;](production.md#set-payment-services-as-payment-method), sélectionnez **[!UICONTROL Authorize]** ou **Autoriser et capturer**.
1. Pour **[!UICONTROL Show on checkout page]**, choisissez `Yes` pour activer les champs de carte de crédit sur la page de passage en caisse.
1. Pour **[!UICONTROL Vault Enabled]**, choisissez `Yes` pour activer la mise en valeur par carte de crédit pour le passage en caisse.
1. Pour **[!UICONTROL Vault Enabled in Admin]**, choisissez `Yes` pour permettre au marchand de créer des commandes pour les clients utilisant leur carte de crédit voûtée.
1. Pour **[!UICONTROL Debug Mode]**, choisissez `Yes` pour activer le mode de débogage (ou `No` pour la désactiver).
1. Pour activer **[!UICONTROL 3DS Secure authentication]** (`Off` par défaut) choisissez `Always` ou `When required`.
1. Cliquez sur **[!UICONTROL Save Config]** pour enregistrer vos modifications.
1. Accédez à **[!UICONTROL System]** > **[!UICONTROL Cache Management]**, puis cliquez sur **[!UICONTROL Flush Cache]** pour actualiser tous les caches non valides.

#### Options de configuration

| Champ | Portée | Description |
|---|---|---|
| [!UICONTROL Title] | vue de magasin | Ajoutez le texte à afficher comme titre de cette option de paiement dans la vue Mode de paiement lors de l’extraction. Options : [!UICONTROL text field] |
| [!UICONTROL Payment Action] | site web | La variable [action de paiement](https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html) pour le mode de paiement spécifié. Options : [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Show on checkout page] | site web | Activez ou désactivez les champs de carte de crédit sur la page de passage en caisse. Options : [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Vault enabled] | vue de magasin | Activer ou désactiver [coffre-fort à carte de crédit](vaulting.md). Options : [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Vault enabled in Admin] | vue de magasin | Activation ou désactivation de la fonctionnalité [le marchand pour terminer les commandes des clients dans l’administrateur](vaulting.md) utilisation d’un mode de paiement par défaut. Options : [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL 3DS Secure authentication] | site web | Activer ou désactiver [Authentification sécurisée 3DS](security.md#3ds). Options : [!UICONTROL Always] / [!UICONTROL When Required] / [!UICONTROL Off] |
| [!UICONTROL Debug Mode] | site web | Activez ou désactivez le mode de débogage. Options : [!UICONTROL Yes] / [!UICONTROL No] |

## [!DNL PayPal Smart Buttons]

La variable [!DNL PayPal Smart Buttons] les options de paiement offrent un processus de paiement simple, rapide et sécurisé pour votre client.

Voir [Options de paiement](payments-options.md#paypal-smart-buttons) pour plus d’informations.

### Configurer [!DNL PayPal Smart Buttons]

Vous pouvez activer et configurer les options de paiement des boutons intelligents PayPal au sein de l’administrateur :

1. Sur le _Administration_ barre latérale, accédez à **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Dans le panneau de gauche, développez **[!UICONTROL Sales]** et choisissez **[!UICONTROL Payment Methods]**.
1. Développez l’objet _[!UICONTROL Recommended Solutions]_.
1. Dans le _[!UICONTROL Payment Services]_, développez la section_[!UICONTROL PayPal Smart Buttons]_ .
1. Pour modifier le nom du mode de paiement, comme indiqué lors de l’extraction, modifiez la variable _[!UICONTROL Title]_champ .
1. À [définir l’action de paiement ;](production.md#set-payment-services-as-payment-method), sélectionnez **[!UICONTROL Authorize]** ou **[!UICONTROL Authorize and Capture]**.
1. Pour activer/désactiver la fonction [Payer les messages plus tard](payments-options.md#pay-later-button), sélectionnez `Yes`/`No` pour **[!UICONTROL Display Pay Later Message]**.
1. Pour afficher les boutons intelligents PayPal sur la page de passage en caisse, sélectionnez `Yes` pour le **[!UICONTROL Show buttons on checkout page]**.
1. Pour afficher les boutons intelligents PayPal dans l’aperçu du mini panier, sélectionnez `Yes` pour **[!UICONTROL Show buttons in mini cart preview]**.
1. Pour activer l’option de paiement Venmo, sélectionnez `Yes` pour **[!UICONTROL Venmo Enabled]**.
1. Pour activer l’option Paiement Apple en tant que paiement, sélectionnez `Yes` pour **[!UICONTROL Apple Pay Enabled]**.
1. Pour activer les cartes de crédit et de débit PayPal comme option de paiement (bouton PayPal Smart), sélectionnez `Yes` pour **[!UICONTROL PayPal Credit and Debit Card Enabled]**.
1. Pour activer/désactiver la fonction [PayPal - Payer plus tard](payments-options.md#pay-later-button) option de paiement, sélectionnez `Yes`/`No` pour **[!UICONTROL PayPal Pay Later Enabled]**.
1. Pour activer le mode de débogage, sélectionnez `Yes` pour le **[!UICONTROL Debug Mode]** (`No` la désactive).
1. Pour enregistrer vos modifications, cliquez sur **[!UICONTROL Save Config]** .
1. Accédez à **[!UICONTROL System]** > **[!UICONTROL Cache Management]**, puis cliquez sur **[!UICONTROL Flush Cache]** pour actualiser tous les caches non valides.

### Options de configuration

| Champ | Portée | Description |
|---|---|---|
| [!UICONTROL Title] | vue de magasin | Ajoutez le texte à afficher comme titre pour cette option de paiement dans la vue Mode de paiement lors de l’extraction. Options : champ de texte |
| [!UICONTROL Payment Action] | site web | La variable [action de paiement](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target="_blank"} pour le mode de paiement spécifié. Options : [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Display Pay Later Message] | site web | Activez ou désactivez la messagerie Payer plus tard dans le panier, la page du produit, le mini-panier et pendant le flux de passage en caisse. Options : [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show buttons on checkout page] | vue de magasin | Activer ou désactiver [!DNL PayPal Smart Buttons] sur la page de passage en caisse. Options : [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show buttons on product detail page] | vue de magasin | Activer ou désactiver [!DNL PayPal Smart Buttons] sur la page des détails du produit. Options : [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show buttons in mini-cart preview] | vue de magasin | Activer ou désactiver [!DNL PayPal Smart Buttons] dans l’aperçu du mini-panier. Options : [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Venmo Enabled] | vue de magasin | Activez ou désactivez l’option de paiement Venmo lorsque les boutons de paiement s’affichent. Options : [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Apple Pay Enabled] | vue de magasin | Activez ou désactivez l’option Paiement Apple dans laquelle les boutons de paiement s’affichent. Options : [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL PayPal Credit and Debit Card Enabled] | vue de magasin | Activez ou désactivez les options de carte de crédit et de débit PayPal où les boutons de paiement s’affichent. Options : [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL PayPal Pay Later Enabled] | vue de magasin | Activez ou désactivez l’aspect de l’option Payer plus tard lorsque des boutons de paiement s’affichent. Options : [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Debug Mode] | site web | Activez ou désactivez le mode de débogage. Options : [!UICONTROL Yes] / [!UICONTROL No] |

### [!DNL PayPal Smart Buttons] Options de style

| Champ | Portée | Description |
|--- |--- |--- |
| [!UICONTROL Layout] | Affichage en magasin | Définissez le style de mise en page des boutons Paypal Smart. Options : [!UICONTROL Vertical] / [!UICONTROL Horizontal] |
| [!UICONTROL Color] | Affichage en magasin | Définissez la couleur des boutons Paypal Smart. Options : [!UICONTROL Blue] / [!UICONTROL Gold] / [!UICONTROL Silver] / [!UICONTROL White] / [!UICONTROL Black] |
| [!UICONTROL Shape] | Affichage en magasin | Définissez la forme des boutons intelligents de Paypal. Options : [!UICONTROL Rectangular] / [!UICONTROL Pill] |
| [!UICONTROL Use Default Height] | Affichage en magasin | Définit si les boutons intelligents PayPal utilisent une hauteur par défaut. Options : [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Height] | Affichage en magasin | Définissez la hauteur des boutons intelligents PayPal. Valeur par défaut : aucune |
| [!UICONTROL Label] | Affichage en magasin | Définissez le libellé qui apparaît dans les boutons intelligents PayPal. Options : [!UICONTROL PayPal] / [!UICONTROL Checkout] / [!UICONTROL Buynow] / [!UICONTROL Pay] / [!UICONTROL Installment] |
| [!UICONTROL Tagline] | Affichage en magasin | Active le tag. Options : [!UICONTROL Yes] / [!UICONTROL No] |

## Vider le cache

Si vous modifiez la configuration, [vider manuellement le cache ;](/help/payment-services/settings.md#flush-the-cache) afin que votre boutique affiche les derniers paramètres de configuration.
