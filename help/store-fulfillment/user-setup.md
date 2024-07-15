---
title: Configuration de l’utilisateur
description: Configurez des sources Inventory management améliorées en tant que boutiques de commerce pour prendre en charge la solution d’exécution de magasin pour Adobe Commerce.
role: Admin, Developer
level: Intermediate
feature: Shipping/Delivery, User Account, Tools and External Services
exl-id: eb735bef-c339-4d0b-b3e7-10328915725b
source-git-commit: 36b57648e156ead801764f3ee4e5e6a0f3245fe6
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# Configuration de l’utilisateur

Application d’aide à la boutique Les utilisateurs sont gérés dans Adobe Commerce. Toutefois, ces utilisateurs n’interagissent pas directement avec Adobe Commerce. La gestion des utilisateurs est configurée dans Adobe Commerce pour activer les connexions sécurisées entre Adobe Commerce et l’application.

Le modèle utilisateur de l’application d’exécution de magasin est séparé des autres modèles d’utilisateur Adobe Commerce. L’application conserve son propre modèle d’autorisation par le biais de rôles utilisateur et d’utilisateurs pouvant être affectés à tous les emplacements ou à des emplacements spécifiques. Les autorisations suivantes sont prises en charge : Ordre de sélection, Ordre de remise et Réduction de la quantité d’articles (et annulation).

>[!TIP]
>
>Pour de meilleurs résultats, [configurez votre connexion](connect-set-up-service.md) avant d’ajouter des utilisateurs et des autorisations pour les associés au magasin qui utilisent l’application d’aide au magasin.

## Application d’assistance de la boutique - Rôles utilisateur

Lors de la configuration initiale de l’utilisateur pour l’application d’aide à la boutique, créez des rôles d’utilisateur pour personnaliser les autorisations d’utilisateur sur l’application d’aide à la boutique. Par exemple, vous pouvez créer différents rôles pour les gestionnaires de magasins et les associés de magasin et affecter différentes ressources de rôles pour gérer les autorisations pour chaque type d’utilisateur.

Configurez les rôles utilisateur de **[!UICONTROL System > Store Fulfillment App Permissions > All Store Fulfillment App Users]**.

### Infos sur le rôle

| **Field** | **Description** | **Portée** | **Obligatoire** |
|----------------------------|-------------------------|-----------|--------------|
| **[!UICONTROL Role Name]** | Activez ou désactivez l’utilisateur. | Global | Oui |

### Ressources de rôle

| **Field** | **Description** | **Portée** | **Obligatoire** |
|----------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Resource Access]** | Répertorie les groupes d’autorisations disponibles pouvant être affectés à un rôle d’utilisateur. Actuellement, la solution d’exécution de magasin n’a pas de niveaux d’autorisation différents définis pour les rôles de ressources. Tous les rôles utilisateur ont le même accès aux ressources. | Global | Oui |

## Aide de la boutique - Informations sur l’utilisateur

Gérez les profils utilisateur de l’application d’assistance de la boutique à partir des paramètres du système d’administration : **[!UICONTROL System > Store Fulfillment App Permissions > All Store Fulfillment App Users]**.

| **Field** | **Description** | **Portée** | **Obligatoire** |
|------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL is Active]** | Activez ou désactivez l’utilisateur. | Global | Oui |
| **[!UICONTROL User Name]** | Nom d’utilisateur associé à l’utilisateur | Global | Oui |
| **[!UICONTROL First Name]** | Prénom associé à l’utilisateur | Global | Non |
| **[!UICONTROL Last Name]** | Nom associé à l’utilisateur | Global | Non |
| **[!UICONTROL Role]** | Rôle associé à l’utilisateur | Global | Non |
| **[!UICONTROL Access to all locations]** | Attribuez aux utilisateurs l’accès à tous les magasins ou sélectionnez des magasins individuellement. | Global | Non |
| **Paramètre régional de l’interface** | Si votre boutique comporte plusieurs langues, définissez Paramètres régionaux de l’interface sur la langue à utiliser pour l’interface d’administration. | Global | Non |
| **Actif À Partir De** | Pour définir une date de début, cliquez sur l&#39;icône de calendrier. | Global | Non |
| **Actif À** | Définissez la Date d’expiration en cliquant sur l’icône de calendrier. La définition d’une date d’expiration est utile pour configurer des affectations temporaires d’utilisateurs ou de rôles. Après la date d’expiration, l’état du compte utilisateur passe à `Inactive`, mais le compte peut toujours être mis à jour si nécessaire. | Global | Non |
