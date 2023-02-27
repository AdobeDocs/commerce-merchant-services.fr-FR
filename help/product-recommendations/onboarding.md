---
title: Intégration
description: Découvrez les exigences et les plateformes prises en charge dans [!DNL Product Recommendations].
exl-id: ad47ac39-8f6f-4765-84ad-9e3d104385db
source-git-commit: d56fd57281a5b675e128cca75d4057756a0bf4bf
workflow-type: tm+mt
source-wordcount: '240'
ht-degree: 0%

---

# Intégration

Le processus d’intégration pour [!DNL Product Recommendations] requiert l’accès à la ligne de commande du serveur et comprend les étapes suivantes. Si vous n’êtes pas familiarisé avec l’utilisation de la ligne de commande, demandez de l’aide à un développeur ou à un intégrateur système.

- [Workflow de mise en oeuvre](implementation-workflow.md)
- [Installation et configuration](install-configure.md)
- [Paramètres](settings.md)
- [Vérifier](verify.md)
- [Environnement d’évaluation](staging-environment.md)

## Conditions

- Adobe Commerce 2.3.x, 2.4.x
- PHP 7.3 / 7.4 / 8.1
- Compositeur

### Plateformes prises en charge

- Adobe Commerce on premise (EE) : 2.4.x
- Adobe Commerce on Cloud (CEE) : 2.4.x

### Prise en charge du créateur de pages

[!DNL Product Recommendations] peut être ajouté à une page sous la forme d’un type de contenu Page Builder . Pour ajouter la prise en charge de Page Builder à Recommendations de produit, reportez-vous à la section [Installation et configuration](install-configure.md).

Voir [[!DNL Page Builder] Intégration](page-builder.md) pour obtenir des instructions sur l’ajout de [!DNL Product Recommendations] into [!DNL Page Builder] contenu.

### Prise en charge B2B {#b2bsupport}

Les vitrines B2B nécessitent souvent une logique complexe qui détermine la visibilité et la tarification des produits pour chaque acheteur ou groupe de clients. [!DNL Product Recommendations] now [support](release-notes.md) cette fonctionnalité en respectant [permissions de catégorie](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/category-permissions.html), [catalogues partagés](https://experienceleague.adobe.com/docs/commerce-admin/b2b/shared-catalogs/catalog-shared.html), et [tarification spécifique au groupe de clients](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/pricing-advanced.html). Par exemple, si vous avez masqué certaines catégories de votre segment de client au détail, un acheteur de ce segment n’affichera pas les recommandations pour les produits de ces catégories. En outre, lorsque vous définissez un catalogue partagé pour des groupes de clients et des entreprises spécifiques, ces acheteurs ne voient des recommandations que pour les produits auxquels ils ont accès. Tous les produits recommandés reflètent un prix spécifique au groupe de clients correct en fonction du groupe de clients de chaque acheteur.
