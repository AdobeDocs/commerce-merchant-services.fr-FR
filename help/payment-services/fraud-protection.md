---
title: Signifyd contre la fraude
description: Activez la protection anti-fraude automatisée pour  [!DNL Payment Services] avec Signifyd.
role: Admin, User
level: Intermediate
feature: Payments, Checkout, Configuration, Security
exl-id: 440296bb-a6ff-408b-8195-3027916e4f84
source-git-commit: 480b35fbc57b8528dbc305aa7db52483ba49d98c
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# Protection Signifyd contre la fraude

Vous pouvez activer la protection automatisée contre la fraude pour [!DNL Payment Services] avec l’ [extension Signifyd](https://commercemarketplace.adobe.com/signifyd-module-connect.html).

Adobe Commerce prend en charge les versions 5.4.0 et ultérieures de Signifyd. [!DNL Payment Services] prend en charge les flux pre-auth et post-auth Signifyd.

L’intégration Signifyd/[!DNL Payment Services] fournit une couverture pour les cartes de crédit, les cartes de débit, les cartes votées, le passage en caisse par le biais de l’administrateur et les méthodes de paiement PayPal et Apple. Bien que certains détails des transactions ne soient pas partagés entre les Services de paiement et Signifyd, Signifyd offre une couverture de risque complète pour tous les modes de paiement, assurant une protection optimale.

Voir la [documentation Signifyd](https://community.signifyd.com/support/s/article/magento-2-extension-install-guide?language=en_US#downloadandinstallingmagento2extension) pour en savoir plus sur l’installation et la configuration de l’extension.

## Intégration

Vous devez communiquer directement avec Signifyd à bord de l’extension pour l’utiliser avec [!DNL Payment Services]. Aucune configuration [!DNL Payment Services] n’est nécessaire. Une fois installée, vous pouvez configurer l’extension Signifyd dans l’Admin. Toute prise en charge liée à cette extension sera gérée par Signifyd.

Lors de l’intégration avec Signifyd, vous devez :

1. Contactez Signifyd pour configurer un nouveau compte.
1. Par défaut, Signifyd est [placé sur la liste autorisée](https://github.com/signifyd/magento2/blob/main/docs/RESTRICT-PAYMENTS.md) pour s’assurer que Signifyd ne se déclenche pas pour d’autres options de paiement qu’il ne prend actuellement pas en charge. Si vous souhaitez interdire un mode de paiement particulier, vous devez apporter des modifications.
1. Confirmez avec Signifyd que PayPal ne rejettera pas les commandes, via le paramètre de protection anti-fraude du marchand dans Paypal, qui pourraient être approuvées par Signifyd.
1. Activez l’extension Signifyd pour qu’elle soit compatible avec [!DNL Payment Services] :
   * Lorsque vous utilisez [!DNL Payment Services] en mode _Live_, Signifyd doit être en mode de production.
   * Lors de l’utilisation de [!DNL Payment Services] en mode _Sandbox_, Signifyd doit être en mode test.

## Configuration

Signifyd pouvant agir sur vos commandes, il est nécessaire de configurer l’extension pour qu’elle se comporte correctement en fonction de l’action de paiement que vous avez définie pour [!DNL Payment Services].

Ces options de configuration ne sont pas compatibles avec les services de paiement et l’intégration de Signifyd :

* Lorsque [!DNL Payment Services] est configuré avec l’action de paiement `Authorize` _et_ Signifyd est en mode `PostAuth` avec l’option _[!UICONTROL Decline Guarantees]_définie sur **Créer un avoir**.

  Motif : [!DNL Payment Services] crée une transaction d’autorisation que Signify tente ensuite de rembourser.


* [!DNL Payment Services] est configuré avec l’ `Authorize and Capture` action de paiement _et_ Signifyd est en mode `PostAuth` avec l’option _[!UICONTROL Decline Guarantees]_définie sur **Annuler la commande**.

  Raison : [!DNL Payment Services] crée une transaction de capture que Signifyd tente ensuite d’annuler.


Voir la documentation Signifyd pour plus d’informations sur [la configuration de l’extension](https://community.signifyd.com/support/s/article/magento-2-extension-install-guide?language=en_US#configuringmagento2extension).

Voir la documentation Signifyd pour [en savoir plus sur les workflows de commande](https://community.signifyd.com/support/s/article/magento-2-extension-install-guide?language=en_US#howmagento2works).
