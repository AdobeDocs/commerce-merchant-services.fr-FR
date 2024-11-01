---
title: Test et déploiement de l’exécution du magasin
description: Planifiez le test pour vérifier la fonctionnalité d’exécution de magasin. Les tests couvrent l’API de synchronisation du stock, le workflow d’exécution de bout en bout pour les commandes annulées, la gestion des utilisateurs de l’application Store Fulfillment et l’expérience d’archivage client.
role: User, Admin
level: Intermediate
feature: Shipping/Delivery, User Account, Roles/Permissions
exl-id: 77285a66-5161-407b-94cd-b3f412d7949d
source-git-commit: 37380063242b6d904910be731b8e58471625e9cb
workflow-type: tm+mt
source-wordcount: '2661'
ht-degree: 0%

---

# Test et déploiement de l’exécution de la boutique pour Adobe Commerce

Une fois le processus d’intégration terminé dans votre environnement de développement, vous pouvez démarrer le processus de test et de déploiement de la solution Store Fulfillment dans votre environnement de production.

**Conditions préalables**

Avant de tester ou de synchroniser des informations, des magasins ou des commandes, vérifiez que vous avez effectué les tâches suivantes :

- [Configuration générale](enable-general.md) pour les services d’exécution de magasin.

- [Ajout et validation des informations d’identification du compte et des détails de connexion pour votre environnement de test et vos environnements de production](connect-set-up-service.md#configure-store-fulfillment-account-credentials)

- Vérifiez que l’ [ intégration Adobe Commerce](connect-set-up-service.md#configure-store-fulfillment-account-credentials) pour la solution d’exécution de magasin est disponible et autorisé.

## Préparation du test

La configuration de la connexion doit être effectuée avant de pouvoir créer des commandes de test ou effectuer des tests d’intégration. Avant de procéder au test, vous devez également vérifier que les données de votre magasin sont synchronisées.

1. Synchronisez les sources d’exécution de magasin.

   - Accédez à **[!UICONTROL Stores > Sources]**.

   - Sélectionnez **[!UICONTROL Synchronize Store Fulfillment Sources]**.

1. Dans la grille de magasin, vérifiez que les magasins ont été marqués comme `Synced` avant de créer des commandes de test.

## Exemple de plan de test

Les détaillants valident les fonctionnalités de base de la solution d’exécution de magasin pendant les phases de configuration et de test d’un déploiement. Cet exemple de plan de test fournit un point de départ pour les tests. Ajoutez d’autres scénarios en fonction de vos besoins.

>[!NOTE]
>
>Après avoir effectué l’intégration initiale de la solution Store Fulfillment ou mis à jour une installation existante, testez toujours l’application dans un environnement hors production avant de la déployer en production.

Cet exemple de plan de test couvre les domaines fonctionnels suivants :

| Domaine fonctionnel | Fonction | Rôle |
|-------------------------------------|------------------------------------------|----------------------------------|
| Synchronisation des stocks et des commandes | Synchronisation de l’API d’inventaire | Administrateur Adobe Commerce |
| De bout en bout | Workflows d’annulation de commande | Client, administrateur, associé de magasin |
| Administration | Autorisations de l’application d’exécution de magasin | Administration |
| Adobe Commerce Frontend | Types de produits | Client, administrateur |
| Formulaire d’archivage</br>Frontend Checkout | Expérience d’archivage | Client, administrateur |
| Application d’aide à la boutique | Commande</br>Pick</br>Stage</br>et passation | Association de magasin |

### Synchronisation des API d’inventaire

Cette section du plan de test couvre la synchronisation des stocks et des stocks afin de vérifier que les mises à jour des sources et des stocks de récupération sont synchronisées correctement entre Adobe Commerce et la solution d’exécution de magasin.

**Domaine fonctionnel** : synchronisation de l’inventaire et des commandes</br>
**Rôle :** Admin</br>
**Type de test :** All Positive

<table>
<thead>
<tr>
<th>Fonction</th>
<th>Scénario de test</th>
<th>Résultats attendus</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>Ajouter la source du stock de prise en charge</strong></td>
<td>Enregistrez une nouvelle source de stock de reprise.</td>
<td>La synchronisation en temps réel envoie les détails source au service de GIF Walmart dans les 5 minutes.</td>
</tr>
<tr>
<td><strong>Mettre à jour la source du stock de prise en charge existante</strong></td>
<td>Enregistrez les mises à jour dans une source de stock existante.</td>
<td>L’opération de synchronisation en temps réel envoie les détails au GIF Walmart dans les 5 minutes.</td>
</tr>
<tr>
<td><strong>État de la source du stock de récupération</br><code>Is Synced</code></strong></td>
<td>Enregistrez les mises à jour dans une source de stock existante.</td>
<td>Après une opération réussie, la colonne <code>Is Synced</code> de la page Gérer Source se met à jour de <code>No</code> vers <code>Yes</code>.</td>
</tr>
<tr>
<td><strong>Modification du processus de réservation de stock</strong></td>
<td>Créez et envoyez une nouvelle commande pour un produit.</td>
<td>La quantité vendue pour le produit diminue en conséquence.</td>
</tr>
<tr>
<td><strong>Nouvelle commande push, synchronisation d’API, commande client</strong></td>
<td>Le client envoie une commande de prise en main de magasin.</td>
<td><ul><li>Dans la vue Admin Order, un <strong>utilisateur administrateur Adobe Commerce</strong> constate que l’état de synchronisation des commandes a été mis à jour vers <code>Sent</code></li><li>Le journal des détails de la commande comprend le message <code>Order was sent to BOPIS solution for sync, it's not yet acknowledged yet.</code></li></ul></td>
</tr>
<tr>
<td><strong>Nouvelle commande push, synchronisation API : l’administrateur envoie la commande</strong></td>
<td>Un <strong>administrateur</strong> Adobe Commerce envoie une commande de récupération.</td>
<td><ul><li>Dans la vue Admin Order, l’état de synchronisation des commandes est mis à jour vers <code>Sent</code>.</li><li>Le journal des détails de la commande comprend le message <code>Order was sent to BOPIS solution for sync, it's not yet acknowledged yet.</code></li></ul></td>
</tr>
<tr>
<td><strong>Nouvelle commande push, file d’attente des exceptions<strong></td>
<td>Identifiez plusieurs produits virtuels et téléchargeables dans l’administrateur Adobe Commerce qui peuvent être exécutés via Adobe Commerce sans avoir à interagir avec le service d’exécution (FaaS).</td>
<td>Ces produits sont supprimés ou marqués de manière appropriée dans l’exportation afin d’éviter un conflit en aval avec la FaaS.</td>
</tr>
</tbody>
</table>

### Workflows d’annulation de commande

Cette section du plan de test comprend des scénarios de test visant à tester le workflow de bout en bout pour les commandes annulées via Adobe Commerce.

**Zone fonctionnelle :** Administrateur Adobe Commerce</br>
**Rôle :** de bout en bout (administrateur, associé de magasin, client)</br>
**Type de résultat du test :** positif pour tous les scénarios

<table style="table-layout:fixed">
<tr>
<th>Fonction</th>
<th>Scénario</th>
<th>Résultats attendus</th>
</tr>
<tr>
<td><strong>Annulation complète de commande</strong></td>
<td><ol>
<li>Ordre de priorité.</li>
<li>Attendez que la commande soit synchronisée.</li>
<li>Vérifier la création d'une facture (le cas échéant autoriser et enregistrer) à réception de l'email de facture.</li>
<li>Créez une Note de crédit avec tous les produits commandés depuis la vue Facture.</li>
</ol>
</td>
<td>
<ul>
<li>Historique des commandes mis à jour avec <code>We refunded $X online. Transaction ID: transactionID</code> et <code>Received Cancel acknowledgment from the BOPIS solution.</code></li>
<li>L’état de la commande est <code>Closed</code>. (Nous avons défini la vérification des paiements maintenant.)</li>
<li>Note de crédit créée dans Adobe Commerce. (Attendez que cron fonctionne.)</li>
<li>Si tous les éléments sont sélectionnés, alors prêt pour le sélecteur <code>DISPLAY COMMENT HISTORY</code> affiche <code>Order is ready for pickup</code> (<code>CUSTOMER NOTIFIED</code> l’indicateur est <code>true</code>).</li>
<li>Si tous les éléments ne sont pas sélectionnés, le courrier électronique d’annulation et l’ HISTORIQUE DU COMMENTAIRE AFFICHAGE s’affichent. <code>Order has been canceled - all items were not available</code></li>
<li><code>CUSTOMER NOTIFIED</code> L’indicateur est <code>true</code>.)</li>
</ul>
</td>
</tr>
<tr><td><strong>Annulation partielle de la commande<strong></td>
<td>
<ol>
<li>Passer commande avec au moins deux produits.</li>
<li>Attendez que la commande soit synchronisée.</li>
<li>Vérifier que la facture a été créée (si autoriser et enregistrer) et que le courrier électronique de facture a été reçu.</li>
<li>Patientez deux heures pour le règlement des transactions.</li>
<li>Créez une Note de crédit avec uniquement une partie des produits commandés à partir de la vue Facture.</li>
</td>
<td>
<ul>
<li>Mise à jour de l’historique des commandes : <code>We refunded $X online. Transaction ID: transactionID</code></li>
<li>Mise à jour de l’historique des commandes : <code>Order notified as partly canceled at: Date and Hour</code></li>
<li>Réception de l'email de remboursement de la commande : <code>$x amount was refunded</code></li>
<li>L’état de la commande est <code>Processing</code>.</li>
<li>Note de crédit créée dans Adobe Commerce (attendez que cron fonctionne).</li>
<li>Si certains articles n'ont pas été sélectionnés, vérifiez que l'email [!UICONTROL Ready for Pickup] avec la section nil pick or return s'affiche. <code>DISPLAY COMMENT HISTORY</code> affiche <code>Order is ready for pickup, but some items not available.</code>.</li>
<li><code>CUSTOMER NOTIFIED</code> L’indicateur est <code>true</code>.</li>
</ul>
</td>
</tr>
<td><strong>Prêt pour la récupération</br></br>Annulation complète</br>(tous les produits sont définis comme sélectionnés avec une quantité 0)</strong></td>
<td>
<ol>
<li>Placez la commande.</li>
<li>Attendez que la commande soit synchronisée.</li>
<li>Vérifier que la facture a été créée (si autoriser et enregistrer) et que le courrier électronique de facture a été reçu.</li>
<li>Accédez à Postman et exécutez la requête Ready for Pickup (Prêt pour la collecte) avec tous les produits définis comme <code>picked</code> avec <code>0 qty</code>.</li>
</ol>
</td>
<td>
<ul>
<li>Historique des commandes mis à jour : <code>We refunded $X offline</code></li>
<li>L’état de la commande est <code>CLOSED</code>.
<li>L’avoir est créé. (Attendez que cron fonctionne.)</li>
<li>Réception de l’email de remboursement : <code>$x amount was refunded</code></li>
<li>Envoi de l’email d’annulation de commande.</li>
</ul>
</td>
</tr>
<tr>
<td><strong>Prêt pour la récupération - Annulation partielle</strong></br></br><strong>(Certains produits sont sélectionnés et d’autres sont sélectionnés avec <code>0 qty</code>)</strong>
</td>
<td>
<ol>
<li>Placez la commande.</li>
<li>Attendez que la commande soit synchronisée.</li>
<li>Vérifier que la facture a été créée (si autoriser et enregistrer) et que le courrier électronique de facture a été reçu.</li>
<li>Accédez à Postman et exécutez la demande Prêt pour la collecte avec une partie des produits définis comme sélectionnés avec 0 quantité et le reste d’entre eux sélectionnés.</li>
</ol>
</td>
<td>
<ul>
<li><code>Your order is ready for pickup</code> avec les tables [!UICONTROL Ready for Pickup Items] et [!UICONTROL Canceled Items]. </li>
<li>L’état de la commande est PRÊT À ÊTRE SÉLECTIONNÉ. </li>
<li>Historique des commandes mis à jour : <code>We refunded $X offline.</code>
<li>Historique des commandes mis à jour : <code>Order notified as partly canceled at: Date and hour</code>
<li>Réception de l’e-mail de remboursement : <code>$x amount was refunded</code>
<li>La note de crédit est créée. (Attendez que cron fonctionne.)</li>
</ul>
</td>
</tr>
<tr>
<td><strong>Prêt pour la récupération - Annulation partielle</br></br>Certains produits sont sélectionnés et d’autres le sont avec <code>0 qty</code>)</strong>
</td>
<td><ol>
<li>Placez la commande.</li>
<li>Attendez que la commande soit synchronisée.</li>
<li>Vérifier que la facture a été créée (si autoriser et enregistrer) et que le courrier électronique de facture a été reçu.</li>
<li>Accédez à Postman et exécutez la demande Prêt pour la collecte avec une partie des produits définis comme sélectionnés avec 0 quantité et le reste d’entre eux sélectionnés.</li>
</ol>
</td>
<td><ul>
<li><code>Your order is ready for pickup</code> avec les tables [!UICONTROL Ready for Pickup Items] et [!UICONTROL Canceled Items]. </li>
<li>L’état de la commande est PRÊT À ÊTRE SÉLECTIONNÉ. </li>
<li>Historique des commandes mis à jour : <code>We refunded $X offline.</code>
<li>Historique des commandes mis à jour : <code>Order notified as partly canceled at: Date and hour</code>
<li>Réception de l’e-mail de remboursement : <code>$x amount was refunded</code>
<li>La note de crédit est créée. (Attendez que cron fonctionne.)</li>
</ul>
</td>
</tr>
<tr>
<td><strong>Distribué (pendant la distribution) </br></br>Annulation complète (tous les produits sont définis comme rejetés)</strong>
</td>
<td>
<ol>
<li>Placez la commande.</li>
<li>Attendez que la commande soit synchronisée.</li>
<li>Vérifier que la facture a été créée (si autoriser et enregistrer) et que le courrier électronique de facture a été reçu.</li>
<li>Accédez à Postman et exécutez la demande Prêt pour la collecte avec tous les produits définis comme sélectionnés.</li>
<li>Ouvrez votre boîte mail, recherchez l'email Prêt pour la collecte . Cliquez ensuite sur **[!UICONTROL Confirm Arrival]**.</li>
<li>Archivez-vous.</li>
<li>Accédez à Postman et exécutez la requête Distribué avec tous les produits définis comme rejetés.</li>
</ol>
<td><ul>
<li>Historique des commandes mis à jour : <code>We refunded $X offline.</code></li>
<li>Réception de l’email de remboursement : <code>$x amount was refunded</code></li>
<li>État défini sur <code>CLOSED</code>.</li>
<li>Note de crédit créée. (Attendez que cron fonctionne.)</li>
</ul>
</td>
</tr>
<tr>
<td><strong>Distribué (pendant la distribution)</br></br>Annulation partielle</br>(Certains produits sont refusés ; certains sont rejetés.)</strong>
</td>
<td>
<ol>
<li>Placez la commande.</li>
<li>Attendez que la commande soit synchronisée.</li>
<li>Vérifier que la facture a été créée (si autoriser et enregistrer) et que le courrier électronique de facture a été reçu.</li>
<li>Accédez à Postman, puis exécutez la demande Prêt pour la collecte avec tous les produits définis comme sélectionnés.</li>
<li>Ouvrez votre boîte aux lettres. Recherchez l'email Prêt pour la collecte et sélectionnez <code>Confirm Arrival</code>.</li>
<li>Archivez-vous.</li>
<li>Accédez à Postman, puis exécutez la requête Distribué avec certains produits dont le statut est Distribué et certains produits rejetés.</li>
</ol>
</td>
<td>
<li>Historique des commandes mis à jour : <code>We refunded $X offline</code></li>
<li><code>Order notified as partly canceled at: Date and Hour</code>
<li>Réception de l’e-mail de remboursement : <code>$x amount was refunded</code>
<li>État de la commande défini sur <code>Ready for pickup Dispensed</code>
<li>Note de crédit créée. (Attendez que cron fonctionne.)</li>
</td>
</tr>
<tr>
<td> <strong>Nouvelle RAM après retour (complète)</strong>
</td>
<td>
<ol>
<li>Placez la commande.</li>
<li>Attendez que la commande soit synchronisée.</li>
<li>Si l'option d'autorisation et de capture est paramétrée, vérifiez que la facture a été créée et que le client a bien reçu l'email de la facture.</li>
<li>Sélectionnez tous les produits avec Postman.</li>
<li>Archivez-vous.</li>
<li>Fais un passe-temps.</li>
<li>Accédez à la commande et sélectionnez<strong>[!UICONTROL Create returns]=
<li>Créez la zone de gestion régionale.</li>
</ol>
</td>
<td>
<ul>
<li>La RMA a été créée et s’affiche sous l’onglet <strong>[!UICONTROL Returns]</b> de la vue Commande.</li>
<li>Le client a reçu un e-mail de confirmation RMA.</li>
</ul>
</td>
</tr>
<tr>
<td><strong>Nouvelle RAM après retour — Partiel</strong>
</td>
<td>
<ol>
<li>Placez la commande.</li>
<li>Attendez que la commande soit synchronisée.</li>
<li>Vérifier que la facture a été créée (si autoriser et enregistrer) et que le courrier électronique de facture a été reçu.</li>
<li>Sélectionnez tous les produits avec Postman.</li>
<li>Archivez-vous.</li>
<li>Fais un passe-temps.</li>
<li>Exécutez la commande, puis sélectionnez  <strong>[!UICONTROL Create returns]</strong></li>
<li>Créez la RAM avec une partie des produits commandés.</li>
</ol>
<td>
<ul>
<li>RMA créée et affichée sous l’onglet <strong>[!UICONTROL Returns]</strong> dans la vue Commande.</li>
<li>Le client a reçu l’e-mail de confirmation de la RMA.</li>
<li>Après avoir créé la RMA, obtenez l’autorisation RMA : depuis l’administrateur, accédez à <strong>[!UICONTROL Sales > Returns]</strong>. Sélectionnez la RMA que vous avez créée et autorisez-la.</li>
<li>Vérifiez que le client a reçu l’e-mail de confirmation d’autorisation RMA.</li>
<li>Vérifiez que le remboursement a été ajouté à l'historique des transactions et des commandes.</li>
</ul>
</td>
</tr>
</table>


