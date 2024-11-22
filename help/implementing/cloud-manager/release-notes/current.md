---
title: Notes de mise à jour de Cloud Manager 2024.11.0 dans Adobe Experience Manager as a Cloud Service
description: En savoir plus sur la version 2024.11.0 de Cloud Manager dans AEM as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: e454581a2e6f2b8184a54d6550daec60e58bbc6c
workflow-type: tm+mt
source-wordcount: '784'
ht-degree: 100%

---

# Notes de mise à jour de Cloud Manager 2024.11.0 dans Adobe Experience Manager as a Cloud Service {#release-notes}

En savoir plus sur la version 2024.11.0 de Cloud Manager dans AEM (Adobe Experience Manager) as a Cloud Service.

>[!NOTE]
>
>Consultez les [notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Dates de publication {#release-date}

La date de publication de Cloud Manager dans AEM as a Cloud Service 2024.11.0 est le 7 novembre 2024.

La prochaine version est prévue le 5 décembre 2024.

## Nouveautés {#what-is-new}

* Découvrez les dernières innovations d’Edge Delivery Services avec AEM Cloud Service, désormais disponible dans votre programme Sandbox. [En savoir plus](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-sandbox-programs.md#auto-creation) <!-- (CMGR-62319) -->
* La page des paramètres du domaine d’AEM Cloud Manager comprend désormais une fonction de recherche qui vous permet de localiser rapidement les domaines par nom. Vous pouvez saisir des mots-clés dans le champ de recherche pour filtrer et afficher les domaines correspondants, facilitant ainsi la gestion efficace de multiples domaines. En outre, la page propose des filtres de statut, tels que **Vérifié** et **Non vérifié**, pour affiner davantage les résultats de la recherche.<!-- (CMGR-62615) -->

![Champ de recherche dans les paramètres du domaine](/help/implementing/cloud-manager/assets/domain-settings-search.png)

## Programme d’adoption précoce {#early-adoption}

Prenez part à notre programme d’adoption précoce de Cloud Manager afin de pouvoir tester certaines fonctionnalités à venir.

### Page d’accueil AEM {#aem-home}

La page d’accueil AEM est le point de départ centralisé de la gestion du contenu, des ressources et des sites dans Adobe Experience Manager. Conçue pour offrir une expérience personnalisée, elle vous permet de naviguer de manière fluide à travers l’écosystème AEM en fonction de vos rôles et objectifs. Véritable guide, elle vous fournit des informations clés et vous recommande des actions pour vous aider à atteindre vos objectifs de manière efficace. Avec une interface claire et centrée sur les utilisateurs et les utilisatrices, la page d’accueil AEM facilite un accès rapide aux outils essentiels et offre une expérience efficace et rationalisée pour utiliser toutes les fonctionnalités d’AEM.

Actuellement en phase d’adoption précoce., la page d’accueil AEM offre une expérience optimisée axée sur l’amélioration des workflows, la hiérarchisation des objectifs et la diffusion de résultats. En participant à ce test, vous pouvez avoir un impact sur le développement de cette page en fournissant des commentaires qui contribuent à façonner son évolution et à améliorer sa valeur pour l’ensemble de la communauté AEM.

Pour exprimer votre intérêt et partager vos commentaires, envoyez un e-mail à [Grp-AemHome@adobe.com](mailto:Grp-AemHome@adobe.com) à partir de l’adresse e-mail associée à votre Adobe ID. N’oubliez pas d’inclure les informations suivantes :

* Le rôle qui correspond le mieux à votre profil : créateur ou créatrice de contenu, développeur ou développeuse, propriétaire d’entreprise, membre de l’équipe d’administration ou autre (fournissez une description).
* Votre principale surface d’accès à AEM : AEM Sites, AEM Assets, AEM Forms, Cloud Manager, ou Autre (fournir une description).

### Apportez votre propre Git - avec prise en charge de GitLab et Bitbucket {#gitlab-bitbucket}

<!-- BOTH CS & AMS -->

La fonctionnalité **Apportez votre propre Git** a été étendue pour inclure la prise en charge de référentiels externes tels que GitLab et Bitbucket. Cette nouvelle prise en charge s’ajoute à la prise en charge existante des référentiels GitHub privés et d’entreprise. Lorsque vous ajoutez ces nouveaux référentiels, vous pouvez également les lier directement à vos pipelines. Vous pouvez héberger ces référentiels sur des plateformes cloud publiques ou dans votre infrastructure ou cloud privés. Cette intégration élimine également la nécessité d’une synchronisation constante du code avec le référentiel d’Adobe et permet de valider les requêtes d’extraction avant de les fusionner dans une branche principale.

Voir [Ajouter des référentiels externes dans Cloud Manager](/help/implementing/cloud-manager/managing-code/external-repositories.md).

![Boîte de dialogue Ajouter un référentiel](/help/implementing/cloud-manager/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>Actuellement, les contrôles de qualité du code des requêtes d’extraction prêts à l’emploi sont exclusifs aux référentiels hébergés par GitHub, mais une mise à jour permettant d’étendre cette fonctionnalité à d’autres fournisseurs Git est en cours.

Si vous souhaitez tester cette nouvelle fonctionnalité et faire part de vos commentaires, envoyez un e-mail à [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com) à partir de l’adresse e-mail associée à votre Adobe ID. Veillez à inclure la plateforme Git à utiliser et indiquez si vous utilisez une structure de référentiel privée/publique ou d’entreprise.


## Correctifs

* Une mise à jour récente a corrigé un problème dans SonarQube où les mots de passe codés en dur n’étaient pas toujours détectés. Le correctif inclut désormais une vérification de modèle étendue et s’aligne sur les normes de détection par défaut dans SonarQube. <!-- CMGR-62682 -->
* Lors de la mise à jour d’un certificat SSL dans Cloud Manager, une erreur inconnue s’affichait après avoir cliqué sur **[!UICONTROL Mettre à jour]** dans la boîte de dialogue **[!UICONTROL Afficher et mettre à jour le certificat SSL]**. <!-- CMGR-62848 -->
* Dans Cloud Manager, les mises à jour des certificats SSL échouaient en raison d’une erreur indiquant « Le nouveau certificat ne correspond pas aux domaines existants », même si les domaines étaient identiques mais présentaient des variations de casse (majuscules/minuscules). La mise à jour permet désormais de reconnaître les domaines comme insensibles à la casse, conformément aux normes RFC. <!-- CMGR-62844 -->
* Dans Cloud Manager, le statut des liaisons pour les adresses IP autorisées restait bloqué sur « en cours » faute de liens de clé étrangère avec les configurations des domaines. Le correctif assure désormais que les liaisons des adresses IP autorisées sont correctement associées aux configurations de domaine correspondantes. <!-- CMGR-62838 -->
* Cloud Manager valide le statut OCSP (Online Certificate Status Protocol) d’un certificat SSL. Adobe vous recommande également de valider l’intégrité de votre certificat localement à l’aide d’un outil comme `openssl verify -untrusted intermediate.pem certificate.pem` avant de l’installer via Cloud Manager. Pour plus d’informations, consultez la [documentation sur les conditions requises pour les certificats SSL](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-ssl-certificates/introduction-to-ssl-certificates#requirements). <!-- CMGR-62341  -->



<!-- ## Known issues {#known-issues} -->