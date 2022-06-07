---
title: '"Installez le [!DNL Quick Checkout] pour l’extension Adobe Commerce"'
description: '"Procédez comme suit pour installer le [!DNL Quick Checkout] dans votre projet Adobe Commerce."'
exl-id: e1dabc9a-0ab0-4f8d-98d3-7a32abbedcb8
source-git-commit: 9841db7616c8aa6d5bc5af3e6e92c0abe9a4a1e2
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# Installez le [!DNL Quick Checkout]

Le [!DNL Quick Checkout] pour Adobe Commerce offre une expérience de passage en caisse transparente, conçue pour convertir des clients invités uniques en détenteurs de compte fidèles.

Le [!DNL Quick Checkout] extension pour Adobe Commerce et [!DNL Magento Open Source] peut être installé avec [!DNL Composer keys], qui sont liés à la variable [Identifiant du Magento (mageid)](https://devdocs.magento.com/marketplace/sellers/profile-personal.html#field-descriptions){target=&quot;_blank&quot;} fourni dans le processus d’inscription. Le compositeur utilise ces clés lors de l’installation initiale d’Adobe Commerce ou dans les cas où la fonction [!DNL Composer keys] n’ont pas été précédemment enregistrés dans le `auth.json` fichier .

Voir [Obtention des clés d’authentification](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html)Rubrique {target=&quot;_blank&quot;} pour plus d’informations sur l’obtention [!DNL Composer keys].

Il existe deux manières d’installer cette extension : pour [Adobe Commerce sur l’infrastructure cloud](#magento-commerce-cloud) ou [sur site](#on-premises) installations. Pour utiliser ces méthodes, vous devez utiliser l’interface de ligne de commande.

## Mise à jour du paramètre de stabilité minimale

Avant d’installer l’extension, vous pouvez modifier la variable `minimum-stability` obligatoire `RC` (candidat à la publication) dans votre `composer.json` si vous souhaitez essayer la version du candidat de version. Vous pouvez utiliser un IDE ou votre éditeur de texte préféré (comme Visual Studio Code ou Sublime Text).

Dans votre `composer.json` fichier, modifier `"minimum-stability": "stable"` to `"minimum-stability": "RC"`.

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

   Le `composer update` met à jour toutes les dépendances. Si vous ne souhaitez pas mettre à jour toutes les dépendances en même temps, utilisez plutôt la commande suivante : `composer update magento/quick-checkout`.

1. Validez et envoyez vos modifications.

### Sur site

Cette méthode est utilisée pour installer le [!DNL Quick Checkout] pour une instance On-Premise.

1. Ajoutez le module Achat rapide au `require` de la section `composer.json` fichier :

   ```bash
   composer require magento/quick-checkout --no-update
   ```

1. Mettez à jour les dépendances et installez l’extension :

   ```bash
   composer update
   ```

   Le `composer update` met à jour toutes les dépendances. Si vous ne souhaitez pas mettre à jour toutes les dépendances en même temps, utilisez plutôt la commande suivante : `composer update magento/quick-checkout`.

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

   Le `composer update` met à jour toutes les dépendances. Si vous ne souhaitez pas mettre à jour toutes les dépendances en même temps, utilisez plutôt la commande suivante : `composer update magento/quick-checkout`.

1. Validez et envoyez vos modifications.

## Dépannage

Des erreurs peuvent s’afficher lors de la tentative d’installation du [!DNL Quick Checkout] extension .

Reportez-vous à la section [dépannage](../quick-checkout/troubleshooting.md) rubrique pour plus d’informations si vous rencontrez des problèmes lors de l’installation de la variable [!DNL Quick Checkout].

## Conditions préalables

Voir [conditions préalables](../quick-checkout/prerequisites.md) pour plus d’informations.
