---
title: "Prise en main de [!DNL Live Search]"
description: "Découvrez la configuration requise et les étapes d’installation pour [!DNL Live Search] d’Adobe Commerce."
exl-id: aa251bb0-d52c-4cff-bccb-76a08ae2a3b2
role: Admin, Developer
source-git-commit: c66eab4ae0dda9a447a17f357ee0bb7364dc46ba
workflow-type: tm+mt
source-wordcount: '2405'
ht-degree: 0%

---

# Configurez pour la réussite avec [!DNL Live Search]

Adobe Commerce [!DNL Live Search] et [[!DNL Catalog Service]](../catalog-service/guide-overview.md) collaborez pour offrir une solution de recherche performante, pertinente et intuitive afin de permettre à vos clients de trouver rapidement ce dont ils ont exactement besoin. Plus précisément : [!DNL Catalog Service] affiche vos données de catalogue pour les services SaaS, comme [!DNL Live Search] à utiliser.

Cet article fournit des instructions détaillées pour la mise en oeuvre de [!DNL Live Search] avec [!DNL Catalog Service].

>[!IMPORTANT]
>
>En ce qui concerne la recherche de site, Adobe Commerce vous offre des options. Veillez à lire [Limites et limites](boundaries-limits.md) avant l’implémentation, pour vérifier [!DNL Live Search] est adapté aux besoins de votre entreprise.

## Audience

Cet article est destiné au développeur ou à l’intégrateur de systèmes de votre équipe responsable de l’installation et de la configuration de votre instance Adobe Commerce.

## Conditions

