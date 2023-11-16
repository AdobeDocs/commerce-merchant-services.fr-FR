---
title: Ajout de groupes de champs au schéma XDM
description: Découvrez comment ajouter des groupes de champs spécifiques à Adobe Commerce à un schéma XDM.
exl-id: 4401bbe7-1ccc-4349-a998-9e9ee9db590f
role: Admin, Developer
feature: Personalization, Integration
source-git-commit: 4a5877d6e1a5c7d840e36f4913306b0c440bbac5
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---

# Ajout de groupes de champs au schéma XDM

L’un des [Etapes d’intégration](overview.md#onboarding-steps) pour utiliser la variable [!DNL Data Connection] l’extension est pour accéder à l’espace de travail datastream et [créer un flux de données ;](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) spécifique à Adobe Commerce. Lorsque vous créez ce flux de données, vous devez également sélectionner un schéma XDM qui représente les données que vous prévoyez d’ingérer. Cette rubrique vous fournit les groupes de champs que votre schéma XDM doit inclure pour collecter avec succès les données fournies par Adobe Commerce. [events](events.md).

1. Si vous ne disposez pas déjà d’un schéma XDM, [create](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#create) un. Sinon, [edit](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#edit) votre schéma XDM existant dans l’interface utilisateur de Adobe Experience Platform.

1. [Ajouter](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#add-field-groups) les groupes de champs spécifiques à Commerce suivants :

   - Recherche de site
   - Page Web Visite
   - Processus de connexion de l’utilisateur
   - Clés de référence
   - Détails du contact personnel
   - Détails du commerce
   - Adobe Analytics ExperienceEvent Commerce (si vous souhaitez envoyer des données à Adobe Analytics)
   - Carte des identités

   >[!NOTE]
   >
   > Ne définissez aucun groupe de champs spécifique à Commerce comme `Primary identity`. Cela permet d’identifier le champ selon les besoins et l’Experience Platform attend ce champ dans chaque événement. Si ce champ est absent, l’ingestion des données échoue.

   Votre schéma XDM contient désormais des groupes de champs spécifiques à Commerce afin que les données collectées auprès de Commerce [events](events.md) est représenté dans XDM.

1. [Création d’un jeu de données](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) en fonction du schéma que vous avez créé ou mis à jour.

   Un jeu de données est une structure de stockage et de gestion pour une collecte de données, généralement sous la forme d’un tableau, qui contient un schéma (des colonnes) et des champs (des lignes). Les jeux de données contiennent également des métadonnées qui décrivent divers aspects des données qu’ils stockent.

1. [Création d’un flux de données](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) et sélectionnez le schéma XDM contenant les groupes de champs spécifiques à Commerce et le jeu de données correspondant.

   La chaîne de données transfère les données collectées au jeu de données. Les données sont représentées dans le jeu de données en fonction du schéma sélectionné.
