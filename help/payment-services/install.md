---
title: Installer [!DNL Payment Services]
description: Installez l’extension Payments Services.
exl-id: babaa91a-9376-4acb-b934-a89f9df52016
source-git-commit: bcb817775fe9cd9ac7096931dd40d5ec0c4a5cfc
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 0%

---

# Installer [!DNL Payment Services]

Installation de la variable [!DNL Payment Services] l’extension pour Adobe Commerce et Magento Open Source est une étape prérequise pour l’utilisation de [!DNL Payment Services].

![[!DNL Payment Services] vue d’administration de l’extension](assets/admin-view.png)

Le [!DNL Payment Services] L’extension pour Adobe Commerce et Magento Open Source peut être installée avec les clés du compositeur, liées à l’identifiant du Magento ([mageid](https://devdocs.magento.com/marketplace/sellers/profile-personal.html#field-descriptions) fourni dans le processus d’inscription. Le compositeur utilise ces clés lors de l’installation initiale d’Adobe Commerce, ou dans les cas où les clés du compositeur n’étaient pas précédemment enregistrées dans la variable `auth.json` fichier .

Voir [Obtention des clés d’authentification](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) pour plus d’informations sur l’obtention des clés du compositeur.

Il existe deux manières d’installer cette extension : pour [Adobe Commerce sur l’infrastructure cloud](https://devdocs.magento.com/payment-services/install-payments.html#magento-commerce-cloud) ou [Sur site](https://devdocs.magento.com/payment-services/install-payments.html#on-premises) installations. Pour utiliser ces méthodes, vous devez utiliser l’interface de ligne de commande.

## Mise à jour du paramètre de stabilité minimale

Avant d’installer l’extension, vous devez modifier la variable `minimum-stability` obligatoire `RC` (candidat à la publication) dans votre `composer.json` fichier . Vous pouvez utiliser un IDE ou votre éditeur de texte préféré (comme Visual Studio Code ou Sublime Text).

Dans votre `composer.json` fichier, modifier `"minimum-stability": "stable"` to `"minimum-stability": "RC"`.

## Installation de l’extension

Vous pouvez installer le [!DNL Payment Services] extension pour Adobe Commerce sur l’infrastructure cloud et les instances sur site.

### Adobe Commerce sur l’infrastructure cloud

Cette méthode est utilisée pour installer le [!DNL Payment Services] pour une instance de Commerce Cloud.

1. Mettez à jour votre `composer.json` fichier :

   ```bash
   composer require magento/payment-services --no-update
   ```

1. Mettez à jour les dépendances et installez l’extension :

   ```bash
   composer update
   ```

   Le `composer update` met à jour toutes les dépendances. Si vous ne souhaitez pas mettre à jour toutes les dépendances en même temps, utilisez plutôt la commande suivante : `composer require magento/payment-services`.

1. Validez et envoyez vos modifications.

### Sur site

Cette méthode est utilisée pour installer le [!DNL Payment Services] pour une instance On-Premise.

1. Pour obtenir l’extension, exécutez les commandes suivantes :

   ```bash
   composer require magento/payment-services --no-update
   ```

1. Mettez à jour les dépendances et installez l’extension :

   ```bash
   composer update
   ```

   Le `composer update` met à jour toutes les dépendances. Si vous ne souhaitez pas mettre à jour toutes les dépendances en même temps, utilisez plutôt la commande suivante : `composer require magento/payment-services`.

1. Mettre à niveau Adobe Commerce :

   ```bash
   bin/magento setup:upgrade
   ```

1. Effacez le cache :

   ```bash
   bin/magento cache:clean
   ```

1. Validez les modifications.
1. Pour vous assurer que le code validé est déployé, mettez à jour votre instance sur site .

## Mettre à niveau l’extension

Lorsqu’une nouvelle version de [!DNL Payment Services] est publiée, vous pouvez facilement mettre à niveau votre extension.

1. Pour obtenir la version la plus récente du package :

   ```bash
   composer update
   ```

   Le `composer update` met à jour toutes les dépendances. Si vous ne souhaitez pas mettre à jour toutes les dépendances en même temps, utilisez plutôt la commande suivante : `composer update magento/payment-services`.

1. Validez et envoyez vos modifications.

## Dépannage

Des erreurs peuvent s’afficher lors de la tentative d’installation du [!DNL Payment Services] extension . Utilisez les méthodes de dépannage suivantes pour résoudre les erreurs.

### Clés de compositeur incorrectes

Si l’erreur suivante indique que vous disposez des clés de compositeur incorrectes :

```terminal
Could not find a matching version of package magento/payment-services. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (stable).
```

Vérifiez que vos clés de compositeur sont liées à l’ID de Magento utilisé pendant la [!DNL Payment Services] enregistrement.

Pour voir quelles clés de compositeur sont configurées :

1. Recherchez l’emplacement du `auth.json` fichier :

   ```bash
   composer config --global home
   ```

1. Afficher la variable `auth.json` fichier :

   ```bash
   cat /path/to/auth.json
   ```

1. Voir [les clés associées à votre ID de Magento](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html).

### Mémoire insuffisante pour PHP

Si l’erreur suivante indique que vous n’avez pas assez de mémoire pour PHP :

```terminal
Fatal error: Allowed memory size of 2146435072 bytes exhausted (tried to allocate 4096 bytes) in phar:///usr/local/bin/composer/src/Composer/DependencyResolver/RuleWatchGraph.php on line 52
```

[Augmentation de la limite de mémoire](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html#increase-php-memory-limit) pour PHP sur votre environnement dans `php.ini`.

Vous pouvez également spécifier la limite de mémoire à l’aide de cette commande : `php -d memory_limit=-1 [path to composer]/composer require magento/payment-services`.

Par exemple :

```bash
php -d memory_limit=-1 vendor/bin/composer require magento/payment-services
```
