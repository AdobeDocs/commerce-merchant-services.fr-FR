---
title: Interface de ligne de commande de l’exportation des données SaaS
description: Découvrez comment utiliser les commandes de l’interface de ligne de commande pour gérer les flux et les processus pour le [!DNL data export extension] pour les services Adobe Commerce SaaS.
recommendations: noCatalog
exl-id: f360d920-7d02-4317-8c56-c7d4c4ed2ff2
source-git-commit: af9de40a717d2cb55a5f42483bd0e4cbcd913f64
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 0%

---

# Référence de l’interface de ligne de commande de l’exportation de données SaaS

Les développeurs et les administrateurs système peuvent gérer les opérations de synchronisation pour l’exportation des données SaaS à l’aide du [Outil de ligne de commande Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/config-cli) (interface en ligne de commande). La variable `saas:resync` est incluse dans la variable `magento/saas-export` module.

Adobe déconseille d’utiliser la variable `saas:resync` régulièrement. Les scénarios types d’utilisation de la commande sont les suivants :

- Synchronisation initiale
- La variable [ID d’espace de données SaaS](https://experienceleague.adobe.com/en/docs/commerce-admin/config/services/saas) a été modifié et vous devez synchroniser les données dans le nouvel espace de données.
- Dépannage

## Synchronisation initiale

>[!NOTE]
>Si vous utilisez la recherche en direct ou le Recommendations de produit, il n’est pas nécessaire d’exécuter la synchronisation initiale. Le processus est lancé automatiquement une fois que vous avez connecté le service à votre instance Commerce.

Lorsque vous déclenchez une `saas:resync` de la ligne de commande, selon la taille de votre catalogue, la mise à jour des données peut prendre de quelques minutes à quelques heures.

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

Avant d’utiliser `saas:resync` , passez en revue les [description des options](#command-options).

- Effectuez une resynchronisation complète pour un flux d’entité.

  ```
  bin/magento saas:resync --feed='<FEED_NAME>' 1
  ```

  Les flux qui ont déjà été exportés avec succès ne sont pas resynchronisés.

- Resynchronisation complète des données de nettoyage et de flux spécifiées

  ```
  bin/magento saas:resync --feed='FEED_NAME' --cleanup-feed
  ```

  N’utilisez qu’après avoir effectué une [!DNL Data Space ID Cleanup] opération.

- Pour les flux d’exportation immédiats, renvoyez toutes les données aux services Commerce connectés sans tronquer les données d’index dans la table des flux.

  ```
   bin/magento saas:resync --feed='FEED_NAME' --no-reindex
  ```

- Liste des commandes et options disponibles avec des descriptions.

  ```
  bin/magento saas:resync --help
  ```

## Options de commande

Les options suivantes sont disponibles pour la gestion de `saas:resync` opérations.

>[!NOTE]
>
>La variable `saas:resync` prend également en charge les options avancées permettant d’améliorer les commandes d’exportation de données en augmentant la taille du lot et en ajoutant un traitement multithread. Voir [Personnalisation du traitement de l’exportation](customize-export-processing.md).

### `feed`

Cette option obligatoire spécifie l’entité de flux à resynchroniser, telle que `products`.

La variable `feed` La valeur d’option peut inclure n’importe quel flux d’entité disponible :

- `products`: flux de données de produit
- `productAttributes`: flux de données des attributs de produit
- `categories`: flux de données de catégories
- `variants`: flux de données de variations de produits configurables
- `prices`: flux de données sur les prix des produits
- `categoryPermissions`: flux de données des autorisations de catégorie
- `productOverrides`: flux de données des autorisations de produit
- `inventoryStockStatus`: flux de données d’état du stock
- `scopesWebsite`: sites web avec des magasins et des flux de données de vues de magasin
- `scopesCustomerGroup`: flux de données de groupes de clients
- `orders`: flux de données des commandes client

Selon le [Services Commerce](../landing/saas.md) sont installés, il se peut qu’un autre ensemble de flux soit disponible pour la variable `saas:resync` .

### `no-reindex`

Cette option envoie à nouveau les données de catalogue existantes vers [!DNL Commerce Services] sans réindexation. Si cette option n’est pas spécifiée, la commande exécute une réindexation complète avant de synchroniser les données.

Le comportement de cette option dépend de l’exportation ou non du flux dans [mode d’exportation hérité ou immédiat](data-synchronization.md#synchronization-modes)

- Pour les flux d’exportation hérités, le processus de synchronisation ne tronque pas les données indexées dans la table des flux. Au lieu de cela, il envoie toutes les données au service Adobe Commerce.
- Pour les flux d’exportation immédiats, cette option est ignorée si elle est spécifiée. Pour ces flux, le processus de resynchronisation ne tronque pas l’index et ne resynchronise que les mises à jour ou les éléments qui avaient précédemment échoué.

### `cleanup`

Cette option nettoie la table de l’indexeur de flux avant une synchronisation. Lorsqu’elle est spécifiée, l’exportation des données SaaS exécute une resynchronisation complète pour le flux spécifié et nettoie toutes les données existantes dans le tableau du flux.

Adobe recommande de n’utiliser cette commande qu’après avoir exécuté la [!DNL Data Space ID Cleanup] opération.

>[!WARNING]
>
>**N’utilisez pas régulièrement cette option**. Cela peut entraîner des problèmes de synchronisation des données dans les services Adobe Commerce. Par exemple, la variable `delete product event` peut ne pas se propager au service Adobe Commerce si la variable `cleanup` est utilisée.

## Dépannage

Si vous ne voyez pas les données attendues dans les services Commerce connectés, résolvez les problèmes en vérifiant les journaux d’erreurs d’exportation des données et en utilisant la variable `saas:resync` avec des variables d’environnement pour examiner les payloads et les données du profileur. Voir [Consultez les journaux et dépannage](troubleshooting-logging.md).
