---
title: Introduction à [!DNL Live Search]
description: "[!DNL Live Search] d’Adobe Commerce offre une expérience de recherche rapide, pertinente et intuitive."
exl-id: aca0ef19-ead1-4c79-90c3-db5ec48cb3c1
recommendations: noCatalog
source-git-commit: 12c9fa011662e2e9fd7bb088db97359dcde87915
workflow-type: tm+mt
source-wordcount: '722'
ht-degree: 0%

---

# Introduction à [!DNL Live Search]

[!DNL Live Search] est un service pour Adobe Commerce qui remplace les fonctionnalités de recherche standard. La variable [!DNL Live Search] module est installé avec le compositeur et connecte votre [!DNL Commerce] à l’emplacement [!DNL Live Search] [service](../landing/saas.md). Lorsqu’il est configuré, le champ de texte de recherche par défaut est remplacé par le champ [!DNL Live Search] Champ de texte. [!DNL Live Search] installe également le widget Page de liste de produits (PLP) qui fournit de puissantes fonctionnalités de filtrage lors de la navigation dans les résultats de recherche.

[!DNL Live Search] apparaît sur la *Marketing* sous *SEO &amp; Search* dans le [!DNL Commerce] *Administration*.

Le côté Adobe Commerce de l’architecture inclut l’hébergement de la recherche. *Administration*, synchroniser les données du catalogue et exécuter le service de requête. Après [!DNL Live Search] est installé et configuré, Adobe Commerce commence à partager les données de recherche et de catalogue avec les services SaaS. À ce stade, les utilisateurs administrateurs peuvent configurer, personnaliser et gérer la recherche. [facettes](facets.md), [synonyms](synonyms.md), et [règles de marchandisage](category-merch.md).

## Composants de recherche en direct

* [!DNL Live Search] [widget contextuel](storefront-popover.md) est la zone qui s’ouvre sous le champ de recherche qui contient les résultats de la recherche.
* [Widget de page de liste de produits](plp-styling.md) fournit une page de liste de produits pouvant faire l’objet d’une recherche, avec facettes et prise en charge de synonymes.
* Composants CIF AEM : [widget contextuel](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/content-and-commerce/integrations/live-search-popover.html?lang=en) et la variable [Widget PLP](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/content-and-commerce/integrations/live-search-plp.html) permettre aux AEM sites de tirer parti des [!DNL Live Search].
* [[!DNL Live Search] Administration](workspace.md) est l’emplacement où les règles, les facettes et les synonymes sont configurés.

## Workflow - Aperçu

[!DNL Live Search] fonctionne en déplaçant les données du catalogue vers l’infrastructure Adobe Commerce SaaS et en créant des index qui sont utilisés pour fournir rapidement les résultats de recherche lorsque les utilisateurs entrent dans le type .

### 1. Installation

[!DNL Live Search] is [installé](install.md) dans votre instance Adobe Commerce via [Compositeur](https://getcomposer.org/). Cette opération installe les modules requis qui se connectent au service et configure l’instance Commerce pour remplacer le champ de recherche par défaut. Il installe également les options d’administration de Commerce pour configurer le service.

### 2. Synchroniser les données

[!DNL Live Search] déplace les données du catalogue vers l’infrastructure SaaS d’Adobe. Les données sont indexées et les résultats de la recherche sont diffusés de cet index directement sur le storefront. Selon la taille et la complexité, l’indexation peut prendre de 30 minutes à quelques heures.

### 3. Configurer les données

La configuration correcte des données de vos produits garantit de bons résultats de recherche pour vos clients. Deux étapes de configuration sont nécessaires : l’attribution des catégories et la configuration des attributs.

#### Attribution de catégories

Produit renvoyé dans [!DNL Live Search] doit se voir attribuer un [category](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/categories.html). Dans Luma, par exemple, les produits sont classés dans des catégories telles que &quot;Hommes&quot;, &quot;Femmes&quot; et &quot;Porcs&quot;. Les sous-catégories sont également configurées pour &quot;Tops&quot;, &quot;Bottoms&quot; et &quot;Montres&quot;. Cela permet une meilleure granularité lors du filtrage.

#### Champs indexables et filtrables

Les produits sont attribués [Attributs](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) qui peuvent être utilisés pour la recherche et le filtrage. Les attributs sont des éléments tels que &quot;Couleur&quot;, &quot;Taille&quot;, &quot;Type de matière&quot;. Avec ces attributs, les utilisateurs peuvent rechercher des &quot;ordinateurs verts&quot;. De nombreux attributs peuvent être définis pour chaque produit dans l’administrateur Commerce.

Chacun de ces attributs peut être défini comme [&quot;searchable&quot;](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html) dans l’administrateur. Lorsqu’ils sont définis sur &quot;pouvant faire l’objet d’une recherche&quot;, ces attributs peuvent être recherchés par [!DNL Live Search].

[Facettes](facets.md) sont des attributs de produit définis dans [!DNL Live Search] pour être filtrable. Tout attribut filtrable peut être défini comme une facette dans [!DNL Live Search] mais il existe des limites au nombre de facettes pouvant être recherchées simultanément.

[Synonymes](synonyms.md) sont des termes que vous pouvez définir pour guider les utilisateurs vers le produit approprié. Les utilisateurs qui recherchent un pantalon peuvent taper &quot;pantalon&quot; ou &quot;pantalons&quot;. Vous pouvez définir des synonymes de sorte que ces termes de recherche amènent les utilisateurs aux résultats &quot;pantalon&quot;.

## [!DNL Live Search] workspace

La variable [!DNL Live Search] [workspace](workspace.md) est la zone de l’administrateur dans laquelle vous configurez [!DNL Live Search] fonctions telles que les synonymes, les facettes et le marchandisage par catégorie.

## Événements

[!DNL Live Search] uses [events](events.md) pour calculer [Marchandisage intelligent](category-merch.md) et [performance](performance.md) tableaux de bord. Le mode Eventing est fourni avec les implémentations par défaut. Le mode Eventing pour les vitrines sans interface doit être activé manuellement.

## Personnalisation des widgets

La plupart des propriétaires de magasins souhaitent s’assurer que la variable [!DNL Live Search] Les widgets sont conformes à leur apparence de magasin.

Les widgets contextuels et PLP peuvent être stylisés en définissant des règles CSS personnalisées selon les besoins. Voir [Style des éléments contextuels](storefront-popover-styling.md) et [Widget de page de liste de produits](plp-styling.md).

Si vous souhaitez étendre les fonctionnalités des widgets, le code source de chacun d’eux est disponible dans un référentiel public.
Dans ce scénario, vous pouvez personnaliser le code JavaScript en fonction de vos besoins, puis héberger votre code personnalisé sur votre réseau de diffusion de contenu. Ce script personnalisé communique avec la variable [!DNL Live Search] et renvoie les résultats comme s’ils étaient normaux, ce qui vous permet de contrôler les fonctionnalités du widget.

* [Référentiel de widgets PLP](https://github.com/adobe/storefront-product-listing-page)
* [Référentiel de barre de recherche](https://github.com/adobe/storefront-search-as-you-type)

En savoir plus sur [!DNL Live Search] dans le [Présentation technique](technical-overview.md).

## [!DNL Live Search] demo

Regardez cette vidéo pour en savoir plus sur [!DNL Live Search]:

>[!VIDEO](https://video.tv.adobe.com/v/3418679?quality=12&learn=on)

Pour une vidéo plus détaillée sur l’utilisation et la configuration de la recherche en direct, voir [Manifestation complète sur [!DNL Live Search]](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/capabilities/live-search-full-demonstration.html) rubrique.
