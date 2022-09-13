---
title: Configuration générale
description: Configuration des paramètres généraux à activer [!DNL Store Fulfillment] pour votre magasin. Configurez les paramètres d’extension globaux, les paramètres système pour la journalisation, la synchronisation des données et la sécurité. Fournissez des données clés pour activer l’intégration entre Adobe Commerce et les services d’exécution de magasin.
role: User, Admin
level: Intermediate
exl-id: 51dcfc95-3dd6-40d9-bd26-d8409a25f3c8
source-git-commit: fda4620f57aa7aa9fb930b10f5717fee98983378
workflow-type: tm+mt
source-wordcount: '2518'
ht-degree: 0%

---

# Configuration du service et des ventes en magasin

Configurer[!DNL Store Fulfillment] pour activer l’extension, spécifiez les paramètres d’extension, configurez les paramètres de sécurité pour les utilisateurs de l’application d’assistance de la boutique et définissez les options des méthodes de diffusion.

>[!IMPORTANT]
>
>La configuration du service d’exécution de magasin s’applique uniquement après la connexion de votre instance Adobe Commerce et de l’événement [!DNL Store Fulfillment] application. Voir [Connexion à l’exécution du magasin](connect-set-up-service.md).

Configurez les paramètres des services d’exécution de magasin dans le menu Configuration de la boutique d’administration dans Adobe Commerce.

Accédez aux paramètres pour activer l’extension, configurez les paramètres globaux et spécifiez les options de sécurité pour les connexions utilisateur et les comptes de l’application d’assistance de la boutique en sélectionnant **[!UICONTROL Stores > Configuration > Services > Store Fulfillment by Walmart Commerce Technologies]**.

![Configuration des services de la boutique d’administration pour l’exécution du magasin](assets/store-services-admin-sf-config.png)

Accédez aux paramètres de configuration des méthodes de diffusion en sélectionnant **[!UICONTROL Store > Configuration > Sales > Delivery Methods > In-Store Pickup]**.

![Configuration des ventes de la boutique d’administration pour l’exécution du magasin](assets/store-sales-admin-sf-deliver-config.png)

## Paramètres de base

<table>
<thead>
<tr>
<td><strong>Champ</strong></td>
<td><strong>Description</strong></td>
<td><strong>Portée</strong></td>
<td><strong>Obligatoire</strong></td>
</tr>
</thead>
<tbody>
<tr>
<td><strong>[!UICONTROL Price]</strong></td>
<td>Le prix que vous facturez au client pour la récupération en magasin. La valeur par défaut est zéro.</td>
<td>Site Web</td>
<td>Non</td>
</tr>
<tr>
<td><strong>[!UICONTROL Search Radius]</strong></td>
<td>Rayon, en kilomètres, à utiliser lorsqu’un acheteur recherche un emplacement de récupération d’un magasin dans le passage en caisse du storefront. Les résultats de la recherche renvoient uniquement les magasins situés dans le rayon de recherche spécifié.</td>
<td>Site Web</td>
<td>Non</td>
</tr>
<tr>
<td><strong>[!UICONTROL Displayed error message]</strong></td>
<td>Message qui s’affiche lorsqu’un client sélectionne une sélection en magasin, mais que la méthode de remise n’est pas disponible. Si nécessaire, vous pouvez personnaliser le texte par défaut.
</td>
<td>Affichage en magasin</td>
<td>Non</td>
</tr>
</tbody>
</table>

>[!NOTE]
>
>Le [!UICONTROL Search Radius] n’est utilisé que si vous avez configuré la variable [configuration de l’emplacement et du mappage du magasin](store-location-map-provider-setup.md) pour Adobe Commerce.

## Activation de la solution d’exécution de magasin

Activez la variable [!DNL Store Fulfillment] pour ajouter les fonctionnalités de sélection en magasin et côté serveur aux expériences d’achat et de passage en caisse de votre vitrine Adobe Commerce.

<table>
<thead>
<tr>
<td><strong>Champ</strong></td>
<td><strong>Description</strong></td>
<td><strong>Portée</strong></td>
<td><strong>Obligatoire</strong></td>
</tr>
 </thead>
 <tbody>
