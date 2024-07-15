---
title: '[!DNL Product Recommendations] Notes de mise à jour'
description: Informations les plus récentes sur la version  [!DNL Product Recommendations] d’Adobe Commerce.
exl-id: 1758e688-d26f-45e7-818c-d4726338a6c3
feature: Services, Recommendations, Release Notes
source-git-commit: 6f31361e95b17ee3fa19ff3c2f4a7e2d6d9bc091
workflow-type: tm+mt
source-wordcount: '1376'
ht-degree: 0%

---

# Notes de mise à jour [!DNL Product Recommendations]

Les notes de mise à jour contiennent des mises à jour des modules [!DNL Product Recommendations] suivants :

* [!DNL Product Recommendations] métapackage : `magento/product-recommendations`
* Prise en charge de Page Builder dans le module [!DNL Product Recommendations] (facultatif) : `magento/module-page-builder-product-recommendations`
* Prise en charge du type de recommandation de similarité visuelle pour le module [!DNL Product Recommendations] (facultatif) : `magento/module-visual-product-recommendations`

La prise en charge de la version majeure actuelle est fournie. Les notes de mise à jour des versions antérieures sont fournies à titre de référence.
Les notes de mise à jour incluent :

![New](../assets/new.svg) Nouvelles fonctionnalités
![ Correctifs et améliorations ](../assets/fix.svg)
![Bug](../assets/bug.svg) Problèmes connus

Consultez la documentation destinée aux développeurs pour [en savoir plus sur la prise en charge des produits](https://experienceleague.adobe.com/en/docs/commerce-operations/release/product-availability).

## Mises à jour du service hébergé

Ces notes décrivent les mises à jour ou les problèmes connus qui ont été publiés ou découverts en dehors d’une version ou des améliorations apportées au service hébergé.

_28 juin 2024_

![Bogue](../assets/bug.svg) Les produits ajoutés au panier à partir d’une unité [!DNL Product Recommendations] sur la page du panier ne sont pas supprimés de la liste des produits recommandés lors du rechargement de la page du panier.
![Bug](../assets/bug.svg) Les produits supprimés du panier persistent dans le tableau `cartSkus` jusqu’au rechargement de la page du panier.

_18 juillet 2023_

![New](../assets/new.svg) [!DNL Product Recommendations] possède désormais une requête GraphQL [`recommendations`](https://developer.adobe.com/commerce/services/graphql/recommendations/recommendations/).

_25 avril 2023_

Les clients ![ nouveaux ](../assets/new.svg) [!DNL Product Recommendations] peuvent désormais profiter de l’ [indexation de prix SaaS](../price-index/price-indexing.md).

## Version majeure actuelle

### 6.0.2 de magento/product-recommendations

_9 mai 2024_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Correctif](../assets/fix.svg) Correction d’un problème en raison duquel le fait de cliquer sur le bouton **[!DNL Add to Cart]** d’un produit simple dans une unité Recommendations de produit redirigeait l’acheteur vers la page d’accueil plutôt que de rester sur la page active.
![Bug](../assets/bug.svg) Une erreur de validation est provoquée par l’élément `referenceBlock` dans le fichier XML `ProductRecommendations Layout`.

### Versions précédentes

### 6.0.1 de magento/product-recommendations

_19 mars 2024_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) Ajout de la prise en charge de PHP 8.3.

### 6.0.0 de magento/product-recommendations

_22 février 2024_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![New](../assets/new.svg) [!DNL Catalog Sync Dashboard] est désormais [[!DNL Data Management Dashboard]](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard). Ce tableau de bord repensé fournit des informations sur les flux de données pour [!DNL Product Recommendations], [!DNL Live Search] et [!DNL Catalog Service].
![Correctif](../assets/fix.svg) Correction d’un problème qui provoquait des erreurs de passage en caisse pour [!DNL Product Recommendations].

+++5.0.0 et versions antérieures

### 5.0.1 de magento/product-recommendations

_15 septembre 2023_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) Ajout de nouveaux modules pour la prise en charge de l’ [indexeur de prix Saas](../price-index/price-indexing.md).
![Nouveau](../assets/new.svg) Ajout de nouveaux modules d’exportation de données pour prendre en charge l’exportation d’autres types de produits, y compris les produits regroupés et les cartes-cadeaux.
![Correctif](../assets/fix.svg) La taille de la table des flux de produits et de prix a été considérablement réduite. Les tableaux `catalog_data_exporter_products` et `catalog_data_exporter_product_prices` devraient bénéficier d’une réduction de taille importante.

#### Limites connues

* La valeur `websiteCode` est incorrectement renvoyée si elle contient un trait de soulignement (_).

### 5.0.0 de magento/product-recommendations

