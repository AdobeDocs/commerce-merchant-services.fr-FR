---
title: Événements
description: Découvrez les données que chaque événement capture.
exl-id: b0c88af3-29c1-4661-9901-3c6d134c2386
source-git-commit: 1484a465f3ce5b5578a7c5cf3f5f3b7d68d69c41
workflow-type: tm+mt
source-wordcount: '4605'
ht-degree: 0%

---

# Événements de connecteur Experience Platform

Vous trouverez ci-dessous la liste des événements Commerce disponibles lorsque vous installez l’extension Experience Platform Connector. Les données collectées par ces événements sont envoyées à Adobe Experience Platform Edge. Vous pouvez également créer des [événements personnalisés](custom-events.md) pour collecter des données supplémentaires qui ne sont pas prêtes à l’emploi.

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

### openCart

| Description | Nom de l’événement XDM |
|---|---|
| Déclenché lors de la création d’un panier, c’est-à-dire lorsqu’un produit est ajouté à un panier vide. | `commerce.productListOpens` |

#### Données collectées à partir d’openCart

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

### removeFromCart

| Description | Nom de l’événement XDM |
|---|---|
| Déclenché chaque fois qu’un produit est supprimé ou que la quantité d’un produit dans le panier est décrémentée. | `commerce.productListRemovals` |

#### Données collectées à partir de removeFromCart

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

### shoppingCartView

| Description | Nom de l’événement XDM |
|---|---|
| Déclenché lors du chargement d’une page de panier. | `commerce.productListViews` |

#### Données collectées à partir de shoppingCartView

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

### pageView

| Description | Nom de l’événement XDM |
|---|---|
| Déclenché lors du chargement d’une page. | `web.webpagedetails.pageViews` |

#### Données collectées à partir de pageView

Le tableau suivant décrit les données collectées pour cet événement.

| Champ | Description |
|---|---|
| `pageViews` | Indique si une page a été chargée. A `value` de `1` indique que la page a été chargée. |

### productPageView

| Description | Nom de l’événement XDM |
|---|---|
| Déclenché lors du chargement d’une page de produits. | `commerce.productViews` |

#### Données collectées à partir de productPageView

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

### startCheckout

| Description | Nom de l’événement XDM |
|---|---|
| Déclenché lorsque l’acheteur clique sur un bouton de passage en caisse. | `commerce.checkouts` |

#### Données collectées à partir de startCheckout

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

### completeCheckout

| Description | Nom de l’événement XDM |
|---|---|
| Déclenché lorsque l’acheteur commande. | `commerce.order` |

