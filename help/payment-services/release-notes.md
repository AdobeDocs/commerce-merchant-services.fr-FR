---
title: "[!DNL Payment Services] Notes de mise à jour"
description: Consultez les notes de mise à jour pour plus d’informations sur toutes les [!DNL Payment Services] versions.
exl-id: 104aa2c7-7735-4ac2-8ed1-a03cd9911273
feature: Payments, Release Notes
source-git-commit: f61a9c9ed1eedded4b304d2fe3f9e2930d10e027
workflow-type: tm+mt
source-wordcount: '2279'
ht-degree: 0%

---

# Notes de mise à jour

Ces notes de mise à jour décrivent la version initiale de [!DNL Payment Services] et incluent :

![Nouveau](../assets/new.svg) Nouvelles fonctionnalités
![Correction d’un problème](../assets/fix.svg) Correctifs et améliorations
![Problème connu](../assets/bug.svg) Problèmes connus

Pour les modifications et correctifs de fonctionnalités publiés en dehors de la version standard des fonctionnalités, consultez la ou les sections Mises à jour du service hébergé .

Voir [Versions à venir](https://devdocs.magento.com/release/) pour en savoir plus sur les calendriers de publication et l’assistance.

Voir [Disponibilité du produit](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html) pour découvrir quelles versions d’Adobe Commerce prennent en charge cette extension.

## Mises à jour du service hébergé

Ces notes de mise à jour décrivent les modifications et correctifs de fonctionnalités qui se sont produits et qui ont été publiés en dehors des versions régulières des fonctionnalités pour le service hébergé.

+++Mises à jour du service hébergé

_10 octobre 2023_

![Nouveau problème](../assets/fix.svg)<!-- Issue PAY-4888 --> Désormais, les marchands peuvent filtrer les transactions de carte de crédit et de débit selon les quatre derniers chiffres du numéro de carte dans la variable [Rapport des transactions](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/transactions.html).

_12 juillet 2023_

![Correction d’un problème](../assets/fix.svg)<!-- Issue PAY-4587 --> Un problème apparu dans la version 2.1.0 des services de paiement, qui empêchait les vides d’autorisation placés par les versions précédentes de l’extension, est désormais résolu. Les commerçants qui utilisent n’importe quelle version de Services de paiement peuvent annuler des autorisations.

_9 juin 2023_

![Nouveau](../assets/new.svg)<!-- Issue PAY-4288 --> Maintenant, les marchands peuvent [configure _only_ Boutons de paiement PayPal](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html#use-only-paypal-payment-buttons)—and _not_ utilisez l’option de paiement par carte de crédit PayPal . Cela permet aux commerçants de proposer diverses options de paiement, notamment des boutons de paiement Venmo et PayPal, et d’utiliser un fournisseur de carte de crédit existant au lieu de l’option de paiement par carte de crédit PayPal.

![Nouveau](../assets/new.svg)<!-- Issue PAY-4050 --> Ajout d’une [visualisation des données](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html#order-payment-status-data-visualization-view), qui s’affiche sur la page d’accueil du service de paiement, pour le rapport d’état des paiements des commandes .

![Correction d’un problème](../assets/fix.svg)<!-- Issue PAY-4486--> Auparavant, le bouton PayPal PayLater n’apparaissait pas dans le passage en caisse des commerçants britanniques. Ce problème est résolu.

![Correction d’un problème](../assets/fix.svg)<!-- Issue PAY-4485--> Les vues de visualisation des données de rapport s’affichent désormais sur la page d’accueil des services de paiement lorsque les services de paiement sont désactivés.

_25 janvier 2023_

![Problème connu](../assets/bug.svg)<!-- Issue PAY-4102 --> Les nouvelles installations de Services de paiement ne peuvent pas configurer les Services de commerce, ce qui rend les Services de paiement inutilisables. Pour résoudre ce problème, mettez à jour votre extension de services de paiement vers la version 1.5.3.

_12 septembre 2022_

![Nouveau](../assets/new.svg)<!-- Issue PAY-3705 --> La variable `increment_id` est désormais disponible pour être utilisé dans le cadre de la réconciliation des paiements dans les systèmes ERP externes. Il est propagé vers la variable [`custom_id` _et_ `invoice_id`](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/data.html#reconcile-with-erp-system), visible dans le webhook PayPal et dans le détail de l’activité commerciale pour un paiement.

_31 août 2022_

![Correction d’un problème](../assets/fix.svg)<!-- Issue PAY-3629 --> Lorsqu’un nouveau commerçant accède pour la première fois à la page d’accueil des services de paiement, la page se charge désormais immédiatement pour afficher le contenu au lieu de devoir actualiser la page.

_9 août 2021_

![Nouveau](../assets/new.svg)<!-- Issue PAY-3420 --> Le paiement Apple est désormais disponible sous la forme d’un bouton PayPal Smart. Ceci [option de paiement](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-options.html#apple-pay-button) permet aux clients d’utiliser la fonctionnalité d’identifiant tactile de leur appareil iOS ou macOS pour sélectionner Apple Pay. Apple Pay traite le paiement à l’aide des informations d’identification de paiement de carte de crédit et de débit stockées sur l’appareil.

_28 juin 2021_

![Nouveau](../assets/new.svg)<!-- Issue PAY-1720 --> Les litiges relatifs aux commandes de magasins sont désormais disponibles dans [le rapport État du paiement de la commande](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html#view-disputes). Vous pouvez agir en cas de conflit en accédant directement au centre de résolution PayPal à partir de [!DNL Payment Services].

![Nouveau](../assets/new.svg)<!-- Issue PAY-2854 --> Améliorations de l’expérience utilisateur à partir de [!DNL Payment Services] Accueil permet de modifier une configuration au niveau de l’héritage actuel et améliore l’affichage de l’en-tête et de la navigation.

![Nouveau](../assets/new.svg)<!-- Issue PAY-2854 --> Vous pouvez désormais voir des avertissements lorsque vous passez du mode sandbox au mode de production et lorsque vous tentez de quitter une vue avec des mises à jour qui n’ont pas été enregistrées.

![Nouveau](../assets/new.svg)<!-- Issue PAY-2761 --> Vous pouvez désormais personnaliser les données qui s’affichent dans la variable [Rapport d’état des paiements de commande](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html#show-and-hide-columns) et la variable [Rapport de paiements](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/payouts.html#show-and-hide-columns) en affichant ou en masquant les colonnes à l’aide du contrôle Paramètres de colonne .

+++

## v2.2.1

_27 septembre 2023_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Correction d’un problème](../assets/fix.svg)<!-- Issue PAY-4870 --> Correction d’un problème qui renseignait incorrectement le nouvel attribut d’en-tête dans Storefront lors de l’envoi de la version d’extension avec la dernière version. Auparavant, avec la variable `1.3.0` la version du connecteur Commerce Services, vous n’avez pas pu étendre la variable `User-Agent header` à partir de l’extension Services de paiement.

## v2.2.0

_30 août 2023_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg)<!-- PAY-4638 --> Ajout d’une [intégration avec Signifyd](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/security-compliance/fraud-protection.html), qui fournit des services automatisés de protection contre la fraude.

![Nouveau](../assets/new.svg)<!-- PAY-3981 --> [Paiement Apple promu à une option de paiement distincte](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html?lang=en#apple-pay-button), en dehors des boutons de paiement PayPal, pour accroître la visibilité de l’option de paiement pour les acheteurs et permettre aux commerçants de contrôler l’emplacement et le style de la paye Apple.

![Nouveau](../assets/new.svg)<!-- PAY-4002 --> Amélioration de l’expérience utilisateur du passage en caisse des champs de carte de crédit, y compris des améliorations de style telles que l’ajout d’icônes de paiement, afin de réduire la charge cognitive des acheteurs et d’augmenter les conversions.

![Nouveau](../assets/new.svg)<!-- PAY-4002 --> Ajout d’une fonctionnalité permettant aux commerçants de [trier l’ordre de leurs options de paiement ;](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#payment-buttons) pour donner la priorité à certaines options de paiement. Cette fonctionnalité favorise un taux de conversation de passage en caisse plus élevé.

![Nouveau](../assets/new.svg)<!-- PAY-4035 --> Ajout d’une nouvelle [Rapport des transactions](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/transactions.html) à la page d’accueil Admin du service de paiement afin de fournir une visibilité sur les taux d’autorisation des transactions et les tendances négatives des transactions afin que les marchands puissent contrôler efficacement l’intégrité de leurs magasins et identifier les problèmes de transaction.

## v2.1.0

_9 juin 2023_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg)<!-- Issue xxx --> Ajout de la prise en charge d’Adobe Commerce 2.4.7-beta1.

![Nouveau](../assets/new.svg)<!-- Issue xxx --> Ajout [Disponibilité dans les pays suivants et les devises associées](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html#availability): Australie, France, Royaume-Uni.

![Nouveau](../assets/new.svg)<!-- Issue PAY-4296 --> Ajout [ressources étendues pour les rôles d’administrateur](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#configure-roles) afin de s’assurer que les utilisateurs administrateurs peuvent créer et gérer des commandes pour les clients et qu’ils peuvent voir Services de paiement dans le menu Ventes .

![Nouveau](../assets/new.svg)<!-- Issue PAY-4236 --> Ajout [annulation automatique pour les commandes qui entraînent des erreurs lors de l’extraction](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/checkout.html#order-auto-voided-if-error).

![Nouveau](../assets/new.svg)<!-- Issue PAY-4183 --> Fonctionnalité créée pour [afficher le bouton d’option de paiement de carte de crédit/débit ;](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html#debit-or-credit-card-button) sur la page de passage en caisse.

## v2.0.0

_10 mars 2023_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg)<!-- Issue PAY-4152 --> Ajout de la prise en charge de PHP 8.2 et Adobe Commerce 2.4.6. Non compatible avec PHP 7.x.

## v1.6.1

_10 mars 2023_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Correction](../assets/fix.svg)<!-- Issue PAY-4226 --> Correction d’un problème qui empêchait les nouveaux marchands de services de paiement d’utiliser le passage en caisse dans l’administrateur. Auparavant, les services de paiement utilisaient l’ID client Commerce, qui n’existe pas pour les nouveaux clients.

![Correction](../assets/fix.svg)<!-- Issue PAY-4205 --> Correction d’un problème en raison duquel l’état de l’adresse de livraison spécifiée était remplacé par l’état dans les paramètres de taxe par défaut lors du passage en caisse à l’aide de la variable [Option PayPal](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html#paypal-smart-buttons). Désormais, les clients peuvent faire expédier leurs commandes à un autre état que celui configuré par défaut dans les paramètres fiscaux du marchand.

![Correction](../assets/fix.svg)<!-- Issue PAY-4202 --> Correction d’un problème qui empêchait les clients d’utiliser la mise en valeur de carte pour effectuer un achat ou supprimer un mode de paiement par défaut pour un magasin. [en utilisant la variable `Authorize and Capture` action de paiement](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/production.html#set-payment-services-as-payment-method). Auparavant, une erreur &quot;Provider Vault ID not found&quot; s’affichait lorsque le client tentait d’utiliser ou de modifier ses cartes de crédit en mémoire tampon.

## v1.6.0

_17 février 2023_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg)<!-- Issue PAY-3540 --> Ajout [Fonction de conformité PCI 3DS pour les commerçants qui effectuent des transactions dans l’Union européenne (UE) et en Grande-Bretagne](security.md#3ds). Cette couche supplémentaire de sécurité, qui exige que les acheteurs s’authentifient auprès de l’émetteur de leur carte de crédit, contribue à prévenir la fraude en ligne et est requise dans le cadre des réglementations de conformité de l’Union européenne (UE).

![Nouveau](../assets/new.svg)<!-- Issue PAY-3609 --> Ajout de la capacité à [Activation de la valeur de carte dans l’Admin](vaulting.md#use-vaulting-in-the-admin). Cela permet aux commerçants de créer une commande pour les clients de l’administrateur à l’aide de leurs méthodes de paiement votées.

## v1.5.4

_29 janvier 2023_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Correction d’un problème](../assets/fix.svg)<!-- Issue PAY-4110 --> Correction d’un problème qui empêchait les acheteurs de passer une commande à l’aide de boutons intelligents sur la page du produit, le mini-panier et le panier. Les acheteurs peuvent désormais terminer les commandes avec succès.

## v1.5.3

_25 janvier 2023_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Correction d’un problème](../assets/fix.svg)<!-- Issue PAY-4102 --> Publication d’un correctif pour un problème connu incompatible avec l’arrière. Cette version verrouille la version de l’extension d’ID de service sur la dernière version stable, ce qui permet à de nouvelles installations de services de paiement de configurer Commerce Services.

## v1.5.2

_22 décembre 2022_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Correction d’un problème](../assets/fix.svg)<!-- Issue PAY-3992 --> Amélioration de la facturation dans les services de paiement en cas de refus d’un mode de paiement.

![Correction d’un problème](../assets/fix.svg)<!-- Issue PAY-3999 --> Les services de paiement affichent désormais correctement les boutons intelligents PayPal pour les marchands qui utilisent [Déclenchement du passage en caisse](https://commercemarketplace.adobe.com/swissup-firecheckout.html){target=_blank} modèle personnalisé pour la page de passage en caisse. Auparavant, le minicart affichait par intermittence les boutons.

## v1.5.1

_23 novembre 2022_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg)<!-- Issue PAY-3923 --> Les services de paiement incluent désormais le numéro de version dans l’en-tête de l’agent utilisateur pour que les demandes puissent effectuer le suivi, filtrer ou abandonner les points de terminaison inutilisés.

![Correction d’un problème](../assets/fix.svg)<!-- Issue PAY-3968 --> Les services de paiement affichent désormais correctement les données de commande lorsqu’une commande est passée à partir de la page de produit à l’aide de boutons intelligents.

## v1.5.0

_18 novembre 2022_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg)<!-- Issue PAY-3880 --> Un acheteur peut maintenant [Vault (enregistrer) leurs informations de carte de crédit lors du passage en caisse](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/vaulting.html) à utiliser dans un achat ultérieur pour le même magasin ou un autre dans le même compte marchand.

![Nouveau](../assets/new.svg)<!-- Issue PAY-3950 --> Les vendeurs peuvent désormais activer la variable [Fonctionnalité Commerce d’achat instantané](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/checkout-instant-purchase.html) pour leurs magasins afin que les clients puissent (utiliser [informations de carte de crédit en coffre-fort](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/vaulting.html)) pour accélérer le passage en caisse.

## v1.4.1

_14 octobre 2022_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Correction](../assets/fix.svg)<!-- Issue PAY-3766 --> Lorsque le mode de paiement d’un client est refusé, le message d’erreur visible est plus explicite. Il conseille au client de saisir à nouveau les informations de paiement et de réessayer, d’essayer un autre mode de paiement ou de contacter sa banque au sujet du refus de la transaction.

## v1.4.0

_30 septembre 2022_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg)<!-- Issue PAY-784 --> Les services de paiement incluent désormais la possibilité de configurer un compte marchand pour [utiliser plusieurs comptes commerciaux PayPal ;](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#use-multiple-paypal-accounts). Cela permet au commerçant d’exploiter vos magasins dans plusieurs pays à l’aide de différentes devises ou d’utiliser Adobe Commerce pour une partie de votre entreprise.

![Nouveau](../assets/new.svg)<!-- Issue PAY-3231 --> Les commerçants peuvent [ajouter une [!UICONTROL Soft Descriptor]](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#add-soft-descriptor) sur des sites web ou une configuration de vues de boutique individuelles qui s’affichent sur les relevés bancaires des transactions des clients pour délimiter les marques, les magasins ou les lignes de produits.

![Nouveau](../assets/new.svg)<!-- Issue PAY-3707 --> [Activer ou désactiver les champs de carte de crédit et les boutons intelligents PayPal](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#configure-payment-options) pour l’extraction dans les paramètres des services de paiement.

![Correction d’un problème](../assets/fix.svg)<!-- Issue PAY-3546 --> Lorsqu’un client clique **[!UICONTROL Edit cart]**, la page redirige vers la page du panier et affiche les éléments mis à jour au lieu d’afficher un panier vide.

## v1.3.1

_6 septembre 2022_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Correction d’un problème](../assets/fix.svg)<!-- Issue PAY-3663 --> Désormais, lorsque le magasin d’un commerçant capture une commande autorisée avec une devise non globale, le processus de capture se termine et aucune erreur n’est affichée.

## v1.3.0

_9 août 2022_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg)<!-- Issue PAY-XX --> Disponibilité générale -[!DNL Payment Services] est maintenant [pris en charge par [!DNL Adobe Commerce] et [!DNL Magento Open Source] versions 2.4.0 à 2.4.5](https://devdocs.magento.com/release/availability.html#compatibility).

![Correction d’un problème](../assets/fix.svg)<!-- Issue PAY-x --> Apple Pay est désormais compatible avec le navigateur Safari v15.5 sur mobile et bureau.

## v1.2.0

_29 juin 2022_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Problème connu](../assets/bug.svg)<!-- Issue PAY-x --> Apple Pay est incompatible avec le navigateur Safari v15.5 sur mobile et bureau. Lorsque vous utilisez Safari version 15.5, vous ne pouvez pas terminer l’extraction avec Apple Pay.

![Correction d’un problème](../assets/fix.svg)<!-- Issue PAY-3264 --> Auparavant, lorsqu’un utilisateur connecté sélectionnait une autre adresse de facturation/de livraison que l’adresse par défaut de son compte, l’extraction échouait. Correction de ce problème. Désormais, l’adresse de facturation/d’expédition sélectionnée est envoyée (au lieu de l’adresse enregistrée par défaut) et le passage en caisse est terminé avec succès.

![Correction d’un problème](../assets/fix.svg)<!-- Issue PAY-3314 --> Si vous désactivez les boutons intelligents PayPal pour le passage en caisse, aucune erreur ne s’affiche.

![Correction d’un problème](../assets/fix.svg)<!-- Issue PAY-3330 --> Les paiements n’échouent plus lors du passage en caisse lorsqu’un utilisateur invité saisit un numéro de téléphone contenant des tirets.

![Correction d’un problème](../assets/fix.svg)<!-- Issue PAY-3338 PAY-2502 --> Lorsque les informations d’identification de Commerce Services ne sont pas valides, la variable [!DNL Payment Services] La page d’accueil s’affiche désormais dans l’Admin. Une erreur d’identification s’affiche pour vous signaler que vos informations d’identification ne sont pas valides.

![Problème connu](../assets/bug.svg)<!-- Issue PAY-0 --> [!DNL Payment Services] est actuellement incompatible avec `commerce-data-export` v101.20 et versions ultérieures, ce qui le rend incompatible avec la [[!DNL Channel manager] extension](https://experienceleague.adobe.com/docs/commerce-channels/channel-manager/guide-overview.html).

## v1.1.0

_31 mars 2022_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg)<!-- Issue PAY-2127 --> Disponibilité générale -[!DNL Payment Services] est maintenant [pris en charge par [!DNL Adobe Commerce] et [!DNL Magento Open Source] versions 2.4.0 à 2.4.4](https://devdocs.magento.com/release/availability.html#compatibility).

![Nouveau](../assets/new.svg)<!-- Issue PAY-2682 --> La variable [!DNL Payment Services] extension pour [!DNL Adobe Commerce] et [!DNL Magento Open Source] est maintenant disponible pour les commerçants canadiens. Les vendeurs peuvent afficher la configuration des paiements dans l’une des [Français](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html?lang=fr#carte-de-cr%C3%A9dit-et-devises-accept%C3%A9es) ou [Anglais](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html#accepted-credit-cards-and-currencies).

![Nouveau](../assets/new.svg)<!-- Issue PAY-2681 --> [!DNL Payment Services] prend [Dollars canadiens (CAD)](overview.md#accepted-credit-cards-and-currencies) pour les cartes de crédit et les transactions PayPal.

![Nouveau](../assets/new.svg)<!-- Issue PAY-2680 --> Les commerçants peuvent [onboard [!DNL Payment Services]](onboard.md) en anglais ou en français.

![Nouveau](../assets/new.svg)<!-- Issue PAY-2678 --> Les vendeurs peuvent désormais afficher les rapports financiers, à la fois [Statut de paiement de la commande](order-payment-status.md) et [Rapports sur les paiements](payouts.md), en dollars canadiens (CAD).

![Correction d’un problème](../assets/fix.svg)<!-- Issue PAY-2710 --> [!DNL Payment Services] est désormais compatible avec [PHP 8.1](https://www.php.net/releases/8.1/en.php).

![Correction d’un problème](../assets/fix.svg)<!-- Issue PAY-3017 --> Amélioration de l’alerte du mode sandbox pour afficher les alertes appropriées avec plusieurs magasins.

![Correction d’un problème](../assets/fix.svg)<!-- Issue PAY-2742 --> Vous pouvez désormais activer et désactiver les méthodes de paiement disponibles, telles que Venmo, au niveau de la vue du magasin. Auparavant, vous pouviez configurer des méthodes de paiement par site web uniquement.

![Correction d’un problème](../assets/fix.svg)<!-- Issue PAY-2277 --> Vous pouvez désormais sélectionner [activation ou désactivation de boutons intelligents PayPal individuels](settings.md#payment-buttons).

![Correction d’un problème](../assets/fix.svg)<!-- Issue PAY-2561 --> Les produits précédemment supprimés n’apparaissent pas dans le panier sur la page _Ordre de révision_ page.

![Problème connu](../assets/bug.svg)<!-- Issue PAY-2842 --> Test des transactions de carte de crédit [peut échouer avec PayPal](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-cc-sandbox-failure.html) lors du traitement des paiements dans un environnement de test.

## v1.0.0

_29 novembre 2021_

[!BADGE Pris en charge]{type=Informative tooltip="Pris en charge"}

![Nouveau](../assets/new.svg)<!-- Issue PAY-2127 --> Disponibilité générale -[[!DNL Payment Services]](https://commercemarketplace.adobe.com/magento-payment-services.html) est désormais pris en charge par [!DNL Adobe Commerce] et [!DNL Magento Open Source] versions 2.4.0 à 2.4.3-p1.

![Nouveau](../assets/new.svg)<!-- Issue PAY-124 --> La variable [!DNL Payment Services] extension pour [!DNL Adobe Commerce] et [!DNL Magento Open Source] peut être installé pour [[!DNL Adobe Commerce] sur l’infrastructure cloud](install.md#adobe-commerce-on-cloud-infrastructure) ou [Sur site](install.md#on-premises) instances. Ces méthodes nécessitent l’utilisation d’une interface de ligne de commande.

![Nouveau](../assets/new.svg)<!-- Issue PAY-1986 --> [!DNL Payment Services] prend en charge une [compte sandbox](sandbox.md) qui permet aux commerçants d’évaluer l’extension en mode test.

![Nouveau](../assets/new.svg)<!-- Issue PAY-666 --> Les commerçants peuvent [configuration des services de paiement](settings.md) avec des comportements de paiement de base, tels que l’utilisation de [`Authorize and Capture`](production.md#set-payment-services-as-payment-method) passage d’un environnement de test à un environnement de production.

![Nouveau](../assets/new.svg)<!-- Issue PAY-780 --> Vos acheteurs peuvent vérifier avec [!DNL Payment Services] ou via [création manuelle de commande](create-order.md).

![Nouveau](../assets/new.svg)<!-- Issue PAY-1856 --> Reporting complet, via [Statut de paiement de la commande](order-payment-status.md) et [Rapports sur les paiements](payouts.md), sont disponibles pour [!DNL Payment Services] pour vous donner une vue claire des commandes de votre magasin et des paiements associés.

![Nouveau](../assets/new.svg)<!-- Issue PAY-311 --> [!DNL Payment Services] prend en charge une tarification échelonnée flexible, basée sur le volume total de traitement, adaptée à n’importe quel commerçant.

![Nouveau](../assets/new.svg)<!-- Issue PAY-1443 --> Vous pouvez facilement [personnaliser l’aspect](payments-options.md) des boutons intelligents PayPal et des champs de carte de crédit pour la variable [!DNL Payment Services] extension .

![Problème connu](../assets/bug.svg)<!-- Issue PAY-2473 --> Utilisation [clés de compositeur incorrectes](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-install.html) lors de l’installation de l’extension empêche l’utilisateur de [authentification](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) avec la valeur `MAGEID`.

![Problème connu](../assets/bug.svg)<!-- Issue PAY-2474 --> [!DNL Payment Services] rapports [peut ne pas se synchroniser immédiatement](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-report-info-delayed.html).

![Problème connu](../assets/bug.svg)<!-- Issue PAY-2475 --> Votre [Compte sandbox PayPal](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-paypal-acct.html) pour [!DNL Payment Services] ne peut pas être vérifié si vous créez ce compte lors de l’intégration.
