---
title: Modèles de courrier électronique de vente
description: Configurez les modèles d’email transactionnel pour communiquer avec les clients et les administrateurs de magasin pendant le processus d’exécution des commandes de nettoyage de magasin.
role: Admin
level: Intermediate
feature: Shipping/Delivery, Communications, Configuration
exl-id: 688732e3-06f0-4613-a589-2d465597eb28
source-git-commit: 78b09113e72382053b01d6016276bae3aa545fa3
workflow-type: tm+mt
source-wordcount: '1233'
ht-degree: 0%

---


# Modèles de courrier électronique de vente

L’exécution de magasin offre un ensemble étendu de modèles d’email transactionnel pour prendre en charge les workflows de commande et d’exécution. Ils offrent une communication et des messages cohérents et automatisés sur tous les canaux : ils avertissent les clients et les administrateurs de magasins des changements d’état de la commande, des instructions pour les commandes de prise en main en magasin, etc.

Les modèles de courrier électronique d’exécution de magasin sont configurés avec la messagerie et les paramètres par défaut. Les administrateurs du commerce dans Adobe Commerce peuvent gérer et modifier les configurations, et sélectionner les modèles d’email pour communiquer avec les clients dans différents scénarios. Les administrateurs peuvent également configurer et personnaliser des modèles.

Configurez les modèles d’email de vente à partir de l’administrateur : **[!UICONTROL Stores > Configuration > Sales > Sales Emails]**.

