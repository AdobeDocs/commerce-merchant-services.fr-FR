---
title: Notes de mise à jour
description: Les dernières informations de mise à jour pour [!DNL Product Recommendations] d’Adobe Commerce.
source-git-commit: 7fe89df32dc5363817f957180e5b75e7217fc14a
workflow-type: tm+mt
source-wordcount: '888'
ht-degree: 0%

---

# Notes de mise à jour

Les notes de mise à jour contiennent des mises à jour des [!DNL Product Recommendations] modules :

* En mars 2021, [!DNL Product Recommendations] sont désormais prises en charge dans [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/) storefronts.
* [!DNL Product Recommendations] metapackage : `magento/product-recommendations`
* Prise en charge du créateur de pages dans [!DNL Product Recommendations] module (facultatif) : `magento/module-page-builder-product-recommendations`
* Prise en charge du type de recommandation similarité visuelle pour [!DNL Product Recommendations] module (facultatif) : `magento/module-visual-product-recommendations`

Les notes de mise à jour incluent :

* ![Nouveau](../assets/new.svg) - Nouvelles fonctionnalités
* ![Correction](../assets/fix.svg) - Correctifs et améliorations

Consultez la documentation destinée aux développeurs pour [en savoir plus sur la compatibilité des produits](https://devdocs.magento.com/release/availability.html).

## Adobe Commerce 2.3.x et 2.4.x

## 3.3.7 de magento/product-recommendations

* ![Nouveau](../assets/new.svg) - Ajout de la prise en charge de PHP 8.1
* ![Nouveau](../assets/new.svg) - Amélioration du redimensionnement des images, de sorte que les images de taille différente soient gérées de manière plus cohérente dans le modèle d’affichage de référence

## 3.3.6 de magento/product-recommendations

* ![Nouveau](../assets/new.svg) - Optimisé [!DNL Product Recommendations] métapackage en répertoriant explicitement les dépendances

### 3.3.5 de magento/product-recommendations

* ![Nouveau](../assets/new.svg) - Ajout [Prise en charge B2B](onboarding.md#b2bsupport) dans Recommendations de produit
* ![Nouveau](../assets/new.svg) - Ajout de nouveaux flux à [données du catalogue de synchronisation](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-catalog-sync.html) à Commerce Services via la ligne de commande

### 3.3.3 de Magento/product-recommendations

* ![Nouveau](../assets/new.svg) - Ajout de nouvelles [types de recommandations](type.md): Conversion (affichage au panier), Conversion (affichage à l’achat) et Récemment consultés. Ces nouveaux types de recommandations sont disponibles dans la variable `magento/product-recommendations` module 3.2.2 et versions ultérieures.
* ![Correction](../assets/fix.svg) - Correction d’un problème en raison duquel le pare-feu d’applications web de Fastly bloquait incorrectement un cookie.
* ![Correction](../assets/fix.svg) - Correction d’un problème en raison duquel les produits affectés à la vue de magasin non par défaut n’étaient pas affichés dans la variable _Aperçu du produit Recommendations_ lors de la création d’une recommandation pour cette vue de magasin spécifique
* ![Correction](../assets/fix.svg) - Correction d’un problème en raison duquel certains noms d’unité de recommandation dans le Créateur de pages empêchaient l’affichage de l’unité de recommandation sur le storefront.

### 3.3.2 de magento/product-recommendations

* ![Correction](../assets/fix.svg) - Correction d’une dépendance manquante pour la prise en charge B2B.

### 3.3.1 de magento/product-recommendations

* ![Nouveau](../assets/new.svg) - Ajout de la prise en charge de la tarification de groupe de clients B2B. Lorsque vous définissez une [filtre de prix](filters.md) sur une unité de recommandation, les clients B2B connectés voient les prix de groupe de clients définis pour les produits affichés.

### 3.3.0 de magento/product-recommendations

* ![Nouveau](../assets/new.svg) - Ajout de la prise en charge de la couche de données client Adobe pour normaliser la collecte de données comportementales sur les fonctionnalités et services Adobe Commerce. Voir [readme](https://github.com/adobe/magento-storefront-event-collector/blob/main/README.md) pour en savoir plus.

### 3.2.6 de Magento/product-recommendations

* ![Correction](../assets/fix.svg) - Correction d’une erreur modale JavaScript
* ![Correction](../assets/fix.svg) - Correction d’un problème en raison duquel le pare-feu d’applications web de Fastly bloquait incorrectement un cookie.

### 3.2.5 de magento/product-recommendations

* ![Nouveau](../assets/new.svg) - Services Magento renommés en [Services de commerce](https://docs.magento.com/user-guide/system/saas.html) et amélioration de l’utilisation dans l’administration

### 3.2.4 de magento/product-recommendations

* ![Correction](../assets/fix.svg) - Correction de l’erreur &quot;Impossible de récupérer les données des options de produit configurables&quot; lors de l’indexation des attributs de produit

### 3.2.3 de Magento/product-recommendations

* ![Correction](../assets/fix.svg) - Correction de l’erreur &quot;Impossible de récupérer les données des options de produit configurables&quot; lors de la synchronisation du catalogue
* ![Correction](../assets/fix.svg) - Correction d’un problème en raison duquel le code de magasin n’était pas correctement défini lorsque vous avez activé la configuration &quot;Ajouter le code de magasin à l’URL&quot;.
* ![Correction](../assets/fix.svg) - Amélioration de la détection des modifications de configuration du panneau d’administration pour s’assurer que ces modifications sont répercutées dans les données de synchronisation du catalogue

### 3.2.2 de Magento/product-recommendations

* ![Nouveau](../assets/new.svg) - Ajout de la capacité à [aperçu des résultats de la recommandation](create.md) au moment de la création. Cela peut nécessiter la mise à jour de votre module vers la dernière version.
* ![Nouveau](../assets/new.svg) - Ajout de la capacité à [surveillance et gestion](https://docs.magento.com/user-guide/system/catalog-sync.html) le processus de synchronisation du catalogue à partir de l’administrateur.
* ![Nouveau](../assets/new.svg) - Ajout [filtres](filters.md) pour contrôler les produits affichés dans les recommandations.
* ![Nouveau](../assets/new.svg) - Ajout de la fonction [similarité visuelle](type.md#visualsim) type de recommandation.

### 1.2.1 de Magento/module-page-builder-product-recommendations pour le Créateur de pages

* ![Nouveau](../assets/new.svg) - Ajout de la prise en charge de la version 3.2.0+ de la variable `magento/product-recommendations` module

### 3.1.0 de magento/product-recommendations

* ![Nouveau](../assets/new.svg) - Ajout de la capacité à [resync](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-catalog-sync.html) votre catalogue vers les services SaaS via la ligne de commande.
* ![Nouveau](../assets/new.svg) - Ajout de la prise en charge des préfixes de table de base de données
* ![Correction](../assets/fix.svg) - Suppression de la prise en charge de PHP 7.1

### 3.0.8 de magento/product-recommendations

* ![Correction](../assets/fix.svg) - Correction d’un problème en raison duquel des événements étaient envoyés pour la collecte de données avant la configuration du module, provoquant un trafic non valide.

### 3.0.6 de magento/product-recommendations

* ![Nouveau](../assets/new.svg) - **(Version bêta)** Inclut la prise en charge de nouvelles [similarité visuelle](type.md#visualsim) type de recommandation.

### 1.0.0 de magento/module-visuel-product-recommendations

* ![Nouveau](../assets/new.svg) - **(Version bêta)** [similarité visuelle](type.md#visualsim). Avec le _similarité visuelle_ type de recommandation, vous pouvez déployer une unité de recommandation sur la page des détails du produit qui affiche les produits visuellement similaires au produit consulté.

### 3.0.5 de magento/product-recommendations

* ![Correction](../assets/fix.svg) - Correction de l’erreur &quot;Impossible de récupérer les données des options de produit&quot; qui pouvait se produire lors de l’exportation du catalogue.
* ![Correction](../assets/fix.svg) - Symbole de devise dans la variable _Recettes_ sur la _Recommendations de produit_ Le tableau de bord reflète désormais correctement la devise de base configurée.

### 3.0.4 de magento/product-recommendations

* ![Correction](../assets/fix.svg) - Ajout de la prise en charge d’Adobe Commerce 2.4.0

### 3.0.3 de magento/product-recommendations

* ![Correction](../assets/fix.svg) - Amélioration de l’implémentation des symboles dans le modèle storefront

### 1.0.4 de Magento/module-page-builder-product-recommendations pour le Créateur de pages

* ![Nouveau](../assets/new.svg) - Ajout du nom de la recommandation de produit lors de la modification du type de contenu Page Builder

### 3.0.2 magento/product-recommendations

* ![Nouveau](../assets/new.svg) - Ajout d’une colonne d’état sur la grille lors de la sélection des unités de recommandation dans le créateur de pages
* ![Correction](../assets/fix.svg) - Correction d’un problème lié à des protocoles http/https incorrects dans les URL de produit et d’image.

### 3.0.1 de magento/product-recommendations

Il s’agit d’une version majeure. Vous devez [edit](install-configure.md#update) le fichier racine compositeur.json de votre projet.

* ![Nouveau](../assets/new.svg) - Récupérer [!DNL Product Recommendations] d’autres espaces de données SaaS. Vous pouvez ainsi utiliser des recommandations de produits calculées dans votre environnement de produit sur d’autres environnements hors production. [Changement d’espace de données SaaS](settings.md) décrit plus en détail cette fonctionnalité.

* ![Correction](../assets/fix.svg) - Correction d’un problème en raison duquel le passage en caisse était bloqué pour les acheteurs utilisant l’origine du bloc
* ![Correction](../assets/fix.svg) - Correction d’un problème lors de l’envoi d’événements de panier à ajouter superflus.

### 1.0.3 de Magento/module-page-builder-product-recommendations pour le Créateur de pages

* ![Nouveau](../assets/new.svg) - Prise en charge du créateur de pages. Avec l’intégration du Créateur de pages, vous pouvez placer les unités de recommandation avec précision et granularité dans n’importe quel emplacement arbitraire sur le contenu créé par le Créateur de pages. Vous pouvez également mettre en forme les en-têtes et les unités de recommandation elles-mêmes. Accédez à [Page Builder](https://docs.magento.com/user-guide/cms/page-builder-add-recommendations.html) pour plus d’informations.

### 2.0.0 de magento/product-recommendations

* ![Nouveau](../assets/new.svg) - Disponibilité générale !

## Documentation

Pour en savoir plus sur [!DNL Product Recommendations] et [!DNL Product Recommendations] development :

* [Guide de l’utilisateur](overview.md)
* [Documentation destinée aux développeurs](https://devdocs.magento.com/recommendations/product-recs.html)