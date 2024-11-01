---
title: Inventory management Source Transfer
description: "Configurez les stocks pour le  [!DNL Store Fulfillment solution]  avec Adobe Commerce Inventory management. Configurez un nouveau stock et transférez le stock par défaut afin de pouvoir l’affecter aux sources configurées pour activer les fonctionnalités de nettoyage de magasin requises par la solution d’exécution de magasin."
role: Admin
level: Intermediate
feature: Shipping/Delivery, Inventory, Configuration
exl-id: 669d4dce-4cac-4bde-acc5-26c70a51f7f1
source-git-commit: 37380063242b6d904910be731b8e58471625e9cb
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---


# Inventory management Source Transfer

La solution [!DNL Store Fulfillment] utilise Adobe Commerce Inventory management natif. Par défaut, la configuration [!DNL Commerce] attribue tous les stocks web au stock par défaut, qui ne peut pas avoir de sources supplémentaires affectées. Un site web ne pouvant se voir attribuer qu’un seul stock, un commerçant doit configurer un nouveau stock et éventuellement transférer son stock source par défaut à une source affectée à la portée appropriée. Ensuite, la source peut être affectée au nouveau stock.

>[!IMPORTANT]
>
>Les vendeurs doivent conserver la source par défaut pour tous les produits inclus dans les types de produits de groupe et de regroupement. Ces produits ont besoin d’une quantité de stock qui respecte le seuil de quantité minimal pour dans les articles en stock et qui inclut un état de stock de [!UICONTROL In Stock].

Ces modifications de configuration vous permettent d’accomplir trois tâches :

1. [ Transférez l’inventaire à la source](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/quantities/inventory-transfer) pour déplacer l’inventaire du stock/de la source par défaut vers le nouveau stock/la nouvelle source.

1. [Affectez des sources en bloc](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/quantities/bulk-assignment) pour ajouter les nouvelles sources pour tous vos produits.

1. [ Effectuez des mises à jour en masse pour les attributs de produit ](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update) afin d’ajouter les attributs `Allow Store Pickup` et `Allow Home Delivery` aux produits existants. Lorsque la solution est installée, les attributs ont les valeurs *default* optimales. Toutefois, ces attributs ne sont pas appliqués aux produits existants tant que vous n’avez pas terminé le processus de mise à jour des conteneurs en masse.

L’inventaire est déduit de la source sélectionnée (emplacement du magasin de détail ou entrepôt de commerce électronique). Les sources utilisées comme entrepôts de commerce électronique doivent être affectées au même stock que l’emplacement de prise en charge du magasin et classées par priorité avant les emplacements de vente au détail. Pour plus d’informations, voir [Hiérarchisation des sources pour un stock](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/stocks/stocks-prioritize-sources).

Pour plus d’informations sur la gestion des stocks, des stocks et des sources, consultez la documentation utilisateur d’Adobe Commerce :

- [Gestion de l’inventaire](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/introduction)

- [Gestion des quantités d’inventaire](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/quantities/quantities-manage)

- [Gestion des stocks](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/stocks/stocks-manage)

- [Gestion des sources](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/sources/sources-manage)

- [Hiérarchisation des sources pour un stock](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/stocks/stocks-prioritize-sources)

- [Mises à jour en bloc des attributs de produit](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update)


>[!IMPORTANT]
>
>La modification de la configuration des sources d’inventaire et de stock peut également avoir un impact en aval sur les systèmes intégrés. Assurez-vous de comprendre l’impact des modifications apportées à la configuration de l’inventaire sur ces systèmes.
