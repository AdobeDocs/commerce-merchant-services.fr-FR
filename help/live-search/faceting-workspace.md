---
title: Facturation de Workspace
description: Découvrez comment contourner l’espace de travail  [!DNL Live Search] faceting.
exl-id: b47b5c19-59bb-41e4-9599-3b90cbc44b70
source-git-commit: 4978bdb5549f5df911863a23fdfbfc9ab9ad05df
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%

---

# Facturation de Workspace

L’espace de travail *Faceting* répertorie toutes les facettes actuellement disponibles et permet d’accéder aux outils dont vous avez besoin pour configurer et gérer les facettes. Les facettes épinglées apparaissent en premier dans la liste des facettes existantes, suivies de facettes dynamiques. La liste peut être filtrée pour afficher toutes les facettes ou uniquement celles qui sont épinglées ou dynamiques.

![Espace de travail de faceting](assets/faceting-workspace.png)

## Définition de la portée

Si votre installation Adobe Commerce comprend plusieurs vues de magasin, définissez **Scope** sur la [vue de magasin](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) où s’appliquent vos paramètres de facette.

## Filtrer la liste

1. Cliquez sur la commande **Filtrer par** .
1. Choisissez l’une des options suivantes :

   * Tous les filtres
   * Pindu
   * Dynamique

## Ajout d’une facette

1. Cliquez sur **Ajouter des facettes**.
1. Voir [Ajout de facettes](facets-add.md) pour obtenir des instructions détaillées.

## Descriptions des colonnes

| Colonne | Description |
|--- |--- |
| (première colonne) | Répertorie les facettes épinglées et dynamiques par le [label](facets-type.md) visible par l’acheteur. |
| Type de tri | L’ [ ordre de tri](facets-type.md) des valeurs de facette. Les facettes sont triées par ordre alphabétique pour toutes les [!DNL Commerce] vitrines. Pour les implémentations [headless], les facettes peuvent être triées soit par ordre alphabétique, soit par nombre. Options : Alphabétique, Comptage (headless uniquement) |
| Valeur maximale | Nombre de valeurs de facette disponibles dans le storefront sous forme de filtres, avec un maximum de 10. |

## Contrôles

| Contrôle | Description |
|--- |--- |
| Ajout de facettes | Ouvre l’ [éditeur de facettes](facets-add.md). |
| Filtrer par | Détermine le [type de facettes](facets-type.md) qui apparaît dans la liste. Options : Tous, Épinglé, Dynamique |
