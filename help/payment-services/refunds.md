---
title: Remboursement
description: Créer des remboursements pour [!DNL Payment Services] commandes dans l’administrateur dans le cadre du processus d’avis de crédit.
exl-id: 2b3721a1-9c9d-4e3f-ab7d-5bd61573dcb4
feature: Payments, Checkout
source-git-commit: 90bfa7099924feb308397960cff76bdf177bbe49
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 0%

---

# Remboursement

Remboursements pour [!DNL Payment Services] les commandes sont créées dans l’administrateur dans le cadre du processus de notation de crédit. Un avis de crédit est un document qui indique le montant dû au client, pour un remboursement complet ou partiel, qui peut être appliqué à un achat ou remboursé directement au client. Les notes de crédit ne peuvent être émises que pour les commandes qui sont [facturée](https://docs.magento.com/user-guide/sales/invoice-create.html){target="_blank"}.

Voir [Avoir](https://docs.magento.com/user-guide/sales/credit-memos.html){target="_blank"} dans notre guide d’utilisation principal pour plus d’informations et pour savoir comment émettre et imprimer des notes de crédit.

Pour les commandes traitées avec PayPal ou une carte de crédit, vous pouvez :

* Remboursement de la commande
* Remboursement d’un montant partiel d’une commande (ou de plusieurs montants partiels)
* Rembourser un montant inférieur à la valeur d’un article de commande spécifique

Voir [Émission d’une note de crédit](https://docs.magento.com/user-guide/sales/credit-memo-create.html){target="_blank"} pour plus d’informations.

>[!NOTE]
>
>Une erreur se produit pour PayPal ou les commandes traitées par carte de crédit si vous tentez de partiellement rembourser une commande pour plus que le montant restant de la commande (montant original moins le total des remboursements existants), ou si vous effectuez un remboursement pour un montant supérieur au montant total de la commande.

La variable [!UICONTROL Payment Action] dans votre [!UICONTROL Payment Settings] configuration : soit `Authorize` ou `Authorize and Capture`: détermine la variable [workflow de remboursement de base](https://docs.magento.com/user-guide/sales/credit-memos.html#refund-workflow){target="_blank"} pour les commandes.

Voir [Section de paramétrage des actions de paiement](https://docs.magento.com/user-guide/sales/credit-memo-create.html#payment-action-setting){target="_blank"} de _Émission d’une note de crédit_ pour plus d’informations.
