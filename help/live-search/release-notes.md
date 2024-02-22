---
title: "[!DNL Live Search] Notes de mise à jour"
description: "Informations les plus récentes sur la version [!DNL Live Search] d’Adobe Commerce."
exl-id: 2a581e43-35f5-48ce-9752-844430ccdebf
feature: Services, Search, Release Notes
source-git-commit: 89f0cd15e7eeb7f8f1f76df7a3612ba3ef02391e
workflow-type: tm+mt
source-wordcount: '1900'
ht-degree: 0%

---

# [!DNL Live Search] Notes de mise à jour

Ces notes de mise à jour décrivent les dernières versions de [!DNL Live Search].
La prise en charge de la version majeure actuelle est fournie. Les notes de mise à jour des versions antérieures sont fournies à titre de référence.
Les mises à jour sont les suivantes :

![Nouveau](../assets/new.svg) Nouvelles fonctionnalités
![Correction](../assets/fix.svg) Correctifs et améliorations
![Bogue](../assets/bug.svg) Problèmes connus

## Mises à jour du service hébergé

Ces notes décrivent les mises à jour publiées en dehors d’une version ou les améliorations apportées au service hébergé.

_13 février 2024_

![Nouveau](../assets/new.svg) [!DNL Live Search] prend désormais en charge la définition d’une règle par défaut pour [Marchandisage des recherches](rules.md).

_27 octobre 2023_

![Nouveau](../assets/new.svg) La variable [!DNL Live Search] Le widget PLP prend désormais en charge les échantillons de couleurs.

_12 octobre 2023_

![Nouveau](../assets/new.svg) Les administrateurs de commerce peuvent maintenant spécifier la langue de l’index pour [!DNL Live Search]. Voir [Paramètres](settings.md).
![Correction](../assets/fix.svg) L’onglet &quot;Règles de recherche&quot; a été renommé &quot;Marchandisage de recherche&quot;.

_13 juin 2023_

![Correction](../assets/fix.svg) Correction d’un problème en raison duquel certains caractères, tels que les guillemets ou les apostrophes, provoquaient des problèmes de classement. La réindexation résoudra ces problèmes.

_25 avril 2023_

![Nouveau](../assets/new.svg) [!DNL Live Search] les clients peuvent désormais profiter de la nouvelle [Indexeur de prix SaaS](../price-index/index.md).

## [!DNL Live Search] 4.1.0 {#410}

_22 février 2024_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

### Nouvelles fonctionnalités

![Nouveau](../assets/new.svg) La variable [[!DNL Data Management Dashboard]](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-dashboard.html) est désormais disponible. Ce tableau de bord restructuré fournit des informations sur les flux de données pour [!DNL Product Recommendations], [!DNL Live Search], et [!DNL Catalog Service].
![Nouveau](../assets/new.svg) Plusieurs nouvelles fonctionnalités ont été ajoutées au [Widget PLP](plp-styling.md):

* Modification du mode Liste/grille
* Boutons Ajouter au panier
* Prise en charge des échantillons
* Images multiples par produit
* Curseurs de prix
* Prise en charge linguistique

Les vendeurs doivent mettre à niveau la variable [!DNL Live Search] extension vers la version >= 4.1.0 pour accéder à ces fonctionnalités.

### Mises à jour

![Correction](../assets/fix.svg) Correction d’un problème qui provoquait une erreur lorsque des utilisateurs invités ajoutaient des produits à un panier dans des vues de magasin autres que celles par défaut.
![Correction](../assets/fix.svg) Correction d’un problème en raison duquel la fenêtre contextuelle de recherche affichait toujours le symbole de devise devant la valeur de prix, quels que soient les paramètres régionaux.
![Correction](../assets/fix.svg) Suppression des définitions de type inutiles pour les modules externes principaux désactivés afin de résoudre les problèmes de compatibilité lors de l’installation.

## [!DNL Live Search] 4.0.0 {#400}

