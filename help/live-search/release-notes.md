---
title: "[!DNL Live Search] Notes de mise à jour"
description: "Informations les plus récentes sur la version de  [!DNL Live Search] à partir d’Adobe Commerce."
exl-id: 2a581e43-35f5-48ce-9752-844430ccdebf
feature: Services, Search, Release Notes
source-git-commit: 7f536c93ab1c87bf88bc892b2a485067fa8f8110
workflow-type: tm+mt
source-wordcount: '2042'
ht-degree: 0%

---

# Notes de mise à jour [!DNL Live Search]

Ces notes de mise à jour décrivent les dernières versions de [!DNL Live Search].
La prise en charge de la version majeure actuelle est fournie. Les notes de mise à jour des versions antérieures sont fournies à titre de référence.
Les mises à jour sont les suivantes :

![New](../assets/new.svg) Nouvelles fonctionnalités
![ Correctifs et améliorations ](../assets/fix.svg)
![Bug](../assets/bug.svg) Problèmes connus

## Mises à jour du service hébergé

Ces notes décrivent les mises à jour publiées en dehors d’une version ou les améliorations apportées au service hébergé.

_19 septembre 2024_

![Nouveau](../assets/new.svg) Une version bêta qui prend en charge trois nouvelles fonctionnalités de recherche est disponible : couches, commence par et contient. [En savoir plus](install.md#install-the-live-search-beta).

_4 septembre 2024_

![Correctif](../assets/fix.svg) Augmentation du nombre maximal de compartiments pouvant être renvoyés [dans une facette](boundaries-limits.md#facets) à 100.

_7 août 2024_

![Correctif](../assets/fix.svg) Augmentation de la valeur d’intervalle maximal ou de la plage de prix pour [faceting de prix](settings.md#price-faceting) de 10 000 à 40 000 000.

_13 février 2024_

![New](../assets/new.svg) [!DNL Live Search] prend désormais en charge la définition d’une règle par défaut pour le [marchandisage de recherche](rules.md).

_12 octobre 2023_

![New](../assets/new.svg) Les administrateurs Commerce peuvent désormais spécifier la langue de l’index pour [!DNL Live Search]. Voir [Paramètres](settings.md).
![Correctif](../assets/fix.svg) L’onglet &quot;Règles de recherche&quot; a été renommé &quot;Marchandisage de recherche&quot;.

_13 juin 2023_

![Correctif](../assets/fix.svg) Correction d’un problème en raison duquel certains caractères, tels que les guillemets ou les apostrophes, provoquaient des problèmes de classement. La réindexation résout ces problèmes.

_25 avril 2023_

Les clients ![nouveaux](../assets/new.svg) [!DNL Live Search] peuvent désormais profiter du nouvel [indexeur de prix SaaS](../price-index/price-indexing.md).

### Widget PLP

_31 mai 2024_

![New](../assets/new.svg) Version 2.0.0 du widget PLP, qui ajoute la prise en charge des fonctionnalités suivantes :

- Boutons Ajouter au panier - Disponible uniquement pour les produits simples.
- Plusieurs images par produit : l’image peut changer lorsqu’une autre couleur est sélectionnée pour un produit configurable.

_27 octobre 2023_

![Nouveau](../assets/new.svg) Le widget [!DNL Live Search] PLP prend désormais en charge les échantillons de couleurs.

## [!DNL Live Search] 4.2.1 {#421}

_31 juillet 2024_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Correctif](../assets/fix.svg) Correction d’un problème en raison duquel certains scripts ne se chargeaient pas sur la page de passage en caisse.
![Fix](../assets/fix.svg) Correction d’une version de dépendance dans le fichier `composer.json`.

## [!DNL Live Search] 4.2.0 {#420}

_31 mai 2024_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) Mise à jour de l’extension Live Search pour utiliser les widgets PLP version 2.0.0.

## [!DNL Live Search] 4.1.2 {#412}

_16 mai 2024_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

### Mises à jour

![Fix](../assets/fix.svg) Correction de la requête GraphQL [`productSearch`](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/#filtering-by-categories) pour qu’elle soit correctement filtrée en fonction des `categoryPath` et `categoryList` pour les catégories.

## [!DNL Live Search] 4.1.1 {#411}

_19 mars 2024_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

### Nouvelles fonctionnalités

![Nouveau](../assets/new.svg) Ajout de la prise en charge de la langue pour le polonais.
![New](../assets/new.svg) [!DNL Live Search] prend désormais en charge PHP 8.3 pour les installations exécutant Adobe Commerce 2.4.4.

## [!DNL Live Search] 4.1.0 {#410}

_22 février 2024_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

### Nouvelles fonctionnalités

![Nouveau](../assets/new.svg) [[!DNL Data Management Dashboard]](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard) est désormais disponible. Ce tableau de bord repensé fournit des informations sur les flux de données pour [!DNL Product Recommendations], [!DNL Live Search] et [!DNL Catalog Service].

### Mises à jour

![Correctif](../assets/fix.svg) Correction d’un problème qui provoquait une erreur lorsque des utilisateurs invités ajoutaient des produits à un panier dans des vues de magasin autres que celles par défaut.
![Correctif](../assets/fix.svg) Correction d’un problème en raison duquel la fenêtre contextuelle de recherche affichait toujours le symbole de devise devant la valeur du prix, quels que soient les paramètres régionaux.
![Fix](../assets/fix.svg) Suppression des définitions de type inutiles pour les modules externes principaux désactivés afin de résoudre les problèmes de compatibilité lors de l’installation.

## [!DNL Live Search] 4.0.0 {#400}

_13 novembre 2023_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

### Nouvelles fonctionnalités

![New](../assets/new.svg) [!DNL Live Search] prend désormais en charge les échantillons de couleurs dans le widget PLP.
![New](../assets/new.svg) [!DNL Live Search] affiche désormais le nom de la catégorie plutôt que l’ID de la catégorie.
![New](../assets/new.svg) [!DNL Live Search] prend désormais en charge les prix récurrents dans le widget PLP.
![Nouveau](../assets/new.svg) Ajout du bouton &quot;Masquer les filtres&quot; pour masquer le panneau des filtres.


### Mises à jour

![Fix](../assets/fix.svg) Le widget [!DNL Live Search] PLP est désormais activé par défaut pour les nouvelles installations.
![Fix](../assets/fix.svg) Reconfiguration des styles CSS pour mieux isoler les classes de widget.
![Correctif](../assets/fix.svg) Correctifs de bogues mineurs

Après avoir installé la version 3.1.1 ou ultérieure, activez les nouveaux indexeurs :

- Flux de prix du produit
- Porte le flux de données du site web
- Porte le flux de données de groupes de clients

Après la mise à niveau, testez la configuration mise à jour dans l’AQ ou l’Évaluation avant de publier les modifications en production.

## Versions précédentes

+++3.1.1 et versions antérieures

## [!DNL Live Search] 3.1.1 {#311}

_15 septembre 2023_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) Un nouvel onglet Marchandisage de catégorie a été ajouté. Les utilisateurs peuvent désormais ajouter des classements intelligents et des classements manuels (épingle, amplification, inhumation, masquage) par catégorie.
![New](../assets/new.svg) Les utilisateurs peuvent ajouter une règle de catégorie unique avec un classement intelligent ou manuel
![Nouveaux](../assets/new.svg) utilisateurs peuvent désormais ajouter des règles de classement intelligent aux sous-catégories
![Nouveau](../assets/new.svg) Des informations détaillées sont fournies lors de la suppression de sous-catégories avec un classement intelligent
![Nouveau](../assets/new.svg) Possibilité de supprimer des règles pour les stratégies de classement héritées
![Nouveau](../assets/new.svg) Possibilité de supprimer des règles pour une seule catégorie
![New](../assets/new.svg) Les utilisateurs peuvent désormais effectuer des recherches par nom de catégorie lors de l’ajout d’une règle
![Nouveau](../assets/new.svg) Avec l’arborescence des catégories, les utilisateurs peuvent désormais afficher la catégorie pour laquelle des règles sont appliquées.
![New](../assets/new.svg) Category Preview affiche uniquement la catégorie sélectionnée.
![Nouveau](../assets/new.svg) AEM les composants CIF [Widget de fenêtre contextuelle](https://github.com/adobe/aem-cif-guides-venia/pull/319) et [widget PLP](https://github.com/adobe/aem-cif-guides-venia/pull/320) permettent aux sites d’AEM de profiter de [!DNL Live Search].

### Mises à jour

![Correctif](../assets/fix.svg) La taille de la table des flux de produits et de prix a été considérablement réduite. Les tableaux `catalog_data_exporter_products` et `catalog_data_exporter_product_prices` devraient bénéficier d’une réduction de taille importante.
![Correctif](../assets/fix.svg) L’onglet &quot;Règles&quot; est renommé &quot;Règles de recherche&quot;
![Correctif](../assets/fix.svg) Lors du classement par &quot;tendance&quot;, vous pouvez désormais choisir entre :
- 3 jours (par défaut)
- 14 jours
- 30 jours
![Fix](../assets/fix.svg) ’Events’ (Boost/Pin/Bury/Hide) a été renommé &quot;Classement manuel&quot;
![Correctif](../assets/fix.svg) ’Le type de classement’ a été renommé en ’Classement intelligent’
![Correctif](../assets/fix.svg) Correctifs de bogues mineurs

## [!DNL Live Search] 3.1.0 {#310}

_1 septembre 2023_

[!BADGE Pris en charge]{type="Informatif" tooltip="Pris en charge"}

### Mises à jour

![Correctif](../assets/fix.svg) Le widget Liste des produits a été mis à jour pour utiliser l’ [ API Catalog Service](https://developer.adobe.com/commerce/services/graphql/catalog-service/product-search/).

## [!DNL Live Search] 3.0.2 {#302}

_7 août 2023_

[!BADGE Pris en charge]{type="Informatif" tooltip="Pris en charge"}

### Nouvelles fonctionnalités

![New](../assets/new.svg) Les valeurs suivantes ont été ajoutées à l’objet `storeDetails` :

- &quot;Autoriser tous les produits par page&quot;
- Taux de change
- &quot;Produits par page sur les valeurs autorisées de la grille&quot;
- &quot;Produits par page sur la valeur par défaut de la grille&quot;
- Langue du magasin

### Mises à jour

![Fix](../assets/fix.svg) Les modules du service de catalogue ont été ajoutés au métaphorage pour prendre en charge la récupération avancée des données.
![Correctif](../assets/fix.svg) La navigation de la page **Mon compte** ne disparaît plus lors de l’utilisation du widget Page de liste de produits.

Les commerçants doivent mettre à niveau l’extension [!DNL Live Search] version >= 3.0.2 pour accéder à ces fonctionnalités.

Il est recommandé de mettre à niveau et de tester avant de passer en production. Envisagez de mettre à niveau l’environnement de production pendant les heures creuses après avoir vérifié les résultats de l’environnement de test.

### Limites

L’utilisation du widget Page de liste des produits de la recherche en direct entraîne l’échec du Gestionnaire de balises de Google. Utilisez l’adaptateur de recherche par défaut si Google Tag Manager est nécessaire.

## [!DNL Live Search] 3.0.1 {#301}

_14 mars 2023_

[!BADGE Pris en charge]{type="Informatif" tooltip="Pris en charge"}

### Nouvelles fonctionnalités

![New](../assets/new.svg) Product Item Card dans l’aperçu des règles
![Nouveau](../assets/new.svg) [Widget de page de liste de produits](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/live-search-storefront/plp-styling)
![Nouveau](../assets/new.svg) [Options de filtrage par catégorie](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/#facets)
![New](../assets/new.svg) Ajout de la possibilité de faire glisser et déposer des événements d’épingle
![New](../assets/new.svg) New Pin actions :
- Epingler au point - Bouton Epingler pour créer un événement Epingler en un clic
- Epingler au haut - Place le produit en première position
- Epingler vers le bas : place le produit au bas des résultats.
- Déépingler un événement d’un seul clic
![Nouveau](../assets/new.svg) [Classement intelligent pour les règles](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/live-search-admin/rules/rules-add)
![New](../assets/new.svg) [!DNL Live Search] prend désormais en charge toutes les fonctionnalités [Inventory management](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/introduction) dans Commerce (anciennement appelée inventaire multi-Source ou MSI). Pour activer la prise en charge complète, vous devez [mettre à jour](install.md#update) le module de dépendance `commerce-data-export` vers la version 102.2.0+.

### Mises à jour

![Correctif](../assets/fix.svg) La configuration des règles trie désormais automatiquement les positions de manière unique.
![Correctif](../assets/fix.svg) La suppression d’un événement existant met désormais à jour l’aperçu
![Correctif](../assets/fix.svg) Les règles sans événement peuvent être enregistrées.
![Fix](../assets/fix.svg) Supprimer le sélecteur de facette &quot;Sélectionner un type&quot;
![Correctif](../assets/fix.svg) Ajout d’un nouvel état &quot;En édition&quot; pour les règles non enregistrées

### Correctifs

![Fix](../assets/fix.svg) Correction d’une erreur du serveur en cas d’événement inachevé pendant l’enregistrement
![Correctif](../assets/fix.svg) Correction d’une suppression correcte d’événement spécifique lorsqu’il y a plusieurs événements
![Correctif](../assets/fix.svg) Correction d’un événement de règle existant qui ne se mettait pas à jour lorsqu’un nouvel événement a été ajouté.
![Correctif](../assets/fix.svg) Correction d’un second clic &quot;Modifier&quot; à partir des détails de la page [!DNL Live Search] nécessitant un rechargement.
![Fix](../assets/fix.svg) Synonymes : correction d’un problème en raison duquel un utilisateur cliquait en dehors d’une entrée pour ne pas retourner la cible d’action sur le champ.
![Correctif](../assets/fix.svg) Autres correctifs mineurs et mises à jour des performances


![Bug](../assets/bug.svg) - Le classement par &quot;Recommandé pour vous&quot; n’est pris en charge que dans les widgets de recherche en direct. Elle n’est pas prise en charge avec la fonctionnalité de recherche par défaut de Luma et de PWA.
![Bug](../assets/bug.svg) - Les facettes d’attributs de prix personnalisés ne s’affichent pas correctement dans Luma, mais l’API les filtre correctement.

Les commerçants doivent mettre à niveau l’extension [!DNL Live Search] version >= 3.0.1 pour accéder à ces fonctionnalités.

Il est recommandé de mettre à niveau et de tester avant de passer en production. Envisagez de mettre à niveau l’environnement de production pendant les heures creuses après avoir vérifié les résultats de l’environnement de test.

## [!DNL Live Search] 2.0.5 {#205}

[!BADGE Pris en charge]{type="Informatif" tooltip="Pris en charge"}

![Fix](../assets/fix.svg) - La recherche en direct générait une erreur lorsque les ressources du SDK n’étaient pas disponibles en raison de problèmes réseau. Ce bogue a été corrigé.

Les commerçants doivent mettre à niveau l’extension Live Search >= 2.0.5 pour accéder à ces fonctionnalités.

Il est recommandé de mettre à niveau et de tester avant de passer en production. Envisagez de mettre à niveau l’environnement de production pendant les heures creuses après avoir vérifié les résultats de l’environnement de test.

### [!DNL Live Search] 2.0.4 {#204}

[!BADGE Pris en charge]{type="Informatif" tooltip="Pris en charge"}

![New](../assets/new.svg) La recherche en direct prend désormais en charge le filtrage par le paramètre &quot;Afficher les produits en rupture de stock&quot; dans l’administrateur. Si &quot;Afficher les produits en rupture de stock&quot; est défini sur false, `inStock = true` est ajouté au filtre.
![Correctif](../assets/fix.svg) Pour améliorer les performances, le bloc &quot;Suggestions&quot; a été supprimé de la fenêtre contextuelle Recherche en direct. Les données sont toujours transmises par GraphQL, au cas où vous souhaitez remplacer la fonctionnalité.
![Fix](../assets/fix.svg) `categories` et `categoryPath` ont remplacé `categoryIds` pour le filtrage de catégorie. Pour en savoir plus, consultez la rubrique [productSearch](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/) .
![Correctif](../assets/fix.svg) Auparavant, un utilisateur lié à une entreprise B2B recevait un code de groupe client incorrect lors de recherches. La fonction de recherche en direct renvoie désormais la valeur correcte.
![Correctif](../assets/fix.svg) Auparavant, la recherche d’un terme qui n’existe pas renvoyait une erreur. Ce bogue est maintenant corrigé.

Les commerçants doivent mettre à niveau l’extension [!DNL Live Search] version >= 2.0.4 pour accéder à ces fonctionnalités.

Il est conseillé aux utilisateurs de mettre à niveau et de tester avant de passer en production. Envisagez de mettre à niveau l’environnement de production pendant les heures creuses après avoir vérifié les résultats de l’environnement de test.

### [!DNL Live Search] 2.0.3 {#203}

[!BADGE Pris en charge]{type="Informatif" tooltip="Pris en charge"}

![Nouvelle](../assets/new.svg) La recherche en direct prend désormais en charge les fonctionnalités B2B en respectant les autorisations de catégorie, les catalogues partagés et la tarification spécifique aux groupes de clients.

Les commerçants doivent mettre à niveau l’extension [!DNL Live Search] version >= 2.0.3 pour accéder à ces fonctionnalités.

Il est conseillé aux utilisateurs de mettre à niveau et de tester avant de passer en production. Envisagez de mettre à niveau l’environnement de production pendant les heures creuses après avoir vérifié les résultats de l’environnement de test.

### [!DNL Live Search] 2.0 {#20}

[!BADGE Pris en charge]{type="Informatif" tooltip="Pris en charge"}

Les installations [!DNL Live Search] existantes doivent être mises à niveau vers [!DNL Live Search] 2.0.0 pour tirer parti des nouvelles fonctionnalités, correctifs et améliorations suivants :

![New](../assets/new.svg) [!DNL Live Search] prend désormais en charge PHP 8.1 pour les installations exécutant Adobe Commerce 2.4.4.
![Nouveau](../assets/new.svg) Le module `Magento_ElasticsearchCatalogPermissionsGraphQl` est ajouté à la liste des modules désactivés lors de l’installation.
![Nouveau](../assets/new.svg) Le nombre de lignes disponibles dans [[!DNL storefront popover]](overview.md) peut être configuré à partir de l’ *Admin*.
![Nouveau](../assets/new.svg) Beta [PWA](https://developer.adobe.com/commerce/pwa-studio/) pris en charge pour [!DNL Live Search].
![Nouveau](../assets/new.svg) Le processus d’installation de [!DNL Live Search] est mis à jour avec des modifications de processus avancées.
![Correctif](../assets/fix.svg) [Lien de recherche avancée](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search) supprimé du pied de page du storefront.
![Bug](../assets/bug.svg) Les attributs de produit suivants ne sont pas pris en charge par [l&#39;API Commerce GraphQL](https://developer.adobe.com/commerce/services/graphql/live-search/) lorsqu&#39;ils sont utilisés en relation avec la version bêta de PWA : `description`, `name`, `short_description`
![Bug](../assets/bug.svg) La version bêta de PWA pour [!DNL Live Search] ne prend pas en charge la [gestion des événements](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/).

### [!DNL Live Search] 1.3.1 {#131}

[!BADGE Pris en charge]{type="Informatif" tooltip="Pris en charge"}

![Fix](../assets/fix.svg) [Attribut de prix personnalisé](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/product-attributes/attributes-input-types) ne renvoie plus d’erreur lorsqu’il est configuré comme une [facette](facets-add.md).
![Correction](../assets/fix.svg) Correction d’un problème qui provoquait une erreur lorsqu’aucun [ symbole monétaire](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/site-store/currency/currency-configuration#step-5-customize-currency-symbols-optional) (`data-currency-symbol`) n’était disponible.
![Le correctif ](../assets/fix.svg) [[!DNL Storefront popover]](storefront-popover.md) affiche désormais le [Prix spécial](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/pricing/product-price-special) (prix final minimum) lorsqu&#39;il est disponible.

### [!DNL Live Search] 1.3.0 {#130}

[!BADGE Pris en charge]{type="Informatif" tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) [Le tableau de bord des rapports de performances](performance.md) donne des informations sur les termes de recherche que les acheteurs utilisent.
![Nouveau](../assets/new.svg) [!DNL Live Search] [Le SDK des événements Storefront](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/) permet d’accéder à une couche de données commune avec des services de publication et d’abonnement d’événements, ainsi que des mesures.
![Fix](../assets/fix.svg) [[!DNL Storefront popover]](storefront-popover.md) comporte une nouvelle classe `active` pour le conteneur `.search-autocomplete` qui contrôle la visibilité.
![Correctif](../assets/fix.svg) Dans le storefront, le lien de pied de page [Termes de recherche](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search-terms) est supprimé et son cache désactivé pour les installations [!DNL Live Search].
![Bug](../assets/bug.svg) Correctif pour l’adaptateur de recherche qui gère les produits en double.
![Bug](../assets/bug.svg) [!DNL Live Search] prend en charge les [ emplacements d&#39;inventaire à source unique](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/sources/sources-manage) (physiques) avec plusieurs [stocks](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/stocks/stocks-manage) (virtuels). Plusieurs sources d’inventaire ne sont désormais pas prises en charge.

### [!DNL Live Search] 1.2.0 {#120}

[!BADGE Pris en charge]{type="Informatif" tooltip="Pris en charge"}

![New](../assets/new.svg) [[!DNL Storefront popover]](storefront-popover.md) affiche des produits suggérés et des images miniatures des principaux résultats de recherche sous la forme de requêtes de type shoppers dans la zone de recherche.
La session ![Nouvelle](../assets/new.svg) Commerce *Admin* reste ouverte pendant les longues périodes d’inactivité du clavier.
![New](../assets/new.svg) [!DNL Live Search] est automatiquement activé après l’intégration
![Correctif](../assets/fix.svg) Le temps d’indexation initial est inférieur à une heure
![Correction](../assets/fix.svg) Des mises à jour incrémentielles de produit quasiment en temps réel (après installation et configuration)
![Correctif](../assets/fix.svg) Colonnes pouvant être triées dans l’éditeur Synonyme
![Fix](../assets/fix.svg) [!DNL Live Search] ne renvoie plus d’erreur si les critères de recherche contiennent une valeur d’ordre de tri vide
![Fix](../assets/fix.svg) Le filtrage de plage ne rompt plus si les codes d’attribut contiennent des chaînes &quot;to&quot; ou &quot;from&quot;

### [!DNL Live Search] 1.1.0 {#110}

[!BADGE Pris en charge]{type="Informatif" tooltip="Pris en charge"}

![Bug](../assets/bug.svg) Le service [!DNL Live Search] ne prend en charge que la [devise de base](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/site-store/currency/currency-configuration) de l’installation Adobe Commerce.
![Bogue](../assets/bug.svg) Lors de l’ajout d’une facette, le flux d’attributs de produit ne se met pas à jour correctement lorsqu’il est défini sur `Update on Save`. Pour éviter ce problème, accédez à [Gestion des index](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) et définissez Flux d’attributs de produit sur `Update by Schedule`.
![Bug](../assets/bug.svg) [!DNL Live Search] Les synonymes sont définis par vue de magasin, mais sont actuellement stockés par site web et identifiés par une combinaison de `environmentId` et `storeViewCode`. Par conséquent, tous les sites web et toutes les vues de magasin dans l’installation Adobe Commerce partagent des synonymes. Le dernier ensemble de synonymes créé pour la vue de magasin est prioritaire.
![Bug](../assets/bug.svg) Si un terme de synonyme contient plusieurs mots, chaque mot est traité comme un synonyme distinct. Par exemple, si vous définissez &quot;pièce temporelle&quot; comme un synonyme de &quot;montre&quot;, &quot;heure&quot; et &quot;pièce&quot; sont tous deux traités comme des synonymes de montre.

+++

## Documentation

Pour en savoir plus :

- [Documentation du développeur Adobe Commerce](https://developer.adobe.com/commerce/docs)
- [Guide de l’utilisateur Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce)
- [[!DNL Live Search] sur Marketplace](https://commercemarketplace.adobe.com/magento-live-search.html)
