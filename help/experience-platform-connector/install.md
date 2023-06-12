---
title: Installation et configuration de Adobe Experience Platform Connector depuis Adobe Commerce
description: Découvrez comment installer, configurer, mettre à jour et désinstaller Adobe Experience Platform Connector à partir d’Adobe Commerce.
exl-id: e78e8ab0-8757-4ab6-8ee1-d2e137fe6ced
source-git-commit: 052b9fe32797e62d5802241c7b3420decf593fc1
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# Installation et configuration du connecteur Experience Platform

Avant d’installer l’extension, [revoir les conditions préalables](overview.md#prereqs).

## Installation de l’extension

L’extension Experience Platform Connector est disponible à partir de la [Adobe Marketplace](https://marketplace.magento.com/magento-experience-platform-connector.html). Lorsque vous installez cette extension à partir de la ligne de commande du serveur, elle se connecte à votre installation Adobe Commerce en tant que [service](../landing/saas.md). Une fois le processus terminé, **Connecteur Experience Platform** et **Connecteur Commerce Services** apparaissent sur le **Système** sous **Services** dans Commerce _Administration_.

>[!NOTE]
>
>![B2B pour Adobe Commerce](../assets/b2b.svg) Pour les commerçants B2B, vous devez installer une extension distincte. Cette extension ajoute la prise en charge des événements spécifiques B2B. [En savoir plus](#install-the-b2b-extension).


1. Pour télécharger le `experience-platform-connector` , exécutez les éléments suivants à partir de la ligne de commande :

   ```bash
   composer require magento/experience-platform-connector
   ```

   Ce métappackage contient les modules et extensions suivants :

   * `module-experience-connector-admin` - Met à jour l’interface utilisateur d’administration afin que vous puissiez sélectionner l’identifiant de flux de données pour une instance Adobe Commerce spécifique.
   * `module-experience-connector` - Définit la variable `Organization ID` et `datastreamId` dans le SDK des événements Storefront
   * `data-services` - Fournit un contexte d’attribut pour les événements storefront. Par exemple, lorsqu’un événement de passage en caisse se produit, des informations sur le nombre d’articles figurant dans le panier et les données d’attribut de produit pour ces articles sont incluses.
   * `services-id` - Connecte votre instance Adobe Commerce à [Adobe Commerce SaaS](../landing/saas.md) à l’aide des clés d’API de test et de production et de Adobe Experience Platform pour récupérer l’ID d’organisation IMS ;

1. (Facultatif) Pour inclure [!DNL Live Search] , qui comprend les événements de recherche, installez la variable [[!DNL Live Search]](../live-search/install.md) extension .

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

Pour effectuer une mise à jour vers une version majeure, telle que de 1.0.0 à 2.0.0, modifiez la racine du projet. [!DNL Composer] `.json` comme suit :

1. Ouvrez la racine `composer.json` fichier et recherchez `magento/experience-platform-connector`.

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

   ou, pour les marchands B2B :

   ```bash
   composer update magento/experience-platform-connector-b2b --with-dependencies
   ```

## Désinstallation du connecteur Experience Platform {#uninstall}

Pour désinstaller le connecteur Experience Platform, reportez-vous à la section [désinstallation des modules](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html).
