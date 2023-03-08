---
title: Options de paiement
description: Définissez les options de paiement pour personnaliser les méthodes disponibles pour les clients de votre magasin.
exl-id: 95e648e6-6cb8-4226-b5ea-e1857212f20a
source-git-commit: 31665f90909ce2364579fc7f9c97087e2376c0a6
workflow-type: tm+mt
source-wordcount: '1003'
ht-degree: 0%

---

# Options de paiement

Avec [!DNL Adobe Commerce] et [!DNL Magento Open Source] [!DNL Payment Services], plusieurs options de paiement sont à votre disposition. Vous pouvez configurer ces options de paiement en procédant comme suit :

* [Paramètres d’accueil](payments-home.md)
* [Configuration du magasin](configure-admin.md) (recommandé pour les options de paiement héritées ou une configuration multi-magasin)

Il existe différents comportements pour chaque mode de paiement en fonction de l’endroit où vous vous trouvez dans le processus de passage en caisse :

* Page de produit : page de produit d’un article.
* Mini panier : disponible en un clic sur l’icône de panier lorsqu’un produit a été ajouté au panier.
* Panier : disponible en un clic de _Afficher et modifier le panier_ du mini-panier
* Mode Extraction : disponible en un clic de _Passez à la Passage en caisse ._ à partir d’un mini-panier ou d’un panier

>[!IMPORTANT]
>
>L’intégration des services de paiement doit être effectuée avant que les paiements puissent être traités.

## [!UICONTROL Credit Card Fields]

[!UICONTROL Credit Card Fields] proposer un passage en caisse simple et sécurisé pour les modes de paiement par carte de crédit ou carte de débit ; Lorsqu’un acheteur passe en caisse en utilisant des champs de carte de crédit, il saisit son nom, son adresse de facturation et les informations de carte de crédit ou de débit pour passer sa commande. Les informations sur les clients sont utilisées de manière sécurisée au cours de la session d’achat pour les guider de manière transparente tout au long du flux de passage en caisse.

