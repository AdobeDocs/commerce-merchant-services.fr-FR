---
title: "Règles"
description: "[!DNL Live Search] les règles combinent logique et actions pour façonner l’expérience d’achat."
exl-id: d06a3040-6987-4813-90ae-2f7b3ad0b232
source-git-commit: 941fdc25f93679593cb3c5db0d29d7a561fcce58
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 0%

---

# Règles

[!DNL Live Search] les règles combinent logique et actions pour former l’expérience de recherche d’un acheteur dans votre magasin. Vous pouvez utiliser des règles pour dynamiser, enterrer, épingler ou masquer des produits afin d’étalonner les résultats de recherche en temps réel en fonction des objectifs de votre entreprise.

Chaque règle comporte trois composants principaux :

* Conditions : conditions qui déclenchent une action.
* Événements : actions qui se produisent lorsque les conditions sont remplies.
* Détails : nom de la règle, période et description facultative.

Vous pouvez combiner plusieurs conditions et actions et planifier une règle pour qu’elle soit principale pendant une période.

## Conditions

Une règle simple peut comporter une seule condition et un seul événement, tandis qu’une règle complexe peut comporter jusqu’à dix conditions qui déclenchent jusqu’à 25 événements.
Les règles peuvent comporter :

* Jusqu’à dix conditions
* Jusqu’à 25 événements

Le texte de la requête peut contenir :

* Caractères alphanumériques (lettres et chiffres)
* Caractères majuscules ou minuscules. La mise en majuscule est ignorée.

## Opérateurs logiques

Les opérateurs logiques `AND` et `OR` joignez deux conditions et renvoyez des résultats différents. Tous les opérateurs logiques utilisés dans une règle avec plusieurs conditions sont identiques. Il n’est pas possible d’utiliser les deux `AND` et `OR` dans la même règle.

### Opérateurs de correspondance

Les opérateurs Correspondance `All` et `Any` déterminer l’opérateur logique utilisé pour associer plusieurs conditions dans la règle et qui peut être utilisé pour modifier l’opérateur existant ;

* `All` - Utilise la variable `AND` opérateur logique pour joindre plusieurs conditions. Une règle qui utilise la variable `All` L’opérateur de correspondance ne peut avoir qu’un seul `Search query is` condition.
* `Any` - Utilise la variable `OR` opérateur logique pour joindre plusieurs conditions.

Lors de la composition d’une règle complexe, il peut être utile de l’écrire avec une mise en retrait pour décrire les conditions, les événements associés, les noms de produits ou les SKU nécessaires pour renvoyer les résultats que vous souhaitez obtenir. Ensuite, créez la règle et testez le résultat.
