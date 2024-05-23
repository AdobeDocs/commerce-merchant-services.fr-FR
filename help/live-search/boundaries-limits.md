---
title: "Limites et limites"
description: En savoir plus sur les limites et les limites de [!DNL Live Search] pour vous assurer qu’il répond aux besoins de votre entreprise.
role: Admin, Developer
exl-id: ad6737f9-6ecd-4d82-89e7-d95425e4ba53
source-git-commit: 0f4860afa38dc188c19ee8bcbd386d3fb5d0907f
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 0%

---

# Limites et limites

En ce qui concerne la recherche de site, Adobe Commerce vous offre des options. Vérifiez les limites et limites suivantes pour vous assurer que [!DNL Live Search] et [!DNL Catalog Service] répondre aux besoins de votre entreprise ; Si vous avez besoin de fonctionnalités de recherche avancées telles que la recherche de contenu, l’introduction de votre propre algorithme (BYOA) ou le marchandisage basé sur les attributs, envisagez une solution de recherche tierce.

## Général

- La variable [Recherche avancée](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search) module est désactivé lorsque [!DNL Live Search] est installé et le lien Recherche avancée dans le pied de page du storefront est supprimé.
- [Tarifs de niveau](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/pricing/product-price-tier) et [Tarifs spéciaux](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/pricing/product-price-special) ne sont pas pris en charge dans la variable [!DNL Live Search] champ et widget de page de liste de produits.
- Les prix des produits ne comprennent pas la TVA.
- La recherche de contenu n’est pas prise en charge.
- Il existe une limite de 10 000 produits pouvant être paginés.
- L’adaptateur de recherche ne prend pas en charge les attributs de produit créés avec un modèle source personnalisé et utilisés comme facettes. Pour prendre en charge cette fonctionnalité, vous devez utiliser la variable [Widget de page de liste de produits](plp-styling.md).

## Indexation

- [!DNL Live Search] [index](indexing.md) jusqu’à 450 attributs de produit par consultation de magasin. Ils sont répartis comme suit :
   - 50 attributs triables
   - 200 attributs filtrables
   - 200 attributs pouvant faire l’objet de recherches
- [!DNL Live Search] répertorie uniquement les produits de la base de données Adobe Commerce.
- Les pages CMS ne sont pas indexées.

## Facettes

- 100 attributs au maximum peuvent être configurés en tant que facettes à partir des 200 attributs filtrables pouvant être indexés.
- Dans une facette, un maximum de 30 compartiments peuvent être renvoyés. Si plus de 30 compartiments doivent être renvoyés, [créer un ticket d’assistance](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) ainsi, Adobe peut analyser l’impact sur les performances et déterminer s’il est possible d’augmenter cette limite pour votre environnement.
- Les facettes dynamiques peuvent entraîner des problèmes de performances dans les index volumineux et les index dont la qualité est élevée. Si vous avez créé des facettes dynamiques et que vous constatez une détérioration des performances ou un non-chargement de page avec des erreurs de délai d’expiration, essayez de modifier vos facettes pour les épingler afin de déterminer si cela résout votre problème de performances.
- Etat des stocks (`quantity_and_stock_status`) n’est pas pris en charge en tant que facette. Vous pouvez utiliser `inStock: 'true'` pour exclure les produits en stock. Cette fonctionnalité est prise en charge par défaut dans la variable `LiveSearchAdapter` lorsque &quot;Display out of stock products&quot; est défini sur &quot;True&quot; dans la variable [!DNL Commerce] Administrateur.

## Requête

- [!DNL Live Search] n’a pas accès à la taxonomie complète de l’arborescence des catégories, ce qui rend certains scénarios de recherche de navigation par couches hors de sa portée.
- [!DNL Live Search] utilise une variable [Point de terminaison GraphQL](https://developer.adobe.com/commerce/services/graphql/live-search/) pour les requêtes afin de prendre en charge des fonctionnalités telles que les facettes dynamiques et la recherche par saisie. Bien que similaire à la variable [API GRAPHQL](https://developer.adobe.com/commerce/webapi/graphql/), il existe quelques différences et certains champs peuvent ne pas être entièrement compatibles.
- Le nombre maximal de résultats pouvant être renvoyés dans une requête de recherche est de 10 000.

## Règles

- Nombre maximal de marchandisage de recherche [rules](rules.md) la vue de magasin est de 50.
- Le marchandisage des catégories peut comporter une règle par catégorie.
- Le nombre maximal de conditions par règle est de 10.
- Le nombre maximal d’événements par règle est de 25.

## Synonymes

- [!DNL Live Search] peut gérer jusqu’à 200 [synonyms](synonyms.md) par vue de magasin.
- Les synonymes à plusieurs mots ne sont pas pris en charge.

## Marchandisage des catégories

- Une règle par catégorie peut être créée pour chaque vue de magasin. Chaque règle peut avoir :
   - Jusqu’à dix conditions
   - Jusqu’à 25 événements

## Autorisations B2B et de catégorie

- Les produits ne s’affichent pas s’ils ne sont pas ajoutés à un catalogue partagé par défaut.
- Pour restreindre les groupes de clients à l’aide des autorisations du catalogue :
   - Les produits doivent être affectés à la catégorie Racine .
   - Le groupe de clients &quot;Non connecté&quot; doit disposer des autorisations de navigation &quot;Autoriser&quot;.
   - Pour limiter les produits au groupe de clients &quot;Non connecté&quot;, accédez à chaque catégorie et définissez des autorisations pour chaque groupe de clients.
- La prise en charge de B2B avec la recherche en direct pour PWA Studio n’est pas prise en charge pour le moment.
