---
title: Intégration et installation
description: "Découvrez comment installer [!DNL Catalog Service]"
exl-id: 4e9fbdc9-67a1-4703-b8c0-8b159e0cc2a7
source-git-commit: 8a98e069cd9ec3d2c4fec33485e5c8186d94518f
workflow-type: tm+mt
source-wordcount: '629'
ht-degree: 0%

---

# Intégration et installation

Les vidéos suivantes vous guident tout au long de la [!DNL Catalog Service] processus.

**Partie 1**: intégration et installation

>[!VIDEO](https://video.tv.adobe.com/v/3415599)

**Partie 2**: en utilisant la variable [!DNL Catalog Service]

>[!VIDEO](https://video.tv.adobe.com/v/3415600)

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

Toutes les instances de test de Commerce doivent utiliser le point de terminaison Sandbox.

Le test de chargement ne doit être effectué que sur le point de terminaison Sandbox. Il est recommandé d’effectuer une [ticket d’assistance](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) être ouvert lors du test de chargement afin que l’équipe Services puisse anticiper le trafic de serveur supplémentaire.

## Installation et configuration

Pour commencer à utiliser [!DNL Catalog Service] Pour Adobe Commerce, les étapes suivantes sont requises :

- Installation des extensions d’exportation de données
- Configuration du service et de l’exportation des données
- Accès au service

### Installation des extensions d’exportation de données

Le processus d’intégration pour [!DNL Catalog Service] requiert l’accès à la ligne de commande du serveur.

La variable [!DNL Catalog Service] L’extension peut être installée sur l’infrastructure cloud Adobe Commerce et sur les instances sur site.

La variable [!DNL Catalog Service] est installé avec les clés du compositeur, liées au compte Commerce. [`mageid`](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-information/) fourni pendant le processus d’inscription. Le compositeur utilise ces clés lors de l’installation initiale d’Adobe Commerce, ou dans les cas où les clés du compositeur n’étaient pas précédemment enregistrées dans une instance externe `auth.json` fichier .

Voir [Obtention des clés d’authentification](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/authentication-keys.html) pour plus d’informations sur l’obtention des clés du compositeur.

#### Adobe Commerce sur l’infrastructure cloud

Utilisez cette méthode pour installer le [!DNL Catalog Service] pour une instance de Commerce Cloud.

1. Sur votre poste de travail local, modifiez le répertoire de votre projet.
1. Ajoutez le module Catalog Service.

   ```bash
   composer require "magento/catalog-service" "^3.0.1"
   ```

1. Mettez à jour les dépendances de package.

   ```bash
   composer update
   ```

1. Validation et modification du code push pour la variable `composer.json` et `composer.lock` fichiers .

#### Sur site

Utilisez cette méthode pour installer le [!DNL Catalog Service] pour une instance sur site.

1. Utilisez le compositeur pour ajouter le module de service de catalogue à votre projet :

   ```bash
   composer require "magento/catalog-service" "^3.0.1"
   ```

1. Mettez à jour les dépendances et installez l’extension :

   ```bash
   composer update
   ```

1. Mettre à niveau Adobe Commerce :

   ```bash
   bin/magento setup:upgrade
   ```

1. Effacez le cache :

   ```bash
   bin/magento cache:clean
   ```

### Configuration du service et de l’exportation des données

Après l’installation [!DNL Catalog Service], vous devez configurer le [Connecteur Commerce Services](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html#apikey) en spécifiant les clés d’API et en sélectionnant un espace de données SaaS.

Une fois la configuration SaaS terminée, effectuez une synchronisation initiale des données en utilisant la variable [Tableau de bord de la gestion des données](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard). Vous pouvez utiliser ce tableau de bord pour surveiller l’état de synchronisation des données de produit transférées de la base de données Commerce vers les services Commerce SaaS.

Pour vous assurer que l’exportation du catalogue s’exécute correctement :

- Vérifiez que les tâches cron sont en cours d’exécution.
- Vérifiez que les indexeurs sont en cours d’exécution.
- Assurez-vous que la variable `Catalog Attributes Feed, Product Feed, Product Overrides Feed`, et `Product Variant Feed` les indexeurs sont définis sur &quot;Mise à jour par planification&quot;.

La synchronisation initiale peut prendre de quelques minutes à des heures selon la taille du catalogue. Après la synchronisation initiale, le catalogue exporte en permanence les données de produit du serveur Commerce vers les services Commerce afin de maintenir les services à jour. Pour surveiller l’état de la synchronisation, reportez-vous à la section [[!DNL Data Management Dashboard]](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-dashboard.html).

### Accès au service

La variable [!DNL Catalog Service] L’API est accessible à l’aide des commandes du POST via HTTPS.

Pour obtenir la clé api, accédez à la zone Commerce Service Connector dans l’administrateur et copiez la clé API publique.

Lisez la section [Documentation GraphQL](https://developer.adobe.com/commerce/services/graphql/) pour comprendre comment interroger et envoyer les en-têtes nécessaires à la génération de requêtes d’API.

Pour autoriser [!DNL Catalog Service] via un pare-feu, ajoutez `commerce.adobe.io` à la liste autorisée.

## Service de catalogue et maillage d’API

La variable [Maillage d’API pour Adobe Developer App Builder](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) permet aux développeurs d’intégrer des API privées ou tierces, ainsi que d’autres interfaces avec des produits Adobe à l’aide des E/S d’Adobe.

Voir  [[!DNL Catalog Service] et maillage API](mesh.md) pour plus d’informations sur l’installation et la configuration.

## Tableau de bord de la gestion des données

Les utilisateurs peuvent se référer à la section [Tableau de bord de la gestion des données](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-dashboard.html) pour plus d’informations sur [!DNL Catalog Service] synchronisation des données.
