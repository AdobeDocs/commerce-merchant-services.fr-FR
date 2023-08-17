---
title: "[!DNL Live Search] Indexation"
description: "Découvrez comment [!DNL Live Search] indexe les propriétés d’attribut de produit."
exl-id: 04441e58-ffac-4335-aa26-893988a89720
source-git-commit: 7eece9b341a27637d7ac00216f18b7fad7c50740
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---

# Indexation

Les propriétés d’attribut de produit (métadonnées) déterminent :

* Utilisation d’un attribut dans le catalogue
* Son apparence et son comportement dans le magasin
* Données incluses dans les opérations de transfert de données

La portée des métadonnées d’attribut est `website/store/store view`.

La variable [!DNL Live Search] L’API permet à un client de trier selon n’importe quel attribut de produit qui possède la variable [storefront, propriété](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) `Use in Search` défini sur `Yes` dans l’administrateur Adobe Commerce. Lorsqu’elle est activée, `Search Weight` et `Visible in Advanced Search` peut être défini pour l’attribut .

[!DNL Live Search] n’indexe pas les produits supprimés ou ceux définis sur `Not Visible Individually`.

>[!NOTE]
>
> Clients commerciaux avec [!DNL Live Search] peuvent tirer parti des modifications de prix plus rapides et du temps de synchronisation sur leurs sites web avec la variable [Indexeur de prix SaaS](../price-index/index.md).

## Indexation du pipeline

Le client appelle le service de recherche à partir du storefront pour récupérer les métadonnées d’index (filtrables, triables). Attributs de produit pouvant faire l’objet d’une recherche uniquement avec la variable *Utilisation dans la navigation par calques* définie sur `Filterable (with results)` et *Utilisation pour le tri dans la liste des produits* défini sur `Yes` peut être appelé par le service de recherche.
Pour construire une requête dynamique, le service de recherche doit savoir quels attributs peuvent faire l’objet d’une recherche et leur poids. [!DNL Live Search] honore les poids de recherche Adobe Commerce (1 à 10, où 10 est la priorité la plus élevée). La liste des données synchronisées et partagées avec le service de catalogue se trouve dans le schéma, défini dans :

`vendor/magento/module-catalog-data-exporter/etc/et_schema.xml`

![[!DNL Live Search] schéma de recherche client d’indexation](assets/indexing-pipeline.svg)

1. Vérifier le commerçant pour [!DNL Live Search] droits.
1. Obtenez des vues de magasin avec des modifications des métadonnées d’attribut.
1. Stocker les attributs d’indexation.
1. Réindexez l’index de recherche.

### Index complet

When [!DNL Live Search] est configuré et synchronisé lors de l’intégration. La création de l’index initial peut prendre jusqu’à 30 minutes. L’indexation des catalogues volumineux peut prendre plus de temps. Le processus commence après `cron` envoie le flux et termine l’exécution.

Les événements suivants déclenchent une synchronisation complète et une génération d’index :

* Intégration [synchronisation des données du catalogue](install.md#synchronize-catalog-data)
* Modifications des métadonnées d’attribut

Par exemple, modifiez la variable `Use in Search` de la propriété `color` de `No` to `Yes` modifie les métadonnées d’attribut en `searchable=true`et déclenche une synchronisation et une réindexation complètes. Les métadonnées d’attribut suivantes déclenchent une synchronisation et une réindexation complètes en cas de modification :

* `filterableInSearch`
* `searchable`
* `sortable`
* `visibleInSearch`

### Diffusion en continu des mises à jour des produits

Une fois l’index initial créé pendant la [intégration](install.md#synchronize-catalog-data), les mises à jour incrémentielles suivantes du produit sont synchronisées et réindexées en continu :

* Nouveaux produits ajoutés au catalogue
* Modifications des valeurs d’attribut de produit

Par exemple, l’ajout d’une nouvelle valeur d’échantillon au `color` est géré comme une mise à jour de produit par flux.
Workflow de mise à jour en flux continu :

1. Les produits mis à jour sont synchronisés de l’instance Adobe Commerce vers le service de catalogue.
1. Le service d’indexation recherche en permanence les mises à jour de produit à partir du service de catalogue. Les produits mis à jour sont indexés à leur arrivée dans le service de catalogue.
1. La disponibilité d’une mise à jour de produit dans peut prendre jusqu’à 15 minutes. [!DNL Live Search].

## Recherche de client

La variable [!DNL Live Search] L’API permet à un client de trier selon n’importe quel attribut de produit triable en définissant la variable [storefront, propriété](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html), *Utilisé pour le tri dans les listes de produits* to `Yes`. En fonction du thème, ce paramètre entraîne l’inclusion de l’attribut comme option dans la variable [Tri par](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation.html) contrôle de pagination sur les pages du catalogue. Jusqu’à 200 attributs de produit peuvent être indexés par [!DNL Live Search], avec [propriétés storefront](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) qui peuvent faire l’objet de recherches et être filtrées.
Les métadonnées d’index sont stockées dans le pipeline d’indexation et sont accessibles par le service de recherche.

![[!DNL Live Search] diagramme de l’API des métadonnées d’index](assets/index-metadata-api.svg)

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
