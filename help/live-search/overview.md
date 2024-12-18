---
title: Qu’est-ce que  [!DNL Live Search] ?
description: '[!DNL Live Search] d’Adobe Commerce offre une expérience de recherche rapide, pertinente et intuitive.'
exl-id: aca0ef19-ead1-4c79-90c3-db5ec48cb3c1
recommendations: noCatalog
source-git-commit: 7f536c93ab1c87bf88bc892b2a485067fa8f8110
workflow-type: tm+mt
source-wordcount: '726'
ht-degree: 0%

---

# Qu’est-ce que [!DNL Live Search] ?

[!DNL Live Search] est une fonctionnalité qui remplace les fonctionnalités de recherche standard dans Adobe Commerce. La fonction [!DNL Live Search] est installée avec le compositeur et connecte votre boutique [!DNL Commerce] au [connecteur Commerce Services](../landing/saas.md). Lorsqu’il est configuré, le champ de texte de recherche par défaut est remplacé par le champ de texte [!DNL Live Search]. [!DNL Live Search] installe également le widget Page de liste de produits (PLP), qui fournit de puissantes fonctionnalités de filtrage lors de la navigation dans les résultats de recherche.

Avec [!DNL Live Search], vous pouvez :

- Créez des expériences de recherche significatives pour aider les acheteurs et les acheteurs à trouver ce qu’ils veulent avec le moins d’effort possible.
- Tirez parti de la facette dynamique optimisée par l’IA et du reclassement des résultats de recherche en réponse aux comportements d’achat de session.
- Utilisez un service léger basé sur SaaS qui offre des mises à jour simples et qui est inclus dans votre licence, ce qui réduit le coût total de propriété.
- Apportez des informations techniques en activant l’API GraphQL, la flexibilité sans interface utilisateur, les environnements de test d’API et les applications SaaS ultra-rapides.

>[!IMPORTANT]
>
>En ce qui concerne la recherche de site, Adobe Commerce vous offre des options. Avant de procéder à la mise en oeuvre, passez en revue les informations [Limites et limites](boundaries-limits.md) pour vous assurer que [!DNL Live Search] est adapté à vos besoins professionnels.

## Architecture

Le côté Adobe Commerce de l’architecture inclut l’hébergement de la recherche *Admin*, la synchronisation des données de catalogue et l’exécution du service de requête. Une fois [!DNL Live Search] installé et configuré, Adobe Commerce commence à partager les données de recherche et de catalogue avec les services SaaS. À ce stade, les utilisateurs administrateurs peuvent configurer, personnaliser et gérer la recherche [facettes](facets.md), [synonymes](synonyms.md) et [règles de marchandisage](category-merch.md).

![Flux de données de recherche en direct](assets/ls-cs-data-flow.png)

## Présentation rapide

En mettant l&#39;accent sur la vitesse, la pertinence et la facilité d&#39;utilisation, [!DNL Live Search] change la donne pour les acheteurs comme pour les commerçants. Regardez la vidéo suivante, puis faites un tour rapide de [!DNL Live Search] depuis le storefront.

>[!VIDEO](https://video.tv.adobe.com/v/3418797?learn=on)

Pour une vidéo plus détaillée sur l’utilisation et la configuration de la recherche en direct, consultez la rubrique [Démonstration complète sur [!DNL Live Search]](https://experienceleague.adobe.com/en/docs/commerce-learn/tutorials/getting-started/capabilities/live-search-full-demonstration) .

### Recherche en cours de frappe

[!DNL Live Search] répond avec des suggestions de produits et une image miniature des principaux résultats de recherche dans une [fenêtre contextuelle](storefront-popover.md) en tant que requêtes de type shoppers dans la zone [Search](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search). La page [Détails du produit](https://experienceleague.adobe.com/en/docs/commerce-admin/start/storefront/storefront) s’affiche lorsque les acheteurs cliquent sur un produit suggéré ou présenté. Un lien _Afficher tout_ dans le pied de page de la fenêtre contextuelle affiche la page des résultats de la recherche.

[!DNL Live Search] renvoie les résultats de &quot;recherche en cours de frappe&quot; pour une requête de deux caractères ou plus. Pour une correspondance partielle, le nombre maximal de caractères par mot est de 20. Le nombre de caractères dans la requête n’est pas configurable. La fenêtre contextuelle comprend les champs`name`, `sku` et `category_ids`.

![Exemple de storefront - effectuez une recherche lorsque vous tapez](assets/storefront-search-as-you-type.png)

### Afficher tous les résultats de recherche

Pour répertorier tous les produits renvoyés par la requête &quot;rechercher lorsque vous tapez&quot;, cliquez sur _Afficher tout_ dans le pied de page de la fenêtre contextuelle.

![Exemple de storefront - facettes de prix](assets/storefront-view-all-search-results.png)

### Recherche filtrée avec facettes

La recherche filtrée utilise plusieurs dimensions de valeurs d’attribut, ou [facettes](facets.md), comme critères de recherche. La sélection des filtres est définie par le commerçant et change en fonction des produits renvoyés, les facettes les plus couramment utilisées étant collées en haut de la liste.

Utilisez les facettes comme paramètres d’URL :`http://yourwebsite.com?color=red` et les résultats des filtres de recherche en direct en fonction de ces valeurs d’attribut.

### Synonymes

[Synonymes](synonyms.md) élargit la portée et accentue la cible des requêtes en incluant des mots que les acheteurs peuvent utiliser qui diffèrent de ceux du catalogue. Vous pouvez affiner le dictionnaire de synonyme pour que les acheteurs restent actifs et sur le chemin de l’achat.

### Règles de marchandisage

Le marchandisage [rules](rules.md) façonne l’expérience d’achat avec des instructions if-then ajoutant une logique et des événements à rechercher. Vous pouvez facilement booster ou enterrer des produits pour une promotion, une saison ou toute autre période.

### Prise en charge des termes de recherche

[!DNL Live Search] prend en charge les [redirections de termes de recherche](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search-terms) de Commerce. Par exemple, les utilisateurs peuvent rechercher un terme tel que &quot;Taux de livraison&quot; et être redirigés directement vers la page des taux de livraison.

## Composants de recherche en direct

- [!DNL Live Search] [le widget contextuel](storefront-popover.md) est la zone qui s’ouvre sous le champ de recherche qui contient les résultats de la recherche.
- [Le widget de page de liste de produits ](plp-styling.md) (PLP) fournit une page de liste de produits pouvant faire l’objet de recherches, avec des facettes et une prise en charge de synonymes. Le widget est installé et activé dans Live Search 4.0.0+.
- (**Obsolète**) L’adaptateur de recherche était le précurseur du widget PLP et a été installé avec Live Search &lt; 4.0.0. Si vous utilisez une version de Live Search antérieure à 4.0.0, Commerce vous recommande de mettre à niveau pour bénéficier des avantages des fonctionnalités du widget PLP et des améliorations futures.

## [!DNL Live Search] espace de travail

L’ [!DNL Live Search] [espace de travail](workspace.md) est la zone de l’administrateur dans laquelle vous configurez des fonctionnalités [!DNL Live Search] telles que des synonymes, des facettes et le marchandisage par catégorie.

## Événements

[!DNL Live Search] utilise [events](events.md) pour calculer les tableaux de bord [Marchandisage intelligent](category-merch.md) et [performance](performance.md). Le mode Eventing est fourni avec les implémentations par défaut. Le mode Eventing pour les vitrines sans interface doit être activé manuellement.
