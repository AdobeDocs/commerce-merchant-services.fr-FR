---
title: "Facettes"
description: "[!DNL Live Search] les facettes utilisent plusieurs dimensions de valeurs d’attribut comme critères de recherche."
exl-id: 63c0b255-6be9-41ad-b4bf-13bb7ff098fd
source-git-commit: 460065ecf6478e4313bd31ea848e04c7e8e192a3
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 0%

---

# Facettes

La facette est une méthode de filtrage haute performance qui utilise plusieurs dimensions de valeurs d’attribut comme critères de recherche. La recherche à facettes est similaire, mais considérablement &quot;plus intelligente&quot; que la [navigation par couches](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-layered.html) standard. La liste des filtres disponibles est déterminée par les [attributs filtrables](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-layered.html#filterable-attributes) des produits renvoyés dans les résultats de recherche.

[!DNL Live Search] utilise la requête `productSearch`, qui renvoie des facettes et d’autres données spécifiques à [!DNL Live Search]. Pour obtenir des exemples de code, reportez-vous à la requête [`productSearch`](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/) dans la documentation destinée aux développeurs.

![Résultats de la recherche filtrés](assets/storefront-search-results-run.png)

Toute facette définie peut être utilisée comme paramètre d’URL et les résultats seront filtrés en fonction des valeurs du paramètre : `http://yourstore.com?brand=acme&color=red`.

## Configuration requise

Les exigences d’attribut de catégorie et de produit pour la facette sont similaires aux attributs filtrables utilisés pour la navigation par couches. Pour chaque propriété storefront d’un attribut, la valeur &quot;Use in Search Results Layered Navigation&quot; doit être définie sur &quot;Yes&quot;.

[!DNL Live Search] prend en charge jusqu’à :

* 100 attributs configurés en tant que facettes
* 50 attributs triables
* 200 attributs filtrables
* 200 attributs pouvant faire l’objet de recherches

>[!NOTE]
>
> Si plus de 200 attributs filtrables sont définis, il n’est pas déterministe de savoir lequel 200 sera réellement indexé.

Si vous avez un grand nombre d’attributs à utiliser, pensez à combiner les attributs en un seul &quot;méta-attribut&quot;. Par exemple, les chaussures ont généralement des tailles numériques, tandis que les chemises sont généralement de la taille &quot;S/M/L/XL&quot;. Ces deux types de tailles peuvent être combinés en un seul attribut pouvant faire l’objet d’une recherche.

| Paramètre | Description |
|--- |--- |
| [ Paramètres d’affichage des catégories](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/create/categories-display-settings.html) | Ancre - `Yes` |
| [Propriétés d’attribut](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/attribute-product-create.html) | [Type d’entrée de catalogue](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/attributes-input-types.html) - `Yes/No`, `Dropdown`, `Multiple Select`, `Price`, `Visual swatch` (widget uniquement), `Text swatch` (widget uniquement) |
| Propriétés Attribute storefront | Utilisation dans la navigation par couches des résultats de recherche - `Yes` |

## Agrégation des facettes

L’agrégation des facettes est effectuée comme suit : si le storefront comporte trois facettes (catégories, couleur et prix) et que les filtres de la boutique sont appliqués aux trois éléments (couleur = bleu, le prix est compris entre 10,00 $ et 50,00 $, catégories = `promotions`).

* `categories` - Agrégat `categories`, puis applique les filtres `color` et `price`, mais pas le filtre `categories`.
* `color` - Agrégat `color`, puis applique les filtres `price` et `categories`, mais pas le filtre `color`.
* `price` - Agrégat `price`, puis applique les filtres `color` et `categories`, mais pas le filtre `price`.

## Valeurs d’attribut par défaut

Les attributs de produit suivants ont des [propriétés storefront](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) utilisées par [!DNL Live Search] et activées par défaut.

| Propriété | Propriété Storefront | Attribut |
|---|---|---|
| Triable | Utilisé pour le tri dans la liste des produits | `price` |
| Recherche | Utilisation dans la recherche | `price` <br />`sku`<br />`name` |
| FilterableInSearch | Utilisation dans la navigation par couches - Filtrable (avec résultats) | `price`<br />`visibility`<br />`category_name` |

## Propriétés d’attribut non système par défaut

Le tableau suivant présente les propriétés de recherche et de filtrage par défaut des attributs non-système, y compris ceux spécifiques aux exemples de données Luma. La définition de la propriété d’attribut *Use in Search* sur `Yes` rend l’attribut consultable dans [!DNL Live Search] et dans Adobe Commerce natif.

| Code d’attribut | Recherche | Utilisation dans la navigation par calques |
|--- |--- |--- |
| activité | Oui | Filtrable (avec résultats) |
| attributes_brand | Oui | Non |
| marque | Oui | Non |
| climat | Oui | Filtrable (avec résultats) |
| collier | Oui | Filtrable (avec résultats) |
| color | Oui | Filtrable (avec résultats) |
| coût | Oui | Non |
| eco_collection | Oui | Filtrable (avec résultats) |
| gender | Oui | Filtrable (avec résultats) |
| manufacturer | Oui | Filtrable (avec résultats) |
| matériau | Oui | Filtrable (avec résultats) |
| objectif | Oui | Filtrable (avec résultats) |
| strap_bags | Oui | Filtrable (avec résultats) |
| style_general | Oui | Filtrable (avec résultats) |

## Propriétés d’attribut système par défaut

Le tableau suivant présente les propriétés de recherche et de filtrage par défaut des attributs système.

| Code d’attribut | Recherche | Utilisation dans la navigation par calques |
|--- |--- |--- |
| allow_open_amount | Oui | Filtrable (avec résultats) |
| description | Oui | Non |
| name | Oui | Non |
| prix | Oui | Filtrable (avec résultats) |
| short_description | Oui | Non |
| sku | Oui | Non |
| status | Oui | Non |
| tax_class_id | Oui | Non |
| url_key | Oui | Non |
| poids | Oui | Non |
