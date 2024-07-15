---
title: Données comportementales
description: Découvrez les données comportementales et quand vous pouvez commencer à les utiliser.
exl-id: d68a97b9-1497-4603-a72c-4aaaf6e048cb
source-git-commit: 840b091638aedd3f6ac097a010d035eff997ffe2
workflow-type: tm+mt
source-wordcount: '647'
ht-degree: 0%

---

# Données comportementales

Certains types de recommandations utilisent les données comportementales de vos acheteurs pour former des modèles d’apprentissage automatique afin de créer des recommandations personnalisées. D’autres types de recommandations utilisent uniquement les données du catalogue et n’utilisent aucune donnée comportementale. Si vous souhaitez démarrer rapidement, vous pouvez utiliser les types de recommandations suivants, catalogue uniquement :

- `More like this`
- `Visual similarity`

Dans ces conditions, quand commencer à utiliser des types de recommandations qui utilisent des données comportementales ? Ça dépend. On parle alors de problème _Cold Start_.

Le problème _Cold Start_ mesure le temps nécessaire à l’entraînement d’un modèle avant qu’il puisse être considéré comme de haute qualité. Dans les recommandations de produits, cela se traduit par l’attente d’Adobe Sensei pour entraîner ses modèles d’apprentissage automatique avant de déployer des unités de recommandation sur votre site. Plus ces modèles contiennent de données, plus les recommandations sont précises et utiles. La collecte de ces données prend du temps et varie en fonction du volume de trafic. Ces données ne pouvant être collectées que sur un site de production, il est dans votre intérêt de déployer la collecte de données dès que possible sur ce site. Pour ce faire, [installez et configurez](install-configure.md) le module `magento/production-recommendations`.

Le tableau suivant fournit des instructions générales sur le temps nécessaire à la collecte de données suffisantes pour chaque type de recommandation :

| Type de recommandation | Heure de formation | Remarques |
|---|---|---|
| Basé sur la popularité (`Most viewed`, `Most purchased`, `Most added to cart`) | Variable | Dépend du volume des événements : les vues sont les plus courantes et l’apprentissage est donc plus rapide ; elles sont ensuite ajoutées au panier, puis les achats |
| `Viewed this, viewed that` | Nécessite une formation plus poussée | Le volume des consultations de produits est relativement élevé. |
| `Viewed this, bought that`, `Bought this, bought that` | Nécessite le plus de formation | Les événements d’achat sont les événements les plus rares sur le site de commerce, en particulier par rapport aux consultations de produits. |
| `Trending` | Nécessite trois jours de données pour établir une base de popularité | Les tendances sont une mesure de l’élan récent de popularité d’un produit par rapport à sa propre référence de popularité. Le score de tendance d’un produit est calculé à l’aide d’un jeu de premier plan (une popularité récente sur 24 heures) et d’un jeu d’arrière-plan (une ligne de base de popularité sur 72 heures). Si un élément est devenu beaucoup plus populaire au cours des dernières 24 heures par rapport à sa popularité de base, il reçoit alors un score de tendance élevé. Chaque produit a ce score, et les plus élevés à tout moment forment l’ensemble des produits les plus tendance. |

Autres variables pouvant avoir un impact sur le temps nécessaire à l’entraînement :

- Un volume de trafic plus élevé contribue à accélérer l’apprentissage
- Certains types de recommandations s’exécutent plus rapidement que d’autres.
- Adobe Commerce recalcule les données comportementales toutes les quatre heures. Recommendations devient plus précis plus longtemps il est utilisé sur votre site.

Pour vous aider à visualiser la progression de la formation de chaque type de recommandation, la page [créer une recommandation](create.md) affiche des indicateurs de préparation.

Bien que les données soient collectées sur les modèles de production et d’apprentissage automatique, vous pouvez implémenter les [tâches restantes](implementation-workflow.md) nécessaires pour déployer des recommandations sur votre vitrine. Lorsque vous avez terminé les tests et la configuration des recommandations, les modèles d’apprentissage automatique ont collecté et calculé suffisamment de données pour créer des recommandations pertinentes, ce qui vous permet de déployer les recommandations sur votre vitrine.

S’il y a un trafic insuffisant (vues, produits achetés, tendance) pour la majorité des SKU, il se peut qu’il n’y ait pas assez de données pour terminer le processus d’apprentissage. Cela peut donner l’impression que l’indicateur de préparation dans l’administrateur était bloqué.
Les indicateurs de préparation sont destinés à fournir aux commerçants un autre point de données pour choisir le type de recommandations qui convient le mieux à leur magasin. Les chiffres sont un guide et peuvent ne jamais atteindre 100 %.

## Recommandations de sauvegarde {#backuprecs}

S’il n’existe pas de données d’entrée suffisantes pour fournir tous les éléments de recommandation demandés dans une unité, Adobe Commerce fournit des recommandations de sauvegarde pour remplir les unités de recommandation. Par exemple, si vous déployez le type de recommandation `Recommended for you` sur votre page d’accueil, un nouvel acheteur de votre site n’a pas généré suffisamment de données comportementales pour recommander avec précision des produits personnalisés. Dans ce cas, Adobe Commerce affiche des éléments en fonction du type de recommandation `Most viewed` pour cet acheteur.

Les types de recommandations suivants reviennent au type de recommandation `Most viewed` s’il n’y a pas suffisamment de données d’entrée collectées :

- `Recommended for you`
- `Viewed this, viewed that`
- `Viewed this, bought that`
- `Bought this, bought that`
- `Trending`
- `Conversion (view to purchase)`
- `Conversion (view to cart)`
