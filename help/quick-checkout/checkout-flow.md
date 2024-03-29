---
title: "Flux de passage en caisse dans Adobe Commerce"
description: "Présentation de la variable [!DNL Quick Checkout] flux dans Adobe Commerce."
exl-id: 82761627-a0d4-4cb0-aad1-9865fcb550d4
feature: Checkout, Services, Storefront
source-git-commit: 6ba5a283d9138b4c1be11b80486826304c63247f
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 0%

---

# [!DNL Quick Checkout] Flux

Cette section présente un aperçu de l’expérience de passage en caisse classique à l’aide de la méthode [!DNL Quick Checkout] pour l’extension Adobe Commerce.

Une réussite [!DNL Quick Checkout] Le flux se compose des étapes suivantes :

1. Ouvrez votre storefront et ajoutez des éléments dans votre panier.
1. Passez à la caisse.

![Passage en caisse](assets/proceed-checkout.png){width="200" zoomable="yes"}

>[!NOTE]
>
> Vous pouvez activer la connexion automatique pour votre commerçant. Voir [Rubrique Activer la connexion automatique de la balise](https://help.bolt.com/products/embedded/direct-api/auto-login/) pour plus d’informations.

1. Lorsque vous y êtes invité, saisissez une adresse électronique associée à un événement [!DNL Bolt] compte .
1. Saisissez le mot de passe unique (OTP) envoyé à cette fin. [!DNL Bolt] adresse électronique ou numéro de téléphone du compte.

![pop-up OTP](assets/new-logo-otp-email.png){width="300" zoomable="yes"}

1. Une fois connecté avec votre [!DNL Bolt] compte, les détails du passage en caisse sont automatiquement renseignés :

   - Informations d’expédition
   - Mode de paiement

   >[!NOTE]
   >
   > Vous pouvez utiliser les informations de votre portefeuille existant (informations d’adresse ou de carte de crédit) même si les détails de votre passage en caisse sont automatiquement renseignés.

1. Ordre.

La variable [!DNL Quick Checkout] est compatible avec les options de passage en caisse standard d’Adobe Commerce, telles que [cartes cadeau](https://docs.magento.com/user-guide/catalog/product-gift-card.html) ou [codes remise](https://docs.magento.com/user-guide/marketing/price-rules-cart-coupon.html).

## [!DNL Quick Checkout] cas d’utilisation

La variable [!DNL Quick Checkout] permet plusieurs cas d’utilisation lors d’un flux de passage en caisse :

- [Utilisateur invité](../quick-checkout/checkout-bolt.md) avec un enregistrement ou un nouveau [!DNL Bolt] compte .
- Une [Utilisateur Adobe Commerce](../quick-checkout/checkout-adobe-commerce.md) avec ou sans enregistrement [!DNL Bolt] compte .

## Obtenir de l’aide

Contactez l’assistance d’Adobe Commerce via le [Centre d’aide Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html) pour toute assistance.
