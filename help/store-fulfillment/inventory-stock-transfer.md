---
title: Transfert de source Inventory management
description: Configurez les stocks pour l’exécution de magasin en configurant un nouveau stock et en transférant les stocks hors stock par défaut.
role: User, Admin
level: Intermediate
exl-id: 669d4dce-4cac-4bde-acc5-26c70a51f7f1
source-git-commit: 4ea03b3be11056526adc42d875b1e26a24736d15
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 0%

---

# Transfert de source Inventory management

Le [!DNL Store Fulfillment] La solution utilise Adobe Commerce Inventory management natif. Par défaut, la variable [!DNL Commerce] La configuration affecte l’ensemble de l’inventaire web au stock par défaut, auquel aucune source supplémentaire ne peut être affectée. Un site web ne pouvant se voir attribuer qu’un seul stock, un commerçant doit configurer un nouveau stock et éventuellement transférer son stock source par défaut à une source affectée à la portée appropriée. Ensuite, la source peut être affectée au nouveau stock.

Ces modifications de configuration vous permettent d’accomplir trois tâches :

1. [Transférer l’inventaire à la source](https://docs.magento.com/user-guide/catalog/inventory-bulk-transfer-inventory.html) pour déplacer le stock du stock/de la source par défaut vers le nouveau stock/la nouvelle source.

2. [Affectation de sources en bloc](https://docs.magento.com/user-guide/catalog/inventory-bulk-assign-sources.html) pour ajouter les nouvelles sources pour tous vos produits.

3. [Mises à jour en bloc complètes des attributs de produit](https://docs.magento.com/user-guide/stores/bulk-product-attribute-update.html) pour ajouter la variable `Allow Store Pickup` et `Allow Home Delivery` Attributs aux produits existants. Lorsque la solution est installée, les attributs ont la valeur optimale *default* valeurs. Toutefois, ces attributs ne sont pas appliqués aux produits existants tant que vous n’avez pas terminé le processus de mises à jour en bloc.

L’inventaire est déduit de la source sélectionnée (emplacement du magasin de détail ou entrepôt de commerce électronique). Les sources utilisées comme entrepôts de commerce électronique doivent être affectées au même stock que l’emplacement de prise en charge du magasin et classées par priorité avant les emplacements de vente au détail. Pour plus d’informations, voir [Hiérarchisation des sources pour un stock](https://docs.magento.com/user-guide/catalog/inventory-stock-priority.html).


Pour plus d’informations sur la gestion des stocks, des stocks et des sources, consultez la documentation utilisateur d’Adobe Commerce :

- [Gestion du stock](https://docs.magento.com/user-guide/catalog/inventory-management.html)

- [Gestion des quantités d’inventaire](https://docs.magento.com/user-guide/catalog/inventory-manage-inventory-quantities.html)

- [Gestion des stocks](https://docs.magento.com/user-guide/catalog/inventory-stock.html)

- [Gestion des sources](https://docs.magento.com/user-guide/catalog/inventory-sources.html)

- [Hiérarchisation des sources pour un stock](https://docs.magento.com/user-guide/catalog/inventory-stock-priority.html)

- [Mises à jour en bloc des attributs de produit](https://docs.magento.com/user-guide/stores/bulk-product-attribute-update.html)


>[!IMPORTANT]
>
>La modification de la configuration des sources d’inventaire et de stock peut également avoir un impact en aval sur les systèmes intégrés. Assurez-vous de comprendre l’impact des modifications apportées à la configuration de l’inventaire sur ces systèmes.
