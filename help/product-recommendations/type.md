---
title: Types de recommandations
description: Découvrez les recommandations à déployer sur différentes pages de votre site.
exl-id: c3b16307-479b-4736-968b-b6ab38233a48
source-git-commit: 42cb709f4699fcdd56df7ca02466ab416f01cab2
workflow-type: tm+mt
source-wordcount: '1575'
ht-degree: 0%

---

# Types de recommandations

Adobe Commerce fournit un vaste ensemble de recommandations que vous pouvez déployer sur différentes pages de votre site. Tous les types de recommandations dépendent des données. Elles sont alimentées par des données comportementales, des données d’attributs de produit et des mesures. À titre de référence simple, les types de recommandations sont regroupés comme suit :

- [Personnalisé](#personalized)
- [Ventes croisées et ventes incitatives](#crossup)
- [Popularité](#popularity)
- [Très performant](#highperf)

En règle générale, Adobe recommande les directives suivantes lorsque vous utilisez des recommandations :

- Vous pouvez diversifier vos types de recommandations. Les clients commencent à ignorer les recommandations s’ils suggèrent les mêmes produits encore et encore.

- Ne déployez pas les mêmes recommandations sur la page de votre panier et la page de confirmation de commande. Envisager d’utiliser `Most Added to Cart` pour la page panier et `Bought This, Bought That` pour la page de confirmation de commande.

- Maintenez votre site en ordre. Ne déployez pas plus de trois unités de recommandations sur la même page.

- Si votre boutique vend des vêtements, la variable `More like this` La recommandation peut suggérer des produits spécifiques au genre qui ne correspondent pas au genre du produit consulté. Envisagez d’utiliser ce type de recommandation uniquement pour les catégories autres que vêtements.

## Personnalisé {#personalized}

Ces types de recommandations recommandent des produits en fonction de l’historique comportemental spécifique de l’acheteur sur votre site.

| Type | Description |
|---|---|
| Recommandé pour vous | Recommande des produits en fonction du comportement actuel et précédent de chaque client sur site. Présente des recommandations hautement pertinentes en fonction de l’historique de navigation et d’achat de l’acheteur. Ce type de recommandation est effectif sur la page d’accueil où la plupart des acheteurs commencent leur parcours sur un site. Pour les nouveaux acheteurs de votre site qui n’ont généré aucun signal pour personnaliser leur expérience, Adobe Commerce affiche des produits en fonction du type de recommandation Le plus consulté. Cependant, lorsque l’acheteur commence à interagir avec les produits sur le site, les produits recommandés s’adaptent en temps réel à leur comportement.<br/><br/>**En cas d’utilisation :**<br/>- Page d’accueil<br/>- Catégorie <br/><br/>**Étiquettes proposées :**<br/> - Juste pour vous<br/>- Recommandé pour vous<br/>- Inspiré par vos tendances d’achat |
| Récemment consultés | Affiche les produits les plus récemment consultés par l’acheteur, en fonction de l’historique de son navigateur. Tous les produits supprimés sont supprimés par l’unité de recommandation. L’unité de recommandation n’est pas affichée s’il n’existe aucun historique de navigateur ou si les règles de filtrage sont appliquées de manière insuffisante. Si les résultats contiennent moins de produits que ceux configurés, l’unité de recommandation affiche uniquement les produits renvoyés.<br/><br/>**En cas d’utilisation :**<br/>- Page d’accueil<br/>- Catégorie<br/>- Détails du produit<br/>- Panier<br/>- Confirmation <br/><br/>**Étiquettes proposées :**<br/>- Récemment consultés<br/>- Reprendre un autre aspect |

## Ventes croisées et ventes incitatives {#crossup}

Ces types de recommandations sont à l’épreuve des réseaux sociaux afin d’aider les acheteurs à trouver ce que les autres aiment ou ce qu’ils aiment pour les aider à trouver d’autres produits similaires.

| Type | Description |
|---|---|
| A consulté ceci, consulté cela | Recommande les produits que les acheteurs consultent de manière disproportionnée plus souvent avec le produit actuellement consulté.<br/><br/>**En cas d’utilisation :**<br/>- Détails du produit<br/>- Panier<br/>- Confirmation <br/><br/>**Étiquettes proposées :**<br/>- Les clients qui ont consulté ce produit ont également consulté (PDP) |
| Consulté ceci, acheté cela | Recommande les produits que les acheteurs tendent à acheter de manière disproportionnée plus souvent après avoir consulté le produit actuel. Permet de guider les acheteurs vers la découverte de produits qu’ils n’auraient pas remarqués autrement.<br/><br/>**En cas d’utilisation :**<br/>- Détails du produit<br/>- Panier<br/>- Confirmation <br/><br/>**Étiquettes proposées :**<br/>- Clients ayant consulté cet achat ultime<br/>- Clients achetés en fin de compte<br/>- Que les autres achètent après avoir consulté ce produit ? |
| Acheté ceci, acheté cela | Recommande les produits que les acheteurs achètent de manière disproportionnée plus souvent avec le produit actuellement consulté. Le plus souvent utilisé sur le panier ou la page des détails du produit pour augmenter l’exposition du produit de vente croisée associé afin d’augmenter la valeur moyenne de la commande. Présente les produits hautement pertinents que les acheteurs peuvent ajouter à leur panier en agrégeant ce que d’autres acheteurs ont acheté avec le produit actuel.<br/><br/>**En cas d’utilisation :**<br/>- Détails du produit<br/>- Panier<br/>- Confirmation <br/><br/>**Étiquettes proposées :**<br/>- Obtenir tout ce dont vous avez besoin<br/>- N&#39;oubliez pas ceux-ci<br/>- Fréquemment achetés ensemble |
| Plus comme suit | Recommande des produits basés sur des métadonnées similaires telles que le nom, la description, l’attribution de catégories et les attributs. En évaluant les attributs des produits consultés, recommande des produits similaires dans la même catégorie. Par exemple, si un acheteur navigue sur des matelas de yoga, d’autres produits de la catégorie équipement sont recommandés. Comme ce type de recommandation ne fait pas la distinction entre les sexes, il n’est pas recommandé pour les vêtements, la mode ou d’autres secteurs verticaux spécifiques au genre.<br/><br/>**En cas d’utilisation :**<br/>- Détails du produit<br/>- Panier<br/>- Confirmation <br/><br/>**Étiquettes proposées :**<br/> - Plus de produits comme celui-ci<br/>- Similaire à ceci |
| [similarité visuelle](#visualsim) | Recommande des produits à l’apparence similaire au produit consulté. Ce type de recommandation est plus utile si les images et les aspects visuels des produits sont importants pour l’expérience d’achat. |

## Popularité {#popularity}

Ces types de recommandations recommandent les produits les plus populaires ou les plus tendance des sept derniers jours.

| Type | Description |
|---|---|
| Le plus consulté | Recommande les produits les plus consultés en comptant le nombre de sessions au cours desquelles une action d’affichage a eu lieu au cours des sept derniers jours.<br/><br/>**En cas d’utilisation :**<br/>- Page d’accueil<br/>- Catégorie<br/>- Détails du produit<br/>- Panier<br/>- Confirmation <br/><br/>**Étiquettes proposées :**<br/>- Le plus populaire<br/>- Trending<br/>- Populaire en ce moment<br/>- Récemment populaires<br/>- Produits populaires inspirés par ce produit (PDP)<br/>- Meilleurs vendeurs |
| Le plus acheté | Recommande les produits achetés le plus souvent par les acheteurs au cours des sept derniers jours.<br/><br/>**En cas d’utilisation :**<br/>- Page d’accueil<br/>- Catégorie<br/>- Détails du produit<br/>- Panier<br/>- Confirmation <br/><br/>**Étiquettes proposées :**<br/> - Le plus populaire<br/>- Trending<br/>- Populaire en ce moment<br/>- Récemment populaires<br/>- Produits populaires inspirés par ce produit (PDP)<br/>- Meilleurs vendeurs |
| Les plus ajoutés au panier | Recommande les produits les plus fréquemment ajoutés au panier par les acheteurs au cours des sept derniers jours. Ce type de recommandation peut être utilisé sur toutes les pages.<br/><br/>**En cas d’utilisation :**<br/>- Page d’accueil<br/>- Catégorie<br/>- Détails du produit<br/>- Panier<br/>- Confirmation <br/><br/>**Étiquettes proposées :**<br/> - Le plus populaire<br/>- Trending<br/>- Populaire en ce moment<br/>- Récemment populaires<br/>- Produits populaires inspirés par ce produit (PDP)<br/>- Meilleurs vendeurs |
| Tendance | Recommande des produits en fonction de l’élan récent de popularité d’un produit sur votre site.<br/><br/>Adobe Sensei agrège les données de navigation et d’achat sur votre site afin de déterminer et de classer les produits les plus récemment populaires auprès de vos acheteurs. Comme Trending analyse l’élan récent du produit, il s’agit d’un type de recommandation efficace pour les catalogues dont le chiffre d’affaires est élevé. Si votre catalogue est plus statique, il peut ne pas être aussi utile, à moins que les modèles d’achat de votre audience soient très variables.<br/><br/>Lorsqu’il est utilisé sur la page d’accueil, Trending recommande des produits récemment populaires sur l’ensemble du site. Les tendances n’affichent pas les produits qui sont constamment populaires, mais plutôt ceux qui sont récemment devenus populaires. Si, par exemple, vous avez une campagne de marketing par e-mail faisant la promotion de certains produits, l’augmentation de popularité générée par le e-mail augmente la probabilité que les produits promus soient classés en tendance.<br/><br/>**En cas d’utilisation :**<br/>- Page d’accueil<br/>- Catégorie<br/>- Détails du produit<br/>- Panier<br/>- Confirmation <br/><br/>**Étiquettes proposées :**<br/>- Trending<br/>- Tendance maintenant<br/>- Dernières tendances<br/>- Produits chauds<br/>- Trending related products (PDP) |

## Élevé {#highperf}

Ces types de recommandations recommandent les produits les plus performants en fonction de critères de réussite tels que les taux de conversion ou de ajouts au panier.

| Type | Description |
|---|---|
| Afficher la conversion d’achat | Recommande les produits présentant le taux de conversion d’achat le plus élevé. De toutes les sessions d’acheteurs qui ont enregistré une consultation de produit, quelle est la proportion qui a finalement enregistré un achat par l’acheteur.<br/><br/>**En cas d’utilisation :**<br/>- Page d’accueil<br/>- Catégorie<br/>- Détails du produit<br/>- Panier<br/>- Confirmation <br/><br/>**Étiquettes proposées :**<br/> -Meilleurs vendeurs<br/>- Produits populaires<br/>- Il se peut que vous soyez intéressé par |
| Conversion de l’affichage dans le panier | Recommande les produits présentant le taux de conversion d’affichage au panier le plus élevé. De toutes les sessions d’acheteurs qui ont enregistré une consultation de produit, quelle est la proportion qui a finalement enregistré un ajout au panier par l’acheteur.<br/><br/>**En cas d’utilisation :**<br/>- Page d’accueil<br/>- Catégorie<br/>- Détails du produit<br/>- Panier<br/>- Confirmation <br/><br/>**Étiquettes proposées :**<br/> - Meilleurs vendeurs<br/>- Produits populaires<br/>- Il se peut que vous soyez intéressé par |
| Le plus acheté | Souvent appelé &quot;Meilleurs vendeurs&quot;, ce type de recommandation comptabilise le nombre de sessions au cours desquelles une action de commande a eu lieu au cours des sept derniers jours. Ce type de recommandation peut être utilisé sur toutes les pages.<br/><br/>**En cas d’utilisation :**<br/>- Page d’accueil<br/>- Catégorie<br/>- Détails du produit<br/>- Panier<br/>- Confirmation <br/><br/>**Étiquettes proposées :**<br/> - Le plus populaire<br/>- Trending<br/>- Populaire en ce moment<br/>- Récemment populaires<br/>- Produits populaires inspirés par ce produit (PDP)<br/>- Meilleurs vendeurs |
| Les plus ajoutés au panier | Recommande les produits les plus fréquemment ajoutés au panier par les acheteurs au cours des sept derniers jours. Ce type de recommandation peut être utilisé sur toutes les pages.<br/><br/>**En cas d’utilisation :**<br/>- Page d’accueil<br/>- Catégorie<br/>- Détails du produit<br/>- Panier<br/>- Confirmation <br/><br/>**Étiquettes proposées :**<br/> - Le plus populaire<br/>- Trending<br/>- Populaire en ce moment<br/>- Récemment populaires<br/>- Produits populaires inspirés par ce produit (PDP)<br/>- Meilleurs vendeurs |

## similarité visuelle {#visualsim}

La variable _similarité visuelle_ le type de recommandation recommande des produits à l’aspect similaire au produit consulté. Ce type de recommandation est particulièrement utile lorsque les images et les aspects visuels des produits sont des éléments importants de l’expérience d’achat.

### Fonctionnement

La variable _similarité visuelle_ type de recommandation offre des recommandations pour d’autres produits de votre catalogue présentant une similarité visuelle avec l’imagerie actuellement consultée. La similarité visuelle comprend des aspects tels que :

- Couleur
- Forme
- Taille
- Texture
- Matériau
- Style

Adobe Sensei utilise l’IA pour traiter et analyser les images de votre catalogue et créer les attributs utilisés pour déterminer les similarités visuelles.

>[!NOTE]
>
> Si vous testez ce type de recommandation dans un environnement hors production, assurez-vous que vos URL d’image sont accessibles au public.

>[!NOTE]
>
> Actuellement, la taille des images du produit doit être inférieure ou égale à 10 Mo.

Ce type de recommandation n’étant pas applicable à la plupart des catalogues, il n’est pas activé par défaut. Vous devez activer explicitement ce type de recommandation.

### Activation du type de recommandation similarité visuelle

>[!NOTE]
>
> La variable _similarité visuelle_ le type de recommandation est disponible lorsque [install](install-configure.md) en tant que module optionnel.

1. Sur le _Administration_ barre latérale, accédez à **Marketing** > _Promotions_ > **Recommendations de produit** pour afficher la variable _Recommendations de produit_ tableau de bord.

1. Cliquez sur **Paramètres** (icône représentant un engrenage) pour afficher la variable _Paramètres_ page.

1. Dans le _Visual Recommendations_ , sélectionnez **Activer Visual Recommendations**.

1. Cliquez sur **Enregistrer les modifications** lorsque vous avez terminé.

   La variable [Créer une recommandation](create.md) page désormais affichée **similarité visuelle** comme type de recommandation sélectionnable lorsque le type de page est **Détails du produit**.

Une fois les recommandations visuelles activées, Adobe Sensei lance le traitement des images. Le temps nécessaire dépend de la taille de votre catalogue.

### Où utilisé

- Détails du produit

### Étiquettes de vitrine proposées

- Vous pouvez également
- Nous avons trouvé d’autres produits que vous pourriez aimer.
- Inspiré par ce style

### Exemple

L’image suivante montre la page des détails du produit pour la variable _Clamer Watch_:

![Clamer Watch](assets/visual-sim-pdp.png)

Le tableau suivant présente la variable _similarité visuelle_ unité de recommandation pour _Clamer Watch_:

![Unité de similarité visuelle](assets/visual-sim-unit.png)
