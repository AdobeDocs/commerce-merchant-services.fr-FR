---
title: Emplacement du magasin et configuration du système de mappage
description: Configurez un fournisseur de distance pour prendre en charge le mappage de l’emplacement du magasin dans l’interface utilisateur de storefront. Les solutions d’exécution de magasin nécessitent un fournisseur de distance pour activer la recherche de magasin de détail, ainsi que d’autres fonctionnalités de mappage et de planification pour le workflow d’exécution de bout en bout.
role: Admin
level: Intermediate
feature: Shipping/Delivery, Integration, Tools and External Services, Configuration
exl-id: d09c4652-e2eb-49dc-8c42-2aa9b6be5d6b
source-git-commit: 37380063242b6d904910be731b8e58471625e9cb
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 0%

---

# Configuration de l’emplacement et du mappage du magasin

Activez les fonctionnalités d’emplacement et de mappage du magasin pour l’exécution du magasin en configurant un [fournisseur de distance](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/configuration/distance-priority-algorithm) pour rechercher des emplacements de magasin de détail.

**Exigences**

Pendant le processus de configuration, vous fournissez une clé d’API Google pour la plateforme Google Maps. Si vous n&#39;en avez pas, [générez-en un à partir de la plateforme Google Maps](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/configuration/distance-priority-algorithm#configure-google-maps).

Pour configurer le fournisseur de distance :

1. À partir de la configuration **[!UICONTROL Stores > General]** de l’Admin, ajoutez l’intégration Google Maps pour le type de contenu Map .

   - Accédez à **[!UICONTROL Stores > Configuration  > General > Content Management]**.

   - Ajoutez votre clé API Google au champ **[!UICONTROL Google Maps API Key]**.

1. Dans la configuration **[!UICONTROL Stores > Inventory]** de l’administrateur, sélectionnez le fournisseur de distance pour l’exécution du magasin.

   - Accédez à **[!UICONTROL Stores > Configuration > Catalog > Inventory]**.

   - Développez la section **[!UICONTROL Distance Provider for Distance Based SSA]** .

   - Définissez le **Provider** sur **Google Map**.

1. Configurez les paramètres pour le **[!UICONTROL Google Distance Provider]**.

   - Ajoutez votre **clé d’API Google**.

   - Définissez **[!UICONTROL Computation Mode]** sur `Driving` et **[!UICONTROL Value]** sur `Distance`
