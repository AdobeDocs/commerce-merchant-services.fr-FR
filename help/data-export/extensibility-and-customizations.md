---
title: Étendre et personnaliser les données de flux d’exportation de données SaaS
description: Découvrez comment étendre et personnaliser les données de flux  [!DNL SaaS Data Export] .
role: Admin, Developer
exl-id: 69300242-d317-4ec8-86d0-0cd5d0c9c958
source-git-commit: 06ef294d2670e5d36bbb6cd18deafce2cc751772
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 0%

---

# Étendre et personnaliser les données de flux d’exportation de données SaaS

L’extension [!DNL Commerce Data Export] permet d’exporter des données de l’application [!DNL Commerce] vers les services Commerce tels que Live Search, Catalog Service et Product Recommendations. Si nécessaire, vous pouvez étendre et personnaliser les données de flux afin d’inclure des données d’attribut supplémentaires ou de modifier les données collectées.

Après l’ajout de données d’attribut, elles sont accessibles à partir du [champ d’attributs](https://developer.adobe.com/commerce/services/graphql/catalog-service/products/#productviewattribute-type) dans le schéma GraphQL pour le service storefront.

>[!NOTE]
>
>L’ajout ou la modification de données de flux peut avoir un impact sur les performances et la logique de traitement sur le serveur principal Commerce. Testez le code personnalisé avant de le fusionner en production. Au lieu d’ajouter des données au serveur principal, utilisez le maillage API pour étendre le schéma GraphQL du service de catalogue. Pour plus d’informations sur la configuration, voir [Service de catalogue et maillage API](../catalog-service/mesh.md).

## Étendre les données d’attributs système dans le flux de produits

Le flux de produits comprend des attributs système par défaut, requis pour le traitement du produit ou couramment utilisés par les consommateurs. Vous pouvez inclure des attributs système supplémentaires dans le flux de produits en les ajoutant au flux.

Pour terminer cette tâche, mettez à jour le module `magento/catalog-data-exporter` afin d’ajouter les attributs système supplémentaires au [fichier de configuration d’injection de dépendance](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/) (`di.xml`).

Ajoutez les attributs à la requête d’attribut de produit (`Magento\CatalogDataExporter\Model\Query\ProductAttributeQuery`).

**Exemple**

```xml
    <type name="Magento\CatalogDataExporter\Model\Query\ProductAttributeQuery">
        <arguments>
            <argument name="systemAttributes" xsi:type="array">
                <item name="news_from_date" xsi:type="string">news_from_date</item>
                ...
                <item name="some_system_attribute_code">some_system_attribute_code</item>
            </argument>
        </arguments>
    </type>
```

## Ajout d’attributs de produit à Adobe Commerce

Les développeurs peuvent ajouter des attributs de produit accessibles à partir du [champ d’attributs de produit](https://developer.adobe.com/commerce/services/graphql/catalog-service/products/#output-fields) en utilisant l’une des méthodes suivantes :

- Ajoutez l’attribut à Adobe Commerce pour l’inclusion dans les données de flux `products` exportées vers les services Commerce storefront.
- Ajoutez l’attribut dynamiquement pendant le processus de synchronisation des flux à l’aide d’un module externe.

### Ajout de l’attribut à Adobe Commerce

Vous pouvez ajouter un attribut de produit à partir de l’administrateur Commerce ou par programmation en utilisant un module PHP personnalisé pour définir l’attribut et mettre à jour Adobe Commerce. Il s’agit de la méthode la plus simple pour ajouter un attribut de produit, car vous pouvez ajouter l’attribut et toutes les métadonnées requises. Le nouvel attribut et ses propriétés de métadonnées sont automatiquement exportés vers les services SaaS lors de la prochaine synchronisation planifiée.

#### Création de l’attribut de produit à partir de l’administrateur

1. Depuis l’administrateur Commerce, créez l’attribut à partir de la page de configuration des attributs de produit ([!UICONTROL Stores] > *[!UICONTROL Attributes]* > [!UICONTROL Product]).

1. Ajoutez l’attribut à un jeu d’attributs selon vos besoins.

Voir [Création d’attributs de produit](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/product-attributes/create/attribute-product-create) dans le *Guide de l’administrateur Adobe Commerce*.

#### Créer l’attribut de produit par programmation

Ajoutez un attribut de produit par programmation en créant un correctif de données qui implémente le `DataPatchInterface` et instanciez une copie de la classe `EavSetup Factory` dans le constructeur pour configurer les options d’attribut.

Lorsque vous définissez les options d’attribut, tous les paramètres d’attribut, à l’exception de `type`, `label` et `input`, sont facultatifs. Définissez les options supplémentaires suivantes ainsi que toute autre option différente des paramètres par défaut.

- Vérifiez que la propriété est exportée vers les services storefront lors de la synchronisation des données en définissant `user_defined` = `1`
- Pour vous assurer que l’attribut est accessible dans la requête de base de données de liste de produits, définissez `used_in_product_listing` = `1`.

Pour plus d’informations sur la création de correctifs de données, voir [Développer des correctifs de données et de schéma](https://developer.adobe.com/commerce/php/development/components/declarative-schema/patches/) dans le *Guide du développeur PHP*.

### Ajouter dynamiquement l’attribut de produit

Pour plus d’informations sur la création dynamique d’attributs de produit sans l’introduction de nouveaux attributs Eav, voir [Ajout dynamique d’attribut](add-attribute-dynamically.md).
