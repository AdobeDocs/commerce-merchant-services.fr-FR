---
title: Données disponibles
description: Utilisez les données de reporting financier pour réconcilier les rapports avec les systèmes autres que Commerce.
role: User
level: Intermediate
exl-id: dbf41ce9-01f9-45d0-b651-e4c499e83822
feature: Payments, Checkout, Data Import/Export
source-git-commit: 6ba5a283d9138b4c1be11b80486826304c63247f
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 0%

---

# Données disponibles

Vous disposez de certaines données de commande et de paiement afin de pouvoir coordonner les rapports financiers Adobe Commerce sur les systèmes externes.

## Réconcilier avec le système ERP

Vous pouvez réconcilier le reporting financier d’Adobe Commerce avec votre système ERP (Enterprise Resource Planning) autre qu’Adobe à l’aide de l’identifiant d’incrément associé à une commande spécifique.

Lorsque les services de paiement envoient la commande Commerce à PayPal, l’ID d’incrément est inclus en tant que `custom_id` _et_ dans le `invoice_id` (qui contient également une chaîne aléatoire après l’événement `increment_id`).

Les identifiants sont facilement accessibles dans les détails de l’activité commerciale pour un paiement et dans le webhook PayPal.

La variable `invoice_id` et `custom_id` s’affichent près du bas du détail de l’activité commerciale pour un paiement :

![`custom_id` dans le détail de l’activité commerciale](assets/merchant-activity-ids.png){width="600" zoomable="yes"}

`custom_id` et `invoice_id` dans les détails du webhook de PayPal :

```json
   ...
   {
    "id": "4E855005GK253170H",
    "intent": "AUTHORIZE",
    "status": "COMPLETED",
    "payment_source": {
        ...
    },
    "purchase_units": [
        {
            ...
            "custom_id": "000001322",
            "invoice_id": "000001322-c01bd7c3-920f-4542-a900-738082177e92",
            ...
            "payments": {
                "authorizations": [
                    {
                       ...
                        "invoice_id": "000001322-c01bd7c3-920f-4542-a900-738082177e92",
                        "custom_id": "000001322",
                        ...
                    }
                ],
                "captures": [
                    {
                        ...
                        "invoice_id": "000001322-c01bd7c3-920f-4542-a900-738082177e92",
                        "custom_id": "000001322",
                        ...
                    }
                ]
            }
        }
    ],
    "payer": {
        ...
    },
    "create_time": "2022-09-12T14:59:01Z",
    "update_time": "2022-09-12T14:59:45Z",
    "links": [
        ...
    ]
}
   ...
```

Pour plus d’informations, consultez la documentation sur les API REST de PayPal :

* [`purchase_unit`, dans laquelle `custom_id` et `invoice_id` résider](https://developer.paypal.com/docs/api/orders/v2/#definition-purchase_unit:~:text=Read%20only.-,purchase_unit,-Réduire)
* [Afficher les détails de commande](https://developer.paypal.com/docs/api/orders/v2/#orders_get)
