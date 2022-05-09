---
title: Connexion à votre instance
description: Connectez votre instance Commerce à l’aide d’une clé API et d’une clé privée, puis spécifiez l’espace de données dans la configuration.
exl-id: 5038fd31-bac5-419e-a172-66919a9b5272
source-git-commit: 9596815e31402f23b399b223f3221074331c1773
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Connexion à votre instance

[!DNL Payment Services] est optimisé par Commerce Services et déployé en tant que SaaS (logiciel en tant que service). Connectez votre instance Commerce à l’aide d’une clé API et d’une clé privée, puis spécifiez l’espace de données dans la configuration. Vous ne configurez cette connexion qu’une seule fois.

Voir [Connecteur Commerce Services](https://docs.magento.com/user-guide/system/saas.html){target=&quot;_blank&quot;} dans le guide d’utilisation principal pour obtenir des informations détaillées sur ce service.

## Obtention des informations d’identification de l’API

Pour utiliser un service SaaS Commerce, vous devez utiliser les clés d’API de votre instance, qui sont créées et gérées dans votre [Mon tableau de bord de compte](https://account.magento.com/customer/account/login){target=&quot;_blank&quot;}. Il est possible de créer deux paires de clés d’API différentes pour un compte Commerce (une pour les environnements de test et une pour la production (paiements en direct)), bien qu’une seule paire puisse être utilisée activement à la fois.

>[!NOTE]
>
>Besoin d’aide pour accéder à [!UICONTROL My Account] tableau de bord ? Voir [Création d’un compte Commerce](https://docs.magento.com/user-guide/magento/magento-account-create.html){target=&quot;_blank&quot;} dans le guide d’utilisation principal.

Une paire de clés d’API donnée est valide pour tous les services de commerce dans un environnement. Par conséquent, si vous avez déjà configuré les services de commerce pour votre instance de commerce, votre paire de clés d’API est déjà présente dans l’administrateur. Si votre clé d’API privée est perdue, une nouvelle paire de clés d’API doit être générée et appliquée à la configuration de Commerce Services dans l’administrateur.

Pour savoir comment générer une clé API pour des environnements de test ou de production, voir [Connecteur Commerce Services](https://docs.magento.com/user-guide/system/saas.html){target=&quot;_blank&quot;} dans le guide d’utilisation principal.

>[!IMPORTANT]
>
>Si vous régénérez une paire de clés API et modifiez l’identifiant SaaS, tous les services de commerce utilisés par cette instance se connectent à un autre entrepôt de données et votre accès (y compris les données précédemment stockées) est perdu. Il est recommandé de ne pas régénérer une paire de clés API et de modifier l’identifiant SaaS sur une instance de production principale.

### Clé API de commerce et clé privée

Certains [!DNL Adobe Commerce] et [!DNL Magento Open Source] Les fonctionnalités sont déployées en tant que SaaS (logiciel en tant que service), connue sous le nom de Commerce Services. Pour utiliser ces services, vous devez connecter votre instance Commerce à ces services à l’aide d’une clé API et d’une clé privée, puis spécifier l’espace de données souhaité dans la variable [configuration](https://docs.magento.com/user-guide/configuration/services/saas.html){target=&quot;_blank&quot;}.

Lorsque vous créez un compte Commerce, identifié par un MageID, vous pouvez générer une clé API Commerce et une clé privée. Pour utiliser les services de commerce, tels que [!DNL Payment Services], [!DNL Product Recommendations]ou [!DNL Live Search], le détenteur de licence doit générer ces clés pour passer la validation des droits. Ces clés peuvent ensuite être transmises à l’intégrateur système ou à l’équipe de développement qui gère les projets et les environnements pour le compte du détenteur de licence. Si vous êtes un intégrateur de solution, vous avez également le droit d’utiliser ces services pour vos propres besoins. Dans ce cas, le signataire du contrat de partenaire commercial doit générer les clés.

### Génération d’une clé API et d’une clé privée

1. Connectez-vous à votre compte Commerce à l’adresse [https://account.magento.com/customer/account/login](https://account.magento.com/customer/account/login).
1. Sous , **[!UICONTROL Magento]** onglet, sélectionnez **[!UICONTROL API Portal]** dans la barre latérale.
1. Dans la _[!UICONTROL Environment]_menu, sélectionnez **[!UICONTROL Sandbox]**, puis **[!UICONTROL Production]**.

   >[!IMPORTANT]
   >
   >Des clés d’API sont requises pour les deux environnements.

1. Saisissez un nom dans le champ _[!UICONTROL API Keys]_et cliquez sur **[!UICONTROL Add New]**.

   Cette action ouvre une boîte de dialogue pour télécharger la nouvelle clé.

   >[!IMPORTANT]
   >
   >Cette boîte de dialogue est la seule opportunité dont vous avez besoin pour copier ou télécharger votre clé.

1. Cliquez sur **[!UICONTROL Download]** puis cliquez sur **[!UICONTROL Cancel]**.

   Le _[!UICONTROL API Keys]_affiche désormais votre clé API.

1. Copiez la clé API et la clé privée lorsque vous sélectionnez ou créez un projet SaaS.

   Voir [SaaS](https://docs.magento.com/user-guide/system/saas.html){target=&quot;_blank&quot;} dans le guide d’utilisation principal pour plus d’informations.

La même clé API peut être utilisée sur plusieurs instances, mais chaque instance doit disposer de son propre espace de données SaaS.

Lorsque vous créez un projet SaaS, Commerce génère un ou plusieurs espaces de données SaaS en fonction de votre licence Commerce :

* [!DNL Adobe Commerce] - un espace de données de production ; deux espaces de données de test
* [!DNL Magento Open Source] - un espace de données de production ; aucun espace de données de test

### Configuration du projet SaaS

>[!NOTE]
>
>Si vous ne voyez pas l’événement _[!UICONTROL Commerce Services Connector]_dans la configuration de Commerce, vous devez installer les modules Commerce pour le service Commerce souhaité, comme [[!DNL Payment Services]](install.md).

Pour sélectionner ou créer un projet SaaS, demandez la clé API Commerce au détenteur de licence Commerce pour votre magasin.

1. Sur le _Administration_ barre latérale, accédez à **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Dans le panneau de gauche, développez **[!UICONTROL Services]** et choisissez **[!UICONTROL Commerce Services Connector]**.
1. Dans le _[!UICONTROL API Keys]_, collez vos valeurs clés.

   >[!IMPORTANT]
   >
   >Ajout de valeurs clés pour les deux **[!UICONTROL sandbox]** et **[!UICONTROL production]** des environnements.

1. Cliquez sur **[!UICONTROL Save Config]**.

   Lorsque vous enregistrez, si des projets SaaS sont associés à votre clé API, ces projets apparaissent dans la variable _[!UICONTROL SaaS Project]_dans le champ_[!UICONTROL SaaS Identifier]_ .

1. S’il n’existe aucun projet SaaS, cliquez sur **[!UICONTROL Create Project]**. Saisissez ensuite un nom pour votre projet SaaS dans la **[!UICONTROL Project Name]** champ .
1. Pour utiliser pour la configuration actuelle de votre boutique Commerce, sélectionnez la variable **[!UICONTROL SaaS Data Space]**.

>[!IMPORTANT]
>
>Si vous régénérez vos clés dans la section Portail API de Mon compte, mettez immédiatement à jour les clés API dans la configuration Admin. Si vous générez de nouvelles clés et que vous ne les mettez pas à jour dans l’Admin, vos extensions SaaS ne fonctionneront plus et vous perdrez des données importantes.

Vous pouvez modifier les noms en cliquant sur le bouton **[!UICONTROL Rename this Project]** ou **[!UICONTROL Rename Data Space]** des boutons, respectivement.

## Configuration de Commerce Services

Première étape de l’intégration [!DNL Payment Services] est de configurer vos services de commerce dans l’administrateur.

1. Sur le _Administration_ barre latérale, accédez à **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]**.
1. Cliquez sur **[!UICONTROL Configure Commerce Services]**.

   Cette option est visible si vous n’avez pas encore configuré Commerce Services pour votre compte.

   Vous êtes dirigé vers la zone de configuration de l’administrateur, **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**>**[!UICONTROL Commerce Services Connector]**, pour configurer votre connecteur Commerce Services.

1. Pour configurer vos services de commerce, procédez comme décrit dans la section [Services de commerce](https://docs.magento.com/user-guide/system/saas.html#createsaasenv){target=&quot;_blank&quot;}.