Activer [coffre-fort à carte de crédit](#vaulting) pour que vos magasins permettent aux clients de sauvegarder (enregistrer) leurs informations de carte de crédit pour un passage en caisse rapide plus tard.

Vous pouvez configurer [!UICONTROL Credit Card Fields] dans la configuration du magasin ou dans la page d’accueil des services de paiement. Voir [Paramètres](settings.md#credit-card-fields) pour plus d’informations.

## [!DNL PayPal Smart Buttons]

[!DNL PayPal Smart Buttons], qui utilise PayPal pour effectuer un achat, stocke l’adresse de livraison de votre acheteur, les adresses de facturation et les détails de paiement en vue d’une utilisation ultérieure. Les acheteurs peuvent utiliser n&#39;importe quel mode de paiement précédemment stocké ou proposé par PayPal.

![[!DNL PayPal Smart Buttons] options](assets/buttons-md.png)

Vous pouvez configurer [!UICONTROL PayPal Smart Buttons] dans la configuration du magasin ou dans la page d’accueil des services de paiement.  Voir [Paramètres](settings.md#payment-buttons) pour plus d’informations.

### [!DNL PayPal] button

Les clients peuvent effectuer leur paiement en toute simplicité et en toute confiance à l’aide du bouton PayPal .

Le [!DNL PayPal] est visible à partir de la page produit, du mini-panier, du panier et des vues de passage en caisse.

### [!DNL Venmo] button

Les clients peuvent extraire à l’aide de la variable [Venmo](https://venmo.com/) bouton .

Le [!DNL Venmo] est visible à partir de la page produit, du mini-panier, du panier et des vues de passage en caisse.

### [!DNL Apple Pay] button

Les clients peuvent utiliser des Touch ID sur leurs appareils. [[!DNL Apple Pay]](https://www.apple.com/apple-pay/), qui utilise les informations d’identification de paiement de carte de crédit et de débit stockées sur leur appareil iOS ou macOS.

Le [!DNL Apple Pay] est visible à partir de la page produit, du mini-panier, du panier et des vues de passage en caisse.

>[!NOTE]
>
> Pour utiliser Apple Pay, contactez votre représentant commercial ou votre équipe de compte d’Adobe afin de l’activer pour vos magasins actifs.

### [!DNL Pay Later] button

Offrez à vos clients des paiements à court terme sans intérêts et d’autres options de financement afin qu’ils puissent acheter maintenant et payer ultérieurement avec le [!DNL Pay Later] bouton .

Le [!DNL Pay Later] est visible à partir de la page produit, du mini-panier, du panier et des vues de passage en caisse :

* **Lorsqu’un client sélectionne un produit entre 30 et 600 $**, messagerie sous PayPal et [!DNL Pay Later] Les boutons donnent au client plus d’informations sur la variable [!DNL Pay in 4] option de paiement. Les clients peuvent cliquer sur **En savoir plus** pour en savoir plus sur le[!DNL Pay in 4]Option &quot; _ou_ cliquez sur le texte &quot;Ou voir 6 mois de financement spécial&quot; dans la fenêtre contextuelle pour en savoir plus et demander l’option Crédit PayPal .
* **Lorsqu’un client sélectionne un ou plusieurs produits dépassant 98,99 $**, messagerie sous PayPal et [!DNL Pay Later] Les boutons donnent aux clients plus d’informations sur l’option de paiement du crédit PayPal. Les clients peuvent cliquer sur **En savoir plus** pour en savoir plus sur l’option Crédit PayPal et faire une demande pour cette option, _ou_ cliquez sur le texte &quot;Ou voir Payer en 4&quot; dans la fenêtre contextuelle pour en savoir plus sur la variable [!DNL Pay in 4] .

   >[!NOTE]
   >
   >Les montants listés ci-dessus peuvent être modifiés.

Voir [Paramètres](settings.md#payment-buttons) pour savoir comment désactiver/activer le [!DNL Pay Later] messages.

Il existe deux options de paiement avec la variable [!DNL Pay Later] button :

* **Payer 4**: les clients peuvent payer leur solde de commande en quatre paiements sans intérêts (toutes les deux semaines) après un premier versement initial. Voir [Documentation paiement](https://www.paypal.com/us/digital-wallet/ways-to-pay/buy-now-pay-later) pour plus d’informations.
* **Crédit PayPal**: les clients peuvent payer leur solde de commande en intégralité sur une période de six mois, sans intérêts. Voir [Documentation sur le crédit PayPal](https://www.paypal.com/us/webapps/mpp/paypal-credit) pour plus d’informations.

### [!DNL Pay Now] button

Le [!DNL Pay Now] est visible dans la fenêtre contextuelle PayPal lorsqu’un client clique sur un bouton de paiement dans l’écran des paiements.

Si le montant final de la commande n’est pas encore connu (par exemple, lorsque vous ne disposez pas encore des informations sur l’adresse de livraison) et que le client est en train d’extraire de la page produit, du mini-panier ou du panier, une _Continuer_ est disponible à la place. Lorsqu’un client clique _Continuer_, une fois qu’ils ont confirmé leur mode de paiement, ils sont dirigés vers une page de vérification de commande afin de rassembler les détails nécessaires avant de terminer le passage en caisse.

## recalcul de la commande

Lorsqu’un client entre dans le flux de passage en caisse à partir du mini-panier, du panier ou de la page du produit, il est dirigé vers une page de vérification de la commande où il peut voir l’adresse de livraison sélectionnée dans une fenêtre contextuelle PayPal. Une fois que le client a sélectionné le mode de livraison, le montant de la commande est correctement recalculé et le client peut voir les frais de livraison et les taxes.

Lorsqu’un client entre dans le flux de passage en caisse à partir de la page de passage en caisse, le système connaît déjà l’adresse de livraison et le montant calculé final, et les totaux sont correctement représentés.

Les jours fériés, les frais de livraison et les taxes de vente peuvent varier considérablement d&#39;un lieu à l&#39;autre. Après [!DNL Payment Services] reçoit l&#39;adresse et le prix de livraison, il recalcule rapidement tous les coûts applicables et les affiche correctement lors des dernières étapes de la commande.

## Passage en caisse à partir de la page du produit

Lorsqu’un client extrait directement de la page du produit, à l’aide de PayPal ou [!DNL Pay Later] , seul l’article représenté dans la page produit active est acheté. Les articles qui figurent déjà dans le panier du client ne sont pas ajoutés au flux de passage en caisse et ne sont pas achetés.

Si le client annule la commande, l’article de la page du produit en cours est ajouté au panier du client, en y joignant tous les autres articles présents dans le panier. Cette fonction permet au client d’acheter rapidement l’article qu’il consulte actuellement, tout en conservant tous les autres articles qu’il a ajoutés à son panier antérieurement lors de la navigation dans les produits.

Lorsqu’un client entre dans le flux de passage en caisse à partir de la page du produit, la page de passage en caisse est simplifiée ; la vue affiche uniquement les données et les options liées à la commande.

## Valorisation des cartes de crédit

Les acheteurs peuvent sauvegarder (ou &quot;enregistrer&quot;) leurs informations de carte de crédit pour les achats futurs au niveau du site web (tout magasin dans le même compte du commerçant).

Voir [Valorisation des cartes de crédit](vaulting.md) pour plus d’informations.

## Sécurité

Voir [Conformité PCI](security.md#pci-compliance) pour plus d’informations.