_13 novembre 2023_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

### Nouvelles fonctionnalités

![Nouveau](../assets/new.svg) [!DNL Live Search] prend désormais en charge les échantillons de couleurs dans le widget PLP.
![Nouveau](../assets/new.svg) [!DNL Live Search] affiche maintenant le nom de la catégorie plutôt que l’ID de catégorie.
![Nouveau](../assets/new.svg) [!DNL Live Search] prend désormais en charge les prix balisés dans le widget PLP.
![Nouveau](../assets/new.svg) Ajout du bouton &quot;Masquer les filtres&quot; pour masquer le panneau des filtres.


### Mises à jour

![Correction](../assets/fix.svg) La variable [!DNL Live Search] Le widget PLP est désormais activé par défaut pour les nouvelles installations.
![Correction](../assets/fix.svg) Reconfiguration des styles CSS pour mieux isoler les classes de widget.
![Correction](../assets/fix.svg) Correctifs de bogues mineurs

Après avoir installé la version 3.1.1 ou ultérieure, activez les nouveaux indexeurs :

* Flux de prix du produit
* Porte le flux de données du site web
* Porte le flux de données de groupes de clients

Après la mise à niveau, testez la configuration mise à jour dans l’AQ ou l’Évaluation avant de publier les modifications en production.

## Versions précédentes

+++3.1.1 et versions antérieures

## [!DNL Live Search] 3.1.1 {#311}

