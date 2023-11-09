---
title: Extension de l’adaptateur de catalogue
description: Utilisation de l’adaptateur de catalogue pour effectuer le rendu des prix à partir de Commerce Services
seo-title: Catalog Adapter Extension
seo-description: Using Catalog Adapter to render prices from Commerce Services
source-git-commit: a637ece6e806771dfc6359dacececf8ccf05b983
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%

---


# Adaptateur de catalogue

La variable `Catalog Adapter` L’extension désactive l’indexeur de prix de produit Adobe Commerce par défaut et utilise à la place les prix fournis à partir de la variable [Service de catalogue](../catalog-service/overview.md).
L’indexeur de prix des produits Adobe Commerce est désactivé et ne peut pas être activé si ces modules d’extension sont installés. Ce n’est qu’en supprimant ou en désactivant cette extension que l’indexeur de prix de produit par défaut peut être réactivé.

## Conditions

* Adobe Commerce 2.4.4+
* Vous devez installer les deux services Commerce suivants :

   * [Service de catalogue](../catalog-service/overview.md)
   * [Recherche en direct](../live-search/guide-overview.md)

## Installation

Pour utiliser la variable `catalog-adapter` module, [!DNL Live Search] et [!DNL Catalog Service] doit d’abord être installé et configuré. Suivez la [Installer [!DNL Live Search]](../live-search/install.md) et [Installation du service de catalogue](../catalog-service/installation.md) avant de poursuivre.

Une fois ces services installés, exécutez la commande suivante :

```bash
composer require adobe-commerce/catalog-adapter
```

## Réactivez l’indexeur de prix des produits Adobe Commerce

Si des applications tierces dépendent de l’indexeur de prix des produits Adobe Commerce par défaut, elles peuvent être réactivées à l’aide des commandes suivantes :

```bash
# re-enable Product Price indexer
bin/magento module:disable Magento_PriceIndexerDisabler
# re-index Product Price indexer 
bin/magento index:reindex catalog_product_price
```

## Désactivation de l’indexeur de prix de produit pour le scénario Storefront sans affichage

Si vous disposez d’une instance Commerce sans interface utilisateur graphique, vous devrez peut-être désactiver l’indexeur de prix des produits Adobe Commerce pour réduire la charge sur votre instance Adobe Commerce.
Pour ce faire, installez le `magento/module-price-indexer-disabler` module :

```bash
composer require magento/module-price-indexer-disabler
```

## Scénarios d’utilisation

Voici quelques exemples courants `Catalog Adapter` scénarios.

### Aucune dépendance sur l’indexeur de prix de produit Adobe Commerce

* Vous êtes un commerçant Luma ou Adobe Commerce Core GraphQL qui a installé le service requis (Live Search, Recommendations produit, Catalog Service).
* Aucune extension tierce reposant sur l’indexeur de prix de produit Adobe Commerce

1. Installez l’adaptateur de catalogue.

### Avec dépendances sur l’indexeur de prix de produit Adobe Commerce

* Vous êtes un commerçant Luma ou Adobe Commerce Core GraphQL qui a installé un service pris en charge (Live Search, Recommendations produit, Catalog Service).
* Vous utilisez une extension tierce basée sur l’indexeur de prix des produits Adobe Commerce.

1. Installez l’adaptateur de catalogue.
1. Réactivez l’indexeur de prix de produit Adobe Commerce par défaut.

### Instances Commerce sans tête

* Un commerçant avec une instance Commerce sans interface utilisateur graphique avec les services requis installés (Live Search, Recommendations produit, Catalog Service)
* Ne pas dépendre de l’indexeur de prix de produit Adobe Commerce par défaut

1. Installez le `magento/module-price-indexer-disabler` du module de l’adaptateur de catalogue.