<tr>
<td><strong>[!UICONTROL Enabled]</strong></td>
<td>Activez ou désactivez la solution. Lorsque cette option est activée, configurez et utilisez les fonctionnalités d’exécution de magasin et établissez la connexion entre votre boutique Adobe Commerce et les services d’exécution de magasin. Lorsque cette option est désactivée, toutes les fonctions d’exécution de magasin sont désactivées et il n’existe aucune communication entre Adobe Commerce et les services d’exécution de magasin. Les informations de commande ne peuvent pas être traitées ni reçues.</td>
<td>Global</td>
<td>Oui</td>
</tr>
</tbody>
</table>

## Ajout d’informations d’identification de compte

<table>
<tr>
<td><strong>Champ</strong></td>
<td><strong>Description</strong></td>
<td><strong>Portée</strong></td>
<td><strong>Obligatoire</strong></td>
    </tr>
<tr>
<td><strong>[!UICONTROL Environment]</strong></td>
<td>Sélectionnez <i>Sandbox</i> ou <i>Production</i><br></br> Sandbox communique avec les services d’exécution dans un test.La production communique avec un environnement en ligne. Utilisation <strong>only</strong> en production.<br></br>Un ensemble d’informations d’identification vous est attribué pour chaque environnement et vous permet de gérer les deux ensembles dans la même installation. <br></br>Enregistrez les informations d’identification avant de valider la connexion.</td>
<td>Global</td>
<td>Oui</td>
    </tr>
<tr>
<td><strong>[!UICONTROL API Server URL]</strong></td>
<td>URL du point d’entrée de l’API d’exécution de la boutique Walmart. Il doit s’agir de l’URL complète qui vous a été fournie au cours de votre processus d’intégration. Les clients d’exécution de magasin reçoivent à la fois un sandbox et une URL de production. Veillez à copier/coller l’URL complète, y compris la barre oblique "/" à la fin.</td>
<td>Global</td>
<td>Oui</td>
    </tr>
<tr>
<td><strong>[!UICONTROL Token Auth Server URL]</strong></td>
<td>URL du point de terminaison de l’authentification de l’exécution de la boutique Walmart. La valeur doit correspondre à l’URL complète qui vous a été fournie au cours de votre processus d’intégration. Vous recevez à la fois une URL Sandbox et une URL de production. Veillez à copier/coller l’URL complète, y compris la barre oblique "/" à la fin.</td>
<td>Global</td>
<td>Oui</td>
    </tr>
<tr>
<td><strong>[!UICONTROL Merchant Id]</strong></td>
<td>Votre identifiant de commerçant (client) unique fourni lors de votre processus d’intégration. Votre identifiant est utilisé pour acheminer vos commandes et vous assurer que vos magasins marchands les reçoivent.</td>
<td>Global</td>
<td>Oui</td>
    </tr>
<tr>
<td><strong>[!UICONTROL Consumer Id]</strong></td>
<td>Votre identifiant d’intégration unique. Il vous est fourni pendant votre processus d’intégration. Ça ne change pas. Il est utilisé pour authentifier toutes les communications avec les services d’exécution.</td>
<td>Global</td>
<td>Oui</td>
    </tr>
<tr>
<td><strong>[!UICONTROL Consumer Secret]</strong></td>
<td>Votre clé d’intégration unique. Il vous est fourni pendant votre processus d’intégration. Il est utilisé pour authentifier toutes les communications avec les services d’exécution.</td>
<td>Global</td>
<td>Oui</td>
    </tr>
</table>

Après avoir configuré les informations d’identification du compte, sélectionnez <strong>[!UICONTROL Validate Credentials]</strong> pour vérifier et établir une connexion au service web d’exécution pour la première fois.

## Configuration de la journalisation

Lorsque la journalisation est activée, votre fichier journal peut rapidement se développer. Pour éviter les problèmes de temps de réponse dans les environnements de production, veillez à activer la journalisation et activez uniquement pendant une courte période lorsque cela est nécessaire.

