---
title: Valorisation des cartes de crédit
description: Les acheteurs peuvent sauvegarder (enregistrer) les détails de leur carte de crédit pour les achats futurs.
exl-id: b4060307-ffcd-41cb-9b9d-a2fef02f23bd
feature: Payments, Checkout
source-git-commit: 37380063242b6d904910be731b8e58471625e9cb
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# Valorisation des cartes de crédit

Convertissez des clients ponctuels en clients fidèles avec des achats par carte de crédit en chambre forte. Les acheteurs peuvent enregistrer (ou &quot;coffre&quot;) leurs informations d’identification de carte de crédit au cours du passage en caisse afin de les utiliser dans un achat ultérieur pour le même magasin, ou un autre, dans le même compte marchand.

![ Vault leur carte de crédit pour une utilisation ultérieure ](assets/save-card-for-later.png){width="400" zoomable="yes"}

Les acheteurs utilisent le jeton stocké pour effectuer un passage en caisse ultérieur avec les informations de carte de crédit enregistrées.

![Utiliser les informations d’identification stockées pour un achat ultérieur](assets/use-stored-card.png){width="400" zoomable="yes"}

Ils peuvent également facilement supprimer leurs cartes de crédit en coffre de [méthodes de paiement stockées](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/payments/stored-payment-methods) dans leur compte.

![Méthodes de paiement stockées dans mon compte](assets/stored-payment-methods.png){width="400" zoomable="yes"}

>[!WARNING]
>
>PayPal peut actuellement stocker un maximum de cinq cartes en coffre-fort.

## Activation de la mise en valeur

Vous pouvez activer la valeur de carte de crédit (pour les clients _et_ marchands dans l&#39;administrateur) pour vos magasins dans [!DNL Payment Services] [Settings](settings.md#card-vaulting).

## Utilisation de la mise en garde dans l’administrateur

Si un client dispose d’une carte de crédit précédemment votée, un marchand peut créer une commande ultérieure pour ce client dans l’administrateur à l’aide de ses méthodes de paiement par défaut.

Vous ne pouvez utiliser des cartes en mémoire que si le client dispose à la fois d’un compte existant et d’un jeton valide stockés dans le système à partir d’un paiement précédemment effectué.

Pour créer une commande dans l’Admin pour un client à l’aide de sa carte de crédit voûtée :

1. [Créez une commande et ajoutez des produits](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/assist/customer-account-create-order.html).
1. Dans _[!UICONTROL Payment & Shipping Information]_, sélectionnez **[!UICONTROL Stored Cards]**comme méthode de paiement.
1. Sélectionnez le mode de paiement par carte de crédit voûtée de votre choix.
1. Après avoir effectué toute autre étape nécessaire pour la commande, [envoyez-la](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/assist/customer-account-create-order.html?lang=en#step-3%3A-submit-the-order).

   ![Utiliser la carte de crédit en coffre-fort dans Admin pour le client](assets/admin-vaultedcard.png){width="600" zoomable="yes"}

## Sécurité

Les informations minimales relatives aux cartes de crédit sont partagées avec l’acheteur ; il ne voit que les quatre derniers chiffres, la date d’expiration et la marque de sa carte de crédit votée. Les informations de carte de crédit sont stockées avec le fournisseur de paiement pour répondre aux normes de conformité [PCI](security.md#PCI-compliance).