_15 septembre 2023_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) Un nouvel onglet Marchandisage des catégories a été ajouté. Les utilisateurs peuvent désormais ajouter des classements intelligents et des classements manuels (épingle, amplification, inhumation, masquage) par catégorie.
![Nouveau](../assets/new.svg) Les utilisateurs peuvent ajouter une règle de catégorie unique avec un classement intelligent ou manuel
![Nouveau](../assets/new.svg) Les utilisateurs peuvent désormais ajouter des règles de classement intelligent aux sous-catégories.
![Nouveau](../assets/new.svg) Des informations détaillées sont fournies lors de la suppression de sous-catégories avec un classement intelligent
![Nouveau](../assets/new.svg) Ajout de la possibilité de supprimer des règles pour les stratégies de classement héritées
![Nouveau](../assets/new.svg) Ajout de la possibilité de supprimer des règles pour une seule catégorie
![Nouveau](../assets/new.svg) Les utilisateurs peuvent désormais rechercher par nom de catégorie lors de l’ajout d’une règle.
![Nouveau](../assets/new.svg) Avec l’affichage de l’arborescence des catégories, les utilisateurs peuvent désormais afficher la catégorie pour laquelle des règles sont appliquées.
![Nouveau](../assets/new.svg) L’aperçu des catégories affiche uniquement la catégorie sélectionnée.
![Nouveau](../assets/new.svg) AEM CIF [widget contextuel](https://github.com/adobe/aem-cif-guides-venia/pull/319) et [Widget PLP](https://github.com/adobe/aem-cif-guides-venia/pull/320) les composants permettent aux AEM sites de tirer parti des [!DNL Live Search].

### Mises à jour

![Correction](../assets/fix.svg) La taille de la table des flux Produits et Prix a été considérablement réduite. Tableaux `catalog_data_exporter_products` et `catalog_data_exporter_product_prices` devrait voir une réduction substantielle de la taille.
![Correction](../assets/fix.svg) L’onglet &quot;Règles&quot; est renommé &quot;Règles de recherche&quot;.
![Correction](../assets/fix.svg) Lors du classement par &quot;tendance&quot;, vous pouvez désormais choisir entre : * 3 jours (par défaut) * 14 jours * 30 jours
![Correction](../assets/fix.svg) &quot;Événements&quot; (Amplifier/Epingler/Masquer) a été renommé &quot;Classement manuel&quot;
![Correction](../assets/fix.svg) &quot;Type de classement&quot; a été renommé &quot;Classement intelligent&quot;.
![Correction](../assets/fix.svg) Correctifs de bogues mineurs

## [!DNL Live Search] 3.1.0 {#310}

_1 septembre 2023_

[!BADGE Pris en charge]{type="Informatif" tooltip="Pris en charge"}

### Mises à jour

![Correction](../assets/fix.svg) Le widget Liste des produits a été mis à jour pour utiliser la variable [API Catalog Service](https://developer.adobe.com/commerce/services/graphql/catalog-service/product-search/).

## [!DNL Live Search] 3.0.2 {#302}

_7 août 2023_

[!BADGE Pris en charge]{type="Informatif" tooltip="Pris en charge"}

### Nouvelles fonctionnalités

![Nouveau](../assets/new.svg) Les valeurs suivantes ont été ajoutées au `storeDetails` objet :

* &quot;Autoriser tous les produits par page&quot;
* Taux de change
* &quot;Produits par page sur les valeurs autorisées de la grille&quot;
* &quot;Produits par page sur la valeur par défaut de la grille&quot;
* Langue du magasin

### Mises à jour

![Correction](../assets/fix.svg) Les modules de service de catalogue ont été ajoutés au métaphorage pour prendre en charge la récupération avancée des données.
![Correction](../assets/fix.svg) La variable **Mon compte** La navigation sur les pages ne disparaît plus lors de l’utilisation du widget Page de liste de produits .

Les vendeurs doivent mettre à niveau la variable [!DNL Live Search] version d’extension >= 3.0.2 pour accéder à ces fonctionnalités.

Il est recommandé de mettre à niveau et de tester avant de passer en production. Envisagez de mettre à niveau l’environnement de production pendant les heures creuses après avoir vérifié les résultats de l’environnement de test.

### Limites

L’utilisation du widget Page de liste des produits de la recherche en direct entraînera l’échec du Gestionnaire de balises de Google. Utilisez l’adaptateur de recherche par défaut si Google Tag Manager est nécessaire.

## [!DNL Live Search] 3.0.1 {#301}

_14 mars 2023_

[!BADGE Pris en charge]{type="Informatif" tooltip="Pris en charge"}

### Nouvelles fonctionnalités

![Nouveau](../assets/new.svg) Carte des éléments de produit dans l’aperçu des règles
![Nouveau](../assets/new.svg) [Widget de page de liste de produits](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/live-search-storefront/plp-styling.html)
![Nouveau](../assets/new.svg) [Options de filtrage des catégories](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/#facets)
![Nouveau](../assets/new.svg) Ajout de la possibilité de faire glisser et de déposer des événements Pin
![Nouveau](../assets/new.svg) Nouvelles actions Epingler : * Epingler à l’emplacement - Bouton Epingler pour créer l’événement Epingler d’un seul clic * Epingler au haut - Placer le produit dans la première position * Epingler au bas des résultats * Détacher un événement d’un seul clic
![Nouveau](../assets/new.svg) [Classement intelligent des règles](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/live-search-admin/rules/rules-add.html#ranking-type)
![Nouveau](../assets/new.svg) [!DNL Live Search] prend désormais en charge l’intégralité [Inventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/introduction.html) Fonctionnalités dans Commerce (anciennement appelées inventaire multi-source ou MSI). Pour activer la prise en charge complète, vous devez [update](install.md#update) le module de dépendance ; `commerce-data-export` vers la version 102.2.0+.

### Mises à jour

![Correction](../assets/fix.svg) La configuration des règles trie désormais automatiquement les positions de manière unique.
![Correction](../assets/fix.svg) La suppression d’un événement existant met désormais à jour l’aperçu
![Correction](../assets/fix.svg) Les règles sans événement peuvent être enregistrées.
![Correction](../assets/fix.svg) Suppression du sélecteur de facettes &quot;Select Type&quot;
![Correction](../assets/fix.svg) Ajout d’un nouvel état &quot;En édition&quot; pour les règles non enregistrées

### Correctifs

![Correction](../assets/fix.svg) Correction d’une erreur du serveur en cas d’événement inachevé au cours de l’enregistrement.
![Correction](../assets/fix.svg) Correction de la suppression correcte d’un événement spécifique lorsqu’il existe plusieurs événements.
![Correction](../assets/fix.svg) Correction d’un événement de règle existant qui ne se mettait pas à jour lors de l’ajout d’un nouvel événement
![Correction](../assets/fix.svg) Corrigé lors du second clic &quot;Modifier&quot; à partir des détails, [!DNL Live Search] page nécessitant un rechargement
![Correction](../assets/fix.svg) Synonymes : correction d’un problème lorsqu’un utilisateur cliquait en dehors d’une entrée, empêchant la sélection du champ.
![Correction](../assets/fix.svg) Autres correctifs mineurs et mises à jour des performances


![Bogue](../assets/bug.svg) - Le classement par &quot;Recommandé pour vous&quot; n’est pris en charge que dans les widgets de recherche en direct. Elle n’est pas prise en charge avec la fonctionnalité de recherche par défaut de Luma et de PWA.
![Bogue](../assets/bug.svg) - Les facettes d’attribut de prix personnalisées ne s’affichent pas correctement dans Luma, mais l’API les filtre correctement.

Les vendeurs doivent mettre à niveau la variable [!DNL Live Search] version d’extension >= 3.0.1 pour accéder à ces fonctionnalités.

Il est recommandé de mettre à niveau et de tester avant de passer en production. Envisagez de mettre à niveau l’environnement de production pendant les heures creuses après avoir vérifié les résultats de l’environnement de test.

## [!DNL Live Search] 2.0.5 {#205}

[!BADGE Pris en charge]{type="Informatif" tooltip="Pris en charge"}

![Correction](../assets/fix.svg) - La recherche en direct renvoie une erreur lorsque les ressources du SDK n’étaient pas disponibles en raison de problèmes de réseau. Ce bogue a été corrigé.

Les commerçants doivent mettre à niveau l’extension Live Search >= 2.0.5 pour accéder à ces fonctionnalités.

Il est recommandé de mettre à niveau et de tester avant de passer en production. Envisagez de mettre à niveau l’environnement de production pendant les heures creuses après avoir vérifié les résultats de l’environnement de test.

### [!DNL Live Search] 2.0.4 {#204}

[!BADGE Pris en charge]{type="Informatif" tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) La recherche en direct prend désormais en charge le filtrage selon le paramètre &quot;Afficher les produits en rupture de stock&quot; dans l’administrateur. Si &quot;Produits en rupture de stock&quot; est défini sur false, `inStock = true` est ajouté au filtre.
![Correction](../assets/fix.svg) Pour améliorer les performances, le bloc &quot;Suggestions&quot; a été supprimé de la fenêtre contextuelle Recherche en direct . Les données sont toujours transmises par GraphQL, au cas où vous souhaitez remplacer la fonctionnalité.
![Correction](../assets/fix.svg) `categories` et `categoryPath` ont remplacé `categoryIds` pour le filtrage par catégorie. En savoir plus dans la section [productSearch](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/) rubrique.
![Correction](../assets/fix.svg) Auparavant, un utilisateur lié à une entreprise B2B recevait un code de groupe client incorrect lors des recherches. La fonction de recherche en direct renvoie désormais la valeur correcte.
![Correction](../assets/fix.svg) Auparavant, la recherche en direct renvoyait une erreur lors de la recherche d’un terme qui n’existe pas. Ce bogue est maintenant corrigé.

Les vendeurs doivent mettre à niveau la variable [!DNL Live Search] version d’extension >= 2.0.4 pour accéder à ces fonctionnalités.

Il est conseillé aux utilisateurs de mettre à niveau et de tester avant de passer en production. Envisagez de mettre à niveau l’environnement de production pendant les heures creuses après avoir vérifié les résultats de l’environnement de test.

### [!DNL Live Search] 2.0.3 {#203}

[!BADGE Pris en charge]{type="Informatif" tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) La recherche en direct prend désormais en charge les fonctionnalités B2B en respectant les autorisations de catégorie, les catalogues partagés et la tarification spécifique aux groupes de clients.

Les vendeurs doivent mettre à niveau la variable [!DNL Live Search] version d’extension >= 2.0.3 pour accéder à ces fonctionnalités.

Il est conseillé aux utilisateurs de mettre à niveau et de tester avant de passer en production. Envisagez de mettre à niveau l’environnement de production pendant les heures creuses après avoir vérifié les résultats de l’environnement de test.

### [!DNL Live Search] 2,0 {#20}

[!BADGE Pris en charge]{type="Informatif" tooltip="Pris en charge"}

Existant [!DNL Live Search] Les installations doivent être mises à niveau vers [!DNL Live Search] 2.0.0 pour tirer parti des nouvelles fonctionnalités, correctifs et améliorations suivants :

![Nouveau](../assets/new.svg) [!DNL Live Search] prend désormais en charge PHP 8.1 pour les installations exécutant Adobe Commerce 2.4.4.
![Nouveau](../assets/new.svg) La variable `Magento_ElasticsearchCatalogPermissionsGraphQl` module est ajouté à la liste des modules désactivés lors de l’installation.
![Nouveau](../assets/new.svg) Le nombre de lignes disponibles dans la variable [[!DNL storefront popover]](quick-tour.md) peut être configuré à partir du *Administration*.
![Nouveau](../assets/new.svg) Beta [PWA](https://developer.adobe.com/commerce/pwa-studio/) pris en charge pour [!DNL Live Search].
![Nouveau](../assets/new.svg) La variable [!DNL Live Search] le processus d’installation est mis à jour avec des modifications avancées des processus.
![Correction](../assets/fix.svg) [Recherche avancée](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#advanced-search) lien supprimé du pied de page du storefront.
![Bogue](../assets/bug.svg) Les attributs de produit suivants ne sont pas pris en charge par [API Commerce GraphQL](https://developer.adobe.com/commerce/services/graphql/live-search/) lorsqu’elle est utilisée en rapport avec la version bêta de PWA : `description`, `name`, `short_description`
![Bogue](../assets/bug.svg) La version bêta de PWA pour [!DNL Live Search] ne prend pas en charge [gestion des événements](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/).

### [!DNL Live Search] 1.3.1 {#131}

[!BADGE Pris en charge]{type="Informatif" tooltip="Pris en charge"}

![Correction](../assets/fix.svg) [Attribut de prix personnalisé](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/attributes-input-types.html) ne renvoie plus d’erreur lorsqu’elle est configurée en tant que [facette]({% lien live-search/facets-add.md %}).
![Correction](../assets/fix.svg) Correction d’un problème en raison duquel une erreur se produisait lorsqu’aucune [symbole de devise](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/currency/currency-configuration.html#step-5%3A-customize-currency-symbols-(optional)) (`data-currency-symbol`) est disponible.
![Correction](../assets/fix.svg) [[!DNL Storefront popover]](storefront-popover.md) affiche désormais la variable [Prix spécial](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/product-price-special.html) (prix final minimum) le cas échéant.

### [!DNL Live Search] 1.3.0 {#130}

[!BADGE Pris en charge]{type="Informatif" tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) [Performances](performance.md) le tableau de bord des rapports fournit des informations sur les termes de recherche que les acheteurs utilisent.
![Nouveau](../assets/new.svg) [!DNL Live Search] [SDK des événements Storefront](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/) permet d’accéder à une couche de données commune avec des services de publication et d’abonnement d’événements, ainsi que des mesures.
![Correction](../assets/fix.svg) La variable [[!DNL Storefront popover]](storefront-popover.md) comporte une nouvelle `active` pour la classe `.search-autocomplete` conteneur contrôlant la visibilité.
![Correction](../assets/fix.svg) Dans la vitrine, le [Termes de recherche](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-terms.html#popular-search-terms) lien de pied de page supprimé et son cache désactivé pour [!DNL Live Search] installations.
![Bogue](../assets/bug.svg) Le correctif pour l’adaptateur de recherche gère les produits en double.
![Bogue](../assets/bug.svg) [!DNL Live Search] prend [source unique](https://experienceleague.adobe.com/docs/commerce-admin/inventory/sources/sources-manage.html) emplacements d’inventaire (physiques) avec plusieurs emplacements (virtuels) [stocks](https://experienceleague.adobe.com/docs/commerce-admin/inventory/stocks/stocks-manage.html). Plusieurs sources d’inventaire ne sont désormais pas prises en charge.

### [!DNL Live Search] 1.2.0 {#120}

[!BADGE Pris en charge]{type="Informatif" tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) [[!DNL Storefront popover]](storefront-popover.md) affiche les produits suggérés et les images miniatures des principaux résultats de recherche sous la forme de requêtes de type shoppers dans la zone de recherche.
![Nouveau](../assets/new.svg) Commerce *Administration* la session reste ouverte pendant les longues périodes d’inactivité du clavier ;
![Nouveau](../assets/new.svg) [!DNL Live Search] est activé automatiquement après l’intégration
![Correction](../assets/fix.svg) Le temps d’indexation initial est inférieur à une heure
![Correction](../assets/fix.svg) Mises à jour incrémentielles des produits quasiment en temps réel (après installation et configuration)
![Correction](../assets/fix.svg) Tri des colonnes dans l’éditeur de synchronisation
![Correction](../assets/fix.svg) [!DNL Live Search] ne renvoie plus d’erreur si les critères de recherche contiennent une valeur d’ordre de tri vide
![Correction](../assets/fix.svg) Le filtrage de plage ne rompt plus si les codes d’attribut contiennent des chaînes &quot;to&quot; ou &quot;from&quot;

### [!DNL Live Search] 1.1.0 {#110}

[!BADGE Pris en charge]{type="Informatif" tooltip="Pris en charge"}

![Bogue](../assets/bug.svg) La variable [!DNL Live Search] ne prend en charge que les [monnaie de base](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/currency/currency-configuration.html) de l’installation Adobe Commerce.
![Bogue](../assets/bug.svg) Lors de l’ajout d’une facette, le flux d’attributs de produit ne se met pas à jour correctement lorsqu’il est défini sur `Update on Save`. Pour éviter ce problème, accédez à [Gestion des index](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html) et définissez le flux Attributs du produit sur `Update by Schedule`.
![Bogue](../assets/bug.svg) [!DNL Live Search] les synonymes sont définis par vue de magasin, mais sont actuellement stockés par site web et identifiés par une combinaison de `environmentId` et `storeViewCode`. Par conséquent, tous les sites web et toutes les vues de magasin dans l’installation Adobe Commerce partagent des synonymes. Le dernier ensemble de synonymes créé pour la vue de magasin est prioritaire.
![Bogue](../assets/bug.svg) Si un terme de synonyme contient plusieurs mots, chaque mot est traité comme un synonyme distinct. Par exemple, si vous définissez &quot;pièce temporelle&quot; comme un synonyme de &quot;montre&quot;, &quot;heure&quot; et &quot;pièce&quot; sont tous deux traités comme des synonymes de montre.

+++

## Documentation

Pour en savoir plus :

* [Documentation destinée aux développeurs Adobe Commerce](https://developer.adobe.com/commerce/docs)
* [Guide de l’utilisateur d’Adobe Commerce](https://experienceleague.adobe.com/docs/commerce.html)
* [[!DNL Live Search] sur Marketplace](https://commercemarketplace.adobe.com/magento-live-search.html)
