---
title: Signifyd contre la fraude
description: Activation de la protection automatisée contre les fraudes pour [!DNL Payment Services] avec Signifyd.
role: Admin, User
level: Intermediate
feature: Payments, Checkout, Configuration, Security
source-git-commit: 400d1f8a384fceebcd13e9496f8e218e694d2752
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---


# Protection Signifyd contre la fraude

Vous pouvez activer la protection automatisée contre les fraudes pour [!DNL Payment Services] avec la propriété [Extension Signifyd](https://commercemarketplace.adobe.com/signifyd-module-connect.html).

Adobe Commerce prend en charge les versions 5.4.0 et ultérieures de Signifyd. [!DNL Payment Services] prend en charge les flux Signifyd avant et après l’authentification.

Voir [Documentation Signifyd](https://community.signifyd.com/support/s/article/magento-2-extension-install-guide?language=en_US#downloadandinstallingmagento2extension) pour en savoir plus sur l’installation et la configuration de l’extension.

## Limites de l’intégration

Actuellement, les restrictions suivantes s’appliquent à l’intégration entre Signifyd et [!DNL Payment Services]:

* The Signifyd/[!DNL Payment Services] prise en charge de l’intégration uniquement [champs de carte de crédit](../payment-services/payments-options.md#credit-card-fields) (pas les boutons de paiement PayPal ou Apple Pay). [!DNL Payment Services] envoie les données de commande reçues via les boutons de paiement PayPal et le paiement Apple à Signifyd, mais l’intégration ne fournit que les détails des commandes passées via les champs de carte de crédit.
* Signifyd ne prend pas en charge les commandes passées dans l’administrateur par un commerçant pour un acheteur.
* Signifyd ne prend pas en charge les commandes passées avec [cartes de crédit en coffre](../payment-services/vaulting.md).

## Intégration

Vous devez communiquer directement avec Signifyd à bord de l’extension pour l’utiliser avec . [!DNL Payment Services]—il n’y a pas de [!DNL Payment Services] configuration requise. Une fois installée, vous pouvez configurer l’extension Signifyd dans l’Admin. Toute prise en charge liée à cette extension sera gérée par Signifyd.

Lors de l’intégration avec Signifyd, vous devez :

1. Contactez Signifyd pour configurer un nouveau compte.
1. Par défaut, Signifyd est [placé sur la liste autorisée](https://github.com/signifyd/magento2/blob/main/docs/RESTRICT-PAYMENTS.md) pour vous assurer que Signifyd ne se déclenche pas pour d’autres options de paiement qu’il ne prend actuellement pas en charge. Si vous souhaitez interdire un mode de paiement particulier, vous devez apporter des modifications.
1. Confirmez avec Signifyd que PayPal ne rejettera pas les commandes, via le paramètre de protection anti-fraude du marchand dans Paypal, qui pourraient être approuvées par Signifyd.
1. Activer la compatibilité de l’extension Signifyd avec [!DNL Payment Services]:
   * Lorsque vous utilisez [!DNL Payment Services] in _En direct_ , Signifyd doit être en mode Production.
   * Lorsque vous utilisez [!DNL Payment Services] in _Sandbox_ , Signifyd doit être en mode test.

## Configuration

Signifyd pouvant agir sur vos commandes, il est nécessaire de configurer l’extension pour qu’elle se comporte de manière appropriée en fonction de l’action de paiement définie pour [!DNL Payment Services].

Ces options de configuration ne sont pas compatibles avec les services de paiement et l’intégration de Signifyd :

* When [!DNL Payment Services] est configuré à l’aide de la fonction `Authorize` action de paiement _et_ Signifyd est dans `PostAuth` avec la fonction _[!UICONTROL Decline Guarantees]_option définie sur **Créer une note de crédit**.

  Motif : [!DNL Payment Services] crée une transaction d’autorisation que Signify tente ensuite de rembourser.


* [!DNL Payment Services] est configuré à l’aide de la fonction `Authorize and Capture` action de paiement _et_ Signifyd est dans `PostAuth` avec la fonction _[!UICONTROL Decline Guarantees]_option définie sur **Annuler la commande**.

  Motif : [!DNL Payment Services] crée une transaction de capture que Signifyd tente ensuite d’annuler.


Voir la documentation Signifyd pour plus d’informations sur [configuration de l’extension](https://community.signifyd.com/support/s/article/magento-2-extension-install-guide?language=en_US#configuringmagento2extension).

Voir la documentation Signifyd vers [en savoir plus sur les workflows de commande](https://community.signifyd.com/support/s/article/magento-2-extension-install-guide?language=en_US#howmagento2works).
