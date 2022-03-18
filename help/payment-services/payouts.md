---
title: Rapport de paiements
description: Pour effectuer une réconciliation financière, utilisez le rapport Remboursements afin d'obtenir une transparence complète du montant des paiements, du volume traité et des rapports détaillés sur le niveau des transactions.
role: User
level: Intermediate
exl-id: f3f99474-cd28-4c8f-b0ea-dca8e014b108
source-git-commit: aff1a43fedab473b84d02068a7d3fbd33b4fe093
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Rapport de paiements

[!DNL Payment Services] pour Adobe Commerce et Magento Open Source, vous pouvez créer des rapports détaillés afin d’obtenir une vue claire des commandes et des paiements de votre boutique.

![Affichage des rapports financiers](assets/reports-view.png)

Le rapport sur les paiements affiche des informations complètes sur les paiements en un coup d’oeil, ce qui vous permet d’obtenir une transparence complète du montant des paiements, du volume traité et des rapports détaillés sur le niveau des transactions pour la réconciliation financière.

Il n’est pas nécessaire d’ouvrir plusieurs tableaux de bord ou vues pour effectuer des références croisées sur des commandes et des paiements ou réconcilier des comptes. [!DNL Payment Services] pour Adobe Commerce et Magento Open Source, vous pouvez effectuer toutes ces actions à partir d’un seul emplacement (rapport sur les versements) afin de pouvoir visualiser et gérer vos versements efficacement.

Voir les ID de commande et de transaction Commerce liés, le montant des transactions, le mode de paiement par transaction, etc., dans le rapport Paiements de l’administrateur.

Vous pouvez télécharger les transactions de paiement au format .csv pour les utiliser dans les logiciels de gestion des commandes ou de comptabilité existants.

>[!NOTE]
>
>Les données affichées dans ce tableau sont triées par ordre décroissant (`DESC`) par défaut, à l’aide de la fonction `TRANS DATE`. Le `TRANS DATE` est la date et l’heure auxquelles la transaction a été lancée.

## Disponibilité

Sur le _Administration_ barre latérale, accédez à **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Payouts]**.

![Transactions de paiement dans l&#39;administrateur](assets/payouts-report.png)

## Sélectionner la source de données

Dans la vue Rapport de versements, vous pouvez sélectionner la source de données..._[!UICONTROL Live]_ou [!UICONTROL Sandbox]_ : pour lequel vous souhaitez afficher les résultats du rapport.

![Sélection des sources de données](assets/datasource.png)

If _[!UICONTROL Live]_est la source de données sélectionnée. vous pouvez afficher les informations de rapport pour vos boutiques en direct. If [!UICONTROL Sandbox]_ correspond à la source de données sélectionnée, vous pouvez afficher les informations de rapport pour votre environnement Sandbox.

Les sélections de sources de données fonctionnent comme suit :

* Si aucun magasin n’est en mode réel, la sélection de source de données est définie par défaut sur [!UICONTROL Sandbox]_.
* Si vous disposez de magasins (un ou plusieurs) en mode réel, la sélection de source de données est définie par défaut sur _[!UICONTROL Live]_.
* Les exportations de rapports respectent toujours la sélection de la source de données.

Pour sélectionner la source de données de votre rapport État du paiement de la commande :

1. Sur le _Administration_ barre latérale, accédez à **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Payouts]**.
1. Cliquez sur **[!UICONTROL Data source]** et sélectionnez _[!UICONTROL Live]_ou [!UICONTROL Sandbox]_.

   Les résultats du rapport se régénèrent en fonction de la source de données sélectionnée.

## Afficher les transactions

Par défaut, 30 jours de transactions sont affichés dans la grille.

Le nombre de lignes renvoyé dans une recherche, ou indiqué dans les 30 jours par défaut des transactions, s’affiche au-dessus de la grille Vue des paiements avec le filtre du sélecteur de dates de transaction .

Faites défiler l’écran vers la gauche et la droite pour afficher [informations pour chaque transaction de paiement](#column-descriptions) dans le rapport quotidien, notamment la date de transaction, l’ID de référence, le numéro de facture et les détails du mode de paiement.

### Personnalisation de la période des transactions

Dans la vue Versements, vous pouvez personnaliser la période des transactions de paiement que vous souhaitez afficher en saisissant des dates spécifiques ou en sélectionnant une période dans le sélecteur de date :

1. Sur le _Administration_ barre latérale, accédez à **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Payouts]**.
1. Cliquez sur le filtre du sélecteur de calendrier des dates de transaction .
1. Sélectionnez la période applicable.
1. Affichez les états des paiements dans la grille pour les dates spécifiées.

## Téléchargement de transactions

Vous pouvez télécharger un fichier .csv contenant toutes les transactions visibles dans la grille Affichage des paiements .

