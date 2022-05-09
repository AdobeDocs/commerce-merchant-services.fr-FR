---
title: Rapport d’état des paiements de commande
description: Utilisez le rapport État des paiements de la commande pour connaître l’état des paiements de vos commandes et identifier les problèmes potentiels.
role: User
level: Intermediate
exl-id: 192e47b9-d52b-4dcf-a720-38459156fda4
source-git-commit: 9596815e31402f23b399b223f3221074331c1773
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Rapport d’état des paiements de commande

[!DNL Payment Services] pour [!DNL Adobe Commerce] et [!DNL Magento Open Source] vous offre des rapports détaillés afin d’obtenir une vue claire des commandes et des paiements de votre boutique.

![Affichage des rapports financiers](assets/reports-view.png)

Le rapport État des paiements de la commande vous permet de déterminer facilement où se trouve une commande spécifique dans le flux de processus de paiement de la commande. Ce rapport vous permet d’afficher rapidement l’état du paiement de vos commandes et d’identifier les problèmes potentiels.

Vous n’avez pas à ouvrir plusieurs vues pour effectuer manuellement des références croisées entre des commandes et des paiements. [!DNL Payment Services] pour [!DNL Adobe Commerce] et [!DNL Magento Open Source] vous permet d’avoir une vue d’ensemble de vos commandes et paiements, le tout dans le rapport d’état des paiements des commandes .

Consultez les états de paiement, les états facturés et expédiés, les états de remboursement, les états des litiges, etc., dans ce rapport dans l’Administrateur.

Vous pouvez télécharger les transactions d’état des paiements de commande au format .csv pour les utiliser dans les logiciels de gestion des commandes ou de comptabilité existants.

