---
title: Suivi de vos envois dans  [!DNL Payment Services]
description: Personnalisez les  [!DNL Payment Services] envois et les informations de suivi affichées dans le tableau de bord du marchand de paypal.
feature: Payments
source-git-commit: 153e6a82134a34737529f4e1a135eb7803b20e05
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 0%

---


# Tracking de vos envois dans [!DNL Payment Services]

[!DNL Payment Services] permet aux commerçants de voir les informations de suivi d’une expédition dans leur tableau de bord marchand PayPal.

Pour plus d’informations sur la grille des envois pour Adobe Commerce, voir la rubrique [chargements](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/shipments){target=_blank} .

## Fonctionnement du tracking de votre envoi

Cette fonctionnalité dépend de la facturation ou non de la commande, car PayPal doit recevoir un `capture_id` pour traiter les informations de suivi. Si un commerçant envoie ses produits avant la capture, les informations de suivi ne sont pas envoyées à PayPal.

>[!NOTE]
>
> Il est recommandé de créer une expédition par numéro de suivi, en associant les éléments appropriés à l’expédition.

## Ajouter le numéro de tracking

Les instructions suivantes vous guident tout au long du processus de création d’une expédition dans Adobe Commerce avec [!DNL Payment Services] :

1. Sur la barre latérale _Admin_, accédez à **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.

1. Dans la colonne **[!UICONTROL Action]** de l&#39;ordre sélectionné, cliquez sur **[!UICONTROL View]**.

1. Cliquez sur **[!UICONTROL Ship]**.

1. Faites défiler l’écran jusqu’au bloc **[!UICONTROL Payment & Shipping Method]** et cliquez sur **[!UICONTROL Add Tracking Number]** dans **[!UICONTROL Shipping Information]**.

1. Définissez le **[!UICONTROL Carrier]**.

1. Pour tracker l&#39;envoi, saisissez les valeurs **[!UICONTROL Title]** et **[!UICONTROL Number]** .

1. Cliquez sur **[!UICONTROL Submit Shipment]**.

>[!NOTE]
>
> Vous pouvez également utiliser un module d’expédition pour saisir les informations de numéro de suivi. Assurez-vous que le module d’expédition enregistre les informations de numéro de suivi dans le champ `tracking_number` .

### Compatibilité avec des tiers

Toute extension tierce est compatible avec la fonctionnalité lorsqu’une entité d’expédition est créée via [l’API Commerce](https://developer.adobe.com/commerce/webapi/rest/attributes/#magentosalesapishipmentrepositoryinterface-shipmentrepositoryinterface){target=_blank}.
