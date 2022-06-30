---
title: Installation et configuration de Adobe Experience Platform Connector depuis Adobe Commerce
description: Découvrez comment installer, configurer, mettre à jour et désinstaller Adobe Experience Platform Connector à partir d’Adobe Commerce.
exl-id: e78e8ab0-8757-4ab6-8ee1-d2e137fe6ced
source-git-commit: b503c369f12696a2a791af77055a7b53000b827f
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%

---

# Installation et configuration du connecteur Experience Platform

Avant d’installer l’extension, [revoir les conditions préalables](overview.md#prereqs).

## Installation de l’extension

1. Installez le métaphorage du connecteur Experience Platform.

   ```bash
   composer require magento/experience-platform-connector
   ```

   Ce métappackage contient les modules et extensions suivants :

   * `module-platform-connector-admin` - Met à jour l’interface utilisateur d’administration afin que vous puissiez configurer l’identifiant de la banque de données
   * `module-platform-connector` - Définit la variable `ImsOrgId` et `datastreamId` dans le SDK Adobe Commerce Storefront Event
   * `data-services` - Fournit un contexte d’attribut pour les événements storefront. Par exemple, lorsqu’un événement de passage en caisse se produit, des informations sur le nombre d’articles figurant dans le panier et les données d’attribut de produit pour ces articles sont incluses.
   * `commerce-services` - Connecte votre instance Adobe Commerce à [Adobe Commerce SaaS](../landing/saas.md) utilisation des clés d’API de test et de production et de Adobe Experience Platform à l’aide de l’identifiant de l’organisation IMS

1. (Facultatif) Pour inclure [!DNL Live Search] , qui comprend les événements de recherche, installez la variable [[!DNL Live Search]](../live-search/install.md) extension .

## Mettre à jour le connecteur Experience Platform {#update}

Pour mettre à jour le connecteur Experience Platform, exécutez la ligne de commande suivante :

```bash
composer update magento/experience-platform-connector --with-dependencies
```

Pour effectuer une mise à jour vers une version majeure, telle que de 1.0.0 à 2.0.0, modifiez la racine du projet. [!DNL Composer] `.json` comme suit :

1. Ouvrez la racine `composer.json` fichier et recherchez `magento/platform-connector`.

1. Dans le `require` , mettez à jour le numéro de version comme suit :

   ```json
   "require": {
      ...
      "magento/experience-platform-connector": "^2.0",
      ...
    }
   ```

1. **Enregistrer** `composer.json`. Exécutez ensuite la commande suivante à partir de la ligne de commande :

   ```bash
   composer update magento/experience-platform-connector –-with-dependencies
   ```

## Désinstallation du connecteur Experience Platform {#uninstall}

Pour désinstaller le connecteur Experience Platform, reportez-vous à la section [désinstallation des modules](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-uninstall-mods.html).
