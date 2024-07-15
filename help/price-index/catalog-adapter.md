---
title: Extension de l’adaptateur de catalogue
description: Utilisation de l’adaptateur de catalogue pour effectuer le rendu des prix à partir des services Commerce
seo-title: Catalog Adapter Extension
seo-description: Using Catalog Adapter to render prices from Commerce Services
exl-id: 2c9120eb-aa51-48e9-b6a4-fffe25fc31f2
source-git-commit: 8230756c203cb2b4bdb4949f116c398fcaab84ff
workflow-type: tm+mt
source-wordcount: '708'
ht-degree: 0%

---

# Adaptateur de catalogue

L’extension `[!DNL Catalog Adapter]` désactive l’indexeur de prix de produit par défaut inclus dans l’application Commerce et utilise à la place les prix fournis par le [Catalog Service](../catalog-service/overview.md).

L’adaptateur est conçu pour fonctionner avec l’ [ export de données SaaS](../data-export/overview.md) et le service Adobe Commerce. L’exportation des données SaaS est responsable de l’envoi des prix, et [!DNL Catalog Adapter] récupère tous les prix du service Adobe Commerce.

Lorsque vous activez le [!DNL Catalog Adapter], l’indexation et les opérations des prix sont affectées de la manière suivante :

- L’indexeur de prix inclus dans l’application Adobe Commerce est désactivé.
- Les prix sont gérés à l&#39;aide de l&#39;export des données SaaS et de l&#39; [indexeur de prix SaaS](price-indexing.md).
- Lorsqu’un client ouvre un produit, une catégorie ou une autre page qui indique les prix d’un produit, les prix sont récupérés dans le service Adobe Commerce.
- Les prix sont envoyés au service Adobe Commerce en synchronisant les données de l’ [export de données SaaS](../data-export/overview.md).
- Le passage en caisse recalcule les prix dynamiquement.

Vous pouvez réactiver l’indexation de prix dans l’application Commerce en supprimant ou en désactivant l’extension de l’adaptateur de catalogue.

## Conditions

- Adobe Commerce 2.4.4+
- Installez l’un des services Commerce suivants :

   - [Recherche en direct](../live-search/install.md)
   - [Recommendations de produit](../product-recommendations/install-configure.md)
   - [Service de catalogue](../catalog-service/installation.md)

## Installation

L’extension de l’adaptateur de catalogue est un métapaquet de compositeur qui installe les modules suivants :

- **Désactivation de l’indexeur de prix** - Ce module désactive l’index de prix dans l’application Commerce afin que les prix soient délivrés via l’indexation de prix SaaS. L’indexeur de prix de produit de l’application Commerce ne peut pas être activé lorsque l’extension d’indexation de prix SaaS est installée.
- **Fournisseur de prix** - Ce module fournit des prix pour les produits du service Adobe Commerce. Il forme la requête de recherche et obtient les prix des produits en front-end.
- **Adaptateur de recherche de service de catalogue** - Ce module transfère les prix de l’application Adobe Commerce vers un service Adobe Commerce en réponse à une demande de recherche de produit.

## Etapes d&#39;installation

>[!BEGINTABS]

>[!TAB Infrastructure cloud]

Utilisez cette méthode pour installer [!DNL Catalog Adapter] pour une instance de Commerce Cloud.

1. Sur votre poste de travail local, modifiez le répertoire du projet pour votre projet Adobe Commerce sur l’infrastructure cloud.

   >[!NOTE]
   >
   >Pour plus d’informations sur la gestion locale des environnements de projet Commerce, voir [Gestion des branches avec l’interface de ligne de commande](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/cli-branches) dans le _Guide de l’utilisateur d’Adobe Commerce on Cloud Infrastructure_.

1. Consultez la branche d’environnement pour mettre à jour à l’aide de l’interface de ligne de commande de Adobe Commerce Cloud.

   ```shell
   magento-cloud environment:checkout <environment-id>
   ```

