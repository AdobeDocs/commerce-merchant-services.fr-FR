---
title: "Limites et limites"
description: Découvrez les limites de  [!DNL Live Search] pour vous assurer qu’il répond aux besoins de votre entreprise.
role: Admin, Developer
exl-id: ad6737f9-6ecd-4d82-89e7-d95425e4ba53
source-git-commit: ffbb41ef2bc940982b4acb33623ef689542617c1
workflow-type: tm+mt
source-wordcount: '777'
ht-degree: 0%

---

# Limites et limites

En ce qui concerne la recherche de site, Adobe Commerce vous offre des options. Vérifiez les limites et limites suivantes pour vous assurer que [!DNL Live Search] et [!DNL Catalog Service] répondent aux besoins de votre entreprise. Si vous avez besoin de fonctionnalités de recherche avancées telles que la recherche de contenu, l’introduction de votre propre algorithme (BYOA) ou le marchandisage basé sur les attributs, envisagez une solution de recherche tierce.

## Général

- Le module [Recherche avancée](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search) est désactivé lorsque [!DNL Live Search] est installé et le lien Recherche avancée dans le pied de page du storefront est supprimé.
- Les [tarifs de niveau élevé](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/pricing/product-price-tier) et [prix spécial](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/pricing/product-price-special) ne sont pas pris en charge dans le champ [!DNL Live Search] et le widget de page de liste de produits.
- Les prix des produits ne comprennent pas la TVA.
- La recherche de contenu n’est pas prise en charge.
- Il existe une limite de 10 000 produits pouvant être paginés.
- Il existe une limite stricte de 1 Mo par attribut, y compris la description et les attributs personnalisés.
- L’adaptateur de recherche ne prend pas en charge les attributs de produit créés avec un modèle source personnalisé et utilisés comme facettes. Pour prendre en charge cette fonctionnalité, vous devez utiliser le [widget de page de liste de produits](plp-styling.md).

## Indexation

- [!DNL Live Search] [indexes](indexing.md) jusqu’à un total de 450 attributs de produit par consultation de magasin. Ils sont répartis comme suit :
   - 50 attributs triables
   - 200 attributs filtrables
   - 200 attributs pouvant faire l’objet de recherches
- [!DNL Live Search] indexe uniquement les produits de la base de données Adobe Commerce.
- Les pages CMS ne sont pas indexées.
- Les attributs de SKU, de nom et de catégorie peuvent faire l’objet de recherches par défaut et ne peuvent pas être exclus de la recherche. Veillez à annuler l’affectation des produits des catégories s’ils ne sont pas destinés à figurer dans ces catégories.

## Facettes

- 100 attributs au maximum peuvent être configurés en tant que facettes à partir des 200 attributs filtrables pouvant être indexés.
- Dans une facette, un maximum de 30 compartiments peuvent être renvoyés. Si plus de 30 lots doivent être renvoyés, [créez un ticket d’assistance](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) afin que l’Adobe puisse analyser l’impact sur les performances et déterminer s’il est possible d’augmenter cette limite pour votre environnement.
- Les facettes dynamiques peuvent entraîner des problèmes de performances dans les index volumineux et les index dont la qualité est élevée. Si vous avez créé des facettes dynamiques et que vous constatez une détérioration des performances ou un non-chargement de page avec des erreurs de délai d’expiration, essayez de modifier vos facettes pour les épingler afin de déterminer si cela résout votre problème de performances.
- L’état des stocks (`quantity_and_stock_status`) n’est pas pris en charge en tant que facette. Vous pouvez utiliser `inStock: 'true'` pour filtrer les produits en rupture de stock. Ceci est pris en charge par défaut dans le module `LiveSearchAdapter` lorsque &quot;Display out of stock products&quot; est défini sur &quot;True&quot; dans l’administrateur [!DNL Commerce].
- Les attributs de type date ne sont pas pris en charge en tant que facette.

## Requête

- [!DNL Live Search] utilise un [point d’entrée GraphQL](https://developer.adobe.com/commerce/services/graphql/live-search/) unique pour les requêtes afin de prendre en charge des fonctionnalités telles que les facettes dynamiques et la recherche par type. Bien que similaire à l’ [API GraphQL](https://developer.adobe.com/commerce/webapi/graphql/), il existe quelques différences et certains champs peuvent ne pas être entièrement compatibles.
- Le nombre maximal de résultats pouvant être renvoyés dans une requête de recherche est de 10 000.
- Il n’est pas possible de filtrer les résultats à l’aide d’un attribut de type date.

## Règles

- Le nombre maximal de [règles](rules.md) de marchandisage de recherche par vue de magasin est de 50.
- Le marchandisage des catégories peut comporter une règle par catégorie.
- Le nombre maximal de conditions par règle est de 10.
- Le nombre maximal d’événements par règle est de 25.
- Pour éviter des résultats imprévisibles liés aux réponses paginées, le nombre de produits épinglés ne doit pas dépasser la taille de page demandée.

## Synonymes

- [!DNL Live Search] peut gérer jusqu’à 200 [synonymes](synonyms.md) par vue de magasin.
- Les synonymes de plusieurs mots peuvent ne pas toujours fonctionner comme prévu. Veillez à tester ces synonymes dans l’environnement d’évaluation avant de les utiliser en production, car ils peuvent avoir un effet négatif sur la pertinence.

## Marchandisage des catégories

- Une règle par catégorie peut être créée pour chaque vue de magasin. Chaque règle peut avoir :
   - Jusqu’à dix conditions
   - Jusqu’à 25 événements

## Autorisations B2B et de catégorie

- Les produits ne s’affichent pas s’ils ne sont pas ajoutés à un catalogue partagé par défaut.
- Pour restreindre les groupes de clients à l’aide des [autorisations de catégorie](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/category-permissions) :
   - Les produits doivent être affectés à la catégorie racine.
   - Le groupe de clients &quot;Non connecté&quot; doit disposer des autorisations de navigation &quot;Autoriser&quot;.
   - Pour limiter les produits au groupe de clients &quot;Non connecté&quot;, accédez à chaque catégorie et définissez l’autorisation pour chaque [groupe de clients](https://experienceleague.adobe.com/docs/commerce-admin/b2b/shared-catalogs/catalog-shared-manage).
- La prise en charge par défaut de B2B avec le widget PLP sur PWA Studio n’est pas prise en charge pour le moment. Cependant, vous pouvez [utiliser l’API](install.md#pwa-support) pour mettre en oeuvre cette fonctionnalité.
- Les facettes de catégorie dans [!DNL Live Search] peuvent afficher des catégories qui ne sont pas affichables pour un [groupe de clients](https://experienceleague.adobe.com/docs/commerce-admin/b2b/shared-catalogs/catalog-shared-manage) spécifique.
- [!DNL Live Search] peut prendre en charge jusqu’à 1 000 groupes de clients.

## [!DNL Storefront popover]

- [[!DNL popover]](storefront-popover.md) est disponible uniquement pour les magasins qui utilisent le thème *Luma* ou un thème personnalisé basé sur *Luma*. Le chemin de navigation de la page des résultats de recherche ne comporte pas le style *Luma*.
- [!DNL popover] ne prend pas en charge le thème *vierge*.
- [!DNL popover] n’est pas pris en charge dans le formulaire de commande rapide.
- Les listes blanches et les comparaisons de produits ne sont pas prises en charge.
