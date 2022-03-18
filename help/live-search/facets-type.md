---
title: Types de facettes
description: Les facettes de recherche en direct sont dynamiques et apparaissent dans la liste Filtres lorsque cela est pertinent.
exl-id: 49fb7609-64b3-4ae8-928d-54c99032d919
source-git-commit: 19f0c987ab6b43b6fac1cad266b5fd47a7168e73
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Types de facettes

Tous [!DNL Live Search] les facettes sont dynamiques et apparaissent dans la variable *Filtres* n’est répertorié que lorsque cela est pertinent. La liste des facettes disponibles change en fonction des produits renvoyés. Les caractéristiques suivantes affectent leur présentation et leur comportement :

* Facettes épinglées : les facettes les plus couramment utilisées peuvent être collées en haut de la liste. Les autres facettes sont répertoriées dans la section *Type de tri* commande après les facettes épinglées.
* Facettes intelligentes - Attributs de produit qui [Adobe Sensei](https://www.adobe.com/sensei.html) trouve le plus pertinent pour un ensemble de produits et une requête. Le calcul prend en compte les métadonnées d’attribut de l’ensemble du catalogue et détermine au moment de la requête les facettes les plus pertinentes pour la requête.
* Facettes populaires : attributs de produit qui sont le plus souvent présents dans les résultats de recherche.
* Facettes de prix : revenez des produits par tranche de prix. Vous pouvez indiquer le nombre de sélections et l’intervalle de prix sur la variable [*Paramètres*](settings.md) .

Au moment de la requête, [!DNL Live Search] génère les résultats de recherche dans des groupes de facettes intelligentes et populaires.

![Facettes - Prix](assets/storefront-search-results-run-price.png)

## Options Storefront et headless

Facettes rendues pour la variable [!DNL Commerce] storefront est traité par l’adaptateur de recherche, qui achemine les requêtes et effectue le rendu des résultats dans le storefront. Tous [!DNL Commerce] les facettes storefront sont triées par ordre alphabétique avec des options à sélection unique, quel que soit le type d’entrée affecté à l’attribut correspondant. Les facettes disponibles dans le storefront sont rendues en fonction du thème actuel et reflètent toutes les personnalisations apportées à la présentation de la navigation par couches.

En revanche, [headless](https://devdocs.magento.com/guides/v2.4/architecture/archi_perspectives/webapi-vision.html) Les implémentations sont traitées par l’API et prennent en charge des options supplémentaires. Les facettes sans affichage peuvent être triées par ordre alphabétique ou par nombre et peuvent comporter des options à sélection simple ou multiple.

### Sélectionner un type

Pour les implémentations sans interface utilisateur graphique, les facettes peuvent être définies comme `single select` ou `multi-select` avec des opérateurs logiques qui déterminent le jeu de produits renvoyé. Par exemple : `green AND blue` ou `green OR blue`.

![Facettes : sélectionnez le type](assets/facets-select-type.png)

| Sélectionner un type | Description |
|--- |--- |
| Sélection simple | Une facette à sélection unique offre plusieurs options, mais permet à l’acheteur de choisir une seule valeur. |
| Sélection multiple (ou) | (Sans affichage uniquement) Les acheteurs peuvent choisir plusieurs options et les produits renvoyés peuvent correspondre à n’importe quelle valeur sélectionnée. Exemple : `green OR blue` |
| Sélection multiple (et) | (Sans affichage uniquement) Les acheteurs peuvent choisir plusieurs options et les produits renvoyés doivent correspondre à toutes les valeurs sélectionnées. Exemple : `green AND blue` |

### Étiquettes de facettes

Pour [!DNL Commerce] storefronts, l’étiquette de la facette est déterminée par [*Propriétés d’attribut*](https://docs.magento.com/user-guide/stores/attribute-product-create.html). Pour les magasins avec plusieurs vues, des libellés supplémentaires peuvent être définis sous *Gestion des étiquettes*. Pour les implémentations sans interface utilisateur, les libellés sont modifiés à partir de la fonction [espace de travail facetting](faceting-workspace.md).

### Type de tri

Toutes les facettes générées pour le storefront sont triées par ordre alphabétique. Pour les implémentations sans interface utilisateur graphique, les facettes peuvent être triées par ordre alphabétique ou par nombre.

| Type de tri | Description |
|--- |--- |
| Alphabétique | Dans la vitrine *Filtres* liste, les facettes sont triées par ordre alphabétique. |
| Count | (Sans affichage uniquement) Pour les implémentations sans interface utilisateur graphique, les facettes peuvent également être triées par le nombre de valeurs trouvées par facette dans l’ensemble actuel de produits renvoyés. |
