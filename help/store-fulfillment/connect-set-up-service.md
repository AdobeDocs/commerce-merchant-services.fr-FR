---
title: Connexion à la solution d’exécution de magasin
description: Créez les connexions entre Adobe Commerce et la solution d’exécution de magasin. Créez et autorisez une intégration Adobe Commerce, puis ajoutez les informations d’identification du compte Store Fulfillment à la configuration du service Adobe Commerce.
role: Admin, Developer
level: Intermediate
feature: Shipping/Delivery, Install, Configuration, User Account, Tools and External Services
exl-id: 74c71c43-305a-4ea7-84f8-95f3ce0a9482
source-git-commit: 36b57648e156ead801764f3ee4e5e6a0f3245fe6
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# Connexion à la solution d’exécution de magasin

Connectez les services d’exécution de magasin à Adobe Commerce en ajoutant les informations d’authentification et les données de connexion requises à l’administrateur Adobe Commerce.

- **[Configurer [!DNL Commerce integration settings]](#create-an-adobe-commerce-integration)**-Créez une intégration Adobe Commerce pour les services d’exécution de magasin et générez les jetons d’accès pour authentifier les requêtes entrantes des serveurs d’exécution de magasin.

- **[Configuration des informations d’identification du compte pour les services d’exécution de magasin](#configure-store-fulfillment-account-credentials)**- Ajoutez vos informations d’identification pour connecter Adobe Commerce à votre compte d’exécution de magasin.

>[!NOTE]
>
>Effectuez la configuration de la connexion et validez la connexion avant de commencer le test.

## Création d’une intégration Adobe Commerce

Pour intégrer Adobe Commerce aux services d’exécution de magasin, vous créez une intégration Commerce et générez des jetons d’accès qui peuvent être utilisés pour authentifier les requêtes provenant des serveurs d’exécution de magasin. Vous devez également mettre à jour Adobe Commerce [!UICONTROL Consumer Settings] options de prévention `The consumer isn't authorized to access %resources.` erreurs de réponse sur les requêtes d’Adobe Commerce vers [!DNL Store Fulfillment] services.

1. Depuis l’administrateur, créez l’intégration pour l’exécution du magasin.

   - Nommer l’extension
   - Entrez votre adresse électronique
   - Entrez votre mot de passe du compte administrateur.

1. Configurez les autorisations d’accès aux ressources de l’API pour l’intégration avec ce qui suit :

   - Ventes > Mise à jour des commandes BOPIS
   - Système > Autorisations de l’application d’exécution de la boutique

1. Générez les jetons d’accès pour l’authentification en enregistrant et en activant l’intégration.

1. Copiez et enregistrez les jetons d’accès à un emplacement sécurisé et chiffré.

1. Contactez votre gestionnaire de compte pour terminer la configuration du côté Exécution de magasin et autoriser l’intégration.

1. Activation d’Adobe Commerce [!UICONTROL Consumer Settings] option à [!UICONTROL Allow OAuth Access Tokens to be used as standalone Bearer tokens].

   - Depuis l’administrateur, accédez à **[!UICONTROL Stores]** >  [!UICONTROL Configuration] > **[!UICONTROL Services]** >  **[!UICONTROL OAuth]** > **[!UICONTROL Consumer Settings]**

   - Définissez la variable [!UICONTROL Allow OAuth Access Tokens to be used as standalone Bearer tokens] option à **[!UICONTROL Yes]**.

>[!IMPORTANT]
>
> Le jeton d’intégration est spécifique à l’environnement. Si vous restaurez la base de données d’un environnement avec les données source d’un autre environnement (par exemple, la restauration des données de production d’un environnement d’évaluation), excluez la variable `oauth_token` table de l’exportation de la base de données, de sorte que les détails du jeton d’intégration ne soient pas remplacés lors de l’opération de restauration.


## Configuration des informations d’identification du compte d’exécution de magasin

Une fois que vous avez rempli le formulaire de prise en charge, un compte d’exécution de la boutique Walmart est créé pour vous. Vous recevez les informations d’identification suivantes lorsqu’elles sont disponibles :

- [!DNL Merchant ID]
- [!DNL Consumer ID]
- [!DNL Consumer Secret]
- [!DNL API Server URL]
- [!DNL Token Auth Server URL] (généralement identique à la configuration ci-dessus)

Ces informations d’identification sont requises pour configurer et utiliser l’exécution de magasin.

>[!NOTE]
>
>La création du compte peut prendre un certain temps. Pendant que vous attendez les informations d’identification, [révision et configuration d’autres paramètres pour la solution d’exécution de magasin](service-config-settings-overview.md).

### Ajout d’informations d’identification pour se connecter à l’exécution du magasin

1. Configurer [informations d’identification du compte](enable-general.md) pour les environnements de production et Sandbox.

1. Depuis l’administrateur, accédez à **[!UICONTROL Stores > Configuration > Services > Store Fulfillment by Walmart Commerce Technologies]**

1. Saisissez les informations d’identification du compte fournies pour la variable **[!UICONTROL Production environment]**. Tous les champs sont obligatoires.

1. Sélectionner **[!UICONTROL Save Config]**.

1. Testez la connexion en sélectionnant **[!UICONTROL Validate Credentials]**.

>[!NOTE]
>
>Si les informations d’identification ne sont pas valides, vérifiez que vous avez saisi les valeurs correctes pour chaque environnement et revalidez. Contactez votre gestionnaire de compte si vous rencontrez toujours des problèmes de connexion.
