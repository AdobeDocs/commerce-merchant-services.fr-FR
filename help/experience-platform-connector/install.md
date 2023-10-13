---
title: Installation de Adobe Experience Platform Connector
description: Découvrez comment installer, mettre à jour et désinstaller Adobe Experience Platform Connector à partir d’Adobe Commerce.
exl-id: e78e8ab0-8757-4ab6-8ee1-d2e137fe6ced
role: Admin, Developer
feature: Install
source-git-commit: 24494546d6d21cf46e3cb9f0fdd503ec8007daf8
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---

# Installer le connecteur Adobe Experience Platform

Avant d’installer l’extension, [revoir les conditions préalables](overview.md#prereqs).

## Installation de l’extension

L’extension Experience Platform Connector est disponible à partir de la [Adobe Marketplace](https://commercemarketplace.adobe.com/magento-experience-platform-connector.html). Lorsque vous installez cette extension à partir de la ligne de commande du serveur, elle se connecte à votre installation Adobe Commerce en tant que [service](../landing/saas.md). Une fois le processus terminé, **Connecteur Experience Platform** et **Connecteur Commerce Services** apparaissent sur le **Système** sous **Services** dans Commerce _Administration_.

>[!NOTE]
>
>![B2B pour Adobe Commerce](../assets/b2b.svg) Pour les commerçants B2B, vous devez installer une extension distincte. Cette extension ajoute la prise en charge des événements spécifiques B2B. [En savoir plus](#install-the-b2b-extension).

1. Pour télécharger le `experience-platform-connector` , exécutez les éléments suivants à partir de la ligne de commande :

   ```bash
   composer require magento/experience-platform-connector
   ```

   Ce métapaquage contient les modules et extensions suivants :

   * `module-experience-connector-admin` - Met à jour l’interface utilisateur d’administration afin que vous puissiez sélectionner l’identifiant de flux de données pour une instance Adobe Commerce spécifique.
   * `module-experience-connector` - Définit la variable `Organization ID` et `datastreamId` dans le SDK des événements Storefront.
   * `data-services` - Fournit un contexte d’attribut pour les événements storefront. Par exemple, lorsqu’un événement de passage en caisse se produit, des informations sur le nombre d’articles figurant dans le panier et les données d’attribut de produit pour ces articles sont incluses.
   * `services-id` - Connecte votre instance Adobe Commerce à [Adobe Commerce SaaS](../landing/saas.md) à l’aide de l’environnement de test et des clés d’API de production, ainsi qu’à Adobe Experience Platform, pour récupérer l’identifiant de l’organisation IMS.
   * `orders-connector` - Connecte le service d’état de la commande à votre instance Adobe Commerce.

1. (Facultatif) Pour inclure [!DNL Live Search] , qui comprend [événements de recherche](events.md#search-events), installez le [[!DNL Live Search]](../live-search/install.md) extension .

### Configuration du connecteur des commandes

Après avoir installé la variable `experience-platform-connector`, vous devez finaliser l’installation du `orders-connector` module basé sur le type de déploiement : infrastructure sur site ou Adobe Commerce on Cloud.

#### Sur site

Dans les environnements locaux, vous devez activer manuellement la génération de code et les événements Adobe Commerce :

```bash
bin/magento events:generate:module
bin/magento module:enable Magento_AdobeCommerceEvents
bin/magento setup:upgrade
bin/magento setup:di:compile
bin/magento config:set adobe_io_events/eventing/enabled 1
```

#### Sur l’infrastructure cloud

Dans l’infrastructure Adobe Commerce on Cloud, activez la variable `ENABLE_EVENTING` variable globale dans `.magento.env.yaml`. [En savoir plus](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-global.html#enable_eventing).

```bash
stage:
   global:
      ENABLE_EVENTING: true
```

Validez et envoyez les fichiers mis à jour dans l’environnement cloud. Lorsque le déploiement est terminé, activez l’envoi d’événements avec la commande suivante :

```bash
bin/magento config:set adobe_io_events/eventing/enabled 1
```

### Installation de l’extension B2B

Pour les marchands B2B, installez l’extension suivante pour inclure [liste des demandes](events.md#b2b-events) données d’événement.

Téléchargez la `magento/experience-platform-connector-b2b` en exécutant les éléments suivants à partir de la ligne de commande :

```bash
composer require magento/experience-platform-connector-b2b
```

## Mettre à jour le connecteur Experience Platform {#update}

Pour mettre à jour le connecteur Experience Platform, exécutez la ligne de commande suivante :

```bash
composer update magento/experience-platform-connector --with-dependencies
```

ou, pour les marchands B2B :

```bash
composer update magento/experience-platform-connector-b2b --with-dependencies
```

Pour effectuer une mise à jour vers une version majeure, telle que de la version 2.0.0 à la version 3.0.0, modifiez la racine du projet. [!DNL Composer] `.json` comme suit :

1. Ouvrez la racine `composer.json` fichier et recherchez `magento/experience-platform-connector`.

1. Dans le `require` , mettez à jour le numéro de version comme suit :

   ```json
   "require": {
      ...
      "magento/experience-platform-connector": "^3.0",
      ...
    }
   ```

1. **Enregistrer** `composer.json`. Exécutez ensuite la commande suivante à partir de la ligne de commande :

   ```bash
   composer update magento/experience-platform-connector –-with-dependencies
   ```

   ou, pour les marchands B2B :

   ```bash
   composer update magento/experience-platform-connector-b2b --with-dependencies
   ```

## Désinstallation du connecteur Experience Platform {#uninstall}

Pour désinstaller le connecteur Experience Platform, voir [désinstallation des modules](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html).
