---
title: '[!DNL Live Search] Events'
description: Découvrez comment les événements collectent des données pour [!DNL Live Search].
feature: Services, Eventing
exl-id: b0c72212-9be0-432d-bb8d-e4c639225df3
source-git-commit: 0d966c8dbd788563fa453912961fdc62a5a6c23e
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# [!DNL Live Search] Événements

[!DNL Live Search] utilise des événements pour alimenter les algorithmes de recherche tels que &quot;Le plus consulté&quot; et &quot;L’a vu, l’a vu&quot;. Bien que les utilisateurs de LUMA reçoivent des événements prêts à l’emploi, les implémentations sans tête et autres implémentations personnalisées doivent implémenter des événements pour leurs propres besoins.

Puisque [!DNL Live Search] et [!DNL Product Recommendations] utilisent le même algorithme principal, certains événements sont partagés par les deux services. Certains événements Recommendations de produit sont nécessaires pour renseigner le tableau de bord Recommendations.

Ce tableau décrit les événements utilisés par les stratégies [!DNL Live Search].

| Stratégie | Produits | Événements | Page |
| --- | --- | --- | ---|
| Les plus consultés | Recherche en direct <br>Recs de produit | page vue<br>consultation du produit | Page Détails du produit |
| Le plus acheté | Recherche en direct <br>Recs de produit | page vue<br> passage en caisse | Panier/passage en caisse |
| Les plus ajoutés au panier | Recherche en direct <br>Recs de produit | page vue<br>ajouter au panier | Page Détails du produit<br>Page Liste des produits<br>Panier<br>Liste des souhaits |
| A consulté ceci, consulté cela | Recherche en direct <br>Recs de produit | page vue<br>consultation du produit | Page Détails du produit |
| Tendance | Recherche en direct <br>Recs de produit | page vue<br>consultation du produit | Page Détails du produit |
| Consulté ceci, acheté cela | Recs de produit | page vue<br>consultation du produit | Page Détails du produit<br>Panier/Passage en caisse |
| Acheté ceci, acheté cela | Recs de produit | page vue<br>consultation du produit | Page Détails du produit |
| Conversion : Afficher à l’achat | Recs de produit | page vue<br>consultation du produit | Page Détails du produit |
| Conversion : Afficher à l’achat | Recs de produit | page vue<br> passage en caisse | Panier/passage en caisse |
| Conversion : Afficher dans le panier | Recs de produit | page vue<br>consultation du produit | Page Détails du produit |
| Conversion : Afficher dans le panier | Recs de produit | page vue<br>ajouter au panier | Page Détails du produit<br>Page Liste des produits<br>Panier<br>Liste des produits |

>[!NOTE]
>
>La collecte de données aux fins de [!DNL Live Search] n’inclut pas d’informations d’identification personnelle (PII). Tous les identifiants d’utilisateur, tels que les identifiants de cookie et les adresses IP, sont strictement anonymisés. [En savoir plus](https://www.adobe.com/privacy/experience-cloud.html).

## Événements de tableau de bord obligatoires

Certains événements sont nécessaires pour remplir le [tableau de bord de la recherche en direct](performance.md)

| Zone de tableau de bord | Événements | Champ de jointure |
| ------------------- | ------------- | ---------- |
| Recherches uniques | `page-view`, `search-request-sent`, | searchRequestId |
| Aucune recherche de résultats | `page-view`, `search-request-sent`, | searchRequestId |
| Taux zéro résultat | `page-view`, `search-request-sent`, | searchRequestId |
| Recherches populaires | `page-view`, `search-request-sent`, | searchRequestId |
| Durée position du clic | `page-view`, `search-request-sent`, `search-response-received`, `search-results-view`, `search-product-click` | searchRequestId |
| Taux de clics | `page-view`, `search-request-sent`, `search-response-received`, `search-results-view`, `search-product-click` | searchRequestId, sku |
| Taux de conversion | `page-view`, `search-request-sent`, `search-response-received`, `search-results-view`, `search-product-click`, `product-view`, `add-to-cart`, `place-order` | searchRequestId, sku |

### contextes requis

Tous les événements nécessitent les contextes `Page` et `Storefront`. Cela doit se produire au niveau de la page ou de la couche de l’application storefront plutôt que lors de la génération d’événements individuels (par exemple, dans une vitrine PHP, le conteneur de l’application PHP est responsable de les définir au moment de l’exécution).

## Utilisation

Voici un exemple de mise en oeuvre de l’événement `search-request-sent` :

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

Les bloqueurs d’annonces publicitaires et les paramètres de confidentialité peuvent empêcher la capture d’événements et peuvent entraîner un sous-rapport de l’engagement et des [mesures](workspace.md).

Le mode Eventing ne capture pas toutes les transactions qui se produisent sur le site du marchand. L&#39;évènement est destiné à donner au marchand une idée générale des événements qui se déroulent sur le site.

Les implémentations sans affichage doivent implémenter des événements pour alimenter le [tableau de bord Recommendations du produit](../product-recommendations/events.md).

>[!NOTE]
>
>Si le [mode de restriction des cookies](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) est activé, Adobe Commerce ne collecte pas de données comportementales tant que l’acheteur n’a pas consenti à utiliser des cookies. Si le mode Restriction des cookies est désactivé, Adobe Commerce collecte les données comportementales par défaut.
