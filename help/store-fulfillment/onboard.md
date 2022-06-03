---
title: Présentation de l’intégration
description: '"Connectez-vous [!DNL Commerce] à l’instance [!DNL Store Fulfillment Manager] en suivant quelques étapes d’intégration."'
role: User, Admin
level: Intermediate
exl-id: f8e403ac-9bbd-4ea2-b209-9b1a8d1e32a2
source-git-commit: 26d0ddbcbe648b336d527788668caef1f8e688ed
workflow-type: tm+mt
source-wordcount: '553'
ht-degree: 1%

---

# Présentation de l’intégration

Génération d’une boutique intégrée en installant l’extension sur votre instance Commerce et en configurant les connexions API. Ces connexions permettent la communication et la synchronisation des données entre votre instance Commerce, les systèmes tiers pour la gestion des stocks et l’application d’aide au magasin.

Une fois l’intégration terminée, configurez et gérez la solution à partir de l’administrateur Commerce.

![[!DNL Store Fulfillment Service] configuration dans la vue Admin](assets/store-fulfillment-admin-home.png)

## Présentation de l’intégration

1. Installez l’extension Store Fulfillment by Walmart Technologies pour Adobe Commerce.

1. Depuis l’administrateur, activez la solution et effectuez la configuration générale de l’intégration, ses principales fonctionnalités, et remplissez le formulaire d’intégration pour vous connecter aux services d’exécution.

1. Paramétrez les méthodes de diffusion.

1. Configurez des sources comme des magasins physiques et configurez des produits dans votre catalogue.

1. Sélectionnez et configurez les modèles d’email pour gérer la communication client pour les transactions d’achat en ligne, de prise en main en magasin (BOPIS).

1. Créez des utilisateurs et des rôles pour l’application d’aide à la boutique.

1. Configurez les plannings des processus en arrière-plan pour synchroniser les données avec le service d’exécution.

## Conditions

Pour installer, déployer et utiliser la solution, vous devez satisfaire aux exigences suivantes.

* **Informations de compte Commerce**-Installation [!DNL Channel Manager] nécessite une [Compte Commerce](https://docs.magento.com/user-guide/magento/magento-account.html){target=&quot;_blank&quot;}. Vous avez besoin d’un identifiant de compte et d’informations d’identification avec un accès Propriétaire ou Administrateur à la variable [!DNL Adobe Commerce] instance.

* Pour [!DNL Adobe Commerce] sur les projets d’infrastructure cloud, les programmes d’installation doivent disposer d’un accès administrateur au projet Cloud. Voir [Gestion de l’accès des utilisateurs](https://devdocs.magento.com/cloud/project/user-admin.html).

* **Accès à l’archive logicielle Store Fulfillment by Walmart Technologies (fichier .zip) pour l’installation de la solution Store Fulfillment**-Pendant le processus d’intégration et d’activation, votre gestionnaire de compte client vous donnera l’accès en téléchargement au fichier d’installation.

* **Expérience à l’aide du compositeur et de la variable[!DNL Commerce CLI]**—Voir [Installation de l’interface de ligne de commande générale](https://devdocs.magento.com/extensions/install/){target=&quot;_blank&quot;} pour plus d’informations sur l’utilisation de ces outils pour installer et gérer des extensions sur [!DNL Adobe Commerce] et [!DNL Magento Open Source] plateformes.

* [!DNL Inventory Management] extension pour Adobe Commerce et Magento Open Source

   L’extension Inventory management doit être installée et activée sur vos instances Adobe Commerce et Magento Open Source. En règle générale, cette extension est installée et activée par défaut sur Adobe Commerce 2.3.x et versions ultérieures. Pour plus d’informations, voir [Installation d’Inventory management](https://devdocs.magento.com/extensions/inventory-management/) dans la documentation destinée aux développeurs Adobe Commerce.

## Exigences de plateforme et version

Le [!DNL Store Fulfillment] La solution est disponible pour les clients Adobe Commerce sur les plateformes suivantes.

* Adobe Commerce sur l’infrastructure cloud (ECE)
* Adobe Commerce On-Premise (EE)

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

### Conditions requises

Votre entreprise doit satisfaire aux critères minimaux suivants pour mettre en oeuvre la solution d’exécution de magasin.

* Uniquement les entreprises américaines

* Ventilateurs B2C, fabricants de PC vendant D2C ou distributeurs vendant D2C ou à de petites entreprises

* Au moins un magasin ou entrepôt physique

* Gérer votre inventaire de produits avec Inventory management pour Adobe Commerce (MSI)

* Capacité à syndiquer l’inventaire des commerçants

* Disponibilité du Wi-Fi en magasin à tous les emplacements qui prennent en charge la solution d’exécution de magasin

* Les associés de magasin et d’entrepôt ont accès aux appareils mobiles iOS ou Android au cours de leurs équipes, personnels ou fournis par le marchand.

* Les produits gérés à l’aide de la solution d’exécution de magasin doivent posséder des attributs de produit qui incluent un SKU ou un code de produit UPC.
