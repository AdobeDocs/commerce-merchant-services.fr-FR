---
title: Configuration générale
description: Configuration des paramètres généraux à activer [!DNL Store Fulfillment] pour votre magasin. Configurez les paramètres d’extension globaux, les paramètres système pour la journalisation, la synchronisation des données et la sécurité. Fournissez des données clés pour activer l’intégration entre Adobe Commerce et les services d’exécution de magasin.
role: User, Admin
level: Intermediate
source-git-commit: 4ea03b3be11056526adc42d875b1e26a24736d15
workflow-type: tm+mt
source-wordcount: '2409'
ht-degree: 0%

---

# Configuration générale

Dans l’administrateur Adobe Commerce, configurez les paramètres de configuration généraux pour activer [!DNL Store Fulfillment] services pour votre magasin, configurez les paramètres d’extension globale et fournissez des données clés pour l’intégration en configurant la variable [!UICONTROL Account Credentials].

L’intégration doit être connectée au service d’exécution de magasin. Configurez également les paramètres généraux d’exécution de magasin pour activer et personnaliser les services d’exécution de magasin en fonction des fonctionnalités et des besoins opérationnels de votre entreprise.

La configuration générale pour [!DNL Store Fulfillment] inclut les paramètres de configuration suivants :

- [Activation de l’extension](#enable-the-extension)
- [Gérer les informations d’identification du compte pour se connecter aux services d’exécution de magasin](#account-credentials)
- [Configuration de la journalisation](#configure-logging)
- [Définition des options de gestion des opérations de [synchronisation des commandes]](#order-synchronization)
- [Activation des options d’expédition d’exécution de magasin](#enable-store-fullment-shipping-options)
- [Configuration des paramètres de sécurité et d’authentification pour l’application d’exécution de magasin](#store-fulfillment-app)
- [Définition de la disponibilité des méthodes de diffusion et de la configuration des messages](#in-store-delivery-methods)


## Activation de l’extension

| **Champ** | **Description** | **Portée** | **Obligatoire** |
|--------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Enabled]** | Activez ou désactivez la solution. Lorsque cette option est activée, configurez et utilisez les fonctionnalités d’exécution de magasin et établissez la connexion entre votre boutique Adobe Commerce et les services d’exécution de magasin. Lorsque cette option est désactivée, toutes les fonctions d’exécution de magasin sont désactivées et il n’existe aucune communication entre Adobe Commerce et les services d’exécution de magasin. Les informations de commande ne peuvent pas être traitées ni reçues. | Global | Oui |


Pour terminer cette configuration, voir **Magasins → Configuration → Services → Livraison des magasins par Walmart Commerce Technologies**.

## Ajout d’informations d’identification de compte



| **Champ** | **Description** | **Portée** | **Obligatoire** |
|----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Environment]** | Peut sélectionner *Sandbox* ou *Production*:</br> Sandbox communique avec les services d’exécution dans un test.</br>La production communique avec un environnement en ligne. Utilisation **only** en production.</br>Un ensemble d’informations d’identification vous est attribué pour chaque environnement et vous permet de gérer les deux ensembles dans la même installation. </br></br>Enregistrez les informations d’identification avant de valider la connexion. | Global | Oui |
| **[!UICONTROL API Server URL]** | URL du point d’entrée de l’API d’exécution de la boutique Walmart. Il doit s’agir d’une URL complète qui vous a été fournie au cours de votre processus d’intégration. Les clients d’exécution de magasin reçoivent à la fois un sandbox et une URL de production. Veillez à copier/coller l’URL complète, y compris la barre oblique &quot;/&quot; à la fin. | Global | Oui |
| **[!UICONTROL Token Auth Server URL]** | URL du point de terminaison de l’authentification de l’exécution de la boutique Walmart. La valeur doit être l’URL complète qui vous est fournie pendant votre processus d’intégration. Vous recevez à la fois une URL Sandbox et une URL de production. Veillez à copier/coller l’URL complète, y compris la barre oblique de fin. `/`&quot;. | Global | Oui |
| **[!UICONTROL Merchant Id]** | Votre identifiant de commerçant (client) unique fourni lors de votre processus d’intégration. Votre identifiant est utilisé pour acheminer vos commandes et vous assurer que vos magasins marchands les reçoivent. | Global | Oui |
| **[!UICONTROL Consumer Id]** | Votre identifiant d’intégration unique. Il vous est fourni pendant votre processus d’intégration. Ça ne change pas. Il est utilisé pour authentifier toutes les communications avec les services d’exécution. | Global | Oui |
| **[!UICONTROL Consumer Secret]** | Votre clé d’intégration unique. Il vous est fourni pendant votre processus d’intégration. Il est utilisé pour authentifier toutes les communications avec les services d’exécution. | Global | Oui |

Après avoir configuré les informations d’identification du compte, sélectionnez **[!UICONTROL Validate Credentials]** pour vérifier et établir une connexion au service web d’exécution pour la première fois.

## Configuration de la journalisation

Lorsque la journalisation est activée, votre fichier journal peut rapidement se développer. Pour éviter les problèmes de temps de réponse dans les environnements de production, veillez à activer la journalisation et activez uniquement pendant une courte période lorsque cela est nécessaire.

Demandez à l’administrateur système de configurer vos environnements pour autoriser la gestion des exceptions afin que les exceptions liées à l’API puissent être capturées via le pare-feu ou le cache. Vous pouvez également demander à votre administrateur système de configurer la rotation du journal sur ce fichier afin de réduire la taille.

| **Champ** | **Description** | **Portée** | **Obligatoire** |
|----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **Mode de débogage** | Le mode de débogage est utilisé pour augmenter l’activité consignée dans l’intégration. Lorsque cette option est désactivée, aucune information de débogage n’est consignée. Lorsque cette option est activée, toutes les informations de débogage sont consignées.</br> Toutes les données consignées se trouvent dans le fichier : `var/log/walmart-bopis.log` | Global | Non |

## Gestion de la synchronisation des commandes

Configurez les paramètres pour gérer la gestion des erreurs pour la synchronisation des commandes, les attributs de catalogue à utiliser pour l’analyse du code à barres lors du choix de la commande et configurez les tailles des lots de commandes pour la file d’attente d’exécution du magasin.

Vous pouvez afficher des détails sur les opérations de synchronisation des commandes à partir du tableau de bord Gestion des files d’attente d’exécution de magasin dans Admin (
**[!UICONTROL System > Tools > Store Fulfillment Queue]**).

### Gestion des erreurs de synchronisation

| **Champ** | **Description** | **Portée** | **Obligatoire** |
|-----------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------|--------------|
| **Réessayer l’erreur critique** | Indique les tentatives de reprise d’une opération de synchronisation d’enregistrement après une erreur critique.</br></br>Des erreurs critiques se produisent chaque fois que l’intégration ne parvient pas à obtenir une réponse positive de la part du service d’exécution. Cela peut se produire lorsque le service est en panne ou lorsqu’une erreur se produit dans les données de commande envoyées.</br></br>Lorsque le seuil de reprise est atteint, l’élément reste dans la file d’attente mais n’est pas traité à nouveau. Afficher tous les éléments contenant des erreurs de **[!UICONTROL System → Tools → Store Fulfillment Queue]** Gestion dans l’administrateur. Pour résoudre les problèmes liés aux éléments qui échouent constamment, contactez votre gestionnaire de compte. | Global | Non |
| **Activer le message de notification d’erreur** | Activez les notifications d’erreur pour recevoir un courrier électronique lorsque la variable [!UICONTROL Retry Critical Error Threshold] est atteinte pour une commande. La notification inclut tous les détails disponibles sur l’erreur. | Global | Non |
| **Envoyer un courrier électronique de notification d’erreur à** | Liste délimitée par des virgules d’adresses email des destinataires pour les notifications d’erreur. | Global | Non |
| **Modèle de courrier électronique d’exception de synchronisation des commandes** | Indique le modèle d’email utilisé pour avertir les destinataires des erreurs de synchronisation de commande. Un modèle par défaut est fourni. Il ne prend pas en charge la personnalisation. | Affichage en magasin | Non |

### Synchronisation des commandes

| **Champ** | **Description** | **Portée** | **Obligatoire** |
|--------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Barcode Source]** | L’attribut catalog qui stocke le code pouvant être analysé pour les éléments correspondants dans vos emplacements marchands.</br></br>Si vous n’avez qu’un seul emplacement commercial, il est probable que vous utilisiez des codes CUP, tandis que votre canal de commerce électronique identifie les produits par SKU. Si tel est votre scénario, sélectionnez l’attribut catalog qui contient le code UPC.</br></br>Ce paramètre garantit que les commandes envoyées à vos magasins marchands répertorient les éléments avec l’identifiant correct afin que les associés de magasins puissent analyser précisément les éléments pendant le processus de sélection.</br></br>Si vous n’êtes pas sûr, vérifiez auprès de vos associés d’exécution dans le service Expédition et sélection pour déterminer l’attribut à envoyer. Vous devrez peut-être ajouter l’attribut approprié au jeu d’attributs de produit Adobe Commerce si l’attribut n’est pas actuellement inclus dans la base de données. | Site Web | Oui |
| **[!UICONTROL Barcode Type]** | L’attribut catalog qui stocke la source du code à barres pour les éléments correspondants dans vos emplacements marchands.</br></br>Ce paramètre garantit que les commandes envoyées à vos magasins marchands répertorient les éléments avec un identifiant correct afin que les associés de magasins puissent analyser précisément les éléments pendant le processus de sélection. Les options incluent : SKU, UPC, GTIN, UPCA, EAN13, UPCE0, DISA, UAB, CODABAR, Price Embedded UPC.</br></br>Si vous n’êtes pas sûr, sélectionnez l’option qui ressemble le plus aux valeurs contenues dans votre [!UICONTROL Barcode Source] attribut. Les associés de magasin peuvent toujours faire correspondre des éléments manuellement à partir de leur liste de sélection. | Site Web | Oui |
| **[!UICONTROL Max Number of Items]** | Nombre maximal d’éléments à envoyer simultanément à partir de la file d’attente d’exécution du magasin.</br></br>Les commandes BOPIS sont envoyées par lots au service d’exécution, à intervalles réguliers. Ce paramètre vous permet de contrôler la taille du lot.</br></br>La valeur par défaut est de 100 éléments. Selon le volume et la capacité de votre commande, vous devrez peut-être ajuster cette valeur vers le haut ou vers le bas. | Global | Non |


## Activation des options d’expédition d’exécution de magasin

Configurez les options d’expédition d’exécution de magasin qui déterminent la disponibilité des options de récupération en magasin et de remise à domicile pour vos magasins Adobe Commerce.

### Bateau


| **Champ** | **Description** | **Portée** | **Obligatoire** |
|---------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Enable Ship To Store]** | Le paramètre d’expédition vers l’entrepôt tire parti de vos capacités d’expédition vers l’entrepôt existantes. Si vous utilisez Inventory management, ou si vous pouvez accepter et exécuter des commandes dans des emplacements marchands sans inventaire via des transferts d’inventaire magasin à magasin, définissez cette option sur `Yes`.</br></br>Si vous ne pouvez pas prendre en charge l’option de livraison ou si vous ne souhaitez pas l’offrir, définissez sur `No`. Lorsque cette option est désactivée, les éléments de votre catalogue dont l’inventaire n’est pas renseigné pour un magasin marchand ou les éléments situés en dessous de cet emplacement sont [!DNL Out of Stock Threshold], ne sont pas proposées avec les options de récupération en magasin.</br></br>Il s’agit d’un paramètre global qui peut être ajusté par lieu commercial. | Global | Non |

### Ship From

| **Champ** | **Description** | **Portée** | **Obligatoire** |
|-----------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Enable Ship From Store]** | Active ou désactive l’option Livraison à domicile dans vos magasins marchands. Lorsque cette option est activée, les emplacements de magasin marchand sont pris en compte dans l’ensemble avec d’autres sources affectées dans le stock associé à votre site web.</br></br>Dans les services Inventory management standard, la variable [!DNL Ship from Store] L’option est inhérente et ne peut pas être désactivée. Avec la solution d’exécution de magasin, vous avez la possibilité de l’activer ou de la désactiver.</br></br>Il s’agit d’un paramètre global. Vous pouvez également ajuster ce paramètre par emplacement et produit marchand. | Global | Non |


## Gérer les comptes d’utilisation et les autorisations de l’application d’exécution de magasin

Configurez les paramètres de sécurité du compte utilisateur et du mot de passe de l’application d’exécution de la boutique et de l’authentification à deux facteurs.

### Sécurité des applications

| **Champ** | **Description** | **Portée** | **Obligatoire** |
|------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL User Session Lifetime]** | Période, en secondes, pendant laquelle une session utilisateur associée de magasin reste principale avant la déconnexion automatique. Les valeurs valides vont de 60 à 31536000. | Global | Non |
| **[!UICONTROL Maximum Login Failures to Lockout Account]** | Indique le nombre de tentatives de connexion qui ont échoué avant qu’une associée du magasin ne soit verrouillée de son compte.</br></br>Pour désactiver le verrouillage de compte, définissez la valeur sur 0. | Global | Non |
| **[!UICONTROL Lockout Time (minutes)]** | Nombre de minutes pour verrouiller un compte après l’échec de connexion. | Global | Non |
| **[!UICONTROL Force Password Change]** | Détermine si un changement de mot de passe utilisateur est requis.</br></br>`Yes`: L’utilisateur doit modifier son mot de passe après la configuration du compte.</br>`No`: Recommande à l’utilisateur de modifier le mot de passe après la configuration du compte. | Global | Non |
| **Durée de vie du mot de passe** | Nombre de jours pendant lesquels un mot de passe reste valide avant qu’un mot de passe requis ne soit modifié. Laissez vide pour désactiver cette option. | Global | Non |


### Authentification à deux facteurs

| **Champ** | **Description** | **Portée** | **Obligatoire** |
|--------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **Utilisateur APP 2FA** | Activez ou désactivez l’authentification à deux facteurs pour les associés de magasin. Lorsqu’elle est activée, l’associé du magasin est invité à fournir un mot de passe unique généré par un fournisseur d’authentification. | Global | Non |
| **Stratégie APP 2FA** | Définit la stratégie d’application pour l’authentification à deux facteurs.</br></br>**[!UICONTROL Optional]**: L’associé du magasin peut contourner l’authentification à deux facteurs si aucun fournisseur n’est défini.</br></br>**[!UICONTROL Mandatory]**: L’associé de magasin est requis pour effectuer une authentification à deux facteurs. | Global | Non |
| **Fournisseurs 2FA** | Sélectionnez un ou plusieurs services du fournisseur d’authentification pour proposer des associés au magasin. Pour configurer l’authentification et l’authentification à deux facteurs, les associés de magasin doivent installer l’application d’authentification à partir de l’un des fournisseurs disponibles installés sur leurs appareils mobiles. | Global | Non |

### Méthodes de diffusion

L’exécution du magasin fonctionne en étendant le Adobe Commerce natif. [!DNL In-Store Delivery] fonctionnalités.
Une fois l’extension installée, d’autres options de configuration d’administrateur sont disponibles pour les méthodes de remise en magasin. Configurez ces options supplémentaires dans l’onglet Admin en sélectionnant **[!UICONTROL Stores > Configuration > Sales > Delivery Methods > In-Store Pickup]**.

Dans les paramètres d’exécution de la boutique, vous pouvez configurer les méthodes de remise suivantes pour les commandes de nettoyage en magasin.

- **Reprise en magasin**: options d’offre pour la diffusion en magasin pendant le processus de passage en caisse Il s’agit du scénario de livraison le plus courant pour les commandes BOPIS.

- **Ramassage urbain**- Offre des options permettant aux clients de se garer sur un emplacement de magasin et de recevoir leur commande par un associé du magasin.

#### Configuration des méthodes de diffusion

<!---
In-store pickup, says its global setting, but scope is Website.  How do you configure the in-store pickup options at the retail level?
--->

| **Champ** | **Description** | **Portée** | **Obligatoire** |
|-----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Enable In-Store Pickup]** | Activez ou désactivez l’option de prise en charge en magasin disponible lors du passage en caisse pour les clients qui choisissent le nettoyage du magasin. Lorsque le sélecteur en magasin est désactivé, l’option n’est pas affichée.</br></br>Ce paramètre global s’applique à tous les emplacements de magasins de détail. Lorsque cette option est activée, vous pouvez la désactiver de manière sélective à l’emplacement du magasin de détail. | Site Web | Non |
| **Activation de la collecte côté serveur** | Activez ou désactivez l’option de sélection au niveau du curseur au cours du processus de passage en caisse pour les clients qui choisissent la sélection de magasin.</br></br>Ce paramètre global s’applique à tous les emplacements de magasins de détail. Lorsque cette option est activée, vous pouvez la désactiver de manière sélective à l’emplacement du magasin de détail. | Site Web | Non |

