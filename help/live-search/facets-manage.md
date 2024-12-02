---
title: Gestion des facettes
description: Découvrez comment gérer les facettes  [!DNL Live Search] existantes.
exl-id: 1d51a36a-20d6-46b6-b379-11e46c8824a0
source-git-commit: bce69f952e70e2e8dcb892357dea41e18f61e5f6
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# Gestion des facettes

Suivez ces instructions pour mettre à jour les propriétés des facettes existantes ou modifier leur présentation dans le storefront.

## Configuration des groupements de facettes de prix

Reportez-vous à la section [Paramètres](settings.md) pour configurer des intervalles et des groupements de facettes de prix.

## Modifier la facette

1. Recherchez la facette à modifier.
1. S’il existe de nombreuses facettes dans la liste, définissez *Filtrer par* sur l’une des facettes suivantes :

   * Pindu
   * Dynamique

   Pour en savoir plus, consultez [Types de facettes](facets-type.md).

   ![Facettes de filtre](assets/facets-filter-by-cropped.png)

1. Pour modifier les propriétés de la facette, cliquez sur les options **Plus** (...) .
1. Cliquez sur **Modifier**

   ![ Modifier les options](assets/facet-edit-menu.png)

1. Pour modifier le libellé de la facette, effectuez l’une des opérations suivantes :

   * Pour un storefront [!DNL Commerce], modifiez l’ [étiquette d’attribut](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html).
   * Pour une mise en oeuvre sans interface utilisateur graphique, cliquez sur la valeur de la première colonne et modifiez le texte selon vos besoins.

   ![Modifier l’étiquette](assets/facet-edit-label.png)

1. (Sans affichage uniquement) Pour modifier la méthode utilisée pour trier les valeurs de facette, cliquez sur la valeur dans la colonne *Type de tri* et sélectionnez l’une des options suivantes :

   * Alphabétique
   * Count

   ![Modifier le nombre](assets/facets-edit-count.png)

1. Dans la colonne **Max Value** , définissez le nombre maximal (de 0 à 10) de valeurs de filtre de facettes à afficher dans le storefront.
1. Une fois l’opération terminée, cliquez sur **Enregistrer**.
Vos modifications n’apparaîtront sur le storefront qu’après leur publication.

## Epinglage/annulation de la facette

L’épingle change de couleur lorsqu’on clique dessus et sert à déplacer la facette vers la section *Facettes épinglées* ou *Facettes dynamiques* .

1. Pour épingler une facette en haut de la liste *Filtres*, recherchez-la dans la liste *Facettes dynamiques* et cliquez sur la épingle grise (![Sélecteur d’épingles](assets/btn-pin-gray.png)).
L’épingle devient bleue et la facette passe à la section *Facettes épinglées* .
1. Pour désépingler une facette, recherchez-la dans la liste *Facettes épinglées* et cliquez sur la épingle bleue (![Sélecteur d’épingles](assets/btn-pin-blue.png)).
Le pin devient gris et la facette passe à la section *Facettes dynamiques* .

   ![Facettes Pindu et dynamiques](assets/facets-pinned-unpinned.png)

>[!NOTE]
>
>L’ordre des facettes épinglé peut être incohérent s’il existe deux libellés portant le même nom.

## Déplacer la facette épinglée

>[!NOTE]
>
>L’ordre des facettes épinglées n’est pris en charge que dans les implémentations sans interface utilisateur graphique. Si des facettes triées sont nécessaires, utilisez le widget [!DNL Live Search] PLP.

Vous pouvez modifier l’ordre des facettes épinglées en déplaçant la rangée vers une autre position. Les facettes pincées ont une icône *Déplacer* (![Déplacer le sélecteur](assets/btn-move.png)) au début de la ligne. Contrairement aux facettes épinglées, les facettes dynamiques ne peuvent pas être déplacées.

1. Recherchez la facette dans la section *Facettes imprimées* de la liste.
1. Utilisez l’icône **Déplacer** (![Déplacer le sélecteur](assets/btn-move.png)) pour faire glisser la rangée vers un nouvel emplacement dans la section *Facettes épinglées*.
Une fois les modifications publiées, les facettes réorganisées apparaissent dans la liste *Filtres* du storefront.

## Suppression de la facette

1. Recherchez la facette dans la liste et cliquez sur les options **Plus** (...) .
1. Cliquez sur **Supprimer**.
1. Lorsque vous êtes invité à confirmer, cliquez sur **Supprimer la facette**.
La facette est supprimée du storefront une fois les modifications publiées.

## Modifications Publish

1. Pour mettre à jour le storefront avec vos modifications, cliquez sur **Publish changes**.
1. Patientez environ 15 minutes pendant que les mises à jour s’affichent dans votre boutique.
