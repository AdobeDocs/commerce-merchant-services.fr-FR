---
title: Voix
description: Les votes permettent de libérer les fonds dans un compte de carte de crédit ou de débit qui sont bloqués ou conservés par une autorisation pour le montant d’un achat.
exl-id: 029a7038-2812-46ce-b188-929a7a758d89
feature: Payments, Checkout
source-git-commit: 90bfa7099924feb308397960cff76bdf177bbe49
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 0%

---

# Voix

Avec [!DNL Payment Services], vous pouvez utiliser la fonctionnalité Commerce existante pour annuler les transactions. Les votes permettent de libérer les fonds dans un compte de carte de crédit ou de débit qui sont bloqués ou conservés par une autorisation pour le montant d’un achat.

>[!NOTE]
>
>Vous ne pouvez annuler une transaction que si le paiement n’est pas encore capturé.

Si votre boutique est [configurée](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target="_blank"} pour autoriser uniquement (et non pour capturer) des fonds au point de vente, un achat effectué sur votre boutique génère une commande avec le statut `Processing` dans l’administrateur Commerce.

Vous pouvez également [annuler une commande](https://docs.magento.com/user-guide/sales/order-update.html#cancel-a-pending-order){target="_blank"} qui n’est pas facturée. Toutes les autorisations non capturées sont également annulées dans le cadre de ce processus d’annulation.

>[!NOTE]
>
>L’annulation d’une commande engendre également un vide, mais l’annulation d’une commande ne déclenche pas d’annulation.

Pour en savoir plus sur les étapes de base d’une commande, consultez la rubrique [Workflow de commande](https://docs.magento.com/user-guide/sales/order-workflow.html){target="_blank"} du guide de l’utilisateur principal.

Pour en savoir plus sur la fonctionnalité d’annulation et sur la façon d’annuler une transaction de commande, voir [Traitement d’une commande](https://docs.magento.com/user-guide/sales/order-processing.html){target="_blank"} dans le guide d’utilisation principal.