1. Sur le _Administration_ barre latérale, accédez à **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Payouts]**.
1. [Personnalisation de la période de la période de la période pour vos transactions](#customize-transactions-timeframe).
1. Cliquez sur le bouton _Télécharger_ (![](assets/icon-download.png)).

Vos transactions de paiement sont téléchargées au format .csv.

## Informations sur les transactions

La vue Payements affiche des informations détaillées sur chaque transaction affichée dans la grille.

### Descriptions des colonnes

Les rapports de paiement comprennent les informations suivantes.

| Colonne | Description |
| ------------ | -------------------- |
| [!UICONTROL Provider] | Prestataire de paiement |
| [!UICONTROL Provider trans] | ID de transaction |
| [!UICONTROL Trans date] | Date et heure du lancement de la transaction |
| [!UICONTROL Type] | Type de transaction —*[!UICONTROL PAYMENT]*, *[!UICONTROL AUTH]*, *[!UICONTROL BONUS]*, *[!UICONTROL CHARGEBACK]*, *[!UICONTROL CORRECTION]*, *[!UICONTROL CURRENCY_CONVERSATION]*, *[!UICONTROL DEPOSIT]*, *[!UICONTROL DISBURSEMENT]*, *[!UICONTROL DISPUTE]*, *[!UICONTROL FEES]*, *[!UICONTROL HOLD]*, *[!UICONTROL HOLD_RELEASE]*, *[!UICONTROL INCENTIVES]*, *[!UICONTROL OTHERS]*, *[!UICONTROL RECOUP]*, *[!UICONTROL REFUND]*, *[!UICONTROL REVERSAL]*, *[!UICONTROL WITHDRAWAL]* <br> <br>Voir [Types de transaction](#transaction-types) pour plus d’informations. |
| [!UICONTROL Status] | Etat actuel de la transaction —*[!UICONTROL SUCCESS]*, *[!UICONTROL DENIED]*, *[!UICONTROL PENDING]* |
| [!UICONTROL Code] | Code de transaction qui indique soit Crédit (*CR*) ou Débit (*DR*) |
| [!UICONTROL Reference ID] | Identifiant de transaction d’origine pour lequel cet événement est lié |
| [!UICONTROL Invoice] | Identifiant de facture (une par commande) de la transaction |
| [!UICONTROL Commerce order] | ID de commande de commerce <br> <br>Pour afficher les [informations sur la commande](https://docs.magento.com/user-guide/sales/orders.html){target=&quot;_blank&quot;}, cliquez sur l’ID. |
| [!UICONTROL Commerce trans] | Commerce transaction ID <br> <br>Pour afficher les [informations sur les transactions](https://docs.magento.com/user-guide/sales/transactions.html){target=&quot;_blank&quot;}, cliquez sur l’ID. |
| [!UICONTROL Pay method] | Type de carte de crédit —*[!UICONTROL BANK]*, *[!UICONTROL PAYPAL]*, *[!UICONTROL CREDIT_CARD]*: et fournisseur de carte associé (par exemple, *Visa* ou *MasterCard*) |
| [!UICONTROL Trans amt] | Montant de la transaction |
| [!UICONTROL Cur] | Unité de devise pour le montant des transactions |
| [!UICONTROL Pending] | Montant à débourser |
| [!UICONTROL Cur] | Unité de devise pour le montant en attente |
| [!UICONTROL Seller amt] | Montant des fonds transférés à ou à un client <br> <br>Les fonds sortants du compte du vendeur affichent un préfixe tiret (-). |
| [!UICONTROL Cur] | Unité de devise du montant du vendeur |
| [!UICONTROL Partner fee] | Frais de partenaire associés à la transaction <br> <br>Les fonds qui sortent du compte de frais du partenaire affichent un préfixe tiret (-). |
| [!UICONTROL Cur] | Unité de devise pour les frais de partenaire |
| [!UICONTROL Prov fees] | Frais associés à la transaction <br> <br>Les fonds qui sortent du compte de frais du fournisseur affichent un préfixe tiret (-). |
| [!UICONTROL Cur] | Unité de devise pour les frais du fournisseur |
| [!UICONTROL Fee %] | Pourcentage du montant de la transaction imputé en frais |
| [!UICONTROL Fixed fee] | Montant fixe des frais du fournisseur |
| [!UICONTROL Chbk fee] | Redevance associée à la transaction <br> <br>Un préfixe tiret (-) indique que les frais de recharge ont été annulés. |
| [!UICONTROL Cur] | Unité de devise pour les frais de reliquat |
| [!UICONTROL Hold amt] | Montant mis en attente ou libéré du blocage <br> <br>Un préfixe tiret (-) indique que les fonds en attente sont débloqués. |
| [!UICONTROL Cur] | Unité de devise pour le montant de la retenue |
| [!UICONTROL Recoup amt] | Montant récupéré du compte de retour <br> <br>Les fonds sortants du compte de récupération affichent un préfixe de tiret (-). |
| [!UICONTROL Cur] | Unité de devise pour le montant de retour |

### Types de transaction

Ces types de transaction peuvent être indiqués dans les transactions de paiement.

| Rapport | Description |
| ------------ | -------------------- |
| [!UICONTROL PAYMENT] | Argent passé entre un acheteur et un vendeur pour une commande |
| [!UICONTROL AUTH] | Transactions d’autorisation et d’autorisation nulle |
| [!UICONTROL BONUS] | — |
| [!UICONTROL CHARGEBACK] | Transactions d’annulation et d’annulation de frais |
| [!UICONTROL CORRECTION] | — |
| [!UICONTROL CURRENCY_CONVERSION] | — |
| [!UICONTROL DEPOSIT] | — |
| [!UICONTROL DISBURSEMENT] | — |
| [!UICONTROL DISPUTE] | — |
| [!UICONTROL FEES] | Frais de partenaire, frais de paiement et opérations d’annulation de frais |
| [!UICONTROL HOLD] | — |
| [!UICONTROL HOLD_RELEASE] | — |
| [!UICONTROL INCENTIVES] | — |
| [!UICONTROL OTHERS] | — |
| [!UICONTROL RECOUP] | Récupérations à partir de comptes bancaires ou de pertes |
| [!UICONTROL REFUND] | — |
| [!UICONTROL REVERSAL] | — |
| [!UICONTROL WITHDRAWAL] | — |
