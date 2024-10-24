---
title: Test dans l’environnement d’évaluation
description: Découvrez comment utiliser  [!DNL Product Recommendations] de votre environnement de production dans votre environnement d’évaluation à des fins de test.
exl-id: 178ff2aa-7821-45f7-85f1-d490d8182817
feature: Services, Recommendations, Staging
source-git-commit: 4a5c3550b03651279c24de6b6361ffa6dc28776e
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# Test dans l’environnement d’évaluation

Avant de déployer des recommandations dans votre environnement de production, testez le service dans un environnement hors production pour vous assurer que tout fonctionne comme prévu.

[!DNL Product Recommendations] renvoie des produits basés sur les [données de comportement d’achat](events.md) collectées à partir de votre vitrine. Cependant, dans un environnement hors production, il est probable que vous ne disposiez d’aucune donnée comportementale de la part des acheteurs. `More like this` est le seul type de recommandation que vous pouvez tester sans données comportementales. Ce type de recommandation ne nécessite aucune donnée d’entrée, car il utilise une correspondance de similarité de contenu direct.

Les types de recommandations suivants nécessitent des données comportementales :

- Les plus consultés
- A consulté ceci, consulté cela
- Acheté ceci, acheté cela

Comment tester vos recommandations dans un environnement hors production à l’aide de données comportementales ? Il y a deux ou trois options.

## Récupération des recommandations de l’environnement de production (recommandé)

Adobe Commerce vous permet de récupérer des recommandations de votre environnement de production et de les prévisualiser dans votre environnement hors production en [changeant](settings.md) l’espace de données SaaS.

Pour récupérer les recommandations de votre environnement de production, vous devez vous assurer que :

- La collecte de données Storefront est [configurée et activée](install-configure.md) dans l’environnement de production.
- Le catalogue de votre environnement hors production est largement identique à celui de l’environnement de production. L’utilisation de catalogues similaires permet de s’assurer que les produits renvoyés dans les unités de recommandation ressemblent étroitement à ceux de l’environnement de production.

## Générer des données comportementales sur un environnement hors production

1. Déployez le module `magento/product-recommendations` dans un environnement hors production où les données du catalogue sont similaires à votre catalogue de production.

1. Utilisez l’un des ID d’espace de données hors production pour [la configuration](../landing/saas.md#saas-configuration) dans l’administrateur.

1. Générez vous-même les données en cliquant autour de votre vitrine pour imiter le comportement des acheteurs réels (ou créez un script d’automatisation). Grâce à vos tests, vous générez des événements comportementaux sur votre environnement hors production. Ces événements sont utilisés pour produire les affinités produit qui alimentent les recommandations. Pour les tests, [!DNL Commerce] suggère que vous interagissez avec les types de recommandations suivants :

   - Le plus consulté : nécessite un minimum de données d’entrée. Les utilisateurs doivent afficher les produits.
   - A consulté ceci, consulté cela - Nécessite que plusieurs utilisateurs affichent plusieurs produits.
   - Acheté ceci, acheté cela - Nécessite que plusieurs utilisateurs achètent plusieurs produits.

### Avertissements

- Les données comportementales et de catalogue provenant de l’ [espace de données SaaS](../landing/saas.md#saas-configuration) hors production identifient un environnement isolé dans lequel les recommandations de produits résultantes sont entièrement basées sur les données comportementales générées sur le storefront associé.

- Comme vous ne disposez pas de grandes quantités de données comportementales, les données d’entrée pour calculer les associations de produits sont éparses. Toutefois, ces données sont toujours envoyées à Sensei pour calculer les modèles d’apprentissage automatique et fournir des recommandations basées sur les données générées dans cet environnement.