## Emails - Paramètres généraux

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
<td><strong>Envoi asynchrone</strong></td>
<td>Détermine si les courriers électroniques de vente sont envoyés de manière asynchrone. Options : <br/>**`Désactiver** - (par défaut) Les emails de vente sont envoyés lorsqu’ils sont déclenchés par un événement. Pour le délai de communication et de réponse le plus rapide pour le nettoyage de la boutique, utilisez le paramètre par défaut. <br/>**`Activer`** : cette option permet de déplacer les processus qui gèrent le passage en caisse et le traitement des commandes des notifications email en arrière-plan à envoyer à intervalles réguliers et prédéterminés.</td>
<td>Affichage en magasin</td>
<td>Non</td>
</tr>
</tbody></table>

## Commande prête à être sélectionnée en magasin

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
<td><strong>Activé</strong></td>
<td>Cet e-mail est envoyé au client lorsque l’associé du magasin a terminé de sélectionner sa commande. Définissez cette variable sur "Non" pour désactiver la notification électronique. Si le modèle d’email est désactivé, cela n’empêche pas le choix d’une commande par l’associé du magasin.</td>
<td>Affichage en magasin</td>
<td>Non</td>
</tr>
<tr>
<td><strong>Commande prête pour l’expéditeur d’emails de récupération</strong></td>
<td>Identité de l’expéditeur utilisée lors de l’envoi de la notification électronique.</td>
<td>Affichage en magasin</td>
<td>Non</td>
</tr>
<tr>
<td><strong>Modèle De Courrier Électronique Prêt Pour La Commande</strong></td>
<td>Le modèle de message électronique utilisé pour notifier les clients enregistrés. Un modèle par défaut est fourni avec l’intégration.</td>
<td>Affichage en magasin</td>
<td>Non</td>
</tr>
<td><strong>Modèle de courrier électronique de commande prêt à recevoir pour l’invité</strong></td>
<td>Le modèle de message électronique utilisé pour avertir les clients invités. Un modèle par défaut est fourni avec l’intégration.</td>
<td>Affichage en magasin</td>
<td>Non</td>
</tr>
<tr>
<td><strong>Modèle de courrier électronique de commande prêt à recevoir pour un autre contact de collecte</strong></td>
<td>Le modèle de message électronique utilisé pour notifier les contacts supplémentaires nommés dans la commande. Un modèle par défaut est fourni avec l’intégration.</td>
<td>Affichage en magasin</td>
<td>Non</td>
</tr>
<tr>
<td><strong>Envoyer la commande prête pour la copie de l’e-mail de la sélection vers</strong></td>
<td>Liste d’adresses électroniques délimitées par des virgules pour envoyer une copie de chaque notification.</td>
<td>Affichage en magasin</td>
<td>Non</td>
</tr>
<tr>
<td><strong>Envoyer la commande prête pour la méthode Copie d’email de récupération</strong></td>
<td>La méthode de copie d’email (copie carbone) à utiliser.</td>
<td>Affichage en magasin</td>
<td>Non</td>
</tr>
</tbody></table>


## La commande a été récupérée dans le magasin.

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
<td><strong>Activé</strong></td>
<td>Cet e-mail est envoyé au client lorsqu’il souhaite confirmer qu’il a récupéré sa commande dans le magasin. Définissez cette variable sur "Non" pour désactiver la notification électronique. Si le modèle d'email est désactivé, cela n'empêche pas le client de récupérer une commande.</td>
<td>Affichage en magasin</td>
<td>Non</td>
</tr>
<tr>
<td><strong>La commande a été récupérée pour l’expéditeur d’email</strong></td>
<td>Identité de l’expéditeur utilisée lors de l’envoi de la notification électronique.</td>
<td>Affichage en magasin</td>
<td>Non</td>
</tr>
<tr>
<td><strong>Le modèle de courrier électronique de commande a été récupéré</strong></td>
<td>Le modèle de message électronique utilisé pour notifier les clients enregistrés. Un modèle par défaut est fourni avec l’intégration.</td>
<td>Affichage en magasin</td>
<td>Non</td>
</tr>
<td><strong>Le modèle de courrier électronique de commande a été sélectionné pour l’invité</strong></td>
<td>Le modèle de message électronique utilisé pour avertir les clients invités. Un modèle par défaut est fourni avec l’intégration.</td>
<td>Affichage en magasin</td>
<td>Non</td>
</tr>
<tr>
<td><strong>L’option Envoyer a été sélectionnée pour la copie d’email</strong></td>
<td>Liste d’adresses électroniques délimitées par des virgules pour envoyer une copie de chaque notification.</td>
<td>Affichage en magasin</td>
<td>Non</td>
</tr>
<tr>
<td><strong>Méthode Envoyer une copie d’email sélectionnée</strong></td>
<td>La méthode de copie d’email (copie carbone) à utiliser.</td>
<td>Affichage en magasin</td>
<td>Non</td>
</tr>
</tbody></table>

## Ordre différé

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
<td><strong>Activé</strong></td>
<td>Cet email est envoyé au client pour l’informer d’un retard dans le traitement ou le choix de sa commande dans la boutique. Définissez cette variable sur "Non" pour désactiver la notification électronique. Si le modèle d’email est désactivé, la fonction n’empêche pas le retard d’une commande.</td>
<td>Affichage en magasin</td>
<td>Non</td>
</tr>
<tr>
<td><strong>Expéditeur d’emails retardé de commande
</strong></td>
<td>Identité de l’expéditeur utilisée lors de l’envoi de la notification électronique.</td>
<td>Affichage en magasin</td>
<td>Non</td>
</tr>
<tr>
<td><strong>Modèle de courrier électronique retardé de commande</strong></td>
<td>Le modèle de message électronique utilisé pour notifier les clients enregistrés. Un modèle par défaut est fourni avec l’intégration.</td>
<td>Affichage en magasin</td>
<td>Non</td>
</tr>
<td><strong>Modèle de courrier électronique retardé de commande pour l’invité</strong></td>
<td>Le modèle de message électronique utilisé pour avertir les clients invités. Un modèle par défaut est fourni avec l’intégration.</td>
<td>Affichage en magasin</td>
<td>Non</td>
</tr>
<tr>
<td><strong>Envoyer la copie de l’email retardée de la commande à</strong></td>
<td>Liste d’adresses électroniques délimitées par des virgules pour envoyer une copie de chaque notification.</td>
<td>Affichage en magasin</td>
<td>Non</td>
</tr>
<tr>
<td><strong>Méthode Envoyer la copie retardée de la commande</strong></td>
<td>La méthode de copie d’email (copie carbone) à utiliser.</td>
<td>Affichage en magasin</td>
<td>Non</td>
</tr>
</tbody></table>



## Commande annulée

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
<td><strong>Activé</strong></td>
<td>Cet email est envoyé au client pour l'informer que sa commande a été annulée dans la boutique. Définissez cette variable sur <code>No</code> pour désactiver la notification électronique. Si le modèle d'email est désactivé, sa fonctionnalité n'empêche pas l'annulation d'une commande.</td>
<td>Affichage en magasin</td>
<td>Non</td>
</tr>
<tr>
<td><strong>Expéditeur d’email annulé de commande
</strong></td>
<td>Identité de l’expéditeur utilisée lors de l’envoi de la notification électronique.</td>
<td>Affichage en magasin</td>
<td>Non</td>
</tr>
<tr>
<td><strong>Modèle de courrier électronique annulé par commande</strong></td>
<td>Le modèle de message électronique utilisé pour notifier les clients enregistrés. Un modèle par défaut est fourni avec l’intégration.</td>
<td>Affichage en magasin</td>
<td>Non</td>
</tr>
<td><strong>Commande annulée pour l’invité</strong></td>
<td>Le modèle de message électronique utilisé pour avertir les clients invités. Un modèle par défaut est fourni avec l’intégration.</td>
<td>Affichage en magasin</td>
<td>Non</td>
</tr>
<tr>
<td><strong>Envoyer la copie de l’email de commande annulée à</strong></td>
<td>Liste d’adresses électroniques délimitées par des virgules pour envoyer une copie de chaque notification.</td>
<td>Affichage en magasin</td>
<td>Non</td>
</tr>
<tr>
<td><strong>Méthode Envoyer la copie annulée de la commande</strong></td>
<td>La méthode de copie d’email (copie carbone) à utiliser.</td>
<td>Affichage en magasin</td>
<td>Non</td>
</tr>
</tbody></table>


## Commande partiellement annulée

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
<td><strong>Activé</strong></td>
<td>Cet email est envoyé au client pour l'informer qu'une partie de sa commande a été annulée dans la boutique. Définissez cette variable sur <code>No</code> pour désactiver la notification électronique. Si le modèle d'email est désactivé, une commande n'est pas partiellement annulée.</td>
<td>Affichage en magasin</td>
<td>Non</td>
</tr>
<tr>
<td><strong>Commande d’expéditeur d’email partiellement annulé
</strong></td>
<td>Identité de l’expéditeur utilisée lors de l’envoi de la notification électronique.</td>
<td>Affichage en magasin</td>
<td>Non</td>
</tr>
<tr>
<td><strong>Modèle de courrier électronique partiellement annulé de commande</strong></td>
<td>Le modèle de message électronique utilisé pour notifier les clients enregistrés. Un modèle par défaut est fourni avec l’intégration.</td>
<td>Affichage en magasin</td>
<td>Non</td>
</tr>
<td><strong>Modèle de courrier électronique partiellement annulé de commande pour un autre contact de collecte.</strong></td>
<td>Le modèle de message électronique utilisé pour notifier les contacts supplémentaires nommés dans la commande. Un modèle par défaut est fourni avec l’intégration.</td>
<td>Affichage en magasin</td>
<td>Non</td>
</tr>
<tr>
<td><strong>Commande partiellement annulée pour l’invité</strong></td>
<td>Le modèle de message électronique utilisé pour avertir les clients invités. Un modèle par défaut est fourni avec l’intégration.</td>
<td>Affichage en magasin</td>
<td>Non</td>
</tr>
<tr>
<td><strong>Envoyer la copie d’email partiellement annulée à la commande</strong></td>
<td>Liste d’adresses électroniques délimitées par des virgules pour envoyer une copie de chaque notification.</td>
<td>Affichage en magasin</td>
<td>Non</td>
</tr>
<tr>
<td><strong>Méthode Envoyer la commande partiellement annulée</strong></td>
<td>La méthode de copie d’email (copie carbone) à utiliser.</td>
<td>Affichage en magasin</td>
<td>Non</td>
</tr>
</tbody></table>

## Bateau

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
<td><strong>Commande possède un expéditeur de produits Expédier</strong></td>
<td>Courrier électronique envoyé au personnel marchand spécifié sous la forme d’un rapport agrégé de toutes les commandes ouvertes qui ne peuvent pas être sélectionnées dans un magasin marchand tant que leur inventaire n’est pas disponible. </br></br> Les vendeurs peuvent utiliser ce rapport pour lancer et gérer les transferts d’inventaire ou le réapprovisionnement de magasin à magasin. </br></br>Cette notification s'applique uniquement lorsque les fonctionnalités [!DNL Ship-to-Store] sont activées.
</br></br>Ce libellé n’affecte pas l’opérateur de livraison sélectionné ni les étiquettes de méthode de livraison disponibles.</td>
<td>Affichage en magasin</td>
<td>Non</td>
</tr>
<tr>
<td><strong>Expéditeur Pour Stocker Les Destinataires De Courriers Électroniques</strong></td>
<td>Liste d’adresses électroniques délimitées par des virgules pour envoyer une copie de chaque notification.</td>
<td>Affichage en magasin</td>
<td>Non</td>
</tr>
<tr>
<td><strong>Modèle de courrier électronique</strong></td>
<td>Le modèle de message électronique utilisé pour notifier les destinataires. Un modèle par défaut est fourni avec l’intégration.</td>
<td>Affichage en magasin</td>
<td>Non</td>
</tr>
</tbody></table>

>[!NOTE]
>
>Si vous autorisez les commandes en arrière-plan, vous devez indiquer une adresse électronique d’administrateur pour recevoir des notifications concernant ces commandes. Ajoutez l’adresse aux paramètres de configuration suivants : **[!UICONTROL Send Order Delayed Email Copy To]** dans le modèle [Délai de commande](#order-delayed) et [!UICONTROL Ship To Store Email Recipients] dans le modèle [Ship to Store](#ship-to-store).



