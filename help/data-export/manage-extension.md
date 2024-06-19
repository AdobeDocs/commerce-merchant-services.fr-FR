---
title: "[!DNL Manage the Data Export extension]"
description: "Découvrez comment mettre à niveau le [!DNL Data Export] et de supprimer ou désactiver les services d’exportation de données qui ne sont pas requis."
role: Admin, Developer
recommendations: noCatalog
source-git-commit: 8230756c203cb2b4bdb4949f116c398fcaab84ff
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---


# Gestion de l’extension d’exportation des données SaaS

La variable [!DNL data export] L’extension pour les services SaaS est un ensemble de modules qui permettent la collecte et la synchronisation des données entre Adobe Commerce et les services Commerce connectés.

Des modules spécifiques sont inclus dans les modules des extensions Adobe Commerce Services, tels que [Recherche en direct](/help/live-search/overview.md), [Recommendations de produit](/help/product-recommendations/overview.md), et [Service de catalogue](/help/catalog-service/overview.md). Si vous utilisez ces services, aucune installation distincte n’est nécessaire pour activer l’extension Data Export.

## Suppression ou désactivation des fonctionnalités d’exportation de données Commerce

Si vous n’avez pas besoin de l’un des modules d’exportation de données de commerce installés, utilisez la variable `magento:module:disable` Commande d’interface de ligne de commande pour la désactiver.

Par exemple, il existe une [API Catégories](https://developer.adobe.com/commerce/services/graphql/catalog-service/categories/) qui utilise les données du flux d’autorisations de catégories en interne. Si vous n’utilisez pas cette API, vous pouvez désactiver l’exportation des données pour le flux d’autorisation des catégories.

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

Si l’instance Commerce est déployée sur l’infrastructure cloud, mettez à jour l’extension à partir du répertoire de votre projet cloud. Voir [Mettre à niveau une extension](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/extensions#upgrade-an-extension) dans le _Guide d’infrastructure d’Adobe Commerce on Cloud_.




