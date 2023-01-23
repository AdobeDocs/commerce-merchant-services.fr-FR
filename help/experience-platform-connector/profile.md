---
title: Chargement de profils d’acheteur dans Adobe Experience Platform
description: Découvrez comment charger des profils d’acheteurs vers Adobe Experience Platform.
exl-id: fd0ee7fa-5274-4640-ba00-bcb2ec78f314
source-git-commit: 9bf28159fdac3a7237956a536f6a522b4e2918fe
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# Chargement d’un profil d’acheteur dans Adobe Experience Platform

Les marchands Adobe Commerce peuvent transférer des données de profil client vers [Profil client en temps réel](https://experienceleague.adobe.com/docs/experience-platform/profile/home.html), qui fait partie de Adobe Experience Platform. Profile vous permet de consolider les données de vos clients dans une vue unifiée, offrant un compte d’activité horodaté et exploitable de chaque interaction client.

>[!NOTE]
>
> Les données de profil doivent inclure une adresse électronique, car c’est ainsi que le lien entre un acheteur et ses données comportementales de storefront est créé.

Une fois les profils de votre acheteur chargés, les données d’événement associées à toutes les interactions que vos acheteurs entreprennent sur votre site sont envoyées à Profile par l’intermédiaire du connecteur Experience Platform et liées à son profil.

>[!NOTE]
>
> Le `createAccount` [storefront, événement](events.md) ne crée pas automatiquement un profil client dans Profile. Cette mesure est limitée pour des raisons de sécurité et est intentionnelle.

Dans cette rubrique, vous allez apprendre à charger vos profils client Adobe Commerce vers Real-time Customer Profile dans Experience Platform.

1. Déterminez où vous stockez les données client. Pour certains commerçants, ces données sont stockées dans Adobe Commerce et peuvent être [exporté](https://docs.magento.com/user-guide/system/data-export.html) sous la forme d’un fichier CSV. Pour d’autres, il peut s’agir d’un système de gestion de la relation client distinct.

1. Une fois que vous avez déterminé où stocker vos données client, recherchez les [connecteur source](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html) selon l’emplacement de stockage des données client. Si vous ne voyez pas de connecteur source approprié, utilisez la méthode [téléchargement de fichier local](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/local-system/local-file-upload.html) connectez et importez vos profils de nouvel acheteur à partir d’un fichier CSV.

   >[!NOTE]
   >
   > Si vous utilisez le connecteur de téléchargement de fichiers local, vous devez activer la variable **Jeu de données de profil** lorsque [définition du jeu de données](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/local-system/local-file-upload.html#use-an-existing-dataset). Cela identifie le jeu de données comme étant des données de profil.

Une fois les profils de nouvel acheteur créés dans Profile, toutes les données de vitrine associées à cet acheteur seront liées à son profil.

## Chargement fréquent de profils

Pour garantir une expérience client améliorée, vous devez importer régulièrement des données de profil. Certains connecteurs source permettent d’importer les données de profil selon un calendrier.
