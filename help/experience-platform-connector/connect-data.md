---
title: Connexion des données commerciales à Adobe Experience Platform
description: Découvrez comment connecter vos données Commerce à Adobe Experience Platform.
exl-id: 87898283-545c-4324-b1ab-eec5e26a303a
source-git-commit: 1af2dee51391c94e19b68481d390cc2629fe1d6e
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# Connexion des données Commerce à Adobe Experience Platform {#connectaep}

Pour connecter votre instance Adobe Commerce à Adobe Experience Platform, vous devez fournir un ID d’organisation et un ID de flux de données.

![Configuration du connecteur Experience Platform](assets/epc-config.png)

1. Connectez-vous à votre compte Adobe dans le [Connecteur Commerce Services](../landing/saas.md#organizationid) et sélectionnez l’ID d’organisation.

1. Dans Admin, accédez à **Système** > Services > **Connecteur Experience Platform**.

1. Dans le **Portée** , définissez le contexte sur **Site Web**.

1. Dans le **ID d’organisation** , l’identifiant associé à votre compte Adobe Experience Platform s’affiche, tel qu’il est configuré dans le champ [Connecteur Commerce Services](../landing/saas.md#organizationid). L’ID d’organisation est global. Un seul ID d’organisation peut être associé par instance Adobe Commerce.

1. Dans le **Identifiant du flux de données** , collez l’identifiant de la banque de données que vous souhaitez [created](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html#create) dans Adobe Experience Platform.

   >[!NOTE]
   >
   >La portée de l’identifiant de flux de données doit être définie au niveau du site web ou supérieur. À ce niveau, le même identifiant de flux de données est utilisé pour chaque site web de la hiérarchie. Vous ne pouvez pas définir la portée de l’identifiant de la banque de données au niveau de l’aperçu de la banque de données.

1. (Facultatif) Si aucun SDK Web AEP n’est déployé sur votre site, laissez ce champ vide et le connecteur Experience Platform en déploie un pour vous. Sinon, ajoutez le nom de votre SDK Web AEP.

## Descriptions des champs

| Champ | Description |
|--- |--- |
| Portée | Site web spécifique sur lequel vous souhaitez appliquer les paramètres de configuration. |
| ID d’organisation (global) | Identifiant appartenant à l’organisation ayant acheté le produit Adobe DX. Cet identifiant associe votre instance Adobe Commerce à Adobe Experience Platform. |
| Identifiant de flux de données (site web) | Identifiant qui permet aux données de passer de Adobe Experience Platform à d’autres produits DX d’Adobe. Cet identifiant doit être associé à un site web spécifique au sein de votre instance Adobe Commerce spécifique. |
| Nom du SDK Web AEP (global) | Si aucun SDK Web AEP n’est déployé sur votre site, laissez ce champ vide et le connecteur Experience Platform en déploie un pour vous. Si un SDK Web AEP est déjà déployé sur votre site, indiquez le nom de ce SDK dans ce champ. Cela permet au collecteur d’événements Storefront et au SDK d’événements Storefront d’utiliser votre SDK Web AEP plutôt que la version déployée par le connecteur Experience Platform. |

Une fois l’extension du connecteur Experience Platform installée, le lien entre Adobe Commerce et Adobe Experience Platform créé et l’identifiant de la banque de données spécifié, les données de commerce commencent à s’enchaîner vers Adobe Experience Platform Edge et d’autres produits Adobe DX.

>[!NOTE]
>
> Le temps nécessaire au flux des données de la périphérie vers d’autres produits DX d’Adobe peut varier.

## Données commerciales en périphérie

Lorsque des données de commerce sont envoyées à Adobe Experience Platform Edge, vous pouvez créer des rapports du type suivant :

![Données commerciales dans Adobe Experience Manager](assets/aem-data-1.png)
_Données commerciales dans Adobe Experience Manager_
