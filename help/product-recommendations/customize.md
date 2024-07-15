---
title: Personnaliser
description: Découvrez comment personnaliser vos recommandations de produits.
exl-id: b1b8e770-45ec-4403-b79b-4f0a9f7bd959
source-git-commit: acfaa1d72265e42b973677a7e014ba4b350ec56b
workflow-type: tm+mt
source-wordcount: '620'
ht-degree: 0%

---

# Personnaliser

Lorsque vous installez le module Recommendations de produit, Adobe Commerce crée le répertoire `ProductRecommendationsLayout`. Ce répertoire contient des fichiers de modèle que vous pouvez personnaliser pour modifier l’affichage des recommandations sur votre vitrine. Plus précisément, vous pouvez modifier ou remplacer le modèle suivant :

`<your theme>/Magento_ProductRecommendationsLayout/web/template/recommendations.html`

Pour plus d’informations sur la modification des fichiers de modèle, reportez-vous à la section [Personnalisation des modèles](https://developer.adobe.com/commerce/frontend-core/guide/templates/walkthrough/) du Guide du développeur de Frontend.

Si vous modifiez le fichier `recommendations.html`, vous devez conserver les balises suivantes dans le fichier pour vous assurer qu’Adobe Commerce peut collecter des mesures de recommandation à partir de votre vitrine :

| Balise | Utilisation |
|---|---|
| `<div data-bind="attr : {'data-unit-id' : unitId }"...</div>` | Collecte les événements d’affichage. |
| `<a data-bind="attr : {'data-sku' : sku, 'data-unit-id'}"...</a>` | Collecte les événements de clic. <br/>**Remarque :** Si vous ajoutez des balises d’ancrage, vous devez inclure ces attributs. |

Outre le fichier `recommendations.html`, le répertoire `ProductRecommendationsLayout` contient les sous-répertoires suivants :

| Répertoire | Objectif |
|---|---|
| `layout` | Contient `*.xml` fichiers pour chaque type de page |
| `templates` | Contient les fichiers qui appellent les scripts de récupération et de rendu |
| `web/js` | Contient les fichiers JavaScript qui récupèrent et effectuent le rendu des recommandations pour votre magasin |
| `web/template` | Contient le modèle pour le module `magento/product-recommendations` |

## Position de l’unité de recommandation

Lorsque vous [créez](create.md) une recommandation, vous spécifiez l’ [emplacement](placement.md) où elle apparaît sur la page. Une unité de recommandation peut être placée en haut ou en bas du conteneur de contenu principal. Vous pouvez toutefois personnaliser cet emplacement. Si vous créez un type de contenu de recommandation Page Builder , utilisez les outils Page Builder pour positionner l’unité de recommandation sur la page. Pour tous les autres types de page, modifiez les fichiers `*.xml` générés lors de la création de la recommandation.

1. Accédez au répertoire `layout` :

   ```bash
   cd `<your theme>/Magento_ProductRecommendationsLayout/layout`
   ```

   Le tableau suivant répertorie les fichiers XML présents dans ce répertoire :

   | Nom du fichier | Page |
   |---|---|
   | `catalog_category_view.xml` | Catégorie |
   | `catalog_product_view.xml` | Détails du produit |
   | `checkout_cart_index.xml` | Panier |
   | `checkout_onepage_success.xml` | Passage en caisse |
   | `cms_index_index.xml` | Accueil |

   >[!NOTE]
   >
   >Les noms de fichier dans le répertoire `layout` peuvent être différents si votre magasin utilise des extensions tierces.

1. Modifiez le fichier `catalog_product_view.xml` afin que l’unité de recommandation apparaisse après l’image du produit sur la page des détails du produit. Avant de personnaliser ce fichier XML, consultez le fichier et comprenez les sections à modifier :

   ```xml
   <?xml version="1.0"?>
   <page xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:View/Layout/etc/page_configuration.xsd">
       <referenceBlock name="page.wrapper">
           <block class="Magento\Framework\View\Element\Template" before="-" name="product_recommendations_fetcher" template="Magento_ProductRecommendationsStorefront::fetcher.phtml" />
       </referenceBlock>
       <body>
           <referenceBlock name="main.content">
               <block class="Magento\ProductRecommendationsStorefront\Block\Renderer" after="-" name="product_recommendations_product_below_content" template="Magento_ProductRecommendationsStorefront::renderer.phtml">
                   <arguments>
                       <argument name="pagePlacement" xsi:type="string">below-main-content</argument>
                   </arguments>
               </block>
           </referenceBlock>
       </body>
   </page>
   ```

   Dans le fragment de code ci-dessus, le bloc de référence `main.content` indique que l’unité de recommandation sera placée quelque part par rapport à cet élément. Son élément `block` contient l’attribut `after="-"` qui spécifie que l’unité de recommandation sera affichée sur la page après le bloc de contenu principal.

1. Modifions ce fichier en spécifiant un autre bloc de contenu.

   Remplacez le bloc de référence `name` de `main.content` par `product.info.media`.

   ```xml
   <?xml version="1.0"?>
   <page xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:View/Layout/etc/page_configuration.xsd">
       <referenceBlock name="page.wrapper">
           <block class="Magento\Framework\View\Element\Template" before="-" name="product_recommendations_fetcher" template="Magento_ProductRecommendationsStorefront::fetcher.phtml" />
       </referenceBlock>
       <body>
           <referenceBlock name="product.info.media">
               <block class="Magento\ProductRecommendationsStorefront\Block\Renderer" after="-" name="product_recommendations_product_below_content" template="Magento_ProductRecommendationsStorefront::renderer.phtml">
                   <arguments>
                       <argument name="pagePlacement" xsi:type="string">below-main-content</argument>
                   </arguments>
               </block>
           </referenceBlock>
       </body>
   </page>
   ```

   Cette modification entraîne l’affichage de votre unité de recommandation après l’image du produit sur la page des détails du produit. Si vous souhaitez que l’unité de recommandation apparaisse avant `product.info.media`, remplacez l’attribut `after="-"` par `before="-"`. L’argument `pagePlacement` est un argument interne qui ne doit pas être modifié.

Pour plus d’informations sur les types de blocs sur la page, reportez-vous à la section [présentation de la mise en page](https://developer.adobe.com/commerce/frontend-core/guide/layouts/) .

## Attributs de produit personnalisés

Les développeurs ont souvent besoin d’accéder aux valeurs d’attribut de produit personnalisées dans les unités de recommandations sur les vitrines afin de pouvoir ajouter des traitements visuels aux produits en fonction de ces attributs.

Par exemple, si votre boutique vend des produits organiques, vous pouvez disposer d’un attribut personnalisé sur ces produits les désignant comme `Organic = Yes`. Vous devrez peut-être accéder à cette valeur d’attribut sur le storefront afin de pouvoir offrir à ces produits un traitement visuel spécial lorsqu’ils apparaissent dans Recommendations. De même, l’accès à ces valeurs d’attribut de produit personnalisées vous permet de marquer des produits ou de générer une logique personnalisée dans la couche de présentation de votre site.

![Ajouter un badge](assets/unit-custom.png)

Pour vous assurer qu’un attribut de produit personnalisé est disponible lorsque vous effectuez le rendu de l’unité de recommandation sur la page, définissez la propriété `Used in Product Listing` sur `Yes` dans la page [Attributs du produit](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/attribute-product-create.html) de l’administrateur.

Lorsque cette propriété est définie, la charge utile JSON inclut un objet `attributes` qui contient un tableau de codes et de valeurs d’attribut. Vous pouvez ensuite appliquer un style personnalisé de storefront en fonction de ces valeurs d’attribut, comme l’ajout de traitements visuels spéciaux ou de badges comme mentionné précédemment.

>[!NOTE]
>
>Les modifications d’attributs de produit peuvent prendre jusqu’à une heure pour apparaître dans la charge utile JSON.
