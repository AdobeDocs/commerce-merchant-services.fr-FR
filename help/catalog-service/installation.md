---
title: Intégration et installation
description: "Découvrez comment installer [!DNL Catalog Service]"
exl-id: 4e9fbdc9-67a1-4703-b8c0-8b159e0cc2a7
source-git-commit: c33ec5a10f9f2570e971e968efd1524e0d384ecd
workflow-type: tm+mt
source-wordcount: '821'
ht-degree: 0%

---

# Intégration et installation

Installez le service de catalogue pour demander et recevoir des données de produit d’une instance Commerce à l’aide du [API GraphQL du service de catalogue](https://developer.adobe.com/commerce/services/graphql/catalog-service/).

>[!NOTE]
>
>Si votre instance Commerce utilise Live Search ou Product Recommendations, le service de catalogue est installé ou mis à jour automatiquement lorsque vous embarquez ou mettez à niveau ces services. Pour plus d’informations, voir les instructions d’installation pour [Recherche en direct](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/install) et [Recommendations de produit](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/getting-started/install-configure).

>[!BEGINSHADEBOX]

## Conditions préalables

Le processus d’intégration pour [!DNL Catalog Service] requiert l’accès à la ligne de commande du serveur. Si vous n’êtes pas familiarisé avec l’utilisation de la ligne de commande, demandez de l’aide à un développeur ou à un intégrateur système.

**Exigences logicielles**

- Adobe Commerce 2.4.4+
- PHP 8.1, 8.2
- Compositeur : 2.x

**Plateformes prises en charge**

- Adobe Commerce sur l’infrastructure cloud : 2.4.4+
- Adobe Commerce sur site : 2.4.4+

>[!ENDSHADEBOX]

## Points de fin

[!DNL Catalog Service] comporte deux points de terminaison disponibles pour l’intégration :

- Environnement de test (`https://catalog-service-sandbox.adobe.io/graphql`) : utilisé pour les tests et la validation avant la mise en ligne.
- Production (`https://catalog-service.adobe.io/graphql`) : utilisé pour le trafic en direct pour les marchands et les sites web Commerce.

Toutes les instances de test Commerce utilisent le point de terminaison Sandbox.

Exécutez tous les tests de chargement sur le point de terminaison Sandbox. Avant de commencer le test de chargement, envoyez une [ticket d’assistance](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) afin que l’équipe Services puisse anticiper le trafic de serveur supplémentaire.

## Installation et configuration

Pour commencer à utiliser [!DNL Catalog Service] Pour Adobe Commerce, les étapes suivantes sont requises :

- Installation des extensions d’exportation de données
- Configuration du service et de l’exportation des données
- Accès au service

### Installation des extensions d’exportation de données

Vous devez avoir accès à la ligne de commande du serveur pour terminer la [!DNL Catalog Service] processus d’intégration.

La variable [!DNL Catalog Service] est installé avec les clés du compositeur, liées au compte Commerce. [`mageid`](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-information/) fourni pendant le processus d’inscription. Le compositeur utilise ces clés lors de l’installation initiale d’Adobe Commerce, ou dans les cas où les clés du compositeur n’étaient pas précédemment enregistrées dans une instance externe `auth.json` fichier .

Voir [Obtention des clés d’authentification](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/authentication-keys.html) pour plus d’informations sur l’obtention des clés du compositeur.

La variable [!DNL Catalog Service] L’extension peut être installée sur l’infrastructure cloud Adobe Commerce et sur les instances sur site.

>[!BEGINTABS]

>[!TAB infrastructure cloud]

Utilisez cette méthode pour installer le [!DNL Catalog Service] pour une instance de Commerce Cloud.

1. Sur votre poste de travail local, modifiez le répertoire du projet pour votre projet Adobe Commerce sur l’infrastructure cloud.

   >[!NOTE]
   >
   >Pour plus d’informations sur la gestion locale des environnements de projet Commerce, voir [Gestion des branches à l’aide de l’interface de ligne de commande](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/cli-branches) dans le _Guide de l’utilisateur d’Adobe Commerce on Cloud Infrastructure_.

1. Consultez la branche d’environnement pour mettre à jour à l’aide de l’interface de ligne de commande de Adobe Commerce Cloud.

   ```shell
   magento-cloud environment:checkout <environment-id>
   ```

1. Ajoutez le module Catalog Service.

   ```bash
   composer require "magento/catalog-service" "^3.0.1" --no-update
   ```

1. Mettez à jour les dépendances de package.

   ```bash
   composer update "magento/catalog-service"
   ```

1. Validation et modification du code push pour la variable `composer.json` et `composer.lock` fichiers .

1. Ajoutez, validez et envoyez les modifications de code pour la variable `composer.json` et `composer.lock` dans l’environnement cloud.

   ```shell
   git add -A
   git commit -m "Add catalog service module"
   git push origin <branch-name>
   ```

   La publication des mises à jour déclenche l’événement [Processus de déploiement cloud Commerce](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/process) pour appliquer les modifications. Vérifiez l’état du déploiement à partir du [log de déploiement](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/log-locations#deploy-log).

>[!TAB Sur site]

Utilisez cette méthode pour installer le [!DNL Catalog Service] pour une instance sur site.

1. Utilisez le compositeur pour ajouter le module de service de catalogue à votre projet :

   ```bash
   composer require "magento/catalog-service" "^3.0.1"  --no-update
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

Après avoir installé la variable [!DNL Catalog Service], effectuez les tâches suivantes pour intégrer le service de catalogue à votre instance Adobe Commerce. Cette intégration permet la synchronisation et la communication des données entre l’instance Commerce, le service de catalogue et d’autres services annexes.

1. Configurez la variable [Connecteur Commerce Services](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/user-guides/integration-services/saas) en spécifiant les clés d’API et en sélectionnant un espace de données SaaS.

   La configuration de Commerce Services Connector est un processus unique requis pour utiliser les services Adobe Commerce tels que le service de catalogue, la recherche en direct et le Recommendations de produit. Si vous avez déjà configuré le connecteur pour un autre service, ignorez cette étape.

1. Effectuez une synchronisation initiale des données à partir de la variable [Tableau de bord de la gestion des données](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard).

   La synchronisation initiale peut prendre de quelques minutes à des heures selon la taille du catalogue. Vous pouvez surveiller l’état de synchronisation à partir du tableau de bord Data Management. Après la synchronisation initiale, le catalogue exporte en permanence les données de produit afin de maintenir les services à jour.

Pour vous assurer que l’exportation du catalogue s’exécute correctement :

- [Confirmation que les tâches cron sont en cours d’exécution](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-readiness-check-issues).
- Vérifiez que les indexeurs s’exécutent à partir du [Administration](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) ou à l’aide de la commande de l’interface de ligne de commande de Commerce `bin/magento indexer:info`.
- Vérifiez que la variable `Catalog Attributes Feed, Product Feed, Product Overrides Feed`, et `Product Variant Feed` les indexeurs sont définis sur `Update by Schedule`.

### Accès au service

La variable [!DNL Catalog Service] L’API GraphQL est accessible à partir de ` https://catalog-service.adobe.io/graphql` point d’entrée à l’aide de commandes POST sur HTTPS.

Dans vos requêtes GraphQL, vous devez spécifier plusieurs en-têtes HTTP, y compris la clé API publique que vous avez ajoutée à la configuration du connecteur Adobe Commerce Services dans l’Admin. Pour plus d’informations, voir [GraphQL des services Storefront](https://developer.adobe.com/commerce/services/graphql/) la documentation.

### Configuration du pare-feu

Pour autoriser [!DNL Catalog Service] via un pare-feu, ajoutez `commerce.adobe.io` à la liste autorisée.

## Service de catalogue et maillage d’API

La variable [Maillage d’API pour Adobe Developer App Builder](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) permet aux développeurs d’intégrer des API privées ou tierces, ainsi que d’autres interfaces avec des produits Adobe à l’aide des E/S d’Adobe.

Voir [[!DNL Catalog Service] et maillage API](mesh.md) pour plus d’informations sur l’installation et la configuration.

## Tableau de bord de la gestion des données

Pour plus d’informations sur [!DNL Catalog Service] synchronisation des données, voir [Tableau de bord de la gestion des données](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard).
