---
title: Connexion à votre instance
description: Connectez votre instance Commerce à l’aide d’une clé API et d’une clé privée, puis spécifiez l’espace de données dans la configuration.
exl-id: 5038fd31-bac5-419e-a172-66919a9b5272
feature: Payments, Checkout, Configuration, Saas
source-git-commit: 6769e29a4ae07b8cf15aa2da3cac2fe8583497e0
workflow-type: tm+mt
source-wordcount: '635'
ht-degree: 0%

---

# Connexion à votre instance

[!DNL Payment Services] est optimisé par Commerce Services et déployé en tant que SaaS (logiciel en tant que service). Vous connectez votre instance Commerce à l’aide d’une clé API et d’une clé privée, puis spécifiez l’espace de données dans la configuration à l’aide de la variable [Connecteur Commerce Services](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html). **Vous ne configurez cette connexion qu’une seule fois.**

* Si vous avez *votre instance déjà connectée*, en obtenant et en utilisant vos informations d’identification d’API et en configurant Commerce Services, vous pouvez passer à [configuration de votre environnement de test](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/sandbox.html).
* Si vous continuez *besoin de connecter votre instance*, reportez-vous aux informations de cette rubrique sur [Obtention des informations d’identification d’API](#obtain-api-credentials) et [configuration de Commerce Services](#configure-commerce-services).
* Si vous *ne pas savoir si votre instance est connectée*, accédez à **Système** > Services > **Connecteur Commerce Services** et d’afficher les valeurs des clés API publiques et privées dans la variable [!UICONTROL Sandbox Keys] et [!UICONTROL Production Keys] et la variable *Projet* et *Espace de données* dans le champ [!UICONTROL SaaS Identifier] . Si ces valeurs sont présentes, votre instance est connectée.

## Obtention des informations d’identification de l’API

Pour utiliser un service SaaS Commerce, vous devez utiliser les clés d’API de votre instance (clé d’API publique Commerce et clé privée) pour l’environnement de test et la production, qui sont créés et gérés dans votre [Mon tableau de bord de compte](https://account.magento.com/customer/account/login). [La paire de clés](https://docs.magento.com/user-guide/configuration/services/saas.html) peut être créé pour un compte Commerce (un pour sandbox et un autre pour la production), bien qu’une seule paire puisse être utilisée activement à la fois.

>[!NOTE]
>
>Besoin d’aide pour accéder à [!UICONTROL My Account] tableau de bord ? Voir [Création d’un compte Commerce](https://docs.magento.com/user-guide/magento/magento-account-create.html).

Une fois créée, une clé API publique est toujours disponible dans le tableau de bord Mon compte. Il peut être copié ou supprimé si nécessaire. La clé d’API privée devient visible lorsque vous créez une clé d’API publique pour l’environnement de test ou la production. Elle n’est disponible que pour la copie ou l’enregistrement à partir de la boîte de dialogue qui s’ensuit et ne peut pas être consultée ultérieurement.

Une paire de clés API donnée est valide pour tous les services de commerce dans un environnement. Par conséquent, si vous avez déjà configuré les services de commerce pour votre instance, votre paire de clés API est déjà présente dans le connecteur de services de commerce.

Si votre clé API est perdue, une nouvelle paire de clés API doit être [généré](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html#generate-an-api-key-and-private-key) et [appliqué](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html#configure-saas-project) à la configuration du connecteur Commerce Services dans l’Admin. Si des clés incorrectes sont configurées ou qu’aucune clé n’existe dans la configuration, une boîte de dialogue d’erreur de vérification de compte s’affiche dans les Services de paiement pour vous informer que le compte n’a pas été vérifié.

Voir [liste des services Commerce disponibles qui utilisent l’API](https://docs.magento.com/user-guide/system/saas.html#available-services).

Pour savoir comment générer une clé API pour des environnements de test ou de production, voir [Informations d’identification](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html#apikey).

>[!IMPORTANT]
>
>Il est recommandé de ne pas régénérer une paire de clés API *et* Modifiez l’identifiant SaaS et/ou l’espace de données sur une instance de production active. Vous perdrez des données pour votre instance si elles sont modifiées.

## Configuration de Commerce Services

La même clé API peut être utilisée entre les instances, mais chaque instance doit avoir sa propre clé [Espace de données SaaS](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html#saasenv).

>[!NOTE]
>
>Les commerçants doivent utiliser les mêmes clés générées pour le MageID pour leurs droits au paiement.

Maintenant que vous avez obtenu vos informations d’identification, vous pouvez configurer votre projet SaaS et Saas Data Space.

1. Sur le _Administration_ barre latérale, accédez à **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]**.
1. Cliquez sur **[!UICONTROL Configure Commerce Services]**.

   Cette option est visible si vous n’avez pas encore configuré Commerce Services pour votre compte.

   Vous êtes dirigé vers la zone de configuration de l’administrateur, **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**>**[!UICONTROL Commerce Services Connector]**, pour configurer votre connecteur Commerce Services.

1. Pour configurer vos services de commerce, procédez comme décrit dans la section [Configuration SaaS](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html#saasenv).
