---
title: Conditions préalables pour l’outil de transfert de contenu
description: Conditions préalables pour l’outil de transfert de contenu
exl-id: 41a9cff1-4d89-480c-b9fc-5e8efc2a0705
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 41%

---

# Conditions préalables pour l’outil de transfert de contenu {#prerequisites}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_prereqs"
>title="Points importants concernant l’utilisation de l’outil de transfert de contenu"
>abstract="Examinez les points importants à prendre en compte pour utiliser l’outil de transfert de contenu, notamment les versions Java™ et AEM, les types d’entrepôt de données pris en charge, les considérations relatives aux groupes d’utilisateurs, etc."
additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/prerequisites-content-transfer-tool.html?lang=fr" text="Points importants concernant l’utilisation de l’outil de transfert de contenu"
additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html?lang=en#best-practices" text="Bonnes pratiques et consignes"

Le tableau suivant résume les conditions préalables requises pour l’utilisation de l’outil de transfert de contenu.

Consultez toutes les considérations ci-dessous :

| Considérations | Éléments actuellement pris en charge |
|---------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Version d’AEM | L’outil de transfert de contenu ne peut être exécuté que sur AEM version 6.3 ou ultérieure. |
| Taille de l’entrepôt de segments | Un référentiel existant qui contient moins de 55 millions de nœuds JCR et jusqu’à 250 Go (taille compactée en ligne) sur l’instance de *Création* et 50 Go sur l’instance de *Publication* est actuellement pris en charge. Créez un ticket d’assistance auprès de l’assistance clientèle d’Adobe afin que vous puissiez discuter des options relatives à la taille de la boutique de segments au-dessus de ces limites. |
| Taille totale du référentiel de contenu <br>*(entrepôt de segments + entrepôt de données)* | L’outil de transfert de contenu est conçu pour transférer du contenu jusqu’à 20 téraoctets pour le type d’entrepôt de données basé sur les fichiers. Tout ce qui est supérieur à 20 téraoctets n’est actuellement pas pris en charge. Créez un ticket d’assistance auprès de l’Assistance clientèle d’Adobe afin que vous puissiez discuter des options relatives au contenu de plus de 20 téraoctets. <br>Pour accélérer considérablement le processus de transfert de contenu pour les référentiels volumineux, une étape de [précopie](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/handling-large-content-repositories.html#setting-up-pre-copy-step) facultative peut être utilisée. Ce processus s’applique aux types de magasin de données File Data Store, Amazon S3 et Azure Data Store. Pour Amazon S3 et Azure Data Store, les tailles de référentiel supérieures à 20 téraoctets sont prises en charge. |
| Taille totale de l’index Lucene | Taille totale de l’index Lucene de 25 Go au maximum, à l’exception `/oak:index/lucene` et `/oak:index/damAssetLucene` est prise en charge. Créez un ticket d’assistance auprès de l’assistance clientèle d’Adobe afin que vous puissiez discuter des options relatives à la taille de l’index supérieure à cette limite. |
| Longueur d’un nom du nœud | La longueur d’un nom de nœud doit être de 150 octets maximum lorsque le chemin d’accès parent du nœud est >= (supérieur ou égal à) 350 octets. Ces noms de noeud doivent être raccourcis à &lt;= 150 octets pour être pris en charge par le magasin de noeuds Document dans AEM as a Cloud Service. Les assimilations échouent si ces noms de noeuds longs ne sont pas corrigés. |
| Contenu dans des chemins immuables | L’outil de transfert de contenu ne peut pas être utilisé pour migrer le contenu dans des chemins immuables. Pour transférer du contenu depuis `/etc`, vous pouvez sélectionner certains `/etc` chemins d’accès, mais uniquement pour la prise en charge [AEM Forms vers AEM Forms as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/setup-configure-migrate/migrate-to-forms-as-a-cloud-service.html#paths-of-various-aem-forms-specific-assets). Pour tous les autres cas d’utilisation, voir [Restructuration des référentiels courants](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/restructuring/all-repository-restructuring-in-aem-6-5.html) pour en savoir plus sur la restructuration du référentiel. |
| Valeur de propriété de nœud dans MongoDB | La valeur des propriétés de nœud stockées dans MongoDB ne doit pas dépasser 16 Mo. Cette règle est appliquée par MongoDB. Les assimilations échouent si des valeurs de propriété sont supérieures à cette limite. Avant d’exécuter une extraction, exécutez le script [oak-run](https://repo1.maven.org/maven2/org/apache/jackrabbit/oak-run/1.38.0/oak-run-1.38.0.jar). Vérifiez toutes les valeurs de propriété de taille importante et validez si elles sont nécessaires. Ceux qui dépassent 16 Mo doivent être convertis en valeurs binaires. |

## Prochaines étapes {#whats-next}

Une fois que vous avez examiné les conditions préalables et déterminé si vous pouvez utiliser l’outil de transfert de contenu dans votre projet de migration, reportez-vous à la section [Conseils et bonnes pratiques relatives à l’utilisation de l’outil de transfert de contenu](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html?lang=fr).
