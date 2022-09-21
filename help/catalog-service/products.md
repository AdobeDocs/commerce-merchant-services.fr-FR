---
title: requête products
description: '"Guide de référence pour la requête GraphQL "products" pour Adobe Commerce Catalog Service."'
source-git-commit: 7edfdd71c0900a6bdc7c064a29a6cce405a361ab
workflow-type: tm+mt
source-wordcount: '1226'
ht-degree: 0%

---


# requête products

Service de catalogue pour Adobe Commerce `products` La requête renvoie des détails sur les SKU spécifiés en tant qu’entrée. Bien que cette requête porte le même nom que le champ [`products` query](https://devdocs.magento.com//guides/v2.4/graphql/queries/products.html) qui est fourni avec Adobe Commerce principal et Magento Open Source, il existe des différences.

La requête du service de catalogue requiert une ou plusieurs valeurs de SKU en entrée. La requête est principalement conçue pour récupérer des informations afin de générer les types de contenu suivants :

* Pages des détails du produit : vous pouvez fournir des détails complets sur le produit identifié par le SKU spécifié.

* Pages de comparaison des produits : vous pouvez récupérer les informations sélectionnées sur plusieurs produits, tels que le nom, le prix et l’image.

Le `ProductView` L’objet de sortie est significativement différent du noyau `products` query `Products` objet output. Les principales différences sont les suivantes :

* Les produits sont simples ou complexes. Les produits de carte cadeau, simples, virtuels et téléchargeables sont mappés à `SimpleProductView`. Tous les autres types de produit sont mappés sur `ComplexProductView`. Les produits simples ont des prix définis. Les produits complexes ont des plages de prix. Comme les produits complexes sont composés de plusieurs produits simples, ils ont accès à des prix de produits simples.

* Les attributs définis par le détaillant sont exposés dans un conteneur de niveau supérieur et indiquent leurs rôles de storefront. Les rôles incluent Afficher sur PDP, Afficher sur PLP et Afficher sur les résultats de recherche.

* Les images sont également accessibles en tant que conteneur de niveau supérieur et peuvent être filtrées selon leur rôle. Une image peut avoir un rôle de base, de petite taille ou de miniature.

## Syntaxe

```graphql
products (skus [String]) [ProductView]
```

## En-têtes requis

Vous devez spécifier les en-têtes HTTP suivants pour exécuter cette requête.

| En-tête | Description |
| --- | --- |
| `Magento-Customer-Group` | Pour les clients storefront, cette valeur sera disponible au niveau du storefront dans la variable `dataservices_customer_group` du cookie. |
| `Magento-Environment-Id` | Cette valeur s’affiche à l’adresse **Système** > **Connecteur Commerce Services** > **Identifiant SaaS** > **Identifiant d’espace de données** ou peut être obtenu en exécutant la fonction `bin/magento config:show services_connector/services_id/environment_id` . |
| `Magento-Store-Code` | Code affecté au magasin associé à la principale vue de magasin. Par exemple, `main_website_store`. |
| `Magento-Store-View-Code` | Code affecté à la principale vue de magasin. Par exemple, `default`. |
| `Magento-Website-Code` | Code affecté au site web associé à la principale vue de magasin. Par exemple, `base`. |
| `X-Api-Key` | Clé unique générée lors du processus d’intégration. |

## Exemple d’utilisation

### Renvoi de détails sur un produit simple

La requête suivante renvoie des détails sur un produit simple.

**Requête :**

```graphql
query {
  products(skus: ["24-MB02"]) {
    id
    sku
    name
    url
    description
    shortDescription
    attributes(roles: ["visible in Search"]) {
      name
      label
      value
      roles
    }
    ... on SimpleProductView {
      price {
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
```

**Réponse :**

```json
{
  "data": {
    "products": [
      {
        "id": "TWpRdFRVSXdNZwBaR1ZtWVhWc2RBAE16UmxNamMwTUdFdE56UTNNeTAwWXpnNUxUZzNNekF0TlRjME1ETm1ZMlV5TjJGbABiV0ZwYmw5M1pXSnphWFJsWDNOMGIzSmwAWW1GelpRAFRVRkhVMVJITURBMU5UYzVNRE00",
        "sku": "24-MB02",
        "name": "Fusion Backpack 567890",
        "url": "http://example.com/fusion-backpack.html",
        "description": "<p>With the Fusion Backpack strapped on, every trek is an adventure - even a bus ride to work. That's partly because two large zippered compartments store everything you need, while a front zippered pocket and side mesh pouches are perfect for stashing those little extras, in case you change your mind and take the day off.</p>\r\n<ul>\r\n<li>Durable nylon construction.</li>\r\n<li>2 main zippered compartments.</li>\r\n<li>1 exterior zippered pocket.</li>\r\n<li>Mesh side pouches.</li>\r\n<li>Padded, adjustable straps.</li>\r\n<li>Top carry handle.</li>\r\n<li>Dimensions: 18\" x 10\" x 6\".</li>\r\n</ul>",
        "shortDescription": "",
        "attributes": [
          {
            "name": "activity",
            "label": "Activity",
            "value": [
              "Hiking",
              "School",
              "Yoga"
            ],
            "roles": [
              "visible in PDP",
              "visible in compare list",
              "visible in Search"
            ]
          },
          {
            "name": "features_bags",
            "label": "Features",
            "value": [
              "Hydration Pocket",
              "Audio Pocket",
              "Waterproof",
              "Lightweight"
            ],
            "roles": [
              "visible in PDP",
              "visible in Search"
            ]
          },
          {
            "name": "material",
            "label": "Material",
            "value": [
              "Burlap",
              "Nylon",
              "Polyester"
            ],
            "roles": [
              "visible in PDP",
              "visible in Search"
            ]
          },
          {
            "name": "strap_bags",
            "label": "Strap/Handle",
            "value": [
              "Adjustable",
              "Double",
              "Padded"
            ],
            "roles": [
              "visible in PDP",
              "visible in Search"
            ]
          },
          {
            "name": "style_bags",
            "label": "Style Bags",
            "value": [
              "Backpack",
              "Laptop"
            ],
            "roles": [
              "visible in PDP",
              "visible in Search"
            ]
          }
        ],
        "price": {
          "regular": {
            "amount": {
              "value": 59,
              "currency": "USD"
            }
          }
        }
      }
    ]
  }
}
```

### Renvoi de détails sur un produit complexe {#complex-product-example}

La requête suivante renvoie des détails sur un produit configurable.

**Requête :**

```graphql
query {
  products(skus: ["MH12"]) {
    __typename
    id
    sku
    name
    url
    description
    shortDescription
    attributes(roles: ["visible in Search"]) {
      name
      label
      value
      roles
    }
    ... on ComplexProductView {
      priceRange {
        maximum {
          regular {
            amount {
              value
              currency
            }
          }
        }
        minimum {
          regular {
            amount {
              value
              currency
            }
          }
        }
      }
      options {
        id
        required
        title
        values {
          id
          title
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
    "products": [
      {
        "__typename": "ComplexProductView",
        "id": "VFVneE1nAFpHVm1ZWFZzZEEATXpSbE1qYzBNR0V0TnpRM015MDBZemc1TFRnM016QXROVGMwTURObVkyVXlOMkZsAGJXRnBibDkzWldKemFYUmxYM04wYjNKbABZbUZ6WlEAVFVGSFUxUkhNREExTlRjNU1ETTQ",
        "sku": "MH12",
        "name": "Ajax Full-Zip Sweatshirt 2",
        "url": "http://example.com/ajax-full-zip-sweatshirt.html",
        "description": "<p>The Ajax Full-Zip Sweatshirt makes the optimal layering or outer piece for archers, golfers, hikers and virtually any other sportsmen. Not only does it have top-notch moisture-wicking abilities, but the tight-weave fabric also prevents pilling from repeated wash-and-wear cycles.</p>\r\n<p>&bull; Mint striped full zip hoodie.<br />&bull; 100% bonded polyester fleece.<br />&bull; Pouch pocket.<br />&bull; Rib cuffs and hem. <br />&bull; Machine washable.</p>",
        "shortDescription": "",
        "attributes": [
          {
            "name": "climate",
            "label": "Climate",
            "value": [
              "All-Weather",
              "Cool",
              "Indoor",
              "Spring",
              "Windy"
            ],
            "roles": [
              "visible in PDP",
              "visible in Search"
            ]
          },
          {
            "name": "customattribute",
            "label": "customAttribute",
            "value": "asd",
            "roles": [
              "visible in PDP",
              "visible in PLP",
              "visible in Search"
            ]
          },
          {
            "name": "material",
            "label": "Material",
            "value": [
              "Fleece",
              "Polyester"
            ],
            "roles": [
              "visible in PDP",
              "visible in Search"
            ]
          },
          {
            "name": "pattern",
            "label": "Pattern",
            "value": "Striped",
            "roles": [
              "visible in PDP",
              "visible in Search"
            ]
          },
          {
            "name": "testtttattribute",
            "label": "testtttAttribute",
            "value": "asd",
            "roles": [
              "visible in PDP",
              "visible in PLP",
              "visible in Search"
            ]
          }
        ],
        "priceRange": {
          "maximum": {
            "regular": {
              "amount": {
                "value": 69,
                "currency": "USD"
              }
            }
          },
          "minimum": {
            "regular": {
              "amount": {
                "value": 69,
                "currency": "USD"
              }
            }
          }
        },
        "options": [
          {
            "id": "color",
            "required": false,
            "title": "Color",
            "values": [
              {
                "id": "Y29uZmlndXJhYmxlLzkzLzU5",
                "title": "Blue"
              },
              {
                "id": "Y29uZmlndXJhYmxlLzkzLzY3",
                "title": "Red"
              },
              {
                "id": "Y29uZmlndXJhYmxlLzkzLzYy",
                "title": "Green"
              }
            ]
          },
          {
            "id": "size",
            "required": false,
            "title": "Size",
            "values": [
              {
                "id": "Y29uZmlndXJhYmxlLzE4Ni8xNzU=",
                "title": "XS"
              },
              {
                "id": "Y29uZmlndXJhYmxlLzE4Ni8xNzY=",
                "title": "S"
              },
              {
                "id": "Y29uZmlndXJhYmxlLzE4Ni8xNzc=",
                "title": "M"
              },
              {
                "id": "Y29uZmlndXJhYmxlLzE4Ni8xNzg=",
                "title": "L"
              },
              {
                "id": "Y29uZmlndXJhYmxlLzE4Ni8xNzk=",
                "title": "XL"
              }
            ]
          }
        ]
      }
    ]
  }
}
```

## Champs de sortie

Le `ProductView` L’objet return est une interface qui peut contenir les champs suivants. Elle est implémentée par la fonction [`SimpleProductView`](#SimpleProductView-type) et [`ComplexProductView`](#ComplexProductView-type) types.

| Champ | Type de données | Description |
|--- | --- | ---|
| `attributes(roles: [String])` | [ProductViewAttribute] | Une liste d’attributs définis par le commerce désignés pour le storefront. |
| `description` | Chaîne | Description détaillée du produit. |
| `id` | Identifiant ! | ID de produit, généré sous la forme d’une clé composite, unique par paramètre régional. |
| `images(roles: [String])` | [ProductViewImage] | Liste d’images définies pour le produit. |
| `metaDescription` | Chaîne | Aperçu rapide du produit pour les listes de résultats de recherche. |
| `metaKeyword` | Chaîne | Liste de mots-clés séparés par des virgules et visibles uniquement par les moteurs de recherche. |
| `metaTitle` | Chaîne | Chaîne affichée dans la barre de titre et l’onglet du navigateur et dans les listes de résultats de recherche. |
| `name` | Chaîne | Nom du produit. |
| `shortDescription` | Chaîne | Résumé du produit. |
| `sku` | Chaîne | SKU du produit. |
| `url` | Chaîne | URL canonique du produit. |

### Type ComplexProductView {#ComplexProductView-type}

Le `ComplexProductView` type représente les produits groupés, configurables et de groupe. Des prix de produit complexes sont renvoyés sous la forme d’une plage de prix, car les valeurs de prix peuvent varier en fonction d’options sélectionnées. Le type implémente `ProductView`.

| Champ | Type de données | Description |
|--- | --- | ---|
| `attributes(roles: [String])` | [ProductViewAttribute] | Une liste d’attributs définis par le commerce désignés pour le storefront. |
| `description` | Chaîne | Description détaillée du produit. |
| `id` | Identifiant ! | ID de produit, généré sous la forme d’une clé composite, unique par paramètre régional. |
| `images(roles: [String])` | [ProductViewImage] | Liste d’images définies pour le produit. |
| `metaDescription` | Chaîne | Aperçu rapide du produit pour les listes de résultats de recherche. |
| `metaKeyword` | Chaîne | Liste de mots-clés séparés par des virgules et visibles uniquement par les moteurs de recherche. |
| `metaTitle` | Chaîne | Chaîne affichée dans la barre de titre et l’onglet du navigateur et dans les listes de résultats de recherche. |
| `name` | Chaîne | Nom du produit. |
| `options` | [ProductViewOption] | Liste des options sélectionnables. |
| `priceRange` | ProductViewPriceRange | Une gamme de prix possibles pour un produit complexe. |
| `shortDescription` | Chaîne | Résumé du produit. |

### Type de prix

Le `Price type` définit le prix d’un produit simple ou d’une partie d’une gamme de prix pour un produit complexe. Elle peut inclure une liste d’ajustements de prix.

| Champ | Type de données | Description |
|--- | --- | ---|
| `amount` | ProductViewMoney | Contient la valeur monétaire et le code de devise d’un produit. |

### Type PriceAdapter

Le `PriceAdjustment` type spécifie le montant et le type d’ajustement de prix. Un exemple de valeur de code est `weee`.

| Champ | Type de données | Description |
|--- | --- | ---|
| `amount` | Flottant | Montant de l&#39;ajustement de prix. |
| `code` | Chaîne | Identifie le type d’ajustement de prix. |

### Type ProductViewAttribute

Le `ProductViewAttribute` type est un conteneur pour les attributs définis par le client qui s’affichent dans le storefront.

| Champ | Type de données | Description |
|--- | --- | ---|
| `label` | Chaîne | Libellé de l’attribut. |
| `name` | Chaîne ! | Nom d’un code d’attribut. |
| `roles` | [Chaîne] | Rôles désignés pour un attribut sur le storefront, comme &quot;Afficher sur PLP&quot;, &quot;Afficher sur PDP&quot; ou &quot;Afficher dans la recherche&quot;. |
| `value` | JSON | Valeur d’attribut, arbitraire de type. |

### Type ProductViewImage

Le `ProductViewImage` type contient des détails sur une image de produit.

| Champ | Type de données | Description |
|--- | --- | ---|
| `label` | Chaîne | Libellé d’affichage de l’image du produit. |
| `roles` | [Chaîne] | Liste qui décrit l’utilisation de l’image. Peut être `image`, `small_image`ou `thumbnail`. |
| `url` | Chaîne ! | URL de l’image du produit. |

### Type ProductViewMoney

Le `ProductViewMoney` type définit une valeur monétaire, y compris une valeur numérique et un code de devise.

| Champ | Type de données | Description |
|--- | --- | ---|
| `currency` | ProductViewCurrency | Code de devise à trois lettres, tel que USD ou EUR. |
| `value` | Flottant | Nombre exprimant une valeur monétaire. |

### Type ProductViewOption

Les options de produit permettent de configurer des produits en effectuant des sélections de valeurs d’option spécifiques. La sélection d’une ou de plusieurs options pointe vers un produit simple spécifique.

| Champ | Type de données | Description |
|--- | --- | ---|
| `id` | ID | L’identifiant de l’option. |
| `multi` | Booléen | Indique si l’option autorise plusieurs choix. |
| `required` | Booléen | Indique si l’option doit être sélectionnée. |
| `title` | Chaîne | Nom d’affichage de l’option. |
| `values` | [ProductViewOptionValue!] | Liste des valeurs d’option disponibles. |

### Interface de ProductViewOptionValue

Le `ProductViewOptionValue` L’interface définit les champs de produit disponibles pour l’ `ProductViewOptionValueProduct` et `ProductViewOptionValueConfiguration` types.

| Champ | Type de données | Description |
|--- | --- | ---|
| `id` | ID | L’identifiant d’une valeur d’option. |
| `title` | Chaîne | Nom d’affichage de la valeur de l’option. |

### Type ProductViewOptionValueConfiguration

Le `ProductViewOptionValueConfiguration` type est une implémentation de `ProductViewOptionValue` pour les valeurs de configuration.

| Champ | Type de données | Description |
|--- | --- | ---|
| `id` | ID | L’identifiant d’une valeur d’option. |
| `title` | Chaîne | Nom d’affichage de la valeur de l’option. |

### Type ProductViewOptionValueProduct

Le `ProductViewOptionValueProduct` type est une implémentation de `ProductViewOptionValue` qui ajoute des détails sur un produit simple.

| Champ | Type de données | Description |
|--- | --- | ---|
| `id` | ID | L’identifiant d’une valeur d’option. |
| `title` | Chaîne | Nom d’affichage de la valeur de l’option. |
| `product` | SimpleProductView | Détails sur un produit simple. |

### Type ProductViewPrice

Le `ProductViewPrice` type fournit la vue du prix du produit de base, inhérente aux produits simples.

| Champ | Type de données | Description |
|--- | --- | ---|
| `final` | Prix | Valeur du prix après remises, à l’exception des promotions personnalisées. |
| `regular` | Prix | Prix de base du produit spécifié par le marchand. |
| `roles` | [Chaîne] | Détermine si le prix doit être visible ou masqué. |

### Type ProductViewPriceRange

Le `ProductViewPriceRange` type répertorie les prix minimum et maximum d’un produit complexe.

| Champ | Type de données | Description |
|--- | --- | ---|
| `maximum` | ProductViewPrice | Prix maximum. |
| `minimum` | ProductViewPrice | Prix minimum. |

### Type SimpleProductView {#SimpleProductView-type}

Le `SimpleProductView` type représente tous les types de produits, à l’exception de bundle, configurable et group. Les prix simples des produits ne contiennent pas de plages de prix. `SimpleProductView` implémente `ProductView`.

| Champ | Type de données | Description |
|--- | --- | ---|
| `attributes(roles: [String])` | [ProductViewAttribute] | Une liste d’attributs définis par le commerce désignés pour le storefront. |
| `description` | Chaîne | Description détaillée du produit. |
| `id` | Identifiant ! | ID de produit, généré sous la forme d’une clé composite, unique par paramètre régional. |
| `images(roles: [String])` | [ProductViewImage] | Liste d’images définies pour le produit. |
| `metaDescription` | Chaîne | Aperçu rapide du produit pour les listes de résultats de recherche. |
| `metaKeyword` | Chaîne | Liste de mots-clés séparés par des virgules et visibles uniquement par les moteurs de recherche. |
| `metaTitle` | Chaîne | Chaîne affichée dans la barre de titre et l’onglet du navigateur et dans les listes de résultats de recherche. |
| `name` | Chaîne | Nom du produit. |
| `price` | ProductViewPrice | Vue de prix du produit de base. |
| `shortDescription` | Chaîne | Résumé du produit. |
| `sku` | Chaîne | SKU du produit. |
| `url` | Chaîne | URL canonique du produit. |