### Autorisations de l’application d’exécution de magasin

Cette section du plan de test couvre la gestion du compte pour les utilisateurs de l’application d’exécution de magasin.

- Vérifiez qu’un associé de magasin peut s’authentifier auprès d’un nouveau compte utilisateur créé à partir de l’administrateur Adobe Commerce.
- Confirmez que les mises à jour des comptes existants sont appliquées avec succès.

**Zone fonctionnelle :** Administrateur Adobe Commerce</br>
**Rôle :** Admin, Magasin Associé</br>
**Type de test :** Tous positifs

<table style="table-layout:auto">
<tr>
<th>Fonction</th>
<th>Scénario</th>
<th>Résultats attendus</th>
</tr>
<tr>
<td><strong> Gestion de compte d’utilisateur - Créer un compte</strong></br></br>
</td>
<td>
<ol>
<li><strong>Admin</strong> — Connectez-vous à l’administrateur Adobe Commerce</li>
<li>Accédez à <strong>[!UICONTROL System] &gt; Autorisations de l’application d’exécution de la boutique &gt; Tous les utilisateurs de l’application d’exécution de la boutique</strong></li>
<li><strong>Ajouter un nouvel utilisateur.</strong></li>
</ol>
<td>
<ul>
<li>Compte créé.</li>
<li>Le nouveau compte utilisateur s’affiche sur le tableau de bord [!UICONTROL Store Fulfillment Users].</li>
<li><strong>Magasin Associé</strong> Connectez-vous à l’application d’assistance en magasin avec un nouveau compte d’utilisateur.</li>
</ul>
</td>
</tr>
<tr>
<td><strong>Gestion des comptes d’utilisateurs - Mettre à jour le compte d’utilisateur existant</strong>
</td>
<td>
<ol>
<li>Connectez-vous à l’administrateur Adobe Commerce avec le compte d’utilisateur administrateur.</li>
<li>Accédez à <strong>[!UICONTROL System] &gt; Autorisations de l’application d’exécution de la boutique &gt; Tous les utilisateurs de l’application d’exécution de la boutique</strong>.</li>
<li>Dans la liste Compte utilisateur , ouvrez un compte utilisateur actif existant en sélectionnant <strong>[!UICONTROL Edit]</strong>.
<li>Désactivez le compte en remplaçant <strong>[!UICONTROL Is Active]</strong> par <strong>Non</strong>.</li>
</ol>
</td>
<td>
<ul>
<li>Sur le tableau de bord <strong>[!UICONTROL Store Fulfillment App Users]</strong>, l’état du compte mis à jour a été remplacé par <strong>[!UICONTROL Inactive]</strong>.</li>
<li>L’association de magasin ne peut pas se connecter à l’application d’assistance de magasin avec les informations d’identification du compte inactif.</li>
</ul>
</td>
</tr>
</table>