Demandez à l’administrateur système de configurer vos environnements pour autoriser la gestion des exceptions afin que les exceptions liées à l’API puissent être capturées via le pare-feu ou le cache. Vous pouvez également demander à votre administrateur système de configurer la rotation du journal sur ce fichier afin de réduire la taille.

<table>
<thead>
<tr>
<td><strong>Champ</strong></td>
<td><strong>Description</strong></td>
<td><strong>Portée</strong></td>
<td><strong>Obligatoire</strong></td>
</tr>
</thead>
<tbody>
<tr>
<td><strong>[!UICONTROL Debug Mode]</strong></td>
<td>Le mode de débogage est utilisé pour augmenter l’activité consignée dans l’intégration. Lorsque cette option est désactivée, aucune information de débogage n’est consignée. Lorsque cette option est activée, toutes les informations de débogage sont consignées. Toutes les données consignées se trouvent dans le fichier : `var/log/walmart-bopis.log`</td>
<td>Global</td>
<td>Non</td>
</tr>
</tbody>
</table>

## Gestion de la synchronisation des commandes

Configurez les paramètres pour gérer la gestion des erreurs pour la synchronisation des commandes, les attributs de catalogue à utiliser pour l’analyse du code à barres lors du choix de la commande et configurez les tailles des lots de commandes pour la file d’attente d’exécution du magasin.

Vous pouvez afficher des détails sur les opérations de synchronisation des commandes à partir du tableau de bord Gestion des files d’attente d’exécution de magasin dans Admin (
<strong>[!UICONTROL System > Tools > Store Fulfillment Queue]</strong>).

### Gestion des erreurs de synchronisation

<table>
<tr>
<td><strong>Champ</strong></td>
<td><strong>Description</strong></td>
<td><strong>Portée</strong></td>
<td><strong>Obligatoire</strong></td>
</tr>
<tr>
<td><strong>[!UICONTROL Retry Critical Error]</strong></td>
<td>Indique les tentatives de reprise d’une opération de synchronisation d’enregistrement après une erreur critique.<br></br>Des erreurs critiques se produisent chaque fois que l’intégration ne parvient pas à obtenir une réponse positive de la part du service d’exécution. Cela peut se produire lorsque le service est en panne ou lorsqu’une erreur se produit dans les données de commande envoyées.<br></br>Lorsque le seuil de reprise est atteint, l’élément reste dans la file d’attente mais n’est pas traité à nouveau. Afficher tous les éléments contenant des erreurs de <strong>[!UICONTROL System > Tools > Store Fulfillment Queue]</strong> Gestion dans l’administrateur. Pour résoudre les problèmes liés aux éléments qui échouent constamment, contactez votre gestionnaire de compte.</td>
<td>Global</td>
<td>Non</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Error Notification Email]</strong></td>
<td>Activez les notifications d’erreur pour recevoir un courrier électronique lorsque la variable [!UICONTROL Retry Critical Error Threshold] est atteinte pour une commande. La notification inclut tous les détails disponibles sur l’erreur.</td>
<td>Global</td>
<td>Non</td>
</tr>
<tr>
<td><strong>[!UICONTROL Send Error Notification Email To]</strong></td>
<td>Liste délimitée par des virgules d’adresses email des destinataires pour les notifications d’erreur.</td>
<td>Global</td>
<td>Non</td>
</tr>
<tr>
<td><strong>[!UICONTROL Order Sync Exception Email Template]</strong></td>
<td>Indique le modèle d’email utilisé pour avertir les destinataires des erreurs de synchronisation de commande. Un modèle par défaut est fourni. Il ne prend pas en charge la personnalisation.</td>
<td>Affichage en magasin</td>
<td>Non</td>
</tr>
</table>

### Synchronisation des commandes

