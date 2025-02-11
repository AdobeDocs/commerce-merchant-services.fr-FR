---
title: Consultez les journaux et dépannage
description: Découvrez comment résoudre les erreurs  [!DNL data export] à l’aide des logs data-export et saas-export.
feature: Services
exl-id: 55903c19-af3a-4115-a7be-9d1efaed8140
source-git-commit: b80bc2867f44e6123adb104eb148ac5e8f80b63d
workflow-type: tm+mt
source-wordcount: '1071'
ht-degree: 0%

---

# Révision des journaux et dépannage

L’extension [!DNL data export] fournit des journaux pour suivre les processus de collecte et de synchronisation des données.

## Journaux

Les journaux sont disponibles dans le répertoire `var/log` du serveur d’applications Commerce.

| nom du journal | filename | description |
|-----------------| ----------| -------------|
| Journal d’exportation des données SaaS | `commerce-data-export.log` | Fournit des informations sur les activités d’exportation de données telles que les événements d’entité et les déclencheurs de resynchronisation complets.  Chaque enregistrement de journal possède une structure spécifique et fournit des informations sur le flux, l’opération, l’état, le temps écoulé, l’ID de processus et l’appelant. |
| Journal des erreurs d’exportation des données SaaS | `data-export-errors.log` | Fournit des messages d’erreur et des traces de pile pour les erreurs qui se produisent pendant le processus de synchronisation des données. |
| Journal d’exportation SaaS | `saas-export.log` | Fournit des informations sur les données envoyées aux services Commerce SaaS. |
| Journal des erreurs d’exportation SaaS | `saas-export-errors.log` | Fournit des informations sur les erreurs qui se produisent lors de l’envoi de données aux services Commerce SaaS. |

