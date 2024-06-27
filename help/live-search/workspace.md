---
title: "Configuration de la recherche en direct"
description: La variable [!DNL Live Search] workspace est utilisé pour configurer, gérer et surveiller les performances de recherche.
exl-id: fb85974a-a5f9-4e6c-bd03-451e6457f2d2
source-git-commit: 5e79bb43449b95b4c6aa0e234a0dbc999c312e59
workflow-type: tm+mt
source-wordcount: '921'
ht-degree: 0%

---

# Configuration de la recherche en direct

L’espace de travail vous permet de configurer, de gérer et de surveiller les performances de [!DNL Live Search]. Le menu situé en haut permet d’accéder aux outils de chaque domaine fonctionnel. Les fonctionnalités disponibles reflètent la sélection de menu actuelle.

![Workspace](assets/workspace.png)

## Collecte de données

Pour vous assurer que chaque zone fonctionnelle de l’espace de travail contient les données correctes, vous devez configurer la collecte des données en fonction de l’implémentation de storefront sélectionnée :

1. Luma - La collecte de données est disponible par défaut.
1. Sans affichage : la collecte de données doit être configurée manuellement, en fonction de l’implémentation du storefront.

Si vous utilisez une vitrine sans interface utilisateur, reportez-vous à la documentation suivante pour obtenir plus d’informations sur les événements requis que vous devez ajouter :