1. Ajoutez le module Adaptateur de catalogue .

   ```bash
   composer require magento/catalog-adapter --no-update
   ```

1. Mettez à jour les dépendances de package.

   ```bash
   composer update "magento/catalog-adapter"
   ```

1. Validez et poussez les modifications de code pour les fichiers `composer.json` et `composer.lock`.

1. Ajoutez, validez et poussez les modifications de code des fichiers `composer.json` et `composer.lock` dans l’environnement cloud.

   ```shell
   git add -A
   git commit -m "Add catalog adapter module"
   git push origin <branch-name>
   ```

   La publication des mises à jour dans l’environnement cloud lance le [processus de déploiement cloud de Commerce](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/process) pour appliquer les modifications. Vérifiez l’état du déploiement à partir du [log de déploiement](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/log-locations#deploy-log).

>[!TAB Sur site]

Utilisez cette méthode pour installer [!DNL Catalog Adapter] pour une instance sur site.

1. Ajoutez l’adaptateur de catalogue à votre projet à l’aide du compositeur :

   ```bash
   composer require magento/catalog-adapter --no-update
   ```

1. Mettez à jour les dépendances et installez l’extension :

   ```bash
   composer update  "magento/catalog-adapter"
   ```

1. Mettre à niveau Adobe Commerce :

   ```bash
   bin/magento setup:upgrade
   ```

1. Effacez le cache :

   ```bash
   bin/magento cache:clean
   ```

   >[!TIP]
   >
   >Dans certains cas, en particulier lors du déploiement en production, vous souhaiterez peut-être éviter de supprimer le code compilé, car cela peut prendre du temps. Assurez-vous de sauvegarder votre système avant d’apporter des modifications.

>[!ENDTABS]


## Réactivez l’indexeur de prix des produits Adobe Commerce

Si des applications tierces dépendent de l’indexeur de prix de produit Adobe Commerce par défaut, vous pouvez le réactiver à l’aide des commandes suivantes :

```bash
# re-enable Product Price indexer
bin/magento module:disable Magento_PriceIndexerDisabler
# re-index Product Price indexer
bin/magento index:reindex catalog_product_price
```

## Désactivation de l’indexeur de prix de produit pour le scénario Storefront sans affichage

Si vous disposez d’une instance Commerce sans interface utilisateur graphique, vous devrez peut-être désactiver l’indexeur de prix de produit Adobe Commerce pour réduire la charge sur votre instance Adobe Commerce. Vous pouvez effectuer cette tâche en installant le module `magento/module-price-indexer-disabler` :

```bash
composer require magento/module-price-indexer-disabler
```

## Scénarios d’utilisation

Voici quelques scénarios `[!DNL Catalog Adapter]` courants.

### Aucune dépendance sur l’indexeur de prix de produit Adobe Commerce

- Vous êtes un commerçant Luma ou Adobe Commerce Core GraphQL qui a installé le service requis (Live Search, Recommendations produit, Catalog Service).
- Aucune intégration avec des extensions tierces qui reposent sur l’indexeur de prix de produit Adobe Commerce

1. Installez le [!DNL Catalog Adapter].

### Avec dépendances sur l’indexeur de prix de produit Adobe Commerce

- Vous êtes un commerçant Luma ou Adobe Commerce Core GraphQL qui a installé un service pris en charge (Live Search, Recommendations produit, Catalog Service).
- Vous utilisez une extension tierce basée sur l’indexeur de prix de produit Adobe Commerce

1. Installez le [!DNL Catalog Adapter].
1. Réactivez l’indexeur de prix de produit Adobe Commerce par défaut.

### Instances Commerce sans tête

- Un commerçant avec une instance Commerce sans interface utilisateur graphique disposant des services requis installés (Live Search, Recommendations produit, Catalog Service)
- Ne pas dépendre de l’indexeur de prix de produit Adobe Commerce par défaut

1. Installez le module `magento/module-price-indexer-disabler` à partir du package [!DNL Catalog Adapter].

