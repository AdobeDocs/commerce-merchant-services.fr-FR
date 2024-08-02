---
title: Configuration des services de paiement hérités
description: Après l’installation, vous pouvez configurer  [!DNL Payment Services] dans l’Admin à la configuration du magasin.
role: Admin, User
level: Intermediate
exl-id: e1a3269d-bdf9-4b0f-972f-e8a0ef469503
feature: Payments, Checkout, Configuration
source-git-commit: 7a886679ad00f9b29e6ffd7d8bc8e2f6fc0082d4
workflow-type: tm+mt
source-wordcount: '1702'
ht-degree: 0%

---

# Configuration héritée de [!DNL Payment Services]

Vous pouvez personnaliser [!DNL Payment Services] en fonction de vos besoins grâce à des options de configuration utiles dans l’Admin.

Lorsque vous configurez [!DNL Payment Services] pour [!DNL Adobe Commerce] et [!DNL Magento Open Source] dans l’Admin, ces configurations s’appliquent uniquement à l’environnement défini dans le champ _[!UICONTROL Method]_de_[!UICONTROL General Configuration]_. Toutes les modifications que vous apportez dans les champs de configuration sont indépendantes du changement de la sélection _[!UICONTROL Method]_. Si vous changez de méthode, vos sélections ne sont pas réinitialisées.

## Configuration générale

Vous pouvez activer [!DNL Payment Services] pour votre magasin et votre _[!UICONTROL Merchant Location]_, et activer le test sandbox ou les paiements en direct dans la section_[!UICONTROL General Configuration]_ .

1. Sur la barre latérale _Admin_, accédez à **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Dans le panneau de gauche, développez **[!UICONTROL Sales]** et choisissez **[!UICONTROL Payment Methods]**.
1. Définissez le champ _[!UICONTROL Merchant Country]_dans le_[!UICONTROL Merchant Location]_. Si un _[!UICONTROL Merchant Country]_n&#39;est pas spécifié, le_[!UICONTROL Default Country]_ de la configuration générale est utilisé.
1. Développez la section _[!UICONTROL FEATURED ADOBE PAYMENT SOLUTION]_pour accéder à la section_[!UICONTROL [!DNL Payment Services]]_.
1. Dans la section _[!UICONTROL [!DNL Payment Services]]_, développez la section_[!UICONTROL General Configuration]_ .
1. Pour **Activer**, définissez-le sur `Yes` pour activer [!DNL Payment Services] pour votre magasin.
1. Pour la **Méthode**, définissez-la sur `Sandbox` si vous testez toujours [!DNL Payment Services] pour votre magasin ou `Production` si vous êtes prêt à activer les paiements en direct.
1. Vos valeurs **[!UICONTROL Payment Services Sandbox ID]** et **[!UICONTROL Payment Services Production ID]** sont automatiquement renseignées une fois que vous avez configuré le [Connecteur Commerce Services](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/user-guides/integration-services/saas){target=_blank} et que vous avez consulté le tableau de bord [!DNL Payment Services] pour la première fois. Procédez comme suit pour terminer l’intégration de votre environnement de test et/ou de vos environnements de production. Ces valeurs associent votre ID SaaS à [!DNL Payment Services].

   >[!WARNING]
   >
   > Si vous devez modifier votre identifiant de zone de données dans Commerce Services Connector, vous devez réinitialiser votre identifiant [!DNL Payment Services]. Cliquez sur **Réinitialiser l’ID des services de paiement** pour réinitialiser votre sandbox ou vos ID de production. Si vous réinitialisez vos [!DNL Payment Services] ID, vous devez à nouveau les intégrer.

