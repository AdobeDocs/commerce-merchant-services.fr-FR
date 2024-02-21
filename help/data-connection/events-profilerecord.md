---
title: Enregistrements de profil
description: Découvrez les données capturées par un enregistrement de profil.
role: Admin, Developer
feature: Personalization, Integration, Eventing
source-git-commit: 655b5d18a4fb77232523c9c18a9fb362de93c70a
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 0%

---

# [!DNL Data Connection] Enregistrements de profil (bêta)

>[!NOTE]
>
>Cette fonctionnalité est en version bêta. Si vous souhaitez rejoindre le programme bêta, envoyez une demande à [dataconnection@adobe.com](mailto:dataconnection@adobe.com).

La section suivante décrit les données d’enregistrement de profil Commerce disponibles lors de l’installation de la variable [!DNL Data Connection] extension . Les données des enregistrements de profil sont envoyées à Adobe Experience Platform.

## Enregistrement de profil

Les mises à jour des enregistrements de profil sont disponibles dans l’Experience Platform lorsqu’un nouveau profil est créé, mis à jour ou supprimé.

### Données collectées à partir de l’enregistrement de profil

La section suivante décrit les données capturées pour un enregistrement de profil.

| Champ | Description |
|---|---|
| `channel` | Contient des informations sur la source des données. Les deux `_id` et `_type` contain [valeurs d’espace de noms](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | L’identifiant unique du canal, tel que `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifie la source des données de canal, telles que `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `person` | Contient des informations sur le client. |
| `person.name` | Contient des informations sur le nom du client. |
| `person.name.firstName` | Contient le prénom du client. |
| `person.name.lastName` | Contient le nom du client. |
| `person.birthDate` | Date de naissance de l’acheteur. |
| `personalEmail` | Adresse électronique personnelle. |
| `personalEmail.address` | L’adresse technique, par exemple : `name@domain.com` comme généralement défini dans la norme RFC2822 et les normes ultérieures. |
| `userAccount` | Indique les détails de fidélité, les préférences, les processus de connexion et d’autres préférences de compte. |
| `userAccount.startDate` | Date de création du profil. |

>[!NOTE]
>
>Chaque enregistrement de profil inclut également la variable [`identityMap`](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html) qui inclut l’adresse électronique de l’acheteur, le cas échéant, et l’ECID.

Découvrez comment [création d’un schéma spécifique à l’enregistrement de profil](profile-data.md) qui peuvent ingérer les données de vos enregistrements de profil.
