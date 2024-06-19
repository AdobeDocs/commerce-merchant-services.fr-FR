---
title: Consultez les journaux et dépannage
description: "Découvrez comment résoudre les problèmes [!DNL data export] erreurs utilisant les logs data-export et saas-export."
feature: Services
recommendations: noCatalog
source-git-commit: 8230756c203cb2b4bdb4949f116c398fcaab84ff
workflow-type: tm+mt
source-wordcount: '783'
ht-degree: 0%

---


# Révision des journaux et dépannage

La variable [!DNL data export] L’extension fournit des journaux pour effectuer le suivi des processus de collecte et de synchronisation des données.

## Journaux

Les journaux sont disponibles dans la variable `var/log` sur le serveur applicatif Commerce.

| nom du journal | filename | description |
|-----------------| ----------| -------------|
| Journal d’exportation des données SaaS | `commerce-data-export.log` | Fournit des informations sur les activités d’exportation de données telles que les événements d’entité et les déclencheurs de resynchronisation complets.  Chaque enregistrement de journal possède une structure spécifique et fournit des informations sur le flux, l’opération, l’état, le temps écoulé, l’ID de processus et l’appelant. |
| Journal des erreurs d’exportation des données SaaS | `data-export-errors.log` | Fournit des messages d’erreur et des traces de pile pour les erreurs qui se produisent pendant le processus de synchronisation des données. |
| Journal d’exportation SaaS | `saas-export.log` | Fournit des informations sur les données envoyées aux services Commerce SaaS. |
| Journal des erreurs d’exportation SaaS | `saas-export-errors.log` | Fournit des informations sur les erreurs qui se produisent lors de l’envoi de données aux services Commerce SaaS. |

Si vous ne voyez pas les données attendues pour un service Adobe Commerce, utilisez les journaux d’erreur pour l’extension d’exportation des données afin de déterminer où le problème s’est produit.

