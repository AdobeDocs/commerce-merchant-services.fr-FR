---
title: '''[!DNL Quick Checkout] Notes de mise à jour'''
description: Consultez les notes de mise à jour pour plus d’informations sur toutes les [!DNL Quick Checkout] versions.
exl-id: 511be2fc-d24d-4323-a47a-d376e38a5c47
source-git-commit: 6162141e1ddf4428126178bd172e8d9bd250c485
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 1%

---

# Notes de mise à jour

Ces notes de mise à jour décrivent la version initiale de [!DNL Quick Checkout] et incluent :

![Nouveau](../assets/new.svg) Nouvelles fonctionnalités
![Correction d’un problème](../assets/fix.svg) Correctifs et améliorations
![Problème connu](../assets/bug.svg) Problèmes connus

Voir [Versions à venir](https://devdocs.magento.com/release/) pour en savoir plus sur les calendriers de publication et l’assistance.

Voir [Disponibilité](https://devdocs.magento.com/release/availability.html) dans la documentation destinée aux développeurs pour en savoir plus sur la compatibilité des produits.

## v1.0.0

![Nouveau](../assets/new.svg)<!-- Issue BOLT-341 --> Disponibilité générale -[[!DNL Quick Checkout]](https://marketplace.magento.com/magento-quick-checkout.html) est désormais compatible avec les versions 2.4.1 à 2.4.4 d’Adobe Commerce.

![Nouveau](../assets/new.svg)<!-- Issue BOLT-340 --> Le [!DNL Quick Checkout] pour Adobe Commerce peut être installé pour Adobe Commerce [sur l’infrastructure cloud](install.md#adobe-commerce-on-cloud-infrastructure) ou [sur site](install.md#on-premises) instances. Ces méthodes nécessitent l&#39;utilisation d&#39;une interface de ligne de commande.

![Nouveau](../assets/new.svg)<!-- Issue BOLT-1 --> Le [!DNL Quick Checkout] pour Adobe Commerce apporte une vitrine optimisée qui permet d’obtenir une [expérience de passage en caisse en un clic](overview.md) sans champ de remplissage requis pour les consommateurs.

![Nouveau](../assets/new.svg)<!-- Issue BOLT-1 --> Le [!DNL Quick Checkout] pour Adobe Commerce reconnaît automatiquement chaque acheteur dans son réseau pour [achats en un clic](checkout-flow.md) directement sur votre site.

![Nouveau](../assets/new.svg)<!-- Issue BOLT-1 --> Le [!DNL Quick Checkout] pour Adobe Commerce, un acheteur peut être simultanément [Connecté aux réseaux Adobe Commerce et Bolt](checkout-flow.md/#quick-checkout-use-cases) afin de fournir un meilleur `one-click checkout` expérience.

![Nouveau](../assets/new.svg)<!-- Issue BOLT-218 --> [!DNL Quick Checkout] pour Adobe Commerce prend en charge une [compte sandbox](testing.md#testing-in-sandbox) qui permet aux commerçants d’évaluer l’extension en mode test.

![Nouveau](../assets/new.svg)<!-- Issue BOLT-780 --> Vos acheteurs peuvent les extraire via le [[!DNL Quick Checkout]](checkout-page.md) ou via une extension [création manuelle de commande](create-order-admin.md).

![Nouveau](../assets/new.svg)<!-- Issue BOLT-666 --> Les vendeurs peuvent configurer la variable [!DNL Quick Checkout] avec des actions de paiement de base, telles que [`Authorize and Capture` ou `Authorize` ](onboarding.md#complete-admin-configuration)ou le passage d’un environnement de test à un autre.

![Nouveau](../assets/new.svg)<!-- Issue BOLT-288 --> Personnalisé [durée de la session utilisateur](user-session-lifetime.md) pour [!DNL Quick Checkout] pour Adobe Commerce.

![Problème connu](../assets/bug.svg)<!-- Issue BOLT-342 --> Utilisation [clés de compositeur incorrectes](https://support.magento.com/hc/en-us/articles/6909450342541) lors de l’installation de la fonction [!DNL Quick Checkout] empêche l’utilisateur de [authentification](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) avec la valeur correcte `MAGEID`.
