---
title: Connexion des données commerciales à Adobe Experience Platform
description: Découvrez comment connecter vos données Commerce à Adobe Experience Platform.
exl-id: 87898283-545c-4324-b1ab-eec5e26a303a
source-git-commit: dead0b8dae69476c196652abd43c4966a38c4141
workflow-type: tm+mt
source-wordcount: '1074'
ht-degree: 0%

---

# Connexion des données Commerce à Adobe Experience Platform

Lorsque vous installez le connecteur Experience Platform, deux nouvelles pages de configuration s’affichent dans la section **Système** sous **Services** dans Commerce _Administration_.

- Connecteur Commerce Services
- Connecteur Experience Platform

Pour connecter votre instance Adobe Commerce à la plateforme Adobe Experience, vous devez configurer les deux connecteurs, en commençant par le connecteur Commerce Services puis en finissant avec le connecteur Experience Platform.

## Mise à jour du connecteur Commerce Services

Si vous avez précédemment installé un service Adobe Commerce, vous avez probablement déjà configuré le connecteur Commerce Services. Si ce n’est pas le cas, vous devez effectuer les tâches suivantes sur la page [Connecteur Commerce Services](../landing/saas.md) page :

1. Connectez-vous à votre compte Commerce pour [récupération de vos clés d’API de production et d’environnement de test](../landing/saas.md#credentials).
1. Sélectionnez une [Espace de données SaaS](../landing/saas.md#saas-configuration).
1. Connectez-vous à votre compte Adobe pour [récupération de votre ID d’organisation](../landing/saas.md#ims-organization-optional).

Après avoir configuré le connecteur Commerce Services, vous pouvez configurer le connecteur Experience Platform.

## Mettre à jour le connecteur Experience Platform

Dans cette section, vous connectez votre instance Adobe Commerce à Adobe Experience Platform à l’aide de votre ID d’organisation. Vous pouvez ensuite spécifier le type de données - storefront ou back office - à envoyer à l’Experience Platform edge.

![Configuration du connecteur Experience Platform](assets/epc-config-dc.png)

## Général

1. Connectez-vous à votre compte Adobe dans le [Connecteur Commerce Services](../landing/saas.md#organizationid) et sélectionnez l’ID d’organisation.

   >[!NOTE]
   >
   >Si vous avez précédemment configuré le connecteur Commerce Services, vous pouvez ignorer cette étape, car votre ID d’organisation a déjà été sélectionné.

1. Dans Admin, accédez à **Système** > Services > **Connecteur Experience Platform**.

1. Dans le **Portée** , définissez le contexte sur **Site Web**.

1. Dans le **ID d’organisation** , vérifiez l’identifiant associé à votre compte Adobe Experience Platform, tel que configuré dans la variable [Connecteur Commerce Services](../landing/saas.md#organizationid). L’ID d’organisation est global. Un seul ID d’organisation peut être associé par instance Adobe Commerce.

1. (Facultatif) Si vous avez déjà une [SDK Web AEP (allié)](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html) déployé sur votre site, cochez la case et ajoutez le nom de votre SDK Web AEP. Sinon, laissez ces champs vides et le connecteur Experience Platform en déploie un pour vous.

   >[!NOTE]
   >
   >Si vous spécifiez votre propre SDK Web AEP, le connecteur Experience Platform utilise l’identifiant de flux de données associé à ce SDK et non l’identifiant de flux de données spécifié sur cette page (le cas échéant).

## Collecte de données

Dans le **Collecte de données** , sélectionnez les données storefront et/ou back-office à envoyer à l’Experience Platform edge. Pour vous assurer que votre instance Adobe Commerce peut commencer la collecte de données, reportez-vous à la section [conditions préalables](overview.md#prerequisites).

Consultez la rubrique Événements pour en savoir plus sur [storefront](events.md#storefront-events) et [back office](events.md#back-office-events) événements .

>[!NOTE]
>
>Tous les champs du champ **Collecte de données** s’appliquent à la section **Site Web** ou supérieure.

1. Sélectionner **Événements Storefront** si vous souhaitez envoyer des données comportementales storefront.

   >[!NOTE]
   >
   >Le **Événements Storefront** est automatiquement activée si le SDK Web AEP et l’ID d’organisation sont valides.

1. Sélectionner **Événements de back-office** si vous souhaitez envoyer des informations sur l’état de la commande, par exemple si une commande a été passée, annulée, remboursée ou expédiée.

   >[!NOTE]
   >
   >Si vous sélectionnez **Événements de back-office**, toutes les données du back-office sont envoyées au serveur Edge de l’Experience Platform. Si un acheteur choisit de se désabonner de la collecte de données, vous devez définir explicitement la préférence de confidentialité de l’acheteur dans l’Experience Platform. Cela diffère des événements storefront où le collecteur gère déjà le consentement en fonction des préférences de l’acheteur. [En savoir plus](https://experienceleague.adobe.com/docs/experience-platform/landing/governance-privacy-security/consent/adobe/dataset.html) à propos de la définition de la préférence de confidentialité d’un acheteur dans l’Experience Platform.

1. Pour garantir les mises à jour des données d’événement du back-office selon un planning [cron](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) , vous devez modifier la fonction `Sales Orders Feed` index à `Update by Schedule`.

   1. Sur le _Administration_ barre latérale, accédez à **[!UICONTROL System]** > _[!UICONTROL Tools]_>**[!UICONTROL Index Management]**.

   1. Cochez la case correspondant au `Sales Orders Feed` indexeur.

   1. Définir **[!UICONTROL Actions]** to `Update by Schedule`.

   1. Si vous activez les données du back-office pour la première fois, exécutez les commandes suivantes pour réindexer et déclencher une nouvelle synchronisation. Les resynchronisations suivantes se produisent automatiquement tant que la variable [cron](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) est configurée correctement.

      ```bash
      bin/magento index:reindex sales_order_data_exporter_v2
      ```

      ```bash
      bin/magento saas:resync --feed orders
      ```

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
| Événements de back-office | Si cette case est cochée, la payload d’événement contient des informations d’état de commande anonymes, telles qu’une commande passée, annulée, remboursée ou expédiée. |
| Identifiant de flux de données (site web) | Identifiant qui permet aux données de passer de Adobe Experience Platform à d’autres produits DX d’Adobe. Cet identifiant doit être associé à un site web spécifique au sein de votre instance Adobe Commerce spécifique. Si vous spécifiez votre propre SDK Web Experience Platform, ne spécifiez pas d’identifiant de flux de données dans ce champ. Le connecteur Experience Platform utilise l’identifiant de flux de données associé à ce SDK et ignore tout identifiant de flux de données spécifié dans ce champ (le cas échéant). |

## Vérifier que les données sont envoyées à l’Experience Platform

Une fois l’intégration effectuée, les données du storefront commencent à s’écouler vers le bord Experience Platform. Les données du back-office prennent environ 5 minutes après l’intégration pour que les données s’affichent à la périphérie. Les mises à jour suivantes sont visibles à la périphérie en fonction de la planification cron.

Lorsque des données Commerce sont envoyées à l’Experience Platform Edge, vous pouvez créer des rapports comme suit :

![Données commerciales dans Adobe Experience Platform](assets/aem-data-1.png)
_Données commerciales dans Adobe Experience Platform_
