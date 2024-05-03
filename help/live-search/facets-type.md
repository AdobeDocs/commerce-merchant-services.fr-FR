---
title: "Types de facettes"
description: "[!DNL Live Search] les facettes sont dynamiques et apparaissent dans la liste Filtres lorsque cela est pertinent."
exl-id: 49fb7609-64b3-4ae8-928d-54c99032d919
source-git-commit: f96f94a16e1926b7dd2f1ee94f124ac0c823a9e0
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# Types de facettes

[!DNL Live Search] utilise divers types de facettes qui apparaissent dans la variable *Filtres* n’est répertorié que lorsque cela est pertinent. La liste des facettes disponibles change en fonction des produits renvoyés. Les caractéristiques suivantes affectent leur présentation et leur comportement :

* Facettes épinglées : les facettes les plus couramment utilisées peuvent être collées en haut de la liste. Les autres facettes sont répertoriées dans la section *Type de tri* commande après les facettes épinglées.
* Facettes dynamiques - Attributs de produit qui [Adobe Sensei](https://www.adobe.com/sensei.html) trouve le plus pertinent pour un ensemble de produits et une requête. Le calcul prend en compte les métadonnées d’attribut de l’ensemble du catalogue et détermine au moment de la requête les facettes les plus pertinentes pour la requête.
* Facettes populaires : attributs de produit qui sont le plus souvent présents dans les résultats de recherche.
* Facettes de prix : revenez des produits par tranche de prix. Vous pouvez indiquer le nombre de sélections et l’intervalle de prix sur la variable [*Paramètres*](settings.md) workspace.

Au moment de la requête, [!DNL Live Search] génère les résultats de recherche dans des groupes de facettes dynamiques et populaires.

![Facettes - Prix](assets/storefront-search-results-run-price.png)

## Options Storefront et headless

Facettes rendues pour la variable [!DNL Commerce] storefront est traité par l’adaptateur de recherche, qui achemine les requêtes et effectue le rendu des résultats dans le storefront. Tous [!DNL Commerce] les facettes storefront sont triées par ordre alphabétique avec des options à sélection unique, quel que soit le type d’entrée affecté à l’attribut correspondant. Les facettes disponibles dans le storefront sont rendues en fonction du thème actuel et reflètent toutes les personnalisations apportées à la présentation de la navigation par couches.

En revanche, [headless](https://developer.adobe.com/commerce/php/architecture/technical-vision/web-api/) Les implémentations sont traitées par l’API et prennent en charge des options supplémentaires. Les facettes sans affichage peuvent être triées par ordre alphabétique ou par nombre et peuvent comporter des options à sélection simple ou multiple.

### Étiquettes de facettes

Pour [!DNL Commerce] storefronts, l’étiquette de la facette est déterminée par [*Propriétés d’attribut*](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/attribute-product-create.html). Pour les magasins avec plusieurs vues, des libellés supplémentaires peuvent être définis sous *Gestion des étiquettes*. Pour les implémentations sans interface utilisateur, les libellés sont modifiés à partir de la fonction [espace de travail facetting](faceting-workspace.md).

### Type de tri

Toutes les facettes générées pour le storefront sont triées par ordre alphabétique. Pour les implémentations sans interface utilisateur graphique, les facettes peuvent être triées par ordre alphabétique ou par nombre.

| Type de tri | Description |
|--- |--- |
| Alphabétique | Dans la vitrine *Filtres* liste, les facettes sont triées par ordre alphabétique. |
| Count | (Sans affichage uniquement) Pour les implémentations sans interface utilisateur graphique, les facettes peuvent également être triées par le nombre de valeurs trouvées par facette dans l’ensemble actuel de produits renvoyés. |
