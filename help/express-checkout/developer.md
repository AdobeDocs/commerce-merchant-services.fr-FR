---
title: '''[!DNL Express Checkout] pour les informations sur les développeurs Adobe Commerce"'
description: '''[!DNL Express Checkout] informations sur les développeurs.'''
exl-id: 8926eda4-b4de-4938-a86c-b095616f61f6
source-git-commit: 1a7df2c5581ea6d590aa1a2f701b4428371d2299
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 0%

---

# [!DNL Express Checkout] informations sur les développeurs

>[!IMPORTANT]
>
> Cette fonctionnalité est réservée aux utilisateurs du Programme des Adopteurs Anticipés (EAP) et n’est pas encore accessible à tous les clients. Actuellement limitée aux clients américains. Contactez l’assistance d’Adobe Commerce pour toute question ou assistance.

Cette rubrique contient des informations destinées aux développeurs qui travaillent en étroite collaboration avec Adobe Commerce et le code du Magento Open Source et qui souhaitent en savoir plus sur les [!DNL Express Checkout] extension .

## Points d’extension

Utilisez des points d’extension pour personnaliser la variable [!DNL Express Checkout].

En utilisant des points d’extension, vous pouvez effectuer des personnalisations sans modifier les composants principaux dans le code de l’application.

### Etape Détails de l&#39;expédition

Un point d’extension peut être utilisé pour personnaliser la navigation de l’étape automatisée après connexion avec [!DNL Bolt].

Une fois qu’un acheteur se connecte avec [!DNL Bolt], toutes les informations valides sont préremplies et redirigées vers l’étape des détails du paiement pour passer la commande. Voir [flux de passage en caisse](https://experienceleague.adobe.com/docs/commerce-merchant-services/express-checkout/manage-checkout/checkout-flow.html) pour plus d’informations.

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
