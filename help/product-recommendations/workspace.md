---
title: '[!DNL Product Recommendations] Workspace'
description: Découvrez comment configurer, gérer et surveiller les performances des recommandations de produits.
exl-id: 85a06cc3-91b9-484a-96a9-fc85718e6d70
source-git-commit: 91e19e30d55259d3287404895d1d893c480743b6
workflow-type: tm+mt
source-wordcount: '781'
ht-degree: 0%

---

# [!DNL Product Recommendations] Workspace

L’espace de travail [!DNL Product Recommendations] affiche une liste des recommandations configurées précédemment avec des mesures qui vous aident à suivre le succès de chaque recommandation. La liste peut être configurée pour calculer des mesures pour le dernier jour, la dernière semaine ou le dernier mois. Vous pouvez utiliser les mesures pour créer des informations exploitables en fonction de la fréquence de consultation ou de clic d’une unité de recommandations, ou pour analyser les performances de vos recommandations.

>[!INFO]
>
>Une unité de recommandation est un widget qui contient le produit recommandé _items_.

![Espace de travail Recommendations](assets/workspace.png)
_Recommendations Workspace_

## Définition de la portée

Au départ, la [portée](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html) de tous les paramètres de recommandation est définie sur `Default Store View`. Si votre installation Commerce comprend plusieurs vues de magasin, définissez **Scope** sur la [vue de magasin](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) où vos recommandations s’appliquent.

## Définition de la période des mesures

1. Cliquez sur la commande **Calendar** ![Calendar selector](assets/icon-calendar.png) .

1. Sélectionnez l’une des options suivantes :

   - 24 dernières heures
   - 7 derniers jours
   - 30 derniers jours

   Les valeurs calculées des colonnes de mesures changent pour refléter la période actuelle.

   >[!NOTE]
   >
   >Les mesures de recommandation de produit sont optimisées pour les vitrines Luma. Si votre vitrine n’est pas basée sur Luma, la façon dont les mesures effectuent le suivi des données dépend de la manière dont vous [ implémentez la collection d’événements](events.md).

## Afficher/masquer les colonnes

1. Dans le coin supérieur gauche, cliquez sur les colonnes **Afficher/masquer** ![Sélecteur de colonnes](assets/icon-show-hide-columns.png) .

   Les colonnes visibles sont cochées en bleu.

1. Dans le menu, effectuez l’une des opérations suivantes :

   - Pour afficher une colonne masquée, cliquez sur le nom d’une colonne sans coche.
   - Pour masquer une colonne visible, cliquez sur le nom d’une colonne avec une coche.

   Le tableau est actualisé afin de n’inclure que les colonnes sélectionnées.

   ![Espace de travail Recommendations](assets/workspace-select-columns.png)
   _Afficher/masquer les colonnes_

## Paramètres

Les paramètres déterminent l’espace de données SaaS qui fournit les données comportementales des recommandations.

- Pour modifier l’origine des données comportementales de recommandation, choisissez un autre espace de données SaaS.

- Pour configurer un nouvel espace de données SaaS, cliquez sur **Modifier la configuration**. Pour en savoir plus, voir [Paramètres](settings.md).

![Paramètres Recommendations](assets/settings.png)
_Paramètres Recommendations_

## Afficher les détails

1. Dans le tableau, cliquez sur la recommandation à examiner.

   ![Espace de travail Recommendations](assets/recommendation-detail.png)
   _Détails sur le taux de conversion de la page d’accueil_

1. Pour modifier l’état de la recommandation, cliquez sur **Activer** ou **Désactiver**.

## Modifier la recommandation

Sur la page des détails de la recommandation, cliquez sur **Modifier**. Pour en savoir plus, accédez à [Modifier Recommendations](edit.md).

## Créer une recommandation

Sur la page des détails de la recommandation, cliquez sur **Créer**. Pour en savoir plus, accédez à [Créer Recommendations](create.md).

## Contrôles Workspace

| Contrôle | Description |
|---|---|
| ![Sélecteur de calendrier](assets/icon-calendar.png) | Détermine la période utilisée pour les calculs de mesures. Options : 24 heures / 7 jours / 30 jours |
| ![Sélecteur de colonnes](assets/icon-show-hide-columns.png) | Détermine les colonnes qui apparaissent dans la table [!DNL Product Recommendations]. |
| Paramètres | Détermine l’espace de données SaaS dans lequel les données de comportement de recommandation sont récupérées et active également le type de recommandation de similarité visuelle. |
| Créer une recommandation | Ouvre la page [Créer une recommandation](create.md). |

## Descriptions des colonnes

| Colonne | Description |
|---|---|
| Nom | Nom de la recommandation. |
| Page | Page dans laquelle la recommandation s’affiche. |
| Type | Type de recommandation. |
| État | État de la recommandation. Options : inactif/actif/brouillon |
| Créé | Date de création de la recommandation. |
| Dernière modification | Date de dernière modification de la recommandation. |
| Impressions | Nombre de chargements et de rendus d’une unité de recommandation sur une page. Une unité de recommandation située sous le pli de la fenêtre d’affichage du navigateur s’affiche sur la page, même si elle n’est pas affichée par l’acheteur. Dans ce cas, l’unité rendue est comptabilisée comme une impression, mais une vue n’est comptabilisée que si l’acheteur fait défiler l’unité dans la vue. |
| vImpressions | (Impressions affichables) Nombre d’unités de recommandations qui enregistrent au moins une vue. Par exemple, si l’unité de recommandation comporte deux lignes, chacune comportant deux produits, et que les deux derniers produits ne sont pas vus par l’acheteur, mais que les deux premiers le sont, l’activité est toujours considérée comme une impression. |
| Vues | Nombre d’unités de recommandations qui apparaissent dans la fenêtre d’affichage du navigateur de l’acheteur. Si l’acheteur fait défiler la page plusieurs fois vers le haut ou vers le bas, l’événement se déclenche plusieurs fois, chaque fois que l’unité est visible. |
| Clics | Somme du nombre de fois où un acheteur clique sur un article dans l’unité de recommandation et du nombre de fois où il clique sur le bouton **Ajouter au panier** dans l’unité de recommandation |
| Recettes | Les recettes générées par la recommandation pour la période en cours. |
| Recettes Lt | (Recettes sur la durée de vie) Les recettes sur la durée de vie générées par une recommandation. |
| Visibilité | Pourcentage d’unités de recommandations qui s’inscrivent pour la vue. |
| CTR | (Taux de clics) Pourcentage d’impressions unitaires pour la recommandation qui enregistre un clic. Le CTR comptabilise toutes les impressions même si l’unité n’entre pas dans la vue de l’acheteur. Si l’entité de recommandation n’est pas visualisée, il est peu probable qu’un utilisateur clique dessus. Toutefois, ces impressions invisibles sont prises en compte dans le score du CTR et réduisent le pourcentage total de CTR. |
| vCTR | (Taux de clics affichables) mesure les clics uniquement en fonction des impressions affichables (recommandations qui s’affichent réellement dans la partie visible de l’écran du nouvel acheteur), ce qui fournit une évaluation plus précise de l’engagement du nouvel acheteur. |
