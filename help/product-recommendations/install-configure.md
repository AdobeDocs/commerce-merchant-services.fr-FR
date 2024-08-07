---
title: Installation et configuration
description: Découvrez comment installer, mettre à jour et désinstaller  [!DNL Product Recommendations].
exl-id: fa599f72-1064-41da-ac54-2b3a3c16a1fe
role: Admin, Developer
source-git-commit: 3a5dec9422aa34eeb204b9fe6f089551e4038f1c
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 0%

---

# Installation et configuration

Le déploiement de [!DNL Product Recommendations] sur votre storefront et de votre administrateur nécessite l’installation du module et la configuration du [Connecteur de services Commerce](../landing/saas.md). Lorsque des mises à jour sont publiées, vous pouvez facilement mettre à jour l’installation avec la dernière version.

- [Installer](#install)
- [Configurer](#configure)
- [Mettre à jour](#update)
- [Désinstaller](#uninstall)

## Installer [!DNL Product Recommendations] {#install}

Comme le module [!DNL Product Recommendations] est un métapaquage autonome, les mises à jour sont publiées plus fréquemment qu’Adobe Commerce. Pour vous assurer que vous êtes à jour avec les derniers correctifs de bogues et fonctionnalités, reportez-vous aux [notes de mise à jour](release-notes.md).

Installez le module `magento/product-recommendations` avec le compositeur :

```bash
composer require magento/product-recommendations
```

### Ajout de la prise en charge du créateur de pages {#pbsupport}

[!DNL Product Recommendations] pour Page Builder est un module facultatif qui est installé séparément. Pour utiliser [!DNL Product Recommendations] avec Page Builder, installez le module en exécutant la commande suivante :

```bash
composer require magento/module-page-builder-product-recommendations
```

En activant [!DNL Product Recommendations] dans le créateur de pages, vous pouvez ajouter une [unité de recommandation](https://experienceleague.adobe.com/en/docs/commerce-admin/page-builder/add-content/recommendations) existante et active à tout contenu créé dans le créateur de pages, tel que les pages, les blocs et les blocs dynamiques.

Pour plus d’informations, voir [Utilisation [!DNL Product Recommendations] avec le contenu du générateur de page](page-builder.md) .

### Ajout d’un type de recommandation similarité visuelle {#vissimsupport}

Le type de recommandation _Similarité visuelle_ vous permet de déployer une unité de recommandations sur la page des détails du produit qui affiche des produits [ visuellement similaires](type.md#visualsim) au produit consulté. Ce type de recommandation est particulièrement utile lorsque les images et les aspects visuels des produits sont des éléments importants de l’expérience d’achat. Installez le type de recommandation _Visual similarity_ en exécutant la commande suivante :

```bash
composer require magento/module-visual-product-recommendations
```

## Configurer [!DNL Product Recommendations] {#configure}

1. Après avoir installé le module `magento/product-recommendations`, configurez le [Connecteur de services Commerce](../landing/saas.md) en spécifiant les clés d’API et en sélectionnant un espace de données SaaS.

   La configuration de cette connexion permet la synchronisation et la communication des données entre l’instance Commerce, le service de catalogue et d’autres services annexes. La synchronisation des données est gérée par l’[ extension d’exportation des données SaaS](../data-export/overview.md).

1. Pour vous assurer que l’exportation du catalogue peut s’exécuter correctement, vérifiez que les tâches [cron](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs) et les [indexers](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/manage-indexers) sont en cours d’exécution et que l’indexeur `Product Feed` est défini sur `Update by Schedule`.

Une fois que vous avez correctement lié l’application Commerce aux services Commerce et que vous avez spécifié l’[espace de données SaaS](../landing/saas.md#saas-configuration), la synchronisation du catalogue commence. Vous pouvez ensuite [vérifier](verify.md) que les données comportementales sont envoyées à votre vitrine.

## Surveillance et dépannage de la synchronisation des données

Depuis l’administrateur Commerce, vous pouvez surveiller le processus de synchronisation à l’aide du [tableau de bord de Data Management](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard). Utilisez l’ [interface de ligne de commande de Commerce](../data-export/data-export-cli-commands.md#troubleshooting) et les journaux pour gérer et résoudre les problèmes liés au processus.

Vous pouvez ensuite [vérifier](verify.md) que les données comportementales sont envoyées à votre vitrine.

## Mettre à jour votre installation [!DNL Product Recommendations] {#update}

Comme toute Adobe Commerce, [!DNL Product Recommendations] utilise le compositeur pour l’installation et les mises à jour. Pour mettre à jour le module `magento/product-recommendations`, exécutez les opérations suivantes :

```bash
composer update magento/product-recommendations --with-dependencies
```

Pour effectuer une mise à jour vers une version majeure, telle que de la version 3.0 à la version 4.0, vous devez modifier le fichier racine `composer.json` de votre projet. (Voir les [notes de mise à jour](release-notes.md) pour plus d’informations sur la dernière version.) Par exemple, ouvrons le fichier `composer.json` principal et recherchons le module `magento/product-recommendations` :

```json
"require": {
    ...
    "magento/product-recommendations": "^3.0",
    ...
}
```

Allons passer la version majeure de `3.0` à `4.0` :

```json
"require": {
    ...
    "magento/product-recommendations": "^4.0",
    ...
}
```

Enregistrez le fichier `composer.json` et exécutez :

```bash
composer update magento/product-recommendations --with-dependencies
```

Ou si vous avez installé les modules `magento/module-visual-product-recommendations` et `magento/module-page-builder-product-recommendations` :

```bash
composer update --with-dependencies magento/product-recommendations magento/module-visual-product-recommendations magento/module-page-builder-product-recommendations
```

>[!NOTE]
>
> Dans les versions 3.x.x de Product Recommendations, vous n’avez besoin que d’une seule clé API. Dans les versions 4.x.x et ultérieures, vous devez fournir des clés API publiques et privées pour les environnements de test et de production. Si vous ne fournissez pas les deux paires de clés d’API, vous ne pouvez pas accéder à la fonction Recommendations du produit dans l’administrateur. Cependant, la collecte des données se poursuit sur votre vitrine et les recommandations existantes continuent à être présentées à vos acheteurs.

## pare-feu

Pour laisser le Recommendations de produit passer par un pare-feu, ajoutez `commerce.adobe.io` à la liste autorisée.

## Désinstaller [!DNL Product Recommendations] {#uninstall}

Si nécessaire, vous pouvez [désinstaller](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/uninstall-modules) le module de recommandations de produits.