>[!NOTE]
>
>Vous ne pouvez pas afficher les rapports financiers si vous n’avez pas [Mode réel intégré et activé](production.md#enable-live-payments) pour [!DNL Payment Services].

## Données utilisées dans le rapport

Le [!DNL Payment Services] Le module utilise les données de commande et les combine à des données de paiement agrégées provenant d’autres sources (y compris PayPal) afin de fournir des rapports pertinents et très utiles.

Les données de commande sont exportées et conservées dans le service de paiement. Lorsque vous [modifier ou ajouter des statuts de commande ;](https://docs.magento.com/user-guide/sales/order-status-custom.html){target=&quot;_blank&quot;} ou [modification d’une vue de magasin](https://docs.magento.com/user-guide/stores/stores-all-view-edit.html){target=&quot;_blank&quot;}, [store](https://docs.magento.com/user-guide/stores/store-information.html){target=&quot;_blank&quot;}, ou nom du site web, ces données sont combinées avec des données de paiement et le rapport d’état du paiement de la commande est renseigné avec les informations combinées.

Ce processus comprend deux étapes :

1. Les données de l’index sont modifiées : `ON SAVE` (chaque fois que les informations de commande ou de magasin sont modifiées) ou `BY SCHEDULE` (selon un planning cron préconfiguré), selon la manière dont il est configuré dans [Gestion des index](https://docs.magento.com/user-guide/system/index-management.html){target=&quot;_blank&quot;} dans l’administrateur.

   Par défaut, l’indexation des données se produit. `ON SAVE`, ce qui signifie que chaque fois qu’un élément change dans l’ordre, l’état de la commande, l’affichage du magasin, le magasin ou le site web, le processus de réindexation se produit immédiatement.

1. Les données indexées sont envoyées au service de paiement, qui les renseigne ensuite dans le rapport État du paiement de la commande .

Les seules données exportées et regroupées à des fins de création de rapports sont les données utilisées par le rapport d’état des paiements des commandes .

>[!NOTE]
>
>Les données affichées dans ce tableau sont triées par ordre décroissant (`DESC`) par défaut, à l’aide de la fonction `ORDER DATE`. Le `ORDER DATE` est la date et l’heure auxquelles la commande a été créée.

### Configurer l’exportation des données

Même si, par défaut, la réindexation se produit dans `ON SAVE` , il est recommandé d’indexer dans `BY SCHEDULE` mode . Le `BY SCHEDULE` s’exécute selon un planning cron d’une minute. Toute donnée modifiée apparaît dans votre rapport d’état de commande dans les deux minutes suivant tout changement de données. Cette réindexation planifiée vous aide à réduire toute contrainte sur votre boutique, en particulier si vous avez un grand volume de commandes entrantes, car cela se produit sur un planning (et non au moment où chaque commande est passée).

Vous pouvez modifier le mode d’index :`ON SAVE` ou `BY SCHEDULE`—[dans Admin](https://docs.magento.com/user-guide/system/index-management.html#change-the-index-mode){target=&quot;_blank&quot;}.

Pour savoir comment configurer l’exportation des données, voir [Configuration de ligne de commande](configure-cli.md#configure-data-export).

## Disponibilité

Sur le _Administration_ barre latérale, accédez à **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Order payment status]** pour afficher les états de paiement de vos commandes.

![Statuts de paiement des commandes dans l’administrateur](assets/order-payment-status-report.png)

## Sélectionner la source de données

Dans la vue Rapport d’état des paiements de la commande, vous pouvez sélectionner la source de données :_[!UICONTROL Live]_ou_[!UICONTROL Sandbox]_: pour lequel vous souhaitez afficher les résultats du rapport.

![Sélection des sources de données](assets/datasource.png)

If _[!UICONTROL Live]_est la source de données sélectionnée. Vous pouvez afficher les informations de rapport pour vos magasins qui utilisent [!DNL Payment Services] in_[!UICONTROL Live]_ mode . If [!UICONTROL Sandbox]_ correspond à la source de données sélectionnée, vous pouvez afficher les informations de rapport pour votre environnement Sandbox.

Les sélections de sources de données fonctionnent comme suit :

* Si vous ne disposez d’aucun magasin qui utilise [!DNL Payment Services] en mode réel, la sélection de source de données est définie par défaut sur [!UICONTROL Sandbox]_.
* Si des magasins (un ou plusieurs magasins) utilisent [!DNL Payment Services] en mode réel, la sélection de source de données est définie par défaut sur _[!UICONTROL Live]_.
* Les exportations de rapports respectent toujours la sélection de la source de données.

Pour sélectionner la source de données [!UICONTROL Order Payment Status] rapport :

1. Sur le _Administration_ barre latérale, accédez à **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Order payment status]**.
1. Cliquez sur **[!UICONTROL Data source]** et sélectionnez _[!UICONTROL Live]_ou [!UICONTROL Sandbox]_.

   Les résultats du rapport se régénèrent en fonction de la source de données sélectionnée.

## Personnalisation de la période de dates

Dans la vue Rapport d’état des paiements de la commande, vous pouvez personnaliser la période des états que vous souhaitez afficher en sélectionnant des dates spécifiques. Par défaut, les états des paiements de la commande sur 30 jours sont affichés dans la grille.

1. Sur le _Administration_ barre latérale, accédez à **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Order payment status]**.
1. Cliquez sur le bouton **[!UICONTROL Order dates]** filtre du sélecteur de calendrier.
1. Sélectionnez la période applicable.
1. Affichez les états des paiements de la commande pour les dates spécifiées dans la grille.

## Affichage des états

Par défaut, les états des paiements de la commande sur 30 jours sont affichés dans la grille.

Faites défiler l’écran vers la gauche et la droite pour afficher [informations d’état de paiement de commande](#column-descriptions), y compris la date de commande, la date autorisée, les factures, l’expédition, l’état de paiement, etc.

Le nombre de lignes renvoyé dans une recherche, ou indiqué dans les 30 jours par défaut de l’état du paiement de la commande, s’affiche au-dessus de la grille d’affichage de l’état du paiement de la commande avec le filtre du sélecteur de calendrier des dates de commande .

## Mise à jour des données de rapport

La vue Rapport d’état des paiements de la commande affiche une _[!UICONTROL Last updated]_horodatage indiquant la dernière fois où les informations du rapport ont été mises à jour. Par défaut, les données du rapport d’état des paiements de la commande sont automatiquement actualisées toutes les trois heures.

Vous pouvez également forcer manuellement l’actualisation des données du rapport État des paiements de la commande afin d’afficher les informations de rapport les plus récentes.

1. Sur le _Administration_ barre latérale, accédez à **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Order payment status]**.
1. Cliquez sur le bouton _Actualiser_ Icône (![icône d’actualisation](assets/refresh-button-med.png)).

   Les données du rapport d’état des paiements de la commande sont actualisées. *[!UICONTROL Update complete]* une confirmation s’affiche et les informations les plus récentes sont présentes dans la grille.

## Télécharger les statuts de paiement des commandes

Vous pouvez télécharger un fichier .csv avec tous les états visibles dans la grille Affichage de l’état des paiements des commandes , que vous visualisiez les 30 jours par défaut des états ou une période personnalisée.

1. Sur le _Administration_ barre latérale, accédez à **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Order payment status]**.
1. Si vous souhaitez afficher les états pour une période autre que les 30 derniers jours, [personnaliser la période de la période de la période pour vos états ;](#customize-dates-timeframe).
1. Cliquez sur le bouton _Télécharger_ (![icône de téléchargement](assets/icon-download.png)).

Les statuts de paiement de votre commande sont téléchargés au format .csv .

<!-- ## Default order payment status timeframes

These order payment status timeframes are currently available in [!DNL Payment Services].

| Report       | Description          |
| ------------ | -------------------- |
| Yesterday | Available from the Order payment status dates selector, this shows information for the prior date. |
| | Today | Available from the Order payment status dates selector, this shows information for the current day. |
| Last 7 days | Available from the Order payment status dates selector, this shows information for the last seven days. |
| Last 30 days | Available from the Order payment status dates selector and by default in the Order payment statuses view, this shows information for the last 30 days. |
| Last 90 days | Available from the Order payment status dates selector, this shows information for the last 90 days. |
| Year to date | Available from the Order payment status dates selector, this shows information for the the entire year to date. |
| Custom range | Available from the Order payment status dates selector, this can be filtered to show a custom date range. |
-->

## Informations sur l’état du paiement de la commande

La vue État des paiements de la commande affiche des informations détaillées sur chaque état affiché dans la grille.

### Descriptions des colonnes

Les rapports d’état des paiements de commande incluent les informations suivantes.

| Colonne | Description |
| ------------ | -------------------- |
| [!UICONTROL Order ID] | ID de commande de commerce<br> <br>Pour afficher les [informations sur la commande](https://docs.magento.com/user-guide/sales/orders.html){target=&quot;_blank&quot;}, cliquez sur l’ID. |
| [!UICONTROL Order Date] | Date et heure de la commande |
| [!UICONTROL Authorized Date] | Date et heure de l’autorisation de paiement |
| [!UICONTROL Order Status] | Commerce actuel [état de commande](https://docs.magento.com/user-guide/sales/order-status.html){target=&quot;_blank&quot;} |
| [!UICONTROL Invoiced] | Statut de la facture —*[!UICONTROL No]*, *[!UICONTROL Partial]* ou *[!UICONTROL Yes]* |
| [!UICONTROL Shipped] | Etat de livraison de la commande —*[!UICONTROL No]*, *[!UICONTROL Partial]* ou *[!UICONTROL Yes]* |
| [!UICONTROL Order Amt] | Montant total général de la commande |
| [!UICONTROL Cur] | Type de devise de la commande |
| [!UICONTROL Pay Status] | État de paiement d’une commande spécifique |
| [!UICONTROL Paid Amt] | Montant payé sur une commande |
| [!UICONTROL Cur] | Type de devise du montant payé sur une commande. |
| [!UICONTROL Refund Status] | État d’un remboursement sur une commande (comme des informations provenant de retours, de MA et de notes de crédit)—   *[!UICONTROL Requires refund]*, *[!UICONTROL Refund requested]*, *[!UICONTROL Refunded]*, *[!UICONTROL Refund failed]* ou *[!UICONTROL Voided]* |
| [!UICONTROL Refund Amount] | Montant total remboursé pour une commande |
| [!UICONTROL Cur] | Type de devise du montant remboursé pour une commande. |
| [!UICONTROL Dispute Status] | État de tout litige sur une ordonnance (information issue de litiges et de recharges)—*[!UICONTROL New]*, *[!UICONTROL Representment]*, *[!UICONTROL Accepted]*, *[!UICONTROL Pre-arbitration received]*, *[!UICONTROL Arbitration]* ou *[!UICONTROL Arbitration received]* |
| [!UICONTROL Payment Method] | Mode de paiement utilisé dans la transaction Commerce pour une commande |
| [!UICONTROL Website] | Site web à partir duquel la commande a été passée |
| [!UICONTROL Store] | Magasin à partir duquel la commande a été passée |
| [!UICONTROL Store View] | Vue de magasin à partir de laquelle la commande a été passée |
