---
title: Créer des événements personnalisés
description: Découvrez comment créer des événements personnalisés pour connecter vos données Adobe Commerce à d’autres produits Adobe DX.
source-git-commit: 1dd8f94e632bb98666ad252badf8420a014260fb
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 0%

---

# Créer des événements personnalisés

Vous pouvez étendre la variable [plateforme eventing](events.md) en créant vos propres événements storefront afin de collecter des données propres à votre secteur d’activité. Lorsque vous créez et configurez un événement personnalisé, il est envoyé au [Collecteur d’événements Storefront Magento](https://www.npmjs.com/package/@adobe/magento-storefront-event-collector).

## Gestion des événements personnalisés

Les événements personnalisés ne sont pris en charge que pour Adobe Experience Platform. Les données personnalisées ne sont pas transférées vers les tableaux de bord et les dispositifs de suivi des mesures Adobe Commerce.

Pour tout `custom` , le collecteur ajoute un événement `personId` (`ecid`) à `customContext` et enveloppe un `xdm` autour de celle-ci avant de procéder au transfert vers l’Edge.

Exemple :

Événement personnalisé publié via le SDK MSE :

```javascript
mse.publish.custom({
    customContext: { customStrAttr: "cheetah", customNumAttr: 128 },
});
```

Dans Experience Platform Edge :

```javascript
{
    xdm: {
        personId: 'ecid1234',
        customStrAttr: 'cheetah',
        customNumAttr: 128
    }
}
```

>[!NOTE]
>
> L’utilisation d’événements personnalisés peut affecter les rapports Adobe Analytics par défaut.

## Gestion des remplacements d’événements (attributs personnalisés)

Les remplacements d’attributs pour les événements standard sont pris en charge pour l’Experience Platform uniquement. Les données personnalisées ne sont pas transférées vers les tableaux de bord et les dispositifs de suivi de mesures Commerce.

Pour tout événement avec un paramètre `customContext`, le collecteur remplace `personId` et les compteurs Adobe Analytics, et transfère tous les autres attributs définis dans `customContext`.

Exemples :

Consultation produit avec remplacements publiés via le SDK MSE :

```javascript
mse.publish.productPageView({
    customContext: { customCode: "okapi" },
});
```

Dans Experience Platform Edge :

```javascript
{
    xdm: {
        eventType: 'commerce.productViews',
        personId: 'ecid1234',
        customCode: 'okapi',
        commerce: {
            productViews: {
                value : 1
            }
        }
    }
}
```

L’affichage du produit avec Adobe Commerce remplace celui publié via le SDK MSE :

```javascript
mse.publish.productPageView({
    customContext: { commerce: { customCode: "mongoose" } },
});
```

Dans Experience Platform Edge :

```javascript
{
    xdm: {
        eventType: 'commerce.productViews',
        personId: 'ecid1234',
        commerce: {
            customCode: 'mongoose',
            productViews: {
                value : 1
            }
        }
    }
}
```

>[!NOTE]
>
> Le remplacement d’événements avec des attributs personnalisés peut affecter les rapports Adobe Analytics par défaut.
