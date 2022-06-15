---
title: '"Flux de passage en caisse"'
description: '"Présentation de la variable [!DNL Quick Checkout] flux dans Adobe Commerce."'
exl-id: 82761627-a0d4-4cb0-aad1-9865fcb550d4
source-git-commit: c0b1185a53cb84be2335e2e1beb392c9f23070c9
workflow-type: tm+mt
source-wordcount: '553'
ht-degree: 0%

---

# [!DNL Quick Checkout] flow

Cette section présente un aperçu de l’expérience de passage en caisse classique à l’aide de la méthode [!DNL Quick Checkout] pour l’extension Adobe Commerce.

Une réussite [!DNL Quick Checkout] Le flux se compose des étapes suivantes :

1. Ouvrez votre storefront et ajoutez des éléments dans votre panier.
1. Passez à la caisse.

![Passage en caisse](assets/proceed-checkout.png)

1. Lorsque vous y êtes invité, saisissez une adresse électronique associée à un événement [!DNL Bolt] compte .
1. Saisissez le mot de passe unique (OTP) envoyé à cette fin. [!DNL Bolt] adresse électronique ou numéro de téléphone du compte.
1. Une fois connecté avec votre [!DNL Bolt] compte, les détails du passage en caisse sont automatiquement renseignés :

   - Informations d’expédition
   - Mode de paiement

   >[!NOTE]
   >
   > Vous pouvez utiliser les informations de votre portefeuille existant (informations d’adresse ou de carte de crédit) même si les détails de votre passage en caisse sont automatiquement renseignés.

1. Ordre.

Le [!DNL Quick Checkout] est compatible avec les options de passage en caisse standard d’Adobe Commerce, telles que [cartes cadeau](https://docs.magento.com/user-guide/catalog/product-gift-card.html) ou [codes remise](https://docs.magento.com/user-guide/marketing/price-rules-cart-coupon.html).

## [!DNL Quick Checkout] cas d’utilisation

Le [!DNL Quick Checkout] permet plusieurs cas d’utilisation lors d’un flux de passage en caisse :

- Utilisateur invité avec un enregistré [!DNL Bolt] compte .
- Utilisateur invité avec un nouveau [!DNL Bolt] compte .
- Un utilisateur Adobe Commerce existant avec/sans enregistrement [!DNL Bolt] compte .

## Passage en caisse des utilisateurs invités : Fonctionnement

L’expérience de passage en caisse des invités est différente de l’expérience de connexion. Lorsqu’un acheteur entre une adresse électronique dans un passage en caisse, la variable [!DNL Quick Checkout] valide la recherche d’un [!DNL Bolt] compte .

### Inscrits [!DNL Bolt] account

Si une [!DNL Bolt] compte trouvé, les acheteurs continuent avec leurs [!DNL Quick Checkout] passage en caisse transparent :

1. Saisissez le mot de passe unique (OTP) envoyé à cette fin. [!DNL Bolt] adresse électronique du compte ou mobile, selon les préférences de l’utilisateur dans la variable [!DNL Bolt] compte .
1. Une fois connecté avec votre [!DNL Bolt] , il remplit automatiquement les détails du passage en caisse :

   - Informations d’expédition
   - Mode de paiement

1. Ordre.

>[!TIP]
>
> L’utilisateur invité place la commande et peut s’enregistrer dans Adobe Commerce.

### Nouveau [!DNL Bolt] account

Si non [!DNL Bolt] est trouvé, les clients continuent de passer en caisse Adobe Commerce par défaut et shopper fournit tous les détails nécessaires pour passer commande :

- Informations sur l’expédition et la facturation
- Mode de livraison
- Vérification du mode de paiement
- Une case à cocher s’affiche pour s’enregistrer dans [!DNL Bolt] pour des passages en caisse plus rapides avant de passer la commande. Ils peuvent accepter les conditions générales pour créer leur [!DNL Bolt] compte .

   ![Mémoriser [!DNL Bolt]](assets/checked-bolt.png)

- L’utilisateur invité place la commande et peut s’enregistrer dans Adobe Commerce.

## Un utilisateur Adobe Commerce existant : Fonctionnement

Un utilisateur existant peut sélectionner des détails existants lorsqu’un utilisateur commande avec la variable [!DNL Quick Checkout] pour une expérience de passage en caisse plus rapide.

Lorsqu’un acheteur entre une adresse électronique dans un passage en caisse, la variable [!DNL Quick Checkout] valide la recherche d’un [!DNL Bolt] compte .

### Inscrits [!DNL Bolt] compte avec un utilisateur Adobe Commerce

Si une [!DNL Bolt] est trouvé, les clients continuent de payer leur passage en caisse Adobe Commerce par défaut, et l’acheteur fournit tous les détails nécessaires, puis passe commande :

- Informations sur l’expédition et la facturation
- Mode de livraison
- Vérification du mode de paiement

Si vous rencontrez des problèmes lorsque vous passez une commande en tant qu’utilisateur Adobe Commerce existant, reportez-vous à la section [Dépannage des problèmes de paiement rapide](https://support.magento.com/hc/en-us/articles/6909450342541) Article du Centre d’aide Adobe Commerce.

>[!NOTE]
>
> Si l’utilisateur dispose d’un [!DNL Bolt] Le compte et l’e-mail n’apparaissent pas comme enregistrés dans Adobe Commerce, ils déclenchent la connexion avec mot de passe unique (OTP). Voir [registered [!DNL Bolt] account](#registered-bolt-account) flux.

### Nouveau [!DNL Bolt] account

Si non [!DNL Bolt] Le compte est trouvé, les acheteurs continuent de passer en caisse Adobe Commerce par défaut et l’acheteur sélectionne tous les détails nécessaires dans les informations enregistrées pour passer la commande :

- Informations sur l’expédition et la facturation
- Mode de livraison
- Vérification du mode de paiement
- Une case à cocher s’affiche pour s’enregistrer dans [!DNL Bolt] pour des passages en caisse plus rapides avant de passer la commande. Ils peuvent accepter les conditions générales pour créer leur [!DNL Bolt] compte .

   ![Mémoriser [!DNL Bolt]](assets/checked-bolt.png)

## Obtenir de l’aide

Contact [Prise en charge d’Adobe Commerce](mailto:quick-checkout-support@adobe.com) pour toute assistance.
