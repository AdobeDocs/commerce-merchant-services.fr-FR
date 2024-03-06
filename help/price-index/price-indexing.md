---
title: Indexation des prix SaaS
description: Utilisation de l’indexation des prix SaaS pour améliorer les performances
seo-title: Adobe SaaS Price Indexing
seo-description: Price indexing give performance improvements using SaaS infrastructure
exl-id: 5b92d6ea-cfd6-4976-a430-1a3aeaed51fd
source-git-commit: a90fcd8401b7745a65715f68efccdb3ce7c77ccb
workflow-type: tm+mt
source-wordcount: '409'
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

Ce guide décrit le fonctionnement de l’indexation de prix SaaS et comment l’activer.

## Conditions

* Adobe Commerce 2.4.4+
* Au moins l’un des services Commerce suivants avec la dernière version de l’extension Adobe Commerce :

   * [Service de catalogue](../catalog-service/overview.md)
   * [Recherche en direct](../live-search/guide-overview.md)
   * [Recommendations de produit](../product-recommendations/guide-overview.md)

Les utilisateurs de Luma et Adobe Commerce Core GraphQL peuvent installer la variable [`catalog-adapter`](catalog-adapter.md) qui fournit la compatibilité Luma et Core GraphQl et désactive l’indexeur de prix des produits Adobe Commerce.

## Utilisation

Après la mise à niveau de votre instance Adobe Commerce avec la prise en charge de l’indexation de prix SaaS, synchronisez les nouveaux flux :

```bash
bin/magento saas:resync --feed=scopesCustomerGroup
bin/magento saas:resync --feed=scopesWebsite
bin/magento saas:resync --feed=prices
```

## Prix des types de produits personnalisés

Les calculs de prix sont pris en charge pour les types de produits personnalisés tels que le prix de base, le prix spécial, le prix de groupe, le prix de règle de catalogue, etc.

Si vous disposez d’un type de produit personnalisé qui utilise une formule spécifique pour calculer le prix final, vous pouvez étendre le comportement du flux de prix du produit.

1. Créez un module externe sur le `Magento\ProductPriceDataExporter\Model\Provider\ProductPrice` classe .

   ```xml
   <config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
           xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
       <type name="Magento\ProductPriceDataExporter\Model\Provider\ProductPrice">
           <plugin name="custom_type_price_feed" type="YourModule\CustomProductType\Plugin\UpdatePriceFromFeed" />
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
           // Override the output $result with your data for the corresponding products (see original method for details) 
           return $result;
       }
   }
   ```
