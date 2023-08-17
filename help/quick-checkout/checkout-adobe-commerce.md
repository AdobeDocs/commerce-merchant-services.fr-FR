---
title: "Flux de passage en caisse pour un utilisateur Adobe Commerce"
description: "Présentation de la variable [!DNL Quick Checkout] flux pour un utilisateur Adobe Commerce."
exl-id: 085e393b-15f6-4d5a-a04d-927b1f95b74e
feature: Checkout, Services, Storefront
source-git-commit: b1984a26463e14b8dc9a789421e49e5ea81ad039
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 0%

---

# Un utilisateur Adobe Commerce existant : son fonctionnement

Un utilisateur Adobe Commerce existant peut sélectionner des informations d’expédition et de paiement enregistrées lors du placement d’une commande avec la variable [!DNL Quick Checkout] pour accélérer le passage en caisse.

Lorsqu’un acheteur saisit son adresse électronique au moment de l’extraction, la variable [!DNL Quick Checkout] valide et trouve un [!DNL Bolt] compte .

## Utilisateur enregistré dans Adobe Commerce et [!DNL Bolt]

Lorsqu’un acheteur est un utilisateur enregistré dans Adobe Commerce et [!DNL Bolt] Les deux réseaux sont fournis avec les informations d’expédition et de paiement stockées.

Si une [!DNL Bolt] compte trouvé lors du passage en caisse, les clients peuvent continuer avec leur [!DNL Quick Checkout] passage en caisse transparent :

1. Saisissez le mot de passe unique (OTP) envoyé à cette fin. [!DNL Bolt] adresse électronique ou mobile du compte, en fonction des [préférences de l’utilisateur dans la variable [!DNL Bolt] account](https://help.bolt.com/shoppers/account/account-settings/#how-to-set-preferred-login-method){target=_blank}.

![pop-up OTP](assets/new-logo-otp-email.png)

1. Une fois connecté avec votre [!DNL Bolt] , les détails sont automatiquement ajoutés :

   - Informations d’expédition
   - Mode de paiement

1. Faites votre commande.

>[!NOTE]
>
> La fenêtre contextuelle bulle OTP s’affiche uniquement lorsque l’acheteur se trouve sur la page de passage en caisse. L’acheteur peut se désabonner de se connecter à Bolt en fermant cette fenêtre contextuelle.

Si l’acheteur est connecté à Adobe Commerce avant l’extraction, la variable [!DNL Bolt] La fenêtre contextuelle OTP ne s’affiche pas lors du passage en caisse, mais un message s’affiche suggérant à l’acheteur de se connecter pour accéder à son portefeuille de contrôle.

Si vous rencontrez des problèmes lorsque vous passez une commande en tant qu’utilisateur Adobe Commerce existant, reportez-vous à la section [Dépannage des problèmes de paiement rapide](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/quick-checkout-issues.html) Article du Centre d’aide Adobe Commerce.

## Connexion automatique

Le composant Connexion automatique détecte lorsqu’un acheteur dispose d’une session de blocage active et connecte automatiquement l’acheteur. Cela permet d’ignorer les étapes de détection de compte et de code de passe unique (OTP), car l’acheteur les a terminées au cours d’une session précédente.

Il est possible de configurer une connexion automatique pour [!DNL Quick Checkout] utilisateurs. Vous pouvez activer une configuration pour vous connecter automatiquement à un utilisateur lors de l’extraction.

1. Sur le _Administration_ barre latérale, accédez à **Magasins** > **Configuration** > **Passage en caisse** pour accéder à la page de configuration générale de l’administrateur de passage en caisse .
1. Dans le _Paramètres du service_ section pour [!DNL Quick Checkout], fournissez tous les détails requis pour configurer la connexion automatique.

Voir [[!DNL Quick Checkout] configuration des paramètres de service](../quick-checkout/onboarding.md#configure-service-settings) pour plus d’informations.

>[!NOTE]
>
> Première connexion lorsque **connexion automatique** est activé nécessite le consentement de l’utilisateur pour l’autoriser en acceptant une fenêtre contextuelle.

## Nouveau [!DNL Bolt] account

Si non [!DNL Bolt] est trouvé, les acheteurs continuent de passer en caisse Adobe Commerce par défaut et l’acheteur sélectionne tous les détails nécessaires dans les informations enregistrées pour passer la commande :

- Informations sur l’expédition et la facturation
- Mode de livraison
- Vérification du mode de paiement
- L’option d’enregistrement dans [!DNL Bolt] pour des passages en caisse plus rapides avant que la commande ne s’affiche. L’acheteur peut accepter les conditions générales pour créer sa [!DNL Bolt] compte .

  ![Mémoriser [!DNL Bolt]](assets/checkbox-remember-bolt.png)
