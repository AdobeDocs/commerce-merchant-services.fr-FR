---
title: Synchronisation du catalogue
description: Découvrez comment exporter des données de produit à partir du [!DNL Commerce] serveur à [!DNL Commerce Services].
exl-id: 19d29731-097c-4f5f-b8c0-12f9c91848ac
feature: Catalog Management, Data Import/Export, Catalog Service
source-git-commit: 151b57d7b31637178c645149d78c0d3670ee1c3e
workflow-type: tm+mt
source-wordcount: '1166'
ht-degree: 0%

---


# Synchronisation du catalogue

Adobe Commerce utilise des indexeurs pour compiler des données de catalogue dans des tables. Le processus est automatiquement déclenché par [events](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html#events-that-trigger-full-reindexing) comme une modification du prix d’un produit ou du niveau de stock.

Le service de synchronisation de catalogue déplace les données de produit d’une [!DNL Adobe Commerce] à l’instance [!DNL Commerce Services] plateforme de manière continue afin de maintenir les données à jour. Par exemple : [[!DNL Product Recommendations]](/help/product-recommendations/overview.md) nécessite des informations de catalogue actuelles pour renvoyer avec précision des recommandations dont les noms, les tarifs et la disponibilité sont corrects. Utilisez la variable _Synchronisation du catalogue_ tableau de bord pour observer et gérer le processus de synchronisation ou l’ [interface de ligne de commande](#resynccmdline) pour déclencher une synchronisation de catalogue et réindexer les données de produit pour les utiliser par [!DNL Commerce Services].

>[!NOTE]
>
> Pour utiliser la variable _Synchronisation du catalogue_ d’un tableau de bord ou d’une interface de ligne de commande, vous devez disposer d’un [Clé API et espace de données SaaS configuré](saas.md).

## Accès au tableau de bord de synchronisation du catalogue

>[!NOTE]
>
> La variable _Synchronisation du catalogue_ Le tableau de bord n’est disponible que lorsque la variable _Recommendations de produit_ Les modules sont installés et reflètent les projections de données liées à cette fonctionnalité uniquement. Prise en charge d’autres services Commerce, tels que _Recherche en direct_ et _Service de catalogue_ sont planifiées pour le futur.

Pour accéder au tableau de bord de synchronisation du catalogue, sélectionnez **Système** > _Transfert de données_ > **Synchronisation du catalogue**.

Avec la variable **Synchronisation du catalogue** Vous pouvez réaliser les opérations suivantes dans le tableau de bord :

- Afficher l’état de synchronisation (**En cours**, **Succès**, **En échec**)
- Afficher le nombre total de produits synchronisés
- Rechercher des produits synchronisés pour afficher leur état actuel
- Rechercher dans le catalogue du magasin par nom, SKU, etc.
- Affichage des détails du produit synchronisé dans JSON pour aider à diagnostiquer une incohérence de synchronisation
- Réinitialiser le processus de synchronisation

### Dernière synchronisation

Signale un état de synchronisation de :

- **Succès** - Affiche la date et l’heure de réussite de la synchronisation et le nombre de produits mis à jour.
- **En échec** : affiche la date et l’heure de tentative de synchronisation
- **En cours** : affiche la date et l’heure de la dernière synchronisation réussie.

Le processus de synchronisation de catalogue s’exécute automatiquement toutes les heures. Si vous ne voyez pas les produits attendus sur le storefront ou si les produits ne reflètent pas les modifications récentes que vous avez apportées, vous pouvez résoudre [problèmes de synchronisation du catalogue](#resolvesync).

### Produits synchronisés

Affiche le nombre total de produits synchronisés à partir de votre [!DNL Commerce] catalogue. Après la synchronisation initiale, seuls les produits modifiés doivent être synchronisés.

## Resync {#resync}

Si vous devez lancer une nouvelle synchronisation de votre catalogue avant que la synchronisation horaire ne se produise, vous pouvez forcer une nouvelle synchronisation.

>[!NOTE]
>
> L’obligation d’une resynchronisation déclenche une nouvelle synchronisation de l’ensemble de votre catalogue de produits, ce qui peut augmenter la charge sur les ressources matérielles.

1. Dans la _Synchronisation du catalogue_ tableau de bord, sélectionnez **Paramètres**.

   La variable _Paramètres de synchronisation du catalogue_ s’affiche.

1. Dans le _Resynchronisation des données_ , cliquez sur [!UICONTROL Resync].

   [!DNL Commerce] synchronise votre catalogue lors de la prochaine fenêtre de synchronisation planifiée. Selon la taille de votre catalogue, cette opération peut prendre un certain temps.


## Produits de catalogue synchronisés

La variable **Produits de catalogue synchronisés** le tableau affiche les informations suivantes.

| Champ | Description |
|---|---|
| ID | Identifiant unique du produit |
| Nom | Nom de la vitrine du produit |
| Type | Identifie le type de produit, par exemple simple, configurable ou téléchargeable. |
| Dernière exportation | Date à laquelle le produit a été exporté pour la dernière fois depuis votre catalogue |
| Dernière modification | Date de la dernière modification du produit dans votre catalogue |
| SKU | Affiche l’unité de gestion des stocks du produit. |
| Prix | Prix du produit |
| Visibilité | Paramètre de visibilité d’un produit tel que défini dans la variable [!DNL Commerce] catalogue |

## Résolution des problèmes de synchronisation de catalogue {#resolvesync}

Lorsque vous déclenchez une nouvelle synchronisation des données, la mise à jour des données peut prendre jusqu’à une heure pour être répercutée dans les composants de l’interface utilisateur, tels que les unités de recommandation. Si vous constatez toujours des incohérences entre votre catalogue et les données sur le storefront, ou si la synchronisation du catalogue a échoué, reportez-vous à ce qui suit :

### Incohérence des données

1. Affichez la vue détaillée du produit en question dans les résultats de la recherche.
1. Copiez la sortie JSON et vérifiez que le contenu correspond à ce que vous avez dans la variable [!DNL Commerce] catalogue.
1. Si le contenu ne correspond pas, apportez une modification mineure au produit de votre catalogue, comme l’ajout d’un espace ou d’un point.
1. Attendez une nouvelle synchronisation ou [déclencher une resynchronisation manuelle](#resync).

### Synchronisation non en cours

Si la synchronisation n’est pas en cours d’exécution ou si rien n’est synchronisé, reportez-vous à cette section [KnowledgeBase](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/troubleshoot-product-recommendations-module-in-magento-commerce.html) article.

### Échec de la synchronisation

Si l’état de la synchronisation du catalogue est **En échec**, soumettez une [ticket de support](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket).

## Interface de ligne de commande {#resynccmdline}

La variable `saas:resync` fait partie de la `magento/saas-export` et est disponible prêt à l’emploi avec l’un des [!DNL Commerce Services] les produits, tels que [[!DNL Product Recommendations]](/help/product-recommendations/install-configure.md) ou [[!DNL Live Search]](/help/live-search/install.md).

>[!NOTE]
>
> Lors de la première exécution d’une synchronisation des données, exécutez la variable `productattributes` flux en premier, suivi de `productoverrides`, avant d’exécuter la fonction `products` flux.

Options de commande :

```bash
bin/magento saas:resync --feed <feed name> [no-reindex|cleanup-feed]
```

Le tableau suivant décrit la variable `saas:resync` paramètres et descriptions.

| Paramètre | Description | Obligatoire ? |
|---| ---| ---|
| `feed` | Indique l’entité à resynchroniser, telle que `products` | Oui |
| `no-reindex` | Envoie les données de catalogue existantes à [!DNL Commerce Services] sans réindexation. Lorsque ce paramètre n’est pas spécifié, la commande exécute une réindexation complète avant de synchroniser les données. | Non |
| `cleanup-feed` | Nettoyez la table des indexeurs de flux avant une synchronisation. | Non |

Le nom du flux peut être l’un des suivants :

- `products`— Produits dans votre catalogue
- `productattributes`— Attributs de produit tels que `activity`, `gender`, `tops`, `bottoms`, etc.
- `variants`— Variations de produit d’un produit configurable, telles que la couleur et la taille
- `prices` — Prix des produits
- `scopesCustomerGroup` — Groupes clients
- `scopesWebsite` — Sites web avec vues de magasin
- `categories`— Catégories dans votre catalogue
- `categoryPermissions` - Autorisations pour chacune des catégories
- `productoverrides`: règles de tarification et de visibilité du catalogue spécifiques au client, telles que celles basées sur les autorisations de catégorie

Selon le [Services de commerce](../landing/saas.md) sont installés, vous pouvez avoir différents jeux de flux disponibles pour `saas:resync` .

Il n’est pas recommandé d’exécuter la variable `saas:resync` de façon régulière. Vous devrez peut-être exécuter la commande manuellement dans deux scénarios :

- Synchronisation initiale
- La variable [ID d’espace de données SaaS](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html) a été modifié

### Synchronisation initiale

Lorsque vous déclenchez une `saas:resync` de la ligne de commande, selon la taille de votre catalogue, la mise à jour des données peut prendre de quelques minutes à quelques heures.

Pour la synchronisation initiale, il est recommandé d’exécuter les commandes dans l’ordre suivant :

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

### Dépannage

Si vous ne voyez pas les données attendues dans [!DNL Commerce Service], vérifiez si un problème s’est produit au cours de la synchronisation avec l’événement [!DNL Adobe Commerce] à l’instance [!DNL Commerce Service] plateforme.

Il existe 2 fichiers journaux dans la variable `var/log/` directory:

- `commerce-data-export-errors.log` - si une erreur s’est produite au cours de _collecte_ phase
- `saas-export-errors.log` - si une erreur s’est produite au cours de _transmission_ phase

#### Vérification de la payload du flux

Il peut s’avérer utile d’afficher la charge utile du flux qui a été envoyée à la variable [!DNL Commerce Service]. Pour ce faire, vous pouvez transmettre la variable d’environnement. `EXPORTER_EXTENDED_LOG=1`. La variable `no-reindex` L’indicateur signifie que seules les données actuellement collectées sont envoyées.

```bash
EXPORTER_EXTENDED_LOG=1 bin/magento saas:resync --feed=products --no-reindex
```

La payload est disponible dans `var/log/saas-export.log`.

#### Préserver la charge utile dans la table d’index du flux

Commencer à partir de `magento/module-data-exporter:103.0.0` certains flux : flux de produit, flux de prix, conserver uniquement les données minimales requises dans la table d’index.

La conservation des données de payload dans la table d’index n’est pas recommandée en production, mais elle peut s’avérer utile sur une instance de développeur. Pour ce faire, transmettez la variable `PERSIST_EXPORTED_FEED=1` Variable d’environnement :

```bash
PERSIST_EXPORTED_FEED=1 bin/magento saas:resync --feed=products
```

#### Profilage

Si le processus de réindexation d’un flux spécifique prend un temps déraisonnable, exécutez le profileur pour collecter des données supplémentaires qui pourraient s’avérer utiles à l’équipe d’assistance. Pour ce faire, transmettez la variable `EXPORTER_PROFILER=1`Variable d’environnement :

```bash
EXPORTER_PROFILER=1 bin/magento indexer:reindex catalog_data_exporter_products
```

Les données de profil sont stockées dans `var/log/commerce-data-export.log` au format suivant :

`<Provider class name>, <# of processed entities>, <execution time im ms>, <memory consumption in Mb>`

#### Soumettre une demande d’assistance

Si des erreurs ne sont pas liées à la configuration ou aux extensions tierces, envoyez une [ticket de support](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) avec autant d’informations que possible.
