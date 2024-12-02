---
title: Options de paiement
description: Définissez les options de paiement pour personnaliser les méthodes disponibles pour les clients de votre magasin.
exl-id: 95e648e6-6cb8-4226-b5ea-e1857212f20a
feature: Payments, Checkout, Configuration
source-git-commit: 23743bb3cc62e1f4f33c4f1046f341b99e47d9c5
workflow-type: tm+mt
source-wordcount: '1174'
ht-degree: 0%

---

# Options de paiement

Avec [!DNL Adobe Commerce] et [!DNL Magento Open Source] [!DNL Payment Services], plusieurs options de paiement sont à votre disposition.

Vous pouvez configurer ces options de paiement dans les [Paramètres de l’accueil](payments-home.md) ou la [configuration du magasin](configure-admin.md) (recommandée pour les options de paiement héritées ou une configuration multi-boutique).

Il existe différents comportements pour chaque mode de paiement en fonction de l’emplacement du processus de passage en caisse :

* Page de produit : page de produit d’un article.
* Mini panier : disponible en un clic sur l’icône de panier lorsqu’un produit a été ajouté au panier.
* Panier : disponible en un clic sur _Afficher et modifier le panier_ depuis le mini panier
* Mode Passage en caisse : disponible en un clic de _passage en caisse_ à partir du mini-panier ou du panier

>[!IMPORTANT]
>
>L’intégration de [!DNL Payment Services] doit être terminée avant que les paiements puissent être traités.

## Comparaison entre l’expérience de paiement standard et l’expérience de paiement avancé

[!DNL Payment Services] fournit des options de paiement et des flux d’intégration **Advanced** (entièrement pris en charge) et **Standard** (Express Checkout), selon le pays dans lequel vous opérez.

