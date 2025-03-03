---
title: Types de synchronisation
description: Les synonymes  [!DNL Live Search] unidirectionnels et bidirectionnels étendent la définition des mots-clés.
exl-id: 708d7b0d-7361-44f4-ae9e-b92f574ac975
source-git-commit: cb5db979828eb0b678d19c926de2823829717c02
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---

# Types de synchronisation

Les synonymes unidirectionnels et bidirectionnels élargissent la définition des mots-clés. Certaines sont interchangeables avec le mot-clé, tandis que d’autres représentent un sous-ensemble du mot-clé.

## À double sens

Les synonymes bidirectionnels ont la même signification et renvoient les mêmes résultats de recherche. Dans l&#39;exemple suivant, le premier mot en gras est le mot-clé utilisé dans le catalogue, suivi de mots ayant la même signification que le mot-clé d&#39;origine. Vous pouvez créer une simple paire de synonymes bidirectionnels ou une chaîne de plusieurs synonymes bidirectionnels pour le même mot-clé.

**** ![Sélecteur bidirectionnel](assets/btn-two-way.png)
**pants** ![Sélecteur bidirectionnel](assets/btn-two-way.png) ajoute des pantalons ![Sélecteur bidirectionnel](assets/btn-two-way.png)

## A sens unique

Un synonyme unidirectionnel est un sous-ensemble d’un mot-clé, mais avec une signification plus précise. Par exemple, les pantalons et les shorts sont des pantalons, mais tous ne sont pas des pantalons ou des shorts. Une recherche de pantalon inclut des pantalons et des shorts. Cependant, une recherche de raccourcis ne renvoie pas d’événement.

**sweatshirt** ![Sélecteur à sens unique](assets/btn-one-way.png)
**pants** ![Sélecteur à sens unique](assets/btn-one-way.png) capris ![Sélecteur à sens unique multiples](assets/btn-multiple-one-way.png) calf-length-pants ![Sélecteur à sens unique multiples](assets/btn-multiple-one-way.png) des pureurs de pétales

## Bonnes pratiques

Gardez à l’esprit les bonnes pratiques suivantes pour tirer le meilleur parti des synonymes [!DNL Live Search].

### Évitez les &quot;mots d’arrêt&quot;

[!DNL Live Search] filtre les &quot;mots d’arrêt&quot; anglais courants des synonymes, tels que :

a, an et sont, en tant que, à, être, mais, par, pour, si, in, into, is, it, no, of, on, or, such, the, they, then, they, this, to, was, will with

Les mots d’arrêt ne rendent pas les synonymes plus significatifs, mais augmentent la quantité de données à traiter.

### Utiliser des mots simples

Si un terme de synonyme contient plusieurs mots, l’espace entre les mots les traite comme des synonymes distincts. Par exemple, si vous définissez &quot;pièce temporelle&quot; comme synonyme de &quot;montre&quot;, les mots &quot;heure&quot; et &quot;pièce&quot; sont traités comme des synonymes distincts.

### Utilisation du singulier et du pluriel

Il n&#39;est pas nécessaire de définir les formes singulière et plurielle d&#39;un mot comme synonyme. Si votre catalogue contient un mélange de termes singuliers et pluriels, la fonction de recherche trouve l’ensemble de produits approprié. Par exemple, si vous utilisez le mot &quot;pant&quot; dans le nom du produit et qu’un acheteur recherche &quot;pantalon&quot;, l’ensemble correct de produits est renvoyé et le mot &quot;pant&quot; unique est proposé sous forme de suggestion. Le terme singulier &quot;pant&quot; est souvent utilisé dans l&#39;industrie de la mode et parfois dans la vente au détail, bien que la forme plurielle &quot;pantalon&quot; soit plus courante dans certaines zones. (Le mot &quot;pantalon&quot; fait techniquement référence à la partie d&#39;un vêtement qui couvre une jambe, c&#39;est pourquoi il faut une &quot;paire de pantalons&quot; pour couvrir les deux jambes.)

### Cohérence

Soyez cohérent avec la manière dont la terminologie est utilisée dans votre catalogue. Gardez à l’esprit qu’il peut y avoir des différences régionales d’utilisation et parfois des différences au sein d’un secteur d’activité.
