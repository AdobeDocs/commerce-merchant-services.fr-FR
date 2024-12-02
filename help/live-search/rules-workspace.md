---
title: Recherche dans Workspace de marchandisage
description: Découvrez comment contourner l’espace de travail Rechercher le marchandisage .
exl-id: a52839fb-2264-4443-83c3-9eaa2ccb6996
source-git-commit: 52be82fa080474d6df81fd16d1655a421771e5e2
workflow-type: tm+mt
source-wordcount: '573'
ht-degree: 1%

---

# Recherche dans Workspace de marchandisage

L’espace de travail *Rechercher le marchandisage* répertorie la sélection actuelle des règles et leur état, et permet d’accéder aux outils dont vous avez besoin pour créer et gérer des règles. Dans l’espace de travail, vous pouvez :

* Recherche de règles
* Afficher les détails des règles
* Activer/désactiver des règles
* Supprimer des règles
* Accès à l’éditeur de règles

![Rechercher dans le Workspace de marchandisage](assets/rules-workspace.png)

## Définition de la portée

Si votre installation Adobe Commerce comprend plusieurs vues de magasin, définissez **Scope** sur la [vue de magasin](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) où vos règles s’appliquent.

## Afficher/masquer les colonnes

1. Dans le coin supérieur droit, cliquez sur les colonnes **Afficher/masquer** ![Sélecteur de colonnes](assets/btn-show-hide-columns.png) .
Les colonnes visibles sont cochées en bleu dans le menu d’options. Le nom de la règle est la seule colonne qui ne peut pas être masquée.

1. Dans le menu, effectuez l’une des opérations suivantes :

   * Pour afficher une colonne masquée, cliquez sur le nom d’une colonne sans coche.
   * Pour masquer une colonne visible, cliquez sur le nom d’une colonne avec une coche.

## Filtrage des règles par statut

1. Si votre boutique comporte de nombreuses règles, vous pouvez les filtrer par statut afin de les raccourcir. Par défaut, la liste Règles affiche toutes les règles.

1. Pour répertorier uniquement les règles avec un paramètre d’état spécifique, définissez **Status** sur l’un des paramètres suivants :

   * Tous
   * Actif
   * Inactif
   * Planifié

## Rechercher des règles de recherche par nom

Commencez à saisir le nom de la règle ou tout mot du nom de la règle.
La recherche trouve la ou les règles correspondantes lorsque vous tapez. La chaîne des caractères correspondants est mise en surbrillance dans le nom de chaque règle trouvée.

![Règles - rechercher par nom](assets/rules-workspace-search-name.png)

## Afficher les détails

Le panneau Détails affiche le nom, l’état, les conditions et événements de la règle, la date de début et de fin, la description et la date de dernière modification de la règle. Les règles peuvent être activées, modifiées et supprimées du panneau Détails.

1. Dans l’espace de travail *Rechercher le marchandisage*, recherchez la règle dans la grille à afficher, puis cliquez sur **Plus** (...).
1. Cliquez sur **Afficher les détails**.
Vous pouvez effectuer l’une des opérations suivantes à partir du panneau Afficher les détails :

   * Modifier la règle
   * Supprimer la règle
   * Activer/Désactiver la règle

1. Pour fermer le panneau *Afficher les détails*, cliquez sur **Fermer** (X) dans le coin supérieur droit.

   ![Règle - détails](assets/rules-workspace-details.png)

## Descriptions des colonnes

| Colonne | Description |
|--- |--- |
| Nom | Nom de la règle. |
| Dernière mise à jour | Date de la dernière mise à jour de la règle. |
| Date de début | Date de début d’une règle planifiée. |
| Date de fin | Date de fin d’une règle planifiée. |
| État | L’état codé par couleur indique l’état actuel de la règle. Utilisez le contrôle État situé au-dessus de la grille pour filtrer les règles par état. Valeurs : <br />Tout état : affiche toutes les règles, quel que soit l’état.<br />Actif (bleu) - Affiche uniquement les règles actives.<br />Planifié (orange) - affiche uniquement les règles planifiées.<br />Inactif (gris) : affiche uniquement les règles inactives. |

## Contrôles

| Contrôle | Description |
|--- |--- |
| Ajouter une règle | Ouvre l’ [éditeur de règles](rules-add.md). |
| État | Filtre la liste des règles par statut. Options : Toutes, Actives, Inactives, Planifiées |
| ![Sélecteur de colonnes](assets/btn-show-hide-columns.png) | Spécifie les colonnes visibles dans la grille. Options : Dernière mise à jour, Date de début, Date de fin, État |
| Rechercher | Recherche une règle par nom complet ou correspondance partielle. |
| ![Plus de sélecteur](assets/btn-more.png) | Affiche un menu d’actions supplémentaires pouvant être appliquées à la règle sélectionnée. Options : modification, afficher les détails, supprimer |

## Détails de la règle

| Champ | Description |
|--- |--- |
| État | État actuel de la règle. |
| Conditions | Requête de recherche qui décrit les conditions associées à la règle. |
| Date de début | Date d’entrée en vigueur de la règle, le cas échéant. |
| Date de fin | Date d’expiration de la règle, le cas échéant. |
| Description | Brève description de la règle. |
| Dernière mise à jour | Date et heure de la dernière mise à jour de la règle. |
| Activé | Contrôle qui modifie l’état de la règle. Options : activé/désactivé |
