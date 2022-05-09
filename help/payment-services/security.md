---
title: Sécurité et conformité
description: Examinez les exigences en matière de sécurité et de conformité de votre site.
exl-id: 083c5a12-1d78-48b5-b9e3-612b104ce7e0
source-git-commit: 9596815e31402f23b399b223f3221074331c1773
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 0%

---

# Sécurité et conformité

La sécurité est la plus grande préoccupation de la [!DNL Payment Services] et aucune information privée ou réglementée par le secteur des cartes de paiement (PCI) n’est transmise sur votre [!DNL Payment Services].

## Sécurité commerciale

[!DNL Adobe Commerce] et [!DNL Magento Open Source] prendre en charge plusieurs fonctionnalités de sécurité ;

Voir [Sécurité](https://docs.magento.com/user-guide/stores/security.html){target=&quot;_blank&quot;} dans le guide d’utilisation principal pour passer en revue les bonnes pratiques en matière de sécurité et apprendre à gérer les sessions d’administration et les informations d’identification, mettre en oeuvre CAPTCHA et gérer les restrictions du site web.

## Conformité PCI

Le secteur des cartes de paiement (PCI) a établi un ensemble d’exigences pour les entreprises qui acceptent le paiement par carte de crédit sur Internet. En plus de maintenir un environnement sécurisé, les marchands qui traitent les informations de carte de crédit client doivent respecter certaines instructions standard.

Voir [Instructions de conformité PCI](https://docs.magento.com/user-guide/stores/compliance-pci.html){target=&quot;_blank&quot;} pour plus d’informations.

Les vendeurs peuvent effectuer une [questionnaire d’auto-évaluation (SAQ)](https://www.pcisecuritystandards.org/pci_security/completing_self_assessment){target=&quot;_blank&quot;}, qui est un outil d’auto-validation permettant d’évaluer la sécurité des données du détenteur de carte.

### Champs de carte de crédit

Avec les champs de carte de crédit, aucune donnée réglementée par PCI n’est transmise à vos services. Vous n’avez pas à stocker ni à gérer ces données, ce qui réduit considérablement les problèmes de conformité PCI.

### Boutons intelligents PayPal

Avec les boutons PayPal Smart, aucune donnée PCI n’est transmise à vos services. Vous n’avez pas à stocker ni à gérer ces données, ce qui réduit considérablement les problèmes de conformité PCI.

Pour des raisons de sécurité, PayPal ne transmet pas l’adresse de facturation lors du passage en caisse : le pays, l’email et le nom sont les seules informations de facturation utilisées. Vous pouvez éventuellement activer le passage en caisse PayPal de votre site pour renvoyer l’adresse de facturation complète en contactant PayPal et en effectuant un processus de vérification.

PayPal dispose également d&#39;une protection intégrée contre les fraudes qui utilise l&#39;apprentissage automatique pour vous aider à combattre la fraude. Voir PayPal [Documentation sur la protection des revendeurs](https://www.paypal.com/us/webapps/mpp/security/seller-protection) pour plus d’informations.
