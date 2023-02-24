---
title: Emplacement du magasin et configuration du système de mappage
description: Configurez un fournisseur de distance pour prendre en charge le mappage de l’emplacement du magasin dans l’interface utilisateur de storefront. Les solutions d’exécution de magasin nécessitent un fournisseur de distance pour activer la recherche de magasin de détail et d’autres fonctionnalités de mappage et de planification pour le workflow d’exécution de bout en bout.
role: User, Admin
level: Intermediate
exl-id: d09c4652-e2eb-49dc-8c42-2aa9b6be5d6b
source-git-commit: 4c10ab59ed304002cfde7398762bb70b223180ce
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---

# Configuration de l’emplacement et du mappage du magasin

Activez l’emplacement de magasin et les fonctionnalités de mappage pour l’exécution du magasin en configurant une [fournisseur de distance](https://docs.magento.com/user-guide/catalog/inventory-configure-distance-priority.html) pour rechercher des emplacements de magasins de détail.

**Conditions**

Pendant le processus de configuration, vous fournissez une clé d’API Google pour la plateforme Google Maps. Si vous n’en avez pas, [en générer un à partir de la plateforme Google Maps](https://docs.magento.com/user-guide/catalog/inventory-configure-distance-priority.html#configure-google-maps).

Pour configurer le fournisseur de distance :

1. Dans la **[!UICONTROL Stores > General]** dans Admin, ajoutez l’intégration Google Maps pour le type de contenu Map .

   - Accédez à **[!UICONTROL Stores > Configuration  > General > Content Management]**.

   - Ajoutez votre clé API Google à **[!UICONTROL Google Maps API Key]** champ .

1. Dans la **[!UICONTROL Stores > Inventory]** dans Admin, sélectionnez le fournisseur de distance pour l’exécution du magasin.

   - Accédez à **[!UICONTROL Stores > Configuration > Catalog > Inventory]**.

   - Développez l’objet **[!UICONTROL Distance Provider for Distance Based SSA]** .

   - Définissez la variable **Fournisseur** to **Carte Google**.

1. Configurez les paramètres de la variable **[!UICONTROL Google Distance Provider]**.

   - Ajoutez vos **Clé API Google**.

   - Définir **[!UICONTROL Computation Mode]** to `Driving` et **[!UICONTROL Value]** to `Distance`
