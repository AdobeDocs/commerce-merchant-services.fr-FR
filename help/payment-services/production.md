---
title: Activer [!DNL Payment Services] pour la production
description: Terminez le processus d’intégration en activant  [!DNL Payment Services] pour la production.
exl-id: 3b1269e8-127b-47f8-9738-9722a5737c63
feature: Payments, Checkout, Configuration, Install
source-git-commit: 37380063242b6d904910be731b8e58471625e9cb
workflow-type: tm+mt
source-wordcount: '1019'
ht-degree: 0%

---

# Activer [!DNL Payment Services] pour la production

Vous pouvez mettre le service en production et terminer le [processus d’intégration](onboard.md), selon les étapes de cette rubrique, après avoir :

* [Installer](install.md) l’extension des services de paiement
* [Configurer et connecter](connect.md) votre instance
* [ Configurez ](sandbox.md) et [testez](test-validate.md) votre environnement de test

## Définir [!DNL Payment Services] comme méthode de paiement

Après avoir [ configuré vos services Commerce ](connect.md#configure-commerce-services) et activé le [test sandbox](sandbox.md#enable-sandbox-testing) ou les [paiements en direct](#enable-live-payments), vous devez définir [!DNL Payment Services] comme méthode de paiement.

1. Sur la barre latérale _Admin_, accédez à **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Cliquez sur **[!UICONTROL Enable Payment Services]**.

   Cette option est visible si vous n’avez pas encore configuré [!DNL Payment Services] comme méthode de paiement pour un ou plusieurs de vos sites web.

   Vous êtes dirigé vers la zone de paramètres dans la vue Accueil avec les options appropriées développées (**[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > _[!UICONTROL Settings]_), où vous pouvez activer les options [!DNL Payment Services] comme [ méthode de paiement ](https://experienceleague.adobe.com/en/docs/commerce-admin/config/sales/payment-methods/payment-methods){target="_blank"}.

1. Dans _[!UICONTROL General Configuration]_, définissez **[!UICONTROL Enable]**sur `Yes`.
1. Définissez **[!UICONTROL Payment Action]**, pour _[!UICONTROL Credit Card Fields]_et_[!UICONTROL PayPal payment buttons]_, sur l’un des paramètres suivants :

   | Paramètre | Description |
   |---|---|
   | `Authorize` | Approuve l’achat et met une mainmise sur les fonds. Le montant n’est pas retiré tant qu’il n’a pas été &quot;capturé&quot; par le marchand. |
   | `Authorize and Capture` | Approuve l’achat et le commerçant &quot;capture&quot; les fonds. |

   >[!IMPORTANT]
   >
   >[!DNL Payment Services] prend en charge les captures partielles. Un commerçant peut partiellement capturer (facture) des parties d’une commande. Par exemple, vous pouvez capturer chaque élément individuellement, ou un élément maintenant et le reste ultérieurement.

1. Cliquez sur **[!UICONTROL Save]**.
1. Cliquez sur **[!UICONTROL Go to Payment Services]** pour revenir à la page d’accueil [!DNL Payment Services].
1. [Effacez votre cache](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cache-management.html).

   L’effacement doit être effectué après chaque modification de configuration.

Pour plus d’informations sur la configuration des champs de carte de crédit et des boutons de paiement PayPal, voir [Configuration des services de paiement](settings.md) .

## Intégration complète de commerce

L’étape suivante permettant à vos magasins de passer en ligne avec les Services de paiement consiste à effectuer l’intégration en direct.

Les services de paiement offrent des options de paiement [**Avancé** (entièrement prises en charge) et **Standard** (paiement express)](../payment-services/payments-options.md#standard-vs-advanced-payments-experience) et des flux d’intégration, selon le pays dans lequel vous opérez et votre expérience de paiement préférée.

1. Sur la barre latérale _Admin_, accédez à **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Cliquez sur **[!UICONTROL Live onboarding]**.

   Cette option est visible si vous n’avez pas encore effectué l’intégration en direct pour [!DNL Payment Services].

1. Dans le modal _Sélectionner votre pays_ , sélectionnez le pays à partir duquel vous opérez.

   Les services de paiement prennent en charge toutes les options de paiement dans [cinq pays](../payment-services/overview.md#availability) actuellement. Les Services de paiement offrent des fonctionnalités de paiement express (un sous-ensemble d’options de paiement) pour tous les autres pays représentés dans la liste des pays.

   Le pays que vous choisissez dans la liste détermine les options de paiement et le flux d’intégration ([Advanced](#advanced-onboarding) (entièrement pris en charge) ou [Standard](#standard-onboarding) (Express Checkout)), disponible pour vous.

>[!TIP]
>
> Une fois que vous avez choisi et traité une option d’intégration (Standard ou Avancé), vous devez terminer l’intégration pour effectuer une mise à niveau ou une rétrogradation à partir de votre sélection initiale.

### Intégration avancée

Ce flux d’intégration est disponible pour les commerçants des [ pays entièrement pris en charge](../payment-services/overview.md#availability).

Une fois le pays sélectionné :

1. Dans le modal qui s’affiche, sélectionnez **Avancé**.

   Pour l’option **Standard**, passez au [flux d’intégration standard](#standard-onboarding).

1. Cliquez sur **Continuer**.
1. Poursuivez avec le flux PayPal pour l’intégration avancée entièrement prise en charge, en utilisant les informations d’identification de votre compte PayPal (et non les informations d’identification de votre compte sandbox) _ou_ vous inscrivez à un nouveau compte PayPal.

>[!IMPORTANT]
>
>**L’intégration avancée** nécessite que les commerçants [ demandent des droits de paiement ](#request-payments-entitlement-from-adobe) pour activer l’intégration en direct.

### Intégration standard

Ce flux d’intégration standard est disponible pour les commerçants des pays disponibles pour lesquels la [seule prise en charge du passage en caisse express](../payment-services/overview.md#availability) est fournie.

Une fois le pays sélectionné :

1. Dans le modal _Paiement Services Agreement_ qui s’affiche, cliquez sur le lien **Paiement Services Agreement** pour afficher le contrat Adobe Commerce payment Services.
1. Dans le modal _Paiement Services Agreement_, cliquez sur **I accept**.
1. Passez au flux PayPal pour l’intégration du paiement express, en utilisant les informations d’identification de votre compte PayPal (et non les informations d’identification de votre compte sandbox) ou en vous inscrivant à un nouveau compte PayPal.

>[!IMPORTANT]
>
>[Les champs de carte de paiement et de paiement Apple](../payment-services/payments-options.md) ne sont pas disponibles pour l’ **intégration standard**.

## Confirmer l’adresse électronique

1. Dans la barre latérale Admin, accédez à **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**

   Le bouton _[!UICONTROL Live onboarding]_n’est plus visible et une zone de texte &quot;[!UICONTROL Live payments pending]&quot; s’affiche.

   Dans cette zone de texte, vous pouvez également être invité à confirmer votre adresse électronique avec PayPal pour terminer l’intégration.

1. Si vous êtes invité à confirmer votre adresse électronique, vérifiez que le message de confirmation envoyé par PayPal s’affiche dans votre message de confirmation, puis cliquez sur pour confirmer votre adresse électronique.
1. Dans la barre latérale Admin, accédez à **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Actualisez la fenêtre de votre navigateur.

   Une fois votre intégration des commerçants PayPal approuvée, une notification vous indique que votre système de paiement est en mode sandbox et qu’il ne traite pas les paiements en direct.

   >[!IMPORTANT]
   >
   >Si vous révoquez le consentement à [!DNL Payment Services] pour [!DNL Adobe Commerce] et [!DNL Magento Open Source] pour le traitement de vos paiements (dans les paramètres de votre compte PayPal), les commandes de votre boutique ne peuvent pas être traitées par [!DNL Payment Services]. Sur votre page d’accueil des services de paiement, une alerte concernant le consentement révoqué s’affiche.

## Demander des droits sur les paiements depuis l’Adobe

Pour activer vos magasins, demandez des droits de paiement à l’Adobe (pour [l’intégration avancée uniquement](#advanced-onboarding)) :

1. Sur la barre latérale _Admin_, accédez à **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Cliquez sur **[!UICONTROL Get Live Payments]** dans votre [!DNL Payment Services] Accueil.

   ![Demander des droits](assets/request-entitlements.png){width="500" zoomable="yes"}

1. Remplissez le formulaire.
1. Un membre de l&#39;équipe commerciale vous contactera.

Vous pouvez également demander des droits de paiement à Adobe à l’adresse [business.adobe.com](https://business.adobe.com/resources/payment-services.html).

>[!IMPORTANT]
>
>**L’intégration en direct** n’est pas accessible tant que les droits des paiements n’ont pas été approuvés.

## Configurer le niveau de tarification

Procurez-vous votre [!DNL Payment Services] _Merchant ID_ :

1. Sur la barre latérale _Admin_, accédez à **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Dans la vue Accueil, cliquez sur **[!UICONTROL Settings]**. Voir [Accueil](payments-home.md) pour plus d’informations.
1. Sélectionnez l’_identifiant du commerçant_ requis et envoyez-le à votre représentant commercial, qui configurera le niveau de tarification approprié.

Pour plus d’informations sur les transactions de paiement, voir [Traitement de niveau 2 et de niveau 3](levels-card-payment-transactions.md).

## Activer les paiements en direct

Un _identifiant de commerçant de production_ est généré automatiquement et renseigné dans la [configuration](configure-admin.md). Ne modifiez pas ou ne modifiez pas cet identifiant.

Activer les paiements en direct :

1. Sur la barre latérale _Admin_, accédez à **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Sur la page d’accueil, cliquez sur **[!UICONTROL Settings]** en haut à droite de la page. Voir [Accueil](payments-home.md) pour plus d’informations.
1. Dans la section _[!UICONTROL General Configuration]_, définissez **[!UICONTROL Payment mode]**sur `Production`.
1. Cliquez sur **[!UICONTROL Save]**.
1. [Effacez votre cache](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management){target="_blank"}.

   >[!IMPORTANT]
   >
   >Si vous n’effacez pas votre cache, les clients ne peuvent pas voir les options de paiement PayPal lors du passage en caisse.

Si vous revenez à la page d’accueil [!DNL Payment Services], le message Mode de paiement Sandbox n’apparaît plus car vous traitez désormais les paiements en direct.

Voir [Configuration dans l’Admin](configure-admin.md) pour connaître les options de configuration héritées.

>[!IMPORTANT]
>
>Si vous révoquez le consentement à [!DNL Payment Services] pour le traitement de vos paiements (dans les paramètres de votre compte PayPal), les commandes de votre boutique ne peuvent pas être traitées par [!DNL Payment Services]. Si vous souhaitez réactiver le traitement des paiements, vous devez effectuer à nouveau l’intégration. Sur votre page d’accueil des services de paiement, une alerte concernant le consentement révoqué s’affiche.

## Test en production

Il est vivement recommandé de tester les paiements en production, avec de vraies cartes de crédit et des banques, avant d’exposer cette fonctionnalité aux acheteurs.

Voir [Test et validation](test-validate.md) pour plus d’informations.
