---
title: Créer une recommandation
description: Découvrez comment créer une unité de recommandation de produit.
exl-id: d393ab78-0523-463f-9b03-ad3f523dce0f
source-git-commit: 51ff52eba117fe438d592ca886dbca25304a0d15
workflow-type: tm+mt
source-wordcount: '1022'
ht-degree: 0%

---

# Créer une recommandation

Lorsque vous créez une recommandation, vous créez une _unité de recommandation_ qui contient le produit recommandé _items_.

![Unité de recommandation](assets/unit.png)
_Unité de recommandation_

Lorsque vous activez l’entité de recommandation, Adobe Commerce commence à [collecter des données](workspace.md) pour mesurer les impressions, les vues, les clics, etc. La variable [!DNL Product Recommendations] le tableau affiche les mesures de chaque unité de recommandations afin de vous aider à prendre des décisions professionnelles éclairées.

1. Sur le _Administration_ barre latérale, accédez à **Marketing** > _Promotions_ > **Recommendations de produit** pour afficher la variable _Recommendations de produit_ workspace.

1. Spécifiez la variable [Affichage en magasin](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) où vous souhaitez que les recommandations s’affichent.

   >[!NOTE]
   >
   > Les unités de recommandation du Créateur de pages doivent être créées dans la vue de magasin par défaut, mais peuvent ensuite être utilisées n’importe où. Pour en savoir plus sur la création de recommandations de produits avec le générateur de pages, voir [Ajouter du contenu - Recommendations de produit](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html).

1. Cliquez sur **Créer une recommandation**.

1. Dans le _Nommer votre recommandation_ , saisissez un nom descriptif pour la référence interne, tel que `Home page most popular`.

