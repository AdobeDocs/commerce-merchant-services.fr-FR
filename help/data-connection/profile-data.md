---
title: Mise à jour du schéma d’enregistrement de profil pour l’ingestion de données Commerce
description: Découvrez comment créer un schéma, un jeu de données et un flux de données pour collecter et envoyer des données d’enregistrement de profil Commerce à l’Experience Platform.
role: Admin, Developer
feature: Personalization, Integration
exl-id: 86a3ba12-7f26-4f7e-98a0-9af0d1d8d881
source-git-commit: 813be62b366b1c76a2b909079cfba31ef8000617
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 0%

---

# Mise à jour du schéma d’enregistrement de profil pour l’ingestion de données Commerce (version bêta)

Lorsque vos acheteurs créent un profil sur votre site Commerce, un enregistrement de profil est créé et des données sont capturées. Vous devez créer un schéma et un jeu de données spécifiques à cet enregistrement de profil avant de pouvoir diffuser ces données de profil vers l’Experience Platform.

1. [Créer](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/ui/resources/schemas) un schéma et définissez la classe sur **Profil individuel**.

1. [Ajouter](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/ui/resources/schemas) les groupes de champs spécifiques au profil suivants :

   - identityMap
   - Détails démographiques
   - Détails du contact personnel
   - Détails du compte d’utilisateur

1. [Activer](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/ui/resources/schemas) le schéma pour Profile.

   Lorsqu’un schéma est activé pour Profile, tous les jeux de données créés à partir de ce schéma participent à Real-Time CDP, qui fusionne les données de sources disparates pour créer une vue complète de chaque client.

1. [Création d’un jeu de données](https://experienceleague.adobe.com/en/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform) en fonction du schéma que vous avez créé ou mis à jour.

   Un jeu de données est une structure de stockage et de gestion pour une collecte de données, généralement un tableau contenant un schéma (des colonnes) et des champs (des lignes). Les jeux de données contiennent également des métadonnées qui décrivent divers aspects des données qu’ils stockent.

1. Créez un [espace de noms personnalisé](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/namespaces#create-namespaces) en Experience Platform avec les valeurs suivantes :

   - **Nom d’affichage**: _ID de client Commerce_
   - **Symbole d’identité**: _CustomerId_
   - **Type**: _Identifiant individuel multi-appareils_

   ![Créer un espace de noms personnalisé](assets/custom-namespace.png){width="700" zoomable="yes"}

   Cliquez sur **[!UICONTROL Create]**. Un espace de noms personnalisé est utilisé par le service de profil unifié pour assembler les fragments de profil.

Avec le schéma, le jeu de données et l’espace de noms personnalisé configurés pour les données d’enregistrement de profil client, vous pouvez [configure](connect-data.md#data-collection) votre instance Commerce pour collecter et envoyer ces données à Experience Platform.

Pour créer un schéma, un jeu de données et un flux de données pour les données d’événement comportemental et back-office, voir [mise à jour des schémas d’événements de série temporelle pour l’ingestion de données Commerce](update-xdm.md).
