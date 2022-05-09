---
title: '"[!DNL Payment Services] Notes de mise à jour"'
description: Consultez les notes de mise à jour pour plus d’informations sur toutes les [!DNL Payment Services] versions.
exl-id: 104aa2c7-7735-4ac2-8ed1-a03cd9911273
source-git-commit: 9596815e31402f23b399b223f3221074331c1773
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Notes de mise à jour

Ces notes de mise à jour décrivent la version initiale de [!DNL Payment Services] et incluent :

![Nouveau](../assets/new.svg) Nouvelles fonctionnalités
![Correction d’un problème](../assets/fix.svg) Correctifs et améliorations
![Problème connu](../assets/bug.svg) Problèmes connus

## v1.1.0

![Nouveau](../assets/new.svg)<!-- Issue PAY-2127 --> [[!DNL Payment Services]](https://marketplace.magento.com/magento-payment-services.html) est désormais compatible avec [!DNL Adobe Commerce] et [!DNL Magento Open Source] versions 2.4.0 à 2.4.4.

![Nouveau](../assets/new.svg)<!-- Issue PAY-2682 --> Le [!DNL Payment Services] extension pour [!DNL Adobe Commerce] et [!DNL Magento Open Source] est disponible pour les commerçants canadiens. Les vendeurs peuvent afficher la configuration des paiements dans l’une des [Français](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html?lang=fr) ou [Anglais](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html?lang=en).

![Nouveau](../assets/new.svg)<!-- Issue PAY-2681 --> [!DNL Payment Services] prend en charge [Dollars canadiens (CAD)](overview.md#accepted-credit-cards-and-currencies) avec Carte de crédit et Paypal. Les acheteurs peuvent avoir une expérience d’achat dans la langue de leur choix, en fonction des paramètres régionaux de la boutique dans laquelle ils font leurs achats.

![Nouveau](../assets/new.svg)<!-- Issue PAY-2680 --> Les commerçants peuvent [onboard [!DNL Payment Services]](onboard.md) dans la langue de leur choix.

![Nouveau](../assets/new.svg)<!-- Issue PAY-2678 --> Les vendeurs peuvent désormais afficher [rapports financiers](order-payment-status.md) en dollars canadiens (CAD).

![Correction d’un problème](../assets/fix.svg)<!-- Issue PAY-2710 --> [!DNL Payment Services] est désormais compatible avec [PHP 8.1](https://www.php.net/releases/8.1/en.php).

![Correction d’un problème](../assets/fix.svg)<!-- Issue PAY-3035 --> Amélioration du passage en caisse d’administration pour le [!DNL Payment Services] extension .

![Correction d’un problème](../assets/fix.svg)<!-- Issue PAY-3017 --> Amélioration de l’alerte du mode sandbox pour afficher les alertes appropriées avec plusieurs magasins.

![Correction d’un problème](../assets/fix.svg)<!-- Issue PAY-2742 --> [!DNL Payment Services] permet d’activer/désactiver les méthodes de paiement disponibles, telles que Venmo, au niveau de l’aperçu.

![Correction d’un problème](../assets/fix.svg)<!-- Issue PAY-2277 --> Amélioration de la capacité du commerçant dans l’administrateur de désactiver/activer sélectivement les boutons intelligents PayPal.

![Correction d’un problème](../assets/fix.svg)<!-- Issue PAY-2561 --> Les produits précédemment supprimés n’apparaissent pas dans le panier sur la page _Ordre de révision_ page.

![Correction d’un problème](../assets/fix.svg)<!-- Issue PAY-2456 --> [!DNL Payment Services] améliore les libellés des modes de paiement dans l’Admin.

![Problème connu](../assets/bug.svg)<!-- Issue PAY-2473 --> Utilisation [clés de compositeur incorrectes](https://support.magento.com/hc/en-us/articles/4406603542541) lors de l’installation de l’extension empêche l’utilisateur de [authentifier](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) avec correct `MAGEID`.

![Problème connu](../assets/bug.svg)<!-- Issue PAY-2474 --> [!DNL Payment Services] [rapports](https://support.magento.com/hc/en-us/articles/4406114741517) pour l’état de paiement des paiements et des commandes, il se peut que la synchronisation ne se produise pas immédiatement.

![Problème connu](../assets/bug.svg)<!-- Issue PAY-2475 --> [Compte sandbox PayPal](https://support.magento.com/hc/en-us/articles/4406954952461) pour [!DNL Payment Services] ne peut pas être vérifié si le compte est créé lors de l’intégration.

![Problème connu](../assets/bug.svg)<!-- Issue PAY-2842 --> [Échec du test de la carte de crédit](https://support.magento.com/hc/en-us/articles/5201041963917) avec PayPal lors du traitement des paiements dans un environnement Sandbox.

## v1.0.0

![Nouveau](../assets/new.svg)<!-- Issue PAY-2127 --> Disponibilité générale [Services de paiement](https://marketplace.magento.com/magento-payment-services.html) est désormais compatible avec [!DNL Adobe Commerce] et [!DNL Magento Open Source] versions 2.4.0 à 2.4.3-p1.

![Nouveau](../assets/new.svg)<!-- Issue PAY-124 --> Le [!DNL Payment Services] extension pour [!DNL Adobe Commerce] et [!DNL Magento Open Source] peut être installé pour [[!DNL Adobe Commerce] sur l’infrastructure cloud](install.md#magento-commerce-cloud) ou [Sur site](install.md#on-premises) instances. Ces méthodes nécessitent l’utilisation d’une interface de ligne de commande.

![Nouveau](../assets/new.svg)<!-- Issue PAY-1986 --> [!DNL Payment Services] prend en charge une [compte sandbox](onboard.md#enable-sandbox-testing) qui permet aux commerçants d’évaluer l’extension en mode test.

![Nouveau](../assets/new.svg)<!-- Issue PAY-666 --> Les commerçants peuvent [configuration des services de paiement](settings.md) l’extension avec des comportements de paiement de base (tels que la capture d’authentification conjointement et le passage d’un environnement de test à un autre ou à un environnement de production).

![Nouveau](../assets/new.svg)<!-- Issue PAY-780 --> Les acheteurs peuvent vérifier avec [!DNL Payment Services] ou vous pouvez passer la commande par téléphone et [création d’une commande entière](create-order.md) dans Admin pour eux.

![Nouveau](../assets/new.svg)<!-- Issue PAY-1856 --> [!DNL Payment Services] proposer des rapports complets aux vendeurs afin que vous puissiez avoir une vue précise de vos commandes et paiements en magasin.

![Nouveau](../assets/new.svg)<!-- Issue PAY-311 --> [!DNL Payment Services] prend en charge des prix à plusieurs niveaux (basés sur TPV) adaptés à n’importe quel commerçant.

![Nouveau](../assets/new.svg)<!-- Issue PAY-1443 --> Il est possible de personnaliser l’aspect des boutons PayPal et les champs CC pour les [Services de paiement](payments-options.md) extension .

![Problème connu](../assets/bug.svg)<!-- Issue PAY-2473 --> Utilisation [clés de compositeur incorrectes](https://support.magento.com/hc/en-us/articles/4406603542541) lors de l’installation de l’extension empêche l’utilisateur de [authentifier](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) avec correct `MAGEID`.

![Problème connu](../assets/bug.svg)<!-- Issue PAY-2474 --> [!DNL Payment Services] [rapports](https://support.magento.com/hc/en-us/articles/4406114741517) pour l’état de paiement des paiements et des commandes, il se peut que la synchronisation ne se produise pas immédiatement.

![Problème connu](../assets/bug.svg)<!-- Issue PAY-2475 --> [Compte sandbox PayPal](https://support.magento.com/hc/en-us/articles/4406954952461) pour [!DNL Payment Services] ne peut pas être vérifié.
