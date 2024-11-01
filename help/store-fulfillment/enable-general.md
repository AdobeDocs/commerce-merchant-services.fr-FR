---
title: Configuration générale
description: Configurez les paramètres généraux pour activer  [!DNL Store Fulfillment] pour votre magasin. Configurez les paramètres d’extension globaux, les paramètres système pour la journalisation, la synchronisation des données et la sécurité. Fournissez des données clés pour activer l’intégration entre Adobe Commerce et les services d’exécution de magasin.
role: Admin
level: Intermediate
exl-id: 51dcfc95-3dd6-40d9-bd26-d8409a25f3c8
source-git-commit: 37380063242b6d904910be731b8e58471625e9cb
workflow-type: tm+mt
source-wordcount: '2405'
ht-degree: 0%

---

# Configuration du service de magasin et des ventes

Activez l’extension [!DNL Store Fulfillment] de l’administrateur [!DNL Commerce] en configurant les paramètres d’extension, les paramètres de sécurité pour les utilisateurs de l’application d’assistance de la boutique et les options de méthode de remise.

>[!IMPORTANT]
>
>La configuration du service d’exécution de magasin s’applique uniquement après la connexion de votre instance Adobe Commerce et de l’application [!DNL Store Fulfillment]. Voir [Connexion à l’exécution de la boutique](connect-set-up-service.md).

## Gestion des paramètres des services d’exécution de magasin

Gérez les paramètres des services d’exécution de magasin depuis le menu [!DNL Commerce Admin Store Configuration].

- Activez l’extension, configurez les paramètres globaux et spécifiez les options de sécurité pour les connexions utilisateur et les comptes de l’application d’assistance de la boutique en sélectionnant **[!UICONTROL Stores > Configuration > Services > Store Fulfillment by Walmart Commerce Technologies]**.

  ![ Configuration des services de la boutique d’administration pour l’exécution du magasin ](assets/store-services-admin-sf-config.png)

- Configurez les méthodes de diffusion en sélectionnant **[!UICONTROL Store > Configuration > Sales > Delivery Methods > In-Store Pickup]**.

  ![ Configuration des ventes de l’Admin Store pour l’exécution du magasin ](assets/store-sales-admin-sf-deliver-config.png)

## Paramètres de base

<table>
<thead>
<tr>
<td><strong>Champ</strong></td>
<td><strong>Description</strong></td>
<td><strong>Champ d’application</strong></td>
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
<td>Message qui s’affiche lorsqu’un client sélectionne un élément récupéré en magasin pour un élément qui n’est pas disponible pour le nettoyage en magasin. Si nécessaire, vous pouvez personnaliser le texte par défaut.
</td>
<td>Affichage en magasin</td>
<td>Non</td>
</tr>
</tbody>
</table>

>[!NOTE]
>
>Le paramètre [!UICONTROL Search Radius] n’est utilisé que si vous avez configuré l’ [emplacement du magasin et configuration du mappage](store-location-map-provider-setup.md) pour Adobe Commerce.

## Activation de la solution d’exécution de magasin

Activez la solution [!DNL Store Fulfillment] pour ajouter les fonctionnalités de nettoyage en magasin et côté serveur aux expériences d’achat et de passage en caisse dans votre vitrine Adobe Commerce.

<table>
<thead>
<tr>
<td><strong>Champ</strong></td>
<td><strong>Description</strong></td>
<td><strong>Champ d’application</strong></td>
<td><strong>Obligatoire</strong></td>
</tr>
 </thead>
 <tbody>
<tr>
<td><strong>[!UICONTROL Enabled]</strong></td>
<td>Activez ou désactivez la solution. Lorsque cette option est activée, configurez et utilisez les fonctionnalités d’exécution de magasin et établissez la connexion entre votre boutique Adobe Commerce et les services [!DNL Store Fulfillment]. Lorsque cette option est désactivée, toutes les fonctions d’exécution de magasin sont désactivées. Il n’existe aucune communication entre Adobe Commerce et les services d’exécution de magasin. Les informations de commande ne peuvent pas être traitées ni reçues.</td>
<td>Site Web</td>
<td>Oui</td>
</tr>
</tbody>
</table>

## Ajout des informations d’identification du compte

