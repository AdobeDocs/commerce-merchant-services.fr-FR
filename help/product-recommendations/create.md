---
title: Créer une recommandation
description: Découvrez comment créer une unité de recommandation de produit.
exl-id: d393ab78-0523-463f-9b03-ad3f523dce0f
source-git-commit: 0d6e935fc5812efd7d3359a4fa242f8d5d85043e
workflow-type: tm+mt
source-wordcount: '1497'
ht-degree: 0%

---

# Créer une recommandation

Lorsque vous créez une recommandation, vous créez une _unité de recommandation_, ou widget, qui contient les _éléments_ recommandés.

![Unité de recommandation](assets/unit.png)
_Unité de recommandation_

Lorsque vous activez l’unité de recommandation, Adobe Commerce commence à [collecter des données](workspace.md) pour mesurer les impressions, les vues, les clics, etc. Le tableau [!DNL Product Recommendations] affiche les mesures de chaque unité de recommandations afin de vous aider à prendre des décisions professionnelles éclairées.

>[!NOTE]
>
>Les mesures de recommandation de produit sont optimisées pour les vitrines Luma. Si votre vitrine n’est pas basée sur Luma, la façon dont les mesures effectuent le suivi des données dépend de la manière dont vous [ implémentez la collection d’événements](events.md).

1. Sur la barre latérale _Admin_, accédez à **Marketing** > _Promotions_ > **Recommendations de produit** pour afficher l’espace de travail _Recommendations de produit_.

