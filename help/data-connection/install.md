---
title: Installer [!DNL Data Connection]
description: Découvrez comment installer, mettre à jour et désinstaller l’extension  [!DNL Data Connection] à partir d’Adobe Commerce.
exl-id: e78e8ab0-8757-4ab6-8ee1-d2e137fe6ced
role: Admin, Developer
feature: Install
source-git-commit: 962452b7e3fdfecabe05f5af3d16afd8d24f2740
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# Installer [!DNL Data Connection]

Avant d’installer l’extension, [vérifiez les conditions préalables](overview.md#prereqs).

## Installation de l’extension

L’extension [!DNL Data Connection] est disponible sur [Adobe Marketplace](https://commercemarketplace.adobe.com/magento-experience-platform-connector.html). Lorsque vous installez cette extension à partir de la ligne de commande du serveur, elle se connecte à votre installation Adobe Commerce en tant que [service](../landing/saas.md). Une fois le processus terminé, **[!DNL Data Connection]** et **Commerce Services Connector** apparaissent dans le menu **System** sous **Services** dans Commerce _Admin_.

![[!DNL Data Connection] extension Admin view](assets/epc-adminui.png)

>[!IMPORTANT]
>
>Bien que le nom de l’extension ait été remplacé par [!DNL Data Connection] depuis le connecteur Experience Platform, le nom du package reste `experience-platform-connector` pour prendre en charge la compatibilité ascendante.

1. Pour télécharger le package `experience-platform-connector`, exécutez le suivant à partir de la ligne de commande :

   ```bash
   composer require magento/experience-platform-connector
   ```

   Ce métapaquage contient les modules et extensions suivants :

   - `magento/orders-connector`
   - `magento/data-services`
   - `magento/customers-connector`
   - `magento/module-experience-connector`
   - `magento/module-experience-connector-admin`
   - `magento/module-experience-connector-admin-graph-ql`
   - `magento/module-experience-connector-aep-integration`

1. (Facultatif) Pour inclure des données [!DNL Live Search], qui comprennent [des événements de recherche](events.md#search-events), installez l’extension [[!DNL Live Search]](../live-search/install.md).

1. (Facultatif) Pour inclure des données B2B, qui comprennent [ événements de demande](events.md#b2b-events), installez l’ [extension B2B](#install-the-b2b-extension).

### Installez les événements Adobe I/O et configurez le module customer-connector

Après avoir installé l’extension `experience-platform-connector`, vous devez installer les événements d’Adobe I/O pour Adobe Commerce et configurer le module `customers-connector`.

Les étapes suivantes s’appliquent à Adobe Commerce sur l’infrastructure cloud et aux installations sur site.

1. Si vous exécutez Commerce 2.4.4 ou 2.4.5, utilisez la commande suivante pour charger les modules d’événement :

   ```bash
   composer require magento/commerce-eventing=^1.0 --no-update
   ```

   Commerce 2.4.6 et versions ultérieures chargent ces modules automatiquement.

1. Mettez à jour les dépendances du projet.

   ```bash
   composer update
   ```

1. Activez les nouveaux modules :

   ```bash
   bin/magento module:enable Magento_AdobeCommerceEventsClient Magento_AdobeCommerceEventsGenerator Magento_AdobeIoEventsClient Magento_AdobeCommerceOutOfProcessExtensibility
   ```

Finalisez l’installation en fonction du type de déploiement : Adobe Commerce sur l’infrastructure cloud ou sur site.

#### Sur l’infrastructure cloud

Dans l’infrastructure Adobe Commerce on Cloud, activez la variable globale `ENABLE_EVENTING` dans `.magento.env.yaml`. [En savoir plus](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-global.html#enable_eventing).

```bash
stage:
   global:
      ENABLE_EVENTING: true
```

Validez et envoyez les fichiers mis à jour dans l’environnement cloud. Lorsque le déploiement est terminé, activez l’envoi d’événements avec la commande suivante :

```bash
bin/magento config:set adobe_io_events/eventing/enabled 1
```

#### Sur site

Dans les environnements locaux, vous devez activer manuellement la génération de code et les événements Adobe Commerce :

```bash
bin/magento events:generate:module
bin/magento module:enable Magento_AdobeCommerceEvents
bin/magento setup:upgrade
bin/magento setup:di:compile
bin/magento config:set adobe_io_events/eventing/enabled 1
```

### Installation de l’extension B2B

Pour les commerçants B2B, installez l’extension suivante afin d’inclure les données d’événement [liste de demandes](events.md#b2b-events).

Téléchargez l’extension `magento/experience-platform-connector-b2b` en exécutant les opérations suivantes à partir de la ligne de commande :

```bash
composer require magento/experience-platform-connector-b2b
```

## Mettre à jour l’extension [!DNL Data Connection] {#update}

Pour mettre à jour l’extension [!DNL Data Connection], exécutez les opérations suivantes à partir de la ligne de commande :

```bash
composer update magento/experience-platform-connector --with-dependencies
```

Ou, pour les marchands B2B :

```bash
composer update magento/experience-platform-connector-b2b --with-dependencies
```

Pour effectuer une mise à jour vers une version majeure, telle que de 2.0.0 à 3.0.0, modifiez le fichier [!DNL Composer] `.json` racine du projet comme suit :

1. Ouvrez le fichier racine `composer.json` et recherchez `magento/experience-platform-connector`.

1. Dans la section `require` , mettez à jour le numéro de version comme suit :

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

   Ou, pour les marchands B2B :

   ```bash
   composer update magento/experience-platform-connector-b2b --with-dependencies
   ```

## Désinstaller l’extension [!DNL Data Connection] {#uninstall}

Pour désinstaller l’extension [!DNL Data Connection], reportez-vous à la section [désinstallation des modules](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html).
