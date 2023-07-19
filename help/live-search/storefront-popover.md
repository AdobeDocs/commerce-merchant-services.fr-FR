---
title: "[!DNL Storefront Popover]"
description: "Le [!DNL Live Search storefront popover] renvoie dynamiquement les produits suggérés et les miniatures."
exl-id: 88fdc3ed-b606-40de-94b7-435be09c4072
source-git-commit: 96a5791c5716f612f473540f27bd3f99b1bfe7c8
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---

# [!DNL Storefront Popover]

When [!DNL Live Search] is [installé](install.md), un [!DNL popover] apparaît dans le storefront lorsque les clients saisissent dans la variable [Rechercher](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#quick-search) de la boîte. Avec chaque caractère saisi, la variable [!DNL popover] est mis à jour avec des suggestions de produits et des images miniatures des principaux résultats de recherche.

[!DNL Live Search] renvoie les résultats d’une requête de deux caractères ou plus. Pour une correspondance partielle, le nombre maximal de caractères par mot est de 20. Le nombre de caractères d’une requête &quot;Rechercher lorsque vous tapez&quot; n’est pas configurable.

## Attributs pouvant faire l’objet d’une recherche

Pour produire des résultats très ciblés, passez en revue le jeu de [searchable](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) (`searchable=true`) des attributs de produit. Pour garantir la pertinence, ne autorisez la recherche des attributs que s’ils contiennent du contenu ayant une signification claire et concise. Évitez d’utiliser des attributs contenant un texte plus long et moins précis, comme `description`, qui, bien que la recherche soit activée par défaut, peut réduire la précision des résultats de recherche. Par exemple, si une personne recherche &quot;shorts&quot; et qu’il y a des chemises avec une description qui inclut le terme &quot;manches courtes&quot;, les chemises seront incluses dans les résultats de la recherche.

Les attributs suivants peuvent toujours faire l’objet de recherches :

* `sku`
* `name`
* `categories`

[[!DNL Live Search popover]](assets/storefront-search-as-you-type.png)

## [!DNL Popover] taille de page

Taille de page de la variable [!DNL popover] détermine le nombre de lignes de produits à terminer automatiquement qui peuvent être renvoyées. Auparavant, la taille de la page était codée en dur comme six lignes. Toutefois, la variable `page_size` est désormais un paramètre qui peut être configuré à partir de la variable *Administration*. Au cours de l’installation de Live Search, la variable `page_size` change en fonction de la valeur actuelle de la variable [Recherche catalogue](https://experienceleague.adobe.com/docs/commerce-admin/config/catalog/catalog.html) - `Autocomplete Limit` .

Par défaut, la valeur Recherche catalogue - Limite de saisie automatique est définie sur huit lignes (ou lignes). Pour modifier la taille de page de la variable [!DNL popover], procédez comme suit :

1. Sur le *Administration* barre latérale, accédez à **Magasins** > Paramètres > **Configuration**.
1. Dans le panneau de gauche, développez **Catalogue** et choisissez **Catalogue** dans la liste des paramètres.
1. Développez l’objet *Recherche catalogue* .
1. Définissez la variable **Limite de saisie automatique** au nombre de lignes que vous souhaitez autoriser dans la variable [!DNL popover].
1. Une fois l’opération terminée, cliquez sur **Enregistrer la configuration**.

## Service de catalogue

Le [Service de catalogue pour Adobe Commerce](../catalog-service/overview.md) L’extension fournit des données de catalogue de modèles d’affichage enrichies pour générer rapidement et intégralement des expériences storefront liées aux produits. Le service de catalogue peut être utilisé conjointement avec Live Search pour fournir des fonctionnalités qui ne sont actuellement pas prises en charge par l’extension native :

* Échantillons de couleurs
* Attributs étendus
* D’autres informations sur les produits peuvent être introduites

Les marchands peuvent personnaliser et étendre des widgets ou des éléments de storefront à l’aide du service de catalogue, mais cela n’a pas de portée pour l’équipe d’assistance d’Adobe.

## Limites

* Le [!DNL Live Search] [!DNL storefront popover] est disponible uniquement pour les magasins qui utilisent la variable *Luma* ou un thème personnalisé basé sur *Luma*. Le chemin de navigation de la page des résultats de recherche ne comporte pas *Lume* style.
* Le [!DNL popover] ne prend pas en charge la variable *Vide* thème. Voir [Style [!DNL Popover] Éléments](storefront-popover-styling.md) pour en savoir plus.
* Le [!DNL popover] n’est pas pris en charge dans le formulaire de commande rapide.
* Les listes blanches et les comparaisons de produits ne sont pas prises en charge.
* Seule la devise de base est prise en charge.
