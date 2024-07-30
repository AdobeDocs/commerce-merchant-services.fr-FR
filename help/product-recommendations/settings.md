---
title: Paramètres
description: Découvrez comment modifier la source de vos données  [!DNL Product Recommendations] et comment activer les recommandations visuelles.
exl-id: 8c074e11-e0cb-4d55-b646-30279c79bbc2
source-git-commit: 3a5dec9422aa34eeb204b9fe6f089551e4038f1c
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# Paramètres

Lorsque vous [configurez un espace de données SaaS](../landing/saas.md#saas-configuration) pour Recommendations, l’espace de données SaaS collecte des données de catalogue et des données comportementales de storefront. [Adobe Sensei](https://www.adobe.com/sensei.html) analyse les données et calcule les associations de produits utilisées pour diffuser le Recommendations de produits.

Les environnements hors production pour le test ou l’évaluation n’ont généralement pas la quantité ou la qualité des données comportementales de storefront pour fournir des recommandations de produits réalistes. Le comportement réel des acheteurs à l’échelle ne peut être capturé que dans un environnement de production. Pour résoudre ce problème, Adobe Commerce vous permet d’utiliser les recommandations de produits de votre environnement de production avec d’autres espaces de données SaaS hors production. L’utilisation de données de vitrine réelles dans un environnement hors production vous permet de prévisualiser les recommandations que vos acheteurs voient et d’expérimenter avec différents types de recommandations et emplacements. Les acheteurs peuvent prévisualiser les Recommendations d’un autre espace de données SaaS, mais pas cliquer dessus.

Les commandes d’évaluation sont enregistrées à l’aide de l’évaluation `environmentId`. Cela n’a aucune incidence sur les données de production. Les données de production sont récupérées à l’aide de `alternateEnvironmentId`.

>[!NOTE]
>
>Lors de l’utilisation de Recommendations de produit par le biais de REST, le paramètre `alternateEnvironmentId` peut être utilisé pour spécifier d’autres aspects des données. Lorsque vous utilisez le Recommendations de produit via GraphQL, ce paramètre n’est pas disponible.

## Choisissez la source des recommandations

Pour modifier la source de vos données de recommandations de produits, choisissez l’espace de données SaaS avec les données comportementales que vous souhaitez utiliser. Avant de commencer, assurez-vous que :

- La collecte de données Storefront doit être [ configurée et activée](install-configure.md) pour votre environnement de production et [vérifiée](verify.md) que les données comportementales sont envoyées à Adobe Commerce.
- Votre catalogue d’environnements hors production doit être essentiellement le même que votre catalogue de production. L’utilisation de catalogues similaires permet de s’assurer que les unités de recommandations de produits renvoyées ressemblent étroitement à celles en production.

1. Connectez-vous à l’administrateur de votre environnement Adobe Commerce hors production.

1. Sur la barre latérale _Admin_, accédez à **Marketing** > _Promotions_ > **Recommendations de produit**.

1. Cliquez sur **Paramètres**.

   ![paramètres de recommandation de produit](assets/settings.png)
   _Paramètres_

1. Dans la section _Source Recommendations_ , activez l’option **Récupérer les recommandations à partir d’un autre espace de données SaaS** . La section _Source Recommendations_ apparaît uniquement dans un environnement hors production.

   Une liste de _Espaces de données SaaS disponibles_ s’affiche.

   ![paramètres de recommandation de produit](assets/settings-select-saas.png)
   _Paramètres_

1. Sélectionnez l’espace de données SaaS contenant les données de nouvel acheteur que vous souhaitez utiliser.

1. Cliquez sur **Enregistrer les modifications**.

   Adobe Commerce récupère désormais les recommandations de l’espace de données sélectionné.

   >[!NOTE]
   >
   > Bien que vous puissiez afficher les recommandations récupérées à partir d’un autre espace de données SaaS sur le storefront hors production, vous ne pouvez pas cliquer sur les recommandations.

### Configuration d’un nouvel espace de données SaaS

1. Dans la section source Recommendations, cliquez sur **Modifier la configuration**.

1. Suivez les instructions pour configurer un nouveau [[!DNL Commerce] service](/help/landing/saas.md).

## Activation des recommandations visuelles

Si le module [Visual Product Recommendations](install-configure.md) est installé, vous devez activer Visual Recommendations pour utiliser le type de recommandation [Visual Similarity](type.md#visualsim).

Dans la section _Visual Recommendations_, définissez **Activer Visual Recommendations** sur la position active.