- [Adobe Commerce](https://business.adobe.com/products/magento/magento-commerce.html) 2.4.4+
- PHP 8.1 / 8.2 / 8.3
- [!DNL Composer]

## Plateformes prises en charge

- Adobe Commerce on Cloud (CEE) : 2.4.4+
- Adobe Commerce on-premise (EE) : 2.4.4+

## Workflow - Aperçu

à un niveau élevé ; [!DNL Live Search] requiert que vous :

![Processus de recherche en direct](assets/livesearch-workflow.png)

## 1. Installez le [!DNL Live Search] extension

[!DNL Live Search] est installé en tant qu’extension de [Adobe Marketplace](https://commercemarketplace.adobe.com/magento-live-search.html) through [Compositeur](https://getcomposer.org/). Après avoir installé et configuré [!DNL Live Search], ADOBE [!DNL Commerce] Commence à partager les données de recherche et de catalogue avec les services SaaS. À ce stade, *Administration* les utilisateurs peuvent configurer, personnaliser et gérer des facettes de recherche, des synonymes et des règles de marchandisage.

>[!NOTE]
>
>À partir de [!DNL Live Search] 3.0.2, la variable [!DNL Catalog Service] l’extension est regroupée avec la fonction [!DNL Live Search] installation.

1. Confirmez que [tâches cron](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs) et [indexeurs](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) sont en cours d’exécution.

   >[!IMPORTANT]
   >
   >En raison de l’annonce de fin de prise en charge de 7 Elasticsearch pour août 2023, il est recommandé à tous les clients Adobe Commerce de migrer vers le moteur de recherche OpenSearch 2.x. Pour plus d’informations sur la migration de votre moteur de recherche lors d’une mise à niveau de produit, voir [Migration vers OpenSearch](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/prepare/opensearch-migration) dans le _Guide de mise à niveau_.

1. Téléchargez la `live-search` du module [Adobe Marketplace](https://commercemarketplace.adobe.com/magento-live-search.html).

1. Exécutez la commande suivante à partir de la ligne de commande :

   ```bash
   composer require magento/live-search
   ```

   Si vous ajoutez l’événement [!DNL Live Search] d’une extension **new** Installation d’Adobe Commerce, exécutez les opérations suivantes pour désactiver [!DNL OpenSearch] et les modules connexes, puis installez [!DNL Live Search]. Passez ensuite à l’étape 4.

   ```bash
      bin/magento module:disable Magento_Elasticsearch Magento_Elasticsearch7 Magento_OpenSearch Magento_ElasticsearchCatalogPermissions Magento_InventoryElasticsearch Magento_ElasticsearchCatalogPermissionsGraphQl
   ```

   Si vous ajoutez l’événement [!DNL Live Search] d’une extension **existant** Pour désactiver temporairement l’installation d’Adobe Commerce, procédez comme suit : [!DNL Live Search] modules qui diffusent les résultats de recherche storefront. Passez ensuite à l’étape 4 :

   ```bash
      bin/magento module:disable Magento_LiveSearchAdapter Magento_LiveSearchStorefrontPopover Magento_LiveSearchProductListing 
   ```

   [!DNL Elasticsearch] continue à gérer les requêtes de recherche à partir du storefront pendant que la fonction [!DNL Live Search] Le service synchronise les données du catalogue et indexe les produits en arrière-plan.

1. Exécutez les opérations suivantes :

   ```bash
   bin/magento setup:upgrade
   ```

1. Vérifiez que les [indexeurs](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) sont définis sur &quot;Mise à jour par planification&quot; :

   - Flux de produit
   - Flux de variante de produit
   - Flux d’attributs du catalogue
   - Flux de prix du produit
   - Portée du flux de données du site web
   - Portée Flux de données de groupes de clients
   - Flux de catégories
   - Flux d’autorisations de catégorie

1. Si vous installez [!DNL Live Search] sur une nouvelle instance Commerce, vous avez terminé et vous pouvez accéder à la fonction [2. Configuration des clés d’API](#2-configure-api-keys) . Si vous installez Live Search sur une instance Commerce existante, passez à l’étape suivante.

1. Exécutez les commandes suivantes pour activer la fonction [!DNL Live Search] extension, désactiver [!DNL OpenSearch], puis exécutez `setup`.

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

## 2. Configuration des clés d’API

La clé d’API Adobe Commerce et sa clé privée associée sont nécessaires pour se connecter. [!DNL Live Search] à une installation d’Adobe Commerce. La clé API est générée et conservée dans le compte de la variable [!DNL Commerce] titulaire de la licence, qui peut la partager avec le développeur ou l’intégrateur de systèmes. Le développeur peut ensuite créer et gérer les espaces de données SaaS pour le compte du détenteur de licence. Si vous disposez déjà d’un ensemble de clés d’API, vous n’avez pas besoin de les régénérer.

Découvrez comment configurer vos clés d’API dans le [Connecteur Commerce Services](../landing/saas.md) article.

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
> Bien que les données soient indexées et synchronisées, les opérations de recherche et de navigation de catégorie ne sont pas disponibles dans le storefront. Selon la taille de votre catalogue, le processus peut prendre au moins une heure à partir du `cron` s’exécute pour synchroniser vos données avec les services SaaS.

### Surveillance de la progression de la synchronisation

Vous pouvez afficher les données synchronisées et partagées à l’aide de la variable [Tableau de bord de la gestion des données](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard). Ce tableau de bord fournit des informations précieuses sur la disponibilité des données de produit pour votre storefront, afin qu’elles puissent être rapidement affichées pour vos clients.

![Tableau de bord de la gestion des données](assets/data-management-dashboard.png)

#### Futures mises à jour des produits

Après la synchronisation initiale, il peut s’écouler jusqu’à 15 minutes avant que les mises à jour incrémentielles des produits ne soient disponibles pour la recherche storefront. Pour en savoir plus, voir [Indexation - Mises à jour des produits en flux continu](indexing.md).

## 4. Vérifier que les données ont été exportées {#verify-export}

Pour vérifier que les données du catalogue ont été exportées à partir de votre instance Adobe Commerce et sont synchronisées pour [!DNL Live Search], vous disposez de plusieurs options :

- Recherchez des entrées dans les tableaux suivants :

   - `catalog_data_exporter_products`
   - `catalog_data_exporter_product_attributes`

- Utilisez la variable [Jeu GraphQL](https://developer.adobe.com/commerce/services/graphql/live-search/) avec la requête par défaut pour vérifier les éléments suivants :

   - Le nombre de produits renvoyé est proche de ce que vous attendez pour la vue de magasin.
   - Les facettes sont renvoyées.

Pour obtenir une aide supplémentaire, voir [[!DNL Live Search] catalogue non synchronisé](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/live-search-catalog-data-sync) dans la base de connaissances d’assistance.

## 5. Configurer les données

La configuration correcte des données de vos produits garantit de bons résultats de recherche pour vos clients. Dans cette section, vous activez les widgets de liste de produits et affectez des catégories et des attributs.

### Activation des widgets de liste de produits

Lors de l’installation [!DNL Live Search] 4.0.0+, les widgets de liste de produits sont activés par défaut. Lorsque les widgets sont activés, un composant d’interface utilisateur différent est utilisé pour la page des résultats de recherche et la page de liste des produits du navigateur de catégorie. Ce composant d’IU effectue des appels directs vers [API Catalog Service](https://developer.adobe.com/commerce/services/graphql/catalog-service/product-search/), ce qui se traduit par des temps de réponse plus rapides.

Si vous avez une [!DNL Live Search] version antérieure à 4.0.0+, vous devez activer manuellement le widget de liste de produits.

1. Dans la *Administration*, accédez à **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Sous **[!UICONTROL Live Search]**, sélectionnez **[!UICONTROL Storefront Features]**.
1. Définir **[!UICONTROL Enable Product Listing Widgets]** to `Yes`.

   ![Activation des widgets de liste de produits](assets/ls-admin-enable-widget.png)

Lorsque vous modifiez cette configuration, le message `Page cache is invalidated` apparaît. Vous devez vider le cache du Magento pour enregistrer votre modification.

1. Accédez au [Gestion du cache](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management) en effectuant l’une des opérations suivantes :

   - Cliquez sur le bouton **[!UICONTROL Cache Management]** dans le message situé au-dessus de l’espace de travail.
   - Sur le _Administration_ barre latérale, accédez à **[!UICONTROL System]** > _[!UICONTROL Tools]_>**[!UICONTROL Cache Management]**.

1. Sélectionnez la variable **Configuration** [!UICONTROL Cache Type] et cliquez sur **[!UICONTROL Flush Magento Cache]**.

   Les modifications apportées au storefront sont immédiates une fois le cache vidé.

### Attribution de catégories

Produits renvoyés dans [!DNL Live Search] doit être affecté à une [category](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/categories/categories). Dans Luma, par exemple, les produits sont classés dans des catégories telles que &quot;Hommes&quot;, &quot;Femmes&quot; et &quot;Porcs&quot;. Les sous-catégories sont également configurées pour &quot;Tops&quot;, &quot;Bottoms&quot; et &quot;Montres&quot;. Cela permet une meilleure granularité lors du filtrage.

### Champs indexables et filtrables

Les produits sont attribués [Attributs](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/product-attributes/product-attributes) qui peuvent être utilisés pour la recherche et le filtrage. Les attributs sont des éléments tels que &quot;Couleur&quot;, &quot;Taille&quot;, &quot;Type de matière&quot;. Avec ces attributs, les utilisateurs peuvent rechercher des &quot;ordinateurs verts&quot;. De nombreux attributs peuvent être définis dans chaque produit. [!DNL Commerce] Administrateur.

Chacun de ces attributs peut être défini comme [&quot;searchable&quot;](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search) dans Admin. Lorsqu’ils sont définis sur &quot;pouvant faire l’objet d’une recherche&quot;, ces attributs peuvent être recherchés par [!DNL Live Search].

[Facettes](facets.md) sont des attributs de produit définis dans [!DNL Live Search] pour être filtrable. Tout attribut filtrable peut être défini comme une facette dans [!DNL Live Search] mais il existe des limites au nombre de facettes pouvant être recherchées simultanément.

[Synonymes](synonyms.md) sont des termes que vous pouvez définir pour guider les utilisateurs vers le produit approprié. Les utilisateurs qui recherchent un pantalon peuvent taper &quot;pantalon&quot; ou &quot;pantalons&quot;. Vous pouvez définir des synonymes de sorte que ces termes de recherche amènent les utilisateurs aux résultats &quot;pantalon&quot;.

## 6. Tester la connexion {#test-connection}

Maintenant que vos données de catalogue sont dans SaaS, vérifiez que les données de produit sont renvoyées dans les scénarios suivants :

- La variable [!UICONTROL Search] la zone renvoie les résultats correctement
- La navigation dans les catégories renvoie correctement les résultats.
- Les facettes sont disponibles sous forme de filtres sur les pages de résultats de recherche.

Si tout fonctionne correctement, [!DNL Live Search] est installé, connecté et prêt à l’emploi.

Si vous rencontrez des problèmes dans le storefront, vérifiez la variable `var/log/system.log` pour les erreurs ou échecs de communication de l’API côté services.

Pour autoriser [!DNL Live Search] via un pare-feu, ajoutez `commerce.adobe.io` à la liste autorisée.

## 7. Personnaliser pour votre vitrine

Vous avez installé le [!DNL Live Search] extension, synchronisé, validé et configuré vos données. Vous allez maintenant vous assurer que la variable [!DNL Live Search] Les widgets sont conformes à l’aspect de votre boutique.

Vous pouvez mettre en forme la fenêtre contextuelle et les widgets PLP en définissant des règles CSS personnalisées si nécessaire. Voir [Style des éléments contextuels](storefront-popover-styling.md) et [Widget de page de liste de produits](plp-styling.md).

Si vous souhaitez étendre les fonctionnalités des widgets, le code source de chacun d’eux est disponible dans un référentiel public.
Dans ce scénario, vous pouvez personnaliser le code JavaScript en fonction de vos besoins, puis héberger votre code personnalisé sur votre réseau de diffusion de contenu. Ce script personnalisé communique avec la variable [!DNL Live Search] et renvoie les résultats comme s’ils étaient normaux, ce qui vous permet de contrôler les fonctionnalités du widget.

- [Référentiel de widgets PLP](https://github.com/adobe/storefront-product-listing-page)
- [Référentiel de barre de recherche](https://github.com/adobe/storefront-search-as-you-type)

## Mise à jour [!DNL Live Search] {#update}

Avant de mettre à jour la recherche en direct, exécutez le code suivant depuis la ligne de commande pour vérifier la version de la recherche en direct installée :

```bash
composer show magento/module-live-search | grep version
```

Pour mettre à jour [!DNL Live Search], exécutez les opérations suivantes à partir de la ligne de commande :

```bash
composer update magento/live-search --with-dependencies
```

Pour effectuer une mise à jour vers une version majeure, telle que de 3.1.1 à 4.0.0, modifiez la racine du projet. [!DNL Composer] `.json` comme suit :

1. Si votre `magento/live-search` version est `3.1.1` ou version inférieure et que vous effectuez une mise à niveau vers la version `4.0.0` ou supérieur, exécutez la commande suivante avant la mise à niveau :

   ```bash
   bin/magento module:enable Magento_AdvancedSearch
   ```

   Pour plus d’informations sur la version actuellement installée `magento/live-search` version, exécutez la commande suivante :

   ```bash
   composer show magento/live-search
   ```

1. Ouvrez la racine `composer.json` fichier et recherchez `magento/live-search`.

1. Dans le `require` , mettez à jour le numéro de version comme suit :

   ```json
   "require": {
      ...
      "magento/live-search": "^4.0",
      ...
    }
   ```

1. Enregistrer `composer.json`. Exécutez ensuite la commande suivante à partir de la ligne de commande :

   ```bash
   composer update magento/live-search --with-dependencies
   ```

## Désinstallation [!DNL Live Search] {#uninstall}

Pour désinstaller [!DNL Live Search], voir [Désinstallation des modules](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/uninstall-modules).

## [!DNL Live Search] packages {#packages}

La variable [!DNL Live Search] L’extension se compose des packages suivants :

| Package | Description |
|--- |--- |
| `module-live-search` | Permet aux commerçants de configurer leurs paramètres de recherche pour la facette, les synonymes, les règles de requête, etc., et permet d’accéder à un terrain de jeu GraphQL en lecture seule pour tester les requêtes à partir de la variable *Administration*. |
| `module-live-search-adapter` | Permet d’acheminer les requêtes de recherche du storefront vers le [!DNL Live Search] et effectue le rendu des résultats dans le storefront. <br />- Navigation dans les catégories - achemine les demandes depuis le storefront [navigation supérieure](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/navigation/navigation-top) au service de recherche.<br />- Recherche globale - achemine les requêtes de la [recherche rapide](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search) dans le coin supérieur droit du storefront vers la propriété [!DNL Live Search] service. |
| `module-live-search-storefront-popover` | Une fenêtre contextuelle &quot;Rechercher lorsque vous tapez&quot; remplace la recherche rapide standard et renvoie les données et les miniatures des principaux résultats de la recherche. |

## [!DNL Live Search] dependencies {#dependencies}

Les éléments suivants [!DNL Live Search] les dépendances sont capturées par [!DNL Composer].

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

[!DNL Live Search] communique par le biais du point de terminaison à l’adresse `https://catalog-service.adobe.io/graphql`.

As [!DNL Live Search] n&#39;a pas accès à la base de données complète des produits, [!DNL Live Search] GraphQL et Commerce core GraphQL n’auront pas une parité complète.

Il est recommandé d’appeler directement les API SaaS, en particulier le point d’entrée du service de catalogue.

- Obtenir des performances et réduire la charge du processeur en contournant le processus base de données Commerce/Graphql
- Profitez de la fonction [!DNL Catalog Service] fédération à appeler [!DNL Live Search], [!DNL Catalog Service], et [!DNL Product Recommendations] à partir d’un seul point de terminaison.

Pour certains cas d’utilisation, il peut être préférable d’appeler [!DNL Catalog Service] pour plus d’informations sur les produits et les cas similaires. Voir [refineProduct](https://developer.adobe.com/commerce/services/graphql/catalog-service/refine-product/) pour plus d’informations.

Si vous disposez d’une implémentation personnalisée sans interface utilisateur graphique, extrayez le [!DNL Live Search] implémentations de référence :

- [Widget PLP](https://github.com/adobe/storefront-product-listing-page)
- [Champ de recherche en direct](https://github.com/adobe/storefront-search-as-you-type)

Si vous n’utilisez pas les composants par défaut, tels que l’adaptateur de recherche ou les widgets sur Luma ou les widgets d’AEM CIF, les événements (données de parcours de navigation qui alimentent Adobe Sensei pour les mesures de marchandisage et de performances intelligentes) ne fonctionneront pas immédiatement et nécessitent un développement personnalisé pour implémenter des événements sans interface.

La dernière version de [!DNL Live Search] utilise déjà [!DNL Catalog Service].

### Prise en charge linguistique

[!DNL Live Search] Les widgets prennent en charge les langues suivantes :

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

Si le widget détecte que le paramètre de langue d’administration de Commerce (_Magasins_ > Paramètres > _Configuration_ > _Général_ > Options de pays) correspond à une langue prise en charge. Par défaut, cette langue est utilisée. Sinon, les widgets sont définis par défaut sur Anglais.

Les administrateurs peuvent également définir la langue de la variable [index de recherche](settings.md#language), pour améliorer les résultats de la recherche.

### Référentiel de code de widget

Le widget Page de liste de produits et le widget Champ de recherche en direct peuvent tous deux être téléchargés à partir de leur référentiel github.

Cela permet aux développeurs de personnaliser entièrement les fonctionnalités et le style. Ces utilisateurs hébergent le code eux-mêmes tout en tirant parti de la fonction [!DNL Live Search] service.

- [Widget PLP](https://github.com/adobe/storefront-product-listing-page)
- [Barre de recherche](https://github.com/adobe/storefront-search-as-you-type)

### Inventory management

[!DNL Live Search] prend [Inventory management](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/introduction) Fonctionnalités de Commerce (anciennement appelées inventaire multi-source ou MSI). Pour activer la prise en charge complète, vous devez [update](install.md#update) le module de dépendance ; `commerce-data-export` vers la version 102.2.0+.

[!DNL Live Search] renvoie une valeur booléenne indiquant si un produit est disponible dans Inventory management, mais ne contient pas d’informations sur la source qui possède le stock.

### Indexateur de prix

Les clients Live Search peuvent utiliser la nouvelle [Indexeur de prix SaaS](../price-index/price-indexing.md), qui accélère les mises à jour des changements de prix et le temps de synchronisation.

### Prise en charge des prix

Les widgets de recherche en direct prennent en charge la plupart, mais pas tous les types de prix pris en charge par Adobe Commerce.

Actuellement, les prix de base sont pris en charge. Les prix avancés non pris en charge sont les suivants :

- Coût
- Prix publicitaire minimal

Regarder [Mesh de l’API](../catalog-service/mesh.md) pour des calculs de prix plus complexes.

Le format de prix prend en charge le paramètre de configuration des paramètres régionaux dans l’instance Commerce : *Magasins* > Paramètres > *Configuration* > Général > *Général* > Options locales > Paramètres régionaux.

### Prise en charge de storefront sans interface

Si vous le souhaitez, vous devrez peut-être installer le `module-data-services-graphql` qui étend la couverture GraphQL existante de l’application afin d’inclure les champs requis pour la collecte de données comportementales storefront.

```bash
composer require magento/module-data-services-graphql
```

Ce module ajoute des contextes supplémentaires aux requêtes GraphQL :

- `dataServicesStorefrontInstanceContext`
- `dataServicesMagentoExtensionContext`
- `dataServicesStoreConfigurationContext`

### Prise en charge des PWA

[!DNL Live Search] fonctionne avec PWA Studio, mais les utilisateurs peuvent voir de légères différences par rapport aux autres mises en oeuvre de Commerce. Les fonctionnalités de base telles que la recherche et la liste de produits fonctionnent dans Venia, mais certaines permutations de Graphql peuvent ne pas fonctionner correctement. Il peut également y avoir des différences de performances.

- L’implémentation actuelle du PWA de [!DNL Live Search] nécessite plus de temps de traitement pour renvoyer les résultats de recherche que [!DNL Live Search] avec la vitrine Commerce native.
- [!DNL Live Search] dans PWA ne prend pas en charge [gestion des événements](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/). Par conséquent, les rapports de recherche et le marchandisage intelligent fonctionneront.
- Filtrage directement sur `description`, `name`, `short_description` n’est pas pris en charge par GraphQL lorsqu’il est utilisé avec [PWA](https://developer.adobe.com/commerce/pwa-studio/), mais ils sont renvoyés avec un filtre plus général.

Pour utiliser [!DNL Live Search] avec PWA Studio, les intégrateurs doivent également :

1. Installer [livesearch-storefront-utils](https://www.npmjs.com/package/@magento/ds-livesearch-storefront-utils).
1. Définissez la variable `environmentId` dans le `storeDetails` .

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

[!DNL Live Search] collecte des données d’interaction utilisateur dans le cadre de ses fonctionnalités de base et utilise des cookies pour stocker ces données. Lors de la collecte de toute information utilisateur, l’utilisateur doit accepter de stocker les cookies. [!DNL Live Search] et [!DNL Product Recommendations] partagez le flux de données et, par conséquent, le même mécanisme de cookie. En savoir plus à ce sujet dans [Gérer les restrictions de cookie](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/developer/setting-cookie).
