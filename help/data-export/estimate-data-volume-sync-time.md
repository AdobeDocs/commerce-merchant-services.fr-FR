---
title: Estimation du volume des données et du temps de transmission
description: Découvrez comment estimer le volume des données et le temps de transmission requis par l’outil  [!DNL data export] pour synchroniser les données de flux entre Adobe Commerce et les services connectés.
role: Admin, Developer
exl-id: 51ea98fd-cf90-44bd-a639-992bfc7f3eca
source-git-commit: 7e33b1d5dfc825f8a4d252bcfcbd4f591e337aed
workflow-type: tm+mt
source-wordcount: '559'
ht-degree: 0%

---

# Estimation du volume des données et du temps de transmission pour la synchronisation des données

Adobe recommande d’estimer le volume des données et le temps de synchronisation avant de démarrer toute synchronisation des flux de données afin de garantir une planification fluide et d’éviter les perturbations dans les opérations du site. Cette estimation est importante lors de la planification des synchronisations initiales ou des mises à jour de catalogue à grande échelle, telles que les changements de prix en masse.

Par défaut, l’outil d’exportation de données traite les données en mode mono-thread avec une taille de lot par défaut. Avec la configuration par défaut, il n’existe aucune mise en parallèle du processus d’envoi du flux. En outre, ce composant accepte les demandes par seconde (RPS) qui se traduisent par ce qui suit :

- Jusqu’à 10 000 produits par minute lorsqu’un produit est un SKU avec des attributs dans un storeview spécifique
- Jusqu&#39;à 50 000 prix par minute

Les facteurs suivants affectent le temps de transmission des données lors de la synchronisation.

- Le nombre de threads est défini sur 1 (par défaut).
- La taille du lot est définie sur _100_ pour tous les flux, à l’exception du flux `prices`, où elle est définie sur _500_.
- Le taux d’acceptation du flux est de 2 demandes par seconde.
- Tous les produits sont affectés à tous les sites web existants.
- Pour les scénarios de calcul des prix, des prix spéciaux et groupés sont attribués à tous les produits.


## Calcul de la transmission des données par flux

Utilisez les valeurs et formules du tableau suivant pour calculer le volume des données et le temps de synchronisation pour chaque flux de données.

>[!NOTE]
>
>Ces calculs sont basés sur un taux de transmission de 2 demandes par seconde. La vitesse est basée sur le temps requis pour la collecte et l’envoi des données. La vitesse de transmission réelle varie en fonction de la taille de charge utile de la requête et de la charge actuelle sur le serveur d’applications Commerce.

| Flux | Exemple de données | Formule de calcul des enregistrements | Nombre de requêtes prédit | Heure de resynchronisation prévue |
| --- | --- | --- | --- | --- |
| Produits | Produits (P) : 10000, Vues des magasins (SV) : 4 | P * SV = 40000 | 40 000 / Taille du lot (100) = 400 demandes | (400 demandes * 0,5 seconde par demande) / 60 = 3,3 minutes |
| Catégories | Catégories (C) : 500, Vues magasins (SV) : 4 | C * SV = 2 000 | 2 000 / Taille du lot (100) = 20 demandes | (20 demandes * 0,5 seconde par demande) / 60 = 0,1 minute (4 secondes) |
| Prix | Produits (P) : 10000, Groupes clients (CG) : 6 (par exemple, prix unique dans le catalogue partagé), Sites web (WS) : 2 | P \* WS * CG = 120000 | 120000 / Taille du lot (500) = 240 demandes | (240 demandes * 0,5 seconde par demande) / 60 = 2 minutes |
| Remplacements de produits | Produits avec des autorisations ou dans un catalogue partagé (P) : 10000, Groupes clients affectés (CG) : 5, Sites web attribués WS : 2 | P \* WS * CG = 100000 | 100000 / Taille du lot (100) = 1 000 demandes | (1 000 demandes * 0,5 seconde par demande) / 60 = 8,3 minutes |
| Variantes de produit | Variantes (produits enfants) affectées aux produits configurables (PV) : 100000 | PV = 100000 | 100000 / Taille du lot (100) = 1 000 demandes | (1 000 demandes * 0,5 seconde par demande) / 60 = 8,3 minutes |
| Autorisations de catégorie | Comptage de toutes les autorisations de catégorie + 4 enregistrements de secours (CP) : 10 000 | CP = 10000 | 10 000 / Taille du lot (100) = 100 demandes | (100 demandes * 0,5 seconde par demande) / 60 = 0,8 minute (50 secondes) |
| État du stock | Produits (P) : 10 000, Stocks de produits affectés à (S) : 5 (en supposant que chaque produit soit affecté à chaque stock) | P * S = 50 000 | 50 000 / Taille du lot (100) = 500 demandes | (500 demandes * 0,5 seconde par demande) / 60 = 4,2 minutes |
| Commandes de ventes | Tous les enregistrements de commande (y compris les factures, les envois, etc.) (SO) : 10000 | SO = 10000 | 10 000 / Taille du lot (100) = 100 demandes | (100 demandes * 0,5 seconde par demande) / 60 = 0,8 minute (50 secondes) |
