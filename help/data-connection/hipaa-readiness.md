---
title: Conformité HIPAA aux normes  [!DNL Commerce]  services
description: Découvrez comment utiliser l’extension  [!DNL Data Connection]  pour partager  [!DNL Commerce]  données avec des Experience Platform et maintenir la conformité à la loi HIPAA.
role: Admin, Leader
feature: Security, Compliance
source-git-commit: 53fada6634a349dc4baa03b566b2802ddece65f1
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Préparation de la loi HIPAA pour les services [!DNL Commerce]

L’extension [!DNL Data Connection] vous permet de partager [!DNL Commerce] données d’événement de back-office avec des Experience Platform et de respecter la conformité HIPAA.

>[!IMPORTANT]
>
>Comme les événements storefront sont générés côté client, il est de la responsabilité du commerçant [de ne pas envoyer de données d’événement storefront](connect-data.md#data-collection) à l’Experience Platform.

Dans cet article, vous apprendrez :

- Éléments à installer
- Comment s’assurer que les données envoyées à l’Experience Platform sont conformes à la loi HIPAA
- Chiffrement des données dans [!DNL Commerce]

## Installation

Si vous avez acheté le module complémentaire de soins de santé pour Adobe [!DNL Commerce], il est probable que vous ayez déjà installé l’extension [ conforme à la norme HIPAA](https://experienceleague.adobe.com/en/docs/commerce-admin/start/compliance/hipaa-ready-service/overview#installation). Pour vous assurer que vos données d’événement back-office [!DNL Commerce] sont conformes à la loi HIPAA, vous devez également installer l’extension [!DNL Data Connection] avec l’extension **Data Services HIPAA** supplémentaire. L’extension **Data Services HIPAA** garantit que toutes les données de back-office que vous envoyez à l’Experience Platform sont conformes à la loi HIPAA. Découvrez [ comment installer l’extension ](install.md#install-the-data-services-hipaa-extension).

>[!IMPORTANT]
>
>Lorsque vous installez l’extension **Data Services HIPAA**, les données d’événement de storefront utilisées par Live Search et Product Recommendations ne sont plus capturées. En effet, les données d’événement de storefront sont générées côté client. Pour continuer à capturer et à envoyer des données d’événement de storefront, réactivez la collecte d’événements pour ces services. Voir [configuration générale](https://experienceleague.adobe.com/en/docs/commerce-admin/config/general/general.html#data-services) pour en savoir plus.

## Comment s’assurer que les données envoyées à l’Experience Platform sont conformes à la loi HIPAA

Toutes les données d’événement de back-office envoyées par l’extension [!DNL Data Connection] à l’Experience Platform sont considérées comme sensibles dans [!DNL Commerce]. Cependant, il est de la responsabilité du commerçant d’appliquer des libellés d’utilisation des données à son schéma de [!DNL Commerce] en Experience Platform afin d’identifier explicitement les données spécifiques comme sensibles. Lorsque vous appliquez des libellés d’utilisation des données directement à un schéma, ces libellés sont propagés à tous les jeux de données existants et futurs basés sur ce schéma.

Pour obtenir une présentation des libellés d’utilisation des données et de leur rôle dans le cadre de la gouvernance des données, consultez la [ présentation des libellés d’utilisation des données ](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/labels/overview) dans la documentation de l’Experience Platform.

### Appliquer des libellés d’utilisation des données aux champs de [!DNL Commerce]

Suivez les étapes du tutoriel [gérer les libellés d’utilisation des données pour un schéma](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/tutorials/labels) pour savoir comment appliquer des libellés à votre schéma de [!DNL Commerce].

Voir le [glossaire des libellés sensibles](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/labels/reference#sensitive) pour en savoir plus sur les libellés disponibles que vous pouvez appliquer aux champs de votre schéma de [!DNL Commerce]. Par exemple, l’étiquette `RHD` identifie des informations protégées sur la santé (ISP) ou des informations sur un patient que vous êtes contractuellement autorisé(e) par l’Adobe à télécharger.

Lorsque vos données [!DNL Commerce] sont étiquetées comme sensibles, vous pouvez appliquer des politiques afin d’empêcher les opérations de données qui constituent des violations de politique. En savoir plus sur [l’application des politiques](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/enforcement/overview) dans Experience Platform.

## Chiffrement des données dans Commerce

Adobe [!DNL Commerce] utilise le chiffrement au niveau du bloc. Pour le stockage, [!DNL Commerce] utilise Amazon Elastic Block Store (EBS). Tous les volumes EBS sont chiffrés à l&#39;aide de l&#39;algorithme AES-256, ce qui signifie que les données sont chiffrées au repos. [!DNL Commerce] données en transit sont acheminées par le biais de connexions sécurisées et chiffrées à l’aide de HTTPS [TLS v1.2](https://datatracker.ietf.org/doc/html/rfc5246).

>[!IMPORTANT]
>
>Commerce ne prend pas en charge le chiffrement au niveau des colonnes ou des lignes lorsque les données ne sont pas au repos ou en transit entre les serveurs.

### Chiffrement des données dans l’Experience Platform

Lorsque les commerçants envoient leurs données à l’Experience Platform, ces données sont envoyées à l’aide de HTTPS TLS v1.2. En savoir plus sur la façon dont [Experience Platform ](https://experienceleague.adobe.com/en/docs/experience-platform/landing/governance-privacy-security/encryption) chiffre les données.

## Gestion [!DNL Commerce] demandes d’accès à des informations personnelles

Découvrez comment [!DNL Commerce] [gère les demandes d’accès à des informations personnelles](handle-privacy-request.md).
