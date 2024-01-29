---
title: Configuration des services de paiement hérités
description: Après l’installation, vous pouvez configurer [!DNL Payment Services] dans la configuration du magasin.
role: Admin, User
level: Intermediate
exl-id: e1a3269d-bdf9-4b0f-972f-e8a0ef469503
feature: Payments, Checkout, Configuration
source-git-commit: 8dd4f629fa60959588cee4ea22f9fb577f338716
workflow-type: tm+mt
source-wordcount: '1402'
ht-degree: 0%

---

# Hérité [!DNL Payment Services] Configuration

Vous pouvez personnaliser [!DNL Payment Services] à vos besoins avec des options de configuration utiles dans l’Admin.

Lorsque vous configurez [!DNL Payment Services] pour [!DNL Adobe Commerce] et [!DNL Magento Open Source] dans l’Admin, ces configurations s’appliquent uniquement à l’environnement défini dans la variable _[!UICONTROL Method]_champ de_[!UICONTROL General Configuration]_. Les modifications que vous apportez dans les champs de configuration ne sont pas liées au changement de _[!UICONTROL Method]_selection : si vous changez de méthode, vos sélections ne sont pas réinitialisées.

## Configuration générale

Vous pouvez activer [!DNL Payment Services] pour votre magasin et activez le test sandbox ou les paiements en direct dans la variable _[!UICONTROL General Configuration]_.

1. Sur le _Administration_ barre latérale, accédez à **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Dans le panneau de gauche, développez **[!UICONTROL Sales]** et choisissez **[!UICONTROL Payment Methods]**.

   ![Affichage des méthodes](assets/methods-view.png){width="400" zoomable="yes"}

1. Développez l’objet _[!UICONTROL Recommended Solutions]_.
1. Dans le _[!UICONTROL [!DNL Payment Services]]_, développez la section_[!UICONTROL General Configuration]_ .
1. Pour **Activer**, définissez-le sur `Yes` pour activer [!DNL Payment Services] pour votre magasin.
1. Pour **Méthode**, définissez-le sur `Sandbox` si vous effectuez toujours des tests [!DNL Payment Services] pour votre boutique ou `Production` si vous êtes prêt à activer les paiements en direct.

   >[!WARNING]
   >
   >Votre _[!UICONTROL Sandbox Merchant ID]_et_[!UICONTROL Production Merchant ID]_ sont générés automatiquement et présents dans leurs champs respectables lorsque vous avez terminé l’intégration à l’environnement de test et/ou à la production. Ne supprimez ou ne modifiez pas ces identifiants.

1. Pour **Descripteur de Soft** (valeurs personnalisées qui s’affichent sur les relevés de banque de transactions client pour délimiter les magasins/marques/catalogues), ajoutez votre texte personnalisé (jusqu’à 22 caractères) dans le champ de texte, en remplaçant `Custom descriptor` ou la valeur existante.
1. Cliquez sur **[!UICONTROL Save Config]** pour enregistrer vos modifications.
1. Accédez à **[!UICONTROL System]** > **[!UICONTROL Cache Management]**, puis cliquez sur **[!UICONTROL Flush Cache]** pour actualiser tous les caches non valides.

### Options de configuration