_20 mars 2023_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) Mise à jour de [!DNL Product Recommendations] pour la prise en charge d’Adobe Commerce 2.4.6.
![Nouveau](../assets/new.svg) Il s’agit d’une version majeure. [Modifiez](install-configure.md#update) le fichier `composer.json` racine de votre projet.
![Nouveau](../assets/new.svg) [!DNL Product Recommendations] prend désormais en charge toutes les fonctionnalités [Inventory management](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/introduction) dans Commerce (anciennement appelée Inventaire multi-Source ou MSI). Pour activer la prise en charge complète, vous devez [mettre à jour](install-configure.md#update) le module de dépendance `commerce-data-export` vers la version 102.2.0+.

### 4.0.1 de magento/product-recommendations

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Fix](../assets/fix.svg) Auparavant, [!DNL Product Recommendations] affichait une erreur lorsque la devise d’affichage était remplacée par une devise autre que celle par défaut. Le changement de devise fonctionne désormais correctement.

### 4.0.0 de magento/product-recommendations

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) Ajout de [indicateurs de préparation](create.md) pour vous aider à visualiser la progression de la formation de chaque type de recommandation.
![Nouveau](../assets/new.svg) Il s’agit d’une version majeure. [Modifiez](install-configure.md#update) le fichier `composer.json` racine de votre projet. Cette version nécessite également de fournir deux clés d’API lors de l’installation et de la configuration de [!DNL Product Recommendations] : [une clé de production et une clé d’environnement de test](../landing/saas.md).

#### Limites connues

* La valeur `websiteCode` est incorrectement renvoyée si elle contient un trait de soulignement (_).

### 3.3.7 de magento/product-recommendations

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) Prise en charge de PHP 8.1 ajoutée
![Nouveau](../assets/new.svg) : redimensionnement d’image amélioré de sorte que le dimensionnement des images soit géré de manière plus cohérente dans le modèle d’affichage de référence.

### 3.3.6 de magento/product-recommendations

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![New](../assets/new.svg) Optimized [!DNL Product Recommendations] en répertoriant explicitement les dépendances

### 3.3.5 de magento/product-recommendations

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) Ajout de la [prise en charge B2B](onboarding.md#b2bsupport) dans [!DNL Product Recommendations]
![Nouveau](../assets/new.svg) Ajout de nouveaux flux aux [données de catalogue synchronisées](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/user-guides/data-services/catalog-sync) aux services Commerce via la ligne de commande

### 3.3.3 de Magento/product-recommendations

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![New](../assets/new.svg) Ajout de [types de recommandations](type.md) : Conversion (vue sur le panier), Conversion (vue sur l’achat) et Récemment consultée. Ces nouveaux types de recommandations sont disponibles dans le module `magento/product-recommendations` 3.2.2 et versions ultérieures.
![Correctif](../assets/fix.svg) Correction d’un problème en raison duquel le pare-feu d’applications web Fastly bloquait incorrectement un cookie.
![Correction](../assets/fix.svg) Correction d’un problème en raison duquel les produits attribués à la vue de magasin autre que la vue par défaut n’étaient pas affichés dans le panneau _Aperçu du produit Recommendations_ lors de la création d’une recommandation pour cette vue de magasin spécifique.
![Correctif](../assets/fix.svg) Correction d’un problème en raison duquel certains noms d’unité de recommandation dans le générateur de pages empêchaient l’unité de recommandation de s’afficher sur le storefront.

### 3.3.2 de magento/product-recommendations

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Correctif](../assets/fix.svg) Correction d’une dépendance manquante pour la prise en charge B2B

### 3.3.1 de magento/product-recommendations

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) Ajout de la prise en charge de la tarification de groupe de clients B2B. Lorsque vous définissez un [filtre de prix](filters.md) sur une unité de recommandation, les clients B2B connectés voient le groupe de prix défini pour les produits affichés.

### 3.3.0 de magento/product-recommendations

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) Ajout de la prise en charge de la couche de données client Adobe pour normaliser la collecte de données comportementales dans les fonctionnalités et services Adobe Commerce. Pour en savoir plus, consultez le [readme](https://github.com/adobe/commerce-events/blob/main/packages/storefront-events-collector/README.md) .

### 3.2.6 de Magento/product-recommendations

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Correctif](../assets/fix.svg) Correction d’une erreur modale JavaScript
![Correctif](../assets/fix.svg) Correction d’un problème en raison duquel le pare-feu d’applications web Fastly bloquait incorrectement un cookie.

### 3.2.5 de magento/product-recommendations

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) Services de Magento renommés [Services Commerce](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/user-guides/integration-services/saas) et amélioration de l’utilisation dans l’administration

### 3.2.4 de magento/product-recommendations

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Correctif](../assets/fix.svg) Correction de l’erreur &quot;Impossible de récupérer les données d’options de produit configurables&quot; lors de l’indexation des attributs de produit

### 3.2.3 de Magento/product-recommendations

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Correctif](../assets/fix.svg) Correction de l’erreur &quot;Impossible de récupérer les données d’options de produit configurables&quot; lors de la synchronisation du catalogue
![Correctif](../assets/fix.svg) Correction d’un problème en raison duquel le code de magasin n’était pas correctement défini lorsque vous avez activé la configuration &quot;Ajouter le code de magasin à l’URL&quot;.
![Correctif](../assets/fix.svg) Amélioration de la détection des modifications de configuration du panneau d’administration pour s’assurer que ces modifications sont répercutées dans les données de synchronisation du catalogue.

