---
title: Workflow de mise en oeuvre
description: Découvrez les étapes à suivre pour implémenter avec succès [!DNL Product Recommendations] sur votre vitrine.
source-git-commit: 4ad607c8595b25d01b5f5020b787fc1d35d4df25
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 0%

---

# Workflow de mise en oeuvre

[!DNL Product Recommendations] utilise les données comportementales et catalogues :

- Comportement : données provenant de l’engagement d’un acheteur sur votre site, telles que les consultations de produits, les articles ajoutés à un panier et les achats. Adobe Commerce et Adobe Sensei ne collectent pas d’informations d’identification personnelle.

- Catalogue : métadonnées de produit, telles que le nom, le prix et la disponibilité.

Lorsque vous installez le `magento/product-recommendations module`, Adobe Sensei agrège les données comportementales et de catalogue et crée [!DNL Product Recommendations] pour chaque type de recommandation. Le [!DNL Product Recommendations] le service déploie ensuite ces recommandations sur votre storefront. Pour vous aider à mettre en oeuvre des recommandations de produits sur votre vitrine, utilisez le workflow suivant :

>[!NOTE]
>
> Si votre vitrine est implémentée à l’aide de PWA Studio, reportez-vous à la section [Documentation du PWA](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). Si vous utilisez une technologie front-end personnalisée telle que React ou Vue JS, découvrez comment [intégrer](headless.md) [!DNL Product Recommendations] dans votre vitrine sans tête.

## Workflow

1. **Déploiement de la collecte de données en production**

   Déploiement [!DNL Product Recommendations] requiert deux éléments principaux [sources de données](type.md): catalogue et comportement. La production étant le seul environnement dans lequel les actions de vos acheteurs sont capturées et analysées, il est dans votre intérêt de commencer dès que possible la collecte de données en production. [En savoir plus](behavioral-data.md) la manière dont Adobe Sensei entraîne des modèles d’apprentissage automatique qui génèrent des recommandations de meilleure qualité. En outre, lorsque vous commencez à collecter des données comportementales sur la production, vous pouvez [récupérer les recommandations](verify.md) sur la base de ces données de production lors de l’exploitation dans des environnements hors production. Vous pouvez ensuite tester et tester différentes recommandations calculées à partir de données réelles d’acheteurs collectées en production.

   Pour déployer la collecte de données en production, vous devez [installation et configuration](install-configure.md) la valeur [!DNL Product Recommendations] en fournissant un module [Clé API](https://docs.magento.com/user-guide/system/saas.html#apikey).

   >[!TIP]
   >
   > Le déploiement de la collecte de données ne modifie pas l’aspect de votre vitrine ni l’expérience de vos acheteurs. Seule la création et le déploiement d’unités de recommandation modifient l’expérience client sur votre storefront. Assurez-vous de tester votre environnement hors production avant de procéder au déploiement en production. De plus, ne créez pas d’unités de recommandations tant que vous n’avez pas personnalisé votre modèle. Voir l’étape suivante.

1. **Personnaliser le modèle pour qu’il corresponde à votre style**

   Votre vitrine représente votre marque. Veillez donc à modifier le modèle de recommandations de produits pour qu’il corresponde au thème de votre site.

   >[!TIP]
   >
   > En personnalisant le modèle, vous pouvez spécifier votre feuille de style, remplacer l’emplacement d’affichage d’une unité de recommandation sur une page, etc.

   Voir [Personnaliser](https://devdocs.magento.com/recommendations/customize.html) dans la documentation destinée aux développeurs pour savoir comment effectuer cette étape.

1. **Test de recommandations sur votre environnement hors production**

   Il est toujours recommandé de tester une nouvelle technologie dans votre environnement hors production avant de la déployer en production. Les recommandations de test sur votre environnement hors production vous permettent de lire avec différents types d’unités de recommandation, de positionnement et de pages. Vous pouvez extraire des recommandations basées sur des données comportementales déjà collectées en production lors du test dans votre environnement hors production, de sorte que les résultats des recommandations soient basés sur le comportement d’achat des clients réels.

   >[!TIP]
   >
   > Assurez-vous que votre catalogue d’environnement hors production est largement identique à celui que vous avez en production. L’utilisation de catalogues similaires permet de s’assurer que les produits renvoyés dans les unités de recommandation ressemblent étroitement aux produits en production.

   Voir [Récupérer](staging-environment.md) données comportementales de votre environnement de production pour savoir comment terminer cette étape.

1. **Créer et déployer des recommandations sur votre vitrine de production**

   Maintenant que vous avez déployé la collecte de données comportementales en production, modifié le modèle de recommandations de produits et testé les recommandations à l’aide du comportement d’achat réel, vous êtes prêt à convertir tout le code en production et [create](create.md) recommandations de produits en direct.
