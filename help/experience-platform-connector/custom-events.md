---
title: Créer des événements personnalisés
description: Découvrez comment créer des événements personnalisés pour connecter vos données Adobe Commerce à d’autres produits Adobe DX.
exl-id: 5a754106-c66a-4280-9896-6d065df8a841
role: Admin, Developer
feature: Personalization, Integration, Eventing
source-git-commit: 659dd2d1b298ec2a98bb4365a46b09d7468daaad
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 0%

---

# Créer des événements personnalisés

Vous pouvez étendre la variable [plateforme eventing](events.md) en créant vos propres événements storefront afin de collecter des données propres à votre secteur d’activité. Lorsque vous créez et configurez un événement personnalisé, il est envoyé au [Collecteur d’événements Adobe Commerce](https://github.com/adobe/commerce-events/tree/main/packages/commerce-events-collectors).

## Gestion des événements personnalisés

Les événements personnalisés ne sont pris en charge que pour Adobe Experience Platform. Les données personnalisées ne sont pas transférées vers les tableaux de bord et les dispositifs de suivi des mesures Adobe Commerce.

Pour tout `custom` , le collecteur :

- Ajouts `identityMap` avec `ECID` comme identité principale
- Inclut `email` in `identityMap` comme identité secondaire _if_ `personalEmail.address` est défini dans l’événement .
- Entoure l’événement complet dans une `xdm` avant le transfert vers l’Edge

Exemple :

Événement personnalisé publié via le SDK Adobe Commerce Events :

```javascript
mse.publish.custom({
    commerce: {
        saveForLaters: {
            value: 1,
        },
    },
});
```

Dans Experience Platform Edge :

```javascript
{
  xdm: {
    identityMap: {
      ECID: [
        {
          id: 'ecid1234',
          primary: true
        }
      ],
      email: [
        {
          id: "runs@safari.ke",
          primary: false
        }
      ]
    },
    commerce: {
        saveForLaters: {
            value: 1
        }
    }
  }
}
```

>[!NOTE]
>
> L’utilisation d’événements personnalisés peut affecter les rapports Adobe Analytics par défaut.

## Gestion des remplacements d’événements (attributs personnalisés)

Les remplacements d’attributs pour les événements standard sont pris en charge pour l’Experience Platform uniquement. Les données personnalisées ne sont pas transférées vers les tableaux de bord et les dispositifs de suivi de mesures Commerce.

Pour tout événement avec `customContext`, le collecteur remplace les champs définis dans les contextes appropriés avec les champs dans `customContext`. Le cas d’utilisation des remplacements est lorsqu’un développeur souhaite réutiliser et étendre des contextes définis par d’autres parties de la page dans des événements déjà pris en charge.

>[!NOTE]
>
>Lors du remplacement d’événements personnalisés, le transfert d’événement vers l’Experience Platform doit être désactivé pour ce type d’événement afin d’éviter un double comptage.

Exemples :

Consultation produit avec remplacements publiés via le SDK Adobe Commerce Events :

```javascript
mse.publish.productPageView({
    productListItems: [
        {
            productCategories: [
                {
                    categoryID: "cat_15",
                    categoryName: "summer pants",
                    categoryPath: "pants/mens/summer",
                },
            ],
        },
    ],
});
```

Dans Experience Platform Edge :

```javascript
{
  xdm: {
    eventType: 'commerce.productViews',
    identityMap: {
      ECID: [
        {
          id: 'ecid1234',
          primary: true,
        }
      ]
    },
    commerce: {
      productViews: {
        value : 1,
      }
    },
    productListItems: [{
        SKU: "1234",
        name: "leora summer pants",
        productCategories: [{
            categoryID: "cat_15",
            categoryName: "summer pants",
            categoryPath: "pants/mens/summer",
        }],
    }],
  }
}
```

>[!NOTE]
>
> Le remplacement d’événements avec des attributs personnalisés peut affecter les rapports Adobe Analytics par défaut.