<table>
<tr>
<td><strong>Champ</strong></td>
<td><strong>Description</strong></td>
<td><strong>Champ d’application</strong></td>
<td><strong>Obligatoire</strong></td>
</tr>
<tr>
<td><strong>[!UICONTROL Environment]</strong></td>
<td>Sélectionnez <i>[!UICONTROL Sandbox]</i> ou <i>[!UICONTROL Production]</i><br></br>La sélection de [!UICONTROL Sandbox] permet la communication avec les services d’exécution dans un environnement de test.<br></br>La sélection de [!UICONTROL Production] permet la communication avec les services d’exécution dans un environnement en ligne.<br></br>Vous recevez un ensemble d’informations d’identification pour chaque environnement et vous pouvez gérer les deux ensembles dans la même installation. <br></br>Enregistrez les informations d’identification avant de valider la connexion.</td>
<td>Global</td>
<td>Oui</td>
</tr>
<tr>
<td><strong>[!UICONTROL API Server URL]</strong></td>
<td>URL du point d’entrée de l’API d’exécution de la boutique Walmart. La valeur doit correspondre à l’URL complète fournie pendant le processus d’intégration. Les clients d’exécution de magasin reçoivent à la fois un sandbox et une URL de production. Lors de l’ajout de valeurs, veillez à copier et coller l’URL complète, y compris la barre oblique à la fin "/".</td>
<td>Global</td>
<td>Oui</td>
</tr>
<tr>
<td><strong>[!UICONTROL Token Auth Server URL]</strong></td>
<td>URL du point de terminaison de l’authentification de l’exécution de la boutique Walmart. La valeur doit correspondre à l’URL complète fournie pendant le processus d’intégration. Vous recevez à la fois une URL Sandbox et une URL de production. Lors de l’ajout de valeurs, veillez à copier et coller l’URL complète, y compris la barre oblique à la fin "/".</td>
<td>Global</td>
<td>Oui</td>
</tr>
<tr>
<td><strong>[!UICONTROL Merchant Id]</strong></td>
<td>Votre identifiant commercial (client) unique fourni pendant le processus d’intégration. Cet identifiant est utilisé pour acheminer les commandes afin de vous assurer que vos magasins marchands les reçoivent.</td>
<td>Global</td>
<td>Oui</td>
</tr>
<tr>
<td><strong>[!UICONTROL Consumer Id]</strong></td>
<td>Identifiant d’intégration unique fourni pendant le processus d’intégration. Cet identifiant est utilisé pour authentifier toutes les communications entre Adobe Commerce et les services d’exécution de magasin.</td>
<td>Global</td>
<td>Oui</td>
</tr>
<tr>
<td><strong>[!UICONTROL Consumer Secret]</strong></td>
<td>Clé d’intégration unique fournie lors du processus d’intégration. Cette clé est utilisée pour authentifier toutes les communications entre Adobe Commerce et le service d’exécution de magasin.</td>
<td>Global</td>
<td>Oui</td>
</tr>
</table>

Après avoir configuré le [!UICONTROL Account Credentials], sélectionnez <strong>[!UICONTROL Validate Credentials]</strong> pour vérifier et établir une connexion au service d’exécution de magasin pour la première fois.

## Configuration de la journalisation

Les journaux des services d’exécution de magasin sont disponibles dans le fichier journal `var/log/walmart-bopis.log`.

Demandez à l’administrateur système de configurer vos environnements pour autoriser la gestion des exceptions afin que les exceptions liées à l’API puissent être capturées via le pare-feu ou le cache.

Comme le fichier journal de l’application peut croître rapidement, n’activez la journalisation de l’application que pendant une courte période, si nécessaire, par exemple lors de la résolution des problèmes d’exécution du magasin pour une commande [!DNL Commerce]. Cette configuration empêche les problèmes de temps de réponse dans les environnements de production causés par des fichiers journaux volumineux.

