---
title: "Installer [!DNL Quick Checkout] pour l’extension Adobe Commerce"
description: "Suivez ces étapes pour installer [!DNL Quick Checkout] dans votre projet Adobe Commerce."
exl-id: e1dabc9a-0ab0-4f8d-98d3-7a32abbedcb8
feature: Checkout, Services, Install
source-git-commit: b1984a26463e14b8dc9a789421e49e5ea81ad039
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# Installer [!DNL Quick Checkout]

La variable [!DNL Quick Checkout] extension pour Adobe Commerce et [!DNL Magento Open Source] peut être installé avec [!DNL Composer keys], qui sont liés au compte Commerce [`mageid`](https://devdocs.magento.com/marketplace/sellers/profile-personal.html#field-descriptions){target="_blank"} fourni dans le processus d’inscription. Le compositeur utilise ces clés lors de l’installation initiale d’Adobe Commerce ou dans les cas où la fonction [!DNL Composer keys] n’ont pas été précédemment enregistrés dans la variable `auth.json` fichier .

Voir [Obtention des clés d’authentification](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html){target="_blank"} rubrique pour plus d’informations sur l’obtention [!DNL Composer keys].

Il existe deux manières d’installer cette extension : pour [Adobe Commerce sur l’infrastructure cloud](#magento-commerce-cloud) ou [sur site](#on-premises) installations. Pour utiliser ces méthodes, vous devez utiliser l’interface de ligne de commande.

## Mise à jour du paramètre de stabilité minimale

Avant d’installer l’extension, assurez-vous que la variable `minimum-stability` dans votre `composer.json` est défini sur `"stable"`:

`"minimum-stability": "stable"`

## Installation de l’extension

Vous pouvez installer le [!DNL Quick Checkout] extension pour Adobe Commerce sur l’infrastructure cloud et les instances sur site.

### Adobe Commerce sur l’infrastructure cloud

Cette méthode est utilisée pour installer le [!DNL Quick Checkout] pour une instance de Commerce Cloud.

1. Sur votre poste de travail local, accédez au répertoire racine du projet Cloud.

1. Mettez à jour votre `composer.json` fichier :

   ```bash
   composer require magento/quick-checkout --no-update
   ```

1. Mettez à jour les dépendances et installez l’extension :

   ```bash
   composer update
   ```

   La variable `composer update` met à jour toutes les dépendances. Si vous ne souhaitez pas mettre à jour toutes les dépendances en même temps, utilisez plutôt la commande suivante : `composer update magento/quick-checkout`.

1. Validez et poussez vos modifications.

### Sur site

Cette méthode est utilisée pour installer le [!DNL Quick Checkout] pour une instance On-Premise.

1. Ajoutez le module Achat rapide au `require` de la `composer.json` fichier :

   ```bash
   composer require magento/quick-checkout --no-update
   ```

1. Mettez à jour les dépendances et installez l’extension :

   ```bash
   composer update
   ```

   La variable `composer update` met à jour toutes les dépendances. Si vous ne souhaitez pas mettre à jour toutes les dépendances en même temps, utilisez plutôt la commande suivante : `composer update magento/quick-checkout`.

1. Mettre à niveau Adobe Commerce :

   ```bash
   bin/magento setup:upgrade
   ```

1. Effacez le cache :

   ```bash
   bin/magento cache:clean
   ```

1. Validez les modifications.
1. Mettez à jour votre instance sur site pour vous assurer que le code validé est déployé.

## Mettre à niveau l’extension

Lorsque nous publions une nouvelle version de la variable [!DNL Quick Checkout], vous pouvez facilement mettre à niveau votre extension.

1. Pour obtenir la version la plus récente du package :

   ```bash
   composer update
   ```

   La variable `composer update` met à jour toutes les dépendances. Si vous ne souhaitez pas mettre à jour toutes les dépendances en même temps, utilisez plutôt la commande suivante : `composer update magento/quick-checkout`.

1. Validez et poussez vos modifications.

## Dépannage

Des erreurs peuvent s’afficher lors de la tentative d’installation du [!DNL Quick Checkout] extension .

Si vous rencontrez des problèmes au cours de la [!DNL Quick Checkout] processus d’installation, voir [Dépannage des problèmes de paiement rapide](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/quick-checkout-issues.html) dans le centre d’aide d’Adobe Commerce.

## Conditions préalables

Voir [conditions préalables](../quick-checkout/prerequisites.md) pour plus d’informations.
