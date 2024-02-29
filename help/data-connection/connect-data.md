---
title: Connexion des données commerciales à Adobe Experience Platform
description: Découvrez comment connecter vos données Commerce à Adobe Experience Platform.
exl-id: 87898283-545c-4324-b1ab-eec5e26a303a
feature: Personalization, Integration, Configuration
source-git-commit: 99d1097b98ea18c8a317613b2366a97db131432f
workflow-type: tm+mt
source-wordcount: '2480'
ht-degree: 0%

---

# Connexion des données Commerce à Adobe Experience Platform

Lorsque vous installez le [!DNL Data Connection] , deux nouvelles pages de configuration s’affichent dans **Système** sous **Services** dans Commerce _Administration_.

- Connecteur Commerce Services
- [!DNL Data Connection]

Pour connecter votre instance Adobe Commerce à Adobe Experience Platform, vous devez configurer les deux connecteurs, en commençant par le connecteur Commerce Services , puis en finissant par le [!DNL Data Connection] extension .

## Configuration du connecteur Commerce Services

Si vous avez précédemment installé un service Adobe Commerce, vous avez probablement déjà configuré le connecteur Commerce Services. Dans le cas contraire, vous devez effectuer les tâches suivantes sur la page [Connecteur Commerce Services](../landing/saas.md) page :

