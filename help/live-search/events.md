---
title: '[!DNL Live Search] Events'
description: Découvrez comment les événements collectent des données pour [!DNL Live Search].
feature: Services, Eventing
exl-id: b0c72212-9be0-432d-bb8d-e4c639225df3
source-git-commit: f771e741d92bf94f46772934edf7a6bc39c75999
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 0%

---

# [!DNL Live Search] Événements

[!DNL Live Search] utilise des événements pour alimenter les algorithmes de recherche tels que &quot;Le plus consulté&quot; et &quot;L’a vu, l’a vu&quot;. Bien que l’exemple [Commerce Luma theme](https://experienceleague.adobe.com/en/docs/commerce-admin/content-design/design/themes/themes#the-default-theme) soit prêt à l’emploi, les implémentations sans interface et personnalisées doivent implémenter des événements pour leurs propres besoins.

Ce tableau décrit les événements utilisés par les [!DNL Live Search] [stratégies de classement](rules-add.md#intelligent-ranking).

| Stratégie de classement | Événements | Page |
| --- | --- | --- |
| Les plus consultés | `page-view`<br>`product-view` | Page Détails du produit |
| Le plus acheté | `page-view`<br>`complete-checkout` | Panier/passage en caisse |
| Les plus ajoutés au panier | `page-view`<br>`add-to-cart` | Page Détails du produit<br>Page Liste des produits<br>Panier<br>Liste des souhaits |
| A consulté ceci, consulté cela | `page-view`<br>`product-view` | Page Détails du produit |

>[!NOTE]
>
>La collecte de données aux fins de [!DNL Live Search] n’inclut pas d’informations d’identification personnelle (PII). Tous les identifiants d’utilisateur, tels que les identifiants de cookie et les adresses IP, sont strictement anonymisés. [En savoir plus](https://www.adobe.com/privacy/experience-cloud.html).

## Événements de tableau de bord obligatoires

Certains événements sont nécessaires pour remplir le [tableau de bord de la recherche en direct](performance.md)

| Zone de tableau de bord | Événements | Champ de jointure |
| ------------------- | ------------- | ---------- |
| Recherches uniques | `page-view`, `search-request-sent`, `search-response-received` | `searchRequestId` |
| Aucune recherche de résultats | `page-view`, `search-request-sent`, `search-response-received` | `searchRequestId` |
| Taux zéro résultat | `page-view`, `search-request-sent`, `search-response-received` | `searchRequestId` |
| Recherches populaires | `page-view`, `search-request-sent`, `search-response-received` | `searchRequestId` |
| Durée position du clic | `page-view`, `search-request-sent`, `search-response-received`, `search-results-view`, `search-product-click` | searchRequestId |
| Taux de clics | `page-view`, `search-request-sent`, `search-response-received`, `search-results-view`, `search-product-click` | `searchRequestId`, `sku`, `parentSku` |
| Taux de conversion | `page-view`, `search-request-sent`, `search-response-received`, `search-results-view`, `search-product-click`, `product-view`, `add-to-cart`, `place-order` | `searchRequestId`, `sku`, `parentSku` |

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

- Les bloqueurs d’annonces publicitaires et les paramètres de confidentialité peuvent empêcher la capture d’événements et peuvent entraîner un sous-rapport de l’engagement et des [mesures](performance.md). De plus, certains événements peuvent ne pas être envoyés en raison de problèmes de réseaux ou de pages laissés par les acheteurs.
- Les implémentations sans affichage doivent implémenter des événements pour alimenter le marchandisage intelligent.

>[!NOTE]
>
>Si le [mode de restriction des cookies](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) est activé, Adobe Commerce ne collecte pas de données comportementales tant que l’acheteur n’a pas consenti à utiliser des cookies. Si le mode Restriction des cookies est désactivé, Adobe Commerce collecte les données comportementales par défaut.
