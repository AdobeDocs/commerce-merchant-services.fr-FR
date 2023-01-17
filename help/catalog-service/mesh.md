---
title: '[!DNL Catalog Service and API Mesh]'
description: '''[!DNL API Mesh] pour Adobe Commerce, permet d’intégrer plusieurs sources de données par le biais d’un point de terminaison GraphQL commun."'
source-git-commit: 7b95be48c21e17cb6ba88d326fd061f7de2f8fb5
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---

# [!DNL Catalog Service and API Mesh]

Le [Maillage d’API pour Adobe Developer App Builder](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) permet aux développeurs d’intégrer des API privées ou tierces, ainsi que d’autres interfaces avec des produits Adobe à l’aide des E/S d’Adobe.

La première étape de l’utilisation du maillage API avec le service de catalogue consiste à connecter le maillage API à votre instance. Voir les instructions détaillées dans [Création d’un maillage](https://developer.adobe.com/graphql-mesh-gateway/gateway/create-mesh/).

Pour terminer la configuration, vous devez [Module d’interface de ligne de commande d’Adobe IO](https://developer.adobe.com/runtime/docs/guides/tools/cli_install/) installé.

Une fois que le maillage est configuré sur l’Adobe IO, exécutez la commande suivante qui ajoute une `CommerceCatalogServiceGraph` source à votre impression.

```bash
aio api-mesh:source:install "CommerceCatalogServiceGraph" -f variables.json
```

where `variables.json` est un fichier distinct qui stocke les valeurs couramment utilisées pour les E/S d’Adobe.
Par exemple, la clé API peut être enregistrée dans le fichier :

```json
{
    "CATALOG_SERVICE_API_KEY":"your_api_key"
}
```

Après l’exécution de cette commande, le service de catalogue doit s’exécuter par le biais du maillage API. Vous pouvez exécuter la variable `aio api-mesh:get` pour afficher la configuration de votre impression mise à jour.

## Utilisation du maillage API

Le maillage API permet aux utilisateurs d’utiliser des sources de données externes pour améliorer votre instance Adobe Commerce. Il peut également être utilisé pour configurer les données Commerce existantes afin d’activer une nouvelle fonctionnalité.

Dans cet exemple, le maillage API est utilisé pour activer les prix de niveau dans Adobe Commerce.
Remplacez la variable `name `, `endpoint` et `x-api-key` valeurs.

```json
{
  "meshConfig": {
    "sources": [
      {
        "name": "<Commerce Instance Name>",
        "handler": {
          "graphql": {
            "endpoint": "<Adobe Commerce GraphQL endpoint>"
          }
        },
        "transforms": [
            {
                "prefix": {
                    "includeRootOperations": true,
                    "value": "Core_"
                }
            }
        ]
      },
      {
        "name": "CommerceCatalogServiceGraph",
        "handler": {
          "graphql": {
            "endpoint": "https://commerce.adobe.io/catalog-service/graphql/",
            "operationHeaders": {
              "Magento-Store-View-Code": "{context.headers['magento-store-view-code']}",
              "Magento-Website-Code": "{context.headers['magento-website-code']}",
              "Magento-Store-Code": "{context.headers['magento-store-code']}",
              "Magento-Environment-Id": "{context.headers['magento-environment-id']}",
              "x-api-key": "storefront-catalog-apollo",
              "Magento-Customer-Group": "{context.headers['magento-customer-group']}"
            },
            "schemaHeaders": {
              "x-api-key": "<YOUR API-KEY>"
            }
          }
        }
      }
    ],
    "additionalTypeDefs": "extend interface ProductView {\n  price_tiers: [Core_TierPrice]\n}\n extend type SimpleProductView {\n  price_tiers: [Core_TierPrice]\n}\n extend type ComplexProductView {\n  price_tiers: [Core_TierPrice]\n}\n",
    "additionalResolvers": [
        {  
            "targetTypeName": "ProductView",
            "targetFieldName": "price_tiers",
            "sourceName": "MagentoStageCore",
            "sourceTypeName": "Query",
            "sourceFieldName": "Core_products",
            "requiredSelectionSet": "{\n    items {\n  sku\n    price_tiers {\n        quantity,\n        final_price {\n          value\n          currency\n        }\n      }\n    }\n  }",
            "sourceArgs": {
                "filter.sku.eq": "{root.sku}"
            },
            "result": "items[0].price_tiers"
        },
        {  
            "targetTypeName": "SimpleProductView",
            "targetFieldName": "price_tiers",
            "sourceName": "MagentoStageCore",
            "sourceTypeName": "Query",
            "sourceFieldName": "Core_products",
            "requiredSelectionSet": "{\n    items {\n  sku\n    price_tiers {\n        quantity,\n        final_price {\n          value\n          currency\n        }\n      }\n    }\n  }",
            "sourceArgs": {
                "filter.sku.eq": "{root.sku}"
            },
            "result": "items[0].price_tiers"
        },
        {  
            "targetTypeName": "ComplexProductView",
            "targetFieldName": "price_tiers",
            "sourceName": "MagentoStageCore",
            "sourceTypeName": "Query",
            "sourceFieldName": "Core_products",
            "requiredSelectionSet": "{\n    items {\n  sku\n    price_tiers {\n        quantity,\n        final_price {\n          value\n          currency\n        }\n      }\n    }\n  }",
            "sourceArgs": {
                "filter.sku.eq": "{root.sku}"
            },
            "result": "items[0].price_tiers"
        }
    ]
   }
}
```

Une fois la configuration effectuée, interrogez le maillage pour une tarification à plusieurs niveaux :

```json
query {
  products(skus: ["24-MB04"]) {
    sku
    description
    price_tiers {
        quantity
        final_price {
          value
          currency
        }
      }
    ... on SimpleProductView {
      id
       
      price {
        final {
          amount {
            value
          }
        }
      }
    }
  }
}
```
