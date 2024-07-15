---
title: Développement de l’administrateur Recommendations du produit
description: Présentation de l’architecture et des fonctionnalités de développement de Recommendations de produit.
exl-id: caef5e0c-dd69-4846-8f85-b1c5e1c6a28f
source-git-commit: a433d970e83792a9f53b2a09afd84c335d980024
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# Développement de l’administrateur Recommendations du produit

Product Recommendations est un puissant outil marketing que vous pouvez utiliser pour augmenter les conversions, augmenter les recettes et stimuler l’engagement des acheteurs. Les Recommendations produit sont affichées sur le storefront sous la forme d’unités telles que &quot;Les clients qui ont consulté ce produit ont également consulté&quot;, &quot;Les clients qui ont acheté ce produit ont également acheté&quot;, &quot;Recommandé pour vous&quot;, etc. Adobe Commerce Product Recommendations est optimisé par [Adobe Sensei](https://www.adobe.com/sensei.html), qui utilise une intelligence artificielle et des algorithmes d’apprentissage automatique pour effectuer une analyse approfondie des données d’acheteurs agrégées. Ces données, lorsqu’elles sont combinées à votre catalogue Commerce, génèrent des expériences hautement attrayantes, pertinentes et personnalisées pour l’acheteur.

>[!NOTE]
>
>Si votre vitrine est mise en oeuvre à l’aide de PWA Studio, reportez-vous à la [documentation du PWA](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). Si vous utilisez une technologie front-end personnalisée telle que React ou Vue JS, reportez-vous au guide d’utilisation pour découvrir comment intégrer Product Recommendations dans un environnement [headless](headless.md). Les instances sans affichage doivent implémenter des événements pour alimenter l’espace de travail de recommandation de produit.

## Présentation de l’architecture

À un niveau élevé, les Recommendations de produits Commerce sont déployés en tant que SaaS. Le côté Commerce comprend le storefront, qui contient le collecteur d’événements et le modèle de mise en page des recommandations, ainsi que le serveur principal, qui inclut les services de données, le module d’exportation SaaS et l’interface utilisateur d’administration. Les services de renseignement Adobe Sensei sont utilisés du côté SaaS.

![ Diagramme d’architecture des recommandations de produits ](assets/arch-diag-sensei.svg)

Une fois les modules de recommandation installés et configurés, votre vitrine commence à collecter des données comportementales. Adobe Sensei traite ces données comportementales avec vos données de catalogue et calcule les associations de produits qui sont exploitées par le service de recommandations. À ce stade, le marchand peut créer, gérer et déployer des unités de recommandations de produits sur son storefront directement depuis l’interface utilisateur d’administration.

## Types de données

Product Recommendations nécessite les données suivantes :

- **Comportement** - Données provenant de l’engagement d’un acheteur sur votre site, telles que les consultations de produits, les articles ajoutés à un panier et les achats. Commerce et Adobe Sensei ne collectent pas d’informations d’identification personnelle.

- **Catalogue** - Métadonnées de produit telles que le nom, le prix, la disponibilité, etc.

Lors de l’installation du module `magento/product-recommendations`, Adobe Sensei agrège les données comportementales et de catalogue, créant ainsi un Recommendations de produits pour chaque type de recommandation. Le service Recommendations de produit déploie ensuite ces recommandations sur votre vitrine.

>[!NOTE]
>
>Pour les produits configurables, le Recommendations de produit utilise l’image du produit parent dans l’unité de recommandation. Si aucune image n’est spécifiée pour le produit configurable, l’unité de recommandation sera vide pour ce produit spécifique.

## Étapes suivantes

Lisez les rubriques suivantes pour commencer à utiliser Product Recommendations :

- [Comment mettre en oeuvre le Recommendations de produit](implementation-workflow.md)

- [Installation et configuration de Product Recommendations](install-configure.md)

- [Créer un Recommendations de produit](create.md)
