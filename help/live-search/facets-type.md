---
title: "Types de facettes"
description: "[!DNL Live Search] les facettes sont dynamiques et apparaissent dans la liste Filtres lorsque cela est pertinent."
exl-id: 49fb7609-64b3-4ae8-928d-54c99032d919
source-git-commit: ffbb41ef2bc940982b4acb33623ef689542617c1
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---

# Types de facettes

[!DNL Live Search] utilise divers types de facettes et ils apparaissent dans la liste *Filtres* uniquement lorsque cela est pertinent. La liste des facettes disponibles change en fonction des produits renvoyés. Les caractéristiques suivantes affectent leur présentation et leur comportement :

* Facettes épinglées : les facettes les plus couramment utilisées peuvent être collées en haut de la liste. Les autres facettes sont répertoriées dans l’ordre *Type de tri* après les facettes épinglées.
* Facettes dynamiques : attributs de produit qui [Adobe Sensei](https://www.adobe.com/sensei.html) trouvent les plus pertinents pour un ensemble de produits et une requête. Le calcul prend en compte les métadonnées d’attribut de l’ensemble du catalogue et détermine au moment de la requête les facettes les plus pertinentes pour la requête.

  >[!NOTE]
  >
  >Si vous constatez que des erreurs de délai d’expiration s’affichent dans la réponse de requête GraphQL après la création de facettes dynamiques, modifiez toutes les facettes à épingler pour voir si cela résout les problèmes de performances.

* Facettes populaires : attributs de produit qui sont le plus souvent présents dans les résultats de recherche.
* Facettes de prix : revenez des produits par tranche de prix. Vous pouvez spécifier le nombre de sélections et l’intervalle de prix sur l’espace de travail [*Paramètres*](settings.md).

Au moment de la requête, [!DNL Live Search] génère les résultats de la recherche dans des groupes de facettes dynamiques et populaires.

![Facettes - Price](assets/storefront-search-results-run-price.png)

## Options Storefront et headless

Les facettes rendues pour le storefront [!DNL Commerce] sont traitées par l’adaptateur de recherche, qui achemine les requêtes et effectue le rendu des résultats dans le storefront. Toutes les facettes de storefront [!DNL Commerce] sont triées par ordre alphabétique avec des options à sélection unique, quel que soit le type d’entrée affecté à l’attribut correspondant. Les facettes disponibles dans le storefront sont rendues en fonction du thème actuel et reflètent toutes les personnalisations apportées à la présentation de la navigation par couches.

En revanche, les implémentations [headless](https://developer.adobe.com/commerce/php/architecture/technical-vision/web-api/) sont traitées par l’API et prennent en charge des options supplémentaires. Les facettes sans affichage peuvent être triées par ordre alphabétique ou par nombre et peuvent comporter des options à sélection simple ou multiple.

### Étiquettes de facettes

Pour [!DNL Commerce] storefronts, le libellé de la facette est déterminé par les [*Propriétés de l’attribut*](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/attribute-product-create.html). Pour les magasins avec plusieurs vues, des étiquettes supplémentaires peuvent être définies sous *Gérer les étiquettes*. Pour les implémentations sans interface utilisateur, les libellés sont modifiés à partir de l’[ espace de travail de faceting](faceting-workspace.md).

### Type de tri

Toutes les facettes générées pour le storefront sont triées par ordre alphabétique. Pour les implémentations sans interface utilisateur graphique, les facettes peuvent être triées par ordre alphabétique ou par nombre.

| Type de tri | Description |
|--- |--- |
| Alphabétique | Dans la liste *Filtres* de la vitrine, les facettes sont triées par ordre alphabétique. |
| Count | (Sans affichage uniquement) Pour les implémentations sans interface utilisateur graphique, les facettes peuvent également être triées par le nombre de valeurs trouvées par facette dans l’ensemble actuel de produits renvoyés. |
