---
title: Événements
description: Découvrez les données que chaque événement capture.
exl-id: b0c88af3-29c1-4661-9901-3c6d134c2386
role: Admin, Developer
feature: Personalization, Integration, Eventing
source-git-commit: 136cd11e65674ec6e797aeaabd80750a50324566
workflow-type: tm+mt
source-wordcount: '6957'
ht-degree: 0%

---

# [!DNL Data Connection] Événements

Vous trouverez ci-dessous la liste des événements Commerce disponibles lors de l’installation du [!DNL Data Connection] extension . Les données collectées par ces événements sont envoyées à Adobe Experience Platform Edge. Vous pouvez également créer [événements personnalisés](custom-events.md) pour collecter des données supplémentaires qui ne sont pas fournies en standard.

Outre les données collectées par les événements suivants, vous obtenez également [autres données](https://experienceleague.adobe.com/docs/experience-platform/edge/data-collection/automatic-information.html) fourni par le SDK Web de Adobe Experience Platform.

## Événements Storefront

Les événements storefront collectent des données comportementales anonymes de vos acheteurs lorsqu’ils parcourent votre site. Vous pouvez utiliser les données collectées par ces événements pour créer des promotions et des campagnes ciblées sur un ensemble spécifique d’acheteurs. Les données d’événement Storefront incluent uniquement des produits simples et configurables.

>[!NOTE]
>
>Tous les événements storefront incluent la variable [`identityMap`](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html) qui inclut l’adresse électronique de l’acheteur, le cas échéant, et l’ECID. En incluant ces données de profil dans chaque événement, vous n’avez pas besoin d’importer de compte d’utilisateur distinct depuis Adobe Commerce.

### addToCart

| Description | Nom de l’événement XDM |
|---|---|
| Déclenché lorsqu’un produit est ajouté au panier ou lorsque la quantité d’un produit dans le panier est incrémentée. | `commerce.productListAdds` |

#### Données collectées à partir de addToCart

Le tableau suivant décrit les données collectées pour cet événement.

| Champ | Description |
|---|---|
| `commerce.productListAdds` | Indique si un produit a été ajouté à un panier. Une valeur de `1` indique qu’un produit a été ajouté. |
| `commerce.cart.cartID` | Identifiant unique qui identifie le panier du client. |
| `commerce.commerceScope` | Indique l’emplacement d’un événement (affichage en magasin, magasin, site web, etc.). |
| `commerce.commerceScope.environmentID` | Identifiant de l’environnement. ID alphanumérique de 32 chiffres séparés par des tirets. |
| `commerce.commerceScope.storeCode` | Code de magasin unique. Vous pouvez avoir de nombreux magasins par site web. |
| `commerce.commerceScope.storeViewCode` | Code d’affichage de magasin unique. Vous pouvez avoir de nombreuses vues de magasin par magasin. |
| `commerce.commerceScope.websiteCode` | Code unique du site web. Vous pouvez avoir de nombreux sites Web dans un environnement. |
| `productListItems` | Tableau de produits qui ont été ajoutés au panier. |
| `productListItems.SKU` | Unité de gestion des stocks. Identifiant unique du produit. |
| `productListItems.name` | Nom d’affichage ou nom lisible du produit. |
| `productListItems.priceTotal` | Prix total de l’article de ligne de produit. |
| `productListItems.quantity` | Nombre d’unités de produits dans le panier. |
| `productListItems.discountAmount` | Indique le montant de la remise appliquée. |
| `productListItems.currencyCode` | La variable [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) code de devise utilisé, par exemple `USD` ou `EUR`. |
| `productListItems.productImageUrl` | URL de l’image principale du produit. |
| `productListItems.selectedOptions` | Champ utilisé pour un produit configurable. |
| `productListItems.selectedOptions.attribute` | Identifie un attribut du produit configurable, tel que `size` ou `color`. |
| `productListItems.selectedOptions.value` | Identifie la valeur de l’attribut, telle que `small` ou `black`. |

### openCart

| Description | Nom de l’événement XDM |
|---|---|
| Déclenché lors de la création d’un panier, c’est-à-dire lorsqu’un produit est ajouté à un panier vide. | `commerce.productListOpens` |

#### Données collectées à partir d’openCart

Le tableau suivant décrit les données collectées pour cet événement.

| Champ | Description |
|---|---|
| `commerce.productListOpens` | Indique si un panier a été créé. Une valeur de `1` indique qu’un panier a été créé. |
| `commerce.cart.cartID` | Identifiant unique qui identifie le panier du client. |
| `commerce.commerceScope` | Indique l’emplacement d’un événement (affichage en magasin, magasin, site web, etc.). |
| `commerce.commerceScope.environmentID` | Identifiant de l’environnement. ID alphanumérique de 32 chiffres séparés par des tirets. |
| `commerce.commerceScope.storeCode` | Code de magasin unique. Vous pouvez avoir de nombreux magasins par site web. |
| `commerce.commerceScope.storeViewCode` | Code d’affichage de magasin unique. Vous pouvez avoir de nombreuses vues de magasin par magasin. |
| `commerce.commerceScope.websiteCode` | Code unique du site web. Vous pouvez avoir de nombreux sites Web dans un environnement. |
| `productListItems` | Tableau de produits qui ont été ajoutés au panier. |
| `productListItems.SKU` | Unité de gestion des stocks. Identifiant unique du produit. |
| `productListItems.name` | Nom d’affichage ou nom lisible du produit. |
| `productListItems.priceTotal` | Prix total de l’article de ligne de produit. |
| `productListItems.quantity` | Nombre d’unités de produits dans le panier. |
| `productListItems.discountAmount` | Indique le montant de la remise appliquée. |
| `productListItems.currencyCode` | La variable [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) code de devise utilisé, par exemple `USD` ou `EUR`. |
| `productListItems.productImageUrl` | URL de l’image principale du produit. |
| `productListItems.selectedOptions` | Champ utilisé pour un produit configurable. |
| `productListItems.selectedOptions.attribute` | Identifie un attribut du produit configurable, tel que `size` ou `color`. |
| `productListItems.selectedOptions.value` | Identifie la valeur de l’attribut, telle que `small` ou `black`. |

### removeFromCart

| Description | Nom de l’événement XDM |
|---|---|
| Déclenché chaque fois qu’un produit est supprimé ou que la quantité d’un produit dans le panier est décrémentée. | `commerce.productListRemovals` |

#### Données collectées à partir de removeFromCart

Le tableau suivant décrit les données collectées pour cet événement.

| Champ | Description |
|---|---|
| `commerce.productListRemovals` | Indique si un produit a été supprimé du panier. Une valeur de `1` indique qu’un produit a été supprimé du panier. |
| `commerce.cart.cartID` | Identifiant unique qui identifie le panier du client. |
| `commerce.commerceScope` | Indique l’emplacement d’un événement (affichage en magasin, magasin, site web, etc.). |
| `commerce.commerceScope.environmentID` | Identifiant de l’environnement. ID alphanumérique de 32 chiffres séparés par des tirets. |
| `commerce.commerceScope.storeCode` | Code de magasin unique. Vous pouvez avoir de nombreux magasins par site web. |
| `commerce.commerceScope.storeViewCode` | Code d’affichage de magasin unique. Vous pouvez avoir de nombreuses vues de magasin par magasin. |
| `commerce.commerceScope.websiteCode` | Code unique du site web. Vous pouvez avoir de nombreux sites Web dans un environnement. |
| `productListItems` | Tableau de produits qui ont été ajoutés au panier. |
| `productListItems.SKU` | Unité de gestion des stocks. Identifiant unique du produit. |
| `productListItems.name` | Nom d’affichage ou nom lisible du produit. |
| `productListItems.priceTotal` | Prix total de l’article de ligne de produit. |
| `productListItems.quantity` | Nombre d’unités de produits dans le panier. |
| `productListItems.discountAmount` | Indique le montant de la remise appliquée. |
| `productListItems.currencyCode` | La variable [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) code de devise utilisé, par exemple `USD` ou `EUR`. |
| `productListItems.productImageUrl` | URL de l’image principale du produit. |
| `productListItems.selectedOptions` | Champ utilisé pour un produit configurable. |
| `productListItems.selectedOptions.attribute` | Identifie un attribut du produit configurable, tel que `size` ou `color`. |
| `productListItems.selectedOptions.value` | Identifie la valeur de l’attribut, telle que `small` ou `black`. |

### shoppingCartView

| Description | Nom de l’événement XDM |
|---|---|
| Déclenché lors du chargement d’une page de panier. | `commerce.productListViews` |

#### Données collectées à partir de shoppingCartView

Le tableau suivant décrit les données collectées pour cet événement.

| Champ | Description |
|---|---|
| `commerce.productListViews` | Indique si une liste de produits a été consultée. |
| `commerce.cart.cartID` | Identifiant unique qui identifie le panier du client. |
| `commerce.commerceScope` | Indique l’emplacement d’un événement (affichage en magasin, magasin, site web, etc.). |
| `commerce.commerceScope.environmentID` | Identifiant de l’environnement. ID alphanumérique de 32 chiffres séparés par des tirets. |
| `commerce.commerceScope.storeCode` | Code de magasin unique. Vous pouvez avoir de nombreux magasins par site web. |
| `commerce.commerceScope.storeViewCode` | Code d’affichage de magasin unique. Vous pouvez avoir de nombreuses vues de magasin par magasin. |
| `commerce.commerceScope.websiteCode` | Code unique du site web. Vous pouvez avoir de nombreux sites Web dans un environnement. |
| `productListItems` | Tableau de produits qui ont été ajoutés au panier. |
| `productListItems.SKU` | Unité de gestion des stocks. Identifiant unique du produit. |
| `productListItems.name` | Nom d’affichage ou nom lisible du produit. |
| `productListItems.priceTotal` | Prix total de l’article de ligne de produit. |
| `productListItems.quantity` | Nombre d’unités de produits dans le panier. |
| `productListItems.discountAmount` | Indique le montant de la remise appliquée. |
| `productListItems.currencyCode` | La variable [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) code de devise utilisé, par exemple `USD` ou `EUR`. |
| `productListItems.productImageUrl` | URL de l’image principale du produit. |
| `productListItems.selectedOptions` | Champ utilisé pour un produit configurable. |
| `productListItems.selectedOptions.attribute` | Identifie un attribut du produit configurable, tel que `size` ou `color`. |
| `productListItems.selectedOptions.value` | Identifie la valeur de l’attribut, telle que `small` ou `black`. |

### pageView

| Description | Nom de l’événement XDM |
|---|---|
| Déclenché lors du chargement d’une page. | `web.webpagedetails.pageViews` |

#### Données collectées à partir de pageView

Le tableau suivant décrit les données collectées pour cet événement.

| Champ | Description |
|---|---|
| `web.webPageDetails.pageViews` | Indique si une page a été chargée. A `value` de `1` indique que la page a été chargée. |
| `web.webPageDetails.URL` | URL normative ou habituelle de la page web. Il peut s’agir de l’URL réelle utilisée pour atteindre la page, qui serait enregistrée à l’aide de `Web Link`. |
| `web.webPageDetails.name` | Nom normatif de la page web. Ce nom n’est pas nécessairement le titre de la page ou directement associé au contenu de la page, mais il est utilisé pour organiser les pages d’un site à des fins de classification. |
| `web.webReferrer.URL` | URL de la page web visitée par un acheteur avant de cliquer sur un lien vers votre site. |
| `commerce.commerceScope` | Indique l’emplacement d’un événement (affichage en magasin, magasin, site web, etc.). |
| `commerce.commerceScope.environmentID` | Identifiant de l’environnement. ID alphanumérique de 32 chiffres séparés par des tirets. |
| `commerce.commerceScope.storeCode` | Code de magasin unique. Vous pouvez avoir de nombreux magasins par site web. |
| `commerce.commerceScope.storeViewCode` | Code d’affichage de magasin unique. Vous pouvez avoir de nombreuses vues de magasin par magasin. |
| `commerce.commerceScope.websiteCode` | Code unique du site web. Vous pouvez avoir de nombreux sites Web dans un environnement. |

### productPageView

| Description | Nom de l’événement XDM |
|---|---|
| Déclenché lors du chargement d’une page de produits. | `commerce.productViews` |

#### Données collectées à partir de productPageView

Le tableau suivant décrit les données collectées pour cet événement.

| Champ | Description |
|---|---|
| `commerce.productViews` | Indique si le produit a été consulté. |
| `commerce.commerceScope` | Indique l’emplacement d’un événement (affichage en magasin, magasin, site web, etc.). |
| `commerce.commerceScope.environmentID` | Identifiant de l’environnement. ID alphanumérique de 32 chiffres séparés par des tirets. |
| `commerce.commerceScope.storeCode` | Code de magasin unique. Vous pouvez avoir de nombreux magasins par site web. |
| `commerce.commerceScope.storeViewCode` | Code d’affichage de magasin unique. Vous pouvez avoir de nombreuses vues de magasin par magasin. |
| `commerce.commerceScope.websiteCode` | Code unique du site web. Vous pouvez avoir de nombreux sites Web dans un environnement. |
| `productListItems` | Tableau de produits qui ont été ajoutés au panier. |
| `productListItems.SKU` | Unité de gestion des stocks. Identifiant unique du produit. |
| `productListItems.name` | Nom d’affichage ou nom lisible du produit. |
| `productListItems.priceTotal` | Prix total de l’article de ligne de produit. |
| `productListItems.quantity` | Nombre d’unités de produits dans le panier. |
| `productListItems.discountAmount` | Indique le montant de la remise appliquée. |
| `productListItems.currencyCode` | La variable [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) code de devise utilisé, par exemple `USD` ou `EUR`. |
| `productListItems.productImageUrl` | URL de l’image principale du produit. |
| `productListItems.selectedOptions` | Champ utilisé pour un produit configurable. |
| `productListItems.selectedOptions.attribute` | Identifie un attribut du produit configurable, tel que `size` ou `color`. |
| `productListItems.selectedOptions.value` | Identifie la valeur de l’attribut, telle que `small` ou `black`. |

### startCheckout

| Description | Nom de l’événement XDM |
|---|---|
| Déclenché lorsque l’acheteur clique sur un bouton de passage en caisse. | `commerce.checkouts` |

#### Données collectées à partir de startCheckout

Le tableau suivant décrit les données collectées pour cet événement.

| Champ | Description |
|---|---|
| `commerce.checkouts` | Indique si une action s’est produite au cours du processus de passage en caisse. |
| `commerce.cart.cartID` | Identifiant unique qui identifie le panier du client. |
| `commerce.commerceScope` | Indique l’emplacement d’un événement (affichage en magasin, magasin, site web, etc.). |
| `commerce.commerceScope.environmentID` | Identifiant de l’environnement. ID alphanumérique de 32 chiffres séparés par des tirets. |
| `commerce.commerceScope.storeCode` | Code de magasin unique. Vous pouvez avoir de nombreux magasins par site web. |
| `commerce.commerceScope.storeViewCode` | Code d’affichage de magasin unique. Vous pouvez avoir de nombreuses vues de magasin par magasin. |
| `commerce.commerceScope.websiteCode` | Code unique du site web. Vous pouvez avoir de nombreux sites Web dans un environnement. |
| `productListItems` | Tableau de produits qui ont été ajoutés au panier. |
| `productListItems.SKU` | Unité de gestion des stocks. Identifiant unique du produit. |
| `productListItems.name` | Nom d’affichage ou nom lisible du produit. |
| `productListItems.priceTotal` | Prix total de l’article de ligne de produit. |
| `productListItems.quantity` | Nombre d’unités de produits dans le panier. |
| `productListItems.discountAmount` | Indique le montant de la remise appliquée. |
| `productListItems.currencyCode` | La variable [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) code de devise utilisé, par exemple `USD` ou `EUR`. |
| `productListItems.productImageUrl` | URL de l’image principale du produit. |
| `productListItems.selectedOptions` | Champ utilisé pour un produit configurable. |
| `productListItems.selectedOptions.attribute` | Identifie un attribut du produit configurable, tel que `size` ou `color`. |
| `productListItems.selectedOptions.value` | Identifie la valeur de l’attribut, telle que `small` ou `black`. |

### completeCheckout

| Description | Nom de l’événement XDM |
|---|---|
| Déclenché lorsque l’acheteur commande. | `commerce.purchases` |

#### Données collectées depuis completeCheckout

Le tableau suivant décrit les données collectées pour cet événement.

| Champ | Description |
|---|---|
| `commerce.purchases` | Indique si une commande a été acceptée. |
| `commerce.order` | Contient des informations sur la commande passée pour un ou plusieurs produits. |
| `commerce.order.purchaseID` | Identifiant unique attribué par le vendeur pour cet achat ou ce contrat. Il n’existe aucune garantie que l’identifiant est unique. |
| `commerce.order.payments` | Liste des paiements pour cette commande. |
| `commerce.order.payments.paymentTransactionID` | Identifiant unique de cette transaction de paiement. |
| `commerce.order.payments.paymentAmount` | Valeur du paiement. |
| `commerce.order.payments.paymentType` | Mode de paiement de cette commande. Les options sont les suivantes : `cash`, `credit_card`, `debit_card`, `gift_card`, `check`, `paypal`, `wire_transfer`, `credit_card_reference`, `other`. |
| `commerce.order.payments.currencyCode` | La variable [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) code de devise utilisé, par exemple `USD` ou `EUR`. |
| `commerce.order.taxAmount` | Montant de l&#39;impôt payé par l&#39;acheteur dans le cadre du paiement final. |
| `commerce.order.discountAmount` | Indique le montant de remise appliqué à la commande entière. |
| `commerce.order.createdDate` | Heure et date de création d’une commande dans le système commercial. Par exemple : `2022-10-15T20:20:39+00:00`. |
| `commerce.shipping` | Informations d’expédition pour un ou plusieurs produits. |
| `commerce.shipping.shippingMethod` | Mode d’expédition choisi par le client, tel que la livraison standard, la livraison accélérée, la prise en charge en magasin, etc. |
| `commerce.shipping.shippingAmount` | Le montant que le client a dû payer pour l’expédition. |  | `shipping` | Informations d’expédition pour un ou plusieurs produits. |
| `commerce.shipping.currencyCode` | La variable [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) code de devise utilisé, par exemple `USD` ou `EUR`. |
| `commerce.commerceScope` | Indique l’emplacement d’un événement (affichage en magasin, magasin, site web, etc.). |
| `commerce.commerceScope.environmentID` | Identifiant de l’environnement. ID alphanumérique de 32 chiffres séparés par des tirets. |
| `commerce.commerceScope.storeCode` | Code de magasin unique. Vous pouvez avoir de nombreux magasins par site web. |
| `commerce.commerceScope.storeViewCode` | Code d’affichage de magasin unique. Vous pouvez avoir de nombreuses vues de magasin par magasin. |
| `commerce.commerceScope.websiteCode` | Code unique du site web. Vous pouvez avoir de nombreux sites Web dans un environnement. |
| `personalEmail` | Adresse électronique personnelle. |
| `personalEmail.address` | L’adresse technique, par exemple : `name@domain.com` comme généralement défini dans la norme RFC2822 et les normes ultérieures. |
| `productListItems` | Tableau de produits qui ont été ajoutés au panier. |
| `productListItems.SKU` | Unité de gestion des stocks. Identifiant unique du produit. |
| `productListItems.name` | Nom d’affichage ou nom lisible du produit. |
| `productListItems.priceTotal` | Prix total de l’article de ligne de produit. |
| `productListItems.quantity` | Nombre d’unités de produits dans le panier. |
| `productListItems.discountAmount` | Indique le montant de la remise appliquée. |
| `productListItems.productImageUrl` | URL de l’image principale du produit. |
| `productListItems.selectedOptions` | Champ utilisé pour un produit configurable. |
| `productListItems.selectedOptions.attribute` | Identifie un attribut du produit configurable, tel que `size` ou `color`. |
| `productListItems.selectedOptions.value` | Identifie la valeur de l’attribut, telle que `small` ou `black`. |

## Événements de profil

Les événements de profil incluent des informations de compte, telles que `signIn`, `signOut`, `createAccount`, et `editAccount`. Ces données permettent de renseigner les détails clés des clients nécessaires pour mieux définir les segments ou exécuter des campagnes marketing, par exemple si vous souhaitez cibler les acheteurs qui vivent à New York.

### signIn

| Description | Nom de l’événement XDM |
|---|---|
| Déclenché lorsqu’un acheteur tente de se connecter. | `userAccount.login` |

>[!NOTE]
>
> Cet événement est déclenché lorsque l’action spécifique est tentée. Cela n’indique pas que l’action a réussi.

#### Données collectées à partir de signIn

Le tableau suivant décrit les données collectées pour cet événement.

| Champ | Description |
|---|---|
| `person` | Acteur, contact ou propriétaire individuel. |
| `person.accountID` | Capture l’ID du compte d’utilisateur. |
| `person.accountType` | Capture le type de compte d’utilisateur, tel que `Personal` ou `Company`, le cas échéant. |
| `person.personalEmailID` | L’adresse technique, par exemple : `name@domain.com` comme généralement défini dans la norme RFC2822 et les normes ultérieures. |
| `personalEmail` | Capture les coordonnées : un e-mail et les informations associées. |
| `personalEmail.address` | L’adresse technique, par exemple : `name@domain.com` comme généralement défini dans la norme RFC2822 et les normes ultérieures. |
| `userAccount` | Indique les détails de fidélité, les préférences, les processus de connexion et d’autres préférences de compte. |
| `userAccount.login` | Indique si un visiteur a tenté de se connecter. |
| `commerce.commerceScope` | Indique l’emplacement d’un événement (affichage en magasin, magasin, site web, etc.). |
| `commerce.commerceScope.environmentID` | Identifiant de l’environnement. ID alphanumérique de 32 chiffres séparés par des tirets. |
| `commerce.commerceScope.storeCode` | Code de magasin unique. Vous pouvez avoir de nombreux magasins par site web. |
| `commerce.commerceScope.storeViewCode` | Code d’affichage de magasin unique. Vous pouvez avoir de nombreuses vues de magasin par magasin. |
| `commerce.commerceScope.websiteCode` | Code unique du site web. Vous pouvez avoir de nombreux sites Web dans un environnement. |

### signOut

| Description | Nom de l’événement XDM |
|---|---|
| Déclenché lorsqu’un acheteur tente de se déconnecter. | `userAccount.logout` |

>[!NOTE]
>
> Cet événement est déclenché lorsque l’action spécifique est tentée. Cela n’indique pas que l’action a réussi.

#### Données collectées à partir de la déconnexion

Le tableau suivant décrit les données collectées pour cet événement.

| Champ | Description |
|---|---|
| `userAccount` | Indique les détails de fidélité, les préférences, les processus de connexion et d’autres préférences de compte. |
| `userAccount.logout` | Indique si un visiteur a tenté de se déconnecter. |
| `commerce.commerceScope` | Indique l’emplacement d’un événement (affichage en magasin, magasin, site web, etc.). |
| `commerce.commerceScope.environmentID` | Identifiant de l’environnement. ID alphanumérique de 32 chiffres séparés par des tirets. |
| `commerce.commerceScope.storeCode` | Code de magasin unique. Vous pouvez avoir de nombreux magasins par site web. |
| `commerce.commerceScope.storeViewCode` | Code d’affichage de magasin unique. Vous pouvez avoir de nombreuses vues de magasin par magasin. |
| `commerce.commerceScope.websiteCode` | Code unique du site web. Vous pouvez avoir de nombreux sites Web dans un environnement. |

### createAccount

| Description | Nom de l’événement XDM |
|---|---|
| Déclenché lorsqu’un acheteur tente de créer un compte. | `userAccount.createProfile` |

>[!NOTE]
>
> Cet événement est déclenché lorsque l’action spécifique est tentée. Cela n’indique pas que l’action a réussi.

#### Données collectées à partir de createAccount

Le tableau suivant décrit les données collectées pour cet événement.

| Champ | Description |
|---|---|
| `person` | Acteur, contact ou propriétaire individuel. |
| `person.accountID` | Capture l’ID du compte d’utilisateur. |
| `person.accountType` | Capture le type de compte d’utilisateur, tel que `Personal` ou `Company`, le cas échéant. |
| `person.personalEmailID` | L’adresse technique, par exemple : `name@domain.com` comme généralement défini dans la norme RFC2822 et les normes ultérieures. |
| `personalEmail` | Capture les coordonnées : un e-mail et les informations associées. |
| `personalEmail.address` | L’adresse technique, par exemple : `name@domain.com` comme généralement défini dans la norme RFC2822 et les normes ultérieures. |
| `userAccount` | Indique les détails de fidélité, les préférences, les processus de connexion et d’autres préférences de compte. |
| `userAccount.updateProfile` | Indique si un utilisateur a mis à jour son profil de compte. |
| `commerce.commerceScope` | Indique l’emplacement d’un événement (affichage en magasin, magasin, site web, etc.). |
| `commerce.commerceScope.environmentID` | Identifiant de l’environnement. ID alphanumérique de 32 chiffres séparés par des tirets. |
| `commerce.commerceScope.storeCode` | Code de magasin unique. Vous pouvez avoir de nombreux magasins par site web. |
| `commerce.commerceScope.storeViewCode` | Code d’affichage de magasin unique. Vous pouvez avoir de nombreuses vues de magasin par magasin. |
| `commerce.commerceScope.websiteCode` | Code unique du site web. Vous pouvez avoir de nombreux sites Web dans un environnement. |

### editAccount

| Description | Nom de l’événement XDM |
|---|---|
| Déclenché lorsqu’un acheteur tente de modifier un compte. | `userAccount.updateProfile` |

>[!NOTE]
>
> Cet événement est déclenché lorsque l’action spécifique est tentée. Cela n’indique pas que l’action a réussi.

#### Données collectées à partir de editAccount

Le tableau suivant décrit les données collectées pour cet événement.

| Champ | Description |
|---|---|
| `person` | Acteur, contact ou propriétaire individuel. |
| `person.accountID` | Capture l’ID du compte d’utilisateur. |
| `person.accountType` | Capture le type de compte d’utilisateur, tel que `Personal` ou `Company`, le cas échéant. |
| `person.personalEmailID` | L’adresse technique, par exemple : `name@domain.com` comme généralement défini dans la norme RFC2822 et les normes ultérieures. |
| `personalEmail` | Capture les coordonnées : un e-mail et les informations associées. |
| `personalEmail.address` | L’adresse technique, par exemple : `name@domain.com` comme généralement défini dans la norme RFC2822 et les normes ultérieures. |
| `userAccount` | Indique les détails de fidélité, les préférences, les processus de connexion et d’autres préférences de compte. |
| `userAccount.updateProfile` | Indique si un utilisateur a mis à jour son profil de compte. |
| `commerce.commerceScope` | Indique l’emplacement d’un événement (affichage en magasin, magasin, site web, etc.). |
| `commerce.commerceScope.environmentID` | Identifiant de l’environnement. ID alphanumérique de 32 chiffres séparés par des tirets. |
| `commerce.commerceScope.storeCode` | Code de magasin unique. Vous pouvez avoir de nombreux magasins par site web. |
| `commerce.commerceScope.storeViewCode` | Code d’affichage de magasin unique. Vous pouvez avoir de nombreuses vues de magasin par magasin. |
| `commerce.commerceScope.websiteCode` | Code unique du site web. Vous pouvez avoir de nombreux sites Web dans un environnement. |

## Recherche d’événements

Les événements de recherche fournissent des données pertinentes pour l’intention de l’acheteur. L’aperçu de l’intention d’un acheteur permet aux marchands de voir comment les acheteurs recherchent des articles, ce sur quoi ils cliquent, et en fin de compte achètent ou abandonnent. Vous pouvez, par exemple, utiliser ces données si vous souhaitez cibler les acheteurs existants qui recherchent votre meilleur produit, mais n’achètent jamais le produit.

Utilisez la variable `searchRequest.id` et `searchResponse.id` des champs figurant dans les deux `searchRequestSent` et `searchResponseReceived` pour effectuer une référence croisée à une requête de recherche vers la réponse de recherche correspondante.

### searchRequestSent

| Description | Nom de l’événement XDM |
|---|---|
| Déclenché par les événements suivants dans la fenêtre contextuelle &quot;Rechercher lorsque vous tapez&quot; :<br><br>Appuyez sur Entrée, puis cliquez sur _Afficher tout_<br><br> Déclenché par les événements suivants sur les pages de résultats de recherche :<br><br>Sélectionnez un filtre, puis Modifiez l’ordre de tri (_Trier par_), Modifier la direction du tri (ascendant ou descendant), Modifier le nombre de résultats par page (_Afficher le nombre par page_), Accédez à la page suivante, à la page précédente, à une autre page. | `searchRequest` |

>[!NOTE]
>
>Les événements de recherche ne sont pas pris en charge sur une édition Adobe Commerce Enterprise avec l’extension B2B installée.

#### Données collectées à partir de searchRequestSent

Le tableau suivant décrit les données collectées pour cet événement.

| Champ | Description |
|---|---|
| `searchRequest` | Indique si une requête de recherche a été envoyée. |
| `searchRequest.id` | L’identifiant unique de cette requête de recherche spécifique. |
| `searchRequest.value` | Valeur quantifiable de la requête. |
| `siteSearch` | Contient des informations sur la recherche. |
| `siteSearch.filter` | Indique si des filtres ont été appliqués pour limiter les résultats de la recherche. |
| `siteSearch.filter.attribute` (filter) | La facette d’un élément utilisée pour déterminer s’il doit être inclus dans les résultats de recherche. |
| `siteSearch.filter.isRange` | Si la valeur est true, les valeurs indiquent les points de fin d’une plage de valeurs acceptable. |
| `siteSearch.filter.value` | Valeur d’attribut utilisée pour déterminer les éléments qui sont inclus dans les résultats de recherche. |
| `siteSearch.sort` | Indique le mode de tri des résultats de recherche. |
| `siteSearch.sort.attribute` (sort) | Attribut utilisé pour trier les éléments dans les résultats de recherche. |
| `siteSearch.sort.order` | Ordre dans lequel renvoyer les résultats de la recherche. |
| `siteSearch.query` | Termes recherchés. |
| `commerce.commerceScope` | Indique l’emplacement d’un événement (affichage en magasin, magasin, site web, etc.). |
| `commerce.commerceScope.environmentID` | Identifiant de l’environnement. ID alphanumérique de 32 chiffres séparés par des tirets. |
| `commerce.commerceScope.storeCode` | Code de magasin unique. Vous pouvez avoir de nombreux magasins par site web. |
| `commerce.commerceScope.storeViewCode` | Code d’affichage de magasin unique. Vous pouvez avoir de nombreuses vues de magasin par magasin. |
| `commerce.commerceScope.websiteCode` | Code unique du site web. Vous pouvez avoir de nombreux sites Web dans un environnement. |

### searchResponseReceived

| Description | Nom de l’événement XDM |
|---|---|
| Déclenché lorsque la recherche en direct renvoie les résultats de la fenêtre contextuelle &quot;Rechercher lorsque vous tapez&quot; ou de la page des résultats de la recherche. | `searchResponse` |

>[!NOTE]
>
>Les événements de recherche ne sont pas pris en charge sur une édition Adobe Commerce Enterprise avec l’extension B2B installée.

#### Données collectées à partir de searchResponseReceived

Le tableau suivant décrit les données collectées pour cet événement.

| Champ | Description |
|---|---|
| `searchResponse` | Indique si une réponse de recherche a été reçue. |
| `searchResponse.id` | L’identifiant unique de cette réponse de recherche spécifique. |
| `searchResponse.value` | Valeur quantifiable de la réponse. |
| `siteSearch.numberOfResults` | Nombre de produits renvoyés. |
| `siteSearch.suggestions` | Tableau de chaînes qui incluent les noms des produits et des catégories existant dans le catalogue et similaires à la requête de recherche. |
| `productListItems` | Tableau de produits qui ont été ajoutés au panier. |
| `productListItems.SKU` | Unité de gestion des stocks. Identifiant unique du produit. |
| `productListItems.name` | Nom d’affichage ou nom lisible du produit. |
| `productListItems.productImageUrl` | URL de l’image principale du produit. |
| `commerce.commerceScope` | Indique l’emplacement d’un événement (affichage en magasin, magasin, site web, etc.). |
| `commerce.commerceScope.environmentID` | Identifiant de l’environnement. ID alphanumérique de 32 chiffres séparés par des tirets. |
| `commerce.commerceScope.storeCode` | Code de magasin unique. Vous pouvez avoir de nombreux magasins par site web. |
| `commerce.commerceScope.storeViewCode` | Code d’affichage de magasin unique. Vous pouvez avoir de nombreuses vues de magasin par magasin. |
| `commerce.commerceScope.websiteCode` | Code unique du site web. Vous pouvez avoir de nombreux sites Web dans un environnement. |

## Événements B2B

![B2B pour Adobe Commerce](../assets/b2b.svg) Pour les marchands B2B, vous devez [install](install.md#install-the-b2b-extension) la valeur `experience-platform-connector-b2b` pour activer ces événements.

Les événements B2B contiennent [liste des demandes](https://experienceleague.adobe.com/docs/commerce-admin/b2b/requisition-lists/requisition-lists.html) des informations, par exemple si une liste de demandes d’achat a été créée, ajoutée ou supprimée. En suivant les événements spécifiques aux listes de commandes, vous pouvez identifier les produits que vos clients achètent fréquemment et créer des campagnes basées sur ces données.

### createRequestList

| Description | Nom de l’événement XDM |
|---|---|
| Déclenché lorsqu’un acheteur crée une liste de demandes d’achat. | `commerce.requisitionListOpens` |

#### Données collectées à partir de createRequestList

Le tableau suivant décrit les données collectées pour cet événement.

| Champ | Description |
|---|---|
| `commerce.requisitionListOpens` | Indique l’initialisation d’une nouvelle liste de demandes d’achat. |
| `commerce.requisitionList` | Propriétés de la liste de demandes créée par le client. |
| `commerce.requisitionList.ID` | Identifiant unique de la liste des demandes. |
| `commerce.requisitionList.name` | Nom de la liste des demandes spécifiée par le client. |
| `commerce.requisitionList.description` | Description de la liste des demandes spécifiée par le client. |
| `commerce.commerceScope` | Indique l’emplacement d’un événement (affichage en magasin, magasin, site web, etc.). |
| `commerce.commerceScope.environmentID` | Identifiant de l’environnement. ID alphanumérique de 32 chiffres séparés par des tirets. |
| `commerce.commerceScope.storeCode` | Code de magasin unique. Vous pouvez avoir de nombreux magasins par site web. |
| `commerce.commerceScope.storeViewCode` | Code d’affichage de magasin unique. Vous pouvez avoir de nombreuses vues de magasin par magasin. |
| `commerce.commerceScope.websiteCode` | Code unique du site web. Vous pouvez avoir de nombreux sites Web dans un environnement. |

### addToRequestList

| Description | Nom de l’événement XDM |
|---|---|
| Déclenché lorsqu’un acheteur ajoute un produit à une liste de demande existante ou lors de la création d’une liste. | `commerce.requisitionListAdds` |

#### Données collectées à partir de addToRequestList

Le tableau suivant décrit les données collectées pour cet événement.

| Champ | Description |
|---|---|
| `commerce.requisitionListAdds` | Indique l’ajout d’un ou de plusieurs produits à une liste de demandes d’achat. |
| `commerce.requisitionList` | Propriétés de la liste de demandes créée par le client. |
| `commerce.requisitionList.ID` | Identifiant unique de la liste des demandes. |
| `commerce.requisitionList.name` | Nom de la liste des demandes spécifiée par le client. |
| `commerce.requisitionList.description` | Description de la liste des demandes spécifiée par le client. |
| `commerce.commerceScope` | Indique l’emplacement d’un événement (affichage en magasin, magasin, site web, etc.). |
| `commerce.commerceScope.environmentID` | Identifiant de l’environnement. ID alphanumérique de 32 chiffres séparés par des tirets. |
| `commerce.commerceScope.storeCode` | Code de magasin unique. Vous pouvez avoir de nombreux magasins par site web. |
| `commerce.commerceScope.storeViewCode` | Code d’affichage de magasin unique. Vous pouvez avoir de nombreuses vues de magasin par magasin. |
| `commerce.commerceScope.websiteCode` | Code unique du site web. Vous pouvez avoir de nombreux sites Web dans un environnement. |
| `productListItems` | Tableau de produits qui ont été ajoutés à la liste des demandes d’acquisition. |
| `productListItems.SKU` | Unité de gestion des stocks. Identifiant unique du produit. |
| `productListItems.name` | Nom d’affichage ou nom lisible du produit. |
| `productListItems.priceTotal` | Prix total de l’article de ligne de produit. |
| `productListItems.quantity` | Nombre d’unités de produits dans le panier. |
| `productListItems.discountAmount` | Indique le montant de la remise appliquée. |
| `productListItems.currencyCode` | La variable [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) code de devise utilisé, par exemple `USD` ou `EUR`. |
| `productListItems.selectedOptions` | Champ utilisé pour un produit configurable. |
| `productListItems.selectedOptions.attribute` | Identifie un attribut du produit configurable, tel que `size` ou `color`. |
| `productListItems.selectedOptions.value` | Identifie la valeur de l’attribut, telle que `small` ou `black`. |

### removeFromRequestList

| Description | Nom de l’événement XDM |
|---|---|
| Déclenché lorsqu’un acheteur supprime un produit d’une liste de demandes d’achat. | `commerce.requisitionListRemovals` |

#### Données collectées à partir de removeFromRequestList

Le tableau suivant décrit les données collectées pour cet événement.

| Champ | Description |
|---|---|
| `commerce.requsitionListRemovals` | Indique la suppression d’un ou de plusieurs produits d’une liste de demandes d’achat. |
| `commerce.requisitionList` | Propriétés de la liste de demandes créée par le client. |
| `commerce.requisitionList.ID` | Identifiant unique de la liste des demandes. |
| `commerce.requisitionList.name` | Nom de la liste des demandes spécifiée par le client. |
| `commerce.requisitionList.description` | Description de la liste des demandes spécifiée par le client. |
| `commerce.commerceScope` | Indique l’emplacement d’un événement (affichage en magasin, magasin, site web, etc.). |
| `commerce.commerceScope.environmentID` | Identifiant de l’environnement. ID alphanumérique de 32 chiffres séparés par des tirets. |
| `commerce.commerceScope.storeCode` | Code de magasin unique. Vous pouvez avoir de nombreux magasins par site web. |
| `commerce.commerceScope.storeViewCode` | Code d’affichage de magasin unique. Vous pouvez avoir de nombreuses vues de magasin par magasin. |
| `commerce.commerceScope.websiteCode` | Code unique du site web. Vous pouvez avoir de nombreux sites Web dans un environnement. |
| `productListItems` | Tableau de produits qui ont été ajoutés à la liste des demandes d’acquisition. |
| `productListItems.SKU` | Unité de gestion des stocks. Identifiant unique du produit. |
| `productListItems.name` | Nom d’affichage ou nom lisible du produit. |
| `productListItems.priceTotal` | Prix total de l’article de ligne de produit. |
| `productListItems.quantity` | Nombre d’unités de produits dans le panier. |
| `productListItems.discountAmount` | Indique le montant de la remise appliquée. |
| `productListItems.currencyCode` | La variable [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) code de devise utilisé, par exemple `USD` ou `EUR`. |
| `productListItems.selectedOptions` | Champ utilisé pour un produit configurable. |
| `productListItems.selectedOptions.attribute` | Identifie un attribut du produit configurable, tel que `size` ou `color`. |
| `productListItems.selectedOptions.value` | Identifie la valeur de l’attribut, telle que `small` ou `black`. |

### deleteRequestList

| Description | Nom de l’événement XDM |
|---|---|
| Déclenché lorsqu’un acheteur supprime une liste de demandes d’achat. | `commerce.requisitionListDeletes` |

#### Données collectées à partir de deleteRequestList

Le tableau suivant décrit les données collectées pour cet événement.

| Champ | Description |
|---|---|
| `commerce.requisitionListDeletes` | Indique qu’une liste de demandes d’achat a été supprimée. |
| `commerce.requisitionList` | Propriétés de la liste de demandes créée par le client. |
| `commerce.requisitionList.ID` | Identifiant unique de la liste des demandes. |
| `commerce.requisitionList.name` | Nom de la liste des demandes spécifiée par le client. |
| `commerce.requisitionList.description` | Description de la liste des demandes spécifiée par le client. |
| `commerce.commerceScope` | Indique l’emplacement d’un événement (affichage en magasin, magasin, site web, etc.). |
| `commerce.commerceScope.environmentID` | Identifiant de l’environnement. ID alphanumérique de 32 chiffres séparés par des tirets. |
| `commerce.commerceScope.storeCode` | Code de magasin unique. Vous pouvez avoir de nombreux magasins par site web. |
| `commerce.commerceScope.storeViewCode` | Code d’affichage de magasin unique. Vous pouvez avoir de nombreuses vues de magasin par magasin. |
| `commerce.commerceScope.websiteCode` | Code unique du site web. Vous pouvez avoir de nombreux sites Web dans un environnement. |

## Événements de back-office

Les événements back-office contiennent des informations sur l’état d’une commande, par exemple si une commande a été passée, annulée, remboursée, expédiée ou terminée. Les données collectées par ces événements côté serveur affichent une vue 360 de la commande du client. Cette vue permet aux commerçants de mieux cibler ou analyser l’état complet de la commande lors du développement de campagnes marketing. Vous pouvez, par exemple, repérer des tendances dans certaines catégories de produits qui se portent bien à différents moments de l’année. Des vêtements d’hiver qui se vendent mieux pendant les mois les plus froids ou certaines couleurs de produits qui intéressent les acheteurs au fil des ans. En outre, les données sur l’état de la commande peuvent vous aider à calculer la valeur client sur la durée de vie en comprenant la propension d’un acheteur à effectuer des conversions en fonction des commandes précédentes.

>[!NOTE]
>
>Tous les événements back-office incluent [`identityMap`](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html) qui indique l’adresse électronique de l’acheteur. En incluant ces données de profil dans chaque événement, vous n’avez pas besoin d’importer de compte d’utilisateur distinct depuis Adobe Commerce.

### orderPlaced

| Description | Nom de l’événement XDM |
|---|---|
| Déclenché lorsqu’un acheteur commande. | `commerce.backofficeOrderPlaced` |

#### Données collectées à partir de orderPlaced

Le tableau suivant décrit les données collectées pour cet événement.

| Champ | Description |
|---|---|
| `commerce.order` | Contient des informations sur la commande. |
| `commerce.order.purchaseID` | Identifiant unique attribué par le vendeur pour cet achat ou ce contrat. Il n’existe aucune garantie que l’identifiant est unique. |
| `commerce.order.payments` | Liste des paiements pour cette commande. |
| `commerce.order.payments.paymentTransactionID` | Identifiant unique de cette transaction de paiement. |
| `commerce.order.payments.paymentAmount` | Valeur du paiement. |
| `commerce.order.payments.paymentType` | Mode de paiement de cette commande. Valeurs comptées et personnalisées autorisées. |
| `commerce.order.payments.currencyCode` | La variable [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) code de devise utilisé, par exemple `USD` ou `EUR`. |
| `commerce.order.taxAmount` | Montant de l&#39;impôt payé par l&#39;acheteur dans le cadre du paiement final. |
| `commerce.order.discountAmount` | Indique le montant de remise appliqué à la commande entière. |
| `commerce.order.createdDate` | Heure et date de création d’une commande dans le système commercial. Par exemple : `2022-10-15T20:20:39+00:00`. |
| `commerce.order.currencyCode` | Code de devise ISO 4217 utilisé pour les totaux de commande. |
| `commerce.shipping` | Informations d’expédition pour un ou plusieurs produits. |
| `commerce.shipping.shippingMethod` | Mode d’expédition choisi par le client, tel que la livraison standard, la livraison accélérée, la prise en charge en magasin, etc. |
| `commerce.shipping.shippingAmount` | Le montant que le client a dû payer pour l’expédition. |
| `commerce.shipping.currencyCode` | Code de devise ISO 4217 utilisé pour le total de la livraison. |
| `commerce.commerceScope` | Indique l’emplacement d’un événement (affichage en magasin, magasin, site web, etc.). |
| `commerce.commerceScope.environmentID` | Identifiant de l’environnement. ID alphanumérique de 32 chiffres séparés par des tirets. |
| `commerce.commerceScope.storeCode` | Code de magasin unique. Vous pouvez avoir de nombreux magasins par site web. |
| `commerce.commerceScope.storeViewCode` | Code d’affichage de magasin unique. Vous pouvez avoir de nombreuses vues de magasin par magasin. |
| `commerce.commerceScope.websiteCode` | Code unique du site web. Vous pouvez avoir de nombreux sites Web dans un environnement. |
| `commerce.billing.address` | Adresse postale de facturation. |
| `commerce.billing.address.street1` | Principal des informations sur le niveau de la rue, le numéro de l’appartement, le numéro de la rue et le nom de la rue |
| `commerce.billing.address.street2` | Champ supplémentaire pour les informations au niveau de la rue. |
| `commerce.billing.address.city` | Nom de la ville. |
| `commerce.billing.address.state` | Nom de l’état. C&#39;est un champ de forme libre. |
| `commerce.billing.address.postalCode` | Code postal de l’emplacement. Les codes postaux ne sont pas disponibles pour tous les pays. Dans certains pays, ce champ ne contiendra qu&#39;une partie du code postal. |
| `commerce.billing.address.country` | Nom du territoire administré par le gouvernement. Autre que `xdm:countryCode`, il s’agit d’un champ de forme libre qui peut avoir le nom du pays dans n’importe quelle langue. |
| `personalEmail` | Adresse électronique personnelle. |
| `personalEmail.address` | L’adresse technique, par exemple : `name@domain.com` comme généralement défini dans la norme RFC2822 et les normes ultérieures. |
| `productListItems` | Tableau de produits dans la commande. |
| `productListItems.id` | Identifiant de l’élément de ligne pour cette entrée de produit. |
| `productListItems.SKU` | Unité de gestion des stocks. Identifiant unique du produit. |
| `productListItems.name` | Nom d’affichage ou nom lisible du produit. |
| `productListItems.priceTotal` | Prix total de l’article de ligne de produit. |
| `productListItems.quantity` | Nombre d’unités de produits dans le panier. |
| `productListItems.discountAmount` | Indique le montant de la remise appliquée. |
| `productListItems.currencyCode` | La variable [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) code de devise utilisé, par exemple `USD` ou `EUR`. |
| `productListItems.selectedOptions` | Champ utilisé pour un produit configurable. |
| `productListItems.selectedOptions.attribute` | Identifie un attribut du produit configurable, tel que `size` ou `color`. |
| `productListItems.selectedOptions.value` | Identifie la valeur de l’attribut, telle que `small` ou `black`. |
| `productListItems.categories` | Contient des informations sur la catégorie d’un produit. |
| `productListItems.categories.id` | Identifiant unique de la catégorie. |
| `productListItems.categories.name` | Nom de la catégorie. |
| `productListItems.categories.path` | Chemin d’accès à la catégorie. |
| `productListItems.productImageUrl` | URL de l’image principale du produit. |

### orderInvotered

| Description | Nom de l’événement XDM |
|---|---|
| Déclenché lorsqu’un marchand envoie une facture pour demander le paiement. | `commerce.backofficeOrderInvoiced` |

#### Données collectées à partir de orderInvotered

Le tableau suivant décrit les données collectées pour cet événement.

| Champ | Description |
|---|---|
| `commerce.order` | Contient des informations sur la commande. |
| `commerce.order.purchaseID` | Identifiant unique attribué par le vendeur pour cet achat ou ce contrat. Il n’existe aucune garantie que l’identifiant est unique. |
| `commerce.order.priceTotal` | Le prix total de cette commande une fois toutes les remises et taxes appliquées. |
| `commerce.order.currencyCode` | Code de devise ISO 4217 utilisé pour les totaux de commande. |
| `commerce.order.purchaseOrderNumber` | Identifiant unique attribué par l’acheteur pour cet achat ou ce contrat. |
| `commerce.order.payments` | Liste des paiements pour cette commande. |
| `commerce.order.payments.currencyCode` | La variable [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) code de devise utilisé, par exemple `USD` ou `EUR`. |
| `commerce.order.payments.paymentType` | Mode de paiement de cette commande. Valeurs comptées et personnalisées autorisées. |
| `commerce.order.payments.paymentAmount` | Valeur du paiement. |
| `commerce.shipping` | Informations d’expédition pour un ou plusieurs produits. |
| `commerce.shipping.shippingMethod` | Mode d’expédition choisi par le client, tel que la livraison standard, la livraison accélérée, la prise en charge en magasin, etc. |
| `commerce.shipping.shippingAmount` | Le montant que le client a dû payer pour l’expédition. |
| `commerce.commerceScope` | Indique l’emplacement d’un événement (affichage en magasin, magasin, site web, etc.). |
| `commerce.commerceScope.environmentID` | Identifiant de l’environnement. ID alphanumérique de 32 chiffres séparés par des tirets. |
| `commerce.commerceScope.storeCode` | Code de magasin unique. Vous pouvez avoir de nombreux magasins par site web. |
| `commerce.commerceScope.storeViewCode` | Code d’affichage de magasin unique. Vous pouvez avoir de nombreuses vues de magasin par magasin. |
| `commerce.commerceScope.websiteCode` | Code unique du site web. Vous pouvez avoir de nombreux sites Web dans un environnement. |
| `personalEmail` | Adresse électronique personnelle. |
| `personalEmail.address` | L’adresse technique, par exemple : `name@domain.com` comme généralement défini dans la norme RFC2822 et les normes ultérieures. |
| `productListItems` | Tableau de produits dans la commande. |
| `productListItems.id` | Identifiant de l’élément de ligne pour cette entrée de produit. |
| `productListItems.SKU` | Unité de gestion des stocks. Identifiant unique du produit. |
| `productListItems.name` | Nom d’affichage ou nom lisible du produit. |
| `productListItems.priceTotal` | Prix total de l’article de ligne de produit. |
| `productListItems.quantity` | Nombre d’unités de produits dans le panier. |
| `productListItems.discountAmount` | Indique le montant de la remise appliquée. |
| `productListItems.categories` | Contient des informations sur la catégorie d’un produit. |
| `productListItems.categories.id` | Identifiant unique de la catégorie. |
| `productListItems.categories.name` | Nom de la catégorie. |
| `productListItems.categories.path` | Chemin d’accès à la catégorie. |

### orderItemsShipped

| Description | Nom de l’événement XDM |
|---|---|
| Déclenché lorsqu’une commande est expédiée. | `commerce.backofficeOrderItemsShipped` |

#### Données collectées à partir de orderItemsShipped

Le tableau suivant décrit les données collectées pour cet événement.

| Champ | Description |
|---|---|
| `commerce.order` | Contient des informations sur la commande. |
| `commerce.order.purchaseID` | Identifiant unique attribué par le vendeur pour cet achat ou ce contrat. Il n’existe aucune garantie que l’identifiant est unique. |
| `commerce.order.payments` | Liste des paiements pour cette commande. |
| `commerce.order.payments.paymentTransactionID` | Identifiant unique de cette transaction de paiement. |
| `commerce.order.payments.paymentAmount` | Valeur du paiement. |
| `commerce.order.payments.paymentType` | Mode de paiement de cette commande. Valeurs comptées et personnalisées autorisées. |
| `commerce.order.payments.currencyCode` | La variable [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) code de devise utilisé, par exemple `USD` ou `EUR`. |
| `commerce.order.priceTotal` | Le prix total de cette commande une fois toutes les remises et taxes appliquées. |
| `commerce.order.purchaseOrderNumber` | Identifiant unique attribué par l’acheteur pour cet achat ou ce contrat. |
| `commerce.order.currencyCode` | La variable [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) code de devise utilisé, par exemple `USD` ou `EUR`. |
| `commerce.order.lastUpdatedDate` | Heure à laquelle un enregistrement de commande particulier est mis à jour pour la dernière fois dans le système commercial. |
| `commerce.shipping` | Informations d’expédition pour un ou plusieurs produits. |
| `commerce.shipping.shippingMethod` | Mode d’expédition choisi par le client, tel que la livraison standard, la livraison accélérée, la prise en charge en magasin, etc. |
| `commerce.shipping.shippingAmount` | Le montant que le client a dû payer pour l’expédition. |
| `commerce.shipping.address` | Adresse de transport physique. |
| `commerce.shipping.address.street1` | Informations au niveau de la rue par Principal, numéro d’appartement, numéro de rue et nom de rue. |
| `commerce.shipping.address.street2` | Informations facultatives sur la rue, deuxième ligne. |
| `commerce.shipping.address.city` | Nom de la ville. |
| `commerce.shipping.address.state` | Nom de l’État. C&#39;est un champ de forme libre. |
| `commerce.shipping.address.postalCode` | Code postal de l’emplacement. Les codes postaux ne sont pas disponibles pour tous les pays. Dans certains pays, ce champ ne contiendra qu&#39;une partie du code postal. |
| `commerce.shipping.address.country` | Nom du territoire administré par le gouvernement. Autre que `xdm:countryCode`, il s’agit d’un champ de forme libre qui peut avoir le nom du pays dans n’importe quelle langue. |
| `commerce.shipping.currencyCode` | La variable [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) code de devise utilisé, par exemple `USD` ou `EUR`. |
| `commerce.shipping.trackingNumber` | Numéro de suivi fourni par le transporteur pour l’expédition d’un article de commande. |
| `commerce.shipping.trackingURL` | URL permettant de suivre l’état de livraison d’un article de commande. |
| `commerce.shipping.shipDate` | Date à laquelle un ou plusieurs articles d’une commande sont expédiés. |
| `commerce.commerceScope` | Indique l’emplacement d’un événement (affichage en magasin, magasin, site web, etc.). |
| `commerce.commerceScope.environmentID` | Identifiant de l’environnement. ID alphanumérique de 32 chiffres séparés par des tirets. |
| `commerce.commerceScope.storeCode` | Code de magasin unique. Vous pouvez avoir de nombreux magasins par site web. |
| `commerce.commerceScope.storeViewCode` | Code d’affichage de magasin unique. Vous pouvez avoir de nombreuses vues de magasin par magasin. |
| `commerce.commerceScope.websiteCode` | Code unique du site web. Vous pouvez avoir de nombreux sites Web dans un environnement. |
| `commerce.billing.address` | Adresse postale de facturation. |
| `commerce.billing.address.street1` | Principal des informations sur le niveau de la rue, le numéro de l’appartement, le numéro de la rue et le nom de la rue |
| `commerce.billing.address.street2` | Champ supplémentaire pour les informations au niveau de la rue. |
| `commerce.billing.address.city` | Nom de la ville. |
| `commerce.billing.address.state` | Nom de l’état. C&#39;est un champ de forme libre. |
| `commerce.billing.address.postalCode` | Code postal de l’emplacement. Les codes postaux ne sont pas disponibles pour tous les pays. Dans certains pays, ce champ ne contiendra qu&#39;une partie du code postal. |
| `commerce.billing.address.country` | Nom du territoire administré par le gouvernement. Autre que `xdm:countryCode`, il s’agit d’un champ de forme libre qui peut avoir le nom du pays dans n’importe quelle langue. |
| `personalEmail` | Adresse électronique personnelle. |
| `personalEmail.address` | L’adresse technique, par exemple : `name@domain.com` comme généralement défini dans la norme RFC2822 et les normes ultérieures. |
| `productListItems` | Tableau de produits dans la commande. |
| `productListItems.SKU` | Unité de gestion des stocks. Identifiant unique du produit. |
| `productListItems.name` | Nom d’affichage ou nom lisible du produit. |
| `productListItems.priceTotal` | Prix total de l’article de ligne de produit. |
| `productListItems.quantity` | Nombre d’unités de produits dans le panier. |
| `productListItems.discountAmount` | Indique le montant de la remise appliquée. |
| `productListItems.currencyCode` | La variable [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) code de devise utilisé, par exemple `USD` ou `EUR`. |
| `productListItems.selectedOptions` | Champ utilisé pour un produit configurable. |
| `productListItems.selectedOptions.attribute` | Identifie un attribut du produit configurable, tel que `size` ou `color`. |
| `productListItems.selectedOptions.value` | Identifie la valeur de l’attribut, telle que `small` ou `black`. |
| `productListItems.categories` | Contient des informations sur la catégorie d’un produit. |
| `productListItems.categories.id` | Identifiant unique de la catégorie. |
| `productListItems.categories.name` | Nom de la catégorie. |
| `productListItems.categories.path` | Chemin d’accès à la catégorie. |

### orderCancelled

| Description | Nom de l’événement XDM |
|---|---|
| Déclenché lorsqu’un acheteur annule une commande. | `commerce.backofficeOrderCancelled` |

#### Données collectées à partir de orderCancelled

Le tableau suivant décrit les données collectées pour cet événement.

| Champ | Description |
|---|---|
| `commerce.order` | Contient des informations sur la commande. |
| `commerce.order.purchaseID` | Identifiant unique attribué par le vendeur pour cet achat ou ce contrat. Il n’existe aucune garantie que l’identifiant est unique. |
| `commerce.order.purchaseOrderNumber` | Identifiant unique attribué par l’acheteur pour cet achat ou ce contrat. |
| `commerce.order.cancelDate` | Date et heure auxquelles un acheteur annule une commande. |
| `commerce.order.lastUpdatedDate` | Heure à laquelle un enregistrement de commande particulier est mis à jour pour la dernière fois dans le système commercial. |
| `commerce.commerceScope` | Indique l’emplacement d’un événement (affichage en magasin, magasin, site web, etc.). |
| `commerce.commerceScope.environmentID` | Identifiant de l’environnement. ID alphanumérique de 32 chiffres séparés par des tirets. |
| `commerce.commerceScope.storeCode` | Code de magasin unique. Vous pouvez avoir de nombreux magasins par site web. |
| `commerce.commerceScope.storeViewCode` | Code d’affichage de magasin unique. Vous pouvez avoir de nombreuses vues de magasin par magasin. |
| `commerce.commerceScope.websiteCode` | Code unique du site web. Vous pouvez avoir de nombreux sites Web dans un environnement. |
| `personalEmail` | Adresse électronique personnelle. |
| `personalEmail.address` | L’adresse technique, par exemple : `name@domain.com` comme généralement défini dans la norme RFC2822 et les normes ultérieures. |

### orderLineItemRefunding

| Description | Nom de l’événement XDM |
|---|---|
| Déclenché lorsqu’un acheteur est remboursé pour un article renvoyé. | `commerce.backofficeCreditMemoIssued` |

#### Données collectées à partir de orderLineItemRefunding

Le tableau suivant décrit les données collectées pour cet événement.

| Champ | Description |
|---|---|
| `commerce.order` | Contient des informations sur la commande. |
| `commerce.order.purchaseID` | Identifiant unique attribué par le vendeur pour cet achat ou ce contrat. Il n’existe aucune garantie que l’identifiant est unique. |
| `commerce.order.lastUpdatedDate` | Heure à laquelle un enregistrement de commande particulier est mis à jour pour la dernière fois dans le système commercial. |
| `commerce.order.purchaseOrderNumber` | Identifiant unique attribué par l’acheteur pour cet achat ou ce contrat. |
| `commerce.refunds` | La liste des remboursements pour cette commande. |
| `commerce.refunds.transactionID` | Identifiant unique pour ce remboursement. |
| `commerce.refunds.refundAmount` | La valeur du remboursement. |
| `commerce.refunds.refundPaymentType` | Mode de paiement de cette commande. Valeurs comptées et personnalisées autorisées. |
| `commerce.refunds.currencyCode` | La variable [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) code de devise utilisé, par exemple `USD` ou `EUR`. |
| `personalEmail` | Adresse électronique personnelle. |
| `personalEmail.address` | L’adresse technique, par exemple : `name@domain.com` comme généralement défini dans la norme RFC2822 et les normes ultérieures. |
| `productListItems` | Tableau de produits dans la commande. |
| `productListItems.SKU` | Unité de gestion des stocks. Identifiant unique du produit. |
| `productListItems.name` | Nom d’affichage ou nom lisible du produit. |
| `productListItems.priceTotal` | Prix total de l’article de ligne de produit. |
| `productListItems.quantity` | Nombre d’unités de produits dans le panier. |
| `productListItems.discountAmount` | Indique le montant de la remise appliquée. |
| `productListItems.currencyCode` | La variable [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) code de devise utilisé, par exemple `USD` ou `EUR`. |
| `productListItems.selectedOptions` | Champ utilisé pour un produit configurable. |
| `productListItems.selectedOptions.attribute` | Identifie un attribut du produit configurable, tel que `size` ou `color`. |
| `productListItems.selectedOptions.value` | Identifie la valeur de l’attribut, telle que `small` ou `black`. |
| `productListItems.categories` | Contient des informations sur la catégorie d’un produit. |
| `productListItems.categories.id` | Identifiant unique de la catégorie. |
| `productListItems.categories.name` | Nom de la catégorie. |
| `productListItems.categories.path` | Chemin d’accès à la catégorie. |

### orderItemsReturnInitiated

| Description | Nom de l’événement XDM |
|---|---|
| Déclenché lorsqu’un acheteur demande de renvoyer un élément. | `commerce.backofficeOrderItemsReturnInitiated` |

#### Données collectées à partir de orderItemsReturnInitiated

Le tableau suivant décrit les données collectées pour cet événement.

| Champ | Description |
|---|---|
| `commerce.order` | Contient des informations sur la commande. |
| `commerce.order.purchaseID` | Identifiant unique attribué par le vendeur pour cet achat ou ce contrat. Il n’existe aucune garantie que l’identifiant est unique. |
| `commerce.order.returns` | Informations de la RMA (Return Merchandise Authorization) pour cette commande. |
| `commerce.order.returns.returnID` | Identifiant unique de cette RMA (Return Merchandise Authorization). |
| `commerce.order.returns.returnStatus` | État de la RAM (autorisation de marchandisage de retour), tel que En attente, Fermé, etc. |
| `commerce.commerceScope` | Indique l’emplacement d’un événement (affichage en magasin, magasin, site web, etc.). |
| `commerce.commerceScope.environmentID` | Identifiant de l’environnement. ID alphanumérique de 32 chiffres séparés par des tirets. |
| `commerce.commerceScope.storeCode` | Code de magasin unique. Vous pouvez avoir de nombreux magasins par site web. |
| `commerce.commerceScope.storeViewCode` | Code d’affichage de magasin unique. Vous pouvez avoir de nombreuses vues de magasin par magasin. |
| `commerce.commerceScope.websiteCode` | Code unique du site web. Vous pouvez avoir de nombreux sites Web dans un environnement. |
| `personalEmail` | Adresse électronique personnelle. |
| `personalEmail.address` | L’adresse technique, par exemple : `name@domain.com` comme généralement défini dans la norme RFC2822 et les normes ultérieures. |
| `productListItems` | Tableau de produits dans la commande. |
| `productListItems.SKU` | Unité de gestion des stocks. Identifiant unique du produit. |
| `productListItems.name` | Nom d’affichage ou nom lisible du produit. |
| `productListItems.quantity` | Nombre d’unités de produits dans le panier. |
| `productListItems.selectedOptions` | Champ utilisé pour un produit configurable. |
| `productListItems.selectedOptions.attribute` | Identifie un attribut du produit configurable, tel que `size` ou `color`. |
| `productListItems.selectedOptions.value` | Identifie la valeur de l’attribut, telle que `small` ou `black`. |
| `productListItems.categories` | Contient des informations sur la catégorie d’un produit. |
| `productListItems.categories.id` | Identifiant unique de la catégorie. |
| `productListItems.categories.name` | Nom de la catégorie. |
| `productListItems.categories.path` | Chemin d’accès à la catégorie. |
| `productListItems.returnItem` | Informations de la RMA (Return Merchandise Authorization) pour cet élément. |
| `productListItems.returnItem.returnStatus` | État de l’élément renvoyé, par exemple En attente, Approuvé, etc. |
| `productListItems.returnItem.returnReason` | Motif pour lequel un retour est demandé pour cet élément. |
| `productListItems.returnItem.returnItemCondition` | La condition de l’élément pour lequel le renvoi est demandé. |
| `productListItems.returnItem.returnResolution` | Résolution demandée de l’élément renvoyé, telle que Rembourser, Exchange, etc. |
| `productListItems.returnItem.returnQuantityRequested` | Numéro de cet élément que l’acheteur a demandé de renvoyer. |
| `productListItems.returnItem.returnQuantityAuthorized` | Numéro de cet élément autorisé à être renvoyé. |
| `productListItems.returnItem.eturnQuantityReceived` | Nombre d’éléments renvoyés reçus. |
| `productListItems.returnItem.returnQuantityApproved` | Numéro de cet élément avec le renvoi complet et approuvé. |

### orderItemReturnCompleted

| Description | Nom de l’événement XDM |
|---|---|
| Déclenché lorsqu’un article qu’un acheteur demandait de renvoyer est terminé. | `commerce.backofficeOrderItemsReturnCompleted` |

#### Données collectées à partir de orderItemReturnCompleted

Le tableau suivant décrit les données collectées pour cet événement.

| Champ | Description |
|---|---|
| `commerce.order` | Contient des informations sur la commande. |
| `commerce.order.purchaseID` | Identifiant unique attribué par le vendeur pour cet achat ou ce contrat. Il n’existe aucune garantie que l’identifiant est unique. |
| `commerce.order.returns` | Informations de la RMA (Return Merchandise Authorization) pour cette commande. |
| `commerce.order.returns.returnID` | Identifiant unique de cette RMA (Return Merchandise Authorization). |
| `commerce.order.returns.returnStatus` | État de la RAM (autorisation de marchandisage de retour), tel que En attente, Fermé, etc. |
| `commerce.commerceScope` | Indique l’emplacement d’un événement (affichage en magasin, magasin, site web, etc.). |
| `commerce.commerceScope.environmentID` | Identifiant de l’environnement. ID alphanumérique de 32 chiffres séparés par des tirets. |
| `commerce.commerceScope.storeCode` | Code de magasin unique. Vous pouvez avoir de nombreux magasins par site web. |
| `commerce.commerceScope.storeViewCode` | Code d’affichage de magasin unique. Vous pouvez avoir de nombreuses vues de magasin par magasin. |
| `commerce.commerceScope.websiteCode` | Code unique du site web. Vous pouvez avoir de nombreux sites Web dans un environnement. |
| `personalEmail` | Adresse électronique personnelle. |
| `personalEmail.address` | L’adresse technique, par exemple : `name@domain.com` comme généralement défini dans la norme RFC2822 et les normes ultérieures. |
| `productListItems` | Tableau de produits dans la commande. |
| `productListItems.SKU` | Unité de gestion des stocks. Identifiant unique du produit. |
| `productListItems.name` | Nom d’affichage ou nom lisible du produit. |
| `productListItems.selectedOptions` | Champ utilisé pour un produit configurable. |
| `productListItems.selectedOptions.attribute` | Identifie un attribut du produit configurable, tel que `size` ou `color`. |
| `productListItems.selectedOptions.value` | Identifie la valeur de l’attribut, telle que `small` ou `black`. |
| `productListItems.categories` | Contient des informations sur la catégorie d’un produit. |
| `productListItems.categories.id` | Identifiant unique de la catégorie. |
| `productListItems.categories.name` | Nom de la catégorie. |
| `productListItems.categories.path` | Chemin d’accès à la catégorie. |
| `productListItems.returnItem` | Informations de la RMA (Return Merchandise Authorization) pour cet élément. |
| `productListItems.returnItem.returnStatus` | État de l’élément renvoyé, par exemple En attente, Approuvé, etc. |
| `productListItems.returnItem.returnReason` | Motif pour lequel un retour est demandé pour cet élément. |
| `productListItems.returnItem.returnItemCondition` | La condition de l’élément pour lequel le renvoi est demandé. |
| `productListItems.returnItem.returnResolution` | Résolution demandée de l’élément renvoyé, telle que Rembourser, Exchange, etc. |
| `productListItems.returnItem.returnQuantityRequested` | Numéro de cet élément que l’acheteur a demandé de renvoyer. |
| `productListItems.returnItem.returnQuantityAuthorized` | Numéro de cet élément autorisé à être renvoyé. |
| `productListItems.returnItem.eturnQuantityReceived` | Nombre d’éléments renvoyés reçus. |
| `productListItems.returnItem.returnQuantityApproved` | Numéro de cet élément avec le renvoi complet et approuvé. |

### orderShipmentCompleted

| Description | Nom de l’événement XDM |
|---|---|
| Déclenché à la fin d’une expédition. | `commerce.backofficeOrderShipmentCompleted` |

#### Données collectées à partir de orderShipmentCompleted

Le tableau suivant décrit les données collectées pour cet événement.

| Champ | Description |
|---|---|
| `commerce.order` | Contient des informations sur la commande. |
| `commerce.order.purchaseID` | Identifiant unique attribué par le vendeur pour cet achat ou ce contrat. Il n’existe aucune garantie que l’identifiant est unique. |
| `commerce.order.payments` | Liste des paiements pour cette commande. |
| `commerce.order.payments.paymentTransactionID` | Identifiant unique de cette transaction de paiement. |
| `commerce.order.payments.paymentAmount` | Valeur du paiement. |
| `commerce.order.payments.paymentType` | Mode de paiement de cette commande. Valeurs comptées et personnalisées autorisées. |
| `commerce.order.payments.currencyCode` | La variable [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) code de devise utilisé, par exemple `USD` ou `EUR`. |
| `commerce.order.taxAmount` | Montant de l&#39;impôt payé par l&#39;acheteur dans le cadre du paiement final. |
| `commerce.order.createdDate` | Heure et date de création d’une commande dans le système commercial. Par exemple : `2022-10-15T20:20:39+00:00`. |
| `commerce.shipping` | Informations d’expédition pour un ou plusieurs produits. |
| `commerce.shipping.shippingMethod` | Mode d’expédition choisi par le client, tel que la livraison standard, la livraison accélérée, la prise en charge en magasin, etc. |
| `commerce.shipping.shippingAmount` | Le montant que le client a dû payer pour l’expédition. |
| `commerce.shipping.shipDate` | Date à laquelle un ou plusieurs articles d’une commande sont expédiés. |
| `commerce.shipping.address` | Adresse de transport physique. |
| `commerce.shipping.address.street1` | Informations au niveau de la rue par Principal, numéro d’appartement, numéro de rue et nom de rue. |
| `commerce.shipping.address.street2` | Informations facultatives sur la rue, deuxième ligne. |
| `commerce.shipping.address.city` | Nom de la ville. |
| `commerce.shipping.address.state` | Nom de l’État. C&#39;est un champ de forme libre. |
| `commerce.shipping.address.postalCode` | Code postal de l’emplacement. Les codes postaux ne sont pas disponibles pour tous les pays. Dans certains pays, ce champ ne contiendra qu&#39;une partie du code postal. |
| `commerce.shipping.address.country` | Nom du territoire administré par le gouvernement. Autre que `xdm:countryCode`, il s’agit d’un champ de forme libre qui peut avoir le nom du pays dans n’importe quelle langue. |
| `commerce.billing.address` | Adresse postale de facturation. |
| `commerce.billing.address.street1` | Principal des informations sur le niveau de la rue, le numéro de l’appartement, le numéro de la rue et le nom de la rue |
| `commerce.billing.address.street2` | Champ supplémentaire pour les informations au niveau de la rue. |
| `commerce.billing.address.city` | Nom de la ville. |
| `commerce.billing.address.state` | Nom de l’état. C&#39;est un champ de forme libre. |
| `commerce.billing.address.postalCode` | Code postal de l’emplacement. Les codes postaux ne sont pas disponibles pour tous les pays. Dans certains pays, ce champ ne contiendra qu&#39;une partie du code postal. |
| `commerce.billing.address.country` | Nom du territoire administré par le gouvernement. Autre que `xdm:countryCode`, il s’agit d’un champ de forme libre qui peut avoir le nom du pays dans n’importe quelle langue. |
| `personalEmail` | Adresse électronique personnelle. |
| `personalEmail.address` | L’adresse technique, par exemple : `name@domain.com` comme généralement défini dans la norme RFC2822 et les normes ultérieures. |
| `productListItems` | Tableau de produits dans la commande. |
| `productListItems.SKU` | Unité de gestion des stocks. Identifiant unique du produit. |
| `productListItems.name` | Nom d’affichage ou nom lisible du produit. |
| `productListItems.priceTotal` | Prix total de l’article de ligne de produit. |
| `productListItems.quantity` | Nombre d’unités de produits dans le panier. |
| `productListItems.discountAmount` | Indique le montant de la remise appliquée. |
| `productListItems.currencyCode` | La variable [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) code de devise utilisé, par exemple `USD` ou `EUR`. |
| `productListItems.selectedOptions` | Champ utilisé pour un produit configurable. |
| `productListItems.selectedOptions.attribute` | Identifie un attribut du produit configurable, tel que `size` ou `color`. |
| `productListItems.selectedOptions.value` | Identifie la valeur de l’attribut, telle que `small` ou `black`. |
| `productListItems.categories` | Contient des informations sur la catégorie d’un produit. |
| `productListItems.categories.id` | Identifiant unique de la catégorie. |
| `productListItems.categories.name` | Nom de la catégorie. |
| `productListItems.categories.path` | Chemin d’accès à la catégorie. |
