---
title: Installation manuelle de l’indexation des prix SaaS
description: Installation de l’indexation des prix SaaS pour une ancienne version
seo-title: SaaS Price Indexing installation
seo-description: Installing SaaS Price indexing
exl-id: a607e852-aa04-4be3-9576-a6bf45f8751f
role: Admin, Developer
source-git-commit: b7989b416f852d2c7164d21e8f0598373662b760
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 0%

---

# Installation manuelle de l’indexation des prix SaaS

L’indexation des prix SaaS est disponible prête à l’emploi pour la prise en charge [dernière version](index.md#Requirements) de Commerce Services.
Si vous ne disposez pas de la dernière version et souhaitez activer l’indexation des prix SaaS pour votre instance Adobe Commerce, veuillez utiliser ce mini-guide.

## Conditions préalables

* Adobe Commerce 2.4.4+
* Au moins un des services SaaS suivants est installé :

   * [Service de catalogue](../catalog-service/overview.md)
   * [Recherche en direct](../live-search/guide-overview.md)
   * [Recommendations de produit](../product-recommendations/guide-overview.md)

## Installation des modules requis

Selon votre configuration, le processus d’installation peut être légèrement différent.
Il existe des extensions qui ajoutent les nouveaux flux et le code qui les prend en charge.

1. Ajoutez les modules suivants à votre `composer.json` fichier :

   ```json
   "magento/module-saas-price": "^103.0",
   "magento/module-saas-scopes": "^103.0",
   "magento/module-bundle-product-override-data-exporter": "^103.0",
   "magento/module-gift-card-product-data-exporter": "^103.0",
   ```

1. Exécutez la commande de mise à niveau :

   ```bash
   bin/magento setup:upgrade
   ```

Après la mise à niveau, trois nouveaux flux sont disponibles :

* `prices` - responsable de la diffusion des données de prix au service
* `scopesCustomerGroup` : responsable de la diffusion des groupes de clients au service
* `scopesWebsite` : responsable de la diffusion des sites web, des groupes de magasins et des vues de magasin au service.


1. Configurez les nouveaux flux à définir en mode &quot;Mise à jour selon le calendrier&quot; :

   ```bash
   bin/magento indexer:set-mode schedule catalog_data_exporter_product_prices scopes_customergroup_data_exporter scopes_website_data_exporter
   ```

1. Réindexez les nouveaux flux :

   ```bash
   bin/magento saas:resync --feed=scopesCustomerGroup
   bin/magento saas:resync --feed=scopesWebsite
   bin/magento saas:resync --feed=prices
   ```

Exécutez les indexeurs ci-dessus manuellement, si nécessaire. Dans le cas contraire, les données sont actualisées dans le processus de synchronisation standard. En savoir plus sur les [Synchronisation du catalogue](../landing/catalog-sync.md) service.


Pour configurer la recherche en direct et l’adaptateur de catalogue, suivez la [Connecteur Commerce Services](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) instructions.

## Avertissements

Avant `103.0.0` version, l’indexation des prix SaaS prenait en charge les types de produits simples, groupés, virtuels, configurables et dynamiques de lot.
La prise en charge des types de produits téléchargeables, Gift Cards et Bundle Fixe est disponible à partir de `magento/module-saas-price:103.0.0` version et disponible prêt à l’emploi pour les services de commerce pris en charge.

Les nouveaux flux doivent être synchronisés manuellement avec la variable `resync` [Commande CLI](../landing/catalog-sync.md#resynccmdline). Dans le cas contraire, les données sont actualisées dans le processus de synchronisation standard. Obtenez plus d’informations sur la variable [Synchronisation du catalogue](../landing/catalog-sync.md) processus.