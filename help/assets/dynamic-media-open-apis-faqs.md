---
title: Questions fréquentes sur Dynamic Media avec fonctionnalités OpenAPI
description: Questions fréquentes sur Dynamic Media avec fonctionnalités OpenAPI
role: User
exl-id: 3450e050-4b0b-4184-8e71-5e667d9ca721
source-git-commit: c3bac140c2e0b33cfc206cda7c0591fc75a47a1f
workflow-type: tm+mt
source-wordcount: '1609'
ht-degree: 94%

---

# Questions fréquentes sur Dynamic Media avec fonctionnalités OpenAPI {#new-dynaminc-media-apis-frequently-asked-questions}

## Toutes les ressources du référentiel Experience Manager Assets as a Cloud Service sont-elles disponibles pour la recherche et la diffusion à l’aide de Dynamic Media avec des fonctionnalités OpenAPI ? {#assets-available-for-search}

Non, seule la [version approuvée et la dernière version des ressources](/help/assets/approve-assets.md) est disponible pour la recherche et la diffusion à l’aide des fonctionnalités Dynamic Media avec OpenAPI, ce qui assure la cohérence de la marque sur tous les canaux et applications.


## Comment les administrateurs et administratrices peuvent-ils ou elles marquer les nouvelles ressources et les ressources existantes ajoutées à un dossier comme approuvées ? {#add-assets-to-folder-as-approved}

Le statut d’une ressource dans Experience Manager Assets est régi par la propriété `jcr:content/metadata/dam:status`. Les valeurs de cette propriété peuvent être les suivantes :

* Approuvé

* Refusé

* Modifications demandées

Experience Manager Assets distingue le statut Approuvé à l’aide d’une icône Approuvé disponible sur la carte de la ressource, comme illustré dans les images suivantes pour les vues d’administration et de ressource :

**URL d’administration**

![Ressources approuvées dans la vue d’administration](/help/assets/assets/approved-assets-thumbs-up.png)

**Vue Assets**

![Ressources approuvées dans la vue Assets](/help/assets/assets/approved-assets-thumbs-up-assets-view.png)


