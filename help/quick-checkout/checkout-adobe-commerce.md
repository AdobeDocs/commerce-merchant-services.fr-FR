---
title: "Flux de passage en caisse pour un utilisateur Adobe Commerce"
description: "Présentation de la variable [!DNL Quick Checkout] flux pour un utilisateur Adobe Commerce."
exl-id: 085e393b-15f6-4d5a-a04d-927b1f95b74e
source-git-commit: d4b58b0ee3da866d460cf18d96ec9dd27b195f7a
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# Un utilisateur Adobe Commerce existant : Fonctionnement

Un utilisateur Adobe Commerce existant peut sélectionner des informations d’expédition et de paiement enregistrées lors du placement d’une commande avec la variable [!DNL Quick Checkout] pour une expérience de passage en caisse plus rapide.

Lorsqu’un acheteur saisit son adresse électronique au moment de l’extraction, la variable [!DNL Quick Checkout] valide et trouve un [!DNL Bolt] compte .

## Utilisateur enregistré dans Adobe Commerce et [!DNL Bolt]

Lorsqu’un acheteur est un utilisateur enregistré dans Adobe Commerce et [!DNL Bolt] Les deux réseaux sont fournis avec les informations d’expédition et de paiement stockées.

Si une [!DNL Bolt] compte trouvé lors du passage en caisse, les clients peuvent continuer avec leur [!DNL Quick Checkout] passage en caisse transparent :

1. Saisissez le mot de passe unique (OTP) envoyé à cette fin. [!DNL Bolt] adresse électronique ou mobile du compte, en fonction des [préférences de l’utilisateur dans la variable [!DNL Bolt] account](https://help.bolt.com/shoppers/account/account-settings/#how-to-set-preferred-login-method){target=_blank}.

![Fenêtre contextuelle OTP](assets/pop-up.png)

1. Une fois connecté avec votre [!DNL Bolt] , les détails sont automatiquement ajoutés :

   - Informations d’expédition
   - Mode de paiement

1. Faites votre commande.

>[!NOTE]
>
> La fenêtre contextuelle bulle OTP s’affiche uniquement lorsque l’acheteur se trouve sur la page de passage en caisse. L’acheteur peut se désabonner de se connecter à Bolt en fermant cette fenêtre contextuelle.

Si l’acheteur est connecté à Adobe Commerce avant l’extraction, la variable [!DNL Bolt] La fenêtre contextuelle OTP n’apparaîtra pas lors du passage en caisse.

Si vous rencontrez des problèmes lorsque vous passez une commande en tant qu’utilisateur Adobe Commerce existant, reportez-vous à la section [Dépannage des problèmes de paiement rapide](https://support.magento.com/hc/en-us/articles/6909450342541) Article du Centre d’aide Adobe Commerce.

## Nouveau [!DNL Bolt] account

Si non [!DNL Bolt] est trouvé, les acheteurs continuent de passer en caisse Adobe Commerce par défaut et l’acheteur sélectionne tous les détails nécessaires dans les informations enregistrées pour passer la commande :

- Informations sur l’expédition et la facturation
- Mode de livraison
- Vérification du mode de paiement
- L’option d’enregistrement dans [!DNL Bolt] pour des passages en caisse plus rapides avant de placer la commande. L’acheteur peut accepter les conditions générales pour créer sa [!DNL Bolt] compte .

   ![Mémoriser [!DNL Bolt]](assets/checkbox-remember-bolt.png)
