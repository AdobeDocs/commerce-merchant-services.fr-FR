---
title: Configuration de l’application
description: Configurez les [!DNL Store Assist] pour gérer les processus d’exécution de magasin de bout en bout et les processus d’achat en ligne, sélectionnez dans les commandes de magasin.
role: User, Admin
level: Intermediate
exl-id: bcb5b02b-0141-407a-ad55-6e10e8e1aa90
source-git-commit: 1fb22b4644d41ea5c60aead3fe2c455dfa3382f8
workflow-type: tm+mt
source-wordcount: '604'
ht-degree: 0%

---

# Configuration de l’application

Store Assist est une application de plateforme FaaS (fulfillment as a service) optimisée par Walmart Commerce Technologies. L’application fournit des fonctionnalités d’exécution en magasin à gérer. [!DNL buy online, pick up in store] Commandes (BOPIS). Grâce à l’assistant de magasin, les associés peuvent identifier les articles commandés par les clients, sélectionner les articles appropriés plus rapidement et configurer les commandes exécutées pour la remise en magasin ou à la prise en main aux clients.

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

- Paramètres du système d’administration Adobe Commerce pour [gestion des comptes utilisateur, des rôles utilisateur, des autorisations de ressources](user-setup.md), et [la marque de voiture et les sélections de modèles disponibles pour les clients lors du processus d’archivage ;](check-in-experience-setup.md).

- Paramètres de configuration de front-end pour personnaliser l’interface de l’application d’assistance à la boutique et d’autres paramètres, notamment :

   - **Marque l’application d’assistance Boutique**: personnalisez l’interface utilisateur de l’application avec le logo et les couleurs de votre société.

   - **Mise à jour des instructions par défaut**: personnalisez les instructions des modules d’aide à la boutique, sélection, évaluation, passation de commandes et commande pour guider Store Associates tout au long de chaque étape du processus d’exécution pour votre entreprise.

   - **Localisation**: sélectionnez la langue disponible pour l’application. Sélectionnez le format de date et d’heure, puis les unités de mesure par défaut et la devise par défaut.

   - **Durée d’inactivité**: indiquez la durée pendant laquelle l’application doit être inactive avant de se déconnecter.

   - **Annulation de la boutique**: indiquez si les commandes peuvent être annulées à partir du magasin et quels rôles disposent de droits d’annulation.

   - **Fenêtre de nettoyage des commandes**: indiquez le délai au-delà duquel une commande sélectionnée reste en cours d’évaluation avant d’être redémarrée (trois jours, par exemple).

   - Personnalisez toutes les instructions de l’application (sélection, évaluation, remise).

   - **Sélectionner des notifications**: indiquez si vous souhaitez envoyer une notification push pour démarrer le processus de sélection après qu’un client a passé une commande.

   - **Archivage des notifications**: indiquez s’il faut envoyer une notification push pendant le processus d’archivage pour les récupérations de commande. Après l’enregistrement, le temps d’attente du client dépasse une période spécifiée. Vous pouvez également désactiver la notification.

   - **Traitement de la main**: activez les processus facultatifs lorsque l’associé du magasin envoie une commande au client ; par exemple, il requiert une signature du client ou invite l’associé à vérifier l’ID de client.

   - **Activer le rejet d’élément lors de la remise**: permet aux clients de renvoyer ou d’annuler des articles de commande lors de la remise de commande.
   Collaborez avec l’équipe des services clients de Walmart Commerce Technologies pour terminer la configuration frontale de l’application d’assistance au magasin.

## Téléchargement et installation des applications

Une fois l’application d’aide à la boutique configurée et configurée, Store Associates peut la télécharger, l’installer et se connecter à l’application d’aide à la boutique à partir de ses appareils mobiles.

- Vérifiez que le périphérique mobile répond à la variable [configuration matérielle et logicielle requise](solution-requirements.md#store-assist-app-requirements) pour la solution d’exécution de magasin.

- Téléchargez l’application d’aide à la boutique à partir du [Apple App Store](https://apps.apple.com/us/app/store-assist-by-walmart/id1609281539){target=&quot;_blank&quot;} ou la variable [Google Play store](https://play.google.com/store/apps/details?id=com.walmart.faas.storeassist){target=&quot;_blank&quot;}.

- Store Associates nécessite les informations suivantes pour se connecter :

   - **[!UICONTROL Company name]** associé au compte d’assistance de magasin

   - **Informations d’identification du compte d’assistance de la boutique**—nom d’utilisateur et mot de passe pour leur compte.
   Un administrateur Adobe Commerce peut créer un compte d’utilisateur et définir des autorisations pour le [!DNL Store Assist app] comptes d’utilisateurs pour les emplacements de magasin qui ont [Collecte en magasin](merchant-store-configuration.md#pickup-location-configuration) activée dans les paramètres des boutiques d’administration.
