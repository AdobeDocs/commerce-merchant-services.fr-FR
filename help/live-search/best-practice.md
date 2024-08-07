---
title: '[!DNL Live Search] Bonnes pratiques'
description: Découvrez les bonnes pratiques pour implémenter  [!DNL Live Search] dans votre boutique.
role: Admin, Developer
source-git-commit: 88be2212f3a992e7a2d18bf1d5c2e8d5d2b64b80
workflow-type: tm+mt
source-wordcount: '2355'
ht-degree: 0%

---

# Bonnes pratiques

Cet article aide les marchandiseurs à améliorer leurs fonctionnalités de recherche de site, en assurant une expérience d’achat transparente et efficace qui maximise les taux de conversion. En suivant les stratégies décrites, vous apprenez à mettre en oeuvre des fonctionnalités de recherche avancées et à affiner continuellement votre outil de recherche pour des performances optimales avec Adobe Commerce [!DNL Live Search].

Plusieurs facteurs clés déterminent la pertinence et l’efficacité des résultats de recherche :

- Des données de produit bien structurées garantissent que les algorithmes de recherche peuvent faire correspondre efficacement les produits aux requêtes. Des données de produit de mauvaise qualité conduisent à des résultats de recherche peu pertinents. Pour affecter directement le succès de votre stratégie de marchandisage :
   - Configurez les attributs corrects comme pouvant faire l’objet d’une recherche avec leur poids correspondant.
   - Assurez-vous que les données de ces attributs sont pertinentes.
- Une expérience de recherche bien conçue renforce la confiance avec les clients et leur permet de croire qu’ils trouveront ce dont ils ont besoin.
- Les règles de recherche sont essentielles, car elles peuvent améliorer la visibilité de certains produits en fonction de leur popularité, de leurs nouveaux arrivants, de leurs critères promotionnels ou de toute autre stratégie de marchandisage pour répondre aux besoins de votre entreprise.
- La navigation à facettes permet aux acheteurs d’affiner leur recherche et d’obtenir rapidement des résultats pertinents.

Pour gérer [!DNL Live Search], accédez à **Marketing** > *SEO &amp; Search* > **[!DNL Live Search]** dans l’Adobe [!DNL Commerce] Admin. 

## Optimisation de la fonctionnalité de recherche

Dans cette section, vous découvrez comment optimiser vos fonctionnalités de recherche en utilisant des fonctionnalités telles que la saisie automatique pour fournir des suggestions en temps réel comme le type de nouvel acheteur, des synonymes et des orthographes pour vous assurer que les visiteurs trouvent des produits même s’ils utilisent des mots différents, des facettes pour permettre aux acheteurs de réduire les résultats de recherche et des redirections de recherche pour rediriger automatiquement les acheteurs d’une requête de recherche vers une page spécifique.

### Autocomplete

La saisie semi-automatique, également appelée saisie anticipée ou saisie automatique, est une fonction de recherche interactive qui affiche dynamiquement des suggestions aux acheteurs lorsqu’ils saisissent leurs termes de recherche. Cela permet aux acheteurs de trouver facilement et rapidement des produits en leur proposant des suggestions en temps réel basées sur leurs entrées.

Le widget [!DNL Live Search] [[!DNL popover]](storefront-popover.md) permet des options de recherche de saisie automatique pour suggérer des produits populaires. Avec chaque caractère saisi par l’acheteur, la fenêtre contextuelle se met à jour avec les produits suggérés et les images miniatures des principaux résultats de recherche.

[!DNL Live Search] commence à renvoyer des résultats lorsque l’utilisateur a saisi deux caractères. Pour une correspondance partielle, le nombre maximal de caractères par mot est de 20. Le nombre de caractères d’une requête &quot;Rechercher lorsque vous tapez&quot; n’est pas configurable.

En savoir plus sur le widget [popover](storefront-popover.md).

### Synonymes et orthographes

Incluez des synonymes et des fautes d’orthographe courantes pour garantir des résultats de recherche complets. De plus, vous pouvez développer la requête de recherche afin d’inclure des mots que les acheteurs peuvent utiliser qui diffèrent des mots spécifiés dans votre catalogue. Vous ne voulez pas perdre une vente parce que quelqu&#39;un cherche un &quot;canapé&quot;, alors que votre produit est listé comme &quot;canapé&quot;. Vous pouvez capturer un large éventail de termes de recherche en saisissant tous les mots que les clients peuvent utiliser pour trouver vos produits. Vous pouvez [définir des synonymes d’une ou deux manières](synonyms-add.md#step-2-define-the-synonym-by-type) pour améliorer les résultats.

