---
title: Conditions préalables pour l’outil de transfert de contenu
description: Conditions préalables pour l’outil de transfert de contenu
exl-id: 41a9cff1-4d89-480c-b9fc-5e8efc2a0705
source-git-commit: eb633db8fe64a62661c094b88f0ce8d9950ed6d7
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 95%

---

# Conditions préalables pour l’outil de transfert de contenu {#prerequisites}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_prereqs"
>title="Points importants concernant l’utilisation de l’outil de transfert de contenu"
>abstract="Examinez les points importants à prendre en compte pour utiliser l’outil de transfert de contenu, notamment les versions Java et AEM, les types de magasin de données pris en charge, les considérations relatives aux groupes d’utilisateurs et d’utilisatrices, etc."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html#pre-reqs?lang=fr" text="Points importants concernant l’utilisation de l’outil de transfert de contenu"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html#best-practices?lang=fr" text="Bonnes pratiques et consignes"

Le tableau suivant résume les conditions préalables requises pour l’utilisation de l’outil de transfert de contenu.

Veuillez consulter toutes les considérations ci-dessous :

| Considérations | Éléments actuellement pris en charge |
|---------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Version d’AEM | L’outil de transfert de contenu ne peut être exécuté que sur AEM version 6.3 ou ultérieure. |
| Taille de l’entrepôt de segments | Un référentiel existant qui contient moins de 55 millions de nœuds JCR et jusqu’à 250 Go (taille compactée en ligne) sur l’instance de *Création* et 50 Go sur l’instance de *Publication* est actuellement pris en charge. Créez un ticket d’assistance auprès de l’assistance clientèle d’Adobe pour discuter des options relatives à la taille de l’entrepôt de segments au-dessus de ces limites. |
| Taille totale du référentiel de contenu <br>*(entrepôt de segments + entrepôt de données)* | L’outil de transfert de contenu est conçu pour transférer jusqu’à 20 To de contenu pour le type de magasin de données File Data Store. Tout ce qui dépasse 20 To n’est actuellement pas pris en charge. Créez un ticket de support auprès de l’assistance clientèle d’Adobe pour discuter des options relatives au contenu de plus de 20 To. <br>Pour accélérer considérablement le processus de transfert de contenu pour les référentiels volumineux, une étape de [précopie](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=fr#setting-up-pre-copy-step) facultative peut être utilisée. Cela s’applique aux types de magasin de données File Data Store, Amazon S3 et Azure Data Store. Pour Amazon S3 et Azure Data Store, les tailles de référentiel supérieures à 20 To sont prises en charge. |
| Taille totale de l’index Lucene | La taille totale de l’index Lucene pris en charge, `/oak:index/lucene` `/oak:index/damAssetLucene` non compris, est actuellement de 25 Go au maximum. Créez un ticket d’assistance auprès de l’assistance clientèle d’Adobe pour discuter des options relatives à la taille d’index supérieure à cette limite. |
| Longueur d’un nom du nœud | La longueur d’un nom de nœud doit être de 150 octets maximum lorsque le chemin d’accès parent du nœud est >= (supérieur ou égal à) 350 octets. Ces noms de nœud doivent être raccourcis pour être &lt;= 150 octets afin d’être pris en charge par l’entrepôt de nœuds Document dans AEM as a Cloud Service. Les assimilations échouent si ces noms de nœuds longs ne sont pas corrigés. |
| Contenu dans des chemins immuables | L’outil de transfert de contenu ne peut pas être utilisé pour migrer le contenu dans des chemins immuables. Pour transférer le contenu de `/etc`, seuls certains chemins `/etc` peuvent être sélectionnés, mais uniquement pour prendre en charge [AEM Forms vers AEM Forms as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/migrate-to-forms-as-a-cloud-service.html#paths-of-various-aem-forms-specific-assets). Pour tous les autres cas d’utilisation, reportez-vous à la section [Restructuration des référentiels communs](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/restructuring/all-repository-restructuring-in-aem-6-5.html) pour en savoir plus sur la restructuration des référentiels. |
| Valeur de propriété de nœud dans MongoDB | La valeur des propriétés de nœud stockées dans MongoDB ne doit pas dépasser 16 Mo. Cette limitation est exigée par MongoDB. Les ingestions échouent si une des valeurs de propriété est supérieure à cette limite. Avant d’exécuter une extraction, exécutez le script [oak-run](https://repo1.maven.org/maven2/org/apache/jackrabbit/oak-run/1.38.0/oak-run-1.38.0.jar). Vérifiez toutes les valeurs de propriété de taille importante et validez si elles sont nécessaires. Celles qui dépassent 16 Mo devront être converties en valeurs binaires. |

## Prochaines étapes {#whats-next}

Une fois que vous avez examiné les conditions préalables et déterminé si vous pouvez utiliser l’outil de transfert de contenu dans votre projet de migration, reportez-vous à la section [Bonnes pratiques et instructions pour l’utilisation de l’outil de transfert de contenu](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html).
