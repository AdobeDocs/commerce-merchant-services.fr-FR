---
title: "Règles"
description: "[!DNL Live Search] les règles combinent logique et actions pour façonner l’expérience d’achat."
exl-id: d06a3040-6987-4813-90ae-2f7b3ad0b232
source-git-commit: 7307702a62a6b2c3e6c6083a59f2ac3587b0985e
workflow-type: tm+mt
source-wordcount: '588'
ht-degree: 0%

---

# Règles

[!DNL Live Search] les règles combinent logique et actions pour former l’expérience de recherche d’un acheteur dans votre magasin. Vous pouvez utiliser des règles pour dynamiser, enterrer, épingler ou masquer des produits afin d’étalonner les résultats de recherche en temps réel en fonction des objectifs de votre entreprise.

Chaque règle comporte trois composants principaux :

* Conditions : conditions qui déclenchent une action.
* Événements : actions qui se produisent lorsque les conditions sont remplies.
* Détails : nom de la règle, période et description facultative.

Vous pouvez combiner plusieurs conditions et actions et programmer l’activation d’une règle pour une période.

## Conditions

Une règle simple peut comporter une seule condition et un seul événement, tandis qu’une règle complexe peut comporter jusqu’à dix conditions qui déclenchent jusqu’à 25 événements.
Les règles peuvent comporter :

* Jusqu’à dix conditions
* Jusqu’à 25 événements

Le texte de la requête peut contenir :

* Caractères alphanumériques (lettres et chiffres)
* Caractères majuscules ou minuscules. La mise en majuscule est ignorée.

## Opérateurs logiques

Les opérateurs logiques `AND` et `OR` joignez deux conditions et renvoyez des résultats différents. Tous les opérateurs logiques utilisés dans une règle avec plusieurs conditions sont identiques. Il est impossible d’utiliser les deux `AND` et `OR` dans la même règle.

### Opérateurs de correspondance

Les opérateurs Correspondance `All` et `Any` déterminer l’opérateur logique utilisé pour associer plusieurs conditions dans la règle et qui peut être utilisé pour modifier l’opérateur existant ;

* `All` - Utilise la variable `AND` opérateur logique pour joindre plusieurs conditions. Une règle qui utilise la variable `All` L’opérateur de correspondance ne peut avoir qu’un seul `Search query is` condition.
* `Any` - Utilise la variable `OR` opérateur logique pour joindre plusieurs conditions.

Lors de la composition d’une règle complexe, il peut être utile de l’écrire avec une mise en retrait pour décrire les conditions, les événements associés, les noms de produits ou les SKU nécessaires pour renvoyer les résultats que vous souhaitez obtenir. Ensuite, créez la règle et testez le résultat.

## Ordre de priorité avec plusieurs règles

Une seule règle est appliquée à un terme de recherche à la fois.
Si plusieurs règles s’appliquent à une expression de recherche, toutes ces règles sont appliquées. En cas de collision entre deux règles —`rule 1` qui amplifie sku1 mais `rule 2` masque le même SKU, puis la règle la plus récemment appliquée (`rule 2`) a la priorité.

* Les règles sont classées selon l’horodatage &quot;Dernière modification&quot;. La règle la plus récemment modifiée est appliquée en premier, puis les règles plus anciennes, dans l’ordre d’horodatage.
* La variable `query is` La condition a la priorité sur les autres conditions. Si une règle plus récente contient une `query contains` , mais une règle plus ancienne comporte une `query is` , la condition `query is` est appliquée.

### Demandes Storefront

Si une règle active contenant une `query is` La condition correspond à l’expression recherchée, elle est appliquée. S’il existe plusieurs règles correspondantes avec une `query is` , la règle active mise à jour le plus récemment est appliquée.
Dans le cas contraire, la règle active mise à jour le plus récemment est appliquée.

### Aperçu des requêtes

Les requêtes effectuées dans l’administrateur fonctionnent légèrement différemment. Lors de la prévisualisation dans l’administrateur, toutes les règles sont appliquées, y compris celles qui ont expiré et planifiées.

* Si la règle en cours de prévisualisation comporte une `query is` , elle est appliquée.
* Si la règle en cours de prévisualisation n’a pas de `query is` et une règle active, correspondante suivante avec une `query is` est trouvée, la condition `query is` est appliquée.
* Si la règle en cours de prévisualisation n’a pas de `query is` et aucune autre règle avec une `query is` condition est trouvée, puis la règle en cours de prévisualisation est appliquée.

## Règles de catégorie et affectations de produits de catégorie

[!DNL Live Search] vous permet de filtrer par catégories.
Cependant, dans Adobe Commerce, vous pouvez créer une catégorie virtuelle avec [Affectations de produits de catégorie](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/products-in-category/categories-product-assignments.html). Ce type de catégorie est créé au moment de l’exécution et n’existe pas dans la base de données des catégories. Par conséquent, [!DNL Live Search] ne peuvent pas lire ni utiliser ce type de catégorie.
