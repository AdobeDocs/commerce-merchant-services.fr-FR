---
title: Connecteur Commerce Services
description: Découvrez comment intégrer votre instance Adobe Commerce ou Magento Open Source aux services à l’aide des clés d’API de production et d’environnement de test.
exl-id: 28027a83-449b-4b96-b926-a7bfbfd883d8
feature: Services, Saas
role: Admin, User
source-git-commit: 391208f63c092f1eebb7330e2445079e09594890
workflow-type: tm+mt
source-wordcount: '1048'
ht-degree: 0%

---

# [!DNL Commerce Services Connector]

Certaines fonctionnalités Adobe Commerce et Magento Open Source sont optimisées par [!DNL Commerce Services] et déployées en tant que SaaS (logiciel en tant que service). Pour utiliser ces services, vous devez connecter votre instance [!DNL Commerce] à l’aide des clés d’API de production et d’environnement de test, et spécifier l’espace de données dans la [configuration](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html). Il vous suffit de configurer la connexion une seule fois pour chaque instance Commerce.

## Services disponibles {#availableservices}

La liste suivante répertorie les fonctionnalités [!DNL Commerce] auxquelles vous pouvez accéder par l’intermédiaire de [!DNL Commerce Services Connector] :

| Service | Disponibilité |
| ---|--- |
| [[!DNL Product Recommendations]](/help/product-recommendations/overview.md) avec technologie Adobe Sensei | Adobe Commerce |
| [[!DNL Live Search]](/help/live-search/overview.md) avec technologie Adobe Sensei | Adobe Commerce |
| [[!DNL Payment Services]](/help/payment-services/overview.md) | Adobe Commerce et Magento Open Source |
| [[!DNL Site-Wide Analysis Tool]](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/intro.html) | Adobe Commerce |
| [[!DNL Catalog Service]](/help/catalog-service/overview.md) | Adobe Commerce |
| [[!DNL Data Connection]](/help/data-connection/overview.md) | Adobe Commerce |

## Architecture

À un niveau élevé, le [!DNL Commerce Services Connector] est constitué des éléments principaux suivants :

![Architecture du connecteur de services Commerce](assets/saas-config-sync-workflow.png)

Les sections suivantes abordent plus en détail chacun de ces éléments.

## Informations d’identification {#apikey}

Les clés d’API de production et d’environnement de test sont générées à partir du compte [!DNL Commerce] du [propriétaire de licence](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/start/onboarding). Le compte Commerce est identifié par un [!DNL Commerce] ID unique (MageID). Le propriétaire de la licence de l’organisation du commerçant peut générer des clés d’API pour des services tels que Recommendations de produit ou Live Search, à condition que le compte soit en règle.

Les clés peuvent être partagées &quot;au besoin&quot; avec l’intégrateur système ou l’équipe de développement qui gère les projets et environnements pour le compte du détenteur de la licence. Les développeurs qui ont reçu [!DNL Shared Access] par le propriétaire de la licence ne peuvent pas générer les clés en leur nom, même si l’organisation du commerçant est présente dans la liste déroulante [!DNL Switch Accounts] de leur compte.

De plus, les intégrateurs de solution sont également autorisés à utiliser [!DNL Commerce Services]. Si vous êtes un intégrateur de solution, le signataire du contrat de partenaire [!DNL Commerce] doit générer les clés d’API.

>[!NOTE]
>
>Le propriétaire de la licence est généralement le contact par Principal sur le compte Adobe Commerce et n’est pas toujours le même que le propriétaire du projet Adobe Commerce sur le projet d’infrastructure cloud.

### Génération des clés d’API de production et d’environnement de test {#genapikey}

