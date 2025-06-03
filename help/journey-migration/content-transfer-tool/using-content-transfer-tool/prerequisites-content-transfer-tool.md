---
title: Conditions préalables pour l’outil de transfert de contenu
description: Familiarisez-vous avec les conditions préalables requises pour l’outil de transfert de contenu
exl-id: 41a9cff1-4d89-480c-b9fc-5e8efc2a0705
feature: Migration
role: Admin
source-git-commit: 3e3d018dfd4babce9abef858e487bf1c116ed3a6
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 91%

---


# Conditions préalables pour l’outil de transfert de contenu {#prerequisites}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_prereqs"
>title="Points importants concernant l’utilisation de l’outil de transfert de contenu"
>abstract="Examinez les points à prendre en compte lors de l’utilisation de l’outil de transfert de contenu, notamment les versions Java™ et AEM, les types de magasins de données pris en charge, les considérations relatives aux groupes d’utilisateurs, etc."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/prerequisites-content-transfer-tool.html?lang=fr" text="Points importants concernant l’utilisation de l’outil de transfert de contenu"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html?lang=fr#best-practices" text="Bonnes pratiques et consignes"

Le tableau suivant résume les conditions préalables requises pour l’utilisation de l’outil de transfert de contenu.

Consultez toutes les considérations ci-dessous :

| Considérations | Éléments actuellement pris en charge |
|--------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Version d’AEM | L’outil de transfert de contenu ne peut être exécuté que sur AEM version 6.3 ou ultérieure. |
| Taille de l’entrepôt de segments | Un référentiel existant qui contient moins de 750 millions de nœuds JCR et jusqu’à 500 Go (taille compactée en ligne) sur *Auteur* et 50 Go sur *Publier* est actuellement pris en charge. Créez un ticket d’assistance auprès de l’assistance clientèle d’Adobe pour discuter des options relatives à la taille de la banque de segments au-dessus de ces limites. |
| Taille totale du référentiel de contenu <br>*(magasin de segments + magasin de données)* | L’outil de transfert de contenu est conçu pour transférer jusqu’à 20 téraoctets de contenu pour le type de magasin de données Magasin de données de fichiers. Tout ce qui dépasse 20 téraoctets n’est actuellement pas pris en charge. Créez un ticket de support auprès de l’assistance clientèle d’Adobe pour discuter des options relatives au contenu de plus de 20 téraoctets. <br>Pour accélérer considérablement le processus de transfert de contenu pour les référentiels volumineux, une étape de [précopie](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=fr#setting-up-pre-copy-step) facultative peut être utilisée. Ce processus s’applique aux types de magasin de données Magasin de données de fichiers, Amazon S3 et magasin de données Azure. Pour Amazon S3 et le magasin de données Azure, les tailles de référentiel supérieures à 20 téraoctets sont prises en charge. |
| Taille totale de l’index Lucene | La taille totale de l’index Lucene pris en charge, `/oak:index/lucene` et `/oak:index/damAssetLucene` non compris, est de 25 Go au maximum. Créez un ticket d’assistance auprès de l’assistance clientèle d’Adobe pour discuter des options relatives à la taille d’index supérieure à cette limite. |
| Contenu dans des chemins immuables | L’outil de transfert de contenu ne peut pas être utilisé pour migrer le contenu dans des chemins immuables. Pour transférer du contenu depuis `/etc`, vous pouvez sélectionner certains chemins `/etc`, mais uniquement pour la prise en charge d’[AEM Forms vers AEM Forms as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/setup-configure-migrate/migrate-to-forms-as-a-cloud-service.html#paths-of-various-aem-forms-specific-assets?lang=fr). Pour tous les autres cas d’utilisation, reportez-vous à la section [Restructuration des référentiels communs](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/restructuring/all-repository-restructuring-in-aem-6-5.html?lang=fr) pour en savoir plus sur la restructuration des référentiels. |
| Valeur de propriété de nœud dans MongoDB | La valeur des propriétés de nœud stockées dans MongoDB ne doit pas dépasser 16 Mo. Cette règle est exigée par MongoDB. Les ingestions échouent si une des valeurs de propriété est supérieure à cette limite. Avant d’exécuter une extraction, exécutez le script [oak-run](https://repo1.maven.org/maven2/org/apache/jackrabbit/oak-run/1.38.0/oak-run-1.38.0.jar). Vérifiez toutes les valeurs de propriété de taille importante et validez si elles sont nécessaires. Celles qui dépassent 16 Mo doivent être converties en valeurs binaires. |

## Prochaines étapes {#whats-next}

Une fois que vous avez examiné les conditions préalables et déterminé si vous pouvez utiliser l’outil de transfert de contenu dans votre projet de migration, reportez-vous à la section [Bonnes pratiques et instructions pour l’utilisation de l’outil de transfert de contenu](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html?lang=fr).