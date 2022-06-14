---
title: Conditions préalables pour l’outil de transfert de contenu (hérité)
description: Conditions préalables pour l’outil de transfert de contenu
hide: true
hidefromtoc: true
exl-id: 6b2878cb-6882-452b-8cab-e590316633f6
source-git-commit: 22bbf15e33ab3d5608dc01ed293bb04b07cb6c8c
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 98%

---

# Conditions préalables pour l’outil de transfert de contenu (Legacy) {#prerequisites}

Le tableau suivant résume les conditions préalables requises pour l’utilisation de l’outil de transfert de contenu.

Veuillez consulter toutes les considérations ci-dessous :

| Considérations | Éléments actuellement pris en charge |
|--- |--- |
| Version d’AEM | L’outil de transfert de contenu ne peut être exécuté que sur AEM version 6.3 ou ultérieure. |
| Taille de l’entrepôt de segments | Un référentiel existant qui contient moins de 55 millions de nœuds JCR et jusqu’à 83 Go (taille compactée en ligne) sur *Auteur* et 31 Go sur *Publier* est actuellement pris en charge. Créez un ticket d’assistance auprès de l’assistance clientèle d’Adobe pour discuter des options relatives à la taille de l’entrepôt de segments au-dessus de ces limites. |
| Taille totale du référentiel de contenu <br>*(entrepôt de segments + entrepôt de données)* | L’outil de transfert de contenu est conçu pour transférer jusqu’à 20 To de contenu pour le type de magasin de données File Data Store. Tout ce qui dépasse 20 To n’est actuellement pas pris en charge. Créez un ticket de support auprès de l’assistance clientèle d’Adobe pour discuter des options relatives au contenu de plus de 20 To. <br>Pour accélérer considérablement le processus de transfert de contenu pour les référentiels volumineux, une étape de [précopie](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=fr#setting-up-pre-copy-step) facultative peut être utilisée. Cela s’applique aux types de magasin de données File Data Store, Amazon S3 et Azure Data Store. Pour Amazon S3 et Azure Data Store, les tailles de référentiel supérieures à 20 To sont prises en charge. |
| Taille totale de l’index Lucene | La taille totale de l’index Lucene de 25 Go au maximum est actuellement prise en charge. Créez un ticket d’assistance auprès de l’assistance clientèle d’Adobe pour discuter des options relatives à la taille d’index supérieure à cette limite. |
| Longueur d’un nom du nœud | La longueur d’un nom de nœud doit être de 150 octets ou moins. Les noms de nœud de plus de 150 octets doivent être raccourcis pour être &lt;= 150 octets afin d’être pris en charge par l’entrepôt de nœuds Document dans AEM as a Cloud Service. Les assimilations échouent si ces noms de nœuds longs ne sont pas corrigés. |
| Contenu dans des chemins immuables | L’outil de transfert de contenu ne peut pas être utilisé pour migrer le contenu dans des chemins immuables. Pour transférer le contenu de `/etc`, seuls certains chemins `/etc` peuvent être sélectionnés, mais uniquement pour prendre en charge [AEM Forms vers AEM Forms as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/migrate-to-forms-as-a-cloud-service.html?lang=fr#paths-of-various-aem-forms-specific-assets). Pour tous les autres cas d’utilisation, reportez-vous à la section [Restructuration des référentiels communs](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/restructuring/all-repository-restructuring-in-aem-6-4.html?lang=fr#restructuring) pour en savoir plus sur la restructuration des référentiels. |
| Valeur de propriété de nœud dans MongoDB | La valeur des propriétés de nœud stockées dans MongoDB ne doit pas dépasser 16 Mo. Cette limitation est exigée par MongoDB. Les ingestions échouent si une des valeurs de propriété est supérieure à cette limite. Avant d’exécuter une extraction, exécutez le script [oak-run](https://repo1.maven.org/maven2/org/apache/jackrabbit/oak-run/1.38.0/oak-run-1.38.0.jar). Vérifiez toutes les valeurs de propriété de taille importante et validez si elles sont nécessaires. Celles qui dépassent 16 Mo devront être converties en valeurs binaires. |

## Prochaines étapes {#whats-next}

Une fois que vous avez examiné les conditions préalables et déterminé si vous pouvez utiliser l’outil de transfert de contenu dans votre projet de migration, reportez-vous à la section [Bonnes pratiques et instructions pour l’utilisation de l’outil de transfert de contenu](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html?lang=fr).
