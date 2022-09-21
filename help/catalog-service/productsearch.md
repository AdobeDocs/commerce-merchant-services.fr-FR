---
title: requête productSearch
description: '"Guide de référence pour la requête GraphQL "productSearch" pour le service de catalogue Adobe Commerce."'
source-git-commit: 49692cf4375ebb975b2cf132d21ac8debe609a90
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 2%

---


# requête productSearch

Service de catalogue pour Adobe Commerce `productSearch` La requête peut utiliser la fonction de recherche en direct pour renvoyer des détails sur les SKU spécifiés en tant qu’entrée. Bien que cette requête soit identique au [`productSearch` query](https://devdocs.magento.com//live-search/product-search.html), la recherche en direct renvoie une `productView` . Voir [`productSearch` query](https://devdocs.magento.com//live-search/product-search.html) rubrique pour obtenir des informations de référence.

## Syntaxe

```graphql
productSearch(
    phrase: String!
    page_size: Int = 20
    current_page: Int = 1
    filter: [SearchClauseInput!]
    sort: [ProductSearchSortInput!]
): ProductSearchResponse!
```

## En-têtes requis

Vous devez spécifier les en-têtes HTTP suivants pour exécuter cette requête.

| En-tête | Description |
|--- | ---|
| `Magento-Customer-Group` | Pour les clients storefront, cette valeur sera disponible au niveau du storefront dans la variable `dataservices_customer_group` du cookie. |
| `Magento-Environment-Id` | Cette valeur peut être obtenue en exécutant la variable `bin/magento config:show services_connector/services_id/environment_id` . Voir le champ &quot;Espace de données&quot; dans [Services de commerce](https://docs.magento.com/user-guide/configuration/services/saas.html) |
| `Magento-Store-Code` | Code affecté au magasin associé à la principale vue de magasin. Par exemple, `main_website_store`. |
| `Magento-Store-View-Code` | Code affecté à la principale vue de magasin. Par exemple, `default`. |
| `Magento-Website-Code` | Code affecté au site web associé à la principale vue de magasin. Par exemple, `base`. |
| `X-Api-Key` | Clé unique générée lors du processus d’intégration. |

## Exemple d’utilisation

Dans l&#39;exemple suivant, la requête renvoie des informations sur les mêmes produits que l&#39;exemple précédent. Cependant, il a été créé pour renvoyer des informations d’élément dans le service de catalogue. `productView` au lieu de l’objet principal `product` . Notez que les informations sur les prix varient en fonction du type de produit. Par souci de concision, les informations de facette ne sont pas affichées.

**Requête :**

```graphql
{
  productSearch(
    phrase: "bag"
    sort: [
      {
        attribute: "price"
        direction: DESC }]
    page_size: 9
  ) {
    page_info {
      current_page
      page_size
      total_pages
    }
    items {
      productView {
        name
        sku
        ... on SimpleProductView {
          price {
            final {
              amount {
                value
                currency
              }
            }
            regular {
              amount {
                value
                currency
              }
            }
          }
        }
        ... on ComplexProductView {
          options {
            id
            title
            required
            values {
              id
              title
            }
          }
          priceRange {
            maximum {
              final {
                amount {
                  value
                  currency
                }
              }
              regular {
                amount {
                  value
                  currency
                }
              }
            }
            minimum {
              final {
                amount {
                  value
                  currency
                }
              }
              regular {
                amount {
                  value
                  currency
                }
              }
            }
          }
        }
      }
    }
  }
}
```

**Réponse :**

```json
{
  "data": {
    "productSearch": {
      "page_info": {
        "current_page": 1,
        "page_size": 9,
        "total_pages": 3
      },
      "items": [
        {
          "productView": {
            "name": "Impulse Duffle",
            "sku": "24-UB02",
            "price": {
              "final": {
                "amount": {
                  "value": 74,
                  "currency": "USD"
                }
              },
              "regular": {
                "amount": {
                  "value": 74,
                  "currency": "USD"
                }
              }
            }
          }
        },
        {
          "productView": {
            "name": "Fusion Backpack 567890",
            "sku": "24-MB02",
            "price": {
              "final": {
                "amount": {
                  "value": 59,
                  "currency": "USD"
                }
              },
              "regular": {
                "amount": {
                  "value": 59,
                  "currency": "USD"
                }
              }
            }
          }
        },
        {
          "productView": {
            "name": "Rival Field Messenger",
            "sku": "24-MB06",
            "price": {
              "final": {
                "amount": {
                  "value": 45,
                  "currency": "USD"
                }
              },
              "regular": {
                "amount": {
                  "value": 45,
                  "currency": "USD"
                }
              }
            }
          }
        },
        {
          "productView": {
            "name": "Push It Messenger Bag",
            "sku": "24-WB04",
            "price": {
              "final": {
                "amount": {
                  "value": 45,
                  "currency": "USD"
                }
              },
              "regular": {
                "amount": {
                  "value": 45,
                  "currency": "USD"
                }
              }
            }
          }
        },
        {
          "productView": {
            "name": "Overnight Duffle",
            "sku": "24-WB07",
            "price": {
              "final": {
                "amount": {
                  "value": 45,
                  "currency": "USD"
                }
              },
              "regular": {
                "amount": {
                  "value": 45,
                  "currency": "USD"
                }
              }
            }
          }
        },
        {
          "productView": {
            "name": "Wayfarer Messenger Bag 987",
            "sku": "24-MB05",
            "price": {
              "final": {
                "amount": {
                  "value": 44,
                  "currency": "USD"
                }
              },
              "regular": {
                "amount": {
                  "value": 44,
                  "currency": "USD"
                }
              }
            }
          }
        },
        {
          "productView": {
            "name": "Driven Backpack",
            "sku": "24-WB03",
            "price": {
              "final": {
                "amount": {
                  "value": 36,
                  "currency": "USD"
                }
              },
              "regular": {
                "amount": {
                  "value": 36,
                  "currency": "USD"
                }
              }
            }
          }
        }
      ]
    }
  }
}
```
