---
title: Configuration de la boutique marchande
description: 'Configurez des sources Inventory management améliorées en tant que magasins marchands. '
role: User, Admin
level: Intermediate
source-git-commit: 4ea03b3be11056526adc42d875b1e26a24736d15
workflow-type: tm+mt
source-wordcount: '1209'
ht-degree: 0%

---

# Configuration des magasins marchands (source)

Cette solution améliore les fonctionnalités natives d’Inventory management en étendant les sources de stock avec des fonctionnalités orientées sur les opérations pour les commerçants.

- Ajout des coordonnées géographiques de l’emplacement du magasin
- Désigner la source en tant que [!DNL Store Pickup Location] et spécifier les capacités d’expédition disponibles (navire à stocker, navire à partir du magasin).
- Spécifiez les options de sélection disponibles (en magasin ou côté serveur), des instructions de sélection personnalisées et d’autres informations pour communiquer les détails et les instructions de sélection aux clients.

Les termes _source_ et _emplacement du magasin marchand_ sont interchangeables. Tous les enregistrements sont des sources d’inventaire, mais les sources peuvent également être des emplacements de magasin marchand, selon les paramètres de configuration.

Gérer la configuration des magasins marchands depuis l’administrateur : **[!UICONTROL Stores > Inventory > Sources >  Edit Source]**.

>[!NOTE]
>
>Au cours du processus de configuration, il peut être nécessaire de vider le cache après avoir créé des sources ou mis à jour des sources existantes.

## **Général**

<table>
<tbody>
<tr>
<th>Champ</th>
<th>Description</th>
<th>Portée</th>
<th>Obligatoire</th>
</tr>
<tr>
<td><strong>[!UICONTROL Latitude]</strong></br><code>Base Attribute: latitude</code></td>
<td>Coordonnée latine de l’emplacement du magasin marchand. Ces informations requises sont utilisées dans la recherche d’emplacement et l’emplacement des cartes sur l’expérience storefront. La valeur doit correspondre à l’adresse exacte du magasin pour être validée.</td>
<td>Global</td>
<td>Oui</td>
</tr>
<tr>
<td><strong>[!UICONTROL Longitude]</strong></br><code>Base Attribute: Longitude</code></td>
<td>Coordonnée longitude l’emplacement du magasin marchand. Ces informations requises sont utilisées dans la recherche d’emplacement et l’emplacement des cartes sur l’expérience storefront. La valeur doit correspondre à l’adresse exacte du magasin pour être validée.</td>
<td>Global</td>
<td>Oui</td>
</tr>
<tr>
<td><strong>[!UICONTROL Use as Pickup Location]</br></strong><code>Base Attribute: is_pickup_location_active</code></td>
<td>Désignez la source comme emplacement de collecte de magasin disponible. Ce paramètre détermine si la source est synchronisée et affichée pour les visiteurs.</td>
<td>Global</td>
<td>Non</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Ship to Store]</strong><br><code>Extension Attribute: allow_ship_to_store</code></td>
<td>Configurez les fonctionnalités de livraison à stockage au niveau de la source. Pour plus d’informations, voir l’option [Configuration générale] (enable-general.md), <strong>[!UICONTROL Enable Ship To Store]
</tr>
<tr>
<td><strong>[!UICONTROL Latitude]</strong></br><code>Base Attribute: latitude</code></td>
<td>Coordonnée latine de l’emplacement du magasin marchand. Ces informations requises sont utilisées dans la recherche d’emplacement et l’emplacement des cartes sur l’expérience storefront. La valeur doit correspondre à l’adresse exacte du magasin pour être validée.</td>
<td>Global</td>
<td>Oui</td>
</tr>
<tr>
<td><strong>[!UICONTROL Longitude]</strong></br><code>Base Attribute: Longitude</code></td>
<td>Coordonnée longitude l’emplacement du magasin marchand. Ces informations requises sont utilisées dans la recherche d’emplacement et l’emplacement des cartes sur l’expérience storefront. La valeur doit correspondre à l’adresse exacte du magasin pour être validée.</td>
<td>Global</td>
<td>Oui</td>
</tr>
<tr>
<td><strong>[!UICONTROL Use as Pickup Location]</br></strong><code>Base Attribute: is_pickup_location_active</code></td>
<td>Désignez la source comme emplacement de collecte de magasin disponible. Ce paramètre détermine si la source est synchronisée et affichée pour les visiteurs.</td>
<td>Global</td>
<td>Non</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Ship to Store]</strong></br> <code>Extension Attribute: [!DNL allow_ship_to_store]</code></td>
<td>Configurez les fonctionnalités de livraison à stockage au niveau de la source. Pour plus d’informations, voir l’option [Configuration générale] (enable-general.md), <strong>[!UICONTROL Enable Ship To Store]</strong>.</td>
<td>Global</td>
<td>Non</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Ship From Store]</strong></br><code>Extension Attribute: [!DNL use_as_shipping_source]</code></td>
 <td>Configurez les fonctionnalités d’expédition à partir du magasin au niveau de la source. Pour plus d’informations, voir l’option [Configuration générale] (enable-general.md), [!UICONTROL Enable Ship From Store].</td>
