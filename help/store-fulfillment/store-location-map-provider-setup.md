---
title: Emplacement du magasin et configuration du système de mappage
description: Configurez un fournisseur de distance pour prendre en charge le mappage de l’emplacement du magasin dans l’interface utilisateur de storefront.
role: User, Admin
level: Intermediate
source-git-commit: 4ea03b3be11056526adc42d875b1e26a24736d15
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---


# Configuration de l’emplacement et du mappage du magasin

Activez l’emplacement de magasin et les fonctionnalités de mappage pour l’exécution du magasin en configurant une [fournisseur de distance](https://docs.magento.com/user-guide/catalog/inventory-configure-distance-priority.html) pour rechercher des emplacements de magasins de détail.

**Conditions**

Pendant le processus de configuration, vous fournissez une clé d’API Google pour la plateforme Google Maps. Si vous n’en avez pas, [en générer un à partir de la plateforme Google Maps](https://docs.magento.com/user-guide/catalog/inventory-configure-distance-priority.html#configure-google-maps).

Pour configurer le fournisseur de distance :

1. Dans la [!UICONTROL Stores > General] dans Admin, ajoutez l’intégration Google Maps pour le type de contenu Map .

   - Accédez à **[!UICONTROL Stores > Configuration  > General > Content Management]**.

   - Ajoutez votre clé API Google à **[!UICONTROL Google Maps API Key]** champ .

1. Dans la [!UICONTROL Stores > Inventory] dans Admin, sélectionnez le fournisseur de distance pour l’exécution du magasin.

   - Accédez à **[!UICONTROL Stores > Configuration > Catalog > Inventory]**.

   - Développez l’objet **[!UICONTROL Distance Provider for Distance Based SSA]** .

   - Définissez la variable **Fournisseur** to **Carte Google**.

1. Configurez les paramètres de la variable **[!UICONTROL Google Distance Provider]**.

   - Ajoutez vos **Clé API Google**.

   - Définir **[!UICONTROL Computation Mode]** to `Driving` et **[!UICONTROL Value]** to `Distance`

