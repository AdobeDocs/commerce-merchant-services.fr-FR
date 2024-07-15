---
title: Remboursement
description: Créez des remboursements pour  [!DNL Payment Services] commandes dans l’Admin dans le cadre du processus d’avis de crédit.
exl-id: 2b3721a1-9c9d-4e3f-ab7d-5bd61573dcb4
feature: Payments, Checkout
source-git-commit: 90bfa7099924feb308397960cff76bdf177bbe49
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 0%

---

# Remboursement

Les remboursements pour [!DNL Payment Services] commandes sont créés dans l’administrateur dans le cadre du processus de notation de crédit. Un avis de crédit est un document qui indique le montant dû au client, pour un remboursement complet ou partiel, qui peut être appliqué à un achat ou remboursé directement au client. Les notes de crédit ne peuvent être émises que pour les commandes [facturées](https://docs.magento.com/user-guide/sales/invoice-create.html){target="_blank"}.

Pour plus d’informations et pour savoir comment émettre et imprimer des notes de crédit, consultez la section [Mises de crédit](https://docs.magento.com/user-guide/sales/credit-memos.html){target="_blank"} de notre guide d’utilisation principal.

Pour les commandes traitées avec PayPal ou une carte de crédit, vous pouvez :

* Remboursement de la commande
* Remboursement d’un montant partiel d’une commande (ou de plusieurs montants partiels)
* Rembourser un montant inférieur à la valeur d’un article de commande spécifique

Pour plus d’informations, consultez la section [Émission d’un avoir](https://docs.magento.com/user-guide/sales/credit-memo-create.html){target="_blank"} de notre guide d’utilisation principal.

>[!NOTE]
>
>Une erreur se produit pour PayPal ou les commandes traitées par carte de crédit si vous tentez de partiellement rembourser une commande pour plus que le montant restant de la commande (montant original moins le total des remboursements existants), ou si vous effectuez un remboursement pour un montant supérieur au montant total de la commande.

Le paramètre [!UICONTROL Payment Action] de votre configuration [!UICONTROL Payment Settings], `Authorize` ou `Authorize and Capture`, détermine le [processus de remboursement de base](https://docs.magento.com/user-guide/sales/credit-memos.html#refund-workflow){target="_blank"} pour les commandes.

Pour plus d’informations, consultez la [section Paramètre d’action de paiement](https://docs.magento.com/user-guide/sales/credit-memo-create.html#payment-action-setting){target="_blank"} de _Emission d’un avoir_.
