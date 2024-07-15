---
title: "Paramètres"
description: "Configurez les paramètres du service  [!DNL Live Search] ."
exl-id: a0b63116-4b8f-490c-a54e-e21f1b02b634
source-git-commit: ba7e92d5b3aaabe6a8c71f86b0e4eab38aec9adf
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# Paramètres

Utilisez l’espace de travail *Paramètres* pour configurer les plages et les intervalles de facettes de prix, ainsi que la langue par défaut de l’index.

La facette des prix indique le nombre de groupes de prix et la manière dont les valeurs de prix sont réparties entre eux.

Le paramètre Language indique au service [!DNL Live Search] la langue à attendre lors de l’écriture de l’index.

![Paramètres](assets/settings.png)

## Facturation des prix

Vous pouvez indiquer le nombre de groupes de prix et la manière dont les valeurs de prix sont réparties. Chaque période de prix chevauche le groupe précédent d’une unité. Par exemple, cinq groupes avec un intervalle de 20 créent les plages de prix suivantes : 0-20, 20-40, 40-60, 60-80 et >80. Si le catalogue ne contient pas suffisamment de produits pour remplir toutes les plages définies, l’affichage des groupes disponibles est adapté en conséquence. Par exemple : 0-20, 60-80, >80.

1. Dans l’administrateur, accédez à **Marketing** > *SEO &amp; Search* > **[!DNL Live Search]**.
1. Sur l’espace de travail **Settings** sous *Price faceting*, procédez comme suit :
   * Saisissez le **Nombre de sélections**, ou les groupements de prix à mettre à disposition. Il est possible de définir jusqu’à 50 groupements de prix.
   * Entrez la **valeur d&#39;intervalle** ou la plage de prix pour chaque groupe. La valeur maximale est 10 000.
1. Cliquez sur **Enregistrer**.

   Il faut environ 15 minutes pour que les paramètres mis à jour soient disponibles dans le storefront.

### Descriptions des champs

| Champ | Description |
|--- |--- |
| Nombre de sélections | Indique le nombre de groupements de plages de prix pouvant être utilisés comme filtres de recherche dans le storefront. Valeur par défaut : 8, Valeur maximale : 50 |
| Valeur d&#39;intervalle | Indique l’intervalle de prix pour chaque groupe. Par exemple, cinq sélections avec une valeur d’intervalle de 20 créent cinq groupes de 0 à 20, 20 à 40, 40 à 60, 60 à 80 et >80. Valeur par défaut : 5, Valeur maximale : 10 000 |

## Langue

Le paramètre Langue indique à [!DNL Live Search] la langue à attendre lors de la lecture du catalogue et de l’écriture de l’index.

Les langues ont différents ensembles de règles grammaticales : la séparation des mots, les tenses de verbe et les formulaires de mots, par exemple.
Le paramètre Langue garantit que le jeu correct de règles est appliqué au mécanisme d’indexation.

Définissez le paramètre Langue sur la langue principale du catalogue. Lorsque vous modifiez la langue de l’index, il peut s’écouler entre 5 et 60 minutes avant que la modification du storefront ne soit reflétée, selon la taille et la complexité du catalogue.

| Langue | Code |
|----|----|
| Arabe | ar |
| Arménien | hy |
| Basque | eu |
| Bengali | bn |
| Brésilien | pt-br |
| Bulgare | bg |
| Catalan | ca |
| Chinois (simplifié) | zh-cn |
| Chinois (traditionnel) | zh-tw |
| Tchèque | cs |
| Danois | da |
| Néerlandais | nl |
| Anglais | en |
| Estonien | et |
| Finnois | fi |
| Français | fr |
| Galicien | gl |
| Allemand | de |
| Grec | el |
| Hindi | hi |
| Hongrois | hu |
| Indonésien | id |
| Irlandais | ga |
| Italien | it |
| Japonais (Katakana) | ja |
| Coréen | ko |
| Letton | lv |
| Lituanien | lt |
| Norvégien | non |
| Perse | fa |
| Portuge | pt |
| Roumain | ro |
| Russe | ru |
| Sorani | ku |
| Espagnol | es |
| Suédois | sv |
| Turc | tr |
| Thaï | th |
