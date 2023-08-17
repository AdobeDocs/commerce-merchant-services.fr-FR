---
title: Configuration du processus d’arrière-plan
description: "Configuration des plannings pour [!DNL Store Fulfillment] processus d’arrière-plan utilisés pour synchroniser les données avec les services d’exécution."
role: Admin, Developer
level: Intermediate
exl-id: 742ae59e-77a0-4db6-b156-2992d4403be7
source-git-commit: 36b57648e156ead801764f3ee4e5e6a0f3245fe6
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 0%

---


# Configuration du processus d’arrière-plan

L’intégration d’exécution de magasin utilise des processus en arrière-plan et des files d’attente de messages pour des performances et une échelle optimales. Créez des environnements pour vos magasins Adobe Commerce à l’aide de [variables de déploiement](https://devdocs.magento.com/cloud/env/variables-deploy.html#cron_consumers_runner) qui démarre automatiquement [exécuteurs de file d’attente des messages](https://devdocs.magento.com/guides/v2.4/config-guide/mq/rabbitmq-overview.html).

Les processus en arrière-plan sont gérés à l’aide de la Adobe Commerce standard. [Tâches planifiées](https://docs.magento.com/user-guide/system/cron.html) . Ces processus sont chargés de synchroniser les données de configuration de magasin de commerce et de commande avec les services web d’exécution de magasin.

## Gestion des tâches planifiées pour l’exécution du magasin

Depuis l’administrateur, accédez à **[!UICONTROL Stores > Configuration > Advanced > System > Cron (Scheduled Tasks) > Cron configuration options for group:store_fulfillment]**.

Examinez la configuration par défaut des services d’exécution de magasin. Vous pouvez personnaliser ces paramètres en fonction du volume de traitement des commandes et de la disponibilité des ressources.
