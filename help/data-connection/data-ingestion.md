---
title: Types de données Commerce
description: Découvrez les types de données que vous pouvez collecter et envoyer à l’Experience Platform.
role: Admin, Developer
feature: Personalization, Integration
exl-id: 1cdf3fcb-fb16-47ef-be5c-0ebbf1feaff4
source-git-commit: d5d5741442973d86a2d403edc940d18333defd67
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# Types de données Commerce

L’ [ extension de connexion aux données](overview.md) connecte vos données Commerce à l’Experience Platform. Les données destinées à être utilisées dans l’Experience Platform sont regroupées en deux types de comportement : les données de série temporelle, qui appartiennent à la classe **Experience Event** et les données d’enregistrement, qui appartiennent à la classe **Individual Profile**.

En savoir plus sur [le comportement des données](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html#data-behaviors) et [les classes](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html#class) en Experience Platform.

## Données de série temporelle

Les données de série temporelle fournissent un instantané du système au moment où une action a été entreprise, directement ou indirectement, par un sujet enregistré. Par exemple, lorsqu’un acheteur navigue sur un produit de votre site, ajoute un produit à son panier, commande, etc. Les données de série temporelle sont ingérées dans l’Experience Platform à l’aide d’un schéma dont la classe est définie sur **Experience Event**.

### Données de série temporelle capturées

Voir [événements comportementaux](events.md) et [événements administratifs](events-backoffice.md) pour savoir quelles données sont capturées lorsqu’un événement de série temporelle est généré.

### Schéma nécessaire pour ingérer des données d’événement de série temporelle

Découvrez comment [créer un schéma](update-xdm.md) qui peut ingérer des données d’événement de série temporelle comportementale et de back-office.

## Enregistrer les données

Les données d’enregistrement fournissent des informations sur les attributs d’un sujet. Un sujet peut être une organisation ou un individu. Par exemple, un acheteur sur votre site crée un compte et génère des données d’enregistrement. Ces données sont ingérées dans l’Experience Platform à l’aide d’un schéma dont la classe est définie sur **Individual Profile**. Vous pouvez envoyer ces données d’enregistrement au service de gestion et de segmentation des profils d’Adobe : [Real-Time CDP](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/intro/rtcdp-intro/overview.html?lang=fr).

### Données d’enregistrement de profil capturées

Voir [données d’enregistrement de profil client](events-profilerecord.md) pour savoir quelles données sont capturées lorsqu’un enregistrement de profil est généré.

### Schéma nécessaire pour ingérer des données d’enregistrement de profil

Découvrez comment [créer un schéma](profile-data.md) qui peut ingérer des données d’enregistrement de profil.
