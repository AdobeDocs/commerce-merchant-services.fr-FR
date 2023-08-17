---
title: Exigences d’exécution du magasin
description: Conditions requises pour la configuration et l’intégration de la variable [!DNL Store Fulfillment solution].
role: Leader, Admin, Developer
level: Intermediate
feature: Shipping/Delivery, Install
exl-id: f9e05049-5904-4f6c-b45d-9f81fbc76b69
source-git-commit: 36b57648e156ead801764f3ee4e5e6a0f3245fe6
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 2%

---

# Conditions requises pour l’exécution du magasin pour Adobe Commerce

Les sections suivantes décrivent les exigences techniques et métier de l’installation et de l’activation de la solution d’exécution de magasin pour Adobe Commerce.

## Exigences en matière de version de plateforme et de logiciel

La variable [!DNL Store Fulfillment] La solution est disponible pour les clients Adobe Commerce sur les plateformes suivantes.

- Adobe Commerce sur l’infrastructure cloud (ECE)
- Adobe Commerce On-Premise (EE)

La solution Store Fulfillment est compatible avec les versions logicielles répertoriées dans la section *Compatibilité logicielle* table.

**Compatibilité logicielle**

| **Logiciels** | **Version minimale** | **Version maximale** |
|----------------|---------------------|---------------------|
| Adobe Commerce | 2.4.0 | 2.4.5 |
| Compositeur | 1.x | 2.x |
| MariaDB | 10.2 | 10.4 |
| MySQL | 5.7 | 8.0 |
| PHP | 7.4 | 8.1 |

Pour connaître les exigences détaillées, consultez Adobe Commerce [Configuration requise](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html) dans le *Guide d’installation d’Adobe Commerce*.

## Exigences de l’application d’assistance à la boutique

Le processus de bout en bout de gestion des commandes de saut de magasin est géré via l’application d’assistance Boutique installée sur les périphériques mobiles. Ces appareils, fournis par le détaillant ou par les employés du magasin à l’aide de leurs smartphones personnels, doivent répondre aux exigences suivantes :

**Configuration requise du système d’exploitation**

- Android 6
- iOS 12

**Configuration matérielle requise**

- 1 Go de RAM
- 600 Mo d’espace disque disponible

## Exigences commerciales

Votre entreprise doit satisfaire aux critères minimaux suivants pour mettre en oeuvre la solution d’exécution de magasin :

- Entreprises basées aux États-Unis uniquement

- Entreprises avec des consommateurs (B2C) Détaillants, Consommateurs de marchandises emballées (CPG) Fabricants qui vendent directement aux consommateurs (D2C) ou distributeurs qui vendent directement aux consommateurs ou aux petites entreprises

- Au moins un magasin ou entrepôt physique

- Gestion de l’inventaire de vos produits avec Inventory management pour Adobe Commerce (alias MSI)

- Capacité à syndiquer l’inventaire des commerçants

- Disponibilité du Wi-Fi en magasin à tous les emplacements qui prennent en charge la solution Store Fulfillment : vitesse Internet minimale de 3 Mbit/s.

- Les associés de magasin et d’entrepôt ont accès aux appareils mobiles iOS ou Android au cours de leurs équipes, personnels ou fournis par le marchand.

- Les produits gérés à l’aide de la solution d’exécution de magasin doivent posséder des attributs de produit qui incluent un SKU ou un code de produit UPC.
