---
title: Rapport de paiements
description: Pour effectuer une réconciliation financière, utilisez le rapport Remboursements afin d'obtenir une transparence complète du montant des paiements, du volume traité et des rapports détaillés sur le niveau des transactions.
role: User
level: Intermediate
exl-id: f3f99474-cd28-4c8f-b0ea-dca8e014b108
feature: Payments, Checkout
source-git-commit: 90bfa7099924feb308397960cff76bdf177bbe49
workflow-type: tm+mt
source-wordcount: '1326'
ht-degree: 0%

---

# Rapport de paiements

[!DNL Payment Services] pour [!DNL Adobe Commerce] et [!DNL Magento Open Source] vous offre des rapports détaillés afin d’obtenir une vue claire des commandes et des paiements de votre boutique.

Il existe deux vues de rapport sur les versements disponibles pour vous permettre d’afficher des informations détaillées sur tous vos versements :

* **[Vue de visualisation des données de paiement](#payouts-data-visualization-view)**—Graphique disponible sur la page d’accueil des services de paiement qui est une représentation visuelle des montants agrégés par jour de la vue du rapport sur les paiements
* **[Vue du rapport Payements](#payouts-report-view)**: rapport disponible dans les paiements qui affiche des informations détaillées sur les paiements pour toutes les transactions.

Les vues Payouts affichent des informations complètes en un coup d’oeil, ce qui vous permet d’obtenir une transparence complète du montant du paiement, du volume traité et des rapports détaillés au niveau de la transaction pour la réconciliation financière.

>[!NOTE]
>
>Les rapports sur les paiements affichent uniquement les commandes capturées (l’action de paiement est définie sur [`Authorize and Capture`](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/production.html#set-payment-services-as-payment-method))—ou [Marqué comme `Invoiced`](https://docs.magento.com/user-guide/sales/invoice-create.html).

## Vue de visualisation des données de paiement

La vue de visualisation des données de paiement est disponible dans la page d’accueil des services de paiement. Il s’agit d’une représentation visuelle des montants agrégés par jour du tableau détaillé [Vue du rapport Payements](#payouts-report-view).

Sur le _Administration_ barre latérale, accédez à **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** pour afficher le graphique de visualisation des données des crédits par rapport aux débits et les moyennes mobiles au fil du temps.

![Visualisation des données de paiement dans l’Admin](assets/payouts-report.png){zoomable=yes}

Cliquez sur **[!UICONTROL View Report]** pour accéder au tableau détaillé [Vue du rapport Payements](#payouts-report-view).

### Personnalisation de la période des transactions

Par défaut, 30 jours de transactions sont affichés.

Dans la vue Visualisation des données de paiement , vous pouvez personnaliser la période des transactions de paiement que vous souhaitez afficher en sélectionnant une plage de dates :

1. Sur le _Administration_ barre latérale, accédez à **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**. La vue de visualisation des données de paiement est visible dans la section Paiements .
1. Cliquez sur le bouton **[!UICONTROL Range]** filtre de sélecteur.
1. Sélectionnez la période applicable : 30 jours, 15 jours ou 7 jours.
1. Affichez les informations sur les transactions pour les dates spécifiées.

### Informations sur les transactions

Les montants des transactions pour une période sélectionnée sont affichés à gauche de la vue de visualisation des données de paiement. Les dates de la période sélectionnée s’affichent au bas de la vue. En l’absence de paiement à une date spécifique, cette date n’apparaîtra pas.

La vue de visualisation des données de paiement comprend les informations suivantes.

| Données | Description |
| ------------ | -------------------- |
| [!UICONTROL Transaction amount] | Période pour les transactions sur une période spécifiée ; données sur l’axe Y (gauche) |
| Période | Période pour la période spécifiée ; données sur l’axe X (bas) |
| Crédit | Paiements pour la période spécifiée |
| Débit | Débits (remboursements) pour la période spécifiée |
| Moyenne glissante | Représentation du paiement moyen pour chaque date de la période spécifiée |
| Net pour la plage | Montant net des paiements pour la période (période) spécifiée |

## Vue du rapport Payements

La vue Rapport de paiements est disponible dans la vue Versements des Services de paiement. Elle contient toutes les informations disponibles sur les paiements pour vos magasins. La variable [Vue de visualisation des données de paiement](#payouts-data-visualization-view) dans la page d’accueil des services de paiement est une représentation visuelle des montants agrégés par jour dans cette vue de rapport plus détaillée.

Sur le _Administration_ barre latérale, accédez à **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Payouts]** pour afficher le tableau détaillé de la vue Rapport de versements .

![Transactions de paiement dans l&#39;administrateur](assets/payouts-report-new.png){zoomable=yes}

Vous pouvez configurer cette vue, selon les sections de cette rubrique, pour présenter au mieux les données que vous souhaitez afficher.

Voir les ID de commande et de transaction Commerce liés, le montant des transactions, le mode de paiement par transaction, etc., dans le rapport Paiements de l’administrateur.

Vous pouvez [téléchargement des transactions de paiement](#download-transactions) dans un format de fichier .csv à utiliser dans les logiciels de gestion des commandes ou de comptabilité existants.

>[!NOTE]
>
>Les données affichées dans ce tableau sont triées par ordre décroissant (`DESC`) par défaut, à l’aide de la fonction `TRANS DATE`. La variable `TRANS DATE` est la date et l’heure auxquelles la transaction a été lancée.

### Sélectionner la source de données

Dans la vue Rapport de versements, vous pouvez sélectionner la source de données..._[!UICONTROL Live]_ou_[!UICONTROL Sandbox]_: pour lequel vous souhaitez afficher les résultats du rapport.

![Sélection des sources de données](assets/datasource.png){width=400px}

If _[!UICONTROL Live]_est la source de données sélectionnée. vous pouvez afficher les informations du rapport pour les magasins en mode de production. If_[!UICONTROL Sandbox]_ est la source de données sélectionnée. vous pouvez afficher les magasins d’informations de rapport en mode sandbox.

Les sélections de sources de données fonctionnent comme suit :

* Si aucun magasin n’est en mode réel, la sélection de source de données est définie par défaut sur _[!UICONTROL Sandbox]_.
* Si vous disposez de magasins (un ou plusieurs) en mode réel, la sélection de source de données est définie par défaut sur _[!UICONTROL Live]_.
* Les exportations de rapports respectent toujours la sélection de la source de données.

Pour sélectionner la source de données de votre rapport État du paiement de la commande :

1. Sur le _Administration_ barre latérale, accédez à **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Payouts]**.
1. Cliquez sur **[!UICONTROL Data source]** et sélectionnez _[!UICONTROL Live]_ou_[!UICONTROL Sandbox]_.

   Les résultats du rapport se régénèrent en fonction de la source de données sélectionnée.

### Afficher les transactions

Par défaut, 30 jours de transactions sont affichés.

Le nombre de lignes renvoyé dans une recherche, ou indiqué dans les 30 jours par défaut des transactions, s’affiche au-dessus de la grille Vue des paiements avec le filtre du sélecteur de dates de transaction .

Faites défiler vers la gauche et la droite pour afficher [informations pour chaque transaction de paiement](#column-descriptions) dans le rapport quotidien, notamment la date de transaction, l’ID de référence, le numéro de facture et les détails du mode de paiement.

#### Personnalisation de la période des transactions

Dans la vue Rapport de versements, vous pouvez personnaliser la période des transactions de paiement que vous souhaitez afficher en saisissant des dates spécifiques ou en sélectionnant une plage de dates dans le sélecteur de date :

1. Sur le _Administration_ barre latérale, accédez à **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Payouts]**.
1. Cliquez sur le filtre du sélecteur de calendrier des dates de transaction .
1. Sélectionnez la période applicable.
1. Affichez les états des paiements dans la grille pour les dates spécifiées.

### Afficher et masquer les colonnes

La vue Rapport de paiements affiche la plupart des colonnes d’informations disponibles par défaut. Vous pouvez toutefois personnaliser les colonnes affichées dans le rapport.

1. Sur le _Administration_ barre latérale, accédez à **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Payouts]**.
1. Cliquez sur le bouton _Paramètres des colonnes_ icône (![icône des paramètres de colonne](assets/column-settings.png)).
1. Pour personnaliser les colonnes affichées dans le rapport, cochez ou décochez les colonnes de la liste.

   La vue du rapport Versions affiche immédiatement les modifications que vous avez apportées au menu Paramètres de colonne. Les préférences de colonne seront enregistrées et resteront en vigueur si vous quittez la vue du rapport.

### Téléchargement de transactions

Vous pouvez télécharger un fichier .csv contenant toutes les transactions visibles dans la grille Affichage des paiements .

1. Sur le _Administration_ barre latérale, accédez à **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Payouts]**.
1. [Personnalisation de la période de la période de la période pour vos transactions](#customize-transactions-timeframe).
1. Cliquez sur le bouton _Télécharger_ (![](assets/icon-download.png)).

Vos transactions de paiement sont téléchargées au format .csv.

### Descriptions des colonnes

Les rapports de paiement comprennent les informations suivantes.

| Colonne | Description |
| ------------ | -------------------- |
| [!UICONTROL Provider] | Prestataire de paiement |
| [!UICONTROL Provider trans] | ID de transaction |
| [!UICONTROL Trans date] | Date et heure du lancement de la transaction |
| [!UICONTROL Type] | Type de transaction —*[!UICONTROL PAYMENT]*, *[!UICONTROL BONUS]*, *[!UICONTROL CHARGEBACK]*, *[!UICONTROL CORRECTION]*, *[!UICONTROL CURRENCY_CONVERSATION]*, *[!UICONTROL DEPOSIT]*, *[!UICONTROL DISBURSEMENT]*, *[!UICONTROL DISPUTE]*, *[!UICONTROL FEES]*, *[!UICONTROL HOLD]*, *[!UICONTROL HOLD_RELEASE]*, *[!UICONTROL INCENTIVES]*, *[!UICONTROL OTHERS]*, *[!UICONTROL RECOUP]*, *[!UICONTROL REFUND]*, *[!UICONTROL REVERSAL]*, *[!UICONTROL WITHDRAWAL]* <br> <br>Voir [Types de transaction](#transaction-types) pour plus d’informations. |
| [!UICONTROL Status] | Etat actuel de la transaction —*[!UICONTROL SUCCESS]*, *[!UICONTROL DENIED]*, *[!UICONTROL PENDING]* |
| [!UICONTROL Code] | Code de transaction qui indique soit Crédit (*CR*) ou Débit (*DR*) |
| [!UICONTROL Reference ID] | Identifiant de transaction d’origine pour lequel cet événement est lié |
| [!UICONTROL Invoice] | Identifiant de facture (une par commande) de la transaction |
| [!UICONTROL Commerce order] | ID de commande de commerce <br> <br>Pour afficher les [informations sur la commande](https://docs.magento.com/user-guide/sales/orders.html), cliquez sur l’identifiant. |
| [!UICONTROL Commerce trans] | Commerce transaction ID |
| [!UICONTROL Pay method] | Type de carte de crédit —*[!UICONTROL BANK]*, *[!UICONTROL PAYPAL]*, *[!UICONTROL CREDIT_CARD]*: et le fournisseur de carte associé (par exemple, *Visa* ou *MasterCard*) |
| [!UICONTROL TRANS AMT] | Montant de la transaction |
| [!UICONTROL CUR] | Unité de devise pour le montant des transactions |
| [!UICONTROL PENDING] | Montant à débourser |
| [!UICONTROL CUR] | Unité de devise pour le montant en attente |
| [!UICONTROL SELLER AMT] | Montant des fonds transférés à ou à un client <br> <br>Les fonds sortants du compte du vendeur affichent un préfixe tiret (-). |
| [!UICONTROL CUR] | Unité de devise pour le montant du vendeur |
| [!UICONTROL PARTNER FEE] | Frais de partenaire associés à la transaction <br> <br>Les fonds qui sortent du compte de frais du partenaire affichent un préfixe tiret (-). |
| [!UICONTROL CUR] | Unité de devise pour les frais de partenaire |
| [!UICONTROL PROV FEES] | Frais associés à la transaction <br> <br>Les fonds qui sortent du compte de frais du fournisseur affichent un préfixe tiret (-). |
| [!UICONTROL CUR] | Unité de devise pour les frais du fournisseur |
| [!UICONTROL FEE %] | Pourcentage du montant de la transaction imputé en frais |
| [!UICONTROL FIXED FEE] | Montant fixe des frais du fournisseur |
| [!UICONTROL CHBK FEE] | Redevance associée à la transaction <br> <br>Un préfixe tiret (-) indique que les frais de recharge ont été annulés. |
| [!UICONTROL CUR] | Unité de devise pour les frais de reliquat |
| [!UICONTROL HOLD AMT] | Montant mis en attente ou libéré du blocage <br> <br>Un préfixe tiret (-) indique que les fonds en attente sont débloqués. |
| [!UICONTROL CUR] | Unité de devise pour le montant de la retenue |
| [!UICONTROL RECOUP AMT] | Montant récupéré du compte de retour <br> <br>Les fonds sortants du compte de récupération affichent un préfixe de tiret (-). |
| [!UICONTROL CUR] | Unité de devise pour le montant de retour |

### Types de transaction

Ces types de transaction peuvent être indiqués dans les transactions de paiement.

| Rapport | Description |
| ------------ | -------------------- |
| [!UICONTROL PAYMENT] | Argent passé entre un acheteur et un vendeur pour une commande |
| [!UICONTROL AUTH] | Transactions d’autorisation et d’autorisation nulle |
| [!UICONTROL BONUS] | — |
| [!UICONTROL CHARGEBACK] | Transactions d’annulation et d’annulation de frais |
| [!UICONTROL CORRECTION] | -- |
| [!UICONTROL CURRENCY_CONVERSION] | -- |
| [!UICONTROL DEPOSIT] | -- |
| [!UICONTROL DISBURSEMENT] | -- |
| [!UICONTROL DISPUTE] | -- |
| [!UICONTROL FEES] | Frais de partenaire, frais de paiement et opérations d’annulation de frais |
| [!UICONTROL HOLD] | -- |
| [!UICONTROL HOLD_RELEASE] | -- |
| [!UICONTROL INCENTIVES] | -- |
| [!UICONTROL OTHERS] | -- |
| [!UICONTROL RECOUP] | Récupérations à partir de comptes bancaires ou de pertes |
| [!UICONTROL REFUND] | -- |
| [!UICONTROL REVERSAL] | -- |
| [!UICONTROL WITHDRAWAL] | -- |
