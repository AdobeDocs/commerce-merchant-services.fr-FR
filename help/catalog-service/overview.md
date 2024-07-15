---
title: '[!DNL Catalog Service]'
description: '[!DNL Catalog Service] pour Adobe Commerce permet de récupérer le contenu des pages d’affichage de produit et des pages de liste de produits beaucoup plus rapidement que les requêtes GraphQL natives.'
exl-id: 266faca4-6a65-4590-99a9-65b1705cac87
recommendations: noCatalog
source-git-commit: 7293914fab34381deb5bc841d147371f9f3470a5
workflow-type: tm+mt
source-wordcount: '918'
ht-degree: 0%

---

# [!DNL Catalog Service] pour Adobe Commerce

L’extension [!DNL Catalog Service] pour Adobe Commerce fournit des données de catalogue de modèles d’affichage enrichies (lecture seule) pour effectuer rapidement et intégralement le rendu des expériences de storefront liées aux produits, notamment :

* Pages Détails du produit
* Pages de liste de produits et de catégories
* Pages de résultats de recherche
* Carrousels de produit
* Pages de comparaison des produits
* Toute autre page qui effectue le rendu des données de produit, telles que les pages de panier, de commande et de liste de souhaits

[!DNL Catalog Service] utilise [GraphQL](https://graphql.org/) pour demander et recevoir des données de produit. GraphQL est un langage de requête utilisé par un client frontal pour communiquer avec l’API (interface de programmation d’application) définie sur un serveur principal tel qu’Adobe Commerce. GraphQL est une méthode de communication courante, car elle est légère et permet à un intégrateur système de spécifier le contenu et l’ordre de chaque réponse.

Adobe Commerce possède deux systèmes GraphQL. Le système GraphQL principal fournit un large éventail de requêtes (opérations de lecture) et de mutations (opérations d’écriture) qui permettent à un acheteur d’interagir avec de nombreux types de pages, notamment un produit, un compte client, un panier, un passage en caisse, etc. Toutefois, les requêtes qui renvoient des informations sur les produits ne sont pas optimisées pour la vitesse. Le système GraphQL des services peut uniquement exécuter des requêtes sur les produits et les informations associées. Ces requêtes sont plus performantes que les requêtes principales similaires.

Les clients [!DNL Catalog Service] peuvent utiliser le nouvel [indexeur de prix SaaS](../price-index/price-indexing.md), qui permet d’accélérer les mises à jour des changements de prix et le temps de synchronisation.

## Architecture

Le diagramme suivant illustre les deux systèmes GraphQL :

![Diagramme d’architecture de catalogue](assets/catalog-service-architecture.png)

Dans le système GraphQL principal, le PWA envoie une demande à l’application Commerce, qui reçoit chaque demande, la traite, peut-être en envoyant une demande par l’intermédiaire de plusieurs sous-systèmes, puis renvoie une réponse au storefront. Ce aller-retour peut ralentir le temps de chargement des pages, ce qui peut entraîner des taux de conversion plus faibles.

[!DNL Catalog Service] est une passerelle des services de Storefront. Le service accède à une base de données distincte qui contient les détails du produit et les informations connexes, telles que les attributs de produit, les variantes, les prix et les catégories. Le service maintient la synchronisation de la base de données avec Adobe Commerce par le biais de l’indexation.
Comme le service contourne la communication directe avec l’application, il peut réduire la latence du cycle de demande et de réponse.

Les systèmes GraphQL principaux et de service ne communiquent pas directement entre eux. Vous accédez à chaque système à partir d’une URL différente et les appels nécessitent des informations d’en-tête différentes. Les deux systèmes GraphQL sont conçus pour être utilisés ensemble. Le système [!DNL Catalog Service] GraphQL augmente le système principal pour accélérer l’expérience du storefront de produits.

Vous pouvez éventuellement mettre en oeuvre [API Mesh for Adobe Developer App Builder](https://developer.adobe.com/graphql-mesh-gateway/) pour intégrer les deux systèmes Adobe Commerce GraphQL avec des API privées et tierces et d’autres interfaces logicielles à l’aide d’Adobe Developer. L’impression peut être configurée pour s’assurer que les appels acheminés vers chaque point de terminaison contiennent les informations d’autorisation correctes dans les en-têtes.

## Détails architecturaux

Les sections suivantes décrivent certaines des différences entre les deux systèmes GraphQL.

### Gestion des schémas

Comme le service de catalogue fonctionne comme un service, les intégrateurs n’ont pas à se soucier de la version sous-jacente de Commerce. La syntaxe des requêtes est la même pour toutes les versions. En outre, le schéma est cohérent pour tous les commerçants. Cette cohérence facilite l’établissement de bonnes pratiques et accroît considérablement la réutilisation des widgets storefront.

### Simplification des types de produits

Le schéma réduit la diversité des types de produits à deux cas d’utilisation :

* Les produits simples sont ceux qui sont définis avec un seul prix et une seule quantité. Le service de catalogue mappe les types de produits de carte-cadeau, simples, virtuels, téléchargeables et à `simpleProductViews`.

* Les produits complexes sont constitués de plusieurs produits simples. Les composants produits simples peuvent avoir des prix différents. Un produit complexe peut également être défini de sorte que l’acheteur puisse spécifier la quantité de produits simples de composant. Le service de catalogue mappe les types de produits configurables, regroupés et regroupés à `complexProductViews`.

Les options de produits complexes sont unifiées et distinguées par leur comportement, et non par leur type. Chaque valeur d’option représente un produit simple. Cette valeur d’option a accès aux attributs de produit simples, y compris le prix. Lorsque l’acheteur sélectionne toutes les options d’un produit complexe, la combinaison des options sélectionnées pointe vers un produit simple spécifique. Le produit simple reste ambigu jusqu’à ce que l’acheteur sélectionne une valeur pour toutes les options disponibles.

### Prix

Les produits simples représentent l’unité de vente de base qui a un prix. [!DNL Catalog Service] calcule le prix normal avant remises ainsi que le prix final après remises. Les calculs de tarifs peuvent inclure des taxes fixes sur les produits. Elles excluent les promotions personnalisées.

Un produit complexe n’a pas de prix fixe. Au lieu de cela, le service de catalogue renvoie les prix de l&#39;utilisation simple liée. Par exemple, un commerçant peut initialement attribuer les mêmes prix à toutes les variantes d’un produit configurable. Si certaines tailles ou couleurs sont impopulaires, le marchand peut réduire les prix de ces variantes. Ainsi, le prix du produit complexe (configurable) affiche au début une gamme de prix, reflétant le prix des variantes standard et impopulaires. Une fois que l’acheteur a sélectionné une valeur pour toutes les options disponibles, le storefront affiche un seul prix.

Le service de catalogue garantit des mises à jour et des calculs de prix précis en prenant en charge les prix avec des valeurs élevées (jusqu’à 16 chiffres) et une précision décimale élevée (jusqu’à 4 décimales).

>[!NOTE]
>
> Les clients Commerce disposant de [!DNL Catalog Service] peuvent tirer parti des modifications de prix plus rapides et du temps de synchronisation sur leurs sites web avec l’ [ indexeur de prix SaaS](../price-index/price-indexing.md).

## Implémentation

Le processus d’installation nécessite la configuration du [connecteur Commerce Services](../landing/saas.md). Une fois cette opération effectuée, l’étape suivante consiste pour un intégrateur de systèmes à mettre à jour le code storefront afin d’incorporer les requêtes [!DNL Catalog Service]. Toutes les requêtes [!DNL Catalog Service] sont acheminées vers la passerelle GraphQL. L’URL est fournie pendant le processus d’intégration.
