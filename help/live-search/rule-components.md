---
title: "Composants de règle"
description: "En savoir plus sur [!DNL Live Search] composants de règle et opérateurs."
exl-id: 4065aec3-a8d4-4d55-b939-16ad7b0f33ee
source-git-commit: 0a1d70465247422db44daee302c67fe1a5a29d32
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---

# Composants de règle

Une règle décrit les conditions requises pour déclencher des événements qui modifient les résultats de recherche renvoyés en réponse à la requête d’un acheteur.

## Conditions

Une règle simple peut comporter une seule condition et un seul événement, tandis qu’une règle complexe peut comporter jusqu’à dix conditions qui déclenchent jusqu’à 25 événements.
Les règles peuvent comporter :

* Jusqu’à dix conditions
* Jusqu’à 25 événements

Le texte de la requête peut contenir :

* Caractères alphanumériques (lettres et chiffres)
* Caractères majuscules ou minuscules

## Opérateurs logiques

Les opérateurs logiques `AND` et `OR` joignez deux conditions et renvoyez des résultats différents. Tous les opérateurs logiques utilisés dans une règle avec plusieurs conditions sont identiques. Il n’est pas possible d’utiliser les deux `AND` et `OR` dans la même règle.

### Opérateurs de correspondance

Les opérateurs Correspondance `All` et `Any` déterminer l’opérateur logique utilisé pour associer plusieurs conditions dans la règle et qui peut être utilisé pour modifier l’opérateur existant ;

* `All` - Utilise la variable `AND` opérateur logique pour joindre plusieurs conditions. Une règle qui utilise la variable `All` L’opérateur de correspondance ne peut avoir qu’un seul `Search query is` condition.
* `Any` - Utilise la variable `OR` opérateur logique pour joindre plusieurs conditions.

Lors de la composition d’une règle complexe, il peut être utile de l’écrire avec une mise en retrait pour décrire les conditions, les événements associés, les noms de produits ou les SKU nécessaires pour renvoyer les résultats que vous souhaitez obtenir. Ensuite, créez la règle et testez le résultat.
