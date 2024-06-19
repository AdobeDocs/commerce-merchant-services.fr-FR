---
title: Amélioration des performances d’exportation des données SaaS
description: "Découvrez comment améliorer les performances d’exportation des données SaaS pour les services Commerce en utilisant le mode d’exportation de données multithreads."
role: Admin, Developer
recommendations: noCatalog
source-git-commit: 8230756c203cb2b4bdb4949f116c398fcaab84ff
workflow-type: tm+mt
source-wordcount: '652'
ht-degree: 0%

---

# Amélioration des performances d’exportation des données SaaS

**Mode d&#39;export de données multi-thread** accélère le processus d’exportation en divisant les données de flux en lots et en les traitant en parallèle.

Les développeurs ou les intégrateurs système peuvent améliorer les performances en utilisant le mode d’exportation de données multi-thread au lieu du mode par défaut à thread unique. En mode thread unique, il n’existe aucune mise en parallèle du processus d’envoi du flux. En outre, en raison des limites par défaut définies, tous les clients ne peuvent utiliser qu’un seul thread. Dans la plupart des cas, la personnalisation de la configuration n’est pas requise.

## Observations relatives à l’utilisation du mode multi-thread

Lorsque vous utilisez des services d’exportation de données, vous souhaitez optimiser les performances tout en assurant une synchronisation précise.
Adobe recommande d’utiliser la configuration par défaut pour l’ingestion des données, qui répond généralement aux exigences de synchronisation des commerçants Commerce. Cependant, il existe des scénarios où la personnalisation peut accélérer le temps de traitement.

Tenez compte des facteurs clés suivants lorsque vous décidez de personnaliser ou non la configuration de l’exportation des données :

- **Synchronisation initiale**- Évaluer le nombre de produits et [estimation du volume des données et du temps de transmission](estimate-data-volume-sync-time.md) selon la configuration par défaut. Posez-vous la question suivante : pouvez-vous attendre la synchronisation initiale des données après l’intégration d’un service Commerce ?

- **Ajout de nouvelles vues de magasin ou de sites web**-Si vous prévoyez d’ajouter des vues de magasin ou des sites web avec le même nombre de produits après mise en ligne, estimez le volume des données et le temps de transmission. Déterminez si le temps de synchronisation est acceptable avec la configuration par défaut ou si un traitement multi-thread est nécessaire.

- **Imports réguliers**-Anticipez les importations régulières, telles que les mises à jour de prix ou les changements d’état des stocks. Déterminez si ces mises à jour peuvent être appliquées dans un délai acceptable ou si un traitement plus rapide est nécessaire.

- **Poids du produit**- Déterminez si vos produits sont légers ou lourds. Ajustez la taille du lot en conséquence si les descriptions ou attributs de produit gonflent la taille du produit.

N’oubliez pas que la planification attentive, notamment l’estimation du volume des données et du temps de synchronisation, peut souvent éliminer le besoin de personnalisation. Planifiez les opérations d’ingestion des flux en fonction de ces estimations afin d’obtenir des résultats optimaux.

>[!NOTE]
>
>Adobe recommande d’être prudent lors de l’utilisation du traitement multithread. Cette fonctionnalité est une fonctionnalité d’accès anticipé qui est encore en cours d’amélioration. Si vous configurez le multithread pour des performances plus rapides, vous pouvez déclencher des garde-fous Adobe Commerce Services inclus afin d’éviter toute mauvaise utilisation du système lors de l’ingestion des données. Ces barrières de sécurité empêchent également les utilisateurs de déclencher des modifications de synchronisation pouvant surcharger le système. Lorsque les barrières de sécurité sont déclenchées, les demandes sont bloquées et le système renvoie des erreurs 429. Si vous rencontrez ces erreurs, ajustez votre configuration et envoyez un ticket d’assistance pour obtenir de l’aide.

## Configuration du multi-thread

Le mode multi-thread est pris en charge pour tous [méthodes de synchronisation](data-synchronization.md#synchronization-process): synchronisation complète, synchronisation partielle et synchronisation des éléments ayant échoué. Pour configurer le multithread, vous spécifiez le nombre de threads et la taille de lot à utiliser lors de la synchronisation.

- `threadCount` est le nombre de threads activés pour traiter les entités. Par défaut `threadCount` is `1`.
- `batchSize` est le nombre d’entités qui sont traitées dans une itération. Par défaut `batchSize` is `100` enregistre tous les flux, à l’exception du flux de prix. Pour le flux de prix, la valeur par défaut est `500` enregistrements.

Vous pouvez configurer le multithread comme option temporaire lors de l’exécution d’une commande de resynchronisation ou en ajoutant la configuration multithread à la configuration de l’application Adobe Commerce.

>[!NOTE]
>
>Veillez à aligner les performances de l’exportation des données SaaS avec la limite de taux définie pour un client du côté client.

### Configuration du multi-thread au moment de l’exécution

Lorsque vous exécutez une commande de synchronisation complète à partir de la ligne de commande, spécifiez le traitement multi-thread en ajoutant la variable `threadCount` et `batchSize` à la commande de l’interface de ligne de commande.

```
bin/magento saas:resync --feed=products --threadCount=2 --batchSize=200
```

Les options spécifiées sur la ligne de commande remplacent la configuration d’exportation des données spécifiée dans l’application Adobe Commerce. `config.php` fichier .

### Ajout d’un multi-thread à la configuration Commerce

Pour traiter toutes les opérations d’exportation de données à l’aide de plusieurs threads, les intégrateurs système ou les développeurs peuvent modifier le nombre de threads et la taille de lot de chaque flux dans la configuration de l’application Commerce.

Ces modifications peuvent être appliquées en ajoutant des valeurs personnalisées à la variable [section système](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/files/config-reference-configphp#system) du fichier de configuration, `app/etc/config.php`.

**Exemple : paramétrer le multithread pour les produits et les prix**

```php
<?php
return [
    'system' => [
        'default' => [
            'commerce_data_export' => [
                'feeds' => [
                    'products' => [
                        'batch_size' => 100,
                        'thread_count' => 2,
                    ],
                    'prices' => [
                        'batch_size' => 400,
                        'thread_count' => 4,
                    ]
                ]
            ],
//   ...
```
