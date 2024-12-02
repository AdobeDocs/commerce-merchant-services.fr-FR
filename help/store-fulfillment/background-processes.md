---
title: Configuration du processus d’arrière-plan
description: Configurez les plannings pour les processus  [!DNL Store Fulfillment] en arrière-plan utilisés pour synchroniser les données avec les services d’exécution.
role: Admin, Developer
level: Intermediate
exl-id: 742ae59e-77a0-4db6-b156-2992d4403be7
source-git-commit: 37380063242b6d904910be731b8e58471625e9cb
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 0%

---


# Configuration du processus d’arrière-plan

L’intégration d’exécution de magasin utilise des processus en arrière-plan et des files d’attente de messages pour des performances et une échelle optimales. Créez des environnements pour vos magasins Adobe Commerce à l’aide de [variables de déploiement](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#cron_consumers_runner) qui démarrent automatiquement les [ exécutants de la file d’attente des messages](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/message-queues/message-queue-framework).

Les processus en arrière-plan sont gérés à l’aide de la fonctionnalité standard d’ [ tâches planifiées](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cron) d’Adobe Commerce. Ces processus sont chargés de synchroniser les données de configuration de magasin de commerce et de commande avec les services web d’exécution de magasin.

## Gestion des tâches planifiées pour l’exécution du magasin

Depuis l’administrateur, accédez à **[!UICONTROL Stores > Configuration > Advanced > System > Cron (Scheduled Tasks) > Cron configuration options for group:store_fulfillment]**.

Examinez la configuration par défaut des services d’exécution de magasin. Vous pouvez personnaliser ces paramètres en fonction du volume de traitement des commandes et de la disponibilité des ressources.
