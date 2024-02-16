---
title: Mise à jour du schéma d’enregistrement de profil pour l’ingestion de données commerciales
description: Découvrez comment créer un schéma, un jeu de données et un flux de données pour collecter et envoyer des données d’enregistrement de profil Commerce à l’Experience Platform.
role: Admin, Developer
feature: Personalization, Integration
source-git-commit: 8456f9b81812cf8ace55b7406d8b4fe50332c17a
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 0%

---

# Mise à jour du schéma d’enregistrement de profil pour l’ingestion de données commerciales

>[!NOTE]
>
>Cette fonctionnalité est en version bêta. Si vous souhaitez rejoindre le programme bêta, envoyez une demande à [dataconnection@adobe.com](mailto:dataconnection@adobe.com).

Lorsque vos acheteurs créent un profil sur votre site Commerce, un enregistrement de profil est créé et des données sont capturées. Vous devez créer un schéma et un jeu de données spécifiques à cet enregistrement de profil avant de pouvoir diffuser ces données de profil vers l’Experience Platform.

1. [Créer](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#create) un schéma et définissez la classe sur **Profil individuel**.

1. [Ajouter](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#add-field-groups) les groupes de champs spécifiques au profil suivants :

   - identityMap
   - Détails démographiques
   - Détails du contact personnel
   - Détails du compte d’utilisateur

1. [Activer](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#profile) le schéma pour Profile.

   Lorsqu’un schéma est activé pour Profile, tous les jeux de données créés à partir de ce schéma participent à Real-Time CDP, qui fusionne les données de sources disparates pour créer une vue complète de chaque client.

1. [Création d’un jeu de données](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) en fonction du schéma que vous avez créé ou mis à jour.

   Un jeu de données est une structure de stockage et de gestion pour une collecte de données, généralement un tableau contenant un schéma (des colonnes) et des champs (des lignes). Les jeux de données contiennent également des métadonnées qui décrivent divers aspects des données qu’ils stockent.

Avec le schéma et le jeu de données configurés pour les données d’enregistrement de profil client, vous pouvez [configure](connect-data.md#data-collection) votre instance Commerce pour collecter et envoyer ces données à l’Experience Platform.

Pour créer un schéma, un jeu de données et un flux de données pour les données d’événement comportemental et back-office, voir [mise à jour des schémas d’événements de série temporelle pour l’ingestion de données Commerce](update-xdm.md).
