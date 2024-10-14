---
title: Workflow de mise en oeuvre
description: Découvrez les étapes pour implémenter  [!DNL Product Recommendations] avec succès sur votre storefront.
exl-id: 766e1191-0330-4515-9331-e45318539dc9
source-git-commit: 91e19e30d55259d3287404895d1d893c480743b6
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 0%

---

# Workflow de mise en oeuvre

[!DNL Product Recommendations] utilise les données comportementales et catalogues :

- Comportement : données provenant de l’engagement d’un acheteur sur votre site, telles que les consultations de produits, les articles ajoutés à un panier et les achats. Adobe Commerce et Adobe Sensei ne collectent pas d’informations d’identification personnelle.

- Catalogue : métadonnées de produit, telles que le nom, le prix et la disponibilité.

Lors de l’installation de `magento/product-recommendations module`, Adobe Sensei agrège les données comportementales et de catalogue et crée [!DNL Product Recommendations] pour chaque type de recommandation. Le service [!DNL Product Recommendations] déploie ensuite ces recommandations sur votre vitrine. Pour vous aider à mettre en oeuvre des recommandations de produits sur votre vitrine, utilisez le workflow suivant :

>[!NOTE]
>
> Si votre vitrine est mise en oeuvre à l’aide de PWA Studio, reportez-vous à la [documentation du PWA](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). Si vous utilisez une technologie front-end personnalisée telle que React ou Vue JS, apprenez à [intégrer](headless.md) [!DNL Product Recommendations] dans votre vitrine sans interface utilisateur.

## Workflow

1. **Déployer la collecte de données en production**

   Le déploiement de [!DNL Product Recommendations] nécessite deux [sources de données](type.md) principales : catalogue et comportement. La production étant le seul environnement dans lequel les actions de vos acheteurs sont capturées et analysées, commencez la collecte de données en production le plus tôt possible. [ Découvrez comment Adobe Sensei entraîne des modèles d’apprentissage automatique qui génèrent des recommandations de meilleure qualité. ](events.md) En outre, lorsque vous commencez à collecter des données comportementales en production, vous pouvez [récupérer les recommandations](verify.md) en fonction de ces données de production lors de l’exploitation dans des environnements hors production. Vous pouvez ensuite tester et tester différentes recommandations calculées à partir de données réelles d’acheteurs collectées en production.

   Pour déployer la collecte de données en production, vous devez [installer et configurer](install-configure.md) le module [!DNL Product Recommendations] en fournissant une [clé API](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html).

   >[!TIP]
   >
   > Le déploiement de la collecte de données ne modifie pas l’aspect de votre vitrine ni l’expérience de vos acheteurs. Seule la création et le déploiement d’unités de recommandation modifient l’expérience client sur votre storefront. Assurez-vous de tester votre environnement hors production avant de procéder au déploiement en production. De plus, ne créez pas d’unités de recommandations tant que vous n’avez pas personnalisé votre modèle. Voir l’étape suivante.

1. **Personnaliser le modèle pour qu&#39;il corresponde à votre style**

   Votre vitrine représente votre marque. Veillez donc à modifier le modèle de recommandations de produits pour qu’il corresponde au thème de votre site.

   >[!TIP]
   >
   > En personnalisant le modèle, vous pouvez spécifier votre feuille de style, remplacer l’emplacement d’affichage d’une unité de recommandation sur une page, etc.

   Voir [Personnaliser](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/customize.html) dans la documentation destinée aux développeurs pour savoir comment effectuer cette étape.

1. **Tester les recommandations sur votre environnement hors production**

   Il est toujours recommandé de tester une nouvelle technologie dans votre environnement hors production avant de la déployer en production. Les recommandations de test sur votre environnement hors production vous permettent de lire avec différents types d’unités de recommandation, de positionnement et de pages. Vous pouvez extraire des recommandations basées sur des données comportementales déjà collectées en production lors du test dans votre environnement hors production, de sorte que les résultats des recommandations soient basés sur le comportement d’achat des clients réels.

   >[!TIP]
   >
   > Assurez-vous que votre catalogue d’environnement hors production est largement identique à celui que vous avez en production. L’utilisation de catalogues similaires permet de s’assurer que les produits renvoyés dans les unités de recommandation ressemblent étroitement aux produits en production.

   Voir [Récupérer](staging-environment.md) des données comportementales de votre environnement de production pour savoir comment terminer cette étape.

1. **Créez et déployez des recommandations sur votre storefront de production**

   Maintenant que vous avez déployé la collecte de données comportementales en production, modifié le modèle de recommandations de produits et testé les recommandations à l’aide du comportement réel de l’acheteur, vous êtes prêt à convertir tout le code en production et à [créer](create.md) recommandations de produits en direct.
