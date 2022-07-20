---
title: Durée de la session utilisateur
description: L’administrateur permet de configurer la durée de vie des cookies de votre utilisateur Adobe Commerce pour la variable [!DNL Quick Checkout] extension .
source-git-commit: a95d2ed92c69feba03d1b84d44abf08c1d1b4029
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Durée de la session utilisateur

La durée de vie d’une session d’acheteur est déterminée par plusieurs facteurs, qui peuvent être configurés dans votre administrateur Adobe Commerce. Voir [Configuration de la durée de vie du cookie](https://docs.magento.com/user-guide/customers/customer-online-options.html){target=_blank} pour plus d’informations.

La durée de vie configurée des cookies peut affecter votre [!DNL Quick Checkout] if :

1. En raison de l’inactivité, l’acheteur est déconnecté d’Adobe Commerce.
1. Le [!DNL Bolt] expire.

Si un acheteur passe une commande lors de la [!DNL Bolt] expire, la commande est placée correctement, mais l’utilisateur est déconnecté des deux réseaux.

Si l’utilisateur est toujours principal après un passage en caisse réussi, il ne sera pas déconnecté d’Adobe Commerce et de [!DNL Bolt].