## Types de produits Adobe Commerce

Les scénarios de test pour les types de produits Adobe Commerce vérifient que les clients voient les informations appropriées sur les produits, les stocks et les méthodes de diffusion pour différents types de produits :

- [!UICONTROL Configurable]
- [!UICONTROL Grouped]
- [!UICONTROL Virtual]
- [!UICONTROL Bundle products] dans le storefront Adobe Commerce.

**Zone fonctionnelle :** Adobe Commerce Frontend</br>
**Rôle :** Utilisateur de l’application d’assistance au magasin (associé au magasin)</br>
**Type de test :** Tous positifs

<table style="table-layout:auto">
<tr>
<th>Fonction</th>
<th>Scénario</th>
<th>Commentaires</th>
</tr>
<tr>
<td><strong>Produits configurables</strong>
</td>
<td>
<ul>
<li>Vérifiez que l’utilisateur ne peut afficher que ces options configurables, quelle source est activée, quel stock est affecté et qu’il existe certains éléments en stock, et vérifiez les produits enfants.</li>
<li>Vérifiez que lorsque vous sélectionnez un autre magasin, les options qui ne sont pas disponibles s’affichent comme barré.</li>
<li>Vérifiez que si l’utilisateur sélectionne un autre magasin, les options configurables ne sont pas sélectionnées.</li>
<li>Vérifiez que si un produit configurable est déjà dans le panier et qu’un utilisateur sélectionne un autre magasin, le produit s’affiche comme étant en rupture de stock.</li>
</ul>
</td>
<td></td>
</td>
</tr>
<tr>
<td><strong>Produits groupés</strong>
</td>
<td>
<ul>
<li>Vérifiez que les méthodes de diffusion et le bouton [!UICONTROL Add to cart] sont désactivés pour le client lorsque tous les produits enfants ont
<code>qty</code> défini sur <code>0</code>.</li>
<li>Vérifiez que les méthodes de diffusion sont activées pour le client lorsque <code>qty</code> est défini sur au moins un des produits enfants. <code>0.</code></li>
<li>Vérifiez que la méthode [!UICONTROL Store Pickup Delivery] est visible et active uniquement pour les produits pour lesquels [!UICONTROL Available for Store Pickup] est activé. (Vérifiez le produit enfant.)</li>
</ul>
</td>
<td></td>
</tr>
<tr>
<td><strong>Produits virtuels</strong>
</td>
<td>
Vérifiez que les produits virtuels ne proposent pas la méthode de diffusion [!UICONTROL In-store Pickup].
<td></td>
</td>
</tr>
<tr>
<td><strong>Bundle products</strong>
</td>
<td>
<ul>
<li>Vérifiez que si [!UICONTROL Available for Store Pickup] au moins un produit enfant est désactivé, l’option de remise Stocker le sélecteur n’est pas disponible pour le client.</li>
<li>Vérifiez que si au moins un produit enfant est désactivé, l’option Livraison à domicile n’est pas disponible pour le client.[!UICONTROL Available for Home Delivery]</li>
<li>Vérifiez si au moins un des produits enfants d’un lot est en rupture de stock, le lot (produit parent) s’affiche également.
comme [!UICONTROL Out of stock].</li>
</ul>
</td>
<td></td>
</tr>
<tbody>
</table>

