---
title: "Ajouter des règles"
description: "Découvrez comment créer [!DNL Live Search] règles."
exl-id: c6b92ef5-3b08-47f9-8412-955a9c95a9ee
source-git-commit: 3d0de3eeb4aa96c996bc9fa38cffd7597e89e7ca
workflow-type: tm+mt
source-wordcount: '1290'
ht-degree: 0%

---

# Ajout de règles

Pour créer une règle, la première étape consiste à utiliser l’éditeur de règles pour définir les conditions dans le texte de requête de l’acheteur qui déclenchent les événements associés. Renseignez ensuite les détails de la règle, testez les résultats et publiez la règle.

## Étape 1 : Ajouter une règle

1. Dans Admin, accédez à **Marketing** > SEO &amp; Search > **Recherche en direct**.
1. Définissez la variable **Portée** pour identifier la variable [vue de magasin](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) lorsque la règle s’applique.
1. Cliquez sur le bouton **Règles** .
1. Cliquez sur **Ajouter une règle** pour lancer l’éditeur de règles.

   ![Espace de travail des règles](assets/rules-workspace-add-rule.png)

## Étape 2 : Description des conditions

Les conditions sont les conditions requises pour déclencher un événement. Une règle peut comporter jusqu’à dix conditions et 25 événements.

![Règle - Créer votre règle](assets/rules-add-workspace.png)

### Condition unique

1. Sous *Créer votre règle*, sélectionnez la variable **Condition** et suivez les instructions pour remplir l’instruction .

   * Requête de recherche contenant : entrez la chaîne de texte qui doit se trouver dans la requête de l’acheteur. Le paramètre Correspondance détermine le degré auquel la requête de l’acheteur correspond au catalogue. Options :<br /> N’importe lequel : toute partie du texte de requête de l’acheteur peut correspondre à la condition.<br />Tous : toutes les requêtes de l’acheteur doivent correspondre à la condition .
   * La requête de recherche est : entrez une chaîne de texte correspondant exactement à la requête de l’acheteur. Par exemple : &quot;pantalon de yoga&quot;. Règles avec `Search query is` et Correspondance `All` ne peut comporter qu’une seule condition.
   * La requête de recherche commence par : saisissez un caractère ou une chaîne de texte qui doit se trouver au début de la requête du client.
   * La requête de recherche se termine par : saisissez un caractère ou une chaîne de texte qui doit se trouver à la fin de la requête du client.

   Les résultats apparaissent immédiatement dans la variable *Tester votre règle* et sont numérotés par priorité. Vous pouvez utiliser la variable *Résultats par ligne* curseur dans le coin supérieur droit pour modifier le nombre de produits dans chaque ligne.

   ![Règle - simple](assets/rule-simple-test.png)

1. Pour tester d’autres requêtes, modifiez le texte de la requête dans la variable *Tester votre règle* zone de recherche et appuyez sur **Retour**.
Au départ, le volet de test effectue le rendu de la requête à partir de la zone de recherche Conditions. Mais maintenant, la requête est rendue à partir de la boîte de requête de test. Le volet de test effectue le rendu d’une seule requête à la fois.

   ![Règle - Test de mise à jour](assets/rule-update-test.png)

