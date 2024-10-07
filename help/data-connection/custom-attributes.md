---
title: Ajout d’attributs de commande personnalisés
description: Découvrez comment ajouter des attributs de commande personnalisés à vos données de back-office et envoyer ces attributs à l’Experience Platform.
role: Admin, Developer
feature: Personalization, Integration
source-git-commit: 14d190726324e2f42d66c2270f2e27be5a74132f
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 2%

---

# Ajout d’attributs de commande personnalisés

Dans cet article, vous apprenez à ajouter des attributs personnalisés aux événements back-office. Avec les attributs personnalisés, vous pouvez capturer des informations riches sur les données afin d’améliorer les analyses et de créer davantage d’expériences personnalisées pour vos acheteurs.

Les attributs personnalisés sont pris en charge à deux niveaux :

- Niveau de commande
- Niveau de l’élément de commande

>[!NOTE]
>
>Adobe [!DNL Commerce] prend en charge les attributs personnalisés ayant un type de données chaîne, booléen ou date.

L’ajout d’attributs personnalisés aux événements back-office requiert que vous :

1. Créez un projet dans votre installation [!DNL Commerce].
1. Mettez à jour votre schéma afin que les nouveaux attributs personnalisés puissent être correctement ingérés dans Experience Platform.
1. Dans Admin, vérifiez que les attributs personnalisés sont capturés et envoyés à l’Experience Platform.

>[!IMPORTANT]
>
>La structure de répertoire et les exemples de code ci-dessous illustrent la manière dont vous pouvez implémenter des attributs personnalisés. La structure de répertoire et le code réels requis dépendent de la configuration et de l’environnement de votre magasin.

## Etape 1 : création de la structure de répertoire

1. Accédez au répertoire `app/code` de votre installation [!DNL Commerce] et créez un répertoire de module. Par exemple : `Magento/AepCustomAttributes`. Ce répertoire contient les fichiers nécessaires à vos attributs personnalisés.
1. Dans le répertoire du module, créez un sous-répertoire appelé `etc`. Le répertoire `etc` contient les fichiers `module.xml`, `query.xml`, `di.xml` et `et_schema.xml`.

## Étape 2 : définir les dépendances et la version de configuration

Créez un fichier `module.xml` qui définit les dépendances et la version de configuration. Par exemple :

```xml
<?xml version="1.0"?>
<!--
/**
* Copyright (c) [year], [name]. All rights reserved.
*/
-->
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:Module/etc/module.xsd">
    <module name="Magento_SalesRuleStaging" setup_version="2.0.0">
        <sequence>
            <module name="Magento_Staging"/>
            <module name="Magento_SalesRule"/>
        </sequence>
    </module>
</config>
```

## Étape 3 : récupération des données de commande client

Créez un fichier `query.xml` qui récupère les données de commande client. Par exemple :

```xml
<query>
    <source name="sales_order" type="sales">
        <attribute name="increment_id" operator="eq" alias="order_increment_id"/>
        <link source="inventory_source_item" condition_type="by_sku"/>
    </source>
</query>
```

## Étape 4 : configuration de l’injection de dépendance

Créez un fichier `di.xml` qui configure l’injection de dépendance. Par exemple :

```xml
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
          package="com.example.instrumentedtest"
          android:versionCode="1"
          android:versionName="1.0">
    <uses-sdk android:minSdkVersion="8" android:targetSdkVersion="15"/>
    
    <instrumentation
        android:name=".MyInstrumentationTestRunner"
        android:targetPackage="com.example.instrumentedtest"/>
    
    <!-- More instrumentation elements might be here -->
</manifest>
```

## Étape 5 : définition des services utilisés pour l’injection de dépendance

Créez un fichier `et_schema.xml` qui définit les services utilisés pour l’injection de dépendance. Par exemple :

```xml
<services>
    <service id="App\Controller\MainController" class="App\Controller\MainController">
        <argument type="service" id="doctrine.orm.default_entity_manager"/>
        <argument type="service" id="form.factory"/>
        <argument type="service" id="security.authorization_checker"/>
    </service>

    <!-- ... -->

    <service id="App\Controller\SecurityController" class="App\Controller\SecurityController">
        <argument type="service" id="security.authentication_utils"/>
        <tag name="controller.service_arguments"/>
    </service>

    <!-- ... -->
</services>
```

## Étape 6 : création d’un répertoire pour les fichiers PHP

Au même niveau que le répertoire `etc`, créez un répertoire appelé `Module/Provider`. Ce répertoire contient les fichiers PHP `OrderCustomAttributes` et `OrderItemCustomAttributes`.

## Étape 7 : Définition des attributs OrderCustomAttributes

Créez un fichier `OrderCustomAttributes.php` qui définit les attributs personnalisés de commande. Par exemple :

```php
namespace App\Transformers;

use League\Fractal\TransformerAbstract;
use Illuminate\Support\Collection;

class CustomAttributeTransformer extends TransformerAbstract
{
    protected $availableIncludes = [];
    protected $defaultIncludes = [];

    public function __construct($signsField, $jsonSignsField = null)
    {
        $this->signsField = $signsField;
        $this->jsonSignsField = $jsonSignsField;
    }

    public function transform(Collection $collection)
    {
        // Initialize array for additional information.
        $additionalInformation = [];

        // Source - this comes from values sent to this transformer.
        foreach ($collection->{$this->signsField} ?: [] as $value) {
            if (is_array($value)) {
                // If value is an array, serialize it.
                foreach ($value as &$item) {
                    if (isset($item['custom_attr'])) {
                        // Serialize custom attribute data.
                        ...
                    }
                }
            } else {
                // Add non-array values directly.
                ...
            }
        }

        ...

        return [
            'current' => ...,
            'additional_information' => ...,
            'source' => ...,
        ];
    }

    private function flatten(array $values)
    {
      return Arr::flatten($values);
  }
}
```