Vous pouvez étendre les journaux avec des données supplémentaires pour le suivi et le dépannage. Voir [Journalisation étendue](#extended-logging).

### Format du journal

Chaque enregistrement de journal possède la structure suivante.

```
[<log record datetime>] report.<log level>:
{
   "feed": "<feed name>",
   "operation": "<executed operation>",
   "status": "<status of operation>",
   "elapsed": "<time elaspsed from script run>",
   "pid": "<proccess id who executed `operation`>",
   "caller": "<who called this `operation`>"
} [] []
```

>[!NOTE]
>
>La chaîne basée sur JSON est embellie pour une meilleure lisibilité.

Le tableau suivant décrit les types d’opérations qui peuvent être enregistrés dans les journaux.

| Opération | Description | Exemple d&#39;appel |
|----------------------------|---------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|
| synchronisation complète | La synchronisation complète collecte et envoie toutes les données au SaaS pour un flux donné. | `bin/magento saas:resync --feed=products` |
| réindexation partielle | La synchronisation partielle collecte et envoie des données à SaaS pour les entités mises à jour uniquement dans un flux donné. Ce journal n’est présent que s’il existe des entités mises à jour. | `bin/magento cron:run --group=index` |
| reprise des éléments ayant échoué | Renvoie les éléments d’un flux donné à SaaS si l’opération de synchronisation précédente a échoué en raison d’une erreur d’application Commerce ou de serveur. Ce journal n’est présent que si des éléments ont échoué. | `bin/magento cron:run --group=saas_data_exporter`  (tout groupe cron &quot;*_data_exportateur&quot;) |
| synchronisation complète (héritée) | Synchronisation complète pour un flux donné en mode d’exportation hérité. | `bin/magento saas:resync --feed=categories` |
| réindexation partielle (héritée) | Envoie les entités mises à jour à SaaS pour un flux donné en mode d’exportation hérité. Ce journal n’est présent que s’il existe des entités mises à jour. | `bin/magento cron:run --group=index` |
| synchronisation partielle (héritée) | Envoie les entités mises à jour à SaaS pour un flux donné en mode d’exportation hérité. Ce journal n’est présent que s’il existe des entités mises à jour. | `bin/magento cron:run --group=saas_data_exporter` (tout groupe cron &quot;*_data_exportateur&quot;) |


### Exemples de journalisation

Lors d’une synchronisation complète, la progression est suivie et consignée toutes les 30 secondes par défaut. Voici un exemple d’entrée de journal.

```json
{
   "feed": "prices",
   "operation": "full sync",
   "status": "Progress: 2/5, processed: 200, synced: 100",
   "elapsed": "00:00:00 190 ms",
   "pid": "12824",
   "caller": "bin/magento saas:resync --feed=products"
}
```

Dans cet exemple, la variable `status` Les valeurs fournissent des informations sur l’opération de synchronisation :

- **`"Progress 2/5"`** indique que 2 itérations sur 5 ont été effectuées. Le nombre d’itérations dépend du nombre d’entités exportées.
- **`"processed: 200"`** indique que 200 éléments ont été traités.
- **`"synced: 100"`** indique que 100 éléments ont été envoyés à SaaS. On s&#39;attend à ce que `"synced"` n’est pas égal à `"processed"`. Voici un exemple :
   - **`"synced" < "processed"`** signifie que la table des flux n’a détecté aucune modification de l’élément par rapport à la version synchronisée précédemment. Ces éléments sont ignorés lors de l’opération de synchronisation.
   - **`"synced" > "processed"`** le même identifiant d’entité (par exemple, `Product ID`) peuvent avoir plusieurs valeurs dans des portées différentes. Par exemple, un produit peut être affecté à cinq sites web. Dans ce cas, vous pouvez avoir &quot;1 élément traité&quot; et &quot;5 éléments synchronisés&quot;.

+++ Exemple : log de resynchronisation complet du flux de prix

```
Price feed full resync:

[2024-03-05T21:00:51.754687+00:00] report.INFO: {"feed":"prices","operation":"full sync","status":"Initialize","elapsed":"383 ms","pid":"14469","caller":"bin\/magento saas:resync --feed=prices"} [] []
[2024-03-05T21:00:51.803178+00:00] report.INFO: {"feed":"prices","operation":"full sync","status":"Creating batch table `catalog_data_exporter_product_prices_index_batches`. Start position: 30515","elapsed":"434 ms","pid":"14469","caller":"bin\/magento saas:resync --feed=prices"} [] []
[2024-03-05T21:00:51.851878+00:00] report.INFO: {"feed":"prices","operation":"full sync","status":"Batch table `catalog_data_exporter_product_prices_index_batches` created. Total Items: 500, batches: ~1","elapsed":"482 ms","pid":"14469","caller":"bin\/magento saas:resync --feed=prices"} [] []
[2024-03-05T21:00:51.852548+00:00] report.INFO: {"feed":"prices","operation":"full sync","status":"start processing `500` items in `1` threads with `500` batch size","elapsed":"483 ms","pid":"14469","caller":"bin\/magento saas:resync --feed=prices"} [] []
[2024-03-05T21:00:52.288369+00:00] report.INFO: {"feed":"prices","operation":"full sync","status":"Progress 1\/1, processed 500, synced 0","elapsed":"919 ms","pid":"14469","caller":"bin\/magento saas:resync --feed=prices"} [] []
[2024-03-05T21:00:53.994249+00:00] report.INFO: {"feed":"prices","operation":"full sync","status":"Progress 1\/1, processed 500, synced 100","elapsed":"00:00:02 625 ms","pid":"14469","caller":"bin\/magento saas:resync --feed=prices"} [] []
[2024-03-05T21:00:53.995168+00:00] report.INFO: {"feed":"prices","operation":"full sync","status":"Complete","elapsed":"00:00:02 626 ms","pid":"14469","caller":"bin\/magento saas:resync --feed=prices"} [] []
```

+++

## Affichage et dépannage des journaux avec New Relic

Si vous stockez des journaux Adobe Commerce dans New Relic, vous pouvez ajouter des règles d’analyse afin d’améliorer la lisibilité et l’expérience de requête.

1. Connectez-vous à New Relic.

1. Accédez à `Logs => Parsing`.

1. Cliquez sur `Create parsing rule`.

1. Configurez la règle d’analyse en ajoutant les valeurs suivantes.

   - **Filtrage des journaux en fonction de NRQL**

     `filePath LIKE '%commerce-data-export%.log'`

   - **Règle d’analyse**

     `\[%{DATA:timestamp}\] report.%{DATA:logLevel} %{GREEDYDATA:feed:json}`

Cet exemple ajoute une règle qui vous permet d’interroger les journaux New Relic par type de flux, opération, etc.

**Exemple de chaîne de requête**—`feed.feed:"products" and feed.status:"Complete"`

## Journalisation étendue

Vous pouvez utiliser des variables d’environnement pour étendre les journaux avec des données supplémentaires pour le suivi et la résolution des problèmes.

### Vérification de la payload du flux

Inclure la payload du flux dans le journal d’exportation SaaS en ajoutant la variable `EXPORTER_EXTENDED_LOG=1` lors de la nouvelle synchronisation du flux.

```shell script
EXPORTER_EXTENDED_LOG=1 bin/magento saas:resync --feed=products
```

Une fois l’opération terminée, la charge utile du flux est disponible pour révision dans le journal d’exportation SaaS (`var/.log/saas-export.log`).

### Préserver la charge utile dans la table d’index du flux

Pour l’extension d’exportation des données SaaS Commerce (`magento/module-data-exporter`) 103.3.0 et versions ultérieures, les flux d’exportation immédiats conservent uniquement les données minimales requises dans la table d’index. Les flux incluent tous les flux d’état de stock et de catalogue.

La conservation des données de payload dans la table d’index n’est pas recommandée dans les environnements de production, mais elle peut s’avérer utile dans un environnement de développement. Inclure la charge utile du flux dans l’index en ajoutant la variable `PERSIST_EXPORTED_FEED=1` lors de la nouvelle synchronisation du flux.

```shell script
PERSIST_EXPORTED_FEED=1 bin/magento saas:resync --feed=products
```

### Exécution du profileur pour résoudre les problèmes de performances lentes

Si le processus de réindexation d’un flux spécifique prend un temps déraisonnable, exécutez le profileur pour collecter des données supplémentaires qui peuvent s’avérer utiles à l’équipe d’assistance.

Exécutez le profileur en ajoutant la variable `EXPORTER_PROFILER=1` Variable d’environnement lorsque vous exécutez la commande reindex.

```
EXPORTER_PROFILER=1 bin/magento indexer:reindex catalog_data_exporter_products
```

Les données du profileur sont stockées dans le journal d&#39;export des données (`var/log/commerce-data-export.log`) au format suivant :

```
<Provider class name>, <# of processed entities>, <execution time im ms>, <memory consumption in Mb>
```




