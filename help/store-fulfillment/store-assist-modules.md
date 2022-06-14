---
title: '"Workflows d’exécution de l’assistant de stockage"'
description: '"Découvrez les modules Pick, Stage, Hand-Off et Commandes disponibles dans l’application d’aide à la boutique. Ces modules permettent d’exécuter de bout en bout le workflow d’exécution des magasins pour les commandes BOPIS. Store Associates utilise ces modules pour gérer et envoyer des commandes de nettoyage de magasin aux clients.'
role: User
level: Intermediate
source-git-commit: 4ea03b3be11056526adc42d875b1e26a24736d15
workflow-type: tm+mt
source-wordcount: '790'
ht-degree: 0%

---


# Workflows d’assistance de magasin

L’application d’assistance Boutique fournit à Store Associates quatre modules pour gérer le processus d’exécution en magasin pour l’achat en ligne et la prise en charge des commandes en magasin :

**[Pick](#pick-module)**: obtenez une visibilité complète de tous les articles commandés et des outils pour vous assurer que les bons articles et les bonnes quantités sont sélectionnés. Les associés de magasin peuvent sélectionner une ou plusieurs commandes simultanément pour une plus grande efficacité.

**[Évaluation](#stage-module)**: entrez l’emplacement où les commandes sont passées pendant que les clients se rendent dans le magasin afin que les associés du magasin puissent les trouver facilement pour le transfert de commande.

**[Main désactivée](#hand-off)**: Recevez des notifications en temps réel après l’arrivée des clients dans le magasin afin de minimiser le temps d’attente et de passer les commandes en toute transparence.

**[Commandes](#orders-module)**: affichez la liste de toutes les commandes passées pour un magasin afin que chacun connaisse le nombre de commandes et l’état de chaque commande.

>[!NOTE]
>
>Pour que Store Associates puisse utiliser l’application d’assistance, un administrateur doit renseigner la variable [processus de configuration de l’application](app-setup.md).

## Choisir le module

Le module Pick permet aux associés de magasin de rechercher et d’analyser les articles commandés par le client et de les classer pour récupération. Vous pouvez voir le nombre de commandes en retard et commencer immédiatement à les sélectionner. Vous pouvez également choisir d’autres commandes à sélectionner en premier. Les commandes sont triées par délai de livraison, avec d’abord les commandes en retard. Les associés au magasin peuvent sélectionner les commandes qu’ils souhaitent sélectionner dans l’ordre requis pour vos opérations.

Vos associés peuvent également choisir de sélectionner une commande à la fois ou plusieurs commandes en même temps.

Lors de la sélection, les associés au magasin affichent une liste de tous les articles à sélectionner pour chaque commande, leurs quantités, leur prix et la description du produit de votre catalogue. Une barre de progression s’affiche pour les aider à naviguer dans l’assistant de magasin lors du choix des commandes.

Une fois que vos associés commencent à sélectionner les éléments à sélectionner, toutes les informations appropriées s’affichent, telles que : taille, couleur, quantité, prix, description, ajustement et SKU/UPC. Deux actions sont disponibles pour les associés lors du choix des commandes :

- Indique que l’article est introuvable et déclenche un remboursement.
- Analysez le code à barres sur l’élément. L’analyse a pour but de vérifier qu’ils ont sélectionné l’élément correct. Si la caméra ne parvient pas à lire le code à barres, les associés de magasin doivent saisir manuellement le SKU de l’élément qu’ils ont sélectionné.

Si les associés ne parviennent pas à trouver un élément, ils peuvent l’ignorer et y revenir ultérieurement.  Le remboursement mentionné ci-dessus n&#39;est émis qu&#39;une fois qu&#39;ils ont terminé leur étape de la commande.

## Module d’évaluation

Le module d’évaluation indique l’emplacement de la commande mise en sacs jusqu’à ce que le client arrive pour la récupérer. La définition de cet emplacement est une étape essentielle pour éviter la perte de commandes lorsque les associés du magasin terminent leur équipe avant l’arrivée du client ou si vous avez plusieurs commandes. Dans les deux cas, il est conçu pour vous aider à trouver rapidement le bon ordre avec toutes les informations pertinentes à son sujet.

Vous pouvez utiliser une barre de texte de formulaire libre pour indiquer l’emplacement de la commande : sous le comptoir, dans la pièce arrière ou à l’emplacement B3, le tout en fonction de vos opérations.

Vous pouvez également facilement mettre à jour l’emplacement d’évaluation dans l’application, si vos associés ont besoin de le placer ailleurs.

## Module de désactivation de la main

Le [!UICONTROL Hand Off] indique les clients qui se sont connectés pour reprendre leurs commandes, et où leurs commandes sont mises en scène et les attendent. Les clients peuvent prendre des commandes soit dans le magasin soit dans le parking à l&#39;extérieur ou au bord du trottoir. Les informations sur leur emplacement exact sont présentées dans ce module une fois qu’elles sont connectées.

Une fois que vous avez sélectionné une commande prête à être remise au client. Tout le monde peut consulter les informations sur la commande, y compris les éléments introuvables, l’emplacement d’attente du client, le temps d’attente, l’emplacement d’évaluation de la commande et, le cas échéant, le numéro de téléphone du client.

Le client a peut-être choisi une autre personne pour passer la commande. Dans ce cas, le nom et les coordonnées de la personne censée choisir la commande s’affichent.

Lors de la remise de la commande au client, l’associé du magasin doit accepter la commande ou rejeter certains articles. Une fois que le client est satisfait, il doit signer la commande sur l’appareil de votre associé, si une signature de votre société nécessite une signature.

Si les clients arrivent sans s’enregistrer, vos associés peuvent les archiver manuellement.

## Module Commandes

Le module Commandes affiche toutes les commandes existantes et leur état. Lorsqu’un client appelle pour vérifier sa commande, Store Associates peut trouver rapidement les informations en recherchant le numéro ou en effectuant une recherche à partir du module Commandes.
