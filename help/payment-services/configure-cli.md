---
title: Configuration de ligne de commande
description: Après l’installation, vous pouvez configurer [!DNL Payment Services] à l’aide de l’interface de ligne de commande.
role: Admin, Developer
level: Intermediate
exl-id: 265ab1be-fe52-41f3-85cb-addbc2ddfb17
source-git-commit: bcb817775fe9cd9ac7096931dd40d5ec0c4a5cfc
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Configuration de ligne de commande

Après l’installation [!DNL Payment Services], vous pouvez facilement la configurer à partir de [au sein de l’administrateur](configure-admin.md) ou via l’interface de ligne de commande.

## Configurer l’exportation des données

[!DNL Payment Services] combine les données de commande exportées depuis Magento Open Source et Adobe Commerce avec les données de paiement agrégées des fournisseurs de paiement afin de créer des rapports utiles. Le [!DNL Payment Services] l’extension utilise des indexeurs pour collecter efficacement toutes les données nécessaires aux rapports.

Pour en savoir plus sur les données utilisées dans [!DNL Payment Services] reporting, voir [Rapport d’état des paiements de commande](order-payment-status.md#data-used-in-the-report).

### Configuration de cron sur Magento Open Source

Si vous souhaitez utiliser une `BY SCHEDULE` en mode index sur Magento Open Source, vous devez configurer cron. Voir [Configuration et exécution de cron](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html).

### Définition des indexeurs

Les données de commande sont exportées et conservées dans le service de paiement, à l’aide de l’un des deux modes d’index :`ON SAVE` (par défaut) ou `BY SCHEDULE` (recommandé).

Les index suivants sont destinés à [!DNL Payment Services]:

| Code | Nom | Description |
|    ---    |  ---  |  ---  |
| `sales_order_data_exporter` | Flux de commande commerciale | Construit l’index des données de commande |
| `sales_order_status_data_exporter` | Flux États de commande commerciale | Génère l’index des données sur les états des commandes client |
| `store_data_exporter` | Flux de stockage | Création de l’index des données de magasin |

Pour modifier le mode d’index pour les trois indexeurs, exécutez :

```bash
bin/magento indexer:set-mode schedule sales_order_data_exporter sales_order_status_data_exporter store_data_exporter
```

>[!TIP]
>
>Si vous ne spécifiez aucun indexeur dans votre commande, tous les indexeurs sont mis à jour vers la même valeur. Si vous souhaitez modifier un indexeur spécifique, vous devez le lister dans votre commande.

Pour en savoir plus sur la modification manuelle du mode d’un indexeur, voir [Configuration des indexeurs](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html#configure-indexers){target=&quot;_blank&quot;} dans la documentation destinée aux développeurs. Pour savoir comment le modifier dans Admin, voir [Gestion des index](https://docs.magento.com/user-guide/system/index-management.html#change-the-index-mode){target=&quot;_blank&quot;} dans le guide d’utilisation principal.

### Réindexation manuelle des données

Vous pouvez réindexer manuellement les données au lieu d’attendre qu’elles se produisent automatiquement. Voir [Reindex](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html#reindex){target=&quot;_blank&quot;} dans [Gestion des indexeurs](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html){target=&quot;_blank&quot;} pour plus d’informations.

When `BY SCHEDULE` est défini, le système effectue le suivi des entités modifiées et la tâche cron met à jour l’index pour ces entités selon une planification définie. Voir [Exécutez cron à partir de la ligne de commande](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html#config-cli-cron-group-run) in [Configuration et exécution de cron](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html)) pour savoir comment déclencher manuellement l’indexation à l’aide de tâches cron.

### Envoi de données réindexées au service de paiement

Une fois les données indexées, elles sont envoyées automatiquement à [!DNL Payment Services]. Vous pouvez également déclencher manuellement le processus d&#39;envoi de données indexées avec cette commande :

```bash
bin/magento saas:resync --feed [feedName]
```

Utilisez les options de commande suivantes :

| Commande | Description |
|  ---  |  ---  |
| `bin/magento saas:resync --feed [feedName]` | Réindexation du flux spécifié et envoi au service correspondant |
| `bin/magento saas:resync --no-reindex` | Ignore l’indexation et envoie des données non synchronisées à partir des index. |

Le `--feed` vous permet de spécifier le flux à envoyer :

| Flux | Description |
|  ---  |  ---  |
| `paymentServicesOrdersProduction` | Flux de commandes en mode Production |
| `paymentServicesOrdersSandbox` | Flux de commandes en mode sandbox |
| `paymentServicesOrderStatusesProduction` | Statuts des commandes en mode Production |
| `paymentServicesOrderStatusesSandbox` | Statuts des commandes en mode sandbox |
| `paymentServicesStoresProduction` | Magasins en mode de production |
| `paymentServicesStoresSandbox` | Magasins en mode sandbox |

Toutes les données nécessaires aux rapports sont envoyées à [!DNL Payment Services] automatiquement si cron est configuré et installé. Vous pouvez également déclencher manuellement le processus d’envoi de données cron vers [!DNL Payment Services].

```bash
bin/magento cron:run --group payment_services_data_export
```

Pour en savoir plus sur la réindexation et les indexeurs, voir [Gestion des indexeurs](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html) dans la documentation destinée aux développeurs.
