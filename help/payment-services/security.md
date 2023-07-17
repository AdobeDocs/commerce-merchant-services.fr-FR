---
title: Sécurité et conformité
description: Examinez les exigences en matière de sécurité et de conformité de votre site.
exl-id: 083c5a12-1d78-48b5-b9e3-612b104ce7e0
feature: Payments, Checkout, Compliance
source-git-commit: 90bfa7099924feb308397960cff76bdf177bbe49
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 0%

---

# Sécurité et conformité

La sécurité est la plus grande préoccupation de la [!DNL Payment Services] et aucune information privée ou réglementée par le secteur des cartes de paiement (PCI) n’est transmise sur votre [!DNL Payment Services].

## Sécurité commerciale

[!DNL Adobe Commerce] et [!DNL Magento Open Source] prendre en charge plusieurs fonctionnalités de sécurité ;

Voir [Sécurité](https://docs.magento.com/user-guide/stores/security.html){target="_blank"} dans le guide d’utilisation principal pour passer en revue les bonnes pratiques en matière de sécurité et apprendre à gérer les sessions d’administration et les informations d’identification, mettre en oeuvre CAPTCHA et gérer les restrictions du site web.

## Conformité PCI

Le secteur des cartes de paiement (PCI) a établi un ensemble d’exigences pour les entreprises qui acceptent le paiement par carte de crédit sur Internet. En plus de maintenir un environnement sécurisé, les marchands qui traitent les informations de carte de crédit client doivent respecter certaines instructions standard.

Voir [Instructions de conformité PCI](https://docs.magento.com/user-guide/stores/compliance-pci.html){target="_blank"} pour plus d’informations.

Les vendeurs peuvent effectuer une [questionnaire d’auto-évaluation (SAQ)](https://www.pcisecuritystandards.org/pci_security/completing_self_assessment){target="_blank"}, qui est un outil d’auto-validation permettant d’évaluer la sécurité des données des titulaires de carte.

### Champs de carte de crédit

Avec les champs de carte de crédit, aucune donnée réglementée par PCI n’est transmise à vos services. Vous n’avez pas à stocker ni à gérer ces données, ce qui réduit considérablement les problèmes de conformité PCI.

### 3DS

PCI 3-D Secure (3DS) permet une authentification de l’acheteur avec son émetteur de carte de crédit lors d’achats en ligne de cartes de crédit. Cette couche supplémentaire de sécurité permet de prévenir la fraude en ligne et est requise dans le cadre des réglementations de conformité de l’Union européenne (UE).

[!UICONTROL Payment Services] fournit une fonctionnalité 3DS permettant aux commerçants de se conformer aux réglementations de l’UE et de protéger les clients et les marchands contre les activités frauduleuses dans leurs magasins.

Si vous êtes un commerçant de l’UE ou de Grande-Bretagne où la conformité 3DS est requise, vous devez activer manuellement la 3DS (c’est-à-dire : `Off` par défaut) dans [Paramètres](settings.md#credit-card-fields).

>[!NOTE]
>
>L’exigence 3DS s’applique aux transactions où l’entreprise et la banque du détenteur de carte se trouvent dans la zone [Espace économique européen](https://www.efta.int/eea) (EEE) et Grande-Bretagne. Les commerçants des États-Unis n’ont pas besoin de 3DS, mais peuvent l’activer pour leurs transactions si vous le souhaitez.

Les commandes passées pour l’acheteur par le vendeur ou le personnel du magasin ne sont pas configurées avec des mesures de conformité 3DS.

Voir [3DS dans les paramètres](settings.md#3ds) pour plus d’informations.

### Valorisation des cartes

Lorsqu’un acheteur [les valeurs (ou &quot;enregistre&quot;) leurs informations de carte de crédit](vaulting.md) pour les achats futurs dans vos magasins, des informations minimales sur les cartes de crédit sont partagées avec l’acheteur (quatre derniers chiffres, date d’expiration de la carte et marque de carte). Les informations de carte de crédit sont stockées avec le fournisseur de paiement. Lorsqu’une carte arrive à expiration ou qu’il n’a plus besoin des informations enregistrées, il peut supprimer ce jeton afin que les informations ne soient plus stockées par le fournisseur de paiement.

Voir [Valorisation des cartes de crédit](vaulting.md) pour plus d’informations.

### Boutons intelligents PayPal

Avec les boutons PayPal Smart, aucune donnée PCI n’est transmise à vos services. Vous n’avez pas à stocker ni à gérer ces données, ce qui réduit considérablement les problèmes de conformité PCI.

Pour des raisons de sécurité, PayPal ne transmet pas l’adresse de facturation lors du passage en caisse : le pays, l’email et le nom sont les seules informations de facturation utilisées. Vous pouvez éventuellement activer le passage en caisse PayPal de votre site pour renvoyer l’adresse de facturation complète en contactant PayPal et en effectuant un processus de vérification.

PayPal dispose également d&#39;une protection intégrée contre les fraudes qui utilise l&#39;apprentissage automatique pour vous aider à combattre la fraude. Voir PayPal [Documentation sur la protection des revendeurs](https://www.paypal.com/us/webapps/mpp/security/seller-protection) pour plus d’informations.
