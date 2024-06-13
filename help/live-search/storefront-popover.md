---
title: "[!DNL Storefront Popover]"
description: "Le [!DNL Live Search storefront popover] renvoie dynamiquement les produits suggérés et les miniatures."
exl-id: 88fdc3ed-b606-40de-94b7-435be09c4072
source-git-commit: 099a4b9ce3ab71bc3c7ae181be242863a55d0ca9
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# [!DNL Storefront Popover]

When [!DNL Live Search] is [installé](install.md), un [!DNL popover] apparaît dans le storefront lorsque les clients saisissent dans la variable [Rechercher](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#quick-search) de la boîte. Avec chaque caractère saisi, la variable [!DNL popover] est mis à jour avec des suggestions de produits et des images miniatures des principaux résultats de recherche.

[!DNL Live Search] renvoie les résultats d’une requête de deux caractères ou plus. Pour une correspondance partielle, le nombre maximal de caractères par mot est de 20. Le nombre de caractères d’une requête &quot;Rechercher lorsque vous tapez&quot; n’est pas configurable.

Par défaut, [!DNL Live Search] prend [redirections de termes de recherche](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-terms.html).

![[!DNL Live Search popover]](assets/storefront-search-as-you-type.png)

## [!DNL Popover] taille de page

Taille de page de la variable [!DNL popover] détermine le nombre de lignes de produits à terminer automatiquement qui peuvent être renvoyées. Auparavant, la taille de la page était codée en dur comme six lignes. Toutefois, la variable `page_size` est désormais un paramètre qui peut être configuré à partir de la variable *Administration*. Pendant l’installation de Live Search, la variable `page_size` change en fonction de la valeur actuelle de la variable [Recherche catalogue](https://experienceleague.adobe.com/docs/commerce-admin/config/catalog/catalog.html) - `Autocomplete Limit` .

Par défaut, la valeur Recherche catalogue - Limite de saisie automatique est définie sur huit lignes (ou lignes). Pour modifier la taille de page de la variable [!DNL popover], procédez comme suit :

1. Sur le *Administration* barre latérale, accédez à **Magasins** > Paramètres > **Configuration**.
1. Dans le panneau de gauche, développez **Catalogue** et choisissez **Catalogue** dans la liste des paramètres.
1. Développez l’objet *Recherche catalogue* .
1. Définissez la variable **Limite de saisie automatique** au nombre de lignes que vous souhaitez autoriser dans la variable [!DNL popover].
1. Lorsque vous avez terminé, cliquez sur **Enregistrer la configuration**.

## Service de catalogue

La variable [Service de catalogue pour Adobe Commerce](../catalog-service/overview.md) L’extension fournit des données de catalogue de modèles d’affichage enrichies pour générer rapidement et intégralement des expériences storefront liées aux produits. Le service de catalogue peut être utilisé conjointement avec Live Search pour fournir des fonctionnalités qui ne sont actuellement pas prises en charge par l’extension native :

* Attributs étendus
* D’autres informations sur les produits peuvent être introduites

Les marchands peuvent personnaliser et étendre des widgets ou des éléments de storefront à l’aide du service de catalogue, mais cela n’a pas de portée pour l’équipe d’assistance d’Adobe.

## Implémentations sans affichage

Pour les implémentations sans interface utilisateur graphique, il est possible d’installer la fenêtre contextuelle Live Search avec une [package npm](https://www.npmjs.com/package/@magento/ds-livesearch-storefront-utils).

## Limites

* La variable [!DNL Live Search] [!DNL storefront popover] est disponible uniquement pour les magasins qui utilisent la variable *Luma* ou un thème personnalisé basé sur *Luma*. Le chemin de navigation de la page des résultats de recherche ne comporte pas *Luma* style.
* La variable [!DNL popover] ne prend pas en charge la variable *Vide* thème. Voir [Style [!DNL Popover] Éléments](storefront-popover-styling.md) pour en savoir plus.
* La variable [!DNL popover] n’est pas pris en charge dans le formulaire de commande rapide.
* Les listes blanches et les comparaisons de produits ne sont pas prises en charge.
