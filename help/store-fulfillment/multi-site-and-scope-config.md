---
title: Configuration de plusieurs sites web et périmètre
description: Configurez les stocks et les méthodes de diffusion pour plusieurs sites web et portées de magasin.
role: User, Admin
level: Intermediate
source-git-commit: 42b0118b427b1e04186793b4a57c058bc1cabdd4
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---


# Configuration de plusieurs sites web et périmètre

Vous pouvez définir la variable [Portée](https://docs.magento.com/user-guide/configuration/scope.html) pour quelques éléments afin d’accueillir plusieurs sites web, magasins et vues de magasin :

- [Gérer Stock](https://docs.magento.com/user-guide/catalog/inventory-stock.html) par portée

- Gérer [!DNL Delivery Methods] par portée

Vous pouvez attribuer du stock à un site web ou à une portée de magasin. Ensuite, mettez à jour les sources des magasins afin de définir les méthodes de remise disponibles (livraison à domicile, prise en main du magasin).

Une fois la configuration mise à jour, les options de récupération de magasin sur la page des détails du produit (PDP) dans le storefront Adobe Commerce ne peuvent être sélectionnées que pour les produits disponibles à partir d’une source de stock qui permet la récupération de magasin.

## Gérer les paramètres de récupération en magasin

Activez ou désactivez la variable [!UICONTROL In-Store Pickup] options pour chaque site web ou la portée du magasin à partir de [Configurations des méthodes de diffusion](enable-general.md#delivery-methods) dans Admin.

1. Accédez à **[!UICONTROL Stores > Configuration]**.

1. Sélectionnez la portée (Site Web vers magasin) à configurer.

1. Avec la portée sélectionnée, accédez à **[!UICONTROL Sales > Delivery Methods]**.

1. Désactivez ou activez l’option **[!UICONTROL In-Store Pickup]** Méthode de diffusion.

Vous pouvez également gérer si la sélection côté serveur ou en magasin est disponible globalement dans cette section.

Gérer les [!UICONTROL In-Store Pickup] et [!UICONTROL Delivery Method] paramètres par source de stock. Il existe de nombreuses autres configurations pour une parfaite flexibilité de votre mise en oeuvre.
