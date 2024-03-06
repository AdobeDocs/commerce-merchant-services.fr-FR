---
title: '''[!DNL Product Recommendations] Notes de mise à jour d’'
description: Les dernières informations de mise à jour pour [!DNL Product Recommendations] d’Adobe Commerce.
exl-id: 1758e688-d26f-45e7-818c-d4726338a6c3
feature: Services, Recommendations, Release Notes
source-git-commit: a90fcd8401b7745a65715f68efccdb3ce7c77ccb
workflow-type: tm+mt
source-wordcount: '1281'
ht-degree: 0%

---

# [!DNL Product Recommendations] Notes de mise à jour

Les notes de mise à jour contiennent des mises à jour des [!DNL Product Recommendations] modules :

* [!DNL Product Recommendations] metapackage : `magento/product-recommendations`
* Prise en charge du créateur de pages dans [!DNL Product Recommendations] module (facultatif) : `magento/module-page-builder-product-recommendations`
* Prise en charge du type de recommandation similarité visuelle pour [!DNL Product Recommendations] module (facultatif) : `magento/module-visual-product-recommendations`

La prise en charge de la version majeure actuelle est fournie. Les notes de mise à jour des versions antérieures sont fournies à titre de référence.
Les notes de mise à jour incluent :

![Nouveau](../assets/new.svg) Nouvelles fonctionnalités
![Correction](../assets/fix.svg) Correctifs et améliorations
![Bogue](../assets/bug.svg) Problèmes connus

Consultez la documentation destinée aux développeurs pour [en savoir plus sur l’assistance produit](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).

## Mises à jour du service hébergé

Ces notes décrivent les mises à jour publiées en dehors d’une version ou les améliorations apportées au service hébergé.

+++Mises à jour du service hébergé

_18 juillet 2023_

![Nouveau](../assets/new.svg) Recommendations de produit dispose désormais d’un GraphQL [`recommendations`](https://developer.adobe.com/commerce/services/graphql/recommendations/recommendations/) requête.

_25 avril 2023_

![Nouveau](../assets/new.svg) Les clients Recommendations de produit peuvent désormais tirer parti des [Indexation des prix SaaS](../price-index/price-indexing.md).

+++

## Version majeure actuelle

### 6.0.0 de magento/product-recommendations

_22 février 2024_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) La variable [!DNL Catalog Sync Dashboard] est désormais défini sur [[!DNL Data Management Dashboard]](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-dashboard.html). Ce tableau de bord restructuré fournit des informations sur les flux de données pour [!DNL Product Recommendations], [!DNL Live Search], et [!DNL Catalog Service].
![Correction](../assets/fix.svg) Correction d’un problème qui provoquait des erreurs d’extraction pour le Recommendations de produit.

### Versions précédentes

+++5.0.0 et versions antérieures

### 5.0.1 de magento/product-recommendations

_15 septembre 2023_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) Ajout de nouveaux modules pour la prise en charge de la fonction [Indexeur de prix Saas](../price-index/price-indexing.md).
![Nouveau](../assets/new.svg) Ajout de nouveaux modules d’exportation de données pour la prise en charge de l’exportation d’autres types de produits, y compris les produits regroupés et les cartes-cadeaux.
![Correction](../assets/fix.svg) La taille de la table des flux Produits et Prix a été considérablement réduite. Tableaux `catalog_data_exporter_products` et `catalog_data_exporter_product_prices` devrait voir une réduction substantielle de la taille.

#### Limites connues

* La variable `websiteCode` est renvoyée de manière incorrecte si elle contient un trait de soulignement (_).

### 5.0.0 de magento/product-recommendations

_20 mars 2023_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) Mise à jour de Product Recommendations pour la prise en charge d’Adobe Commerce 2.4.6.
![Nouveau](../assets/new.svg) Il s’agit d’une version majeure. [Modifier](install-configure.md#update) la racine `composer.json` pour votre projet.
![Nouveau](../assets/new.svg) [!DNL Product Recommendations] prend désormais en charge l’intégralité [Inventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/introduction.html) Fonctionnalités dans Commerce (anciennement appelées inventaire multi-source ou MSI). Pour activer la prise en charge complète, vous devez [update](install-configure.md#update) le module de dépendance ; `commerce-data-export` vers la version 102.2.0+.

### 4.0.1 de magento/product-recommendations

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Correction](../assets/fix.svg) Auparavant, le Recommendations de produit affichait une erreur lorsque la devise d’affichage était remplacée par une devise autre que celle par défaut. Le changement de devise fonctionne désormais correctement.

### 4.0.0 de magento/product-recommendations

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) Ajout [indicateurs de préparation](create.md) pour vous aider à visualiser la progression de la formation de chaque type de recommandation.
![Nouveau](../assets/new.svg) Il s’agit d’une version majeure. [Modifier](install-configure.md#update) la racine `composer.json` pour votre projet. Cette version requiert également que vous fournissiez deux clés d’API lors de l’installation et de la configuration de Product Recommendations : [une clé de production et une clé sandbox ;](../landing/saas.md).

#### Limites connues

* La variable `websiteCode` est renvoyée de manière incorrecte si elle contient un trait de soulignement (_).

### 3.3.7 de magento/product-recommendations

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) Prise en charge de PHP 8.1 ajoutée
![Nouveau](../assets/new.svg) Amélioration du redimensionnement des images, de sorte que le dimensionnement des images soit géré de manière plus cohérente dans le modèle d’affichage de référence.

### 3.3.6 de magento/product-recommendations

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) Optimisé [!DNL Product Recommendations] métapackage en répertoriant explicitement les dépendances

### 3.3.5 de magento/product-recommendations

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) Ajout [Prise en charge B2B](onboarding.md#b2bsupport) dans Recommendations de produit
![Nouveau](../assets/new.svg) Ajout de nouveaux flux à [données du catalogue de synchronisation](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html) à Commerce Services via la ligne de commande

### 3.3.3 de Magento/product-recommendations

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) Ajout de nouvelles [types de recommandations](type.md): conversion (affichage du panier), conversion (affichage de l’achat) et affichage récent. Ces nouveaux types de recommandations sont disponibles dans la variable `magento/product-recommendations` module 3.2.2 et versions ultérieures.
![Correction](../assets/fix.svg) Correction d’un problème en raison duquel le pare-feu d’application web de Fastly bloquait incorrectement un cookie.
![Correction](../assets/fix.svg) Correction d’un problème en raison duquel les produits affectés à la vue de magasin non par défaut n’étaient pas affichés dans la variable _Aperçu du produit Recommendations_ lors de la création d’une recommandation pour cette vue de magasin spécifique
![Correction](../assets/fix.svg) Correction d’un problème en raison duquel certains noms d’unité de recommandation dans le Créateur de pages empêchaient l’affichage de l’unité de recommandation sur le storefront.

### 3.3.2 de magento/product-recommendations

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Correction](../assets/fix.svg) Correction d’une dépendance manquante pour la prise en charge B2B.

### 3.3.1 de magento/product-recommendations

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) Ajout de la prise en charge de la tarification de groupe de clients B2B. Lorsque vous définissez une [filtre de prix](filters.md) sur une unité de recommandation, les clients B2B connectés voient les prix de groupe de clients définis pour les produits affichés.

### 3.3.0 de magento/product-recommendations

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) Ajout de la prise en charge de la couche de données client Adobe pour normaliser la collecte de données comportementales sur les fonctionnalités et services Adobe Commerce. Voir [readme](https://github.com/adobe/magento-storefront-event-collector/blob/main/README.md) pour en savoir plus.

### 3.2.6 de Magento/product-recommendations

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Correction](../assets/fix.svg) Correction d’une erreur modale JavaScript
![Correction](../assets/fix.svg) Correction d’un problème en raison duquel le pare-feu d’application web de Fastly bloquait incorrectement un cookie.

### 3.2.5 de magento/product-recommendations

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) Les services Magento renommés en [Services de commerce](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) et amélioration de l’utilisation dans l’administration

### 3.2.4 de magento/product-recommendations

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Correction](../assets/fix.svg) Correction de l’erreur &quot;Impossible de récupérer les données d’options de produit configurables&quot; lors de l’indexation des attributs de produit.

### 3.2.3 de Magento/product-recommendations

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Correction](../assets/fix.svg) Correction de l’erreur &quot;Impossible de récupérer les données d’options de produit configurables&quot; lors de la synchronisation du catalogue.
![Correction](../assets/fix.svg) Correction d’un problème en raison duquel le code de magasin n’était pas correctement défini lorsque vous avez activé la configuration &quot;Ajouter le code de magasin à l’URL&quot;.
![Correction](../assets/fix.svg) Amélioration de la détection des modifications de configuration du panneau d’administration pour s’assurer que ces modifications sont répercutées dans les données de synchronisation du catalogue

### 3.2.2 de Magento/product-recommendations

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) Ajout de la capacité à [aperçu des résultats de la recommandation](create.md) au moment de la création. Cela peut nécessiter la mise à jour de votre module vers la dernière version.
![Nouveau](../assets/new.svg) Ajout de la capacité à [surveillance et gestion](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html) le processus de synchronisation du catalogue à partir de l’administrateur.
![Nouveau](../assets/new.svg) Ajout [filtres](filters.md) pour contrôler les produits affichés dans les recommandations.
![Nouveau](../assets/new.svg) Ajout de la [similarité visuelle](type.md#visualsim) type de recommandation.

### 1.2.1 de Magento/module-page-builder-product-recommendations pour le Créateur de pages

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) Ajout de la prise en charge de la version 3.2.0+ de la variable `magento/product-recommendations` module

### 3.1.0 de magento/product-recommendations

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) Ajout de la capacité à [resync](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html) votre catalogue vers les services SaaS via la ligne de commande.
![Nouveau](../assets/new.svg) Ajout de la prise en charge des préfixes de table de base de données
![Correction](../assets/fix.svg) Suppression du support PHP 7.1.

### 3.0.8 de magento/product-recommendations

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Correction](../assets/fix.svg) Correction d’un problème en raison duquel des événements étaient envoyés pour la collecte de données avant la configuration du module, provoquant un trafic non valide.

### 3.0.6 de magento/product-recommendations

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) **(Version bêta)** Inclut la prise en charge de nouvelles [similarité visuelle](type.md#visualsim) type de recommandation.

### 1.0.0 de magento/module-visuel-product-recommendations

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) **(Version bêta)** [similarité visuelle](type.md#visualsim). Avec la variable _similarité visuelle_ type de recommandation, vous pouvez déployer une unité de recommandation sur la page des détails du produit qui affiche les produits visuellement similaires au produit consulté.

### 3.0.5 de magento/product-recommendations

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Correction](../assets/fix.svg) Correction de l’erreur &quot;Impossible de récupérer les données des options de produit&quot; qui pouvait se produire lors de l’exportation du catalogue.
![Correction](../assets/fix.svg) Symbole de devise dans la variable _Recettes_ sur la _Recommendations de produit_ Le tableau de bord reflète désormais correctement la devise de base configurée.

### 3.0.4 de magento/product-recommendations

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Correction](../assets/fix.svg) Prise en charge supplémentaire d’Adobe Commerce 2.4.0

### 3.0.3 de magento/product-recommendations

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Correction](../assets/fix.svg) Amélioration de l’implémentation des symboles dans le modèle storefront

### 1.0.4 de Magento/module-page-builder-product-recommendations pour le Créateur de pages

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) Ajout du nom de la recommandation de produit lors de la modification du type de contenu Page Builder

### 3.0.2 magento/product-recommendations

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) Ajout d’une colonne d’état sur la grille lors de la sélection des unités de recommandation dans le créateur de pages
![Correction](../assets/fix.svg) Correction d’un problème lié à des protocoles http/https incorrects dans les URL de produit et d’image.

### 3.0.1 de magento/product-recommendations

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

Il s’agit d’une version majeure. [Modifier](install-configure.md#update) le fichier racine compositeur.json de votre projet.

![Nouveau](../assets/new.svg) Récupérer [!DNL Product Recommendations] d’autres espaces de données SaaS. Cela vous permet d’utiliser des recommandations de produits calculées dans votre environnement de produit sur d’autres environnements hors production. [Changement d’espace de données SaaS](settings.md) décrit plus en détail cette fonctionnalité.

![Correction](../assets/fix.svg) Correction d’un problème en raison duquel le passage en caisse était bloqué pour les acheteurs utilisant l’origine du bloc
![Correction](../assets/fix.svg) Correction d’un problème lors de l’envoi d’événements de panier à ajouter superflus.

### 1.0.3 de Magento/module-page-builder-product-recommendations pour le Créateur de pages

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) Prise en charge du créateur de pages. Avec l’intégration du Créateur de pages, vous pouvez placer les unités de recommandation avec précision et granularité dans n’importe quel emplacement arbitraire sur le contenu créé par le Créateur de pages. Vous pouvez également mettre en forme les en-têtes et les unités de recommandation elles-mêmes. Accédez à [Page Builder](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html) pour plus d’informations.

### 2.0.0 de magento/product-recommendations

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg) Disponibilité générale

+++

## Documentation

Pour en savoir plus sur [!DNL Product Recommendations] et [!DNL Product Recommendations] development :

* [Guide d’utilisation](overview.md)
* [Documentation destinée aux développeurs](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/development-overview.html)
