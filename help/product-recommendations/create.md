---
title: Créer une recommandation
description: Découvrez comment créer une unité de recommandation de produit.
source-git-commit: 4ad607c8595b25d01b5f5020b787fc1d35d4df25
workflow-type: tm+mt
source-wordcount: '674'
ht-degree: 0%

---

# Créer une recommandation

Lorsque vous créez une recommandation, vous créez une _unité de recommandation_ qui contient le produit recommandé _items_.

![Unité de recommandation](assets/unit.png)
_Unité de recommandation_

Lorsque vous activez l’entité de recommandation, Adobe Commerce commence à [collecter des données](workspace.md) pour mesurer les impressions, les vues, les clics, etc. Le [!DNL Product Recommendations] le tableau affiche les mesures de chaque unité de recommandations afin de vous aider à prendre des décisions professionnelles éclairées.

1. Sur le _Administration_ barre latérale, accédez à **Marketing** > _Promotions_ > **Recommendations de produit** pour afficher la variable _Recommendations de produit_ workspace.

1. Spécifiez la variable [Affichage en magasin](https://docs.magento.com/user-guide/configuration/scope.html) où afficher les recommandations.

   >[!NOTE]
   >
   > Les unités de recommandations du Créateur de pages peuvent uniquement être créées pour la vue de magasin par défaut. Pour en savoir plus sur la création de recommandations de produits avec le générateur de pages, voir [Ajouter du contenu - Recommendations de produit](https://docs.magento.com/user-guide/cms/page-builder-add-recommendations.html).

1. Cliquez sur **Créer une recommandation**.

1. Dans le _Nommer votre recommandation_ , saisissez un nom descriptif pour la référence interne, tel que `Home page most popular`.

1. Dans le _Sélectionner le type de page_ , sélectionnez la page sur laquelle vous souhaitez que la recommandation apparaisse dans les options suivantes :

   - Page d’accueil
   - Catégorie
   - Détails du produit
   - Panier
   - Confirmation
   - [Page Builder](https://docs.magento.com/user-guide/cms/page-builder-add-recommendations.html)

   Vous pouvez créer jusqu’à cinq unités de recommandations principales pour chaque type de page et jusqu’à 25 unités pour le créateur de pages. Le type de page est grisé Lorsque la limite est atteinte.

   ![Nom de la recommandation](assets/create-recommendation.png)
   _Nom et emplacement de la recommandation_

1. Dans le _Sélectionner le type de recommandation_ , spécifiez la variable [type de recommandation](type.md) vous souhaitez afficher la page sélectionnée. Pour certaines pages, la variable [placement](placement.md) de recommandations est limitée à certains types.

1. Dans le _Libellé d’affichage de la vitrine_ , saisissez la [label](placement.md#recommendation-labels) qui est visible par vos acheteurs, par exemple &quot;Meilleurs vendeurs&quot;.

   ![Nom de la recommandation](assets/create-recommendation-select-type.png)
   _Type de recommandation_

1. Dans le _Choisir le nombre de produits_ , utilisez le curseur pour spécifier le nombre de produits à afficher dans l’unité de recommandation.

   La valeur par défaut est `5`, avec un maximum de `20`.

1. Dans le _Sélectionner un emplacement_ , indiquez l’emplacement d’affichage de l’unité de recommandation sur la page.

   - Au bas du contenu principal
   - En haut du contenu principal

1. (Facultatif) Pour modifier l’ordre des recommandations, sélectionnez et déplacez les lignes dans la variable _Choisir la position_ table.

   Le _Choisir la position_ affiche toutes les recommandations (le cas échéant) créées pour le type de page que vous avez sélectionné.

   ![Nom de la recommandation](assets/create-recommendation-select-placement.png)
   _Type de recommandation_

1. (Facultatif) Dans le _Filtres_ , [appliquer des filtres ;](filters.md) pour contrôler les produits qui apparaissent dans l’unité de recommandation.

   ![Nom de la recommandation](assets/create-recommendation-select-placement.png)
   _Filtres de produits de recommandation_

1. Une fois l’opération terminée, cliquez sur l’une des options suivantes :

   - **Enregistrer en tant que brouillon** pour modifier ultérieurement l’unité de recommandation. Vous ne pouvez pas modifier le type de page ou de recommandation d’une unité de recommandation dans un état de brouillon.

   - **Activer** pour activer l’unité de recommandation sur votre vitrine.

## Aperçu de Recommendations {#preview}

Le _Aperçu des produits recommandés_ est toujours disponible avec un exemple de sélection de produits pouvant apparaître dans l’unité de recommandation lors de son déploiement sur storefront.

Pour tester une recommandation dans un environnement hors production, vous pouvez récupérer les données de recommandation d’une [source différente](settings.md). Cela permet aux commerçants d’expérimenter des règles et de prévisualiser les recommandations avant leur déploiement en production.

| Champ | Description |
|---|---|
| Nom | Nom du produit. |
| SKU | Unité de gestion des stocks affectée au produit |
| Prix | Le prix du produit. |
| Type de résultat | Principal : indique qu’il existe suffisamment de données de formation collectées pour afficher une recommandation.<br />Sauvegarde : indique qu’il n’y a pas suffisamment de données d’entraînement collectées. Une recommandation de sauvegarde est donc utilisée pour remplir l’emplacement. Accédez à [Données comportementales](behavioral-data.md) pour en savoir plus sur les modèles d’apprentissage automatique et les recommandations de sauvegarde. |

À mesure que vous créez votre unité de recommandations, testez le type de page, le type de recommandation et les filtres pour obtenir des commentaires en temps réel immédiats sur les produits qui seront inclus. Lorsque vous commencez à comprendre les produits qui apparaissent, vous pouvez configurer l’unité de recommandations en fonction des besoins de votre entreprise.

Adobe Commerce [filtres](filters.md) recommandations pour éviter d’afficher les produits en double lorsque plusieurs unités de recommandations sont déployées sur une seule page. Par conséquent, les produits qui apparaissent dans le panneau d’aperçu peuvent différer de ceux qui apparaissent dans le storefront.

>[!NOTE]
>
> Vous ne pouvez pas prévisualiser la variable `Recently viewed` type de recommandation, car les données ne sont pas disponibles dans l’administrateur.