1. Si vous souhaitez le résultat, mettez à jour le texte dans la variable *Conditions* zone de recherche. Cliquez ensuite n’importe où sur la page pour mettre à jour les résultats dans le volet de test.
1. Pour créer une règle simple avec une condition, accédez à l’étape 3 : [Ajout d’événements](#events).

### Conditions multiples

1. Pour créer une règle avec plusieurs conditions, cliquez sur **Ajouter une condition**.
Une règle peut comporter jusqu&#39;à dix conditions. L’opérateur logique qui rejoint deux conditions est basé sur la condition actuelle *Correspondance* . Par défaut, *Correspondance* is `All` et l’opérateur logique est `AND`.

   ![Règles : la requête de recherche contient](assets/rules-search-query-contains-and.png)

1. Sélectionnez la seconde condition et saisissez le texte de la requête.

   ![Conditions de règle](assets/rules-add-condition.png)

1. Pour modifier la logique de la règle, modifiez la variable **Correspondance** pour déterminer dans quelle mesure les critères de recherche de l’acheteur doivent correspondre à la condition de requête. Définir **Correspondance** à l’une des options suivantes :

   * Any - (par défaut) Tous les opérateurs logiques de la règle sont définis sur `OR` et les résultats apparaissent dans le volet test.
   * Tous : tous les opérateurs logiques de la règle sont définis sur `AND` et les résultats apparaissent dans le volet test.

   Le *Correspondance* détermine l’opérateur logique utilisé pour joindre plusieurs conditions. Changement de la variable *Correspondance* modifie tous les opérateurs logiques de la règle. Il n’est pas possible de combiner des `AND` et `OR` dans la même règle.

   Dans cet exemple, plutôt que de rechercher &quot;pantalon de yoga&quot;, il existe deux requêtes distinctes qui recherchent &quot;yoga&quot; ou &quot;pantalon&quot;. Cette règle est moins spécifique et est déclenchée plus souvent dans le storefront que l’autre.

   ![Règles - Correspondance](assets/rules-match.png)

1. Pour ajouter une autre condition, cliquez sur **Ajouter une condition** et répétez le processus.

## Étape 3 : Ajout d’événements

Les événements sont des actions qui modifient les résultats de la recherche lorsque les conditions sont remplies. Une seule règle peut comporter jusqu’à 25 événements.

1. Sous *Événements*, choisissez la variable **Événement** à se produire lorsque les conditions associées sont remplies.

   Par exemple, choisissez `Pin a product`. Saisissez ensuite le nom du produit à épingler. Si vous avez besoin d’aide, vous pouvez trouver le nom dans le volet de test.
Ensuite, saisissez le *Position* où le produit épinglé doit apparaître. Le produit est déplacé vers la nouvelle position dans le volet de test et est marqué d’une mention *Pindu* badge aperçu.

   ![Règles - Correspondance](assets/rule-event-pin-product.png)

1. Pour plusieurs événements, choisissez les autres événements à déclencher lorsque les conditions sont remplies.

   * Amplifier - Sélectionnez Amplifier. Ensuite, saisissez le nom du produit ou le SKU que vous souhaitez déplacer plus haut dans les résultats de recherche. Dans le volet de test, chaque produit dopé comporte une *Booaded* badge aperçu.
   * Bury : déplace un SKU plus bas dans les résultats de recherche. Chaque SKU est marqué par une *Enterré* badge d’aperçu dans le volet test.
   * Épingler un produit : saisissez le nom du produit ou le SKU. Sélectionnez ensuite la Position dans les résultats de recherche où le produit doit apparaître. Le produit est marqué d’une *Pindu* badge d’aperçu dans le volet test.
   * Masquer un produit : exclut un SKU des résultats de recherche.

## Étape 4 : Compléter les détails

Les informations saisies ici apparaissent dans le [Détails de la règle](rules-workspace.md) du panneau.

1. Sous *Détails*, saisissez une **Nom** pour la règle. Tous les noms de règle doivent être uniques.
1. Entrez un résumé **Description** de la règle.
1. Saisissez le **Date de début** et **Date de fin** pour que la règle soit principale ou sélectionnez les dates du calendrier.

   Pour sélectionner une plage de dates, cliquez sur la première date et faites glisser le curseur pour la sélectionner.

   ![Règle - Terminé](assets/rule-add-details.png)

## Étape 5 : Tester la règle

1. Examinez les résultats de la règle dans le volet de test.
1. Si la règle comporte plusieurs requêtes, testez chacune d’elles susceptibles d’être affectées par la règle.

## Étape 6 : Enregistrer et publier

1. Une fois l’opération terminée, cliquez sur **Enregistrer et publier**.

   La règle est ajoutée à la liste dans l’espace de travail des règles.

1. Bien que les principales règles entrent immédiatement en vigueur, vous devrez peut-être attendre jusqu’à 15 minutes que les résultats de la requête mise en cache dans le storefront soient actualisés.

## Descriptions des champs

### Conditions (si)

| Condition | Description |
|--- |--- |
| La requête de recherche contient | Caractère ou chaîne de texte inclus dans la requête de l’acheteur. La requête du client ne doit correspondre qu’à un seul caractère pour remplir cette condition. |
| La requête de recherche est | Caractère ou chaîne de texte correspondant exactement à la requête de l’acheteur. Les requêtes complexes avec plusieurs conditions ne peuvent pas être composées lorsque cette condition est utilisée. |
| La requête de recherche commence par | La requête de l’acheteur commence par ce caractère ou cette chaîne de texte. |
| La requête de recherche se termine par | La requête de l’acheteur se termine par ce caractère ou cette chaîne de texte. |

### Opérateurs logiques

| Opérateur | Description |
|--- |--- |
| OU | (Par défaut) L’opérateur logique `OR` compare deux conditions et répond aux exigences afin de déclencher un événement si au moins une condition est vraie. |
| ET | Opérateur logique `AND` compare deux conditions et répond aux exigences afin de déclencher un événement si les deux conditions sont vraies. |

### Opérateurs de correspondance

| Opérateur | Description |
|--- |--- |
| Quelconque | Modifie tous les opérateurs logiques de la règle en `OR` et renvoie l’ensemble des produits correspondants. |
| Tous | Modifie tous les opérateurs logiques de la règle en `AND` et renvoie l’ensemble des produits correspondants. |

### Événements

| Événement | Description |
|--- |--- |
| Amplifier | Déplace un SKU ou une plage de SKU plus haut dans les résultats de recherche. Chacun d’eux est marqué d’un badge d’aperçu &quot;rechargé&quot; dans les résultats de recherche du test. |
| Bury | Déplace un SKU ou une plage de SKU vers le bas dans les résultats de recherche. Chacun est marqué d’un badge d’aperçu &quot;enterré&quot; dans les résultats de recherche du test. |
| Epinglage d’un produit | Associe un seul SKU à une position spécifique dans les résultats de recherche. Le produit est marqué d’un badge d’aperçu &quot;épinglé&quot; dans les résultats de la recherche de test. |
| Masquer un produit | Exclut un SKU, ou une plage de SKU, des résultats de recherche. |

### Détails

| Champ | Description |
|--- |--- |
| Nom | Nom de la règle. Les noms des règles doivent être uniques. |
| Date de début | Date de début de la règle, le cas échéant. |
| Date de fin | Date de fin de la règle, le cas échéant. |
| Description | Brève description de la règle. |
