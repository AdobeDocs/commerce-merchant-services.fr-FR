---
title: Connexion des données Commerce à Adobe Experience Platform
description: Découvrez comment connecter vos données Commerce à Adobe Experience Platform.
exl-id: 87898283-545c-4324-b1ab-eec5e26a303a
feature: Personalization, Integration, Configuration
source-git-commit: c252c2fb614ec74f1bdd11cc482066a7133dd523
workflow-type: tm+mt
source-wordcount: '2532'
ht-degree: 0%

---

# Connexion des données Commerce à Adobe Experience Platform

Lors de l’installation de l’extension [!DNL Data Connection], deux nouvelles pages de configuration s’affichent dans le menu **System** sous **Services** dans Commerce _Admin_.

- Connecteur Commerce Services
- [!DNL Data Connection]

Pour connecter votre instance Adobe Commerce à Adobe Experience Platform, vous devez configurer les deux connecteurs, en commençant par le connecteur Commerce Services , puis en finissant avec l’extension [!DNL Data Connection].

## Configuration du connecteur Commerce Services

Si vous avez précédemment installé un service Adobe Commerce, vous avez probablement déjà configuré le connecteur Commerce Services. Dans le cas contraire, vous devez effectuer les tâches suivantes sur la page [Connecteur Commerce Services](../landing/saas.md) :

