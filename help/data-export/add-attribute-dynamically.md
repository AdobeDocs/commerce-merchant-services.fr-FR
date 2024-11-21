---
title: Ajout d’attributs de produit par programmation au flux Data Exporter
description: Découvrez comment ajouter des attributs de produit personnalisés aux données de flux  [!DNL SaaS Data Export] .
role: Admin, Developer
source-git-commit: 06ef294d2670e5d36bbb6cd18deafce2cc751772
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---

# Ajout d’attributs de produit par programmation au flux Data Exporter

Vous pouvez étendre les attributs de produit sans les enregistrer dans Adobe Commerce en créant un module externe pour ajouter les attributs pendant le processus de synchronisation des données.

>[!NOTE]
>
>La meilleure façon d’étendre les attributs de produit est de [les ajouter à Adobe Commerce](extensibility-and-customizations.md#add-product-attributes-to-adobe-commerce) où vous pouvez les configurer et les gérer à partir de l’administrateur Commerce. Ajoutez-les de manière dynamique uniquement si vous en avez besoin uniquement pour les services de storefront Commerce et ne souhaitez pas les enregistrer dans Adobe Commerce. Vous avez également la possibilité de gérer des attributs personnalisés à l’aide de [Maillage d’API avec le service de catalogue](../catalog-service/mesh.md) pour étendre le schéma GraphQL du service de catalogue.

## Ajout d’attributs de produit

Créez un module externe qui ajoute un `customer_attribute` à la classe `Magento\CatalogDataExporter\Model\Provider\Product\Attributes`.

1. Mettez à jour le [fichier de configuration d’injection de dépendance](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/) (`di.xml`) pour définir le module externe.

   ```xml
   <type name="Magento\CatalogDataExporter\Model\Provider\Product\Attributes">
     <plugin name="product_customer_attributes" type="Vendor\CatalogDataExporter\Model\Plugin\AddAttribute"/>
   </type>
   ```

1. Créez le module externe .

   ```php
    <?php
    declare(strict_types=1);
   
    namespace Vendor\CatalogDataExporter\Model\Plugin;
   
    use Magento\CatalogDataExporter\Model\Provider\Product\Attributes;
   
    class AddAttribute {
   
         /**
          * @param Attributes $subject
          * @param array $result
          * @param $arguments
          * @return array
          * @throws \Zend_Db_Statement_Exception
          */
         public function afterGet(Attributes $subject, array $result, $arguments): array
         {
              $productIds = \array_column($arguments, 'productId');
   
              foreach ($productIds as $productId) {
                    $result[] = [
                         'productId' => $productId,
                         // "storeViewCode" must be specified for products where the customer attribute value should be set
                         'storeViewCode' => 'default',
                         'attributes' => [
                              // specify the customer attribute code
                              'attributeCode' => 'customer_attribute',
                              // provide single or multiple values for the attribute
                              'value' => [
                                    rand(41,43)
                              ]
                         ]
                    ];
              }
   
              return $result;
         }
    }
   ```

   Une fois le module externe ajouté, les modifications sont synchronisées avec les services storefront connectés lors de la prochaine synchronisation planifiée. Pour envoyer immédiatement les mises à jour, utilisez la commande d’interface de ligne de commande suivante pour lancer manuellement le processus de synchronisation.

   ```
   bin/magento saas:resync --feed=products
   ```

## Déclarer les métadonnées d’attribut de produit personnalisé

Si vous créez dynamiquement un attribut de produit personnalisé et souhaitez l’utiliser pour l’affichage, la recherche ou le filtrage dans les services storefront, ajoutez les métadonnées d’attribut de produit pour configurer le comportement storefront.

1. Mettez à jour le [fichier de configuration d’injection de dépendance](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/) (`di.xml`) pour définir le module externe pour les métadonnées d’attribut de produit.

   ```xml
   <type name="\Magento\CatalogDataExporter\Model\Provider\ProductMetadata">
     <plugin name="product_customer_attributes_metadata" type="Vendor\CatalogDataExporter\Model\Plugin\AddAttributeMetadata"/>
   </type>
   ```

1. Créez le module externe auprès du fournisseur suivant `\Magento\CatalogDataExporter\Model\Provider\ProductMetadata`.

   Vérifiez `ProductAttributeMetadata` dans `vendor/magento/module-catalog-data-exporter/etc/et_schema.xml` pour les champs obligatoires.

   ```php
    <?php
    declare(strict_types=1);
   
    namespace Vendor\CatalogDataExporter\Model\Plugin;
   
    use Magento\CatalogDataExporter\Model\Provider\ProductMetadata;
   
    class AddAttributeMetadata {
   
         /**
          * @param ProductMetadata $subject
          * @param array $result
          * @param $arguments
          * @return array
          * @throws \Zend_Db_Statement_Exception
          */
         public function afterGet(ProductMetadata $subject, array $result, $arguments): array
         {
              $result[] = [
                'id' => '123',
                'storeCode' => 'default',
                'websiteCode' => 'base',
                'storeViewCode' => 'default',
                // specify the customer attribute code - should be the same as used in the products attributes plugin
                'attributeCode' => 'customer_attribute',
                // only product attributes are supported
                'attributeType' => 'catalog_product',
                // specify the data type
                'dataType' => 'int',
                'multi' => false,
                'label' => 'Customer Attribute',
                'frontendInput' => 'select',
                'required' => false,
                'unique' => false,
                'global' => true,
                'visible' => true,
                'searchable' => true,
                'filterable' => true,
                // This value must be set to true to export it to the storefront services
                'visibleInCompareList' => true,
                'visibleInListing' => true,
                'sortable' => true,
                'visibleInSearch' => true,
                'filterableInSearch' => true,
                'searchWeight' => 1.0,
                'usedForRules' => true,
                'boolean' => false,
                'systemAttribute' => false,
                'numeric' => false,
                // specify the list of attribute options
                'attributeOptions' => [
                    'option1',
                    'option2',
                    'option3'
                ]
             ];
   
              return $result;
         }
      }
   ```

   Une fois le module externe ajouté, les modifications sont synchronisées avec les services storefront connectés lors de la prochaine synchronisation planifiée. Pour envoyer immédiatement les mises à jour, utilisez la commande d’interface de ligne de commande suivante pour lancer manuellement le processus de synchronisation.

   ```
   bin/magento saas:resync --feed=productattributes
   ```




