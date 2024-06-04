---
title: Traitement de niveau 2 et de niveau 3
description: Niveaux de traitement des paiements par carte dans [!DNL Payment Services] transactions.
role: Admin
feature: Payments
source-git-commit: d1379bb108f2259051641a7bf77cd8b459fd9cbf
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---


# Traitement de niveau 2 et de niveau 3

Trois niveaux de traitement des cartes sont disponibles via [!DNL Payment Services]:

* Le niveau 1 est le plus courant et nécessite moins d’informations. Il entraîne donc des frais d’échange plus élevés que les transactions traitées avec les données de niveau 2 ou 3, qui sont généralement liées aux cartes de crédit d’entreprise et d’achat.

* Avec le niveau 2 et le niveau 3, [!DNL Payment Services] les clients qui acceptent un grand nombre de transactions par carte d’achat ou par carte d’entreprise et qui bénéficient d’un taux de traitement plus élevé peuvent bénéficier d’un taux de traitement plus faible en autorisant [!DNL Payment Services] pour envoyer plus d’informations sur une transaction. Si la transaction est admissible, conformément aux exigences du réseau de cartes, le marchand peut alors recevoir un taux de traitement plus faible pour une transaction particulière.

>[!NOTE]
>
>Les tarifs de niveau 2 et 3 s&#39;appliquent uniquement aux transactions Visa et MasterCard. American Express ne propose que des tarifs de niveau 2. Discover ne propose pas de tarifs de niveau 2 ni de niveau 3. Voir [traitement des paiements](https://developer.paypal.com/docs/checkout/advanced/processing/){target=_blank} pour plus d’informations, voir la documentation destinée aux développeurs PayPal .

Voir [Présentation d’IC++?](https://www.paypal.com/us/brc/article/what-is-interchange-plus-plus){target=_blank} dans la documentation destinée aux développeurs de PayPal pour plus d’informations.

Les données de traitement de niveau 2 et de niveau 3 permettent aux commerçants de réduire leur prix IC++ s’ils fournissent des détails supplémentaires sur l’achat, ce qui réduit les risques du processeur et apporte des avantages :

* Les gros clients payeront moins en fournissant ces données de traitement.

* Les clients sont moins susceptibles de rencontrer des situations frauduleuses, car les commandes comportent plus d’informations.

Cependant, les réseaux de cartes, comme Visa et Mastercard, déterminent finalement si une transaction est admissible pour le traitement de niveau 2 ou 3 :

* Les données de niveau 2 contiennent des informations supplémentaires, telles que le montant de la taxe pour la commande, le code client ou le numéro du bon de commande.

* Les données de niveau 3 sont des informations plus détaillées sur la vente, ce qui permet de se qualifier pour des taux d’échange encore plus faibles par rapport au niveau 2. Les données de niveau 3 contiennent des informations telles qu’une description de l’article acheté, la quantité d’unités achetées, l’unité de mesure des articles commandés et d’autres détails spécifiques.

[!DNL Payment Services] collecte ces données et fournit un reporting détaillé de vos transactions de paiement.

## les transactions de paiement par carte de niveau 2 et de niveau 3 dans les [!DNL Payment Services]

Pour être admissible au traitement de niveau 2 ou 3, les marchands doivent envoyer les informations précédentes, bien que ce soient les réseaux de cartes qui déterminent finalement le niveau auquel une transaction peut être admissible lors de son traitement.

Voir [FAQ sur le traitement des paiements](https://www.paypal.com/us/cshelp/article/ts2278?_ga=1.131773126.875104296.1712843492){target=_blank} dans la documentation destinée aux développeurs de PayPal pour plus d’informations.

Le traitement des niveaux 2 et 3 est désactivé par défaut pour les [!DNL Payment Services] commerçants au niveau du magasin.

Le traitement des niveaux 2 et 3 est disponible si vous utilisez déjà la tarification IC++. Pour activer cette fonctionnalité, vous pouvez le faire via le [Interface de ligne de commande (CLI)](configure-cli.md).

>[!IMPORTANT]
>
>Si vous avez des questions, contactez votre [!DNL Payment Services] gestionnaire de compte.
