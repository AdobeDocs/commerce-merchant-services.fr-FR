---
title: Présentation de la configuration de l’exécution de magasin
description: Découvrez les catégories de paramètres de configuration de l’administrateur disponibles pour la solution d’exécution de magasin et la manière dont elles sont configurées.
role: User, Admin
level: Intermediate
source-git-commit: 4ea03b3be11056526adc42d875b1e26a24736d15
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# Présentation de la configuration pour l’exécution du magasin

Dans l’administrateur Adobe Commerce, les paramètres de configuration des services d’exécution de magasin par Walmart Commerce Technologies sont classés par type.

**Paramètres de configuration d’exécution de magasin par type**

| **Type** | **Description** | **API configurable** |
|--------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------|
| [Configuration générale](enable-general.md) | Intégration générale configurée pour la solution d’exécution de magasin, ses principales fonctionnalités et ses informations d’identification pour se connecter aux services d’exécution. | Non |
| [Configuration des e-mails de ventes](sales-emails.md) | Configurez des modèles d’e-mail supplémentaires pour les notifications client envoyées pendant le processus d’archivage. | Non |
| [Configuration de la boutique marchande](merchant-store-configuration.md) | Configurez des sources Inventory management améliorées en tant que magasins marchands. | Oui |
| [Gestion des stocks de produits](product-stock.md) | Configurez les fonctionnalités et la messagerie du stock commercial disponibles pour les clients. | Oui |
| [Transfert de source Inventory management](inventory-stock-transfer.md) | Configurez un nouveau stock, transférez le stock par défaut. | Oui |
| [Configuration de plusieurs sites web/domaines](multi-site-and-scope-config.md) | Configurez les stocks et les méthodes de diffusion pour plusieurs sites web/portées de magasin. | Non |
| [Configuration du système de processus en arrière-plan](background-processes.md) | Configurez les plannings des processus en arrière-plan utilisés pour synchroniser les données avec les services d’exécution. | Non |
| [Configuration de l’emplacement et du mappage du magasin](store-location-map-provider-setup.md) | Configurer la possibilité d’utiliser un fournisseur de distance pour rechercher des magasins de détail et afficher ces informations dans la carte SLS | Oui |
| [Configuration de l’expérience d’archivage](store-location-map-provider-setup.md) | Configurez la couleur de la voiture et les options de la marque de voiture qui seront disponibles pendant le processus d’archivage. | Oui |
| [Configuration de l’utilisateur](user-setup.md) | Gérez les comptes d’utilisateurs, les rôles et les autorisations des associés de magasin qui utilisent l’application d’aide au magasin. portées. | Oui |
| [Configuration de l’application](app-setup.md) | Vérifiez les configurations disponibles pour l’application d’assistance à la boutique requises pour terminer le processus d’intégration. Ces paramètres ne peuvent pas être configurés à partir de l’administrateur Adobe Commerce. | Oui |


## Utilisation de la référence de configuration

Affichez la référence de configuration pour chaque type de paramètre en sélectionnant le nom du type dans la _Paramètres de configuration d’exécution de magasin par type_ table.

Dans la référence de configuration de chaque type, les détails de configuration sont affichés dans un tableau avec les en-têtes de colonne suivants :

- **Champ** fait référence au nom du champ à configurer

- **Description** fournit des détails importants sur l’objectif et le comportement du champ ;

- **Portée** indique la portée de la configuration Adobe Commerce pour le paramètre (global, site web, magasin).

- **Obligatoire** indique si une valeur doit être définie sur le champ.

À titre de référence technique, vous pouvez également trouver le chemin de configuration interne de chaque champ.
