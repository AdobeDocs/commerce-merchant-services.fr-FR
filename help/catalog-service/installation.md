---
title: Intégration et installation
description: Découvrez comment installer [!DNL Catalog Service]
exl-id: 4e9fbdc9-67a1-4703-b8c0-8b159e0cc2a7
source-git-commit: 55c35e7775505ab9f6a61a458b6cd6fa4c7f1702
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 0%

---

# Intégration et installation

## Conditions préalables

Le processus d’intégration pour [!DNL Catalog Service] requiert l’accès à la ligne de commande du serveur. Si vous n’êtes pas familiarisé avec l’utilisation de la ligne de commande, demandez de l’aide à un développeur ou à un intégrateur système.

### Exigences logicielles

- Adobe Commerce 2.4.x
- PHP 8.1, 7.4, 7.3
- Compositeur : 2.x, 1.x

### Plateformes prises en charge

- Adobe Commerce sur l’infrastructure cloud : 2.4.x
- Adobe Commerce sur site : 2.4.x

## Environnements

Le service de catalogue propose deux environnements d’intégration :

- Environnement de test (https://catalog-service-sandbox.adobe.io/graphql) : utilisé pour le test et la validation avant la mise en ligne.
- Production (https://catalog-service.adobe.io/graphql)- utilisée pour le trafic en direct pour les marchands et les sites web de commerce

## Installation et configuration

Pour commencer à utiliser le service de catalogue pour Adobe Commerce , procédez comme suit :

- Installation des extensions d’exportation de données
- Configuration du service et de l’exportation des données
- Accès au service

### Installation des extensions d’exportation de données

Le processus d’intégration du service de catalogue requiert l’accès à la ligne de commande du serveur.

L’extension Catalog Service peut être installée sur l’infrastructure cloud Adobe Commerce et sur les instances sur site.

Le service de catalogue est installé avec les clés du compositeur, qui sont liées au compte Commerce. [mageid](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-personal/#field-descriptions) fourni pendant le processus d’inscription. Le compositeur utilise ces clés lors de l’installation initiale d’Adobe Commerce, ou dans les cas où les clés du compositeur n’étaient pas précédemment enregistrées dans une instance externe `auth.json` fichier .

Voir [Obtention des clés d’authentification](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/authentication-keys.html) pour plus d’informations sur l’obtention des clés du compositeur.

#### Adobe Commerce sur l’infrastructure cloud

Utilisez cette méthode pour installer l’extension Catalog Service pour une instance de Commerce Cloud.

1. Ouvrez le `<Commerce_root>/composer.json` dans un éditeur de texte et mettez à jour la section requise comme suit :

   ```json
   "require": {
     "magento/module-saas-catalog": "^101.4.0",
     "magento/module-saas-product-override": "^101.4.0",
     "magento/module-saas-product-variant": "^101.4.0",
     "magento/module-bundle-product-data-exporter": "^101.3.1",
     "magento/module-catalog-data-exporter": "^101.3.1",
     "magento/module-catalog-inventory-data-exporter": "^101.3.1",
     "magento/module-catalog-url-rewrite-data-exporter": "^101.3.1",
     "magento/module-configurable-product-data-exporter": "^101.3.1",
     "magento/module-data-exporter": "^101.3.1",
     "magento/module-parent-product-data-exporter": "^101.3.1",
     "magento/module-product-override-data-exporter": "^101.3.1",
     "magento/data-services": "^7.0.11",
     "magento/services-id": "^3.0.1",
     "magento/services-connector": "1.2.1",
     "magento/module-catalog-service-installer": "1.0.1"
   }
   ```

1. Testez localement la nouvelle configuration et mettez à jour les dépendances :

```bash
composer update
```

La commande met à jour toutes les dépendances.

1. Validez et envoyez vos modifications pour `composer.json` et `composer.lock`.

#### Sur site

Utilisez cette méthode pour installer l’extension Catalog Service pour une instance sur site.

1. Ouvrez le `<Commerce_root>/composer.json` dans un éditeur de texte et mettez à jour la section requise comme suit :

```json
"require": {
 "magento/module-saas-catalog": "^101.4.0",
 "magento/module-saas-product-override": "^101.4.0",
 "magento/module-saas-product-variant": "^101.4.0",
 "magento/module-bundle-product-data-exporter": "^101.3.1",
 "magento/module-catalog-data-exporter": "^101.3.1",
 "magento/module-catalog-inventory-data-exporter": "^101.3.1",
 "magento/module-catalog-url-rewrite-data-exporter": "^101.3.1",
 "magento/module-configurable-product-data-exporter": "^101.3.1",
 "magento/module-data-exporter": "^101.3.1",
 "magento/module-parent-product-data-exporter": "^101.3.1",
 "magento/module-product-override-data-exporter": "^101.3.1",
 "magento/data-services": "^7.0.11",
 "magento/services-id": "^3.0.1",
 "magento/services-connector": "1.2.1",
 "magento/module-catalog-service-installer": "1.0.1"
}
```

1. Mettez à jour les dépendances et installez l’extension :

```bash
composer update
```

La commande met à jour toutes les dépendances.

1. Mettre à niveau Adobe Commerce :

```bash
bin/magento setup:upgrade
```

1. Effacez le cache :

```bash
bin/magento cache:clean
```

### Configuration du service et de l’exportation des données

Après avoir installé le service de catalogue, vous devez configurer la variable [Connecteur Commerce Services](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html#apikey) en spécifiant les clés d’API et en sélectionnant un espace de données SaaS.

Une fois la configuration SaaS terminée, effectuez une synchronisation initiale des données en suivant le guide de synchronisation du catalogue .

Pour vous assurer que l’exportation du catalogue s’exécute correctement :

- Vérifiez que les tâches cron sont en cours d’exécution.
- Vérifiez que les indexeurs sont en cours d’exécution.
- Assurez-vous que la variable `Catalog Attributes Feed, Product Feed, Product Overrides Feed`, et `Product Variant Feed` les indexeurs sont définis sur &quot;Mise à jour par planification&quot;.

La synchronisation initiale peut prendre de quelques minutes à des heures selon la taille du catalogue. Après la synchronisation initiale, le catalogue exporte en permanence les données de produit du serveur Commerce vers les services Commerce afin de maintenir les services à jour.

### Accès au service

L’API Catalog Service est accessible à l’aide de commandes POST via HTTPS.

Pour obtenir la clé api, accédez à la zone Commerce Service Connector dans l’administrateur et copiez la clé API publique.

Lisez le [Documentation GraphQL](https://developer.adobe.com/commerce/webapi/graphql/) pour comprendre comment interroger et envoyer les en-têtes nécessaires à la génération de requêtes d’API.

## Service de catalogue et maillage d’API

Le [Maillage d’API pour Adobe Developer App Builder](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) permet aux développeurs d’intégrer des API privées ou tierces, ainsi que d’autres interfaces avec des produits Adobe à l’aide des E/S d’Adobe.

Voir  [Service de catalogue et maillage d’API](mesh.md) pour plus d’informations sur l’installation et la configuration.
