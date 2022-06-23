---
title: Exigences d’exécution du magasin
description: Conditions requises pour la configuration et l’intégration de la variable [!DNL Store Fulfillment solution].
role: User, Admin
level: Intermediate
exl-id: f9e05049-5904-4f6c-b45d-9f81fbc76b69
source-git-commit: 421c90f4c8bd687216cd48c72f30301a32115522
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 2%

---

# Exigences d’exécution de la boutique pour Adobe Commerce

Pour installer et activer la solution d’exécution de magasin pour Adobe Commerce, vous devez répondre aux exigences techniques et métier suivantes.

## Exigences en matière de version de plateforme et de logiciel

Le [!DNL Store Fulfillment] La solution est disponible pour les clients Adobe Commerce sur les plateformes suivantes.

- Adobe Commerce sur l’infrastructure cloud (ECE)
- Adobe Commerce On-Premise (EE)

La solution Store Fulfillment est compatible avec les versions logicielles suivantes.

**Compatibilité logicielle**

| **Logiciels** | **Version minimale** | **Version maximale** |
|----------------|---------------------|---------------------|
| Adobe Commerce | 2.4.0 | 2.4.4 |
| Compositeur | 1.x | 2.x |
| MariaDB | 10.2 | 10.4 |
| MySQL | 5,7 | 8,0 |
| PHP | 7,4 | 8.1 |

Pour connaître les exigences détaillées, consultez Adobe Commerce [Configuration requise](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html) dans la documentation destinée aux développeurs.

## Exigences de l’application d’assistance à la boutique

Le processus de bout en bout de gestion des commandes de saut de magasin est géré via l’application d’assistance Boutique installée sur les périphériques mobiles. Ces appareils, fournis par le détaillant ou par les employés du magasin à l’aide de leurs smartphones personnels, doivent répondre aux exigences suivantes :

**Configuration minimale requise pour le système d’exploitation**

- Android 6
- iOS 12

**Configuration matérielle requise**

- 1 Go de RAM
- 600 Mo d’espace disque disponible

## Exigences commerciales

Votre entreprise doit satisfaire aux critères minimaux suivants pour mettre en oeuvre la solution d’exécution de magasin.

- Entreprises basées aux États-Unis uniquement

- Ventilateurs B2C, fabricants CPG vendant D2C ou distributeurs vendant D2C ou aux petites entreprises

- Au moins un magasin ou entrepôt physique

- Gestion de l’inventaire de vos produits avec Inventory management pour Adobe Commerce (alias MSI)

- Capacité à syndiquer l’inventaire des commerçants

- Disponibilité du Wi-Fi dans tous les emplacements qui prennent en charge la solution Store Fulfillment : Vitesse Internet minimale de 3 Mbit/s

- Les associés de magasin et d’entrepôt ont accès aux appareils mobiles iOS ou Android au cours de leurs équipes, personnels ou fournis par le marchand.

- Les produits gérés à l’aide de la solution d’exécution de magasin doivent posséder des attributs de produit qui incluent un SKU ou un code de produit UPC.