<table>
<thead>
<tr>
<td><strong>Champ</strong></td>
<td><strong>Description</strong></td>
<td><strong>Portée</strong></td>
<td><strong>Obligatoire</strong></td>
</tr>
</thead>
<tbody>
<tr>
<td><strong>[!UICONTROL Barcode Source]</strong></td>
<td>L’attribut catalog qui stocke le code pouvant être analysé pour les éléments correspondants dans vos emplacements marchands.<br></br>Si vous n’avez qu’un seul emplacement commercial, il est probable que vous utilisiez des codes CUP, tandis que votre canal de commerce électronique identifie les produits par SKU. Si tel est votre scénario, sélectionnez l’attribut catalog qui contient le code UPC.<br></br>Ce paramètre garantit que les commandes envoyées à vos magasins répertorient les éléments avec l’identifiant correct afin que les associés de magasin puissent analyser précisément les éléments pendant le processus de sélection.<br></br>Si vous n’êtes pas sûr, vérifiez auprès de vos associés d’exécution dans le service Expédition et sélection pour déterminer l’attribut à envoyer. Vous devrez peut-être ajouter l’attribut approprié au jeu d’attributs de produit Adobe Commerce si l’attribut n’est pas actuellement inclus dans la base de données.</td>
<td>Site Web</td>
<td>Oui</td>
</tr>
<tr>
<td><strong>[!UICONTROL Barcode Type]</strong></td>
<td>L’attribut catalog qui stocke la source du code à barres pour les éléments correspondants dans vos emplacements marchands.<br></br>Ce paramètre garantit que les commandes envoyées à vos magasins répertorient les éléments avec l’identifiant correct afin que les associés de magasin puissent analyser précisément les éléments pendant le processus de sélection. Les options incluent : SKU, UPC, GTIN, UPCA, EAN13, UPCE0, DISA, UAB, CODABAR, Price Embedded UPC.<br></br>Si vous n’êtes pas sûr, sélectionnez l’option qui ressemble le plus aux valeurs contenues dans votre [!UICONTROL Barcode Source] attribut. Les associés de magasin peuvent toujours faire correspondre des éléments manuellement à partir de leur liste de sélection.</td>
<td>Site Web</td>
<td>Oui</td>
</tr>
<tr>
<td><strong>[!UICONTROL Max Number of Items]</strong></td>
<td>Nombre maximal d’éléments à envoyer simultanément à partir de la file d’attente d’exécution du magasin.<br></br>Les commandes BOPIS sont envoyées par lots au service d’exécution, à intervalles réguliers. Ce paramètre vous permet de contrôler la taille du lot.<br></br>La valeur par défaut est de 100 éléments. Selon le volume et la capacité de votre commande, vous devrez peut-être ajuster cette valeur vers le haut ou vers le bas.</td>
<td>Global</td>
<td>Non</td>
</tr>
</tbody>
</table>

## Activation des options d’expédition d’exécution de magasin

Configurez les options d’expédition d’exécution de magasin qui déterminent la disponibilité des options de récupération en magasin et de remise à domicile pour vos magasins Adobe Commerce.

### Bateau

<table>
<thead>
<tr>
<td><strong>Champ</strong></td>
<td><strong>Description</strong></td>
<td><strong>Portée</strong></td>
<td><strong>Obligatoire</strong></td>
</tr>
</thead>
<tbody>
<tr>
<td><strong>[!UICONTROL Enable Ship To Store]</strong></td>
<td>Le paramètre d’expédition vers l’entrepôt repose sur vos capacités d’expédition vers l’entrepôt existantes. Si vous utilisez Inventory management, ou si vous pouvez accepter et exécuter des commandes dans des emplacements marchands sans inventaire via des transferts d’inventaire magasin à magasin, définissez cette option sur "Oui".<br></br>Si vous ne pouvez pas prendre en charge l’option d’envoi au magasin ou ne souhaitez pas l’offrir, définissez sur "Non". Lorsque cette option est désactivée, les éléments de votre catalogue dont l’inventaire n’est pas renseigné pour un magasin marchand ou les éléments situés en dessous de cet emplacement sont [!DNL Out of Stock Threshold], ne sont pas proposées avec les options de récupération en magasin.<br></br>Il s’agit d’un paramètre global qui peut être ajusté par lieu commercial.</td>
<td>Global</td>
<td>Non</td>
</tr>
</tbody>
</table>

### Ship From

