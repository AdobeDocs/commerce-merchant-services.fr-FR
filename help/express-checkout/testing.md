---
title: Test de la variable [!DNL Express Checkout] pour l’extension Adobe Commerce
description: Le test et la validation garantissent que la variable [!DNL Express Checkout] fonctionne comme prévu.
exl-id: 308f39e1-e2f6-40d8-b876-0f9013effed3
source-git-commit: d8302d2d652b4e2380cc862183e58cbd2cca831b
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Test de la variable [!DNL Express Checkout] pour l’extension Adobe Commerce

>[!IMPORTANT]
>
> Cette fonctionnalité est réservée aux utilisateurs du Programme des Adopteurs Anticipés (EAP) et n’est pas encore accessible à tous les clients. Actuellement limitée aux clients américains. Contactez l’assistance d’Adobe Commerce pour toute question ou assistance.

Avant d’exposer la variable [!DNL Express Checkout] pour l’extension Adobe Commerce à vos clients, il est recommandé de tester dans un environnement de test et dans votre environnement de production. Les tests et la validation permettent de s’assurer que la variable [!DNL Express Checkout] fonctionne comme prévu et offre une expérience de passage en caisse transparente à votre magasin et à vos clients.

Avant de configurer la variable [!DNL Express Checkout] dans votre administrateur Adobe Commerce, vous devez créer une [production](https://merchant.bolt.com/register){target=&quot;_blank&quot;} et [sandbox](https://merchant-sandbox.bolt.com/register)Compte marchand {target=&quot;_blank&quot;} dans Bolt.

## Test dans un environnement de test

Test de la variable [!DNL Express Checkout] dans un environnement de test est une étape de validation très importante, même s’il s’agit d’un environnement de simulation connecté uniquement au compte sandbox Bolt, et non aux banques ou aux commerçants réels.

### Utilisation d’un compte sandbox

Lorsque vous testez et validez votre environnement de test, vous devez utiliser un faux numéro de carte de crédit et une [sandbox](https://merchant-sandbox.bolt.com/register){target=&quot;_blank&quot;} compte marchand en Bolt, de sorte que vous ne créiez pas de frais réels pour un compte de carte de crédit existant.

## Test en production

>[!NOTE]
>
> Il est vivement recommandé de tester la variable [!DNL Express Checkout] dans un environnement de production, avec de vraies cartes de crédit et des banques, avant d&#39;exposer l&#39;extension aux acheteurs. Même si les tests dans les environnements de test sont importants, les tests en production sont la méthode la plus infaillible pour s’assurer qu’ils fonctionnent comme prévu.

Il est recommandé de tester en production de l’une des deux façons suivantes :

- Choisissez une heure à laquelle vous savez qu’aucune commande ne sera passée par les acheteurs.
- Utilisez un webstore temporairement inaccessible pour les acheteurs, mais accessible à des fins de test.

Effectuez vos tests de production avec de vraies cartes de crédit et des comptes de production Bolt, en testant l’ensemble du cycle de vie d’un passage en caisse. Lorsque vous terminez l’ensemble du flux de passage en caisse au cours du test, vous obtenez une vue d’ensemble claire du fonctionnement de vos fonctionnalités lorsque les acheteurs en direct les utilisent.

Vous devez également vérifier que les informations qui apparaissent sur les relevés bancaires pour les méthodes de paiement que vous utilisez dans les tests de production sont correctes et attendues (y compris la description de votre entreprise).

## Comment tester la variable [!DNL Express Checkout] extension

Effectuez un passage en caisse réussi à partir de votre boutique en procédant comme suit :

1. Positionnez-vous sur votre vitrine et placez les articles de votre choix dans votre panier.
1. Passez à la caisse.
1. Entrez une adresse électronique associée à un compte de contrôle lorsque vous y êtes invité.
1. Saisissez le mot de passe unique (OTP) envoyé à l’adresse électronique du compte.
1. Sélectionnez le tableau de bord de l&#39;environnement :

   - Sandbox
   - Production

1. Ordre.

Une fois une commande passée, vous pouvez afficher les détails de vos commandes dans vos _Grille des commandes_ view :

1. Accédez à _Ventes_ > _Commandes_.
1. Voir la liste de toutes les commandes passées.

Voir [commandes](https://docs.magento.com/user-guide/sales/orders.html) rubrique pour plus d’informations sur votre _Grille des commandes_ vue.