## Expérience d’archivage

Cette section du plan de test couvre l’ expérience d’archivage des commandes de nettoyage de magasin pour les fonctionnalités suivantes :

- Autre contact de récupération : vérifiez le workflow pour ajouter un [!UICONTROL Alternate Pickup Contact] et sélectionner un [!UICONTROL Preferred Contact] dans les commandes de nettoyage de la boutique.

- Formulaire d’archivage : vérifiez le processus d’envoi d’une demande d’archivage pour les commandes de nettoyage de la boutique.

**Domaines fonctionnels :** Passage en caisse, Formulaire d’archivage pour les commandes de prise en main du magasin</br>
**Rôle :** Admin, client, associé de magasin</br>
**Type de test :** Tous positifs

### Autre contact de collecte


**Zone fonctionnelle :** Passage en caisse</br>
**Rôle :** Client</br>
**Type de test :** Tous positifs

<table style="table-layout:auto">
<tr>
<th>Fonction</th>
<th>Scénario</th>
<th>Résultats attendus</th>
</tr>
<tr>
<td><strong>Autre contact de collecte</br>
Archivage<strong>
</td>
<td>
Un client envoie une commande avec l’option Sélecteur en magasin .</td>
<td>Pendant le processus de paiement, le client voit l’option [!UICONTROL Alternate Pickup Contact] sur l’étape Expédition.
</td>
</tr>
<tr>
<td><strong>Autre contact de collecte préféré, archivage</strong>
<td>
Un client envoie une commande avec l’option Sélecteur en magasin . Pendant le passage en caisse, le client ajoute un [!UICONTROL Alternate Pickup Contact].</td>
<td>Pendant le processus de paiement, le client voit l’option [!UICONTROL Preferred Contact] sur l’étape d’expédition.</td>
</td>
</tr>
<tr>
<td><strong>Autres coordonnées de contact de collecte, Check in</strong>
</td>
<td>
Un client envoie une commande avec l’option Sélecteur en magasin . Lors du passage en caisse, le client sélectionne [!UICONTROL Alternate Pickup Contact] sur l’étape d’expédition.
</td>
<td>Le client voit les options d’entrée pour saisir les coordonnées : [!UICONTROL First name], [!UICONTROL Last name], [!UICONTROL Phone] et [!UICONTROL Email].</td>
</tr>
<tr>
<td><strong>Autre ticket, archiver courrier électronique</strong>
</td>
<td>Un client envoie une commande avec l’option Sélecteur en magasin . Lors du passage en caisse, le client sélectionne [!UICONTROL Alternate Pickup Contact] sur l’étape d’expédition, ajoute les coordonnées et envoie la commande.</td>
<td>Le client et le contact suppléant reçoivent tous deux un e-mail d’archivage pour la commande.</td>
</tr>
<td><strong>Autre achat, détail de la commande</strong></td>
<td>Un client envoie une commande avec l’option Sélecteur en magasin . Lors du passage en caisse, le client sélectionne [!UICONTROL Alternate Pickup Contact] sur l’étape d’expédition, ajoute les coordonnées et envoie la commande.</td>
<td>L’administrateur voit les informations de contact supplémentaires sur la commande enregistrée.</td>
</tr>
<tr>
<td><strong>Autre contact de collecte, vue de commande associée du magasin</strong>
</td>
<td>Un client envoie une commande avec l’option Sélecteur en magasin . Lors du passage en caisse, le client sélectionne [!UICONTROL Alternate Pickup Contact] sur l’étape d’expédition, ajoute les coordonnées et envoie la commande.</td>
<td>L’associé du magasin peut voir les informations de contact supplémentaires sur la commande dans FaaS/ChaaS.</td>
</td>
</tr>
</tbody>
</table>

