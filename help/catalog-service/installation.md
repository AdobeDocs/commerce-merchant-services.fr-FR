---
title: Intégration et installation
description: Découvrez comment installer [!DNL Catalog Service]
exl-id: 4e9fbdc9-67a1-4703-b8c0-8b159e0cc2a7
source-git-commit: ea4b386d7e378b30641e623cb190923dc50563d8
workflow-type: tm+mt
source-wordcount: '456'
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

## Installation de l’extension

Vous pouvez installer le [!DNL Catalog Service] extension pour Adobe Commerce sur l’infrastructure cloud et les instances sur site.

Le [!DNL Catalog Service] est installé avec les clés du compositeur, liées au compte Commerce ; [mageid](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-personal/#field-descriptions) fourni dans le processus d’inscription. Le compositeur utilise ces clés lors de l’installation initiale de [!DNL Adobe Commerce], ou dans les cas où les clés du compositeur n’ont pas été précédemment enregistrées dans la variable `auth.json` fichier .

Voir [Obtention des clés d’authentification](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) pour plus d’informations sur l’obtention des clés du compositeur.

### Adobe Commerce sur l’infrastructure cloud

Utilisez cette méthode pour installer le [!DNL Catalog Service] pour une instance de Commerce Cloud.

1. Ouvrez le `<Commerce_root>/composer.json` dans un éditeur de texte et mettez à jour la variable `require` , comme suit :

   ```json
   "require":{
   "magento/composer-root-update-plugin":"^2.0.2",
   "magento/magento-cloud-metapackage":">=2.4.5 <2.4.6",
   "magento/catalog-service": "^1.0.0"
      }
   ```

1. Testez localement la nouvelle configuration et mettez à jour les dépendances :

   ```bash
   composer update
   ```

   La commande met à jour toutes les dépendances.

1. Validez et envoyez vos modifications pour `composer.json` et `composer.lock`.

### Sur site

Utilisez cette méthode pour installer le [!DNL Catalog Service] pour une instance sur site.

1. Ouvrez le `<Commerce_root>/composer.json` dans un éditeur de texte et mettez à jour la variable `require` , comme suit :

   ```json
   "require": {
   "magento/composer-root-update-plugin":"^2.0.2",
   "magento/catalog-service": "^1.0.0"
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

## Service de catalogue et maillage d’API

Le [Mesh de l’API](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) permet aux développeurs d’intégrer des API privées ou tierces, ainsi que d’autres interfaces avec des produits Adobe à l’aide des E/S d’Adobe.

La première étape de l’utilisation du maillage API avec le service de catalogue consiste à connecter le maillage API à votre instance. Voir les instructions détaillées dans [Création d’un maillage](https://developer.adobe.com/graphql-mesh-gateway/gateway/create-mesh/).

Pour terminer la configuration, vous devez [Module d’interface de ligne de commande d’Adobe IO](https://developer.adobe.com/runtime/docs/guides/tools/cli_install/) installé.

Une fois que le maillage est configuré sur l’Adobe IO, exécutez la commande suivante pour connecter le nouveau maillage.

```bash
aio api-mesh:source:install "CommerceCatalogServiceGraph" -f variables.json
```

where `variables.json` est un fichier distinct qui stocke les valeurs couramment utilisées pour les E/S d’Adobe.
Par exemple, la clé API peut être enregistrée dans le fichier :

```json
{
    "CATALOG_SERVICE_API_KEY":"your_api_key"
}
```

Après l’exécution de cette commande, le service de catalogue doit s’exécuter par le biais du maillage API.

## Configuration de l’exportation de catalogue

Après l’installation [!DNL Catalog Service], vous devez configurer la variable [Connecteur Commerce Services](../landing/saas.md) en spécifiant les clés d’API et en sélectionnant un espace de données SaaS.

Pour vous assurer que l’exportation du catalogue s’exécute correctement :

- Confirmez que [tâches cron](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html) sont en cours d’exécution.
- Vérifiez les [indexeurs](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html) sont en cours d’exécution.
- Assurez-vous que la variable `Catalog Attributes Feed`, `Product Feed`, `Product Overrides Feed`, et `Product Variant Feed` les indexeurs sont définis sur `Update by Schedule`.

## [!DNL Catalog Service] demo

Regardez cette vidéo pour en savoir plus sur [!DNL Catalog Service] installation et test :

>[!VIDEO](https://video.tv.adobe.com/v/3409390?quality=12&learn=on)
