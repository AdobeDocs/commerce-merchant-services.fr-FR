---
title: "Prise en main de [!DNL Live Search]"
description: "Découvrez la configuration requise et les étapes d’installation de  [!DNL Live Search] à partir d’Adobe Commerce."
exl-id: aa251bb0-d52c-4cff-bccb-76a08ae2a3b2
role: Admin, Developer
source-git-commit: 89dd5ae305563e5f6bbcdb80764fd9eeb177b491
workflow-type: tm+mt
source-wordcount: '3093'
ht-degree: 0%

---

# Configurer pour la réussite avec [!DNL Live Search]

Adobe Commerce [!DNL Live Search] et [[!DNL Catalog Service]](../catalog-service/guide-overview.md) travaillent ensemble pour fournir une solution de recherche performante, pertinente et intuitive afin de permettre à vos clients de trouver rapidement ce dont ils ont exactement besoin. Plus précisément, [!DNL Catalog Service] affiche vos données de catalogue pour les services SaaS, comme [!DNL Live Search] à utiliser.

Cet article fournit des instructions détaillées pour l’implémentation de [!DNL Live Search] avec [!DNL Catalog Service].

>[!IMPORTANT]
>
>En ce qui concerne la recherche de site, Adobe Commerce vous offre des options. Assurez-vous de lire [Limites et limites](boundaries-limits.md) avant de procéder à l’implémentation, afin de vous assurer que [!DNL Live Search] est adapté aux besoins de votre entreprise.

## Audience

Cet article est destiné au développeur ou à l’intégrateur de systèmes de votre équipe responsable de l’installation et de la configuration de votre instance Adobe Commerce.

## Conditions