1. Connectez-vous à votre compte [!DNL Commerce] à l’adresse [https://account.magento.com](https://account.magento.com/){:target=&quot;_blank&quot;}.

1. Sous l’onglet **Magento**, sélectionnez **Portail API** sur la barre latérale.

1. Dans le menu _Environnement_, sélectionnez **Production** ou **Sandbox**.

1. Saisissez un nom dans la section _Clés API_, puis cliquez sur **Ajouter nouveau** pour ouvrir la boîte de dialogue de téléchargement de la nouvelle clé.

   ![Télécharger la clé privée](assets/download-api-private-key.png)

   >[!WARNING]
   >
   > Cette boîte de dialogue vous offre la seule opportunité de copier ou télécharger vos clés.

1. Cliquez sur **Télécharger** puis sur **Annuler**.

1. Répétez les étapes ci-dessus pour chaque environnement (production et environnement de test).

   La section **Clés API** affiche désormais vos clés API (publiques). Vous avez besoin des clés de production et d’environnement de test (Public + Privé) lorsque vous [ sélectionnez ou créez un projet SaaS ](#createsaasenv).

## Configuration SaaS {#saasenv}

Les instances [!DNL Commerce] doivent être configurées avec un projet SaaS et un espace de données SaaS afin que [!DNL Commerce Services] puisse envoyer des données vers le bon emplacement. Un projet SaaS regroupe tous les espaces de données SaaS. Les espaces de données SaaS sont utilisés pour collecter et stocker des données qui permettent à [!DNL Commerce Services] de fonctionner. Certaines de ces données peuvent être exportées à partir de l’instance [!DNL Commerce] et d’autres peuvent être collectées à partir du comportement d’achat sur le storefront. Ces données sont ensuite conservées pour sécuriser l’espace de stockage dans le cloud.

Pour [!DNL Product Recommendations], l’espace de données SaaS contient des données de catalogue et de comportement. Vous pouvez pointer une instance [!DNL Commerce] vers un espace de données SaaS en [la sélectionnant](https://docs.magento.com/user-guide/configuration/services/saas.html) dans la configuration [!DNL Commerce].

>[!WARNING]
>
> Utilisez votre espace de données SaaS de production uniquement sur votre installation de production [!DNL Commerce] pour éviter les collisions de données. Sinon, vous risquez de polluer les données de votre site de production avec des données de test, ce qui entraîne des retards de déploiement. Par exemple, vos données de produit de production peuvent être écrasées par erreur des données d’évaluation, telles que les URL d’évaluation.

### Sélection ou création d’un projet SaaS {#createsaasenv}

Pour sélectionner ou créer un projet SaaS, demandez la clé d’API [!DNL Commerce] au propriétaire de licence [!DNL Commerce] pour votre magasin :

>[!NOTE]
>
> Si vous ne voyez pas la section **[!UICONTROL Commerce Services Connector]** dans la configuration [!DNL Commerce], vous devez installer les modules [!DNL Commerce] pour le [[!DNL Commerce] service](#availableservices) souhaité.

1. Dans la barre latérale _Admin_, accédez à **Système** > Services > **Connecteur de services Commerce**.

   Si vous ne voyez pas la section **[!UICONTROL Commerce Services Connector]** dans la configuration [!DNL Commerce], installez les modules [!DNL Commerce] correspondant au [[!DNL Commerce] service](#availableservices) souhaité. Vérifiez également que le package `magento/module-services-id` est installé.

1. Dans les sections _Clés d’API Sandbox_ et _Clés d’API de production_ , collez vos valeurs de clé.

   Les clés privées doivent inclure `----BEGIN PRIVATE KEY---` au début de la clé et `----END PRIVATE KEY----` à la fin de la clé privée.

1. Cliquez sur **Enregistrer**.

Tous les projets SaaS associés à vos clés apparaissent dans le champ **Projet** de la section **Identifiant SaaS** .

1. S’il n’existe aucun projet SaaS, cliquez sur **Créer un projet**. Ensuite, dans le champ **Projet** , saisissez un nom pour votre projet SaaS.

   Lorsque vous créez un projet SaaS, [!DNL Commerce] génère un ou plusieurs espaces de données SaaS en fonction de votre licence [!DNL Commerce] :
   - Adobe Commerce : un espace de données de production ; deux espaces de données de test uniquement. Sur les projets Cloud Pro comportant plusieurs environnements d’évaluation, vous pouvez demander des espaces de données de test supplémentaires pour chaque environnement d’évaluation en [envoyant une demande d’assistance](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket).
   - Magento Open Source : un espace de données de production ; aucun espace de données de test

1. Sélectionnez l’ **espace de données** à utiliser pour la configuration actuelle de votre magasin [!DNL Commerce].

>[!NOTE]
>
>Si vous disposez d’instances distinctes à intégrer aux services Commerce, [envoyez un ticket d’assistance](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket) pour demander un nouveau projet SaaS pour chaque instance supplémentaire. Une fois que la prise en charge a créé le projet SaaS, configurez l’intégration des services Commerce pour l’instance à l’aide de la même clé d’API et sélectionnez le nouveau projet SaaS pour l’espace de données.

>[!WARNING]
>
> Si vous générez de nouvelles clés dans la section Portail API de Mon compte, mettez immédiatement à jour les clés API dans la configuration Admin. Si vous générez de nouvelles clés sans les mettre à jour dans l’Admin, vos extensions SaaS ne fonctionnent plus et vous perdez des données importantes.

Pour modifier les noms de votre projet SaaS ou de votre espace de données, cliquez sur **Renommer** en regard de l’un ou l’autre. La modification du nom n’affecte pas votre service, car il s’agit uniquement d’un libellé qui vous permet d’identifier et de différencier les projets et les espaces de données.

## Organisation IMS (facultatif) {#organizationid}

Pour connecter votre instance Adobe Commerce à Adobe Experience Platform, connectez-vous à votre compte Adobe à l’aide de votre Adobe ID. Une fois connecté, l’organisation IMS associée à votre compte d’Adobe s’affiche dans cette section.

## Exportation des données SaaS

Lorsque votre instance [!DNL Commerce] se connecte correctement à [!DNL Commerce Services], le processus d’exportation des données SaaS exporte les données Commerce de votre serveur [!DNL Commerce] vers [!DNL Commerce SaaS Services] afin qu’elles puissent être synchronisées avec les services Commerce connectés. Dans l’administrateur, vous pouvez vérifier l’état de synchronisation à l’aide du [tableau de bord de Data Management](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard). Pour plus d’informations, consultez le [Guide d’exportation des données SaaS](../data-export/overview.md).
