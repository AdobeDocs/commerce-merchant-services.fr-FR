---
title: Synchronisation du catalogue
description: Découvrez comment exporter des données de produit à partir du [!DNL Commerce] serveur à [!DNL Commerce Services] afin de maintenir les services à jour.
exl-id: 19d29731-097c-4f5f-b8c0-12f9c91848ac
source-git-commit: dd9ba7171cf6a199701b1abb8083a65326e89f5d
workflow-type: tm+mt
source-wordcount: '932'
ht-degree: 0%

---

# Synchronisation du catalogue

Adobe Commerce et Magento Open Source utilisent des indexeurs pour compiler des données de catalogue dans des tables. Le processus est automatiquement déclenché par [events](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html#events-that-trigger-full-reindexing) comme une modification du prix d’un produit ou du niveau de stock.

Le processus de synchronisation du catalogue s’exécute toutes les heures pour permettre [!DNL Commerce] services pour utiliser les données de catalogue. La synchronisation du catalogue exporte les données de produit à partir de [!DNL Commerce] serveur à [!DNL Commerce] services de façon continue afin de maintenir les services à jour. Par exemple : [[!DNL Product Recommendations]](/help/product-recommendations/overview.md) nécessite des informations de catalogue actuelles pour renvoyer avec précision des recommandations avec les noms, les tarifs et la disponibilité corrects. Vous pouvez utiliser la variable _Synchronisation du catalogue_ tableau de bord pour observer et gérer le processus de synchronisation ou l’ [interface de ligne de commande](#resynccmdline) pour déclencher la synchronisation du catalogue et réindexer les données de produit pour les utiliser par [!DNL Commerce] services.

>[!NOTE]
>
> Pour utiliser la variable _Synchronisation du catalogue_ d’un tableau de bord ou d’une interface de ligne de commande, vous devez disposer d’un [Clé API et espace de données SaaS configuré](saas.md).

## Accès au tableau de bord de synchronisation du catalogue

>[!NOTE]
>
> Le _Synchronisation du catalogue_ Le tableau de bord n’est disponible que lorsque la variable _Recommendations de produit_ Les modules sont installés et reflètent les projections de données liées à cette fonctionnalité uniquement. Prise en charge d’autres services Commerce, tels que _Recherche en direct_ et _Service de catalogue_ sont planifiées pour le futur.

Pour accéder au tableau de bord de synchronisation du catalogue, sélectionnez **Système** > _Transfert de données_ > **Synchronisation du catalogue**.

Avec le **Synchronisation du catalogue** Vous pouvez réaliser les opérations suivantes dans le tableau de bord :

- Afficher l’état de synchronisation (**En cours**, **Succès**, **En échec**)
- Afficher le nombre total de produits synchronisés, en cas de réussite
- Rechercher des produits synchronisés pour afficher leur état actuel
- Rechercher dans le catalogue du magasin par nom, SKU, etc.
- Affichage des détails du produit synchronisé dans JSON pour aider à diagnostiquer une incohérence de synchronisation
- Réinitialiser le processus de synchronisation

### Dernière synchronisation

Signale un état de synchronisation de :

- **Succès** - Affiche la date et l’heure de réussite de la synchronisation et le nombre de produits mis à jour.
- **En échec** : affiche la date et l’heure de tentative de synchronisation.
- **En cours** : affiche la date et l’heure de la dernière synchronisation réussie.

>[!NOTE]
>
> Le processus de synchronisation de catalogue s’exécute automatiquement toutes les heures. Cependant, si vous ne voyez pas de produits sur votre storefront ou si les produits ne reflètent pas les modifications récentes que vous avez apportées, vous pouvez résoudre [problèmes de synchronisation du catalogue](#resolvesync).

### Produits synchronisés

Affiche le nombre total de produits synchronisés à partir de votre [!DNL Commerce] catalogue. Après la synchronisation initiale, vous devez vous attendre à ce que seuls les produits modifiés soient synchronisés.

## Resync {#resync}

Si vous devez initier une nouvelle synchronisation de votre catalogue avant que la synchronisation planifiée horaire ne se produise, vous pouvez forcer une nouvelle synchronisation.

>[!NOTE]
>
> L’obligation d’une resynchronisation déclenche une nouvelle synchronisation de l’ensemble de votre catalogue de produits, ce qui peut augmenter la charge sur les ressources matérielles.

1. Dans la _Synchronisation du catalogue_ tableau de bord, sélectionnez **Paramètres**.

   Le _Paramètres de synchronisation du catalogue_ s’affiche.

1. Dans le _Resynchronisation des données_ , cliquez sur [!UICONTROL Resync].

   [!DNL Commerce] synchronise votre catalogue lors de la prochaine fenêtre de synchronisation planifiée. Selon la taille de votre catalogue, cette opération peut prendre un certain temps.

## Produits de catalogue synchronisés

Le **Produits de catalogue synchronisés** le tableau affiche les informations suivantes.

| Champ | Description |
|---|---|
| ID | Identifiant unique du produit |
| Nom | Nom de la vitrine du produit |
| Type | Identifie le type de produit, par exemple simple, configurable, téléchargeable, etc. |
| Dernière exportation | Date à laquelle le produit a été exporté pour la dernière fois à partir de votre catalogue |
| Dernière modification | Date de la dernière modification du produit dans votre catalogue |
| SKU | Affiche l’unité de gestion des stocks du produit. |
| Prix | Prix du produit |
| Visibilité | Paramètre de visibilité d’un produit tel que défini dans la variable [!DNL Commerce] catalogue |

## Résolution des problèmes de synchronisation de catalogue {#resolvesync}

Lorsque vous déclenchez une nouvelle synchronisation des données, la mise à jour des données peut prendre jusqu’à une heure pour être répercutée dans les composants de l’interface utilisateur, tels que les unités de recommandation. Cependant, si, après une heure d’attente, vous constatez toujours des incohérences entre votre catalogue et ce qui apparaît sur votre storefront, ou si la synchronisation du catalogue a échoué, reportez-vous à ce qui suit :

### Incohérence des données

1. Affichez la vue détaillée du produit en question dans les résultats de la recherche.
1. Copiez la sortie JSON et vérifiez que le contenu correspond à ce que vous avez dans la variable [!DNL Commerce] catalogue.
1. Si le contenu ne correspond pas, apportez une modification mineure au produit de votre catalogue, par exemple en ajoutant un espace ou un point.
1. Attendez une nouvelle synchronisation ou [déclencher une resynchronisation manuelle](#resync).

### Synchronisation non en cours

Si la synchronisation n’est pas en cours d’exécution ou que rien n’est synchronisé, reportez-vous à la section [KnowledgeBase](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/troubleshoot-product-recommendations-module-in-magento-commerce.html).

### Échec de la synchronisation

Si l’état de la synchronisation du catalogue est **En échec**, soumettez une [ticket de support](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket).

## Interface de ligne de commande {#resynccmdline}

Le `saas:resync` fait partie de la commande `magento/saas-export` module. Vous pouvez installer ce module à l’aide de l’une des [!DNL Commerce Services] les produits, tels que [[!DNL Product Recommendations]](/help/product-recommendations/install-configure.md) ou [[!DNL Live Search]](/help/live-search/install.md).

>[!NOTE]
>
> Lors de la première exécution d’une synchronisation des données, il est important d’exécuter la variable `productattributes` flux en premier, suivi de `productoverrides`, avant d’exécuter la fonction `products` flux.

Options de commande :

```bash
bin/magento saas:resync --feed <feed name> [no-reindex]
```

Le tableau suivant décrit la variable `saas:resync` paramètres et descriptions.

| Paramètre | Description | Obligatoire ? |
|---| ---| ---|
| `feed` | Indique l’entité à resynchroniser, telle que `products` | Oui |
| `no-reindex` | Envoie les données de catalogue existantes à [!DNL Commerce Services] sans réindexation. Lorsque ce paramètre n’est pas spécifié, la commande exécute une réindexation complète avant de synchroniser les données. | Non |

Le nom du flux peut être l’un des suivants :

- `products`— Produits dans votre catalogue
- `categories`— Catégories dans votre catalogue
- `variants`— Variations de produit d’un produit configurable, telles que la couleur et la taille
- `productattributes`— Attributs de produit tels que `activity`, `gender`, `tops`, `bottoms`, etc.
- `productoverrides`: règles de tarification et de visibilité du catalogue spécifiques au client, telles que celles basées sur les autorisations de catégorie

Lorsque vous déclenchez une nouvelle synchronisation des données à partir de la ligne de commande, la mise à jour des données peut prendre jusqu’à une heure.

### Exemples

L’exemple suivant réindexe les données de produit de la variable [!DNL Commerce] catalogue et resynchronisation sur les services Commerce :

```bash
bin/magento saas:resync --feed products
```

Si vous ne souhaitez pas exécuter une réindexation complète des produits, vous pouvez plutôt synchroniser les données de produit qui ont déjà été générées :

```bash
bin/magento saas:resync --feed products --no-reindex
```
