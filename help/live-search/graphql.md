---
title: GraphQL
description: L’espace de travail  [!DNL Live Search] GraphQL vous permet de créer des requêtes avec vos données actives.
exl-id: f7b17c5a-a97b-4724-a50e-83e28a4c4c38
source-git-commit: cf94623fd4a87c13d15c81ac62243a508cb1d14d
workflow-type: tm+mt
source-wordcount: '39'
ht-degree: 0%

---

# GraphQL

L’espace de travail *GraphQL* permet aux administrateurs de créer et de tester des requêtes GraphQL à l’aide de leurs propres données.

Cet espace de travail prend en charge les requêtes [`productSearch`](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/) et [`attributeMetadata`](https://developer.adobe.com/commerce/services/graphql/live-search/attribute-metadata/).

![Espace de travail GraphQL](assets/graphql.png)

```graphql
query productSearch {
  productSearch(phrase: "a306") {
    total_count
    items {
      product {
        sku
		name
      }
    }
    facets {
      title
    }
  }
}
```

Variables :

```json
{
  "Magento-Environment-Id": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
  "Magento-Website-Code": "base",
  "Magento-Store-Code": "base",
  "Magento-Store-View-Code": "default",
  "X-Api-Key": "search_gql"
}
```

