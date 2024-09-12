---
title: Passage en caisse dans [!DNL Payment Services]
description: Personnalisez  [!DNL Payment Services] le passage en caisse pour répondre aux besoins de votre client.
feature: Payments, Checkout
exl-id: 47df165f-2145-4e0e-b272-54b8e768cf19
source-git-commit: 153e6a82134a34737529f4e1a135eb7803b20e05
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---


# Passage en caisse dans [!DNL Payment Services]

Vous pouvez configurer le passage en caisse pour Adobe Commerce [!DNL Payment Services] en fonction de vos acheteurs. Des fonctionnalités telles que le [remplacement automatique de commande](#order-auto-voided-if-error) et la [ résolution de carte de crédit](#credit-card-vaulting) garantissent que vos clients bénéficient d’une expérience utilisateur fluide.

## Commande auto-annulée en cas d’erreur

Si une erreur se produit lors du passage en caisse, [!DNL Payment Services] annule/annule automatiquement la commande.

Un message d’erreur s’affiche sur la page de passage en caisse de l’acheteur. Le message peut varier.

![Erreur lors de la vérification](assets/user-checkout-error.png "Erreur lors de la vérification"){width="600" zoomable="yes"}

Un commentaire concernant la commande annulée s’affiche également dans l’administrateur pour une [commande](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/orders.html?lang=en) spécifique.

![Annulation du commentaire de commande dans Admin for order](assets/admin-checkout-error.png "Annulation du commentaire de commande dans Admin for order"){width="600" zoomable="yes"}

Si un acheteur obtient l’autorisation pour une commande, mais que la commande n’a pas été créée et convertie en `Capture`, la commande est automatiquement annulée. Ce processus garantit qu’aucun crédit n’est réservé sur la carte de crédit de l’acheteur et évite les frais du fournisseur de paiement qui surviennent lorsque l’autorisation est annulée à la fin de la période standard de 29 jours.

>[!NOTE]
>
>Le vidage automatique des commandes ne se produit que lorsque le client utilise un mode de paiement défini sur le mode `Authorize` et non le mode `Authorize and Capture`.

## Passage en caisse à partir de la page du produit

Lorsqu’un client extrait directement de la page du produit à l’aide des boutons PayPal ou [!DNL Pay Later] , seul l’article représenté sur la page du produit en cours est acheté. Les éléments qui résident déjà dans le panier du client ne sont pas ajoutés au flux de passage en caisse et ne sont pas achetés.

Cette fonction permet au client d’acheter rapidement l’article qu’il consulte actuellement, tout en conservant les articles précédemment ajoutés à son panier.
Si le client annule la commande, l’article figurant dans la page du produit en cours est ajouté au panier du client.

Lorsqu’un client entre dans le flux de passage en caisse à partir de la page du produit, la page de passage en caisse est simplifiée ; la vue affiche uniquement les données et les options liées à la commande.

## Valorisation des cartes de crédit

Les acheteurs peuvent sauvegarder (ou &quot;enregistrer&quot;) leurs informations de carte de crédit pour les achats futurs au niveau du site web (tout magasin dans le même compte du commerçant).

Pour plus d’informations, voir [Validage par carte de crédit](vaulting.md)
