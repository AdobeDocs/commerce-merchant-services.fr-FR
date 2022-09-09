---
title: Données disponibles
description: Utilisez les données de reporting financier pour réconcilier les rapports avec les systèmes autres que Commerce.
role: User
level: Intermediate
source-git-commit: 1186b4e52f1d613332a7862c58f482c2591e29a8
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---

# Données disponibles

Vous disposez de certaines données de commande et de paiement afin de pouvoir coordonner les rapports financiers Adobe Commerce sur les systèmes externes.

## Réconcilier avec le système ERP

Vous pouvez réconcilier le reporting financier d’Adobe Commerce avec votre système ERP (Enterprise Resource Planning) autre qu’Adobe à l’aide de l’identifiant d’incrément associé à une commande spécifique.

Lorsque les services de paiement envoient la commande Commerce à PayPal, l’ID d’incrément est inclus en tant que `custom_id`. Le `custom_id` est visible dans les détails de l’activité commerciale pour un paiement et dans le webhook PayPal.

`custom_id` au bas du détail de l’activité commerciale pour un paiement :

![`custom_id` dans le détail de l’activité commerciale](assets/merchant-activity.png)

`custom_id` dans les détails du webhook de PayPal :

```json
   ...
   },
   "seller_protection": {
   "status": "NOT_ELIGIBLE"
   },
   "create_time": "2022-08-28T21:06:53Z",
   "custom_id": "000000829",
   "supplementary_data": {
   "related_ids":

   { "authorization_id": "6WW957787A749904A", "order_id": "3SV13726F9525791J" }
   },
   ...
```

Pour plus d’informations, consultez la documentation sur les API REST de PayPal :

* [`purchase_unit` dans lequel `custom_id` réside](https://developer.paypal.com/docs/api/orders/v2/#definition-purchase_unit:~:text=Read%20only.-,purchase_unit,-Réduire)
* [Afficher les détails de commande](https://developer.paypal.com/docs/api/orders/v2/#orders_get)