>[!TIP]
>
>Pour les installations sur site d’Adobe Commerce, demandez à votre administrateur système de configurer la rotation des journaux pour le fichier `var/log/walmart-bopis.log` afin de réduire la taille. Pour les installations sur site Adobe Commerce, reportez-vous à la section [Rotation du journal](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/next-steps/configuration.html#server-settings) du _Guide d’installation d’Adobe Commerce_. Pour Adobe Commerce sur les projets d’infrastructure cloud, voir [Affichage et gestion des journaux](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html).

<table>
<thead>
<tr>
<td><strong>Champ</strong></td>
<td><strong>Description</strong></td>
<td><strong>Champ d’application</strong></td>
<td><strong>Obligatoire</strong></td>
</tr>
</thead>
<tbody>
<tr>
<td><strong>[!UICONTROL Debug Mode]</strong></td>
<td>Le mode de débogage est utilisé pour augmenter l’activité consignée dans l’intégration. Lorsque cette option est désactivée, aucune information de débogage n’est consignée. Lorsque cette option est activée, toutes les informations de débogage sont consignées <br></br>Toutes les données consignées se trouvent dans le fichier : <pre>var/log/walmart-bopis.log</pre>
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
<td><strong>Champ d’application</strong></td>
<td><strong>Obligatoire</strong></td>
</tr>
<tr>
<td><strong>[!UICONTROL Retry Critical Error]</strong></td>
<td>Indique les tentatives de reprise d’une opération de synchronisation d’enregistrement après une erreur critique.<br></br>Des erreurs critiques se produisent chaque fois que l’intégration échoue à obtenir une réponse positive de la part du service d’exécution. Ces problèmes se produisent lorsque le service est en panne ou lorsqu’une erreur se produit dans les données de commande envoyées.<br></br>Lorsque le seuil de reprise est atteint, l’élément reste dans la file d’attente, mais n’est pas traité à nouveau. Affichez tous les éléments contenant des erreurs de la gestion de <strong>[!UICONTROL System > Tools > Store Fulfillment Queue]</strong> dans l’administrateur. Pour résoudre les problèmes liés aux éléments qui échouent constamment, contactez votre gestionnaire de compte.</td>
<td>Global</td>
<td>Non</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Error Notification Email]</strong></td>
<td>Activez les notifications d’erreur pour recevoir un courrier électronique lorsque le [!UICONTROL Retry Critical Error Threshold] est atteint pour une commande. La notification inclut tous les détails disponibles sur l’erreur.</td>
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
<td><strong>Champ d’application</strong></td>
<td><strong>Obligatoire</strong></td>
</tr>
</thead>
<tbody>
<tr>
<td><strong>[!UICONTROL Barcode Source]</strong></td>
<td>L’attribut catalog qui stocke le code pouvant être analysé pour les éléments correspondants dans vos emplacements marchands.<br></br>Si vous n’avez qu’un seul emplacement commercial existant, il est probable que vous utilisiez des codes CUP, tandis que votre canal de commerce électronique identifie les produits par SKU. Dans ce scénario, sélectionnez l’attribut catalog qui contient le code UPC.<br></br>Ce paramètre garantit que les commandes envoyées à vos magasins répertorient les éléments avec l’identifiant correct afin que les associés au magasin puissent analyser précisément les éléments pendant le processus de sélection.<br></br>Si vous n’êtes pas sûr, vérifiez auprès de vos associés d’exécution du service Expédition et sélection pour déterminer l’attribut à envoyer. Si l’attribut n’est pas actuellement inclus dans la base de données, vous pouvez l’ajouter au jeu d’attributs de produit Adobe Commerce.</td>
<td>Site Web</td>
<td>Oui</td>
</tr>
<tr>
<td><strong>[!UICONTROL Barcode Type]</strong></td>
<td>L’attribut catalog qui stocke la source du code à barres pour les éléments correspondants dans vos emplacements marchands.<br></br>Ce paramètre garantit que les commandes envoyées à vos magasins répertorient les éléments avec un identifiant correct afin que les associés au magasin puissent analyser précisément les éléments pendant le processus de sélection. Les options incluent : SKU, UPC, GTIN, UPCA, EAN13, UPCE0, DISA, UAB, CODABAR, Price Embedded UPC.<br></br>Si vous n’êtes pas sûr, sélectionnez l’option qui ressemble le plus aux valeurs contenues dans votre attribut [!UICONTROL Barcode Source]. Les associés de magasin peuvent toujours faire correspondre des éléments manuellement à partir de leur liste de sélection.</td>
<td>Site Web</td>
<td>Oui</td>
</tr>
<tr>
<td><strong>[!UICONTROL Max Number of Items]</strong></td>
<td>Nombre maximal d’éléments à envoyer simultanément à partir de la file d’attente d’exécution du magasin.<br></br>Les commandes BOPIS sont envoyées par lots au service d’exécution, à intervalles réguliers. Ce paramètre vous permet de contrôler la taille du lot.<br></br>La valeur par défaut est de 100 éléments. Selon le volume et la capacité de votre commande, vous pouvez ajuster la valeur maximale vers le haut ou vers le bas.</td>
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
<td><strong>Champ d’application</strong></td>
<td><strong>Obligatoire</strong></td>
</tr>
</thead>
<tbody>
<tr>
<td><strong>[!UICONTROL Enable Ship To Store]</strong></td>
<td>Le paramètre d’expédition vers l’entrepôt repose sur vos capacités d’expédition vers l’entrepôt existantes. Si vous utilisez Inventory management, ou si vous pouvez accepter et exécuter des commandes dans des emplacements marchands sans inventaire via des transferts d’inventaire magasin à magasin, définissez cette option sur "Oui".<br></br>Si vous ne pouvez pas prendre en charge l’option de livraison ou si vous ne souhaitez pas l’offrir, définissez sur "Non". Lorsque cette option est désactivée, les articles de votre catalogue dont l’inventaire est nul pour un magasin marchand ou ceux qui se trouvent sous le [!DNL Out of Stock Threshold] de cet emplacement ne sont pas proposés avec les options de récupération en magasin.<br></br>Vous pouvez ajuster la valeur de ce paramètre par emplacement commercial.</td>
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
<td><strong>Champ d’application</strong></td>
<td><strong>Obligatoire</strong></td>
</tr>
</thead>
<tbody>
<tr>
<td><strong>[!UICONTROL Enable Ship From Store]</strong></td>
<td>Active ou désactive l’option Livraison à domicile dans vos magasins marchands. Lorsque cette option est activée, les emplacements de magasin marchand sont pris en compte dans l’ensemble avec d’autres sources affectées dans le stock associé à votre site web.<br></br>Dans les services Inventory management standard, l’option [!DNL Ship from Store] est inhérente et ne peut pas être désactivée. Avec la solution d’exécution de magasin, vous pouvez l’activer ou la désactiver.<br></br>Vous pouvez ajuster ce paramètre par emplacement commercial et par produit.</td>
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
<td><strong>Champ d’application</strong></td>
<td><strong>Obligatoire</strong></td>
</tr>
 </thead>
 <tbody>
