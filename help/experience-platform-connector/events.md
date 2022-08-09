---
title: Événements
description: Découvrez quels événements capturent des données et consultez la définition de schéma complète.
exl-id: b0c88af3-29c1-4661-9901-3c6d134c2386
source-git-commit: 2b735c292920bb0e9052d86bf152748e7ce96079
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Événements de connecteur Experience Platform

Vous trouverez ci-dessous la liste des événements Commerce disponibles lorsque vous installez l’extension Experience Platform Connector. Les données collectées par ces événements sont envoyées à Adobe Experience Platform Edge. Vous pouvez également créer des [événements personnalisés](custom-events.md) pour collecter des données supplémentaires qui ne sont pas prêtes à l’emploi.

Cliquez sur le nom de l’événement pour afficher la définition de schéma complète.

| Événement | Type |
|---|---|
| [Ajouter au panier](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/product/addToCartAEP.ts) | Storefront |
| [Afficher le panier](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/shoppingCart/viewAEP.ts) | Storefront |
| [Afficher la page](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/page/viewAEP.ts) | Storefront |
| [Afficher le produit](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/product/viewAEP.ts) | Storefront |
| [Démarrer le paiement](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/shoppingCart/initiateCheckoutAEP.ts) | Storefront |
| [Finalisation du passage en caisse](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/checkout/placeOrderAEP.ts) | Storefront |
| [Se connecter](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/signInAEP.ts) | Profil |
| [Se déconnecter](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/signOutAEP.ts) | Profil |
| [Créer un compte](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/createAccountAEP.ts) | Profil |
| [Modifier le compte](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/editAccountAEP.ts) | Profil |
| [Requête de recherche envoyée](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/search/searchRequestSentAEP.ts) | Rechercher |
| [Réponse de recherche reçue](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/search/searchResponseReceivedAEP.ts) | Rechercher |

>[!NOTE]
>
> Le `Sign In`, `Sign Out`, `Create Account`, et `Update Account` Les événements sont déclenchés lors de la tentative d’action spécifique. Cela n’indique pas que l’action a réussi.