#### Données collectées à partir de completeCheckout

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
| `personalEmail` | Indique l’adresse électronique personnelle |
| `address` | L’adresse technique, par exemple : `name@domain.com` comme couramment défini dans la norme RFC2822 et les normes ultérieures. |
| `productListItems` | Tableau de produits dans le panier |
| `SKU` | Unité de gestion des stocks. Identifiant unique du produit. |
| `name` | Nom d’affichage ou nom lisible du produit. |
| `priceTotal` | Prix total de l’article de ligne de produit |
| `quantity` | Nombre d’unités de produits dans le panier |
| `discountAmount` | Indique le montant de remise appliqué |
| `currencyCode` | Le [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) code de devise utilisé pour les totaux de commande. |
| `productImageUrl` | URL de l’image principale du produit |
| `selectedOptions` | Champ utilisé pour un produit configurable. `attribute` identifie un attribut du produit configurable, tel que `size` ou `color` et `value` identifie la valeur de l’attribut, telle que `small` ou `black`. |

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
| `person` | Acteur, contact ou propriétaire individuel |
| `accountID` | Capture l’ID du compte d’utilisateur |
| `accountType` | Capture le type de compte d’utilisateur, tel que `Personal` ou `Company`, le cas échéant |
| `personalEmailID` | L’adresse technique, par exemple : `name@domain.com` comme couramment défini dans la norme RFC2822 et les normes ultérieures. |
| `personalEmail` | Capture les coordonnées - un email et les informations associées |
| `address` | L’adresse technique, par exemple : `name@domain.com` comme couramment défini dans la norme RFC2822 et les normes ultérieures. |
| `userAccount` | Indique les détails de fidélité, les préférences, les processus de connexion et les autres préférences de compte. |
| `login` | Indique si un visiteur a tenté de se connecter. |

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
| `userAccount` | Indique les détails de fidélité, les préférences, les processus de connexion et les autres préférences de compte. |
| `logout` | Indique si un visiteur a tenté de se déconnecter. |

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
| `person` | Acteur, contact ou propriétaire individuel |
| `accountID` | Capture l’ID du compte d’utilisateur |
| `accountType` | Capture le type de compte d’utilisateur, tel que `Personal` ou `Company`, le cas échéant |
| `personalEmailID` | L’adresse technique, par exemple : `name@domain.com` comme couramment défini dans la norme RFC2822 et les normes ultérieures. |
| `personalEmail` | Capture les coordonnées - un email et les informations associées |
| `address` | L’adresse technique, par exemple : `name@domain.com` comme couramment défini dans la norme RFC2822 et les normes ultérieures. |
| `userAccount` | Indique les détails de fidélité, les préférences, les processus de connexion et les autres préférences de compte. |
| `createProfile` | Indique si un utilisateur a créé un profil de compte |

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
| `person` | Acteur, contact ou propriétaire individuel |
| `accountID` | Capture l’ID du compte d’utilisateur |
| `accountType` | Capture le type de compte d’utilisateur, tel que `Personal` ou `Company`, le cas échéant |
| `personalEmailID` | L’adresse technique, par exemple : `name@domain.com` comme couramment défini dans la norme RFC2822 et les normes ultérieures. |
| `personalEmail` | Capture les coordonnées - un email et les informations associées |
| `address` | L’adresse technique, par exemple : `name@domain.com` comme couramment défini dans la norme RFC2822 et les normes ultérieures. |
| `userAccount` | Indique les détails de fidélité, les préférences, les processus de connexion et les autres préférences de compte. |
| `updateProfile` | Indique si un utilisateur a mis à jour son profil de compte |

## Recherche d’événements

Les événements de recherche fournissent des données pertinentes pour l’intention de l’acheteur. L’aperçu de l’intention d’un acheteur permet aux marchands de voir comment les acheteurs recherchent des articles, ce sur quoi ils cliquent et, au bout du compte, achètent ou abandonnent. Vous pouvez, par exemple, utiliser ces données si vous souhaitez cibler les acheteurs existants qui recherchent votre meilleur produit, mais n’achètent jamais le produit.

Utilisez la variable `uniqueIdentifier` champ situé dans les deux `searchRequestSent` et `searchResponseReceived` pour effectuer une référence croisée à une requête de recherche vers la réponse de recherche correspondante.

### searchRequestSent

