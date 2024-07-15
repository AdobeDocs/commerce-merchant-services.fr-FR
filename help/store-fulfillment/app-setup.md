---
title: Configuration de l’application
description: Configurez l’application  [!DNL Store Assist] pour gérer les processus et les processus d’exécution de magasin de bout en bout pour l’achat en ligne, récupérez dans les commandes du magasin.
level: Intermediate
role: Admin
feature: Shipping/Delivery, Configuration, Tools and External Services
exl-id: bcb5b02b-0141-407a-ad55-6e10e8e1aa90
source-git-commit: 78b09113e72382053b01d6016276bae3aa545fa3
workflow-type: tm+mt
source-wordcount: '619'
ht-degree: 0%

---

# Configuration de l’application

Store Assist est une application de plateforme en tant que service (FaaS) optimisée par Walmart Commerce Technologies. L’application fournit des fonctionnalités d’exécution en magasin pour gérer les commandes [!DNL buy online, pick up in store] (BOPIS). Grâce à l’assistant de magasin, les associés peuvent identifier les articles commandés par les clients, sélectionner les articles appropriés plus rapidement et configurer les commandes exécutées pour la remise en magasin ou à la prise en main aux clients.

L’application d’aide au magasin reçoit toutes les informations sur la commande et les clients, depuis les détails de la commande jusqu’aux heures de prise en charge, et met les données à la disposition des associés du magasin en ligne, via les appareils mobiles. L’application comprend les modules [!UICONTROL Pick], [!UICONTROL Stage], [!UICONTROL Handoff] et [!UICONTROL Orders] pour aider Store Associates à exécuter des activités telles que :

- Attribuez des dates et heures de remise de commande.
- Recevez des notifications des clients lorsqu’ils arrivent pour le nettoyage de la commande.
- Commandes d’évaluation pour la remise aux clients.
- Suivez l’état des commandes pour toutes les commandes dans les emplacements de magasin qui leur sont attribués.

>[!NOTE]
>
>Pour en savoir plus sur l’application d’aide à la boutique, consultez la rubrique [Workflows d’assistance à la boutique](store-assist-modules.md) .

## Configuration de l’application d’aide à la boutique

L’application d’aide à la boutique nécessite deux types de configuration :

- Paramètres du système d’administration Adobe Commerce pour [ gérer les comptes d’utilisateurs, les rôles utilisateur, les autorisations de ressources ](user-setup.md) et [la marque de voiture et les sélections de modèles disponibles pour les clients pendant le processus d’archivage](check-in-experience-setup.md).

- Paramètres de configuration de front-end pour personnaliser l’interface de l’application d’assistance à la boutique et d’autres paramètres, notamment :

   - **Marquez l’application d’aide à la boutique** : personnalisez l’interface utilisateur de l’application avec le logo et les couleurs de votre société.

   - **Mettez à jour les instructions par défaut** : personnalisez les instructions des modules Store Assist Pick, Stage, Handoff et Order pour guider Store Associates à chaque étape du processus d’exécution pour votre entreprise.

   - **Localisation** : sélectionnez la langue disponible pour l’application. Choisissez le format de date et d’heure, puis sélectionnez vos unités de mesure par défaut et votre devise par défaut.

   - **Durée d’inactivité** : spécifiez la durée pendant laquelle l’application doit être inactive avant de se déconnecter.

   - **Annulation du magasin** : indiquez si les commandes peuvent être annulées du magasin et quels rôles disposent d’autorisations d’annulation.

   - **Fenêtre de nettoyage de la commande** : spécifiez le délai écoulé depuis le [délai d’avance estimé de récupération](enable-general.md#delivery-method-title-configuration) qu’une commande sélectionnée reste en cours d’évaluation avant d’être redémarrée, par exemple trois jours. La valeur par défaut est de sept jours. Si cette configuration est activée, la commande est automatiquement annulée à l’expiration de cette période. Les articles sont réactivés et le marchand reçoit un email d’annulation.

   - Personnalisez toutes les instructions de l’application (sélection, évaluation, remise).

   - **Notifications de la sélection** : indiquez si vous souhaitez envoyer une notification push pour démarrer le processus de sélection après qu’un client ait passé une commande.

   - **Archiver des notifications** : indiquez si vous souhaitez envoyer une notification push pendant le processus d’archivage pour les récupérations de commande. Après l’archivage, le temps d’attente du client dépasse une période spécifiée. Vous pouvez également désactiver la notification.

   - **Processus de désactivation** : activez les processus facultatifs lorsque l’associé de magasin envoie une commande au client ; par exemple, exigez une signature de client ou invitez l’associé à vérifier l’ID de client.

   - **Activer le rejet d’article lors de la remise** : autorisez les clients à retourner ou annuler des articles de commande lors de la remise de commande.

  Collaborez avec l’équipe des services clients de Walmart Commerce Technologies pour terminer la configuration frontale de l’application d’assistance au magasin.

## Téléchargement et installation des applications

Une fois l’application d’aide à la boutique configurée et configurée, Store Associates peut la télécharger, l’installer et se connecter à l’application d’aide à la boutique à partir de ses appareils mobiles.

- Vérifiez que l’appareil mobile répond à la [configuration matérielle et logicielle requise](solution-requirements.md#store-assist-app-requirements) pour la solution d’exécution de magasin.

- Téléchargez l’application d’aide à la boutique à partir de [Apple App Store](https://apps.apple.com/us/app/store-assist-by-walmart/id1609281539){target="_blank"} ou de la [boutique Google Play](https://play.google.com/store/apps/details?id=com.walmart.faas.storeassist){target="_blank"}.

- Store Associates nécessite les informations suivantes pour se connecter :

   - **[!UICONTROL Company name]** associé au compte d’assistance de magasin

   - **Informations d’identification du compte d’assistance de la boutique** : nom d’utilisateur et mot de passe pour leur compte.

  Un administrateur Adobe Commerce peut créer et gérer des comptes d’utilisateurs [!DNL Store Assist app] pour tous les emplacements de magasin où le [nettoyage en magasin](merchant-store-configuration.md#pickup-location-configuration) est activé dans les paramètres des boutiques d’administration.
