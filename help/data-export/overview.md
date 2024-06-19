---
title: "[!DNL SaaS Data Export Guide]"
description: "En savoir plus sur l’utilisation de la variable [!DNL data export] extension pour les services Adobe Commerce SaaS qui synchronisent les données entre Adobe Commerce et les services Commerce connectés."
role: Admin, Developer
recommendations: noCatalog
source-git-commit: 8230756c203cb2b4bdb4949f116c398fcaab84ff
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# Guide [!DNL SaaS Data Export]

[!DNL SaaS data export] améliore les performances front-end en optimisant la synchronisation des données entre une instance Adobe Commerce et les services Commerce connectés. Lorsque vous ajoutez Live Search, Product Recommendations ou Catalog Service à une installation Adobe Commerce, la variable [!DNL Data export] l’extension est installée automatiquement.

L’exportation des données SaaS collecte et exporte divers types de données, appelés _flux_, qui regroupe des types d’informations spécifiques. Selon les services Commerce installés, les flux d’exportation de données SaaS incluent :

- **Flux d’entité de catalogue** agrégez les données de produit. Les données comprennent les produits, les attributs de produit, les prix des produits, les variations de produit, les catégories, les autorisations de catégorie et les autorisations de produit.
- La variable **Flux Scopes** agrège les données pour les groupes de clients, les sites web, les magasins et les vues de magasin.
- La variable **Saut de commande** agrège les données des commandes, y compris les entités qui leur sont associées, telles que les factures, les envois, les notes de crédit, etc.
- La variable **Flux d’inventaire multisource** agrège les données sur les éléments d’état de stock.

L’extension d’export de données prend en charge plusieurs méthodes pour lancer et gérer le processus de synchronisation des données.

- **Synchronisation manuelle depuis l’administrateur ou la ligne de commande**

   - La variable [Tableau de bord Data Management](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard) dans Commerce Admin fournit une vue graphique de l’état de synchronisation. Vous pouvez utiliser le tableau de bord pour effectuer une resynchronisation complète (_synchronisation complète_) de tous les flux. Toutefois, Adobe recommande de n’effectuer une synchronisation complète que la première fois que vous connectez Adobe Commerce à un service Commerce. Voir [Processus de synchronisation](data-synchronization.md).

   - La variable [Outil de ligne de commande Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/config-cli) (interface de ligne de commande) fournit des commandes pour synchroniser des flux spécifiques et inclut des options supplémentaires pour personnaliser le traitement des flux.

- **Synchronisation automatisée avec les tâches cron**

   - [Synchronisation partielle des données](data-synchronization.md#partial-synchronization-with-cron-jobs): les tâches Cron déclenchent une synchronisation partielle des données lorsqu’un utilisateur administrateur Commerce met à jour une entité. Le processus d’exportation des données envoie uniquement ces mises à jour aux services Commerce connectés. Le processus de synchronisation partielle est basé sur le mécanisme MView et ne nécessite aucune action de la part de l’utilisateur administrateur ou de l’intégrateur système.

   - [Réessayer automatique pour les erreurs de synchronisation](data-synchronization.md#failed-items-sync-for-error-recovery): les tâches Cron déclenchent une reprise automatique du processus de synchronisation lorsque des erreurs se produisent pendant le processus de synchronisation des données.

- **Planification et performances de l’exportation**

   - Les développeurs et les intégrateurs système peuvent estimer le temps nécessaire à l’exportation des données SaaS pour synchroniser les données entre Adobe Commerce et les services connectés. Cette estimation peut vous aider à planifier le traitement de l’exportation des données afin d’éviter toute interruption de site. Voir [Estimation du volume des données et du temps de transmission](estimate-data-volume-sync-time.md).

   - Dans les cas où la synchronisation doit se produire plus rapidement, l’exportation des données SaaS fournit des options de personnalisation pour améliorer les performances de traitement de l’exportation. Voir [Amélioration des performances d’exportation des données](customize-export-processing.md).

- **Suivi et dépannage des activités d’exportation de données**: utilisez les journaux d’exportation de données et d’exportation de données pour passer en revue l’état de synchronisation et les payloads du flux pendant le processus de synchronisation et d’indexation. Voir [Journalisation et dépannage](troubleshooting-logging.md).



