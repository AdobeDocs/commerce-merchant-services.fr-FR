---
title: "Installer [!DNL Live Search]"
description: "Découvrez comment installer, mettre à jour et désinstaller [!DNL Live Search] d’Adobe Commerce."
exl-id: aa251bb0-d52c-4cff-bccb-76a08ae2a3b2
role: Admin, Developer
source-git-commit: 97a743b1f7162af01930a37db448432acb9f89d5
workflow-type: tm+mt
source-wordcount: '1323'
ht-degree: 0%

---

# Installer [!DNL Live Search]

[!DNL Live Search] est installé en tant qu’extension à partir d’Adobe Marketplace. Après la [!DNL Live Search] module (avec les modules de catalogue comme dépendances) est installé et configuré, [!DNL Commerce] Commence à partager les données de recherche et de catalogue avec les services SaaS. À ce stade, *Administration* les utilisateurs peuvent configurer, personnaliser et gérer des facettes de recherche, des synonymes et des règles de marchandisage.

Cette rubrique fournit des instructions pour effectuer les opérations suivantes :

* Installer [!DNL Live Search] (Méthodes 1 et 2)
* [Mettre à jour [!DNL Live Search]](#update)
* [Désinstaller [!DNL Live Search]](#uninstall)

## Avant de commencer {#before-you-begin}

Procédez comme suit :

1. Confirmez que [tâches cron](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html) et [indexeurs](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html) sont en cours d’exécution.

1. Choisissez la méthode d’intégration qui répond à vos besoins et suivez les instructions.

   * [Méthode 1](#method-1): installation sans [!DNL Elasticsearch]
   * [Méthode 2](#method-2): installation avec [!DNL Elasticsearch] (Pas d’interruption)

## Méthode 1 : installation sans Elasticsearch {#method-1}

Cette méthode d’intégration est recommandée lors de l’installation de [!DNL Live Search] à un :

* Nouveau [!DNL Commerce] installation
* Environnement d’évaluation

Dans ce scénario, les opérations de storefront sont interrompues pendant que la fonction [!DNL Live Search] service indexe tous les produits du catalogue. Pendant l&#39;installation, [!DNL Live Search] les modules sont activés et [!DNL Elasticsearch] Les modules sont désactivés.

>[!NOTE]
>
>Depuis mars 2023, Live Search ne prend en charge que les versions 2.4.4 et ultérieures.

1. Installez Adobe Commerce 2.4.4+ sans [!DNL Live Search].

1. Pour télécharger le `live-search` , exécutez les éléments suivants à partir de la ligne de commande :

   ```bash
   composer require magento/live-search
   ```

   Voir à ce sujet la liste des [!DNL Live Search] [dependencies](#dependencies) qui sont capturés par [!DNL Composer].

1. Exécutez les commandes suivantes pour désactiver [!DNL Elasticsearch] et les modules connexes, puis installez [!DNL Live Search]:

   ```bash
   bin/magento module:disable Magento_Elasticsearch Magento_Elasticsearch7 Magento_OpenSearch Magento_ElasticsearchCatalogPermissions Magento_InventoryElasticsearch Magento_ElasticsearchCatalogPermissionsGraphQl
   ```

   ```bash
   bin/magento setup:upgrade
   ```

   >[!WARNING]
   >
   > Bien que les données soient indexées et synchronisées, les opérations de recherche et de navigation de catégorie ne sont pas disponibles dans le storefront. Selon la taille de votre catalogue, le processus peut prendre au moins une heure à partir du `cron` s’exécute pour synchroniser vos données avec [!DNL Live Search] services.

1. Vérifiez que les [indexeurs](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html) sont définis sur `Update by Schedule`:

   * Flux de produit
   * Flux de variante de produit
   * Flux d’attributs du catalogue
   * Flux de prix du produit
   * Flux de données de site web de Portée
   * Portée Flux de données de groupes de clients

1. Configurez vos [Clés API](#configure-api-keys) et vérifier que les données de votre catalogue sont [synchronisé](#synchronize-catalog-data) avec [!DNL Live Search] services.

1. Pour rendre les facettes disponibles en tant que filtres dans le storefront, ajoutez le [facettes](facets-add.md) vous avez besoin, en fonction des [configuration requise](facets.md).

   Vous devriez pouvoir ajouter des facettes après `cron` exécute les flux d’attributs et exporte les métadonnées d’attribut.

1. Patientez au moins une heure après `cron` s’exécute pour synchroniser les données. Alors, [verify](#verify-export) que les données ont été exportées.

1. [Test](#test-the-connection) la connexion depuis le storefront.

## Méthode 2 : installation avec Elasticsearch {#method-2}

>[!IMPORTANT]
>
>En raison de l’annonce de fin de prise en charge de 7 Elasticsearch pour août 2023, il est recommandé à tous les clients Adobe Commerce de migrer vers le moteur de recherche OpenSearch 2.x. Pour plus d’informations sur la migration de votre moteur de recherche lors de la mise à niveau du produit, voir [Migration vers OpenSearch](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/prepare/opensearch-migration.html) dans le _Guide de mise à niveau_.

Cette méthode d’intégration est recommandée lors de l’installation de [!DNL Live Search] à :

* Une production existante [!DNL Commerce] installation

Dans ce scénario, [!DNL Elasticsearch] gère temporairement les requêtes de recherche à partir du storefront pendant que la fonction [!DNL Live Search] service indexe tous les produits en arrière-plan, sans interruption des opérations standard de storefront. [!DNL Elasticsearch] est désactivé et [!DNL Live Search] activée une fois que toutes les données de catalogue sont indexées et synchronisées.

1. Pour télécharger le `live-search` , exécutez les éléments suivants à partir de la ligne de commande :

   ```bash
   composer require magento/live-search
   ```

   Voir à ce sujet la liste des [!DNL Live Search] [dependencies](#live-search-dependencies) qui sont capturés par [!DNL Composer].

1. Exécutez la commande suivante pour désactiver temporairement la fonction [!DNL Live Search] modules qui diffusent les résultats de recherche storefront.

   ```bash
   bin/magento module:disable Magento_LiveSearchAdapter Magento_LiveSearchStorefrontPopover
   ```

   ```bash
   bin/magento setup:upgrade
   ```

   [!DNL Elasticsearch] continue à gérer les requêtes de recherche à partir du storefront pendant que la fonction [!DNL Live Search] Le service synchronise les données du catalogue et indexe les produits en arrière-plan.

1. Vérifiez que les [indexeurs](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html) sont définis sur `Update by Schedule`:

   * Flux de produit
   * Flux de variante de produit
   * Flux d’attributs du catalogue
   * Flux de prix du produit
   * Porte le flux de données du site web
   * Porte le flux de données de groupes de clients

1. Configurez vos [Clés API](#configure-api-keys) et vérifier que les données de votre catalogue sont [synchronisé](#synchronize-catalog-data) avec [!DNL Live Search] services.

1. Pour rendre les facettes disponibles en tant que filtres dans le storefront, ajoutez le [facettes](facets-add.md) vous avez besoin, en fonction des [configuration requise](facets.md).

   Vous devriez pouvoir ajouter des facettes après `cron` exécute les flux de produit et d’attribut et exporte les métadonnées d’attribut vers [!DNL Live Search] services.

1. Patientez au moins une heure pour que les données soient indexées et synchronisées. Ensuite, utilisez le [Jeu GraphQL](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/) avec la requête par défaut pour vérifier les éléments suivants :

   * Le nombre de produits renvoyé est proche de ce que vous attendez pour la vue de magasin.
   * Les facettes sont renvoyées.

1. Exécutez les commandes suivantes pour activer [!DNL Live Search] modules, désactiver [!DNL Elasticsearch], puis exécutez `setup`.

   ```bash
   bin/magento module:enable Magento_LiveSearchAdapter Magento_LiveSearchStorefrontPopover
   ```

   ```bash
   bin/magento module:disable Magento_Elasticsearch Magento_Elasticsearch6 Magento_Elasticsearch7 Magento_ElasticsearchCatalogPermissions Magento_InventoryElasticsearch 
   Magento_ElasticsearchCatalogPermissionsGraphQl
   ```

   ```bash
   bin/magento setup:upgrade
   ```

1. [Test](#test-the-connection) la connexion depuis le storefront.

## Configuration des clés d’API {#configure-api-keys}

La clé d’API Adobe Commerce et sa clé privée associée sont nécessaires pour se connecter. [!DNL Live Search] à une installation d’Adobe Commerce. La clé API est générée et conservée dans le compte de la variable [!DNL Commerce] titulaire de la licence, qui peut la partager avec le développeur ou l’instance SI. Le développeur peut ensuite créer et gérer les espaces de données SaaS pour le compte du détenteur de licence.  Si vous disposez déjà d’un ensemble de clés d’API, vous n’avez pas besoin de les régénérer.

### détenteur d’une licence Adobe Commerce

Pour générer une clé API et une clé privée, reportez-vous à la section [Connecteur Commerce Services](../landing/saas.md).

### Développeur Adobe Commerce ou SI

Le développeur ou l’ID configure l’espace de données SaaS comme décrit dans la section *Services de commerce* de la configuration. Dans le *Administration*, Commerce Services devient disponible dans le *Configuration* barre latérale lorsqu’un module SaaS est installé.

## Synchronisation des données de catalogue {#synchronize-catalog-data}

[!DNL Live Search] nécessite des données de produit synchronisées pour les opérations de recherche et des données d’attribut synchronisées pour configurer les facettes. La synchronisation initiale entre le catalogue de produits et le service de catalogue commence lorsque [!DNL Live Search] est d’abord connecté. Selon la méthode d&#39;installation et la taille du catalogue, l&#39;export et l&#39;indexation des données par peuvent prendre jusqu&#39;à 30 minutes. [!DNL Live Search]. La liste des données synchronisées et partagées avec le service de catalogue se trouve dans le schéma, défini dans :

`vendor/magento/module-catalog-data-exporter/etc/et_schema.xml`

### Vérifier l’exportation {#verify-export}

Pour vérifier que les données du catalogue ont été exportées à partir de votre instance Adobe Commerce et sont synchronisées pour [!DNL Live Search], recherchez les entrées dans les tableaux suivants :

* `catalog_data_exporter_products`
* `catalog_data_exporter_product_attributes`

Pour obtenir une aide supplémentaire, reportez-vous à la section [[!DNL Live Search] catalogue non synchronisé](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/live-search-catalog-data-sync.html) dans la base de connaissances d’assistance.

### Futures mises à jour des produits

Après la synchronisation initiale, il peut s’écouler jusqu’à 15 minutes avant que les mises à jour incrémentielles des produits ne soient disponibles pour la recherche storefront. Pour en savoir plus, accédez à [Indexation - Mises à jour des produits en flux continu](indexing.md).

## Tester la connexion {#test-connection}

Dans le storefront, vérifiez les éléments suivants :

* La variable [!UICONTROL Search] la zone renvoie les résultats correctement
* La navigation dans les catégories renvoie correctement les résultats.
* Les facettes sont disponibles sous forme de filtres sur les pages de résultats de recherche.

Si tout fonctionne correctement, félicitations ! [!DNL Live Search] est installé, connecté et prêt à l’emploi.

Si vous rencontrez des problèmes dans le storefront, vérifiez la variable `var/log/system.log` pour les erreurs ou échecs de communication de l’API côté services.

Pour autoriser la recherche en direct par le biais d’un pare-feu, ajoutez `commerce.adobe.io` à la liste autorisée.

## Vérification de la version installée

Avant de mettre à jour la recherche en direct, exécutez le code suivant depuis la ligne de commande pour vérifier la version de la recherche en direct actuellement installée :

```bash
composer show magento/module-live-search | grep version
```

## Mise à jour [!DNL Live Search] {#update}

Pour mettre à jour [!DNL Live Search], exécutez les opérations suivantes à partir de la ligne de commande :

```bash
composer update magento/live-search --with-dependencies
```

Pour effectuer une mise à jour vers une version majeure, telle que de la version 2.0.0 à la version 3.1.1, modifiez la racine du projet. [!DNL Composer] `.json` comme suit :

1. Si votre `magento/live-search` version est `2.0.3` ou version inférieure et que vous effectuez une mise à niveau vers la version `3.0.0` ou supérieur, exécutez la commande suivante avant la mise à niveau :

   ```bash
   bin/magento module:enable Magento_AdvancedSearch
   ```

   Pour plus d’informations sur la version actuellement installée `magento/live-search` version, exécutez la commande suivante :

   ```bash
   composer show magento/live-search
   ```

1. Ouvrez la racine `composer.json` fichier et recherchez `magento/live-search`.

1. Dans le `require` , mettez à jour le numéro de version comme suit :

   ```json
   "require": {
      ...
      "magento/live-search": "^3.0",
      ...
    }
   ```

1. **Enregistrer** `composer.json`. Exécutez ensuite la commande suivante à partir de la ligne de commande :

   ```bash
   composer update magento/live-search --with-dependencies
   ```

## Désinstallation [!DNL Live Search] {#uninstall}

Pour désinstaller [!DNL Live Search], voir [Désinstallation des modules](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html).

## [!DNL Live Search] packages {#packages}

| Package | Description |
|--- |--- |
| `module-live-search` | Permet aux commerçants de configurer leurs paramètres de recherche pour la facette, les synonymes, les règles de requête, etc., et permet d’accéder à un terrain de jeu GraphQL en lecture seule pour tester les requêtes à partir de la variable *Administration*. |
| `module-live-search-adapter` | Permet d’acheminer les requêtes de recherche du storefront vers le [!DNL Live Search] et effectue le rendu des résultats dans le storefront. <br />- Navigation dans les catégories - achemine les demandes depuis le storefront [navigation supérieure](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-top.html) au service de recherche.<br />- Recherche globale - achemine les requêtes de la [recherche rapide](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#quick-search) dans le coin supérieur droit du storefront vers la propriété [!DNL Live Search] service. |
| `module-live-search-storefront-popover` | Une fenêtre contextuelle &quot;Rechercher lorsque vous tapez&quot; remplace la recherche rapide standard et renvoie les données et les miniatures des principaux résultats de la recherche. |

## [!DNL Live Search] dependencies {#dependencies}

Les éléments suivants [!DNL Live Search] les dépendances sont capturées par [!DNL Composer]:

| Dépendance | Description |
|--- |--- |
| Exporter les modules | Les modules suivants collectent et synchronisent les données du catalogue :<br />`module-sass-catalog`<br />`module-sass-product-override`<br />`module-bundle-product-data-exporter`<br />`module-catalog-data-exporter`<br />`module-catalog-inventory-data-exporter`<br />`module-catalog-url-rewrite-data-exporter`<br />`module-configurable-product-data-exporter`<br />`module-data-exporter`<br />`module-parent-product-data-exporter`<br />`module-product-override-data-exporter` |
| `data-services` | Requis pour configurer votre connexion à Commerce Services. |
| `services-id` | Requis pour configurer votre connexion à Commerce Services. |
