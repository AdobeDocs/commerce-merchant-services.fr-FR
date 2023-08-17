---
title: Installation
description: "Installez le [!DNL Store Fulfillment solution] pour un storefront Adobe Commerce utilisant Composer pour PHP."
role: Admin, Developer
level: Intermediate
feature: Shipping/Delivery, Install
exl-id: 6613268a-7d22-4c54-af89-834921b7f262
source-git-commit: 36b57648e156ead801764f3ee4e5e6a0f3245fe6
workflow-type: tm+mt
source-wordcount: '660'
ht-degree: 0%

---


# Installation

Procédez à l’installation initiale de la fonction [!DNL Store Fulfillment for Adobe Commerce by Walmart Commerce Technologies] dans un environnement hors production, avec un gestionnaire de file d’attente en cours d’exécution et une mise en cache configurés pour permettre la gestion des exceptions. Assurez-vous que votre environnement de développement comprend des outils de développement pour garantir les bonnes pratiques d’exploitation et de maintenance de votre instance Adobe Commerce.

## Conditions préalables

Consultez la section [conditions requises](solution-requirements.md) pour la solution Store Fulfillment et collectez les informations requises avant d’installer le [!DNL Store Fulfillment] pour Adobe Commerce.

Si vous avez installé une version bêta ou préliminaire de l’extension Store Fulfillment for Adobe Commerce, utilisez la commande suivante pour la supprimer avant d’installer la version actuelle.

```terminal
rm -rf composer.lock vendor/walmart &&
composer require walmart/magento-bopis-metapackage:1.0.0
```

## Configuration requise

- **Accès à l’exécution du magasin par l’archive logicielle Walmart Commerce Technologies (fichier .zip)**: pendant le processus d’intégration et d’activation, travaillez avec votre gestionnaire de compte pour accéder au fichier d’installation de l’extension Store Fulfillment.

