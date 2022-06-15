---
title: Configuration de l’application
description: '"Configurez la variable [!DNL Store Assist] pour gérer les workflows d’exécution de magasin de bout en bout et les processus d’achat en ligne, passez commande en magasin." '
role: User, Admin
level: Intermediate
source-git-commit: 42b0118b427b1e04186793b4a57c058bc1cabdd4
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---


# Configuration de l’application

Store Assist est une application de plateforme FaaS (fulfillment as a service) optimisée par Walmart Commerce Technologies. L’application fournit des fonctionnalités d’exécution en magasin à gérer. [!DNL buy online], [!DNL pick up in store] Commandes (BOPIS).  Grâce à l’assistant de magasin, les associés peuvent identifier les articles commandés par les clients, sélectionner les articles appropriés plus rapidement et configurer les commandes exécutées pour la remise en magasin ou à la prise en main aux clients.

L’application d’aide au magasin reçoit toutes les informations sur la commande et les clients, depuis les détails de la commande jusqu’aux heures de prise en charge, et met les données à la disposition des associés du magasin en ligne, via les appareils mobiles. L’application comprend : [!UICONTROL Pick], [!UICONTROL Stage], [!UICONTROL Handoff], et [!UICONTROL Orders] modules pour aider Store Associates à exécuter des activités d’exécution comme celles-ci :

- Attribuez des dates et heures de remise de commande.
- Recevez des notifications des clients lorsqu’ils arrivent pour le nettoyage de la commande.
- Commandes d’évaluation pour la remise aux clients.
- Suivez l’état des commandes pour toutes les commandes dans les emplacements de magasin qui leur sont attribués.

>[!NOTE]
>
>Voir [Workflows d’exécution de l’assistant de magasin](store-assist-modules.md) pour en savoir plus sur l’application d’aide à la boutique.

## Configuration de l’application d’aide à la boutique

L’application d’aide à la boutique nécessite deux types de configuration :

- Paramètres de configuration de l’administrateur Adobe Commerce pour [gérer les comptes utilisateur, les rôles utilisateur et les autorisations de ressources à partir des paramètres du système d’administration Adobe Commerce.](user-setup.md).

- Paramètres de configuration de front-end pour personnaliser l’interface de l’application d’assistance à la boutique et d’autres paramètres, notamment :

   - **Marque l’application d’assistance Boutique**: personnalisez l’interface utilisateur de l’application avec le logo et les couleurs de votre société.

   - **Mise à jour des instructions par défaut**: personnalisez les instructions des interfaces d’aide à la boutique pour les modules de sélection, d’évaluation, de passation de commandes et de commande afin de respecter les politiques et procédures de votre société, et guidez les associés à la boutique à travers chaque étape du processus d’exécution.

   - **Localisation**: sélectionnez la langue disponible pour l’application. Sélectionnez le format de date et d’heure, puis les unités de mesure par défaut et la devise par défaut.

   - **Durée d’inactivité**: indiquez la durée pendant laquelle l’application doit être inactive avant de se déconnecter.

   - **Annulation de la boutique**: indiquez si les commandes peuvent être annulées à partir du magasin et quels rôles disposent de droits d’annulation.

   - **Fenêtre de nettoyage des commandes**: indiquez le délai au-delà duquel une commande sélectionnée reste en cours d’évaluation avant d’être redémarrée (trois jours, par exemple).

   - Personnalisez toutes les instructions de l’application (sélection, évaluation, remise).

   - **Sélectionner des notifications**-Indiquez si une notification push doit être envoyée pour démarrer le processus de sélection après qu’un client a passé une commande.

   - **Archivage des notifications**-Indiquez si une notification push doit être envoyée pendant le processus d’archivage pour les récupérations de commande : après l’enregistrement, le temps d’attente du client dépasse une période spécifiée. Vous pouvez également désactiver la notification.

   - **Traitement de la main**: activez les processus facultatifs lorsque l’associé du magasin envoie une commande au client ; par exemple, il requiert une signature du client ou invite l’associé à vérifier l’ID de client.

   - **Activer le rejet d’élément lors de la remise**- Autoriser les clients à retourner ou annuler des articles de commande lors de la remise de commande.

   Collaborez avec l’équipe des services clients de Walmart Commerce Technologies pour terminer la configuration frontale de l’application d’assistance au magasin.

## Téléchargement et installation des applications

Une fois la configuration de l’application d’aide à la boutique terminée, les associés au magasin peuvent télécharger, installer et se connecter à l’application d’aide à la boutique à partir de leurs appareils mobiles.

- Téléchargez l’application d’aide à la boutique à partir du [Apple App Store](https://apps.apple.com/us/app/store-assist-by-walmart/id16092815390) ou le magasin Google Play.

- Store Associates nécessite les informations suivantes pour se connecter :

   - Nom de la société associé à votre compte d’assistance en magasin

   - Informations d’identification du compte d’assistance de la boutique : nom d’utilisateur et mot de passe de leur compte.
   Un administrateur Adobe Commerce peut créer un compte d’utilisateur et définir des autorisations pour les comptes d’utilisateurs de l’application d’assistance en magasin pour les emplacements de magasin. [Collecte en magasin](merchant-store-configuration.md#pickup-location-configuration) activée dans les paramètres des boutiques d’administration.

