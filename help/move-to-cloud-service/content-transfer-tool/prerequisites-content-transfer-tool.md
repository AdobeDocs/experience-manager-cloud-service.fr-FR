---
title: Conditions préalables pour l’outil de transfert de contenu
description: Conditions préalables pour l’outil de transfert de contenu
exl-id: ef6d0e1a-0ed2-4485-adab-df6e0cf3ac4d
source-git-commit: ac44eeda36a7c8e1232bfd3275fb872e6523f87d
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 14%

---

# Conditions préalables pour l’outil de transfert de contenu {#prerequisites}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_prereqs"
>title="Points importants concernant l’utilisation de l’outil de transfert de contenu"
>abstract="Examinez les points importants à prendre en compte pour utiliser l’outil de transfert de contenu, notamment les versions Java et AEM, les types d’entrepôt de données pris en charge, les considérations relatives aux groupes d’utilisateurs, etc."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#pre-reqs" text="Points importants concernant l’utilisation de l’outil de transfert de contenu"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html?lang=fr#best-practices" text="Bonnes pratiques et consignes"

Le tableau suivant résume les conditions préalables requises pour l’utilisation de l’outil de transfert de contenu.

Veuillez consulter toutes les considérations ci-dessous :

| Considérations | Éléments actuellement pris en charge |
|--- |--- |
| Version d’AEM | L’outil de transfert de contenu ne peut être exécuté que sur AEM version 6.3 ou ultérieure. Pour pouvoir utiliser l’outil de transfert de contenu avec AEM version 6.2 ou antérieure, une mise à niveau statique du référentiel de contenu vers AEM 6.5 est requise. Il n’est pas nécessaire de mettre à niveau le code vers AEM 6.5 pour cela. |
| Taille de l’entrepôt de segments | Jusqu’à 83 Go sur *Auteur* et 31 Go sur *Publication* sont actuellement pris en charge. Créez un ticket d’assistance auprès de l’assistance clientèle d’Adobe pour discuter des options relatives à la taille de la boutique de segments au-dessus de ces limites. |
| Taille totale du référentiel de contenu <br>*(entrepôt de segments + entrepôt de données)* | L’outil de transfert de contenu est conçu pour transférer du contenu jusqu’à 10 To pour le type d’entrepôt de données basé sur les fichiers. Tout ce qui dépasse 10 To n’est actuellement pas pris en charge. Créez un ticket d’assistance auprès de l’assistance clientèle d’Adobe pour discuter des options relatives au contenu de plus de 10 To. <br>Pour les types d’entrepôt de données Amazon S3 et Azure Data Store, une étape de  [ ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=en#setting-up-pre-copy-step) copie préalable facultative peut être utilisée pour accélérer considérablement le processus de transfert de contenu et prendre en charge une taille de stockage de données supérieure à 10 To. |
| Taille totale de l’index | La taille totale de l’index de 25 Go au maximum est actuellement prise en charge. Créez un ticket d’assistance auprès de l’assistance clientèle d’Adobe pour discuter des options relatives à la taille d’index supérieure à cette limite. |
| Longueur du nom du noeud | La longueur d’un nom de noeud doit être de 150 octets ou moins. Les noms de noeud de plus de 150 octets doivent être raccourcis pour être &lt;= 150 octets afin d’être pris en charge par le magasin de noeuds Document dans AEM en tant que Cloud Service. Les assimilations échouent si ces noms de noeuds longs ne sont pas corrigés. |
| Contenu sur les chemins immuables | L’outil de transfert de contenu ne peut pas être utilisé pour migrer le contenu dans des chemins immuables. Pour transférer le contenu de `/etc`, seuls certains `/etc` chemins peuvent être sélectionnés, mais uniquement pour prendre en charge [AEM Forms vers AEM Forms as a3/>. ](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/migrate-to-forms-as-a-cloud-service.html?lang=en#paths-of-various-aem-forms-specific-assets) Pour tous les autres cas d’utilisation, reportez-vous à la section [Restructuration des référentiels communs](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/restructuring/all-repository-restructuring-in-aem-6-4.html?lang=en#restructuring) pour en savoir plus sur la restructuration des référentiels. |

## Et après ? {#whats-next}

Une fois que vous avez examiné les conditions préalables et déterminé si vous pouvez utiliser l’outil de transfert de contenu dans votre projet de migration, reportez-vous à la section [Bonnes pratiques et remarques supplémentaires](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md) lors de l’utilisation de l’outil de transfert de contenu.
