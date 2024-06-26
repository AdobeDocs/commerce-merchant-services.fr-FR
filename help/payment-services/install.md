---
title: Installer [!DNL Payment Services]
description: Installez l’extension Payments Services.
exl-id: babaa91a-9376-4acb-b934-a89f9df52016
role: Admin
feature: Payments, Checkout, Install, Upgrade
source-git-commit: 5c4fe370507e4154d4495d4c09e2ff8705e53191
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# Installer [!DNL Payment Services]

Pour commencer à utiliser les services de paiement pour [!DNL Adobe Commerce] et [!DNL Magento Open Source], vous devez effectuer quelques étapes d’intégration.

>[!INFO]
>
> Voir notre [Configurer [!DNL Payment Services] pour Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-learn/tutorials/admin/adobe-commerce-services/configure-adobe-payment-services) vidéo pour plus d’informations.

Téléchargement et installation du [!DNL Payment Services] extension pour [!DNL Adobe Commerce] et [!DNL Magento Open Source] est une étape prérequise pour utiliser [!DNL Payment Services].

![[!DNL Payment Services] vue d’administration de l’extension](assets/admin-view.png){width="300" zoomable="yes"}

## Télécharger l’extension

Vous devez d’abord télécharger l’extension depuis [Commerce Marketplace](https://experienceleague.adobe.com/docs/commerce-admin/start/resources/commerce-marketplace.html) avant de l’installer.

1. Accédez au [Extension des services de paiement dans le Commerce Marketplace](https://commercemarketplace.adobe.com/magento-payment-services.html).
1. Pour choisir l’édition et la version, basculez **[!UICONTROL Edition]** et **[!UICONTROL Your store version]** à vos sélections préférées.
1. Cliquez sur **[!UICONTROL Add to Cart]**.
1. Terminer le passage en caisse et cliquer sur **[!UICONTROL Place Order]**.
1. Vérifiez l’e-mail associé à votre téléchargement Marketplace pour la confirmation de commande et les détails.

## Installation de l’extension

Vous pouvez installer le [!DNL Payment Services] extension pour les deux [!DNL Adobe Commerce] sur l’infrastructure cloud et les instances sur site, qui sont liées à votre compte Commerce. [mageid](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-information/#access-keys) fourni dans le processus d’inscription.
[!DNL Magento Open Source] Les clients utilisent les instructions sur site.

Le compositeur utilise ces clés lors de l’installation initiale de [!DNL Adobe Commerce], ou dans les cas où les clés du compositeur n’ont pas été précédemment enregistrées dans la variable `auth.json` fichier .

Voir [Obtention des clés d’authentification](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) pour plus d’informations sur l’obtention des clés du compositeur.

Voir [Installer une extension](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/extensions.html) pour plus d’informations sur ce qu’il faut prendre en compte avant de télécharger et d’installer une extension.

### [!DNL Adobe Commerce] sur l’infrastructure cloud

Cette méthode est utilisée pour installer le [!DNL Payment Services] pour une instance de Commerce Cloud.

1. Mettez à jour votre `composer.json` fichier :

   ```bash
   composer require magento/payment-services --no-update
   ```

1. Mettez à jour les dépendances et installez l’extension :

   ```bash
   composer update magento/payment-services --with-dependencies
   ```

   Utilisez la variable `composer update` pour mettre à jour toutes les dépendances racine.

1. Validez et poussez vos modifications.

### Sur site et autres configurations

Cette méthode est utilisée pour installer le [!DNL Payment Services] extension pour une instance sur site et [!DNL Magento Open Source] clients.

1. Pour obtenir l’extension, exécutez les commandes suivantes :

   ```bash
   composer require magento/payment-services --no-update
   ```

1. Mettez à jour les dépendances et installez l’extension :

   ```bash
   composer update magento/payment-services --with-dependencies
   ```

   Utilisez la variable `composer update` pour mettre à jour toutes les dépendances racine.

1. Mettez à niveau votre instance :

   ```bash
   bin/magento setup:upgrade
   ```

1. Effacez le cache :

   ```bash
   bin/magento cache:clean
   ```

1. Validez les modifications.
1. Pour vous assurer que le code validé est déployé, mettez à jour votre instance .

## Mettre à niveau l’extension

Lorsqu’une nouvelle version de [!DNL Payment Services] est publiée, vous pouvez facilement mettre à niveau votre extension.

1. Pour obtenir la version la plus récente du package :

   ```bash
   composer update magento/payment-services --with-dependencies
   ```

   Utilisez la variable `composer update` pour mettre à jour toutes les dépendances racine.

1. Validez et poussez vos modifications.

## Dépannage

Des erreurs peuvent s’afficher lors de la tentative d’installation du [!DNL Payment Services] extension . Utilisez les méthodes de dépannage suivantes pour résoudre les erreurs.

### Clés de compositeur incorrectes

Si l’erreur suivante indique que vous disposez des clés de compositeur incorrectes :

```terminal
Could not find a matching version of package magento/payment-services. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (stable).
```

Vérifiez que vos clés de compositeur sont valides et que vous avez accès à d’autres packages de Magento.

Pour voir quelles clés de compositeur sont configurées :

1. Recherchez l’emplacement du `auth.json` fichier :

   ```bash
   composer config --global home
   ```

1. Afficher la variable `auth.json` fichier :

   ```bash
   cat /path/to/auth.json
   ```

1. Voir [les clés associées à votre compte Commerce `MageID`](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html).

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
