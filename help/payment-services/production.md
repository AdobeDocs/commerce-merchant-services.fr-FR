---
title: Activer [!DNL Payment Services] pour la production
description: Terminez le processus d’intégration en activant [!DNL Payment Services] pour la production.
exl-id: 3b1269e8-127b-47f8-9738-9722a5737c63
feature: Payments, Checkout, Configuration, Install
source-git-commit: 6ba5a283d9138b4c1be11b80486826304c63247f
workflow-type: tm+mt
source-wordcount: '702'
ht-degree: 0%

---

# Activer [!DNL Payment Services] pour la production

Vous pouvez mettre le service en production et terminer la [processus d’intégration](onboard.md), selon les étapes de cette rubrique, après avoir :

* [Installer](install.md) l’extension des services de paiement ;
* [Configuration et connexion](connect.md) votre instance
* [Configuration](sandbox.md) et [test](test-validate.md) votre environnement de test

## Définir [!DNL Payment Services] comme mode de paiement

Après vous [Configuration de Commerce Services](connect.md#configure-commerce-services) et activez [test des environnements de test](sandbox.md#enable-sandbox-testing) ou [paiements en direct](#enable-live-payments), vous devez définir [!DNL Payment Services] comme méthode de paiement.

1. Sur le _Administration_ barre latérale, accédez à **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Cliquez sur **[!UICONTROL Enable Payment Services]**.

   Cette option est visible si vous n’avez pas encore configuré . [!DNL Payment Services] comme mode de paiement pour un ou plusieurs de vos sites web.

   Vous êtes dirigé vers la zone des paramètres dans la vue Accueil avec les options appropriées développées (**[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > _[!UICONTROL Settings]_), où vous pouvez activer la fonction [!DNL Payment Services] d’ [mode de paiement](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html){target="_blank"}.

1. Dans _[!UICONTROL General Configuration]_, définit **[!UICONTROL Enable]**to `Yes`.
1. Définir **[!UICONTROL Payment Action]**, pour les _[!UICONTROL Credit Card Fields]_et_[!UICONTROL PayPal Smart Buttons]_, à l’une des méthodes suivantes :

   | Paramètre | Description |
   |---|---|
   | `Authorize` | Approuve l’achat et met une mainmise sur les fonds. Le montant n’est pas retiré tant qu’il n’a pas été &quot;capturé&quot; par le marchand. |
   | `Authorize and Capture` | Approuve l’achat et le commerçant &quot;capture&quot; les fonds. |

1. Cliquez sur **[!UICONTROL Save]**.
1. Cliquez sur **[!UICONTROL Go to Payment Services]** pour être dirigé vers le [!DNL Payment Services] Chez soi.
1. [Effacer le cache](https://docs.magento.com/user-guide/system/cache-management.html){target="_blank"}.

   L’effacement doit être effectué après chaque modification de configuration.

Voir [Configuration des services de paiement](settings.md) pour plus d’informations sur la configuration des champs de carte de crédit et des boutons intelligents PayPal.

## Intégration complète de commerce

1. Sur le _Administration_ barre latérale, accédez à **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Cliquez sur **[!UICONTROL Live onboarding]**.

   Cette option est visible si vous n’avez pas encore terminé l’intégration pour [!DNL Payment Services].

   Une fenêtre PayPal s’affiche.

1. Poursuivez avec le flux PayPal, en utilisant les informations d’identification de votre compte PayPal (et non les informations d’identification de votre compte sandbox) ou inscrivez-vous à un nouveau compte PayPal.
1. Dans la barre latérale d’administration, accédez à **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**

   La variable _[!UICONTROL Live onboarding]_n’est plus visible et un &quot;[!UICONTROL Live payments pending]&quot;.

   Dans cette zone de texte, vous pouvez également être invité à confirmer votre adresse électronique avec PayPal pour terminer l’intégration.

1. Si vous êtes invité à confirmer votre adresse électronique, vérifiez que le message de confirmation envoyé par PayPal s’affiche dans votre message de confirmation, puis cliquez sur pour confirmer votre adresse électronique.
1. Dans la barre latérale d’administration, accédez à **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Actualisez la fenêtre de votre navigateur.

   Une fois votre intégration des commerçants PayPal approuvée, une notification vous indique que votre système de paiement est en mode sandbox et qu’il ne traite pas les paiements en direct.

   >[!IMPORTANT]
   >
   >Si vous révoquez le consentement de [!DNL Payment Services] pour [!DNL Adobe Commerce] et [!DNL Magento Open Source] pour le traitement de vos paiements (dans les paramètres de votre compte PayPal), les commandes de votre boutique ne peuvent pas être traitées par [!DNL Payment Services]. Sur votre page d’accueil des services de paiement, une alerte concernant le consentement révoqué s’affiche.

## Demander des droits sur les paiements depuis l’Adobe

Pour activer l’intégration en direct, vous devez demander des droits de paiement à l’Adobe :

1. Sur le _Administration_ barre latérale, accédez à **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Cliquez sur **[!UICONTROL Get Live Payments]** dans votre [!DNL Payment Services] Chez soi.

   ![Demande de droits](assets/request-entitlements.png){width="500" zoomable="yes"}

1. Remplissez le formulaire.
1. Un membre de l&#39;équipe commerciale vous contactera.

Vous pouvez également demander des droits au paiement auprès d’un Adobe à l’adresse [business.adobe.com](https://business.adobe.com/resources/payment-services.html).

>[!IMPORTANT]
>
>**Intégration en direct** n’est pas accessible tant que les droits aux paiements n’ont pas été validés.

## Configurer le niveau de tarification

Pour obtenir votre [!DNL Payment Services] _Identifiant du marchand_:


1. Sur le _Administration_ barre latérale, accédez à **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Dans la vue Accueil, cliquez sur **[!UICONTROL Settings]**. Voir [Accueil](payments-home.md) pour plus d’informations.
1. Sélectionnez les _Identifiant du marchand_ et soumettez-le à votre représentant commercial, qui configurera le niveau de tarification approprié.

## Activer les paiements en direct

A _identifiant du commerçant de production_ est généré automatiquement et renseigné dans la variable [configuration](configure-admin.md). Ne modifiez pas ou ne modifiez pas cet identifiant.

Pour activer les paiements en direct :

1. Sur le _Administration_ barre latérale, accédez à **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Sur la page d’accueil, cliquez sur **[!UICONTROL Settings]** en haut à droite de la page. Voir [Accueil](payments-home.md) pour plus d’informations.
1. Dans le _[!UICONTROL General Configuration]_ensemble de sections **[!UICONTROL Payment mode]**to `Production`.
1. Cliquez sur **[!UICONTROL Save]**.
1. [Effacer le cache](https://docs.magento.com/user-guide/system/cache-management.html){target="_blank"}.

   >[!IMPORTANT]
   >
   >Si vous n’effacez pas votre cache, les clients ne peuvent pas voir les options de paiement PayPal lors du passage en caisse.

Si vous revenez à [!DNL Payment Services] Accueil, le message Mode de paiement Sandbox n’apparaît plus, car vous traitez désormais les paiements en direct.

Voir [Configuration dans l’administrateur](configure-admin.md) pour les options de configuration héritées.

>[!IMPORTANT]
>
>Si vous révoquez le consentement de [!DNL Payment Services] pour le traitement de vos paiements (dans les paramètres de votre compte PayPal), les commandes de votre boutique ne peuvent pas être traitées par [!DNL Payment Services]. Si vous souhaitez réactiver le traitement des paiements, vous devez effectuer à nouveau l’intégration. Sur votre page d’accueil des services de paiement, une alerte concernant le consentement révoqué s’affiche.

## Test en production

Il est vivement recommandé de tester les paiements en production, avec de vraies cartes de crédit et des banques, avant d’exposer cette fonctionnalité aux acheteurs.

Voir [Tester et valider](test-validate.md) pour plus d’informations.
