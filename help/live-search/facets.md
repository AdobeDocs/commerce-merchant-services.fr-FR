---
title: Facettes
description: Les facettes de recherche en direct utilisent plusieurs dimensions de valeurs d’attribut comme critères de recherche.
exl-id: 63c0b255-6be9-41ad-b4bf-13bb7ff098fd
source-git-commit: 19f0c987ab6b43b6fac1cad266b5fd47a7168e73
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Facettes

La facette est une méthode de filtrage haute performance qui utilise plusieurs dimensions de valeurs d’attribut comme critères de recherche. La recherche à facettes est similaire, mais considérablement &quot;plus intelligente&quot; que la norme [navigation par couches](https://docs.magento.com/user-guide/catalog/navigation-layered.html). La liste des filtres disponibles est déterminée par la variable [attributs filtrables](https://docs.magento.com/user-guide/catalog/navigation-layered-filterable-attributes.html) des produits renvoyés dans les résultats de recherche. Vous pouvez configurer jusqu’à 100 facettes avec [!DNL Live Search].

![Résultats de la recherche filtrés](assets/storefront-search-results-run.png)

## Facturation des exigences

Les exigences d’attribut de catégorie et de produit pour la facette sont similaires aux attributs filtrables utilisés pour la navigation par couches. Les propriétés storefront de chaque attribut doivent être définies sur `filterable (with results)`.

| Paramètre | Description |
|--- |--- |
| [Paramètres d’affichage des catégories](https://docs.magento.com/user-guide/catalog/categories-display-settings.html) | Ancre - `Yes` |
| [Propriétés d’attribut](https://docs.magento.com/user-guide/stores/attribute-product-create.html) | [Type d’entrée de catalogue](https://docs.magento.com/user-guide/stores/attributes-input-types.html) - `Yes/No`, `Dropdown`, `Multiple Select`, `Price` |
| Propriétés Attribute storefront | Utilisation dans la navigation par couches - `Filterable (with results)` |

## Propriétés d’attribut non système par défaut

Le tableau suivant présente les propriétés de recherche et de filtrage par défaut des attributs non-système, y compris ceux spécifiques aux exemples de données Luma. La définition de la variable *Utilisation dans la recherche* Attribuer la propriété à `Yes` rend l’attribut consultable dans les deux [!DNL Live Search] et Adobe Commerce natif.

| Code d’attribut | Searchable | Utilisation dans la navigation par calques |
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

| Code d’attribut | Searchable | Utilisation dans la navigation par calques |
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
