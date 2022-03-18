---
title: Fenêtre contextuelle Storefront
description: La fenêtre contextuelle de recherche en direct renvoie dynamiquement les produits suggérés et les miniatures.
exl-id: 88fdc3ed-b606-40de-94b7-435be09c4072
source-git-commit: 7402e97f53b71e488d860215487f4809572b7e6f
workflow-type: tm+mt
source-wordcount: '239'
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
