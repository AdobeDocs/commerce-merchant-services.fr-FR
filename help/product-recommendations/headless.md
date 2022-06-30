---
title: Headless
description: Découvrez comment intégrer [!DNL Product Recommendations] dans une vitrine sans tête.
exl-id: 316d0b0c-5938-4e2f-9d0d-747746cf6056
source-git-commit: ce437d7a991affd2665c86c9e91bb7f39ec626c0
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---

# Headless

Vous pouvez intégrer des [!DNL Product Recommendations] dans une vitrine sans interface utilisant soit [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/) ou une technologie front-end personnalisée, telle que React ou Vue JS.

[!DNL Product Recommendations] require [données comportementales et catalogues](https://devdocs.magento.com/recommendations/product-recs.html#typesofdata) pour fonctionner. Le processus de synchronisation des données de catalogue reste inchangé dans une mise en oeuvre sans interface utilisateur, mais des modifications sont nécessaires pour la collecte de données comportementales.

Pour intégrer [!DNL Product Recommendations] dans une vitrine sans interface, vous devez :

1. Envoyez des données comportementales à Adobe Sensei pour analyser et calculer les résultats des recommandations de produits. Vous pouvez également envoyer des données supplémentaires pour activer la recommandation de produit. [rapport sur les mesures](workspace.md).

1. Récupérez les résultats des recommandations de produits et effectuez le rendu de ces résultats sur la page.

Vous pouvez effectuer ces deux actions à l’aide des SDK disponibles, comme décrit dans le workflow suivant.

1. [Installer](install-configure.md) la valeur [!DNL Product Recommendations] module .

1. Installez et utilisez la méthode [SDK d’événement Adobe Commerce Storefront](https://devdocs.magento.com/shared-services/storefront-events-sdk.html) pour déclencher la variable [événements comportementaux](https://devdocs.magento.com/recommendations/events.html).

   Le nombre minimum d’événements requis à renvoyer [!DNL Product Recommendations] résultats :

   | Événement | Catégorie |
   |--- | ---|
   | `view` | product |
   | `add-to-cart` | product |
   | `place-order` | passage en caisse |

   Pour activer [rapport sur les mesures](workspace.md), les événements supplémentaires suivants sont requis :

   | Événement | Catégorie |
   |--- | ---|
   | `impression-render` | recommendation-unit |
   | `view` | recommendation-unit |
   | `rec-click` | recommendation-unit |
   | `rec-add-to-cart-click` | unité-recommandation (si un bouton d’ajout au panier est présent dans le modèle de recommandations) |

1. Lorsque les événements sont déclenchés, utilisez la variable [Collecteur d’événements Adobe Commerce Storefront](https://devdocs.magento.com/shared-services/storefront-event-collector.html) pour gérer les événements et les envoyer à Adobe Sensei.

1. Une fois les données comportementales collectées, vous pouvez [create](create.md) [!DNL Product Recommendations] dans Admin.

1. Utilisez la variable [SDK Recommendations](https://devdocs.magento.com/recommendations/recs-api.html) pour récupérer les unités de recommandations sur le storefront. Le SDK renvoie les données de produit nécessaires pour effectuer le rendu des unités de recommandation sur une page.
