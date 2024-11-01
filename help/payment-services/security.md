---
title: Sécurité et conformité
description: Examinez les exigences en matière de sécurité et de conformité de votre site.
exl-id: 083c5a12-1d78-48b5-b9e3-612b104ce7e0
feature: Payments, Checkout, Compliance
redirect_from: https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/security.html
source-git-commit: 37380063242b6d904910be731b8e58471625e9cb
workflow-type: tm+mt
source-wordcount: '525'
ht-degree: 0%

---

# Sécurité et conformité

La sécurité est un problème majeur dans [!DNL Payment Services] et aucune information réglementée par le secteur privé ou par carte de paiement (PCI) n&#39;est transmise à votre [!DNL Payment Services].

## Sécurité Commerce

[!DNL Adobe Commerce] et [!DNL Magento Open Source] incluent la prise en charge de plusieurs fonctionnalités de sécurité.

Voir [Sécurité](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security){target="_blank"} dans le guide d’utilisation principal pour passer en revue les bonnes pratiques en matière de sécurité et apprendre à gérer les sessions d’administration et les informations d’identification, mettre en oeuvre CAPTCHA et gérer les restrictions du site web.

## Conformité PCI

Le secteur des cartes de paiement (PCI) a établi un ensemble d’exigences pour les entreprises qui acceptent le paiement par carte de crédit sur Internet. En plus de maintenir un environnement sécurisé, les marchands qui traitent les informations de carte de crédit client doivent respecter certaines instructions standard.

Pour plus d’informations, voir [Directives de conformité PCI](https://experienceleague.adobe.com/en/docs/commerce-admin/start/compliance/payments/compliance-pci){target="_blank"} .

Les commerçants peuvent remplir un [questionnaire d’auto-évaluation (SAQ)](https://www.pcisecuritystandards.org/pci_security/completing_self_assessment){target="_blank"}, qui est un outil d’auto-validation permettant d’évaluer la sécurité des données des titulaires de carte.

### Champs de carte de crédit

Avec les champs de carte de crédit, aucune donnée réglementée par PCI n’est transmise à vos services. Vous n’avez pas à stocker ni à gérer ces données, ce qui réduit considérablement les problèmes de conformité PCI.

### 3DS

PCI 3-D Secure (3DS) permet une authentification de l’acheteur avec son émetteur de carte de crédit lors d’achats en ligne de cartes de crédit. Cette couche supplémentaire de sécurité permet de prévenir la fraude en ligne et est requise dans le cadre des réglementations de conformité de l’Union européenne (UE).

[!UICONTROL Payment Services] fournit une fonctionnalité 3DS permettant aux commerçants de se conformer aux réglementations de l’UE et de protéger les clients et les marchands contre les activités frauduleuses dans leurs magasins.

Si vous êtes un commerçant dans l’UE ou en Grande-Bretagne où la conformité 3DS est requise, vous devez activer manuellement la 3DS (il s’agit de `Off` par défaut) dans [Settings](settings.md#credit-card-fields).

>[!NOTE]
>
>L&#39;exigence 3DS s&#39;applique aux transactions où l&#39;entreprise et la banque du détenteur de carte se trouvent dans l&#39;[Espace économique européen](https://www.efta.int/eea) (EEE) et en Grande-Bretagne. Les commerçants des États-Unis n’ont pas besoin de 3DS, mais peuvent l’activer pour leurs transactions si vous le souhaitez.

Les commandes passées pour l’acheteur par le vendeur ou le personnel du magasin ne sont pas configurées avec des mesures de conformité 3DS.

Pour plus d’informations, voir [3DS dans Paramètres](settings.md#3ds) .

### Valorisation des cartes

Lorsqu&#39;un nouvel acheteur [valide—ou &quot;enregistre&quot;—ses informations de carte de crédit](vaulting.md) pour les achats futurs dans vos magasins, un minimum d&#39;informations de carte de crédit est partagé avec l&#39;acheteur (quatre derniers chiffres, date d&#39;expiration de la carte et marque de la carte). Les informations de carte de crédit sont stockées avec le fournisseur de paiement. Lorsqu’une carte arrive à expiration ou qu’il n’a plus besoin des informations enregistrées, il peut supprimer ce jeton afin que les informations ne soient plus stockées par le fournisseur de paiement.

Pour plus d’informations, voir [Valorisation des cartes de crédit](vaulting.md) .

### Boutons de paiement PayPal

Avec les boutons de paiement PayPal, aucune donnée réglementée par PCI n’est transmise à vos services. Vous n’avez pas à stocker ni à gérer ces données, ce qui réduit considérablement les problèmes de conformité PCI.

Pour des raisons de sécurité, PayPal ne transmet pas l’adresse de facturation lors du passage en caisse : le pays, l’email et le nom sont les seules informations de facturation utilisées. Vous pouvez éventuellement activer le passage en caisse PayPal de votre site pour renvoyer l’adresse de facturation complète en contactant PayPal et en effectuant un processus de vérification.

PayPal dispose également d&#39;une protection intégrée contre les fraudes qui utilise l&#39;apprentissage automatique pour vous aider à lutter contre les fraudes. Pour plus d’informations, consultez la [documentation sur la protection des vendeurs](https://www.paypal.com/us/webapps/mpp/security/seller-protection) de PayPal.

## Protection contre les fraudes

Vous pouvez activer la protection anti-fraude automatisée pour les services de paiement avec l’ [extension Signifyd](https://commercemarketplace.adobe.com/signifyd-module-connect.html).

Pour plus d’informations, voir [Protection Signifyd contre la fraude](fraud-protection.md) .

