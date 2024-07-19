---
title: Indexation des prix SaaS
description: Utilisation de l’indexation des prix SaaS pour améliorer les performances
seo-title: Adobe SaaS Price Indexing
seo-description: Price indexing give performance improvements using SaaS infrastructure
exl-id: 5b92d6ea-cfd6-4976-a430-1a3aeaed51fd
source-git-commit: 0b0bc88c13d8c90a6209d9156f6fd6a7ce040f72
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# Indexation des prix SaaS

L’indexation des prix SaaS optimise les performances du site en déchargeant les tâches gourmandes en ressources (comme l’indexation et le calcul des prix) de l’application Commerce vers l’infrastructure cloud d’Adobe. Cette approche permet aux commerçants de mettre rapidement à l’échelle les ressources afin d’accélérer les temps d’indexation des prix et de fournir des mises à jour de prix plus rapidement au storefront et aux services Commerce connectés.

Le diagramme suivant montre le flux de données d’indexation vers les services SaaS lorsque Commerce utilise le processus [price indexing](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/manage-indexers) inclus dans l’application Commerce :

![Flux de données par défaut](assets/old_way.png)

Lorsque l’indexation des prix SaaS est activée, le flux de données change. L’indexation des prix est effectuée à l’aide de l’ [exportation des données Commerce SaaS](../data-export/data-synchronization.md).

![Flux de données d’indexation de prix SaaS](assets/new_way.png)

Tous les commerçants peuvent bénéficier de l’indexation de prix SaaS, mais les marchands qui ont des projets avec les caractéristiques suivantes peuvent réaliser les plus grands avantages :

* **Changements constants de prix** - Les marchands qui nécessitent des modifications répétées de leurs prix pour atteindre des objectifs stratégiques tels que des promotions fréquentes, des remises saisonnières ou des marqueurs d’inventaire.
* **Plusieurs sites web et/ou groupes de clients** - Marchands avec des catalogues de produits partagés sur plusieurs sites web (domaines/marques) et/ou groupes de clients.
* **- Nombreux prix uniques sur plusieurs sites web ou groupes de clients** - Marchands avec de vastes catalogues de produits partagés qui contiennent des prix uniques sur plusieurs sites web ou groupes de clients. Par exemple, les marchands B2B qui ont des prix négociés au préalable ou des marques ayant des stratégies de tarification différentes.

## Utilisation de l’indexation des prix SaaS

L’indexation des prix SaaS est activée automatiquement lors de l’installation des services Adobe Commerce. Il prend en charge le calcul des prix pour tous les types de produits Adobe Commerce intégrés.

### Conditions

* Adobe Commerce 2.4.4+

### Conditions préalables

* L’un des services Commerce suivants doit être installé avec la dernière version de l’extension Commerce :

   * [Service de catalogue](../catalog-service/overview.md)
   * [Recherche en direct](../live-search/overview.md)
   * [Recommendations de produit](../product-recommendations/guide-overview.md)


>[!NOTE]
>
>Si nécessaire, l’indexeur de prix par défaut dans l’application Commerce peut être désactivé à l’aide de l’ [adaptateur de catalogue](catalog-adapter.md).

## Synchronisation des prix avec l’indexation des prix SaaS

Après avoir activé l’indexation des prix SaaS pour Adobe Commerce, mettez à jour les prix sur Storefront et dans les services Commerce en synchronisant les nouveaux flux :

```bash
bin/magento saas:resync --feed=scopesCustomerGroup
bin/magento saas:resync --feed=scopesWebsite
bin/magento saas:resync --feed=prices
```

### Prix des types de produits personnalisés

Les calculs de prix sont pris en charge pour les types de produits personnalisés tels que le prix de base, le prix spécial, le prix du groupe, le prix des règles de catalogue, etc.

Si vous disposez d’un type de produit personnalisé qui utilise une formule spécifique pour calculer le prix final, vous pouvez étendre le comportement du flux de prix du produit.

1. Créez un module externe sur la classe `Magento\ProductPriceDataExporter\Model\Provider\ProductPrice`.

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