Pour plus d’informations sur la personnalisation des méthodes de diffusion dans des emplacements de magasins de détail sélectionnés, voir **Configuration de la boutique de détail**.


#### Configuration du titre de la méthode de diffusion

<table>
<thead>
<tr>
<th><strong>Champ</strong></th>
<th><strong>Description</strong></th>
<th><strong>Portée</strong></th>
<th><strong>Obligatoire</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>Titre de la diffusion d’accueil</strong></td>
<td>Spécifie le titre à afficher pour l’option Livraison à domicile dans les zones Produit, Panier et Passage en caisse. La diffusion à domicile fait référence aux capacités d’expédition standard d’Adobe Commerce, depuis un entrepôt, par un opérateur, vers l’adresse d’expédition fournie par le client.</br></br>Ce libellé n’a aucune incidence sur l’opérateur de livraison sélectionné ni sur les étiquettes de méthode de livraison disponibles.</td>
<td>Affichage en magasin</td>
<td>Non</td>
</tr>
<tr>
<td><strong>Description de la diffusion d’accueil</strong></td>
<td>Description facultative qui s’affiche chaque fois que le titre de la diffusion d’accueil est présenté aux clients. La plupart du temps, la description est un message statique pour communiquer vos promesses de diffusion. Quelques exemples :</br><code>Same-day shipping on orders by 4</code></br></br><code>Ships within 2 business days</code></td>
<td>Affichage en magasin</td>
<td>Non</td>
</tr>
<tr>
<td><strong>Titre du ticket de magasin</strong></td>
<td>Ce libellé s’affiche lorsqu’un client dispose d’options de remise et qu’un sélecteur en magasin est disponible.</br></br>Vous pouvez personnaliser ce libellé qui s’affiche dans les zones produit, panier et passage en caisse.</td>
<td>Affichage en magasin</td>
<td>Non</td>
</tr>
<td><strong>Description du ticket de magasin</strong></td>
<td>Où que le titre de la sélecteur de magasin s’affiche, vous pouvez éventuellement inclure une description. Ce message statique permet d’améliorer les communications client liées à l’expérience de récupération du magasin. Quelques exemples :</br></br><code>Get it today for free!</code></br></br><code>Ready for pickup in an hour!</code></td>
<td>Affichage en magasin</td>
<td>Non</td>
</tr>
<tr>
<td><strong>Titre de la sélection en magasin</strong></td>
<td>Lorsque l’option de remise Sélecteur de magasin est activée, ce titre s’affiche pour les clients en tant qu’option de remise Sélecteur de magasin . Vous pouvez personnaliser son libellé.</td>
<td>Affichage en magasin</td>
<td>Non</td>
</tr>
<tr>
<tr>
<td><strong>Titre de la sélection côté ville</strong></td>
<td>Lorsque l’option Collecte en périphérie est activée, elle s’affiche pour les clients sous la forme d’une option de remise Stocker la collecte . Vous pouvez personnaliser son libellé ici.</td>
<td>Affichage en magasin</td>
<td>Non</td>
</tr>
<tr>
<td><strong>Instructions de récupération en magasin</strong></td>
<td>Lorsqu’une commande est prête à être récupérée dans vos magasins de détail, le client est averti par e-mail. Si le client a sélectionné [!DNL In-Store Pickup] pendant le passage en caisse, vous pouvez personnaliser les instructions de sélection ici.</br></br>Il s’agit d’un paramètre global qui s’applique à tous les emplacements de magasins de détail. Vous pouvez également personnaliser les instructions au niveau de l’emplacement du magasin de détail.</td>
<td>Affichage en magasin</td>
<td>Non</td>
</tr>
<tr>
<td><strong>Instructions de récupération des banlieues</strong></td>
<td>Spécifie les instructions de sélection de commande personnalisées à inclure dans les notifications par e-mail des clients pour les commandes de sélection de commandes.</br></br>Il s’agit d’un paramètre global qui s’applique à tous les emplacements de magasins de détail. Vous pouvez également personnaliser les instructions au niveau de l’emplacement du magasin de détail.</td>
<td>Affichage en magasin</td>
<td>Non</td>
</tr>
<tr>
<td><strong>Délai d’avance estimé pour la collecte</strong></td>
<td>Nombre de minutes nécessaires avant la réception, l’exécution et la préparation d’une commande. Ces informations s’affichent pour le client lors de la sélection de l’emplacement d’un magasin de détail pour l’option de remise Sélecteur de magasin .</br></br>Il s’agit d’un paramètre global qui s’applique à tous les emplacements de magasins de détail. Vous pouvez également personnaliser le délai d’avance au niveau de l’emplacement du magasin de détail.</td>
<td>Affichage en magasin</td>
<td>Non</td>
</tr>
<tr>
<td><strong>Étiquette du temps de récupération estimé</strong></td>
<td>Affiche la durée estimée jusqu’à ce qu’une commande soit disponible pour la récupération des clients. Ces informations s’affichent pour les clients lorsqu’ils sélectionnent un emplacement de magasin de détail pour l’option de remise Sélecteur de magasin .</br></br>Lors de la personnalisation de ce libellé, vous pouvez utiliser le code <code>%1</code> pour insérer vos <strong>Délai d’avance estimé pour la collecte</strong>.Par exemple :</br></br><code>Ready for Pickup in %1 minutes.</code></br></br>Il s’agit d’un paramètre global qui s’applique à tous les emplacements de magasins de détail. Vous pouvez également personnaliser le délai d’avance au niveau de l’emplacement du magasin de détail.</br></br><code>Ready for Pickup in %1 minutes.</code></br></br></td>
<td>Affichage en magasin</td>
<td>Non</td>
<tr>
<td><strong>Clause de non-responsabilité du temps de récupération</strong></td>
<td>Le contenu affiché sur la page du produit dans l’info-bulle qui répertorie les heures de stockage, les jours fériés, les fermetures inattendues, etc.</td>
<td>Affichage en magasin
</td>
<td>Non
</td>
</tr>
</tbody></table>

