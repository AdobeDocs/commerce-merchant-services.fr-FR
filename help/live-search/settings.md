---
title: "[!DNL Live Search] Paramètres"
description: "Configurez les paramètres de la variable [!DNL Live Search] service."
exl-id: a0b63116-4b8f-490c-a54e-e21f1b02b634
source-git-commit: eefae3c849545062012cea1a7092c27f7df56b58
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 0%

---

# Paramètres

Utilisez la variable *Paramètres* pour configurer les plages de facettes de prix et les intervalles, ainsi que la langue par défaut de l’index.

La facette des prix indique le nombre de groupes de prix et la manière dont les valeurs de prix sont réparties entre eux.

Les paramètres de langue indiquent la variable [!DNL Live Search] service de la langue à attendre lors de l’écriture de l’index.

![Paramètres](assets/settings.png)

## Facturation des prix

Vous pouvez indiquer le nombre de groupes de prix et la manière dont les valeurs de prix sont réparties. Chaque période de prix chevauche le groupe précédent d’une unité. Par exemple, cinq groupes avec un intervalle de 20 créent les plages de prix suivantes : 0-20, 20-40, 40-60, 60-80 et >80. Si le catalogue ne contient pas suffisamment de produits pour remplir toutes les plages définies, l’affichage des groupes disponibles est adapté en conséquence. Par exemple : 0-20, 60-80, >80.

1. Dans Admin, accédez à **Marketing** > *SEO &amp; Search* > **[!DNL Live Search]**.
1. Sur le **Paramètres** sous *Facturation des prix*, procédez comme suit :
   * Saisissez le **Nombre de sélections**, ou des groupements de prix à mettre à disposition. Il est possible de définir jusqu’à 50 groupements de prix.
   * Saisissez le **Valeur d&#39;intervalle**, ou plage de prix pour chaque groupe. La valeur maximale est 10 000.
1. Cliquez sur **Enregistrer**.

   Il faut environ 15 minutes pour que les paramètres mis à jour soient disponibles dans le storefront.

### Descriptions des champs

| Champ | Description |
|--- |--- |
| Nombre de sélections | Indique le nombre de groupements de plages de prix pouvant être utilisés comme filtres de recherche dans le storefront. Valeur par défaut : 8, Valeur maximale : 50 |
| Valeur d&#39;intervalle | Indique l’intervalle de prix pour chaque groupe. Par exemple, cinq sélections avec une valeur d’intervalle de 20 créent cinq groupes de 0 à 20, 20 à 40, 40 à 60, 60 à 80 et >80. Valeur par défaut : 5, Valeur maximale : 10 000 |

<!-- ## Language

The Language setting tells [!DNL Live Search] which language to expect when reading the catalog and writing the index. 

Languages have different sets of rules for grammar: how words are separated, verb tenses and synonyms, for example.
The Language setting ensures that the correct set of rules are applied to the indexing mechanism.

The Language settings should be set to the primary language of the catalog. -->
