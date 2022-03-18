---
title: Remboursement
description: Créer des remboursements pour [!DNL Payment Services] commandes dans l’administrateur dans le cadre du processus d’avis de crédit.
exl-id: 2b3721a1-9c9d-4e3f-ab7d-5bd61573dcb4
source-git-commit: fd818dadbaa2a58efd7313ce888c7dda27d25f14
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---

# Remboursement

Remboursements pour [!DNL Payment Services] les commandes sont créées dans l’administrateur dans le cadre du processus de notation de crédit. Un avis de crédit est un document qui indique le montant dû au client, pour un remboursement complet ou partiel, qui peut être appliqué à un achat ou remboursé directement au client. Les notes de crédit ne peuvent être émises que pour les commandes qui sont [facturée](https://docs.magento.com/user-guide/sales/invoice-create.html){target=&quot;_blank&quot;}.

Voir [Avoir](https://docs.magento.com/user-guide/sales/credit-memos.html){target=&quot;_blank&quot;} dans notre guide d’utilisation principal pour plus d’informations et pour apprendre à émettre et à imprimer des notes de crédit.

Pour les commandes traitées avec PayPal ou une carte de crédit, vous pouvez :

* Remboursement de la commande
* Remboursement d’un montant partiel d’une commande (ou de plusieurs montants partiels)
* Rembourser un montant inférieur à la valeur d’un article de commande spécifique

Voir [Émission d’un avoir](https://docs.magento.com/user-guide/sales/credit-memo-create.html){target=&quot;_blank&quot;} dans notre guide d’utilisation principal pour plus d’informations.

>[!NOTE]
>
>Une erreur se produit pour PayPal ou les commandes traitées par carte de crédit si vous tentez de partiellement rembourser une commande pour plus que le montant restant de la commande (montant original moins le total des remboursements existants), ou si vous effectuez un remboursement pour un montant supérieur au montant total de la commande.

Le [!UICONTROL Payment Action] dans votre [!UICONTROL Payment Settings] configuration : soit `Authorize` ou `Authorize and Capture`: détermine la variable [workflow de remboursement de base](https://docs.magento.com/user-guide/sales/credit-memos.html#refund-workflow){target=&quot;_blank&quot;} pour les commandes.

Voir [Section de paramétrage des actions de paiement](https://docs.magento.com/user-guide/sales/credit-memo-create.html#payment-action-setting){target=&quot;_blank&quot;} de _Émission d’un avoir_ pour plus d’informations.
