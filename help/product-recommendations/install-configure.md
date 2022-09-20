---
title: Installation et configuration
description: Découvrez comment installer, mettre à jour et désinstaller [!DNL Product Recommendations].
exl-id: fa599f72-1064-41da-ac54-2b3a3c16a1fe
source-git-commit: 09609fd0b5bd3da9e884115de001bc33832ad792
workflow-type: tm+mt
source-wordcount: '0'
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

En activant [!DNL Product Recommendations] Dans le créateur de pages, vous pouvez ajouter une variable principale existante [unité de recommandation](https://docs.magento.com/user-guide/cms/page-builder-add-recommendations.html) à tout contenu créé dans le Créateur de pages, tel que les pages, les blocs et les blocs dynamiques.

>[!NOTE]
>
>[!DNL Page Builder] les unités de recommandation ne peuvent être créées que pour la vue de magasin par défaut.

### Ajout d’un type de recommandation similarité visuelle {#vissimsupport}

Le _similarité visuelle_ le type de recommandation vous permet de déployer une unité de recommandation sur la page des détails du produit qui affiche les produits qui sont [similaire visuellement](type.md#visualsim) au produit consulté. Ce type de recommandation est particulièrement utile lorsque les images et les aspects visuels des produits sont des éléments importants de l’expérience d’achat. Installez le _similarité visuelle_ type de recommandation en exécutant la commande suivante :

```bash
composer require magento/module-visual-product-recommendations
```

## Configurer [!DNL Product Recommendations] {#configure}

Après avoir installé la variable `magento/product-recommendations` , vous devez configurer la variable [Connecteur Commerce Services](https://docs.magento.com/user-guide/configuration/services/saas.html) en spécifiant les clés d’API et en sélectionnant un espace de données SaaS.

Pour vous assurer que l’exportation de catalogue s’exécute correctement, vérifiez que la variable [cron](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html) les tâches et la [indexeurs](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html) sont en cours d’exécution et la variable `Product Feed` l’indexeur est défini sur `Update by Schedule`.

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

Reprenons la version majeure de `3.0` to `4.0`:

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

>[!NOTE]
>
> Dans les versions 3.x.x de Product Recommendations, vous n’avez besoin que d’une seule clé API. Dans les versions 4.x.x et ultérieures, vous devez fournir des clés API publiques et privées de production, ainsi que des clés API publiques et privées de sandbox. Si vous ne fournissez pas les deux paires de clés d’API, vous ne pourrez pas accéder à la fonction Recommendations du produit dans l’administrateur. Toutefois, la collecte de données se poursuit sur votre storefront et les recommandations existantes continueront à être présentées à vos acheteurs.

## Désinstaller [!DNL Product Recommendations] {#uninstall}

Si nécessaire, vous pouvez [uninstall](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-uninstall-mods.html) le module de recommandations de produits.
