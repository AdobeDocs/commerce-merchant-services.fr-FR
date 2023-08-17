---
title: Vérification de la collecte des événements
description: Découvrez comment vérifier que les données comportementales sont envoyées à Adobe Commerce.
exl-id: c8c34db4-9d87-4012-b8f0-e9b1da214305
source-git-commit: d8be88f47f103c5d632540dae743ede398a9b7ad
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# Vérification de la collecte des événements

Après vous [installation et configuration](install-configure.md) la valeur `magento/product-recommendations` , vous pouvez vérifier que les données comportementales sont envoyées à Adobe Commerce. Vous pouvez utiliser les outils de développement disponibles dans Chrome ou installer l’extension Snowplow Chrome. Si vous avez besoin d’aide supplémentaire, reportez-vous à la section [Résolution des problèmes [!DNL Product Recommendations] module](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/troubleshoot-product-recommendations-module-in-magento-commerce.html) dans la base de connaissances d’assistance.

## Vérification à l’aide des outils de développement dans Chrome

Pour vous assurer que le fichier JS du collecteur d’événements se charge sur toutes les pages du site :

1. Dans Chrome, choisissez **Personnalisation et contrôle de Google Chrome** puis sélectionnez **Autres outils** > **Outils de développement**.
1. Choisissez la **Réseau** puis sélectionnez l’option **JS** type.
1. Filtrer pour `ds.`
1. Rechargez la page.
1. Vous devriez voir `ds.js` ou `ds.min.js` dans le **Nom** colonne .

![JS du collecteur d’événements](assets/filter-ds.png)
_JS du collecteur d’événements_

Pour vous assurer que les événements se déclenchent sur les pages de votre site (accueil, produit, passage en caisse, etc.) :

1. Veillez à désactiver tous les bloqueurs d’annonces publicitaires de votre navigateur et accepter les cookies du site.
1. Dans Chrome, choisissez **Personnalisation et contrôle de Google Chrome** (les trois points verticaux dans le coin supérieur droit du navigateur), puis sélectionnez **Autres outils** > **Outils de développement**.
1. Choisissez la **Réseau** onglet et filtre pour `tp2`.
1. Rechargez la page.
1. Vous devriez voir des appels sous `tp2` dans le **Nom** colonne .

![Déclenchement des événements](assets/filter-tp2.png)
_Vérification du déclenchement des événements_

## Vérification à l’aide de l’extension Chrome Snowplow

Installez le [Extension Snowplow Analytics Debugger pour Chrome](https://chrome.google.com/webstore/detail/snowplow-analytics-debugg/jbnlcgeengmijcghameodeaenefieedm). Cette extension affiche les événements collectés et envoyés à Adobe Commerce.

1. Veillez à désactiver tous les bloqueurs d’annonces publicitaires de votre navigateur et accepter les cookies du site.

1. Dans Chrome, choisissez **Personnalisation et contrôle de Google Chrome** (les trois points verticaux dans le coin supérieur droit du navigateur), puis sélectionnez **Autres outils** > **Outils de développement**.

1. Choisissez la **Débogueur Snowplow Analytics** .

1. Sous , **Événement** colonne, sélectionnez **Événement structuré**.

1. Faites défiler l’écran vers le bas jusqu’à ce que vous voyiez **Données contextuelles _n_**. Recherchez l’instance storefront dans le **Schéma**.

1. Vérifiez que la variable [ID d’espace de données SaaS](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html) est définie correctement.

![Filtre Snowpload](assets/snowplow-filter.png)
_Filtre de transfert de neige_

>[!NOTE]
>
> Une valeur de `Data validity : NOT FOUND` dans le débogueur indique un schéma interne. Le module Chrome Snowplow ne peut pas valider les événements avec un schéma interne. Cela n’a aucun impact sur les fonctionnalités réelles.

## Vérification du déclenchement correct des événements

Pour vérifier que les événements utilisés pour les mesures se déclenchent correctement, recherchez la variable `impression-render`, `view`, et `rec-click` dans le débogueur Snowplow Analytics. Voir [liste complète des événements](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/events.html).

>[!NOTE]
>
> If [Mode de restriction des cookies](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) est activée, Adobe Commerce ne collecte les données comportementales que si l’acheteur a donné son consentement. Si le mode Restriction des cookies est désactivé, les données comportementales sont collectées par défaut.
