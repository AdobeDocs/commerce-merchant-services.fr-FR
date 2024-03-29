---
title: '[!DNL Quick Checkout] rapport'
description: '''[!DNL Quick Checkout] offre des informations de création de rapports complètes."'
exl-id: 91c687f4-9953-4c2f-b240-73430603e6a1
feature: Checkout, Services
source-git-commit: 6ba5a283d9138b4c1be11b80486826304c63247f
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 1%

---

# Rapports

[!DNL Quick Checkout] pour Adobe Commerce et Magento Open Source, vous pouvez créer des rapports détaillés afin d’obtenir des informations détaillées sur les statistiques d’expérience de passage en caisse de votre boutique.

![Vue Rapports](assets/reports-view-big-checkout.png){width="600" zoomable="yes"}

>[!WARNING]
>
> Pour permettre à Adobe Commerce de partager les informations de passage en caisse avec Bolt, la variable [**Tracking de passage en caisse**](../quick-checkout/settings-quick-checkout.md)  doit être activé dans Admin. Par défaut, cette option de configuration est définie sur **Oui**. Si cette option est définie sur **Non**, la création de rapports sera affectée. Bolt actualise les informations de rapport une fois par jour à 03h00, heure normale de l’Est (HNE).

## Rapports de présentation

Les graphiques de la section Aperçu contiennent des informations détaillées sur les performances de passage en caisse de votre magasin, notamment le temps moyen de passage en caisse, les nouveaux comptes créés lors du passage en caisse ou de l’abandon du passage en caisse.

![Présentation des rapports](assets/overview-report-checkout.png){width="600" zoomable="yes"}

| Graphique | Description |
|---|---|
| [!UICONTROL Checkout abandonment] | Pourcentage de visiteurs qui quittent le processus de passage en caisse sans effectuer d’achat. |
| [!UICONTROL Checkout abandonment breakdown] | Abandon de passage en caisse divisé par type de visiteur. L’info-bulle affiche une différence en pourcentage entre Bolt et Guest. Options : [!UICONTROL Bolt] / [!UICONTROL Merchant] / [!UICONTROL Guest] |
| [!UICONTROL Average checkout time] | La durée moyenne de passage en caisse d’un visiteur. |
| [!UICONTROL Average checkout time breakdown] | Durée moyenne de passage en caisse divisée par type de visiteur. L’info-bulle affiche une différence en pourcentage entre Bolt et Guest. Options : [!UICONTROL Bolt] / [!UICONTROL Merchant] / [!UICONTROL Guest] |
| [!UICONTROL Orders by account type] | Commandes passées divisées par type de visiteur. Options : [!UICONTROL Bolt] / [!UICONTROL Merchant] / [!UICONTROL Guest] |

## Rapports sur les tendances

Les graphiques de la section Tendances affichent les tendances de votre expérience de passage en caisse filtrées par type de compte ou les nouveaux comptes créés pendant le passage en caisse.

![Tendances des rapports](assets/trends-report-checkout.png){width="600" zoomable="yes"}

| Graphique | Description |
|---|---|
| [!UICONTROL Checkout abandonment by account type] | La tendance d’abandon des passages en caisse divisée par type de visiteur. Options : [!UICONTROL Bolt] / [!UICONTROL Merchant] / [!UICONTROL Guest] |
| [!UICONTROL Orders by account type] | La tendance des commandes passées est divisée par type de visiteur. Options : [!UICONTROL Bolt] / [!UICONTROL Merchant] / [!UICONTROL Guest] |
| [!UICONTROL New accounts on your store] | Nouveaux comptes sur la tendance de votre boutique. |

## Filtrage des données

Vous pouvez filtrer les résultats affichés par date ou les paramètres prédéfinis existants, comme **30 derniers jours**.

![Affichage des filtres](assets/filter-view.png){width="300" zoomable="yes"}

| Champ | Description |
|---|---|
| [!UICONTROL Preset] | Liste déroulante qui affiche des paramètres prédéfinis par défaut pouvant être utilisés pour afficher des plages de données spécifiques. Par défaut : 30 derniers jours |
| [!UICONTROL Date range] | Une liste déroulante qui vous permet de sélectionner une plage de données spécifique en fonction des dates sélectionnées. |
