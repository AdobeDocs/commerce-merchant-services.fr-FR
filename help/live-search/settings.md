---
title: Paramètres de recherche en direct
description: Configurez les plages de facettes de prix et les intervalles pour les facettes de recherche en direct.
exl-id: a0b63116-4b8f-490c-a54e-e21f1b02b634
source-git-commit: 19f0c987ab6b43b6fac1cad266b5fd47a7168e73
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# Paramètres

Utilisez la variable *Paramètres* pour configurer les plages de facettes de prix et les intervalles disponibles en tant que filtres de recherche dans le storefront. Les paramètres de facette de prix sont statiques plutôt que dynamiques et ne sont pas basés sur les résultats de la recherche.
Vous pouvez indiquer le nombre de groupes de prix et la manière dont les valeurs de prix sont réparties. Chaque période de prix chevauche le groupe précédent d’une unité. Par exemple, cinq groupes avec un intervalle de vingt créent les plages de prix suivantes : 0-20, 20-40, 40-60, 60-80 et >80. Si le catalogue ne contient pas suffisamment de produits pour remplir toutes les plages définies, l’affichage des groupes disponibles est adapté en conséquence. Par exemple : 0-20, 60-80, >80.

![Paramètres](assets/settings.png)

## Configuration des groupements de facettes de prix

1. Dans Admin, accédez à **Marketing** > *SEO &amp; Search* > **Recherche en direct**.
1. Sur le **Paramètres** sous *Facturation des prix*, procédez comme suit :
   * Saisissez le **Nombre de sélections**, ou des groupements de prix à mettre à disposition. Il est possible de définir jusqu’à 50 groupements de prix.
   * Saisissez le **Valeur d&#39;intervalle**, ou plage de prix pour chaque groupe. La valeur maximale est 10 000.
1. Cliquez sur **Enregistrer**.
Cela prend environ quinze minutes pour que les paramètres mis à jour soient disponibles dans le storefront.

## Descriptions des champs

| Champ | Description |
|--- |--- |
| Nombre de sélections | Indique le nombre de groupements de plages de prix pouvant être utilisés comme filtres de recherche dans le storefront. Valeur par défaut : 8, Valeur maximale : 50 |
| Valeur d&#39;intervalle | Indique l’intervalle de prix pour chaque groupe. Par exemple, cinq sélections avec une valeur d’intervalle de vingt créent cinq regroupements de 0 à 20, 20 à 40, 40 à 60, 60 à 80 et >80. Valeur par défaut : 5, Valeur maximale : 10 000 |
