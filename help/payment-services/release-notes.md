---
title: "[!DNL Payment Services] Notes de mise à jour"
description: Consultez les notes de mise à jour pour plus d’informations sur toutes les versions de  [!DNL Payment Services]  .
exl-id: 104aa2c7-7735-4ac2-8ed1-a03cd9911273
feature: Payments, Release Notes
source-git-commit: 153e6a82134a34737529f4e1a135eb7803b20e05
workflow-type: tm+mt
source-wordcount: '2968'
ht-degree: 0%

---


# Notes de mise à jour

Ces notes de mise à jour décrivent la version initiale de [!DNL Payment Services] et incluent :

![New](../assets/new.svg) Nouvelles fonctionnalités
![Problème corrigé](../assets/fix.svg) Correctifs et améliorations
![Problème connu](../assets/bug.svg) Problèmes connus

Pour les modifications et correctifs de fonctionnalités publiés en dehors de la version de publication standard des fonctionnalités, consultez les sections _Mises à jour du service hébergé_ .

Pour en savoir plus sur les prochaines versions, la prise en charge des produits et les versions d’Adobe Commerce qui prennent en charge l’extension [!DNL Payment Services], consultez les rubriques [Calendrier des versions](https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/schedule) et [Disponibilité des produits](https://experienceleague.adobe.com/en/docs/commerce-operations/release/product-availability) d’Adobe Commerce.

## Mises à jour du service hébergé

Ces notes de mise à jour décrivent les modifications et correctifs de fonctionnalités qui se sont produits et qui ont été publiés en dehors des versions standard des fonctionnalités pour le service hébergé.

+++Mises à jour du service hébergé

_30 août 2024_

![Nouveau problème](../assets/new.svg)<!-- Issue PAY-5658 --> Désormais, les vendeurs peuvent filtrer les transactions selon les détails du paiement dans le [rapport sur les transactions](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/transactions.html) pour obtenir des données plus détaillées et plus précises sur les méthodes de paiement.

_15 juillet 2024_

![Nouveau problème](../assets/new.svg)<!-- Issue PAY-5571 --> Désormais, les vendeurs peuvent filtrer les transactions par e-mail client Commerce dans le [rapport sur les transactions](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/transactions.html). Entrez l’adresse électronique du client pour filtrer les transactions relatives à cet adresse électronique spécifique.

_9 juillet 2024_

![Nouveau problème](../assets/new.svg)<!-- Issue PAY-5488 --> Désormais, les marchands peuvent afficher l’ID de client Commerce sous la forme d’une colonne dans le [rapport sur les transactions](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/transactions.html) pour identifier les transactions qu’un client particulier a effectuées. En outre, les marchands peuvent filtrer le rapport des transactions selon cet ID de client Commerce pour les commandes associées.

_5 mars 2024_

![Problème corrigé](../assets/fix.svg)<!-- Issue PAY-5252 --> Désormais, les marchands peuvent copier des données des grilles du tableau de bord en sélectionnant le contenu d’une seule cellule.

_10 octobre 2023_

![Nouveau problème](../assets/fix.svg)<!-- Issue PAY-4888 --> Désormais, les vendeurs peuvent filtrer les transactions de carte de crédit et de débit selon les quatre derniers chiffres du numéro de carte dans le [rapport sur les transactions](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/transactions.html).

_12 juillet 2023_

![Correction d’un problème](../assets/fix.svg)<!-- Issue PAY-4587 --> Un problème introduit dans la version [!DNL Payment Services] 2.1.0 qui empêchait les vides d’autorisation placés par les versions précédentes de l’extension est désormais résolu. Les commerçants qui utilisent n’importe quelle version de [!DNL Payment Services] peuvent annuler des autorisations.

_9 juin 2023_

![Nouveau](../assets/new.svg)<!-- Issue PAY-4288 --> Désormais, les vendeurs peuvent [ configurer _uniquement_ boutons de paiement PayPal](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html#use-only-paypal-payment-buttons)—et _non_ utiliser l’option de paiement par carte de crédit PayPal. Cela permet aux commerçants de proposer diverses options de paiement, notamment des boutons de paiement Venmo et PayPal, et d’utiliser un fournisseur de carte de crédit existant au lieu de l’option de paiement par carte de crédit PayPal.

![Nouveau](../assets/new.svg)<!-- Issue PAY-4050 --> Ajout d’une [ vue de visualisation des données](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html#order-payment-status-data-visualization-view), qui s’affiche sur la page d’accueil du service de paiement, pour le rapport d’état du paiement de la commande.

![Correction d’un problème](../assets/fix.svg)<!-- Issue PAY-4486--> Auparavant, le bouton PayPal PayLater ne s’affichait pas dans le passage en caisse pour les commerçants britanniques. Ce problème est résolu.

![Problème corrigé :](../assets/fix.svg)<!-- Issue PAY-4485--> Les vues de visualisation des données de rapport s’affichent désormais sur la [!DNL Payment Services] page d’accueil lorsque[!DNL Payment Services] est désactivé.

_25 janvier 2023_

![Problème connu](../assets/bug.svg)<!-- Issue PAY-4102 --> Les nouvelles installations de [!DNL Payment Services] ne peuvent pas configurer les services Commerce, ce qui rend [!DNL Payment Services] inutilisable. Pour résoudre ce problème, mettez à jour votre extension [!DNL Payment Services] vers la version 1.5.3.

_12 septembre 2022_

![Nouveau](../assets/new.svg)<!-- Issue PAY-3705 --> `increment_id` est désormais disponible pour la réconciliation des paiements dans les systèmes ERP externes. Il est propagé vers les [`custom_id` _et_ `invoice_id`](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/data.html#reconcile-with-erp-system), visibles dans le webhook PayPal et dans le détail de l’activité du commerce pour un paiement.

_31 août 2022_

![Correction d’un problème ](../assets/fix.svg)<!-- Issue PAY-3629 --> Lorsqu’un nouveau commerçant accède pour la première fois à l’accueil [!DNL Payment Services], la page se charge désormais immédiatement pour afficher le contenu au lieu de devoir actualiser la page.

_9 août 2021_

![Nouveau](../assets/new.svg)<!-- Issue PAY-3420 --> Le paiement Apple est désormais disponible sous la forme d’un bouton PayPal Smart. Cette [option de paiement](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-options.html#apple-pay-button) permet aux clients d’utiliser la fonctionnalité d’identifiant tactile de leur appareil iOS ou macOS pour sélectionner Apple Pay. Apple Pay traite le paiement à l’aide des informations d’identification de paiement de carte de crédit et de débit stockées sur l’appareil.

_28 juin 2021_

![Nouveau](../assets/new.svg)<!-- Issue PAY-1720 --> Les différends relatifs aux commandes en magasin sont désormais disponibles dans le [rapport sur l&#39;état des paiements des commandes](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html#view-disputes). Vous pouvez résoudre les conflits en accédant directement au centre de résolution PayPal à partir de [!DNL Payment Services].

![Nouvelles](../assets/new.svg)<!-- Issue PAY-2854 --> Les améliorations de l’expérience utilisateur de l’accueil [!DNL Payment Services] incluent la possibilité de modifier une configuration au niveau de l’héritage actuel et des améliorations de l’affichage de l’en-tête et de la navigation.

![Nouveau](../assets/new.svg)<!-- Issue PAY-2854 --> Vous pouvez désormais voir des avertissements lorsque vous passez du mode sandbox au mode de production et lorsque vous tentez de quitter une vue avec des mises à jour qui n’ont pas été enregistrées.

![Nouveau](../assets/new.svg)<!-- Issue PAY-2761 --> Vous pouvez désormais personnaliser les données qui s’affichent dans le [rapport État des paiements de commande](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html#show-and-hide-columns) et le [rapport sur les paiements](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/payouts.html#show-and-hide-columns) en affichant ou en masquant les colonnes à l’aide du contrôle Paramètres de colonne.

+++

## v2.8.0

_13 septembre 2024_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![New](../assets/new.svg)<!-- PAY-5499 --> [!DNL Payment Services] prend désormais en charge l’envoi d’informations de numéro de suivi à PayPal lorsqu’un [ numéro de suivi est entré](track-shipment.md) dans Adobe Commerce.

![Fix](../assets/fix.svg)<!-- PAY-5626 --> [!DNL Payment Services] a optimisé le processus de demande au registre du commerce lorsque les clients visitent la page de passage en caisse de Commerce. Auparavant, des demandes distinctes étaient effectuées pour chaque mode de paiement (champs hébergés, paiement Google, paiement Apple et boutons intelligents). Cette amélioration réduit le nombre d’appels, améliore les performances et l’efficacité pendant le processus de passage en caisse.

![Fix](../assets/fix.svg)<!-- PAY-5645 --> [!DNL Payment Services] empêche désormais la fenêtre contextuelle Payer PayPal/Google de s’ouvrir si l’acheteur n’a pas accepté que le marchand crée des conditions générales personnalisées sur la page de passage en caisse.

![Fix](../assets/fix.svg)<!-- PAY-5648 -->  [!DNL Payment Services] a résolu un problème lié à la ventilation des taxes par ligne sur le portail PayPal. Si le coût d’expédition d’une commande est associé à une taxe, celle-ci sera incluse dans le coût d’expédition et sera visible de cette manière dans les détails des éléments de ligne affichés sur le portail PayPal.

## v2.7.0

_2 août 2024_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![New](../assets/new.svg)<!-- PAY-4844 --> [!DNL Payment Services] prend désormais en charge les [données d’élément de ligne au niveau de la commande](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/payment-services/payments-checkout/manage/line-items). Cette fonctionnalité permet aux marchands d’afficher des informations détaillées sur les articles d’une commande, telles que les détails du produit, la quantité et le prix (y compris la taxe de vente, les remises et d’autres informations pertinentes).

![New](../assets/new.svg)<!-- PAY-5380 --> [!DNL Payment Services] améliore l’expérience [Configuration dans l’Admin](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/payment-services/configure/configure-admin#general-configuration) pour les vendeurs afin d’offrir un processus d’intégration plus simple et plus intuitif. Cette fonctionnalité permet aux commerçants de réinitialiser leurs [!DNL Payment Services] ID.

![New](../assets/new.svg)<!-- PAY-5255 --> [!DNL Payment Services] comprend une [ notification d’échec du paiement ](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/point-of-purchase/checkout/checkout-payment-failed-emails). Cette fonctionnalité fournit des notifications en temps quasi réel d’échecs de paiement aux marchands. Vous pouvez donc enregistrer les commandes en contactant l’acheteur et en améliorant potentiellement la résolution des problèmes.

![Correctif](../assets/fix.svg)<!-- PAY-5469 --> Correction d’un problème en raison duquel la fenêtre contextuelle **Paye Google était bloquée par Safari**. Les acheteurs peuvent désormais effectuer leurs transactions de paiement payant Google sur Safari.

![Correctif](../assets/fix.svg)<!-- PAY-5492 --> Correction d’un problème qui survenait lorsqu’un commerçant ajoutait des termes et des conditions personnalisés à la page de passage en caisse. Au cours d’un [passage en caisse express](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options#standard-vs-advanced-payments-experience), un acheteur peut désormais accepter ces conditions générales pour terminer le passage en caisse sans problème.

![Correctif](../assets/fix.svg)<!-- PAY-5532 --> Amélioration des fonctionnalités de nettoyage en magasin (ISPU) avec **InstantPurchase**. Les **méthodes de remise ISPU** ne s’affichent plus lorsqu’un acheteur commande avec **InstantPurchase**.

![Correctif](../assets/fix.svg)<!-- PAY-5606 --> Correction d’un problème dans le sélecteur de pays **Page de configuration** qui se produisait lorsque le pays du commerçant était défini sur **Allemagne**.

## v2.6.0

_4 juin 2024_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![New](../assets/new.svg)<!-- PAY-4877 --> Maintenant, [!DNL Payment Services] prend en charge les [fonctionnalités de tarification L2/L3](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/levels-card-payment-transactions.html). Cette fonctionnalité est disponible uniquement pour les clients [!DNL Payment Services] dont la tarification IC++ est activée. Si vous souhaitez utiliser les données de traitement L2/L3 pour [!DNL Payment Services], contactez votre gestionnaire de compte [!DNL Payment Services].

![Fix](../assets/fix.svg)<!-- PAY-5455 -->[!DNL Payment Services] permet d’activer Apple Pay directement à partir de l’extension sans télécharger ni héberger le [fichier d’association de domaine](https://developer.paypal.com/docs/checkout/apm/apple-pay/#register-your-live-domain).

## v2.5.0

_23 avril 2024_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Fix](../assets/fix.svg)<!-- Issue PAY-5396 -->[!DNL Payment Services] prend désormais en charge [les instructions Adobe Commerce pour le `--db-prefix` paramètre](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/advanced#install-from-the-command-line) pour Adobe Commerce versions 2.4.7 et ultérieures.

## v2.4.3

_16 avril 2024_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Correctif](../assets/fix.svg)<!-- Issue PAY-5106 --> Correction d’un problème qui renseignait incorrectement les totaux des montants de commande lors de l’extraction entre PayPal et Adobe Commerce. Désormais, les vendeurs peuvent s’assurer que les totaux des montants de commande sont corrects lors du placement d’une commande.

## v2.4.2

_11 avril 2024_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg)<!-- Issue xxx --> Prise en charge d’Adobe Commerce 2.4.7.

## v2.4.1

_4 avril 2024_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Fix](../assets/fix.svg)<!-- PAY-5322 --> Correction d’un problème de compatibilité PCI avec les nouvelles versions d’Adobe Commerce. Désormais, [!DNL Payment Services] est adapté aux conditions de passage en caisse dans Adobe Commerce en tant qu’option de paiement.

![Fix](../assets/fix.svg)<!-- PAY-5323 --> PayLater et Venmo s’affichent correctement dans Adobe Commerce. Correction d’une erreur qui empêchait l’administrateur d’afficher les options de basculement PayLater et Venmo .

## v2.4.0

_20 mars 2024_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg)<!-- PAY-4868 --> Les vendeurs peuvent [ configurer le paiement Google tout au long de l’expérience d’achat ](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html), comme les autres boutons de paiement dans [!DNL Payment Services] par l’intermédiaire de l’administrateur.

![New](../assets/new.svg)<!-- PAY-4381 --> [ Les services de paiement prennent en charge le paiement Google par le biais de GraphQL](https://developer.adobe.com/commerce/webapi/graphql/payment-services/), ce qui permet aux commerçants d’avoir une expérience Commerce sans interface avec le mode de paiement Google.

![Nouveau](../assets/new.svg)<!-- PAY-4878 --> Désormais, la fonction de paiement de base [!DNL Payment Services] est fournie pour les marchands Adobe Commerce et Magento Open Source.[!DNL Payment Services] peut désormais prendre en charge les commerçants avec des entreprises dans l’une des 200 régions du monde.[!DNL Payment Services] Le paiement de base fournit les options de débit/crédit, PayPal, Venmo (le cas échéant) et PayLater (le cas échéant) dans une intégration en libre-service.

![Correctif](../assets/fix.svg)<!-- PAY-5291 --> La réception de la confirmation de paiement pour certaines transactions peut être retardée. Dans ce cas, les vendeurs peuvent désormais obtenir un état de paiement mis à jour pour une commande. [Les services de paiement détectent l’état en attente d’une transaction de paiement](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html) dans une commande en détectant les transactions en attente et en surveillant de manière proactive ces transactions et en mettant à jour lorsque l’état en attente a été capturé.

## v2.3.4

_1 mars 2024_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![New](../assets/new.svg)<!-- PAY-5244 --> Correction de la compatibilité de passage en caisse asynchrone.

![Fix](../assets/fix.svg)<!-- PAY-5253 --> Correction d’une erreur qui empêchait la suppression d’un jeton de coffre non appartenant à [!DNL Payment Services].

## v2.3.3

_14 février 2024_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg)<!-- PAY-5048 --> Prise en charge de PHP 8.3

![Fix](../assets/fix.svg)<!-- PAY-5048 --> Correction d’une erreur avec l’indicateur `is_deleted`. Désormais, les commandes n’échouent pas en raison de l’état `Rejected` envoyé à partir de l’extension.

## v2.3.2

_26 janvier 2024_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Correction](../assets/fix.svg)<!-- PAY-5183 --> Correction de problèmes de performances REST/GraphQL. Désormais, le bouton de carte de crédit s’affiche lorsqu’il est récupéré via l’API.

## v2.3.1

_7 décembre 2023_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg)<!-- PAY-5047 --> La marque de carte de crédit/débit ou le type de méthode de paiement est désormais disponible à partir des emplacements suivants :

- la page de commande du client sur le storefront
- l’e-mail de confirmation de commande envoyé au client
- de la [vue Détails de la commande](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/order-processing.html#view-an-order) dans l’administrateur Commerce.

## v2.3.0

_1 décembre 2023_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![New](../assets/new.svg)<!-- PAY-4381 --> [Les services de paiement prennent désormais en charge l’intégration de GraphQL](https://developer.adobe.com/commerce/webapi/graphql/payment-services/). Avec la prise en charge par GraphQL des boutons de paiement PayPal, des champs hébergés et d’Apple Pay, [!DNL Payment Services] prend désormais en charge une configuration Commerce sans interface utilisateur graphique.

## v2.2.1

_27 septembre 2023_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Correction d’un problème ](../assets/fix.svg)<!-- Issue PAY-4870 --> Correction d’un problème qui renseignait incorrectement le nouvel attribut d’en-tête dans Storefront lors de l’envoi de la version d’extension avec la dernière version. Auparavant, avec la version `1.3.0` du connecteur Commerce Services, vous ne pouviez pas étendre `User-Agent header` à partir de l’extension [!DNL Payment Services].

## v2.2.0

_30 août 2023_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![New](../assets/new.svg)<!-- PAY-4638 --> Ajout d’une [intégration à Signifyd](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/security-compliance/fraud-protection.html), qui fournit des services de protection automatisée contre les fraudes.

![New](../assets/new.svg)<!-- PAY-3981 --> [ La fonction Payer Apple promu vers une option de paiement distincte ](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html?lang=en#apple-pay-button), en dehors des boutons de paiement PayPal, pour accroître la visibilité de l’option de paiement pour les acheteurs et permettre aux vendeurs de contrôler le placement et le style de la paye Apple.

![Nouveau](../assets/new.svg)<!-- PAY-4002 --> Amélioration de l’expérience utilisateur du passage en caisse des champs de carte de crédit, y compris des améliorations de style telles que l’ajout d’icônes de paiement, pour réduire la charge cognitive des acheteurs et augmenter les conversions.

![Nouveau](../assets/new.svg)<!-- PAY-4002 --> Une fonctionnalité a été ajoutée pour permettre aux commerçants de [trier l&#39;ordre de leurs options de paiement](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#payment-buttons) afin de prioriser certaines options de paiement. Cette fonctionnalité favorise un taux de conversation de passage en caisse plus élevé.

![New](../assets/new.svg)<!-- PAY-4035 --> Les vendeurs peuvent désormais surveiller efficacement l’intégrité de leurs magasins et identifier les problèmes de transaction à l’aide du nouveau [rapport sur les transactions](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/transactions.html) disponible sur la page d’accueil de l’administrateur [!DNL Payment Services]. Le rapport présente également des données sur les taux d’autorisation des transactions et les tendances négatives des transactions.

## v2.1.0

_9 juin 2023_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg)<!-- Issue xxx --> Ajout de la prise en charge d’Adobe Commerce 2.4.7-beta1.

![New](../assets/new.svg)<!-- Issue xxx --> Ajout de la [ disponibilité dans les pays suivants et les devises associées](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html#availability) : Australie, France, Royaume-Uni.

![Nouveau](../assets/new.svg)<!-- Issue PAY-4296 --> Ajout de [ ressources étendues pour les rôles d’administrateur](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#configure-roles) afin de s’assurer que les utilisateurs administrateurs peuvent créer et gérer des commandes pour les clients et peuvent voir [!DNL Payment Services] dans le menu Ventes.

![Nouveau](../assets/new.svg)<!-- Issue PAY-4236 --> Ajout de [l&#39;annulation automatique des commandes qui entraînent des erreurs au cours de l&#39;extraction](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/checkout.html#order-auto-voided-if-error).

![Nouvelle](../assets/new.svg)<!-- Issue PAY-4183 --> La fonctionnalité créée pour [ afficher le bouton d’option de paiement par carte de crédit/débit](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html#debit-or-credit-card-button) sur la page de paiement.

## v2.0.0

_10 mars 2023_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg)<!-- Issue PAY-4152 --> Ajout de la prise en charge de PHP 8.2 et Adobe Commerce 2.4.6. Non compatible avec PHP 7.x.

## v1.6.1

_10 mars 2023_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Correctif](../assets/fix.svg)<!-- Issue PAY-4226 --> Correction d’un problème qui empêchait les nouveaux [!DNL Payment Services] commerçants d’utiliser le passage en caisse dans l’administrateur.[!DNL Payment Services] utilisait auparavant l’ID de client Commerce, qui n’existe pas pour les nouveaux clients.

![Correctif](../assets/fix.svg)<!-- Issue PAY-4205 --> Correction d’un problème en raison duquel l’état spécifié de l’adresse de livraison était remplacé par l’état dans les paramètres de taxe par défaut lors du passage en caisse à l’aide de l’option [PayPal](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html#paypal-smart-buttons). Désormais, les clients peuvent faire expédier leurs commandes à un autre état que celui configuré par défaut dans les paramètres fiscaux du marchand.

![Correction](../assets/fix.svg)<!-- Issue PAY-4202 --> Correction d’un problème qui empêchait les clients d’utiliser la mise en valeur par carte pour effectuer un achat ou supprimer un mode de paiement Vault pour un magasin [ à l’aide de l’ `Authorize and Capture` action de paiement ](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/production.html#set-payment-services-as-payment-method). Auparavant, une erreur &quot;Provider Vault ID not found&quot; s’affichait lorsque le client tentait d’utiliser ou de modifier ses cartes de crédit en mémoire tampon.

## v1.6.0

_17 février 2023_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg)<!-- Issue PAY-3540 --> Ajout de la [fonctionnalité de conformité PCI 3DS pour les marchands opérant dans l’Union européenne (UE) et en Grande-Bretagne](security.md#3ds). Cette couche supplémentaire de sécurité, qui exige que les acheteurs s’authentifient auprès de l’émetteur de leur carte de crédit, contribue à prévenir la fraude en ligne et est requise dans le cadre des réglementations de conformité de l’Union européenne (UE).

![Nouveau](../assets/new.svg)<!-- Issue PAY-3609 --> Possibilité d’ [activer la mise en valeur de carte dans l’Admin](vaulting.md#use-vaulting-in-the-admin). Cela permet aux commerçants de créer une commande pour les clients de l’administrateur à l’aide de leurs méthodes de paiement votées.

## v1.5.4

_29 janvier 2023_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![ Correction d’un problème ](../assets/fix.svg)<!-- Issue PAY-4110 --> qui empêchait les acheteurs de passer une commande à l’aide de boutons de paiement sur la page de produits, le mini-panier et le panier. Les acheteurs peuvent désormais terminer les commandes avec succès.

## v1.5.3

_25 janvier 2023_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![ Correction d’un problème ](../assets/fix.svg)<!-- Issue PAY-4102 -->. Publication d’un correctif pour un problème connu incompatible avec l’arrière. Cette version verrouille la version de l’extension d’ID de service sur la dernière version stable, ce qui permet à de nouvelles installations [!DNL Payment Services] de configurer les services Commerce.

## v1.5.2

_22 décembre 2022_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Correction d’un problème ](../assets/fix.svg)<!-- Issue PAY-3992 --> Amélioration de la facturation dans [!DNL Payment Services] en cas de refus d’un mode de paiement.

![ Correction d’un problème ](../assets/fix.svg)<!-- Issue PAY-3999 -->[!DNL Payment Services] qui affiche désormais correctement les boutons de paiement PayPal pour les marchands qui utilisent le modèle personnalisé [ Fire Checkout](https://commercemarketplace.adobe.com/swissup-firecheckout.html){target=_blank} pour la page de passage en caisse. Auparavant, le minicart affichait par intermittence les boutons.

## v1.5.1

_23 novembre 2022_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![New](../assets/new.svg)<!-- Issue PAY-3923 -->[!DNL Payment Services] inclut désormais le numéro de version dans l’en-tête de l’agent utilisateur afin que les requêtes puissent effectuer le suivi, filtrer ou abandonner les points de terminaison inutilisés.

![Correction d’un problème ](../assets/fix.svg)<!-- Issue PAY-3968 -->[!DNL Payment Services] qui affiche désormais correctement les données de commande lorsqu’une commande est passée à partir de la page de produit à l’aide de boutons de paiement.

## v1.5.0

_18 novembre 2022_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg)<!-- Issue PAY-3880 --> Un acheteur peut désormais [sauvegarder (enregistrer) ses informations de carte de crédit lors du passage en caisse](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/vaulting.html) pour les utiliser dans un achat ultérieur pour le même magasin ou un autre dans le même compte marchand.

![Nouveau](../assets/new.svg)<!-- Issue PAY-3950 --> Les vendeurs peuvent désormais activer la [fonction Commerce d’achat instantané](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/checkout-instant-purchase.html) pour leurs magasins afin que les acheteurs puissent (utiliser les [informations de carte de crédit Vault Vault Vault validées](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/vaulting.html)) pour accélérer le paiement.

## v1.4.1

_14 octobre 2022_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Correctif](../assets/fix.svg)<!-- Issue PAY-3766 --> Lorsque le mode de paiement d’un client est refusé, le message d’erreur visible est plus explicite. Il conseille au client de saisir à nouveau les informations de paiement et de réessayer, d’essayer un autre mode de paiement ou de contacter sa banque au sujet du refus de la transaction.

## v1.4.0

_30 septembre 2022_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![New](../assets/new.svg)<!-- Issue PAY-784 -->[!DNL Payment Services] offre désormais la possibilité de configurer un compte marchand pour [utiliser plusieurs comptes commerciaux PayPal](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#use-multiple-paypal-accounts). Cela permet au commerçant d’exploiter vos magasins dans plusieurs pays à l’aide de différentes devises ou d’utiliser Adobe Commerce pour une partie de votre entreprise.

![New](../assets/new.svg)<!-- Issue PAY-3231 --> Les commerçants peuvent [ ajouter un [!UICONTROL Soft Descriptor]](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#add-soft-descriptor) à des sites web ou à une configuration de vues de boutique individuelles qui s’affichent sur les relevés de banque de transactions des clients pour délimiter les marques, les magasins ou les lignes de produits.

![New](../assets/new.svg)<!-- Issue PAY-3707 --> [ Activez ou désactivez les champs de carte de crédit et les boutons de paiement PayPal](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#configure-payment-options) pour le passage en caisse dans les paramètres [!DNL Payment Services].

![Correction d’un problème ](../assets/fix.svg)<!-- Issue PAY-3546 --> Lorsqu’un client clique sur **[!UICONTROL Edit cart]**, la page redirige vers la page du panier et affiche les éléments mis à jour au lieu d’afficher un panier vide.

## v1.3.1

_6 septembre 2022_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Correction d’un problème](../assets/fix.svg)<!-- Issue PAY-3663 --> Désormais, lorsqu’un magasin d’un commerçant capture une commande autorisée avec une devise non globale, le processus de capture se termine et aucune erreur n’est affichée.

## v1.3.0

_9 août 2022_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouvelle](../assets/new.svg)<!-- Issue PAY-XX --> Disponibilité générale—[!DNL Payment Services] est désormais [ prise en charge par [!DNL Adobe Commerce] et [!DNL Magento Open Source] versions 2.4.0 à 2.4.5](https://devdocs.magento.com/release/availability.html#compatibility).

![Problème corrigé](../assets/fix.svg)<!-- Issue PAY-x --> La paie Apple est désormais compatible avec le navigateur Safari v15.5 sur mobile et bureau.

## v1.2.0

_29 juin 2022_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Problème connu](../assets/bug.svg)<!-- Issue PAY-x --> Le paiement Apple est incompatible avec le navigateur Safari v15.5 sur mobile et bureau. Lorsque vous utilisez Safari version 15.5, vous ne pouvez pas terminer l’extraction avec Apple Pay.

![Correction d’un problème](../assets/fix.svg)<!-- Issue PAY-3264 --> Auparavant, l’extraction échouait lorsqu’un utilisateur connecté sélectionnait une adresse de facturation/de livraison autre que l’adresse par défaut de son compte. Désormais, l’adresse de facturation/d’expédition sélectionnée est envoyée (au lieu de l’adresse enregistrée par défaut) et le passage en caisse est terminé avec succès.

![ Correction d’un problème ](../assets/fix.svg)<!-- Issue PAY-3314 --> Si vous désactivez les boutons de paiement PayPal pour le passage en caisse, aucune erreur ne s’affiche.

![ Correction d’un problème ](../assets/fix.svg)<!-- Issue PAY-3330 --> Les paiements n’échouent plus lors de l’extraction lorsqu’un utilisateur invité saisit un numéro de téléphone contenant des tirets.

![Correction d’un problème ](../assets/fix.svg)<!-- Issue PAY-3338 PAY-2502 --> Lorsque les informations d’identification des services Commerce ne sont pas valides, [!DNL Payment Services] vous avertit désormais en affichant une erreur d’identification à partir de la [!DNL Payment Services] Accueil dans l’administrateur.

![Problème connu](../assets/bug.svg)<!-- Issue PAY-0 --> [!DNL Payment Services] est incompatible avec `commerce-data-export` v101.20 et versions ultérieures, ce qui le rend incompatible avec l’ [[!DNL Channel manager] extension](https://experienceleague.adobe.com/docs/commerce-channels/channel-manager/guide-overview.html).

## v1.1.0

_31 mars 2022_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouvelle](../assets/new.svg)<!-- Issue PAY-2127 --> Disponibilité générale—[!DNL Payment Services] est désormais [ prise en charge par [!DNL Adobe Commerce] et [!DNL Magento Open Source] versions 2.4.0 à 2.4.4](https://devdocs.magento.com/release/availability.html#compatibility).

![Nouveau](../assets/new.svg)<!-- Issue PAY-2682 --> L’extension [!DNL Payment Services] pour [!DNL Adobe Commerce] et [!DNL Magento Open Source] est désormais disponible pour les commerçants canadiens. Les commerçants peuvent afficher la configuration des paiements en [français](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html?lang=fr#carte-de-cr%C3%A9dit-et-devises-accept%C3%A9es) ou [anglais](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html#accepted-credit-cards-and-currencies).

![New](../assets/new.svg)<!-- Issue PAY-2681 --> [!DNL Payment Services] prend en charge [ dollars canadiens (CAD)](overview.md#accepted-credit-cards-and-currencies) pour les cartes de crédit et les transactions PayPal.

![New](../assets/new.svg)<!-- Issue PAY-2680 --> Les vendeurs peuvent [onboard [!DNL Payment Services]](onboard.md) extension en anglais ou en français.

![New](../assets/new.svg)<!-- Issue PAY-2678 --> Les commerçants peuvent désormais afficher des rapports financiers, aussi bien le [statut des paiements de commande](order-payment-status.md) que les [rapports de paiements](payouts.md), en dollars canadiens (CAD).

![Correction d’un problème](../assets/fix.svg)<!-- Issue PAY-2710 -->[!DNL Payment Services] compatible avec [PHP 8.1](https://www.php.net/releases/8.1/en.php).

![Correction d’un problème](../assets/fix.svg)<!-- Issue PAY-3017 --> Amélioration de l’alerte du mode sandbox pour afficher des alertes correctes avec plusieurs magasins.

![Problème corrigé](../assets/fix.svg)<!-- Issue PAY-2742 --> Vous pouvez désormais activer et désactiver les méthodes de paiement disponibles, telles que Venmo, au niveau de la vue du magasin. Auparavant, vous pouviez configurer des méthodes de paiement par site web uniquement.

![Problème corrigé](../assets/fix.svg)<!-- Issue PAY-2277 --> Vous pouvez désormais activer ou désactiver sélectivement les boutons de paiement PayPal](settings.md#payment-buttons).[

![Problème corrigé](../assets/fix.svg)<!-- Issue PAY-2561 --> Les produits précédemment supprimés n’apparaissent pas dans le panier sur la page _Commande de révision_.

![Problème connu](../assets/bug.svg)<!-- Issue PAY-2842 --> Le test des transactions de carte de crédit [ peut échouer avec PayPal](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-cc-sandbox-failure.html) lors du traitement des paiements dans un environnement de test.

## v1.0.0

_29 novembre 2021_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouvelle](../assets/new.svg)<!-- Issue PAY-2127 --> Disponibilité générale—[[!DNL Payment Services]](https://commercemarketplace.adobe.com/magento-payment-services.html) prise en charge par [!DNL Adobe Commerce] et [!DNL Magento Open Source] versions 2.4.0 à 2.4.3-p1.

![Nouveau](../assets/new.svg)<!-- Issue PAY-124 --> L’extension [!DNL Payment Services] pour [!DNL Adobe Commerce] et [!DNL Magento Open Source] peut être installée soit pour [[!DNL Adobe Commerce]  sur l’infrastructure cloud ](install.md#adobe-commerce-on-cloud-infrastructure), soit pour les instances [ sur site ](install.md#on-premises). Ces méthodes nécessitent l’utilisation d’une interface de ligne de commande.

![New](../assets/new.svg)<!-- Issue PAY-1986 --> [!DNL Payment Services] prend en charge un [compte sandbox](sandbox.md) qui permet aux marchands d’évaluer l’extension en mode test.

![New](../assets/new.svg)<!-- Issue PAY-666 --> Les vendeurs peuvent [ configurer l’extension ](settings.md) des services de paiement avec des comportements de paiement de base, comme l’utilisation de [`Authorize and Capture`](production.md#set-payment-services-as-payment-method) permutation entre des environnements de test ou de production.

![Nouveau](../assets/new.svg)<!-- Issue PAY-780 --> Vos acheteurs peuvent extraire avec [!DNL Payment Services] ou par l’intermédiaire de la [création manuelle de commande](create-order.md).

![Nouveau](../assets/new.svg)<!-- Issue PAY-1856 --> Des rapports complets, par l&#39;intermédiaire des [ états de paiement des commandes](order-payment-status.md) et des [ rapports de paiements](payouts.md), sont disponibles pour [!DNL Payment Services] afin de vous donner une vue claire des commandes de votre magasin et des paiements associés.

![New](../assets/new.svg)<!-- Issue PAY-311 --> [!DNL Payment Services] prend en charge une tarification échelonnée flexible, basée sur le volume total de traitement, adaptée à n’importe quel commerçant.

![Nouveau](../assets/new.svg)<!-- Issue PAY-1443 --> Vous pouvez facilement [ personnaliser l’aspect](payments-options.md) des boutons de paiement et des champs de carte de crédit PayPal pour l’extension [!DNL Payment Services].

![Problème connu](../assets/bug.svg)<!-- Issue PAY-2473 --> L’utilisation de [clés de compositeur incorrectes](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-install.html) lors de l’installation de l’extension empêche l’utilisateur de [s’authentifier](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) avec les `MAGEID` corrects.

![Problème connu](../assets/bug.svg)<!-- Issue PAY-2474 --> [!DNL Payment Services] rapports [ peuvent ne pas se synchroniser immédiatement ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-report-info-delayed.html).

![Problème connu](../assets/bug.svg)<!-- Issue PAY-2475 --> Votre [ compte sandbox PayPal ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-paypal-acct.html) pour [!DNL Payment Services] ne peut pas être vérifié si vous créez ce compte pendant l’intégration.
