---
title: "Gestion des facettes"
description: "Découvrez comment gérer les [!DNL Live Search] facettes."
exl-id: 1d51a36a-20d6-46b6-b379-11e46c8824a0
source-git-commit: 3d0de3eeb4aa96c996bc9fa38cffd7597e89e7ca
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# Gestion des facettes

Suivez ces instructions pour mettre à jour les propriétés des facettes existantes ou modifier leur présentation dans le storefront.

## Configuration des groupements de facettes de prix

Voir [Paramètres](settings.md) pour configurer des intervalles et des groupements de facettes de prix.

## Modifier la facette

1. Recherchez la facette à modifier.
1. S’il existe de nombreuses facettes dans la liste, définissez *Filtrer par* à l’une des options suivantes :

   * Pindu
   * Dynamique

   Pour en savoir plus, accédez à [Types de facettes](facets-type.md).

   ![Facettes de filtrage](assets/facets-filter-by-cropped.png)

1. Pour modifier les propriétés de la facette, cliquez sur **Plus** (...).
1. Cliquez sur **Modifier**

   ![Options de modification](assets/facet-edit-menu.png)

1. Pour modifier le libellé de la facette, effectuez l’une des opérations suivantes :

   * Pour un [!DNL Commerce] storefront, modifiez la variable [label](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html).
   * Pour une mise en oeuvre sans interface utilisateur graphique, cliquez sur la valeur de la première colonne et modifiez le texte selon vos besoins.

   ![Modifier le libellé](assets/facet-edit-label.png)

1. (Sans affichage uniquement) Pour modifier la méthode utilisée pour trier les valeurs de facette, cliquez sur la valeur dans la variable *Type de tri* et sélectionnez l’une des options suivantes :

   * Alphabétique
   * Count

   ![Modifier le nombre](assets/facets-edit-count.png)

1. Dans le **Valeur max.** , définissez le nombre maximal (de 0 à 10) de valeurs de filtre de facettes à afficher dans le storefront.
1. Une fois l’opération terminée, cliquez sur **Enregistrer**.
Vos modifications n’apparaîtront sur le storefront qu’après leur publication.

## Epinglage/annulation de la facette

L’épingle change de couleur lorsque l’utilisateur clique dessus. Elle est utilisée pour déplacer la facette vers l’une des options suivantes : *Facettes épinglées* ou le *Facettes dynamiques* .

1. Pour épingler une facette en haut de la page *Filtres* recherchez la facette dans la liste *Facettes dynamiques* et cliquez sur la épingle grise (![Sélecteur d’épingles](assets/btn-pin-gray.png)).
L’épingle devient bleue et la facette se déplace vers le *Facettes épinglées* .
1. Pour dissocier une facette, recherchez-la dans la variable *Facettes épinglées* et cliquez sur l’épingle bleue (![Sélecteur d’épingles](assets/btn-pin-blue.png)).
La broche devient grise et la facette passe à la fenêtre *Facettes dynamiques* .

   ![Facettes Pinces et dynamiques](assets/facets-pinned-unpinned.png)

## Déplacer la facette épinglée

Vous pouvez modifier l’ordre des facettes épinglées en déplaçant la rangée vers une autre position. Les facettes pincées ont une *Déplacer* Icône (![Sélecteur de déplacement](assets/btn-move.png)) au début de la ligne. Contrairement aux facettes épinglées, les facettes dynamiques ne peuvent pas être déplacées.

1. Recherchez la facette dans le *Facettes épinglées* de la liste.
1. Utilisez la variable **Déplacer** (![Sélecteur de déplacement](assets/btn-move.png)) pour faire glisser la rangée vers un nouvel emplacement dans le *Facettes épinglées* .
Une fois les modifications publiées, les facettes réorganisées apparaissent dans le storefront. *Filtres* liste.

## Suppression de la facette

1. Recherchez la facette dans la liste, puis cliquez sur **Plus** (...).
1. Cliquez sur **Supprimer**.
1. Lorsque vous y êtes invité, cliquez sur **Suppression de la facette**.
La facette est supprimée du storefront une fois les modifications publiées.

## Publier les modifications

1. Pour mettre à jour le storefront avec vos modifications, cliquez sur **Publier les modifications**.
1. Patientez environ 15 minutes pendant que les mises à jour s’affichent dans votre boutique.