<table>
<thead>
<tr>
<td><strong>Champ</strong></td>
<td><strong>Description</strong></td>
<td><strong>Portée</strong></td>
<td><strong>Obligatoire</strong></td>
</tr>
</thead>
<tbody>
<tr>
<td><strong>[!UICONTROL Enable Ship From Store]</strong></td>
<td>Active ou désactive l’option Livraison à domicile dans vos magasins marchands. Lorsque cette option est activée, les emplacements de magasin marchand sont pris en compte dans l’ensemble avec d’autres sources affectées dans le stock associé à votre site web.<br></br>Dans les services Inventory management standard, la variable [!DNL Ship from Store] L’option est inhérente et ne peut pas être désactivée. Avec la solution d’exécution de magasin, vous pouvez l’activer ou la désactiver.<br></br>Il s’agit d’un paramètre global. Vous pouvez également ajuster ce paramètre par emplacement et produit marchand.</td>
<td>Global</td>
<td>Non</td>
</tr>
</tbody>
</table>


## Gérer les comptes d’utilisation et les autorisations de l’application d’exécution de magasin

Configurez les paramètres de sécurité du compte utilisateur et du mot de passe de l’application d’exécution de la boutique et de l’authentification à deux facteurs.

### Sécurité des applications

<table>
<thead>
<tr>
<td><strong>Champ</strong></td>
<td><strong>Description</strong></td>
<td><strong>Portée</strong></td>
<td><strong>Obligatoire</strong></td>
</tr>
 </thead>
 <tbody>
<tr>
<td><strong>[!UICONTROL User Session Lifetime]</strong></td>
<td>Période, en secondes, pendant laquelle une session utilisateur associée de magasin reste principale avant la déconnexion automatique. Les valeurs valides vont de 60 à 31536000.</td>
<td>Global</td>
<td>Non</td>
</tr>
<tr>
<td><strong>[!UICONTROL Maximum Login Failures to Lockout Account]</strong></td>
<td>Indique le nombre de tentatives de connexion qui ont échoué avant qu’une associée du magasin ne soit verrouillée de son compte.<br></br>Pour désactiver le verrouillage de compte, définissez la valeur sur 0.</td>
<td>Global</td>
<td>Non</td>
</tr>
<tr>
<td><strong>[!UICONTROL Lockout Time (minutes)]</strong></td>
<td>Nombre de minutes pour verrouiller un compte après l’échec de connexion.</td>
<td>Global</td>
<td>Non</td>
</tr>
<tr>
<td><strong>[!UICONTROL Force Password Change]</strong></td>
<td>Détermine si un changement de mot de passe utilisateur est requis.<br></br>`Oui` : L’utilisateur doit modifier son mot de passe après la configuration du compte.`Non` : Recommande à l’utilisateur de modifier le mot de passe après la configuration du compte.</td>
<td>Global</td>
<td>Non</td>
</tr>
<tr>
<td><strong>[!UICONTROL Password Lifetime]</strong></td>
<td>Nombre de jours pendant lesquels un mot de passe reste valide avant qu’un mot de passe requis ne soit modifié. Laissez vide pour désactiver cette option.</td>
<td>Global</td>
<td>Non</td>
</tr>
</tbody>
</table>

### Authentification à deux facteurs

<table>
<thead>
<tr>
<td><strong>Champ</strong></td>
<td><strong>Description</strong></td>
<td><strong>Portée</strong></td>
<td><strong>Obligatoire</strong></td>
</tr>
 </thead>
 <tbody>
<tr>
<td><strong>[!UICONTROL APP User 2FA]</strong></td>
<td>Activez ou désactivez l’authentification à deux facteurs pour les associés de magasin. Lorsqu’elle est activée, l’associé du magasin est invité à fournir un mot de passe unique généré par un fournisseur d’authentification.</td>
<td>Global</td>
<td>Non</td>
</tr>
<tr>
<td><strong>[!UICONTROL APP 2FA Policy]</strong></td>
<td>Définit la stratégie d’application pour l’authentification à deux facteurs.<br></br><strong>[!UICONTROL Optional]</strong>: L’associé du magasin peut contourner l’authentification à deux facteurs si aucun fournisseur n’est défini.<br></br><strong>[!UICONTROL Mandatory]</strong>: L’associé de magasin est requis pour effectuer une authentification à deux facteurs.</td>
<td>Global</td>
<td>Non</td>
</tr>
<tr>
<td><strong>[!UICONTROL 2FA Providers]</strong></td>
<td>Sélectionnez un ou plusieurs services du fournisseur d’authentification pour proposer des associés au magasin. Pour configurer l’authentification et l’authentification à deux facteurs, les associés de magasin doivent installer l’application d’authentification à partir de l’un des fournisseurs disponibles installés sur leurs appareils mobiles.</td>
<td>Global</td>
<td>Non</td>
</tr>
</tbody>
</table>

