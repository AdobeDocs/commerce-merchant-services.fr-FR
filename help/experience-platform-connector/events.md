---
title: Événements
description: Découvrez les données que chaque événement capture.
exl-id: b0c88af3-29c1-4661-9901-3c6d134c2386
source-git-commit: bd1cf8a3b4740594cf6b8678d899d771a886cb2e
workflow-type: tm+mt
source-wordcount: '1987'
ht-degree: 0%

---

# Événements de connecteur Experience Platform

Vous trouverez ci-dessous la liste des événements Commerce disponibles lorsque vous installez l’extension Experience Platform Connector. Les données collectées par ces événements sont envoyées à Adobe Experience Platform Edge. Vous pouvez également créer des [événements personnalisés](custom-events.md) pour collecter des données supplémentaires qui ne sont pas prêtes à l’emploi.

Outre les données collectées par les événements suivants, vous obtenez également [autres données](https://experienceleague.adobe.com/docs/experience-platform/edge/data-collection/automatic-information.html) fourni par le SDK Web de Adobe Experience Platform.

>[!NOTE]
>
>Tous les événements storefront incluent la variable `personID` qui est un identifiant unique de la personne.

## addToCart

Déclenché lorsqu’un produit est ajouté au panier ou lorsque la quantité d’un produit dans le panier est incrémentée.

### Nom de l’événement XDM

`commerce.productListAdds`

### Type

Storefront

### Données collectées

Le tableau suivant décrit les données collectées pour cet événement.

| Champ | Description |
|---|---|
| `productListAdds` | Indique si un produit a été ajouté à un panier. Une valeur de `1` indique qu’un produit a été ajouté. |
| `productListItems` | Tableau de produits ajoutés au panier |
| `SKU` | Unité de gestion des stocks. Identifiant unique du produit. |
| `name` | Nom d’affichage ou nom lisible du produit. |
| `priceTotal` | Prix total de l’article de ligne de produit |
| `quantity` | Nombre d’unités de produits ajoutées au panier |
| `discountAmount` | Indique le montant de remise appliqué |
| `currencyCode` | Le [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) devise du produit |
| `productImageUrl` | URL de l’image principale du produit |
| `selectedOptions` | Champ utilisé pour un produit configurable. `attribute` identifie un attribut du produit configurable, tel que `size` ou `color` et `value` identifie la valeur de l’attribut, telle que `small` ou `black`. |
| `cartID` | Identifiant unique qui identifie le panier du client |

## openCart

Déclenché lors de la création d’un panier, c’est-à-dire lorsqu’un produit est ajouté à un panier vide.

### Nom de l’événement XDM

`commerce.productListOpens`

### Type

Storefront

### Données collectées

Le tableau suivant décrit les données collectées pour cet événement.

| Champ | Description |
|---|---|
| `productListOpens` | Indique si un panier a été créé. Une valeur de `1` indique qu’un panier a été créé. |
| `productListItems` | Tableau de produits ajoutés au panier |
| `SKU` | Unité de gestion des stocks. Identifiant unique du produit. |
| `name` | Nom d’affichage ou nom lisible du produit. |
| `priceTotal` | Prix total de l’article de ligne de produit |
| `quantity` | Nombre d’unités de produits ajoutées au panier |
| `discountAmount` | Indique le montant de remise appliqué |
| `currencyCode` | Le [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) devise du produit |
| `productImageUrl` | URL de l’image principale du produit |
| `selectedOptions` | Champ utilisé pour un produit configurable. `attribute` identifie un attribut du produit configurable, tel que `size` ou `color` et `value` identifie la valeur de l’attribut, telle que `small` ou `black`. |
| `cartID` | Identifiant unique qui identifie le panier du client |

## removeFromCart

Déclenché chaque fois qu’un produit est supprimé ou que la quantité d’un produit dans le panier est décrémentée.

### Nom de l’événement XDM

`commerce.productListRemovals`

### Type

Storefront

### Données collectées

Le tableau suivant décrit les données collectées pour cet événement.

| Champ | Description |
|---|---|
| `productListRemovals` | Indique si un produit a été supprimé du panier. Une valeur de `1` indique qu’un produit a été supprimé du panier. |
| `productListItems` | Tableau de produits supprimés du panier |
| `SKU` | Unité de gestion des stocks. Identifiant unique du produit. |
| `name` | Nom d’affichage ou nom lisible du produit. |
| `priceTotal` | Prix total de l’article de ligne de produit |
| `quantity` | Nombre d’unités de produits supprimées du panier |
| `discountAmount` | Indique le montant de remise appliqué |
| `currencyCode` | Le [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) devise du produit |
| `productImageUrl` | URL de l’image principale du produit |
| `selectedOptions` | Champ utilisé pour un produit configurable. `attribute` identifie un attribut du produit configurable, tel que `size` ou `color` et `value` identifie la valeur de l’attribut, telle que `small` ou `black`. |
| `cartID` | Identifiant unique qui identifie le panier du client |

## shoppingCartView

Déclenché lors du chargement d’une page de panier.

### Nom de l’événement XDM

`commerce.productListViews`

### Type

Storefront

### Données collectées

Le tableau suivant décrit les données collectées pour cet événement.

| Champ | Description |
|---|---|
| `productListViews` | Indique si une liste de produits a été affichée |
| `productListItems` | Tableau de produits dans le panier |
| `SKU` | Unité de gestion des stocks. Identifiant unique du produit. |
| `name` | Nom d’affichage ou nom lisible du produit. |
| `priceTotal` | Prix total de l’article de ligne de produit |
| `quantity` | Nombre d’unités de produits dans le panier |
| `discountAmount` | Indique le montant de remise appliqué |
| `currencyCode` | Le [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) devise du produit |
| `productImageUrl` | URL de l’image principale du produit |
| `selectedOptions` | Champ utilisé pour un produit configurable. `attribute` identifie un attribut du produit configurable, tel que `size` ou `color` et `value` identifie la valeur de l’attribut, telle que `small` ou `black`. |
| `cartID` | Identifiant unique qui identifie le panier du client |

## pageView

Déclenché lors du chargement d’une page.

### Nom de l’événement XDM

`web.webpagedetails.pageViews`

### Type

Storefront

### Données collectées

Le tableau suivant décrit les données collectées pour cet événement.

| Champ | Description |
|---|---|
| `pageViews` | Indique si une page a été chargée. A `value` de `1` indique que la page a été chargée. |

## productPageView

Déclenché lors du chargement d’une page de produits.

### Nom de l’événement XDM

`commerce.productViews`

### Type

Storefront

### Données collectées

Le tableau suivant décrit les données collectées pour cet événement.

| Champ | Description |
|---|---|
| `productViews` | Indique si le produit a été consulté |
| `productListItems` | Tableau de produits dans le panier |
| `SKU` | Unité de gestion des stocks. Identifiant unique du produit. |
| `name` | Nom d’affichage ou nom lisible du produit. |
| `priceTotal` | Prix total de l’article de ligne de produit |
| `discountAmount` | Indique le montant de remise appliqué |
| `currencyCode` | Le [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) devise du produit |
| `productImageUrl` | URL de l’image principale du produit |
| `selectedOptions` | Champ utilisé pour un produit configurable. `attribute` identifie un attribut du produit configurable, tel que `size` ou `color` et `value` identifie la valeur de l’attribut, telle que `small` ou `black`. |

## startCheckout

Déclenché lorsque l’acheteur clique sur un bouton de passage en caisse.

### Nom de l’événement XDM

`commerce.checkouts`

### Type

Storefront

### Données collectées

Le tableau suivant décrit les données collectées pour cet événement.

| Champ | Description |
|---|---|
| `checkouts` | Indique si une action s’est produite pendant le processus de passage en caisse |
| `productListItems` | Tableau de produits dans le panier |
| `SKU` | Unité de gestion des stocks. Identifiant unique du produit. |
| `name` | Nom d’affichage ou nom lisible du produit. |
| `priceTotal` | Prix total de l’article de ligne de produit |
| `quantity` | Nombre d’unités de produits dans le panier |
| `discountAmount` | Indique le montant de remise appliqué |
| `currencyCode` | Le [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) devise du produit |
| `productImageUrl` | URL de l’image principale du produit |
| `selectedOptions` | Champ utilisé pour un produit configurable. `attribute` identifie un attribut du produit configurable, tel que `size` ou `color` et `value` identifie la valeur de l’attribut, telle que `small` ou `black`. |
| `cartID` | Identifiant unique qui identifie le panier du client |

## completeCheckout

Déclenché lorsque l’acheteur commande.

### Nom de l’événement XDM

`commerce.order`

### Type

Storefront

### Données collectées

Le tableau suivant décrit les données collectées pour cet événement.

| Champ | Description |
|---|---|
| `purchases` | Indique si une commande a été acceptée |
| `order` | Contient des informations sur la commande passée pour un ou plusieurs produits. |
| `purchaseID` | Identifiant unique attribué par le vendeur pour cet achat ou ce contrat. Il n’existe aucune garantie que l’identifiant est unique. |
| `orderType` | Indique le type de commande qui a été passé, tel que Passage en caisse ou Achat instantané |
| `payments` | Liste des paiements pour cette commande |
| `currencyCode` | Le [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) code de devise utilisé pour cet élément de paiement. Par exemple : `USD` ou `EUR`. |
| `paymentAmount` | Valeur du paiement |
| `paymentType` | Mode de paiement de cette commande. Les options sont les suivantes : `cash`, `credit_card`, `debit_card`, `gift_card`, `check`, `paypal`, `wire_transfer`, `credit_card_reference`, `other` |
| `transactionID` | L’identifiant de transaction unique de cet élément de paiement |
| `shipping` | Informations sur l’expédition d’un ou de plusieurs produits. |
| `shippingMethod` | Le mode d’expédition choisi par le client, tel que la livraison standard, la livraison accélérée, la prise en charge en magasin, etc. |
| `shippingAmount` | Le coût total de livraison des articles du panier. |
| `promotionID` | Identifiant unique de la promotion, le cas échéant |
| `productListItems` | Tableau de produits dans le panier |
| `SKU` | Unité de gestion des stocks. Identifiant unique du produit. |
| `name` | Nom d’affichage ou nom lisible du produit. |
| `priceTotal` | Prix total de l’article de ligne de produit |
| `quantity` | Nombre d’unités de produits dans le panier |
| `discountAmount` | Indique le montant de remise appliqué |
| `currencyCode` | Le [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) code de devise utilisé pour les totaux de commande. |
| `productImageUrl` | URL de l’image principale du produit |
| `selectedOptions` | Champ utilisé pour un produit configurable. `attribute` identifie un attribut du produit configurable, tel que `size` ou `color` et `value` identifie la valeur de l’attribut, telle que `small` ou `black`. |

## signIn

Déclenché lorsqu’un acheteur tente de se connecter.

>[!NOTE]
>
> Cet événement est déclenché lorsque l’action spécifique est tentée. Cela n’indique pas que l’action a réussi.

### Nom de l’événement XDM

`userAccount.login`

### Type

Profil

### Données collectées

Le tableau suivant décrit les données collectées pour cet événement.

| Champ | Description |
|---|---|
| `eventType` | Type d’événement Principal pour cet enregistrement de série temporelle, tel que : `userAccount.login` |
| `person` | Acteur, contact ou propriétaire individuel |
| `accountID` | Capture l’ID du compte d’utilisateur |
| `personalEmailID` | Indique l’identifiant unique de l’adresse électronique personnelle. |
| `address` | L’adresse technique, par exemple : `name@domain.com` comme couramment défini dans la norme RFC2822 et les normes ultérieures. |
| `userAccount` | Indique les détails de fidélité, les préférences, les processus de connexion et les autres préférences de compte. |
| `login` | Indique si un visiteur a tenté de se connecter. |

## signOut

Déclenché lorsqu’un acheteur tente de se déconnecter.

>[!NOTE]
>
> Cet événement est déclenché lorsque l’action spécifique est tentée. Cela n’indique pas que l’action a réussi.

### Nom de l’événement XDM

`userAccount.logout`

### Type

Profil

### Données collectées

Le tableau suivant décrit les données collectées pour cet événement.

| Champ | Description |
|---|---|
| `eventType` | Type d’événement Principal pour cet enregistrement de série temporelle, tel que : `userAccount.logout` |
| `userAccount` | Indique les détails de fidélité, les préférences, les processus de connexion et les autres préférences de compte. |
| `logout` | Indique si un visiteur a tenté de se déconnecter. |

## createAccount

Déclenché lorsqu’un acheteur tente de créer un compte.

>[!NOTE]
>
> Cet événement est déclenché lorsque l’action spécifique est tentée. Cela n’indique pas que l’action a réussi.

### Nom de l’événement XDM

`userAccount.createProfile`

### Type

Profil

### Données collectées

Le tableau suivant décrit les données collectées pour cet événement.

| Champ | Description |
|---|---|
| `eventType` | Type d’événement Principal pour cet enregistrement de série temporelle, tel que : `account.createProfile` |
| `person` | Acteur, contact ou propriétaire individuel |
| `accountID` | Capture l’ID du compte d’utilisateur |
| `accountType` | Capture le type de compte d’utilisateur, tel que `Personal` ou `Company`, le cas échéant |
| `personalEmailID` | Indique l’identifiant unique de l’adresse électronique personnelle. |
| `address` | L’adresse technique, par exemple : `name@domain.com` comme couramment défini dans la norme RFC2822 et les normes ultérieures. |
| `userAccount` | Indique les détails de fidélité, les préférences, les processus de connexion et les autres préférences de compte. |
| `createProfile` | Indique si un utilisateur a créé un profil de compte |

## editAccount

Déclenché lorsqu’un acheteur tente de modifier un compte.

>[!NOTE]
>
> Cet événement est déclenché lorsque l’action spécifique est tentée. Cela n’indique pas que l’action a réussi.

### Nom de l’événement XDM

`userAccount.updateProfile`

### Type

Profil

### Données collectées

Le tableau suivant décrit les données collectées pour cet événement.

| Champ | Description |
|---|---|
| `eventType` | Type d’événement Principal pour cet enregistrement de série temporelle, tel que : `account.updateProfile` |
| `person` | Acteur, contact ou propriétaire individuel |
| `accountID` | Capture l’ID du compte d’utilisateur |
| `accountType` | Capture le type de compte d’utilisateur, tel que `Personal` ou `Company`, le cas échéant |
| `personalEmailID` | Indique l’identifiant unique de l’adresse électronique personnelle. |
| `personalEmail` | Indique l’adresse électronique personnelle |
| `address` | L’adresse technique, par exemple : `name@domain.com` comme couramment défini dans la norme RFC2822 et les normes ultérieures. |
| `userAccount` | Indique les détails de fidélité, les préférences, les processus de connexion et les autres préférences de compte. |
| `updateProfile` | Indique si un utilisateur a mis à jour son profil de compte |

## searchRequestSent

Déclenché par les événements suivants dans la fenêtre contextuelle &quot;Rechercher lorsque vous tapez&quot; :

- Appuyez sur Entrée
- Cliquez sur _Afficher tout_

Déclenché par les événements suivants sur les pages de résultats de recherche :

- Sélectionner un filtre
- Modifiez l’ordre de tri (_Trier par_)
- Modifier la direction du tri (ascendant ou descendant)
- Modifier le nombre de résultats par page (_Afficher # par page_)
- Accéder à la page suivante
- Accéder à la page précédente
- Accéder à une autre page

>[!NOTE]
>
>Les événements de recherche ne sont pas pris en charge sur une édition Adobe Commerce Enterprise avec le module B2B installé.

### Nom de l’événement XDM

`searchRequest`

### Type

Rechercher

### Données collectées

Le tableau suivant décrit les données collectées pour cet événement.

| Champ | Description |
|---|---|
| `searchRequest` | Indique si une requête de recherche a été envoyée |
| `filter` | Indique si des filtres ont été appliqués pour limiter les résultats de recherche. |
| `attribute` (filter) | La facette d’un élément utilisée pour déterminer s’il doit être inclus dans les résultats de recherche |
| `value` | Valeurs d’attribut utilisées pour déterminer les éléments inclus dans les résultats de recherche |
| `isRange` | Si la valeur est true, les valeurs indiquent les points de fin d’une plage de valeurs acceptable. |
| `sort` | Indique le mode de tri des résultats de recherche. |
| `attribute` (sort) | Attribut utilisé pour trier les éléments dans les résultats de recherche |
| `order` | Ordre dans lequel renvoyer les résultats de la recherche |
| `query` | Termes recherchés |

## searchResponseReceived

Déclenché lorsque la recherche en direct renvoie les résultats de la fenêtre contextuelle &quot;Rechercher lorsque vous tapez&quot; ou de la page des résultats de la recherche.

>[!NOTE]
>
>Les événements de recherche ne sont pas pris en charge sur une édition Adobe Commerce Enterprise avec le module B2B installé.

### Nom de l’événement XDM

`searchResponse`

### Type

Rechercher

### Données collectées

Le tableau suivant décrit les données collectées pour cet événement.

| Champ | Description |
|---|---|
| `searchResponse` | Indique si une réponse de recherche a été reçue |
| `suggestions` | Tableau de chaînes qui incluent les noms des produits et des catégories existant dans le catalogue et similaires à la requête de recherche |
| `numberOfResults` | Le nombre de produits renvoyés |
| `productListItems` | Un tableau de produits dans le panier. |
| `SKU` | Unité de gestion des stocks. Identifiant unique du produit. |
| `name` | Nom d’affichage ou nom lisible du produit. |
| `productImageUrl` | URL de l’image principale du produit |
