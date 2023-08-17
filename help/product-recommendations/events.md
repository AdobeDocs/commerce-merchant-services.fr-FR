---
title: Collecter des données
description: Découvrez comment les événements collectent des données pour les recommandations de produits.
exl-id: b827d88c-327f-4986-8239-8f1921d8383c
feature: Services, Recommendations, Eventing
source-git-commit: 9ae4aff1851e9ce9920c4fbf11d2616d6f0f6307
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# Collecter des données

Lorsque vous installez et configurez des fonctionnalités Adobe Commerce basées sur SaaS telles que [Recommendations de produit](install-configure.md) ou [Recherche en direct](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html), les modules déploient la collecte de données comportementales sur votre storefront. Ce mécanisme collecte des données comportementales anonymes auprès de vos acheteurs et alimente les recommandations de produits. Par exemple, la variable `view` est utilisé pour calculer la variable `Viewed this, viewed that` le type de recommandation et la variable `place-order` est utilisé pour calculer la variable `Bought this, bought that` type de recommandation.

>[!NOTE]
>
>La collecte de données aux fins des recommandations de produits n’inclut pas d’informations d’identification personnelle (PII). Tous les identifiants d’utilisateur, tels que les identifiants de cookie et les adresses IP, sont strictement anonymisés. [En savoir plus](https://www.adobe.com/privacy/experience-cloud.html).

Les événements suivants ne sont pas spécifiques à Product Recommendations, mais sont nécessaires pour renvoyer des résultats :

- `view`
- `add-to-cart`
- `place-order`

La variable [Collecteur d’événements Adobe Commerce Storefront](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/#quick-start) répertorie tous les événements déployés sur votre storefront. Toutefois, il existe dans cette liste un sous-ensemble d’événements spécifiques à Recommendations de produit. Ces événements collectent des données lorsque les acheteurs interagissent avec les unités de recommandations sur le storefront et optimisent les mesures utilisées pour vous aider à analyser les performances de vos recommandations.

| Événement | Description | [Utilisé pour les mesures ?](workspace.md) |
| --- | --- | --- |
| `impression-render` | L’unité de recommandation est générée sur la page. | Oui |
| `rec-add-to-cart-click` | Le client clique sur la variable **Ajouter au panier** pour un élément de l’entité de recommandation. | Oui, lorsqu’un **Ajouter au panier** est présent dans le modèle de recommandations. |
| `rec-click` | Le client clique sur un produit dans l’unité de recommandation. | Oui |
| `view` | L’unité de recommandation peut alors être consultée sur la page, par exemple en faisant défiler la page. | Oui |

Si votre vitrine est implémentée avec PWA Studio, reportez-vous à la section [Documentation du PWA](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). Si vous utilisez une technologie front-end personnalisée telle que React ou Vue JS, reportez-vous au guide d’utilisation pour découvrir comment intégrer Product Recommendations dans une [headless](headless.md) environnement.

## Avertissements

Les bloqueurs d’annonces publicitaires et les paramètres de confidentialité peuvent empêcher la variable `magento/product-recommendations` de capturer des événements et peut entraîner l’engagement et les recettes. [mesures](workspace.md) à être sous-estimées.

Le mode Eventing ne capture pas toutes les transactions qui se produisent sur le site du marchand. L&#39;évènement est destiné à donner au marchand une idée générale des événements qui se déroulent sur le site.

Les implémentations sans affichage doivent implémenter des événements pour alimenter le tableau de bord Recommendations du produit.

>[!NOTE]
>
>If [Mode de restriction des cookies](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) est activée, Adobe Commerce ne collecte les données comportementales que si l’acheteur a consenti à utiliser des cookies. Si le mode Restriction des cookies est désactivé, Adobe Commerce collecte les données comportementales par défaut.
