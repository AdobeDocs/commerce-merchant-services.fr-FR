---
title: Installation et configuration de Adobe Experience Platform Connector depuis Adobe Commerce
description: Découvrez comment installer, configurer, mettre à jour et désinstaller Adobe Experience Platform Connector à partir d’Adobe Commerce.
exl-id: e78e8ab0-8757-4ab6-8ee1-d2e137fe6ced
source-git-commit: c7344efead97b0562a146f096123dd84f998fd5e
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 0%

---

# Installation et configuration du connecteur Experience Platform

Avant d’installer l’extension, [revoir les conditions préalables](overview.md#prereqs).

## Installation de l’extension

L’extension Experience Platform Connector est installée à partir de la ligne de commande du serveur et se connecte à votre installation Adobe Commerce en tant que [service](../landing/saas.md). Une fois le processus terminé, **Connecteur Experience Platform** apparaît sur la **Système** sous **Services** dans Commerce _Administration_.

Le connecteur Experience Platform est installé en tant qu’extension à partir de [Adobe Marketplace](https://marketplace.magento.com/magento-experience-platform-connector.html).

1. Pour télécharger le `experience-platform-connector` , exécutez les éléments suivants à partir de la ligne de commande :

   ```bash
   composer require magento/experience-platform-connector
   ```

   Ce métappackage contient les modules et extensions suivants :

   * `module-platform-connector-admin` - Met à jour l’interface utilisateur d’administration afin que vous puissiez sélectionner l’identifiant de flux de données pour une instance Adobe Commerce spécifique.
   * `module-platform-connector` - Définit la variable `ImsOrgId` et `datastreamId` dans le SDK Adobe Commerce Storefront Event
   * `data-services` - Fournit un contexte d’attribut pour les événements storefront. Par exemple, lorsqu’un événement de passage en caisse se produit, des informations sur le nombre d’articles figurant dans le panier et les données d’attribut de produit pour ces articles sont incluses.
   * `services-id` - Connecte votre instance Adobe Commerce à [Adobe Commerce SaaS](../landing/saas.md) à l’aide des clés d’API de test et de production et de Adobe Experience Platform pour récupérer l’ID d’organisation IMS ;

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
