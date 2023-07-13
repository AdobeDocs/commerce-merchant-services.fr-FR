---
title: Test dans l’environnement d’évaluation
description: Découvrez comment utiliser [!DNL Product Recommendations] de votre environnement de production dans votre environnement d’évaluation à des fins de test.
exl-id: 178ff2aa-7821-45f7-85f1-d490d8182817
feature: Services, Recommendations, Staging
source-git-commit: 9ae4aff1851e9ce9920c4fbf11d2616d6f0f6307
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# Test dans l’environnement d’évaluation

Avant de déployer des recommandations dans votre environnement de production, vous devez tester un environnement hors production pour vous assurer que tout fonctionne comme prévu.

[!DNL Product Recommendations] renvoyer des produits en fonction de [données comportementales des acheteurs](behavioral-data.md) collecté à partir de votre storefront. Cependant, dans un environnement hors production, il est probable que vous ne disposiez d’aucune donnée comportementale de la part des acheteurs. Le seul type de recommandation que vous pouvez tester sans données comportementales est `More like this`. Ce type de recommandation ne nécessite aucune donnée d’entrée, car il utilise une correspondance de similarité de contenu direct.

Les types de recommandations suivants nécessitent des données comportementales :

- Les plus consultés
- A consulté ceci, consulté cela
- Acheté ceci, acheté cela

Comment pouvez-vous tester vos recommandations dans un environnement hors production à l’aide de données comportementales ? Il y a quelques options.

## Récupération des recommandations de l’environnement de production (recommandé)

Adobe Commerce vous permet de récupérer des recommandations de votre environnement de production et de les prévisualiser dans votre environnement hors production en [changement](settings.md) l’espace de données SaaS.

Pour récupérer les recommandations de votre environnement de production, vous devez vous assurer que :

- La collecte de données Storefront est [configuré et activé](install-configure.md) en production.
- Votre catalogue d’environnement hors production est largement le même que celui que vous avez en production. L’utilisation de catalogues similaires permet de s’assurer que les produits renvoyés dans les unités de recommandation ressemblent étroitement à ceux en production.

## Générer des données comportementales sur un environnement hors production

1. Déployez la variable `magento/product-recommendations` dans un environnement hors production où les données du catalogue sont similaires à votre catalogue de production.

1. Utilisez l’un des identifiants d’espace de données hors production pour [configuration](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html) dans Admin.

1. Générez vous-même les données en cliquant autour de votre vitrine pour imiter le comportement des acheteurs réels (ou créez un script d’automatisation). Grâce à vos tests, vous générez des événements comportementaux sur votre environnement hors production. Ces événements sont utilisés pour produire les affinités produit qui alimentent les recommandations. Pour les tests, [!DNL Commerce] suggère que vous interagissiez avec les types de recommandations suivants :

   - Le plus consulté : nécessite un minimum de données d’entrée. Les utilisateurs doivent afficher les produits.
   - A consulté ceci, consulté cela : nécessite que plusieurs utilisateurs affichent plusieurs produits.
   - Acheté ceci, acheté cela - Nécessite que plusieurs utilisateurs achètent plusieurs produits.

### Avertissements

- Les données comportementales et de catalogue de l’espace de données SaaS hors production identifient un environnement isolé dans lequel les recommandations de produits résultantes sont entièrement basées sur les données comportementales générées sur le storefront associé.

- Comme vous ne disposez pas de grandes quantités de données comportementales, les données d’entrée pour calculer les associations de produits sont éparses. Toutefois, ces données sont toujours envoyées à Sensei pour calculer les modèles d’apprentissage automatique et fournir des recommandations basées sur les données que vous avez générées dans cet environnement.
