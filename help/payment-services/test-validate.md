---
title: Test et validation
description: Les tests et la validation permettent de s’assurer que [!DNL Payment Services] fonctionnent comme prévu et offrent les meilleures options de paiement à vos clients.
exl-id: 95b4615e-73b0-41e8-83e2-e65a0b22f10f
feature: Payments, Checkout
source-git-commit: 5fe23b5aba9ad0a2a6c995fa6ade78f46fe7e3e1
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# Test et validation

Avant l’affichage [!DNL Payment Services] pour [!DNL Adobe Commerce] et [!DNL Magento Open Source] pour vos clients, il est préférable de tester dans votre environnement de test. _et_ en production. Les tests et la validation permettent de s’assurer que [!DNL Payment Services] fonctionnent comme prévu et offrent les meilleures options de paiement pour votre boutique et vos clients.

## Test dans l’environnement de test

Tests [!DNL Payment Services] dans un environnement de test est une étape de validation importante, même s’il s’agit d’un environnement de simulation connecté uniquement à l’environnement de test PayPal, et non aux banques et commerçants réels.

1. Effectuez un passage en caisse réussi à partir de votre boutique, avec [Champs de carte de crédit](payments-options.md#credit-card-fields) ou l’un des [Boutons de paiement PayPal](payments-options.md#paypal-smart-buttons). Voir [Test des informations d’identification](#testing-credentials) pour plus d’informations sur l’utilisation de fausses cartes de crédit à des fins de test.
1. Capture (lorsque votre action de paiement est [défini sur `Authorize and Capture`](onboard.md#set-payment-services-as-payment-method)), [remboursement](refunds.md), ou [void](voids.md) l’ordre qui vient d’être terminé. Vous pouvez également simplement [créer une facture](https://docs.magento.com/user-guide/sales/invoice-create.html){target="_blank"} pour une commande, si votre action de paiement est définie sur `Authorize` au lieu de `Authorize and Capture`.
1. Dans les 24 à 48 heures, consultez la transaction et d’autres informations dans la variable [Rapport de paiements](payouts.md).
1. Voir les détails de la commande dans la [Rapport d’état des paiements de commande](order-payment-status.md).

### Test des informations d’identification

Lors du test et de la validation de votre environnement de test, vous devez utiliser de faux numéros de carte de crédit, de sorte que vous ne créiez pas de frais réels pour un compte de carte de crédit existant.

Utilisez le générateur de carte de crédit de PayPal pour [générer des informations de carte de crédit aléatoire ;](https://www.paypal.com/us/smarthelp/article/where-can-i-find-test-credit-card-numbers-ts2157) pour les tests.

Pour tester le paiement Apple en mode sandbox :

* Créez un [Compte de test sandbox Apple](https://developer.apple.com/apple-pay/sandbox-testing/#create-a-sandbox-tester-account), accompagnés de fausses informations de carte de crédit et de facturation.
* [Enregistrement des domaines des environnements de test](https://developer.paypal.com/docs/checkout/apm/apple-pay/#link-registeryoursandboxdomains).

>[!NOTE]
>
>Le traitement des paiements sandbox de PayPal est parfois lent et le service peut parfois diminuer. Cette situation n’est pas une indication de la vitesse et de l’efficacité du traitement des paiements de produits en direct.

## Test en production

Il est vivement recommandé de tester [!DNL Payment Services] en production, avec de vraies cartes de crédit et banques, avant d’exposer cette fonctionnalité aux acheteurs. Même lors du test [!DNL Payment Services] dans sandbox est important, le test en production est la méthode la plus infaillible pour assurer [!DNL Payment Services] fonctionne comme prévu.

Vous pouvez tester [!DNL Payment Services] en production de l’une des deux façons suivantes :

* Choisissez une heure à laquelle vous savez qu’aucune commande ne sera passée par les acheteurs.
* Utilisez un webstore temporairement inaccessible pour les acheteurs, mais accessible à des fins de test.

Effectuez vos tests de production avec des cartes de crédit réelles et des comptes PayPal, en testant l’ensemble du cycle de vie d’un paiement, y compris la capture et le remboursement. L’ensemble du flux de paiement et de passage en caisse au cours du test vous donne une idée plus précise de la manière dont votre [!DNL Payment Services] fonctionne lorsque les acheteurs actifs l’utilisent.

Vous devez également vérifier que les informations qui apparaissent sur les relevés bancaires pour les méthodes de paiement que vous utilisez dans les tests de production sont correctes et attendues (y compris la description de votre entreprise).

Pour tester le paiement Apple en mode de production, vous devez [enregistrer vos domaines de production ;](https://developer.paypal.com/docs/checkout/apm/apple-pay/#register-your-live-domain).
