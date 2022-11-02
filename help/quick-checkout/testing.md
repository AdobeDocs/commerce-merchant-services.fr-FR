---
title: "Test de la [!DNL Quick Checkout] pour l’extension Adobe Commerce"
description: "Le test et la validation garantissent que la variable [!DNL Quick Checkout] fonctionne comme prévu."
exl-id: 308f39e1-e2f6-40d8-b876-0f9013effed3
source-git-commit: bd02a8083d3f4c9cb0422b27d61bd5462187ffc3
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Testez la variable [!DNL Quick Checkout] extension

Avant d’exposer la variable [!DNL Quick Checkout] pour l’extension Adobe Commerce à vos clients, il est recommandé de tester dans un environnement de test et dans votre environnement de production. Les tests et la validation permettent de s’assurer que la variable [!DNL Quick Checkout] fonctionne comme prévu et offre une expérience de passage en caisse transparente à votre magasin et à vos clients.

Avant de configurer la variable [!DNL Quick Checkout] Dans votre administrateur Adobe Commerce, il est nécessaire de créer  [production](https://merchant.bolt.com/register){target=&quot;_blank&quot;} et [sandbox](https://merchant-sandbox.bolt.com/register){target=&quot;_blank&quot;} comptes de commerce dans [!DNL Bolt].

## Test dans un environnement de test

Test de la variable [!DNL Quick Checkout] dans un environnement de test est une étape de validation très importante, même s’il s’agit d’un environnement de simulation connecté uniquement à la fonction [!DNL Bolt] compte sandbox, pas aux banques réelles ou aux marchands.

### Utilisation d’un compte sandbox

Lorsque vous testez et validez votre environnement de test, vous devez utiliser un faux numéro de carte de crédit et une [sandbox](https://merchant-sandbox.bolt.com/register)compte commercial {target=&quot;_blank&quot;} dans [!DNL Bolt], afin que vous ne créiez pas de frais réels pour un compte de carte de crédit existant.

## Test en production

>[!NOTE]
>
> Il est vivement recommandé de tester la variable [!DNL Quick Checkout] dans un environnement de production, avec de vraies cartes de crédit et des banques, avant d&#39;exposer l&#39;extension aux acheteurs. Même si les tests dans les environnements de test sont importants, les tests en production sont la méthode la plus infaillible pour s’assurer qu’ils fonctionnent comme prévu.

Testez votre environnement de production de l’une des deux façons recommandées :

- Choisissez une heure à laquelle vous savez qu’aucune commande ne sera passée par les acheteurs.
- Utilisez un webstore temporairement inaccessible pour les acheteurs, mais accessible à des fins de test.

Effectuez vos tests de production avec de vraies cartes de crédit et [!DNL Bolt] comptes de production, testant l’ensemble du cycle de vie d’un passage en caisse. Lorsque vous terminez l’intégralité du flux de passage en caisse au cours du test, vous obtenez une vue d’ensemble claire de vos fonctionnalités lorsque les acheteurs en direct les utilisent.

Vous devez également vérifier que les informations qui apparaissent sur les relevés bancaires pour les méthodes de paiement que vous utilisez dans les tests de production sont correctes et attendues (y compris la description de votre entreprise).

## Comment tester la variable [!DNL Quick Checkout] extension

Effectuez un passage en caisse réussi à partir de votre magasin :

1. Positionnez-vous sur votre vitrine et placez les articles de votre choix dans votre panier.
1. Passez à la caisse.
1. Entrez une adresse électronique associée à un [!DNL Bolt] compte lorsque vous y êtes invité.
1. Saisissez le mot de passe unique (OTP) envoyé à l’adresse électronique du compte.
1. Sélectionnez le tableau de bord de l&#39;environnement :

   - Sandbox
   - Production

1. Placez la commande.

Une fois une commande passée, vous pouvez afficher les détails de vos commandes dans vos _Grille des commandes_ view :

1. Accédez à _Ventes_ > _Commandes_.
1. Voir la liste de toutes les commandes passées.

Voir [Commandes](https://docs.magento.com/user-guide/sales/orders.html) rubrique pour plus d’informations sur votre _Grille des commandes_ vue.