1. Pour **Descripteur de Soft** (valeurs personnalisées qui s’affichent sur les relevés de banque de transactions client pour délimiter les magasins/marques/catalogues), ajoutez votre texte personnalisé (jusqu’à 22 caractères) dans le champ de texte, en remplaçant `Soft descriptor` ou la valeur existante.
1. Cliquez sur **[!UICONTROL Save Config]** pour enregistrer vos modifications.
1. Accédez à **[!UICONTROL System]** > **[!UICONTROL Cache Management]**, puis cliquez sur **[!UICONTROL Flush Cache]** pour actualiser tous les caches non valides.

![Vue de la solution Adobe en vedette](assets/featured-adobe-solution-view.png){width="700" zoomable="yes"}

### Options de configuration

| Champ | Portée | Description |
|---|---|---|
| [!UICONTROL Enable] | site web | Activez ou désactivez [!DNL Payment Services] pour votre site web. Options : `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Method] | vue de magasin | Définissez la méthode, ou l’environnement, de votre magasin. Options : [!UICONTROL Sandbox] / [!UICONTROL Production] |
| [!UICONTROL Payment Services Sandbox ID] | vue de magasin | Votre ID de marchand d’environnement de test, qui est généré automatiquement lors de l’intégration des environnements de test. |
| [!UICONTROL Payment Services Production ID] | vue de magasin | Votre identifiant commercial de production, qui est généré automatiquement lors de l’intégration des environnements de test. |
| [!UICONTROL Soft Descriptor] | site web ou vue de magasin | Ajoutez un descripteur logiciel à votre ou vos sites web et vues de magasin pour ajouter des informations aux transactions client qui délimitent les marques, les magasins ou les lignes de produits. |

## [!UICONTROL Credit Card Fields]

Les options de paiement [!UICONTROL Credit Card Fields] offrent un passage en caisse simple et sécurisé pour les modes de paiement par carte de crédit ou carte de débit.

Voir [Options de paiement](payments-options.md#paypal-smart-buttons) pour plus d’informations.

1. Sur la barre latérale _Admin_, accédez à **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Dans le panneau de gauche, développez **[!UICONTROL Sales]** et choisissez **[!UICONTROL Payment Methods]**.
1. Développez la section _[!UICONTROL FEATURED ADOBE PAYMENT SOLUTION]_.
1. Dans la section _[!UICONTROL Payment Services]_, développez la section_[!UICONTROL Credit Card Fields]_ .
1. Pour **[!UICONTROL Title]**, saisissez du texte (si nécessaire) pour modifier le nom du mode de paiement, comme indiqué lors du passage en caisse.
1. Pour [définir l’action de paiement](production.md#set-payment-services-as-payment-method), sélectionnez **[!UICONTROL Authorize]** ou **Autoriser et capturer**.
1. Pour donner la priorité à un mode de paiement sur la page de passage en caisse, indiquez une valeur `Numeric Only` dans le champ **[!UICONTROL Sort order]**.
1. Pour **[!UICONTROL Show on checkout page]**, choisissez `Yes` pour activer les champs de carte de crédit sur la page de passage en caisse.
1. Pour **[!UICONTROL Vault Enabled]**, choisissez `Yes` pour activer la mise en valeur de carte de crédit pour le passage en caisse.
1. Pour **[!UICONTROL Vault Enabled in Admin]**, choisissez `Yes` pour permettre au marchand de créer des commandes pour les clients utilisant leur carte de crédit voûtée.
1. Pour activer **[!UICONTROL 3DS Secure authentication]** (`Off` par défaut), choisissez `Always` ou `When required`.
1. Pour **[!UICONTROL Debug Mode]**, choisissez `Yes` pour activer le mode de débogage ou `No` pour le désactiver.
1. Cliquez sur **[!UICONTROL Save Config]** pour enregistrer vos modifications.
1. Accédez à **[!UICONTROL System]** > **[!UICONTROL Cache Management]**, puis cliquez sur **[!UICONTROL Flush Cache]** pour actualiser tous les caches non valides.

### Options de configuration

| Champ | Portée | Description |
|---|---|---|
| [!UICONTROL Title] | vue de magasin | Ajoutez le texte à afficher comme titre de cette option de paiement dans la vue Mode de paiement lors de l’extraction. Options : [!UICONTROL text field] |
| [!UICONTROL Payment Action] | site web | [action de paiement](https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html) pour le mode de paiement spécifié. Options : [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Sort order] | vue de magasin | Ordre de tri du mode de paiement spécifié sur la page de passage en caisse. `Numeric Only` value |
| [!UICONTROL Show on checkout page] | site web | Activez ou désactivez les champs de carte de crédit sur la page de passage en caisse. Options : [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Vault enabled] | vue de magasin | Activez ou désactivez la [valeur de carte de crédit](vaulting.md). Options : [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Vault enabled in Admin] | vue de magasin | Activez ou désactivez la possibilité pour le [commerçant d’exécuter des commandes pour les clients dans l’Admin](vaulting.md) à l’aide d’un mode de paiement Vault. Options : [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL 3DS Secure authentication] | site web | Activez ou désactivez l’ [authentification sécurisée 3DS](security.md#3ds). Options : [!UICONTROL Always] / [!UICONTROL When Required] / [!UICONTROL Off] |
| [!UICONTROL Debug Mode] | site web | Activez ou désactivez le mode de débogage. Options : `[!UICONTROL Yes]` / `[!UICONTROL No]` |

## [!UICONTROL Apple Pay]

L’option de paiement [!UICONTROL Apple Pay] permet au marchand d’offrir Apple Pay à ses acheteurs, qui peuvent utiliser un identifiant tactile sur leurs appareils pour effectuer des achats depuis le navigateur Safari. Les commerçants peuvent ajouter jusqu’à 99 domaines par compte marchand.

Voir [Options de paiement](payments-options.md#apple-pay-button) pour plus d’informations.

1. Sur la barre latérale _Admin_, accédez à **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Dans le panneau de gauche, développez **[!UICONTROL Sales]** et choisissez **[!UICONTROL Payment Methods]**.
1. Développez la section _[!UICONTROL FEATURED ADOBE PAYMENT SOLUTION]_.
1. Dans la section _[!UICONTROL Payment Services]_, développez la section_[!UICONTROL Apple Pay]_ .
1. Pour **[!UICONTROL Title]**, saisissez du texte (si nécessaire) pour modifier le nom du mode de paiement, comme indiqué lors du passage en caisse.
1. Pour [définir l&#39;action de paiement](production.md#set-payment-services-as-payment-method), sélectionnez **[!UICONTROL Authorize]** ou **[!UICONTROL Authorize and Capture]**.
1. Spécifiez où l’option [!DNL Apple Pay] est activée dans Adobe Commerce en sélectionnant `Yes` dans les options suivantes, le cas échéant :
   * **[!UICONTROL Show Apple Pay on checkout page]**
   * **[!UICONTROL Show Apple Pay on product detail page]**
   * **[!UICONTROL Show Apple Pay in mini cart preview]**
   * **[!UICONTROL Show Apple Pay on cart page]**
1. Pour activer le mode de débogage, sélectionnez `Yes` pour le **[!UICONTROL Debug Mode]** (`No` le désactive).
1. Pour enregistrer vos modifications, cliquez sur **[!UICONTROL Save Config]** .
1. Accédez à **[!UICONTROL System]** > **[!UICONTROL Cache Management]**, puis cliquez sur **[!UICONTROL Flush Cache]** pour actualiser tous les caches non valides.

### Options de configuration

| Champ | Portée | Description |
|---|---|---|
| [!UICONTROL Title] | vue de magasin | Ajoutez le texte à afficher comme titre de cette option de paiement dans la vue Mode de paiement lors de l’extraction. Options : [!UICONTROL text field] |
| [!UICONTROL Payment Action] | site web | [action de paiement](https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html) pour le mode de paiement spécifié. Options : [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Show on checkout page] | site web | Activez ou désactivez [!DNL Apple Pay] sur la page de passage en caisse. Options : `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Sort order] | vue de magasin | Ordre de tri du mode de paiement spécifié sur la page de passage en caisse. `Numeric Only` value |
| [!UICONTROL Show buttons on product detail page] | vue de magasin | Activez ou désactivez [!DNL Apple Pay] sur la page des détails du produit. Options : `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons in mini-cart preview] | vue de magasin | Activez ou désactivez [!DNL Apple Pay] dans l’aperçu du mini-panier. Options : `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons on cart page] | vue de magasin | Activez ou désactivez [!DNL Apple Pay] dans la page du panier. Options : `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Debug Mode] | site web | Activez ou désactivez le mode de débogage. Options : `[!UICONTROL Yes]` / `[!UICONTROL No]` |

## [!UICONTROL Google Pay]

L’option de paiement [!UICONTROL Google Pay] permet au marchand d’offrir le paiement Google à ses acheteurs, qui peuvent utiliser le portefeuille Google sur leurs appareils pour effectuer des achats.

Voir [Options de paiement](payments-options.md#google-pay-button) pour plus d’informations.

1. Sur la barre latérale _Admin_, accédez à **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Dans le panneau de gauche, développez **[!UICONTROL Sales]** et choisissez **[!UICONTROL Payment Methods]**.
1. Développez la section _[!UICONTROL FEATURED ADOBE PAYMENT SOLUTION]_.
1. Dans la section _[!UICONTROL Payment Services]_, développez la section_[!UICONTROL Google Pay]_ .
1. (Facultatif) Modifiez le nom du mode de paiement affiché lors de l’extraction en saisissant le nouveau nom dans le champ **[!UICONTROL Title]**.
1. [Définissez l’action de paiement](production.md#set-payment-services-as-payment-method) en sélectionnant **[!UICONTROL Authorize]** ou **[!UICONTROL Authorize and Capture]**.
1. Spécifiez où l’option [!DNL Google Pay] est activée dans Adobe Commerce en sélectionnant `Yes` dans les options suivantes, le cas échéant :
   * **[!UICONTROL Show Google Pay on checkout page]**
   * **[!UICONTROL Show Google Pay on product detail page]**
   * **[!UICONTROL Show Google Pay in mini cart preview]**
   * **[!UICONTROL Show Google Pay on cart page]**
1. Pour activer le mode de débogage, sélectionnez `Yes` pour le **[!UICONTROL Debug Mode]** (`No` le désactive).
1. Configurez l’aspect du bouton _[!UICONTROL Google Pay]_en sélectionnant **[!UICONTROL Button Color]**,**[!UICONTROL Button Type]**et **[!UICONTROL Button Style]**selon les besoins.
1. Pour définir la hauteur, utilise la valeur par défaut pour la hauteur définie dans **[!UICONTROL Button Style]**.
1. Pour enregistrer vos modifications, cliquez sur **[!UICONTROL Save Config]** .
1. Accédez à **[!UICONTROL System]** > **[!UICONTROL Cache Management]**, puis cliquez sur **[!UICONTROL Flush Cache]** pour actualiser tous les caches non valides.

### Options de configuration

| Champ | Portée | Description |
|---|---|---|
| [!UICONTROL Title] | vue de magasin | Indique le libellé de texte qui s’affiche pour cette option de paiement dans la vue Mode de paiement lors du passage en caisse. Options : `[!UICONTROL text field]` |
| [!UICONTROL Payment Action] | site web | [action de paiement](https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html) pour le mode de paiement spécifié. Options : `[!UICONTROL Authorize]` / `[!UICONTROL Authorize and Capture]` |
| [!UICONTROL Show on checkout page] | site web | Activez ou désactivez [!DNL Google Pay] sur la page de passage en caisse. Options : `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Sort order] | vue de magasin | Ordre de tri du mode de paiement spécifié sur la page de passage en caisse. `Numeric Only` value |
| [!UICONTROL Show buttons on product detail page] | vue de magasin | Activez ou désactivez [!DNL Google Pay] sur la page des détails du produit. Options : `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons in mini-cart preview] | vue de magasin | Activez ou désactivez [!DNL Google Pay] dans l’aperçu du mini-panier. Options : `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons on cart page] | vue de magasin | Activez ou désactivez [!DNL Google Pay] sur la page du panier. Options : `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Debug Mode] | site web | Activez ou désactivez le mode de débogage. Options : `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Button Color] | Affichage en magasin | Définissez la couleur du bouton [!DNL Google Pay]. Options : `[!UICONTROL Default]` / `[!UICONTROL Black]` / `[!UICONTROL White]` |
| [!UICONTROL Button Type] | Affichage en magasin | Définissez le type du bouton [!DNL Google Pay]. Options : `[!UICONTROL buy]` / `[!UICONTROL checkout]` / `[!UICONTROL order]` / `[!UICONTROL pay]` / `[!UICONTROL plain]` |