* **Avancé** - Toutes les [ options de paiement disponibles](../payment-services/payments-options.md) sont disponibles pour les [ pays actuellement ](../payment-services/overview.md#availability) entièrement pris en charge. Lors de l’intégration pour activer les paiements en direct, sélectionnez l’ [option d’intégration avancée](../payment-services/production.md#advanced-onboarding).
* **Standard** - Un sous-ensemble d’options de paiement (paiement express) : cartes de crédit et de débit PayPal est disponible pour les autres pays pris en charge. Les [ champs de carte de crédit ](#credit-card-fields) et [paiement Apple](#apple-pay-button) ne sont pas disponibles pour cette option d’intégration. Lors de l’intégration pour activer les paiements en direct, sélectionnez l’ [option d’intégration standard](../payment-services/production.md#standard-onboarding).

Voir [Activer [!DNL Payment Services] pour la production](../payment-services/production.md#complete-merchant-onboarding) pour plus d’informations sur l’intégration d’Advanced and Standard.

## [!UICONTROL Credit Card Fields]

[!UICONTROL Credit Card Fields] fournit un passage en caisse simple et sécurisé pour les méthodes de paiement par carte de crédit ou carte de débit. Lorsqu’un acheteur passe en caisse en utilisant des champs de carte de crédit, il saisit son nom, son adresse de facturation et les informations de carte de crédit ou de débit pour passer sa commande. Les informations sur les clients sont utilisées de manière sécurisée au cours de la session d’achat pour les guider de manière transparente tout au long du flux de passage en caisse.

![Champs de carte de crédit dans le passage en caisse](assets/credit-card-fields.png){width="500" zoomable="yes"}

Activez la [valeur de carte de crédit](#vaulting) pour que vos magasins permettent aux acheteurs de sauvegarder (enregistrer) leurs informations de carte de crédit pour un passage en caisse rapide plus tard.

Vous pouvez configurer [!UICONTROL Credit Card Fields] dans la configuration du magasin ou l’ [!DNL Payment Services] accueil. Voir [Paramètres](settings.md#credit-card-fields) pour plus d’informations.

Vous pouvez également modifier la disposition, la largeur, la hauteur et le style externe des champs de la carte de crédit. Pour plus d’informations, consultez la [documentation PayPal](https://developer.paypal.com/docs/checkout/advanced/customize/card-field-style/) .

## Bouton [!DNL Apple Pay]

Les clients peuvent utiliser [[!DNL Apple Pay]](https://www.apple.com/apple-pay/), qui utilise des informations d’identification de paiement de carte de crédit et de débit stockées sur un appareil iOS ou macOS, pour effectuer des achats.

[!DNL Apple Pay] n’est disponible que dans le navigateur Safari. Les commerçants peuvent ajouter jusqu’à 99 domaines par compte marchand.

![Bouton Payer Apple dans le minicart](assets/applepay-button.png){width="500" zoomable="yes"}

Le bouton [!DNL Apple Pay] est visible à partir de la page du produit, du mini-panier, du panier et des vues de passage en caisse.

Pour utiliser [!DNL Apple Pay] pour vos magasins, effectuez l&#39;[auto-inscription avec [!DNL Apple Pay]](https://developer.paypal.com/docs/checkout/apm/apple-pay/#register-your-live-domain) (_Enregistrez votre domaine actif_ uniquement) et [configurez-le pour vos magasins dans  [!DNL Payment Services]](settings.md#payment-buttons).

>[!NOTE]
>
> Voir [passage en caisse avancé](https://www.paypal.com/us/cshelp/article/what-is-paypal-advanced-checkout-and-how-do-i-get-started-help953){target=_blank} dans la documentation destinée aux développeurs PayPal pour vérifier comment permettre aux acheteurs de payer avec Apple Pay sur votre site.

Vous pouvez configurer [!UICONTROL Apple Pay] dans la configuration du magasin ou dans la page d’accueil des services de paiement. Voir [Paramètres](settings.md#apple-pay) pour plus d’informations.

## Bouton [!DNL Google Pay]

Les clients peuvent utiliser [[!DNL Google Pay]](https://pay.google.com/about/) en ajoutant des détails de paiement à leur compte Google, où ils sont stockés en toute sécurité pour une expérience de passage en caisse transparente.

[!DNL Google Pay] n’est disponible que dans certains pays ou régions et sur certains périphériques. Pour plus d’informations, voir [[!DNL Google Pay] documentation](https://developer.paypal.com/docs/checkout/apm/google-pay/#link-googlepayintegration) .

![Bouton Payer Google dans le passage en caisse](assets/google-pay-button.png){width="500" zoomable="yes"}

Le bouton [!DNL Google Pay] est visible à partir de la page du produit, du mini-panier, du panier et des vues de passage en caisse.

Vous pouvez configurer [!UICONTROL Google Pay] dans la configuration du magasin ou dans la page d’accueil des services de paiement. Voir [Paramètres](configure-admin.md) pour plus d’informations.

>[!NOTE]
>
> L’API [!DNL Google Pay] ne peut être utilisée que sur des sites web dans un contexte sécurisé. Pour plus d’informations, voir la documentation [Dépannage](https://developers.google.com/pay/api/web/support/troubleshooting) .

## [!DNL PayPal Payment Buttons]

[!DNL PayPal payment buttons], qui utilise PayPal pour effectuer un achat, stocke l’adresse de livraison de votre acheteur, les adresses de facturation et les détails de paiement en vue d’une utilisation ultérieure. Les acheteurs peuvent utiliser n&#39;importe quel mode de paiement précédemment stocké ou proposé par PayPal.

![Bouton PayPal](assets/paypal-button.png){width="350" zoomable="yes"}

Vous pouvez configurer [!UICONTROL PayPal payment buttons] dans la configuration du magasin ou l’ [!DNL Payment Services] accueil. Voir [Paramètres](settings.md#payment-buttons) pour plus d’informations.

Découvrez la disponibilité des méthodes de paiement par pays dans la [documentation sur les méthodes de paiement](https://developer.paypal.com/docs/checkout/payment-methods/) de PayPal.

### Bouton [!DNL PayPal]

Les clients peuvent effectuer leur paiement en toute simplicité et en toute confiance à l’aide du bouton PayPal .

Le bouton [!DNL PayPal] est visible à partir de la page du produit, du mini-panier, du panier et des vues de passage en caisse.

### Bouton [!DNL Venmo]

Les clients peuvent extraire à l’aide du bouton [Venmo](https://venmo.com/) .

Le bouton [!DNL Venmo] est visible à partir de la page du produit, du mini-panier, du panier et des vues de passage en caisse.

### Bouton Débit PayPal ou Carte de crédit

Les clients peuvent régler leur paiement à l’aide du bouton Payer le débit ou la carte de crédit .

Le bouton Débit PayPal ou Carte de crédit est visible à partir de la page de passage en caisse.

Cette option peut être utilisée pour proposer une option de paiement par carte de crédit ou de débit à vos acheteurs avec un bouton hébergé par PayPal comme alternative à une intégration par carte de crédit.

### Bouton [!DNL Pay Later]

Offrez à vos clients des paiements à court terme sans intérêts et d’autres options de financement afin qu’ils puissent acheter maintenant et payer ultérieurement avec le bouton [!DNL Pay Later].

Le bouton [!DNL Pay Later] est visible à partir de la page du produit, du mini-panier, du panier et des vues de passage en caisse.

Consultez les informations sur les offres Payer plus tard dans la documentation [PayPal&#39;s Pay Later offres ](https://developer.paypal.com/docs/checkout/pay-later/us/). Utilisez la liste déroulante **Pays ou région** pour sélectionner une région d’intérêt.

Découvrez comment désactiver ou activer la messagerie [!DNL Pay Later] en mettant à jour la configuration [Settings](settings.md#payment-buttons).

## Utiliser uniquement les boutons de paiement PayPal

Pour passer rapidement en mode de production, vous pouvez configurer les boutons de paiement _only_ de PayPal (Venmo, PayPal, etc.): au lieu d’utiliser également l’option de paiement par carte de crédit PayPal .

Vous pouvez ainsi :

* Fournissez diverses options de paiement à vos clients, notamment des boutons de paiement Venmo et PayPal, avec la possibilité de désactiver les champs de carte hébergée PayPal et d’utiliser un fournisseur de carte de crédit existant.
* Utilisez le fournisseur de carte de crédit existant pour les paiements par carte de crédit, tout en utilisant les autres options de paiement de PayPal.
* Utilisez les boutons de paiement de PayPal dans les régions où PayPal ne prend pas en charge les cartes de crédit comme option de paiement.

Pour **capturer les paiements avec _uniquement_ boutons de paiement PayPal (_not_ l’option de paiement par carte de crédit PayPal)** :

1. Assurez-vous que votre magasin est [ en mode de production ](settings.md#enable-payment-services).
1. [Configurez les boutons de paiement PayPal de votre choix](settings.md#payment-buttons) dans Paramètres.
1. Désactivez l’option _Off_ de **[[!UICONTROL Show PayPal Credit and Debit card button]](settings.md#payment-buttons)** dans la section _[!UICONTROL Payment buttons]_.

Pour **capturer les paiements avec votre fournisseur de carte de crédit existant _et_ boutons de paiement PayPal** :

1. Assurez-vous que votre magasin est [ en mode de production ](settings.md#enable-payment-services).
1. [Configurez les boutons de paiement PayPal de votre choix](settings.md#payment-buttons).
1. Désactivez l’option _Off_ de **[[!UICONTROL PayPal Show Credit and Debit card button]](settings.md#payment-buttons)** dans la section _[!UICONTROL Payment buttons]_.
1. Désactivez l&#39;option _Off_ dans la section _[!UICONTROL Credit card fields]_et utilisez le [ compte de fournisseur de carte de crédit existant ](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/payments/payments.html#payments).**[[!UICONTROL Show on checkout page]](settings.md#credit-card-fields)**

## recalcul de la commande

Lorsqu’un client entre dans le flux de passage en caisse à partir du mini-panier, du panier ou de la page du produit, il est dirigé vers une page de vérification de la commande où il peut voir l’adresse de livraison sélectionnée dans une fenêtre contextuelle PayPal. Une fois que le client a sélectionné le mode de livraison, le montant de la commande est correctement recalculé et le client peut voir les frais de livraison et les taxes.

Lorsqu’un client entre dans le flux de passage en caisse à partir de la page de passage en caisse, le système connaît déjà l’adresse de livraison et le montant calculé final, et les totaux sont correctement représentés.

Les jours fériés, les frais de livraison et les taxes de vente peuvent varier considérablement d&#39;un lieu à l&#39;autre. Une fois que [!DNL Payment Services] a reçu l’adresse et le taux de livraison, il recalcule rapidement tous les coûts applicables et les affiche correctement lors des dernières étapes de la commande.

## Valorisation des cartes de crédit

Les acheteurs peuvent sauvegarder (ou &quot;enregistrer&quot;) leurs informations de carte de crédit pour les achats futurs au niveau du site web (tout magasin dans le même compte du commerçant).

Pour plus d’informations, voir [Valorisation des cartes de crédit](vaulting.md) .

## Sécurité

Voir [Conformité PCI](security.md#pci-compliance) pour plus d’informations.
