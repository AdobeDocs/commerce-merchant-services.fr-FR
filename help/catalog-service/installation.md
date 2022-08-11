---
title: '"Intégration et installation"'
description: '"Découvrez comment installer [!DNL Catalog Service]"'
source-git-commit: 7f6955ffc52669ff3b95957642b3a115bf1eb741
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---


# Intégration et installation

Les partenaires et les clients peuvent commencer à utiliser la variable [!DNL Catalog Service] pour la version bêta d’Adobe Commerce publiée le 9 août 2022. Pour participer, vous devez lire et accepter notre [Termes du programme Adobe Commerce bêta](https://experiencecloudpanel.adobe.com/h/s/6eGskQlHvLSHztsNmKCWMy).

Une fois que vous avez signé l&#39;accord, contactez notre équipe au sujet de la [#storefront-services](https://magentocommeng.slack.com/archives/C03HVPG8RS4) canal du Slack public. Nous vous fournirons toutes les informations et les étapes suivantes nécessaires pour travailler avec le [!DNL Catalog Service] Version bêta.

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

Le [!DNL Catalog Service] est installé avec les clés du compositeur, qui sont liées à l’ID de Magento ([mageid](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-personal/#field-descriptions) fourni dans le processus d’inscription. Le compositeur utilise ces clés lors de l’installation initiale de [!DNL Adobe Commerce], ou dans les cas où les clés du compositeur n’ont pas été précédemment enregistrées dans la variable `auth.json` fichier .

Voir [Obtention des clés d’authentification](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) pour plus d’informations sur l’obtention des clés du compositeur.

### Adobe Commerce sur l’infrastructure cloud

Utilisez cette méthode pour installer le [!DNL Catalog Service] pour une instance de Commerce Cloud.

1. Ouvrez le `<Commerce_root>/composer.json` dans un éditeur de texte et mettez à jour la variable `require` , comme suit :

   ```json
   "require": {
     "magento/magento-cloud-metapackage": ">=2.4.3 <2.4.4",
     "magento/composer-root-update-plugin": "~1.1",
     "magento/saas-export": "^101.3.1",
     "magento/commerce-data-export": "^101.2.4",    
     "magento/commerce-data-export-ee": "^101.2.4",
     "magento/services-id": "^3.0.0",
     "magento/services-connector": "1.2.1"
   }
   ```

   <!-- What if the customer already has other services installed, and some of these lines are already present? Do they need to delete the duplications? What if the version numbers are different? -->

1. Mettez à jour les dépendances et installez l’extension :

   ```bash
   composer update
   ```

   La commande met à jour toutes les dépendances.

1. Validez et envoyez vos modifications.

### Sur site

Utilisez cette méthode pour installer le [!DNL Catalog Service] pour une instance sur site.

1. Ouvrez le `<Commerce_root>/composer.json` dans un éditeur de texte et mettez à jour la variable `require` , comme suit :

   ```json
   "require": {
     "magento/magento-cloud-metapackage": ">=2.4.3 <2.4.4",
     "magento/composer-root-update-plugin": "~1.1",
     "magento/saas-export": "^101.3.1",
     "magento/commerce-data-export": "^101.2.4",    
     "magento/commerce-data-export-ee": "^101.2.4",
     "magento/services-id": "^3.0.0",
     "magento/services-connector": "1.2.1"
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

## Configuration de l’exportation de catalogue

Après l’installation [!DNL Catalog Service], vous devez configurer la variable [Connecteur Commerce Services](../landing/saas.md) en spécifiant les clés d’API et en sélectionnant un espace de données SaaS.

Pour vous assurer que l’exportation de catalogue s’exécute correctement, vérifiez que la variable [tâches cron](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html) et le [indexeurs](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html) sont en cours d’exécution et l’indexeur de flux de produit est défini sur Mettre à jour par planification.