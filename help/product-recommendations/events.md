---
title: Collecter des données
description: Découvrez comment les événements collectent des données pour les recommandations de produits.
exl-id: b827d88c-327f-4986-8239-8f1921d8383c
feature: Services, Recommendations, Eventing
source-git-commit: cd1ce643d7c1ffeec8e9853cfc6ffc5519ce8f7a
workflow-type: tm+mt
source-wordcount: '1316'
ht-degree: 0%

---

# Collecter des données

Lorsque vous installez et configurez des fonctionnalités Adobe Commerce basées sur SaaS telles que [ Product Recommendations](install-configure.md) ou [Live Search](../live-search/install.md), les modules déploient la collecte de données comportementales sur votre vitrine. Ce mécanisme collecte des données comportementales anonymes auprès de vos acheteurs et alimente les recommandations de produits et les résultats de la [recherche en direct](../live-search/overview.md). Par exemple, l’événement `view` est utilisé pour calculer le type de recommandation `Viewed this, viewed that` et l’événement `place-order` est utilisé pour calculer le type de recommandation `Bought this, bought that`.

>[!NOTE]
>
>La collecte de données aux fins des recommandations de produits n’inclut pas d’informations d’identification personnelle (PII). Tous les identifiants d’utilisateur, tels que les identifiants de cookie et les adresses IP, sont strictement anonymisés. Découvrez [more](https://www.adobe.com/privacy/experience-cloud.html).

## Types et événements de données

Il existe deux types de données utilisés dans Product Recommendations :

- **Comportement** - Données provenant de l’engagement d’un acheteur sur votre site, telles que les consultations de produits, les articles ajoutés à un panier et les achats.
- **Catalogue** - Métadonnées de produit telles que le nom, le prix, la disponibilité, etc.

Lors de l’installation du module `magento/product-recommendations`, Adobe Sensei agrège les données comportementales et de catalogue, créant ainsi un Recommendations de produits pour chaque type de recommandation. Le service Recommendations de produit déploie ensuite ces recommandations sur votre storefront sous la forme d’un widget contenant les _éléments_ recommandés.

Certains types de recommandations utilisent les données comportementales de vos acheteurs pour former des modèles d’apprentissage automatique afin de créer des recommandations personnalisées. D’autres types de recommandations utilisent uniquement les données du catalogue et n’utilisent aucune donnée comportementale. Si vous souhaitez commencer rapidement à utiliser Product Recommendations sur votre site, vous pouvez utiliser les types de recommandations suivants, catalogue uniquement :

- `More like this`
- `Visual similarity`

### Démarrage à froid

Quand pouvez-vous commencer à utiliser des types de recommandations qui utilisent des données comportementales ? Ça dépend. On parle alors de problème _Cold Start_.

Le problème _Cold Start_ fait référence au temps nécessaire pour qu’un modèle s’entraîne et devienne efficace. Pour les recommandations de produits, cela signifie attendre qu’Adobe Sensei collecte suffisamment de données pour former ses modèles d’apprentissage automatique avant de déployer des unités de recommandation sur votre site. Plus les modèles contiennent de données, plus les recommandations sont précises et utiles. Comme la collecte des données se produit sur un site actif, il est préférable de démarrer ce processus tôt en installant et en configurant le module `magento/production-recommendations`.

Le tableau suivant fournit des instructions générales sur le temps nécessaire à la collecte de données suffisantes pour chaque type de recommandation :

| Type de recommandation | Heure de formation | Remarques |
|---|---|---|
| Basé sur la popularité (`Most viewed`, `Most purchased`, `Most added to cart`) | Variable | Dépend du volume des événements : les vues sont les plus courantes et l’apprentissage est donc plus rapide ; elles sont ensuite ajoutées au panier, puis les achats |
| `Viewed this, viewed that` | Nécessite une formation plus poussée | Le volume des consultations de produits est relativement élevé. |
| `Viewed this, bought that`, `Bought this, bought that` | Nécessite le plus de formation | Les événements d’achat sont les événements les plus rares d’un site de commerce, en particulier par rapport aux consultations de produits. |
| `Trending` | Nécessite trois jours de données pour établir une base de popularité | Les tendances sont une mesure de l’élan récent de popularité d’un produit par rapport à sa propre référence de popularité. Le score de tendance d’un produit est calculé à l’aide d’un jeu de premier plan (une popularité récente sur 24 heures) et d’un jeu d’arrière-plan (une ligne de base de popularité sur 72 heures). Si la popularité d’un élément augmente significativement au cours d’une période de 24 heures par rapport à sa popularité de base, il reçoit alors un score de tendance élevé. Chaque produit a ce score, et les éléments ayant le meilleur score à tout moment forment l’ensemble des produits les plus tendance. |

Autres variables pouvant avoir un impact sur le temps nécessaire à l’entraînement :

- Un volume de trafic plus élevé contribue à accélérer l’apprentissage
- Certains types de recommandations s’exécutent plus rapidement que d’autres.
- Adobe Commerce recalcule les données comportementales toutes les quatre heures. Recommendations devient plus précis plus longtemps il est utilisé sur votre site.

Pour vous aider à visualiser la progression de la formation de chaque type de recommandation, la page [créer une recommandation](create.md#readiness-indicators) affiche des indicateurs de préparation.

Pendant que les données sont collectées sur votre site actif et que les modèles d’apprentissage automatique sont en cours de formation, vous pouvez terminer d’autres tâches de test et de configuration nécessaires à la configuration des recommandations. Lorsque ce travail sera terminé, les modèles disposeront de suffisamment de données pour créer des recommandations utiles, ce qui vous permettra de les déployer sur votre vitrine.

Si votre site ne reçoit pas suffisamment de trafic (vues, achats, tendances) pour la plupart des SKU de produits, il se peut qu’il n’y ait pas assez de données pour terminer le processus d’apprentissage. Cela peut rendre l’indicateur de préparation dans l’Admin bloqué. Les indicateurs de préparation sont destinés à fournir aux commerçants un autre point de données pour choisir le type de recommandations qui convient le mieux à leur magasin. Les chiffres sont un guide et peuvent ne jamais atteindre 100 %. [En savoir plus](create.md#readiness-indicators) sur les indicateurs de préparation.

### Recommandations de sauvegarde {#backuprecs}

Si les données d’entrée ne suffisent pas à fournir tous les éléments de recommandation demandés dans une unité, Adobe Commerce fournit des recommandations de sauvegarde pour remplir les unités de recommandation. Par exemple, si vous déployez le type de recommandation `Recommended for you` sur votre page d’accueil, un nouvel acheteur de votre site n’a pas généré suffisamment de données comportementales pour recommander avec précision des produits personnalisés. Dans ce cas, Adobe Commerce affiche des éléments en fonction du type de recommandation `Most viewed` pour cet acheteur.

Dans le cas d’une collecte de données d’entrée insuffisante, les types de recommandations suivants reviennent au type de recommandation `Most viewed` :

- `Recommended for you`
- `Viewed this, viewed that`
- `Viewed this, bought that`
- `Bought this, bought that`
- `Trending`
- `Conversion (view to purchase)`
- `Conversion (view to cart)`

### Événements

Le [collecteur d’événements Adobe Commerce Storefront](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/#quick-start) répertorie tous les événements déployés sur votre storefront. Toutefois, il existe dans cette liste un sous-ensemble d’événements spécifiques à Recommendations de produit. Ces événements collectent des données lorsque les acheteurs interagissent avec les unités de recommandations sur le storefront et optimisent les mesures utilisées pour vous aider à analyser les performances de vos recommandations.

| Événement | Description |
| --- | --- |
| `impression-render` | Envoyé lorsque l’unité de recommandation est générée sur la page. Si une page comporte deux unités de recommandation (achat-achat, affichage-affichage), deux événements `impression-render` sont envoyés. Cet événement est utilisé pour effectuer le suivi de la mesure pour les impressions. |
| `rec-add-to-cart-click` | L’acheteur clique sur le bouton **Ajouter au panier** pour un article de l’unité de recommandation. |
| `rec-click` | L’acheteur clique sur un produit dans l’unité de recommandation. |
| `view` | Envoyé lorsque l’unité de recommandation devient visible à au moins 50 %, par exemple en faisant défiler la page vers le bas. Par exemple, si une unité de recommandation comporte deux lignes, un événement `view` est envoyé lorsqu’une ligne plus un pixel de la seconde ligne devient visible pour l’acheteur. Si l’acheteur fait défiler plusieurs fois la page vers le haut ou vers le bas, l’événement `view` est envoyé autant de fois que l’acheteur voit à nouveau l’entité de recommandation entière sur la page. |

>[!NOTE]
>
>Les mesures de recommandation de produit sont optimisées pour les vitrines Luma. Si votre vitrine est implémentée avec PWA Studio, reportez-vous à la [documentation du PWA](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). Si vous utilisez une technologie front-end personnalisée telle que React ou Vue JS, apprenez à intégrer [Product Recommendations dans un environnement sans interface](headless.md).

#### Événements de tableau de bord obligatoires

Les événements suivants sont nécessaires pour remplir le [[!DNL Product Recommendations] tableau de bord](workspace.md)

| Colonne du tableau de bord | Événements | Champ de jointure |
| ---------------- | --------- | ----------- |
| Impressions | `page-view`, `recs-request-sent`, `recs-response-received`, `recs-unit-render` | `unitId` |
| Vues | `page-view`, `recs-request-sent`, `recs-response-received`, `recs-unit-render`, `recs-unit-view` | `unitId` |
| Clics | `page-view`, `recs-request-sent`, `recs-response-received`, `recs-item-click`, `recs-add-to-cart-click` | `unitId` |
| Recettes | `page-view`, `recs-request-sent`, `recs-response-received`, `recs-item-click`, `recs-add-to-cart-click`, `place-order` | `unitId`, `sku`, `parentSku` |
| Recettes LT | `page-view`, `recs-request-sent`, `recs-response-received`, `recs-item-click`, `recs-add-to-cart-click`, `place-order` | `unitId`, `sku`, `parentSku` |
| CTR | `page-view`, `recs-request-sent`, `recs-response-received`, `recs-unit-render`, `recs-item-click`, `recs-add-to-cart-click` | `unitId`, `sku`, `parentSku` |
| vCTR | `page-view`, `recs-request-sent`, `recs-response-received`, `recs-unit-render`, `recs-unit-view`, `recs-item-click`, `recs-add-to-cart-click` | `unitId`, `sku`, `parentSku` |

Les événements suivants ne sont pas spécifiques à Product Recommendations, mais sont nécessaires pour qu’Adobe Sensei interprète correctement les données des acheteurs :

- `view`
- `add-to-cart`
- `place-order`

#### Type de recommandation

Ce tableau décrit les événements utilisés par chaque type de recommandation.

| Type de recommandation | Événements | Page |
| --- | --- | --- |
| Les plus consultés | `page-view`<br>`product-view` | Page Détails du produit |
| Le plus acheté | `page-view`<br>`complete-checkout` | Panier/passage en caisse |
| Les plus ajoutés au panier | `page-view`<br>`add-to-cart` | Page Détails du produit<br>Page Liste des produits<br>Panier<br>Liste des souhaits |
| A consulté ceci, consulté cela | `page-view`<br>`product-view` | Page Détails du produit |
| Consulté ceci, acheté cela | Recs de produit | `page-view`<br>`product-view` | Page Détails du produit<br>Panier/Passage en caisse |
| Acheté ceci, acheté cela | Recs de produit | `page-view`<br>`product-view` | Page Détails du produit |
| Tendance | `page-view`<br>`product-view` | Page Détails du produit |
| Conversion : Afficher à l’achat | Recs de produit | `page-view`<br>`product-view` | Page Détails du produit |
| Conversion : Afficher à l’achat | Recs de produit | `page-view`<br>`complete-checkout` | Panier/passage en caisse |
| Conversion : Afficher dans le panier | Recs de produit | `page-view`<br>`product-view` | Page Détails du produit |
| Conversion : Afficher dans le panier | Recs de produit | `page-view`<br>`add-to-cart` | Page Détails du produit<br>Page Liste des produits<br>Panier<br>Liste des produits |

#### Avertissements

- Les bloqueurs d’annonces publicitaires et les paramètres de confidentialité peuvent empêcher la capture d’événements et peuvent entraîner un sous-rapport de l’engagement et des [mesures](workspace.md#column-descriptions). De plus, certains événements peuvent ne pas être envoyés en raison de problèmes de réseaux ou de pages laissés par les acheteurs.
- [Les implémentations sans affichage](headless.md) doivent implémenter des événements pour alimenter le tableau de bord Recommendations du produit.
- Pour les produits configurables, le Recommendations de produit utilise l’image du produit parent dans l’unité de recommandation. Si aucune image n’est spécifiée pour le produit configurable, l’unité de recommandation sera vide pour ce produit spécifique.

>[!NOTE]
>
>Si le [mode de restriction des cookies](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) est activé, Adobe Commerce ne collecte pas de données comportementales tant que l’acheteur n’a pas consenti à utiliser des cookies. Si le mode Restriction des cookies est désactivé, Adobe Commerce collecte les données comportementales par défaut.
