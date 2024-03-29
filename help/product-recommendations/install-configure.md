---
title: Installation et configuration
description: Découvrez comment installer, mettre à jour et désinstaller [!DNL Product Recommendations].
exl-id: fa599f72-1064-41da-ac54-2b3a3c16a1fe
role: Admin, Developer
source-git-commit: 96a5791c5716f612f473540f27bd3f99b1bfe7c8
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 0%

---

# Installation et configuration

Déploiement [!DNL Product Recommendations] à votre storefront et l’administrateur requiert que vous installez le module et configurez la variable [Connecteur Commerce Services](../landing/saas.md). Lorsque des mises à jour sont publiées, vous pouvez facilement mettre à jour votre installation avec la dernière version.

- [Installer](#install)
- [Configurer](#configure)
- [Mettre à jour](#update)
- [Désinstaller](#uninstall)

## Installer [!DNL Product Recommendations] {#install}

Parce que la variable [!DNL Product Recommendations] est un métapaquage autonome, les mises à jour sont publiées plus souvent qu’Adobe Commerce. Pour vous assurer que vous êtes à jour avec les derniers correctifs et fonctionnalités, reportez-vous à la section [notes de mise à jour](release-notes.md).

Installez le `magento/product-recommendations` module avec le compositeur :

```bash
composer require magento/product-recommendations
```

### Ajout de la prise en charge du créateur de pages {#pbsupport}

[!DNL Product Recommendations] Page Builder est un module facultatif qui est installé séparément. Pour utiliser [!DNL Product Recommendations] avec Page Builder, installez le module en exécutant la commande suivante :

```bash
composer require magento/module-page-builder-product-recommendations
```

En activant [!DNL Product Recommendations] dans le créateur de pages, vous pouvez ajouter une [unité de recommandation](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html) à tout contenu créé dans le Créateur de pages, tel que les pages, les blocs et les blocs dynamiques.

Voir [Utilisation [!DNL Product Recommendations] avec le contenu du créateur de pages](page-builder.md) pour plus d’informations.

### Ajout d’un type de recommandation similarité visuelle {#vissimsupport}

La variable _similarité visuelle_ le type de recommandation vous permet de déployer une unité de recommandation sur la page des détails du produit qui affiche les produits qui sont [similaire visuellement](type.md#visualsim) au produit consulté. Ce type de recommandation est particulièrement utile lorsque les images et les aspects visuels des produits sont des éléments importants de l’expérience d’achat. Installez le _similarité visuelle_ type de recommandation en exécutant la commande suivante :

```bash
composer require magento/module-visual-product-recommendations
```

## Configurer [!DNL Product Recommendations] {#configure}

Après avoir installé la variable `magento/product-recommendations` , vous devez configurer la variable [Connecteur Commerce Services](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html) en spécifiant les clés d’API et en sélectionnant un espace de données SaaS.

Pour vous assurer que l’exportation de catalogue s’exécute correctement, vérifiez que la variable [cron](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html) les tâches et la [indexeurs](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html) sont en cours d’exécution et le `Product Feed` l’indexeur est défini sur `Update by Schedule`.

Lorsque vous parvenez à établir un lien vers Commerce Services par le biais de clés d’API et à spécifier l’espace de données SaaS, la synchronisation du catalogue commence. Vous pouvez alors [verify](verify.md) que les données comportementales sont envoyées à votre storefront.

## Mettez à jour votre [!DNL Product Recommendations] installation {#update}

Comme toutes les Adobe Commerce, [!DNL Product Recommendations] utilise le compositeur pour l’installation et les mises à jour. Pour mettre à jour la variable `magento/product-recommendations` , exécutez les opérations suivantes :

```bash
composer update magento/product-recommendations --with-dependencies
```

Pour effectuer une mise à jour vers une version majeure, telle que de la version 3.0 à la version 4.0, vous devez modifier la racine. `composer.json` pour votre projet. (Voir [notes de mise à jour](release-notes.md) pour plus d’informations sur la dernière version.) Par exemple, ouvrons l’objet principal `composer.json` et recherchez `magento/product-recommendations` module :

```json
"require": {
    ...
    "magento/product-recommendations": "^3.0",
    ...
}
```

Revenons à la version majeure de `3.0` to `4.0`:

```json
"require": {
    ...
    "magento/product-recommendations": "^4.0",
    ...
}
```

Enregistrez le `composer.json` et exécutez :

```bash
composer update magento/product-recommendations --with-dependencies
```

Ou si vous avez installé le `magento/module-visual-product-recommendations` et `magento/module-page-builder-product-recommendations` modules :

```bash
composer update --with-dependencies magento/product-recommendations magento/module-visual-product-recommendations magento/module-page-builder-product-recommendations
```

>[!NOTE]
>
> Dans les versions 3.x.x de Product Recommendations, vous n’avez besoin que d’une seule clé API. Dans les versions 4.x.x et ultérieures, vous devez fournir des clés API publiques et privées de production, ainsi que des clés API publiques et privées de sandbox. Si vous ne fournissez pas les deux paires de clés d’API, vous ne pouvez pas accéder à la fonction Recommendations du produit dans l’administrateur. Toutefois, la collecte de données se poursuit sur votre storefront et les recommandations existantes continueront à être présentées à vos acheteurs.

## pare-feu

Pour laisser le Recommendations de produit passer par un pare-feu, ajoutez `commerce.adobe.io` à la liste autorisée.

## Désinstaller [!DNL Product Recommendations] {#uninstall}

Si nécessaire, vous pouvez [uninstall](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html) le module de recommandations de produits.
