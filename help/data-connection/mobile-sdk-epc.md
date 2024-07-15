---
title: Intégration du SDK Adobe Experience Platform Mobile à Commerce
description: Découvrez comment utiliser le SDK Mobile Adobe Experience Platform avec votre vitrine Commerce personnalisée ou sans interface.
role: Admin, Developer
feature: Personalization, Integration, Eventing
exl-id: d1340b15-e7de-42b5-ad64-d4c31f0db029
source-git-commit: 593e92ebf890bd7d9bfef1cd13be727ca6be172b
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 0%

---

# Intégration du SDK Adobe Experience Platform Mobile à Commerce

>[!IMPORTANT]
>
>Le SDK Mobile Adobe Experience Platform pour iOS prend en charge iOS 11 ou version ultérieure.

L’intégration du [SDK Mobile Adobe Experience Platform](https://developer.adobe.com/client-sdks/home/) avec l’application mobile Commerce permet aux marchands d’envoyer des [données d’événement](events.md) Commerce à la périphérie Experience Platform.

Lorsque les données d’événement Commerce sont disponibles à la périphérie, elles sont accessibles par d’autres applications Adobe Experience Cloud. Par exemple, vous pouvez utiliser les données pour créer des audiences dans Real-Time CDP, puis [utiliser ces audiences](https://experienceleague.adobe.com/docs/commerce-admin/customers/audience-activation.html) pour personnaliser votre application mobile Commerce.

## Configuration

Pour commencer à utiliser le SDK Mobile Adobe Experience Platform avec Commerce, installez et configurez le SDK dans l’Experience Platform. Finalisez ensuite votre configuration dans Commerce.

### Experience Platform

1. Découvrez les fonctionnalités des applications mobiles en consultant le [tutoriel Adobe Experience Cloud dans les applications mobiles](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/overview.html).

1. [Installez et configurez](https://developer.adobe.com/client-sdks/documentation/getting-started/) le SDK dans Experience Platform.

   >[!NOTE]
   >
   >Le schéma que vous créez et configurez dans l’Experience Platform est le même que celui que vous utilisez dans le code de l’application dans votre application mobile Commerce.

### Commerce

Après avoir terminé la configuration du SDK pour Experience Platform, ajoutez la configuration du SDK à Commerce.

1. Pour envoyer des données d’événement Commerce à l’Experience Platform via le SDK, vous devez fournir un schéma XDM dans le code de l’application. Ce schéma doit correspondre au schéma [configuré](https://developer.adobe.com/client-sdks/home/getting-started/set-up-schemas-and-datasets/) du SDK dans l’Experience Platform.

   L’exemple suivant montre comment effectuer le suivi de l’événement `web.webpagedetails.pageViews` et définir le `identityMap` à l’aide du champ de courrier électronique.

   ```swift
   let stateName = "luma: content: ios: us: en: home"
   var xdmData: [String: Any] = [
       "eventType": "web.webpagedetails.pageViews",
       "web": [
           "webPageDetails": [
               "pageViews": [
                   "value": 1
               ],
               "name": "Home page"
           ]
       ]
   ]
   
   let experienceEvent = ExperienceEvent(xdm: xdmData)
   Edge.sendEvent(experienceEvent: experienceEvent)
   
   // Adobe Experience Platform - Update Identity
   
   let emailLabel = "mobileuser@example.com"
   
   let identityMap: IdentityMap = IdentityMap()
   identityMap.add(item: IdentityItem(id: emailLabel), withNamespace: "Email")
   Identity.updateIdentities(with: identityMap)
   ```

1. Connectez-vous à l’environnement de Commerce Cloud.

   Dans les paramètres de création de votre projet, ajoutez l’URL au point de terminaison Commerce GraphQL. Par exemple :

   - Débogage : http://_debug_.commercesite.cloud/graphql/
   - Version : http://_release_.commercesite.cloud/graphql/

1. Pour récupérer des données à partir des points de terminaison GraphQL Commerce, générez d’abord les fichiers et répertoires nécessaires dans votre projet à l’aide du [générateur de code Apollo](https://www.apollographql.com/docs/ios/).

   1. Dans le répertoire de votre projet, [installez](https://www.apollographql.com/docs/ios/get-started#1-install-the-apollo-frameworks) Apollo iOS.

   1. [Initialisez](https://www.apollographql.com/docs/ios/code-generation/codegen-cli/#initialize) l’interface de ligne de commande Apollo Codegen.

      Cela crée un fichier `apollo-codegen-configuration.json`.

   1. Générez les fichiers et répertoires GraphQL nécessaires dans votre projet en remplaçant le contenu du fichier `apollo-codegen-configuration.json` par ce qui suit :

      ```json
      {
      "schemaName" : "MagentoAPI",
      "input" : {
          "operationSearchPaths" : [
          "**/*.graphql"
          ],
          "schemaSearchPaths" : [
          "**/*.graphqls"
          ]
      },
      "output" : {
          "testMocks" : {
          "none" : {
          }
          },
          "schemaTypes" : {
          "path" : "../MagentoAPI",
          "moduleType" : {
              "swiftPackageManager" : {
              }
          }
          },
          "operations" : {
          "inSchemaModule" : {
          }
          }
      },
      "schemaDownloadConfiguration": {
          "downloadMethod": {
              "introspection": {
                  "endpointURL": "http://magento24.com/graphql/",
                  "httpMethod": {
                      "POST": {}
                  },
                  "includeDeprecatedInputValues": false,
                  "outputFormat": "SDL"
              }
          },
          "downloadTimeout": 60,
          "headers": [],
          "outputPath": "magento.graphqls"
      }
      }
      ```

   1. [Récupérer](https://www.apollographql.com/docs/ios/code-generation/codegen-cli/#fetch-schema) le schéma GraphQL Commerce.

      Assurez-vous que le chemin d’accès est au fichier `./apollo-codegen-config.json`, qui contient la référence au schéma GraphQL Commerce.

   1. [Générer](https://www.apollographql.com/docs/ios/code-generation/codegen-cli/#generate) le code source.

      Assurez-vous que le chemin d’accès est au fichier `./apollo-codegen-config.json`, qui contient les informations de configuration pour générer les fichiers et répertoires nécessaires.

   1. Dans le dossier **GraphQLGenerated** nouvellement créé, ajoutez ou modifiez des types GraphQL. Par exemple, vous pouvez ajouter un type `DynamicBlocks.graphql` avec le contenu suivant :

      ```graphql
      query dynamicBlocks($input: DynamicBlocksFilterInput){
          dynamicBlocks(input: $input)
          {
              items {
                  content {
                      html
                  }
              }
          }
      }
      ```

   Vous avez maintenant intégré le SDK Mobile Adobe Experience Platform à votre application mobile Commerce. Les données d’événement s’enchaînent de l’application au bord Experience Platform.

## Comment distinguer les événements Commerce générés des applications mobiles

Tous les [événements](events.md) contiennent un champ appelé `channel`. Le champ `channel` contient `channel._id` et `channel._type` qui, pour un storefront Luma, possèdent respectivement des valeurs d’espace de noms `"https://ns.adobe.com/xdm/channels/web"` et `"https://ns.adobe.com/xdm/channel-types/web"`. Toutefois, pour une vitrine mobile, les valeurs de l’espace de noms sont `"https://ns.adobe.com/xdm/channels/mobile-app"` et `"https://ns.adobe.com/xdm/channel-types/mobile"` respectivement.

## Étapes suivantes

Pour savoir comment récupérer des audiences Real-Time CDP à partir de votre application mobile Commerce afin d’informer les règles de prix du panier, les blocs dynamiques et les règles de produit associées, voir [Audience Activation](https://experienceleague.adobe.com/docs/commerce-admin/customers/audience-activation.html#retrieve-audiences-using-the-adobe-experience-platform-mobile-sdk).
