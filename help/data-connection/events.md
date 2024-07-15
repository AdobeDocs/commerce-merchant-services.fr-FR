---
title: Événements comportementaux
description: Découvrez les données que chaque événement comportemental capture.
exl-id: b0c88af3-29c1-4661-9901-3c6d134c2386
role: Admin, Developer
feature: Personalization, Integration, Eventing
source-git-commit: ace61fa579404962a9ca3eb97f61ed50bc43db52
workflow-type: tm+mt
source-wordcount: '4516'
ht-degree: 0%

---

# [!DNL Data Connection] événements comportementaux

Vous trouverez ci-dessous la liste des événements comportementaux Commerce disponibles lorsque vous installez l’extension [!DNL Data Connection]. Les données collectées par ces événements sont envoyées à Adobe Experience Platform. Vous pouvez également créer des [événements personnalisés](custom-events.md) pour collecter des données supplémentaires non fournies en standard.

Outre les données que les événements suivants collectent, vous obtenez également [d’autres données](https://experienceleague.adobe.com/docs/experience-platform/edge/data-collection/automatic-information.html) fournies par le SDK Web de Adobe Experience Platform.

Les événements comportementaux collectent des données comportementales anonymes de vos clients lorsqu’ils naviguent sur votre site. Vous pouvez utiliser les données collectées par ces événements pour créer des promotions et des campagnes ciblées sur un ensemble spécifique d’acheteurs.

>[!NOTE]
>
>Tous les événements comportementaux incluent le champ [`identityMap`](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html), qui inclut l’adresse électronique de l’acheteur, le cas échéant, et l’ECID.

## Événements Storefront

Les événements Storefront capturent des données provenant des interactions des clients sur le site et incluent des événements tels que [`addToCart`](#addtocart), [`pageView`](#pageview), [`createAccount`](#createaccount), [`editAccount`](#editaccount), [`startCheckout`](#startcheckout), [`completeCheckout`](#completecheckout), [`signIn`](#signin), [`signOut`](#signout), etc. Les événements Storefront s’appliquent uniquement aux produits simples et configurables.

### addToCart

| Description | Nom de l’événement XDM |
|---|---|
| Déclenché lorsqu’un produit est ajouté au panier ou lorsque la quantité d’un produit dans le panier est incrémentée. | `commerce.productListAdds` |

#### Données collectées à partir de addToCart

Le tableau suivant décrit les données collectées pour cet événement.

| Champ | Description |
|---|---|
| `channel` | Contient des informations sur la source des données. `_id` et `_type` contiennent tous deux [ espaces de noms ](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | L’identifiant unique du canal, tel que `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifie la source des données de canal, telles que `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `commerce.productListAdds` | Indique si un produit a été ajouté à un panier. Une valeur `1` indique qu’un produit a été ajouté. |
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
| `productListItems.currencyCode` | Code de devise [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) utilisé, par exemple `USD` ou `EUR`. |
| `productListItems.productImageUrl` | URL de l’image principale du produit. |
| `productListItems.selectedOptions` | Champ utilisé pour un produit configurable. |
| `productListItems.selectedOptions.attribute` | Identifie un attribut du produit configurable, tel que `size` ou `color`. |
| `productListItems.selectedOptions.value` | Identifie la valeur de l’attribut tel que `small` ou `black`. |

### openCart

| Description | Nom de l’événement XDM |
|---|---|
| Déclenché lors de la création d’un panier, c’est-à-dire lorsqu’un produit est ajouté à un panier vide. | `commerce.productListOpens` |

#### Données collectées à partir d’openCart

Le tableau suivant décrit les données collectées pour cet événement.

| Champ | Description |
|---|---|
| `channel` | Contient des informations sur la source des données. `_id` et `_type` contiennent tous deux [ espaces de noms ](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | L’identifiant unique du canal, tel que `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifie la source des données de canal, telles que `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `commerce.productListOpens` | Indique si un panier a été créé. Une valeur `1` indique qu’un panier a été créé. |
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
| `productListItems.currencyCode` | Code de devise [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) utilisé, par exemple `USD` ou `EUR`. |
| `productListItems.productImageUrl` | URL de l’image principale du produit. |
| `productListItems.selectedOptions` | Champ utilisé pour un produit configurable. |
| `productListItems.selectedOptions.attribute` | Identifie un attribut du produit configurable, tel que `size` ou `color`. |
| `productListItems.selectedOptions.value` | Identifie la valeur de l’attribut tel que `small` ou `black`. |

### removeFromCart

| Description | Nom de l’événement XDM |
|---|---|
| Déclenché chaque fois qu’un produit est supprimé ou que la quantité d’un produit dans le panier est décrémentée. | `commerce.productListRemovals` |

#### Données collectées à partir de removeFromCart

Le tableau suivant décrit les données collectées pour cet événement.

| Champ | Description |
|---|---|
| `channel` | Contient des informations sur la source des données. `_id` et `_type` contiennent tous deux [ espaces de noms ](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | L’identifiant unique du canal, tel que `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifie la source des données de canal, telles que `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `commerce.productListRemovals` | Indique si un produit a été supprimé du panier. Une valeur `1` indique qu’un produit a été supprimé du panier. |
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
| `productListItems.currencyCode` | Code de devise [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) utilisé, par exemple `USD` ou `EUR`. |
| `productListItems.productImageUrl` | URL de l’image principale du produit. |
| `productListItems.selectedOptions` | Champ utilisé pour un produit configurable. |
| `productListItems.selectedOptions.attribute` | Identifie un attribut du produit configurable, tel que `size` ou `color`. |
| `productListItems.selectedOptions.value` | Identifie la valeur de l’attribut tel que `small` ou `black`. |

### shoppingCartView

| Description | Nom de l’événement XDM |
|---|---|
| Déclenché lors du chargement d’une page de panier. | `commerce.productListViews` |

#### Données collectées à partir de shoppingCartView

Le tableau suivant décrit les données collectées pour cet événement.

| Champ | Description |
|---|---|
| `channel` | Contient des informations sur la source des données. `_id` et `_type` contiennent tous deux [ espaces de noms ](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | L’identifiant unique du canal, tel que `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifie la source des données de canal, telles que `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `commerce.productListViews` | Indique si une liste de produits a été consultée. |
| `commerce.cart.cartID` | Identifiant unique qui identifie le panier du client. |
| `commerce.commerceScope` | Indique l’emplacement d’un événement (affichage en magasin, magasin, site web, etc.). |
| `commerce.commerceScope.environmentID` | Identifiant de l’environnement. ID alphanumérique de 32 chiffres séparés par des tirets. |
| `commerce.commerceScope.storeCode` | Code de magasin unique. Vous pouvez avoir de nombreux magasins par site web. |
| `commerce.commerceScope.storeViewCode` | Code d’affichage de magasin unique. Vous pouvez avoir de nombreuses vues de magasin par magasin. |
| `commerce.commerceScope.websiteCode` | Code unique du site web. Vous pouvez avoir de nombreux sites Web dans un environnement. |
| `commerce.order` | Contient des informations sur la commande en attente d’un ou de plusieurs produits. |
| `commerce.order.discountAmount` | Indique le montant de remise appliqué à la commande entière. |
| `productListItems` | Tableau de produits qui ont été ajoutés au panier. |
| `productListItems.SKU` | Unité de gestion des stocks. Identifiant unique du produit. |
| `productListItems.name` | Nom d’affichage ou nom lisible du produit. |
| `productListItems.priceTotal` | Prix total de l’article de ligne de produit. |
| `productListItems.quantity` | Nombre d’unités de produits dans le panier. |
| `productListItems.discountAmount` | Indique le montant de la remise appliquée. |
| `productListItems.currencyCode` | Code de devise [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) utilisé, par exemple `USD` ou `EUR`. |
| `productListItems.productImageUrl` | URL de l’image principale du produit. |
| `productListItems.selectedOptions` | Champ utilisé pour un produit configurable. |
| `productListItems.selectedOptions.attribute` | Identifie un attribut du produit configurable, tel que `size` ou `color`. |
| `productListItems.selectedOptions.value` | Identifie la valeur de l’attribut tel que `small` ou `black`. |

### pageView

| Description | Nom de l’événement XDM |
|---|---|
| Déclenché lors du chargement d’une page. | `web.webpagedetails.pageViews` |

#### Données collectées à partir de pageView

Le tableau suivant décrit les données collectées pour cet événement.

| Champ | Description |
|---|---|
| `channel` | Contient des informations sur la source des données. `_id` et `_type` contiennent tous deux [ espaces de noms ](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | L’identifiant unique du canal, tel que `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifie la source des données de canal, telles que `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `web.webPageDetails.pageViews` | Indique si une page a été chargée. Un `value` de `1` indique que la page a été chargée. |
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
| `channel` | Contient des informations sur la source des données. `_id` et `_type` contiennent tous deux [ espaces de noms ](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | L’identifiant unique du canal, tel que `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifie la source des données de canal, telles que `"https://ns.adobe.com/xdm/channel-types/web"`. |
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
| `productListItems.currencyCode` | Code de devise [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) utilisé, par exemple `USD` ou `EUR`. |
| `productListItems.productImageUrl` | URL de l’image principale du produit. |
| `productListItems.selectedOptions` | Champ utilisé pour un produit configurable. |
| `productListItems.selectedOptions.attribute` | Identifie un attribut du produit configurable, tel que `size` ou `color`. |
| `productListItems.selectedOptions.value` | Identifie la valeur de l’attribut tel que `small` ou `black`. |

### startCheckout

| Description | Nom de l’événement XDM |
|---|---|
| Déclenché lorsque l’acheteur clique sur un bouton de passage en caisse. | `commerce.checkouts` |

#### Données collectées à partir de startCheckout

Le tableau suivant décrit les données collectées pour cet événement.

| Champ | Description |
|---|---|
| `channel` | Contient des informations sur la source des données. `_id` et `_type` contiennent tous deux [ espaces de noms ](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | L’identifiant unique du canal, tel que `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifie la source des données de canal, telles que `"https://ns.adobe.com/xdm/channel-types/web"`. |
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
| `productListItems.currencyCode` | Code de devise [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) utilisé, par exemple `USD` ou `EUR`. |
| `productListItems.productImageUrl` | URL de l’image principale du produit. |
| `productListItems.selectedOptions` | Champ utilisé pour un produit configurable. |
| `productListItems.selectedOptions.attribute` | Identifie un attribut du produit configurable, tel que `size` ou `color`. |
| `productListItems.selectedOptions.value` | Identifie la valeur de l’attribut tel que `small` ou `black`. |

### completeCheckout

| Description | Nom de l’événement XDM |
|---|---|
| Déclenché lorsque l’acheteur commande. | `commerce.purchases` |

#### Données collectées depuis completeCheckout

Le tableau suivant décrit les données collectées pour cet événement.

| Champ | Description |
|---|---|
| `channel` | Contient des informations sur la source des données. `_id` et `_type` contiennent tous deux [ espaces de noms ](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | L’identifiant unique du canal, tel que `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifie la source des données de canal, telles que `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `commerce.purchases` | Indique si une commande a été acceptée. |
| `commerce.order` | Contient des informations sur la commande passée pour un ou plusieurs produits. |
| `commerce.order.purchaseID` | Identifiant unique attribué par le vendeur pour cet achat ou ce contrat. Il n’existe aucune garantie que l’identifiant est unique. |
| `commerce.order.payments` | Liste des paiements pour cette commande. |
| `commerce.order.payments.paymentTransactionID` | Identifiant unique de cette transaction de paiement. |
| `commerce.order.payments.paymentAmount` | Valeur du paiement. |
| `commerce.order.payments.paymentType` | Mode de paiement de cette commande. Les options sont : `cash`, `credit_card`, `debit_card`, `gift_card`, `check`, `paypal`, `wire_transfer`, `credit_card_reference`, `other`. |
| `commerce.order.payments.currencyCode` | Code de devise [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) utilisé, par exemple `USD` ou `EUR`. |
| `commerce.order.taxAmount` | Montant de l&#39;impôt payé par l&#39;acheteur dans le cadre du paiement final. |
| `commerce.order.discountAmount` | Indique le montant de remise appliqué à la commande entière. |
| `commerce.order.createdDate` | Heure et date de création d’une commande dans le système commercial. Par exemple, `2022-10-15T20:20:39+00:00`. |
| `commerce.shipping` | Informations d’expédition pour un ou plusieurs produits. |
| `commerce.shipping.shippingMethod` | Mode d’expédition choisi par le client, tel que la livraison standard, la livraison accélérée, la prise en charge en magasin, etc. |
| `commerce.shipping.shippingAmount` | Le montant que le client a dû payer pour l’expédition. |  | `shipping` | Informations d’expédition pour un ou plusieurs produits. |
| `commerce.shipping.currencyCode` | Code de devise [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) utilisé, par exemple `USD` ou `EUR`. |
| `commerce.commerceScope` | Indique l’emplacement d’un événement (affichage en magasin, magasin, site web, etc.). |
| `commerce.commerceScope.environmentID` | Identifiant de l’environnement. ID alphanumérique de 32 chiffres séparés par des tirets. |
| `commerce.commerceScope.storeCode` | Code de magasin unique. Vous pouvez avoir de nombreux magasins par site web. |
| `commerce.commerceScope.storeViewCode` | Code d’affichage de magasin unique. Vous pouvez avoir de nombreuses vues de magasin par magasin. |
| `commerce.commerceScope.websiteCode` | Code unique du site web. Vous pouvez avoir de nombreux sites Web dans un environnement. |
| `personalEmail` | Adresse électronique personnelle. |
| `personalEmail.address` | Adresse technique, par exemple, `name@domain.com` telle que généralement définie dans la norme RFC2822 et les normes ultérieures. |
| `productListItems` | Tableau de produits qui ont été ajoutés au panier. |
| `productListItems.SKU` | Unité de gestion des stocks. Identifiant unique du produit. |
| `productListItems.name` | Nom d’affichage ou nom lisible du produit. |
| `productListItems.priceTotal` | Prix total de l’article de ligne de produit. |
| `productListItems.quantity` | Nombre d’unités de produits dans le panier. |
| `productListItems.discountAmount` | Indique le montant de la remise appliquée. |
| `productListItems.productImageUrl` | URL de l’image principale du produit. |
| `productListItems.selectedOptions` | Champ utilisé pour un produit configurable. |
| `productListItems.selectedOptions.attribute` | Identifie un attribut du produit configurable, tel que `size` ou `color`. |
| `productListItems.selectedOptions.value` | Identifie la valeur de l’attribut tel que `small` ou `black`. |

## Événements de profil client

Les événements de profil capturés depuis le storefront incluent des informations de compte, telles que `signIn`, `signOut`, `createAccount` et `editAccount`. Ces données permettent de renseigner les détails clés des clients nécessaires pour mieux définir les segments ou exécuter des campagnes marketing, comme envoyer des offres de réduction d’inscription, confirmer des changements de compte, etc. Des événements de profil similaires sont capturés à partir de [côté serveur](events-backoffice.md#customer-profile-events).

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
| `channel` | Contient des informations sur la source des données. `_id` et `_type` contiennent tous deux [ espaces de noms ](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | L’identifiant unique du canal, tel que `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifie la source des données de canal, telles que `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `person` | Acteur, contact ou propriétaire individuel. |
| `person.accountID` | Capture l’ID du compte d’utilisateur. |
| `person.accountType` | Capture le type de compte utilisateur, par exemple `Personal` ou `Company`, le cas échéant. |
| `person.personalEmailID` | Adresse technique, par exemple, `name@domain.com` telle que généralement définie dans la norme RFC2822 et les normes ultérieures. |
| `personalEmail` | Capture les coordonnées : un e-mail et les informations associées. |
| `personalEmail.address` | Adresse technique, par exemple, `name@domain.com` telle que généralement définie dans la norme RFC2822 et les normes ultérieures. |
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
| `channel` | Contient des informations sur la source des données. `_id` et `_type` contiennent tous deux [ espaces de noms ](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | L’identifiant unique du canal, tel que `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifie la source des données de canal, telles que `"https://ns.adobe.com/xdm/channel-types/web"`. |
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
| `channel` | Contient des informations sur la source des données. `_id` et `_type` contiennent tous deux [ espaces de noms ](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | L’identifiant unique du canal, tel que `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifie la source des données de canal, telles que `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `person` | Acteur, contact ou propriétaire individuel. |
| `person.accountID` | Capture l’ID du compte d’utilisateur. |
| `person.accountType` | Capture le type de compte utilisateur, par exemple `Personal` ou `Company`, le cas échéant. |
| `person.personalEmailID` | Adresse technique, par exemple, `name@domain.com` telle que généralement définie dans la norme RFC2822 et les normes ultérieures. |
| `personalEmail` | Capture les coordonnées : un e-mail et les informations associées. |
| `personalEmail.address` | Adresse technique, par exemple, `name@domain.com` telle que généralement définie dans la norme RFC2822 et les normes ultérieures. |
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
| `channel` | Contient des informations sur la source des données. `_id` et `_type` contiennent tous deux [ espaces de noms ](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | L’identifiant unique du canal, tel que `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifie la source des données de canal, telles que `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `person` | Acteur, contact ou propriétaire individuel. |
| `person.accountID` | Capture l’ID du compte d’utilisateur. |
| `person.accountType` | Capture le type de compte utilisateur, par exemple `Personal` ou `Company`, le cas échéant. |
| `person.personalEmailID` | Adresse technique, par exemple, `name@domain.com` telle que généralement définie dans la norme RFC2822 et les normes ultérieures. |
| `personalEmail` | Capture les coordonnées : un e-mail et les informations associées. |
| `personalEmail.address` | Adresse technique, par exemple, `name@domain.com` telle que généralement définie dans la norme RFC2822 et les normes ultérieures. |
| `userAccount` | Indique les détails de fidélité, les préférences, les processus de connexion et d’autres préférences de compte. |
| `userAccount.updateProfile` | Indique si un utilisateur a mis à jour son profil de compte. |
| `commerce.commerceScope` | Indique l’emplacement d’un événement (affichage en magasin, magasin, site web, etc.). |
| `commerce.commerceScope.environmentID` | Identifiant de l’environnement. ID alphanumérique de 32 chiffres séparés par des tirets. |
| `commerce.commerceScope.storeCode` | Code de magasin unique. Vous pouvez avoir de nombreux magasins par site web. |
| `commerce.commerceScope.storeViewCode` | Code d’affichage de magasin unique. Vous pouvez avoir de nombreuses vues de magasin par magasin. |
| `commerce.commerceScope.websiteCode` | Code unique du site web. Vous pouvez avoir de nombreux sites Web dans un environnement. |

## Recherche d’événements

Les événements de recherche fournissent des données pertinentes pour l’intention de l’acheteur. L’aperçu de l’intention d’un acheteur permet aux marchands de voir comment les acheteurs recherchent des articles, ce sur quoi ils cliquent, et en fin de compte achètent ou abandonnent. Vous pouvez, par exemple, utiliser ces données si vous souhaitez cibler les acheteurs existants qui recherchent votre meilleur produit, mais n’achètent jamais le produit. Vous devez installer l’extension [[!DNL Live Search]](../live-search/install.md) pour accéder à ces événements.

Utilisez les champs `searchRequest.id` et `searchResponse.id` trouvés dans les événements `searchRequestSent` et `searchResponseReceived` pour effectuer une référence croisée à une requête de recherche vers la réponse de recherche correspondante.

### searchRequestSent

| Description | Nom de l’événement XDM |
|---|---|
| Déclenché par les événements suivants dans la fenêtre contextuelle &quot;Rechercher en cours de frappe&quot; :<br><br>Appuyez sur Entrée, cliquez sur _Afficher tout_<br><br> Déclenché par les événements suivants sur les pages de résultats de recherche :<br><br>Sélectionnez un filtre, Modifiez l’ordre de tri (_Trier par_), Modifiez la direction du tri (ascendant ou descendant), modifiez le nombre de résultats par page (_Afficher # par page_), Accédez à la page suivante, à la page précédente, à une autre page. | `searchRequest` |

>[!NOTE]
>
>Les événements de recherche ne sont pas pris en charge sur une édition Adobe Commerce Enterprise avec l’extension B2B installée.

#### Données collectées à partir de searchRequestSent

Le tableau suivant décrit les données collectées pour cet événement.

| Champ | Description |
|---|---|
| `channel` | Contient des informations sur la source des données. `_id` et `_type` contiennent tous deux [ espaces de noms ](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | L’identifiant unique du canal, tel que `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifie la source des données de canal, telles que `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `searchRequest` | Indique si une requête de recherche a été envoyée. |
| `searchRequest.id` | L’identifiant unique de cette requête de recherche spécifique. |
| `searchRequest.value` | Valeur quantifiable de la requête. |
| `siteSearch` | Contient des informations sur la recherche. |
| `siteSearch.filter` | Indique si des filtres ont été appliqués pour limiter les résultats de la recherche. |
| `siteSearch.filter.attribute` (filtre) | La facette d’un élément utilisée pour déterminer s’il doit être inclus dans les résultats de recherche. |
| `siteSearch.filter.isRange` | Si la valeur est true, les valeurs indiquent les points de fin d’une plage de valeurs acceptable. |
| `siteSearch.filter.value` | Valeur d’attribut utilisée pour déterminer les éléments qui sont inclus dans les résultats de recherche. |
| `siteSearch.sort` | Indique le mode de tri des résultats de recherche. |
| `siteSearch.sort.attribute` (tri) | Attribut utilisé pour trier les éléments dans les résultats de recherche. |
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
| `channel` | Contient des informations sur la source des données. `_id` et `_type` contiennent tous deux [ espaces de noms ](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | L’identifiant unique du canal, tel que `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifie la source des données de canal, telles que `"https://ns.adobe.com/xdm/channel-types/web"`. |
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

![B2B pour Adobe Commerce](../assets/b2b.svg) Pour les commerçants B2B, vous devez [installer](install.md#install-the-b2b-extension) l’extension `experience-platform-connector-b2b` pour accéder à ces événements.

Les événements B2B contiennent des informations [liste de demandes](https://experienceleague.adobe.com/docs/commerce-admin/b2b/requisition-lists/requisition-lists.html), telles que si une liste de demandes a été créée, ajoutée ou supprimée. En suivant les événements spécifiques aux listes de commandes, vous pouvez identifier les produits que vos clients achètent fréquemment et créer des campagnes basées sur ces données.

### createRequestList

| Description | Nom de l’événement XDM |
|---|---|
| Déclenché lorsqu’un acheteur crée une liste de demandes d’achat. | `commerce.requisitionListOpens` |

#### Données collectées à partir de createRequestList

Le tableau suivant décrit les données collectées pour cet événement.

| Champ | Description |
|---|---|
| `channel` | Contient des informations sur la source des données. `_id` et `_type` contiennent tous deux [ espaces de noms ](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | L’identifiant unique du canal, tel que `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifie la source des données de canal, telles que `"https://ns.adobe.com/xdm/channel-types/web"`. |
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
| `channel` | Contient des informations sur la source des données. `_id` et `_type` contiennent tous deux [ espaces de noms ](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | L’identifiant unique du canal, tel que `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifie la source des données de canal, telles que `"https://ns.adobe.com/xdm/channel-types/web"`. |
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
| `productListItems.currencyCode` | Code de devise [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) utilisé, par exemple `USD` ou `EUR`. |
| `productListItems.selectedOptions` | Champ utilisé pour un produit configurable. |
| `productListItems.selectedOptions.attribute` | Identifie un attribut du produit configurable, tel que `size` ou `color`. |
| `productListItems.selectedOptions.value` | Identifie la valeur de l’attribut tel que `small` ou `black`. |

### removeFromRequestList

| Description | Nom de l’événement XDM |
|---|---|
| Déclenché lorsqu’un acheteur supprime un produit d’une liste de demandes d’achat. | `commerce.requisitionListRemovals` |

#### Données collectées à partir de removeFromRequestList

Le tableau suivant décrit les données collectées pour cet événement.

| Champ | Description |
|---|---|
| `channel` | Contient des informations sur la source des données. `_id` et `_type` contiennent tous deux [ espaces de noms ](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | L’identifiant unique du canal, tel que `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifie la source des données de canal, telles que `"https://ns.adobe.com/xdm/channel-types/web"`. |
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
| `productListItems.currencyCode` | Code de devise [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) utilisé, par exemple `USD` ou `EUR`. |
| `productListItems.selectedOptions` | Champ utilisé pour un produit configurable. |
| `productListItems.selectedOptions.attribute` | Identifie un attribut du produit configurable, tel que `size` ou `color`. |
| `productListItems.selectedOptions.value` | Identifie la valeur de l’attribut tel que `small` ou `black`. |

### deleteRequestList

| Description | Nom de l’événement XDM |
|---|---|
| Déclenché lorsqu’un acheteur supprime une liste de demandes d’achat. | `commerce.requisitionListDeletes` |

#### Données collectées à partir de deleteRequestList

Le tableau suivant décrit les données collectées pour cet événement.

| Champ | Description |
|---|---|
| `channel` | Contient des informations sur la source des données. `_id` et `_type` contiennent tous deux [ espaces de noms ](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | L’identifiant unique du canal, tel que `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifie la source des données de canal, telles que `"https://ns.adobe.com/xdm/channel-types/web"`. |
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