### 3.2.2 de Magento/product-recommendations

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) Ajout de la possibilité de [prévisualiser les résultats de la recommandation](create.md) au moment de la création. Cela peut nécessiter la mise à jour de votre module vers la dernière version.
![Nouveau](../assets/new.svg) Possibilité de [surveiller et gérer](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/user-guides/data-services/catalog-sync) le processus de synchronisation du catalogue à partir de l’administrateur.
![Nouveau](../assets/new.svg) Des [filtres](filters.md) ont été ajoutés pour contrôler les produits affichés dans les recommandations.
![New](../assets/new.svg) Ajout du type de recommandation [Visual similarity](type.md#visualsim).

### 1.2.1 de Magento/module-page-builder-product-recommendations pour le Créateur de pages

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) Prise en charge supplémentaire de la version 3.2.0+ du module `magento/product-recommendations`

### 3.1.0 de magento/product-recommendations

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) Possibilité de [resynchroniser](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/user-guides/data-services/catalog-sync) votre catalogue vers les services SaaS via la ligne de commande.
![Nouveau](../assets/new.svg) Ajout de la prise en charge des préfixes de table de base de données
![Fix](../assets/fix.svg) Suppression de la prise en charge de PHP 7.1

### 3.0.8 de magento/product-recommendations

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Correctif](../assets/fix.svg) Correction d’un problème en raison duquel des événements étaient envoyés pour la collecte de données avant la configuration du module, provoquant un trafic non valide.

### 3.0.6 de magento/product-recommendations

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![New](../assets/new.svg) **(Beta)** Inclut la prise en charge du nouveau type de recommandation [Visual similarity](type.md#visualsim).

### 1.0.0 de magento/module-visuel-product-recommendations

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) **(Beta)** [Similarité visuelle](type.md#visualsim). Avec le type de recommandation _Similarité visuelle_, vous pouvez déployer une unité de recommandations sur la page des détails du produit qui affiche les produits visuellement similaires au produit consulté.

### 3.0.5 de magento/product-recommendations

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Correctif](../assets/fix.svg) Correction de l’erreur &quot;Impossible de récupérer les données des options de produit&quot; qui pouvait se produire lors de l’exportation du catalogue.
![Correctif](../assets/fix.svg) Le symbole de devise dans la colonne _Recettes_ du tableau de bord _[!DNL Product Recommendations]_reflète désormais correctement la devise de base configurée.

### 3.0.4 de magento/product-recommendations

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Correctif](../assets/fix.svg) Ajout de la prise en charge d’Adobe Commerce 2.4.0

### 3.0.3 de magento/product-recommendations

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Correctif](../assets/fix.svg) Amélioration de l’implémentation des symboles dans le modèle storefront

### 1.0.4 de Magento/module-page-builder-product-recommendations pour le Créateur de pages

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) Ajout du nom de la recommandation de produit lors de la modification du type de contenu Page Builder

### 3.0.2 magento/product-recommendations

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) Ajout d’une colonne d’état sur la grille lors de la sélection des unités de recommandation dans le générateur de pages
![ Correction d’un problème lié à des protocoles http/https incorrects dans les URL de produit et d’image.](../assets/fix.svg)

### 3.0.1 de magento/product-recommendations

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

Il s’agit d’une version majeure. [Modifiez](install-configure.md#update) le fichier racine du compositeur.json de votre projet.

![Nouveau](../assets/new.svg) Récupérez [!DNL Product Recommendations] à partir d’autres espaces de données SaaS. Cela vous permet d’utiliser [!DNL Product Recommendations] calculé dans votre environnement de produit sur d’autres environnements hors production. [Le changement d’espace de données SaaS](settings.md) décrit plus en détail cette fonctionnalité.

![Correctif](../assets/fix.svg) Correction d’un problème en raison duquel le passage en caisse était bloqué pour les acheteurs utilisant l’origine du bloc
![Correctif](../assets/fix.svg) Correction d’un problème qui envoyait des événements de panier à ajouter superflus.

### 1.0.3 de Magento/module-page-builder-product-recommendations pour le Créateur de pages

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) prise en charge du Créateur de pages. Avec l’intégration du Créateur de pages, vous pouvez placer les unités de recommandation avec précision et granularité dans n’importe quel emplacement arbitraire sur le contenu créé par le Créateur de pages. Vous pouvez également mettre en forme les en-têtes et les unités de recommandation elles-mêmes. Accédez à [Page Builder](https://experienceleague.adobe.com/en/docs/commerce-admin/page-builder/add-content/recommendations) pour plus d’informations.

### 2.0.0 de magento/product-recommendations

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouvelle version](../assets/new.svg) Disponibilité générale !

+++

## Documentation

Pour en savoir plus sur le développement [!DNL Product Recommendations] et [!DNL Product Recommendations] :

* [Guide d’utilisation](overview.md)
* [Documentation pour les développeurs](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/developer/development-overview)