| Champ | Portée | Description |
|---|---|---|
| [!UICONTROL Enable] | site web | Activer ou désactiver [!DNL Payment Services] pour votre site web. Options : `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Method] | vue de magasin | Définissez la méthode, ou l’environnement, de votre magasin. Options : [!UICONTROL Sandbox] / [!UICONTROL Production] |
| [!UICONTROL Sandbox Merchant ID] | vue de magasin | Votre ID de marchand d’environnement de test, qui est généré automatiquement lors de l’intégration des environnements de test. Ne modifiez pas ou ne modifiez pas cet identifiant. |
| [!UICONTROL Production Merchant ID] | vue de magasin | Votre identifiant commercial de production, qui est généré automatiquement lors de l’intégration des environnements de test. Ne modifiez pas ou ne modifiez pas cet identifiant. |
| [!UICONTROL Soft Descriptor] | site web ou vue de magasin | Ajoutez un descripteur logiciel à votre ou vos sites web et vues de magasin pour ajouter des informations aux transactions client qui délimitent les marques, les magasins ou les lignes de produits. |

## [!UICONTROL Credit Card Fields]

La variable [!UICONTROL Credit Card Fields] les options de paiement offrent un passage en caisse simple et sécurisé pour les modes de paiement par carte de crédit ou carte de débit.

Voir [Options de paiement](payments-options.md#paypal-smart-buttons) pour plus d’informations.

1. Sur le _Administration_ barre latérale, accédez à **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Dans le panneau de gauche, développez **[!UICONTROL Sales]** et choisissez **[!UICONTROL Payment Methods]**.
1. Développez l’objet _[!UICONTROL Recommended Solutions]_.
1. Dans le _[!UICONTROL Payment Services]_, développez la section_[!UICONTROL Credit Card Fields]_ .
1. Pour **[!UICONTROL Title]**, saisissez du texte (si nécessaire) pour modifier le nom du mode de paiement, comme indiqué lors du passage en caisse.
1. À [définir l’action de paiement ;](production.md#set-payment-services-as-payment-method), sélectionnez **[!UICONTROL Authorize]** ou **Autoriser et capturer**.
1. Pour donner la priorité à un mode de paiement sur la page de passage en caisse, fournissez un `Numeric Only` dans la variable **[!UICONTROL Sort order]** champ .
1. Pour **[!UICONTROL Show on checkout page]**, choisissez `Yes` pour activer les champs de carte de crédit sur la page de passage en caisse.
1. Pour **[!UICONTROL Vault Enabled]**, choisissez `Yes` pour activer la mise en valeur par carte de crédit pour le passage en caisse.
1. Pour **[!UICONTROL Vault Enabled in Admin]**, choisissez `Yes` pour permettre au marchand de créer des commandes pour les clients utilisant leur carte de crédit voûtée.
1. Pour activer **[!UICONTROL 3DS Secure authentication]** (`Off` par défaut) choisissez `Always` ou `When required`.
1. Pour **[!UICONTROL Debug Mode]**, choisissez `Yes` pour activer le mode de débogage, ou `No` pour la désactiver.
1. Cliquez sur **[!UICONTROL Save Config]** pour enregistrer vos modifications.
1. Accédez à **[!UICONTROL System]** > **[!UICONTROL Cache Management]**, puis cliquez sur **[!UICONTROL Flush Cache]** pour actualiser tous les caches non valides.

### Options de configuration

| Champ | Portée | Description |
|---|---|---|
| [!UICONTROL Title] | vue de magasin | Ajoutez le texte à afficher comme titre de cette option de paiement dans la vue Mode de paiement lors de l’extraction. Options : [!UICONTROL text field] |
| [!UICONTROL Payment Action] | site web | La variable [action de paiement](https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html) pour le mode de paiement spécifié. Options : [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Sort order] | vue de magasin | Ordre de tri du mode de paiement spécifié sur la page de passage en caisse. `Numeric Only` value |
| [!UICONTROL Show on checkout page] | site web | Activez ou désactivez les champs de carte de crédit sur la page de passage en caisse. Options : [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Vault enabled] | vue de magasin | Activer ou désactiver [coffre-fort à carte de crédit](vaulting.md). Options : [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Vault enabled in Admin] | vue de magasin | Activation ou désactivation de la fonctionnalité [le marchand pour terminer les commandes des clients dans l’administrateur](vaulting.md) utilisation d’un mode de paiement par défaut. Options : [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL 3DS Secure authentication] | site web | Activer ou désactiver [Authentification sécurisée 3DS](security.md#3ds). Options : [!UICONTROL Always] / [!UICONTROL When Required] / [!UICONTROL Off] |
| [!UICONTROL Debug Mode] | site web | Activez ou désactivez le mode de débogage. Options : `[!UICONTROL Yes]` / `[!UICONTROL No]` |

## [!UICONTROL Apple Pay]

La variable [!UICONTROL Apple Pay] l’option de paiement permet au marchand d’offrir Apple Pay à ses acheteurs, qui peuvent utiliser un identifiant tactile sur leurs appareils pour effectuer des achats depuis le navigateur Safari. Les commerçants peuvent ajouter jusqu’à 99 domaines par compte marchand.

Voir [Options de paiement](payments-options.md#apple-pay-button) pour plus d’informations.

1. Sur le _Administration_ barre latérale, accédez à **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Dans le panneau de gauche, développez **[!UICONTROL Sales]** et choisissez **[!UICONTROL Payment Methods]**.
1. Développez l’objet _[!UICONTROL Recommended Solutions]_.
1. Dans le _[!UICONTROL Payment Services]_, développez la section_[!UICONTROL Apple Pay]_ .
1. Pour **[!UICONTROL Title]**, saisissez du texte (si nécessaire) pour modifier le nom du mode de paiement, comme indiqué lors du passage en caisse.
1. À [définir l’action de paiement ;](production.md#set-payment-services-as-payment-method), sélectionnez **[!UICONTROL Authorize]** ou **[!UICONTROL Authorize and Capture]**.
1. Pour afficher [!DNL Apple Pay] sur la page passage en caisse, sélectionnez `Yes` pour le **[!UICONTROL Show buttons on checkout page]**.
1. Pour afficher [!DNL Apple Pay] sur la page des détails du produit, sélectionnez `Yes` pour le **[!UICONTROL Show buttons on product detail page]**.
1. Pour afficher [!DNL Apple Pay] dans l’aperçu du mini panier, sélectionnez `Yes` pour **[!UICONTROL Show buttons in mini cart preview]**.
1. Pour afficher [!DNL Apple Pay] sur la page panier, sélectionnez `Yes` pour le **[!UICONTROL Show buttons on cart page]**.
1. Pour activer le mode de débogage, sélectionnez `Yes` pour le **[!UICONTROL Debug Mode]** (`No` la désactive).
1. Pour enregistrer vos modifications, cliquez sur **[!UICONTROL Save Config]** .
1. Accédez à **[!UICONTROL System]** > **[!UICONTROL Cache Management]**, puis cliquez sur **[!UICONTROL Flush Cache]** pour actualiser tous les caches non valides.

### Options de configuration

| Champ | Portée | Description |
|---|---|---|
| [!UICONTROL Title] | vue de magasin | Ajoutez le texte à afficher comme titre de cette option de paiement dans la vue Mode de paiement lors de l’extraction. Options : [!UICONTROL text field] |
| [!UICONTROL Payment Action] | site web | La variable [action de paiement](https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html) pour le mode de paiement spécifié. Options : [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Show on checkout page] | site web | Activer ou désactiver [!DNL Apple Pay] sur la page de passage en caisse. Options : `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons on product detail page] | vue de magasin | Activer ou désactiver [!DNL Apple Pay] sur la page des détails du produit. Options : `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons in mini-cart preview] | vue de magasin | Activer ou désactiver [!DNL Apple Pay] dans l’aperçu du mini-panier. Options : `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons on cart page] | vue de magasin | Activer ou désactiver [!DNL Apple Pay] dans la page du panier. Options : `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Debug Mode] | site web | Activez ou désactivez le mode de débogage. Options : `[!UICONTROL Yes]` / `[!UICONTROL No]` |

## [!DNL PayPal Payment Buttons]

La variable [!DNL PayPal payment buttons] les options de paiement offrent un processus de paiement simple, rapide et sécurisé pour votre client.

Voir [Options de paiement](payments-options.md#paypal-smart-buttons) pour plus d’informations.

Configurer [!DNL PayPal payment buttons]

Vous pouvez activer et configurer les options de paiement des boutons de paiement PayPal au sein de l’administrateur :

1. Sur le _Administration_ barre latérale, accédez à **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Dans le panneau de gauche, développez **[!UICONTROL Sales]** et choisissez **[!UICONTROL Payment Methods]**.
1. Développez l’objet _[!UICONTROL Recommended Solutions]_.
1. Dans le _[!UICONTROL Payment Services]_, développez la section_[!UICONTROL PayPal payment buttons]_ .
1. Pour modifier le nom du mode de paiement, comme indiqué lors de l’extraction, modifiez la variable _[!UICONTROL Title]_champ .
1. À [définir l’action de paiement ;](production.md#set-payment-services-as-payment-method), sélectionnez **[!UICONTROL Authorize]** ou **[!UICONTROL Authorize and Capture]**.
1. Pour donner la priorité à un mode de paiement sur la page de passage en caisse, fournissez un `Numeric Only` dans la variable **[!UICONTROL Sort order]** champ .
1. Pour activer/désactiver la fonction [Payer les messages plus tard](payments-options.md#pay-later-button), sélectionnez `Yes`/`No` pour **[!UICONTROL Display Pay Later Message]**.
1. Pour afficher les boutons de paiement PayPal sur la page de passage en caisse, sélectionnez `Yes` pour le **[!UICONTROL Show buttons on checkout page]**.
1. Pour afficher les boutons de paiement PayPal sur la page des détails du produit, sélectionnez `Yes` pour le **[!UICONTROL Show buttons on product detail page]**.
1. Pour afficher les boutons de paiement PayPal dans l’aperçu du mini panier, sélectionnez `Yes` pour **[!UICONTROL Show buttons in mini cart preview]**.
1. Pour afficher les boutons de paiement PayPal sur la page du panier, sélectionnez `Yes` pour le **[!UICONTROL Show buttons on cart page]**.
1. Pour activer l’option de paiement Venmo, sélectionnez `Yes` pour **[!UICONTROL Venmo Enabled]**.
1. Pour activer les cartes de crédit et de débit comme option de paiement (bouton PayPal Smart), sélectionnez `Yes` pour **[!UICONTROL Credit and Debit Card Enabled]**.
1. Pour activer/désactiver la fonction [PayPal - Payer plus tard](payments-options.md#pay-later-button) option de paiement, sélectionnez `Yes`/`No` pour **[!UICONTROL PayPal Pay Later Enabled]**.
1. Pour activer le mode de débogage, sélectionnez `Yes` pour le **[!UICONTROL Debug Mode]** (`No` la désactive).
1. Pour enregistrer vos modifications, cliquez sur **[!UICONTROL Save Config]** .
1. Accédez à **[!UICONTROL System]** > **[!UICONTROL Cache Management]**, puis cliquez sur **[!UICONTROL Flush Cache]** pour actualiser tous les caches non valides.

### Options de configuration

| Champ | Portée | Description |
|---|---|---|
| [!UICONTROL Title] | vue de magasin | Ajoutez le texte à afficher comme titre pour cette option de paiement dans la vue Mode de paiement lors de l’extraction. Options : champ de texte |
| [!UICONTROL Payment Action] | site web | La variable [action de paiement](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target="_blank"} pour le mode de paiement spécifié. Options : [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Display Pay Later Message] | site web | Activez ou désactivez la messagerie Payer plus tard dans le panier, la page du produit, le mini-panier et pendant le flux de passage en caisse. Options : `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons on checkout page] | vue de magasin | Activer ou désactiver [!DNL PayPal payment buttons] sur la page de passage en caisse. Options : `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons on product detail page] | vue de magasin | Activer ou désactiver [!DNL PayPal payment buttons] sur la page des détails du produit. Options : `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons in mini-cart preview] | vue de magasin | Activer ou désactiver [!DNL PayPal payment buttons] dans l’aperçu du mini-panier. Options : `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons on cart page] | vue de magasin | Activer ou désactiver [!DNL PayPal payment buttons] dans la page du panier. Options : `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Venmo Enabled] | vue de magasin | Activez ou désactivez l’option de paiement Venmo lorsque les boutons de paiement s’affichent. Options : `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Credit and Debit Card Enabled] | vue de magasin | Activez ou désactivez les options de carte Crédit et Débit lorsque des boutons de paiement s’affichent. Options : `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL PayPal Pay Later Enabled] | vue de magasin | Activez ou désactivez l’aspect de l’option Payer plus tard lorsque des boutons de paiement s’affichent. Options : `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Debug Mode] | site web | Activez ou désactivez le mode de débogage. Options : `[!UICONTROL Yes]` / `[!UICONTROL No]` |

## Style de bouton

Vous pouvez également configurer la variable _[!UICONTROL Button style]_options des boutons de paiement :

1. Sur le _Administration_ barre latérale, accédez à **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Dans le panneau de gauche, développez **[!UICONTROL Sales]** et choisissez **[!UICONTROL Payment Methods]**.
1. Développez l’objet _[!UICONTROL Recommended Solutions]_.
1. Dans le _[!UICONTROL [!DNL Payment Services]]_, développez la section_[!UICONTROL PayPal Smart Button Styling]_ .
1. Pour définir la mise en page, sélectionnez `Vertical` ou `Horizontal` pour **[!UICONTROL Layout]**
1. Pour définir la couleur, sélectionnez l’une des couleurs disponibles dans **[!UICONTROL Color]**.
1. Pour définir la forme, sélectionnez `Rectangular` ou `Pill` pour **[!UICONTROL Shape]**.
1. Pour utiliser la hauteur par défaut, sélectionnez `Yes` ou `No` pour **[!UICONTROL Use Default Height]**.
1. Pour définir la hauteur personnalisée, ajoutez la hauteur de pixel souhaitée pour **[!UICONTROL Height]**.
1. Pour définir le tag, sélectionnez `Yes` ou `No` pour **[!UICONTROL Tagline]**.
1. Pour enregistrer vos modifications, cliquez sur **[!UICONTROL Save Config]** .
1. Accédez à **[!UICONTROL System]** > **[!UICONTROL Cache Management]**, puis cliquez sur **[!UICONTROL Flush Cache]** pour actualiser tous les caches non valides.

Vous pouvez également configurer le style des boutons de paiement [dans les paramètres](settings.md#button-style) de la page d’accueil des services de paiement.

### Options de configuration

| Champ | Portée | Description |
|--- |--- |--- |
| [!UICONTROL Layout] | Affichage en magasin | Définissez le style de mise en page des boutons de paiement Paypal. Options : `[!UICONTROL Vertical]` / `[!UICONTROL Horizontal]` |
| [!UICONTROL Color] | Affichage en magasin | Définissez la couleur des boutons de paiement Paypal. Options : [!UICONTROL Blue] / `[!UICONTROL Gold]` / `[!UICONTROL Silver]` / `[!UICONTROL White]` / `[!UICONTROL Black]` |
| [!UICONTROL Shape] | Affichage en magasin | Définissez la forme des boutons de paiement Paypal. Options : `[!UICONTROL Rectangular]` / `[!UICONTROL Pill]` |
| [!UICONTROL Use Default Height] | Affichage en magasin | Définit si les boutons de paiement PayPal utilisent une hauteur par défaut. Options : `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Height] | Affichage en magasin | Définissez la hauteur des boutons de paiement PayPal. Valeur par défaut : aucune |
| [!UICONTROL Label] | Affichage en magasin | Définissez le libellé qui apparaît dans les boutons de paiement de PayPal. Options : `[!UICONTROL PayPal]` / `[!UICONTROL Checkout]` / `[!UICONTROL Buynow]` / `[!UICONTROL Pay]` / `[!UICONTROL Installment]` |
| [!UICONTROL Tagline] | Affichage en magasin | Active le tag. Options : `[!UICONTROL Yes]` / `[!UICONTROL No]` |

## Vider le cache

Si vous modifiez la configuration, [vider manuellement le cache ;](/help/payment-services/settings.md#flush-the-cache) afin que votre boutique affiche les derniers paramètres de configuration.
