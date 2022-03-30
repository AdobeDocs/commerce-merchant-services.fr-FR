---
title: Workspace
description: Découvrez comment configurer, gérer et surveiller les performances des recommandations de produits.
source-git-commit: 4ad607c8595b25d01b5f5020b787fc1d35d4df25
workflow-type: tm+mt
source-wordcount: '637'
ht-degree: 0%

---

# Workspace

Le [!DNL Product Recommendations] workspace affiche une liste de recommandations configurées précédemment avec des mesures qui vous aident à suivre le succès de chaque recommandation. La liste peut être configurée pour calculer les mesures du dernier jour, semaine ou mois. Vous pouvez utiliser les mesures pour créer des informations exploitables en fonction de la fréquence de consultation ou de clic d’une unité de recommandations, ou pour analyser les performances de vos recommandations.

![Espace de travail Recommendations](assets/workspace.png)
_Espace de travail Recommendations_

## Définir la portée

Initialement, la variable [scope](https://docs.magento.com/user-guide/stores/websites-stores-views.html) de tous les paramètres de recommandation définis sur `Default Store View`. Si votre installation Commerce comprend plusieurs vues de magasin, définissez **Portée** au [vue de magasin](https://docs.magento.com/user-guide/configuration/scope.html) où s’appliquent vos recommandations.

## Définition de la période des mesures

1. Cliquez sur le bouton **Calendrier** ![Sélecteur de calendrier](assets/icon-calendar.png) contrôle.

1. Sélectionnez l’une des options suivantes :

   - 24 dernières heures
   - 7 derniers jours
   - 30 derniers jours

   Les valeurs calculées des colonnes de mesures changent pour refléter la période actuelle.

## Afficher/masquer les colonnes

1. Dans le coin supérieur gauche, cliquez sur **Afficher/masquer** ![Sélecteur de colonnes](assets/icon-show-hide-columns.png) colonnes.

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

1. Pour modifier le statut de la recommandation, cliquez sur **Activer** ou **Désactiver**.

## Modifier la recommandation

Sur la page des détails de la recommandation, cliquez sur **Modifier**. Pour en savoir plus, accédez à [Modifier Recommendations](edit.md).

## Créer une recommandation

Sur la page des détails de la recommandation, cliquez sur **Créer**. Pour en savoir plus, accédez à [Créer Recommendations](create.md).

## Contrôles Workspace

| Contrôle | Description |
|---|---|
| ![Sélecteur de calendrier](assets/icon-calendar.png) | Détermine la période utilisée pour les calculs de mesures. Options : 24 heures / 7 jours / 30 jours |
| ![Sélecteur de colonnes](assets/icon-show-hide-columns.png) | Détermine les colonnes qui apparaissent dans le [!DNL Product Recommendations] table. |
| Paramètres | Détermine l’espace de données SaaS dans lequel les données de comportement de recommandation sont récupérées et active également le type de recommandation de similarité visuelle. |
| Créer une recommandation | Ouvre la [Créer une recommandation](create.md) page. |

## Descriptions des colonnes

| Colonne | Description |
|---|---|
| Nom | Nom de la recommandation. |
| Page | Page dans laquelle la recommandation s’affiche. |
| Type | Type de recommandation. |
| État | État de la recommandation. Options : Inactif/Principal/Brouillon |
| Créé | Date de création de la recommandation. |
| Dernière modification | Date de dernière modification de la recommandation. |
| Impressions | Nombre de chargements et de rendus d’une unité de recommandation sur une page. Une unité de recommandation située sous le pli de la fenêtre d’affichage du navigateur s’affiche sur la page, mais n’est pas affichée par l’acheteur. Dans ce cas, l’unité rendue est comptée comme une impression, mais une vue n’est comptée que si l’utilisateur fait défiler l’unité dans la vue. |
| vImpressions | (Impressions affichables) Nombre d’unités de recommandations qui enregistrent au moins une vue. |
| Vues | Nombre d’unités de recommandations qui apparaissent dans la fenêtre d’affichage du navigateur de l’acheteur. Cet événement peut se déclencher plusieurs fois sur une page. |
| Clics | Somme du nombre de clics d’un acheteur sur un élément de l’unité de recommandation et du nombre de clics de l’acheteur sur l’événement **Ajouter au panier** dans l’unité de recommandation |
| Recettes | Les recettes générées par la recommandation pour la période en cours. |
| Recettes Lt | (Recettes sur la durée de vie) Les recettes sur la durée de vie générées par une recommandation. |
| Visibilité | Pourcentage d’unités de recommandations qui s’inscrivent pour la vue. |
| Ctr | (Pourcentage de clics enregistrés) Pourcentage du pourcentage d’impressions unitaires pour la recommandation qui enregistre un clic. |
| vCtr | (Pourcentage de clics enregistrés consultables) Pourcentage des impressions affichables pour l’unité de recommandations qui enregistre un clic. |