- [Adobe Commerce](https://business.adobe.com/products/magento/magento-commerce.html) 2.4.4+
- PHP version 8.1, 8.2 ou 8.3
- [!DNL Composer]

## Plateformes prises en charge

- Adobe Commerce on Cloud (CEE) : 2.4.4+
- Adobe Commerce on-premise (EE) : 2.4.4+

## Workflow - Aperçu

À un niveau élevé, l’intégration [!DNL Live Search] requiert que vous :

1. [Installer](#1-install-the-live-search-extension) l’extension [!DNL Live Search]
1. [Configurer](#2-configure-api-keys) les clés d’API
1. [Synchroniser](#3-sync-your-catalog-data) vos données de catalogue
1. [Vérifiez](#4-verify-that-the-data-was-exported) que les données du catalogue ont été exportées.
1. [Configurer](#5-configure-the-data) les données
1. [Test](#6-test-the-connection) de la connexion
1. [Vérifiez](#7-validate-events-are-capturing-data) que les événements capturent des données
1. [Personnaliser](#8-customize-for-your-storefront) votre vitrine

## 1. Installez l’extension [!DNL Live Search]

[!DNL Live Search] est installé en tant qu&#39;extension de [Adobe Marketplace](https://commercemarketplace.adobe.com/magento-live-search.html) à [Composer](https://getcomposer.org/). Après avoir installé et configuré [!DNL Live Search], Adobe [!DNL Commerce] commence à partager les données de recherche et de catalogue avec les services SaaS. À ce stade, les utilisateurs *Admin* peuvent configurer, personnaliser et gérer les facettes de recherche, les synonymes et les règles de marchandisage.

>[!NOTE]
>
>Depuis [!DNL Live Search] 3.0.2, l’extension [!DNL Catalog Service] est intégrée à l’installation [!DNL Live Search].

1. Vérifiez que les [tâches cron](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs) et [indexers](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) sont en cours d’exécution.

   >[!IMPORTANT]
   >
   >En raison de l’annonce de fin de prise en charge de 7 Elasticsearch pour août 2023, il est recommandé à tous les clients Adobe Commerce de migrer vers le moteur de recherche OpenSearch 2.x. Pour plus d’informations sur la migration de votre moteur de recherche lors d’une mise à niveau de produit, voir [Migration vers OpenSearch](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/prepare/opensearch-migration) dans le _Guide de mise à niveau_.

1. Téléchargez le package `live-search` depuis [Adobe Marketplace](https://commercemarketplace.adobe.com/magento-live-search.html).

1. Exécutez la commande suivante à partir de la ligne de commande :

   ```bash
   composer require magento/live-search
   ```

   Si vous ajoutez l’extension [!DNL Live Search] à une installation **new** Adobe Commerce, exécutez la commande suivante pour désactiver temporairement [!DNL OpenSearch] et les modules connexes, puis installez [!DNL Live Search]. Ensuite, passez à l’étape 4.

   ```bash
      bin/magento module:disable Magento_Elasticsearch Magento_Elasticsearch7 Magento_OpenSearch Magento_ElasticsearchCatalogPermissions Magento_InventoryElasticsearch Magento_ElasticsearchCatalogPermissionsGraphQl
   ```

   Si vous ajoutez l’extension [!DNL Live Search] à une installation Adobe Commerce **existante**, exécutez ce qui suit pour désactiver les modules [!DNL Live Search] qui diffusent les résultats de recherche storefront. Ensuite, passez à l’étape 4 :

   ```bash
      bin/magento module:disable Magento_LiveSearchAdapter Magento_LiveSearchStorefrontPopover Magento_LiveSearchProductListing 
   ```

   [!DNL Elasticsearch] continue à gérer les requêtes de recherche à partir du storefront tandis que le service [!DNL Live Search] synchronise les données de catalogue et indexe les produits en arrière-plan.

1. Exécutez les opérations suivantes :

   ```bash
   bin/magento setup:upgrade
   ```

1. Vérifiez que les [indexers](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) suivants sont définis sur &quot;Mise à jour par planification&quot; :

   - Flux de produit
   - Flux de variante de produit
   - Flux d’attributs du catalogue
   - Flux de prix du produit
   - Portée du flux de données du site web
   - Portée Flux de données de groupes de clients
   - Flux de catégories
   - Flux d’autorisations de catégorie

1. Si vous installez [!DNL Live Search] sur une nouvelle instance Commerce, vous avez terminé et vous pouvez passer à [2. Configurez la section Clés API](#2-configure-api-keys) . Si vous installez Live Search sur une instance Commerce existante, passez à l’étape suivante.

1. Exécutez les commandes suivantes pour activer l’extension [!DNL Live Search], désactiver [!DNL OpenSearch] et exécuter `setup`.

   ```bash
   bin/magento module:enable Magento_LiveSearchAdapter Magento_LiveSearchStorefrontPopover  Magento_LiveSearchProductListing 
   ```

   ```bash
   bin/magento module:disable Magento_Elasticsearch Magento_Elasticsearch6 Magento_Elasticsearch7 Magento_ElasticsearchCatalogPermissions Magento_InventoryElasticsearch 
   Magento_ElasticsearchCatalogPermissionsGraphQl
   ```

   ```bash
   bin/magento setup:upgrade
   ```

### Installation de la version bêta de [!DNL Live Search]

>[!IMPORTANT]
>
>La fonctionnalité suivante est en version bêta. Pour participer à la version bêta, envoyez une demande par e-mail à [commerce-storefront-services](mailto:commerce-storefront-services@adobe.com).

Cette version bêta prend en charge trois nouvelles fonctionnalités de la requête [`productSearch`](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/) :

- **Recherche en couches** - Recherche dans un autre contexte de recherche - Grâce à cette fonctionnalité, vous pouvez effectuer jusqu’à deux couches de recherche pour vos requêtes de recherche. Par exemple :

   - **Recherche de calque 1** - Recherchez &quot;engine&quot; sur &quot;product_attribute_1&quot;.
   - **Recherche par couche 2** - Recherchez &quot;numéro de partie 123&quot; sur &quot;product_attribute_2&quot;. Cet exemple recherche &quot;part number 123&quot; dans les résultats pour &quot;engine&quot;.

  La recherche en couches est disponible pour l’indexation de recherche `startsWith` et l’indexation de recherche `contains` comme décrit ci-dessous :

- **startsWith search indexation** - Effectuez une recherche en utilisant l’indexation `startsWith`. Cette nouvelle fonctionnalité permet :

   - La recherche de produits pour lesquels la valeur d’attribut commence par une chaîne spécifique.
   - Configuration d’une recherche &quot;se termine par&quot; afin que les acheteurs puissent rechercher des produits pour lesquels la valeur d’attribut se termine par une chaîne spécifique. Pour activer une recherche &quot;se termine par&quot;, l’attribut de produit doit être ingéré en sens inverse et l’appel API doit également être une chaîne inversée.

- **contient l’indexation de la recherche** - Recherchez un attribut à l’aide de l’indexation contient. Cette nouvelle fonctionnalité permet :

   - Recherche d’une requête dans une chaîne plus grande. Par exemple, si un acheteur recherche le numéro de produit &quot;PE-123&quot; dans la chaîne &quot;HAPE-123&quot;.

      - Remarque : Ce type de recherche est différent de la [recherche d’expression](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/#phrase) existante, qui effectue une recherche de saisie semi-automatique. Par exemple, si la valeur de votre attribut de produit est &quot;pantalon extérieur&quot;, une recherche d’expression renvoie une réponse pour &quot;pantalon d’extraction&quot;, mais ne renvoie pas de réponse pour &quot;fourmis d’extérieur&quot;. Une recherche contient, cependant, renvoie une réponse pour &quot;fourmis pauvres&quot;.

Ces nouvelles conditions améliorent le mécanisme de filtrage des requêtes de recherche pour affiner les résultats de recherche. Ces nouvelles conditions n’affectent pas la requête de recherche principale.

Vous pouvez mettre en oeuvre ces nouvelles conditions sur votre page de résultats de recherche. Par exemple, vous pouvez ajouter une nouvelle section sur la page où l’acheteur peut affiner davantage ses résultats de recherche. Vous pouvez permettre aux acheteurs de sélectionner des attributs de produit spécifiques, tels que &quot;Fabricant&quot;, &quot;Numéro de pièce&quot; et &quot;Description&quot;. À partir de là, ils effectuent des recherches dans ces attributs à l’aide des conditions `contains` ou `startsWith`. Consultez le guide d’administration pour obtenir une liste des [attributs](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/product-attributes/attributes-input-types) pouvant faire l’objet d’une recherche.

1. Pour installer la version bêta, ajoutez la dépendance suivante à votre projet :

   ```bash
   composer require magento/module-live-search-search-types:"^1.0.0-beta1"
   ```

1. Validez et envoyez les modifications à vos fichiers `composer.json` et `composer.lock` dans votre projet cloud. [En savoir plus](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/extensions#upgrade-an-extension).

   Cette version bêta ajoute **[!UICONTROL Search types]** cases à cocher pour **[!UICONTROL Autocomplete]**, **[!UICONTROL Contains]** et **[!UICONTROL Starts with]** dans l’administrateur. Il met également à jour l’API GraphQL [`productSearch`](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/#filtering-using-search-capability) pour inclure ces nouvelles fonctionnalités de recherche.

1. Dans l’administrateur, [définissez un attribut de produit](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/product-attributes/product-attributes-add#step-5-describe-the-storefront-properties) à rechercher et spécifiez la fonctionnalité de recherche de cet attribut, par exemple **Contains** (par défaut) ou **Commence par**. Vous pouvez spécifier un maximum de six attributs à activer pour **Contient** et six attributs à activer pour **Commence par**. Pour la version bêta, sachez que l’administrateur n’applique pas cette restriction, mais qu’il l’applique dans les recherches d’API.

   ![Spécifier la fonctionnalité de recherche](./assets/search-filters-admin.png)

1. Consultez la [ documentation destinée aux développeurs](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/#filtering-using-search-capability) pour savoir comment mettre à jour vos appels d’API [!DNL Live Search] à l’aide des nouvelles fonctionnalités de recherche `contains` et `startsWith`.

### Descriptions des champs

| Champ | Description |
|--- |--- |
| `Autocomplete` | Activé par défaut et ne peut pas être modifié. Avec `Autocomplete`, vous pouvez utiliser `contains` dans le [filtre de recherche](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/#filtering). Ici, la requête de recherche dans `contains` renvoie une réponse de recherche de type saisie automatiquement. Adobe vous recommande d’utiliser ce type de recherche pour les champs de description, qui contiennent généralement plus de 50 caractères. |
| `Contains` | Active une recherche &quot;texte contenu dans une chaîne&quot; au lieu d’une recherche de saisie semi-automatique. Utilisez `contains` dans le [filtre de recherche](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/#filtering-using-search-capability). Pour plus d’informations, voir [Limites](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/#limitations) . |
| `Starts with` | Permet d’interroger des chaînes qui commencent par une valeur particulière. Utilisez `startsWith` dans le [filtre de recherche](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/#filtering-using-search-capability). |

## 2. Configuration des clés d’API

La clé API Adobe Commerce et sa clé privée associée sont nécessaires pour connecter [!DNL Live Search] à une installation d&#39;Adobe Commerce. La clé API est générée et conservée dans le compte du détenteur de licence [!DNL Commerce], qui peut la partager avec le développeur ou l’intégrateur de systèmes. Le développeur peut ensuite créer et gérer les espaces de données SaaS pour le compte du détenteur de licence. Si vous disposez déjà d’un ensemble de clés d’API, vous n’avez pas besoin de les régénérer.

Découvrez comment configurer vos clés d’API dans l’article [Commerce Services Connector](../landing/saas.md).

## 3. Synchroniser les données de votre catalogue {#synchronize-catalog-data}

[!DNL Live Search] déplace les données du catalogue vers l’infrastructure SaaS d’Adobe. Les données sont indexées et les résultats de la recherche sont diffusés de cet index directement sur le storefront. Selon la taille et la complexité, l’indexation peut prendre de 30 minutes à quelques heures.

Pour commencer la synchronisation initiale de vos données de catalogue avec les services SaaS, exécutez les commandes suivantes dans cet ordre :

```bash
bin/magento saas:resync --feed productattributes
bin/magento saas:resync --feed products
bin/magento saas:resync --feed scopesCustomerGroup
bin/magento saas:resync --feed scopesWebsite
bin/magento saas:resync --feed prices
bin/magento saas:resync --feed productoverrides
bin/magento saas:resync --feed variants
bin/magento saas:resync --feed categories
bin/magento saas:resync --feed categoryPermissions
```

Lorsque vous exécutez ces commandes, la synchronisation initiale des données de votre catalogue avec les services SaaS démarre.

>[!WARNING]
>
> Bien que les données soient indexées et synchronisées, les opérations de recherche et de navigation de catégorie ne sont pas disponibles dans le storefront. Selon la taille de votre catalogue, le processus peut prendre au moins une heure à partir du moment où `cron` s’exécute pour synchroniser vos données avec les services SaaS.

### Surveillance de la progression de la synchronisation

Vous pouvez afficher les données synchronisées et partagées à l’aide du [tableau de bord de Data Management](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard). Ce tableau de bord fournit des informations précieuses sur la disponibilité des données de produit pour votre storefront, afin qu’elles puissent être rapidement affichées pour vos clients.

![Tableau de bord de Data Management](assets/data-management-dashboard.png)

Vous pouvez également exécuter des commandes de synchronisation et résoudre les problèmes liés au processus de synchronisation à l’aide de l’[interface de ligne de commande Commerce](../data-export/data-export-cli-commands.md#troubleshooting) et des journaux d’extension d’exportation des données.

#### Futures mises à jour des produits

Après la synchronisation initiale, il peut s’écouler jusqu’à 15 minutes avant que les mises à jour incrémentielles des produits ne soient disponibles pour la recherche storefront. Pour en savoir plus, voir [Mises à jour de produit en flux continu](indexing.md) dans la documentation sur l’indexation.

## 4. Vérifier que les données ont été exportées {#verify-export}

Pour vérifier si vos données de catalogue ont été exportées à partir d’Adobe Commerce et synchronisées avec [!DNL Live Search], vous disposez de quelques options :

- Recherchez des entrées dans les tableaux suivants :

   - `cde_products_feed`
   - `cde_product_attributes_feed`

  >[!NOTE]
  >
  >Si vous obtenez une erreur `table does not exist`, recherchez les entrées dans les tables `catalog_data_exporter_products` et `catalog_data_exporter_product_attributes`. Ces noms de table sont utilisés dans les versions [!DNL Live Search] antérieures à la version 4.2.1.

- Utilisez le [terrain de jeu GraphQL](https://developer.adobe.com/commerce/services/graphql/live-search/) avec la requête par défaut pour vérifier les éléments suivants :

   - Le nombre de produits renvoyé est proche de ce que vous attendez pour la vue de magasin.
   - Les facettes sont renvoyées.

Pour obtenir une aide supplémentaire, reportez-vous à la section [[!DNL Live Search] catalogue non synchronisé](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/live-search-catalog-data-sync) de la base de connaissances d’assistance.

## 5. Configurer les données

La configuration correcte des données de vos produits garantit de bons résultats de recherche pour vos clients. Dans cette section, vous activez les widgets de liste de produits et affectez des catégories.

### Activation des widgets de liste de produits

Lorsque vous installez [!DNL Live Search] 4.0.0+, les widgets de liste de produits sont activés par défaut. Lorsque les widgets sont activés, un composant d’interface utilisateur différent est utilisé pour la page des résultats de recherche et la page de liste des produits de la catégorie de navigation. Ce composant de l’interface utilisateur effectue des appels directs vers l’ [ API Catalog Service](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/), ce qui se traduit par des temps de réponse plus rapides.

Si vous disposez d’une version de [!DNL Live Search] antérieure à 4.0.0+, vous devez activer manuellement le widget de liste de produits.

1. À partir de *Admin*, accédez à **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Sous **[!UICONTROL Live Search]**, sélectionnez **[!UICONTROL Storefront Features]**.
1. Définissez **[!UICONTROL Enable Product Listing Widgets]** sur `Yes`.

   ![Activer les widgets de liste de produits](assets/ls-admin-enable-widget.png)

Lorsque vous modifiez cette configuration, le message `Page cache is invalidated` apparaît. Vous devez vider le cache du Magento pour enregistrer votre modification.

1. Accédez à la page [Gestion du cache](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management) en effectuant l’une des opérations suivantes :

   - Cliquez sur le lien **[!UICONTROL Cache Management]** dans le message situé au-dessus de l’espace de travail.
   - Sur la barre latérale _Admin_, accédez à **[!UICONTROL System]** > _[!UICONTROL Tools]_>**[!UICONTROL Cache Management]**.

1. Sélectionnez la **Configuration** [!UICONTROL Cache Type] et cliquez sur **[!UICONTROL Flush Magento Cache]**.

   Les modifications apportées au storefront sont immédiates une fois le cache vidé.

### Attribution de catégories

Les produits renvoyés dans [!DNL Live Search] doivent être affectés à une [catégorie](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/categories/categories). Dans Luma, par exemple, les produits sont classés dans des catégories telles que &quot;Hommes&quot;, &quot;Femmes&quot; et &quot;Porcs&quot;. Les sous-catégories sont également configurées pour &quot;Tops&quot;, &quot;Bottoms&quot; et &quot;Montres&quot;. Ces affectations de catégorie améliorent la granularité lors du filtrage.

## 6. Tester la connexion {#test-connection}

Maintenant que vos données de catalogue sont dans SaaS, vérifiez que les données de produit sont renvoyées dans les scénarios suivants :

- La zone [!UICONTROL Search] renvoie les résultats correctement.
- La navigation dans les catégories renvoie correctement les résultats.
- Les facettes sont disponibles sous forme de filtres sur les pages de résultats de recherche.

Si tout fonctionne correctement, [!DNL Live Search] est installé, connecté et prêt à l&#39;emploi.

Si vous rencontrez des problèmes dans le storefront, recherchez dans le fichier `var/log/system.log` des échecs de communication de l’API ou des erreurs du côté des services.

Pour autoriser [!DNL Live Search] par le biais d’un pare-feu, ajoutez `commerce.adobe.io` à la liste autorisée.

## 7. Vérifier que les événements capturent des données

Assurez-vous que les événements storefront déployés sur votre site fonctionnent. Ceci est particulièrement important pour les implémentations sans interface.

- Examinez les [événements](events.md) requis pour [!DNL Live Search].
- Assurez-vous que le [tableau de bord de la recherche en direct](performance.md) affiche les données de vos environnements hors production.
- [Vérifier la collecte des événements](../product-recommendations/verify.md). Bien que cette page figure dans le guide [!DNL Product Recommendations], les étapes de vérification s’appliquent également à [!DNL Live Search].

## 8. Personnalisez votre vitrine

Vous avez installé l’extension [!DNL Live Search], synchronisé, validé et configuré vos données. L’étape suivante consiste à s’assurer que les widgets [!DNL Live Search] sont conformes à l’apparence de votre magasin.

Vous pouvez mettre en forme la fenêtre contextuelle et les widgets PLP en définissant des règles CSS personnalisées si nécessaire. Voir [Eléments de fenêtre contextuelle de style](storefront-popover.md#styling-popover-example) et [widget de page de liste de produits](plp-styling.md#styling-example).

Si vous souhaitez étendre les fonctionnalités des widgets, le code source de chacun d’eux est disponible dans un référentiel public.
Dans ce scénario, vous pouvez personnaliser JavaScript selon vos besoins, puis héberger votre code personnalisé sur votre réseau de diffusion de contenu. Ce script personnalisé communique avec le service [!DNL Live Search] et renvoie les résultats comme normaux, ce qui vous permet de contrôler les fonctionnalités du widget.

- [Référentiel de widgets PLP](https://github.com/adobe/storefront-product-listing-page)
- [Référentiel de barre de recherche](https://github.com/adobe/storefront-search-as-you-type)

## Mise à jour de [!DNL Live Search] {#update}

Avant de mettre à jour la recherche en direct, exécutez le code suivant depuis la ligne de commande pour vérifier la version de la recherche en direct installée :

```bash
composer show magento/module-live-search | grep version
```

Pour mettre à jour [!DNL Live Search], exécutez les éléments suivants à partir de la ligne de commande :

```bash
composer update magento/live-search --with-dependencies
```

Pour effectuer une mise à jour vers une version majeure, telle que de 3.1.1 à 4.0.0, modifiez le fichier [!DNL Composer] `.json` racine du projet comme suit :

1. Si votre version `magento/live-search` actuellement installée est `3.1.1` ou inférieure et que vous effectuez une mise à niveau vers la version `4.0.0` ou supérieure, exécutez la commande suivante avant la mise à niveau :

   ```bash
   bin/magento module:enable Magento_AdvancedSearch
   ```

   Pour plus d’informations sur la version `magento/live-search` actuellement installée, exécutez la commande suivante :

   ```bash
   composer show magento/live-search
   ```

1. Ouvrez le fichier racine `composer.json` et recherchez `magento/live-search`.

1. Dans la section `require` , mettez à jour le numéro de version comme suit :

   ```json
   "require": {
      ...
      "magento/live-search": "^4.0",
      ...
    }
   ```

1. Enregistrez `composer.json`. Exécutez ensuite la commande suivante à partir de la ligne de commande :

   ```bash
   composer update magento/live-search --with-dependencies
   ```

## Désinstallation de [!DNL Live Search] {#uninstall}

Pour désinstaller [!DNL Live Search], reportez-vous à la section [Désinstallation des modules](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/uninstall-modules).

## [!DNL Live Search] packages {#packages}

L’extension [!DNL Live Search] se compose des packages suivants :

| Package | Description |
|--- |--- |
| `module-live-search` | Permet aux commerçants de configurer leurs paramètres de recherche pour la facette, les synonymes, les règles de requête, etc. Et permet d’accéder à un terrain de jeu GraphQL en lecture seule pour tester les requêtes à partir de l’*Admin*. |
| `module-live-search-adapter` | Permet d’acheminer les requêtes de recherche du storefront vers le service [!DNL Live Search] et d’afficher les résultats dans le storefront. <br /> - Navigation dans les catégories - Permet d’acheminer les demandes du [haut navigation](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/navigation/navigation-top) du storefront vers le service de recherche.<br /> - Recherche globale : achemine les requêtes de la zone de [recherche rapide](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search) dans le coin supérieur droit du storefront vers le service [!DNL Live Search]. |
| `module-live-search-storefront-popover` | Une fenêtre contextuelle &quot;Rechercher lorsque vous tapez&quot; remplace la recherche rapide standard et renvoie les données et les miniatures des principaux résultats de la recherche. |

## [!DNL Live Search] dépendances {#dependencies}

Le métaphorage [!DNL Composer] pour installer l’extension [!DNL Live Search] comprend les dépendances de module suivantes.

- `magento/module-saas-catalog`
- `magento/module-saas-category`
- `magento/module-saas-category-permissions`
- `magento/module-saas-product-override`
- `magento/module-saas-product-variant`
- `magento/module-saas-price`
- `magento/module-saas-scopes`
- `magento/module-bundle-product-data-exporter`
- `magento/module-catalog-inventory-data-exporter`
- `magento/module-catalog-url-rewrite-data-exporter`
- `magento/module-configurable-product-data-exporter`
- `magento/module-parent-product-data-exporter`
- `magento/module-gift-card-product-data-exporter`
- `magento/module-bundle-product-override-data-exporter`
- `data-services`
- `services-id`

## Concepts avancés

Les sections suivantes contiennent des rubriques plus avancées lorsque vous utilisez [!DNL Live Search] et [!DNL Catalog Service].

### Point d’entrée

[!DNL Live Search] communique par l’intermédiaire du point de terminaison à l’adresse `https://catalog-service.adobe.io/graphql`.

Comme [!DNL Live Search] n’a pas accès à la base de données complète des produits, les API de base de données [!DNL Live Search] GraphQL et Commerce GraphQL ne sont pas entièrement équivalentes.

Adobe recommande d’appeler directement les API SaaS — en particulier le point d’entrée du service de catalogue.

- Obtenir des performances et réduire la charge du processeur en contournant le processus base de données Commerce/Graphql
- Profitez de la fédération [!DNL Catalog Service] pour appeler [!DNL Live Search], [!DNL Catalog Service] et [!DNL Product Recommendations] à partir d’un seul point de terminaison.

Pour certains cas d’utilisation, il est peut-être préférable d’appeler [!DNL Catalog Service] pour obtenir des détails sur les produits et des cas similaires. Voir [refineProduct](https://developer.adobe.com/commerce/services/graphql/catalog-service/refine-product/) pour plus d’informations.

Si vous disposez d’une implémentation personnalisée sans interface utilisateur graphique, consultez les implémentations de référence [!DNL Live Search] :

- [Widget PLP](https://github.com/adobe/storefront-product-listing-page)
- [Champ de recherche en direct](https://github.com/adobe/storefront-search-as-you-type)

La collecte automatique des données d’interaction utilisateur ne fonctionne pas par défaut lorsque vous n’utilisez pas les composants standard tels que l’adaptateur de recherche, les widgets Luma ou les widgets CIF AEM. Adobe Sensei utilise ces données collectées pour le marchandisage intelligent et le suivi des performances. Pour résoudre ce problème, vous devez développer une solution personnalisée afin de mettre en oeuvre cette collecte de données sans interface utilisateur.

La dernière version de [!DNL Live Search] utilise déjà [!DNL Catalog Service].

### Prise en charge linguistique

Les widgets [!DNL Live Search] prennent en charge les langues suivantes :

|  |  |  |  |
|--- |--- |--- |--- |
| Langue | Région | Code de langue | Paramètres régionaux du Magento |
| Bulgare | Bulgarie | bg_BG | bg_BG |
| Catalan | Espagne | ca_ES | ca_ES |
| Tchèque | République tchèque | cs_CZ | cs_CZ |
| Danois | Danemark | da_DK | da_DK |
| Allemand | Allemagne | de_DE | de_DE |
| Grec | Grèce | el_GR | el_GR |
| Anglais | Royaume-Uni | en_GB | en_GB |
| Anglais | États-Unis | en_US | en_US |
| Espagnol | Espagne | es_ES | es_ES |
| Estonien | Estonie | et_EE | et_EE |
| Basque | Espagne | eu_ES | eu_ES |
| Perse | Iran | fa_IR | fa_IR |
| Finnois | Finlande | fi_FI | fi_FI |
| Français | France | fr_FR | fr_FR |
| Galicien | Espagne | gl_ES | gl_ES |
| Hindi | Inde | hi_IN | hi_IN |
| Hongrois | Hongrie | hu_HU | hu_HU |
| Indonésien | Indonésie | id_ID | id_ID |
| Italien | Italie | it_IT | it_IT |
| Coréen | Corée du Sud | ko_KR | ko_KR |
| Lituanien | Lituanie | lt_LT | lt_LT |
| Letton | Lettonie | lv_LV | lv_LV |
| Norvégien | Norvège, bokmal | nb_NO | nb_NO |
| Néerlandais | Pays | nl_NL | nl_NL |
| Polonais | Pologne | pl_PL | pl_PL |
| Portuge | Brésil | pt_BR | pt_BR |
| Portuge | Portugal | pt_PT | pt_PT |
| Roumain | Roumanie | ro_RO | ro_RO |
| Russe | Russie | ru_RU | ru_RU |
| Suédois | Suède | sv_SE | sv_SE |
| Thaï | Thaïlande | th_TH | th_TH |
| Turc | Turquie | tr_TR | tr_TR |
| Chinois | Chine | zh_CN | zh_Hans_CN |
| Chinois | Taiwan | zh_TW | zh_Hant_TW |

Si le widget détecte que le paramètre de langue d’administration de Commerce correspond à une langue prise en charge, il utilise cette langue par défaut. Sinon, le widget est défini par défaut sur Anglais. Dans l’administrateur, le paramètre de langue est configuré en accédant à _[!UICONTROL Stores]_> [!UICONTROL Settings] >_[!UICONTROL Configuration]_ > _[!UICONTROL General]_> [!UICONTROL Country Options].

Les administrateurs peuvent également définir la langue de l’ [index de recherche](settings.md#language), afin de garantir de meilleurs résultats de recherche.

### Référentiel de code de widget

Le code du widget de page de liste de produits et du widget de champ de recherche en direct peut être téléchargé à partir de GitHub.

Les développeurs qui ont accès au code peuvent complètement personnaliser son fonctionnement et son aspect. Ils hébergent le code sur leurs propres serveurs, tout en utilisant le service [!DNL Live Search].

- [Widget PLP](https://github.com/adobe/storefront-product-listing-page)
- [Barre de recherche](https://github.com/adobe/storefront-search-as-you-type)

### Extension Data Export

Une fois la recherche en direct activée, l’extension Exportation de données synchronise les données Commerce entre l’application Commerce et la recherche en direct. Ce processus garantit que les données Commerce les plus récentes sont disponibles sur le storefront. Dans l’Admin, vous pouvez vérifier l’état de synchronisation à l’aide du tableau de bord Data Management. Vous pouvez gérer et résoudre les problèmes liés au processus d’exportation des données à l’aide de l’interface de ligne de commande et des journaux de Commerce. Pour plus d’informations, voir le [Guide d’exportation des données](../data-export/overview.md).

### Inventory management

[!DNL Live Search] prend en charge les fonctionnalités [Inventory management](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/introduction) dans Commerce (anciennement appelée Inventaire multi-Source ou MSI). Pour activer la prise en charge complète, vous devez [mettre à jour](install.md#update) le module de dépendance `commerce-data-export` vers la version 102.2.0+.

[!DNL Live Search] renvoie une valeur booléenne indiquant si un produit est disponible dans Inventory management, mais ne contient pas d’informations sur la source qui possède le stock.

### Indexateur de prix

Les clients Live Search peuvent utiliser l’ [ indexeur de prix SaaS](../price-index/price-indexing.md), qui permet d’accélérer les mises à jour de changement de prix et le temps de synchronisation.

### Prise en charge des prix

Les widgets de recherche en direct prennent en charge la plupart, mais pas tous les types de prix pris en charge par Adobe Commerce.

Actuellement, les prix de base sont pris en charge. Les prix avancés non pris en charge sont les suivants :

- Coût
- Prix publicitaire minimal

Consultez [API Mesh](../catalog-service/mesh.md) pour des calculs de prix plus complexes.

Le format de prix prend en charge le paramètre de configuration des paramètres régionaux dans l’instance Commerce : *Magasins* > Paramètres > *Configuration* > Général > *Général* > Options locales > Paramètre régional.

### Prise en charge de storefront sans interface

Si vous le souhaitez, vous devrez peut-être installer le module `module-data-services-graphql` qui étend la couverture GraphQL existante de l’application pour inclure les champs requis pour la collecte de données comportementales du storefront.

```bash
composer require magento/module-data-services-graphql
```

Ce module ajoute des contextes supplémentaires aux requêtes GraphQL :

- `dataServicesStorefrontInstanceContext`
- `dataServicesMagentoExtensionContext`
- `dataServicesStoreConfigurationContext`

### Prise en charge B2B

[!DNL Live Search] prend en charge la [fonctionnalité B2B](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/guide-overview) avec des [limitations](boundaries-limits.md#b2b-and-category-permissions) supplémentaires.

### Prise en charge des PWA

[!DNL Live Search] fonctionne avec PWA Studio, mais les utilisateurs peuvent constater de légères différences par rapport aux autres implémentations de Commerce. Les fonctionnalités de base telles que la recherche et la liste de produits fonctionnent dans Venia, mais certaines permutations de Graphql peuvent ne pas fonctionner correctement. Il peut également y avoir des différences de performances.

- L’implémentation actuelle du PWA de [!DNL Live Search] nécessite plus de temps de traitement pour renvoyer les résultats de recherche que [!DNL Live Search] avec le storefront Commerce natif.
- [!DNL Live Search] en PWA ne prend pas en charge [la gestion des événements](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/). Par conséquent, les rapports de recherche et le marchandisage intelligent ne fonctionnent pas sur les vitrines des PWA.
- Lors de l’utilisation de [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/), GraphQL ne prend pas en charge le filtrage directement sur `description`, `name`, `short_description`, mais ces champs peuvent être renvoyés avec un filtre plus général.

Pour utiliser [!DNL Live Search] avec PWA Studio, les intégrateurs doivent également :

1. Installez [livesearch-storefront-utils](https://www.npmjs.com/package/@magento/ds-livesearch-storefront-utils).
1. Définissez le `environmentId` dans l’objet `storeDetails`.

   ```javascript
   const storeDetails: StoreDetailsProps = {
       environmentId: <Storefront_ID>,
       websiteCode: "base",
       storeCode: "main_website_store",
       storeViewCode: "default",
       searchUnitId: searchUnitId,
       config: {
           minQueryLength: 5,
           pageSize: 8,
           currencySymbol: "$",
           },
       };
   ```

### Cookies

[!DNL Live Search] collecte des données d’interaction de l’utilisateur dans le cadre de sa fonctionnalité de base et les cookies sont utilisés pour stocker ces données. Lors de la collecte de toute information utilisateur, l’utilisateur doit accepter de stocker les cookies. [!DNL Live Search] et [!DNL Product Recommendations] partagent le flux de données et donc le même mécanisme de cookie. Pour en savoir plus, consultez la section [Handle Cookie Restrictions](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/developer/setting-cookie).
