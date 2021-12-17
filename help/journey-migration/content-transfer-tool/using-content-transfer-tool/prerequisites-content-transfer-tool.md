---
title: Conditions préalables pour l’outil de transfert de contenu
description: Conditions préalables pour l’outil de transfert de contenu
source-git-commit: a6d225943c5d23ebd960fda0b0912a81f1f80014
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 67%

---

# Conditions préalables pour l’outil de transfert de contenu {#prerequisites}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_prereqs"
>title="Points importants concernant l’utilisation de l’outil de transfert de contenu"
>abstract="Examinez les points importants à prendre en compte pour utiliser l’outil de transfert de contenu, notamment les versions Java et AEM, les types d’entrepôt de données pris en charge, les considérations relatives aux groupes d’utilisateurs, etc."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=fr#pre-reqs" text="Points importants concernant l’utilisation de l’outil de transfert de contenu"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html?lang=fr#best-practices" text="Bonnes pratiques et consignes"

Le tableau suivant résume les conditions préalables requises pour l’utilisation de l’outil de transfert de contenu.

Veuillez consulter toutes les considérations ci-dessous :

| Considérations | Éléments actuellement pris en charge |
|--- |--- |
| Version d’AEM | L’outil de transfert de contenu ne peut être exécuté que sur AEM version 6.3 ou ultérieure. |
| Taille de l’entrepôt de segments | Un référentiel existant qui contient moins de 55 millions de nœuds JCR et jusqu’à 83 Go (taille compactée en ligne) sur *Auteur* et 31 Go sur *Publier* est actuellement pris en charge. Créez un ticket d’assistance auprès de l’assistance clientèle d’Adobe pour discuter des options relatives à la taille de l’entrepôt de segments au-dessus de ces limites. |
| Taille totale du référentiel de contenu <br>*(entrepôt de segments + entrepôt de données)* | L’outil de transfert de contenu est conçu pour transférer du contenu jusqu’à 20 To pour le type d’entrepôt de données basé sur les fichiers d’un entrepôt de données. Tout ce qui dépasse 20 To n’est actuellement pas pris en charge. Créez un ticket d’assistance auprès de l’assistance clientèle d’Adobe pour discuter des options relatives au contenu de plus de 20 To. <br>Pour accélérer considérablement le processus de transfert de contenu pour les référentiels volumineux, une option [pre-copy](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=fr#setting-up-pre-copy-step) peut être utilisée. Cela s’applique aux types de magasin de données File Data Store, Amazon S3 et Azure Data Store. Pour Amazon S3 et Azure Data Store, les tailles de référentiel supérieures à 20 To sont prises en charge. |
| Taille totale de l’index Lucene | La taille totale de l’index Lucene de 25 Go au maximum est actuellement prise en charge. Créez un ticket d’assistance auprès de l’assistance clientèle d’Adobe pour discuter des options relatives à la taille d’index supérieure à cette limite. |
| Longueur d’un nom du nœud | La longueur d’un nom de nœud doit être de 150 octets ou moins. Les noms de nœud de plus de 150 octets doivent être raccourcis pour être &lt;= 150 octets afin d’être pris en charge par l’entrepôt de nœuds Document dans AEM as a Cloud Service. Les assimilations échouent si ces noms de nœuds longs ne sont pas corrigés. |
| Contenu dans des chemins immuables | L’outil de transfert de contenu ne peut pas être utilisé pour migrer le contenu dans des chemins immuables. Pour transférer le contenu de `/etc`, seuls certains chemins `/etc` peuvent être sélectionnés, mais uniquement pour prendre en charge [AEM Forms vers AEM Forms as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/migrate-to-forms-as-a-cloud-service.html?lang=fr#paths-of-various-aem-forms-specific-assets). Pour tous les autres cas d’utilisation, reportez-vous à la section [Restructuration des référentiels communs](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/restructuring/all-repository-restructuring-in-aem-6-4.html?lang=fr#restructuring) pour en savoir plus sur la restructuration des référentiels. |
| Valeur de propriété de noeud dans MongoDB | Les valeurs des propriétés de noeud stockées dans MongoDB ne doivent pas dépasser 16 Mo. Cela est appliqué par MongoDB. Les ingérations échouent si des valeurs de propriété sont supérieures à cette limite. Avant d’exécuter une extraction, exécutez-la. [oak-run](https://repo1.maven.org/maven2/org/apache/jackrabbit/oak-run/1.38.0/oak-run-1.38.0.jar) script. Vérifiez toutes les valeurs de propriété volumineuses et validez si elles sont nécessaires. Ceux qui dépassent 16 Mo devront être convertis en valeurs binaires. |

## Et après ? {#whats-next}

Une fois que vous avez examiné les conditions préalables et déterminé si vous pouvez utiliser l’outil de transfert de contenu dans votre projet de migration, reportez-vous à la section [Conseils et bonnes pratiques relatives à l’utilisation de l’outil de transfert de contenu](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html?lang=en).
