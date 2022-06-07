---
title: '"Problèmes de dépannage pour le [!DNL Quick Checkout]"'
description: '"Résolution des problèmes, problèmes connus que vous pouvez rencontrer lors de l’utilisation de la variable [!DNL Quick Checkout] pour l’extension Adobe Commerce."'
exl-id: a379ff81-360d-4cb9-a123-47e8cbc0cdbd
source-git-commit: 9841db7616c8aa6d5bc5af3e6e92c0abe9a4a1e2
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 0%

---

# Résolution des problèmes [!DNL Quick Checkout] pour Adobe Commerce

Utilisez les méthodes de dépannage suivantes pour résoudre ces problèmes spécifiques.

## Incorrect [!DNL Composer keys]

Si l’erreur suivante indique que vous avez le code incorrect [!DNL Composer keys]:

```terminal
Could not find a matching version of package magento/quick-checkout. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (RC).
```

Vérifiez que la variable [!DNL Composer keys] sont liés à l’ID de Magento utilisé lors de l’enregistrement du passage en caisse rapide.

Pour voir laquelle [!DNL Composer keys] sont configurés :

1. Recherchez l’emplacement du `auth.json` fichier :

   ```bash
   composer config --global home
   ```

1. Afficher la variable `auth.json` fichier :

   ```bash
   cat /path/to/auth.json
   ```

1. Voir [les clés associées à votre ID de Magento](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html).

## Stabilité minimale dans la variable `composer.json` est défini sur stable

Si l’erreur suivante indique que vous avez le code incorrect [!DNL Composer keys]:

```terminal
Could not find a matching version of package magento/quick-checkout. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (stable).
```

Définissez la stabilité minimale sur `RC` dans le `composer.json` fichier .

## Mémoire insuffisante pour PHP

Si l’erreur suivante indique que vous n’avez pas assez de mémoire pour PHP :

```terminal
Fatal error: Allowed memory size of 2146435072 bytes exhausted (tried to allocate 4096 bytes) in phar:///usr/local/bin/composer/src/Composer/DependencyResolver/RuleWatchGraph.php on line 52
```

[Augmentation de la limite de mémoire](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html#increase-php-memory-limit) pour PHP sur votre environnement dans `php.ini`.

Vous pouvez également spécifier la limite de mémoire à l’aide de cette commande : `php -d memory_limit=-1 [path to composer]/composer require magento/quick-checkout`.

Par exemple :

```bash
php -d memory_limit=-1 vendor/bin/composer require magento/quick-checkout
```

## Adresse de livraison non valide

Il existe un problème connu pour le [!DNL Quick Checkout].

Lorsque l’adresse de livraison par défaut n’est pas valide, le client est redirigé vers l’étape de l’adresse de livraison. Storefront affiche uniquement les adresses de livraison valides.

>[!WARNING]
>
> s’il n’existe aucune adresse de livraison valide, le client ne voit aucune adresse de livraison disponible.

Reportez-vous à la section [détails de livraison](../quick-checkout/shipping-details.md) pour plus d’informations.

## Ajout de lignes d’adresse de rue avec une nouvelle adresse de livraison

Il existe un problème connu pour le [!DNL Quick Checkout].

Lorsque vous [se connecter à l’aide d’un [!DNL Bolt] account](https://help.bolt.com/shoppers/guides/checkout/log-in/) vous pouvez ajouter une nouvelle adresse de livraison avec une limite de 4 lignes par adresse de rue.

Adobe Commerce peut généralement être configuré pour prendre en charge jusqu’à 20 lignes d’adresses de rue.

## Case à cocher `enable terms and conditions` ne s’affiche pas correctement

Il existe un problème connu pour le [!DNL Quick Checkout].

Lorsque vous activez la variable `Enable terms and conditions` dans l’administrateur et connectez-vous avec un [!DNL Bolt] , `Enable terms and conditions` ne s’affiche pas pendant la passage en caisse. Reportez-vous à la section [Connexion](https://help.bolt.com/shoppers/account/login-dashboard/) [!DNL Bolt] pour plus d’informations.

Voir [conditions générales](https://docs.magento.com/user-guide/sales/terms-and-conditions.html) pour plus d’informations sur la configuration de l’administrateur.

## Comportement inattendu lorsque `Display Billing Address On` est défini sur `payment page`

Il existe un problème connu pour le [!DNL Quick Checkout].

Si vous définissez la variable `Display Billing Address On` du paramètre `payment page` et [se connecter avec un [!DNL Bolt] account](https://help.bolt.com/shoppers/guides/checkout/log-in/) lorsque vous cochez la variable `My billing and shipping address are the same` case à cocher du bouton radio s’affiche `use existing card`.

![Même adresse](assets/checked-address.png)

Voir [Passage en caisse](https://docs.magento.com/user-guide/configuration/sales/checkout.html) rubrique pour plus d’informations sur `Display Billing Address On` .

## Traduire la [!DNL Quick Checkout] extension

Adobe Commerce vous permet de localiser votre boutique pour plusieurs régions et marchés. Vous pouvez même localiser les messages d’erreur dans la vue Admin.

Reportez-vous à la section [traduction et localisation](https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/translations/xlate.html) pour plus d’informations.

## Videz votre cache

1. Accédez à **[!UICONTROL System]** > **[!UICONTROL Cache Management]** et cliquez sur **[!UICONTROL Flush Cache]** pour actualiser tous les caches non valides.

## Obtenir de l’aide

Contact [Prise en charge d’Adobe Commerce](mailto:quick-checkout-support@adobe.com) pour obtenir de l’aide.