## Méthodes de diffusion

L’exécution du magasin fonctionne en étendant le Adobe Commerce natif. [!DNL In-Store Delivery] fonctionnalités.
Une fois l’extension installée, d’autres options de configuration d’administrateur sont disponibles pour les méthodes de remise en magasin. Configurez ces options supplémentaires dans l’onglet Admin en sélectionnant <strong>[!UICONTROL Stores > Configuration > Sales > Delivery Methods > In-Store Pickup]</strong>.

Dans les paramètres d’exécution de la boutique, vous pouvez configurer les méthodes de remise suivantes pour les commandes de nettoyage en magasin.

- **Reprise en magasin**: options d’offre pour la diffusion en magasin pendant le processus de passage en caisse Il s’agit du scénario de livraison le plus courant pour les commandes BOPIS.

- **Ramassage urbain**- Offre des options permettant aux clients de se garer sur un emplacement de magasin et de recevoir leur commande par un associé du magasin.

>[!NOTE]
>
>Pour plus d’informations sur la configuration des options de remise en magasin, voir [Diffusion en magasin](https://docs.magento.com/user-guide/shipping/shipping-in-store-delivery.html) dans le Guide de l’utilisateur d’Adobe Commerce.


### Configuration des méthodes de diffusion

Avec la méthode de remise en magasin, le client peut sélectionner une source à utiliser comme emplacement de récupération lors du passage en caisse.

<table>
<thead>
<tr>
<td><strong>Champ</strong></td>
<td><strong>Description</strong></td>
<td><strong>Portée</strong></td>
<td><strong>Obligatoire</strong></td>
</tr>
 </thead>
 <tbody>
<tr>
<td><strong>[!UICONTROL Enable In-Store Pickup]</strong></td>
<td>Activez ou désactivez l’option de sélection en magasin disponible lors du passage en caisse pour les clients qui choisissent le passage en caisse. Lorsque le sélecteur en magasin est désactivé, l’option n’est pas affichée.<br></br>Ce paramètre global s’applique à tous les emplacements de magasins de détail. Lorsque cette option est activée, vous pouvez la désactiver de manière sélective à l’emplacement du magasin de détail.</td>
<td>Site Web</td>
<td>Non</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Curbside Pickup]</strong></td>
<td>Activez ou désactivez l’option de sélection au niveau du curseur au cours du processus de passage en caisse pour les clients qui choisissent la sélection de magasin.<br></br>Ce paramètre global s’applique à tous les emplacements de magasins de détail. Lorsque cette option est activée, vous pouvez la désactiver de manière sélective à l’emplacement du magasin de détail.</td>
<td>Site Web</td>
<td>Non</td>
</tr>
</tbody>
</table>

### Configuration du titre de la méthode de diffusion

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
<td>Spécifie le titre à afficher pour l’option Livraison à domicile dans les zones Produit, Panier et Passage en caisse. La diffusion à domicile fait référence aux fonctionnalités d’expédition standard d’Adobe Commerce, depuis un entrepôt, par un opérateur ou directement vers l’adresse d’expédition fournie par le client.</br></br>Ce libellé n’a aucune incidence sur l’opérateur de livraison sélectionné ni sur les étiquettes de méthode de livraison disponibles.</td>
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

### Configuration des titres de disponibilité des stocks

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
<td><strong>n-Stock</strong></td>
<td>Lorsqu’un client utilise le localisateur de la boutique de détail, la disponibilité du stock pour un nombre d’articles actuels supplémentaires s’affiche pour chaque emplacement.</br></br>Vous pouvez personnaliser le libellé de statut "en stock" ici.</td>
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
