---
title: Indexation des prix SaaS
description: Utilisation de l’indexation des prix SaaS pour améliorer les performances
seo-title: Adobe SaaS Price Indexing
seo-description: Price indexing give performance improvements using SaaS infrastructure
exl-id: 747c0f3e-dfde-4365-812a-5ab7768342ab
source-git-commit: b7989b416f852d2c7164d21e8f0598373662b760
workflow-type: tm+mt
source-wordcount: '713'
ht-degree: 0%

---

# Indexation des prix SaaS

L’indexation des prix SaaS accélère le temps nécessaire pour que les changements de prix soient répercutés. [Services de commerce](../landing/saas.md) après avoir été soumis. Cela permet aux commerçants disposant de catalogues volumineux et complexes, ou de plusieurs sites web ou groupes de clients, de traiter en permanence les changements de prix.
Si vous disposez d’une vitrine sans interface utilisateur graphique ou utilisez la variable [catalog-adapter](./catalog-adapter.md) , les clients peuvent désactiver l’indexeur de prix de base d’Adobe Commerce.

Les processus lourds informatiques, tels que l’indexation et le calcul des prix, ont été déplacés du coeur de Commerce vers l’infrastructure cloud d’Adobe. Cela permet aux commerçants d’augmenter rapidement les ressources pour augmenter les délais d’indexation des prix et refléter ces changements plus rapidement.

Le flux de données d’indexation principal vers les services SaaS ressemble à ce qui suit :

![Flux de données par défaut](assets/old_way.png)

Avec l’indexation des prix SaaS, le flux est :

![Flux de données d’indexation de prix SaaS](assets/new_way.png)

Tous les commerçants peuvent bénéficier de ces améliorations, mais ceux qui en bénéficieront le plus sont les clients avec :

* Changements constants des prix : les marchands qui nécessitent des modifications répétées de leurs prix pour atteindre des objectifs stratégiques tels que des promotions fréquentes, des remises saisonnières ou des marqueurs d’inventaire.
* Plusieurs sites web et/ou groupes de clients : marchands avec des catalogues de produits partagés sur plusieurs sites web (domaines/marques) et/ou groupes de clients.
* Grand nombre de prix uniques sur plusieurs sites web ou groupes de clients : marchands avec des catalogues de produits partagés étendus qui contiennent des prix uniques sur plusieurs sites web ou groupes de clients, tels que des marchands B2B avec des prix négociés au préalable, des marques avec des stratégies de tarification différentes.

L’indexation des prix SaaS est disponible gratuitement pour les clients utilisant les services Adobe Commerce et prend en charge le calcul des prix pour tous les types de produits Adobe Commerce intégrés.

Ce mini-guide décrit le fonctionnement de l’indexation de prix SaaS et comment l’activer.

## Conditions

* Adobe Commerce 2.4.4+
* Au moins l’un des services Commerce suivants avec la dernière version de l’extension Adobe Commerce :

   * [Service de catalogue](../catalog-service/overview.md)
   * [Recherche en direct](../live-search/guide-overview.md)
   * [Recommendations de produit](../product-recommendations/guide-overview.md)

Les utilisateurs de Luma et Adobe Commerce Core GraphQL peuvent installer la variable [`catalog-adapter`](catalog-adapter.md) qui fournit la compatibilité Luma et Core GraphQl et désactive l’indexeur de prix des produits Adobe Commerce.

## Utilisation

Après la mise à niveau de votre instance Adobe Commerce avec la prise en charge de l’indexation de prix SaaS, synchronisez les nouveaux flux :

```
magento/module-saas-price
magento/module-saas-scopes
magento/module-product-override-price-remover
magento/module-bundle-product-override-data-exporter
magento/module-bundle-product-override-data-exporter
magento/module-gift-card-product-data-exporter
```

## Prix des types de produits personnalisés

Les calculs de prix sont pris en charge pour les types de produits personnalisés tels que le prix de base, le prix spécial, le prix de groupe, le prix de règle de catalogue, etc.

Si vous disposez d’un type de produit personnalisé qui utilise une formule spécifique pour calculer le prix final, vous pouvez étendre le comportement du flux de prix du produit.

