---
title: Indexation des prix SaaS
description: Utilisation de l’indexation des prix SaaS pour améliorer les performances
seo-title: Adobe SaaS Price Indexing
seo-description: Price indexing give performance improvements using SaaS infrastructure
exl-id: 747c0f3e-dfde-4365-812a-5ab7768342ab
source-git-commit: 45999b6499f248ea4138f7de4e910c274e747a04
workflow-type: tm+mt
source-wordcount: '763'
ht-degree: 0%

---

# Indexation des prix SaaS

L’indexation des prix SaaS accélère le temps nécessaire pour que les changements de prix soient répercutés sur le site web d’un client après leur envoi. Ce module optionnel permet aux commerçants disposant de catalogues volumineux et complexes, ou de plusieurs sites web ou groupes de clients, de traiter les changements de prix plus rapidement et en continu.

Le plus grand goulot d’étranglement du pipeline : les processus lourds informatiques tels que l’indexation et le calcul des prix ont été déplacés du coeur de PHP vers l’infrastructure cloud de l’Adobe. Cela permet aux commerçants d’augmenter rapidement les ressources pour augmenter les délais d’indexation des prix et de refléter ces modifications sur les sites web à une vitesse beaucoup plus rapide.

Tous les commerçants qui répondent aux exigences peuvent bénéficier de ces améliorations, mais ceux qui en bénéficieront le plus sont les clients avec :

* Modifications constantes des prix : Les commerçants qui nécessitent des modifications répétées de leurs prix pour atteindre des objectifs stratégiques tels que des promotions fréquentes, des remises saisonnières ou des marqueurs d’inventaire.
* Plusieurs sites web et/ou groupes de clients : Marchands avec des catalogues de produits partagés sur plusieurs sites web (domaines/marques) et/ou groupes de clients.
* Grand nombre de prix uniques sur des sites web ou des groupes de clients : Marchands avec des catalogues de produits partagés étendus qui contiennent des prix uniques sur des sites web ou des groupes de clients, tels que des marchands B2B avec des prix négociés au préalable, des marques avec des stratégies de tarification différentes.

Si des applications tierces dépendent de l’indexeur de prix de base PHP, lisez la documentation et consultez le fournisseur d’extension avant d’apporter des modifications.

L’indexation des prix SaaS est disponible gratuitement pour les clients utilisant les services Adobe Commerce.

Ce mini-guide décrit le fonctionnement de l’indexation de prix SaaS et comment l’activer.

## Configuration requise

Pour utiliser l’indexation des prix SaaS, vous devez :

* Adobe Commerce 2.4.4+
* Au moins un des services SaaS suivants est installé :

   * [Service de catalogue](../catalog-service/overview.md)
   * [Recherche en direct](../live-search/guide-overview.md)
   * [Recommendations de produit](../product-recommendations/guide-overview.md)

## Modules

L’indexation des prix SaaS utilise un ensemble de modules pour fournir des fonctionnalités. La liste des modules requis peut être légèrement différente, selon la configuration du magasin.

Ces modules ajoutent les nouveaux flux à l’administrateur. Ces flux transfèrent les données requises pour le calcul des prix à l’indexeur SaaS et ignorent l’indexeur de prix de base PHP.

```
magento/module-product-override-price-remover
magento/module-bundle-product-override-data-exporter
magento/module-product-override-price-remover
magento/module-bundle-product-override-data-exporter
```

Les clients utilisant Luma et Adobe Commerce Core GraphQL peuvent installer un module qui fournit la compatibilité Luma et désactive l’indexeur de prix de base PHP :

```
adobe-commerce/catalog-adapter
```

Le `catalog-adapter` est uniquement compatible avec la version 2.4.5. La prise en charge des versions 2.4.4 et 2.4.6 sera publiée prochainement.
L’indexeur de prix de base PHP peut être réactivé si nécessaire par une extension tierce ou pour toute autre raison.

## Avertissements

Selon des facteurs tels que les types de produits, la complexité des prix et la taille du catalogue, l’indexation des prix SaaS peut être la bonne solution pour votre boutique. Lisez les restrictions suivantes et déterminez s’il s’agit d’une bonne solution pour votre site.

Actuellement, l’indexation des prix SaaS prend en charge les types de produits simples, groupés, virtuels, configurables et dynamiques de lot.
La prise en charge des types de produits téléchargeables, Gift Cards et Bundle Fixed est bientôt disponible.

L’indexation des prix SaaS prend en charge les prix de base :

* Prix régulier min./max.
* Prix final min./max.
* Prix spéciaux
* Prix du groupe client
* Prix des règles du catalogue

Une fois que vous avez accepté d’utiliser le nouveau flux de tarification, vous pouvez contacter [Assistance](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html) pour vous aider à l’annuler.

Les nouveaux flux doivent être synchronisés manuellement avec la variable `resync` [Commande CLI](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html#resynccmdline). Dans le cas contraire, les données sont actualisées dans le processus de synchronisation standard. Obtenez plus d’informations sur la variable [Synchronisation du catalogue](../landing/catalog-sync.md) processus.

## Scénarios d’utilisation

### Luma sans dépendances d’extension

* Un commerçant Luma ou version ultérieure Commerce Core GraphQL qui a installé le service requis (recherche en direct, Recommendations de produit, service de catalogue)
* Aucune extension tierce reposant sur l’indexeur de prix de base PHP
* Vendre des produits dynamiques simples, configurables, groupés, virtuels et regroupés

1. Activez les nouveaux flux.
1. Installez l’adaptateur de catalogue.

### Luma et versions ultérieures Commerce Core GraphQl avec dépendances de l’indexeur de prix de base PHP

* Un commerçant Luma ou version ultérieure Commerce Core GraphQL qui dispose d’un service pris en charge installé (recherche en direct, Recommendations de produits, service de catalogue)
* Avec une extension tierce reposant sur l’indexeur de prix de base PHP
* Vendre des produits dynamiques simples, configurables, groupés, virtuels et regroupés

1. Activation des nouveaux flux
1. Installez l’adaptateur de catalogue.
1. Réactivez l’indexeur de prix de base PHP.
1. Utilisez les nouveaux flux et le code de compatibilité Luma dans la variable `catalog-adapter` module .

### Marchand sans tête

* Un commerçant sans tête qui dispose d’un service pris en charge installé (recherche en direct, Recommendations de produit, service de catalogue)
* Pas de dépendance à l’indexeur de prix de base PHP
* Vendre des produits dynamiques simples, configurables, groupés, virtuels et regroupés

1. Activation de nouveaux flux
1. Installez l’adaptateur de catalogue, qui désactive l’indexeur de prix de base PHP.

### Luma/Core GraphQL/Headless avec les types de produits non pris en charge

* Marchand Luma/Headless
* Vendre des cartes-cadeaux, des produits téléchargeables ou des produits fixes groupés

Avec les types de produit actuellement non pris en charge, attendez la prise en charge complète du type de produit.
