---
title: Questions fréquentes sur les fonctionnalités OpenAPI de Dynamic Media
description: Questions fréquentes sur les fonctionnalités OpenAPI de Dynamic Media
role: User
exl-id: 3450e050-4b0b-4184-8e71-5e667d9ca721
source-git-commit: ed7331647ea2227e6047e42e21444b743ee5ce6d
workflow-type: tm+mt
source-wordcount: '1546'
ht-degree: 2%

---

# Questions fréquentes sur les fonctionnalités OpenAPI de Dynamic Media {#new-dynaminc-media-apis-frequently-asked-questions}

| [Bonnes pratiques de recherche](/help/assets/search-best-practices.md) | [Bonnes pratiques relatives aux métadonnées](/help/assets/metadata-best-practices.md) | [Hub de contenus](/help/assets/product-overview.md) | [Fonctionnalités Dynamic Media avec OpenAPI](/help/assets/dynamic-media-open-apis-overview.md) | [Documentation de développement pour AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

>[!AVAILABILITY]
>
>Le guide des fonctionnalités de Dynamic Media avec OpenAPI est désormais disponible au format PDF. Téléchargez l’intégralité du guide et utilisez l’assistant Adobe Acrobat AI pour répondre à vos requêtes.
>
>[!BADGE Dynamic Media avec OpenAPI Feature PDF ]{type=Informative url="https://helpx.adobe.com/content/dam/help/en/experience-manager/aem-assets/dynamic-media-with-openapi-capabilities.pdf"}

+++**Toutes les ressources du référentiel as a Cloud Service Experience Manager Assets sont-elles disponibles pour la recherche et la diffusion à l’aide de Dynamic Media avec des fonctionnalités OpenAPI ?**

Non, seule la [version approuvée et la dernière version des ressources](/help/assets/approve-assets.md) est disponible pour la recherche et la diffusion à l’aide des fonctionnalités Dynamic Media avec OpenAPI, ce qui assure la cohérence de la marque sur tous les canaux et applications.

+++

+++**Comment les administrateurs peuvent-ils marquer les nouvelles ressources et les ressources existantes ajoutées à un dossier comme approuvées ?**

L’état d’une ressource dans Experience Manager Assets est régi par la propriété `jcr:content/metadata/dam:status` . Les valeurs de cette propriété peuvent être les suivantes :

* Approuvé

* Refusé

* Modifications demandées

Experience Manager Assets distingue l’état Approuvé à l’aide d’une icône approuvée disponible sur la carte de la ressource, comme illustré dans les images suivantes pour les vues d’administrateur et de ressource :

**URL d’administration**

![Ressources approuvées dans la vue d’administration](/help/assets/assets/approved-assets-thumbs-up.png)

**Vue Assets**

![Ressources approuvées dans la vue Assets](/help/assets/assets/approved-assets-thumbs-up-assets-view.png)


Pour approuver toutes les ressources d’un dossier, reportez-vous aux instructions sur la [validation en masse des ressources dans un dossier](/help/assets/approve-assets.md#bulk-approve-assets). Il y a aussi une vidéo qui montre l&#39;ensemble du processus.

Après avoir configuré un dossier pour l’approbation en bloc, toutes les nouvelles ressources ajoutées au dossier sont automatiquement approuvées. Toutes les ressources existantes sont approuvées après le retraitement des ressources. Voir [Retraitement des ressources numériques](/help/assets/reprocessing.md) pour obtenir des instructions sur la manière de retraiter les ressources. Si vous copiez ou déplacez des ressources non approuvées à partir d’un autre dossier, vous devez [retraiter les ressources](/help/assets/reprocessing.md).

La ressource est marquée comme `Rejected` si l’administrateur spécifie les valeurs `Rejected` ou `Changes requested`. Experience Manager Assets distingue l’état Rejeté à l’aide de ![Rejeter Assets](/help/assets/assets/do-not-localize/reject-assets.svg) disponible sur la carte de ressource dans la vue Admin.

De même, Experience Manager Assets distingue l’état Refusé dans la vue Assets à l’aide de l’état Refusé suivant sur la carte de la ressource :

![Ressources rejetées dans la vue Assets](/help/assets/assets/rejected-assets-admin-view.png)


+++

+++**Comment pouvez-vous utiliser l’identifiant utilisateur ou l’identifiant de groupe Adobe IMS (Adobe Identity Management Services) pour définir les rôles sur les ressources dans la vue d’administration Experience Manager, afin de sécuriser l’expérience de diffusion et de recherche ?**

Les utilisateurs nécessitant l’accès à l’environnement de création Experience Manager sont gérés en tant qu’utilisateurs Adobe IMS dans l’Admin Console d’Adobe. Pour plus d’informations sur ce que sont les utilisateurs Adobe IMS et sur la façon dont ils sont accessibles et gérés en Admin Console, voir [Utilisateurs Adobe IMS](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/adobe-ims-users.html?lang=en).

+++

+++**Pouvez-vous approuver plusieurs ressources simultanément dans un dossier ?**

Oui, vous pouvez approuver plusieurs ressources dans un dossier simultanément.

Exécutez les étapes suivantes pour approuver plusieurs ressources simultanément dans [!DNL Experience Manager Assets Admin view] :

1. Sélectionnez la ou les ressources et cliquez sur **[!UICONTROL Propriétés]**.
1. Dans l’onglet **[!UICONTROL Basic]**, faites défiler l’écran jusqu’à **[!UICONTROL Review Status]**.
1. Remplacez l’état de révision par **[!UICONTROL Approuvé]**.
1. Cliquez sur **[!UICONTROL Enregistrer et fermer]**.

De même, pour approuver plusieurs ressources simultanément dans un dossier dans la vue Assets :

1. Sélectionnez la ou les ressources, puis cliquez sur **[!UICONTROL Modifier les métadonnées en bloc]**.

1. Sélectionnez **[!UICONTROL Approuvé]** dans le champ **[!UICONTROL État]** disponible dans la section [!UICONTROL Propriétés] du volet de droite.

1. Cliquez sur **[!UICONTROL Enregistrer]**.


+++

+++**Comment sécuriser la diffusion des ressources et rechercher les API OpenAPI Dynamic Media ?**

La gouvernance centrale des ressources dans Experience Manager permet aux administrateurs de gestion des actifs numériques ou aux responsables de marque de gérer l’accès aux ressources. Ils peuvent restreindre l’accès en configurant les rôles ou en définissant l’heure d’activation et de désactivation pour les ressources approuvées du côté création, en particulier sur l’instance d’auteur AEM as a Cloud Service.

Les utilisateurs finaux qui recherchent ou utilisent des URL de diffusion peuvent accéder à des ressources restreintes lorsqu’ils réussissent le processus d’autorisation.

Pour plus d’informations, voir [Limitation de l’accès aux ressources dans Experience Manager](restrict-assets-delivery.md#authoring).

+++

+++**Comment obtenir des autorisations pour modifier l’état d’approbation d’une ressource ?**

En tant qu’utilisateur DAM, vous ne disposez peut-être pas des autorisations nécessaires pour [approuver les ressources](approve-assets.md#approve-assets). Pour obtenir les autorisations nécessaires pour modifier l’état d’approbation d’une ressource, les administrateurs peuvent modifier le schéma de métadonnées par défaut ou tout autre schéma de métadonnées appliqué au dossier de ressources afin de fournir des autorisations de modification au champ **[!UICONTROL État de la révision]**. Pour plus d’informations, voir [Comment désactiver la modification du champ État de la révision](approve-assets.md#configuration) .

+++

+++**En quoi les fonctionnalités de Dynamic Media avec OpenAPI diffèrent de la solution Dynamic Media ?**

Dynamic Media avec des fonctionnalités OpenAPI et Dynamic Media représentent des solutions distinctes, chacune offrant ses fonctionnalités de diffusion spécialisées. Il est impératif de passer en revue minutieusement vos exigences spécifiques afin de déterminer la solution la plus adaptée à vos besoins.

Les instructions générales d’Adobe consistent à utiliser Dynamic Media avec la pile OpenAPI pour tous les cas d’utilisation d’intégration (applications propriétaires ou tierces). S’il existe déjà une intégration avec la pile Dynamic Media, nous vous recommandons de ne pas la modifier, car les URL de la pile OpenAPI sont différentes dans leur structure. Pour tous les cas d’utilisation de nouvelles intégrations, utilisez la pile OpenAPI. Si votre cas d’utilisation nécessite des modificateurs avancés non disponibles avec la pile OpenAPI, évitez la pile OpenAPI jusqu’à ce que l’Adobe comble l’écart. Même pour une diffusion native de base à partir des Cloud Service AEM Assets, la pile OpenAPI peut être évaluée tant que votre cas d’utilisation est couvert par les modificateurs disponibles avec la pile OpenAPI. En conclusion, Dynamic Media et Dynamic Media avec la pile OpenAPI peuvent coexister, selon la nature de votre cas d’utilisation.

Voici quelques-unes des principales différences entre Dynamic Media avec les fonctionnalités OpenAPI et Dynamic Media :

| Dynamic Media avec fonctionnalités OpenAPI | Dynamic Media |
|---|---|
| [Disponible uniquement avec Assets as a Cloud Service](/help/assets/dynamic-media-open-apis-overview.md#prerequisites-dynaminc-media-open-apis) | Également disponible avec On-premise ou Adobe Managed Services avec des étapes de configuration et de configuration supplémentaires. |
| [ Ensemble limité de modificateurs d’image pris en charge, tels que la largeur, la hauteur, la rotation, le pivotement, la qualité et le format ](/help/assets/deliver-assets-apis.md) | Jeu riche de modificateurs d’image disponibles |
| [Diffusion de ressources limitée basée sur les utilisateurs, les rôles, la date et l’heure](/help/assets/restrict-assets-delivery.md) | Les Assets publiées sur Dynamic Media sont accessibles à tous les utilisateurs |
| La plupart des développeurs connaissent les spécifications d’OpenAPI. L’extensibilité d’AEM Assets devient très simple en utilisant [Micro-Frontend Asset Selector](/help/assets/overview-asset-selector.md). | API SOAP, qui deviennent un obstacle lors du développement de personnalisations de l’intégration. |
| Toute modification apportée aux ressources approuvées dans la gestion des ressources numériques, y compris les mises à jour de version et les modifications de métadonnées, est automatiquement répercutée dans les URL de diffusion. Avec une valeur TTL (short Time-to-Live) de 10 minutes configurée pour Dynamic Media avec des fonctionnalités OpenAPI via CDN, les mises à jour deviennent visibles dans toutes les interfaces de création et de publication en moins de 10 minutes. | TTL CDN recommandé de 10 heures. Vous pouvez remplacer la valeur TTL à l’aide de l’action d’invalidation du cache. |
| Seules les ressources approuvées sont disponibles pour la diffusion des ressources vers les applications en aval, ce qui permet d’activer les ressources approuvées par marque dans les expériences numériques. | Toutes les mises à jour apportées à une ressource publiée par Dynamic Media sont publiées automatiquement sans processus d’approbation, ce qui ne garantit pas l’utilisation de ressources approuvées par la marque dans les expériences numériques. |
| Rapports d’utilisation basés sur le nombre de ressources diffusées. Cette fonctionnalité sera bientôt disponible. | Les rapports d’utilisation ne sont pas disponibles. Cette fonctionnalité sera bientôt disponible. |
| Les Assets marquées comme étant expirées sur le référentiel as a Cloud Service Assets ne sont plus disponibles pour les applications en aval. | Aucune expiration de ressource inhérente. Une ressource reste publique jusqu’à ce qu’elle soit supprimée du référentiel AEM as a Cloud Service. |
| Ne prend pas en charge les paramètres d’image prédéfinis et les fonctionnalités de recadrage intelligent de vidéo. | Prend en charge les paramètres d’image prédéfinis et les fonctionnalités de recadrage intelligent de vidéo. |
| Codes vidéo dynamiques, qui garantissent que les meilleurs codes sont diffusés en fonction de la vidéo d’entrée. Aucune configuration n’est requise pour la diffusion vidéo native. | Standard 3 code indépendamment de la vidéo d’entrée (peut avoir une incidence sur les performances de diffusion vidéo). Vous devez configurer manuellement différents codes pour différents débits vidéo. |
| Difficile de deviner les URL basées sur UID de la ressource (obscurcissement des URL activé), mais optimisation de l’optimisation pour les moteurs de recherche. | L’obscurcissement des URL n’est disponible que pour les paramètres de requête d’URL. Les Assets ID (noms de ressources) dans les URL sont reconnaissables. |

+++

+++**Comment Dynamic Media avec les fonctionnalités OpenAPI résout les limites de la fonctionnalité Assets connectée ?**

Le tableau ci-dessous présente les principales différences entre les deux solutions :

| Dynamic Media avec fonctionnalités OpenAPI | Ressources connectées |
|---|---|
| Assets sur le déploiement DAM distant est disponible sur AEM as a Cloud Service. | Assets sur le déploiement DAM distant peut être disponible sur AEM as a Cloud Service ou Adobe Managed Services. |
| Les fichiers binaires des ressources ne sont pas copiés lorsque des ressources sur un déploiement DAM distant sont disponibles dans une instance AEM Sites. | Les fichiers binaires des ressources sont copiés lorsque des ressources sur un déploiement DAM distant sont disponibles sur une instance AEM Sites. |
| Prise en charge de tous les types de format de ressource pris en charge par AEM Assets. | Pas de prise en charge des vidéos. |
| Vous pouvez utiliser Dynamic Media sur le déploiement Sites local lors de la récupération de ressources à partir du déploiement DAM distant. | Dynamic Media sur le déploiement Sites local est en lecture seule. |
| Aucune restriction sur le nombre d’instances AEM Sites connectées à un déploiement DAM distant. Vous pouvez [restreindre l’accès aux ressources sur l’instance Sites en configurant des rôles](/help/assets/restrict-assets-delivery.md) pour les ressources approuvées sur DAM distant. | Restriction afin de ne pas connecter plus de 4 instances AEM Sites au déploiement DAM distant. Un nombre accru nécessite des tests supplémentaires. |
| Le sélecteur de ressources et Dynamic Media avec les fonctionnalités OpenAPI sont extensibles pour permettre des intégrations personnalisées. | Les API Assets connectées ne sont pas extensibles pour autoriser les intégrations personnalisées. |
| Toutes les modifications apportées aux ressources approuvées disponibles lors du déploiement DAM distant, y compris les mises à jour de version et les modifications de métadonnées, sont automatiquement répercutées sur l’instance Sites dans une valeur TTL (short Time-to-Live) de 10 minutes. | Les mises à jour des ressources sur le déploiement DAM distant sont gérées automatiquement via les événements de cycle de vie, mais prennent beaucoup plus de temps que dans Dynamic Media avec les fonctionnalités OpenAPI. |
| Les métadonnées des ressources sur DAM distant sont également disponibles sur l’instance AEM Sites. | Les métadonnées des ressources sur DAM distant ne sont pas disponibles sur l’instance AEM Sites. |

+++