<td>Global</td>
<td>Non</td>
</tr>
<tr>
<td>Global</td>
<td>Non</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Ship From Store]</strong><code>Extension Attribute: [!DNL use_as_shipping_source]</code></td><td></td><td></td><td></td></tr></tbody></table>



| **Champ** | **Description** | **Portée** | **Obligatoire** |
|--------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Latitude]**</br>`Base Attribute: latitude` | Coordonnée latine de l’emplacement du magasin marchand. Ces informations requises sont utilisées dans la recherche d’emplacement et l’emplacement des cartes sur l’expérience storefront. La valeur doit correspondre à l’adresse exacte du magasin pour être validée. | Global | Oui |
| **[!UICONTROL Longitude]**</br>`Base Attribute: Longitude` | Coordonnée longitude l’emplacement du magasin marchand. Ces informations requises sont utilisées dans la recherche d’emplacement et l’emplacement des cartes sur l’expérience storefront. La valeur doit correspondre à l’adresse exacte du magasin pour être validée. | Global | Oui |
| **[!UICONTROL Use as Pickup Location]**</br>`Base Attribute:[!DNL is_pickup_location_active]` | Désignez la source comme emplacement de collecte de magasin disponible. Ce paramètre détermine si la source est synchronisée et affichée pour les visiteurs. | Global | Non |
| **[!UICONTROL Enable Ship to Store]**</br>`Extension Attribute: [!DNL allow_ship_to_store]` | Configurez les fonctionnalités de livraison à stockage au niveau de la source. Pour plus d’informations, voir [Configuration générale](enable-general.md) option, **[!UICONTROL Enable Ship To Store]**. | Global | Non |
| **[!UICONTROL Enable Ship From Store]**</br>`Extension Attribute: [!DNL use_as_shipping_source]` | Configurez les fonctionnalités d’expédition à partir du magasin au niveau de la source. Pour plus d’informations, voir [Configuration générale](enable-general.md) option, [!UICONTROL Enable Ship From Store] | Global | Non |

{style=&quot;table-layout:auto&quot;}

## Configuration de l’emplacement de collecte

| **Champ** | **Description** | **Portée** | **Obligatoire** |
|-----------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Allow In-Store Pickup]**</br>`Extension Attribute: [!DNL store_pickup_enabled]` | L’une des deux options de sélection. [!DNL In-Store Pickup] fait référence à la possibilité pour un client d’accéder à l’emplacement de la boutique du commerce pour récupérer sa commande. </br></br>Lorsqu’elle est activée, cette option peut être présentée au client lors de l’extraction. </br></br>Cette option remplace également la configuration globale par [!UICONTROL Enable In-store Pickup] qui a été configuré sur le [!UICONTROL Delivery Method] pour [!UICONTROL In-store Pickup] | Global | Non |
| **Instructions de récupération en magasin**</br>`Extension Attribute: store_pickup_instructions` | Un message personnalisable remis au client dans la variable **Commande prête à être récupérée en magasin** notification électronique. | Global | Non |
| **Allow Curbside**</br>`Extension Attribute: curbside_enabled` | L’une des deux options de sélection. La livraison en ville permet à un client de garer son véhicule à un endroit désigné dans le magasin marchand. Dans ce scénario, la commande est diffusée au client par un associé du magasin. </br></br>Lorsqu’elle est activée, cette option peut être présentée au client lors de son passage en caisse. Il se peut également que le client soit invité à décrire son véhicule et sa place de parking au cours du processus d’archivage. </br></br>Cette option remplace également la configuration globale par **Activation de la collecte côté serveur** qui a été configuré sur le **Méthode de diffusion** pour **Collecte en magasin** | Global | Non |
| **[!UICONTROL Curbside Instructions]**</br>`Extension Attribute: curbside_instructions` | Un message personnalisable remis au client dans la variable [!UICONTROL Order Ready For Pickup in Store] notification électronique. | Global | Non |
| **[!UICONTROL Estimated Pickup Lead Time]**</br>`Extension Attribute: pickup_lead_time` | Nombre de minutes nécessaires avant la réception d’une commande, la sélection et la préparation à la récupération. </br></br>Ces informations sont utilisées pour l’affichage d’une estimation des heures pour la récupération de commande auprès des clients sur le site web.</br></br> La définition de cette option remplace la configuration globale pour **Délai d’avance estimé pour la collecte** configuré pour le **Méthode de diffusion** dans le **Collecte en magasin** configuration. | Global | Non |
| **[!UICONTROL Estimated Pickup Time Label]**</br>`Extension Attribute: pickup_time_label` | Libellé qui affiche le nombre de minutes jusqu’à ce qu’une commande soit prête à être sélectionnée.</br></br> Lors de la personnalisation de ce libellé, vous pouvez utiliser le code %1 pour insérer votre **Délai d’avance estimé pour la collecte**.</br></br> La définition de cette option remplace la configuration globale pour [!UICONTROL Estimated Pickup Time Label] configuré pour le [!UICONTROL Delivery Method] dans le [!UICONTROL In-store Pickup]. | Global | Non |

