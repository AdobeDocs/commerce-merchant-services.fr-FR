---
title: Passage en caisse
description: Personnalisez le passage en caisse en fonction des besoins de votre client.
feature: Payments, Checkout
source-git-commit: 6ba5a283d9138b4c1be11b80486826304c63247f
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%

---


# Passage en caisse

Vous pouvez configurer le passage en caisse pour Adobe Commerce [!DNL Payment Services] pour mieux convenir à vos acheteurs. Fonctionnalités telles que [validation automatique de commande](#order-auto-voided-if-error) et [coffre-fort à carte de crédit](#credit-card-vaulting) assurez-vous que vos acheteurs bénéficient d’une expérience utilisateur fluide.

## Commande auto-annulée en cas d’erreur

Si une erreur se produit lors de l’extraction, [!DNL Payment Services] annule/annule automatiquement la commande.

Un message d’erreur s’affiche sur la page de passage en caisse de l’acheteur. Le message peut varier.

![Erreur lors de la vérification](assets/user-checkout-error.png "Erreur lors de l’extraction"){width="600" zoomable="yes"}

Un commentaire sur la commande annulée s’affiche également dans l’onglet Admin pour un [order](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/orders.html?lang=en).

![Annulation du commentaire de commande dans Admin pour commande](assets/admin-checkout-error.png "Annulation du commentaire de commande dans Admin pour commande"){width="600" zoomable="yes"}

Si un acheteur obtient l’autorisation d’une commande, mais que celle-ci n’a pas été créée et convertie en `Capture`, la commande est automatiquement annulée. Ce processus garantit qu’aucun crédit n’est réservé sur la carte de crédit de l’acheteur et évite les frais du fournisseur de paiement qui surviennent lorsque l’autorisation est annulée à la fin de la période standard de 29 jours.

>[!NOTE]
>
>L’annulation automatique de la commande ne se produit que lorsque le client utilise un mode de paiement défini sur `Authorize` mode, pas `Authorize and Capture` mode .

## Passage en caisse à partir de la page du produit

Lorsqu’un client extrait directement de la page du produit, à l’aide de PayPal ou [!DNL Pay Later] , seul l’article représenté sur la page produit active est acheté. Les éléments qui résident déjà dans le panier du client ne sont pas ajoutés au flux de passage en caisse et ne sont pas achetés.

Cette fonction permet au client d’acheter rapidement l’article qu’il consulte actuellement, tout en conservant les articles précédemment ajoutés à son panier.
Si le client annule la commande, l’article figurant dans la page du produit en cours est ajouté au panier du client.

Lorsqu’un client entre dans le flux de passage en caisse à partir de la page du produit, la page de passage en caisse est simplifiée ; la vue affiche uniquement les données et les options liées à la commande.

## Valorisation des cartes de crédit

Les acheteurs peuvent sauvegarder (ou &quot;enregistrer&quot;) leurs informations de carte de crédit pour les achats futurs au niveau du site web (tout magasin dans le même compte du commerçant).

Voir [Valorisation des cartes de crédit](vaulting.md) pour plus d’informations
