---
title: Introduction à [!DNL Live Search]
description: "[!DNL Live Search] d’Adobe Commerce offre une expérience de recherche rapide, super pertinente et intuitive."
exl-id: aca0ef19-ead1-4c79-90c3-db5ec48cb3c1
recommendations: noCatalog
source-git-commit: 3352bd1390704646f4c21599ebf204eda2e1488c
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---

# Introduction à [!DNL Live Search]

[!DNL Live Search] est un service pour Adobe Commerce qui remplace les fonctionnalités de recherche standard. La variable [!DNL Live Search] module est installé avec le compositeur et connecte votre [!DNL Commerce] à l’emplacement [!DNL Live Search] [service](../landing/saas.md). Lorsqu’il est configuré, le champ de texte de recherche par défaut est remplacé par le champ [!DNL Live Search] Champ de texte.

[!DNL Live Search] apparaît sur la *Marketing* sous *SEO &amp; Search* dans le [!DNL Commerce] *Administration*.

Le côté Adobe Commerce de l’architecture inclut l’hébergement de la recherche. *Administration*, synchroniser les données du catalogue et exécuter le service de requête. Après [!DNL Live Search] est installé et configuré, Adobe Commerce commence à partager les données de recherche et de catalogue avec les services SaaS. À ce stade, les utilisateurs administrateurs peuvent configurer, personnaliser et gérer la recherche. [facettes](facets.md), [synonyms](synonyms.md), et [règles de marchandisage](category-merch.md).

![Schéma de l’architecture de la recherche en direct](assets/architecture-diagram.svg)

## Composants de recherche en direct

* [!DNL Live Search] [fenêtre contextuelle](storefront-popover.md) est la zone qui s’ouvre sous le champ de recherche qui contient les résultats de la recherche.
* [Widget de page de liste de produits](plp-styling.md) fournit une page de liste de produits pouvant faire l’objet d’une recherche, avec facettes et prise en charge de synonymes.
* Composants CIF AEM : [widget contextuel](https://github.com/adobe/aem-cif-guides-venia/pull/319) et la variable [Widget PLP](https://github.com/adobe/aem-cif-guides-venia/pull/320) permettre aux AEM sites de tirer parti des [!DNL Live Search].
* [[!DNL Live Search] Administration](workspace.md) est l’emplacement où les règles, les facettes et les synonymes sont configurés.
* L’adaptateur de recherche est l’implémentation par défaut de [!DNL Live Search].

## [!DNL Live Search] demo

Regardez cette vidéo pour en savoir plus sur [!DNL Live Search]:

>[!VIDEO](https://video.tv.adobe.com/v/3418679?quality=12&learn=on)

Pour une vidéo plus détaillée sur l’utilisation et la configuration de la recherche en direct, voir [Manifestation complète sur [!DNL Live Search]](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/marketing/live-search-full-demonstration.html) rubrique.
