---
title: "[!DNL Payment Services] Notes de mise à jour"
description: Consultez les notes de mise à jour pour plus d’informations sur toutes les [!DNL Payment Services] versions.
exl-id: 104aa2c7-7735-4ac2-8ed1-a03cd9911273
source-git-commit: 77fbe32ec285bd6ab55100971459f685e19f8425
workflow-type: tm+mt
source-wordcount: '1208'
ht-degree: 0%

---

# Notes de mise à jour

Ces notes de mise à jour décrivent la version initiale de [!DNL Payment Services] et incluent :

![Nouveau](../assets/new.svg) Nouvelles fonctionnalités
![Correction d’un problème](../assets/fix.svg) Correctifs et améliorations
![Problème connu](../assets/bug.svg) Problèmes connus

Pour les modifications et correctifs de fonctionnalités publiés en dehors de la version standard des fonctionnalités, consultez la ou les sections Mises à jour du service hébergé .

Voir [Versions à venir](https://devdocs.magento.com/release/) pour en savoir plus sur les calendriers de publication et l’assistance.

Voir [Disponibilité](https://devdocs.magento.com/release/availability.html) dans la documentation destinée aux développeurs pour en savoir plus sur la compatibilité des produits.

## Mises à jour du service hébergé

Ces notes de mise à jour décrivent les modifications et correctifs de fonctionnalités qui se sont produits et qui ont été publiés en dehors des versions régulières des fonctionnalités pour le service hébergé.

+++Mises à jour du service hébergé

_12 septembre 2022_

![Nouveau](../assets/new.svg)<!-- Issue PAY-3705 --> Le `increment_id` est désormais disponible pour être utilisé dans le cadre de la réconciliation des paiements dans les systèmes ERP externes. Il est propagé vers la variable [`custom_id` _et_ `invoice_id`](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/data.html#reconcile-with-erp-system), visible dans le webhook PayPal et dans le détail de l’activité commerciale pour un paiement.

_31 août 2022_

![Correction d’un problème](../assets/fix.svg)<!-- Issue PAY-3629 --> Lorsqu’un nouveau commerçant accède pour la première fois à la page d’accueil des services de paiement, la page se charge désormais immédiatement pour afficher le contenu au lieu de devoir actualiser la page.

_9 août 2021_

![Nouveau](../assets/new.svg)<!-- Issue PAY-3420 --> Le paiement Apple est désormais disponible sous la forme d’un bouton PayPal Smart. Ceci [option de paiement](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-options.html#apple-pay-button) permet aux clients d’utiliser la fonctionnalité d’identifiant tactile de leur appareil iOS ou macOS pour sélectionner Apple Pay. Apple Pay traite le paiement à l’aide des informations d’identification de paiement de carte de crédit et de débit stockées sur l’appareil.

_28 juin 2021_

![Nouveau](../assets/new.svg)<!-- Issue PAY-1720 --> Les litiges relatifs aux commandes de magasins sont désormais disponibles dans [le rapport État du paiement de la commande](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html#view-disputes). Vous pouvez agir en cas de conflit en accédant directement au centre de résolution PayPal à partir de [!DNL Payment Services].

![Nouveau](../assets/new.svg)<!-- Issue PAY-2854 --> Améliorations de l’expérience utilisateur à partir de [!DNL Payment Services] Accueil permet de modifier une configuration au niveau de l’héritage actuel et améliore l’affichage de l’en-tête et de la navigation.

![Nouveau](../assets/new.svg)<!-- Issue PAY-2854 --> Vous pouvez désormais voir des avertissements lorsque vous passez du mode sandbox au mode de production et lorsque vous tentez de quitter une vue avec des mises à jour qui n’ont pas été enregistrées.

![Nouveau](../assets/new.svg)<!-- Issue PAY-2761 --> Vous pouvez désormais personnaliser les données qui s’affichent dans la variable [Rapport d’état des paiements de commande](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html#show-and-hide-columns) et le [Rapport de paiements](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/payouts.html#show-and-hide-columns) en affichant ou en masquant les colonnes à l’aide du contrôle Paramètres de colonne .

+++

## v1.4.1

_14 octobre 2022_

![Nouveau](../assets/new.svg)<!-- Issue PAY-3766 --> Lorsque le mode de paiement d’un client est refusé, le message d’erreur visible est plus explicite. Il conseille au client de saisir à nouveau les informations de paiement et de réessayer, d’essayer un autre mode de paiement ou de contacter sa banque au sujet du refus de la transaction.

## v1.4.0

_30 septembre 2022_

![Nouveau](../assets/new.svg)<!-- Issue PAY-784 --> Les services de paiement incluent désormais la possibilité de configurer un compte marchand pour [utiliser plusieurs comptes commerciaux PayPal ;](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#use-multiple-paypal-accounts). Cela permet au commerçant d’exploiter vos magasins dans plusieurs pays à l’aide de différentes devises ou d’utiliser Adobe Commerce pour une partie de votre entreprise.

![Nouveau](../assets/new.svg)<!-- Issue PAY-3231 --> Les commerçants peuvent [ajouter une [!UICONTROL Soft Descriptor]](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#add-soft-descriptor) sur des sites web ou une configuration de vues de boutique individuelles qui s’affichent sur les relevés bancaires des transactions des clients pour délimiter les marques, les magasins ou les lignes de produits.

![Nouveau](../assets/new.svg)<!-- Issue PAY-3707 --> [Activation ou désactivation des champs de carte de crédit et des boutons intelligents PayPal](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#configure-payment-options) pour l’extraction dans les paramètres des services de paiement.

![Correction d’un problème](../assets/fix.svg)<!-- Issue PAY-3546 --> Lorsqu’un client clique **[!UICONTROL Edit cart]**, la page redirige vers la page du panier et affiche les éléments mis à jour au lieu d’afficher un panier vide.

## v1.3.1

_6 septembre 2022_

![Correction d’un problème](../assets/fix.svg)<!-- Issue PAY-3663 --> Désormais, lorsque le magasin d’un commerçant capture une commande autorisée avec une devise non globale, le processus de capture se termine et aucune erreur n’est affichée.

## v1.3.0

_9 août 2022_

![Nouveau](../assets/new.svg)<!-- Issue PAY-XX --> Disponibilité générale -[!DNL Payment Services] est maintenant [compatible avec [!DNL Adobe Commerce] et [!DNL Magento Open Source] versions 2.4.0 à 2.4.5](https://devdocs.magento.com/release/availability.html#compatibility).

![Correction d’un problème](../assets/fix.svg)<!-- Issue PAY-x --> Apple Pay est désormais compatible avec le navigateur Safari v15.5 sur mobile et bureau.

## v1.2.0

_29 juin 2022_

![Problème connu](../assets/bug.svg)<!-- Issue PAY-x --> Apple Pay est incompatible avec le navigateur Safari v15.5 sur mobile et bureau. Lorsque vous utilisez Safari version 15.5, vous ne pouvez pas terminer l’extraction avec Apple Pay.

![Correction d’un problème](../assets/fix.svg)<!-- Issue PAY-3264 --> Auparavant, lorsqu’un utilisateur connecté sélectionnait une autre adresse de facturation/de livraison que l’adresse par défaut de son compte, l’extraction échouait. Correction de ce problème. Désormais, l’adresse de facturation/d’expédition sélectionnée est envoyée (au lieu de l’adresse enregistrée par défaut) et le passage en caisse est terminé avec succès.

![Correction d’un problème](../assets/fix.svg)<!-- Issue PAY-3314 --> Si vous désactivez les boutons intelligents PayPal pour le passage en caisse, aucune erreur ne s’affiche.

![Correction d’un problème](../assets/fix.svg)<!-- Issue PAY-3330 --> Les paiements n’échouent plus lors du passage en caisse lorsqu’un utilisateur invité saisit un numéro de téléphone contenant des tirets.

![Correction d’un problème](../assets/fix.svg)<!-- Issue PAY-3338 PAY-2502 --> Lorsque les informations d’identification de Commerce Services ne sont pas valides, la variable [!DNL Payment Services] La page d’accueil s’affiche désormais dans l’Admin. Une erreur d’identification s’affiche pour vous signaler que vos informations d’identification ne sont pas valides.

![Problème connu](../assets/bug.svg)<!-- Issue PAY-0 --> [!DNL Payment Services] est actuellement incompatible avec `commerce-data-export` v101.20 et versions ultérieures, ce qui le rend incompatible avec la [[!DNL Channel manager] extension](https://experienceleague.adobe.com/docs/commerce-channels/channel-manager/guide-overview.html).

## v1.1.0

_31 mars 2022_

![Nouveau](../assets/new.svg)<!-- Issue PAY-2127 --> Disponibilité générale -[!DNL Payment Services] est maintenant [compatible avec [!DNL Adobe Commerce] et [!DNL Magento Open Source] versions 2.4.0 à 2.4.4](https://devdocs.magento.com/release/availability.html#compatibility).

![Nouveau](../assets/new.svg)<!-- Issue PAY-2682 --> Le [!DNL Payment Services] extension pour [!DNL Adobe Commerce] et [!DNL Magento Open Source] est maintenant disponible pour les commerçants canadiens. Les vendeurs peuvent afficher la configuration des paiements dans l’une des [Français](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html?lang=fr#carte-de-cr%C3%A9dit-et-devises-accept%C3%A9es) ou [Anglais](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html#accepted-credit-cards-and-currencies).

![Nouveau](../assets/new.svg)<!-- Issue PAY-2681 --> [!DNL Payment Services] prend en charge [Dollars canadiens (CAD)](overview.md#accepted-credit-cards-and-currencies) pour les cartes de crédit et les transactions PayPal.

![Nouveau](../assets/new.svg)<!-- Issue PAY-2680 --> Les commerçants peuvent [onboard [!DNL Payment Services]](onboard.md) en anglais ou en français.

![Nouveau](../assets/new.svg)<!-- Issue PAY-2678 --> Les vendeurs peuvent désormais afficher les rapports financiers, à la fois [Statut de paiement de la commande](order-payment-status.md) et [Rapports sur les paiements](payouts.md), en dollars canadiens (CAD).

![Correction d’un problème](../assets/fix.svg)<!-- Issue PAY-2710 --> [!DNL Payment Services] est désormais compatible avec [PHP 8.1](https://www.php.net/releases/8.1/en.php).

![Correction d’un problème](../assets/fix.svg)<!-- Issue PAY-3017 --> Amélioration de l’alerte du mode sandbox pour afficher les alertes appropriées avec plusieurs magasins.

![Correction d’un problème](../assets/fix.svg)<!-- Issue PAY-2742 --> Vous pouvez désormais activer et désactiver les méthodes de paiement disponibles, telles que Venmo, au niveau de la vue du magasin. Auparavant, vous pouviez configurer des méthodes de paiement par site web uniquement.

![Correction d’un problème](../assets/fix.svg)<!-- Issue PAY-2277 --> Vous pouvez désormais sélectionner [activation ou désactivation de boutons intelligents PayPal individuels](settings.md#payment-buttons).

![Correction d’un problème](../assets/fix.svg)<!-- Issue PAY-2561 --> Les produits précédemment supprimés n’apparaissent pas dans le panier sur la page _Ordre de révision_ page.

![Problème connu](../assets/bug.svg)<!-- Issue PAY-2842 --> Test des transactions de carte de crédit [peut échouer avec PayPal](https://support.magento.com/hc/en-us/articles/5201041963917) lors du traitement des paiements dans un environnement de test.

## v1.0.0

_29 novembre 2021_

![Nouveau](../assets/new.svg)<!-- Issue PAY-2127 --> Disponibilité générale -[[!DNL Payment Services]](https://marketplace.magento.com/magento-payment-services.html) est désormais compatible avec [!DNL Adobe Commerce] et [!DNL Magento Open Source] versions 2.4.0 à 2.4.3-p1.

![Nouveau](../assets/new.svg)<!-- Issue PAY-124 --> Le [!DNL Payment Services] extension pour [!DNL Adobe Commerce] et [!DNL Magento Open Source] peut être installé pour [[!DNL Adobe Commerce] sur l’infrastructure cloud](install.md#adobe-commerce-on-cloud-infrastructure) ou [Sur site](install.md#on-premises) instances. Ces méthodes nécessitent l’utilisation d’une interface de ligne de commande.

![Nouveau](../assets/new.svg)<!-- Issue PAY-1986 --> [!DNL Payment Services] prend en charge une [compte sandbox](sandbox.md) qui permet aux commerçants d’évaluer l’extension en mode test.

![Nouveau](../assets/new.svg)<!-- Issue PAY-666 --> Les commerçants peuvent [configuration des services de paiement](settings.md) avec des comportements de paiement de base, tels que l’utilisation de [`Authorize and Capture`](production.md#set-payment-services-as-payment-method) passage d’un environnement de test à un environnement de production.

![Nouveau](../assets/new.svg)<!-- Issue PAY-780 --> Vos acheteurs peuvent vérifier avec [!DNL Payment Services] ou via [création manuelle de commande](create-order.md).

![Nouveau](../assets/new.svg)<!-- Issue PAY-1856 --> Reporting complet, via [Statut de paiement de la commande](order-payment-status.md) et [Rapports sur les paiements](payouts.md), sont disponibles pour [!DNL Payment Services] pour vous donner une vue claire des commandes de votre magasin et des paiements associés.

![Nouveau](../assets/new.svg)<!-- Issue PAY-311 --> [!DNL Payment Services] prend en charge une tarification échelonnée flexible, basée sur le volume total de traitement, adaptée à n’importe quel commerçant.

![Nouveau](../assets/new.svg)<!-- Issue PAY-1443 --> Vous pouvez facilement [personnaliser l’aspect](payments-options.md) des boutons intelligents PayPal et des champs de carte de crédit pour la variable [!DNL Payment Services] extension .

![Problème connu](../assets/bug.svg)<!-- Issue PAY-2473 --> Utilisation [clés de compositeur incorrectes](https://support.magento.com/hc/en-us/articles/4406603542541) lors de l’installation de l’extension empêche l’utilisateur de [authentification](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) avec la valeur correcte `MAGEID`.

![Problème connu](../assets/bug.svg)<!-- Issue PAY-2474 --> [!DNL Payment Services] rapports [peut ne pas se synchroniser immédiatement](https://support.magento.com/hc/en-us/articles/4406114741517).

![Problème connu](../assets/bug.svg)<!-- Issue PAY-2475 --> Votre [Compte sandbox PayPal](https://support.magento.com/hc/en-us/articles/4406954952461) pour [!DNL Payment Services] ne peut pas être vérifié si vous créez ce compte lors de l’intégration.
