---
title: Mise à jour des schémas d’événement de série temporelle pour l’ingestion de données commerciales
description: Découvrez comment créer un schéma, un jeu de données et un flux de données pour collecter et envoyer des données d’événement de série temporelle pour l’ingestion de données Commerce.
exl-id: 4401bbe7-1ccc-4349-a998-9e9ee9db590f
role: Admin, Developer
feature: Personalization, Integration
source-git-commit: d5824e11b4961b518e35fcf56ff2c7ee00480617
workflow-type: tm+mt
source-wordcount: '997'
ht-degree: 0%

---

# Mise à jour des schémas d’événement de série temporelle pour l’ingestion de données commerciales

L’un des [Etapes d’intégration](overview.md#onboarding-steps) pour utiliser la variable [!DNL Data Connection] l’extension est pour accéder à l’espace de travail datastream et [créer un flux de données ;](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) spécifique à Adobe Commerce. Lorsque vous créez ce flux de données, vous devez également sélectionner un schéma qui décrit les données que vous prévoyez d’ingérer. Ce schéma doit inclure des groupes de champs spécifiques au commerce.

Cet article vous fournit les groupes de champs que votre schéma doit inclure pour collecter avec succès les données de série temporelle suivantes fournies par les événements Adobe Commerce :

- [Comportement](events.md) - Inclut le storefront, le profil, la recherche et les événements B2B.
- [Retour au bureau](events-backoffice.md) - Inclut l’état de la commande et les événements de profil.

En savoir plus sur [données de série temporelle](data-ingestion.md).

En savoir plus sur les [principes de base de la composition des schémas](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html).

## Mise à jour du schéma avec les données comportementales de série temporelle et d’événement back-office

Dans cette section, vous découvrez comment mettre à jour votre schéma existant ou créer un schéma pour inclure des données d’événement comportemental et back-office.

>[!NOTE]
>
>Voir [données d’événement de profil de série temporelle](#time-series-profile-event-data) pour savoir comment ajouter des champs spécifiques au profil.

1. Si vous ne disposez pas déjà d’un schéma, [create](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#create) une avec la classe définie sur **Événement d’expérience**.

1. [Ajouter](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#add-field-groups) les groupes de champs spécifiques au commerce suivants (ou modifiez votre schéma existant et ajoutez ces groupes de champs) :

   - Recherche de site
   - Page Web Visite
   - Processus de connexion de l’utilisateur
   - Clés de référence
   - Détails du contact personnel
   - Détails du canal
   - Détails du commerce
   - Adobe Analytics ExperienceEvent Commerce (si vous souhaitez envoyer des données à Adobe Analytics)

   >[!NOTE]
   >
   > Ne définissez aucun groupe de champs spécifique à Commerce comme `Primary identity`. Cela permet d’identifier le champ selon les besoins et l’Experience Platform attend ce champ dans chaque événement. Si ce champ est absent, l’ingestion des données échoue.

   Votre schéma contient désormais des groupes de champs spécifiques au commerce, de sorte que les données de série temporelle collectées auprès de Commerce [comportemental](events.md) et [back office](events-backoffice.md) est représenté dans le schéma.

1. [Activer](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#profile) le schéma pour Profile.

   Lorsqu’un schéma est activé pour Profile, tous les jeux de données créés à partir de ce schéma participent à Real-Time CDP, qui fusionne les données de sources disparates pour créer une vue complète de chaque client.

1. [Création d’un jeu de données](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) en fonction du schéma que vous avez créé ou mis à jour.

   Un jeu de données est une structure de stockage et de gestion pour une collecte de données, généralement un tableau contenant un schéma (des colonnes) et des champs (des lignes). Les jeux de données contiennent également des métadonnées qui décrivent divers aspects des données qu’ils stockent.

1. [Création d’un flux de données](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) et sélectionnez le schéma qui contient les groupes de champs spécifiques à Commerce et le jeu de données correspondant.

   La chaîne de données transfère les données collectées au jeu de données. Les données sont représentées dans le jeu de données en fonction du schéma sélectionné.

1. **Beta** (Facultatif) Vous pouvez utiliser des attributs personnalisés si vous souhaitez transmettre des données d’événement personnalisé de votre instance Commerce à l’Experience Platform. Cette fonctionnalité est en version bêta. Si vous souhaitez rejoindre le programme bêta, envoyez une demande à [dataconnection@adobe.com](mailto:dataconnection@adobe.com). Dans votre requête, incluez les éléments suivants :

   - Votre [ID d’organisation d’Adobe](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html#concept_EA8AEE5B02CF46ACBDAD6A8508646255). Par exemple `organization_id@AdobeOrg`.
   - Liste des attributs personnalisés au niveau de la commande.
   - Liste des attributs au niveau de l’élément de commande.

   L’équipe Adobe Commerce vous contactera pour plus d’informations et pour connaître les étapes suivantes.

Avec les schémas, les jeux de données et les jeux de données configurés pour les données comportementales et de back-office, vous pouvez [configure](connect-data.md#data-collection) votre instance Commerce pour collecter et envoyer ces données à l’Experience Platform.

Pour inclure les informations de profil de votre acheteur, reportez-vous à la section suivante.

## Données d’événement de profil de série temporelle

>[!NOTE]
>
>Cette fonctionnalité est en version bêta. Si vous souhaitez rejoindre le programme bêta, envoyez une demande à [dataconnection@adobe.com](mailto:dataconnection@adobe.com).

Les données d’événement de profil de série temporelle sont générées à partir des événements suivants :

- [`accountCreated`](events-backoffice.md#accountcreated)
- [`accountUpdated`](events-backoffice.md#accountupdated)
- [`accountDeleted`](events-backoffice.md#accountdeleted)

Si vous souhaitez ingérer les données d’événement de profil de votre client dans l’Experience Platform, vous pouvez mettre à jour votre schéma Commerce existant et utiliser le même flux de données déjà configuré, ou vous pouvez créer un flux de données et un schéma spécifiques au profil. Cette décision est basée sur la gouvernance des données de votre entreprise. Les deux sections suivantes vous guident dans les deux cas.

### Envoyez des données d’événement de profil de série temporelle à l’Experience Platform à l’aide de votre flux de données existant.

Si vous souhaitez ajouter des séries temporelles [données d’événement de profil côté serveur](events-backoffice.md#customer-profile-events-server-side) dans votre flux de données Commerce existant, ajoutez le `Demographic Details` groupe de champs à votre schéma. Votre schéma contient maintenant les groupes de champs suivants spécifiques au commerce :

- Recherche de site
- Page Web Visite
- Processus de connexion de l’utilisateur
- Clés de référence
- Détails du contact personnel
- Détails du canal
- Détails du commerce
- Adobe Analytics ExperienceEvent Commerce (si vous souhaitez envoyer des données à Adobe Analytics)
- Nouveau : **Détails démographiques**

Avec l’ajout de la variable `Demographic Details` groupe de champs de votre schéma Commerce existant, le jeu de données et le jeu de données déjà associés à votre schéma Commerce est utilisé pour ces données de profil de série temporelle.

### Envoi de données d’événement de profil de série temporelle à l’Experience Platform dans un flux de données distinct

Si vous souhaitez ajouter [données d’événement de profil côté serveur](events-backoffice.md#customer-profile-events-server-side) pour créer un nouveau schéma et un nouveau jeu de données spécifique au profil, procédez comme suit.

1. [Créer](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#create) un schéma et définissez la classe sur **Événement d’expérience**.

1. [Ajouter](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#add-field-groups) les groupes de champs spécifiques au profil suivants :

   - Détails démographiques
   - Détails du contact personnel
   - Détails du canal
   - Détails du commerce

1. [Activer](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#profile) le schéma pour Profile.

   Lorsqu’un schéma est activé pour Profile, tous les jeux de données créés à partir de ce schéma participent à Real-Time CDP, qui fusionne les données de sources disparates pour créer une vue complète de chaque client.

1. [Création d’un jeu de données](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) en fonction du schéma que vous avez créé.

   Un jeu de données est une structure de stockage et de gestion pour une collecte de données, généralement un tableau contenant un schéma (des colonnes) et des champs (des lignes). Les jeux de données contiennent également des métadonnées qui décrivent divers aspects des données qu’ils stockent.

1. [Création d’un flux de données](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) et sélectionnez le schéma XDM contenant les groupes de champs spécifiques à Commerce et le jeu de données correspondant.

   La chaîne de données transfère les données collectées au jeu de données. Les données sont représentées dans le jeu de données en fonction du schéma sélectionné.

Avec les schémas, les jeux de données et les jeux de données configurés pour les données de profil client, vous pouvez [configure](connect-data.md#data-collection) votre instance Commerce pour collecter et envoyer ces données à l’Experience Platform.

Pour créer un schéma, un jeu de données et un flux de données pour les données d’enregistrement de profil, voir [envoyer des données d’enregistrement de profil à l’Experience Platform ;](profile-data.md).
