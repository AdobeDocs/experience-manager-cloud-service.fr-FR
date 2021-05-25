---
title: Conditions préalables pour l’outil de transfert de contenu
description: Conditions préalables pour l’outil de transfert de contenu
source-git-commit: ebe12a71df610a68c43048667136e331c1bd8f86
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 1%

---

# Conditions préalables pour l’outil de transfert de contenu {#prerequisites}

Le tableau suivant résume les conditions préalables requises pour l’utilisation de l’outil de transfert de contenu. Veuillez consulter toutes les considérations ci-dessous :

| Considérations | Éléments actuellement pris en charge |
|--- |--- |
| Version d’AEM | L’outil de transfert de contenu ne peut être exécuté que sur AEM version 6.3 ou ultérieure. Pour pouvoir utiliser l’outil de transfert de contenu avec AEM version 6.2 ou antérieure, une mise à niveau statique du référentiel de contenu vers AEM 6.5 est requise. Il n’est pas nécessaire de mettre à niveau le code vers AEM 6.5 pour cela. |
| Taille de l’entrepôt de segments | L’outil de transfert de contenu prend actuellement en charge jusqu’à 83 Go sur *Auteur* et 31 Go sur *Publier*. |
| Taille totale du référentiel de contenu <br>*(entrepôt de contenu + entrepôt de données)* | L’outil de transfert de contenu est conçu pour transférer du contenu jusqu’à 10 To. Tout ce qui dépasse 10 To n’est actuellement pas pris en charge. Créez un ticket d’assistance auprès de l’assistance clientèle d’Adobe pour discuter des options relatives au contenu de plus de 10 To. |
| Contenu sur les chemins immuables | L’outil de transfert de contenu ne fonctionne pas pour la migration du contenu dans des chemins immuables tels que `“/etc”`. <br>Pour en savoir plus sur la restructuration des référentiels et les modèles de workflows, voir  [Restructuration ](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/restructuring/all-repository-restructuring-in-aem-6-4.html?lang=en#restructuring) des référentiels communs . |