#### Conseils pour optimiser les synonymes

- Mappez les noms et abréviations des marques à leurs noms complets, par exemple &quot;HP&quot; à &quot;Hewlett-Packard&quot; et les surnoms de produits courants, par exemple &quot;iPhone&quot; à &quot;Apple iPhone&quot;.
- Incluez le jargon spécifique au secteur et les termes que les acheteurs peuvent utiliser de manière interchangeable, par exemple &quot;baskets&quot; et &quot;chaussures de course&quot;.
- Mettez régulièrement à jour la liste des synonymes en fonction des nouvelles tendances de recherche, des ajouts de produits et du comportement d’achat.
- Testez l’efficacité des mappages de synonymes en analysant les résultats de recherche et les commentaires des acheteurs. Affinez les mappages afin d’améliorer la précision et la pertinence.

En savoir plus sur les synonymes :

- [Types de synonymes](synonyms-type.md)
- [Créer des synonymes](synonyms-add.md)
- [Gestion des synonymes](synonyms-manage.md)
- [Prise en charge linguistique](settings.md#language)

### Facettes

La fonctionnalité de filtre et de facette est un composant essentiel de votre site [!DNL Commerce], conçu pour améliorer l’expérience client en permettant aux clients de réduire les résultats de recherche et de trouver plus efficacement les produits. Cette fonctionnalité permet aux acheteurs de trier de vastes catalogues d’articles en appliquant des critères spécifiques, ce qui rend le processus d’achat plus rapide, plus facile et plus satisfaisant. En mettant en oeuvre des filtres et des facettes efficaces et conviviales pour les acheteurs, vous pouvez aider les clients à trouver exactement ce dont ils ont besoin rapidement et efficacement, ce qui, à terme, améliore la satisfaction et les taux de conversion.

Pour configurer un attribut de produit en tant que facette, il doit avoir les [ propriétés ](facets-add.md#step-1-add-a-facet) suivantes :

- **[!UICONTROL Use in Search]** -  `Yes`
- **[!UICONTROL Use in Layered Navigation]** -  `Filterable (with results)`
- **[!UICONTROL Use in Search Results Layered Navigation]** -  `Yes`

#### Conseils pour optimiser les facettes

- Déterminez les attributs les plus pertinents et utiles pour vos produits, tels que le titre, la catégorie, la marque, la plage de prix, la couleur et la taille, puis définissez-les comme [facettes dynamiques](facets-type.md). 
- Définissez et triez des attributs de produit cohérents dans l’ensemble de votre catalogue et hautement pertinents pour vos produits afin d’améliorer la pertinence et les fonctionnalités de filtrage pour vos clients.
- Assurez-vous que les libellés de facettes sont faciles à comprendre et nommés de manière cohérente sur l’ensemble du site. Par exemple, utilisez &quot;Plage de prix&quot; au lieu de &quot;Coût&quot;.
- Évitez de surcharger les acheteurs en limitant le nombre de facettes aux plus importantes. Trop d’options peuvent entraîner une fatigue de décision. Par défaut, [!DNL Live Search] est limité à un maximum de 100 attributs configurés en tant que facettes et 30 compartiments renvoyés dans chaque facette. En savoir plus sur les [limites des facettes](boundaries-limits.md#facets). 
- Permet aux acheteurs de sélectionner plusieurs critères de filtrage simultanément pour affiner les résultats. Par exemple, les acheteurs peuvent sélectionner les couleurs &quot;Rouge&quot; et &quot;Bleu&quot;.
- Afficher le nombre de produits disponibles en regard de chaque option de facette pour donner aux acheteurs une idée des résultats de recherche auxquels ils peuvent s’attendre.
- Mettez en oeuvre des sections de facettes réductibles pour que l’interface reste propre et gérable, en particulier sur les appareils mobiles.
- Permet aux acheteurs de réinitialiser facilement des facettes individuelles ou tous les filtres sélectionnés pour lancer une nouvelle recherche.

En savoir plus sur les facettes :

- [Types de facettes](facets-type.md)
- [Ajout de facettes](facets-add.md)
- [Gérer les facettes](facets-manage.md) (modifier, épingler une facette, supprimer, publier)
- [Facturation des prix](settings.md#price-faceting)

### Redirections de recherche

Une redirection de recherche vous permet de rediriger automatiquement les acheteurs d’une requête de recherche vers une page spécifique. Les redirections de recherche peuvent améliorer l’expérience client et guider les clients vers le contenu le plus pertinent, tel qu’une page de produit, une catégorie, une page d’entrée ou un ensemble personnalisé de résultats de recherche. Les redirections de recherche permettent de rationaliser l’expérience d’achat et de s’assurer que les acheteurs trouvent ce qu’ils recherchent rapidement et efficacement.

Cas d’utilisation recommandés pour la configuration des redirections de recherche :

- **Produits ou catégories populaires** - Redirigez les acheteurs vers une page ou une catégorie de produits spécifique lorsqu’ils recherchent des termes courants ou populaires. Par exemple, la recherche de &quot;iPhone&quot; peut rediriger directement vers la page de catégorie iPhone ou une page de modèle spécifique.

- **Campagnes promotionnelles** - Lors d’événements promotionnels ou de ventes, redirigez des termes de recherche pertinents vers des landing pages qui présentent des offres spéciales ou des produits présentés.

- **Recherches de marque** - Lorsque les acheteurs recherchent un nom de marque, redirigez-les vers la page dédiée de la marque où tous les produits de cette marque sont répertoriés.

- **Arrêt des produits** - Si un produit est arrêté, vous pouvez rediriger les recherches de ce produit vers des produits similaires ou la nouvelle version du produit.

Testez toujours les redirections de recherche pour vous assurer qu’elles fonctionnent correctement et qu’elles mènent aux pages les plus pertinentes. Surveillez continuellement leurs performances et effectuez les ajustements nécessaires.

Découvrez comment [gérer les redirections de recherche](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search-terms).

## Amélioration de la pertinence des résultats de recherche

Cette section explique comment améliorer la pertinence des résultats de recherche en implémentant des règles de recherche efficaces et en utilisant les métadonnées de produit pour garantir que les attributs précis et détaillés puissent faire l’objet de recherches.

### Règles de recherche

Pour optimiser votre taux de conversion et vos recettes, vous devez implémenter des règles de recherche efficaces. Ajustez les classements de produits en fonction des données de vente, des niveaux de stock et des promotions avec [Rechercher un marchandisage](rules.md).

Il est essentiel d’établir une règle de recherche par défaut bien pensée. Votre [règle par défaut](rules.md#default-rule) détermine la manière dont les résultats de recherche sont initialement triés et affichés aux acheteurs, ce qui améliore leur expérience globale et augmente la probabilité d’achat. La surveillance et l’ajustement réguliers de cette règle assurent qu’elle continue de répondre efficacement aux besoins des acheteurs et aux objectifs commerciaux.

#### Conseils pour optimiser les règles de recherche

- Épinglez ou optimisez des produits avec des volumes de ventes élevés ou une activité de vente récente.
- Classez par ordre de priorité les produits présentant des notes élevées et des avis positifs.
- Assurez-vous que les éléments en stock sont classés plus haut.
- Classez légèrement les produits avec des marges bénéficiaires plus élevées sans compromettre la pertinence.
- Mettre en évidence les produits en vente ou faisant partie de promotions spéciales.
- Définissez automatiquement les règles de recherche lors de la promotion ou des périodes de vente à l’aide de la plage de dates pendant la période de promotion.
- Personnalisez les résultats de la recherche en fonction du comportement d’acheteur individuel en utilisant le [classement intelligent](rules-add.md#intelligent-ranking), tel que &quot;recommandé pour vous&quot;, &quot;le plus consulté&quot;, etc. Pour personnaliser le comportement d’achat, vous devez vous assurer que l’événement est correctement mis en oeuvre. Pour les commerçants Luma, le soir est disponible en standard. Pour les implémentations sans interface utilisateur graphique ou personnalisées, vous devez [implémenter des événements](events.md) en fonction de vos besoins spécifiques.

En savoir plus sur les règles de recherche :

- [Espace de travail de marchandisage](rules-workspace.md#set-the-scope)
- [Conditions](rules.md#requirements)
- [Règle de recherche par défaut](rules.md#default-rule)
- Gestion des règles de recherche
   - [Créer](rules-add.md)
   - [Modifier, afficher, supprimer](rules-manage.md)
- Collecte de données
   - [[!DNL Live Search] événements](events.md)
   - [Collecteur d’événements Adobe Commerce](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/)
   - [Événements Commerce GitHub](https://github.com/adobe/commerce-events/tree/main/examples) 

### Utilisation des métadonnées de produit

Assurez-vous que les attributs de produit précis et détaillés sont [configurés en tant que recherche possible](workspace.md#set-attributes-as-searchable). Notez que les attributs SKU, name et category peuvent faire l’objet de recherches par défaut et ne peuvent pas être exclus de la recherche. 

Pour accroître la pertinence de la recherche, attribuez un poids à chaque attribut pouvant faire l’objet d’une recherche. Les attributs ayant un poids supérieur doivent apparaître plus haut dans les résultats de recherche. Le tri par pertinence est affecté par plusieurs critères, tels que le poids de la recherche. Cela signifie que parfois les attributs ayant un poids de recherche inférieur peuvent toujours avoir plus de pertinence que les attributs ayant un poids de recherche supérieur. D’autres critères peuvent inclure le nombre de correspondances dans un attribut donné, la position du terme de recherche trouvé et la structure de texte globale avant et après un terme de recherche.

Assurez-vous que chaque produit comporte du contenu pertinent dans chaque attribut pouvant faire l’objet d’une recherche. Il n’est pas recommandé de définir un attribut comme pouvant faire l’objet d’une recherche s’il comporte de grandes quantités de contenu, car cela peut réduire la pertinence des résultats de recherche.

En savoir plus sur les attributs de produit pour la recherche :

- [Définir les attributs comme pouvant faire l’objet d’une recherche](workspace.md#set-attributes-as-searchable)
- [Attribuer du poids aux attributs](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search-results#weighted-search)

## Surveillance des résultats de recherche

Pour optimiser les résultats de recherche avec [!DNL Live Search], surveillez les indicateurs de performance clés (IPC) pertinents tels que les requêtes uniques, la position moyenne des clics, les taux de clics publicitaires, le taux de conversion et le taux de résultats zéro pour comprendre comment les acheteurs interagissent avec votre fonctionnalité de recherche. Ces données vous guident pour mettre à jour et affiner régulièrement vos règles de recherche.

Vous pouvez surveiller ces indicateurs clés de performance dans l’ [!DNL Live Search] [espace de travail des performances](performance.md) où vous trouverez les mesures suivantes : 

- **Recherches uniques** - Le nombre de requêtes de recherche distinctes effectuées sur votre site [!DNL Commerce]. Chaque recherche unique est comptabilisée une seule fois, même si elle est répétée plusieurs fois par le même acheteur ou par différents acheteurs. Cette mesure vous aide à comprendre la diversité des termes de recherche utilisés par les clients et fournit des informations sur les produits ou les informations recherchées par les acheteurs. Le suivi des recherches uniques vous permet d’effectuer les opérations suivantes :

   - Identifiez les tendances de recherche les plus courantes et les éléments les plus fréquemment recherchés.
   - Détectez les lacunes potentielles dans votre catalogue de produits ou votre contenu.
   - Optimisez votre fonctionnalité de recherche en ajoutant [des synonymes](synonyms.md), en créant ou en mettant à jour des règles de recherche.

- **Position moyenne des clics** : indique que la position moyenne des résultats de recherche sur lesquels les acheteurs ont cliqué après avoir effectué une requête sur votre site. Cette mesure fournit des informations sur la pertinence et l’efficacité de vos résultats de recherche.

  Une position de clic moyenne inférieure (plus proche de 1) indique que les acheteurs trouvent rapidement les résultats pertinents, ce qui indique que votre stratégie de recherche est efficace. Il vous aide à comprendre le comportement des acheteurs et jusqu’où ils sont prêts à faire défiler pour trouver le produit souhaité. Si la position de clic moyenne est élevée, cela peut indiquer que les résultats les plus pertinents n’apparaissent pas en haut, ce qui nécessite une révision et une optimisation de votre stratégie de recherche.

- **Taux de clics publicitaires (CTR)** - Mesure le pourcentage d’acheteurs qui cliquent sur un résultat de recherche après avoir effectué une requête. Un taux de clics élevé indique que les résultats de la recherche sont pertinents et attrayants pour les acheteurs qui cliquent sur les résultats qu’ils trouvent. Le suivi des CTR peut aider à identifier les domaines à améliorer. Le taux de clics faible peut suggérer que les résultats de recherche ne correspondent pas à l’intention du nouvel acheteur, ce qui nécessite la nécessité d’affiner les règles de recherche, d’améliorer les données du produit ou d’améliorer la présentation des résultats.

- **Taux de conversion** - Indique l’efficacité de votre fonction de recherche pour stimuler les ventes et atteindre les objectifs de l’entreprise. Elle reflète l’efficacité globale de la fonctionnalité de recherche pour répondre aux besoins des acheteurs et faciliter une expérience d’achat fluide. Un taux de conversion élevé indique que vos résultats de recherche sont pertinents et convaincants, ce qui conduit les acheteurs à terminer leurs achats. Si le taux de conversion est faible, il peut suggérer des problèmes de pertinence de la recherche, de disponibilité du produit ou de parcours d’achat global, de la recherche à l’achat.

- **Zéro résultat** - Mesure le pourcentage de requêtes de recherche sur votre site [!DNL Commerce] qui ne renvoient aucun résultat. Cette mesure est essentielle pour comprendre la fréquence à laquelle les recherches des acheteurs échouent et peut fournir des informations sur les lacunes potentielles dans la configuration de votre catalogue de produits ou de votre recherche. Un taux de résultats zéro élevé peut frustrer les acheteurs, ce qui entraîne une expérience d’achat médiocre et une perte potentielle de clients. Il peut indiquer les produits ou catégories manquants dans votre catalogue que les acheteurs recherchent, guidant les décisions d’inventaire et de liste de produits.

  Pour réduire le taux de résultats zéro, vous pouvez :

   - proposer des termes de recherche alternatifs ou associés, tels que [synonyms](synonyms.md) lorsqu’aucune correspondance exacte n’est trouvée ;
   - Fournissez aux acheteurs des suggestions connexes ou alternatives lorsque leur recherche ne donne aucun résultat en définissant des redirections de recherche.
   - Consultez régulièrement zéro requête de résultat pour identifier les modèles et apporter les ajustements nécessaires à votre catalogue de produits et à vos paramètres de recherche.

- **Résultats populaires** - Peut améliorer considérablement vos résultats de recherche en les alignant avec les préférences et les comportements des acheteurs.

Vous pouvez utiliser ces données de mesure pour optimiser la fonctionnalité de recherche des façons suivantes :

- Mettez en oeuvre des règles pour classer automatiquement les produits populaires plus haut dans les résultats de recherche. Les produits fréquemment utilisés ou achetés peuvent recevoir la priorité d’apparaître en haut. Traitez manuellement les listes de produits populaires pour des requêtes de recherche spécifiques et assurez-vous que ces éléments s’affichent correctement.
- Mettez en évidence les produits actuellement tendance ou qui ont récemment connu un pic de popularité. Cela peut s’avérer particulièrement efficace lors d’événements saisonniers, de vacances ou de périodes promotionnelles. Pour ce faire, utilisez le classement intelligent qui correspond mieux à votre cas d’utilisation et aux besoins de votre entreprise lors de la configuration d’une règle de recherche.
- Mettez en évidence les filtres ou facettes populaires, si les acheteurs filtrent fréquemment selon certaines marques ou plages de prix, rendez ces options plus importantes en les épinglant et en les triant en conséquence.
- Lorsqu’une recherche ne donne aucun résultat, utilisez les données de résultats populaires pour suggérer des produits alternatifs ou des catégories connexes présentant un engagement élevé de la part des acheteurs.
- Analysez les termes de recherche courants et les données de produit pour identifier les mots-clés importants. Optimisez les attributs pouvant faire l’objet d’une recherche avec ces mots-clés pour améliorer la pertinence de la recherche.
- Analysez régulièrement vos données de résultats afin de comprendre les tendances, les préférences et les comportements changeants des acheteurs, d’identifier les termes de recherche principaux et de détecter des problèmes. Utilisez cette boucle de rétroaction pour affiner et améliorer continuellement vos règles de recherche et vos offres de produits

Pour obtenir des données correctes dans votre rapport [!DNL Live Search], vous devez vous assurer que l’événement est correctement mis en oeuvre. Pour les commerçants Luma, le soir est disponible en standard. Pour les implémentations sans interface utilisateur graphique ou personnalisées, vous devez [implémenter des événements](events.md) en fonction de vos besoins spécifiques.
