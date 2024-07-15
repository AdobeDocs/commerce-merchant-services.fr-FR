---
title: Vérification de la collecte des événements
description: Découvrez comment vérifier que les données comportementales sont envoyées à Adobe Commerce.
exl-id: c8c34db4-9d87-4012-b8f0-e9b1da214305
source-git-commit: d8be88f47f103c5d632540dae743ede398a9b7ad
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---

# Vérification de la collecte des événements

Après avoir [installé et configuré](install-configure.md) le module `magento/product-recommendations`, vous pouvez vérifier que les données comportementales sont envoyées à Adobe Commerce. Vous pouvez utiliser les outils de développement disponibles dans Chrome ou installer l’extension Snowplow Chrome. Si vous avez besoin d’une aide supplémentaire, reportez-vous à la section [Dépannage [!DNL Product Recommendations] module](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/troubleshoot-product-recommendations-module-in-magento-commerce.html) de la base de connaissances d’assistance.

## Vérification à l’aide des outils de développement dans Chrome

Pour vous assurer que le fichier JS du collecteur d’événements se charge sur toutes les pages du site :

1. Dans Chrome, choisissez **Personnaliser et contrôler Google Chrome**, puis sélectionnez **Plus d’outils** > **Outils de développement**.
1. Sélectionnez l’onglet **Network** , puis le type **JS** .
1. Filtre pour `ds.`
1. Rechargez la page.
1. `ds.js` ou `ds.min.js` devrait apparaître dans la colonne **Nom**.

![Collecteur d’événements JS](assets/filter-ds.png)
_Event Collector JS_

Pour vous assurer que les événements se déclenchent sur les pages de votre site (accueil, produit, passage en caisse, etc.) :

1. Veillez à désactiver tous les bloqueurs d’annonces publicitaires de votre navigateur et accepter les cookies du site.
1. Dans Chrome, choisissez **Personnaliser et contrôler Google Chrome** (les trois points verticaux dans le coin supérieur droit du navigateur), puis sélectionnez **Plus d’outils** > **Outils de développement**.
1. Sélectionnez l’onglet **Réseau** et filtrez `tp2`.
1. Rechargez la page.
1. Vous devriez voir les appels sous `tp2` dans la colonne **Nom**.

![Déclenchement d’événements](assets/filter-tp2.png)
_Vérifiez que les événements se déclenchent_

## Vérification à l’aide de l’extension Snowplow Chrome

Installez l’extension [Snowplow Analytics Debugger pour Chrome](https://chrome.google.com/webstore/detail/snowplow-analytics-debugg/jbnlcgeengmijcghameodeaenefieedm). Cette extension affiche les événements collectés et envoyés à Adobe Commerce.

1. Veillez à désactiver tous les bloqueurs d’annonces publicitaires de votre navigateur et accepter les cookies du site.

1. Dans Chrome, choisissez **Personnaliser et contrôler Google Chrome** (les trois points verticaux dans le coin supérieur droit du navigateur), puis sélectionnez **Plus d’outils** > **Outils de développement**.

1. Sélectionnez l’onglet **Débogueur Snowplow Analytics** .

1. Dans la colonne **Event**, sélectionnez **Structured Event**.

1. Faites défiler l’écran vers le bas jusqu’à ce que vous voyiez **Données contextuelles _n_**. Recherchez l’instance storefront dans le **schéma**.

1. Vérifiez que l’ [identifiant de l’espace de données SaaS](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html) est correctement défini.

![Filtre Snowplow](assets/snowplow-filter.png)
_Filtre Snowplow_

>[!NOTE]
>
> Une valeur `Data validity : NOT FOUND` dans le débogueur indique un schéma interne. Le module externe Snowplow Chrome ne peut pas valider les événements avec un schéma interne. Cela n’a aucun impact sur les fonctionnalités réelles.

## Vérification du déclenchement correct des événements

Pour vérifier que les événements utilisés pour les mesures se déclenchent correctement, recherchez les événements `impression-render`, `view` et `rec-click` dans le débogueur Snowplow Analytics. Voir la [liste complète des événements](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/events.html).

>[!NOTE]
>
> Si le [mode de restriction des cookies](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) est activé, Adobe Commerce ne collecte pas de données comportementales tant que l’acheteur n’a pas donné son consentement. Si le mode Restriction des cookies est désactivé, les données comportementales sont collectées par défaut.
