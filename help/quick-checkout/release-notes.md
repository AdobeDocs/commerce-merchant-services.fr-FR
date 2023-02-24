---
title: '''[!DNL Quick Checkout] Notes de mise à jour de'
description: Consultez les notes de mise à jour pour plus d’informations sur toutes les [!DNL Quick Checkout] versions.
exl-id: 511be2fc-d24d-4323-a47a-d376e38a5c47
source-git-commit: b89427124cf76e7f36076454949191ee1d88f52c
workflow-type: tm+mt
source-wordcount: '1329'
ht-degree: 0%

---

# Notes de mise à jour

Ces notes de mise à jour décrivent la version initiale de [!DNL Quick Checkout] et incluent :

![Nouveau](../assets/new.svg) Nouvelles fonctionnalités
![Correction d’un problème](../assets/fix.svg) Correctifs et améliorations
![Problème connu](../assets/bug.svg) Problèmes connus

Voir [Versions à venir](https://devdocs.magento.com/release/) pour en savoir plus sur les calendriers de publication et l’assistance.

Voir [Disponibilité](https://devdocs.magento.com/release/availability.html) dans la documentation destinée aux développeurs pour en savoir plus sur la compatibilité des produits.

## Mises à jour du panneau d’administration

Ces notes de mise à jour décrivent les modifications et correctifs de fonctionnalités qui se sont produits et qui ont été publiés en dehors des versions standard des fonctionnalités pour le panneau d’administration.

+++Mises à jour du panneau d’administration

_14 décembre 2022_

![Correction d’un problème](../assets/fix.svg)<!-- Issue BOLT-524 --> Le [!DNL Quick Checkout] Le panneau d’administration affiche désormais le total correct des commandes et les informations de création de rapports mises à jour.

_30 novembre 2022_

![Nouveau](../assets/new.svg)<!-- Issue BOLT-502 --> Maintenant, le [reporting](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html) a un nouveau paramètre prédéfini &quot;L’année dernière&quot;.

![Nouveau](../assets/new.svg)<!-- Issue BOLT-471 --> Améliorations de l’expérience utilisateur dans [!DNL Quick Checkout] Pour plus d’informations sur le panneau d’administration, voir [Infobulles](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html).

![Correction d’un problème](../assets/fix.svg)<!-- Issue BOLT-514 --> Améliorations de l’expérience utilisateur dans [!DNL Quick Checkout] Le panneau d’administration affiche le nombre total de commandes correct, la cohérence des couleurs et les légendes correctes pour tous les graphiques.

_2 novembre 2022_

![Nouveau](../assets/new.svg)<!-- Issue BOLT-293 --> Maintenant, le [reporting](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html) dans le [!DNL Quick Checkout] Le panneau d’administration affiche des graphiques et des informations de rapport sur les statistiques d’expérience de passage en caisse de votre magasin.

![Nouveau](../assets/new.svg)<!-- Issue BOLT-422 --> Le [_Présentation_](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html#reports-overview) La section de la rubrique Rapports affiche des informations détaillées sur les performances de passage en caisse de votre magasin, notamment le temps moyen de passage en caisse, les nouveaux comptes créés lors du passage en caisse et l’abandon du passage en caisse.

![Nouveau](../assets/new.svg)<!-- Issue BOLT-423 --> Le [_Tendances_](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html#reports-trends) La section de l’onglet Rapports affiche les tendances de votre expérience de passage en caisse filtrées par type de compte et les nouveaux comptes créés lors du passage en caisse.

![Nouveau](../assets/new.svg)<!-- Issue BOLT-439 --> Le **Rapports** affichage des onglets [paramètres prédéfinis de filtre par défaut](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html#filter-data) qui peut être utilisé pour afficher des plages de données spécifiques.

![Nouveau](../assets/new.svg)<!-- Issue BOLT-433 --> Vous pouvez désormais voir une _Aucune donnée disponible_ pour un graphique lorsqu’une requête ne renvoie aucune donnée.

![Nouveau](../assets/new.svg)<!-- Issue BOLT-473 --> Améliorations de l’expérience utilisateur de [!DNL Quick Checkout] Le panneau d’administration permet d’activer une [suivi de passage en caisse](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/settings-quick-checkout.html#service-settings) qui permet à Adobe Commerce de partager des informations de rapport avec Bolt.

_5 octobre 2022_

![Nouveau](../assets/new.svg)<!-- Issue BOLT-379 --> Maintenant, lorsqu’un nouveau commerçant accède à la variable [!DNL Quick Checkout] Pour la première fois, un panneau d’administration [présentation guidée par Gainsight](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html) apparaît.

![Nouveau](../assets/new.svg)<!-- Issue BOLT-377 --> Le **Rapports** dans le [!DNL Quick Checkout] Le panneau d’administration affiche des graphiques et des analyses des rapports.

![Nouveau](../assets/new.svg)<!-- Issue BOLT-377 --> Le **Rapports** dans le [!DNL Quick Checkout] Le panneau d’administration affiche la période et les paramètres prédéfinis de filtre pour les graphiques et les analyses de rapports.

![Correction d’un problème](../assets/fix.svg)<!-- Issue BOLT-369 --> Maintenant, le [[!DNL Quick Checkout] Panneau d’administration](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) affiche la version de l’application dans le pied de page.

+++

## v1.8.0

_24 février 2023_

![Correction d’un problème](../assets/fix.svg)<!-- Issue BOLT-592 --> Améliorations de l’expérience utilisateur lors du placement d’une commande dans la variable [Panneau d’administration](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/create-order-admin.html) using [Braintree](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/payments/stored-payment-methods.html) comme mode de paiement. Cette fonctionnalité permet aux clients de passer une commande avec Braintree comme mode de paiement lors de l’extraction. [!DNL Quick Checkout] est activée.

## v1.7.0

_22 février 2023_

![Correction d’un problème](../assets/fix.svg)<!-- Issue AC-8002 --> Améliorations de l’expérience utilisateur lors du placement d’une commande à l’aide d’une [Multidiffusion](https://experienceleague.adobe.com/docs/commerce-admin/config/sales/multishipping-settings.html) . Cette fonctionnalité permet d’afficher les méthodes de paiement lors de l’extraction. [!DNL Quick Checkout] est activée.

## v1.6.0

_9 février 2023_

![Correction d’un problème](../assets/fix.svg)<!-- Issue BOLT-567 --> Améliorations de l’expérience utilisateur lors de la [placement d’une commande](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html) en utilisant la variable [Diffusion en magasin](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/delivery/basic-methods/shipping-in-store-delivery.html) avec la méthode [!DNL Quick Checkout] désactivé.

![Correction d’un problème](../assets/fix.svg)<!-- Issue BOLT-569 --> Améliorations de la fonctionnalité de déconnexion qui permet aux acheteurs de [déconnexion du réseau Bolt](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/user-session-lifetime.html).

## v1.5.0

_18 janvier 2023_

![Nouveau](../assets/new.svg)<!-- Issue BOLT-522 --> Une nouvelle configuration peut être activée/désactivée pour détecter si [acheteurs](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/manage-checkout/checkout-options/checkout-adobe-commerce.html) peut être automatiquement connecté à Bolt.

![Nouveau](../assets/new.svg)<!-- Issue BOLT-523 --> Une nouvelle configuration peut être activée/désactivée, ce qui permet aux commerçants de spécifier si les acheteurs peuvent être automatiquement connectés aux deux réseaux, ou simplement au réseau Bolt.

![Correction d’un problème](../assets/fix.svg)<!-- Issue BOLT-542 --> Améliorations de l’expérience utilisateur lors de la [enregistrement d’une carte ou d’une adresse sur un compte Bolt](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html) lorsqu’un acheteur fournit un courrier électronique.

![Correction d’un problème](../assets/fix.svg)<!-- Issue BOLT-550 --> Améliorations de l’expérience utilisateur dans [connexion automatique](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#configure-service-settings) lorsqu’un utilisateur Bolt fournit un courrier électronique.

![Correction d’un problème](../assets/fix.svg)<!-- Issue BOLT-544 --> Améliorations de la compatibilité pour [URL de rappel](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#check-shopper-valid-account) avec [multi-sites](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/multi-sites/ms-overview.html) à Bolt.

## v1.4.0

_30 novembre 2022_

![Nouveau](../assets/new.svg)<!-- Issue BOLT-513 --> Désormais, lorsqu’un client Adobe Commerce est connecté au magasin pendant le processus de passage en caisse et dispose d’un compte Bolt, une option de connexion au compte Bolt du nouvel acheteur s’affiche.

![Nouveau](../assets/new.svg)<!-- Issue BOLT-512 --> Une nouvelle configuration détecte automatiquement si les clients connectés peuvent également être connectés à Bolt.

![Nouveau](../assets/new.svg)<!-- Issue BOLT-480 --> Une nouvelle configuration dans le [!DNL Quick Checkout] Le panneau d’administration vous permet de modifier le flux de navigation par défaut en **Expédition** une fois qu’un client Bolt s’est connecté. Par défaut, il est configuré sur la variable **Paiements** page.

## v1.3.0

_2 novembre 2022_

![Nouveau](../assets/new.svg)<!-- Issue BOLT-293 --> Maintenant, [!DNL Quick Checkout] inclut la possibilité d’activer une [suivi de passage en caisse](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/settings-quick-checkout.html#service-settings) qui permet à Adobe Commerce de partager des informations de rapport avec Bolt.

![Nouveau](../assets/new.svg)<!-- Issue BOLT-461 --> Vous pouvez maintenant voir un message d’avertissement dans votre [!DNL Quick Checkout] Panneau d’administration si [suivi de passage en caisse](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html) est désactivée.

## v1.2.0

_8 septembre 2022_

![Nouveau](../assets/new.svg)<!-- Issue BOLT-341 --> Disponibilité générale -[[!DNL Quick Checkout]](https://marketplace.magento.com/magento-quick-checkout.html) est désormais compatible avec les versions 2.4.5 d’Adobe Commerce.

![Nouveau](../assets/new.svg)<!-- Issue BOLT-328 --> [!DNL Quick Checkout] pour Adobe Commerce et Magento Open Source , fournit une [Vue du panneau d’administration](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/admin-panel.html) avec toutes les informations nécessaires pour configurer et utiliser l’extension.

![Nouveau](../assets/new.svg)<!-- Issue BOLT-364 --> Un utilisateur administrateur [peut configurer des rôles utilisateur et des autorisations.](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/user-roles-setup.html) pour permettre à d’autres utilisateurs d’afficher la variable [!DNL Quick Checkout] Panneau d’administration.

![Nouveau](../assets/new.svg)<!-- Issue BOLT-377 --> [!DNL Quick Checkout] Le panneau d’administration contient désormais un en-tête de page qui comprend des sections spécifiques, telles que **Présentation**, **Rapports**, et **Paramètres**.

![Nouveau](../assets/new.svg)<!-- Issue BOLT-379 --> Lorsqu’un nouveau commerçant accède à la variable [!DNL Quick Checkout] Panneau d’administration pour la première fois qu’un widget Bienvenue s’affiche, qui fournit une présentation des fonctionnalités.

![Nouveau](../assets/new.svg)<!-- Issue BOLT-378 --> [!DNL Quick Checkout] [Vue du panneau d’administration](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/admin-panel.html) incorpore une **Configuration** qui s’affiche lorsque l’API et les clés publiables ne sont pas fournies dans la variable [Paramètres](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) vue.

![Nouveau](../assets/new.svg)<!-- Issue BOLT-380 --> [!DNL Quick Checkout] [Vue du panneau d’administration](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/admin-panel.html) incorpore une **Ressources** qui varie en fonction de l’étape d’intégration.

![Nouveau](../assets/new.svg)<!-- Issue BOLT-381 --> [!DNL Quick Checkout] [Vue du panneau d’administration](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/admin-panel.html) inclut une **Aide et assistance** .

![Correction d’un problème](../assets/fix.svg)<!-- Issue BOLT-369 --> Le [[!DNL Quick Checkout] Panneau d’administration](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) affiche désormais la version de l’extension dans le pied de page.

## v1.1.0

_12 août 2022_

![Correction d’un problème](../assets/fix.svg)<!-- Issue BOLT-375 --> Améliorations de l’expérience utilisateur dans [[!DNL Quick Checkout] Panneau d’administration](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) maintenant inclure uniquement les paramètres visibles et validés lorsque l’extension est activée.

![Correction d’un problème](../assets/fix.svg)<!-- Issue BOLT-349 --> Améliorations de la compatibilité pour les adresses de livraison existantes avec le portefeuille Bolt.

## v1.0.0

_9 août 2022_

![Nouveau](../assets/new.svg)<!-- Issue BOLT-341 --> Disponibilité générale -[[!DNL Quick Checkout]](https://marketplace.magento.com/magento-quick-checkout.html) est désormais compatible avec les versions 2.4.1 à 2.4.4 d’Adobe Commerce.

![Nouveau](../assets/new.svg)<!-- Issue BOLT-340 --> Le [!DNL Quick Checkout] pour Adobe Commerce peut être installé pour Adobe Commerce [sur l’infrastructure cloud](install.md#adobe-commerce-on-cloud-infrastructure) ou [sur site](install.md#on-premises) instances. Ces méthodes nécessitent l&#39;utilisation d&#39;une interface de ligne de commande.

![Nouveau](../assets/new.svg)<!-- Issue BOLT-1 --> Le [!DNL Quick Checkout] pour Adobe Commerce apporte une vitrine optimisée qui permet d’obtenir une [expérience de passage en caisse en un clic](overview.md) sans champ de remplissage requis pour les consommateurs.

![Nouveau](../assets/new.svg)<!-- Issue BOLT-1 --> Le [!DNL Quick Checkout] pour Adobe Commerce reconnaît automatiquement chaque acheteur dans son réseau pour [achats en un clic](checkout-flow.md) directement sur votre site.

![Nouveau](../assets/new.svg)<!-- Issue BOLT-1 --> Le [!DNL Quick Checkout] pour Adobe Commerce, un acheteur peut être simultanément [Connecté aux réseaux Adobe Commerce et Bolt](checkout-flow.md/#quick-checkout-use-cases) afin de fournir un meilleur `one-click checkout` expérience.

![Nouveau](../assets/new.svg)<!-- Issue BOLT-218 --> [!DNL Quick Checkout] pour Adobe Commerce prend en charge une [compte sandbox](testing.md#testing-in-sandbox) qui permet aux commerçants d’évaluer l’extension en mode test.

![Nouveau](../assets/new.svg)<!-- Issue BOLT-780 --> Vos acheteurs peuvent les extraire via le [[!DNL Quick Checkout]](checkout-page.md) ou via une extension [création manuelle de commande](create-order-admin.md).

![Nouveau](../assets/new.svg)<!-- Issue BOLT-666 --> Les vendeurs peuvent configurer la variable [!DNL Quick Checkout] avec des actions de paiement de base, telles que [`Authorize and Capture` ou `Authorize` ](onboarding.md#complete-admin-configuration)ou le passage d’un environnement de test à un autre.

![Nouveau](../assets/new.svg)<!-- Issue BOLT-288 --> Personnalisé [durée de la session utilisateur](user-session-lifetime.md) pour [!DNL Quick Checkout] pour Adobe Commerce.

![Correction d’un problème](../assets/fix.svg)<!-- Issue BOLT-375 --> Améliorations de l’expérience utilisateur dans [[!DNL Quick Checkout] Panneau d’administration](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) vous permet d’enregistrer votre configuration lorsque tous les paramètres requis sont fournis.

![Problème connu](../assets/bug.svg)<!-- Issue BOLT-342 --> Courant [dépannage](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/quick-checkout-issues.html) problèmes lors de l’installation de [!DNL Quick Checkout].
