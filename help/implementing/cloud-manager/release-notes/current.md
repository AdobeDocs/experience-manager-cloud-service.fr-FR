---
title: Notes de mise à jour de Cloud Manager 2024.11.0 dans Adobe Experience Manager as a Cloud Service
description: Découvrez la version de Cloud Manager 2024.11.0 dans AEM as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: 87293526ca9c10a142bc1d1d3a35562b171da385
workflow-type: tm+mt
source-wordcount: '784'
ht-degree: 30%

---

# Notes de mise à jour de Cloud Manager 2024.11.0 dans Adobe Experience Manager as a Cloud Service {#release-notes}

Découvrez la version de Cloud Manager 2024.11.0 dans la version as a Cloud Service d’AEM (Adobe Experience Manager).

>[!NOTE]
>
>Consultez les [notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Dates de publication {#release-date}

La date de publication de Cloud Manager 2024.11.0 dans AEM as a Cloud Service est le 7 novembre 2024.

La prochaine version est prévue le 5 décembre 2024.

## Nouveautés {#what-is-new}

* Découvrez les dernières innovations Edge Delivery Services avec AEM Cloud Service, désormais disponible pour les explorations dans votre programme Sandbox. [En savoir plus](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-sandbox-programs.md#auto-creation) <!-- (CMGR-62319) -->
* La page Paramètres de domaine d’AEM Cloud Manager comprend désormais une fonction de recherche qui vous permet de localiser rapidement les domaines par nom. Vous pouvez saisir des mots-clés dans le champ de recherche pour filtrer et afficher les domaines correspondants, ce qui facilite la gestion efficace de plusieurs domaines. De plus, la page propose des filtres d’état, tels que **Vérifié** et **Non vérifié**, pour affiner davantage les résultats de la recherche. <!-- (CMGR-62615) -->

![Champ de recherche dans Paramètres du domaine](/help/implementing/cloud-manager/assets/domain-settings-search.png)

## Programme d’adoption précoce {#early-adoption}

Prenez part à notre programme d’adoption précoce de Cloud Manager afin de pouvoir tester certaines fonctionnalités à venir.

### Accueil AEM {#aem-home}

AEM Accueil propose un point de départ centralisé pour la gestion du contenu, des ressources et des sites dans Adobe Experience Manager. Conçu pour offrir une expérience personnalisée, AEM Accueil vous permet de naviguer sans problème dans l’écosystème AEM en fonction de vos rôles et objectifs. Il fournit des informations clés et des actions recommandées pour vous aider à atteindre vos objectifs de manière efficace. Grâce à une disposition claire et personnalisée, AEM Accueil vous permet d’accéder rapidement aux outils essentiels, ce qui vous permet d’offrir une expérience rationalisée et efficace dans toutes les fonctions d’AEM.

Disponible pour les utilisateurs précoces, AEM Home offre une expérience optimisée axée sur l’amélioration des workflows, la hiérarchisation des objectifs et la diffusion de résultats. L’opt-in vous permet d’influencer le développement d’AEM Home en fournissant des commentaires qui aident à façonner son avenir et à améliorer sa valeur pour l’ensemble de la communauté AEM.

Si vous souhaitez tester cette nouvelle fonctionnalité et partager vos commentaires, envoyez un email à [Grp-AemHome@adobe.com](mailto:Grp-AemHome@adobe.com) à partir de votre adresse électronique associée à votre Adobe ID. Veillez à inclure les informations suivantes :

* Le rôle qui correspond le mieux à votre profil : auteur de contenu, développeur, propriétaire d’entreprise, administrateur ou autre (fournissez une description).
* Votre surface d’accès principale AEM : AEM Sites, AEM Assets, AEM Forms, Cloud Manager ou Autre (décrivez-la).

### Apportez votre propre Git - avec prise en charge de GitLab et Bitbucket {#gitlab-bitbucket}

<!-- BOTH CS & AMS -->

La fonctionnalité **Apportez votre propre Git** a été étendue pour inclure la prise en charge de référentiels externes tels que GitLab et Bitbucket. Cette nouvelle prise en charge s’ajoute à la prise en charge existante des référentiels GitHub privés et d’entreprise. Lorsque vous ajoutez ces nouveaux référentiels, vous pouvez également les lier directement à vos pipelines. Vous pouvez héberger ces référentiels sur des plateformes cloud publiques ou dans votre infrastructure ou cloud privés. Cette intégration élimine également la nécessité d’une synchronisation constante du code avec le référentiel d’Adobe et permet de valider les requêtes d’extraction avant de les fusionner dans une branche principale.

Voir [Ajouter des référentiels externes dans Cloud Manager](/help/implementing/cloud-manager/managing-code/external-repositories.md).

![Boîte de dialogue Ajouter un référentiel](/help/implementing/cloud-manager/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>Actuellement, les contrôles de qualité du code des requêtes d’extraction prêts à l’emploi sont exclusifs aux référentiels hébergés par GitHub, mais une mise à jour permettant d’étendre cette fonctionnalité à d’autres fournisseurs Git est en cours.

Si vous souhaitez tester cette nouvelle fonctionnalité et faire part de vos commentaires, envoyez un e-mail à [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com) à partir de l’adresse e-mail associée à votre Adobe ID. Veillez à inclure la plateforme Git à utiliser et si vous utilisez une structure de référentiel privée/publique ou d’entreprise. —>


## Correctifs

* Une mise à jour récente corrigeait un problème dans SonarQube en raison duquel les mots de passe codés en dur n’étaient pas détectés dans certains cas. Le correctif inclut désormais une vérification de modèle étendue et s’aligne sur les normes de détection par défaut dans SonarQube. <!-- CMGR-62682 -->
* Lors de la mise à jour d’un certificat SSL dans Cloud Manager, une erreur inconnue s’affichait après avoir cliqué sur **[!UICONTROL Mettre à jour]** dans la boîte de dialogue **[!UICONTROL Afficher et mettre à jour le certificat SSL]**. <!-- CMGR-62848 -->
* Dans Cloud Manager, les mises à jour de certificat SSL échouaient avec l’erreur &quot;Le nouveau certificat ne correspond pas aux domaines existants&quot;, même si les domaines étaient identiques mais présentaient des différences en majuscules ou en minuscules. La mise à jour reconnaît désormais les domaines comme insensibles à la casse, en conformité avec les normes RFC. <!-- CMGR-62844 -->
* Dans Cloud Manager, les liaisons de Liste autorisée IP sont restées bloquées en cours d’exécution, car il manquait des liens de clé étrangère vers les configurations de domaine. Le correctif garantit désormais que les liaisons de Liste autorisée IP sont correctement liées aux configurations de domaine associées. <!-- CMGR-62838 -->
* Cloud Manager valide l’état OCSP (Online Certificate Status Protocol) d’un certificat SSL. Adobe vous recommande également de valider l’intégrité de votre certificat localement à l’aide d’un outil tel que `openssl verify -untrusted intermediate.pem certificate.pem` avant de l’installer via Cloud Manager. Pour plus d’informations, voir la [documentation sur les exigences de certificat SSL](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-ssl-certificates/introduction-to-ssl-certificates#requirements). <!-- CMGR-62341  -->



<!-- ## Known issues {#known-issues} -->