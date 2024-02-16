---
title: Événements de back-office
description: Découvrez les données que chaque événement back-office capture.
role: Admin, Developer
feature: Personalization, Integration, Eventing
source-git-commit: d5824e11b4961b518e35fcf56ff2c7ee00480617
workflow-type: tm+mt
source-wordcount: '3599'
ht-degree: 0%

---

# [!DNL Data Connection] Événements de back-office

La liste suivante répertorie les événements Commerce back-office disponibles lorsque vous installez le [!DNL Data Connection] extension . Les données collectées par ces événements sont envoyées à Adobe Experience Platform. Vous pouvez également créer [événements personnalisés](custom-events.md) pour collecter des données supplémentaires qui ne sont pas fournies en standard.

Outre les données collectées par les événements suivants, vous obtenez également [autres données](https://experienceleague.adobe.com/docs/experience-platform/edge/data-collection/automatic-information.html) fourni par le SDK Web de Adobe Experience Platform.

Les événements back-office contiennent des données côté serveur. Ces données comprennent : [état de la commande](#order-status) informations telles que si une commande a été passée, annulée, remboursée, expédiée ou terminée. Les données côté serveur incluent également [événements de profil client](#customer-profile-events-back-office) des informations, telles que la création, la mise à jour ou la suppression d’un compte.

>[!NOTE]
>
>Tous les événements back-office incluent [`identityMap`](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html) qui inclut l’adresse électronique de l’acheteur, le cas échéant, et l’ECID.

## État de la commande

Les données d’état de la commande affichent une vue 360 de la commande du client. Cette vue permet aux commerçants de mieux cibler ou analyser l’état complet de la commande lors du développement de campagnes marketing. Vous pouvez, par exemple, repérer des tendances dans certaines catégories de produits qui se portent bien à différents moments de l’année. Des vêtements d’hiver qui se vendent mieux pendant les mois les plus froids ou certaines couleurs de produits qui intéressent les acheteurs au fil des ans. En outre, les données sur l’état de la commande peuvent vous aider à calculer la valeur client sur la durée de vie en comprenant la propension d’un acheteur à effectuer des conversions en fonction des commandes précédentes.

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

## Événements de profil client (back-office)

>[!NOTE]
>
>**Beta** Les événements de profil générés côté serveur sont disponibles pour les participants bêta. Si vous souhaitez rejoindre le programme bêta, envoyez une demande à [dataconnection@adobe.com](mailto:dataconnection@adobe.com).

Les événements de profil capturés du côté serveur incluent des informations de compte, telles que `accountCreated`, `accountUpdated`, et `accountDeleted`. Ces données permettent de renseigner les détails clés des clients nécessaires pour mieux définir les segments ou exécuter des campagnes marketing, comme envoyer des offres de réduction d’inscription, confirmer des changements de compte, etc. Des événements de profil similaires sont capturés à partir de la variable [storefront](#customer-profile-events-storefront).

### accountCreated

| Description | Nom de l’événement XDM |
|---|---|
| Déclenché lorsqu’un acheteur tente de créer un compte. | `userAccount.backofficeCreateProfile` |

#### Données collectées depuis accountCreated

Le tableau suivant décrit les données collectées pour cet événement.

| Champ | Description |
|---|---|
| `person` | Contient des informations sur le client. |
| `person.name` | Contient des informations sur le nom du client. |
| `person.name.firstName` | Contient le prénom du client. |
| `person.name.lastName` | Contient le nom du client. |
| `personalEmail` | Adresse électronique personnelle. |
| `personalEmail.address` | L’adresse technique, par exemple : `name@domain.com` comme généralement défini dans la norme RFC2822 et les normes ultérieures. |
| `commerce.commerceScope` | Indique l’emplacement d’un événement (affichage en magasin, magasin, site web, etc.). |
| `commerce.commerceScope.environmentID` | Identifiant de l’environnement. ID alphanumérique de 32 chiffres séparés par des tirets. |
| `commerce.commerceScope.storeCode` | Code de magasin unique. Vous pouvez avoir de nombreux magasins par site web. |
| `commerce.commerceScope.storeViewCode` | Code d’affichage de magasin unique. Vous pouvez avoir de nombreuses vues de magasin par magasin. |
| `commerce.commerceScope.websiteCode` | Code unique du site web. Vous pouvez avoir de nombreux sites Web dans un environnement. |

### accountUpdated

| Description | Nom de l’événement XDM |
|---|---|
| Déclenché lorsqu’un acheteur tente de modifier un compte. | `userAccount.backofficeUpdateProfile` |

#### Données collectées à partir de accountUpdated

Le tableau suivant décrit les données collectées pour cet événement.

| Champ | Description |
|---|---|
| `person` | Contient des informations sur le client. |
| `person.name` | Contient des informations sur le nom du client. |
| `person.name.firstName` | Contient le prénom du client. |
| `person.name.lastName` | Contient le nom du client. |
| `personalEmail` | Adresse électronique personnelle. |
| `personalEmail.address` | L’adresse technique, par exemple : `name@domain.com` comme généralement défini dans la norme RFC2822 et les normes ultérieures. |
| `commerce.commerceScope` | Indique l’emplacement d’un événement (affichage en magasin, magasin, site web, etc.). |
| `commerce.commerceScope.environmentID` | Identifiant de l’environnement. ID alphanumérique de 32 chiffres séparés par des tirets. |
| `commerce.commerceScope.storeCode` | Code de magasin unique. Vous pouvez avoir de nombreux magasins par site web. |
| `commerce.commerceScope.storeViewCode` | Code d’affichage de magasin unique. Vous pouvez avoir de nombreuses vues de magasin par magasin. |
| `commerce.commerceScope.websiteCode` | Code unique du site web. Vous pouvez avoir de nombreux sites Web dans un environnement. |

### accountDeleted

| Description | Nom de l’événement XDM |
|---|---|
| Déclenché lorsqu’un acheteur tente de supprimer un compte. | `userAccount.backofficeDeleteProfile` |

#### Données collectées à partir de accountDeleted

Le tableau suivant décrit les données collectées pour cet événement.

| Champ | Description |
|---|---|
| `person` | Contient des informations sur le client. |
| `person.name` | Contient des informations sur le nom du client. |
| `person.name.firstName` | Contient le prénom du client. |
| `person.name.lastName` | Contient le nom du client. |
| `personalEmail` | Adresse électronique personnelle. |
| `personalEmail.address` | L’adresse technique, par exemple : `name@domain.com` comme généralement défini dans la norme RFC2822 et les normes ultérieures. |
| `commerce.commerceScope` | Indique l’emplacement d’un événement (affichage en magasin, magasin, site web, etc.). |
| `commerce.commerceScope.environmentID` | Identifiant de l’environnement. ID alphanumérique de 32 chiffres séparés par des tirets. |
| `commerce.commerceScope.storeCode` | Code de magasin unique. Vous pouvez avoir de nombreux magasins par site web. |
| `commerce.commerceScope.storeViewCode` | Code d’affichage de magasin unique. Vous pouvez avoir de nombreuses vues de magasin par magasin. |
| `commerce.commerceScope.websiteCode` | Code unique du site web. Vous pouvez avoir de nombreux sites Web dans un environnement. |