<tr>
<td><strong>[!UICONTROL User Session Lifetime]</strong></td>
<td>Période, en secondes, pendant laquelle une session utilisateur associée de magasin reste active avant la déconnexion automatique. Les valeurs valides sont comprises entre 60 et 31536000.</td>
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
<td><em>[!UICONTROL Yes]</em>: l’utilisateur doit modifier son mot de passe après la configuration du compte.<br></br><em>[!UICONTROL No]</em> : recommande à l’utilisateur de changer de mot de passe après la configuration du compte.</td>
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

## Méthodes de diffusion

L’exécution de magasin fonctionne en étendant les fonctionnalités natives d’ Adobe Commerce [!DNL In-Store Delivery] . Après avoir installé l’extension, vous pouvez configurer les méthodes de remise en magasin à l’aide des paramètres étendus suivants qui sont ajoutés à l’administrateur.

- **Prise en main en magasin** : options d’offre pour la diffusion en magasin pendant le processus de passage en caisse
Ces paramètres configurent les scénarios de diffusion les plus courants pour les commandes BOPIS.

- **[!UICONTROL Curbside pick up]** - Options d’offre permettant aux clients de se garer à un emplacement de magasin et de recevoir leur commande par un associé du magasin.

Configurez ces paramètres à partir de l’administrateur en sélectionnant <strong>[!UICONTROL Stores > Configuration > Sales > Delivery Methods > In-Store Pickup]</strong>.

>[!NOTE]
>
>Pour plus d’informations sur la configuration des options de remise en magasin, voir [Diffusion en magasin](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/delivery/basic-methods/shipping-in-store-delivery) dans le _Guide de l’utilisateur d’Adobe Commerce_.


### Configuration des méthodes de diffusion

Avec la méthode de remise en magasin, le client peut sélectionner une source à utiliser comme emplacement de récupération lors du passage en caisse.

