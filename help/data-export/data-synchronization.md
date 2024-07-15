---
title: Synchronisation des données avec l’exportation des données SaaS
description: Découvrez comment le  [!DNL SaaS Data Export] collecte et synchronise les données entre les instances Adobe Commerce et les services SaaS connectés.
role: Admin, Developer
recommendations: noCatalog
exl-id: 530a6ed7-46ec-45fc-94e9-c850168e8aed
source-git-commit: af9de40a717d2cb55a5f42483bd0e4cbcd913f64
workflow-type: tm+mt
source-wordcount: '770'
ht-degree: 0%

---

# Synchronisation des données avec l’exportation des données SaaS

Lorsque vous installez un service Commerce qui requiert l’exportation de données, tel que Catalog Service, Live Search ou Product Recommendations, une collection de modules d’exportation de données Saas est installée pour gérer le processus de collecte et de synchronisation des données.

L’exportation des données SaaS déplace en continu les données de produit d’une instance Adobe Commerce vers la plateforme Commerce Services pour maintenir les données à jour. Par exemple, le Recommendations de produit nécessite des informations de catalogue actuelles pour renvoyer avec précision des recommandations avec les noms, les tarifs et la disponibilité corrects. Utilisez le [tableau de bord de Data Management](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/user-guides/data-services/catalog-sync) pour observer et gérer le processus de synchronisation, ou l’interface de ligne de commande pour déclencher une synchronisation et réindexer les données de produit à utiliser par les services Commerce.

Le diagramme suivant illustre le flux d’exportation des données SaaS.

![Flux de collecte et de synchronisation d’exportation des données SaaS pour Adobe Commerce](assets/data-export-flow.png){width="900" zoomable="yes"}

Les principaux composants du flux d’exportation des données SaaS sont les suivants :

- Les modules d’exportation de données SaaS qui collectent les données pour les flux d’Adobe Commerce, assemblent les éléments de flux, écoutent les mises à jour et conservent l’état du flux.
- SaaS exporte les modules qui exportent des données, configurent le routage et publient les flux sur les services connectés.
- Le service Adobe Commerce gère le processus d’ingestion des données pour valider les flux entrants et conserver les mises à jour des services connectés.

## Modes de synchronisation

L’exportation des données SaaS a deux modes pour traiter les flux d’entité :

- **Mode d’exportation immédiat** : dans ce mode, les données sont collectées et envoyées immédiatement au service Commerce en une seule itération. Ce mode accélère la remise des mises à jour des entités au service Commerce et réduit la taille de stockage des tables de flux.

- **Mode d’exportation hérité** : dans ce mode, les données sont collectées dans un seul processus. Ensuite, une tâche cron envoie les données collectées aux services de commerce connectés. Dans les entrées de journal d’exportation des données, les flux qui utilisent le mode hérité sont étiquetés `(legacy)`.

## Types de synchronisation

L’exportation des données SaaS prend en charge trois types de synchronisation : synchronisation complète, synchronisation partielle et reprise de la synchronisation des éléments ayant échoué.

### Synchronisation complète

Après la connexion d’une instance Adobe Commerce au service Commerce, effectuez une synchronisation complète pour envoyer les données de flux d’entité d’Adobe Commerce au service connecté.

>[!NOTE]
>
>La synchronisation complète est principalement destinée à la phase d’intégration. Évitez toute utilisation régulière pour éviter la surcharge de la base de données. Après la synchronisation initiale, les modifications en cours sont synchronisées automatiquement à l’aide d’une synchronisation partielle.

### Synchronisation partielle

Avec une synchronisation partielle, l’exportation des données SaaS envoie automatiquement les mises à jour de l’application Commerce, telles que les modifications de nom de produit ou les mises à jour de prix, aux services commerciaux connectés.

Le processus d’exportation des données utilise les tâches cron suivantes pour automatiser l’opération de synchronisation partielle.

- &quot;index&quot; tâches du groupe cron :
   - La tâche `indexer_reindex_all_invalid` réindexe tous les flux non valides. Il s’agit d’une tâche Adobe Commerce cron standard.
   - La tâche `saas_data_exporter` est destinée aux flux d’exportation hérités.
   - La tâche `sales_data_exporter` est spécifique au flux d’exportation des données de vente.

Ces tâches s’exécutent toutes les minutes.

Pour que la synchronisation partielle fonctionne, l’application Commerce requiert la configuration suivante :

- [La planification des tâches est activée via les tâches cron](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/next-steps/configuration.html)

- Tous les indexeurs d’exportation de données SaaS sont configurés en mode `Update by Schedule`.

  Dans la version 103.1.0 et ultérieure de l’exportation des données SaaS, le mode `Update by Schedule` est activé par défaut. Vous pouvez vérifier la configuration de l’index sur le serveur à l’aide de la commande d’interface de ligne de commande de Commerce, `bin/magento indexer:show-mode | grep -i feed`

### Retry Failed Items sync

La synchronisation Retry failed items sync utilise un processus distinct pour renvoyer les éléments qui n’ont pas pu être synchronisés en raison d’erreurs au cours du processus de synchronisation, par exemple une erreur d’application, une interruption réseau ou une erreur de service SaaS. L’implémentation de cette synchronisation est également basée sur les tâches cron.

- `resync_failed_feeds_data_exporter` tâches de groupe cron :
   - La tâche `<feed name>_feed_resend_failed_feeds_items` renvoie les éléments qui n’ont pas pu être synchronisés, par exemple `products_feed_resend_failed_items`.

### Afficher et gérer le processus de synchronisation

La plupart des activités de synchronisation sont traitées automatiquement en fonction du paramétrage de l&#39;application. Cependant, l’exportation des données SaaS fournit également des outils pour gérer le processus.

- Les utilisateurs administrateurs peuvent afficher et suivre la progression de la synchronisation et obtenir des informations sur les données à partir du [tableau de bord de Data Management](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard).

- Les développeurs, les intégrateurs système ou les administrateurs ayant accès au serveur d’applications Commerce peuvent gérer le processus de synchronisation et les flux de données à l’aide de l’outil de ligne de commande Adobe Commerce (CLI). Voir [Référence de commande d’exportation de données](data-export-cli-commands.md).

### Vérification de la configuration des applications Commerce

La synchronisation partielle et la reprise des éléments ayant échoué fonctionnent uniquement si l’instance Commerce a été configurée correctement. En règle générale, la configuration est effectuée lors de la configuration du service Commerce. Si l&#39;export des données ne fonctionne pas correctement, vérifiez la configuration suivante.

- [ Vérifiez que les tâches cron sont en cours d’exécution ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-readiness-check-issues).

- Vérifiez que les indexeurs s’exécutent à partir de [Admin](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) ou à l’aide de la commande d’interface de ligne de commande Commerce `bin/magento indexer:info`.

- Vérifiez que les indexeurs des flux suivants sont définis sur `Update by Schedule` : Attributs de catalogue, Produit, Remplacements de produit et Variante de produit. Vous pouvez vérifier les indexeurs à partir de la [gestion des index](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) dans l’administrateur ou à l’aide de l’interface de ligne de commande (`bin/magento indexer:show-mode | grep -i feed`).
