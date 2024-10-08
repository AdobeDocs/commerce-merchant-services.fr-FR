---
title: '[!DNL Manage the Data Export extension]'
description: Découvrez comment mettre à niveau l’extension  [!DNL Data Export] et supprimer ou désactiver les services d’exportation de données qui ne sont pas requis.
role: Admin, Developer
exl-id: d2326673-0f82-4266-bf56-74d55e32fcab
source-git-commit: b80bc2867f44e6123adb104eb148ac5e8f80b63d
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---

# Gestion de l’extension d’exportation des données SaaS

L’extension [!DNL data export] pour les services SaaS est un ensemble de modules qui permettent la collecte et la synchronisation des données entre Adobe Commerce et les services Commerce connectés.

Des modules spécifiques sont inclus dans les modules des extensions Adobe Commerce Services, tels que
en tant que [Live Search](/help/live-search/overview.md), [Product Recommendations](/help/product-recommendations/overview.md) et [Catalog Service](/help/catalog-service/overview.md). Si vous utilisez ces services, aucune installation distincte n’est nécessaire pour activer l’extension Data Export.

## Suppression ou désactivation des fonctionnalités d’exportation de données Commerce

Si vous n’avez pas besoin de l’un des modules d’exportation de données commerciales installés, utilisez la commande d’interface de ligne de commande `magento:module:disable` pour le désactiver.

Par exemple, il existe une [API Catégories](https://developer.adobe.com/commerce/services/graphql/catalog-service/categories/) qui utilise les données de flux d’autorisations de catégories en interne. Si vous n’utilisez pas cette API, vous pouvez désactiver l’exportation des données pour le flux d’autorisation des catégories.

```shell script
bin/magento module:disable Magento_CategoryPermissionDataExporter Magento_SaaSCategoryPermissions
```

### Mise à jour d’un module vers une version spécifique

Vous pouvez mettre à jour n’importe quel module d’exportation de données de commerce installé à l’aide du compositeur. Par exemple, vous pouvez mettre à jour un module vers une version spécifiée, ainsi que toutes les dépendances requises.

1. Connectez-vous au serveur d’applications Commerce.

1. Dans la ligne de commande, mettez à jour le module à l’aide du compositeur :

   ```bash
   composer require magento/module-saas-price:103.3.1 --with-all-dependencies
   ```

Si l’instance Commerce est déployée sur l’infrastructure cloud, mettez à jour l’extension à partir du répertoire de votre projet cloud. Voir [Mise à niveau d’une extension](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/extensions#upgrade-an-extension) dans le _Guide de l’infrastructure d’Adobe Commerce on Cloud_.