| Description | Nom de l’événement XDM |
|---|---|
| Déclenché par les événements suivants dans la fenêtre contextuelle &quot;Rechercher lorsque vous tapez&quot; :<br><br>Appuyez sur Entrée, puis cliquez sur _Afficher tout_<br><br> Déclenché par les événements suivants sur les pages de résultats de recherche :<br><br>Sélectionnez un filtre, puis Modifiez l’ordre de tri (_Trier par_), Modifier la direction du tri (ascendant ou descendant), Modifier le nombre de résultats par page (_Afficher # par page_), Accédez à la page suivante, à la page précédente, à une autre page. | `searchRequest` |

>[!NOTE]
>
>Les événements de recherche ne sont pas pris en charge sur une édition Adobe Commerce Enterprise avec l’extension B2B installée.

#### Données collectées à partir de searchRequestSent

Le tableau suivant décrit les données collectées pour cet événement.

| Champ | Description |
|---|---|
| `searchRequest` | Indique si une requête de recherche a été envoyée |
| `id` | L’identifiant unique de cette requête de recherche spécifique |
| `filter` | Indique si des filtres ont été appliqués pour limiter les résultats de recherche. |
| `attribute` (filter) | La facette d’un élément utilisée pour déterminer s’il doit être inclus dans les résultats de recherche |
| `value` | Valeurs d’attribut utilisées pour déterminer les éléments inclus dans les résultats de recherche |
| `isRange` | Si la valeur est true, les valeurs indiquent les points de fin d’une plage de valeurs acceptable. |
| `sort` | Indique le mode de tri des résultats de recherche. |
| `attribute` (sort) | Attribut utilisé pour trier les éléments dans les résultats de recherche |
| `order` | Ordre dans lequel renvoyer les résultats de la recherche |
| `query` | Termes recherchés |

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
| `searchResponse` | Indique si une réponse de recherche a été reçue |
| `id` | L’identifiant unique de cette réponse de recherche spécifique |
| `suggestions` | Tableau de chaînes qui incluent les noms des produits et des catégories existant dans le catalogue et similaires à la requête de recherche |
| `numberOfResults` | Le nombre de produits renvoyés |
| `productListItems` | Un tableau de produits dans le panier. |
| `SKU` | Unité de gestion des stocks. Identifiant unique du produit. |
| `name` | Nom d’affichage ou nom lisible du produit. |
| `productImageUrl` | URL de l’image principale du produit |

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
| `requisitionList` | Propriétés de la liste de demandes créée par le client |
| `ID` | Identifiant unique de la liste des demandes |
| `name` | Nom de la liste des demandes spécifiée par le client |
| `description` | Description de la liste des demandes spécifiée par le client |

### addToRequestList

| Description | Nom de l’événement XDM |
|---|---|
| Déclenché lorsqu’un acheteur ajoute un produit à une liste de demandes existante ou lors de la création d’une nouvelle liste. | `commerce.requisitionListAdds` |

>[!NOTE]
>
>`addToRequisitionList` n’est pas pris en charge sur les pages d’affichage des catégories ou pour les produits configurables. Elle est prise en charge sur les pages d’affichage de produit et pour les produits simples.

#### Données collectées à partir de addToRequestList

Le tableau suivant décrit les données collectées pour cet événement.

| Champ | Description |
|---|---|
| `requisitionList` | Propriétés de la liste de demandes créée par le client |
| `ID` | Identifiant unique de la liste des demandes |
| `name` | Nom de la liste des demandes spécifiée par le client |
| `description` | Description de la liste des demandes spécifiée par le client |
| `productListItems` | Tableau de produits qui ont été ajoutés à la liste des demandes d’acquisition |
| `name` | Nom d’affichage ou nom lisible du produit. |
| `SKU` | Unité de gestion des stocks. Identifiant unique du produit. |
| `quantity` | Nombre d’unités de produits ajoutées |
| `priceTotal` | Prix total de l’article de ligne de produit |
| `discountAmount` | Indique le montant de remise appliqué |
| `currencyCode` | Le [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) code de devise utilisé pour cet élément de paiement |
| `selectedOptions` | Champ utilisé pour un produit configurable. `attribute` identifie un attribut du produit configurable, tel que `size` ou `color` et `value` identifie la valeur de l’attribut, telle que `small` ou `black`. |

### removeFromRequestList

| Description | Nom de l’événement XDM |
|---|---|
| Déclenché lorsqu’un acheteur supprime un produit d’une liste de demandes d’achat. | `commerce.requisitionListRemovals` |

#### Données collectées à partir de removeFromRequestList

Le tableau suivant décrit les données collectées pour cet événement.

| Champ | Description |
|---|---|
| `requisitionList` | Propriétés de la liste de demandes créée par le client |
| `ID` | Identifiant unique de la liste des demandes |
| `name` | Nom de la liste des demandes spécifiée par le client |
| `description` | Description de la liste des demandes spécifiée par le client |
| `productListItems` | Tableau de produits qui ont été ajoutés à la liste des demandes d’acquisition |
| `name` | Nom d’affichage ou nom lisible du produit. |
| `SKU` | Unité de gestion des stocks. Identifiant unique du produit. |
| `quantity` | Nombre d’unités de produits ajoutées |
| `priceTotal` | Prix total de l’article de ligne de produit |
| `discountAmount` | Indique le montant de remise appliqué |
| `currencyCode` | Le [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) code de devise utilisé pour cet élément de paiement |
| `selectedOptions` | Champ utilisé pour un produit configurable. `attribute` identifie un attribut du produit configurable, tel que `size` ou `color` et `value` identifie la valeur de l’attribut, telle que `small` ou `black`. |

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
| `address` | L’adresse technique, par exemple : `name@domain.com` comme couramment défini dans la norme RFC2822 et les normes ultérieures. |
| `productListItems` | Tableau de produits dans l’ordre |
| `id` | Identifiant de l’élément de ligne pour cette entrée de produit. Le produit lui-même est identifié via la variable `product` champ . |
| `name` | Nom d’affichage ou nom lisible du produit. |
| `SKU` | Unité de gestion des stocks. Identifiant unique du produit. |
| `quantity` | Nombre d’unités de produits dans le panier |
| `priceTotal` | Prix total de l’article de ligne de produit |
| `discountAmount` | Indique le montant de remise appliqué |
| `order` | Contient des informations sur la commande. |
| `purchaseID` | Identifiant unique attribué par le vendeur pour cet achat ou ce contrat. Il n’existe aucune garantie que l’ID est unique. |
| `priceTotal` | Le prix total de cette commande une fois toutes les remises et taxes appliquées |
| `currencyCode` | Code de devise ISO 4217 utilisé pour les totaux de commande. |
| `purchaseOrderNumber` | Identifiant unique attribué par l’acheteur pour cet achat ou ce contrat. |
| `payments` | Liste des paiements pour cette commande |
| `paymentType` | Mode de paiement de cette commande. Valeurs énumérées et personnalisées autorisées. |
| `currencyCode` | Le [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) code de devise utilisé pour cet élément de paiement |
| `paymentAmount` | Valeur du paiement |
| `taxAmount` | Montant de la taxe payé par l&#39;acheteur dans le cadre du paiement final |
| `createdDate` | Heure et date de création d’une commande dans le système commercial. Par exemple : `2022-10-15T20:20:39+00:00` |
| `shipping` | Informations d’expédition pour un ou plusieurs produits |
| `shippingMethod` | Le mode d’expédition choisi par le client, tel que la livraison standard, la livraison accélérée, la prise en charge en magasin, etc. |
| `shippingAmount` | Le montant que le client a dû payer pour l’expédition. |
| `address` | Adresse postale physique |
| `street1` | informations Principales sur le niveau de la rue, numéro d’appartement, numéro de rue et nom de rue |
| `street2` | Champ supplémentaire pour les informations au niveau de la rue |
| `city` | Nom de la ville |
| `state` | Nom de l’état. C&#39;est un champ de forme libre. |
| `postalCode` | Code postal de l’emplacement. Les codes postaux ne sont pas disponibles pour tous les pays. Dans certains pays, ce champ ne contiendra qu&#39;une partie du code postal. |
| `country` | Nom du territoire administré par le gouvernement. Autre que `xdm:countryCode`, il s’agit d’un champ de forme libre qui peut avoir le nom du pays dans n’importe quelle langue. |
| `billingAddress` | Adresse postale de facturation |
| `street1` | informations Principales sur le niveau de la rue, numéro d’appartement, numéro de rue et nom de rue |
| `street2` | Champ supplémentaire pour les informations au niveau de la rue |
| `city` | Nom de la ville |
| `state` | Nom de l’état. C&#39;est un champ de forme libre. |
| `postalCode` | Code postal de l’emplacement. Les codes postaux ne sont pas disponibles pour tous les pays. Dans certains pays, ce champ ne contiendra qu&#39;une partie du code postal. |
| `country` | Nom du territoire administré par le gouvernement. Autre que `xdm:countryCode`, il s’agit d’un champ de forme libre qui peut avoir le nom du pays dans n’importe quelle langue. |
| `personalEmail` | Adresse électronique personnelle |
| `address` | Adresse technique, par exemple, &quot;name@domain.com&quot;, telle que généralement définie dans la norme RFC2822 et les normes ultérieures. |

### orderItemsShipped

| Description | Nom de l’événement XDM |
|---|---|
| Déclenché lorsqu’une commande est expédiée. | `commerce.backofficeOrderItemsShipped` |

#### Données collectées à partir de orderItemsShipped

Le tableau suivant décrit les données collectées pour cet événement.
|Field|Description| |—|—| |`address`|L’adresse technique, par exemple : `name@domain.com` comme défini couramment dans la norme RFC2822 et les normes ultérieures| |`productListItems`|Un tableau de produits dans la commande| |`id`|L’identifiant de l’élément de ligne pour cette entrée de produit. Le produit lui-même est identifié via la variable `product` champ .| |`name`|Nom d’affichage ou nom lisible du produit| |`SKU`|Unité de gestion des stocks. Identifiant unique du produit.| |`quantity`|Le nombre d’unités de produits dans le panier| |`priceTotal`|Le prix total de l’article de ligne de produit| |`discountAmount`|Indique le montant de remise appliqué| |`order`|Contient des informations sur la commande| |`purchaseID`|Identifiant unique attribué par le vendeur pour cet achat ou ce contrat. Il n’existe aucune garantie que l’ID est unique| |`priceTotal`|Le prix total de cette commande une fois toutes les remises et taxes appliquées| |`currencyCode`|Code de devise ISO 4217 utilisé pour les totaux de commande| |`purchaseOrderNumber`|Identifiant unique attribué par l’acheteur pour cet achat ou ce contrat| |`payments`|La liste des paiements pour cette commande| |`paymentType`|Mode de paiement de cette commande. Valeurs énumérées et personnalisées autorisées.| |`currencyCode`|Le [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) code de devise utilisé pour cet élément de paiement| |`paymentAmount`|La valeur du paiement| |`lastUpdatedDate`|Heure à laquelle un enregistrement de commande particulier est mis à jour pour la dernière fois dans le système commercial| |`shipping`|Informations d’expédition pour un ou plusieurs produits| |`shippingMethod`|Le mode de livraison choisi par le client, tel que la livraison standard, la livraison accélérée, la prise en charge en magasin, etc.| |`trackingNumber`|Le numéro de suivi fourni par le transporteur pour l’expédition d’un article de commande| |`trackingURL`|L’URL permettant de suivre l’état d’expédition d’un article de commande| |`shipDate`|La date à laquelle un ou plusieurs articles d’une commande sont expédiés| |`address`|Adresse de livraison physique| |`street1`|Principales informations de niveau rue, numéro d’appartement, numéro de rue et nom de rue| |`street2`|Champ supplémentaire pour les informations au niveau de la rue| |`city`|Nom de la ville| |`state`|Nom de l’état. C&#39;est un champ de forme libre.| |`postalCode`|Code postal de l’emplacement. Les codes postaux ne sont pas disponibles pour tous les pays. Dans certains pays, ce champ ne contiendra qu&#39;une partie du code postal.| |`country`|Le nom du territoire administré par le gouvernement. Autre que `xdm:countryCode`, il s’agit d’un champ de forme libre qui peut avoir le nom du pays dans n’importe quelle langue.| |`shippingAmount`|Le montant que le client a dû payer pour l’expédition.| |`billingAddress`|Adresse postale de facturation| |`street1`|Principales informations de niveau rue, numéro d’appartement, numéro de rue et nom de rue| |`street2`|Champ supplémentaire pour les informations au niveau de la rue| |`city`|Nom de la ville| |`state`|Nom de l’état. C&#39;est un champ de forme libre.| |`postalCode`|Code postal de l’emplacement. Les codes postaux ne sont pas disponibles pour tous les pays. Dans certains pays, ce champ ne contiendra qu&#39;une partie du code postal.| |`country`|Le nom du territoire administré par le gouvernement. Autre que `xdm:countryCode`, il s’agit d’un champ de forme libre qui peut avoir le nom du pays dans n’importe quelle langue.| |`personalEmail`|Une adresse électronique personnelle| |`address`|L’adresse technique, par exemple, &quot;name@domain.com&quot;, telle que généralement définie dans la norme RFC2822 et les normes ultérieures|

### orderCancelled

| Description | Nom de l’événement XDM |
|---|---|
| Déclenché lorsqu’un acheteur annule une commande. | `commerce.backofficeOrderCancelled` |

#### Données collectées à partir de orderCancelled

Le tableau suivant décrit les données collectées pour cet événement.
|Field|Description| |—|—| |`address`|L’adresse technique, par exemple : `name@domain.com` comme défini couramment dans la norme RFC2822 et les normes ultérieures| |`productListItems`|Un tableau de produits dans la commande| |`id`|L’identifiant de l’élément de ligne pour cette entrée de produit. Le produit lui-même est identifié via la variable `product` champ .| |`name`|Nom d’affichage ou nom lisible du produit| |`SKU`|Unité de gestion des stocks. Identifiant unique du produit.| |`quantity`|Le nombre d’unités de produits dans le panier| |`priceTotal`|Le prix total de l’article de ligne de produit| |`discountAmount`|Indique le montant de remise appliqué| |`order`|Contient des informations sur la commande| |`purchaseID`|Identifiant unique attribué par le vendeur pour cet achat ou ce contrat. Il n’existe aucune garantie que l’ID est unique| |`purchaseOrderNumber`|Identifiant unique attribué par l’acheteur pour cet achat ou ce contrat| |`cancelDate`|La date et l’heure auxquelles un acheteur annule une commande| |`lastUpdatedDate`|Heure à laquelle un enregistrement de commande particulier est mis à jour pour la dernière fois dans le système commercial| |`personalEmail`|Une adresse électronique personnelle| |`address`|L’adresse technique, par exemple, &quot;name@domain.com&quot;, telle que généralement définie dans la norme RFC2822 et les normes ultérieures|

### CreditMemoIssued

| Description | Nom de l’événement XDM |
|---|---|
| Déclenché lorsqu’un acheteur renvoie un article dans une commande. | `commerce.backofficeCreditMemoIssued` |

#### Données collectées à partir de CreditMemoIssued

Le tableau suivant décrit les données collectées pour cet événement.
|Field|Description| |—|—| |`address`|L’adresse technique, par exemple : `name@domain.com` comme défini couramment dans la norme RFC2822 et les normes ultérieures| |`productListItems`|Un tableau de produits dans la commande| |`id`|L’identifiant de l’élément de ligne pour cette entrée de produit. Le produit lui-même est identifié via la variable `product` champ .| |`name`|Nom d’affichage ou nom lisible du produit| |`SKU`|Unité de gestion des stocks. Identifiant unique du produit.| |`quantity`|Le nombre d’unités de produits dans le panier| |`priceTotal`|Le prix total de l’article de ligne de produit| |`discountAmount`|Indique le montant de remise appliqué| |`order`|Contient des informations sur la commande| |`purchaseID`|Identifiant unique attribué par le vendeur pour cet achat ou ce contrat. Il n’existe aucune garantie que l’ID est unique| |`purchaseOrderNumber`|Identifiant unique attribué par l’acheteur pour cet achat ou ce contrat| |`lastUpdatedDate`|Heure à laquelle un enregistrement de commande particulier est mis à jour pour la dernière fois dans le système commercial| |`personalEmail`|Une adresse électronique personnelle| |`address`|L’adresse technique, par exemple, &quot;name@domain.com&quot;, telle que généralement définie dans la norme RFC2822 et les normes ultérieures|

### orderShipmentCompleted

| Description | Nom de l’événement XDM |
|---|---|
| Déclenché lorsqu’un acheteur renvoie un article dans une commande. | `commerce.backofficeOrderShipmentCompleted` |

#### Données collectées à partir de orderShipmentCompleted

Le tableau suivant décrit les données collectées pour cet événement.
|Field|Description| |—|—| |`address`|L’adresse technique, par exemple : `name@domain.com` comme défini couramment dans la norme RFC2822 et les normes ultérieures| |`productListItems`|Un tableau de produits dans la commande| |`id`|L’identifiant de l’élément de ligne pour cette entrée de produit. Le produit lui-même est identifié via la variable `product` champ .| |`name`|Nom d’affichage ou nom lisible du produit| |`SKU`|Unité de gestion des stocks. Identifiant unique du produit.| |`quantity`|Le nombre d’unités de produits dans le panier| |`priceTotal`|Le prix total de l’article de ligne de produit| |`discountAmount`|Indique le montant de remise appliqué| |`order`|Contient des informations sur la commande| |`purchaseID`|Identifiant unique attribué par le vendeur pour cet achat ou ce contrat. Il n’existe aucune garantie que l’ID est unique| |`priceTotal`|Le prix total de cette commande une fois toutes les remises et taxes appliquées| |`currencyCode`|Code de devise ISO 4217 utilisé pour les totaux de commande| |`purchaseOrderNumber`|Identifiant unique attribué par l’acheteur pour cet achat ou ce contrat| |`taxAmount`|Le montant de la taxe payé par l’acheteur dans le cadre du paiement final.| |`createdDate`|L’heure et la date de création d’une commande dans le système commercial. Par exemple : `2022-10-15T20:20:39+00:00`| |`payments`|La liste des paiements pour cette commande| |`paymentType`|Mode de paiement de cette commande. Valeurs énumérées et personnalisées autorisées.| |`currencyCode`|Le [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) code de devise utilisé pour cet élément de paiement| |`paymentAmount`|La valeur du paiement| |`shipping`|Informations d’expédition pour un ou plusieurs produits| |`shippingMethod`|Le mode de livraison choisi par le client, tel que la livraison standard, la livraison accélérée, la prise en charge en magasin, etc.| |`address`|Adresse de livraison physique| |`street1`|Principales informations de niveau rue, numéro d’appartement, numéro de rue et nom de rue| |`street2`|Champ supplémentaire pour les informations au niveau de la rue| |`city`|Nom de la ville| |`state`|Nom de l’état. C&#39;est un champ de forme libre.| |`postalCode`|Code postal de l’emplacement. Les codes postaux ne sont pas disponibles pour tous les pays. Dans certains pays, ce champ ne contiendra qu&#39;une partie du code postal.| |`country`|Le nom du territoire administré par le gouvernement. Autre que `xdm:countryCode`, il s’agit d’un champ de forme libre qui peut avoir le nom du pays dans n’importe quelle langue.| |`shippingAmount`|Le montant que le client a dû payer pour l’expédition.| |`address`|L’adresse technique, par exemple : `name@domain.com` comme défini couramment dans la norme RFC2822 et les normes ultérieures| |`billingAddress`|Adresse postale de facturation| |`street1`|Principales informations de niveau rue, numéro d’appartement, numéro de rue et nom de rue| |`street2`|Champ supplémentaire pour les informations au niveau de la rue| |`city`|Nom de la ville| |`state`|Nom de l’état. C&#39;est un champ de forme libre.| |`postalCode`|Code postal de l’emplacement. Les codes postaux ne sont pas disponibles pour tous les pays. Dans certains pays, ces données ne contiennent qu’une partie du code postal.| |`country`|Le nom du territoire administré par le gouvernement. Autre que `xdm:countryCode`, il s’agit d’un champ de forme libre qui peut avoir le nom du pays dans n’importe quelle langue.| |`personalEmail`|Une adresse électronique personnelle| |`address`|L’adresse technique, par exemple, &quot;name@domain.com&quot;, telle que généralement définie dans la norme RFC2822 et les normes ultérieures|
