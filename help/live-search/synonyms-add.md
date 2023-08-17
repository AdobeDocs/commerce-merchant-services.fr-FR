---
title: "Add Synonyms"
description: "Ajouter [!DNL Live Search] synonymes pour améliorer la réponse aux requêtes de recherche."
exl-id: 6c277d88-cb22-4174-abda-6d6bb65fe3be
source-git-commit: c4bca0c7238be653dd13b051634c662e5891767d
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# Ajouter des Synonymes

Augmentez l’engagement des clients en ajoutant votre propre liste organisée de [!DNL Live Search] synonymes. [!DNL Live Search] peut gérer jusqu’à 200 synonymes par `Data Space ID`.

![[!DNL Live Search] synonyms](assets/synonym-workspace.png)

## Étape 1 : Ajouter un synonyme

1. Dans Admin, accédez à **Marketing** > SEO &amp; Search > **[!DNL Live Search]**.
1. Pour plusieurs magasins, définissez **Portée** à la fonction [vue de magasin](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) où les paramètres de synonyme s’appliquent.
1. Cliquez sur le bouton **Synonymes** .
1. Cliquez sur le bouton **Ajouter des synonymes** bouton .

## Etape 2 : définir le synonyme par type

Suivez les instructions de la section [type de synonyme](synonyms-type.md) que vous souhaitez créer.

### synonyme bidirectionnel

1. Acceptation de la valeur par défaut **À double sens** .

   ![Ajouter un synonyme bidirectionnel](assets/synonym-add-two-way.png)


1. Saisissez le **Mot-clé** terme ou expression à mettre en correspondance.
1. Saisissez le **Extension** terme(s) que vous souhaitez ajouter en tant que synonymes pour le mot-clé. Séparez plusieurs termes par une virgule.
Dans cet exemple, le mot-clé à associer est &quot;pantalon&quot; et l’ensemble de termes d’extension est &quot;pantalon long, pantalon, pantalon&quot;.

   ![Exemple de synonyme bidirectionnel](assets/synonym-add-two-way-example.png)

1. Lorsque vous avez terminé, cliquez sur **Enregistrer**.
L’ensemble de synonymes apparaît dans la liste avec une flèche bidirectionnelle entre chaque terme, ce qui signifie que les termes sont interchangeables.

   ![synonyme bidirectionnel](assets/synonym-two-way.png)

### Un synonyme unidirectionnel

1. Cliquez sur le bouton **A sens unique** type de synonyme.

   ![Ajout d’un synonyme unidirectionnel](assets/synonym-add-one-way.png)

1. Saisissez le **Mot-clé** et **Extension** termes. Séparez plusieurs termes par une virgule.

   ![Exemple de synonyme unidirectionnel](assets/synonym-add-one-way-example.png)

   Dans cet exemple, le mot-clé est &quot;pantalon&quot; et les termes d’extension unidirectionnelle &quot;capris, pantalon-length, pédophiles&quot; sont tous deux un sous-ensemble de &quot;pantalons&quot;, mais avec une signification spécifique.

1. Lorsque vous avez terminé, cliquez sur **Enregistrer**.
L’ensemble de synonymes apparaît dans la liste avec une flèche à sens unique indiquant les termes d’extension au mot-clé afin d’indiquer que les termes sont des sous-ensembles du mot-clé. Un signe plus sépare chaque terme d’extension.

   ![Un synonyme unidirectionnel](assets/synonym-one-way.png)

## Étape 3 : Publier les modifications

1. Une fois vos synonymes terminés, cliquez sur **Publier les modifications**.
1. Patientez jusqu’à deux heures pour que vos mises à jour soient disponibles dans le storefront.

## Descriptions des champs

| Champ | Description |
|--- |--- |
| [Type](synonyms.md) | Détermine si les synonymes ont la même signification que le mot-clé ou s’ils sont un sous-ensemble du mot-clé. Options :<br />bidirectionnel (par défaut) : termes ayant la même signification que le mot-clé et renvoyant les mêmes résultats de recherche<br />A sens unique : termes qui sont un sous-ensemble du mot-clé. Les synonymes unidirectionnels renvoient une liste plus étroite de produits spécifiques. |
| Mot-clé | Mot généralement associé à une sélection de produits de votre catalogue. |
| Extension | Termes supplémentaires ayant la même signification ou la même signification que le mot-clé. |
