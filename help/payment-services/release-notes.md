---
title: '"[!DNL Payment Services] Notes de mise à jour"'
description: Consultez les notes de mise à jour pour plus d’informations sur toutes les [!DNL Payment Services] versions.
exl-id: 104aa2c7-7735-4ac2-8ed1-a03cd9911273
source-git-commit: eb8fdba65b4b64730d0ad4fa6e0c9b64bdadc7df
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Notes de mise à jour

Ces notes de mise à jour décrivent la version initiale de [!DNL Payment Services] et incluent :

![Nouveau](../assets/new.svg) Nouvelles fonctionnalités
![Correction d’un problème](../assets/fix.svg) Correctifs et améliorations
![Problème connu](../assets/bug.svg) Problèmes connus

## v1.0.0

![Nouveau](../assets/new.svg)<!-- Issue PAY-2127 --> Disponibilité générale [Services de paiement](https://marketplace.magento.com/magento-payment-services.html) est désormais compatible avec Adobe Commerce et Magento Open Source versions 2.4.0 à 2.4.3-p1.

![Nouveau](../assets/new.svg)<!-- Issue PAY-124 --> Le [!DNL Payment Services] l’extension pour Adobe Commerce et Magento Open Source peut être installée pour [Adobe Commerce sur l’infrastructure cloud](install.md#magento-commerce-cloud) ou [Sur site](install.md#on-premises) instances. Ces méthodes nécessitent l’utilisation d’une interface de ligne de commande.

![Nouveau](../assets/new.svg)<!-- Issue PAY-1986 --> [!DNL Payment Services] prend en charge une [compte sandbox](onboard.md#enable-sandbox-testing) qui permet aux commerçants d’évaluer l’extension en mode test.

![Nouveau](../assets/new.svg)<!-- Issue PAY-666 --> Les commerçants peuvent [configuration des services de paiement](configure-admin.md) l’extension avec des comportements de paiement de base (tels que la capture d’authentification conjointement et le passage d’un environnement de test à un autre ou à un environnement de production).

![Nouveau](../assets/new.svg)<!-- Issue PAY-780 --> Les acheteurs peuvent vérifier avec [!DNL Payment Services] ou vous pouvez passer la commande par téléphone et [création d’une commande entière](create-order.md) dans Admin pour eux.

![Nouveau](../assets/new.svg)<!-- Issue PAY-1856 --> [!DNL Payment Services] proposer des rapports complets aux vendeurs afin que vous puissiez avoir une vue précise de vos commandes et paiements en magasin.

![Nouveau](../assets/new.svg)<!-- Issue PAY-311 --> [!DNL Payment Services] prend en charge des prix à plusieurs niveaux (basés sur TPV) adaptés à n’importe quel commerçant.

![Nouveau](../assets/new.svg)<!-- Issue PAY-1443 --> Il est possible de personnaliser l’aspect des boutons PayPal et les champs CC pour les [Services de paiement](https://devdocs.magento.com/payment-services/customize-buttons-messaging.html) extension .

![Problème connu](../assets/bug.svg)<!-- Issue PAY-2473 --> Utilisation [clés de compositeur incorrectes](https://support.magento.com/hc/en-us/articles/4406603542541) lors de l’installation de l’extension empêche l’utilisateur de [authentifier](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) avec correct `MAGEID`.

![Problème connu](../assets/bug.svg)<!-- Issue PAY-2474 --> [!DNL Payment Services] [rapports](https://support.magento.com/hc/en-us/articles/4406114741517) pour l’état de paiement des paiements et des commandes, il se peut que la synchronisation ne se produise pas immédiatement.

![Problème connu](../assets/bug.svg)<!-- Issue PAY-2475 --> [Compte sandbox PayPal](https://support.magento.com/hc/en-us/articles/4406954952461) pour [!DNL Payment Services] ne peut pas être vérifié.