Pour plus d’informations, consultez la documentation [Options d’objet de demande de l’API de paiement Google](https://developers.google.com/pay/api/web/reference/request-objects) .

## [!DNL PayPal Payment Buttons]

Les options de paiement [!DNL PayPal payment buttons] offrent un processus de paiement simple, rapide et sécurisé pour votre client.

Voir [Options de paiement](payments-options.md#paypal-smart-buttons) pour plus d’informations.

Configurer [!DNL PayPal payment buttons]

Vous pouvez activer et configurer les options de paiement des boutons de paiement PayPal au sein de l’administrateur :

1. Sur la barre latérale _Admin_, accédez à **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Dans le panneau de gauche, développez **[!UICONTROL Sales]** et choisissez **[!UICONTROL Payment Methods]**.
1. Développez la section _[!UICONTROL FEATURED ADOBE PAYMENT SOLUTION]_.
1. Dans la section _[!UICONTROL Payment Services]_, développez la section_[!UICONTROL PayPal payment buttons]_ .
1. Pour modifier le nom du mode de paiement comme indiqué lors du passage en caisse, modifiez le champ _[!UICONTROL Title]_.
1. Pour [définir l&#39;action de paiement](production.md#set-payment-services-as-payment-method), sélectionnez **[!UICONTROL Authorize]** ou **[!UICONTROL Authorize and Capture]**.
1. Pour donner la priorité à un mode de paiement sur la page de passage en caisse, indiquez une valeur `Numeric Only` dans le champ **[!UICONTROL Sort order]**.
1. Pour activer/désactiver la [messagerie plus tard](payments-options.md#pay-later-button), sélectionnez `Yes`/`No` pour **[!UICONTROL Display Pay Later Message]**.
1. Indiquez où les boutons de paiement PayPal sont activés dans Adobe Commerce en sélectionnant `Yes` dans les options suivantes, le cas échéant :
   * **[!UICONTROL Show buttons on checkout page]**
   * **[!UICONTROL Show buttons on product detail page]**
   * **[!UICONTROL Show buttons in mini cart preview]**
   * **[!UICONTROL Show buttons on cart page]**
1. Pour activer Venmo en tant qu’option de paiement, sélectionnez `Yes` pour **[!UICONTROL Venmo Enabled]**.
1. Pour activer les cartes de crédit et de débit comme option de paiement (bouton PayPal Smart), sélectionnez `Yes` pour **[!UICONTROL Credit and Debit Card Enabled]**.
1. Pour activer/désactiver l’option de paiement [ PayPal plus tard](payments-options.md#pay-later-button), sélectionnez `Yes`/`No` pour **[!UICONTROL PayPal Pay Later Enabled]**.
1. Pour activer le mode de débogage, sélectionnez `Yes` pour le **[!UICONTROL Debug Mode]** (`No` le désactive).
1. Pour enregistrer vos modifications, cliquez sur **[!UICONTROL Save Config]** .
1. Accédez à **[!UICONTROL System]** > **[!UICONTROL Cache Management]**, puis cliquez sur **[!UICONTROL Flush Cache]** pour actualiser tous les caches non valides.

### Options de configuration

| Champ | Portée | Description |
|---|---|---|
| [!UICONTROL Title] | vue de magasin | Ajoutez le texte à afficher comme titre pour cette option de paiement dans la vue Mode de paiement lors de l’extraction. Options : champ de texte |
| [!UICONTROL Payment Action] | site web | [action de paiement](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target="_blank"} pour le mode de paiement spécifié. Options : [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Display Pay Later Message] | site web | Activez ou désactivez la messagerie Payer plus tard dans le panier, la page du produit, le mini-panier et pendant le flux de passage en caisse. Options : `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons on checkout page] | vue de magasin | Activez ou désactivez [!DNL PayPal payment buttons] sur la page de passage en caisse. Options : `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons on product detail page] | vue de magasin | Activez ou désactivez [!DNL PayPal payment buttons] sur la page des détails du produit. Options : `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons in mini-cart preview] | vue de magasin | Activez ou désactivez [!DNL PayPal payment buttons] dans l’aperçu du mini-panier. Options : `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons on cart page] | vue de magasin | Activez ou désactivez [!DNL PayPal payment buttons] dans la page du panier. Options : `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Venmo Enabled] | vue de magasin | Activez ou désactivez l’option de paiement Venmo lorsque les boutons de paiement s’affichent. Options : `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Credit and Debit Card Enabled] | vue de magasin | Activez ou désactivez les options de carte Crédit et Débit lorsque des boutons de paiement s’affichent. Options : `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL PayPal Pay Later Enabled] | vue de magasin | Activez ou désactivez l’aspect de l’option Payer plus tard lorsque des boutons de paiement s’affichent. Options : `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Debug Mode] | site web | Activez ou désactivez le mode de débogage. Options : `[!UICONTROL Yes]` / `[!UICONTROL No]` |

## Style de bouton

Vous pouvez également configurer les options _[!UICONTROL Button style]_des boutons de paiement :

1. Sur la barre latérale _Admin_, accédez à **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Dans le panneau de gauche, développez **[!UICONTROL Sales]** et choisissez **[!UICONTROL Payment Methods]**.
1. Développez la section _[!UICONTROL FEATURED ADOBE PAYMENT SOLUTION]_.
1. Dans la section _[!UICONTROL [!DNL Payment Services]]_, développez la section_[!UICONTROL PayPal Smart Button Styling]_ .
1. Pour définir la disposition, sélectionnez `Vertical` ou `Horizontal` pour **[!UICONTROL Layout]**
1. Pour définir la couleur, sélectionnez l’une des couleurs disponibles dans **[!UICONTROL Color]**.
1. Pour définir la forme, sélectionnez `Rectangular` ou `Pill` pour **[!UICONTROL Shape]**.
1. Pour utiliser la hauteur par défaut, sélectionnez `Yes` ou `No` pour **[!UICONTROL Use Default Height]**.
1. Pour définir la hauteur personnalisée, ajoutez la hauteur de pixel souhaitée pour **[!UICONTROL Height]**.
1. Pour définir le tag, sélectionnez `Yes` ou `No` pour **[!UICONTROL Tagline]**.
1. Pour enregistrer vos modifications, cliquez sur **[!UICONTROL Save Config]** .
1. Accédez à **[!UICONTROL System]** > **[!UICONTROL Cache Management]**, puis cliquez sur **[!UICONTROL Flush Cache]** pour actualiser tous les caches non valides.

Vous pouvez également configurer le style du bouton de paiement [ dans Paramètres](settings.md#button-style) à partir de la page d’accueil des services de paiement.

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

Si vous modifiez la configuration, [videz manuellement le cache](/help/payment-services/settings.md#flush-the-cache) afin que votre magasin affiche les derniers paramètres de configuration.
