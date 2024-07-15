---
title: Configuration de plusieurs sites web et de portée
description: Configurez les stocks et les méthodes de diffusion pour plusieurs sites web et portées de magasin.
role: Admin
level: Experienced
feature: Shipping/Delivery, Inventory, Configuration
exl-id: 8939046e-1c26-4380-83be-ff8e074e591d
source-git-commit: 36b57648e156ead801764f3ee4e5e6a0f3245fe6
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---

# Configuration de plusieurs sites web et de portée

Vous pouvez définir la [Portée](https://docs.magento.com/user-guide/configuration/scope.html) pour quelques éléments afin d’accueillir plusieurs sites web, magasins et vues de magasin :

- [Gérer le stock](https://docs.magento.com/user-guide/catalog/inventory-stock.html) par portée

- Gérer [!DNL Delivery Methods] par portée

Vous pouvez attribuer du stock à un site web ou à une portée de magasin. Ensuite, mettez à jour les sources des magasins afin de définir les méthodes de remise disponibles (livraison à domicile, prise en main du magasin).

Une fois la configuration mise à jour, les options de récupération de magasin sur la page Détails du produit (PDP) dans le storefront Adobe Commerce peuvent être sélectionnées uniquement pour les produits disponibles à partir d’une source de stock qui permet la récupération de magasin.

## Gérer les paramètres de récupération en magasin

Activez ou désactivez les options [!UICONTROL In-Store Pickup] pour chaque site web ou portée de magasin à partir des [configurations de méthode de diffusion](enable-general.md#delivery-methods) dans l’administrateur.

1. Accédez à **[!UICONTROL Stores > Configuration]**.

1. Sélectionnez la portée (Site Web vers magasin) à configurer.

1. Avec la portée sélectionnée, accédez à **[!UICONTROL Sales > Delivery Methods]**.

1. Désactivez ou activez la méthode de diffusion **[!UICONTROL In-Store Pickup]**.

Vous pouvez également gérer si la sélection côté serveur ou en magasin est disponible globalement dans cette section.

Gérez les paramètres [!UICONTROL In-Store Pickup] et [!UICONTROL Delivery Method] par source de stock. Il existe de nombreuses autres configurations pour une parfaite flexibilité de votre mise en oeuvre.