## Étape 8 : définition des attributs personnalisés OrderItem

Créez un fichier `OrderItemCustomAttributes.php` qui définit les attributs personnalisés de l’élément de commande. Par exemple :

```php
namespace Magento\AepCustomAttributes\Model\Provider;

use Magento\Framework\Serialize\Serializer\Json;

class OrderItemCustomAttribute
{
    private Json $jsonSerializer;
    private string $usingField;

    public function __construct(Json $jsonSerializer, string $usingField)
    {
        $this->jsonSerializer = $jsonSerializer;
        $this->usingField = $usingField;
    }

    public function get(array $values): array
    {
        $output = [];
        $values = $this->flatten($values);

        foreach ($values as $row) {
            $info = \is_string($row['additionalInformation']) ? $row['additionalInformation'] : '{}';
            $unserializedData = $this->jsonSerializer->unserialize($info) ?? [];

            $attrLabel = implode(',', ['label1', 'label2']);
            $unserializedData['custom_attr1'] = $attrLabel;

            $additionalInformation = [];
            foreach ($unserializedData as $name => $value) {
                $additionalInformation[] = [
                    'name' => $name,
                    'value' => \is_string($value) ? $value : $this->jsonSerializer->serialize($value),
                ];
            }

            foreach ($additionalInformation as $information) {
                $output[] = [
                    'additionalInformation' => $information,
                    $this->usingField => $row[$this->usingField],
                ];
            }
        }

        return $output;
    }

    private function flatten(array $values): array
    {
        return array_merge([], ...array_values($values));
    }
}
```

## Étape 9 : création d’un répertoire pour le fichier productContext

Au même niveau que le répertoire `etc`, créez un répertoire appelé `Plugin/Module`. Ce répertoire contient le fichier `ProductContext.php` .

## Étape 10 : définition de la classe ProductContext

Créez un fichier appelé `ProductContext.php` qui définit la classe `ProductContext`. Par exemple :

```php
namespace Magento\Catalog\Model\Product;

use Magento\Framework\App\ResourceConnection;
use Magento\Quote\Api\Data\CartInterface;

class ProductContext
{
    private $brandCache = [];
    private $resourceConnection;

    public function __construct(
        ResourceConnection $resourceConnection
    ) {
        $this->resourceConnection = $resourceConnection;
    }

    public function afterGetProductData($subject, array $result)
    {
        if (isset($result['brand_id'])) {
            if (!isset($this->brandCache[$result['brand_id']])) {
                // @todo load brand label by brand id.
                $this->brandCache[$result['brand_id']] = 'Brand Label ' . $result['brand_id'];
            }
            $result['brands'] = ['label' => $this->brandCache[$result['brand_id']]];
        }

        return $result;
    }
}
```

## Étape 11 : Enregistrement du module

Au même niveau que le répertoire `etc`, créez un fichier `registration.php` qui enregistre le module. Par exemple :

```php
use \Magento\Framework\Component\ComponentRegistrar;

ComponentRegistrar::register(
    ComponentRegistrar::MODULE,
    'Dfe_Stripe',
    __DIR__
);
```

## Étape 12 : Étendre votre schéma XDM existant

Pour vous assurer que les nouveaux attributs de commande personnalisés peuvent être ingérés par votre schéma [!DNL Commerce] dans Experience Platform, vous devez étendre le schéma pour inclure ces champs personnalisés.

Pour savoir comment étendre un schéma XDM existant afin d’inclure ces champs personnalisés, reportez-vous à l’article [Créer et modifier des schémas dans l’interface utilisateur](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/ui/resources/schemas#custom-fields-for-standard-groups) de la documentation de l’Experience Platform. Le champ Identifiant du client est généré dynamiquement. Toutefois, la structure du champ doit ressembler à l’exemple fourni dans la documentation de l’Experience Platform.

>[!IMPORTANT]
>
>Les attributs personnalisés XDM doivent correspondre aux attributs envoyés depuis [!DNL Commerce].

Pour `commerce.order`, ajoutez un champ pour le niveau de commande :

![Niveau de commande](assets/order-level.png)

Pour `productListItems`, ajoutez des champs au niveau de l’élément de commande :

![Order Item Level](assets/order-item-level.png)

## Étape 12 : confirmer que les données sont capturées

Affichez l’onglet [Personnalisation des données](connect-data.md#data-customization) dans l’Admin pour confirmer que les données d’attributs personnalisés sont capturées et envoyées à l’Experience Platform.

### Dépannage

Si le message `No custom order attributes found.` s&#39;affiche dans l&#39;onglet **[!UICONTROL Data Customization]**, vérifiez les points suivants :

1. Vous avez rempli les conditions préalables pour activer l’[ extension du connecteur de données](overview.md#prerequisites).
1. Vous avez configuré les [attributs de commande personnalisés](#add-custom-order-attributes).
1. Au moins un événement de commande a été généré.