1. Connectez-vous à votre compte Commerce pour [récupération de vos clés d’API de production et d’environnement de test](../landing/saas.md#credentials).
1. Sélectionnez une [Espace de données SaaS](../landing/saas.md#saas-configuration).
1. Connectez-vous à votre compte Adobe pour [récupération de votre ID d’organisation](../landing/saas.md#ims-organization-optional).

Une fois que vous avez configuré le connecteur Commerce Services, vous pouvez configurer la variable [!DNL Data Connection] extension .

## Configurez la variable [!DNL Data Connection] extension

Dans cette section, vous découvrirez comment configurer la variable [!DNL Data Connection] extension .

### Ajout de détails sur le compte de service et les informations d’identification

Si vous prévoyez de collecter et d’envoyer [données d’ordre historique](#send-historical-order-data) ou [données de profil client](#send-customer-profile-data), vous devez ajouter les détails du compte de service et des informations d’identification. En outre, si vous configurez la variable [Audience Activation](https://experienceleague.adobe.com/docs/commerce-admin/customers/audience-activation.html) , vous devez effectuer ces étapes.

Si vous collectez et envoyez uniquement des données de storefront ou back-office, vous pouvez passer à la variable [general](#general) .

#### Étape 1 : création d’un projet dans la console Adobe Developer

Créez un projet dans la console Adobe Developer qui authentifie Commerce afin qu’il puisse effectuer des appels API Experience Platform.

Pour créer le projet, suivez les étapes décrites dans la section [Authentification et accès aux API Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/landing/platform-apis/api-authentication.html) tutoriel .

Lorsque vous passez en revue le tutoriel, assurez-vous que votre projet comporte les éléments suivants :

- L’accès aux [profils de produit](https://experienceleague.adobe.com/docs/experience-platform/landing/platform-apis/api-authentication.html#select-product-profiles): **Accès complet par défaut à la production** et **AEP Accès par défaut**.
- Le bon [les rôles et autorisations sont configurés.](https://experienceleague.adobe.com/docs/experience-platform/landing/platform-apis/api-authentication.html#assign-api-to-a-role).
- Si vous avez décidé d’utiliser des jetons Web JSON (JWT) comme méthode d’authentification serveur à serveur, vous devez également télécharger une clé privée.

Le résultat de cette étape crée un fichier de configuration que vous utilisez à l’étape suivante.

#### Étape 2 : téléchargement du fichier de configuration

Téléchargez la [fichier de configuration de l&#39;espace de travail](https://developer.adobe.com/commerce/extensibility/events/project-setup/#download-the-workspace-configuration-file). Copiez et collez le contenu de ce fichier dans le **Informations d’identification/compte de service** de l’administrateur Commerce.

1. Dans l’administrateur Commerce, accédez à **Magasins** > Paramètres > **Configuration** > **Services** > **[!DNL Data Connection]**.

1. Sélectionnez la méthode d’autorisation serveur à serveur que vous avez mise en oeuvre à partir du **Type d’autorisation Adobe Developer** . Adobe recommande d’utiliser OAuth. JWT a été abandonné. [En savoir plus](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/).

1. (JWT uniquement) Copiez et collez le contenu de votre `private.key` dans le fichier **Secret du client** champ . Utilisez la commande suivante pour copier le contenu.

   ```bash
   cat config/private.key | pbcopy
   ```

   Voir [Authentification du compte de service (JWT)](https://developer.adobe.com/developer-console/docs/guides/authentication/JWT/) pour plus d’informations sur la variable `private.key` fichier .

1. Copiez le contenu de la `<workspace-name>.json` dans le fichier **Informations d’identification/compte de service** champ .

   ![[!DNL Data Connection] Configuration de l’administrateur](./assets/epc-admin-config.png){width="700" zoomable="yes"}

1. Cliquez sur **Enregistrer la configuration**.

### Général

1. Dans Admin, accédez à **Système** > Services > **[!DNL Data Connection]**.

1. Sur le **Paramètres** sous **Général**, vérifiez l’identifiant associé à votre compte Adobe Experience Platform, tel que configuré dans la variable [Connecteur Commerce Services](../landing/saas.md#organizationid). L’ID d’organisation est global. Un seul ID d’organisation peut être associé par instance Adobe Commerce.

1. Dans le **Portée** , définissez le contexte sur **Site Web**.

1. (Facultatif) Si vous avez déjà une [SDK Web AEP (allié)](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html) déployé sur votre site, cochez la case et ajoutez le nom de votre SDK Web AEP. Sinon, laissez ces champs vides et le [!DNL Data Connection] l’extension en déploie un pour vous.

   >[!NOTE]
   >
   >Si vous spécifiez votre propre SDK Web AEP, la variable [!DNL Data Connection] L’extension utilise l’identifiant de la banque de données associé à ce SDK et non l’identifiant de la banque de données spécifié sur cette page (le cas échéant).

### Collecte de données

Dans cette section, vous indiquez le type de données à collecter et à envoyer à l’Experience Platform Edge. Il existe trois types de données :

- **Comportement** (données côté client) est des données capturées sur le storefront. Cela inclut les interactions avec les acheteurs, telles que `View Page`, `View Product`, `Add to Cart`, et [liste des demandes](events.md#b2b-events) informations (pour les commerçants B2B).

- **Retour au bureau** (données côté serveur) est des données capturées dans les serveurs de commerce. Cela inclut des informations sur l’état d’une commande, par exemple si une commande a été passée, annulée, remboursée, expédiée ou terminée. Elle comprend également [données d’ordre historique](#send-historical-order-data).

- **Profil** est des données liées aux informations de profil de votre acheteur. Formation [more](#send-customer-profile-data).

Pour vous assurer que votre instance Adobe Commerce peut commencer la collecte de données, consultez la section [conditions préalables](overview.md#prerequisites).

Consultez la rubrique Événements pour en savoir plus sur [storefront](events.md#storefront-events), [back office](events-backoffice.md), et [profile](events-backoffice.md#customer-profile-events-server-side) événements .

>[!NOTE]
>
>Tous les champs du champ **Collecte de données** s’appliquent à la section **Site Web** ou supérieure.

1. Sélectionner **Événements Storefront** si vous souhaitez envoyer des données comportementales storefront.

1. Sélectionner **Événements de back-office** si vous souhaitez envoyer des informations sur l’état de la commande, par exemple si une commande a été passée, annulée, remboursée ou expédiée.

   >[!NOTE]
   >
   >Si vous sélectionnez **Événements de back-office**, toutes les données du back-office sont envoyées au serveur Edge de l’Experience Platform. Si un acheteur choisit de se désabonner de la collecte de données, vous devez définir explicitement la préférence de confidentialité de l’acheteur dans l’Experience Platform. Cela diffère des événements storefront où le collecteur gère déjà le consentement en fonction des préférences de l’acheteur. Formation [more](https://experienceleague.adobe.com/docs/experience-platform/landing/governance-privacy-security/consent/adobe/dataset.html) à propos de la définition de la préférence de confidentialité d’un acheteur dans l’Experience Platform.

1. (Ignorez cette étape si vous utilisez votre propre SDK Web AEP.) [Créer](https://experienceleague.adobe.com/docs/experience-platform/datastreams/configure.html#create) un flux de données dans Adobe Experience Platform ou sélectionnez un flux de données existant à utiliser pour la collecte. Saisissez cet identifiant de flux de données dans la variable **Identifiant du flux de données** champ .

1. Saisissez le **Identifiant du jeu de données** que vous souhaitez contenir vos données Commerce. Pour trouver l’identifiant du jeu de données :

   1. Ouvrez l’interface utilisateur de l’Experience Platform et sélectionnez **Jeux de données** dans le volet de navigation de gauche pour ouvrir la **Jeux de données** tableau de bord. Le tableau de bord répertorie tous les jeux de données disponibles pour votre organisation. Des détails s’affichent pour chaque jeu de données répertorié, notamment son nom, le schéma auquel le jeu de données adhère et l’état de l’exécution d’ingestion la plus récente.
   1. Ouvrez le jeu de données associé à votre flux de données.
   1. Dans le volet de droite, affichez les détails du jeu de données. Copiez l’identifiant du jeu de données.

1. Pour garantir les mises à jour des données d’événement du back-office selon un planning [cron](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) , vous devez modifier la fonction `Sales Orders Feed` index à `Update by Schedule`.

   1. Sur le _Administration_ barre latérale, accédez à **[!UICONTROL System]** > _[!UICONTROL Tools]_>**[!UICONTROL Index Management]**.

   1. Cochez la case correspondant au `Sales Orders Feed` indexeur.

   1. Définir **[!UICONTROL Actions]** to `Update by Schedule`.

   1. Si vous activez les données du back-office pour la première fois, exécutez les commandes suivantes pour réindexer et déclencher une nouvelle synchronisation. Les resynchronisations suivantes se produisent automatiquement tant que la variable [cron](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) est configurée correctement.

      ```bash
      bin/magento index:reindex sales_order_data_exporter_v2
      ```

      ```bash
      bin/magento saas:resync --feed orders
      ```

#### Descriptions des champs

| Champ | Description |
|--- |--- |
| Portée | Site web spécifique sur lequel vous souhaitez appliquer les paramètres de configuration. |
| ID d’organisation (global) | Identifiant appartenant à l’organisation qui a acheté le produit Adobe DX. Cet identifiant associe votre instance Adobe Commerce à Adobe Experience Platform. |
| Le SDK Web AEP est-il déjà déployé sur votre site ? | Cochez cette case si vous avez déployé votre propre SDK Web AEP sur votre site. |
| Nom du SDK Web AEP (global) | Si un SDK Web Experience Platform est déjà déployé sur votre site, indiquez le nom de ce SDK dans ce champ. Cela permet au collecteur d’événements Storefront et au SDK d’événements Storefront d’utiliser votre SDK Web Experience Platform plutôt que la version déployée par [!DNL Data Connection] extension . Si aucun SDK Web Experience Platform n’est déployé sur votre site, laissez ce champ vide et la variable [!DNL Data Connection] l’extension en déploie un pour vous. |
| Événements Storefront | Est coché par défaut tant que l’ID d’organisation et l’ID de flux de données sont valides. Les événements Storefront collectent des données comportementales anonymes de vos clients lorsqu’ils naviguent sur votre site. |
| Événements de back-office | Si cette case est cochée, la payload d’événement contient des informations d’état de commande anonymes, telles qu’une commande passée, annulée, remboursée ou expédiée. |
| Identifiant de la banque de données (site web) | Identifiant qui permet aux données de passer de Adobe Experience Platform à d’autres produits DX d’Adobe. Cet identifiant doit être associé à un site web spécifique dans votre instance Adobe Commerce spécifique. Si vous spécifiez votre propre SDK Web Experience Platform, ne spécifiez pas d’identifiant de flux de données dans ce champ. La variable [!DNL Data Connection] L’extension utilise l’identifiant de flux de données associé à ce SDK et ignore tout identifiant de flux de données spécifié dans ce champ (le cas échéant). |
| Identifiant du jeu de données (site web) | Identifiant du jeu de données qui contient vos données Commerce. Ce champ est obligatoire, sauf si vous avez désélectionné l’option **Événements Storefront** ou **Événements de back-office** des cases à cocher. En outre, si vous utilisez votre propre SDK Web Experience Platform et n’avez donc pas spécifié d’identifiant de flux de données, vous devez toujours ajouter l’identifiant de jeu de données associé à votre flux de données. Sinon, vous ne pouvez pas enregistrer ce formulaire. |

Une fois l’intégration effectuée, les données du storefront commencent à s’écouler vers le bord Experience Platform. Les données du back-office prennent environ cinq minutes pour s’afficher à la périphérie. Les mises à jour suivantes sont visibles à la périphérie en fonction de la planification cron.

### Envoi des données de profil client

Vous pouvez envoyer à l’Experience Platform deux types de données de profil : les enregistrements de profil et les événements de profil de série temporelle.

Un enregistrement de profil contient des données enregistrées lorsqu’un acheteur crée un profil dans votre instance Commerce, tel que le nom de l’acheteur. Lorsque votre schéma et votre jeu de données sont [correctement configuré](profile-data.md), un enregistrement de profil est envoyé à l’Experience Platform et transféré au service de segmentation et de gestion des profils d’Adobe : [Real-Time CDP](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/intro/rtcdp-intro/overview.html?lang=fr).

Les événements de profil de série temporelle contiennent des données sur les informations de profil de votre acheteur, telles que la création, la modification ou la suppression d’un compte sur votre site. Lorsque des données d’événement de profil sont envoyées à l’Experience Platform, elles se trouvent dans un jeu de données où elles peuvent être utilisées par d’autres produits DX.

1. Assurez-vous que [provided](#add-service-account-and-credential-details) informations de compte de service et d’identification.

1. Assurez-vous que le schéma et le jeu de données sont spécifiés pour [ingestion des données d’enregistrement de profil](profile-data.md) et [ingestion des données d’événement de profil de série temporelle](update-xdm.md#time-series-profile-event-data).

1. Placez une coche dans la variable **Profils client** si vous souhaitez envoyer des données de profil à l’Experience Platform.

1. Saisissez le **Identifiant du jeu de données de profil**.

   Les données d’enregistrement de profil doivent utiliser un jeu de données différent de celui que vous utilisez actuellement pour les données d’événement comportemental et back-office.

1. Si vous ne souhaitez pas diffuser des événements de profil par le biais du même identifiant de flux de données que celui utilisé pour les données comportementales et de back-office, supprimez la coche de la variable **Diffusion en continu des profils client à l’aide du même identifiant de flux de données** et saisissez l’identifiant du flux de données que vous souhaitez utiliser à la place.

Il peut s’écouler environ 10 minutes avant qu’un enregistrement de profil soit disponible dans Real-Time CDP. Les événements de profil commencent immédiatement à être diffusés en continu.

#### Descriptions des champs

| Champ | Description |
|--- |--- |
| Profils client | Cochez cette case si vous souhaitez collecter et envoyer des enregistrements de profil client. |
| Identifiant du jeu de données de profil | Un enregistrement de profil doit utiliser un jeu de données différent de celui utilisé pour les événements de comportement et de back-office. |
| Diffusion en continu des profils client à l’aide du même identifiant de flux de données | Déterminez si vous souhaitez utiliser la même banque de données actuellement utilisée pour vos événements de comportement et back-office ou non. |
| Flux de données pour les profils client | Spécifiez le flux de données spécifique à l’enregistrement du profil client. |

### Envoi de données de commande historiques

Adobe Commerce collecte jusqu’à cinq ans de [données et état de l’ordre historique](events-backoffice.md#back-office-events). Vous pouvez utiliser la variable [!DNL Data Connection] pour envoyer ces données historiques à l’Experience Platform afin d’enrichir vos profils client et de personnaliser les expériences client en fonction de ces commandes passées. Les données sont stockées dans un jeu de données dans Experience Platform.

Bien que Commerce collecte déjà les données de commande historiques, vous devez effectuer plusieurs étapes pour envoyer ces données à Experience Platform.

Regardez cette vidéo pour en savoir plus sur les commandes historiques, puis effectuez les étapes suivantes pour mettre en oeuvre la collecte des commandes historiques.

>[!VIDEO](https://video.tv.adobe.com/v/3424672)

#### Configuration du service de synchronisation des commandes

Le service de synchronisation des commandes utilise la variable [Structure de la file d’attente des messages](https://developer.adobe.com/commerce/php/development/components/message-queues/) et RabbitMQ. Une fois ces étapes terminées, les données d’état de la commande peuvent être synchronisées avec SaaS, ce qui est nécessaire avant d’être envoyées à l’Experience Platform.

1. Assurez-vous que [provided](#add-service-account-and-credential-details) informations de compte de service et d’identification.

1. [Activer](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/rabbitmq.html) RabbitMQ.

   >[!NOTE]
   >
   >RabbitMQ est déjà configuré pour Commerce versions 2.4.7 et ultérieures, mais vous devez activer les consommateurs.

1. Activation des consommateurs de la file de messages par tâche cron dans `.magento.env.yaml` using `CRON_CONSUMERS_RUNNER` Variable d’environnement.

   ```yaml
      stage:
        deploy:
          CRON_CONSUMERS_RUNNER:
            cron_run: true
   ```

   >[!NOTE]
   >
   >Voir [documentation sur les variables de déploiement](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#cron_consumers_runner) pour en savoir plus sur toutes les options de configuration disponibles.

Lorsque le service de synchronisation des commandes est activé, vous pouvez ensuite spécifier la période de commande historique dans la variable **[!UICONTROL [!DNL Data Connection]]** page.

#### Définition de la période d’historique des commandes

Indiquez la période des commandes historiques à envoyer à l’Experience Platform.

1. Dans Admin, accédez à **Système** > Services > **[!DNL Data Connection]**.

1. Sélectionnez la variable **Historique des commandes** .

1. Sous **Synchronisation de l’historique des commandes**, la variable **Copier l’identifiant du jeu de données depuis les paramètres** est déjà activée. Cela vous garantit d’utiliser le même jeu de données que celui spécifié dans la variable **Paramètres** .

1. Dans le **De** et **À** , spécifiez la période des données de l’ordre historique à envoyer. Vous ne pouvez pas sélectionner de période supérieure à cinq ans.

1. Sélectionner **[!UICONTROL Start Sync]** pour déclencher la synchronisation. Les données d’ordre historique sont des données par lots, contrairement aux données de vitrine et de back-office qui diffusent des données en continu. Les données mises en cache prennent environ 45 minutes pour arriver en Experience Platform.

##### Descriptions des champs

| Champ | Description |
|--- |--- |
| Copier l’identifiant du jeu de données depuis les paramètres | Copie l’identifiant du jeu de données que vous avez saisi dans la variable **Paramètres** . |
| Identifiant du jeu de données (site web) | Identifiant du jeu de données qui contient vos données Commerce. Ce champ est obligatoire, sauf si vous avez désélectionné l’option **Événements Storefront** ou **Événements de back-office** des cases à cocher. En outre, si vous utilisez votre propre SDK Web Experience Platform et n’avez donc pas spécifié d’identifiant de flux de données, vous devez toujours ajouter l’identifiant de jeu de données associé à votre flux de données. Sinon, vous ne pouvez pas enregistrer ce formulaire. |
| De | Date à partir de laquelle vous souhaitez commencer à collecter les données de l’historique des commandes. |
| À | Date à partir de laquelle vous souhaitez terminer la collecte des données d’historique des commandes. |
| Démarrer la synchronisation | Démarre le processus de synchronisation des données de l’historique des commandes avec le serveur Experience Platform Edge. Ce bouton est désactivé si la variable **[!UICONTROL Dataset ID]** est vide ou l’identifiant du jeu de données n’est pas valide. |

## Confirmation que les données d’événement sont collectées

Pour confirmer que les données sont collectées à partir de votre boutique Commerce, utilisez la variable [Débogueur Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/debugger/home.html) pour examiner votre site Commerce. Une fois que vous avez confirmé que les données sont en cours de collecte, vous pouvez vérifier que les données d’événement storefront et back-office s’affichent en périphérie en exécutant une requête qui renvoie les données de la variable [jeu de données que vous avez créé](overview.md#prerequisites).

1. Sélectionner **Requêtes** dans le volet de navigation de gauche de Experience Platform, cliquez sur [!UICONTROL Create Query].

   ![Éditeur de requêtes](assets/query-editor.png)

1. À l’ouverture de Query Editor, saisissez une requête qui sélectionne les données du jeu de données.

   ![Créer une requête](assets/create-query.png)

   Par exemple, votre requête peut se présenter comme suit :

   ```sql
   SELECT * from `your_dataset_name` ORDER by TIMESTAMP DESC
   ```

1. Une fois la requête exécutée, les résultats s’affichent dans la variable **Résultats** en regard de l’onglet **Console** . Cette vue affiche la sortie tabulaire de votre requête.

   ![Éditeur de requêtes](assets/query-results.png)

Dans cet exemple, vous voyez les données d’événement de la variable [`commerce.productListAdds`](events.md#addtocart), [`commerce.productViews`](events.md#productpageview), [`web.webpagedetails.pageViews`](events.md#pageview), etc. Cette vue vous permet de vérifier que vos données Commerce sont arrivées à la périphérie.

Si les résultats ne correspondent pas à vos attentes, ouvrez votre jeu de données et recherchez les importations de lots ayant échoué. En savoir plus sur [dépannage des imports par lots](https://experienceleague.adobe.com/docs/experience-platform/ingestion/batch/troubleshooting.html).

## Étapes suivantes

Lorsque des données Commerce sont envoyées à l’Experience Platform Edge, d’autres produits Adobe Experience Cloud, tels que Adobe Journey Optimizer, peuvent utiliser ces données. Vous pouvez, par exemple, configurer Journey Optimizer pour écouter certains événements. En fonction de ces données d’événement, déclencher un courrier électronique pour un nouvel utilisateur ou si un panier est abandonné. Découvrez comment étendre votre plateforme Commerce en [création de parcours client](using-ajo.md) dans Journey Optimizer.
