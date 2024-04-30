---
title: Enregistrements de profil
description: Découvrez les données capturées par un enregistrement de profil.
role: Admin, Developer
feature: Personalization, Integration, Eventing
exl-id: bd04730d-e37a-48a9-822b-0f4aa68a4651
source-git-commit: 89607d22ba8e69e0c98fce97e041022e33d01c07
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# [!DNL Data Connection] Enregistrements de profil (bêta)

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
| `billingAddress` | Adresse postale de facturation. |
| `billingAddress.street1` | Informations au niveau de la rue par Principal, numéro d’appartement, numéro de rue et nom de rue. |
| `billingAddress.street2` | Informations facultatives sur la rue, deuxième ligne. |
| `billingAddress.city` | Nom de la ville. |
| `billingAddress.state` | Nom de l’état. C&#39;est un champ de forme libre. |
| `billingAddress.country` | Nom du territoire administré par le gouvernement. Autre que `xdm:countryCode`, il s’agit d’un champ de forme libre qui peut avoir le nom du pays dans n’importe quelle langue. |
| `billingAddressPhone` | Numéro de téléphone associé à l’adresse de facturation. |
| `billingAddressPhone.number` | Numéro de téléphone. Notez que le numéro de téléphone est une chaîne qui peut contenir des caractères significatifs tels que des crochets. `()`, traits d’union `-`ou les caractères pour indiquer des identifiants de sous-numérotation comme des extensions `x` par exemple,  `1-353(0)18391111` ou `+613 9403600x1234`. |
| `shippingAddress` | Adresse postale de l’expédition. |
| `shippingAddress.street1` | Informations au niveau de la rue par Principal, numéro d’appartement, numéro de rue et nom de rue. |
| `shippingAddress.street2` | Informations facultatives sur la rue, deuxième ligne. |
| `shippingAddress.city` | Nom de la ville. |
| `shippingAddress.state` | Nom de l’état. C&#39;est un champ de forme libre. |
| `shippingAddress.country` | Nom du territoire administré par le gouvernement. Autre que `xdm:countryCode`, il s’agit d’un champ de forme libre qui peut avoir le nom du pays dans n’importe quelle langue. |
| `shippingAddressPhone` | Numéro de téléphone associé à l’adresse de livraison. |
| `shippingAddressPhone.number` | Numéro de téléphone. Notez que le numéro de téléphone est une chaîne qui peut contenir des caractères significatifs tels que des crochets. `()`, traits d’union `-`ou les caractères pour indiquer des identifiants de sous-numérotation comme des extensions `x` par exemple,  `1-353(0)18391111` ou `+613 9403600x1234`. |
| `userAccount` | Indique les détails de fidélité, les préférences, les processus de connexion et d’autres préférences de compte. |
| `userAccount.startDate` | Date de création du profil. |

>[!NOTE]
>
>Chaque enregistrement de profil inclut également la variable [`identityMap`](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html) qui inclut l’ID de client Commerce généré par le système comme identifiant principal du profil et un ID d’adresse électronique utilisé comme identifiant secondaire.

Découvrez comment [création d’un schéma spécifique à l’enregistrement de profil](profile-data.md) qui peuvent ingérer les données de vos enregistrements de profil.
