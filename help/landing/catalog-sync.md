---
title: Synchronisation du catalogue
description: Découvrez comment exporter des données de produit à partir du [!DNL Commerce] serveur à [!DNL Commerce Services].
exl-id: 19d29731-097c-4f5f-b8c0-12f9c91848ac
feature: Catalog Management, Data Import/Export, Catalog Service
source-git-commit: af9de40a717d2cb55a5f42483bd0e4cbcd913f64
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 0%

---


# Synchronisation du catalogue

>[!NOTE]
>
> Le tableau de bord de synchronisation du catalogue est désormais le tableau de bord de la gestion des données. Ce tableau de bord restructuré prend désormais en charge [[!DNL Product Recommendations]](../product-recommendations/guide-overview.md), [[!DNL Live Search]](../live-search/overview.md), et [[!DNL Catalog Service]](../catalog-service/overview.md). Les clients peuvent accéder au tableau de bord de Data Management en mettant à jour la dernière version de l’un de ces services. Pour en savoir plus, voir la section [Tableau de bord de la gestion des données](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-dashboard.html) la documentation. Cette rubrique actuelle reste destinée aux utilisateurs qui n’ont pas encore effectué la mise à niveau et qui disposent toujours du tableau de bord de synchronisation du catalogue.

Adobe Commerce utilise des indexeurs pour compiler des données de catalogue dans des tables. Le processus est automatiquement déclenché par [events](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html#events-that-trigger-full-reindexing) comme une modification du prix d’un produit ou du niveau de stock.

Le service de synchronisation de catalogue déplace les données de produit d’une [!DNL Adobe Commerce] à l’instance [!DNL Commerce Services] plateforme de manière continue afin de maintenir les données à jour. Par exemple : [[!DNL Product Recommendations]](/help/product-recommendations/overview.md) nécessite des informations de catalogue actuelles pour renvoyer avec précision des recommandations dont les noms, les tarifs et la disponibilité sont corrects. Utilisez la variable _Synchronisation du catalogue_ tableau de bord pour observer et gérer le processus de synchronisation ou l’interface de ligne de commande pour déclencher une synchronisation de catalogue et réindexer les données de produit à utiliser par [!DNL Commerce Services]. Voir [Référence de l’interface de ligne de commande](../data-export/data-export-cli-commands.md) dans le _Exportation des données SaaS_ Guide.

## Accès au tableau de bord de synchronisation du catalogue

Pour accéder au tableau de bord de synchronisation du catalogue, sélectionnez **Système** > _Transfert de données_ > **Synchronisation du catalogue**.

Avec la variable **Synchronisation du catalogue** Vous pouvez réaliser les opérations suivantes dans le tableau de bord :

- Afficher l’état de synchronisation (**En cours**, **Succès**, **En échec**)
- Afficher le nombre total de produits synchronisés
- Rechercher des produits synchronisés pour afficher leur état actuel
- Rechercher un catalogue de magasin par nom, SKU, etc.
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

Si vous devez initier une nouvelle synchronisation de votre catalogue avant que la synchronisation planifiée horaire ne se produise, vous pouvez forcer une nouvelle synchronisation.

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

Voir [Journaux et dépannage](../data-export/troubleshooting-logging.md#troubleshooting) dans le _Guide d’exportation des données SaaS_.
