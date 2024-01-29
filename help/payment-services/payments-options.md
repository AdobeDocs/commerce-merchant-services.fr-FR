---
title: Options de paiement
description: Définissez les options de paiement pour personnaliser les méthodes disponibles pour les clients de votre magasin.
exl-id: 95e648e6-6cb8-4226-b5ea-e1857212f20a
feature: Payments, Checkout, Configuration
source-git-commit: 8dd4f629fa60959588cee4ea22f9fb577f338716
workflow-type: tm+mt
source-wordcount: '1054'
ht-degree: 0%

---

# Options de paiement

Avec [!DNL Adobe Commerce] et [!DNL Magento Open Source] [!DNL Payment Services], plusieurs options de paiement sont à votre disposition.

Vous pouvez configurer ces options de paiement dans [Paramètres d’accueil](payments-home.md) ou [Configuration du magasin](configure-admin.md) (recommandé pour les options de paiement héritées ou une configuration multi-magasin).

Il existe différents comportements pour chaque mode de paiement en fonction de l’emplacement du processus de passage en caisse :

* Page de produit : page de produit d’un article.
* Mini panier : disponible en un clic sur l’icône de panier lorsqu’un produit a été ajouté au panier.
* Panier : disponible en un clic de _Afficher et modifier le panier_ du mini-panier
* Mode Extraction : disponible en un clic de _Passez à l’extraction_ depuis un mini-panier ou un panier

>[!IMPORTANT]
>
>[!DNL Payment Services] l’intégration doit être effectuée avant que les paiements puissent être traités.

## Comparaison entre l’expérience de paiement standard et l’expérience de paiement avancé

[!DNL Payment Services] fournit **Avancé** (entièrement pris en charge) et **Standard** les options de paiement et les flux d’intégration (paiement express), en fonction du pays dans lequel vous opérez.

