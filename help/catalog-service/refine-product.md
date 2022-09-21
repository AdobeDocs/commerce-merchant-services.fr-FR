---
title: requête refineProduct
description: '"Guide de référence pour la requête GraphQL "refineProduct" pour le service de catalogue Adobe Commerce."'
source-git-commit: 7edfdd71c0900a6bdc7c064a29a6cce405a361ab
workflow-type: tm+mt
source-wordcount: '1267'
ht-degree: 0%

---


# requête refineProduct

Le `refineProduct` la requête narre les résultats d’une `products` requête exécutée sur un produit complexe. Avant d’exécuter la variable `refineProduct` requête, vous devez exécuter la fonction `products` requête et construction de la réponse afin qu’elle renvoie une liste de `options` dans `ComplexProductView` fragment intégré. Lorsqu’un acheteur sélectionne une option de produit (telle que la taille ou la couleur) sur le storefront, exécutez la variable `refineProduct` requête, en spécifiant le SKU et les identifiants de valeur d’option sélectionnés comme entrée. Selon le nombre d’options de produit du produit complexe, vous devrez peut-être exécuter la variable `refineProduct` interroger plusieurs fois, jusqu’à ce que l’acheteur ait sélectionné une variante spécifique.

Vous devez construire la réponse de votre requête afin qu’elle contienne à la fois la variable `ComplexProductView` et `SimpleProductView` fragments intégrés. Si l’acheteur n’a pas sélectionné toutes les options requises, la requête renvoie les identifiants des options non sélectionnées et le prix minimal et maximal du produit, en fonction des options sélectionnées et des options restantes possibles. Si l’acheteur a sélectionné toutes les options requises, la requête renvoie des détails sur un produit simple, qui inclut un prix fixe.

## Syntaxe

```graphql
refineProduct(sku: String!, optionIds: [String!]!): ProductView
```

## En-têtes requis

Vous devez spécifier les en-têtes HTTP suivants pour exécuter cette requête.

| En-tête | Description |
|--- | ---|
| `Magento-Customer-Group` | Pour les clients storefront, cette valeur sera disponible au niveau du storefront dans la variable `dataservices_customer_group` du cookie. |
| `Magento-Environment-Id` | Cette valeur s’affiche à l’adresse **Système** > **Connecteur Commerce Services** > **Identifiant SaaS** > **Identifiant d’espace de données** ou peut être obtenu en exécutant la fonction `bin/magento config:show services_connector/services_id/environment_id` . |
| `Magento-Store-Code` | Code affecté au magasin associé à la principale vue de magasin. Par exemple, `main_website_store`. |
| `Magento-Store-View-Code` | Code affecté à la principale vue de magasin. Par exemple, `default`. |
| `Magento-Website-Code` | Code affecté au site web associé à la principale vue de magasin. Par exemple, `base`. |
| `X-Api-Key` | Clé unique générée lors du processus d’intégration. |

## Exemple d’utilisation

### Renvoie les détails d’un produit complexe partiellement sélectionné

La requête suivante renvoie des détails sur les options de couleur disponibles pour une variante de taille moyenne d’un produit. `MH12`. La valeur de la variable `optionIDs` Le paramètre d’entrée est extrait de la propriété `products` requête [Renvoi de détails sur un produit complexe](products.md#complex-product-example) par exemple.

**Requête :**

```graphql
query {
    refineProduct(optionIds: ["Y29uZmlndXJhYmxlLzE4Ni8xNzc="], sku: "MH12") {
        __typename
        id
        sku
        name
        url
        ... on SimpleProductView {
            price {
                final {
                    amount {
                        value
                    }
                }
                regular {
                    amount {
                        value
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
                        }
                    }
                    regular {
                        amount {
                            value
                        }
                    }
                }
                minimum {
                    final {
                        amount {
                            value
                        }
                    }
                    regular {
                        amount {
                            value
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
    "refineProduct": {
      "__typename": "ComplexProductView",
      "id": "VFVneE1nAFpHVm1ZWFZzZEEATXpSbE1qYzBNR0V0TnpRM015MDBZemc1TFRnM016QXROVGMwTURObVkyVXlOMkZsAGJXRnBibDkzWldKemFYUmxYM04wYjNKbABZbUZ6WlEAVFVGSFUxUkhNREExTlRjNU1ETTQ",
      "sku": "MH12",
      "name": "Ajax Full-Zip Sweatshirt 2",
      "url": "http://example.com/ajax-full-zip-sweatshirt.html",
      "options": [
        {
          "id": "color",
          "title": "Color",
          "required": false,
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
        }
      ],
      "priceRange": {
        "maximum": {
          "final": {
            "amount": {
              "value": 69
            }
          },
          "regular": {
            "amount": {
              "value": 69
            }
          }
        },
        "minimum": {
          "final": {
            "amount": {
              "value": 69
            }
          },
          "regular": {
            "amount": {
              "value": 69
            }
          }
        }
      }
    }
  }
}
```

### Renvoie les détails d’un produit complexe entièrement sélectionné

Dans la requête suivante, l’acheteur a sélectionné des options pour la taille et la couleur. La réponse contient des détails sur le produit simple correspondant.

**Requête :**

```graphql
query {
    refineProduct(optionIds: ["Y29uZmlndXJhYmxlLzE4Ni8xNzc=", "Y29uZmlndXJhYmxlLzkzLzU5"], sku: "MH12") {
        __typename
        id
        sku
        name
        url
        ... on SimpleProductView {
            price {
                final {
                    amount {
                        value
                    }
                }
                regular {
                    amount {
                        value
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
                        }
                    }
                    regular {
                        amount {
                            value
                        }
                    }
                }
                minimum {
                    final {
                        amount {
                            value
                        }
                    }
                    regular {
                        amount {
                            value
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
    "refineProduct": {
      "__typename": "SimpleProductView",
      "id": "VFVneE1pMU5MVUpzZFdVAFpHVm1ZWFZzZEEATXpSbE1qYzBNR0V0TnpRM015MDBZemc1TFRnM016QXROVGMwTURObVkyVXlOMkZsAGJXRnBibDkzWldKemFYUmxYM04wYjNKbABZbUZ6WlEAVFVGSFUxUkhNREExTlRjNU1ETTQ",
      "sku": "MH12-M-Blue",
      "name": "Ajax Full-Zip Sweatshirt -M-Blue",
      "url": "http://example.com/catalog/product/view/id/235/s/ajax-full-zip-sweatshirt-m-blue/",
      "price": {
        "final": {
          "amount": {
            "value": 69
          }
        },
        "regular": {
          "amount": {
            "value": 69
          }
        }
      }
    }
  }
}
```

## Champs de saisie

Vous devez spécifier une valeur de SKU et au moins un identifiant d’option en tant qu’entrée.

| Champ | Type de données | Description |
|--- | --- | ---|
| `optionIds` | [Chaîne !]! | Liste des identifiants affectés aux options de produit sélectionnées par l’acheteur, telles que les couleurs et tailles spécifiques. |
| `sku` | Chaîne ! | SKU d’un produit complexe. |

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
