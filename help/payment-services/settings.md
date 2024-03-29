---
title: Paramètres des services de paiement
description: Après l’installation, vous pouvez configurer [!DNL Payment Services] dans la Maison.
role: Admin, User
level: Intermediate
exl-id: 108f2b24-39c1-4c87-8deb-d82ee1c24d55
feature: Payments, Checkout, Configuration
source-git-commit: 8dd4f629fa60959588cee4ea22f9fb577f338716
workflow-type: tm+mt
source-wordcount: '2372'
ht-degree: 0%

---

# Paramètres

Vous pouvez personnaliser [!DNL Payment Services] à vos besoins avec des paramètres utiles dans la [!DNL Payment Services] Chez soi.

Pour configurer [!DNL Payment Services] pour [!DNL Adobe Commerce] et [!DNL Magento Open Source] click **[!UICONTROL Settings]**. Ces options de configuration s’appliquent uniquement à l’environnement défini dans la variable _[!UICONTROL Payment mode]_du champ[_ Général _options de configuration](#configure-general-settings).

Pour une configuration multi-magasin ou héritée, voir [Configuration dans l’administrateur](configure-admin.md).

## Configuration des paramètres généraux

La variable [!UICONTROL General] ces paramètres permettent d’activer ou de désactiver les services de paiement en tant que mode de paiement et d’ajouter des informations aux transactions client pour marquer ou préfixer un site web ou stocker des informations personnalisées.

### Activation des services de paiement

Vous pouvez activer [!DNL Payment Services] pour votre site web et activez les tests sandbox ou les paiements en direct.

1. Sur le _Administration_ barre latérale, accédez à **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   ![Vue d’accueil](assets/payment-services-menu-small.png){width="400" zoomable="yes"}

1. Cliquez sur **[!UICONTROL Settings]**. Voir [Introduction à [!DNL Payment Services] Accueil](payments-home.md) pour plus d’informations.

   La variable _[!UICONTROL General]_comprend les paramètres utilisés pour activer [!DNL Payment Services] comme mode de paiement.

1. Pour activer [!DNL Payment Services] comme mode de paiement pour votre boutique, dans la variable _[!UICONTROL General]_section, bascule **[!UICONTROL Enable Payment Services as payment method]**to `Yes`.

1. Si vous effectuez toujours des tests [!DNL Payment Services] pour votre boutique, définissez **Mode de paiement** to `Sandbox`. Si vous êtes prêt à activer les paiements en direct, définissez-le sur `Production`.

   >[!NOTE]
   >
   >Votre _[!UICONTROL Sandbox Merchant ID]_et_[!UICONTROL Production Merchant ID]_ sont générés automatiquement et présents dans leurs champs respectables lorsque vous avez terminé l’intégration pour l’environnement de test et/ou la production.

1. Cliquez sur **[!UICONTROL Save]**.

   Si vous essayez de quitter cette vue sans enregistrer vos modifications, un modal s’affiche pour vous inviter à ignorer les modifications, à continuer les modifications ou à les enregistrer.

1. Accédez à **[!UICONTROL System]** > **[!UICONTROL Cache Management]** et cliquez sur **[!UICONTROL Flush Cache]** pour actualiser tous les caches non valides.

Vous pouvez maintenant modifier les paramètres par défaut pour [options de paiement](#configure-payment-options) fonctions et affichage du storefront.

### Ajout d’un descripteur logiciel

Vous pouvez ajouter une [!UICONTROL Soft Descriptor] à votre(s) site(s) web ou configuration de vues de magasin individuelles. Les descripteurs Soft s’affichent sur les relevés bancaires des transactions client. Si vous disposez de plusieurs magasins, marques ou catalogues, par exemple, vous pouvez facilement les délimiter en ajoutant du texte personnalisé à la variable [!UICONTROL Soft Descriptor] champ .

1. Sur le _Administration_ barre latérale, accédez à **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Cliquez sur **[!UICONTROL Settings]**. Voir [Introduction à [!DNL Payment Services] Accueil](payments-home.md) pour plus d’informations.
1. Sélectionnez la vue du site web ou du magasin dans la **[!UICONTROL Scope]** menu déroulant, pour lequel vous souhaitez créer un descripteur logiciel. Pour la configuration initiale, conservez la valeur **[!UICONTROL Default]** pour définir la valeur par défaut.
1. Ajoutez votre texte personnalisé (jusqu’à 22 caractères) dans le champ de texte, en remplaçant `Custom descriptor`.
1. Cliquez sur **[!UICONTROL Save]**.
1. Pour créer un descripteur logiciel autre que la valeur par défaut configurée pour un site web ou une vue de magasin :
   1. Sélectionnez la vue du site web ou du magasin dans la **[!UICONTROL Scope]** menu déroulant, pour lequel vous souhaitez créer un descripteur logiciel.
   1. Basculer _off_ **[!UICONTROL Use website]** (ou **[!UICONTROL Use default]**, selon la portée sélectionnée).
   1. Ajoutez votre texte personnalisé dans le champ de texte.
   1. Cliquez sur **[!UICONTROL Save]**.
1. Pour activer un site web ou un magasin, consultez le descripteur de configuration douce par défaut _ou_ le descripteur soft utilisé pour le site web parent :
   1. Sélectionnez la vue du site web ou du magasin dans la **[!UICONTROL Scope]** menu déroulant pour lequel vous souhaitez activer un descripteur logiciel existant.
   1. Basculer _on_ **[!UICONTROL Use website]** (ou **[!UICONTROL Use default]**, selon la portée sélectionnée).
   1. Cliquez sur **[!UICONTROL Save]**.

   Si vous essayez de quitter cette vue sans enregistrer vos modifications, un modal s’affiche pour vous inviter à ignorer les modifications, à continuer les modifications ou à les enregistrer.

### Options de configuration

| Champ | Portée | Description |
|---|---|---|
| [!UICONTROL Enable] | site web | Activer ou désactiver [!DNL Payment Services] pour votre site web. Options : [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Payment mode] | vue de magasin | Définissez la méthode, ou l’environnement, de votre magasin. Options : [!UICONTROL Sandbox] / [!UICONTROL Production] |
| [!UICONTROL Sandbox Merchant ID] | vue de magasin | Votre ID de marchand d’environnement de test, qui est généré automatiquement lors de l’intégration des environnements de test. |
| [!UICONTROL Production Merchant ID] | vue de magasin | Votre identifiant commercial de production, qui est généré automatiquement lors de l’intégration des environnements de test. |
| [!UICONTROL Soft Descriptor] | site web ou vue de magasin | Ajoutez un descripteur logiciel à votre ou vos sites web et vues de magasin pour ajouter des informations aux transactions client qui délimitent les marques, les magasins ou les lignes de produits. La variable [!UICONTROL Use website] s’applique à tout descripteur logiciel ajouté au niveau du site web. La variable [!UICONTROL Use default] Le bouton bascule applique tout descripteur de type Soft ajouté comme valeur par défaut. |

## Configuration des options de paiement

Maintenant que vous avez activé [!UICONTROL Payment Services] pour votre site web, vous pouvez modifier les paramètres par défaut des fonctions de paiement et de l’affichage storefront.

1. Sur le _Administration_ barre latérale, accédez à **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Cliquez sur **[!UICONTROL Settings]**. Voir [Introduction à [!DNL Payment Services] Accueil](payments-home.md) pour plus d’informations.
1. Configuration des options de paiement pour [cartes de crédit](#credit-card-fields), [boutons de paiement](#payment-buttons), et [style du bouton](#button-style), selon les sections suivantes.

### Champs de carte de crédit

La variable _[!UICONTROL Credit Card Fields]_ces paramètres offrent une option de paiement simple et sécurisée pour les modes de paiement par carte de crédit ou carte de débit.

Voir [Options de paiement](payments-options.md#credit-card-fields) pour plus d’informations.

1. Sur le _Administration_ barre latérale, accédez à **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Sélectionnez la vue de magasin, dans la **[!UICONTROL Scope]** menu déroulant, pour lequel vous souhaitez activer un mode de paiement.
1. Dans le **[!UICONTROL Credit card fields]** , modifiez la valeur de la variable **[!UICONTROL Checkout title]** pour modifier le nom du mode de paiement affiché lors du passage en caisse.
1. À [définir l’action de paiement ;](production.md#set-payment-services-as-payment-method), bascule **[!UICONTROL Payment action]** to `Authorize` ou `Authorize and Capture`.
1. Pour donner la priorité à un mode de paiement sur la page de passage en caisse, fournissez un `Numeric Only` dans la variable **[!UICONTROL Sort order]** champ .
1. Pour activer [Authentification sécurisée 3DS](security.md#3ds) (`Off` par défaut) activez la fonction **[!UICONTROL 3DS Secure authentication]** sélecteur à `Always` ou `When required`.
1. Pour activer ou désactiver les champs de carte de crédit sur la page de passage en caisse, faites basculer le **[!UICONTROL Show on checkout page]** sélecteur.
1. Pour activer ou désactiver [coffre-fort à carte](#card-vaulting), faites basculer le **[!UICONTROL Vault enabled]** sélecteur.
1. Pour activer ou désactiver [méthodes de paiement en chambre d’arrêt dans l’administrateur](#card-vaulting) (pour que les commerçants exécutent les commandes pour les clients de l’administrateur à l’aide de leur méthode de paiement par défaut), activez la variable **[!UICONTROL Show vaulted methods in Admin]** sélecteur.
1. Pour activer ou désactiver le mode de débogage, activez la fonction **[!UICONTROL Debug Mode]** sélecteur.
1. Cliquez sur **[!UICONTROL Save]**.

   Si vous essayez de quitter cette vue sans enregistrer vos modifications, un modal s’affiche pour vous inviter à ignorer les modifications, à continuer les modifications ou à les enregistrer.

1. [Vider le cache](#flush-the-cache).

#### Options de configuration

| Champ | Portée | Description |
|---|---|---|
| [!UICONTROL Title] | vue de magasin | Ajoutez le texte à afficher comme titre de cette option de paiement dans la vue Mode de paiement lors de l’extraction. Options : [!UICONTROL text field] |
| [!UICONTROL Payment Action] | site web | La variable [action de paiement](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target="_blank"} pour le mode de paiement spécifié. Options : [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Sort order] | vue de magasin | Ordre de tri du mode de paiement spécifié sur la page de passage en caisse. `Numeric Only` value |
| [!UICONTROL 3DS Secure authentication] | site web | Activer ou désactiver [Authentification sécurisée 3DS](security.md#3ds). Options : [!UICONTROL Always] / [!UICONTROL When Required] / [!UICONTROL Off] |
| [!UICONTROL Show on checkout page] | site web | Activez ou désactivez les champs de carte de crédit à afficher sur la page de paiement. Options : [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Vault enabled] | vue de magasin | Activer ou désactiver [coffre-fort à carte de crédit](vaulting.md). Options : [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show vaulted payment methods in Admin] | vue de magasin | Permet d’activer ou de désactiver la possibilité pour le marchand d’exécuter des commandes pour les clients dans l’administrateur. [utilisation d’un mode de paiement par défaut](vaulting.md). Options : [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Debug Mode] | site web | Activez ou désactivez le mode de débogage. Options : [!UICONTROL Off] / [!UICONTROL On] |

### Apple Pay

La variable [!UICONTROL Apple Pay] l’option de paiement de bouton vous permet de fournir un [!UICONTROL Apple Pay] bouton de paiement dans le passage en caisse de votre boutique depuis le navigateur Safari (pour 99 domaines par compte marchand au maximum).

Vous ne pouvez utiliser Apple Pay que si vous avez terminé [Enregistrement automatique des paiements Apple via Paypal](https://developer.paypal.com/docs/checkout/apm/apple-pay/#register-your-live-domain) puis [configurer Apple Pay](settings.md/#payment-buttons) pour vos magasins. Voir [Options de paiement](payments-options.md#apple-pay-button) pour plus d’informations.

Vous pouvez activer et configurer le [!UICONTROL Apple Pay] option de paiement du bouton :

1. Sur le _Administration_ barre latérale, accédez à **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Sélectionnez la vue de magasin, dans la **[!UICONTROL Scope]** menu déroulant, pour lequel vous souhaitez activer un mode de paiement.
1. Dans le **[!UICONTROL Apple Pay]** , modifiez la valeur de la variable _[!UICONTROL Checkout title]_pour modifier le nom du mode de paiement affiché lors du passage en caisse.
1. À [définir l’action de paiement ;](production.md#set-payment-services-as-payment-method), bascule **[!UICONTROL Payment action]** to `Authorize` ou `Authorize and Capture`.
1. Pour activer ou désactiver l’option de paiement Apple sur la page de passage en caisse, faites basculer le **[!UICONTROL Show Apple Pay on checkout page]** sélecteur.
1. Pour activer ou désactiver l’option de paiement Apple sur la page des détails du produit, faites basculer le **[!UICONTROL Show Apple Pay on product detail page]** sélecteur.
1. Pour activer ou désactiver l’option de paiement Apple dans l’aperçu du mini-panier, activez la variable **[!UICONTROL Show Apple Pay on the mini cart preview]** sélecteur.
1. Pour activer ou désactiver l’option de paiement Apple sur la page du panier, faites basculer le **[!UICONTROL Show Apple Pay on cart page]** sélecteur.
1. Pour activer ou désactiver le mode de débogage, activez la fonction **[!UICONTROL Debug Mode]** sélecteur.
1. Cliquez sur **[!UICONTROL Save]**.

   Si vous essayez de quitter cette vue sans enregistrer vos modifications, un modal s’affiche pour vous inviter à ignorer les modifications, à continuer les modifications ou à les enregistrer.

1. [Vider le cache](#flush-the-cache).

#### Options de configuration

| Champ | Portée | Description |
|---|---|---|
| [!UICONTROL Checkout title] | vue de magasin | Ajoutez le texte à afficher comme titre de cette option de paiement dans la vue Mode de paiement lors de l’extraction. Options : [!UICONTROL text field] |
| [!UICONTROL Payment Action] | site web | La variable [action de paiement](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions) pour le mode de paiement spécifié. Options : [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Show on checkout page] | site web | Activez ou désactivez le bouton Payer Apple à afficher sur la page de paiement. Options : [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show on checkout page] | site web | Activez ou désactivez le bouton Payer Apple pour afficher sur la page des détails du produit. Options : [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show on mini cart preview] | site web | Activez ou désactivez le bouton Payer Apple pour afficher l’aperçu du mini panier. Options : [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show on cart page] | site web | Activez ou désactivez le bouton Payer Apple à afficher sur la page du panier. Options : [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Debug Mode] | site web | Activez ou désactivez le mode de débogage. Options : [!UICONTROL Off] / [!UICONTROL On] |

### Boutons de paiement

La variable [!DNL PayPal payment buttons] les options de paiement offrent un processus de paiement simple, rapide et sécurisé pour votre client. Voir [Options de paiement](payments-options.md#paypal-smart-buttons) pour plus d’informations.

Vous pouvez activer et configurer les options de paiement des boutons de paiement PayPal :

1. Sélectionnez la vue de magasin, dans la **[!UICONTROL Scope]** menu déroulant, pour lequel vous souhaitez activer un mode de paiement.
1. Pour modifier le nom du mode de paiement, comme indiqué lors de l’extraction, modifiez la valeur de la variable **[!UICONTROL Checkout Title]** champ .
1. À [définir l’action de paiement ;](production.md#set-payment-services-as-payment-method), bascule **[!UICONTROL Payment action]** to `Authorize` ou `Authorize and Capture`.
1. Pour donner la priorité à un mode de paiement sur la page de passage en caisse, fournissez un `Numeric Only` dans la variable **[!UICONTROL Sort order]** champ .
1. Utilisation des sélecteurs de basculement pour activer ou désactiver [!DNL PayPal smart button] fonctionnalités d’affichage :

   - **[!UICONTROL Show PayPal buttons on product checkout page]**
   - **[!UICONTROL Show PayPal buttons on product detail page]**
   - **[!UICONTROL Show PayPal buttons in mini-cart preview]**
   - **[!UICONTROL Show PayPal buttons on cart page]**
   - **[!UICONTROL Show PayPal Pay Later button]**
   - **[!UICONTROL Show PayPal Pay Later message]**
   - **[!UICONTROL Show Venmo button]**
   - **[!UICONTROL Show Apple Pay button]**
   - **[!UICONTROL Show PayPal Credit and Debit Card button]**

     >[!NOTE]
     >
     > Pour utiliser Apple Pay [posséder un compte de test d’environnement de test Apple](https://developer.apple.com/apple-pay/sandbox-testing/#create-a-sandbox-tester-account) (avec une fausse carte de crédit et des informations de facturation) pour le tester. Lorsque vous êtes prêt à utiliser Apple Pay dans un environnement de test _ou_ mode de production, après avoir effectué toute [test et validation](test-validate.md#test-in-sandbox-environment), complete [auto-inscription avec [!DNL Apple Pay]](https://developer.paypal.com/docs/checkout/apm/apple-pay/#register-your-live-domain) (_Enregistrement de votre domaine de production_ uniquement) et [le configurer pour vos magasins dans [!DNL Payment Services]](settings.md#payment-buttons).

     Lorsque vous activez/désactivez la visibilité des boutons de paiement ou le message PayPal Pay Later, un aperçu visuel de cette configuration s’affiche au bas de la page Paramètres .

1. Pour activer le mode de débogage, activez la fonction **[!UICONTROL Debug Mode]** sélecteur.
1. Cliquez sur **[!UICONTROL Save]**.

   Si vous essayez de quitter cette vue sans enregistrer vos modifications, un modal s’affiche pour vous inviter à ignorer les modifications, à continuer les modifications ou à les enregistrer.

1. [Vider le cache](#flush-the-cache).

#### Options de configuration

| Champ | Portée | Description |
|---|---|---|
| [!UICONTROL Title] | vue de magasin | Ajoutez le texte à afficher comme titre pour cette option de paiement dans la vue Mode de paiement lors de l’extraction. Options : champ de texte |
| [!UICONTROL Payment Action] | site web | La variable [action de paiement](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target="_blank"} pour le mode de paiement spécifié. Options : [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Sort order] | vue de magasin | Ordre de tri du mode de paiement spécifié sur la page de passage en caisse. `Numeric Only` value |
| [!UICONTROL Show PayPal buttons on checkout page] | vue de magasin | Activer ou désactiver [!DNL PayPal payment buttons] sur la page de passage en caisse. Options : [!UICONTROL  Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal buttons on product detail page] | vue de magasin | Activer ou désactiver [!DNL PayPal payment buttons] sur la page des détails du produit. Options : [!UICONTROL  Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal buttons in mini-cart preview] | vue de magasin | Activer ou désactiver [!DNL PayPal payment buttons] dans l’aperçu du mini-panier. Options : [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show PayPal buttons on cart page] | vue de magasin | Activer ou désactiver [!DNL PayPal payment buttons] sur la page du panier. Options : [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show PayPal Pay Later button] | vue de magasin | Activez ou désactivez l’aspect de l’option de paiement ultérieur lorsque des boutons de paiement s’affichent. Options : [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show PayPal Pay Later Message] | site web | Activez ou désactivez la messagerie Payer plus tard dans le panier, la page du produit, le mini-panier et pendant le flux de passage en caisse. Options : [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show Venmo button] | vue de magasin | Activez ou désactivez l’option de paiement Venmo lorsque les boutons de paiement s’affichent. Options : [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show Apple Pay button] | vue de magasin | Activez ou désactivez l’option Paiement Apple dans laquelle les boutons de paiement s’affichent. Options : [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show PayPal Credit and Debit card button] | vue de magasin | Activez ou désactivez l’option de paiement par carte de crédit et de débit où des boutons de paiement s’affichent. Options : [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Debug Mode] | site web | Activez ou désactivez le mode de débogage. Options : [!UICONTROL Off] / [!UICONTROL On] |

### Style de bouton

Vous pouvez également configurer la variable _[!UICONTROL Button style]_options des boutons de paiement :

1. Pour modifier la variable **[!UICONTROL Layout]**, sélectionnez `Vertical` ou `Horizontal`.

   >[!NOTE]
   >
   > Si le style du bouton est configuré comme `Horizontal` et que votre boutique est configurée pour afficher plusieurs boutons de paiement, vous ne pouvez afficher que deux boutons sur la page produit, la page de passage en caisse et le mini-panier, et un seul bouton dans le panier.

1. Pour activer le tag dans une disposition horizontale, faites basculer le **[!UICONTROL Show tagline]** sélecteur.
1. Pour modifier la variable **[!UICONTROL Color]**, sélectionnez la couleur de votre choix.
1. Pour modifier la variable **[!UICONTROL Shape]**, sélectionnez `Pill` ou `Rectangle`.
1. Pour activer le sélecteur de hauteur de bouton, faites basculer le bouton **[!UICONTROL Responsive button height]** sélecteur.
1. Pour modifier la variable **[!UICONTROL Label]**, sélectionnez l’option de libellé de votre choix.

   Lorsque vous modifiez les options de configuration pour la disposition, la couleur, la forme, la hauteur et le libellé, un aperçu visuel de cette configuration s’affiche au bas de la page Paramètres . Dans l’image ci-dessous, la variable **[!UICONTROL Shape]** est défini sur _Rectangle_ et la variable **[!UICONTROL Label]** est défini sur _PayPal (recommandé)_.

   ![[!DNL PayPal payment buttons] options](assets/payment-buttons.png){width="400" zoomable="yes"}

1. Cliquez sur **[!UICONTROL Save]**.

   Si vous essayez de quitter cette vue sans enregistrer vos modifications, un modal s’affiche pour vous inviter à ignorer les modifications, à continuer les modifications ou à les enregistrer.

1. [Vider le cache](#flush-the-cache).

Vous pouvez configurer le style des boutons de paiement [dans la configuration héritée de l’administrateur.](configure-admin.md#configure-paypal-smart-buttons) ou ici dans [!DNL Payment Services Home]. Voir [Guide de style Boutons de PayPal](https://developer.paypal.com/docs/checkout/standard/customize/buttons-style-guide/) pour plus d’informations sur le style des boutons de paiement PayPal.

#### Options de configuration

| Champ | Portée | Description |
|--- |--- |--- |
| [!UICONTROL Layout] | Affichage en magasin | Définissez le style de mise en page des boutons de paiement. Options : [!UICONTROL Vertical] / [!UICONTROL Horizontal] |
| [!UICONTROL Tagline] | Affichage en magasin | Activez/désactivez tagline. Options : [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Color] | Affichage en magasin | Définissez la couleur des boutons de paiement. Options : [!UICONTROL Blue] / [!UICONTROL Gold] / [!UICONTROL Silver] / [!UICONTROL White] / [!UICONTROL Black] |
| [!UICONTROL Shape] | Affichage en magasin | Définissez la forme des boutons de paiement. Options : [!UICONTROL Rectangular] / [!UICONTROL Pill] |
| [!UICONTROL Responsive Button Height] | Affichage en magasin | Définit si les boutons de paiement utilisent une hauteur par défaut. Options : [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Height] | Affichage en magasin | Définissez la hauteur des boutons de paiement. Valeur par défaut : aucune |
| [!UICONTROL Label] | Affichage en magasin | Définissez le libellé qui apparaît dans les boutons de paiement. Options : [!UICONTROL PayPal] / [!UICONTROL Checkout] / [!UICONTROL Buynow] / [!UICONTROL Pay] / [!UICONTROL Installment] |

## Configuration des rôles

Pour vous assurer que les utilisateurs administrateurs peuvent créer et gérer des commandes dans l’administrateur Commerce, activez [!DNL Payment Services]ressources spécifiques aux rôles utilisateur.

Voir [Rôles utilisateur](https://experienceleague.adobe.com/docs/commerce-admin/systems/user-accounts/permissions-user-roles.html) pour apprendre à gérer les rôles.

Lorsque vous attribuez des ressources au rôle, vous devez sélectionner :

- **Payer avec[!DNL Payment Services]**: cette ressource garantit que lorsque vous créez une commande dans l’administrateur, [!DNL Payment Services] les cartes de crédit sont disponibles en tant que mode de paiement. Si vous sélectionnez l’option **Actions** ressource parente, cette ressource sera également sélectionnée.
- **[!DNL Payment Services]**: cette ressource inclut la variable **Tableau de bord** et **Proxy de services SaaS** ressources, qui doit également être sélectionnée. Ils s’assurent que [!DNL Payment Services] apparaît dans la variable _Ventes_ .

  ![Ressources des services de paiement](assets/roles-payments.png){width="400" zoomable="yes"}

## Vider le cache

Si vous modifiez la configuration dans _Paramètres_, par exemple en activant les boutons Payer, Venmo ou Payer plus tard d’Apple, videz manuellement le cache afin que votre boutique affiche les dernières configurations.

1. Sur le _Administration_ barre latérale, accédez à **[!UICONTROL System]** > **[!UICONTROL Cache Management]**.
1. Cliquez sur **[!UICONTROL Flush Cache]** pour actualiser tous les caches non valides.

Si un type de cache dans la table Gestion du cache comporte une `INVALIDATED` , votre boutique peut ne pas afficher la configuration la plus récente pour cet élément. Videz le cache pour mettre à jour votre magasin afin d’afficher la configuration la plus récente.

Pour vous assurer que votre boutique affiche la configuration correcte, vérifiez régulièrement [vider le cache](https://docs.magento.com/user-guide/system/cache-management.html).

## Valorisation des cartes

Vous pouvez activer une fonctionnalité qui permet à vos clients de sauvegarder (ou &quot;enregistrer&quot;) leurs informations de carte de crédit dans leur compte pour les utiliser pour de futurs achats.

Vous pouvez également utiliser la mise en valeur de carte dans l’administrateur pour terminer les commandes suivantes pour les clients existants.

Activation ou désactivation de la valeur de carte dans le [Paramètres des champs de carte de crédit](#credit-card-fields).

Voir [Valorisation des cartes de crédit](vaulting.md) pour plus d’informations.

## 3DS

3DS protège les clients et les commerçants contre les activités frauduleuses dans leurs magasins et permet la conformité aux normes de l’Union européenne (UE).

Activez ou désactivez 3DS dans la variable [Paramètres des champs de carte de crédit](#credit-card-fields).

Voir [3DS en sécurité](security.md#3ds) pour plus d’informations.

## Utilisation de plusieurs comptes PayPal

Dans [!UICONTROL Payment Services], vous pouvez utiliser plusieurs comptes PayPal dans **one** compte commercial au niveau du site web. Par exemple, si vous exploitez votre ou vos boutiques dans plusieurs pays (qui utilisent différents [devises](https://docs.magento.com/user-guide/stores/currency.html)) ou utiliser Adobe Commerce pour certaines parties de votre entreprise, mais pas _all_, vous pouvez configurer votre compte marchand pour utiliser plusieurs comptes PayPal.

Voir [Site, magasin et portée de l’affichage](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html) pour plus d’informations sur la hiérarchie des sites web, des magasins et des vues de magasin.

Votre représentant commercial peut créer [scope](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) pour votre compte marchand et à bord du site supplémentaire avec PayPal afin que tous les boutons PayPal que vous configurez pour apparaître s’affichent sur votre site. Contactez votre représentant commercial pour obtenir de l’aide sur l’utilisation de plusieurs comptes PayPal pour vos sites web.