Si vous ne voyez pas les données attendues pour un service Adobe Commerce, utilisez les journaux d’erreur pour l’extension d’exportation des données afin de déterminer où le problème s’est produit. Vous pouvez également étendre les journaux avec des données supplémentaires pour le suivi et la résolution des problèmes. Voir [Journalisation étendue](#extended-logging).

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
| reprise des éléments ayant échoué | Renvoie les éléments d’un flux donné à SaaS si l’opération de synchronisation précédente a échoué en raison d’une erreur d’application Commerce ou de serveur. Ce journal n’est présent que si des éléments ont échoué. | `bin/magento cron:run --group=saas_data_exporter` (tout groupe cron &quot;*_data_porter&quot;) |
| synchronisation complète (héritée) | Synchronisation complète pour un flux donné en mode d’exportation hérité. | `bin/magento saas:resync --feed=categories` |
| réindexation partielle (héritée) | Envoie les entités mises à jour à SaaS pour un flux donné en mode d’exportation hérité. Ce journal n’est présent que s’il existe des entités mises à jour. | `bin/magento cron:run --group=index` |
| synchronisation partielle (héritée) | Envoie les entités mises à jour à SaaS pour un flux donné en mode d’exportation hérité. Ce journal n’est présent que s’il existe des entités mises à jour. | `bin/magento cron:run --group=saas_data_exporter` (tout groupe cron &quot;*_data_porter&quot;) |


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

Dans cet exemple, les valeurs `status` fournissent des informations sur l’opération de synchronisation :

- **`"Progress 2/5"`** indique que 2 itérations sur 5 ont été terminées. Le nombre d’itérations dépend du nombre d’entités exportées.
- **`"processed: 200"`** indique que 200 éléments ont été traités.
- **`"synced: 100"`** indique que 100 éléments ont été envoyés à SaaS. `"synced"` ne doit pas être égal à `"processed"`. Voici un exemple :
   - **`"synced" < "processed"`** signifie que la table des flux n’a pas détecté de modifications dans l’élément par rapport à la version synchronisée précédemment. Ces éléments sont ignorés lors de l’opération de synchronisation.
   - **`"synced" > "processed"`** le même ID d’entité (par exemple, `Product ID`) peut avoir plusieurs valeurs dans des portées différentes. Par exemple, un produit peut être affecté à cinq sites web. Dans ce cas, vous pouvez avoir &quot;1 élément traité&quot; et &quot;5 éléments synchronisés&quot;.

+++ **Exemple : journal de resynchronisation complet du flux de prix**

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

## Dépannage

Si des données sont manquantes ou incorrectes dans les Services de commerce, vérifiez les journaux pour voir si un problème s’est produit pendant la synchronisation de l’instance Adobe Commerce vers la plateforme du service Commerce. Si nécessaire, utilisez la journalisation étendue pour ajouter des informations supplémentaires aux journaux à des fins de dépannage.

- commerce-data-export-errors.log - si une erreur s’est produite lors de la collecte de la phase
- saas-export-errors.log : si une erreur s’est produite lors de la transmission de la phase

Si des erreurs ne sont pas liées à la configuration ou à des extensions tierces, envoyez un [ticket de support](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=en#submit-ticket) avec autant d’informations que possible.

### Résolution des problèmes de synchronisation de catalogue {#resolvesync}

Lorsque vous déclenchez une nouvelle synchronisation des données, la mise à jour des données peut prendre jusqu’à une heure pour être répercutée dans les composants de l’interface utilisateur, tels que les unités de recherche en direct et de recommandation. Si vous constatez toujours des incohérences entre votre catalogue et les données sur le storefront Commerce, ou si la synchronisation du catalogue a échoué, reportez-vous à ce qui suit :

#### Incohérence des données

1. Affichez la vue détaillée du produit en question dans les résultats de la recherche.
1. Copiez la sortie JSON et vérifiez que le contenu correspond à ce que vous avez dans le catalogue [!DNL Commerce].
1. Si le contenu ne correspond pas, apportez une modification mineure au produit de votre catalogue, comme l’ajout d’un espace ou d’un point.
1. Attendez une nouvelle synchronisation ou [déclenchez une nouvelle synchronisation manuelle](#resync).

#### Synchronisation non en cours

Si la synchronisation ne s’exécute pas selon un calendrier ou si rien n’est synchronisé, reportez-vous à cet article [Base de connaissances](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/troubleshoot-product-recommendations-module-in-magento-commerce.html) .

#### Échec de la synchronisation

Si l’état de la synchronisation du catalogue est **Failed**, envoyez un [ticket de support](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket).

## Journalisation étendue

Pour plus d’informations sur les journaux, vous pouvez utiliser des variables d’environnement afin d’étendre les journaux avec des données supplémentaires pour le suivi et la résolution des problèmes.

Le répertoire `var/log/` contient deux fichiers journaux :

- commerce-data-export-errors.log - si une erreur s’est produite lors de la collecte de la phase
- saas-export-errors.log : si une erreur s’est produite lors de la transmission de la phase

Vous pouvez utiliser des variables d’environnement pour étendre les journaux avec des données supplémentaires pour le suivi et la résolution des problèmes.

### Vérification de la payload du flux

Insérez la charge utile du flux dans le journal d’exportation SaaS en ajoutant la variable d’environnement `EXPORTER_EXTENDED_LOG=1` lorsque vous resynchronisez le flux.

```shell script
EXPORTER_EXTENDED_LOG=1 bin/magento saas:resync --feed=products
```

Une fois l’opération terminée, la charge utile du flux est disponible pour révision dans le journal d’exportation SaaS (`var/.log/saas-export.log`).

### Préserver la charge utile dans la table d’index du flux

Pour l’extension d’exportation de données SaaS Commerce (`magento/module-data-exporter`) 103.3.0 et versions ultérieures, les flux d’exportation immédiats conservent uniquement les données minimales requises dans la table d’index. Les flux incluent tous les flux d’état de stock et de catalogue.

La conservation des données de payload dans la table d’index n’est pas recommandée dans les environnements de production, mais elle peut s’avérer utile dans un environnement de développement. Insérez la charge utile du flux dans l’index en ajoutant la variable d’environnement `PERSIST_EXPORTED_FEED=1` lorsque vous resynchronisez le flux.

```shell script
PERSIST_EXPORTED_FEED=1 bin/magento saas:resync --feed=products
```

### Exécution du profileur pour résoudre les problèmes de performances lentes

Si le processus de réindexation d’un flux spécifique prend un temps déraisonnable, exécutez le profileur pour collecter des données supplémentaires qui peuvent s’avérer utiles à l’équipe d’assistance.

Exécutez le profileur en ajoutant la variable d&#39;environnement `EXPORTER_PROFILER=1` lorsque vous exécutez la commande reindex.

```
EXPORTER_PROFILER=1 bin/magento indexer:reindex catalog_data_exporter_products
```

Les données du profileur sont stockées dans le journal d’exportation des données (`var/log/commerce-data-export.log`) au format suivant :

```
<Provider class name>, <# of processed entities>, <execution time im ms>, <memory consumption in Mb>
```
