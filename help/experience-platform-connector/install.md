---
title: Installation et configuration de Adobe Experience Platform Connector depuis Adobe Commerce
description: Découvrez comment installer, configurer, mettre à jour et désinstaller Adobe Experience Platform Connector à partir d’Adobe Commerce.
source-git-commit: 9b5f2da08167e22bbba504009bccc87d0ab02c48
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%

---

# Installation et configuration du connecteur Experience Platform

Avant d’installer l’extension, [revoir les conditions préalables](overview.md#prereqs).

## Installation de l’extension

1. Installez le métaphorage du connecteur Experience Platform.

   ```bash
   composer require magento/platform-connector
   ```

   Ce métappackage contient les modules suivants :

   * `module-platform-connector-admin` - Mises à jour de l’interface utilisateur d’administration
   * `module-platform-connector` - Définit la variable `ImsOrgId` et `datastreamId` dans le SDK des événements Storefront Magento

1. Installez l’extension Commerce Data Services pour inclure les événements de profil et de passage en caisse.

   ```bash
   composer require magento/data-services
   ```

   L’extension Commerce Data Services fournit un contexte d’attribut pour les événements storefront. Par exemple, lorsqu’un événement de passage en caisse se produit, des informations sur le nombre d’articles figurant dans le panier et les données d’attribut de produit pour ces articles sont incluses.

1. Installez le connecteur Commerce Service.

   ```bash
   composer require magento/commerce-services
   ```

   Commerce Service Connector vous permet de connecter votre instance Adobe Commerce à [Adobe Commerce SaaS](../landing/saas.md) et au Adobe Experience Platform.

1. (Facultatif) Pour inclure [!DNL Live Search] , qui comprend les événements de recherche, installez la variable [[!DNL Live Search]](../live-search/install.md) extension .

## Mettre à jour le connecteur Experience Platform {#update}

Pour mettre à jour le connecteur Experience Platform, exécutez la ligne de commande suivante :

```bash
composer update magento/platform-connector --with-dependencies
```

Pour effectuer une mise à jour vers une version majeure, telle que de 1.0.0 à 2.0.0, modifiez la racine du projet. [!DNL Composer] `.json` comme suit :

1. Ouvrez la racine `composer.json` fichier et recherchez `magento/platform-connector`.

1. Dans le `require` , mettez à jour le numéro de version comme suit :

   ```json
   "require": {
      ...
      "magento/platform-connector": "^2.0",
      ...
    }
   ```

1. **Enregistrer** `composer.json`. Exécutez ensuite la commande suivante à partir de la ligne de commande :

   ```bash
   composer update magento/platform-connector –-with-dependencies
   ```

## Désinstallation du connecteur Experience Platform {#uninstall}

Pour désinstaller le connecteur Experience Platform, reportez-vous à la section [désinstallation des modules](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-uninstall-mods.html).
