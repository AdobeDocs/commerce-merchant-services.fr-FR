---
title: "Performances"
description: "L’ [!DNL Live Search] espace de travail des performances donne des informations sur les termes de recherche que les acheteurs utilisent."
exl-id: ee2053fc-98c5-4d2c-9345-4d1f9a3180fb
source-git-commit: 4978bdb5549f5df911863a23fdfbfc9ab9ad05df
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# Performances

L’espace de travail *Performance* fournit des informations sur les termes de recherche utilisés par les acheteurs. Les informations peuvent être utilisées pour identifier les tendances, augmenter les clics publicitaires et améliorer le taux de conversion. L’espace de travail Performances fournit un instantané des mesures de recherche pour une période spécifique et comprend les rapports suivants :

* Recherches uniques
* Zéro résultat
* Résultats populaires

![Performance](assets/performance-unique-searches.png)

Vous pouvez également vous reporter au [tableau de bord de Data Management](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-dashboard.html) pour plus de données sur la synchronisation des données.

## Affichage d’un rapport

1. Pour entrer dans la **plage de dates**, cliquez sur le calendrier (![Calendrier](assets/btn-calendar.png)) et effectuez l’une des opérations suivantes :

   * Pour indiquer une seule date, double-cliquez sur la date du calendrier.
   * Pour définir une plage de dates, cliquez sur la première et la dernière date du calendrier.

>[!NOTE]
>
>L’espace de travail des performances est mis à jour toutes les 12 heures.

## Descriptions des champs

| Données instantanées | Description |
|--- |--- |
| Recherches uniques | Nombre total de recherches uniques pour la période spécifiée. Plusieurs recherches effectuées par le même acheteur, même pour la même requête, sont considérées comme uniques si elles sont soumises à plus d’une heure d’intervalle. |
| Taux de clics | Pourcentage de recherches qui se terminent par le fait que l’acheteur clique sur un produit. Par exemple, le taux de clics publicitaires est de 50 % si l’acheteur recherche &quot;pantalon&quot; et &quot;chemise&quot;, puis clique sur un résultat dans la recherche &quot;chemise&quot;. |
| Taux de conversion | Pourcentage des produits achetés par l’acheteur par rapport au nombre de produits sur lesquels il clique pour la période spécifiée. Par exemple, le taux de conversion de l’interaction est de 100 % si l’acheteur consulte six produits dans la fenêtre contextuelle, clique sur l’un d’eux et effectue un achat. <br /><br />Le taux de conversion n’est pas affecté par le nombre d’affichages d’un produit donné. Par exemple, le taux de conversion reste le même si l’acheteur utilise la recherche, mais ne clique sur aucun produit. |
| Taux zéro résultat | Pourcentage de recherches uniques ne renvoyant aucun résultat pour la période spécifiée. Par exemple, le taux de résultats zéro est de 66,67 % si l’acheteur recherche &quot;fjjajfjf&quot; deux fois (sans résultats) et &quot;pantalon&quot; une fois (avec résultats). |
| Durée position du clic | Position relative du taux de clics publicitaires moyen en fonction de recherches uniques pour la période spécifiée. |

| Rapports | Description |
|--- |--- |
| Recherches uniques | Répertorie les requêtes de recherche uniques utilisées au cours de la période spécifiée. Les données du rapport sont calculées de la même manière que les données d’instantané de recherche uniques. Si un acheteur effectue deux recherches avec la même requête, mais séparées de plus d’une heure, la recherche est considérée comme deux recherches uniques. Limite de rapport : 500 premiers termes |
| Zéro résultat | Répertorie les requêtes de recherche qui ne renvoient aucun résultat et le nombre de fois utilisées au cours de la période spécifiée. Limite de rapport : 500 premiers termes |
| Résultats populaires | Répertorie les noms des produits qui ont reçu le plus grand nombre d’affichages au cours de la période spécifiée. Les résultats populaires sont calculés uniquement sur la base des impressions et ne sont pas affectés par le nombre de clics ou les recettes générées. Limite de rapport : 500 premiers termes |
