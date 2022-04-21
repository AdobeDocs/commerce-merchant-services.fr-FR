---
title: Installation et configuration
description: Découvrez comment installer, mettre à jour et désinstaller [!DNL Product Recommendations].
source-git-commit: 4ad607c8595b25d01b5f5020b787fc1d35d4df25
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# Installation et configuration

Déploiement [!DNL Product Recommendations] à votre storefront et Admin requiert que vous installez le module et que vous configuriez le connecteur Commerce Services. Lorsque des mises à jour sont publiées, vous pouvez facilement mettre à jour votre installation avec la dernière version.

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

### Ajout d’un type de recommandation similarité visuelle {#vissimsupport}

Le _similarité visuelle_ le type de recommandation vous permet de déployer une unité de recommandation sur la page des détails du produit qui affiche les produits qui sont [similaire visuellement](type.md#visualsim) au produit consulté. Ce type de recommandation est particulièrement utile lorsque les images et les aspects visuels des produits sont des éléments importants de l’expérience d’achat. Installez le _similarité visuelle_ type de recommandation en exécutant la commande suivante :

```bash
composer require magento/module-visual-product-recommendations
```

## Configurer [!DNL Product Recommendations] {#configure}

Après avoir installé la variable `magento/product-recommendations` , vous devez configurer la variable [Connecteur Commerce Services](https://docs.magento.com/user-guide/configuration/services/saas.html) en spécifiant la clé API et en sélectionnant un espace de données SaaS.

Pour vous assurer que l’exportation de catalogue s’exécute correctement, vérifiez que la variable [cron](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html) les tâches et la [indexeurs](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html) sont en cours d’exécution et la variable `Product Feed` l’indexeur est défini sur `Update by Schedule`.

Lorsque vous réussissez à établir un lien vers Commerce Services par le biais de la clé d’API et à spécifier l’espace de données SaaS, la synchronisation du catalogue démarre et [vérifie](verify.md) que les données comportementales sont envoyées à votre storefront.

## Mettez à jour votre [!DNL Product Recommendations] installation {#update}

Comme toutes les Adobe Commerce, [!DNL Product Recommendations] utilise le compositeur pour l’installation et les mises à jour. Pour mettre à jour la variable `magento/product-recommendations` , exécutez les opérations suivantes :

```bash
composer update magento/product-recommendations --with-dependencies
```

Pour effectuer une mise à jour vers une version majeure, telle que de la version 2.0 à la version 3.0, vous devez modifier la racine du projet. `composer.json` fichier . (Voir [notes de mise à jour](release-notes.md) pour plus d’informations sur la dernière version.) Par exemple, ouvrons l’objet principal `composer.json` et recherchez `magento/product-recommendations` module :

```json
"require": {
    ...
    "magento/product-recommendations": "^2.0",
    ...
}
```

Reprenons la version majeure de `2.0` to `3.0`:

```json
"require": {
    ...
    "magento/product-recommendations": "^3.0",
    ...
}
```

Enregistrez le `composer.json` et exécutez :

```bash
composer update magento/product-recommendations --with-dependencies
```

## Désinstaller [!DNL Product Recommendations] {#uninstall}

Si nécessaire, vous pouvez [uninstall](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-uninstall-mods.html) le module de recommandations de produits.