1. Dans le _Sélectionner le type de page_ , sélectionnez la page sur laquelle vous souhaitez que la recommandation apparaisse dans les options suivantes :

   >[!NOTE]
   >
   > Les Recommendations de produit ne sont pas pris en charge sur la page Panier lorsque votre boutique est configurée pour [afficher la page Panier immédiatement après l’ajout d’un produit au panier ;](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/cart/cart-configuration.html#redirect-to-cart).

   * Page d’accueil
   * Catégorie
   * Détails du produit
   * Panier
   * Confirmation
   * [Page Builder](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html)

   Vous pouvez créer jusqu’à cinq unités de recommandations actives pour chaque type de page et jusqu’à 25 unités pour le Créateur de pages. Le type de page est grisé Lorsque la limite est atteinte.

   ![Nom et page de la recommandation](assets/create-recommendation.png)
   _Nom de la recommandation et placement de page_

1. Dans le _Sélectionner le type de recommandation_ , spécifiez la variable [type de recommandation](type.md) vous souhaitez afficher la page sélectionnée. Pour certaines pages, la variable [placement](placement.md) de recommandations est limitée à certains types.

1. Dans le _Libellé d’affichage de la vitrine_ , saisissez la [label](placement.md#recommendation-labels) qui est visible par vos acheteurs, par exemple &quot;Meilleurs vendeurs&quot;.

1. Dans le _Choisir le nombre de produits_ , utilisez le curseur pour spécifier le nombre de produits à afficher dans l’unité de recommandation.

   La valeur par défaut est `5`, avec un maximum de `20`.

1. Dans le _Sélectionner un emplacement_ , indiquez l’emplacement d’affichage de l’unité de recommandation sur la page.

   * Au bas du contenu principal
   * En haut du contenu principal

1. (Facultatif) Pour modifier l’ordre des recommandations, sélectionnez et déplacez les lignes dans la variable _Choisir la position_ table.

   La variable _Choisir la position_ affiche toutes les recommandations (le cas échéant) créées pour le type de page que vous avez sélectionné.

   ![Ordre de recommandation](assets/create-recommendation-select-placement.png)
   _Ordre de recommandation sur la page_

1. (Facultatif) Dans la variable _Filtres_ , [appliquer des filtres ;](filters.md) pour contrôler les produits qui apparaissent dans l’unité de recommandation.

   ![Filtres de recommandations](assets/create-recommendation-filter-products.png)
   _Filtres de produits de recommandation_

1. Une fois l’opération terminée, cliquez sur l’une des options suivantes :

   * **Enregistrer en tant que brouillon** pour modifier ultérieurement l’unité de recommandation. Vous ne pouvez pas modifier le type de page ou de recommandation d’une unité de recommandation dans un état de brouillon.

   * **Activer** pour activer l’unité de recommandation sur votre vitrine.

## Indicateurs de préparation

Certains types de recommandations utilisent les données comportementales de vos acheteurs pour [former des modèles d’apprentissage automatique ;](behavioral-data.md) pour créer des recommandations personnalisées.

Nécessite uniquement des données de catalogue. Aucune donnée comportementale n’est nécessaire pour les éléments suivants :

* _Le plus apprécié_
* _Récemment consultés_
* _Similarité visuelle_

Sur la base des six derniers mois des données comportementales du storefront :

* _A consulté ceci, consulté cela_
* _Consulté ceci, acheté cela_
* _Acheté ceci, acheté cela_
* _Recommandé pour vous_

Les types de recommandations basés sur la popularité utilisent les sept derniers jours des données comportementales du storefront :

* Les plus consultés
* Le plus acheté
* Ajout au panier
* Tendance

Les valeurs des indicateurs de préparation devraient fluctuer en raison de facteurs tels que la taille globale du catalogue, le volume des événements d’interaction du produit (vues, ajouts au panier, achats) et le pourcentage de SKU qui enregistrent ces événements dans une certaine période, comme indiqué ci-dessus. Par exemple, pendant le trafic de haute saison des fêtes, les indicateurs de préparation peuvent afficher des valeurs plus élevées que lors des périodes de volume normal.

Pour vous aider à visualiser la progression de la formation de chaque type de recommandation, la variable _Sélectionner le type de recommandation_ affiche une mesure de l’état de préparation de chaque type. Ces indicateurs de préparation sont calculés sur la base de deux facteurs :

* Taille de jeu de résultats suffisante : la plupart des scénarios renvoient-ils suffisamment de résultats pour éviter d’utiliser [recommandations de sauvegarde](behavioral-data.md#backuprecs)?

* Suffisante variété d’ensembles de résultats : les produits renvoyés représentent-ils une variété de produits de votre catalogue ? L’objectif de ce facteur est d’éviter qu’une minorité de produits soit le seul élément recommandé sur l’ensemble du site.

En fonction des facteurs ci-dessus, une valeur de préparation est calculée et affichée. Un type de recommandation est considéré comme prêt à être déployé lorsque sa valeur de préparation est supérieure ou égale à 75 %. Un type de recommandation est considéré comme partiellement prêt lorsque son état de préparation est d’au moins 50 %. Un type de recommandation est considéré comme non prêt à être déployé lorsque sa valeur de préparation est inférieure à 50 %. Il s’agit de directives générales, mais chaque cas peut varier en fonction de la nature des données collectées, comme indiqué ci-dessus.

![Type de recommandation](assets/create-recommendation-select-type.png)
_Type de recommandation_

>[!NOTE]
>
>Les indicateurs peuvent ne jamais atteindre 100 %.

## Aperçu de Recommendations {#preview}

La variable _Aperçu des produits recommandés_ est toujours disponible avec un exemple de sélection de produits pouvant apparaître dans l’unité de recommandation lors de son déploiement sur storefront.

Pour tester une recommandation dans un environnement hors production, vous pouvez récupérer les données de recommandation d’une [source différente](settings.md). Cela permet aux commerçants d’expérimenter des règles et de prévisualiser les recommandations avant leur déploiement en production.

| Champ | Description |
|---|---|
| Nom | Nom du produit. |
| SKU | Unité de gestion des stocks affectée au produit |
| Prix | Le prix du produit. |
| Type de résultat | Principal : indique qu’il existe suffisamment de données de formation pour afficher une recommandation.<br />Sauvegarde : indique qu’il n’y a pas suffisamment de données d’entraînement collectées. Une recommandation de sauvegarde est donc utilisée pour remplir l’emplacement. Accédez à [Données comportementales](behavioral-data.md) pour en savoir plus sur les modèles d’apprentissage automatique et les recommandations de sauvegarde. |

À mesure que vous créez votre unité de recommandations, testez le type de page, le type de recommandation et les filtres pour obtenir des commentaires en temps réel immédiats sur les produits qui seront inclus. Lorsque vous commencez à comprendre les produits qui apparaissent, vous pouvez configurer l’unité de recommandations en fonction des besoins de votre entreprise.

Adobe Commerce [filtres](filters.md) recommandations pour éviter d’afficher les produits en double lorsque plusieurs unités de recommandations sont déployées sur une seule page. Par conséquent, les produits qui apparaissent dans le panneau d’aperçu peuvent différer de ceux qui apparaissent dans le storefront.

>[!NOTE]
>
> Vous ne pouvez pas prévisualiser la variable `Recently viewed` type de recommandation, car les données ne sont pas disponibles dans l’administrateur.
