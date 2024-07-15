---
title: "Indexation"
description: "Découvrez comment  [!DNL Live Search] indexe les propriétés d’attribut de produit."
exl-id: 04441e58-ffac-4335-aa26-893988a89720
source-git-commit: 4978bdb5549f5df911863a23fdfbfc9ab9ad05df
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 0%

---

# Indexation

Le processus d’indexation [!DNL Live Search] lit le catalogue pour les attributs de produit et crée un index afin que les produits puissent être recherchés, filtrés et présentés rapidement.

Les propriétés d’attribut de produit (métadonnées) déterminent :

* Utilisation d’un attribut dans le catalogue
* Son apparence et son comportement dans le magasin
* Données incluses dans les opérations de transfert de données

La portée des métadonnées d’attribut est `website/store/store view`.

L’API [!DNL Live Search] permet à un client de trier selon n’importe quel attribut de produit dont la propriété [storefront](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) `Use in Search` est définie sur `Yes` dans l’administrateur Adobe Commerce. Lorsqu’elle est activée, `Search Weight` et `Visible in Advanced Search` peuvent être définis pour l’attribut .

[!DNL Live Search] n’indexe pas les produits supprimés ou ceux définis sur `Not Visible Individually`.

>[!NOTE]
>
> Les clients Commerce disposant de [!DNL Live Search] peuvent tirer parti des modifications de prix plus rapides et du temps de synchronisation sur leurs sites web avec l’ [ indexeur de prix SaaS](../price-index/price-indexing.md).

## Indexation du pipeline

Le client appelle le service de recherche à partir du storefront pour récupérer les métadonnées d’index (filtrables, triables). Seuls les attributs de produit pouvant faire l’objet d’une recherche et dont la propriété *Use in Layered Navigation* est définie sur `Filterable (with results)` et *Use for Triting in Product List* définie sur `Yes` peuvent être appelés par le service de recherche.
Pour construire une requête dynamique, le service de recherche doit savoir quels attributs peuvent faire l’objet d’une recherche et leur [poids](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-results.html#weighted-search). [!DNL Live Search] honore les poids de recherche Adobe Commerce (1 à 10, où 10 est la priorité la plus élevée). La liste des données synchronisées et partagées avec le service de catalogue se trouve dans le schéma, défini dans :

`vendor/magento/module-catalog-data-exporter/etc/et_schema.xml`

![[!DNL Live Search] Diagramme de recherche du client d&#39;indexation ](assets/indexing-pipeline.svg)

1. Vérifiez le marchand pour le droit [!DNL Live Search].
1. Obtenez des vues de magasin avec des modifications des métadonnées d’attribut.
1. Stocker les attributs d’indexation.
1. Réindexez l’index de recherche.

### Index complet

Lorsque [!DNL Live Search] est configuré et synchronisé lors de l’intégration, la création de l’index initial peut prendre jusqu’à 60 minutes. L’indexation des catalogues volumineux peut prendre plus de temps. Le processus commence après l’envoi du flux par `cron` et la fin de l’exécution.

Les événements suivants déclenchent une synchronisation complète et une génération d’index :

* Intégration [ de la synchronisation des données de catalogue ](install.md#synchronize-catalog-data)
* Modifications des métadonnées d’attribut

Par exemple, la modification de la propriété `Use in Search` de l’attribut `color` de `No` à `Yes` modifie les métadonnées d’attribut en `searchable=true` et déclenche une synchronisation et une réindexation complètes. Les métadonnées d’attribut suivantes déclenchent une synchronisation et une réindexation complètes en cas de modification :

* `filterableInSearch`
* `searchable`
* `sortable`
* `visibleInSearch`

### Diffusion en continu des mises à jour des produits

Une fois l’index initial créé lors de l’[intégration](install.md#synchronize-catalog-data), les mises à jour incrémentielles suivantes sont synchronisées et réindexées en continu :

* Nouveaux produits ajoutés au catalogue
* Modifications des valeurs d’attribut de produit

Par exemple, l’ajout d’une nouvelle valeur d’échantillon à l’attribut `color` est géré comme une mise à jour de produit par flux.
Workflow de mise à jour en flux continu :

1. Les produits mis à jour sont synchronisés de l’instance Adobe Commerce vers le service de catalogue.
1. Le service d’indexation recherche en permanence les mises à jour de produit à partir du service de catalogue. Les produits mis à jour sont indexés à leur arrivée dans le service de catalogue.
1. La disponibilité d’une mise à jour de produit dans [!DNL Live Search] peut prendre jusqu’à 15 minutes.

## Recherche de client

L’API [!DNL Live Search] permet à un client de trier selon n’importe quel attribut de produit triable en définissant la [propriété storefront](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html), *Utilisée pour le tri dans les listes de produits* sur `Yes`. En fonction du thème, ce paramètre entraîne l’inclusion de l’attribut comme option dans la commande de pagination [Trier par](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation.html) sur les pages du catalogue. Jusqu’à 200 attributs de produit peuvent être indexés par [!DNL Live Search], avec des [propriétés storefront](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) pouvant faire l’objet de recherches et pouvant être filtrées.
Les métadonnées d’index sont stockées dans le pipeline d’indexation et sont accessibles par le service de recherche.

![[!DNL Live Search] Diagramme d’API de métadonnées d’index ](assets/index-metadata-api.svg)

### Workflow des attributs de tri

1. Le client appelle Search Service.
1. Search Service appelle Search Admin Service.
1. Search Service appelle le pipeline d’indexation.

## Indexé pour tous les produits

L’ordre des champs de cette liste reflète l’ordre type des colonnes dans les données de produit exportées.

* `environment_id`
* `website_code`
* `store_code`
* `store_view_code`
* `product_id`
* `sku`
* `name`
* `type`
* `displayable`
* `deleted`
* `url`
* `currency`
* `meta_description`
* `meta_keyword`
* `meta_title`
* `description`
* `short_description`
* `weight`
* `image`
* `small_image`
* `thumbnail_image`
* `prices`
* `in_stock`
* `low_stock`

Le champ suivant est indexé pour tous les produits configurables :

* `childrenSkus`
