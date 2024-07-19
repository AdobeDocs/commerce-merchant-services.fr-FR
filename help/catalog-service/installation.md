---
title: Intégration et installation
description: "Découvrez comment installer [!DNL Catalog Service]"
exl-id: 4e9fbdc9-67a1-4703-b8c0-8b159e0cc2a7
source-git-commit: 0b0bc88c13d8c90a6209d9156f6fd6a7ce040f72
workflow-type: tm+mt
source-wordcount: '867'
ht-degree: 0%

---

# Intégration et installation

Installez le service de catalogue pour demander et recevoir des données de produit d’une instance Commerce à l’aide de l’[ API GraphQL de service de catalogue](https://developer.adobe.com/commerce/services/graphql/catalog-service/). Le service de catalogue est fourni en tant que métapaquet de compositeur à partir du référentiel repo.magento.com.

>[!NOTE]
>
>Si votre instance Commerce utilise Live Search ou Product Recommendations, le service de catalogue est installé ou mis à jour automatiquement lorsque vous embarquez ou mettez à niveau ces services. Pour plus d’informations, reportez-vous aux instructions d’installation pour [Live Search](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/install) et [Product Recommendations](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/getting-started/install-configure).



## Configuration requise

**Exigences logicielles**

- Adobe Commerce 2.4.4+
- PHP 8.1, 8.2, 8.3
- Compositeur : 2.x

**Plateformes prises en charge**

- Adobe Commerce sur l’infrastructure cloud : 2.4.4+
- Adobe Commerce sur site : 2.4.4+

## Points de fin

[!DNL Catalog Service] comporte deux points de terminaison disponibles pour l’intégration :

- Environnement de test (`https://catalog-service-sandbox.adobe.io/graphql`) : utilisé pour le test et la validation avant la mise en ligne.
- Production (`https://catalog-service.adobe.io/graphql`) : utilisé pour le trafic en direct des marchands et des sites web Commerce

Toutes les instances de test Commerce utilisent le point de terminaison Sandbox.

Exécutez tous les tests de chargement sur le point de terminaison Sandbox. Avant de commencer le test de chargement, envoyez un [ticket d’assistance](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) afin que l’équipe des services puisse anticiper le trafic de serveur supplémentaire.

## Installation et configuration

Pour commencer à utiliser [!DNL Catalog Service] pour Adobe Commerce, les étapes suivantes sont requises :

- Installation de l’extension Catalog Service (`magento/catalog-service`)
- Configuration du service et de l’exportation des données
- Accès au service

### Installation de l’extension Catalog Service

>[!BEGINSHADEBOX]

**Condition préalable requise**

- Accédez à [repo.magento.com](https://repo.magento.com) pour installer l’extension. Pour la génération des clés et l’obtention des droits nécessaires, voir [Obtention de vos clés d’authentification](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/authentication-keys). Pour les installations dans le cloud, consultez le [Guide de l’infrastructure de Commerce on Cloud](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/authentication-keys)

- Accès à la ligne de commande du serveur applicatif Adobe Commerce.

>[!ENDSHADEBOX]

Installez la dernière version de l’extension Catalog Services (`magento/catalog-service`) sur une instance Adobe Commerce qui exécute Adobe Commerce version 2.4.4 ou ultérieure. Le service de catalogue est fourni en tant que métapaquet de compositeur à partir du référentiel [repo.magento.com](https://repo.magento.com).

>[!BEGINTABS]

>[!TAB Infrastructure cloud]

Utilisez cette méthode pour installer [!DNL Catalog Service] pour une instance de Commerce Cloud.

1. Sur votre poste de travail local, modifiez le répertoire du projet pour votre projet Adobe Commerce sur l’infrastructure cloud.

   >[!NOTE]
   >
   >Pour plus d’informations sur la gestion locale des environnements de projet Commerce, voir [Gestion des branches avec l’interface de ligne de commande](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/cli-branches) dans le _Guide de l’utilisateur d’Adobe Commerce on Cloud Infrastructure_.

1. Consultez la branche d’environnement pour mettre à jour à l’aide de l’interface de ligne de commande de Adobe Commerce Cloud.

   ```shell
   magento-cloud environment:checkout <environment-id>
   ```

1. Ajoutez le module Catalog Service.

   ```bash
   composer require magento/catalog-service --no-update
   ```

1. Mettez à jour les dépendances de package.

   ```bash
   composer update "magento/catalog-service"
   ```

1. Validez et poussez les modifications de code pour les fichiers `composer.json` et `composer.lock`.

1. Ajoutez, validez et poussez les modifications de code des fichiers `composer.json` et `composer.lock` dans l’environnement cloud.

   ```shell
   git add -A
   git commit -m "Add catalog service module"
   git push origin <branch-name>
   ```

   La publication des mises à jour dans l’environnement cloud lance le [processus de déploiement cloud de Commerce](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/process) pour appliquer les modifications. Vérifiez l’état du déploiement à partir du [log de déploiement](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/log-locations#deploy-log).

>[!TAB Sur site]

Utilisez cette méthode pour installer [!DNL Catalog Service] pour une instance sur site.

1. Utilisez le compositeur pour ajouter le module de service de catalogue à votre projet :

   ```bash
   composer require magento/catalog-service --no-update
   ```

1. Mettez à jour les dépendances et installez l’extension :

   ```bash
   composer update  "magento/catalog-service"
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

### Configuration du service et de l’exportation des données

Après avoir installé [!DNL Catalog Service], effectuez les tâches suivantes pour intégrer le service de catalogue à votre instance Adobe Commerce. Cette intégration permet la synchronisation et la communication des données entre l’instance Commerce, le service de catalogue et d’autres services annexes. La synchronisation des données est gérée par l’[ extension d’exportation des données SaaS](../data-export/overview.md).

1. Configurez le [ Connecteur de services Commerce](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/user-guides/integration-services/saas) en spécifiant les clés d’API et en sélectionnant un espace de données SaaS.

   La configuration de Commerce Services Connector est un processus unique requis pour utiliser les services Adobe Commerce tels que le service de catalogue, la recherche en direct et le Recommendations de produit. Si vous avez déjà configuré le connecteur pour un autre service, ignorez cette étape.

1. Effectuez une synchronisation initiale des données à partir du [tableau de bord de Data Management](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard).

   La synchronisation initiale peut prendre de quelques minutes à des heures selon la taille du catalogue. Vous pouvez surveiller l’état de synchronisation à partir du tableau de bord Data Management. Après la synchronisation initiale, le catalogue exporte en permanence les données de produit afin de maintenir les services à jour.

   >[!NOTE]
   >
   >Vous pouvez également démarrer la synchronisation initiale à partir de la ligne de commande à l’aide de l’interface de ligne de commande de Commerce. Voir [Synchronisation initiale](../data-export/data-export-cli-commands.md#initial-sync) dans le _Guide d’exportation des données SaaS_.

Pour vous assurer que l’exportation du catalogue s’exécute correctement :

- [ Vérifiez que les tâches cron sont en cours d’exécution ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-readiness-check-issues).
- Vérifiez que les indexeurs s’exécutent à partir de [Admin](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) ou à l’aide de la commande d’interface de ligne de commande Commerce `bin/magento indexer:info`.
- Vérifiez que les indexeurs `Catalog Attributes Feed, Product Feed, Product Overrides Feed` et `Product Variant Feed` sont définis sur `Update by Schedule`.

### Surveillance et dépannage de la synchronisation des données

Depuis l’administrateur Commerce, vous pouvez surveiller le processus de synchronisation à l’aide du [tableau de bord de Data Management](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard). Utilisez l’ [interface de ligne de commande de Commerce](../data-export/data-export-cli-commands.md#troubleshooting) et les journaux pour gérer et résoudre les problèmes liés au processus.

### Accès au service

L’API GraphQL [!DNL Catalog Service] est accessible à partir du point d’entrée ` https://catalog-service.adobe.io/graphql` à l’aide de commandes de POST via HTTPS.

Dans vos requêtes GraphQL, vous devez spécifier plusieurs en-têtes HTTP, y compris la clé API publique que vous avez ajoutée à la configuration du connecteur Adobe Commerce Services dans l’Admin. Pour plus d’informations, consultez la documentation [ de Storefront Services GraphQL](https://developer.adobe.com/commerce/services/graphql/) .

### Configuration du pare-feu

Pour autoriser [!DNL Catalog Service] par le biais d’un pare-feu, ajoutez `commerce.adobe.io` à la liste autorisée.

## Service de catalogue et maillage d’API

Le [Mesh API pour Adobe Developer App Builder](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) permet aux développeurs d’intégrer des API privées ou tierces et d’autres interfaces avec des produits Adobe à l’aide d’Adobe IO.

Pour plus d’informations sur l’installation et la configuration, voir la rubrique [[!DNL Catalog Service] et maillage API](mesh.md) .

## Tableau de bord de la gestion des données

Pour plus d’informations sur la synchronisation des données [!DNL Catalog Service], consultez le [tableau de bord de Data Management](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard).