### **Heures d’ouverture**

| **Champ** | **Description** | **Portée** | **Obligatoire** |
|------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Location Timezone]**</br>`Extension Attribute: timezone` | Fuseau horaire de l’emplacement du magasin marchand. Pour chaque jour, définissez les heures d’ouverture et de fermeture.</br></br>Ces paramètres sont utilisés pour optimiser les temps de récupération estimés et dans les rapports du service d’exécution. | Global | Oui |
| **[!UICONTROL Opening Hours]**</br>`Internal Attribute: inventory_source_opening_hours_dynamic_rows` | Heures d’ouverture de l’emplacement du magasin marchand. </br></br>Ces informations peuvent être utilisées pour optimiser les temps de récupération estimés et dans les rapports du service d’exécution. | Global | Oui |

### Configuration des options de l’interface d’archivage



| **Champ** | **Description** | **Portée** | **Obligatoire** |
|---------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Use Parking Spots]**</br>`Extension Attribute: parking_spots_enabled` | Indiquez si l’emplacement du magasin marchand comporte des places de parking désignées pour le ramassage côté serveur. </br></br>Lorsque cette option est activée, vous pouvez configurer les emplacements de stationnement disponibles. | Global | Non |
| **[!UICONTROL Is Parking Spot a Mandatory Field?]**</br>`Extension Attribute: parking_spot_mandatory` | Indiquez si l’identification de la place de parking est requise pour les clients lors de l’expérience d’achat.</br></br>Si cette option est activée, le client est invité à spécifier sa place de parking à son arrivée. Si cette option est désactivée, le client peut ignorer cette entrée. | Global | Non |
| **[!UICONTROL Parking Spots List]**</br> `Internal Attribute: inventory_source_parking_spot_dynamic_rows` | Les places de stationnement disponibles dans ce magasin marchand pour le ramassage en bordure. Utilisez l’interface fournie pour nommer chaque point.</br></br> Il n&#39;est pas nécessaire de nommer toutes les places de parking, seulement les emplacements prévus pour le trottoir. Par exemple, les lignes A à G du stationnement sont disponibles, mais seules les 8 premières places de la ligne A sont désignées pour le nettoyage du bord du trottoir. Dans ce scénario, vous pouvez définir 8 emplacements ; ex : A1, A2, A3, etc. | Global | Non |
| **[!UICONTROL Allow "Other" Parking Spot Field]**</br>`Extension Attribute: custom_parking_spot_enabled` | Lorsqu’il est activé, ce paramètre permet au client de décrire sa place de parking pendant l’archivage. | Global | Non |
| **[!UICONTROL Use Car Color]**</br>`Extension Attribute: use_car_color` | Indiquez si le client doit prendre en charge la collecte de la couleur du véhicule lors de l’archivage. </br></br> Les sélections disponibles pour [!UICONTROL Car Color] sont configurés dans la section Admin [Paramètres système de l’expérience d’archivage](check-in-experience-setup.md). | Global | Non |
| **[!UICONTROL Is Car Color a Mandatory Field?]**</br>`Extension Attribute: car_color_mandatory` | Indiquez si l’identification des couleurs du véhicule est requise pour les clients lors de l’archivage.</br></br>Si cette option est activée, le client est invité à spécifier la couleur de son véhicule à son arrivée. Si cette option est désactivée, le client peut ignorer cette entrée. | Global | Non |
| **[!UICONTROL Use Car Make]** </br>`Extension Attribute: use_car_make` | Indiquez si le client doit prendre en charge la collecte des véhicules effectués lors de l’archivage.</br></br> Les sélections disponibles pour [!UICONTROL Car Make] sont configurés dans la section Admin [Paramètres système de l’expérience d’archivage](check-in-experience-setup.md). | Global | Non |
| **[!UICONTROL Is Car Make a Mandatory Field?]**</br>`Extension Attribute: car_make_mandatory` | Indiquez si les identifiants de marque de véhicule sont requis pour les clients lors de l’archivage.</br></br>Si cette option est activée, le client est invité à indiquer la marque de son véhicule à son arrivée. Si cette option est désactivée, le client peut ignorer cette entrée. | Global | Non |
| **[!UICONTROL Use Additional Information]**</br> `Extension Attribute: use_additional_information` | Indiquez si vous souhaitez prendre en charge la collecte d’informations supplémentaires auprès du client lors de l’archivage. | Global | Non |
| **[!UICONTROL Is Additional Information a Mandatory Field?]**</br>`Extension Attribute: additional_information_mandatory` | Indiquez si des informations supplémentaires sont requises pour les clients lors de l’archivage. </br></br>Si cette option est activée, le client est invité à saisir des informations supplémentaires à son arrivée. Si cette option est désactivée, le client peut ignorer cette entrée. | Global | Non |







