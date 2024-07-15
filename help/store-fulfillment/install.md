---
title: Installation
description: "Installez le  [!DNL Store Fulfillment solution] pour un storefront Adobe Commerce à l’aide du compositeur pour PHP."
role: Admin, Developer
level: Intermediate
feature: Shipping/Delivery, Install
exl-id: 6613268a-7d22-4c54-af89-834921b7f262
source-git-commit: 78b09113e72382053b01d6016276bae3aa545fa3
workflow-type: tm+mt
source-wordcount: '666'
ht-degree: 0%

---


# Installation

Terminez l’installation initiale de l’extension [!DNL Store Fulfillment for Adobe Commerce by Walmart Commerce Technologies] dans un environnement hors production avec le gestionnaire de file d’attente en cours d’exécution et la mise en cache configurés pour permettre la gestion des exceptions. Assurez-vous que votre environnement de développement comprend des outils de développement pour garantir les bonnes pratiques d’exploitation et de maintenance de votre instance Adobe Commerce.

>[!TIP]
>
>Mettez à niveau l’extension d’exécution de magasin pour Adobe Commerce sur site en suivant les [instructions de mise à niveau](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/modules/upgrade.html) du _Guide de mise à niveau d’Adobe Commerce_. Pour Adobe Commerce sur l’infrastructure cloud, reportez-vous à la section [Mise à niveau d’une extension](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/extensions.html#upgrade-an-extension) du *Guide de l’infrastructure de Commerce on Cloud*.

## Conditions préalables

Passez en revue les [exigences](solution-requirements.md) de la solution d’exécution de magasin et rassemblez les informations requises avant d’installer ou de mettre à niveau l’extension [!DNL Store Fulfillment] pour Adobe Commerce.

Si vous avez installé une version bêta ou préliminaire de l’extension Store Fulfillment for Adobe Commerce, utilisez la commande suivante pour la supprimer avant d’installer la version actuelle.

```terminal
rm -rf composer.lock vendor/walmart &&
composer require walmart/magento-bopis-metapackage:1.0.0
```

## Configuration requise

- **Accès à l’exécution de la boutique par l’archive logicielle Walmart Commerce Technologies (fichier .zip)** : pendant le processus d’intégration et d’activation, demandez à votre gestionnaire de compte d’accéder au fichier d’installation de l’extension Store Fulfillment.

- **Informations sur le compte Adobe Commerce** - L’installation de la solution [!DNL Store Fulfillment] nécessite un [[!DNL Commerce] compte](https://docs.magento.com/user-guide/magento/magento-account.html){target="_blank"}. Vous avez besoin d’un ID de compte et d’informations d’identification avec un accès propriétaire ou administrateur au projet [!DNL Adobe Commerce].

- Pour [!DNL Adobe Commerce] sur les projets d’infrastructure cloud, les programmes d’installation doivent disposer d’un accès administrateur au projet Cloud. Voir [Gérer l’accès des utilisateurs](https://devdocs.magento.com/cloud/project/user-admin.html).

- **Expérience avec le compositeur et[!DNL Commerce CLI]**—Voir [Installation générale de l’interface en ligne de commande](https://devdocs.magento.com/extensions/install/){target="_blank"} pour plus d’informations sur l’utilisation de ces outils pour installer et gérer les extensions sur la plateforme [!DNL Adobe Commerce].

- **Expérience d’installation d’extensions tierces sur Adobe Commerce** : à titre de référence, consultez la documentation d’Adobe Commerce.

   - [Installez une extension pour une instance Adobe Commerce sur l’instance d’infrastructure cloud](https://devdocs.magento.com/cloud/howtos/install-components.html#install-an-extension).

   - [Installez une extension pour une instance Adobe Commerce sur site](https://devdocs.magento.com/extensions/install/).

### Étape 1 : téléchargement du lot d’extension

Suivez les instructions fournies par les représentants de votre compte pour télécharger le fichier d’archive contenant les packages du compositeur pour l’installation de l’extension Store Fulfillment Services.

### Étape 2 : Extraire les artefacts d’extension de votre application

Extrayez le fichier d’archive contenant le lot d’intégration pour installer l’extension Store Fulfillment Services.

1. Créez un répertoire cible pour les fichiers extraits.

   - Dans la ligne de commande, accédez au répertoire racine du document du serveur web.

   - Créez un répertoire `artifacts`.

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
>Pour de meilleures performances sur les instances sur site Adobe Commerce, vous pouvez [mettre à jour la configuration de chargement automatique](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/deployment-flow.html#update-the-autoloader) : `composer dump-autoload --optimize`

### Etape 4 : mettre à niveau le schéma et les données de la base de données

Terminez l’installation en utilisant `bin/magento setup:upgrade` pour mettre à jour le schéma et les données de la base de données avec les modifications pour prendre en charge la solution Store Fulfillment.

>[!NOTE]
>
>Pour Adobe Commerce sur les projets d’infrastructure cloud, il n’est pas nécessaire d’enregistrer l’extension. Au lieu de cela, validez les modifications de code de l’étape précédente et poussez-les vers votre branche d’environnement. Les commandes permettant de mettre à jour le schéma et les données de la base de données sont exécutées automatiquement lors du processus de création et de déploiement du cloud.

### Etape 5 : terminer l&#39;installation

1. Enregistrez l’extension avec Adobe Commerce à l’aide de la commande d’interface de ligne de commande du Magento `setup:upgrade`.

   ```terminal
   bin/magento setup:upgrade
   ```

1. Si vous y êtes invité, recompilez votre projet [!DNL Commerce].

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

   Pour les installations sur Adobe Commerce sur l’infrastructure cloud, [ utilisez SSH pour vous connecter à l’environnement distant ](https://devdocs.magento.com/cloud/env/environments-ssh.html#ssh).

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

Si nécessaire, utilisez la commande d’interface de ligne de commande [setup:static-content:deploy](https://experienceleague.adobe.com/docs/commerce-operations/reference/commerce-on-premises.html){target="_blank"} pour déployer les fichiers d’affichage statique dans votre environnement de production.

```terminal
php bin/magento setup:static-content:deploy -f
```

L’option `-f` est requise si vous utilisez un thème vide.

>[!NOTE]
>
>Pour plus d’informations, reportez-vous à l’article [Bonnes pratiques de déploiement de contenu statique dans Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/development/static-content-deployment.html) du Centre d’aide Adobe Commerce.


