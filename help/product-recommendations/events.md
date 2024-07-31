---
title: Collecter des données
description: Découvrez comment les événements collectent des données pour les recommandations de produits.
exl-id: b827d88c-327f-4986-8239-8f1921d8383c
feature: Services, Recommendations, Eventing
source-git-commit: 67296ea42bfddb10b0c86cb1ca47324f5fec7825
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%

---

# Collecter des données

Lorsque vous installez et configurez des fonctionnalités Adobe Commerce basées sur SaaS telles que [ Product Recommendations](install-configure.md) ou [Live Search](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html), les modules déploient la collecte de données comportementales sur votre vitrine. Ce mécanisme collecte des données comportementales anonymes auprès de vos acheteurs et alimente les recommandations de produits. Par exemple, l’événement `view` est utilisé pour calculer le type de recommandation `Viewed this, viewed that` et l’événement `place-order` est utilisé pour calculer le type de recommandation `Bought this, bought that`.

>[!NOTE]
>
>La collecte de données aux fins des recommandations de produits n’inclut pas d’informations d’identification personnelle (PII). Tous les identifiants d’utilisateur, tels que les identifiants de cookie et les adresses IP, sont strictement anonymisés. Découvrez [more](https://www.adobe.com/privacy/experience-cloud.html).

Les événements suivants ne sont pas spécifiques à Product Recommendations, mais sont nécessaires pour renvoyer des résultats :

- `view`
- `add-to-cart`
- `place-order`

Le [collecteur d’événements Adobe Commerce Storefront](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/#quick-start) répertorie tous les événements déployés sur votre storefront. Toutefois, il existe dans cette liste un sous-ensemble d’événements spécifiques à Recommendations de produit. Ces événements collectent des données lorsque les acheteurs interagissent avec les unités de recommandations sur le storefront et optimisent les mesures utilisées pour vous aider à analyser les performances de vos recommandations.

| Événement | Description | Utilisé pour les mesures ? |
| --- | --- | --- |
| `impression-render` | L’unité de recommandation est générée sur la page. | Oui |
| `rec-add-to-cart-click` | Le client clique sur le bouton **Ajouter au panier** pour un article de l’unité de recommandation. | Oui, lorsqu’un bouton **Ajouter au panier** est présent dans le modèle de recommandations. |
| `rec-click` | Le client clique sur un produit dans l’unité de recommandation. | Oui |
| `view` | L’unité de recommandation peut alors être consultée sur la page, par exemple en faisant défiler la page. | Oui |

Les événements suivants sont requis pour remplir correctement le tableau de bord.

| Colonne du tableau de bord | Événements | Champ de jointure |
| ---------------- | --------- | ----------- |
| Impressions | `page-view`, `recs-request-sent`, `recs-response-received`, `recs-unit-render` | unitId |
| Vues | `page-view`, `recs-request-sent`, `recs-response-received`, `recs-unit-render`, `recs-unit-view` | unitId |
| Clics | `page-view`, `recs-request-sent`, `recs-response-received`, `recs-item-click`, `recs-add-to-cart-click` | unitId |
| Recettes | `page-view`, `recs-request-sent`, `recs-response-received`, `recs-item-click`, `recs-add-to-cart-click`, `place-order` | unitId, sku |
| Recettes LT | `page-view`, `recs-request-sent`, `recs-response-received`, `recs-item-click`, `recs-add-to-cart-click`, `place-order` | unitId, sku |
| CTR | `page-view`, `recs-request-sent`, `recs-response-received`, `recs-unit-render`, `recs-item-click`, `recs-add-to-cart-click` | unitId, sku |
| vCTR | `page-view`, `recs-request-sent`, `recs-response-received`, `recs-unit-render`, `recs-unit-view`, `recs-item-click`, `recs-add-to-cart-click` | unitId, sku |

Si votre vitrine est implémentée avec PWA Studio, reportez-vous à la [documentation du PWA](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). Si vous utilisez une technologie front-end personnalisée telle que React ou Vue JS, reportez-vous au guide d’utilisation pour découvrir comment intégrer [Product Recommendations dans un environnement sans interface](headless.md).

## Avertissements

Les bloqueurs d’annonces publicitaires et les paramètres de confidentialité peuvent empêcher le module `magento/product-recommendations` de capturer des événements et peuvent entraîner une sous-évaluation de l’engagement et des [mesures](workspace.md).

Le mode Eventing ne capture pas toutes les transactions qui se produisent sur le site du marchand. L&#39;évènement est destiné à donner au marchand une idée générale des événements qui se déroulent sur le site.

Les implémentations sans affichage doivent implémenter des événements pour alimenter le tableau de bord Recommendations du produit.

>[!NOTE]
>
>Si le [mode de restriction des cookies](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) est activé, Adobe Commerce ne collecte pas de données comportementales tant que l’acheteur n’a pas consenti à utiliser des cookies. Si le mode Restriction des cookies est désactivé, Adobe Commerce collecte les données comportementales par défaut.
