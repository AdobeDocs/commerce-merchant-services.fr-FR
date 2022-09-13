---
title: Connexion des données commerciales à Adobe Experience Platform
description: Découvrez comment connecter vos données Commerce à Adobe Experience Platform.
exl-id: 87898283-545c-4324-b1ab-eec5e26a303a
source-git-commit: c7344efead97b0562a146f096123dd84f998fd5e
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# Connexion des données Commerce à Adobe Experience Platform {#connectaep}

Pour connecter votre instance Adobe Commerce à Adobe Experience Platform, vous devez fournir un ID d’organisation et un ID de flux de données.

![Configuration du connecteur Experience Platform](assets/epc-config.png)

1. Connectez-vous à votre compte Adobe dans le [Connecteur Commerce Services](../landing/saas.md#organizationid) et sélectionnez l’ID d’organisation.

1. Dans Admin, accédez à **Système** > Services > **Connecteur Experience Platform**.

1. Dans le **Portée** , sélectionnez le contexte ou &quot;portée&quot; de la vue magasin.

1. Dans le **ID d’organisation** , l’identifiant associé à votre compte Adobe Experience Platform s’affiche, tel qu’il est configuré dans le champ [Connecteur Commerce Services](../landing/saas.md#organizationid). L’ID d’organisation est global. Un seul ID d’organisation peut être associé par instance Adobe Commerce.

1. Dans le **Identifiant du flux de données** , collez l’identifiant de la banque de données que vous souhaitez [created](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html) dans Adobe Experience Platform.

## Relation de l’identifiant du flux de données et de votre vue d’ensemble de l’instance Commerce

L’identifiant de flux de données active le transfert d’événement de Adobe Experience Platform vers d’autres produits DX d’Adobe et peut être associé à une vue de magasin spécifique dans votre instance Adobe Commerce spécifique. Vous pouvez également associer plusieurs vues de magasin au même identifiant de flux de données. Cela dépend de ce qui a le plus de sens pour votre entreprise. [En savoir plus](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html?lang=en#event-forwarding-settings) à propos du transfert d’événement.

## Descriptions des champs

| Champ | Description |
|--- |--- |
| Portée | Vue de magasin spécifique à laquelle vous souhaitez appliquer les paramètres de configuration. |
| ID d’organisation (global) | Identifiant appartenant à l’organisation ayant acheté le produit Adobe DX. Cet identifiant associe votre instance Adobe Commerce à Adobe Experience Platform. |
| Identifiant de la banque de données (vue Magasin) | Identifiant qui permet aux données de passer de Adobe Experience Platform à d’autres produits DX d’Adobe. Cet identifiant peut être associé à une vue de magasin spécifique dans votre instance Adobe Commerce spécifique. |

Une fois l’extension du connecteur Experience Platform installée, le lien entre Adobe Commerce et Adobe Experience Platform créé et l’identifiant de la banque de données spécifié, les données de commerce commencent à s’enchaîner vers Adobe Experience Platform Edge et d’autres produits Adobe DX.

>[!NOTE]
>
> Le temps nécessaire au flux des données de la périphérie vers d’autres produits DX d’Adobe peut varier.

## Données commerciales en périphérie

Lorsque des données de commerce sont envoyées à Adobe Experience Platform Edge, vous pouvez créer des rapports du type suivant :

![Données commerciales dans Adobe Experience Manager](assets/aem-data-1.png)
_Données commerciales dans Adobe Experience Manager_