#### Configuration des titres de disponibilité des stocks

<table>
<thead>
<tr>
<th><strong>Champ</strong></th>
<th><strong>Description</strong></th>
<th><strong>Portée</strong></th>
<th><strong>Obligatoire</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>En stock</strong></td>
<td>Lorsqu’un client utilise le localisateur du magasin de détail, la disponibilité du stock pour le ou les articles en cours s’affiche pour chaque emplacement.</br></br>Vous pouvez personnaliser le libellé de statut "en stock" ici.</td>
<td>Affichage en magasin</td>
<td>Non</td>
</tr>
<tr>
<td><strong>En rupture de stock</strong></td>
<td>Lorsqu’un client utilise le localisateur de la boutique de détail, la disponibilité du stock de tous les articles en cours s’affiche pour chaque emplacement.</td>
<td>Affichage en magasin</td>
<td>Non</td>
</tr>
<tr>
<td><strong>Partiellement en stock</strong></td>
<td>Lorsqu’un client utilise le localisateur de la boutique de détail, la disponibilité du stock de tous les articles en cours s’affiche pour chaque emplacement.</br></br>Vous pouvez personnaliser le libellé d’état "partiellement en stock" ici.</td>
<td>Affichage en magasin</td>
<td>Non</td>
</tr>
</tbody></table>