### Formulaire d’archivage


**Zone fonctionnelle :** Formulaire d’archivage</br>
**Rôle :** Client</br>
**Type de test :** Tous positifs

<table style="table-layout:auto">
<tr>
<th>Fonction</th>
<th>Scénario</th>
<th>Résultats attendus</th>
</tr>
<tr>
<td><strong> Check in Action—Submit request</strong>
</td>
<td>Sur le formulaire d’archivage, un client remplit tous les champs requis et envoie la demande.</td>
<td>Le client reçoit une réponse de succès.</td>
</tr>
<tr>
<td><strong>Archivage dans l’action : affichez les détails de la requête</strong></td>
<td>Un client envoie une demande d’archivage avec succès.</td>
<td>L’état de la commande est mis à jour dans le système FaaS et l’associé du magasin peut voir les détails de la demande d’archivage dans la FaaS.
</td>
</tr>
<tr>
<td><strong>Archiver l’action : envoyer la demande une seule fois</strong></td>
<td>Après avoir envoyé une demande d’archivage, un client sélectionne une seconde fois le lien pour s’archiver.</td>
<td>Dans le formulaire d’archivage, le client ne voit pas d’option lui permettant de modifier ou de renvoyer le formulaire.</td>
</tr>
<tr>
<td><strong>Archiver l’action : confirmer l’arrivée</strong></td>
<td>Une commande de récupération en magasin est marquée comme prête à être récupérée dans la page Facebook. Le client reçoit un email Prêt pour la collecte et sélectionne [!UICONTROL Confirm Arrival].</td>
<td>Le client voit le formulaire d’archivage pour la commande.</td>
</tr>
</tbody>
</table>

