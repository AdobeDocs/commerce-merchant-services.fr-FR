---
title: Gestion des stocks de produits
description: Configurez les fonctionnalités et la messagerie du stock commercial disponibles pour les clients.
role: User, Admin
level: Intermediate
exl-id: 3ac217f7-e823-4578-8416-5ecceb76aa87
source-git-commit: 4ea03b3be11056526adc42d875b1e26a24736d15
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# Gestion des stocks de produits

En tant que marchand, vous pouvez utiliser Adobe Commerce [Inventory management](https://docs.magento.com/user-guide/catalog/inventory-management.html) options de stock et de source. De plus, vous pouvez contrôler d’autres options de disponibilité du stock relatives aux opérations de magasin marchand avec la solution d’exécution de magasin.

- Option de livraison à domicile des magasins marchands

- Autoriser/Disponible pour le nettoyage de magasin

- UPC/SKU/autres identifiants de produit uniques

- Seuil en rupture de stock

- Décrémentation de l’inventaire à partir de lieux spécifiques lors de la commande

Configurez les options Product Stock depuis l’administrateur : **[!UICONTROL Catalog > Products > Select Product]**

## **Options d’inventaire des produits**

| **Champ** | **Description** | **Portée** | **Obligatoire** |
|----------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------|--------------|
| **Disponible pour la diffusion à domicile** | Définit la disponibilité de la livraison à domicile (Ship-from-Store) pour le produit. Lorsqu’elle est activée, tous les emplacements de magasin de commerce attribués avec l’inventaire disponible du produit sont considérés comme éligibles à l’option Livraison à domicile. Lorsque cette option est désactivée, le produit n’est jamais éligible à la livraison à domicile, même si un magasin commercial dispose d’un stock disponible.</br></br>Dans la plupart des cas, la définition de cette option au niveau de la boutique est suffisante. Cependant, il peut y avoir des cas uniques pour des produits spécifiques, comme ceux soumis à des restrictions de livraison fédérales, qui ne doivent pas être éligibles à la livraison à domicile. | Site Web | Non |
| **[!UICONTROL Available for Store Pickup]** | Définissez la disponibilité de la collecte en magasin pour le produit. Lorsqu’elle est activée, tous les emplacements de boutique affectés avec le stock disponible pour le produit sont considérés comme éligibles à l’option de collecte de magasin. Lorsque cette option est désactivée, le produit n’est jamais éligible à la collecte de magasin, même si un magasin de commerce dispose d’un stock disponible.</br></br>Cette option peut s’avérer utile lorsque vous effectuez le suivi de l’inventaire des commerçants dans le système, mais que vous ne souhaitez pas le vendre sur votre canal de commerce électronique. | Site Web | Non |
| **[!UICONTROL UPC / SKU / Custom Scannable Identifier]** | Cet attribut doit déjà exister en tant qu’attribut de produit et se rapporte à la variable **[!UICONTROL Barcode Source / Barcode Type]** . Cet attribut est utilisé pour effectuer le suivi d’un code à barres numérisable pour vos produits. Cette valeur peut être envoyée lorsqu’une commande est envoyée à vos magasins de vente pour être sélectionnée. Les associés de magasin peuvent utiliser la valeur avec la liste de sélection pour faire correspondre les produits sur l’étagère à l’aide d’un scanner de codes à barres. | Affichage en magasin | Non |

{style=&quot;table-layout:auto&quot;}

## Sources pour l’inventaire au niveau du produit

| **Champ** | **Description** | **Portée** | **Obligatoire** |
|-----------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Out of Stock Threshold]** | Définissez le seuil de stock de l’article dans chaque source. Lorsque le stock tombe en dessous du seuil, il est considéré comme en rupture de stock à la source.</br></br>Pour utiliser le paramètre Configuration de magasin global, cochez la case **[!UICONTROL Use Default]** . | Global | Non |
| **[!UICONTROL Allow Store Pickup]** | Définissez explicitement si l’article est disponible pour la récupération de magasin, quelle que soit la configuration d’emplacement de magasin ou de stock disponible.</br></br> Pour utiliser le paramètre au niveau du produit, désélectionnez la case [!UICONTROL Use Default] et effectuez votre sélection. Sinon, ce paramètre est sélectionné en fonction de la configuration pour **[!UICONTROL Allow In-Store Pickup]** qui est défini sur la source du stock. | Global | Non |

{style=&quot;table-layout:auto&quot;}

