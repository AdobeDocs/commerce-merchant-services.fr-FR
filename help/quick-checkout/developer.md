---
title: "[!DNL Quick Checkout] pour les informations sur les développeurs Adobe Commerce"
description: "[!DNL Quick Checkout] informations sur les développeurs."
exl-id: 8926eda4-b4de-4938-a86c-b095616f61f6
feature: Checkout, Services
role: Developer
source-git-commit: b1984a26463e14b8dc9a789421e49e5ea81ad039
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---

# [!DNL Quick Checkout] Informations sur les développeurs

Cette rubrique contient des informations destinées aux développeurs qui travaillent en étroite collaboration avec Adobe Commerce et [!DNL Magento Open Source] et souhaitez en savoir plus sur les [!DNL Quick Checkout] extension .

## Points d’extension

Utilisez des points d’extension pour personnaliser la variable [!DNL Quick Checkout].

En utilisant des points d’extension, vous pouvez effectuer des personnalisations sans modifier les composants principaux dans le code de l’application.

## Etape Détails de l&#39;expédition

Un point d’extension peut être utilisé pour personnaliser la navigation de l’étape automatisée après connexion avec [!DNL Bolt].

Une fois qu’un acheteur se connecte avec [!DNL Bolt], toutes les informations valides sont préremplies et redirigées vers l’étape des détails du paiement pour passer la commande. Voir [flux de passage en caisse](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/manage-checkout/checkout-flow.html) pour plus d’informations.

Ce point d’extension permet d’empêcher la navigation vers une étape de paiement et peut s’avérer utile en cas d’extensions qui nécessitent qu’un acheteur effectue des actions supplémentaires sur l’étape d’expédition. Consultez un exemple ci-dessous sur l’utilisation du point d’extension avec un mixin :

1. Enregistrement d’un nouveau mixin dans `require-config.js` fichier situé dans `app/code/Vendor/ModuleName/view/frontend/`.

   ```js
   var config = {
       config: {
           mixins: {
               "Magento_ExpressCheckout/js/model/can-navigate-to-payment": {
                   "Vendor/ModuleName/js/model/can-navigate-to-payment-mixin": true
               }
           }
       }
   };
   ```

1. Étendez le modèle dans le `can-navigate-to-payment.js` fichier situé dans `app/code/Vendor/ModuleName/view/frontend/web/js/model/`.

   ```js
   define([
       'Magento_Checkout/js/model/quote',
       'mage/utils/wrapper',
   ], function (quote, wrapper) {
       'use strict';
       return function (canNavigateToPayment) {
           return wrapper.wrap(canNavigateToPayment, function (originalAction) {
               /* Include custom checks or conditions to stay on the shipping step,i.e: your shopper is from Germany */
               return originalAction() && quote.shippingAddress().countryId !== 'DE');
           });
       };
   });
   ```

>[!WARNING]
>
> Voici un exemple pour un acheteur en Allemagne (DE) qui souhaite rester à l’étape Détails de la livraison .

Vérifier [[!DNL Bolt] aide pour les développeurs](https://help.bolt.com/developers/) pour plus d’informations sur [!DNL Bolt] pour les développeurs.
