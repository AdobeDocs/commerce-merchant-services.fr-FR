---
title: Installation de l’indexation des prix SaaS
description: Installation de l’indexation des prix SaaS
seo-title: SaaS Price Indexing installation
seo-description: Installing SaaS Price indexing
exl-id: a607e852-aa04-4be3-9576-a6bf45f8751f
source-git-commit: 3820736a25942b147d6e2c7b8820c360d6a0a535
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 0%

---

# Installation de l’indexation des prix SaaS

La configuration de l’indexation des prix SaaS nécessite l’installation de nouveaux modules et l’exécution des commandes de l’interface de ligne de commande. Les administrateurs ont besoin d’un accès en ligne de commande pour terminer cette installation.

## Conditions préalables

* Adobe Commerce 2.4.4+
* Au moins un des services SaaS suivants est installé :

   * [Service de catalogue](../catalog-service/overview.md)
   * [Recherche en direct](../live-search/guide-overview.md)
   * [Recommendations de produit](../product-recommendations/guide-overview.md)

## Installation des modules requis

Selon votre configuration, le processus d’installation peut être légèrement différent.
Il existe des extensions qui ajoutent les nouveaux flux et le code de prise en charge, ainsi qu’une extension qui supprime le flux de prix par défaut.

1. Ajoutez les modules suivants à votre `composer.json` fichier :

   ```json
   "magento/module-saas-price": "102.2.0",
   "magento/module-saas-scopes": "102.2.0",
   "magento/module-product-override-price-remover": "102.2.0",
   "magento/module-bundle-product-override-data-exporter": "102.2.0",
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

Les utilisateurs de Luma et Adobe Commerce Core GraphQL peuvent installer la variable `catalog-adapter` qui fournit la compatibilité Luma et Core GraphQl et désactive l’indexeur de prix de base PHP.
Pour utiliser la variable `catalog-adapter` module, [!DNL Live Search] et [!DNL Catalog Service] doit d’abord être installé et configuré. Suivez la [Installer [!DNL Live Search]](../live-search/install.md) et [Installation du service de catalogue](../catalog-service/installation.md) avant de poursuivre.

Pour configurer la recherche en direct et l’adaptateur de catalogue, procédez comme suit : [Connecteur Commerce Services](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html?lang=en) instructions.

```bash
composer require adobe-commerce/catalog-adapter
```

Si nécessaire, l&#39;indexeur de prix de base PHP peut être réactivé avec la commande suivante :

```bash
bin/magento module:disable Magento_PriceIndexerDisabler
```