<table>
<thead>
<tr>
<td><strong>Champ</strong></td>
<td><strong>Description</strong></td>
<td><strong>Champ d’application</strong></td>
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
<th><strong>Champ d’application</strong></th>
<th><strong>Obligatoire</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>Titre de la diffusion d’accueil</strong></td>
<td>Spécifie le titre à afficher pour l’option Livraison à domicile dans les zones Produit, Panier et Passage en caisse. La diffusion à domicile fait référence aux fonctionnalités d’expédition standard d’Adobe Commerce, depuis un entrepôt, par un opérateur ou directement vers l’adresse d’expédition fournie par le client. </br></br>Ce libellé n’a aucune incidence sur les étiquettes des méthodes d’expédition pour l’opérateur de livraison sélectionné.</td>
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
<td>Ce libellé s’affiche lorsqu’un client dispose d’options de remise et qu’un sélecteur en magasin est disponible. </br></br>Vous pouvez personnaliser ce libellé qui s’affiche dans les zones produit, panier et passage en caisse.</td>
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
<td>Lorsqu’une commande est prête à être récupérée dans vos magasins de détail, le client est averti par e-mail. Si le client a sélectionné [!DNL In-Store Pickup] pendant le passage en caisse, vous pouvez personnaliser les instructions de prise en main ici. </br></br>Ces instructions sont définies globalement et s’appliquent à tous les emplacements de magasins de détail. Vous pouvez également personnaliser les instructions au niveau de l’emplacement du magasin de détail.</td>
<td>Affichage en magasin</td>
<td>Non</td>
</tr>
<tr>
<td><strong>Instructions de récupération des banlieues</strong></td>
<td>Spécifie les instructions de récupération de commande personnalisées à inclure dans les notifications par e-mail des clients pour les commandes de nettoyage. </br></br>Ces instructions sont définies globalement et s’appliquent à tous les emplacements de magasins de détail. Vous pouvez également personnaliser les instructions au niveau de l’emplacement du magasin de détail.</td>
<td>Affichage en magasin</td>
<td>Non</td>
</tr>
<tr>
<td><strong>Délai d’avance estimé pour la collecte</strong></td>
<td>Nombre de minutes nécessaires avant la réception, l’exécution et la préparation d’une commande. Ces informations s’affichent pour le client lors de la sélection de l’emplacement d’un magasin de détail pour l’option de remise Sélecteur de magasin . Ce paramètre s’applique à tous les emplacements de magasins de détail. Vous pouvez également personnaliser le délai d’avance au niveau de l’emplacement du magasin de détail.</td>
<td>Affichage en magasin</td>
<td>Non</td>
</tr>
<tr>
<td><strong>Étiquette du temps de récupération estimé</strong></td>
<td>Affiche la durée estimée jusqu’à ce qu’une commande soit disponible pour la récupération des clients. Ces informations s’affichent pour les clients lorsqu’ils sélectionnent un emplacement de boutique pour l’option de diffusion [!DNL In-Store Pickup]. </br></br>Lors de la personnalisation de cette étiquette, vous pouvez utiliser le code <code>%1</code> pour insérer le <strong>temps d’avance estimé pour la collecte</strong>. Par exemple : </br></br><code>Ready for Pickup in %1 minutes.</code></br></br>Ce paramètre s’applique à tous les emplacements de magasins de détail. Vous pouvez également personnaliser le délai d’avance au niveau de l’emplacement du magasin de détail.</td>
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
<th><strong>Champ d’application</strong></th>
<th><strong>Obligatoire</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>En stock</strong></td>
<td>Lorsqu’un client utilise le localisateur de la boutique de détail, la disponibilité du stock des articles en cours s’affiche pour chaque emplacement. </br></br>Vous pouvez personnaliser l’étiquette d’état <em>[!UICONTROL in-stock]</em> ici.</td>
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
<td>Lorsqu’un client utilise le localisateur de la boutique de détail, la disponibilité du stock de tous les articles en cours s’affiche pour chaque emplacement. </br></br>Vous pouvez personnaliser l’étiquette d’état <em>[!UICONTROL partially in-stock]</em> ici.</td>
<td>Affichage en magasin</td>
<td>Non</td>
</tr>
</tbody></table>

