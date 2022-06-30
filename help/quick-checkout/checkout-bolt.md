---
title: '"Flux de passage en caisse"'
description: '"Présentation de la variable [!DNL Quick Checkout] flux d’un utilisateur Bolt dans Adobe Commerce."'
source-git-commit: 01bb92d1de1f6a6da1d6326c0190eb7711274045
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 0%

---


# Utilisateurs invités

L’expérience de passage en caisse de l’invité est différente de l’expérience utilisateur de l’Adobe. Lorsqu’un acheteur entre une adresse électronique dans un passage en caisse, la variable [!DNL Quick Checkout] valide et trouve un [!DNL Bolt] compte .

## Inscrits [!DNL Bolt] account

Si une [!DNL Bolt] compte trouvé, les acheteurs continuent avec leurs [!DNL Quick Checkout] passage en caisse transparent :

1. Saisissez le mot de passe unique (OTP) envoyé à cette fin. [!DNL Bolt] adresse électronique ou mobile du compte, selon le [préférences de l’utilisateur dans la variable [!DNL Bolt] account](https://help.bolt.com/shoppers/account/account-settings/#how-to-set-preferred-login-method){target=_blank}.
1. Une fois connecté avec votre [!DNL Bolt] , les détails sont automatiquement ajoutés :

   - Informations d’expédition
   - Mode de paiement

1. Faites votre commande.

>[!TIP]
>
> L’utilisateur invité place la commande et peut éventuellement s’enregistrer dans Adobe Commerce.

## Nouveau [!DNL Bolt] account

Si non [!DNL Bolt] est trouvé, les clients continuent de passer en caisse Adobe Commerce par défaut et l’acheteur fournit tous les détails nécessaires pour passer commande :

- Informations sur l’expédition et la facturation
- Mode de livraison
- Vérification du mode de paiement
- Une case à cocher s’affiche pour s’enregistrer dans [!DNL Bolt] pour des passages en caisse plus rapides avant de passer la commande. L’acheteur peut accepter les conditions générales pour créer sa [!DNL Bolt] compte .

   ![Mémoriser [!DNL Bolt]](assets/checked-bolt.png)

- L’utilisateur invité place la commande et peut éventuellement s’enregistrer dans Adobe Commerce.
