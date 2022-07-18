---
title: Ajout de groupes de champs au schéma XDM
description: Découvrez comment ajouter des groupes de champs spécifiques à Adobe Commerce à un schéma XDM.
source-git-commit: 4d6a4cec81dbb1e71718066be2ba13a4d292aea3
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Ajout de groupes de champs au schéma XDM

L’un des [conditions préalables](overview.md#prereqs) pour utiliser le connecteur Experience Platform, accédez à l’espace de travail du flux de données et [création d’un flux de données](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html?lang=en) qui est spécifique à Adobe Commerce. Lorsque vous créez ce flux de données, vous devez également sélectionner un schéma XDM qui représente les données que vous prévoyez d’ingérer. Cette rubrique vous fournit les groupes de champs que votre schéma XDM doit inclure pour collecter avec succès les données fournies par le storefront Adobe Commerce. [events](events.md).

1. Si vous ne disposez pas déjà d’un schéma XDM, [create](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html?lang=en#create) un. Sinon, [edit](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html?lang=en#edit) votre schéma XDM existant dans l’interface utilisateur de Adobe Experience Platform.
1. [Ajouter](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html?lang=en#add-field-groups) les groupes de champs spécifiques à Commerce suivants :

   - Commerce
   - Recherche de site
   - Page Web Visite
   - Processus de connexion de l’utilisateur
   - Clés de référence
   - Détails du contact personnel
   - Détails du commerce
   - Adobe Analytics Experience Event Commerce (si vous souhaitez envoyer des données à Adobe Analytics)
   - Identifiant de personne

   Votre schéma XDM contient désormais des groupes de champs spécifiques à Commerce afin que les données collectées à partir du storefront Commerce [events](events.md) est représenté dans XDM.
1. Vous devriez maintenant [création d’un flux de données](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html?lang=en) et sélectionnez le schéma XDM contenant les groupes de champs spécifiques à Commerce.
