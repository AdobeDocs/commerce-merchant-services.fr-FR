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

[!DNL Payment Services] pour [!DNL Adobe Commerce] et [!DNL Magento Open Source] vous offre des rapports complets afin que vous puissiez obtenir une vue claire des [transactions](transactions.md), commandes et paiements.

Deux vues de rapport d’état des paiements de commande sont disponibles pour vous permettre d’afficher rapidement l’état des paiements de vos commandes :

* **[Visualisation de l’état des paiements des commandes](#order-payment-status-data-visualization-view)**—Graphique disponible sur la page d’accueil des services de paiement qui est une représentation visuelle des états de paiement agrégés par jour à partir de la vue de rapport État des paiements de la commande
* **[Afficher le rapport d’état des paiements](#order-payment-status-report-view)**: rapport disponible dans le statut Paiement de la commande qui affiche le paiement détaillé, la facture, l’expédition, le remboursement et les statuts des litiges pour toutes les transactions.

Les vues d’état des paiements de la commande vous aident à comprendre facilement où se trouve une commande spécifique dans le flux de processus de trésorerie. Ces rapports vous permettent d’afficher rapidement les commandes, en fonction de leur état de paiement et de leur date de paiement, et d’identifier les problèmes potentiels.

Vous pouvez [télécharger Statuts de paiement des commandes](#download-order-payment-statuses) dans un format de fichier .csv à utiliser dans les logiciels de gestion des commandes ou de comptabilité existants.

>[!NOTE]
>
>Vous ne pouvez pas afficher les rapports financiers si vous n’avez pas [Mode réel intégré et activé](production.md#enable-live-payments) pour [!DNL Payment Services].

## Vue de visualisation des données d’état de paiement des commandes

La visualisation des données d’état des paiements de la commande est disponible dans la page d’accueil des services de paiement. Il s’agit d’une représentation visuelle des états de paiement agrégés par jour à partir du tableau détaillé [Afficher le rapport d’état des paiements](#order-payment-status-report-view).

Sur le _Administration_ barre latérale, accédez à **Ventes** > **Services de paiement** > _Commandes_ pour afficher la visualisation des données [graphique des états des paiements](#statuses-information).

![Visualisation des données de paiement dans l’Admin](assets/orderpayment-dataviz.png){width="800" zoomable="yes"}

Cliquez sur **[!UICONTROL View Report]** pour accéder au tableau détaillé [Afficher le rapport d’état des paiements](#order-payment-status-report-view).

### Personnalisation de la période des états

Par défaut, les états des 30 jours de paiement s’affichent.

Dans la vue Visualisation de l’état des paiements des commandes, vous pouvez personnaliser la période des états de paiement que vous souhaitez afficher en sélectionnant une période :

1. Sur le _Administration_ barre latérale, accédez à **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**. La visualisation des données d’état des paiements de commande est visible dans la _Commandes_ .
1. Cliquez sur le bouton **[!UICONTROL Range]** filtre de sélecteur.
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

Sur le _Administration_ barre latérale, accédez à **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > _[!UICONTROL Orders]_>**[!UICONTROL View Report]**pour afficher le tableau détaillé Rapport d’état des paiements de la commande .

![Commande des transactions d’état de paiement dans l’administrateur](assets/orders-report-data.png){width="800" zoomable="yes"}

Vous pouvez configurer cette vue, selon les sections de cette rubrique, pour présenter au mieux les données que vous souhaitez afficher.

Vous pouvez [téléchargement des transactions de paiement](#download-order-payment-statuses) dans un format de fichier .csv à utiliser dans les logiciels de gestion des commandes ou de comptabilité existants.

>[!NOTE]
>
>Les données affichées dans ce tableau sont triées par ordre décroissant (`DESC`) par défaut, à l’aide de la fonction `TRANS DATE`. La variable `TRANS DATE` est la date et l’heure auxquelles la transaction a été lancée.

### Mises à jour du statut des paiements

Certains modes de paiement nécessitent un délai pour capturer le paiement. [!DNL Payment Services] détecte désormais les états en attente d’une transaction de paiement dans une commande en :

* Détection synchrone `pending capture` transactions
* Surveillance asynchrone `pending capture` transactions

>[!NOTE]
>
>La détection des états en attente des transactions de paiement dans une commande empêche l’expédition accidentelle des commandes si le paiement n’a pas encore été reçu. Cela peut se produire pour les transactions de contrôle électronique et PayPal.

#### Détection synchrone des transactions de capture en attente

Détecter automatiquement les transactions de capture dans un `Pending` et empêcher les commandes de saisir un `Processing` statut lorsqu’une telle transaction est détectée.

Lors de l’extraction d’un client ou lorsqu’un administrateur crée une facture pour un paiement précédemment autorisé, [!DNL Payment Services] détecte automatiquement les transactions de capture dans une `Pending` l’état et les commandes correspondantes sont `Payment Review` statut.

#### Surveillance asynchrone des transactions de capture en attente

Détecter lorsqu’une transaction de capture en attente entre dans une `Completed` de sorte que les marchands puissent reprendre le traitement de la commande affectée.

Pour s’assurer que ce processus fonctionne comme prévu, les marchands doivent configurer une nouvelle tâche cron. Une fois que la tâche est configurée pour s’exécuter automatiquement, aucune autre intervention du marchand n’est attendue.

Voir [Configuration des tâches cron](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html). Une fois configurée, la nouvelle tâche s’exécute toutes les 30 minutes pour récupérer les mises à jour des commandes qui se trouvent dans un `Payment Review` statut.

Les vendeurs peuvent vérifier le statut du paiement mis à jour à l’aide de la vue Rapport d’état des paiements de la commande .

### Données utilisées dans le rapport

[!DNL Payment Services] utilise les données de commande et les combine aux données de paiement agrégées provenant d’autres sources (y compris PayPal) afin de fournir des rapports pertinents et très utiles.

Les données de commande sont exportées et conservées dans le service de paiement. Lorsque vous [modifier ou ajouter des statuts de commande ;](https://docs.magento.com/user-guide/sales/order-status-custom.html) ou [modification d’une vue de magasin](https://docs.magento.com/user-guide/stores/stores-all-view-edit.html), [store](https://docs.magento.com/user-guide/stores/store-information.html), ou nom du site web, ces données sont combinées avec les données de paiement et le rapport État du paiement de la commande est renseigné avec les informations combinées.

Ce processus comprend deux étapes :

1. Les données de l’index sont modifiées : `ON SAVE` (chaque fois que les informations de commande ou de magasin sont modifiées) ou `BY SCHEDULE` (selon un planning cron préconfiguré), selon la manière dont il est configuré dans [Gestion des index](https://docs.magento.com/user-guide/system/index-management.html) dans Admin.

   Par défaut, l’indexation des données se produit. `ON SAVE`, ce qui signifie que chaque fois qu’un élément change dans l’ordre, l’état de la commande, l’affichage du magasin, le magasin ou le site web, le processus de réindexation se produit immédiatement.

1. Les données indexées sont envoyées au service de paiement, qui les renseigne ensuite dans le rapport État du paiement de la commande .

Les seules données exportées et regroupées à des fins de création de rapports sont les données utilisées par le rapport d’état des paiements des commandes .

>[!NOTE]
>
>Les données affichées dans ce tableau sont triées par ordre décroissant (`DESC`) par défaut, à l’aide de la fonction `ORDER DATE`. La variable `ORDER DATE` est la date et l’heure auxquelles la commande a été créée.

#### Configuration de l’exportation des données

Même si, par défaut, la réindexation se produit dans `ON SAVE` , il est recommandé d’indexer dans `BY SCHEDULE` mode . La variable `BY SCHEDULE` s’exécute selon un planning cron d’une minute. Toute donnée modifiée apparaît dans votre rapport d’état de commande dans les deux minutes suivant tout changement de données. Cette réindexation planifiée vous aide à réduire toute contrainte sur votre boutique, en particulier si vous avez un grand volume de commandes entrantes, car cela se produit sur un planning (et non au moment où chaque commande est passée).

Vous pouvez modifier le mode d’index :`ON SAVE` ou `BY SCHEDULE`—[dans Admin](https://docs.magento.com/user-guide/system/index-management.html#change-the-index-mode).

Pour savoir comment configurer l’exportation des données, voir [Configuration de ligne de commande](configure-cli.md#configure-data-export).

### Sélectionner la source de données

Dans la vue Rapport d’état des paiements de la commande, vous pouvez sélectionner la source de données :**[!UICONTROL Live]** _ ou **[!UICONTROL Sandbox]**: pour lequel vous souhaitez afficher les résultats du rapport.

![Sélection des sources de données](assets/datasource.png){width="300" zoomable="yes"}

If _[!UICONTROL Live]_est la source de données sélectionnée. Vous pouvez afficher les informations de rapport pour vos magasins qui utilisent [!DNL Payment Services] en mode de production. If_[!UICONTROL Sandbox]_ est la source de données sélectionnée. vous pouvez afficher les informations de rapport pour le mode sandbox.

Les sélections de sources de données fonctionnent comme suit :

* Si vous ne disposez d’aucun magasin qui utilise [!DNL Payment Services] en mode réel, la sélection de source de données est définie par défaut sur _[!UICONTROL Sandbox]_.
* Si des magasins (un ou plusieurs magasins) utilisent [!DNL Payment Services] en mode réel, la sélection de source de données est définie par défaut sur _[!UICONTROL Live]_.
* Les exportations de rapports respectent toujours la sélection de la source de données.

Pour sélectionner la source de données [!UICONTROL Order Payment Status] rapport :

1. Sur le _Administration_ barre latérale, accédez à **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Orders]** > **[!UICONTROL View Report]**.
1. Cliquez sur le bouton _[!UICONTROL Data source]_filtre de sélecteur et sélectionnez **[!UICONTROL Live]**ou **[!UICONTROL Sandbox]**.

   Les résultats du rapport se régénèrent en fonction de la source de données sélectionnée.

### Personnalisation de la période des dates de commande

Dans la vue Rapport d’état des paiements de la commande, vous pouvez personnaliser la période des résultats d’état que vous souhaitez afficher en sélectionnant des dates spécifiques. Par défaut, 30 jours de statut de paiement de la commande sont affichés dans la grille.

1. Sur le _Administration_ barre latérale, accédez à **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Orders]_>**[!UICONTROL View Report]**.
1. Cliquez sur le bouton _[!UICONTROL Order dates]_filtre du sélecteur de calendrier.
1. Sélectionnez la période applicable.
1. Affichez les états des paiements de la commande pour les dates spécifiées dans la grille.

### Filtrage des informations sur le rapport

Dans la vue Rapport d’état des paiements des commandes , vous pouvez filtrer les résultats des états que vous souhaitez afficher en sélectionnant des critères de filtrage.

1. Sur le _Administration_ barre latérale, accédez à **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Orders]_>**[!UICONTROL View Report]**.
1. Cliquez sur le bouton **[!UICONTROL Filter]** sélecteur.
1. Activez/désactivez la variable _État de paiement_ pour afficher les résultats des rapports uniquement pour les états de paiement de commande sélectionnés.
1. Pour afficher les résultats d’un rapport sur une période de commande, saisissez une _[!UICONTROL Min Order Amount]_ou _[!UICONTROL Max Order Amount_].
1. Cliquez sur **[!UICONTROL Hide filters]** pour masquer le filtre.

### Afficher et masquer les colonnes

Le rapport État du paiement de la commande affiche toutes les colonnes d’informations disponibles par défaut. Vous pouvez toutefois personnaliser les colonnes affichées dans votre rapport.

1. Sur le _Administration_ barre latérale, accédez à **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Orders]_>**[!UICONTROL View Report]**.
1. Cliquez sur le bouton _Paramètres des colonnes_ icône (![icône des paramètres de colonne](assets/column-settings.png){width="20" zoomable="yes"}).
1. Pour personnaliser les colonnes affichées dans le rapport, cochez ou décochez les colonnes de la liste.

   Le rapport État des paiements de la commande affiche immédiatement les modifications que vous avez apportées au menu Paramètres de colonne . Les préférences de colonne sont enregistrées et restent en vigueur si vous quittez la vue du rapport.

### Affichage des états

La vue du rapport État des paiements de la commande affiche des informations complètes sur l’état des paiements pour chaque commande.

Par défaut, 30 jours de statut de paiement de la commande sont affichés dans la grille.

Faites défiler vers la gauche et la droite pour afficher [informations d’état de paiement de commande](#column-descriptions), y compris la date de commande, la date autorisée, les factures, l’expédition, l’état de paiement, etc.

Le nombre de lignes renvoyé dans une recherche, ou indiqué dans les 30 jours par défaut de l’état du paiement de la commande, s’affiche au-dessus de la grille d’affichage de l’état du paiement de la commande avec le filtre du sélecteur de calendrier des dates de commande .

#### Statut de la paie

La colonne État des paiements indique l’état actuel de tout paiement. A `Capture failed` paiement affiche un état d’alerte rouge et un `Voided` paiement affiche l’état d’alerte grise.

#### Statut du remboursement

La colonne Etat du remboursement indique l&#39;état actuel d&#39;un remboursement. A `Capture failed` paiement affiche un état d’alerte rouge et un `Voided` paiement affiche l’état d’alerte grise.

### Mise à jour des données de rapport

La vue Rapport d’état des paiements de la commande affiche une _[!UICONTROL Last updated]_horodatage indiquant la dernière fois où les informations du rapport ont été mises à jour. Par défaut, les données du rapport d’état des paiements de la commande sont automatiquement actualisées toutes les trois heures.

Vous pouvez également forcer manuellement l’actualisation des données du rapport État des paiements de la commande afin d’afficher les informations de rapport les plus récentes.

1. Sur le _Administration_ barre latérale, accédez à **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Orders]_>**[!UICONTROL View Report]**.
1. Cliquez sur le bouton _Actualiser_ icône (![icône d’actualisation](assets/refresh-button-med.png){width="20" zoomable="yes"}).

   Les données du rapport d’état des paiements de la commande sont actualisées. *[!UICONTROL Update complete]* une confirmation s’affiche et les informations les plus récentes sont présentes dans la grille.

### Afficher les conflits

Vous pouvez afficher tous les litiges relatifs aux commandes de votre boutique et accéder au Centre de résolution PayPal pour agir sur ces litiges, depuis le rapport État des paiements des commandes .

1. Sur le _Administration_ barre latérale, accédez à **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Orders]_>**[!UICONTROL View Report]**.
1. Accédez au **[!UICONTROL Disputes column]**.
1. Affichez tous les conflits pour une commande spécifique, puis reportez-vous à la section [le statut du différend](#order-payment-status-information).
1. Consultez les détails du litige depuis [Centre de résolution PayPal](https://www.paypal.com/us/cshelp/article/what-is-the-resolution-center-help246) en cliquant sur le lien ID du conflit qui commence par _PP-D-_.
1. Prenez les mesures appropriées pour résoudre le conflit, le cas échéant.

   Pour trier les conflits d’ordre par état, cliquez sur le bouton [!UICONTROL Disputes] en-tête de colonne.

### Télécharger les statuts de paiement des commandes

Vous pouvez télécharger un fichier .csv avec tous les états visibles dans la grille Affichage de l’état des paiements des commandes , que vous visualisiez les 30 jours par défaut des états ou une période personnalisée.

1. Sur le _Administration_ barre latérale, accédez à **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Orders]_>**[!UICONTROL View Report]**.
1. Si vous souhaitez afficher les états pour une période autre que les 30 derniers jours, [personnaliser la période de la période de la période pour vos états ;](#customize-dates-timeframe).
1. Cliquez sur le bouton _Télécharger_ (![icône de téléchargement](assets/icon-download.png){width="20" zoomable="yes"}).

Les statuts de paiement de votre commande sont téléchargés au format .csv .

### Descriptions des colonnes

Les rapports d’état des paiements de commande incluent les informations suivantes.

| Colonne | Description |
| ------------ | -------------------- |
| [!UICONTROL Order ID] | ID de commande de commerce<br> <br>Pour afficher les [informations sur la commande](https://docs.magento.com/user-guide/sales/orders.html){target="_blank"}, cliquez sur l’identifiant. |
| [!UICONTROL Order Date] | Date et heure de la commande |
| [!UICONTROL Authorized Date] | Date et heure de l’autorisation de paiement |
| [!UICONTROL Order Status] | Commerce actuel [état de la commande](https://docs.magento.com/user-guide/sales/order-status.html){target="_blank"} |
| [!UICONTROL Invoiced] | État de la facture de la commande —*[!UICONTROL No]*, *[!UICONTROL Partial]*, ou *[!UICONTROL Yes]* |
| [!UICONTROL Shipped] | Etat de livraison de la commande —*[!UICONTROL No]*, *[!UICONTROL Partial]*, ou *[!UICONTROL Yes]* |
| [!UICONTROL Order Amt] | Montant total général de la commande |
| [!UICONTROL Cur] | Type de devise de la commande |
| [!UICONTROL Pay Status] | État de paiement d’une commande spécifique |
| [!UICONTROL Paid Amt] | Montant payé sur une commande |
| [!UICONTROL Cur] | Type de devise du montant payé sur une commande. |
| [!UICONTROL Refund Status] | État d’un remboursement sur une commande (comme des informations provenant de retours, de MA et de notes de crédit)—   *[!UICONTROL Requires refund]*, *[!UICONTROL Refund requested]*, *[!UICONTROL Refunded]*, *[!UICONTROL Refund failed]*, ou *[!UICONTROL Voided]* |
| [!UICONTROL Refund Amount] | Montant total remboursé pour une commande |
| [!UICONTROL Cur] | Type de devise du montant remboursé pour une commande. |
| [!UICONTROL Disputes] | État de tout litige sur une ordonnance (information issue de litiges et de recharges)—*[!UICONTROL Open]*, *[!UICONTROL Waiting for buyer response]*, *[!UICONTROL Waiting for seller response]*, *[!UICONTROL Under review]*, *[!UICONTROL Resolved]*, ou *[!UICONTROL Other]* |
| [!UICONTROL Payment Method] | Mode de paiement utilisé dans la transaction Commerce pour une commande |
| [!UICONTROL Website] | Site web à partir duquel la commande a été passée |
| [!UICONTROL Store] | Magasin à partir duquel la commande a été passée |
| [!UICONTROL Store View] | Vue de magasin à partir de laquelle la commande a été passée |
