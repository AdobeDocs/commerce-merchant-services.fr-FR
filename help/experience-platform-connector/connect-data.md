---
title: Connexion des données commerciales à Adobe Experience Platform
description: Découvrez comment connecter vos données Commerce à Adobe Experience Platform.
exl-id: 87898283-545c-4324-b1ab-eec5e26a303a
source-git-commit: 76bc0650f32e99f568c061e67290de6c380f46a4
workflow-type: tm+mt
source-wordcount: '807'
ht-degree: 0%

---

# Connexion des données Commerce à Adobe Experience Platform {#connectaep}

Pour connecter votre instance Adobe Commerce à Adobe Experience Platform, vous devez fournir un ID d’organisation et un ID de flux de données.

![Configuration du connecteur Experience Platform](assets/epc-config-sf.png)

## Général

1. Connectez-vous à votre compte Adobe dans le [Connecteur Commerce Services](../landing/saas.md#organizationid) et sélectionnez l’ID d’organisation.

1. Dans Admin, accédez à **Système** > Services > **Connecteur Experience Platform**.

1. Dans le **Portée** , définissez le contexte sur **Site Web**.

1. Dans le **ID d’organisation** , l’identifiant associé à votre compte Adobe Experience Platform s’affiche, tel qu’il est configuré dans le champ [Connecteur Commerce Services](../landing/saas.md#organizationid). L’ID d’organisation est global. Un seul ID d’organisation peut être associé par instance Adobe Commerce.

1. (Facultatif) Si vous avez déjà une [SDK Web AEP (allié)](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html) déployé sur votre site, cochez la case et ajoutez le nom de votre SDK Web AEP. Sinon, laissez ces champs vides et le connecteur Experience Platform en déploie un pour vous.

   >[!NOTE]
   >
   >Si vous spécifiez votre propre SDK Web AEP, le connecteur Experience Platform utilise l’identifiant de flux de données associé à ce SDK et non l’identifiant de flux de données spécifié sur cette page (le cas échéant).

## Collecte de données

Dans le **Collecte de données** , vous spécifiez les types de données à collecter et à envoyer à l’Experience Platform edge. Par défaut, les événements storefront sont automatiquement envoyés tant que le SDK Web AEP et l’ID d’organisation sont valides. Consultez la rubrique Événements pour en savoir plus sur [storefront](events.md#storefront-events) et [back office](events.md#back-office-events) événements .

![Configuration du connecteur Experience Platform](assets/epc-config-dc.png)

>[!NOTE]
>
>Tous les champs du champ **Collecte de données** s’appliquent à la section **Site Web** ou supérieure.

1. Sélectionner **Événements de back-office** si vous souhaitez envoyer des informations sur l’état de la commande, par exemple si une commande a été passée, annulée, remboursée ou expédiée.

   >[!NOTE]
   >
   >Par défaut, toutes les données de back-office sont envoyées au serveur Edge Experience Platform. Si un acheteur choisit de se désabonner de la collecte de données, vous devez définir explicitement la préférence de confidentialité de l’acheteur dans l’Experience Platform. Cela diffère des événements storefront où le collecteur gère déjà le consentement en fonction des préférences de l’acheteur. [En savoir plus](https://experienceleague.adobe.com/docs/experience-platform/landing/governance-privacy-security/consent/adobe/dataset.html) à propos de la définition de la préférence de confidentialité d’un acheteur dans l’Experience Platform.

1. (Ignorez cette étape si vous utilisez votre propre SDK Web AEP.) [Créer](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/configure.html#create) un flux de données dans Adobe Experience Platform ou sélectionnez un flux de données existant à utiliser pour la collecte.

1. (Ignorez cette étape si vous utilisez votre propre SDK Web AEP.) Dans le **Identifiant du flux de données** collez l’identifiant de ce flux de données nouveau ou existant.

## Descriptions des champs

| Champ | Description |
|--- |--- |
| Portée | Site web spécifique sur lequel vous souhaitez appliquer les paramètres de configuration. |
| ID d’organisation (global) | Identifiant appartenant à l’organisation ayant acheté le produit Adobe DX. Cet identifiant associe votre instance Adobe Commerce à Adobe Experience Platform. |
| Le SDK Web AEP est-il déjà déployé sur votre site ? | Cochez cette case si vous avez déployé votre propre SDK Web AEP sur votre site. |
| Nom du SDK Web AEP (global) | Si un SDK Web Experience Platform est déjà déployé sur votre site, indiquez le nom de ce SDK dans ce champ. Cela permet au collecteur d’événements Storefront et au SDK d’événements Storefront d’utiliser votre SDK web Experience Platform plutôt que la version déployée par le connecteur Experience Platform. Si aucun SDK Web Experience Platform n’est déployé sur votre site, laissez ce champ vide et le connecteur Experience Platform en déploie un pour vous. |
| Événements Storefront | Est coché par défaut tant que l’ID d’organisation et l’ID de flux de données sont valides. Les événements Storefront collectent des données comportementales anonymes de vos clients lorsqu’ils parcourent votre site. |
| Événements de back-office | Si cette case est cochée, la payload d’événement contient des informations d’état de commande anonymes, telles que si une commande a été passée, annulée, remboursée ou expédiée. |
| Identifiant de flux de données (site web) | Identifiant qui permet aux données de passer de Adobe Experience Platform à d’autres produits DX d’Adobe. Cet identifiant doit être associé à un site web spécifique au sein de votre instance Adobe Commerce spécifique. Si vous spécifiez votre propre SDK Web Experience Platform, ne spécifiez pas d’identifiant de flux de données dans ce champ. Le connecteur Experience Platform utilise l’identifiant de flux de données associé à ce SDK et ignore tout identifiant de flux de données spécifié dans ce champ (le cas échéant). |

Une fois l’extension du connecteur Experience Platform installée, le lien entre Adobe Commerce et Adobe Experience Platform créé et l’identifiant de la banque de données spécifié, les données de commerce commencent à s’enchaîner vers Adobe Experience Platform Edge et d’autres produits Adobe DX.

>[!NOTE]
>
> Le temps nécessaire au flux des données de la périphérie vers d’autres produits DX d’Adobe peut varier.

## Vérifier que les données sont envoyées à l’Experience Platform

Lorsque des données de commerce sont envoyées à Adobe Experience Platform Edge, vous pouvez créer des rapports du type suivant :

![Données commerciales dans Adobe Experience Manager](assets/aem-data-1.png)
_Données commerciales dans Adobe Experience Manager_
