---
title: Présentation [!DNL Live Search]?
description: "[!DNL Live Search] d’Adobe Commerce offre une expérience de recherche rapide, pertinente et intuitive."
exl-id: aca0ef19-ead1-4c79-90c3-db5ec48cb3c1
recommendations: noCatalog
source-git-commit: aba552808ea7af540f64f00a2ae4aeaf2b9cc52e
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Présentation [!DNL Live Search]?

[!DNL Live Search] est une extension qui remplace les fonctionnalités de recherche standard dans Adobe Commerce. La variable [!DNL Live Search] l’extension est installée avec le compositeur et connecte votre [!DNL Commerce] à l’emplacement [!DNL Live Search] [service](../landing/saas.md). Lorsqu’il est configuré, le champ de texte de recherche par défaut est remplacé par le champ [!DNL Live Search] Champ de texte. [!DNL Live Search] installe également le widget Page de liste de produits (PLP), qui fournit de puissantes fonctionnalités de filtrage lors de la navigation dans les résultats de recherche.

Avec [!DNL Live Search], vous pouvez :

- Créez des expériences de recherche significatives pour aider les acheteurs et les acheteurs à trouver ce qu’ils veulent avec le moins d’effort possible.
- Tirez parti de la facette dynamique optimisée par l’IA et du reclassement des résultats de recherche en réponse aux comportements d’achat de session.
- Utilisez un service léger basé sur SaaS qui offre des mises à jour simples et qui est inclus dans votre licence, ce qui réduit le coût total de propriété.
- Obtenez des informations techniques en activant l’API graphQL, la flexibilité sans tête, les environnements Sandbox d’API et les applications SaaS ultra-rapides.

>[!IMPORTANT]
>
>En ce qui concerne la recherche de site, Adobe Commerce vous offre des options. Veillez à lire [Limites et limites](boundaries-limits.md) avant l’implémentation, pour vérifier [!DNL Live Search] est adapté aux besoins de votre entreprise.

## Architecture

Le côté Adobe Commerce de l’architecture inclut l’hébergement de la recherche. *Administration*, synchroniser les données du catalogue et exécuter le service de requête. Après [!DNL Live Search] est installé et configuré, Adobe Commerce commence à partager les données de recherche et de catalogue avec les services SaaS. À ce stade, les utilisateurs administrateurs peuvent configurer, personnaliser et gérer la recherche. [facettes](facets.md), [synonyms](synonyms.md), et [règles de marchandisage](category-merch.md).

![Flux de données de recherche en direct](assets/ls-cs-data-flow.png)

## Présentation rapide

En mettant l&#39;accent sur la rapidité, la pertinence et la facilité d&#39;utilisation, [!DNL Live Search] est un outil de transformation pour les acheteurs comme pour les marchands. Regardez la vidéo suivante, puis faites une rapide visite des [!DNL Live Search] de la vitrine.

>[!VIDEO](https://video.tv.adobe.com/v/3418679?quality=12&learn=on)

Pour une vidéo plus détaillée sur l’utilisation et la configuration de la recherche en direct, voir [Manifestation complète sur [!DNL Live Search]](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/capabilities/live-search-full-demonstration.html) rubrique.

### Recherche en cours de frappe

[!DNL Live Search] répond avec des produits suggérés et une miniature des principaux résultats de recherche dans une [fenêtre contextuelle](storefront-popover.md) comme les clients saisissent des requêtes dans la variable [Rechercher](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#quick-search) de la boîte. La variable [détail du produit](https://experienceleague.adobe.com/docs/commerce-admin/start/storefront/storefront.html#product-page) s’affiche lorsque les acheteurs cliquent sur un produit proposé ou présenté. A _Afficher tout_ dans le pied de page de la fenêtre contextuelle affiche la page des résultats de la recherche.

[!DNL Live Search] renvoie &quot;search as you type&quot; (rechercher en cours de frappe) pour une requête de deux caractères ou plus. Pour une correspondance partielle, le nombre maximal de caractères par mot est de 20. Le nombre de caractères dans la requête n’est pas configurable. La fenêtre contextuelle comprend la variable`name`, `sku`, et `category_ids` des champs.

![Exemple de storefront : effectuez une recherche lorsque vous tapez](assets/storefront-search-as-you-type.png)

### Afficher tous les résultats de recherche

Pour répertorier tous les produits renvoyés par la requête &quot;rechercher lorsque vous tapez&quot;, cliquez sur _Afficher tout_ dans le pied de page de la fenêtre contextuelle.

![Exemple de storefront - facettes de prix](assets/storefront-view-all-search-results.png)

### Recherche filtrée avec facettes

La recherche filtrée utilise plusieurs dimensions de valeurs d’attribut, ou [facettes](facets.md), comme critères de recherche. La sélection des filtres est définie par le commerçant et change en fonction des produits renvoyés, les facettes les plus couramment utilisées étant collées en haut de la liste.

Utilisez les facettes comme paramètres d’URL :`http://yourwebsite.com?color=red`et la recherche en direct filtrent les résultats en fonction de ces valeurs d’attribut.

### Synonymes

[Synonymes](synonyms.md) développez la portée et accentuez le focus des requêtes en incluant des mots que les acheteurs peuvent utiliser qui diffèrent de ceux du catalogue. Vous pouvez affiner le dictionnaire de synonyme pour que les acheteurs restent actifs et sur le chemin de l’achat.

### Règles de marchandisage

Marchandisage [rules](rules.md) façonnez l’expérience d’achat avec des instructions if-then ajoutant une logique et des événements à rechercher. Vous pouvez facilement booster ou enterrer des produits pour une promotion, une saison ou toute autre période.

### Prise en charge des termes de recherche

[!DNL Live Search] prend en charge Commerce [redirections de termes de recherche](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-terms.html). Par exemple, les utilisateurs peuvent rechercher un terme tel que &quot;Taux de livraison&quot; et être redirigés directement vers la page des taux de livraison.

## Composants de recherche en direct

- [!DNL Live Search] [widget contextuel](storefront-popover.md) est la zone qui s’ouvre sous le champ de recherche qui contient les résultats de la recherche.
- [Widget de page de liste de produits](plp-styling.md) fournit une page de liste de produits pouvant faire l’objet d’une recherche, avec facettes et prise en charge de synonymes.
- [[!DNL Live Search] Administration](workspace.md) est l’emplacement où les règles, les facettes et les synonymes sont configurés.

## [!DNL Live Search] workspace

La variable [!DNL Live Search] [workspace](workspace.md) est la zone de l’administrateur dans laquelle vous configurez [!DNL Live Search] fonctions telles que les synonymes, les facettes et le marchandisage par catégorie.

## Événements

[!DNL Live Search] uses [events](events.md) pour calculer [Marchandisage intelligent](category-merch.md) et [performance](performance.md) tableaux de bord. Le mode Eventing est fourni avec les implémentations par défaut. Le mode Eventing pour les vitrines sans interface doit être activé manuellement.