## Utilisation

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
    <type name="Magento\ProductPriceDataExporter\Model\Provider\ProductPrice">
        <plugin name="custom_type_price_feed" type="YourModule\CustomProductType\Plugin\UpdatePriceFromFeed" />
    </type>
</config>
```

Les nouveaux flux doivent être synchronisés manuellement avec la variable `resync` [Commande CLI](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html#resynccmdline). Dans le cas contraire, les données sont actualisées dans le processus de synchronisation standard. Obtenez plus d’informations sur la variable [Synchronisation du catalogue](../landing/catalog-sync.md) processus.

## Scénarios d’utilisation

### Luma sans dépendances d’extension

* Un commerçant Luma ou Adobe Commerce Core GraphQL qui a installé le service requis (Live Search, Recommendations produit, Catalog Service)
* Aucune extension tierce reposant sur l’indexeur de prix de base PHP
* Vendre des produits dynamiques simples, configurables, groupés, virtuels et regroupés

1. Activez les nouveaux flux.
1. Installez l’adaptateur de catalogue.

### Luma et Adobe Commerce Core GraphQl avec dépendances de l’indexeur de prix principal PHP

* Un commerçant Luma ou Adobe Commerce Core GraphQL qui a installé un service pris en charge (Live Search, Recommendations produit, Catalog Service)
* Avec une extension tierce reposant sur l’indexeur de prix de base PHP
* Vendre des produits dynamiques simples, configurables, groupés, virtuels et regroupés

1. Activation des nouveaux flux
1. Installez l’adaptateur de catalogue.
1. Réactivez l’indexeur de prix de base PHP.
1. Utilisez les nouveaux flux et le code de compatibilité Luma dans la variable `catalog-adapter` module .

### Marchand sans tête

* Un commerçant sans tête qui dispose d’un service pris en charge installé (recherche en direct, Recommendations de produit, service de catalogue)
* Pas de dépendance à l’indexeur de prix de base PHP
* Vendre des produits dynamiques simples, configurables, groupés, virtuels et regroupés

1. Activation de nouveaux flux
1. Installez l’adaptateur de catalogue, qui désactive l’indexeur de prix de base PHP.

## Prix personnalisés

L’indexeur de prix SaaS prend en charge les fonctionnalités de prix de type de produit personnalisées disponibles dans Adobe Commerce, telles que le prix spécial, le prix du groupe et le prix de la règle de catalogue.

Par exemple : il existe un type de produit personnalisé  `custom_type` et un produit avec le SKU &quot;Produit de type personnalisé&quot;.

Par défaut, l’extension Exportation de données Commerce envoie le flux de prix suivant à l’indexeur de prix :

```json
{
    "sku": "Custom Type Product",
    "type": "SIMPLE", // must be "SIMPLE" regardless of the real product type
    "customerGroupCode": "0",
    "websiteCode": "base",
    "regular": 123, // the regular base price found in catalog_product_entity_decimal table
    "discounts":    // list of discounts: special_price, group, catalog_rule
    [
        {
            "code": "catalog_rule",
            "price": 102.09
        }
    ],
    "deleted": false,
    "updatedAt": "2023-07-31T13:07:54+00:00"
}
```

Si &quot;Type de produit personnalisé&quot; utilise une formule unique pour calculer le prix du produit, les intégrateurs système peuvent remplacer les champs de prix et de remise en étendant l’extension Exportation de données de commerce.

1. Créez un module externe sur le `Magento\ProductPriceDataExporter\Model\Provider\ProductPrice` classe .

`di.xml` fichier :

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
    <type name="Magento\ProductPriceDataExporter\Model\Provider\ProductPrice">
        <plugin name="custom_type_price_feed" type="YourModule\CustomProductType\Plugin\UpdatePriceFromFeed" disabled="false" />
    </type>
</config>
```

1. Créez une méthode avec la formule personnalisée :

```php
class UpdatePriceFromFeed
{
    /**
    * @param ProductPrice $subject
    * @param array $result
    * @param array $values
    *
    * @return array
    */
    public function afterGet(ProductPrice $subject, array $result, array $values) : array
    {
        // Get all custom products, prices and discounts per website and customer groups
        // Override the output $result with your data for the corresponding products
        return $result;
    }
}
```