- [Événements requis](events.md) pour le tableau de bord de la recherche en direct.
- [Collecteur d’événements Storefront](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/) qui doit être ajouté comme condition préalable.
- [Exemples](https://github.com/adobe/commerce-events/tree/main/examples) de la structure des événements.

## Définition de la portée

Initialement, la variable [scope](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) de tous [!DNL Live Search] est défini sur `Default Store View`. Si votre [!DNL Commerce] l’installation comprend plusieurs vues de magasin, définies **Portée** à la fonction [vue de magasin](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html) où s’appliquent vos paramètres de facette.

## Options de menu

| Option | Description |
|--- |--- |
| [Performances](performance.md) | Le tableau de bord donne des informations sur les performances de recherche de produits. |
| [Facturation](facets.md) | Filtrage haute performance qui utilise plusieurs dimensions de valeurs d’attribut pour affiner les critères de recherche. |
| [Synonymes](synonyms.md) | Étendez la portée de la recherche pour inclure les mots que les acheteurs peuvent utiliser pour trouver des produits différents de ceux de votre catalogue. |
| [Marchandisage des recherches](rules.md) | Formez l’expérience de recherche à l’aide de règles logiques qui déclenchent des actions planifiées. Amplifiez, enseignez, épinglez ou masquez des produits afin d’étalonner les résultats de recherche en fonction de vos objectifs commerciaux. |
| [Marchandisage des catégories](category-merch.md) | Appliquez des règles et du marchandisage intelligent au niveau de la catégorie. |
| [GraphQL](graphql.md) | Les développeurs connectés à l’administrateur de votre boutique peuvent composer et tester des requêtes avec des données de catalogue réelles. Pour en savoir plus, accédez à [Présentation de GraphQL](https://developer.adobe.com/commerce/webapi/graphql/) dans le [!DNL Live Search] documentation destinée aux développeurs. |
| [Paramètres](settings.md) | Déterminez comment les valeurs des facettes de prix sont regroupées par tranche de prix dans le storefront et définissez la langue d’indexation. |

## Définir les attributs comme pouvant faire l’objet d’une recherche

Pour produire des résultats très ciblés, passez en revue le jeu de [searchable](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) (`searchable=true`) des attributs de produit. Pour garantir la pertinence, ne autorisez la recherche des attributs que s’ils contiennent du contenu ayant une signification claire et concise. Évitez d’utiliser des attributs contenant un texte plus long et moins précis, comme `description`, qui, bien que la recherche soit activée par défaut, peut réduire la précision des résultats de recherche. Par exemple, si une personne recherche &quot;shorts&quot; et qu’il y a des chemises avec une description qui inclut le terme &quot;manches courtes&quot;, les chemises seront incluses dans les résultats de la recherche.

Pour autoriser la recherche des attributs, procédez comme suit :

1. Dans Admin, accédez à **Magasins** > *Attribut* > **Produit**.
1. Sélectionnez l’attribut que vous souhaitez rechercher, par exemple `color`.
1. Sélectionner **Propriétés Storefront** et défini **Utilisation dans la recherche** to `yes`.

   ![Workspace](assets/attribute-searchable.png)

[!DNL Live Search] respecte également la variable [poids](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-results.html#weighted-search) d’un attribut de produit, tel que défini dans Adobe Commerce. Les attributs ayant un poids supérieur apparaissent plus haut dans les résultats de recherche.

Les attributs suivants peuvent toujours faire l’objet de recherches :

- `sku`
- `name`
- `categories`

[Facettes](facets.md) sont des attributs de produit définis dans [!DNL Live Search] pour être filtrable. Vous pouvez définir n’importe quel attribut filtrable comme facette dans [!DNL Live Search], mais il existe [limites](boundaries-limits.md) au nombre de facettes que vous pouvez rechercher simultanément.

[Synonymes](synonyms.md) sont des termes que vous pouvez définir pour guider les utilisateurs vers le produit approprié. Les utilisateurs qui recherchent un pantalon peuvent taper &quot;pantalon&quot; ou &quot;pantalons&quot;. Vous pouvez définir des synonymes de sorte que ces termes de recherche amènent les utilisateurs aux résultats &quot;pantalon&quot;.

## Paramètres de configuration Commerce

La section suivante décrit les paramètres de configuration Commerce pris en charge et non pris en charge pour [!DNL Live Search].

### Valeurs de configuration compatibles

| Paramètre de configuration Commerce | Description | Pris en charge par Popover | Pris en charge par l’adaptateur |
|---|---|---|---|
| Magasins > Configuration > Catalogue > Catalogue > Recherche catalogue > Autoriser tous les produits par page | Si la variable est définie sur `Yes`, inclut la variable `ALL` dans le contrôle &quot;Afficher par page&quot;. | Oui. 500 produits max | Oui. 500 produits max |
| Magasins > Configuration > Catalogue > Recherche catalogue > Longueur minimale de requête | Nombre minimum de caractères autorisés dans une recherche catalogue. | Oui | Oui |
| Magasins > Configuration > Catalogue > Recherche catalogue > Produits par page sur les valeurs autorisées de la grille | Détermine le nombre de produits affichés en mode Grille. | Oui | Oui |
| Magasins > Configuration > Catalogue > Recherche catalogue > Produits par page sur la valeur par défaut de la grille | Détermine le nombre de produits affichés par page par défaut en mode Grille. | Oui. 500 produits max | Oui. 500 produits max |
| Magasins > Configuration > Catalogue > Inventaire > Afficher les produits en rupture de stock | Affiche les produits en rupture de stock. | Oui avec v2.0.4+ | Oui avec v2.0.4+ |
| Magasins > Configuration > Devise > Devise d’affichage par défaut | Devise principale utilisée pour afficher les prix. | Oui avec 3.1.0+ | Oui avec 3.1.0+ |
| Magasins > Configuration > Général > Configuration de devise > Options de devise > Devise de base | Devise principale utilisée pour toutes les transactions de paiement en ligne. | Oui | Oui |

Les prix dans la page de liste de produits du widget et la fenêtre contextuelle sont convertis en devise d’affichage par défaut à l’aide des taux de devise configurés.

### Valeurs de configuration non prises en charge

| Paramètre de configuration Commerce | Description | Remarques |
|---|---|---|
| Magasins > Configuration > Catalogue > Magasin > Mode Liste | Détermine le format de la liste des résultats de recherche. | Effectue le rendu correctement, mais les événements ne sont pas envoyés pour certaines interactions de page. |
| Magasins > Configuration > Catalogue > Catalogue > Recherche catalogue > Longueur maximale de requête | Nombre maximal de caractères autorisés dans une recherche catalogue. | Non implémenté ; les services de recherche acceptent jusqu’à 255 caractères |
| Configuration > Ventes > Taxe > Paramètres d’affichage des prix > Afficher les prix des produits dans le catalogue | Détermine si les prix des produits publiés dans le catalogue incluent ou excluent la taxe, ou affichent deux versions du prix ; l’une avec et l’autre sans taxe. |  |
| Magasins > Configuration > Catalogue > Magasin > Liste de produits Trier par | Détermine l’ordre de tri de la liste des résultats de la recherche. | Ne s’applique pas à la variable [!DNL Live Search] [Widget de page de liste de produits](plp-styling.md) |

### Termes de recherche

[!DNL Live Search] prend [redirections de termes de recherche](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-terms.html) sur les implémentations dans lesquelles Adobe Commerce gère le routage, par exemple sur Luma et d’autres thèmes basés sur php.