1. Spécifiez la [vue Boutique](https://experienceleague.adobe.com/en/docs/commerce-admin/start/setup/websites-stores-views) où afficher les recommandations.

   >[!NOTE]
   >
   > Les unités de recommandation du Créateur de pages doivent être créées dans la vue de magasin par défaut, mais peuvent ensuite être utilisées n’importe où. Pour en savoir plus sur la création de recommandations de produits avec Page Builder, voir [Ajout de contenu - Recommendations produit](https://experienceleague.adobe.com/en/docs/commerce-admin/page-builder/add-content/recommendations).

1. Cliquez sur **Créer une recommandation**.

1. Dans la section _Nommez votre recommandation_ , saisissez un nom descriptif pour la référence interne, tel que `Home page most popular`.

1. Dans la section _Sélectionner le type de page_ , sélectionnez la page sur laquelle vous souhaitez que la recommandation apparaisse parmi les options suivantes :

   >[!NOTE]
   >
   > Les Recommendations de produit ne sont pas pris en charge sur la page Panier lorsque votre boutique est configurée pour [ afficher la page du panier immédiatement après l’ajout d’un produit au panier ](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/point-of-purchase/cart/cart-configuration).

   * Page d’accueil
   * Catégorie
   * Détails du produit
   * Panier
   * Confirmation
   * [Page Builder](https://experienceleague.adobe.com/en/docs/commerce-admin/page-builder/add-content/recommendations)

   Vous pouvez créer jusqu’à cinq unités de recommandations actives pour chaque type de page et jusqu’à 25 unités pour le Créateur de pages. Le type de page est grisé Lorsque la limite est atteinte.

   ![Nom de la recommandation et page](assets/create-recommendation.png)
   _Nom de la recommandation et emplacement de la page_

1. Dans la section _Sélectionner le type de recommandation_ , spécifiez le [type de recommandation](type.md) que vous souhaitez afficher sur la page sélectionnée. Pour certaines pages, le [placement](placement.md) des recommandations est limité à certains types.

1. Dans la section _Étiquette d’affichage de Storefront_ , saisissez le [libellé](placement.md#recommendation-labels) visible par vos acheteurs, tel que &quot;Meilleurs vendeurs&quot;.

1. Dans la section _Choisir le nombre de produits_ , utilisez le curseur pour spécifier le nombre de produits à afficher dans l’unité de recommandation.

   La valeur par défaut est `5`, avec un maximum de `20`.

1. Dans la section _Sélectionner un emplacement_ , indiquez l’emplacement où l’unité de recommandation doit apparaître sur la page.

   * Au bas du contenu principal
   * En haut du contenu principal

1. (Facultatif) Pour modifier l’ordre des recommandations, sélectionnez et déplacez les lignes dans la table _Choisir la position_.

   La section _Choisir la position_ affiche toutes les recommandations (le cas échéant) créées pour le type de page que vous avez sélectionné.

   ![Ordre de recommandation](assets/create-recommendation-select-placement.png)
   _Ordre de recommandation sur la page_

1. (Facultatif) Dans la section _Filtres_, [appliquez des filtres](filters.md) pour contrôler les produits qui apparaissent dans l’unité de recommandation.

   ![Filtres de recommandation](assets/create-recommendation-filter-products.png)
   _Filtres de produits de recommandation_

1. Une fois l’opération terminée, cliquez sur l’une des options suivantes :

   * **Enregistrer en tant que brouillon** pour modifier ultérieurement l’unité de recommandation. Vous ne pouvez pas modifier le type de page ou de recommandation d’une unité de recommandation dans un état de brouillon.

   * **Activez** pour activer l’unité de recommandation sur votre vitrine.

## Indicateurs de préparation

Les indicateurs de préparation indiquent les types de recommandations les plus performants en fonction du catalogue et des données comportementales disponibles. Vous pouvez également utiliser des indicateurs de préparation pour déterminer si vous rencontrez des problèmes avec votre [événement](events.md) ou si vous n’avez pas assez de trafic pour renseigner le type de recommandation.

Les indicateurs de préparation sont classés dans [basé sur la statique](#static-based) ou [basé sur la dynamique](#dynamic-based). Les données du catalogue basées sur la statique utilisent uniquement les données du catalogue, tandis que les données comportementales dynamiques utilisent les données de vos acheteurs. Ces données comportementales sont utilisées pour [former des modèles d’apprentissage automatique](events.md) afin de créer des recommandations personnalisées et de calculer leur score de préparation.

### Méthode de calcul des indicateurs de préparation

Les indicateurs de préparation indiquent la formation du modèle. Les indicateurs dépendent des types d’événements collectés, de la largeur des produits interactifs et de la taille du catalogue.

Le pourcentage de l’indicateur de préparation est dérivé d’un calcul qui indique le nombre de produits recommandés en fonction du type de recommandation. Les statistiques sont appliquées aux produits en fonction de la taille globale du catalogue, du volume des interactions (vues, clics, ajouts au panier, etc.) et du pourcentage de SKU qui enregistrent ces événements dans une certaine période. Par exemple, pendant le trafic de haute saison des fêtes, les indicateurs de préparation peuvent afficher des valeurs plus élevées que lors des périodes de volume normal.

En raison de ces variables, le pourcentage de l’indicateur de préparation peut fluctuer. Cela explique pourquoi il se peut que les types de recommandations apparaissent et sortent du statut &quot;Prêt pour le déploiement&quot;.

Les indicateurs de préparation sont calculés sur la base de deux facteurs :

* Taille de jeu de résultats suffisante : y a-t-il suffisamment de résultats renvoyés dans la plupart des scénarios pour éviter d’utiliser [recommandations de sauvegarde](events.md#backuprecs) ?

* Suffisante variété d’ensembles de résultats : les produits renvoyés représentent-ils une variété de produits de votre catalogue ? L’objectif de ce facteur est d’éviter qu’une minorité de produits soit le seul élément recommandé sur l’ensemble du site.

En fonction des facteurs ci-dessus, une valeur de préparation est calculée et affichée comme suit :

* 75 % ou plus signifie que les recommandations proposées pour ce type de recommandation seront très pertinentes.
* Au moins 50 % signifie que les recommandations proposées pour ce type de recommandation seront moins pertinentes.
* Moins de 50 % signifie que les recommandations suggérées pour ce type de recommandation peuvent ne pas être pertinentes. Dans ce cas, [recommandations de sauvegarde](events.md#backuprecs) sont utilisées.

En savoir plus sur [pourquoi les indicateurs de préparation peuvent être faibles](#what-to-do-if-the-readiness-indicator-percent-is-low).

### Statique

Les types de recommandations suivants sont statiques, car ils ne nécessitent que des données de catalogue. Aucune donnée comportementale n’est utilisée.

* _Plus comme ceci_
* _Similarité visuelle_

### Basé sur Dynamic

Les types de recommandations suivants sont dynamiques, car ils utilisent des données comportementales storefront.

Les six derniers mois de données comportementales de storefront :

* _A consulté ceci, a consulté cela_
* _A consulté ceci, a acheté cela_
* _Acheté ceci, acheté cela_
* _Recommandé pour vous_

Les sept derniers jours des données comportementales du storefront :

* _Le plus consulté_
* _Le plus acheté_
* _Le plus ajouté au panier_
* _Trending_
* _Afficher pour acheter la conversion_
* _Conversion de l’affichage dans le panier_

Données comportementales du nouvel acheteur (vues uniquement) :

* _Récemment consultés_

### Visualiser la progression

Pour vous aider à visualiser la progression de la formation de chaque type de recommandation, la section _Sélectionner le type de recommandation_ affiche une mesure de la préparation pour chaque type.

![Type de recommandation](assets/create-recommendation-select-type.png)
_Type de recommandation_

>[!NOTE]
>
>Les indicateurs peuvent ne jamais atteindre 100 %.

Le pourcentage de l’indicateur de préparation pour les types de recommandations qui dépendent des données du catalogue ne change pas beaucoup, car le catalogue du commerçant ne change pas souvent. Mais le pourcentage de l’indicateur de préparation pour les types de recommandations basé sur les données comportementales des acheteurs peut changer souvent en fonction de l’activité quotidienne des acheteurs.

#### Que faire si le pourcentage de l’indicateur de préparation est faible

Un pourcentage de faible préparation indique qu’il n’y a pas beaucoup de produits de votre catalogue qui peuvent être inclus dans les recommandations pour ce type de recommandation. Cela signifie qu’il existe une forte probabilité que [recommandations de sauvegarde](events.md#backuprecs) soient renvoyées si vous déployez ce type de recommandation de toute façon.

>[!IMPORTANT]
>
>Les types de produits _Bundle_, _groupé_ et personnalisés ne sont pas pris en charge. Si votre catalogue contient un grand nombre de ces types de produits, vous pouvez vous attendre à un faible taux de préparation. En outre, les SKU avec espaces peuvent réduire la pertinence des recommandations et doivent être évités.

Vous trouverez ci-dessous les raisons possibles et les solutions aux scores de faible niveau de préparation courants :

* **Static-based** - De faibles pourcentages pour ces indicateurs peuvent être causés par l’absence de données de catalogue pour les produits affichables. S’ils sont inférieurs aux attentes, une synchronisation complète peut résoudre ce problème.
* **Dynamique** - Les faibles pourcentages pour les indicateurs dynamiques peuvent être causés par :

   * Champs manquants dans les [événements storefront](events.md) requis pour les types de recommandations respectifs (requestId, product context, etc.)
   * Le faible trafic sur le magasin de sorte que le volume d’événements comportementaux que nous recevons est faible.
   * La variété d’événements comportementaux de storefront sur différents produits de votre magasin est faible. Par exemple, si seulement dix pour cent de vos produits sont consultés ou achetés la plupart du temps, les indicateurs de préparation respectifs seront faibles.

## Aperçu de Recommendations {#preview}

Le panneau _Aperçu des produits recommandés_ est toujours disponible avec un exemple de sélection de produits qui peuvent apparaître dans l’unité de recommandation lorsqu’elle est déployée sur le storefront.

Pour tester une recommandation lorsque vous travaillez dans un environnement hors production, vous pouvez récupérer les données de recommandation d’une [source différente](settings.md). Cela permet aux commerçants d’expérimenter des règles et de prévisualiser les recommandations avant leur déploiement en production.

| Champ | Description |
|---|---|
| Nom | Nom du produit. |
| SKU | Unité de gestion des stocks affectée au produit |
| Prix | Le prix du produit. |
| Type de résultat | Principal : indique qu’il existe suffisamment de données de formation pour afficher une recommandation.<br />Sauvegarde : indique qu’il n’y a pas suffisamment de données d’entraînement collectées. Une recommandation de sauvegarde est donc utilisée pour remplir l’emplacement. Accédez à [Données comportementales](events.md) pour en savoir plus sur les modèles d’apprentissage automatique et les recommandations de sauvegarde. |

À mesure que vous créez votre unité de recommandations, testez le type de page, le type de recommandation et les filtres pour obtenir des commentaires en temps réel immédiats sur les produits qui seront inclus. Lorsque vous commencez à comprendre les produits qui apparaissent, vous pouvez configurer l’unité de recommandations en fonction des besoins de votre entreprise.

Recommandations d’Adobe Commerce [filtres](filters.md) pour éviter d’afficher des produits en double lorsque plusieurs unités de recommandations sont déployées sur une seule page. Par conséquent, les produits qui apparaissent dans le panneau d’aperçu peuvent différer de ceux qui apparaissent dans le storefront.

>[!NOTE]
>
> Vous ne pouvez pas prévisualiser le type de recommandation `Recently viewed`, car les données ne sont pas disponibles dans l’administrateur.
