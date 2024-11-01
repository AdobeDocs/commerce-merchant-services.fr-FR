---
title: Connexion à votre instance
description: Connectez votre instance Commerce à l’aide d’une clé API et d’une clé privée, puis spécifiez l’espace de données dans la configuration.
exl-id: 5038fd31-bac5-419e-a172-66919a9b5272
feature: Payments, Checkout, Configuration, Saas
source-git-commit: 37380063242b6d904910be731b8e58471625e9cb
workflow-type: tm+mt
source-wordcount: '636'
ht-degree: 0%

---

# Connexion à votre instance

[!DNL Payment Services] est optimisé par les services Commerce et déployé en tant que SaaS (logiciel en tant que service). Connectez votre instance Commerce à l’aide d’une clé API et d’une clé privée, puis spécifiez l’espace de données dans la configuration à l’aide du [Connecteur de services Commerce](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html). **Vous n&#39;avez configuré cette connexion qu&#39;une seule fois.**

>[!INFO]
>
> Pour plus d’informations, consultez notre vidéo [[!DNL Adobe Commerce] Connecteur de services](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/admin/adobe-commerce-services/configure-adobe-commerce-services-connector.html?lang=en) .

* Si *vous avez déjà connecté à votre instance*, en obtenant et en utilisant vos informations d’identification d’API et en configurant les services Commerce, vous pouvez passer à la [configuration de votre environnement de test](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/sandbox.html).
* Si vous *devez toujours connecter votre instance*, consultez les informations de cette rubrique sur l’ [obtention des informations d’identification d’API](#obtain-api-credentials) et la [configuration des services Commerce](#configure-commerce-services).
* Si vous ne savez pas si votre instance est connectée *, accédez à&#x200B;**System**> Services >**Commerce Services Connector**et affichez les valeurs des clés API publiques et privées dans les sections [!UICONTROL Sandbox Keys] et [!UICONTROL Production Keys], ainsi que les champs* Project *et* Data Space *de la section [!UICONTROL SaaS Identifier].* Si ces valeurs sont présentes, votre instance est connectée.

>[!NOTE]
>
>Tous les commerçants autorisés pour les services de paiement peuvent utiliser un espace de données de production et deux espaces de données de test.

## Obtention des informations d’identification de l’API

Pour utiliser un service Commerce SaaS, vous devez utiliser les clés d’API de votre instance (clé d’API publique Commerce et clé privée) pour les environnements de test et de production, qui sont créés et gérés dans votre [tableau de bord de votre compte](https://account.magento.com/customer/account/login). [La paire de clés](https://experienceleague.adobe.com/en/docs/commerce-admin/config/services/saas) peut être créée pour un compte Commerce (un pour les environnements de test et un autre pour la production), bien qu’une seule paire puisse être utilisée activement à la fois.

>[!NOTE]
>
>Vous avez besoin d&#39;aide pour accéder à votre tableau de bord [!UICONTROL My Account] ? Voir [Création d’un compte Commerce](https://experienceleague.adobe.com/en/docs/commerce-admin/start/commerce-account/commerce-account-create).

Une fois créée, une clé API publique est toujours disponible dans le tableau de bord Mon compte. Il peut être copié ou supprimé si nécessaire. La clé d’API privée devient visible lorsque vous créez une clé d’API publique pour l’environnement de test ou la production. Elle n’est disponible que pour la copie ou l’enregistrement à partir de la boîte de dialogue qui s’ensuit et ne peut pas être consultée ultérieurement.

Une paire de clés API donnée est valide pour tous les services Commerce dans un environnement. Par conséquent, si vous avez déjà configuré les services Commerce pour votre instance, votre paire de clés API est déjà présente dans le connecteur des services Commerce.

Si votre clé API est perdue, une nouvelle paire de clés API doit être [générée](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html#generate-an-api-key-and-private-key) et [appliquée](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html#configure-saas-project) à la configuration du connecteur Commerce Services dans l’administrateur. Si des clés incorrectes sont configurées ou qu’aucune clé n’existe dans la configuration, une boîte de dialogue d’erreur de vérification de compte s’affiche dans les Services de paiement pour vous informer que le compte n’a pas été vérifié.

Voir la [liste des services Commerce disponibles qui utilisent l’API](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/user-guides/integration-services/saas#availableservices).

Pour savoir comment générer une clé API pour des environnements de test ou de production, voir [Informations d’identification](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html#apikey).

>[!IMPORTANT]
>
>Il est recommandé de ne pas régénérer une paire de clés API *et de* modifier l’identifiant SaaS et/ou l’espace de données sur une instance de production active. Vous perdrez des données pour votre instance si elles sont modifiées.

## Configuration des services Commerce

La même clé API peut être utilisée entre les instances, mais chaque instance doit disposer de son propre [espace de données SaaS](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html#saasenv).

>[!NOTE]
>
>Les commerçants doivent utiliser les mêmes clés générées pour le MageID pour leurs droits au paiement.

Maintenant que vous avez obtenu vos informations d’identification, vous pouvez configurer votre projet SaaS et Saas Data Space.

1. Sur la barre latérale _Admin_, accédez à **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]**.
1. Cliquez sur **[!UICONTROL Configure Commerce Services]**.

   Cette option est visible si vous n’avez pas encore configuré les services Commerce pour votre compte.

   Vous êtes dirigé vers la zone de configuration dans Admin, **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**>**[!UICONTROL Commerce Services Connector]**, pour configurer votre connecteur Commerce Services.

1. Pour configurer vos services Commerce, suivez les étapes décrites dans la [configuration SaaS](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html#saasenv).

   >[!INFO]
   >
   > Pour plus d’informations, consultez notre vidéo [[!DNL Adobe Commerce] Connecteur de services](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/admin/adobe-commerce-services/configure-adobe-commerce-services-connector.html?lang=en#configuration-faqs) .

## Point d’entrée

[!DNL Payment Services] utilise le [ Connecteur de services Commerce](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html) pour se connecter aux services Commerce et le déployer en tant que SaaS. Ce [!DNL Commerce Services Connector] communique par le biais du point de terminaison à l’adresse :

* `commerce-beta.adobe.io` pour les environnements Sandbox.
* `commerce.adobe.io for` pour les environnements en ligne.
