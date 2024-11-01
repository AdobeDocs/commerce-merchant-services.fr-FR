---
title: Voix
description: Les votes permettent de libérer les fonds dans un compte de carte de crédit ou de débit qui sont bloqués ou conservés par une autorisation pour le montant d’un achat.
exl-id: 029a7038-2812-46ce-b188-929a7a758d89
feature: Payments, Checkout
source-git-commit: 37380063242b6d904910be731b8e58471625e9cb
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 0%

---

# Voix

Avec [!DNL Payment Services], vous pouvez utiliser la fonctionnalité Commerce existante pour annuler les transactions. Les votes permettent de libérer les fonds dans un compte de carte de crédit ou de débit qui sont bloqués ou conservés par une autorisation pour le montant d’un achat.

>[!NOTE]
>
>Vous ne pouvez annuler une transaction que si le paiement n’est pas encore capturé.

Si votre boutique est [configurée](https://experienceleague.adobe.com/en/docs/commerce-admin/config/sales/payment-methods/payment-methods#payment-actions){target="_blank"} pour autoriser uniquement (et non pour capturer) des fonds au point de vente, un achat effectué sur votre boutique génère une commande avec le statut `Processing` dans l’administrateur Commerce.

Vous pouvez également [annuler une commande](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/point-of-purchase/assist/customer-account-create-order){target="_blank"} qui n’est pas facturée. Toutes les autorisations non capturées sont également annulées dans le cadre de ce processus d’annulation.

>[!NOTE]
>
>L’annulation d’une commande engendre également un vide, mais l’annulation d’une commande ne déclenche pas d’annulation.

Pour en savoir plus sur les étapes de base d’une commande, consultez la rubrique [Workflow de commande](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/orders/order-processing){target="_blank"} du guide de l’utilisateur principal.

Pour en savoir plus sur la fonctionnalité d’annulation et sur la façon d’annuler une transaction de commande, voir [Traitement d’une commande](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/orders/order-processing#process-an-order){target="_blank"} dans le guide d’utilisation principal.
