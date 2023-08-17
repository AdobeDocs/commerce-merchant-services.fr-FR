---
title: Gérer les restrictions de cookie
description: Découvrez comment les recommandations de produits gèrent les restrictions des cookies.
exl-id: 2f48c47c-569b-455c-a589-8f99b7b74064
source-git-commit: 78f226465b9d84707612596a5aa4622aa7869ee1
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 0%

---

# Gérer les restrictions de cookie

Adobe Commerce et Magento Open Source demandent le consentement avant que les données ne soient stockées dans les cookies du navigateur. Pour plus d’informations, voir [Mode de restriction des cookies](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html).

Lorsque vous déployez la variable `magento/product-recommendations` pour la production, il commence à collecter les événements d’interaction client sur votre storefront. Comme les données de ces événements peuvent être stockées dans des cookies de navigateur ou dans un espace de stockage local, la fonction prend en charge le mode de restriction des cookies en ne collectant pas les événements tant que l’acheteur n’a pas donné son consentement au cookie.

Cela peut ne pas fonctionner avec les solutions de consentement de cookies tiers. Il est de la responsabilité de chaque commerçant de s’assurer que la collecte des données ne se produit pas avant que le consentement au cookie ait été donné, comme le requiert souvent la loi. Si vous gérez le consentement aux cookies à l’aide d’un code personnalisé, vous pouvez utiliser un cookie de suivi à ne pas suivre appelé `mg_dnt` pour limiter la collecte de données.

- Nom du cookie :

  ```text
  `const DNT_COOKIE = "mg_dnt";`
  ```

- Définissez le cookie do-not-track pour désactiver la collecte de données :

  ```text
  `$.mage.cookies.set(DNT_COOKIE, true);`
  ```

- Pour effacer le cookie lorsque l’utilisateur a accepté les cookies :

  ```text
  `$.mage.cookies.clear(DNT_COOKIE);`
  ```
