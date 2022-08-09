---
title: '"[!DNL Catalog Service]"'
description: '"[!DNL Catalog Service] pour Adobe Commerce, vous pouvez récupérer le contenu des pages d’affichage de produit et des pages de liste de produits beaucoup plus rapidement que les requêtes Adobe Commerce GraphQL natives."'
source-git-commit: eb2242ac99cfaef4ed75936a1b5cc800cc451c83
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 0%

---


# [!DNL Catalog Service] pour Adobe Commerce

{{catalog-service-beta}}

Le [!DNL Catalog Service] pour l’extension Adobe Commerce, fournit des données de catalogue de modèles d’affichage enrichies (lecture seule) pour effectuer rapidement et intégralement le rendu des expériences de storefront liées aux produits, notamment :

* Pages Détails du produit
* Pages de liste de produits et de catégories
* Pages de résultats de recherche
* Carrousels de produit
* Pages de comparaison des produits
* Toute autre page qui effectue le rendu des données de produit, telles que les pages de panier, de commande et de liste de souhaits

Le [!DNL Catalog Service] uses [GraphQL](https://graphql.org/) pour demander et recevoir des données de produit. GraphQL est un langage de requête utilisé par un client frontal pour communiquer avec l’interface de programmation d’application (API) définie sur un serveur principal tel qu’Adobe Commerce. GraphQL est une méthode de communication courante, car elle est légère et permet à un intégrateur système de spécifier le contenu et l’ordre de chaque réponse.

Adobe Commerce possède deux systèmes GraphQL. Le système GraphQL de base fournit un large éventail de requêtes (opérations de lecture) et de mutations (opérations d’écriture) qui permettent à un acheteur d’interagir avec de nombreux types de pages, notamment un produit, un compte client, un panier, un passage en caisse, etc. Toutefois, les requêtes qui renvoient des informations sur les produits ne sont pas optimisées pour la vitesse. Le système GraphQL des services peut uniquement exécuter des requêtes sur les produits et les informations associées. Ces requêtes sont plus performantes que les requêtes principales similaires.

## Architecture

Le diagramme suivant montre les deux systèmes GraphQL :

![Diagramme d’architecture du catalogue](assets/catalog-service-architecture.png)

Dans le système GraphQL principal, le PWA envoie une demande à l’application Commerce, qui reçoit chaque demande, la traite, peut-être en envoyant une demande via plusieurs sous-systèmes, puis renvoie une réponse au storefront. Ce aller-retour peut ralentir le chargement des pages, ce qui peut entraîner des taux de conversion plus faibles.

[!DNL Catalog Service] envoie des requêtes à une passerelle GraphQL distincte. Le service accède à une base de données distincte qui contient les détails du produit et les informations connexes, telles que les attributs de produit, les variantes, les prix et les catégories. Le service maintient la synchronisation de la base de données avec Adobe Commerce par le biais de l’indexation.
Comme le service contourne la communication directe avec l’application, il peut réduire la latence du cycle de demande et de réponse.

>[!NOTE]
>
>La passerelle est destinée à une intégration ultérieure avec [!DNL Live Search] et [!DNL Product Recommendations]. Dans cette version, vous pouvez accéder à [!DNL Catalog Service] et les requêtes de recherche en direct du même point de terminaison, si vous disposez d’une clé de licence valide pour les deux produits. Toutefois, les requêtes des deux produits ne partagent actuellement aucune donnée de réponse.

Les systèmes GraphQL de base et de service ne communiquent pas directement entre eux. Vous accédez à chaque système à partir d’une URL différente et les appels nécessitent des informations d’en-tête différentes. Les deux systèmes GraphQL sont conçus pour être utilisés ensemble. Le [!DNL Catalog Service] Le système GraphQL augmente le système de base pour accélérer l’expérience du storefront de produits.

Vous pouvez éventuellement implémenter [Maillage d’API pour Adobe Developer App Builder](https://developer.adobe.com/graphql-mesh-gateway/) pour intégrer les deux systèmes GraphQL Adobe Commerce à des API privées et tierces, ainsi qu’à d’autres interfaces logicielles à l’aide d’Adobe Developer. L’impression peut être configurée pour s’assurer que les appels acheminés vers chaque point de terminaison contiennent les informations d’autorisation correctes dans les en-têtes.

## Implémentation

Le processus d’installation nécessite la configuration de la fonction [Connecteur Commerce Services](../landing/saas.md). Une fois cette opération effectuée, l’étape suivante consiste pour un intégrateur de systèmes à mettre à jour le code storefront afin d’incorporer la variable [!DNL Catalog Service] requêtes. Tous [!DNL Catalog Service] les requêtes sont acheminées vers la passerelle GraphQL. L’URL est fournie pendant le processus d’intégration.

[Périphériques Adobe Commerce](https://devdocs.magento.com/catalog-service/index.html) décrit les différences entre le noyau et [!DNL Catalog Service] requêtes. Des informations de référence pour chaque requête sont également incluses.
