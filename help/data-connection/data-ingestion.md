---
title: Types de données commerciales
description: Découvrez les types de données que vous pouvez collecter et envoyer à l’Experience Platform.
role: Admin, Developer
feature: Personalization, Integration
source-git-commit: 99d1097b98ea18c8a317613b2366a97db131432f
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# Types de données commerciales

La variable [Extension Data Connection](overview.md) connecte vos données Commerce à l’Experience Platform. Les données destinées à être utilisées dans l’Experience Platform sont regroupées en deux types de comportement : les données de série temporelle, qui appartiennent au **Événement d’expérience** et les données d’enregistrement qui appartiennent à la variable **Profil individuel** classe .

En savoir plus sur [comportement des données](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html#data-behaviors) et [classes](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html#class) dans Experience Platform.

## Données de série temporelle

Les données de série temporelle fournissent un instantané du système au moment où une action a été entreprise, directement ou indirectement, par un sujet enregistré. Par exemple, lorsqu’un acheteur navigue sur un produit de votre site, ajoute un produit à son panier, commande, etc. Les données de série temporelle sont ingérées dans l’Experience Platform à l’aide d’un schéma dont la classe est définie sur **Événement d’expérience**.

### Données de série temporelle capturées

Voir [événements comportementaux](events.md) et [événements back office](events-backoffice.md) pour savoir quelles données sont capturées lorsqu’un événement de série temporelle est généré.

### Schéma nécessaire pour ingérer des données d’événement de série temporelle

Découvrez comment [création d’un schéma](update-xdm.md) qui peut ingérer des données d’événement de série temporelle comportementale et de back-office.

## Enregistrer les données

Les données d’enregistrement fournissent des informations sur les attributs d’un sujet. Un sujet peut être une organisation ou un individu. Par exemple, un acheteur sur votre site crée un compte et génère des données d’enregistrement. Ces données sont ingérées dans l’Experience Platform à l’aide d’un schéma dont la classe est définie sur **Profil individuel**. Vous pouvez envoyer ces données d’enregistrement au service de gestion des profils et de segmentation d’Adobe : [Real-Time CDP](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/intro/rtcdp-intro/overview.html?lang=fr).

### Données d’enregistrement de profil capturées

Voir [données d’enregistrement du profil client](events-profilerecord.md) pour savoir quelles données sont capturées lors de la génération d’un enregistrement de profil.

### Schéma nécessaire pour ingérer des données d’enregistrement de profil

Découvrez comment [création d’un schéma](profile-data.md) qui peuvent ingérer des données d’enregistrement de profil.
