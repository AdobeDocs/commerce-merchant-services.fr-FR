---
title: Connexion des données commerciales à Adobe Experience Platform
description: Découvrez comment connecter vos données Commerce à Adobe Experience Platform.
exl-id: 87898283-545c-4324-b1ab-eec5e26a303a
source-git-commit: 5f8fcc3d6d05cdd854eadd14f53e1ca13625dae3
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 0%

---

# Connexion des données Commerce à Adobe Experience Platform {#connectaep}

Avant de connecter vos données Adobe Commerce à Adobe Experience Platform, vous devez vous connecter à votre compte d’Adobe dans le [Connecteur Commerce Services](../landing/saas.md#organizationid). Une fois que vous êtes connecté et que vous avez sélectionné l’ID d’organisation, vous pouvez spécifier la portée et l’ID de flux de données sur le **Connecteur Experience Platform** dans Admin.

![Configuration du connecteur Experience Platform](assets/epc-config.png)

1. Dans Admin, accédez à **Système** > Services > **Connecteur Experience Platform**.

1. Dans le **Portée** , sélectionnez le contexte ou &quot;portée&quot; de la vue magasin.

   L’identifiant de l’organisation IMS est global. Un seul identifiant de l’organisation IMS peut être associé par instance Adobe Commerce.

1. Dans le **Identifiant de l’organisation IMS** , l’identifiant associé à votre compte Adobe Experience Platform s’affiche, tel qu’il est configuré dans le champ [Connecteur Commerce Services](../landing/saas.md#organizationid).

1. Dans le **Identifiant du flux de données** , collez l’identifiant de la banque de données que vous souhaitez [created](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html) dans Adobe Experience Platform.

## Relation de l’identifiant de flux de données et de votre instance de commerce Storeview

L’identifiant de flux de données permet le transfert d’événement de Adobe Experience Platform vers d’autres produits DX d’Adobe et peut être associé à une vue de magasin spécifique dans votre instance Adobe Commerce spécifique. Vous pouvez également associer plusieurs vues de magasin au même identifiant de flux de données. Cela dépend de ce qui a le plus de sens pour votre entreprise. [En savoir plus](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html?lang=en#event-forwarding-settings) à propos du transfert d’événement.

## Descriptions des champs

| Champ | Description |
|--- |--- |
| Portée | Vue de magasin spécifique à laquelle vous souhaitez appliquer les paramètres de configuration. |
| Organisation IMS (globale) | Identifiant appartenant à l’organisation ayant acheté le produit Adobe DX. Cet identifiant associe votre instance Adobe Commerce à Adobe Experience Platform. |
| Identifiant de la banque de données (vue Magasin) | Identifiant qui permet aux données de passer de Adobe Experience Platform à d’autres produits DX d’Adobe. Cet identifiant peut être associé à un storeView spécifique dans votre instance Adobe Commerce spécifique. |

Une fois l’extension du connecteur Experience Platform installée, le lien entre Adobe Commerce et Adobe Experience Platform créé et l’identifiant de la banque de données spécifié, les données de commerce commencent à s’enchaîner vers Adobe Experience Platform Edge et d’autres produits Adobe DX.

## Données commerciales en périphérie

Lorsque des données de commerce sont envoyées à Adobe Experience Platform Edge, vous pouvez créer des rapports du type suivant :

![Données commerciales dans Adobe Experience Manager](assets/aem-data-1.png)
_Données commerciales dans Adobe Experience Manager_
