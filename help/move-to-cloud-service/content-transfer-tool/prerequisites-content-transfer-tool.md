---
title: Conditions préalables pour l’outil de transfert de contenu
description: Conditions préalables pour l’outil de transfert de contenu
source-git-commit: becb8368af8a8228bf3248bde66ad7164187a9c4
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 1%

---

# Conditions préalables pour l’outil de transfert de contenu {#prerequisites}

Le tableau suivant résume les conditions préalables requises pour l’utilisation de l’outil de transfert de contenu.

Veuillez consulter toutes les considérations ci-dessous :

| Considérations | Éléments actuellement pris en charge |
|--- |--- |
| Version d’AEM | L’outil de transfert de contenu ne peut être exécuté que sur AEM version 6.3 ou ultérieure. Pour pouvoir utiliser l’outil de transfert de contenu avec AEM version 6.2 ou antérieure, une mise à niveau statique du référentiel de contenu vers AEM 6.5 est requise. Il n’est pas nécessaire de mettre à niveau le code vers AEM 6.5 pour cela. |
| Taille de l’entrepôt de segments | L’outil de transfert de contenu prend actuellement en charge jusqu’à 83 Go sur *Auteur* et 31 Go sur *Publier*. |
| Taille totale du référentiel de contenu <br>*(entrepôt de segments + entrepôt de données)* | L’outil de transfert de contenu est conçu pour transférer du contenu jusqu’à 10 To. Tout ce qui dépasse 10 To n’est actuellement pas pris en charge. Créez un ticket d’assistance auprès de l’assistance clientèle d’Adobe pour discuter des options relatives au contenu de plus de 10 To. |
| Contenu sur les chemins immuables | L’outil de transfert de contenu ne peut pas être utilisé pour migrer le contenu dans des chemins immuables tels que `“/etc”`. Certains `"/etc"` chemins peuvent être sélectionnés uniquement pour prendre en charge [AEM Forms vers AEM Forms en tant que Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/migrate-to-forms-as-a-cloud-service.html?lang=en#paths-of-various-aem-forms-specific-assets). Pour tous les autres cas d’utilisation, reportez-vous à la section [Restructuration des référentiels communs](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/restructuring/all-repository-restructuring-in-aem-6-4.html?lang=en#restructuring) pour en savoir plus sur la restructuration des référentiels. |

## Suite {#whats-next}

Une fois que vous avez examiné les conditions préalables et déterminé si vous pouvez utiliser l’outil de transfert de contenu dans votre projet de migration, reportez-vous à la section [Bonnes pratiques et remarques supplémentaires](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md) lors de l’utilisation de l’outil de transfert de contenu.
