---
title: '''[!DNL Live Search] Événements'
description: Découvrez comment les événements collectent des données pour [!DNL Live Search].
feature: Services, Eventing
source-git-commit: c14ba55bee54954ffcfe760e26dc1d69646ecd69
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 0%

---

# [!DNL Live Search] Événements

[!DNL Live Search] utilise des événements pour alimenter les algorithmes de recherche tels que &quot;Les plus consultés&quot; et &quot;A consulté ceci, consulté cela&quot;. Bien que les utilisateurs de LUMA reçoivent des événements prêts à l’emploi, les implémentations sans tête et autres implémentations personnalisées doivent implémenter des événements pour leurs propres besoins.

Depuis [!DNL Live Search] et [!DNL Product Recommendations] utilisent le même algorithme principal, certains événements sont partagés par les deux services. Certains événements Recommendations de produit sont nécessaires pour renseigner le tableau de bord Recommendations.

## Événements

Ce tableau décrit les événements utilisés par [!DNL Live Search] stratégies.

| Stratégie | Produits | Événements | Page |
| --- | --- | --- | ---|
| Les plus consultés | Recherche en direct<br>Recs de produit | page vue<br>consultation produit | Page Détails du produit |
| Le plus acheté | Recherche en direct<br>Recs de produit | page vue<br>passage en caisse | Panier/passage en caisse |
| Les plus ajoutés au panier | Recherche en direct<br>Recs de produit | page vue<br>ajouter au panier | Page Détails du produit<br>Page Liste des produits<br>Panier<br>Liste de souhaits |
| A consulté ceci, consulté cela | Recherche en direct<br>Recs de produit | page vue<br>consultation produit | Page Détails du produit |
| Tendance | Recherche en direct<br>Recs de produit | page vue<br>consultation produit | Page Détails du produit |
| Consulté ceci, acheté cela | Recs de produit | page vue<br>consultation produit | Page Détails du produit<br>Panier/passage en caisse |
| Acheté ceci, acheté cela | Recs de produit | page vue<br>consultation produit | Page Détails du produit |
| Conversion : Afficher à l’achat | Recs de produit | page vue<br>consultation produit | Page Détails du produit |
| Conversion : Afficher à l’achat | Recs de produit | page vue<br>passage en caisse | Panier/passage en caisse |
| Conversion : Afficher dans le panier | Recs de produit | page vue<br>consultation produit | Page Détails du produit |
| Conversion : Afficher dans le panier | Recs de produit | page vue<br>ajouter au panier | Page Détails du produit<br>Page Liste des produits<br>Panier<br>Wishlist |

>[!NOTE]
>
>Collecte de données aux fins de [!DNL Live Search] ne contient pas d’informations d’identification personnelle (PII). Tous les identifiants d’utilisateur, tels que les identifiants de cookie et les adresses IP, sont strictement anonymisés. [En savoir plus](https://www.adobe.com/privacy/experience-cloud.html).

## Événements de tableau de bord obligatoires

Certains événements sont nécessaires pour renseigner la variable [Tableau de bord de la recherche en direct](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/live-search-admin/performance.html)

| Zone de tableau de bord | Événements |
| ----- | ---- | 
| Recherches uniques | `search-request-sent`,`search-response-received` |
| Aucune recherche de résultats | `search-request-sent`,`search-response-received` |
| Taux zéro résultat | `search-request-sent`,`search-response-received` |
| Recherches populaires | `search-request-sent`,`search-response-received` |
| Durée position du clic | `search-request-sent`,`search-response-received`, `search-results-view`, `search-product-click` |
| Taux de clics | `search-request-sent`,`search-response-received`, `search-results-view`, `search-product-click` |
| Taux de conversion | `search-request-sent`,`search-response-received`, `search-results-view`, `search-product-click`,`product-view`,`add-to-cart`,`place-order` |

### contextes requis

Tous les événements nécessitent la variable `Page` et `Storefront` contextes. Cela doit se produire au niveau de la page ou de la couche de l’application storefront plutôt que lors de la génération d’événements individuels (par exemple, dans une vitrine PHP, le conteneur de l’application PHP est responsable de les définir au moment de l’exécution).

## Utilisation

Voici un exemple de mise en oeuvre de la variable `search-request-sent` event:

```javascript
const mse = window.magentoStorefrontEvents;

/* set in application container */
// mse.context.page(pageCtx);
// mse.context.setStorefrontInstance(storefrontCtx);

/* set before firing event */
mse.context.setSearchInput(searchInputCtx);
mse.publish.searchRequestSent("search-bar");
```

## Avertissements

Les bloqueurs d’annonces publicitaires et les paramètres de confidentialité peuvent empêcher la capture d’événements et peuvent entraîner un engagement et des recettes. [mesures](workspace.md) à être sous-signalés.

Le mode Eventing ne capture pas toutes les transactions qui se produisent sur le site du marchand. L&#39;évènement est destiné à donner au marchand une idée générale des événements qui se déroulent sur le site.

Les implémentations sans affichage doivent implémenter des événements pour alimenter la variable [Tableau de bord Recommendations du produit](../product-recommendations/events.md).

>[!NOTE]
>
>If [Mode de restriction des cookies](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) est activée, Adobe Commerce ne collecte les données comportementales que si l’acheteur a consenti à utiliser des cookies. Si le mode Restriction des cookies est désactivé, Adobe Commerce collecte les données comportementales par défaut.
