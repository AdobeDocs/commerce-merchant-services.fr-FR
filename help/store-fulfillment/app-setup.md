---
title: Configuration de l’application
description: '"Configurez la variable [!DNL Store Assist] pour gérer les workflows d’exécution de magasin de bout en bout et les processus d’achat en ligne, passez commande en magasin." '
role: User, Admin
level: Intermediate
source-git-commit: 4ea03b3be11056526adc42d875b1e26a24736d15
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 0%

---

# Configuration de l’application

Store Assist est une application de plateforme FaaS (fulfillment as a service) optimisée par Walmart Commerce Technologies. L’application fournit des fonctionnalités d’exécution en magasin à gérer. [!DNL buy online], [!DNL pick up in store] Commandes (BOPIS).

L’application reçoit toutes les informations sur la commande et les clients, depuis les détails de la commande pour déterminer les heures de prise en charge, et met les données à la disposition des associés du magasin en ligne, via les appareils mobiles. Grâce à l’assistant de magasin, les associés peuvent identifier les articles commandés par les clients, sélectionner les articles appropriés plus rapidement et configurer les commandes exécutées pour la remise en magasin ou à la prise en main aux clients.

Store Associates : utilisez l’assistant de magasin [!UICONTROL Pick], [!UICONTROL Stage], [!UICONTROL Handoff], et [!UICONTROL Orders] pour terminer le processus de diffusion et de remise suivant :

- Attribuer des dates et heures de remise de commande
- Recevez des notifications des clients lorsqu’ils arrivent au magasin pour le nettoyage de la commande.
- Commandes d’évaluation pour la remise aux clients
- Suivi de l’état des commandes pour toutes les commandes dans les emplacements de magasin qui leur sont attribués

Voir [Workflows d’exécution de l’assistant de magasin](store-assist-modules.md) pour en savoir plus sur l’application d’aide à la boutique.


## Configuration de l’application d’aide à la boutique

L’application d’aide à la boutique nécessite deux types de configuration :

- Paramètres de configuration de l’administrateur Adobe Commerce pour [Gestion des comptes utilisateur, des rôles utilisateur et des autorisations de ressources à partir des paramètres du système d’administration Adobe Commerce](user-setup.md).

- Paramètres de configuration de front-end pour personnaliser l’interface de l’application d’assistance à la boutique et d’autres paramètres, notamment :

   - **Marque l’application d’assistance Boutique**: personnalisez l’interface utilisateur de l’application avec le logo et les couleurs de votre entreprise.

   - **Mise à jour des instructions par défaut**: personnalisez les instructions qui s’affichent dans les interfaces d’assistance de magasin pour les modules de sélection, d’évaluation, de passation de commandes et de commande afin que vos associés sachent exactement ce qu’ils doivent faire à chaque étape du processus d’exécution.

   - **Localisation**: sélectionnez la langue disponible pour l’application, le format de date et d’heure, les unités de mesure par défaut, la devise par défaut.

   - **Durée d’inactivité**: indiquez la durée pendant laquelle l’application doit être inactive avant de se déconnecter.

   - **Annulation de la boutique**: indiquez si les commandes peuvent être annulées à partir du magasin et quels rôles disposent de droits d’annulation.

   - **Fenêtre de nettoyage des commandes**: indiquez le délai au-delà duquel une commande sélectionnée reste en cours d’évaluation avant d’être redémarrée (trois jours, par exemple).

   - Personnaliser toutes les instructions de l’application (sélection, évaluation, remise)

   - **Sélectionner des notifications**- Configuration si vous souhaitez que les notifications push commencent à être sélectionnées une fois la commande passée

   - **Archivage des notifications**- Configuration si vous souhaitez recevoir des notifications push une fois qu’un client s’est connecté / attend X minutes / ou aucune notification du tout

   - **Traitement de la main**: activez la signature du client, activez une invite pour vérifier l’ID de client avant de remettre la commande.

   - **Activer le rejet d’élément lors de la remise**

   Collaborez avec l’équipe des services clients de Walmart Commerce Technologies pour terminer la configuration de Frontend pour l’application d’assistance en magasin.

## Téléchargement et installation des applications

Une fois la configuration de l’application d’aide à la boutique terminée, les associés au magasin peuvent télécharger et installer l’application d’aide à la boutique sur leurs appareils mobiles et se connecter.

- Téléchargez l’application d’aide à la boutique à partir du [Apple App Store](https://apps.apple.com/us/app/store-assist-by-walmart/id16092815390) ou le magasin Google Play.

- Store Associates nécessite les informations suivantes pour se connecter :

   - Nom de la société associé à votre compte d’assistance de magasin

   - Informations d’identification du compte d’assistance de la boutique : nom d’utilisateur et mot de passe de leur compte.
   Un administrateur Adobe Commerce peut créer des comptes d’utilisateurs de l’application d’assistance de la boutique pour les emplacements de magasin qui ont [Collecte en magasin](merchant-store-configuration.md#pickup-location-configuration) activée dans les paramètres des boutiques d’administration.

