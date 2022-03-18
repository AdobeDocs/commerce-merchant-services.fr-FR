---
title: Flux de passage en caisse
description: Présentation de la variable [!DNL Express Checkout] flux dans Adobe Commerce.
exl-id: 82761627-a0d4-4cb0-aad1-9865fcb550d4
source-git-commit: 163dd5260908b4ea3a8bfbcfdb834531d1603734
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# [!DNL Express Checkout] flow

>[!IMPORTANT]
>
> Cette fonctionnalité est réservée aux utilisateurs du Programme des Adopteurs Anticipés (EAP) et n’est pas encore accessible à tous les clients. Actuellement limitée aux clients américains. Contactez l’assistance d’Adobe Commerce pour toute question ou assistance.

Cette section présente un aperçu de l’expérience de passage en caisse classique à l’aide de la méthode [!DNL Express Checkout] pour l’extension Adobe Commerce.

Une réussite [!DNL Express Checkout] Le flux se compose des étapes suivantes :

1. Ouvrez votre storefront et ajoutez des éléments dans votre panier.
1. Passez à la caisse.

![Passage en caisse](../assets/proceed-checkout.png)

1. Lorsque vous y êtes invité, saisissez une adresse électronique associée à un compte Bolt.
1. Saisissez le mot de passe unique (OTP) envoyé à l’adresse électronique ou au numéro de téléphone de ce compte Bolt.
1. Une fois connecté à votre compte Bolt, les détails de passage en caisse sont automatiquement renseignés :

   - Informations d’expédition
   - Mode de paiement

   >[!NOTE]
   >
   > Vous pouvez utiliser les informations de votre portefeuille existant (informations d’adresse ou de carte de crédit) même si les détails de votre passage en caisse sont automatiquement renseignés.

1. Ordre.

Le [!DNL Express Checkout] est compatible avec les options de passage en caisse standard d’Adobe Commerce, telles que [cartes cadeau](https://docs.magento.com/user-guide/catalog/product-gift-card.html) ou [codes remise](https://docs.magento.com/user-guide/marketing/price-rules-cart-coupon.html).

## [!DNL Express Checkout] cas d’utilisation

Le [!DNL Express Checkout] permet plusieurs cas d’utilisation lors d’un flux de passage en caisse :

- Utilisateur invité avec un compte Bolt enregistré.
- Utilisateur invité avec un nouveau compte Bolt.
- Un utilisateur Adobe Commerce existant avec ou sans compte Bolt enregistré.

## Passage en caisse des utilisateurs invités : Fonctionnement

L’expérience de passage en caisse des invités est différente de l’expérience de connexion. Lorsqu’un acheteur entre une adresse électronique dans un passage en caisse, la variable [!DNL Express Checkout] le valide pour trouver un compte Bolt existant.

### Compte de Bolt enregistré

Si un compte Bolt est trouvé, les acheteurs continuent avec leurs [!DNL Express Checkout] passage en caisse transparent :

1. Saisissez le mot de passe unique (OTP) envoyé à l’adresse électronique ou au mobile de ce compte Bolt, en fonction des préférences de l’utilisateur dans le compte Bolt.
1. Une fois connecté avec votre compte Bolt, il remplit automatiquement les détails de passage en caisse :

   - Informations d’expédition
   - Mode de paiement

1. Ordre.

>[!TIP]
>
> L’utilisateur invité place la commande et peut s’enregistrer dans Adobe Commerce.

### Nouveau compte Bolt

Si aucun compte Bolt n’est trouvé, les acheteurs continuent leur passage en caisse Adobe Commerce par défaut et l’acheteur fournit tous les détails nécessaires pour passer commande :

- Informations sur l’expédition et la facturation
- Mode de livraison
- Vérification du mode de paiement
- Une case à cocher s’affiche dans Bolt pour les passages en caisse plus rapides avant de passer la commande. Ils peuvent accepter les conditions générales de création de leur compte Bolt.

   ![Mémoriser Bolt](../assets/checked-bolt.png)

- L’utilisateur invité place la commande et peut s’enregistrer dans Adobe Commerce.

## Un utilisateur Adobe Commerce existant : Fonctionnement

Un utilisateur existant peut sélectionner des détails existants lorsqu’un utilisateur commande avec la variable [!DNL Express Checkout] pour une expérience de passage en caisse plus rapide.

Lorsqu’un acheteur entre une adresse électronique dans un passage en caisse, la variable [!DNL Express Checkout] le valide pour trouver un compte Bolt existant.

### Compte Bolt enregistré avec un utilisateur Adobe Commerce

Si un compte Bolt est trouvé, les acheteurs continuent leur passage en caisse Adobe Commerce par défaut et l’acheteur fournit tous les détails nécessaires, puis passe la commande :

- Informations sur l’expédition et la facturation
- Mode de livraison
- Vérification du mode de paiement

Reportez-vous à la section [dépannage](../express-checkout/troubleshooting.md) rubrique pour plus d’informations si vous rencontrez des problèmes lorsque vous passez une commande en tant qu’utilisateur Adobe Commerce existant.

>[!NOTE]
>
> Si l’utilisateur dispose d’un compte Bolt et que le courrier électronique ne s’affiche pas comme enregistré dans Adobe Commerce, il déclenche la connexion au mot de passe unique (OTP). Voir [compte Bolt enregistré](#registered-bolt-account) flux.

### Nouveau compte Bolt

Si aucun compte Bolt n’est trouvé, les acheteurs continuent leur passage en caisse Adobe Commerce par défaut et l’acheteur sélectionne tous les détails nécessaires à partir des informations enregistrées pour passer la commande :

- Informations sur l’expédition et la facturation
- Mode de livraison
- Vérification du mode de paiement
- Une case à cocher s’affiche dans Bolt pour les passages en caisse plus rapides avant de passer la commande. Ils peuvent accepter les conditions générales de création de leur compte Bolt.

   ![Mémoriser Bolt](../assets/checked-bolt.png)

## Obtenir de l’aide

Contactez l’assistance d’Adobe Commerce pour toute question ou assistance.
