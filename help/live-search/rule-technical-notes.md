---
title: Notes techniques sur les règles
description: Notes techniques sur l’utilisation des règles de recherche en direct.
exl-id: 24ff6a19-f7cd-42f7-b466-fc18f9091504
source-git-commit: 7402e97f53b71e488d860215487f4809572b7e6f
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Notes techniques sur les règles

[!DNL Live Search] les règles déclenchent des actions en fonction de diverses conditions de requête et permettent aux commerçants de modeler l’expérience de recherche pour différents scénarios.

La version actuelle de [!DNL Live Search] Les règles sont basées sur la chaîne de requête saisie par l’acheteur, plutôt que sur l’ensemble de résultats renvoyés. Une chaîne de requête peut contenir des caractères alphanumériques et la mise en majuscule est ignorée. Comme pour les facettes et les synonymes, les règles sont stockées dans `protobuf dynamo`. Au moment de la requête, le service de recherche récupère les règles via `grpc` appelle vers `search-admin-service`.
