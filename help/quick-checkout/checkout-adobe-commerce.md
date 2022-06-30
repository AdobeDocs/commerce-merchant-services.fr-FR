---
title: '"Flux de passage en caisse"'
description: '"Présentation de la variable [!DNL Quick Checkout] flux pour un utilisateur Adobe Commerce."'
source-git-commit: 01bb92d1de1f6a6da1d6326c0190eb7711274045
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---


# Un utilisateur Adobe Commerce existant : Fonctionnement

Un utilisateur Adobe Commerce existant peut sélectionner des informations d’expédition et de paiement enregistrées lors du placement d’une commande avec la variable [!DNL Quick Checkout] pour une expérience de passage en caisse plus rapide.

Lorsqu’un acheteur saisit son adresse électronique au moment de l’extraction, la variable [!DNL Quick Checkout] valide et trouve un [!DNL Bolt] compte .

## Inscrits [!DNL Bolt] compte avec un utilisateur Adobe Commerce

Si une [!DNL Bolt] compte trouvé, les acheteurs continuent avec leurs [!DNL Quick Checkout] passage en caisse transparent :

1. Saisissez le mot de passe unique (OTP) envoyé à cette fin. [!DNL Bolt] adresse électronique ou mobile du compte, selon le [préférences de l’utilisateur dans la variable [!DNL Bolt] account](https://help.bolt.com/shoppers/account/account-settings/#how-to-set-preferred-login-method){target=_blank}.
1. Une fois connecté avec votre [!DNL Bolt] , les détails sont automatiquement ajoutés :

   - Informations d’expédition
   - Mode de paiement

1. Faites votre commande.

Si vous rencontrez des problèmes lorsque vous passez une commande en tant qu’utilisateur Adobe Commerce existant, reportez-vous à la section [Dépannage des problèmes de paiement rapide](https://support.magento.com/hc/en-us/articles/6909450342541) Article du Centre d’aide Adobe Commerce.

## Nouveau [!DNL Bolt] account

Si non [!DNL Bolt] est trouvé, les acheteurs continuent de passer en caisse Adobe Commerce par défaut et l’acheteur sélectionne tous les détails nécessaires dans les informations enregistrées pour passer la commande :

- Informations sur l’expédition et la facturation
- Mode de livraison
- Vérification du mode de paiement
- L’option d’enregistrement dans [!DNL Bolt] pour des passages en caisse plus rapides avant de placer la commande. L’acheteur peut accepter les conditions générales pour créer sa [!DNL Bolt] compte .

   ![Mémoriser [!DNL Bolt]](assets/checked-bolt.png)
