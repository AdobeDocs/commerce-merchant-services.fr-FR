---
title: Marchandisage des recherches
description: '[!DNL Live Search] Les règles de marchandisage combinent logique et actions pour façonner l’expérience d’achat.'
exl-id: d06a3040-6987-4813-90ae-2f7b3ad0b232
source-git-commit: 2b0ca3f5a68e75ef4b4e71ac7705b17534e16845
workflow-type: tm+mt
source-wordcount: '681'
ht-degree: 0%

---

# Marchandisage des recherches

Le marchandisage de recherche fait référence à un ensemble de règles qui combinent logique et actions pour former l’expérience de recherche d’un acheteur dans votre magasin. Vous pouvez utiliser des règles de marchandisage pour dynamiser, enterrer, épingler ou masquer des produits afin d’étalonner les résultats de recherche en temps réel pour prendre en charge vos objectifs commerciaux.

Chaque règle comporte trois composants principaux :

* Conditions : conditions qui déclenchent une action.
* Événements : actions qui se produisent lorsque les conditions sont remplies.
* Détails : nom de la règle, période et description facultative.

Vous pouvez combiner plusieurs conditions et actions et programmer l’activation d’une règle pour une période. Vous pouvez également définir une règle par défaut qui est appliquée même lorsqu’aucun terme de recherche n’est défini.

## Conditions

Une règle de recherche simple peut comporter une seule condition et un seul événement, tandis qu’une règle complexe peut comporter jusqu’à dix conditions qui déclenchent jusqu’à 25 événements.
Les règles peuvent comporter :

* Jusqu’à dix conditions
* Jusqu’à 25 événements

Le texte de la requête peut contenir :

* Caractères alphanumériques (lettres et chiffres)
* Caractères majuscules ou minuscules. La mise en majuscule est ignorée.

## Opérateurs logiques

Les opérateurs logiques `AND` et `OR` joignent deux conditions et renvoient des résultats différents. Tous les opérateurs logiques utilisés dans une règle avec plusieurs conditions sont identiques. Il n&#39;est pas possible d&#39;utiliser à la fois `AND` et `OR` dans la même règle.

### Opérateurs de correspondance

Les opérateurs de correspondance `All` et `Any` déterminent l’opérateur logique utilisé pour joindre plusieurs conditions dans la règle et peuvent être utilisés pour modifier l’opérateur existant.

* `All` - Utilise l’opérateur logique `AND` pour joindre plusieurs conditions. Une règle qui utilise l’opérateur `All` Correspondance ne peut avoir qu’une seule condition `Search query is`.
* `Any` - Utilise l’opérateur logique `OR` pour joindre plusieurs conditions.

Lors de la composition d’une règle complexe, il peut être utile de l’écrire avec une mise en retrait pour décrire les conditions, les événements associés, les noms de produits ou les SKU nécessaires pour renvoyer les résultats que vous souhaitez obtenir. Ensuite, créez la règle et testez le résultat.

## Règle par défaut

Vous pouvez définir une règle par défaut qui est appliquée lorsqu’aucun terme de recherche n’est fourni ou qu’aucune autre règle de recherche ne peut être appliquée. Si vous définissez la règle par défaut sur &quot;Le plus acheté&quot;, toutes les requêtes seront par défaut de ce type de classement, sauf si elles sont supercédées par un terme de recherche plus spécifique. Aucun terme de recherche ne peut être défini pour la règle par défaut.

## Ordre de priorité avec plusieurs règles

Une seule règle de recherche est appliquée à un terme de recherche à la fois.
Si plusieurs règles s’appliquent à une expression de recherche, toutes ces règles sont appliquées. En cas de collision entre deux règles, `rule 1` qui amplifie sku1 mais `rule 2` masque le même SKU, alors la règle la plus récemment appliquée (`rule 2`) est prioritaire.

* Les règles sont classées selon l’horodatage &quot;Dernière modification&quot;. La règle la plus récemment modifiée est appliquée en premier, puis les règles plus anciennes, dans l’ordre d’horodatage.
* La condition `query is` a la priorité sur les autres conditions. Si une règle plus récente contient une condition `query contains`, mais qu’une règle plus ancienne comporte une condition `query is`, la règle `query is` est appliquée.

### Demandes Storefront

Si une règle active contenant une condition `query is` correspond à l’expression recherchée, elle est appliquée. S’il existe plusieurs règles correspondantes avec une condition `query is`, la règle active la plus récemment mise à jour est appliquée.
Dans le cas contraire, la règle active mise à jour le plus récemment est appliquée.

### Aperçu des requêtes

Les requêtes effectuées dans l’administrateur fonctionnent légèrement différemment. Lors de la prévisualisation dans l’administrateur, toutes les règles sont appliquées, y compris celles qui ont expiré et planifiées.

* Si la règle en cours de prévisualisation a une condition `query is`, elle est appliquée.
* Si la règle en cours de prévisualisation n’a pas de condition `query is` et qu’une règle active correspondante ultérieure avec une condition `query is` est trouvée, la règle `query is` est appliquée.
* Si la règle en cours de prévisualisation n’a pas de condition `query is` et qu’aucune autre règle avec une condition `query is` n’est trouvée, alors la règle en cours de prévisualisation est appliquée.

## Marchandisage des catégories et affectations de produits de catégorie

[!DNL Live Search] vous permet de filtrer par catégories. Pour plus d’informations, voir [Marchandisage par catégorie](category-merch.md) .
Cependant, dans Adobe Commerce, vous pouvez créer une catégorie virtuelle avec des [affectations de produits de catégorie](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/products-in-category/categories-product-assignments.html). Ce type de catégorie est créé au moment de l’exécution et n’existe pas dans la base de données des catégories. Par conséquent, [!DNL Live Search] ne peut pas lire ni utiliser ce type de catégorie.
