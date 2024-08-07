---
title: Intégration
description: Découvrez les exigences et les plateformes prises en charge dans [!DNL Product Recommendations].
exl-id: ad47ac39-8f6f-4765-84ad-9e3d104385db
source-git-commit: a90fcd8401b7745a65715f68efccdb3ce7c77ccb
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 0%

---

# Intégration

Le processus d’intégration de [!DNL Product Recommendations] nécessite l’accès à la ligne de commande du serveur et comprend les étapes suivantes. Si vous n’êtes pas familiarisé avec l’utilisation de la ligne de commande, demandez de l’aide à un développeur ou à un intégrateur système.

- [Workflow de mise en oeuvre](implementation-workflow.md)
- [Installation et configuration](install-configure.md)
- [Paramètres](settings.md)
- [Vérifier](verify.md)
- [Environnement d’évaluation](staging-environment.md)

## Conditions

- Adobe Commerce 2.4.4+
- PHP 8.1, 8.2
- Compositeur 2

### Plateformes prises en charge

- Adobe Commerce on premise (EE) : 2.4.4+
- Adobe Commerce on Cloud (CEE) : 2.4.4+

## Point d’entrée

[!DNL Product Recommendations] communique par l’intermédiaire du point de terminaison à l’adresse `https://catalog-service.adobe.io/graphql`.

### Prise en charge du créateur de pages

[!DNL Product Recommendations] peut être ajouté à une page en tant que type de contenu Page Builder. Pour ajouter la prise en charge de Page Builder à Product Recommendations, reportez-vous à la section [Installation et configuration](install-configure.md).

Voir [[!DNL Page Builder] Intégration](page-builder.md) pour obtenir des instructions sur la façon d&#39;ajouter [!DNL Product Recommendations] au contenu [!DNL Page Builder].

### Indexation des prix SaaS

Les clients de recommandations de produits peuvent utiliser l’ [indexation de prix SaaS](../price-index/price-indexing.md), qui permet d’accélérer les mises à jour des prix et le temps de synchronisation.

### Prise en charge B2B {#b2bsupport}

Les vitrines B2B nécessitent souvent une logique complexe qui détermine la visibilité et la tarification des produits pour chaque acheteur ou groupe de clients. [!DNL Product Recommendations] [ désormais ](release-notes.md) prendre en charge cette fonctionnalité en honorant les [autorisations de catégorie](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/category-permissions.html), les [catalogues partagés](https://experienceleague.adobe.com/docs/commerce-admin/b2b/shared-catalogs/catalog-shared.html) et la [tarification spécifique au groupe de clients](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/pricing-advanced.html). Par exemple, si vous avez masqué certaines catégories de votre segment de client au détail, un acheteur de ce segment n’affichera pas les recommandations pour les produits de ces catégories. En outre, lorsque vous définissez un catalogue partagé pour des groupes de clients et des entreprises spécifiques, ces acheteurs ne voient des recommandations que pour les produits auxquels ils ont accès. Tous les produits recommandés reflètent un prix spécifique au groupe de clients correct en fonction du groupe de clients de chaque acheteur.

>[!NOTE]
>
>Les marchands peuvent personnaliser et étendre des widgets ou des éléments storefront à l’aide de l’API Storefront [ Catalog Service](../catalog-service/overview.md), mais toute personnalisation n’est pas adaptée à l’équipe d’assistance d’Adobe.
