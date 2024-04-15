---
title: Paramètres des configurations Commerce et [!DNL Live Search] '
description: Décrit les paramètres de configuration Adobe Commerce qui [!DNL Live Search] peuvent lire.
exl-id: a4e9e2dd-e912-4ced-a44a-091ac5334e50
features: Services, Search, Configuration
source-git-commit: d1cd70e66e616c052418c719f6da23b010a22241
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 0%

---

# [!DNL Live Search] et Paramètres de configuration Adobe Commerce

Il existe des paramètres de configuration Commerce qui [!DNL Live Search] prend en charge . Cette rubrique répertorie ces valeurs de configuration.

## Valeurs de configuration compatibles

| Paramètre de configuration Commerce | Pris en charge par Popover | Pris en charge par l’adaptateur |
|---|---|---|
| Magasins > Configuration > Catalogue > Catalogue > Recherche catalogue > Autoriser tous les produits par longueur de page | Oui. 500 produits max | Oui. 500 produits max |
| Magasins > Configuration > Catalogue > Recherche catalogue > Longueur minimale de requête | Oui | Oui |
| Magasins > Configuration > Catalogue > Recherche catalogue > Produits par page sur les valeurs autorisées de la grille | Oui | Oui |
| Magasins > Configuration > Catalogue > Recherche catalogue > Produits par page sur la valeur par défaut de la grille | Oui. 500 produits max | Oui. 500 produits max |
| Magasins > Configuration > Catalogue > Inventaire > Afficher les produits en rupture de stock | Oui avec v2.0.4+ | Oui avec v2.0.4+ |
| Magasins > Configuration > Devise > Devise d’affichage par défaut | Oui avec 3.1.0+ | Oui avec 3.1.0+ |
| Magasins > Configuration > Général > Configuration de devise > Options de devise > Devise de base | Oui | Oui |

Les prix dans la page de liste de produits du widget et la fenêtre contextuelle sont désormais convertis en devise d’affichage par défaut à l’aide des taux de devise configurés.

## Termes de recherche

[!DNL Live Search] prend [redirections de termes de recherche](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-terms.html) sur les implémentations dans lesquelles Adobe Commerce gère le routage : Luma et d’autres thèmes basés sur php.

## Valeurs de configuration non prises en charge

[!DNL Live Search] ne peut pas lire toutes les valeurs de configuration. Ce tableau répertorie les valeurs qui peuvent intéresser davantage les développeurs.

| Paramètre de configuration Commerce | Remarques |
|---|---|
| Magasins > Configuration > Catalogue > Magasin > Mode Liste | Les rendus sont corrects, mais les événements ne sont pas envoyés pour certaines interactions de page. |
| Magasins > Configuration > Catalogue > Catalogue > Recherche catalogue > Longueur maximale de requête | Non implémenté ; les services de recherche acceptent jusqu’à 255 caractères |
| Configuration > Ventes > Taxe > Paramètres d’affichage des prix > Afficher les prix des produits dans le catalogue |  |
| Magasins > Configuration > Catalogue > Magasin > Liste de produits Trier par | Ne s’applique pas à la variable [!DNL Live Search] [Widget de page de liste de produits](plp-styling.md) |
