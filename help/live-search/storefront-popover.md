---
title: Fenêtre contextuelle Storefront
description: La fenêtre contextuelle de recherche en direct renvoie dynamiquement les produits suggérés et les miniatures.
exl-id: 88fdc3ed-b606-40de-94b7-435be09c4072
source-git-commit: 10cea4389d685ce0e26b083872b13a1cd19ba2af
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# Fenêtre contextuelle Storefront

When [!DNL Live Search] is [installé](install.md), une fenêtre contextuelle s’affiche dans le storefront lorsque les clients saisissent dans la variable [Rechercher](https://docs.magento.com/user-guide/catalog/search-quick.html) de la boîte. Avec chaque caractère saisi, la fenêtre contextuelle est mise à jour avec les produits suggérés et les images miniatures des principaux résultats de recherche.

[!DNL Live Search] renvoie les résultats d’une requête de deux caractères ou plus. Pour une correspondance partielle, le nombre maximal de caractères par mot est de 20. Le nombre de caractères d’une requête &quot;Rechercher lorsque vous tapez&quot; n’est pas configurable.

>[!NOTE]
>
>Le [!DNL Live Search] storefront apparaît uniquement pour les magasins qui utilisent la variable *Luma* ou un thème personnalisé basé sur *Luma*. Le *Luma* est inclus dans la variable [!DNL Commerce] données d’exemple. La fenêtre contextuelle ne prend pas en charge la variable *Vide* thème. Voir [Utilisation d’un thème modifié](#working-with-modified-theme) pour plus d’informations.

## Attributs pouvant faire l’objet d’une recherche

Pour produire des résultats très ciblés, passez en revue le jeu de [searchable](https://docs.magento.com/user-guide/stores/attributes-product.html#storefront-properties) (`searchable=true`) des attributs de produit. Pour garantir la pertinence, ne autorisez la recherche des attributs que s’ils contiennent du contenu ayant une signification claire et concise. Évitez d’utiliser des attributs contenant un texte plus long et moins précis, comme `description`, qui, bien que la recherche soit activée par défaut, peut réduire la précision des résultats de recherche. Par exemple, si une personne recherche &quot;shorts&quot; et qu’il y a des chemises avec une description qui inclut le terme &quot;manches courtes&quot;, les chemises seront incluses dans les résultats de la recherche.

Les attributs suivants peuvent toujours faire l’objet de recherches :

* `sku`
* `name`
* `categories`

![Fenêtre contextuelle de recherche en direct](assets/storefront-search-as-you-type.png)

## Taille de page de fenêtre contextuelle

La taille de page de la fenêtre contextuelle détermine le nombre de lignes de produits auto-complétés pouvant être renvoyées. Auparavant, la taille de la page était codée en dur comme six lignes. Toutefois, la variable `page_size` est désormais un paramètre qui peut être configuré à partir de la variable *Administration*. Au cours de l’installation de Live Search, la variable `page_size` change en fonction de la valeur actuelle de la variable [Recherche catalogue](https://docs.magento.com/user-guide/configuration/catalog/catalog.html#catalog-search) - `Autocomplete Limit` .

Par défaut, la valeur Recherche catalogue - Limite de saisie automatique est définie sur huit lignes (ou lignes). Pour modifier la taille de page de la fenêtre contextuelle, procédez comme suit :

1. Sur le *Administration* barre latérale, accédez à **Magasins** > Paramètres > **Configuration**.
1. Dans le panneau de gauche, développez **Catalogue** et choisissez **Catalogue** dans la liste des paramètres.
1. Développez l’objet *Recherche catalogue* .
1. Définissez la variable **Limite de saisie automatique** au nombre de lignes que vous souhaitez autoriser dans la fenêtre contextuelle.
1. Une fois l’opération terminée, cliquez sur **Enregistrer la configuration**.
