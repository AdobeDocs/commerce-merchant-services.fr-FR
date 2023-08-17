---
title: "Facturation Workspace"
description: "Découvrez comment contourner le problème [!DNL Live Search] faceting workspace."
exl-id: b47b5c19-59bb-41e4-9599-3b90cbc44b70
source-git-commit: e166c8cb9d715dce573195a188b5335c02d8fd0c
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---

# Facturation de Workspace

La variable [!DNL Live Search] workspace répertorie toutes les facettes actuellement disponibles et permet d’accéder aux outils dont vous avez besoin pour configurer et gérer les facettes. Les facettes épinglées apparaissent en premier dans la liste des facettes existantes, suivies de facettes dynamiques. La liste peut être filtrée pour afficher toutes les facettes ou uniquement celles qui sont épinglées ou dynamiques.

![Espace de travail de facette](assets/faceting-workspace.png)

## Définition de la portée

Si votre installation Adobe Commerce comprend plusieurs vues de magasin, définissez **Portée** à la fonction [vue de magasin](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) où s’appliquent vos paramètres de facette.

## Filtrer la liste

1. Cliquez sur le bouton **Filtrer par** contrôle.
1. Choisissez l’une des options suivantes :

   * Tous les filtres
   * Pindu
   * Dynamique

## Ajout d’une facette

1. Cliquez sur **Ajout de facettes**.
1. Voir [Ajout de facettes](facets-add.md) pour obtenir des instructions détaillées.

## Descriptions des colonnes

| Colonne | Description |
|--- |--- |
| (première colonne) | Répertorie les facettes codées et dynamiques par le [label](facets-type.md) qui est visible par l’acheteur. |
| Type de tri | La variable [ordre de tri](facets-type.md) de valeurs de facette. Les facettes sont triées par ordre alphabétique pour toutes les [!DNL Commerce] storefronts. Pour [headless] implémentations, les facettes peuvent être triées soit par ordre alphabétique, soit par nombre. Options : Alphabétique, Comptage (headless uniquement) |
| Valeur maximale | Nombre de valeurs de facette disponibles dans le storefront sous forme de filtres, avec un maximum de 10. |

## Contrôles

| Contrôle | Description |
|--- |--- |
| Ajout de facettes | Ouvre la [éditeur de facettes](facets-add.md). |
| Filtrer par | Détermine la variable [type de facettes](facets-type.md) qui apparaissent dans la liste. Options : Tous, Épinglé, Dynamique |
