---
title: Personnaliser
description: Découvrez comment personnaliser vos recommandations de produits.
exl-id: b1b8e770-45ec-4403-b79b-4f0a9f7bd959
source-git-commit: a34c3c8a5caca1bbf611b2df650c562aeeab297b
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Personnaliser

Lorsque vous installez le module Recommendations de produit, Adobe Commerce crée la variable `ProductRecommendationsLayout` répertoire . Ce répertoire contient des fichiers de modèle que vous pouvez personnaliser pour modifier l’affichage des recommandations sur votre vitrine. Plus précisément, vous pouvez modifier ou remplacer le modèle suivant :

`<your theme>/Magento_ProductRecommendationsLayout/web/template/recommendations.html`

Pour plus d’informations sur la modification des fichiers de modèle, reportez-vous à la section [Personnalisation des modèles](https://developer.adobe.com/commerce/frontend-core/guide/templates/walkthrough/) dans le guide de développement de Frontend.

Si vous modifiez la variable `recommendations.html` , vous devez conserver les balises suivantes dans le fichier pour vous assurer qu’Adobe Commerce peut collecter des mesures de recommandation à partir de votre vitrine :

| Balise | Utilisation |
|---|---|
| `<div data-bind="attr : {'data-unit-id' : unitId }"...</div>` | Collecte les événements d’affichage. |
| `<a data-bind="attr : {'data-sku' : sku, 'data-unit-id'}"...</a>` | Collecte les événements de clic. <br/>**Remarque :** Si vous ajoutez des balises d’ancrage, vous devez inclure ces attributs. |

En plus de la variable `recommendations.html` , `ProductRecommendationsLayout` contient les sous-répertoires suivants :

| Répertoire | Objectif |
|---|---|
| `layout` | Contient `*.xml` fichiers pour chaque type de page ; |
| `templates` | Contient les fichiers qui appellent les scripts de récupération et de rendu |
| `web/js` | Contient les fichiers JavaScript qui récupèrent et affichent les recommandations pour votre magasin. |
| `web/template` | Contient le modèle pour la variable `magento/product-recommendations` module |

## Position de l’unité de recommandation

Lorsque vous [create](create.md) une recommandation, vous spécifiez la variable [location](placement.md) où il apparaît sur la page. Une unité de recommandation peut être placée en haut ou en bas du conteneur de contenu principal. Vous pouvez toutefois personnaliser cet emplacement. Si vous créez un type de contenu de recommandation Page Builder , utilisez les outils Page Builder pour positionner l’unité de recommandation sur la page. Pour tous les autres types de page, modifiez la variable `*.xml` fichiers générés lors de la création de la recommandation.

1. Changement de la variable `layout` directory:

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
   >Les noms de fichier dans la variable `layout` peut être différent si votre magasin utilise des extensions tierces.

1. Modifions le `catalog_product_view.xml` afin que l’unité de recommandation s’affiche après l’image du produit sur la page des détails du produit. Avant de personnaliser ce fichier XML, jetons un coup d’oeil au fichier et comprenez les sections à modifier :

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

   Dans le fragment de code ci-dessus, la variable `main.content` le bloc de référence indique que l’unité de recommandation sera placée quelque part par rapport à cet élément. Son `block` contient l’élément `after="-"` qui spécifie que l’unité de recommandation s’affiche sur la page après le bloc de contenu principal.

1. Modifions ce fichier en spécifiant un autre bloc de contenu.

   Vous allez modifier le bloc de référence. `name` de `main.content` to `product.info.media`.

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

   Cette modification entraîne l’affichage de votre unité de recommandation après l’image du produit sur la page des détails du produit. Si vous souhaitez que l’unité de recommandation apparaisse avant l’événement `product.info.media`, modifiez la variable `after="-"` Attribuer à `before="-"`. Le `pagePlacement` est un argument interne qui ne doit pas être modifié.

Voir [présentation de la disposition](https://developer.adobe.com/commerce/frontend-core/guide/layouts/) pour plus d’informations sur les types de blocs dans la page.

## Attributs de produit personnalisés

Les développeurs ont souvent besoin d’accéder aux valeurs d’attribut de produit personnalisées dans les unités de recommandations sur les vitrines afin de pouvoir ajouter des traitements visuels aux produits en fonction de ces attributs.

Par exemple, si votre boutique vend des produits organiques, vous pouvez avoir un attribut personnalisé sur ces produits en les désignant comme `Organic = Yes`. Vous devrez peut-être accéder à cette valeur d’attribut sur le storefront afin de pouvoir offrir à ces produits un traitement visuel spécial lorsqu’ils apparaissent dans Recommendations. De même, l’accès à ces valeurs d’attribut de produit personnalisées vous permet de marquer des produits ou de générer une logique personnalisée dans la couche de présentation de votre site.

![Ajouter un badge](assets/unit-custom.png)

Pour vous assurer qu’un attribut de produit personnalisé est disponible lorsque vous effectuez le rendu de l’unité de recommandation sur la page, définissez la variable `Used in Product Listing` de `Yes` dans le [Attributs de produit](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/attribute-product-create.html) dans Admin.

Lorsque cette propriété est définie, la charge utile JSON inclut une `attributes` contenant un tableau de codes d’attributs et de valeurs. Vous pouvez ensuite appliquer un style personnalisé de storefront en fonction de ces valeurs d’attribut, comme l’ajout de traitements visuels spéciaux ou de badges comme mentionné précédemment.

>[!NOTE]
>
>Les modifications d’attributs de produit peuvent prendre jusqu’à une heure pour apparaître dans la charge utile JSON.