1. Connectez-vous à votre compte Commerce pour [récupérer vos clés d’API de production et d’environnement de test](../landing/saas.md#credentials).
1. Sélectionnez un [espace de données SaaS](../landing/saas.md#saas-configuration).
1. Connectez-vous à votre compte d’Adobe pour [ récupérer votre ID d’organisation ](../landing/saas.md#ims-organization-optional).

Après avoir configuré le connecteur Commerce Services, vous pouvez configurer l’extension [!DNL Data Connection].

## Configuration de l’extension [!DNL Data Connection]

Dans cette section, vous apprendrez comment configurer l’extension [!DNL Data Connection].

### Ajout de détails sur le compte de service et les informations d’identification

Si vous prévoyez de collecter et d&#39;envoyer des [données de commande historiques](#send-historical-order-data) ou des [données de profil client](#send-customer-profile-data), vous devez ajouter les détails de compte de service et d&#39;identification. En outre, si vous configurez l’extension [Audience Activation](https://experienceleague.adobe.com/docs/commerce-admin/customers/audience-activation.html), vous devez effectuer ces étapes.

Si vous collectez et envoyez uniquement des données de storefront ou back-office, vous pouvez passer à la section [general](#general) .

#### Étape 1 : création d’un projet dans Adobe Developer Console

Créez un projet dans Adobe Developer Console qui authentifie Commerce afin qu’il puisse effectuer des appels API Experience Platform.

Pour créer le projet, suivez les étapes décrites dans le tutoriel [Authentification et accès aux API Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/landing/platform-apis/api-authentication.html) .

Lorsque vous passez en revue le tutoriel, assurez-vous que votre projet comporte les éléments suivants :

- Accès aux [ profils de produit ](https://experienceleague.adobe.com/docs/experience-platform/landing/platform-apis/api-authentication.html#select-product-profiles) suivants : **Production par défaut tous les accès** et **AEP Tous les accès par défaut**.
- Les [ rôles et autorisations corrects sont configurés ](https://experienceleague.adobe.com/docs/experience-platform/landing/platform-apis/api-authentication.html#assign-api-to-a-role).
- Si vous avez décidé d’utiliser des jetons Web JSON (JWT) comme méthode d’authentification serveur à serveur, vous devez également télécharger une clé privée.

Le résultat de cette étape crée un fichier de configuration que vous utilisez à l’étape suivante.

#### Étape 2 : téléchargement du fichier de configuration

Téléchargez le [fichier de configuration de l&#39;espace de travail](https://developer.adobe.com/commerce/extensibility/events/project-setup/#download-the-workspace-configuration-file). Copiez et collez le contenu de ce fichier dans la page **Informations d’identification/compte de service** de l’administrateur Commerce.

1. Dans l’administrateur Commerce, accédez à **Magasins** > Paramètres > **Configuration** > **Services** > **[!DNL Data Connection]**.

1. Sélectionnez la méthode d’autorisation serveur à serveur que vous avez implémentée dans le menu **Type d’autorisation Adobe Developer** . Adobe recommande d’utiliser OAuth. JWT a été abandonné. [En savoir plus](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/).

1. (JWT uniquement) Copiez et collez le contenu de votre fichier `private.key` dans le champ **Client Secret** . Utilisez la commande suivante pour copier le contenu.

   ```bash
   cat config/private.key | pbcopy
   ```

   Voir [Authentification du compte de service (JWT)](https://developer.adobe.com/developer-console/docs/guides/authentication/JWT/) pour plus d’informations sur le fichier `private.key`.

1. Copiez le contenu du fichier `<workspace-name>.json` dans le champ **Service Account/Credential details**.

   ![[!DNL Data Connection] Configuration de l’administrateur](./assets/epc-admin-config.png){width="700" zoomable="yes"}

1. Cliquez sur **Enregistrer la configuration**.

### Général

1. Dans l’Admin, accédez à **Système** > Services > **[!DNL Data Connection]**.

1. Dans l’onglet **Paramètres** sous **Général**, vérifiez l’ID associé à votre compte Adobe Experience Platform, tel que configuré dans le [Connecteur de services Commerce](../landing/saas.md#organizationid). L’ID d’organisation est global. Un seul ID d’organisation peut être associé par instance Adobe Commerce.

1. Dans la liste déroulante **Scope**, définissez le contexte sur **Website**.

1. (Facultatif) Si un [SDK Web AEP (alliage)](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html) a déjà été déployé sur votre site, cochez la case et ajoutez le nom de votre SDK Web AEP. Sinon, laissez ces champs vides et l’extension [!DNL Data Connection] en déploie un pour vous.

   >[!NOTE]
   >
   >Si vous spécifiez votre propre SDK Web AEP, l’extension [!DNL Data Connection] utilise l’identifiant de flux de données associé à ce SDK et non l’identifiant de flux de données spécifié sur cette page (le cas échéant).

### Collecte de données

Dans cette section, vous indiquez le type de données à collecter et à envoyer à l’Experience Platform Edge. Il existe trois types de données :

- **Comportement** (données côté client) : les données sont capturées sur le storefront. Cela inclut les interactions des acheteurs, telles que `View Page`, `View Product`, `Add to Cart` et les informations [liste de demandes](events.md#b2b-events) (pour les commerçants B2B).

- **Retour au bureau** (données côté serveur) : les données sont capturées dans les serveurs Commerce. Cela inclut des informations sur l’état d’une commande, par exemple si une commande a été passée, annulée, remboursée, expédiée ou terminée. Il comprend également les [données de commande historiques](#send-historical-order-data).

- **Profil (Beta)** est une donnée liée aux informations de profil de votre acheteur. Découvrez [more](#send-customer-profile-data).

Pour vous assurer que votre instance Adobe Commerce peut commencer la collecte de données, passez en revue les [conditions préalables](overview.md#prerequisites).

Pour en savoir plus sur les événements [storefront](events.md#storefront-events), [back office](events-backoffice.md) et [profile](events-backoffice.md#customer-profile-events-server-side), consultez la rubrique événements.

>[!NOTE]
>
>Tous les champs de la section **Collecte de données** s&#39;appliquent à la portée de **Website** ou supérieure.

1. Sélectionnez **Événements Storefront** si vous souhaitez envoyer des données comportementales storefront.

1. Sélectionnez **Evénements administratifs** si vous souhaitez envoyer des informations sur l&#39;état de la commande, par exemple si une commande a été passée, annulée, remboursée ou expédiée.

   >[!NOTE]
   >
   >Si vous sélectionnez **Evénements de back-office**, toutes les données de back-office sont envoyées à l’Experience Platform Edge. Si un acheteur choisit de se désabonner de la collecte de données, vous devez définir explicitement la préférence de confidentialité de l’acheteur dans l’Experience Platform. Cela diffère des événements storefront où le collecteur gère déjà le consentement en fonction des préférences de l’acheteur. Découvrez [plus](https://experienceleague.adobe.com/docs/experience-platform/landing/governance-privacy-security/consent/adobe/dataset.html) sur la définition des préférences de confidentialité d’un acheteur dans l’Experience Platform.

1. (Ignorez cette étape si vous utilisez votre propre SDK Web AEP.) [Créez](https://experienceleague.adobe.com/docs/experience-platform/datastreams/configure.html#create) un flux de données dans Adobe Experience Platform ou sélectionnez un flux de données existant à utiliser pour la collecte. Saisissez cet identifiant de flux de données dans le champ **ID de flux de données**.

1. Saisissez l’ **identifiant du jeu de données** que vous souhaitez contenir vos données Commerce. Pour trouver l’identifiant du jeu de données :

   1. Ouvrez l’interface utilisateur de l’Experience Platform et sélectionnez **Jeux de données** dans le volet de navigation de gauche pour ouvrir le tableau de bord **Jeux de données**. Le tableau de bord répertorie tous les jeux de données disponibles pour votre organisation. Des détails s’affichent pour chaque jeu de données répertorié, notamment son nom, le schéma auquel le jeu de données adhère et l’état de l’exécution d’ingestion la plus récente.
   1. Ouvrez le jeu de données associé à votre flux de données.
   1. Dans le volet de droite, affichez les détails du jeu de données. Copiez l’identifiant du jeu de données.

1. Pour assurer les mises à jour des données d’événement de back-office en fonction d’un planning conformément à une tâche [cron](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html), vous devez remplacer l’index `Sales Orders Feed` par `Update by Schedule`.

   1. Sur la barre latérale _Admin_, accédez à **[!UICONTROL System]** > _[!UICONTROL Tools]_>**[!UICONTROL Index Management]**.

   1. Cochez la case correspondant à l’indexeur `Sales Orders Feed`.

   1. Définissez **[!UICONTROL Actions]** sur `Update by Schedule`.

   1. Si vous activez les données du back-office pour la première fois, exécutez les commandes suivantes pour réindexer et déclencher une nouvelle synchronisation. Les resynchronisations suivantes se produisent automatiquement tant que la tâche [cron](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) est configurée correctement.

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
| Nom du SDK Web AEP (global) | Si un SDK Web Experience Platform est déjà déployé sur votre site, indiquez le nom de ce SDK dans ce champ. Cela permet au collecteur d’événements Storefront et au SDK d’événements Storefront d’utiliser votre SDK web Experience Platform plutôt que la version déployée par l’extension [!DNL Data Connection]. Si aucun SDK Web Experience Platform n’est déployé sur votre site, laissez ce champ vide et l’extension [!DNL Data Connection] en déploie un pour vous. |
| Événements Storefront | Est coché par défaut tant que l’ID d’organisation et l’ID de flux de données sont valides. Les événements Storefront collectent des données comportementales anonymes de vos clients lorsqu’ils naviguent sur votre site. |
| Événements de back-office | Si cette case est cochée, la payload d’événement contient des informations d’état de commande anonymes, telles qu’une commande passée, annulée, remboursée ou expédiée. |
| Identifiant de la banque de données (site web) | Identifiant qui permet aux données de passer de Adobe Experience Platform à d’autres produits DX d’Adobe. Cet identifiant doit être associé à un site web spécifique dans votre instance Adobe Commerce spécifique. Si vous spécifiez votre propre SDK Web Experience Platform, ne spécifiez pas d’identifiant de flux de données dans ce champ. L’extension [!DNL Data Connection] utilise l’identifiant de flux de données associé à ce SDK et ignore tout identifiant de flux de données spécifié dans ce champ (le cas échéant). |
| Identifiant du jeu de données (site web) | Identifiant du jeu de données qui contient vos données Commerce. Ce champ est obligatoire, sauf si vous avez désélectionné les cases à cocher **Evénements Storefront** ou **Evénements Back-office** . En outre, si vous utilisez votre propre SDK Web Experience Platform et n’avez donc pas spécifié d’identifiant de flux de données, vous devez toujours ajouter l’identifiant de jeu de données associé à votre flux de données. Sinon, vous ne pouvez pas enregistrer ce formulaire. |

Une fois l’intégration effectuée, les données du storefront commencent à s’écouler vers le bord Experience Platform. Les données du back-office prennent environ cinq minutes pour s’afficher à la périphérie. Les mises à jour suivantes sont visibles à la périphérie en fonction de la planification cron.

### Envoi des données de profil client

>[!IMPORTANT]
>
>Cette fonctionnalité est en version bêta.

Vous pouvez envoyer à l’Experience Platform deux types de données de profil : les enregistrements de profil et les événements de profil de série temporelle.

Un enregistrement de profil contient des données enregistrées lorsqu’un acheteur crée un profil dans votre instance Commerce, tel que le nom de l’acheteur. Lorsque votre schéma et votre jeu de données sont [correctement configurés](profile-data.md), un enregistrement de profil est envoyé à l’Experience Platform et transféré au service de gestion des profils et de segmentation d’Adobe : [Real-Time CDP](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/intro/rtcdp-intro/overview.html?lang=fr).

Les événements de profil de série temporelle contiennent des données sur les informations de profil de votre acheteur, telles que la création, la modification ou la suppression d’un compte sur votre site. Lorsque des données d’événement de profil sont envoyées à l’Experience Platform, elles se trouvent dans un jeu de données où elles peuvent être utilisées par d’autres produits DX.

1. Vérifiez que vous disposez du compte de service [fourni](#add-service-account-and-credential-details) et des informations d’identification.

1. Assurez-vous qu’un schéma et un jeu de données sont spécifiés pour l’ [ingestion de données d’enregistrement de profil](profile-data.md) et l’ [ ingestion de données d’événement de profil de série temporelle ](update-xdm.md#time-series-profile-event-data).

1. Cochez la case **Profils client** si vous souhaitez envoyer des données de profil à l’Experience Platform.

1. Saisissez l’ **identifiant du jeu de données de profil**.

   Les données d’enregistrement de profil doivent utiliser un jeu de données différent de celui que vous utilisez actuellement pour les données d’événement comportemental et back-office.

1. Si vous ne souhaitez pas diffuser des événements de profil par le biais du même identifiant de flux de données que celui utilisé pour les données comportementales et de back-office, supprimez la coche des **profils client de flux via le même identifiant de flux de données** et saisissez l’identifiant de flux de données que vous souhaitez utiliser à la place.

Il peut s’écouler environ 10 minutes avant qu’un enregistrement de profil soit disponible dans Real-Time CDP. Les événements de profil commencent immédiatement à être diffusés en continu.

>[!TIP]
>
>Si vous ne voyez pas les données de profil dans l’Experience Platform, reportez-vous à la [base de connaissances Commerce](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/data-connection-customer-profiles-not-exported) pour obtenir des suggestions en matière de dépannage.

#### Descriptions des champs

| Champ | Description |
|--- |--- |
| Profils client | Cochez cette case si vous souhaitez collecter et envoyer des enregistrements de profil client. |
| Identifiant du jeu de données de profil | Un enregistrement de profil doit utiliser un jeu de données différent de celui utilisé pour les événements de comportement et de back-office. |
| Diffusion en continu des profils client à l’aide du même identifiant de flux de données | Déterminez si vous souhaitez utiliser la même banque de données actuellement utilisée pour vos événements de comportement et back-office ou non. |
| Flux de données pour les profils client | Spécifiez le flux de données spécifique à l’enregistrement du profil client. |

### Envoi de données de commande historiques

Adobe Commerce collecte jusqu’à cinq années de [données de commande historiques et état](events-backoffice.md#back-office-events). Vous pouvez utiliser l’extension [!DNL Data Connection] pour envoyer ces données historiques à l’Experience Platform afin d’enrichir vos profils client et de personnaliser les expériences client en fonction de ces commandes passées. Les données sont stockées dans un jeu de données dans Experience Platform.

Bien que Commerce collecte déjà les données de commande historiques, vous devez effectuer plusieurs étapes pour envoyer ces données à l’Experience Platform.

Regardez cette vidéo pour en savoir plus sur les commandes historiques, puis effectuez les étapes suivantes pour mettre en oeuvre la collecte des commandes historiques.

>[!VIDEO](https://video.tv.adobe.com/v/3424672)

#### Configuration du service de synchronisation des commandes

Le service de synchronisation des commandes utilise le [Message Queue Framework](https://developer.adobe.com/commerce/php/development/components/message-queues/) et RabbitMQ. Une fois ces étapes terminées, les données d’état de la commande peuvent être synchronisées avec SaaS, ce qui est nécessaire avant d’être envoyées à l’Experience Platform.

1. Vérifiez que vous disposez du compte de service [fourni](#add-service-account-and-credential-details) et des informations d’identification.

1. [Activer](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/rabbitmq.html) RabbitMQ.

   >[!NOTE]
   >
   >RabbitMQ est déjà configuré pour Commerce versions 2.4.7 et ultérieures, mais vous devez activer les consommateurs.

1. Activez les consommateurs de la file d’attente de messages par tâche cron dans `.magento.env.yaml` à l’aide de la variable d’environnement `CRON_CONSUMERS_RUNNER`.

   ```yaml
      stage:
        deploy:
          CRON_CONSUMERS_RUNNER:
            cron_run: true
   ```

   >[!NOTE]
   >
   >Pour en savoir plus sur toutes les options de configuration disponibles, consultez la [documentation sur le déploiement des variables](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#cron_consumers_runner) .

Une fois le service de synchronisation des commandes activé, vous pouvez spécifier la période de commande historique dans la page **[!UICONTROL [!DNL Data Connection]]**.

#### Définition de la période d’historique des commandes

Indiquez la période des commandes historiques à envoyer à l’Experience Platform.

1. Dans l’Admin, accédez à **Système** > Services > **[!DNL Data Connection]**.

1. Sélectionnez l’onglet **Historique des commandes** .

1. Sous **Synchronisation de l’historique des commandes**, la case à cocher **Copier l’identifiant du jeu de données de Paramètres** est déjà activée. Vous avez ainsi la garantie d’utiliser le même jeu de données que celui spécifié dans l’onglet **Paramètres**.

1. Dans les champs **De** et **À** , spécifiez la plage de dates pour les données de l’ordre historique que vous souhaitez envoyer. Vous ne pouvez pas sélectionner de période supérieure à cinq ans.

1. Sélectionnez **[!UICONTROL Start Sync]** pour déclencher la synchronisation. Les données d’ordre historique sont des données par lots, contrairement aux données de vitrine et de back-office qui diffusent des données en continu. Les données mises en cache prennent environ 45 minutes pour arriver en Experience Platform.

##### Descriptions des champs

| Champ | Description |
|--- |--- |
| Copier l’identifiant du jeu de données depuis les paramètres | Copie l’identifiant du jeu de données que vous avez saisi dans l’onglet **Paramètres** . |
| Identifiant du jeu de données (site web) | Identifiant du jeu de données qui contient vos données Commerce. Ce champ est obligatoire, sauf si vous avez désélectionné les cases à cocher **Evénements Storefront** ou **Evénements Back-office** . En outre, si vous utilisez votre propre SDK Web Experience Platform et n’avez donc pas spécifié d’identifiant de flux de données, vous devez toujours ajouter l’identifiant de jeu de données associé à votre flux de données. Sinon, vous ne pouvez pas enregistrer ce formulaire. |
| De | Date à partir de laquelle vous souhaitez commencer à collecter les données de l’historique des commandes. |
| À | Date à partir de laquelle vous souhaitez terminer la collecte des données d’historique des commandes. |
| Démarrer la synchronisation | Démarre le processus de synchronisation des données de l’historique des commandes avec le serveur Experience Platform Edge. Ce bouton est désactivé si le champ **[!UICONTROL Dataset ID]** est vide ou si l’identifiant du jeu de données n’est pas valide. |

## Confirmation que les données d’événement sont collectées

Pour confirmer que les données sont collectées à partir de votre boutique Commerce, utilisez le [débogueur Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/debugger/home.html) pour examiner votre site Commerce. Une fois que vous avez confirmé que les données sont en cours de collecte, vous pouvez vérifier que vos données d’événement storefront et back-office apparaissent en périphérie en exécutant une requête qui renvoie les données du [jeu de données que vous avez créé](overview.md#prerequisites).

1. Sélectionnez **Requêtes** dans le volet de navigation de gauche de l’Experience Platform et cliquez sur [!UICONTROL Create Query].

   ![Éditeur de requête](assets/query-editor.png)

1. À l’ouverture de Query Editor, saisissez une requête qui sélectionne les données du jeu de données.

   ![Créer une requête](assets/create-query.png)

   Par exemple, votre requête peut se présenter comme suit :

   ```sql
   SELECT * from `your_dataset_name` ORDER by TIMESTAMP DESC
   ```

1. Une fois la requête exécutée, les résultats s’affichent dans l’onglet **Résultats**, en regard de l’onglet **Console**. Cette vue affiche la sortie tabulaire de votre requête.

   ![Éditeur de requête](assets/query-results.png)

Dans cet exemple, vous voyez les données d’événement de [`commerce.productListAdds`](events.md#addtocart), [`commerce.productViews`](events.md#productpageview), [`web.webpagedetails.pageViews`](events.md#pageview), etc. Cette vue vous permet de vérifier que vos données Commerce sont arrivées à la périphérie.

Si les résultats ne correspondent pas à vos attentes, ouvrez votre jeu de données et recherchez les importations de lots ayant échoué. En savoir plus sur la [résolution des problèmes d’importation de lots](https://experienceleague.adobe.com/docs/experience-platform/ingestion/batch/troubleshooting.html).

### Vérifier que les données de profil s’affichent dans l’Experience Platform

Si vous ne voyez pas les données de profil dans l’Experience Platform, reportez-vous à la [base de connaissances Commerce](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/data-connection-customer-profiles-not-exported) pour obtenir des suggestions en matière de dépannage.

## Étapes suivantes

Lorsque des données Commerce sont envoyées à l’Experience Platform Edge, d’autres produits Adobe Experience Cloud, tels que Adobe Journey Optimizer, peuvent utiliser ces données. Vous pouvez, par exemple, configurer Journey Optimizer pour écouter certains événements. En fonction de ces données d’événement, déclencher un courrier électronique pour un nouvel utilisateur ou si un panier est abandonné. Découvrez comment étendre votre plateforme Commerce en [créant des parcours client](using-ajo.md) dans Journey Optimizer.