* **Avancé** - Toutes disponibles [options de paiement](../payment-services/payments-options.md) sont disponibles pour les [pays entièrement pris en charge](../payment-services/overview.md#availability). Lors de l’intégration pour activer les paiements en direct, sélectionnez la variable [Option d’intégration avancée](../payment-services/production.md#advanced-onboarding).
* **Standard** - Un sous-ensemble d’options de paiement (paiement express), des cartes de crédit et de débit PayPal, est disponible pour les autres pays pris en charge. [Champs de carte de crédit](#credit-card-fields) et [Apple Pay](#apple-pay-button) ne sont pas disponibles pour cette option d’intégration. Lors de l’intégration pour activer les paiements en direct, sélectionnez la variable [Option d’intégration standard](../payment-services/production.md#standard-onboarding).

Voir [Activer [!DNL Payment Services] pour la production](../payment-services/production.md#complete-merchant-onboarding) pour plus d’informations sur l’intégration à Advanced and Standard.

## [!UICONTROL Credit Card Fields]

[!UICONTROL Credit Card Fields] proposer un passage en caisse simple et sécurisé pour les modes de paiement par carte de crédit ou carte de débit ; Lorsqu’un acheteur passe en caisse en utilisant des champs de carte de crédit, il saisit son nom, son adresse de facturation et les informations de carte de crédit ou de débit pour passer sa commande. Les informations sur les clients sont utilisées de manière sécurisée au cours de la session d’achat pour les guider de manière transparente tout au long du flux de passage en caisse.

![Champs de carte de crédit dans le passage en caisse](assets/credit-card-fields.png){width="500" zoomable="yes"}

Activer [coffre-fort à carte de crédit](#vaulting) pour que vos magasins permettent aux clients de sauvegarder (enregistrer) leurs informations de carte de crédit pour un passage en caisse rapide plus tard.

Vous pouvez configurer [!UICONTROL Credit Card Fields] dans la configuration du magasin ou la [!DNL Payment Services] Chez soi. Voir [Paramètres](settings.md#credit-card-fields) pour plus d’informations.

Vous pouvez également modifier la disposition, la largeur, la hauteur et le style externe des champs de la carte de crédit. Voir [Documentation PayPal](https://developer.paypal.com/docs/checkout/advanced/customize/card-field-style/) pour plus d’informations.

## [!DNL Apple Pay] button

Les clients peuvent utiliser [[!DNL Apple Pay]](https://www.apple.com/apple-pay/), qui utilise les informations d’identification de paiement de carte de crédit et de débit stockées sur un appareil iOS ou macOS, pour effectuer des achats.

[!DNL Apple Pay] n’est disponible que dans le navigateur Safari. Les commerçants peuvent ajouter jusqu’à 99 domaines par compte marchand.

![Bouton Payer Apple dans le minicart](assets/apple-pay-button.png){width="500" zoomable="yes"}

La variable [!DNL Apple Pay] est visible à partir de la page produit, du mini-panier, du panier et des vues de passage en caisse.

>[!NOTE]
>
> Pour utiliser [!DNL Apple Pay] pour vos magasins, effectuez les opérations suivantes : [auto-inscription avec [!DNL Apple Pay]](https://developer.paypal.com/docs/checkout/apm/apple-pay/#register-your-live-domain) (_Enregistrement de votre domaine de production_ uniquement) et [le configurer pour vos magasins dans [!DNL Payment Services]](settings.md#payment-buttons).

Vous pouvez configurer [!UICONTROL Apple Pay] dans la configuration du magasin ou dans la page d’accueil des services de paiement. Voir [Paramètres](settings.md#apple-pay) pour plus d’informations.

## [!DNL PayPal Payment Buttons]

[!DNL PayPal payment buttons], qui utilise PayPal pour effectuer un achat, stocke l’adresse de livraison de votre acheteur, les adresses de facturation et les détails de paiement en vue d’une utilisation ultérieure. Les acheteurs peuvent utiliser n&#39;importe quel mode de paiement précédemment stocké ou proposé par PayPal.

![Bouton Pal](assets/paypal-button.png){width="350" zoomable="yes"}

Vous pouvez configurer [!UICONTROL PayPal payment buttons] dans la configuration du magasin ou la [!DNL Payment Services] Chez soi.  Voir [Paramètres](settings.md#payment-buttons) pour plus d’informations.

Voir PayPal [Documentation sur les méthodes de paiement](https://developer.paypal.com/docs/checkout/payment-methods/) pour savoir dans quels pays chaque mode de paiement est actuellement disponible.

### [!DNL PayPal] button

Les clients peuvent effectuer leur paiement en toute simplicité et en toute confiance à l’aide du bouton PayPal .

La variable [!DNL PayPal] est visible à partir de la page produit, du mini-panier, du panier et des vues de passage en caisse.

### [!DNL Venmo] button

Les clients peuvent extraire à l’aide de la variable [Venmo](https://venmo.com/) bouton .

La variable [!DNL Venmo] est visible à partir de la page produit, du mini-panier, du panier et des vues de passage en caisse.

### Bouton Débit PayPal ou Carte de crédit

Les clients peuvent régler leur paiement à l’aide du bouton Payer le débit ou la carte de crédit .

Le bouton Débit PayPal ou Carte de crédit est visible à partir de la page de passage en caisse.

Cette option peut être utilisée pour proposer une option de paiement par carte de crédit ou de débit à vos acheteurs avec un bouton hébergé par PayPal comme alternative à une intégration par carte de crédit.

### [!DNL Pay Later] button

Offrez à vos clients des paiements à court terme sans intérêts et d’autres options de financement afin qu’ils puissent acheter maintenant et payer ultérieurement avec le [!DNL Pay Later] bouton .

La variable [!DNL Pay Later] est visible à partir de la page produit, du mini-panier, du panier et des vues de passage en caisse.

Consultez les informations sur les offres Payer plus tard dans [Documentation sur les offres PayPal plus tard](https://developer.paypal.com/docs/checkout/pay-later/us/). Utilisez la variable **Pays ou région** pour sélectionner une région intéressante.

Voir [Paramètres](settings.md#payment-buttons) pour savoir comment désactiver/activer le [!DNL Pay Later] messages.

## Utiliser uniquement les boutons de paiement PayPal

Pour passer rapidement votre magasin en mode de production, vous pouvez configurer les _only_ Boutons de paiement PayPal (Venmo, PayPal, etc.): au lieu d’utiliser également l’option de paiement par carte de crédit PayPal .

Vous pouvez ainsi :

* Fournissez diverses options de paiement à vos clients, notamment des boutons de paiement Venmo et PayPal, avec la possibilité de désactiver les champs de carte hébergée PayPal et d’utiliser un fournisseur de carte de crédit existant.
* Utilisez votre fournisseur de carte de crédit existant pour les paiements par carte de crédit, tout en utilisant également les autres options de paiement de PayPal.
* Utilisez les boutons de paiement de PayPal dans une région où PayPal ne prend pas en charge les cartes de crédit comme option de paiement.

À **capture des paiements avec _only_ Boutons de paiement PayPal (_not_ l’option de paiement par carte de crédit PayPal)**:

1. Assurez-vous que votre boutique est [en mode de production](settings.md#enable-payment-services).
1. [Configuration des boutons de paiement PayPal de votre choix](settings.md#payment-buttons) dans Paramètres.
1. Tourner _Off_ la valeur **[[!UICONTROL Show PayPal Credit and Debit card button]](settings.md#payment-buttons)** dans le _[!UICONTROL Payment buttons]_.

À **capture des paiements avec votre fournisseur de carte de crédit existant _et_ Boutons de paiement PayPal**:

1. Assurez-vous que votre boutique est [en mode de production](settings.md#enable-payment-services).
1. [Configuration des boutons de paiement PayPal de votre choix](settings.md#payment-buttons).
1. Tourner _Off_ la valeur **[[!UICONTROL PayPal Show Credit and Debit card button]](settings.md#payment-buttons)** dans le _[!UICONTROL Payment buttons]_.
1. Tourner _Off_ la valeur **[[!UICONTROL Show on checkout page]](settings.md#credit-card-fields)** dans le _[!UICONTROL Credit card fields]_et utilisez vos [compte fournisseur de carte de crédit existant](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/payments/payments.html#payments).

## recalcul de la commande

Lorsqu’un client entre dans le flux de passage en caisse à partir du mini-panier, du panier ou de la page du produit, il est dirigé vers une page de vérification de la commande où il peut voir l’adresse de livraison sélectionnée dans une fenêtre contextuelle PayPal. Une fois que le client a sélectionné le mode de livraison, le montant de la commande est correctement recalculé et le client peut voir les frais de livraison et les taxes.

Lorsqu’un client entre dans le flux de passage en caisse à partir de la page de passage en caisse, le système connaît déjà l’adresse de livraison et le montant calculé final, et les totaux sont correctement représentés.

Les jours fériés, les frais de livraison et les taxes de vente peuvent varier considérablement d&#39;un lieu à l&#39;autre. Après [!DNL Payment Services] reçoit l&#39;adresse et le prix de livraison, il recalcule rapidement tous les coûts applicables et les affiche correctement lors des dernières étapes de la commande.

## Valorisation des cartes de crédit

Les acheteurs peuvent sauvegarder (ou &quot;enregistrer&quot;) leurs informations de carte de crédit pour les achats futurs au niveau du site web (tout magasin dans le même compte du commerçant).

Voir [Valorisation des cartes de crédit](vaulting.md) pour plus d’informations.

## Sécurité

Voir [Conformité PCI](security.md#pci-compliance) pour plus d’informations.