Pour approuver toutes les ressources d’un dossier, reportez-vous aux instructions sur la [validation en masse des ressources dans un dossier](/help/assets/approve-assets.md#bulk-approve-assets). Il y a aussi une vidéo qui montre l’ensemble du processus.

Après avoir configuré un dossier pour l’approbation en masse, toutes les nouvelles ressources ajoutées au dossier sont automatiquement approuvées. Toutes les ressources existantes sont approuvées après le retraitement des ressources. Voir [Retraitement des ressources numériques](/help/assets/reprocessing.md) pour obtenir des instructions sur la manière de retraiter les ressources. Si vous copiez ou déplacez des ressources non approuvées à partir d’un autre dossier, vous devez [retraiter les ressources](/help/assets/reprocessing.md).

La ressource est marquée comme `Rejected` si l’administrateur ou l’administratrice spécifie les valeurs `Rejected` ou `Changes requested`. Experience Manager Assets distingue le statut Rejeté à l’aide de ![Rejeter des ressources](/help/assets/assets/do-not-localize/reject-assets.svg) disponible sur la carte de ressource dans la vue Admin.

De même, Experience Manager Assets distingue le statut Rejeté dans la vue Assets à l’aide du statut Rejeté suivant sur la carte de ressource :

![Ressources rejetées dans la vue Assets](/help/assets/assets/rejected-assets-admin-view.png)


## Comment pouvez-vous utiliser l’identifiant d’utilisateur ou d’utilisatrice ou l’identifiant de groupe Adobe IMS (Adobe Identity Management Services) pour définir les rôles sur les ressources dans la vue d’administration Experience Manager, afin de sécuriser l’expérience de diffusion et de recherche ? {#set-roles-secure-delivery-search}

Les utilisateurs et utilisatrices demandant l’accès au service de l’instance de création AEM sont gérés en tant qu’utilisateurs et utilisatrices Adobe IMS dans Adobe Admin Console. Découvrez ce que sont les utilisateurs et utilisatrices Adobe IMS et comment ils sont accessibles et gérés dans Admin Console en consultant [Utilisateurs et utilisatrices Adobe IMS](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/adobe-ims-users.html?lang=fr).


## Pouvez-vous approuver plusieurs ressources simultanément dans un dossier ? {#approve-multiple-assets-in-folder}

Oui, vous pouvez approuver plusieurs ressources dans un dossier simultanément.

Exécutez les étapes suivantes pour approuver plusieurs ressources simultanément dans [!DNL Experience Manager Assets Admin view] :

1. Sélectionnez les ressources et cliquez sur **[!UICONTROL Propriétés]**.
1. Dans l’onglet **[!UICONTROL De base]**, faites défiler l’écran jusqu’à **[!UICONTROL Statut de révision]**.
1. Remplacez le statut de révision par **[!UICONTROL Approuvé]**.
1. Cliquez sur **[!UICONTROL Enregistrer et fermer]**.

De même, pour approuver plusieurs ressources simultanément dans un dossier dans la vue Assets, procédez comme suit :

1. Sélectionnez la ou les ressources, puis cliquez sur **[!UICONTROL Modifier les métadonnées en masse]**.

1. Sélectionnez **[!UICONTROL Approuvé]** dans le champ **[!UICONTROL Statut]** disponible dans la section [!UICONTROL Propriétés] du volet de droite.

1. Cliquez sur **[!UICONTROL Enregistrer]**.


## Comment sécuriser la diffusion des ressources et rechercher Dynamic Media avec les API ouvertes ? {#secure-asset-delivery}

La gouvernance centrale des ressources dans Experience Manager permet aux administrateurs et administratrices de gestion des ressources numériques ou aux personnes responsables de marque de gérer l’accès aux ressources. Ils peuvent restreindre l’accès en configurant les rôles ou en définissant l’heure d’activation et de désactivation pour les ressources approuvées du côté création, en particulier sur l’instance de création d’AEM as a Cloud Service.

Les utilisateurs et utilisatrices finaux qui recherchent ou utilisent des URL de diffusion peuvent accéder à des ressources restreintes lorsqu’ils réussissent le processus d’autorisation.

Pour plus d’informations, consultez [Restreindre l’accès aux ressources dans Experience Manager](restrict-assets-delivery.md#authoring).


## Comment obtenir des autorisations pour modifier le statut d’approbation d’une ressource ? {#permissions-edit-approval-status}

En tant qu’utilisateur ou utilisatrice de la gestion des ressources numériques, vous ne disposez peut-être pas des autorisations nécessaires pour [approuver les ressources](approve-assets.md#approve-assets). Afin d’obtenir les autorisations nécessaires pour modifier le statut d’approbation d’une ressource, les administrateurs et administratrices peuvent modifier le schéma de métadonnées par défaut ou tout autre schéma de métadonnées appliqué au dossier de ressources afin de fournir des autorisations de modification au champ **[!UICONTROL Statut de révision]**. Pour plus d’informations, voir [Comment désactiver la modification du champ Statut de révision](approve-assets.md#configuration).


## Quelle est la taille de fichier prise en charge pour les vidéos ? {#supported-file-formats-videos}

Dynamic Media avec OpenAPI prend en charge les vidéos de forme longue. Les vidéos de forme longue peuvent prendre en charge jusqu’à 50 Go et 2 heures.


## En quoi Dynamic Media avec les fonctionnalités OpenAPI diffère de la solution Dynamic Media ? {#dynamic-media-and-dynamic-media-with-openapi-differences}

Dynamic Media avec des fonctionnalités OpenAPI et Dynamic Media représentent des solutions distinctes, chacune offrant ses fonctionnalités de diffusion spécialisées. Il est impératif de passer minutieusement en revue vos exigences spécifiques afin de déterminer la solution la plus adaptée à vos besoins.

Les instructions générales d’Adobe consistent à utiliser Dynamic Media avec la pile OpenAPI pour tous les cas d’utilisation d’intégration (applications propriétaires ou tierces). S’il existe déjà une intégration avec la pile Dynamic Media, nous vous recommandons de ne pas la modifier, car les URL de la pile OpenAPI sont différentes dans leur structure. Pour tous les cas d’utilisation de nouvelles intégrations, utilisez la pile OpenAPI. Si votre cas d’utilisation nécessite des modificateurs avancés non disponibles avec la pile OpenAPI, évitez la pile OpenAPI jusqu’à ce qu’Adobe comble cette lacune. Même pour une diffusion native de base à partir d’AEM Assets Cloud Service, la pile OpenAPI peut être évaluée tant que votre cas d’utilisation est couvert par les modificateurs disponibles avec la pile OpenAPI. En conclusion, Dynamic Media et Dynamic Media avec la pile OpenAPI peuvent coexister, selon la nature de votre cas d’utilisation.

Voici quelques-unes des principales différences entre Dynamic Media avec les fonctionnalités OpenAPI et Dynamic Media :

| Dynamic Media avec fonctionnalités OpenAPI | Dynamic Media |
|---|---|
| [Disponible uniquement avec Assets as a Cloud Service](/help/assets/dynamic-media-open-apis-overview.md#prerequisites-dynaminc-media-open-apis) | Également disponible avec On-premise ou Adobe Managed Services avec des étapes de configuration et d’approvisionnement supplémentaires. |
| [Ensemble riche de modificateurs d’image pris en charge, tels que la largeur, la hauteur, la rotation, le retournement, la qualité et le format](/help/assets/deliver-assets-apis.md) | Riche ensemble de modificateurs d’image disponibles |
| [Diffusion de ressources limitée basée sur les utilisateurs et utilisatrices, les rôles, la date et l’heure](/help/assets/restrict-assets-delivery.md) | Les ressources publiées sur Dynamic Media sont accessibles à tous les utilisateurs et utilisatrices. |
| La plupart des développeurs et développeuses connaissent les spécifications d’OpenAPI. L’extensibilité d’AEM Assets devient très simple en utilisant le [sélecteur de ressources micro front-end](/help/assets/overview-asset-selector.md). | API SOAP, qui deviennent un obstacle lors du développement de personnalisations de l’intégration. |
| Toute modification apportée aux ressources approuvées dans la gestion des ressources numériques, y compris les mises à jour de version et les modifications de métadonnées, est automatiquement répercutée dans les URL de diffusion. Avec une durée de vie (Time To Live, TTL) de 10 minutes configurée pour Dynamic Media avec fonctionnalités OpenAPI via CDN, les mises à jour deviennent visibles dans toutes les interfaces de création et de publication en moins de 10 minutes. | La durée de vie (TTL) recommandée du réseau CDN est de 10 heures. Vous pouvez remplacer la valeur TTL à l’aide de l’action d’invalidation du cache. |
| Seules les ressources approuvées sont disponibles pour la diffusion des ressources vers les applications en aval, ce qui permet d’activer les ressources approuvées par marque dans les expériences numériques. | Toutes les mises à jour apportées à une ressource publiée par Dynamic Media sont publiées automatiquement sans processus d’approbation, ce qui ne garantit pas l’utilisation de ressources approuvées par la marque dans les expériences numériques. |
| Rapports d’utilisation basés sur le nombre de ressources diffusées. Cette fonctionnalité sera bientôt disponible. | Les rapports d’utilisation ne sont pas disponibles. Cette fonctionnalité sera bientôt disponible. |
| Les ressources marquées comme ayant expiré sur le référentiel Assets as a Cloud Service ne sont plus disponibles pour les applications en aval. | Aucune expiration de ressource inhérente. Une ressource reste publique jusqu’à ce qu’elle soit supprimée du référentiel AEM as a Cloud Service. |
| Ne prend pas en charge les fonctionnalités de recadrage intelligent de vidéo. | Prend en charge les fonctionnalités de recadrage intelligent vidéo. |
| Codes de vidéo dynamique, ce qui garantit que les meilleurs codes sont diffusés en fonction de la vidéo d’entrée. Aucune configuration n’est requise pour la diffusion vidéo native. | Code Standard 3 indépendamment de la vidéo d’entrée (peut avoir une incidence sur les performances de diffusion vidéo). Vous devez configurer manuellement différents codes pour différents débits vidéo. |
| Active des URL sécurisées et obscurcies à l’aide d’UID de ressource sans compromettre l’optimisation du moteur de recherche. | L’obscurcissement des URL n’est disponible que pour les paramètres de requête d’URL. Les identifiants de ressources (noms de ressources) dans les URL sont reconnaissables. |


## Comment Dynamic Media avec les fonctionnalités OpenAPI résout les limites de la fonctionnalité de ressources connectées ? {#dynamic-media-openapi-addresses-connected-assets-limitations}

Le tableau ci-dessous présente les principales différences entre les deux solutions :

| Dynamic Media avec fonctionnalités OpenAPI | Ressources connectées |
|---|---|
| Les ressources sur le déploiement DAM distant sont disponibles sur AEM as a Cloud Service. | Les ressources sur le déploiement DAM distant peuvent être disponibles sur AEM as a Cloud Service ou Adobe Managed Services. |
| Les fichiers binaires des ressources ne sont pas copiés lorsque des ressources sur un déploiement DAM distant sont disponibles dans une instance AEM Sites. | Les fichiers binaires des ressources sont copiés lorsque des ressources sur un déploiement DAM distant sont disponibles sur une instance AEM Sites. |
| Prise en charge de tous les types de format de ressource pris en charge par AEM Assets. | Pas de prise en charge pour les vidéos. |
| Vous pouvez utiliser Dynamic Media sur le déploiement Sites local lors de la récupération de ressources à partir du déploiement DAM distant. | Dynamic Media sur le déploiement Sites local est en lecture seule. |
| Aucune restriction sur le nombre d’instances AEM Sites connectées à un déploiement DAM distant. Vous pouvez [restreindre l’accès aux ressources sur l’instance Sites en configurant des rôles](/help/assets/restrict-assets-delivery.md) pour les ressources approuvées sur DAM distant. | Restriction afin de ne pas connecter plus de 4 instances AEM Sites au déploiement DAM distant. Un nombre accru nécessite des tests supplémentaires. |
| Le sélecteur de ressources et Dynamic Media avec les fonctionnalités OpenAPI sont extensibles pour permettre des intégrations personnalisées. | Les API Assets connectées ne sont pas extensibles pour autoriser les intégrations personnalisées. |
| Toutes les modifications apportées aux ressources approuvées disponibles lors du déploiement DAM distant, y compris les mises à jour de version et les modifications de métadonnées, sont automatiquement répercutées sur l’instance Sites avec une valeur TTL (durée de vie) courte de 10 minutes. | Les mises à jour des ressources sur le déploiement DAM distant sont gérées automatiquement via les événements de cycle de vie, mais prennent beaucoup plus de temps que dans Dynamic Media avec les fonctionnalités OpenAPI. |
| Les métadonnées des ressources sur DAM distant sont également disponibles sur l’instance AEM Sites. | Les métadonnées des ressources sur DAM distant ne sont pas disponibles sur l’instance AEM Sites. |

## Certains modificateurs sont marqués comme étant en disponibilité limitée. Comment commencer à les utiliser ? {#use-limited-availability-modifiers}

Pour activer l’utilisation en production de [modificateurs en disponibilité limitée](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/) sur votre compte :

1. [Créez un dossier d’assistance Adobe à l’aide d’Admin Console](https://helpx.adobe.com/fr/enterprise/using/support-for-experience-cloud.html).

1. Indiquez les informations suivantes dans le cas d’assistance Adobe :

   * Organisation IMS

   * Liste des modificateurs à activer


## Comment tester des modificateurs expérimentaux ? {#modifiers-not-generally-available}

Vous pouvez tester n’importe quel modificateur, qui n’est généralement pas disponible via les API expérimentales. Par exemple, &lt;/adobe/experiment/advancemodifiers-expires-YYYYMMDD/assets>
Cliquez ici pour en savoir plus sur l’utilisation des [API expérimentales](https://developer.adobe.com/experience-cloud/experience-manager-apis/guides/how-to/#experimental-apis) et la [ liste complète des modificateurs](https://developer.adobe.com/experience-cloud/experience-manager-apis/).
