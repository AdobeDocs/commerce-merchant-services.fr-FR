---
title: Enregistrements de profil
description: Découvrez les données capturées par un enregistrement de profil.
role: Admin, Developer
feature: Personalization, Integration, Eventing
exl-id: bd04730d-e37a-48a9-822b-0f4aa68a4651
source-git-commit: c02496fb3f88f4781b79c5e477d5508c3e3d5224
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# [!DNL Data Connection] Enregistrements de profil (Beta)

La section suivante décrit les données d’enregistrement de profil Commerce disponibles lors de l’installation de l’extension [!DNL Data Connection]. Les données des enregistrements de profil sont envoyées à Adobe Experience Platform.

## Enregistrement de profil

Les mises à jour des enregistrements de profil sont disponibles dans l’Experience Platform lorsqu’un nouveau profil est créé, mis à jour ou supprimé.

### Données collectées à partir de l’enregistrement de profil

La section suivante décrit les données capturées pour un enregistrement de profil.

| Champ | Description |
|---|---|
| `channel` | Contient des informations sur la source des données. `_id` et `_type` contiennent tous deux [ espaces de noms ](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/namespaces). |
| `channel._id` | L’identifiant unique du canal, tel que `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifie la source des données de canal, telles que `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `person` | Contient des informations sur le client. |
| `person.name` | Contient des informations sur le nom du client. |
| `person.name.firstName` | Contient le prénom du client. |
| `person.name.lastName` | Contient le nom du client. |
| `person.birthDate` | Date de naissance de l’acheteur. |
| `personalEmail` | Adresse électronique personnelle. |
| `personalEmail.address` | Adresse technique, par exemple, `name@domain.com` telle que généralement définie dans la norme RFC2822 et les normes ultérieures. |
| `billingAddress` | Adresse postale de facturation. |
| `billingAddress.street1` | Informations au niveau de la rue par Principal, numéro d’appartement, numéro de rue et nom de rue. |
| `billingAddress.street2` | Informations facultatives sur la rue, deuxième ligne. |
| `billingAddress.city` | Nom de la ville. |
| `billingAddress.state` | Nom de l’état. C&#39;est un champ de forme libre. |
| `billingAddress.country` | Nom du territoire administré par le gouvernement. À l’exception de `xdm:countryCode`, il s’agit d’un champ de forme libre qui peut avoir le nom du pays dans n’importe quelle langue. |
| `billingAddress.primary` | Indique s’il s’agit de l’adresse de facturation principale. La valeur est toujours `False`. |
| `billingAddressPhone` | Numéro de téléphone associé à l’adresse de facturation. |
| `billingAddressPhone.number` | Numéro de téléphone. Notez que le numéro de téléphone est une chaîne qui peut contenir des caractères significatifs tels que des crochets `()`, des tirets `-` ou des caractères pour indiquer des identifiants de sous-numérotation comme des extensions `x`, par exemple `1-353(0)18391111` ou `+613 9403600x1234`. |
| `billingAddressPhone.primary` | Indique s’il s’agit du numéro de téléphone principal de l’adresse de facturation. La valeur est toujours `False`. |
| `shippingAddress` | Adresse postale de l’expédition. |
| `shippingAddress.street1` | Informations au niveau de la rue par Principal, numéro d’appartement, numéro de rue et nom de rue. |
| `shippingAddress.street2` | Informations facultatives sur la rue, deuxième ligne. |
| `shippingAddress.city` | Nom de la ville. |
| `shippingAddress.state` | Nom de l’état. C&#39;est un champ de forme libre. |
| `shippingAddress.country` | Nom du territoire administré par le gouvernement. À l’exception de `xdm:countryCode`, il s’agit d’un champ de forme libre qui peut avoir le nom du pays dans n’importe quelle langue. |
| `shippingAddress.primary` | Indique s’il s’agit de l’adresse de livraison principale. La valeur est toujours `False`. |
| `shippingAddressPhone` | Numéro de téléphone associé à l’adresse de livraison. |
| `shippingAddressPhone.number` | Numéro de téléphone. Notez que le numéro de téléphone est une chaîne qui peut contenir des caractères significatifs tels que des crochets `()`, des tirets `-` ou des caractères pour indiquer des identifiants de sous-numérotation comme des extensions `x`, par exemple `1-353(0)18391111` ou `+613 9403600x1234`. |
| `shippingAddressPhone.primary` | Indique s’il s’agit du numéro de téléphone principal de l’adresse de livraison. La valeur est toujours `False`. |
| `userAccount` | Indique les détails de fidélité, les préférences, les processus de connexion et d’autres préférences de compte. |
| `userAccount.startDate` | Date de création du profil. |

>[!NOTE]
>
>Chaque enregistrement de profil inclut également le champ [`identityMap`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/identitymap), qui inclut l’identifiant client Commerce généré par le système comme identifiant principal du profil et un identifiant de courrier électronique utilisé comme identifiant secondaire.

Découvrez comment [créer un schéma spécifique à l’enregistrement de profil](profile-data.md) qui peut ingérer les données de vos enregistrements de profil.
