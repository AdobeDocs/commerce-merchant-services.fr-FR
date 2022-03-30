---
title: Modifier la recommandation
description: Découvrez comment modifier une recommandation de produit.
source-git-commit: 4ad607c8595b25d01b5f5020b787fc1d35d4df25
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# Modifier la recommandation

La page Modifier la recommandation vous permet d’ajuster les paramètres individuels qui constituent la recommandation. Tous les paramètres peuvent être modifiés, à l’exception du type de page et du type de recommandation. Les paramètres suivants peuvent être modifiés :

- [Nom de la recommandation](#name)
- [Libellé du storefront](#label)
- [Nombre de produits](#number)
- [Emplacement et position](#placement)
- [Filtrage des produits](#filters)

L’aperçu sur le côté droit de la page indique comment la recommandation avec les paramètres actuels peut apparaître dans le storefront. Le _Aperçu des produits recommandés_ reste visible à titre de référence lorsque vous faites défiler la page vers le bas. L’aperçu affiche une image miniature du produit, le nom du produit, le SKU, le prix et le type de résultat pour chaque produit renvoyé. Le type de résultat indique s’il existe suffisamment de données comportementales Principales pour générer la recommandation ou s’il utilise des données comportementales de sauvegarde.

![Modifier Recommendations](assets/edit-recommendation.png)

## Modifier une recommandation

1. Sur le _Administration_ barre latérale, accédez à **Marketing** > _Promotions_ > **Recommendations de produit**.

1. Sélectionnez la recommandation à modifier.

1. Cliquez sur **Modifier**. Suivez ensuite les instructions ci-dessous pour apporter les modifications dont vous avez besoin.

1. Une fois l’opération terminée, cliquez sur **Enregistrer les modifications**.

### Nom de la recommandation {#name}

Choisissez un nom explicite indiquant l’objectif de la recommandation. Le nom est à titre de référence interne et n’apparaît pas dans le storefront.

![Modifier le nom](assets/edit-name.png)

### Libellé du storefront {#label}

Saisissez le texte que vous souhaitez utiliser comme libellé pour l’unité de recommandation dans le storefront.

![Modifier le libellé](assets/edit-storefront-label.png)

### Nombre de produits {#number}

Réglez le curseur pour afficher jusqu’à 20 produits dans l’unité de recommandation.

![Modifier le nombre de produits](assets/edit-number-of-products.png)

### Emplacement et position {#placement}

1. Sélectionnez l’emplacement de la page où l’unité de recommandation doit apparaître dans le storefront.

   - Au bas du contenu principal
   - En haut du contenu principal

   ![Modifier l’emplacement](assets/edit-placement.png)

1. Pour modifier l’ordre des recommandations incluses dans l’unité, utilisez la variable **Déplacer** ![Sélecteur de déplacement](assets/icon-move.png) pour faire glisser les recommandations.

   ![Modifier la position](assets/edit-position.png)

### Filtrage des produits {#filters}

Toute modification apportée au produit [filtres](filters.md) sont reflétés dans la variable _Aperçu des produits recommandés_. Seuls les produits qui correspondent aux filtres d’inclusion peuvent être recommandés. Les produits qui correspondent à des filtres d’exclusion ne sont pas recommandés.

Le _Inclusions_ et _Exclusions_ les onglets répertorient les filtres disponibles de chaque type. Dans la liste, chaque principal filtre est identifié par un point bleu.

- Pour afficher les détails de chaque filtre, cliquez sur le nom du filtre.
- Pour modifier l’état du filtre, définissez la variable **Activer le filtre** basculer vers le `on` ou `off` position.

![Modifier les filtres](assets/edit-filters.png)

Les paramètres de filtre décrivent les produits à inclure ou à exclure dans l’unité de recommandation. Par exemple, la variable _Catégorie_ les paramètres d’inclusion de filtre indiquent au système d’inclure uniquement les produits des catégories sélectionnées.

![Modifier le filtre de catégorie](assets/edit-filter-category.png)
