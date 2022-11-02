---
title: "Configurez la variable [!DNL Quick Checkout] pour l’extension Adobe Commerce"
description: "Découvrez les options de configuration pour la [!DNL Quick Checkout] et comment embarquer et configurer l’extension."
source-git-commit: bd02a8083d3f4c9cb0422b27d61bd5462187ffc3
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# [!DNL Quick Checkout] paramètres

[!DNL Quick Checkout] pour Adobe Commerce et Magento Open Source, fournit une vue de configuration avec toutes les informations nécessaires pour configurer l’extension.

Pour accéder à ces paramètres de configuration :

1. Sur le _Administration_ barre latérale, accédez à **Magasins** > _Paramètres_ > **Configuration**.
1. Dans le panneau de gauche, développez **Ventes** et sélectionnez **Passage en caisse**.

   ![Passage en caisse rapide](assets/quick-checkout-main-view-react.png)

Reportez-vous à la section [Intégration](../quick-checkout/onboarding.md) rubrique pour plus d’informations sur la configuration de la variable [!DNL Quick Checkout] pour Adobe Commerce.

## Activer l’extension

| Champ | Portée | Description |
|---|---|---|
| [!UICONTROL Enable] | site web | Activer ou désactiver [!DNL Quick Checkout] pour votre site web. Options : [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Method] | site web | Définissez la méthode ou l’environnement correspondant à votre [!DNL Quick Checkout]. Options : [!UICONTROL Sandbox] / [!UICONTROL Production] |

## Identifiants de compte

| Champ | Portée | Description |
|---|---|---|
| [!UICONTROL API key] | site web | Clé privée utilisée par votre serveur principal pour interagir avec [!DNL Bolt] API. |
| [!UICONTROL Publishable key] | site web | Clé utilisée par votre front-end pour interagir avec [!DNL Bolt] API. |
| [!UICONTROL Signing secret] | site web | Utilisé pour la vérification des signatures sur les demandes reçues d’ [!DNL Bolt]. |

## Paramètres du service

| Champ | Portée | Description |
|---|---|---|
| [!UICONTROL Title] | vue de magasin | Ajoutez le texte à afficher comme titre de cette option de paiement dans la vue Mode de paiement lors de l’extraction. Options : [!UICONTROL text field] |
| [!UICONTROL Payment Action] | site web | Le [action de paiement](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target=&quot;_blank&quot;} pour le mode de paiement spécifié. Options : [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Debug Mode] | site web | Activez ou désactivez le mode de débogage. Options : [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Enable checkout tracking] | site web | Définissez si Adobe Commerce permet le partage des informations de suivi de passage en caisse avec Bolt. Activé par défaut. Si cette option est désactivée, la création de rapports est affectée. Options : [!UICONTROL Yes] / [!UICONTROL No] |
