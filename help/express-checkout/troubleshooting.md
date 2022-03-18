---
title: Résolution des problèmes liés à [!DNL Express Checkout]
description: Dépannage des erreurs, problèmes connus que vous pouvez rencontrer lors de l’utilisation de la variable [!DNL Express Checkout] pour l’extension Adobe Commerce.
exl-id: a379ff81-360d-4cb9-a123-47e8cbc0cdbd
source-git-commit: 163dd5260908b4ea3a8bfbcfdb834531d1603734
workflow-type: tm+mt
source-wordcount: '472'
ht-degree: 0%

---

# Résolution des problèmes [!DNL Express Checkout] pour Adobe Commerce

>[!IMPORTANT]
>
> Cette fonctionnalité est réservée aux utilisateurs du Programme des Adopteurs Anticipés (EAP) et n’est pas encore accessible à tous les clients. Actuellement limitée aux clients américains. Contactez l’assistance d’Adobe Commerce pour toute question ou assistance.

Utilisez les méthodes de dépannage suivantes pour résoudre ces problèmes spécifiques.

## Clés de compositeur incorrectes

Si l’erreur suivante indique que vous disposez des clés de compositeur incorrectes :

```terminal
Could not find a matching version of package magento/express-checkout. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (RC).
```

Vérifiez que vos clés de compositeur sont liées à l’ID de Magento utilisé lors de l’enregistrement du passage en caisse express.

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

## Stabilité minimale dans la variable `composer.json` est défini sur stable

Si l’erreur suivante indique que vous disposez des clés de compositeur incorrectes :

```terminal
Could not find a matching version of package magento/express-checkout. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (stable).
```

Définissez la stabilité minimale sur `RC` dans le `composer.json` fichier .

## Mémoire insuffisante pour PHP

Si l’erreur suivante indique que vous n’avez pas assez de mémoire pour PHP :

```terminal
Fatal error: Allowed memory size of 2146435072 bytes exhausted (tried to allocate 4096 bytes) in phar:///usr/local/bin/composer/src/Composer/DependencyResolver/RuleWatchGraph.php on line 52
```

[Augmentation de la limite de mémoire](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html#increase-php-memory-limit) pour PHP sur votre environnement dans `php.ini`.

Vous pouvez également spécifier la limite de mémoire à l’aide de cette commande : `php -d memory_limit=-1 [path to composer]/composer require magento/express-checkout`.

Par exemple :

```bash
php -d memory_limit=-1 vendor/bin/composer require magento/express-checkout
```

## Adresse de livraison non valide

Il existe un problème connu pour le [!DNL Express Checkout].

Lorsque l’adresse de livraison par défaut n’est pas valide, le client est redirigé vers l’étape de l’adresse de livraison. Storefront affiche uniquement les adresses de livraison valides.

>[!WARNING]
>
> s’il n’existe aucune adresse de livraison valide, le client ne voit aucune adresse de livraison disponible.

Reportez-vous à la section [détails de livraison](../express-checkout/shipping-details.md) pour plus d’informations.

## Ajout de lignes d’adresse de rue avec une nouvelle adresse de livraison

Il existe un problème connu pour le [!DNL Express Checkout].

Lorsque vous [connexion avec un compte Bolt](https://help.bolt.com/shoppers/guides/checkout/log-in/) vous pouvez ajouter une nouvelle adresse de livraison avec une limite de 4 lignes par adresse de rue.

Adobe Commerce peut généralement être configuré pour prendre en charge jusqu’à 20 lignes d’adresses de rue.

## Case à cocher `enable terms and conditions` ne s’affiche pas correctement

Il existe un problème connu pour le [!DNL Express Checkout].

Lorsque vous activez la variable `Enable terms and conditions` et [connexion avec un compte Bolt](https://help.bolt.com/shoppers/guides/checkout/log-in/), la case à cocher n’est pas affichée.

Voir [conditions générales](https://docs.magento.com/user-guide/sales/terms-and-conditions.html) pour plus d’informations.

## Comportement inattendu lorsque `Display Billing Address On` est défini sur `payment page`

Il existe un problème connu pour le [!DNL Express Checkout].

Si vous définissez la variable `Display Billing Address On` du paramètre `payment page` et [connexion avec un compte Bolt](https://help.bolt.com/shoppers/guides/checkout/log-in/) lorsque vous cochez la variable `My billing and shipping address are the same` case à cocher :

![Même adresse](../assets/checked-address.png)

Bouton radio `use existing card`.

Voir [Passage en caisse](https://docs.magento.com/user-guide/configuration/sales/checkout.html) pour plus d’informations sur la rubrique `Display Billing Address On` .

## Traduire la [!DNL Express Checkout] extension

Adobe Commerce vous permet de localiser votre boutique pour plusieurs régions et marchés. Vous pouvez même localiser les messages d’erreur dans la vue Admin.

Reportez-vous à la section [traduction et localisation](https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/translations/xlate.html) pour plus d’informations.

## Obtenir de l’aide

Contactez l’assistance d’Adobe Commerce pour obtenir de l’aide ou des questions supplémentaires.