- **Informations du compte Adobe Commerce**- Installation de la variable [!DNL Store Fulfillment] la solution requiert une [[!DNL Commerce] account](https://docs.magento.com/user-guide/magento/magento-account.html){target="_blank"}. Vous avez besoin d’un identifiant de compte et d’informations d’identification avec un accès Propriétaire ou Administrateur à la variable [!DNL Adobe Commerce] projet.

- Pour [!DNL Adobe Commerce] sur les projets d’infrastructure cloud, les programmes d’installation doivent disposer d’un accès administrateur au projet Cloud. Voir [Gestion de l’accès des utilisateurs](https://devdocs.magento.com/cloud/project/user-admin.html).

- **Expérience à l’aide du compositeur et de la variable[!DNL Commerce CLI]**—Voir [Installation de la ligne de commande générale](https://devdocs.magento.com/extensions/install/){target="_blank"} pour plus d’informations sur l’utilisation de ces outils pour installer et gérer des extensions sur le [!DNL Adobe Commerce] plateforme.

- **Expérience d’installation d’extensions tierces sur Adobe Commerce**—À titre de référence, consultez la documentation d’Adobe Commerce.

   - [Installer une extension pour une instance Adobe Commerce sur une instance d’infrastructure cloud](https://devdocs.magento.com/cloud/howtos/install-components.html#install-an-extension).

   - [Installation d’une extension pour une instance Adobe Commerce sur site](https://devdocs.magento.com/extensions/install/).

### Étape 1 : téléchargement du lot d’extension

Suivez les instructions fournies par les représentants de votre compte pour télécharger le fichier d’archive contenant les packages du compositeur pour l’installation de l’extension Store Fulfillment Services.

### Étape 2 : Extraire les artefacts d’extension de votre application

Extrayez le fichier d’archive contenant le lot d’intégration pour installer l’extension Store Fulfillment Services.

1. Créez un répertoire cible pour les fichiers extraits.

   - Dans la ligne de commande, accédez au répertoire racine du document du serveur web.

   - Créez un `artifacts` répertoire .

1. Extrayez le fichier d’archive dans le nouveau répertoire.

1. Vérifiez que les fichiers ont bien été extraits en consultant la liste des fichiers.

   ```
   ../var/www/html/artifacts]$ ls -a
   .
   ..
   bopis-sdk.zip
   module-magento-bopis-alternate-pickup-contact-admin-ui.zip
   module-magento-bopis-alternate-pickup-contact-api.zip
   ```

### Étape 3 : Configuration de votre application à l’aide du compositeur

Utilisez le compositeur pour configurer le répertoire source de l’installation et installer l’extension Store Fulfillment Services.

1. Configurez le référentiel source pour l’installation du compositeur.

   ```bash
   composer config repositories.artifacts artifact artifacts/
   ```

1. Ajoutez l’extension Store Fulfillment Services à `composer.json`.

   ```bash
   composer require walmart/magento-bopis-metapackage:1.0.0
   ```

>[!NOTE]
>
>Pour de meilleures performances sur les instances Adobe Commerce sur site, vous pouvez [mise à jour de la configuration du chargement automatique](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/deployment-flow.html#update-the-autoloader): `composer dump-autoload --optimize`

### Etape 4 : mettre à niveau le schéma et les données de la base de données

Effectuez l’installation à l’aide de la méthode `bin/magento setup:upgrade` pour mettre à jour le schéma et les données de la base de données avec les modifications afin de prendre en charge la solution d’exécution de magasin.

>[!NOTE]
>
>Pour Adobe Commerce sur les projets d’infrastructure cloud, il n’est pas nécessaire d’enregistrer l’extension. Au lieu de cela, validez les modifications de code de l’étape précédente et poussez-les vers votre branche d’environnement. Les commandes permettant de mettre à jour le schéma et les données de la base de données sont exécutées automatiquement lors du processus de création et de déploiement du cloud.

### Etape 5 : terminer l&#39;installation

1. Enregistrez l’extension avec Adobe Commerce à l’aide de la fonction `setup:upgrade` Commande de l’interface de ligne de commande du Magento.

   ```terminal
   bin/magento setup:upgrade
   ```

1. Si vous y êtes invité, recompilez votre [!DNL Commerce] projet.

   ```bash
   bin/magento setup:di:compile
   ```

1. Nettoyez le cache.

   ```bash
   bin/magento cache:clean
   ```

1. Désactivez le mode de maintenance.

   ```bash
   bin/magento maintenance:disable
   ```

### Etape 6 : vérification de l&#39;installation

Sur le serveur Adobe Commerce, vérifiez que les modules de l’extension Store Fulfillment Services sont installés et activés.

1. Connectez-vous au serveur .

   Pour les installations sur Adobe Commerce sur l’infrastructure cloud, [utiliser SSH pour se connecter à l’environnement distant ;](https://devdocs.magento.com/cloud/env/environments-ssh.html#ssh).

1. Vérifiez que les modules Store Fulfillment Services sont activés.

   ```bash
   bin/magento module:status  --enabled | grep Walmart
   ```

   La sortie doit inclure les modules suivants :

   ```
   Walmart_BopisBase
   Walmart_BopisAlternatePickupContact
   Walmart_BopisAlternatePickupContactFrontend
   Walmart_BopisApiConnector
   Walmart_BopisAlternatePickupContactAdminUi
   Walmart_BopisCheckoutPickInStoreApi
   Walmart_BopisInventorySourceAdminUi
   Walmart_BopisCheckoutPickInStore
   Walmart_BopisInventoryCatalogApi
   Walmart_BopisPreferredLocationApi
   Walmart_BopisHomeDeliveryApi
   Walmart_BopisHomeDelivery
   Walmart_BopisPreferredLocation
   Walmart_BopisInventoryCatalog
   Walmart_BopisPreferredLocationFrontend
   Walmart_BopisCheckoutPickInStoreAdminUi
   Walmart_BopisInventorySourceApi
   Walmart_BopisInventorySourceFaasSync
   Walmart_BopisInventorySourceReservation
   Walmart_BopisLocationCheckInApi
   Walmart_BopisLogging
   Walmart_BopisStoreAssociateApi
   Walmart_BopisLocationCheckInFrontend
   Walmart_BopisStoreAssociate
   Walmart_BopisOperationQueue
   Walmart_BopisOperationQueueAdminUi
   Walmart_BopisOperationQueueApi
   Walmart_BopisOrderFaasSync
   Walmart_BopisOrderUpdateApi
   Walmart_BopisLocationCheckIn
   Walmart_BopisInventoryCatalogAdminUi
   Walmart_BopisPreferredLocationAdminUi
   Walmart_BopisDeliverySelection
   Walmart_BopisCheckoutPickInStoreFrontend
   Walmart_BopisLocationCheckInAdminUi
   Walmart_BopisStoreAssociateAdminUi
   Walmart_BopisOrderUpdate
   Walmart_BopisStoreAssociateTfa
   Walmart_BopisStoreAssociateTfaApi
   ```

### Étapes supplémentaires

Si nécessaire, utilisez la méthode [setup:static-content:deploy](https://experienceleague.adobe.com/docs/commerce-operations/reference/commerce-on-premises.html){target="_blank"} Commande d’interface de ligne de commande pour déployer des fichiers d’affichage statique dans votre environnement de production.

```terminal
php bin/magento setup:static-content:deploy -f
```

La variable `-f` est requise si vous utilisez un thème vide.

>[!NOTE]
>
>Pour plus d’informations, voir [Bonnes pratiques de déploiement de contenu statique dans Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/development/static-content-deployment.html) Article du Centre d’aide Adobe Commerce.

