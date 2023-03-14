---
title: "Paramètres des configurations de commerce et [!DNL Live Search] "
description: "Décrit les paramètres de configuration d’Adobe Commerce qui [!DNL Live Search] peut lire."
source-git-commit: 10edbb6127405d45c06d4c8ffc89d92a6ca061c3
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 0%

---

# [!DNL Live Search] et Paramètres de configuration Adobe Commerce

Il existe des paramètres de configuration de Commerce qui [!DNL Live Search] prend en charge . Cette rubrique répertorie ces valeurs de configuration.

## Valeurs de configuration prises en charge

| Paramètre de configuration Commerce | Pris en charge par Popover | Pris en charge par l’adaptateur |
|---|---|---|
| Magasins -> Configuration -> Catalogue -> Catalogue -> Recherche catalogue -> Longueur minimale de requête | Oui | Oui |
| Magasins -> Configuration -> Catalogue -> Inventaire -> Afficher les produits en rupture de stock | Oui avec v2.0.4+ | Oui avec v2.0.4+ |
| Magasins -> Configuration -> Général -> Configuration de devise -> Options de devise -> Devise de base | Oui | Oui |

## Valeurs de configuration non prises en charge

[!DNL Live Search] ne peut pas lire toutes les valeurs de configuration. Ce tableau répertorie les valeurs qui peuvent intéresser davantage les développeurs.

| Paramètre de configuration du Magento | Remarques |
|---|---|
| Magasins -> Configuration -> Catalogue -> Storefront -> Mode Liste | Les rendus sont corrects, mais les événements ne sont pas envoyés pour certaines interactions de page. |
| Magasins -> Configuration -> Catalogue -> Storefront -> Autoriser tous les produits par page | Non mis en oeuvre ; envoie une requête au service de recherche sans taille de page et [!DNL Live Search] renvoie une taille de page par défaut de 20 |
| Magasins -> Configuration -> Catalogue -> Catalogue -> Recherche catalogue -> Longueur maximale de requête | Non mis en oeuvre ; Search Services accepte jusqu’à 255 caractères |
| Magasins -> Configuration -> Général -> Configuration de devise -> Options de devise -> Devise d’affichage par défaut | Non mis en oeuvre ; [!DNL Live Search] a uniquement accès à la devise de base ; |
| Configuration -> Ventes -> Taxe -> Paramètres d’affichage des prix -> Afficher les prix des produits dans un catalogue |  |
