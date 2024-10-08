---
title: Interface de ligne de commande de l’exportation des données SaaS
description: Découvrez comment utiliser les commandes de l’interface de ligne de commande pour gérer les flux et les processus pour les services SaaS  [!DNL data export extension]  d’Adobe Commerce.
exl-id: f360d920-7d02-4317-8c56-c7d4c4ed2ff2
source-git-commit: b80bc2867f44e6123adb104eb148ac5e8f80b63d
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 0%

---

# Référence de l’interface de ligne de commande de l’exportation de données SaaS

Les développeurs et les administrateurs système peuvent gérer les opérations de synchronisation pour l’exportation des données SaaS à l’aide de l’ [outil de ligne de commande Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/config-cli) (interface de ligne de commande). La commande `saas:resync` est incluse dans le package `magento/saas-export`.

Adobe ne recommande pas d&#39;utiliser régulièrement la commande `saas:resync`. Les scénarios types d’utilisation de la commande sont les suivants :

- Synchronisation initiale
- L’ [ identifiant de l’espace de données SaaS](https://experienceleague.adobe.com/en/docs/commerce-admin/config/services/saas) a été modifié et vous devez synchroniser les données dans le nouvel espace de données.
- Dépannage

## Synchronisation initiale

>[!NOTE]
>Si vous utilisez la recherche en direct ou le Recommendations de produit, il n’est pas nécessaire d’exécuter la synchronisation initiale. Le processus est lancé automatiquement une fois que vous avez connecté le service à votre instance Commerce.

Lorsque vous déclenchez un `saas:resync` à partir de la ligne de commande, selon la taille de votre catalogue, la mise à jour des données peut prendre de quelques minutes à quelques heures.

Pour la synchronisation initiale, Adobe recommande d’exécuter les commandes dans l’ordre suivant :

```bash
bin/magento saas:resync --feed productattributes
bin/magento saas:resync --feed products
bin/magento saas:resync --feed scopesCustomerGroup
bin/magento saas:resync --feed scopesWebsite
bin/magento saas:resync --feed prices
bin/magento saas:resync --feed productoverrides
bin/magento saas:resync --feed variants
bin/magento saas:resync --feed categories
bin/magento saas:resync --feed categoryPermissions
```

## Exemples de commandes

Avant d’utiliser des commandes `saas:resync`, passez en revue les [descriptions d’option](#command-options).

- Effectuez une resynchronisation complète pour un flux d’entité.

  ```
  bin/magento saas:resync --feed='<FEED_NAME>' 1
  ```

  Les flux qui ont déjà été exportés avec succès ne sont pas resynchronisés.

- Resynchronisation complète des données de nettoyage et de flux spécifiées

  ```
  bin/magento saas:resync --feed='FEED_NAME' --cleanup-feed
  ```

  Utilisez uniquement après avoir effectué une opération [!DNL Data Space ID Cleanup].

- Pour les flux d’exportation immédiats, renvoyez toutes les données aux services Commerce connectés sans tronquer les données d’index dans la table des flux.

  ```
   bin/magento saas:resync --feed='FEED_NAME' --no-reindex
  ```

- Liste des commandes et options disponibles avec des descriptions.

  ```
  bin/magento saas:resync --help
  ```

## Options de commande

Les options suivantes sont disponibles pour la gestion des opérations `saas:resync`.

>[!NOTE]
>
>La commande `saas:resync` prend également en charge des options avancées pour améliorer les commandes d’exportation de données en augmentant la taille du lot et en ajoutant un traitement multithread. Voir [Personnalisation du traitement de l’exportation](customize-export-processing.md).

### `feed`

Cette option obligatoire spécifie l’entité de flux à resynchroniser, telle que `products`.

La valeur de l’option `feed` peut inclure n’importe quel flux d’entité disponible :

- `products` : flux de données de produit
- `productAttributes` : flux de données des attributs de produit
- `categories` : flux de données de catégories
- `variants` : flux de données de variantes de produits configurables
- `prices` : flux de données sur les prix des produits
- `categoryPermissions` : flux de données des autorisations de catégorie
- `productOverrides` : flux de données des autorisations de produit
- `inventoryStockStatus` : flux de données d’état du stock
- `scopesWebsite` : sites web avec des magasins et des flux de données de vues de magasin
- `scopesCustomerGroup` : flux de données de groupes de clients
- `orders` : flux de données des commandes client

Selon les [services Commerce](../landing/saas.md) installés, un autre ensemble de flux peut être disponible pour la commande `saas:resync`.

### `no-reindex`

Cette option réenvoie les données de catalogue existantes vers [!DNL Commerce Services] sans réindexation. Si cette option n’est pas spécifiée, la commande exécute une réindexation complète avant de synchroniser les données.

Le comportement de cette option dépend de l’exportation ou non du flux en [mode d’exportation hérité ou immédiat](data-synchronization.md#synchronization-modes)

- Pour les flux d’exportation hérités, le processus de synchronisation ne tronque pas les données indexées dans la table des flux. Au lieu de cela, il envoie toutes les données au service Adobe Commerce.
- Pour les flux d’exportation immédiats, cette option est ignorée si elle est spécifiée. Pour ces flux, le processus de resynchronisation ne tronque pas l’index et ne resynchronise que les mises à jour ou les éléments qui avaient précédemment échoué.

### `cleanup`

Cette option nettoie la table de l’indexeur de flux avant une synchronisation. Lorsqu’elle est spécifiée, l’exportation des données SaaS exécute une resynchronisation complète pour le flux spécifié et nettoie toutes les données existantes dans le tableau du flux.

Adobe recommande de n&#39;utiliser cette commande qu&#39;après avoir effectué l&#39;opération [!DNL Data Space ID Cleanup].

>[!WARNING]
>
>**N’utilisez pas cette option régulièrement**. Cela peut entraîner des problèmes de synchronisation des données dans les services Adobe Commerce. Par exemple, le `delete product event` peut ne pas se propager au service Adobe Commerce si l’option `cleanup` est utilisée.

## Dépannage

Si vous ne voyez pas les données attendues dans les services Commerce connectés, résolvez les problèmes en vérifiant les journaux d’erreurs d’exportation des données et en utilisant la commande `saas:resync` avec des variables d’environnement pour examiner les payloads et les données du profileur. Voir [Journaux des révisions et dépannage](troubleshooting-logging.md).
