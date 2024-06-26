---
title: "Ajouter des facettes"
description: "Découvrez comment ajouter des attributs de produit filtrables en tant que [!DNL Live Search] facettes."
exl-id: 0df6c21b-55b3-41ce-94f4-f70b70ffb84e
source-git-commit: 4978bdb5549f5df911863a23fdfbfc9ab9ad05df
workflow-type: tm+mt
source-wordcount: '597'
ht-degree: 0%

---

# Ajout de facettes

Tout attribut de produit filtrable peut être utilisé comme facette. La variable *Ajout de facettes* répertorie les facettes actives et facilite l’affectation d’attributs de produit supplémentaires en tant que facettes. Au cours de ce processus en trois étapes, un attribut est sélectionné pour être utilisé comme facette, les propriétés sont modifiées si nécessaire et les modifications publiées sur le storefront.

![Ajout de facettes](assets/facets-add.png)

## Étape 1 : Ajout d’une facette

1. Dans Admin, accédez à **Marketing** > SEO &amp; Search > **[!DNL Live Search]**.
1. Sur le *Facturation* , cliquez sur **Ajout de facettes**.
1. Dans le *Ajout de facettes* liste, chaque attribut disponible possède une propriété distincte ![Bouton Ajouter](assets/btn-add.png). Procédez de l’une des manières suivantes :

   * Dans le *Attributs de facette* , sélectionnez l’attribut de produit à utiliser comme facette, puis cliquez sur **Ajouter**.
   * Pour rechercher un attribut de produit spécifique, saisissez les premiers caractères du nom de l’attribut dans la variable *Rechercher* de la boîte. Cliquez ensuite sur **Ajouter**.

     Pour configurer les intervalles et les groupements de facettes de prix, reportez-vous à la section [Paramètres](settings.md). Pour en savoir plus, accédez à [Types de facettes](facets-type.md).
La facette est ajoutée au bas de la *Facettes dynamiques* et la liste *Publier les modifications* devient disponible.

1. Si la facette que vous souhaitez ajouter est introuvable, accédez à **Magasins** > Attributs > **Produit** et vérifiez que l’attribut a la valeur [propriétés requises](facets.md) à utiliser comme facette. Si nécessaire, mettez à jour les propriétés storefront suivantes de l’attribut :

   * Utiliser dans la recherche - `Yes`
   * Utilisation dans la navigation par couches des résultats de recherche - `Yes`
   * Utilisation dans la navigation par couches - `Filterable (with results)`

1. Lorsque vous y êtes invité, actualisez le cache.

   La facette devient disponible dans le storefront lors de la prochaine synchronisation du catalogue avec [!DNL Live Search]. Si la facette n’est pas disponible au bout de deux heures, voir [Synchronisation des données de catalogue](install.md#synchronize-catalog-data).

## Étape 2 : modification des propriétés de facette (facultatif)

1. Pour modifier les propriétés de la facette, cliquez sur **Plus** (![Sélecteur supplémentaire](assets/btn-more.png)) dans la colonne extrême droite.
1. Dans le menu, cliquez sur **Modifier**. Ensuite, ajustez les propriétés suivantes selon les besoins.

   * Libellé - ([Headless](facets-type.md) uniquement) Saisissez le libellé de la facette à utiliser.
   * Type de tri : les facettes sont triées par ordre alphabétique pour toutes les [!DNL Commerce] storefronts. Pour les implémentations sans interface utilisateur graphique, les facettes peuvent être triées soit par ordre alphabétique, soit par nombre. Options : Alphabétique, Comptage (headless uniquement)
   * Max Value : saisissez le nombre maximal de valeurs de facette affichées dans le storefront. Entrées valides : 0 à 30 ; Par défaut : 8

1. Lorsque vous avez terminé, cliquez sur **Enregistrer**.

   ![Modifier les facettes](assets/facet-edit.png)

1. Pour épingler la facette en haut de la page *Filtres* , cliquez sur la punaise grise (![Sélecteur d’épingles](assets/btn-pin-gray.png)).
1. Pour modifier l’ordre de la facette épinglée, cliquez sur le bouton **Déplacer** (![Sélecteur de déplacement](assets/btn-move.png)) et faites glisser la rangée vers un nouvel emplacement dans le *Facettes Pindu* .

## Étape 3 : Publier les modifications

1. Une fois la facette terminée, cliquez sur **Publier les modifications**.
1. Attendez que la facette apparaisse dans le magasin.
Si la facette n’est pas disponible au bout de deux heures, voir [Vérifier l’exportation](install.md#synchronize-catalog-data) dans les instructions d’installation.

## Descriptions des champs

| Champ | Description |
|--- |--- |
| Libellé | ([Headless](facets-type.md) uniquement) La variable [libellé de la facette](facets-type.md) qui est visible dans le storefront peut être modifié pour être cohérent avec votre marque. |
| Type de tri | La méthode utilisée pour [sort](facets-type.md) facettes. Tous [!DNL Commerce] storefronts sort les facettes par ordre alphabétique uniquement. Les implémentations sans affichage peuvent également être triées par `Count`. Options :<br />Alphabétique : trie les facettes par ordre alphabétique.<br />Nombre : (sans affichage uniquement) trie les facettes en fonction du nombre de correspondances trouvées. |
| Valeur max. | Nombre maximal de valeurs pouvant être affichées dans le storefront pour chaque facette. Les facettes qui représentent une plage de valeurs sont uniformément réparties. Entrées valides : 0 à 30 ; Par défaut : 8 |

### Contrôles

| Contrôle | Description |
|--- |--- |
| ![Sélecteur d’épingles](assets/btn-pin-blue.png) | Epinglage ou désolidarisation d’une facette en haut de l’écran *Filtres* liste. |
| ![Sélecteur supplémentaire](assets/btn-more.png) | Affiche un menu d’actions supplémentaires pouvant être appliquées à la facette sélectionnée. Options : modification, suppression |
| ![Sélecteur de déplacement](assets/btn-move.png) | Utilisez la variable *Déplacer* pour faire glisser une facette épinglée vers un autre emplacement de la *Facettes Pindu* . |
