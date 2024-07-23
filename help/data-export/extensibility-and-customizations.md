---
title: Étendre et personnaliser les données de flux d’exportation de données SaaS
description: Découvrez comment étendre et personnaliser les données de flux  [!DNL SaaS Data Export] .
role: Admin, Developer
recommendations: noCatalog
source-git-commit: 51238f86f36a756b86d07bdf6bb0a5cf0c61cbeb
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---

# Étendre et personnaliser les données de flux d’exportation de données SaaS

L’extension [!DNL Commerce Data Export] permet d’exporter des données de l’application [!DNL Commerce] vers les services Commerce tels que Live Search, Catalog Service et Product Recommendations. Si nécessaire, vous pouvez étendre et personnaliser les données de flux pour inclure des données supplémentaires ou modifier les données collectées en mettant à jour le module `Magento\CatalogDataExporter`.

>[!NOTE]
>
>L’ajout de nouvelles données au flux ou la modification de données existantes peut affecter les performances de collecte du flux et entraîner des problèmes dans la logique de traitement du côté Adobe Commerce. Veillez à tester le code personnalisé avant de le fusionner dans un environnement de production.

## Étendre les données d’attributs dans le flux de produits

Le flux de produits comprend des attributs par défaut qui sont requis pour le traitement du produit ou couramment utilisés par les consommateurs. Vous pouvez inclure des attributs système supplémentaires dans le flux de produits en les ajoutant au flux.

Pour terminer cette tâche, mettez à jour le module `magento/catalog-data-exporter` afin d’ajouter les attributs système supplémentaires au [fichier de configuration d’injection de dépendance](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/) (`di.xml`). Ajoutez les attributs à la requête Attribut de produit (`Magento\CatalogDataExporter\Model\Query\ProductAttributeQuery`).

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
