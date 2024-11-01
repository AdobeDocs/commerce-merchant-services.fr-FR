---
title: Installer [!DNL Payment Services]
description: Installez l’extension Payments Services.
exl-id: babaa91a-9376-4acb-b934-a89f9df52016
role: Admin
feature: Payments, Checkout, Install, Upgrade
source-git-commit: 37380063242b6d904910be731b8e58471625e9cb
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 0%

---

# Installer [!DNL Payment Services]

Pour commencer à utiliser les services de paiement pour [!DNL Adobe Commerce] et [!DNL Magento Open Source], vous devez suivre quelques étapes d’intégration.

>[!INFO]
>
> Pour plus d’informations, consultez notre vidéo [Configurer [!DNL Payment Services] pour Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-learn/tutorials/admin/adobe-commerce-services/configure-adobe-payment-services) .

Le téléchargement et l&#39;installation de l&#39;extension [!DNL Payment Services] pour [!DNL Adobe Commerce] et [!DNL Magento Open Source] est une étape prérequise pour l&#39;utilisation de [!DNL Payment Services].

## Télécharger l’extension

Vous devez d’abord télécharger l’extension depuis [Commerce Marketplace](https://experienceleague.adobe.com/docs/commerce-admin/start/resources/commerce-marketplace.html) avant de l’installer.

1. Accédez à l’extension [Paiement Services dans le Commerce Marketplace](https://commercemarketplace.adobe.com/magento-payment-services.html).
1. Pour choisir l’édition et la version, basculez **[!UICONTROL Edition]** et **[!UICONTROL Your store version]** sur vos sélections préférées.
1. Cliquez sur **[!UICONTROL Add to Cart]**.
1. Effectuez le passage en caisse et cliquez sur **[!UICONTROL Place Order]**.
1. Vérifiez l’e-mail associé à votre téléchargement Marketplace pour la confirmation de commande et les détails.

>[!NOTE]
>
> Pour Adobe Commerce versions 2.4.7 ou ultérieures, [!DNL Payment Services] est disponible en standard.

## Installation de l’extension

Vous pouvez installer l’extension [!DNL Payment Services] pour [!DNL Adobe Commerce] sur l’infrastructure cloud et les instances sur site, qui sont liées à votre compte Commerce [mageid](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-information/#access-keys) fourni dans le processus d’inscription.
Les clients [!DNL Magento Open Source] utilisent les instructions sur site.

Le compositeur utilise ces clés lors de l’installation initiale de [!DNL Adobe Commerce] ou dans les cas où les clés du compositeur n’étaient pas précédemment enregistrées dans le fichier `auth.json`.

Voir [Obtention de vos clés d’authentification](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/authentication-keys) pour plus d’informations sur l’obtention des clés du compositeur.

Voir [Installation d’une extension](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/extensions) pour plus d’informations sur ce qu’il faut prendre en compte avant de télécharger et d’installer une extension.

### [!DNL Adobe Commerce] sur l’infrastructure cloud

Cette méthode est utilisée pour installer l’extension [!DNL Payment Services] pour une instance de Commerce Cloud.

1. Mettez à jour votre fichier `composer.json` :

   ```bash
   composer require magento/payment-services --no-update
   ```

1. Mettez à jour les dépendances et installez l’extension :

   ```bash
   composer update magento/payment-services --with-dependencies
   ```

   Utilisez la commande `composer update` pour mettre à jour toutes les dépendances racine.

1. Validez et poussez vos modifications.

### Sur site et autres configurations

Cette méthode est utilisée pour installer l’extension [!DNL Payment Services] pour une instance sur site et les clients [!DNL Magento Open Source].

1. Pour obtenir l’extension, exécutez les commandes suivantes :

   ```bash
   composer require magento/payment-services --no-update
   ```

1. Mettez à jour les dépendances et installez l’extension :

   ```bash
   composer update magento/payment-services --with-dependencies
   ```

   Utilisez la commande `composer update` pour mettre à jour toutes les dépendances racine.

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

>[!NOTE]
>
> [!DNL Payment Services] 1.6.1 est compatible avec les versions 7.x de PHP. Cependant, il est vivement recommandé d’effectuer la mise à jour vers la dernière version de [!DNL Payment Services].

## Mettre à niveau l’extension

Lorsqu’une nouvelle version de [!DNL Payment Services] est publiée, vous pouvez facilement mettre à niveau votre extension.

1. Pour obtenir la version la plus récente du package :

   ```bash
   composer update magento/payment-services --with-dependencies
   ```

   Utilisez la commande `composer update` pour mettre à jour toutes les dépendances racine.

1. Après la mise à jour du compositeur, exécutez :

   ```bash
   bin/magento setup:upgrade
   ```

1. Validez et poussez vos modifications.

## Dépannage

Des erreurs peuvent s’afficher lors de la tentative d’installation de l’extension [!DNL Payment Services]. Utilisez les méthodes de dépannage suivantes pour résoudre les erreurs.

### Liste des référentiels

Vérifiez que `repo.magento.com` est présent dans votre liste de référentiels.

### Clés de compositeur incorrectes

Si l’erreur suivante indique que vous disposez des clés de compositeur incorrectes :

```
Could not find a matching version of package magento/payment-services. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (stable).
```

Vérifiez que vos clés de compositeur sont valides et que vous avez accès à d’autres packages de Magento.

Pour voir quelles clés de compositeur sont configurées :

1. Recherchez l’emplacement du fichier `auth.json` :

   ```bash
   composer config --global home
   ```

1. Affichez le fichier `auth.json` :

   ```bash
   cat /path/to/auth.json
   ```

1. Voir [ clés associées à votre compte Commerce `MageID`](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/authentication-keys).

### Mémoire insuffisante pour PHP

Si l’erreur suivante indique que vous n’avez pas assez de mémoire pour PHP :

```
Fatal error: Allowed memory size of 2146435072 bytes exhausted (tried to allocate 4096 bytes) in phar:///usr/local/bin/composer/src/Composer/DependencyResolver/RuleWatchGraph.php on line 52
```

[Augmentez la limite de mémoire](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/app/php-settings#increase-php-memory-limit) pour PHP sur votre environnement dans `php.ini`.

Vous pouvez également spécifier la limite de mémoire en utilisant cette commande : `php -d memory_limit=-1 [path to composer]/composer require magento/payment-services`.

Par exemple :

```bash
php -d memory_limit=-1 vendor/bin/composer require magento/payment-services
```
