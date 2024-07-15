---
title: Rapport État des paiements de commande
description: Utilisez le rapport État des paiements de la commande pour connaître l’état des paiements de vos commandes et identifier les problèmes potentiels.
role: User
level: Intermediate
exl-id: 192e47b9-d52b-4dcf-a720-38459156fda4
feature: Payments, Checkout, Orders
source-git-commit: 0dc370409ace6ac6b0a56511cd0071cf525620f1
workflow-type: tm+mt
source-wordcount: '2045'
ht-degree: 0%

---

# Rapport État des paiements de commande

[!DNL Payment Services] pour [!DNL Adobe Commerce] et [!DNL Magento Open Source] vous offre des rapports complets afin que vous puissiez obtenir une vue claire des [transactions](transactions.md), commandes et paiements de votre boutique.

Deux vues de rapport d’état des paiements de commande sont disponibles pour vous permettre d’afficher rapidement l’état des paiements de vos commandes :

* **[Vue de visualisation de l’état des paiements des commandes](#order-payment-status-data-visualization-view)** : graphique disponible sur la page d’accueil des services de paiement qui est une représentation visuelle des états de paiement agrégés par jour depuis la vue du rapport d’état des paiements de commande
* **[Rapport d’état de paiement de la commande vue](#order-payment-status-report-view)** : rapport disponible dans l’état de paiement de la commande qui indique le paiement détaillé, la facturation, l’expédition, le remboursement et les statistiques de litige pour toutes les transactions.

Les vues d’état des paiements de la commande vous aident à comprendre facilement où se trouve une commande spécifique dans le flux de processus de trésorerie. Ces rapports vous permettent d’afficher rapidement les commandes, en fonction de leur état de paiement et de leur date de paiement, et d’identifier les problèmes potentiels.

Vous pouvez [télécharger les états de paiement des commandes](#download-order-payment-statuses) au format de fichier .csv pour les utiliser dans les logiciels de comptabilité ou de gestion de commandes existants.

>[!NOTE]
>
>Vous ne pouvez pas afficher de rapports financiers si vous n’avez pas [intégré et activé le mode réel](production.md#enable-live-payments) pour [!DNL Payment Services].

## Vue de visualisation des données d’état de paiement des commandes

La visualisation des données d’état des paiements de la commande est disponible dans la page d’accueil des services de paiement. Il s’agit d’une représentation visuelle des états de paiement agrégés par jour à partir de la [vue de rapport d’état des paiements de la commande](#order-payment-status-report-view) du tableau détaillé.

Sur la barre latérale _Admin_, accédez à **Ventes** > **Services de paiement** > _Commandes_ pour afficher la visualisation de données [ états de paiement ](#statuses-information) de la carte de données.

![Visualisation des données de paiement dans l’Admin](assets/orderpayment-dataviz.png){width="800" zoomable="yes"}

Cliquez sur **[!UICONTROL View Report]** pour accéder au tableau détaillé [ {vue du rapport d’état des paiements de commande](#order-payment-status-report-view).

### Personnalisation de la période des états

Par défaut, les états des 30 jours de paiement s’affichent.

Dans la vue Visualisation de l’état des paiements des commandes, vous pouvez personnaliser la période des états de paiement que vous souhaitez afficher en sélectionnant une période :

1. Sur la barre latérale _Admin_, accédez à **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**. La visualisation des données de statut des paiements de commande est visible dans la section _Commandes_ .
1. Cliquez sur le filtre du sélecteur **[!UICONTROL Range]**.
1. Sélectionnez la période applicable : 30 jours, 15 jours ou 7 jours.
1. Affichez les informations d’état pour les dates spécifiées.

### Informations sur les états

Les états de paiement pour une période sélectionnée sont affichés à gauche de la vue de visualisation des données sur l’état des paiements de la commande . Les dates de la période sélectionnée s’affichent au bas de la vue. Si aucune commande n’a été effectuée à une date spécifique, cette date n’apparaît pas.

La visualisation des données de statut des paiements de commande comprend les informations suivantes.

| Données | Description |
| ------------ | -------------------- |
| [!UICONTROL Orders] | Période des commandes pendant une période donnée ; données sur l’axe Y (gauche) |
| Période | Période pour la période spécifiée ; données sur l’axe X (bas) |
| Autorisé | Commande autorisée |
| Capture demandée | Capture demandée pour commande |
| Capture confirmée | Capture de commande terminée |
| Capture partielle | Commande partiellement capturée |
| Échec de la capture | Échec de la capture de commande |
| Annulé | Ordre annulé |

## Afficher le rapport d’état des paiements

La vue du rapport État des paiements de la commande est disponible dans la vue Accueil des services de paiement. Il comprend des états détaillés (paiement, facturation, expédition, remboursement, litige, etc.) pour toutes les transactions.

Sur la barre latérale _Admin_, accédez à **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > _[!UICONTROL Orders]_>**[!UICONTROL View Report]**pour afficher le rapport détaillé sur l’état des paiements de la commande.

![ Commande des transactions d’état de paiement dans l’Admin](assets/orders-report-data.png){width="800" zoomable="yes"}

Vous pouvez configurer cette vue, selon les sections de cette rubrique, pour présenter au mieux les données que vous souhaitez afficher.

Vous pouvez [télécharger les transactions de paiement](#download-order-payment-statuses) au format de fichier .csv pour les utiliser dans un logiciel de comptabilité ou de gestion de commandes existant.

>[!NOTE]
>
>Les données affichées dans ce tableau sont triées par défaut dans l’ordre décroissant (`DESC`) à l’aide de `TRANS DATE`. `TRANS DATE` est la date et l’heure auxquelles la transaction a été lancée.

### Mises à jour du statut des paiements

Certains modes de paiement nécessitent un délai pour capturer le paiement. [!DNL Payment Services] détecte désormais les états en attente d’une transaction de paiement dans une commande en :

* Détection synchrone de `pending capture` transactions
* Surveillance asynchrone des transactions `pending capture`

>[!NOTE]
>
>La détection des états en attente des transactions de paiement dans une commande empêche l’expédition accidentelle des commandes si le paiement n’a pas encore été reçu. Cela peut se produire pour les transactions de contrôle électronique et PayPal.

#### Détection synchrone des transactions de capture en attente

Détecter automatiquement les transactions de capture dans un état `Pending` et empêcher les commandes de saisir un état `Processing` lorsqu’une telle transaction est détectée.

Lors de l’extraction du client ou lorsqu’un administrateur crée une facture pour un paiement précédemment autorisé, [!DNL Payment Services] détecte automatiquement les transactions de capture dans un état `Pending` et classe les commandes correspondantes dans le statut `Payment Review`.

#### Surveillance asynchrone des transactions de capture en attente

Détectez lorsqu’une transaction de capture en attente entre dans un état `Completed` afin que les marchands puissent reprendre le traitement de la commande affectée.

Pour s’assurer que ce processus fonctionne comme prévu, les marchands doivent configurer une nouvelle tâche cron. Une fois que la tâche est configurée pour s’exécuter automatiquement, aucune autre intervention du marchand n’est attendue.

Voir [Configuration de tâches cron](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html). Une fois configurée, la nouvelle tâche s’exécute toutes les 30 minutes pour récupérer les mises à jour des commandes dont l’état est `Payment Review`.

Les vendeurs peuvent vérifier le statut du paiement mis à jour à l’aide de la vue Rapport d’état des paiements de la commande .

### Données utilisées dans le rapport

[!DNL Payment Services] utilise les données de commande et les combine aux données de paiement agrégées provenant d’autres sources (y compris PayPal) afin de fournir des rapports significatifs et très utiles.

Les données de commande sont exportées et conservées dans le service de paiement. Lorsque vous [modifiez ou ajoutez des statuts de commande](https://docs.magento.com/user-guide/sales/order-status-custom.html) ou [modifiez une vue de magasin](https://docs.magento.com/user-guide/stores/stores-all-view-edit.html), [magasin](https://docs.magento.com/user-guide/stores/store-information.html) ou un nom de site web, ces données sont combinées avec des données de paiement et le rapport d’état du paiement de la commande est renseigné avec les informations combinées.

Ce processus comprend deux étapes :

1. L’index est modifié par `ON SAVE` (chaque fois que les informations de commande ou de magasin sont modifiées) ou `BY SCHEDULE` (selon un planning cron préconfiguré), selon la manière dont il est configuré dans la [Gestion des index](https://docs.magento.com/user-guide/system/index-management.html) dans l’administrateur.

   Par défaut, l’indexation des données se produit `ON SAVE`, ce qui signifie que chaque fois qu’un élément change dans l’ordre, l’état de la commande, la vue de magasin, le magasin ou le site web, le processus de réindexation se produit immédiatement.

1. Les données indexées sont envoyées au service de paiement, qui les renseigne ensuite dans le rapport État du paiement de la commande .

Les seules données exportées et regroupées à des fins de création de rapports sont les données utilisées par le rapport d’état des paiements des commandes .

>[!NOTE]
>
>Les données affichées dans ce tableau sont triées par défaut dans l’ordre décroissant (`DESC`) à l’aide de `ORDER DATE`. `ORDER DATE` est la date et l’heure auxquelles la commande a été créée.

#### Configuration de l’exportation des données

Même si, par défaut, la réindexation se produit en mode `ON SAVE`, il est recommandé d’indexer en mode `BY SCHEDULE`. L’index `BY SCHEDULE` s’exécute selon un planning cron d’une minute, et toutes les données modifiées s’affichent dans votre rapport d’état de la commande dans les deux minutes suivant tout changement de données. Cette réindexation planifiée vous aide à réduire toute contrainte sur votre boutique, en particulier si vous avez un grand volume de commandes entrantes, car cela se produit sur un planning (et non au moment où chaque commande est passée).

Vous pouvez modifier le mode d’index—`ON SAVE` ou `BY SCHEDULE`—[dans l’Admin](https://docs.magento.com/user-guide/system/index-management.html#change-the-index-mode).

Pour savoir comment configurer l’exportation des données, voir [Configuration de ligne de commande](configure-cli.md#configure-data-export).

### Sélectionner la source de données

Dans la vue Rapport d’état des paiements de la commande, vous pouvez sélectionner la source de données, **[!UICONTROL Live]** _ ou **[!UICONTROL Sandbox]**, pour laquelle vous souhaitez afficher les résultats du rapport.

![Choix des sources de données](assets/datasource.png){width="300" zoomable="yes"}

Si _[!UICONTROL Live]_est la source de données sélectionnée, vous pouvez afficher les informations de rapport pour vos magasins qui utilisent [!DNL Payment Services] en mode de production. Si_[!UICONTROL Sandbox]_ est la source de données sélectionnée, vous pouvez afficher les informations de rapport pour le mode sandbox.

Les sélections de sources de données fonctionnent comme suit :

* Si vous ne disposez d’aucun magasin utilisant [!DNL Payment Services] en mode réel, la sélection de source de données est définie par défaut sur _[!UICONTROL Sandbox]_.
* Si vous avez des magasins (un ou plusieurs) qui utilisent [!DNL Payment Services] en mode réel, la sélection de source de données est définie par défaut sur _[!UICONTROL Live]_.
* Les exportations de rapports respectent toujours la sélection de la source de données.

Pour sélectionner la source de données de votre rapport [!UICONTROL Order Payment Status] :

1. Sur la barre latérale _Admin_, accédez à **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Orders]** > **[!UICONTROL View Report]**.
1. Cliquez sur le filtre de sélecteur _[!UICONTROL Data source]_et sélectionnez **[!UICONTROL Live]**ou **[!UICONTROL Sandbox]**.

   Les résultats du rapport se régénèrent en fonction de la source de données sélectionnée.

### Personnalisation de la période des dates de commande

Dans la vue Rapport d’état des paiements de la commande, vous pouvez personnaliser la période des résultats d’état que vous souhaitez afficher en sélectionnant des dates spécifiques. Par défaut, 30 jours de statut de paiement de la commande sont affichés dans la grille.

1. Sur la barre latérale _Admin_, accédez à **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Orders]_>**[!UICONTROL View Report]**.
1. Cliquez sur le filtre du sélecteur de calendrier _[!UICONTROL Order dates]_.
1. Sélectionnez la période applicable.
1. Affichez les états des paiements de la commande pour les dates spécifiées dans la grille.

### Filtrage des informations sur le rapport

Dans la vue Rapport d’état des paiements des commandes , vous pouvez filtrer les résultats des états que vous souhaitez afficher en sélectionnant des critères de filtrage.

1. Sur la barre latérale _Admin_, accédez à **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Orders]_>**[!UICONTROL View Report]**.
1. Cliquez sur le sélecteur **[!UICONTROL Filter]**.
1. Active/désactive les options _État de paiement_ afin d’afficher les résultats des rapports uniquement pour les états de paiement de commande sélectionnés.
1. Affichez les résultats du rapport dans une plage de valeurs de commande en saisissant un _[!UICONTROL Min Order Amount]_ou _[!UICONTROL Max Order Amount_].
1. Cliquez sur **[!UICONTROL Hide filters]** pour masquer le filtre.

### Afficher et masquer les colonnes

Le rapport État du paiement de la commande affiche toutes les colonnes d’informations disponibles par défaut. Vous pouvez toutefois personnaliser les colonnes affichées dans votre rapport.

1. Sur la barre latérale _Admin_, accédez à **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Orders]_>**[!UICONTROL View Report]**.
1. Cliquez sur l&#39;icône _Paramètres de colonne_ (![icône de paramètres de colonne](assets/column-settings.png){width="20" zoomable="yes"}).
1. Pour personnaliser les colonnes affichées dans le rapport, cochez ou décochez les colonnes de la liste.

   Le rapport État des paiements de la commande affiche immédiatement les modifications que vous avez apportées au menu Paramètres de colonne . Les préférences de colonne sont enregistrées et restent en vigueur si vous quittez la vue du rapport.

### Affichage des états

La vue du rapport État des paiements de la commande affiche des informations complètes sur l’état des paiements pour chaque commande.

Par défaut, 30 jours de statut de paiement de la commande sont affichés dans la grille.

Faites défiler vers la gauche et la droite pour afficher les [informations sur l’état du paiement de la commande](#column-descriptions), y compris la date de commande, la date autorisée, la facturation, l’expédition, l’état du paiement, etc.

Le nombre de lignes renvoyé dans une recherche, ou indiqué dans les 30 jours par défaut de l’état du paiement de la commande, s’affiche au-dessus de la grille d’affichage de l’état du paiement de la commande avec le filtre du sélecteur de calendrier des dates de commande .

#### Statut de la paie

La colonne État des paiements indique l’état actuel de tout paiement. Un paiement `Capture failed` affiche un état d’alerte rouge et un paiement `Voided` un état d’alerte gris.

#### Statut du remboursement

La colonne Etat du remboursement indique l&#39;état actuel d&#39;un remboursement. Un paiement `Capture failed` affiche un état d’alerte rouge et un paiement `Voided` un état d’alerte gris.

### Mise à jour des données de rapport

La vue du rapport État des paiements de la commande affiche un horodatage _[!UICONTROL Last updated]_qui indique la dernière fois que les informations du rapport ont été mises à jour. Par défaut, les données du rapport d’état des paiements de la commande sont automatiquement actualisées toutes les trois heures.

Vous pouvez également forcer manuellement l’actualisation des données du rapport État des paiements de la commande afin d’afficher les informations de rapport les plus récentes.

1. Sur la barre latérale _Admin_, accédez à **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Orders]_>**[!UICONTROL View Report]**.
1. Cliquez sur l’icône _Actualiser_ (![icône d’actualisation](assets/refresh-button-med.png){width="20" zoomable="yes"}).

   Les données du rapport d’état des paiements de la commande sont actualisées, une confirmation *[!UICONTROL Update complete]* s’affiche et les informations les plus récentes sont présentes dans la grille.

### Afficher les conflits

Vous pouvez afficher tous les litiges relatifs aux commandes de votre boutique et accéder au Centre de résolution PayPal pour agir sur ces litiges, depuis le rapport État des paiements des commandes .

1. Sur la barre latérale _Admin_, accédez à **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Orders]_>**[!UICONTROL View Report]**.
1. Accédez au **[!UICONTROL Disputes column]**.
1. Affichez tous les litiges pour un ordre spécifique et consultez [le statut du litige](#order-payment-status-information).
1. Passez en revue les détails des litiges à partir du [centre de résolution PayPal](https://www.paypal.com/us/cshelp/article/what-is-the-resolution-center-help246) en cliquant sur le lien ID des litiges qui commence par _PP-D-_.
1. Prenez les mesures appropriées pour résoudre le conflit, le cas échéant.

   Pour trier les conflits d’ordre par état, cliquez sur l’en-tête de colonne [!UICONTROL Disputes].

### Télécharger les statuts de paiement des commandes

Vous pouvez télécharger un fichier .csv avec tous les états visibles dans la grille Affichage de l’état des paiements des commandes , que vous visualisiez les 30 jours par défaut des états ou une période personnalisée.

1. Sur la barre latérale _Admin_, accédez à **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Orders]_>**[!UICONTROL View Report]**.
1. Si vous souhaitez afficher les états pour une période autre que les 30 derniers jours, [personnalisez la période de la période de la période de vos états](#customize-dates-timeframe).
1. Cliquez sur l&#39;icône _Télécharger_ (![icône de téléchargement](assets/icon-download.png){width="20" zoomable="yes"}).

Les statuts de paiement de votre commande sont téléchargés au format .csv .

### Descriptions des colonnes

Les rapports d’état des paiements de commande incluent les informations suivantes.

| Colonne | Description |
| ------------ | -------------------- |
| [!UICONTROL Order ID] | ID de commande Commerce<br> <br>Pour afficher les [informations sur la commande](https://docs.magento.com/user-guide/sales/orders.html){target="_blank"} associées, cliquez sur l’ID. |
| [!UICONTROL Order Date] | Date et heure de la commande |
| [!UICONTROL Authorized Date] | Date et heure de l’autorisation de paiement |
| [!UICONTROL Order Status] | Commerce actuel [état de commande](https://docs.magento.com/user-guide/sales/order-status.html){target="_blank"} |
| [!UICONTROL Invoiced] | État de la facture de la commande : *[!UICONTROL No]*, *[!UICONTROL Partial]* ou *[!UICONTROL Yes]* |
| [!UICONTROL Shipped] | Etat d&#39;expédition de la commande : *[!UICONTROL No]*, *[!UICONTROL Partial]* ou *[!UICONTROL Yes]* |
| [!UICONTROL Order Amt] | Montant total général de la commande |
| [!UICONTROL Cur] | Type de devise de la commande |
| [!UICONTROL Pay Status] | État de paiement d’une commande spécifique |
| [!UICONTROL Paid Amt] | Montant payé sur une commande |
| [!UICONTROL Cur] | Type de devise du montant payé sur une commande. |
| [!UICONTROL Refund Status] | État d’un remboursement sur une commande (comme des informations provenant de retours, de MA et de notes de crédit)—   *[!UICONTROL Requires refund]*, *[!UICONTROL Refund requested]*, *[!UICONTROL Refunded]*, *[!UICONTROL Refund failed]* ou *[!UICONTROL Voided]* |
| [!UICONTROL Refund Amount] | Montant total remboursé pour une commande |
| [!UICONTROL Cur] | Type de devise du montant remboursé pour une commande. |
| [!UICONTROL Disputes] | État de tout litige sur une commande (informations de litiges et de rechargements)—*[!UICONTROL Open]*, *[!UICONTROL Waiting for buyer response]*, *[!UICONTROL Waiting for seller response]*, *[!UICONTROL Under review]*, *[!UICONTROL Resolved]* ou *[!UICONTROL Other]* |
| [!UICONTROL Payment Method] | Mode de paiement utilisé dans la transaction Commerce pour une commande |
| [!UICONTROL Website] | Site web à partir duquel la commande a été passée |
| [!UICONTROL Store] | Magasin à partir duquel la commande a été passée |
| [!UICONTROL Store View] | Vue de magasin à partir de laquelle la commande a été passée |