## Application d’assistance pour la boutique

Cette section du plan de test couvre les scénarios de test des workflows de commande, de sélection et de remise dans l’application d’aide à la boutique.

**Zone fonctionnelle :** Application d’assistance au magasin</br>
**Rôle :** Magasin Associé</br>
**Type de test :** Tous positifs

<table style="table-layout:auto">
<tr>
<th>Fonction</th>
<th>Scénario</th>
<th>Résultats attendus</th>
</tr>
<tr>
<td>
<strong>Sélection de commande unique : chemin heureux, sélection de bordure</strong></td>
<td>Sélectionnez des éléments uniques et multiquantité. Aucun saut nil et saut de bord (avec transfert).
</td>
<td>
</td>
</tr>
<tr>
<td><strong>Sélection multi-commande : chemin heureux, saut de bordure</strong></td>
<td>Éléments uniques et multiquantité. Aucun saut nil et saut de bord (avec transfert intermédiaire)</td>
<td></td>
</tr>
<tr>
<td><strong>Sélection de commande unique : sélection de chemin d’accès heureux en magasin</strong></td>
<td>Éléments uniques et multiquantité. Aucun saut nil et saut en magasin (avec évaluation)</td>
<td>
</td>
</tr>
<tr>
<td><strong>Sélection multi-commande : chemin heureux, saut en magasin</strong></td>
<td>Sélectionnez des éléments uniques et multiquantité. Aucun saut nil et saut de bord (avec transfert).</td>
<td></td>
</tr>
<tr>
<td><strong>Sélection de commande unique : chemin d’accès différent, sélection en magasin</strong></td>
<td>Sélectionnez des éléments uniques et multi-quantité avec sélection partielle, sélection simple et en magasin et sélection en magasin (avec évaluation).</td>
</td>
<td></td>
</tr>
<td><strong>Sélection multi-commande : pas de saut de chemin heureux</strong></td>
<td>Sélectionnez des éléments uniques et multi-quantité avec sélection partielle, sélection simple et en magasin et sélection en magasin (avec évaluation).</td>
<td></td>
</tr>
<td><strong>Sélection d’une seule commande : chemin non heureux, sélection côté serveur</strong></td>
<td>Sélectionnez des éléments uniques et multi-quantité avec sélection partielle, sélection par clic et sélection au niveau du curseur (avec évaluation).</strong></td>
</td>
<td></td>
</tr>
<tr><td><strong>Commande passée - annulée avant sélection</strong></td>
<td></td>
<td></td>
</tr>
<tr>
<td><strong>Commande passée - annulée avant remise</strong></td>
<td></td>
<td></td>
</tr>
<tr>
<td><strong>Ordre placé - Rechercher dans le module d’ordre</strong></td>
<td></td>
<td></td>
</tr>
<tr><td><strong>Commande passée : recherche et archivage manuel pour la remise</strong></td>
<td></td>
<td></td>
</tr>
<tr><td><strong>Ordre de tri : tous les éléments non sélectionnés ou non disponibles marqués par le sélecteur</strong></td>
<td></td>
<td></td></tr>
<tr><td><strong>Commande placée avec des éléments de lot - sélection et remise</strong></td>
<td></td>
<td></td></tr>
<tr><td><strong>Commande passée - Passe avec rejet</strong></td>
<td></td>
<td></td></tr>
<tr><td><strong>Commande passée - Remettez-la avec rejet de tous les éléments.</strong></td>
<td></td>
<td></td></tr>
</tbody>
</table>

## Déployer

Une fois que vous avez vérifié que la solution a été configurée et testée selon vos spécifications, vous êtes prêt à déployer de l’évaluation vers la production.

Le déploiement et les tests varient en fonction de votre infrastructure et de vos capacités.

>[!TIP]
>
>Pour obtenir des instructions de déploiement, des listes de contrôle et des bonnes pratiques pour Adobe Commerce sur les projets d’infrastructure cloud, voir [Déployer votre boutique](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/staging-production) dans la documentation Adobe Commerce Developer.
