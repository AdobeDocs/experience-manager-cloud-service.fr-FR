---
title: Ajouter des référentiels externes dans Cloud Manager
description: Découvrez comment ajouter un référentiel externe dans Cloud Manager. Cloud Manager prend en charge l’intégration aux référentiels GitHub Enterprise, GitLab, Bitbucket et Azure DevOps.
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
badge: label="Private Beta" type="Positive" url="/help/implementing/cloud-manager/release-notes/current.md#gitlab-bitbucket"
exl-id: aebda813-2eb0-4c67-8353-6f8c7c72656c
source-git-commit: b4bbf73cd49f6d7beb47d2edce0910d957879e39
workflow-type: tm+mt
source-wordcount: '2322'
ht-degree: 27%

---

# Ajout de référentiels externes dans Cloud Manager {#external-repositories}

Découvrez comment ajouter un référentiel externe dans Cloud Manager. Cloud Manager prend en charge l’intégration aux référentiels GitHub Enterprise, GitLab et Bitbucket.

Les clients peuvent désormais également intégrer leurs référentiels Git Azure DevOps dans Cloud Manager, avec la prise en charge des référentiels Azure DevOps modernes et VSTS hérités (Visual Studio Team Services).

* Pour les utilisateurs et utilisatrices d’Edge Delivery Services, le référentiel intégré peut être utilisé pour synchroniser et déployer le code du site.
* Pour les utilisateurs et utilisatrices d’AEM as a Cloud Service et d’Adobe Managed Services (AMS), le référentiel peut être lié aux pipelines full stack et front-end.

>[!NOTE]
>
>Les fonctionnalités décrites dans cet article ne sont disponibles que via le programme bêta privé. Pour plus d’informations et pour vous inscrire à la version Private Beta, voir [Apporter votre propre Git](/help/implementing/cloud-manager/release-notes/current.md#gitlab-bitbucket).


## Configuration d’un référentiel externe

La configuration d’un référentiel externe dans Cloud Manager comprend les étapes suivantes :

1. [Ajouter un référentiel externe](#add-external-repo) à un programme sélectionné
1. [Liaison d’un référentiel externe validé à un pipeline](#validate-ext-repo)
   <!-- 1. Provide an access token to the external repository.
    1. Validate ownership of the private GitHub repository. -->
1. [Configurez un webhook](#configure-webhook) dans un référentiel externe.


## Ajout d’un référentiel externe {#add-ext-repo}

>[!NOTE]
>
>Les référentiels externes ne peuvent pas être liés aux pipelines de configuration.

<!-- THIS BULLET REMOVED AS PER https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2024.12.0+Release. THEY CAN NOW START AUTOMATICALLY>
* Pipelines using external repositories (excluding GitHub-hosted repositories) and the **Deployment Trigger** option [!UICONTROL **On Git Changes**], triggers are not automatically started. They must be manually started. -->


1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Sur la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez le programme auquel vous souhaitez lier un référentiel externe.

1. Dans le menu latéral, sous **Programme**, cliquez sur ![Icône Composition du dossier](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderOutline_18_N.svg) **Référentiels**.

   ![Page Référentiels](/help/implementing/cloud-manager/managing-code/assets/repositories-tab.png)

1. Dans le coin supérieur droit de la page **Référentiels**, cliquez sur **Ajouter un référentiel**.

1. Dans la boîte de dialogue **Ajouter un référentiel**, sélectionnez **Référentiel privé** pour lier un référentiel Git externe à votre programme.

   ![Ajout de votre propre référentiel](/help/implementing/cloud-manager/managing-code/assets/repositories-private-repo-type.png)

1. Dans chaque champ respectif, fournissez les détails suivants sur votre référentiel :

   | Champ | Description |
   | --- | --- |
   | **Nom du référentiel** | Obligatoire. Nom expressif pour votre nouveau référentiel. |
   | **URL du référentiel** | Obligatoire. URL du référentiel.<br><br>Si vous utilisez un référentiel hébergé sur GitHub, le chemin d’accès doit se terminer par `.git`.<br>Par exemple, *`https://github.com/org-name/repo-name.git`* (le chemin d’accès de l’URL est fourni à titre d’illustration uniquement).<br><br>Si vous utilisez un référentiel externe, il doit utiliser le format de chemin d’accès d’URL suivant :<br>`https://git-vendor-name.com/org-name/repo-name.git`<br> ou <br>`https://self-hosted-domain/org-name/repo-name.git`<br> et correspondre à votre fournisseur Git. |
   | **Sélection du type de référentiel** | Obligatoire. Sélectionnez le type de référentiel que vous utilisez. Si le chemin d’URL du référentiel inclut le nom du fournisseur Git, tel que GitLab ou Bitbucket, le type de référentiel est déjà présélectionné pour vous.:<ul><li>**GitHub** (GitHub Enterprise et la version auto-hébergée de GitHub)</li><li>**GitLab** (`gitlab.com` et la version auto-hébergée de GitLab) </li><li>**Bitbucket** (uniquement `bitbucket.org` - version cloud) est pris en charge. La version auto-hébergée de Bitbucket a été abandonnée à partir du 15 février 2024.)</li><li>**Azure DevOps** (`dev.azure.com`) </ul> |
   | **Description** | Facultatif. Description détaillée du référentiel. |

1. Sélectionnez **Enregistrer** pour ajouter le référentiel.

   Fournissez maintenant un jeton d’accès pour valider la propriété du référentiel externe.

1. Dans la boîte de dialogue **Validation de la propriété du référentiel privé**, fournissez un jeton d’accès pour valider la propriété du référentiel externe afin que vous puissiez y accéder, puis cliquez sur **Validation**.

   ![Sélection d’un jeton d’accès existant pour un référentiel](/help/implementing/cloud-manager/managing-code/assets/repositories-exisiting-access-token.png)
   *Sélection d’un jeton d’accès existant pour un référentiel Bitbucket (à titre d’illustration uniquement).*

>[!BEGINTABS]

>[!TAB GitHub Enterprise]

<!-- https://git.corp.adobe.com/pages/experience-platform/cloud-manager-repository-service/#/./git-vendors/github -->

| Option de jeton d’accès | Description |
| --- | --- |
| **Utilisation d’un jeton d’accès existant** | Si vous avez déjà fourni un jeton d’accès au référentiel pour votre organisation et que vous avez accès à plusieurs référentiels, vous pouvez sélectionner un jeton existant. Utilisez la liste déroulante **Nom du jeton** pour choisir le jeton que vous souhaitez appliquer au référentiel. Sinon, ajoutez un nouveau jeton d’accès. |
| **Ajout d’un nouveau jeton d’accès** | <ul><li> Dans le champ de texte **Nom du jeton**, saisissez un nom pour le jeton d’accès que vous êtes en train de créer.<li>Créez un jeton d’accès personnel en suivant les instructions de la [documentation GitHub](https://docs.github.com/fr/enterprise-server@3.14/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens).<li>Autorisations requises pour le jeton d’accès personnel (PAT) d’entreprise GitHub <br>ces autorisations permettent à Cloud Manager de valider les demandes d’extraction, de gérer les vérifications de statut de validation et d’accéder aux détails de référentiel nécessaires.<br>Lorsque vous générez le PAT dans GitHub Enterprise, assurez-vous qu’il inclut les autorisations de référentiel suivantes :<ul><li>Demande d’extraction (lecture et écriture)<li>Commit status (lecture et écriture).<li>Métadonnées du référentiel (lecture seule)</li></li></ul></li></ul></ul></ul><ul><li>Dans le champ **Jeton d’accès**, collez le jeton que vous venez de créer. |

Après validation, le référentiel externe est prêt à l’emploi et peut être connecté à un pipeline.

Voir aussi [Gérer les jetons d’accès](/help/implementing/cloud-manager/managing-code/manage-access-tokens.md).

>[!TAB  GitLab ]

<!-- https://git.corp.adobe.com/pages/experience-platform/cloud-manager-repository-service/#/./git-vendors/gitlab -->

| Option de jeton d’accès | Description |
| --- | --- |
| **Utilisation d’un jeton d’accès existant** | Si vous avez déjà fourni un jeton d’accès au référentiel pour votre organisation et que vous avez accès à plusieurs référentiels, vous pouvez sélectionner un jeton existant. Utilisez la liste déroulante **Nom du jeton** pour choisir le jeton que vous souhaitez appliquer au référentiel. Sinon, ajoutez un nouveau jeton d’accès. |
| **Ajout d’un nouveau jeton d’accès** | <ul><li>Dans le champ de texte **Nom du jeton**, saisissez un nom pour le jeton d’accès que vous êtes en train de créer.<li>Créez un jeton d’accès personnel en suivant les instructions de la [documentation GitLab](https://docs.gitlab.com/user/profile/personal_access_tokens/).<li>Autorisations requises pour le jeton d’accès personnel GitLab (PAT)<br>ces portées permettent à Cloud Manager d’accéder aux données du référentiel et aux informations utilisateur selon les besoins pour la validation et l’intégration du webhook.<br>Lorsque vous générez le PAT dans GitLab, assurez-vous qu’il inclut les portées de jeton suivantes :<ul><li>api<li>read_user</li></li></ul></li></li></ul></ul></ul><ul><li>Dans le champ **Jeton d’accès**, collez le jeton que vous venez de créer. |

Après validation, le référentiel externe est prêt à l’emploi et peut être connecté à un pipeline.

Voir aussi [Gérer les jetons d’accès](/help/implementing/cloud-manager/managing-code/manage-access-tokens.md).

>[!TAB Bitbucket]

<!-- https://git.corp.adobe.com/pages/experience-platform/cloud-manager-repository-service/#/./git-vendors/bitbucket -->

| Option de jeton d’accès | Description |
| --- | --- |
| **Utilisation d’un jeton d’accès existant** | Si vous avez déjà fourni un jeton d’accès au référentiel pour votre organisation et que vous avez accès à plusieurs référentiels, vous pouvez sélectionner un jeton existant. Utilisez la liste déroulante **Nom du jeton** pour choisir le jeton que vous souhaitez appliquer au référentiel. Sinon, ajoutez un nouveau jeton d’accès. |
| **Ajout d’un nouveau jeton d’accès** | <ul><li>Dans le champ de texte **Nom du jeton**, saisissez un nom pour le jeton d’accès que vous êtes en train de créer.<li>Créez un jeton d’accès au référentiel à l’aide de la [documentation Bitbucket](https://support.atlassian.com/bitbucket-cloud/docs/create-a-repository-access-token/).<li>Autorisations requises pour le jeton d’accès personnel (PAT) Bitbucket <br>ces autorisations permettent à Cloud Manager d’accéder au contenu du référentiel, de gérer les demandes d’extraction et de configurer des événements webhook ou d’y réagir.<br>Lorsque vous créez le mot de passe de l’application dans Bitbucket, assurez-vous qu’il inclut les autorisations de mot de passe d’application requises suivantes :<ul><li>Référentiel (lecture seule)<li>Requêtes d’extraction (lecture et écriture)<li>Webhooks (lecture et écriture)</li></li></ul></li></li></ul></ul></ul><ul><li>Dans le champ **Jeton d’accès**, collez le jeton que vous venez de créer. |

Après validation, le référentiel externe est prêt à l’emploi et peut être connecté à un pipeline.

Voir aussi [Gérer les jetons d’accès](/help/implementing/cloud-manager/managing-code/manage-access-tokens.md).

>[!TAB Opérations de développement Azure]

<!-- https://git.corp.adobe.com/pages/experience-platform/cloud-manager-repository-service/#/./git-vendors/azure_devops -->

| Option de jeton d’accès | Description |
| --- | --- |
| **Utilisation d’un jeton d’accès existant** | Si vous avez déjà fourni un jeton d’accès au référentiel pour votre organisation et que vous avez accès à plusieurs référentiels, vous pouvez sélectionner un jeton existant. Utilisez la liste déroulante **Nom du jeton** pour choisir le jeton que vous souhaitez appliquer au référentiel. Sinon, ajoutez un nouveau jeton d’accès. |
| **Ajout d’un nouveau jeton d’accès** | <ul><li>Dans le champ de texte **Nom du jeton**, saisissez un nom pour le jeton d’accès que vous êtes en train de créer.<li>Créez un jeton d’accès au référentiel à l’aide de la [documentation Azure DevOps](https://learn.microsoft.com/en-us/azure/devops/organizations/accounts/use-personal-access-tokens-to-authenticate?view=azure-devops&tabs=Windows).<li>Autorisations requises pour le jeton d’accès personnel (PAT) Azure DevOps.<br>Ces autorisations permettent à Cloud Manager d’accéder au contenu du référentiel, de gérer les demandes d’extraction et de configurer des événements webhook ou d’y réagir.<br>Lorsque vous créez le mot de passe de l’application dans Azure DevOps, assurez-vous qu’il inclut les autorisations de mot de passe d’application requises suivantes :<ul><li>Référentiel (lecture seule)</li></ul></li></li></ul></ul></ul><ul><li>Dans le champ **Jeton d’accès**, collez le jeton que vous venez de créer. |

Après validation, le référentiel externe est prêt à l’emploi et peut être connecté à un pipeline.

Voir aussi [Gérer les jetons d’accès](/help/implementing/cloud-manager/managing-code/manage-access-tokens.md).

>[!ENDTABS]


## Liaison d’un référentiel externe validé à un pipeline {#validate-ext-repo}

1. Ajoutez ou modifiez un pipeline :
   * [Ajout d’un pipeline de production](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md)
   * [Ajout d’un pipeline hors production](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md)
   * [Modification d’un pipeline](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#editing-pipelines)

   <!-- Add an Edge Delivery Pipeline -->

   ![Référentiel de code source du pipeline et branche Git](/help/implementing/cloud-manager/managing-code/assets/pipeline-repo-gitbranch.png)
   *Boîte de dialogue Ajout d’un pipeline hors production avec référentiel sélectionné et branche Git*

1. Pour spécifier l’emplacement du **code source** lors de l’ajout ou de la modification d’un pipeline, sélectionnez le référentiel externe de votre choix dans la liste déroulante **Référentiel**.

1. Dans la liste déroulante **Branche Git**, sélectionnez la branche comme source du pipeline.

1. Cliquez sur **Enregistrer**.


>[!TIP]
>
>Pour plus d’informations sur la gestion des référentiels dans Cloud Manager, consultez le document [Référentiels Cloud Manager](/help/implementing/cloud-manager/managing-code/managing-repositories.md).


## Configuration d’un webhook pour un référentiel externe {#configure-webhook}

Cloud Manager vous permet de configurer des webhooks pour les référentiels Git externes que vous avez ajoutés. Voir [ Ajouter un référentiel externe ](#add-ext-repo). Ces webhooks permettent à Cloud Manager de recevoir des événements liés à différentes actions dans votre solution de fournisseur Git.

Par exemple, les webhooks permettent à Cloud Manager de déclencher des actions en fonction d’événements tels que :

* Création de la requête de tirage (PR) - Lance la fonctionnalité de validation PR.
* Événements push : démarre les pipelines lorsque le déclencheur « En cas de validation Git » est activé.
* Futures actions basées sur des commentaires : permettent des workflows, tels que le déploiement direct d’une requête de tirage vers un environnement de développement rapide (RDE).

La configuration Webhook n’est pas requise pour les référentiels hébergés sur `GitHub.com`, car Cloud Manager s’intègre directement via l’application GitHub.

Pour tous les autres référentiels externes intégrés avec un jeton d’accès, tels que GitHub Enterprise, GitLab, Bitbucket et Azure DevOps, la configuration webhook est disponible et doit être configurée manuellement.

**Pour configurer un webhook pour un référentiel externe, procédez comme suit**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Dans la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez le programme pour lequel vous souhaitez configurer un webhook pour un référentiel Git externe.

1. Dans le coin supérieur gauche de la page, cliquez sur ![Icône Afficher le menu](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) pour afficher le menu de gauche.

1. Dans le menu de gauche, sous l’en-tête **Programme**, cliquez sur ![Icône Composition du dossier](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderOutline_18_N.svg) **Référentiels**.

1. Sur la page **Référentiels**, à l’aide de la colonne **Type** pour vous guider dans votre sélection, localisez le référentiel souhaité, puis cliquez sur l’icône ![Points de suspension - Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) en regard de celui-ci.

   ![Configuration de l’option Webhook dans le menu déroulant d’un référentiel sélectionné](/help/implementing/cloud-manager/managing-code/assets/repository-config-webhook.png)

1. Dans le menu déroulant, cliquez sur **Configurer le Webhook**.

   ![Boîte de dialogue Configurer le Webhook](/help/implementing/cloud-manager/managing-code/assets/config-webhook.png)

1. Dans la boîte de dialogue **Configurer le Webhook**, procédez comme suit :

   1. En regard du champ **URL Webhook**, cliquez sur ![Icône Copier](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg).
Collez l’URL dans un fichier texte brut. L’URL copiée est requise pour les paramètres du Webhook de votre fournisseur Git.
   1. En regard du champ **Secret Webhook** jeton/clé, cliquez sur **Générer**, puis sur ![Icône Copier](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg).
Collez le secret dans un fichier texte brut. Le secret copié est requis pour les paramètres du Webhook de votre fournisseur Git.
1. Cliquez sur **Fermer**.
1. Accédez à votre solution de fournisseur Git (GitHub Enterprise, GitLab, Bitbucket ou Azure DevOps).

   Tous les détails sur la configuration webhook et les événements requis pour chaque fournisseur sont disponibles dans [Ajouter un référentiel externe](#add-ext-repo). Sous l’étape 8, consultez le tableau à onglets.

1. Recherchez la section Paramètres **Webhook** de la solution.
1. Collez l’URL du Webhook que vous avez copiée précédemment dans le champ de texte de l’URL.
   1. Remplacez le paramètre de requête `api_key` dans l’URL du Webhook par votre propre clé API réelle.

      Pour générer une clé API, vous devez créer un projet d’intégration dans Adobe Developer Console. Voir [Création d’un projet d’intégration d’API](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/create-api-integration/) pour plus d’informations.

1. Collez le secret Webhook que vous avez copié précédemment dans le champ de texte **Secret** (ou **Clé secrète** ou **Jeton secret**).
1. Configurez le webhook pour envoyer les événements requis par Cloud Manager. Utilisez le tableau suivant pour déterminer les événements corrects pour votre fournisseur Git.

>[!BEGINTABS]

>[!TAB GitHub Enterprise]

<!-- https://git.corp.adobe.com/pages/experience-platform/cloud-manager-repository-service/#/./git-vendors/github -->

| Événements webhook obligatoires |
| --- |
| Ces événements permettent à Cloud Manager de répondre à l’activité GitHub, comme la validation de la demande d’extraction, les déclencheurs basés sur les notifications push pour les pipelines ou la synchronisation du code Edge Delivery Services.<br>Assurez-vous que le webhook est configuré pour se déclencher sur les événements webhook requis suivants :<ul><li>Requêtes d’extraction<li>Notifications push<li>Commentaires sur l&#39;événement</li></li></li></ul></ul></ul> |

>[!TAB  GitLab ]

<!-- https://git.corp.adobe.com/pages/experience-platform/cloud-manager-repository-service/#/./git-vendors/gitlab -->

| Événements webhook obligatoires |
| --- |
| Ces événements webhook permettent à Cloud Manager de déclencher des pipelines lorsque le code est transmis ou qu’une demande de fusion est envoyée. Ils effectuent également le suivi des commentaires liés à la validation de la demande d’extraction (par le biais d’événements de note).<br>Assurez-vous que le webhook est configuré pour se déclencher sur les événements webhook requis suivants<ul><li>Événements push<li>Événements de demande de fusion<li>Événements de note</li></li></li></ul></ul></ul> |

>[!TAB Bitbucket]

<!-- https://git.corp.adobe.com/pages/experience-platform/cloud-manager-repository-service/#/./git-vendors/bitbucket -->

| Événements webhook obligatoires |
| --- |
| Ces événements permettent à Cloud Manager de valider les demandes d’extraction, de répondre aux publications de code et d’interagir avec les commentaires pour la coordination du pipeline.<br>Assurez-vous que le webhook est configuré pour se déclencher sur les événements webhook requis suivants<ul><li>Demande d’extraction : créée<li>Demande d’extraction : mise à jour<li>Demandes d’extraction : fusionnées<li>Demande d’extraction : commentaire<li>Référentiel : Push</li></li></li></ul></ul></ul> |

>[!TAB Opérations de développement Azure]

<!-- https://git.corp.adobe.com/pages/experience-platform/cloud-manager-repository-service/#/./git-vendors/azure_devops -->

| Événements webhook requis et authentification |
| --- |
| Ces événements permettent à Cloud Manager de valider les demandes d’extraction, de répondre aux publications de code et d’interagir avec les commentaires pour la coordination du pipeline.<br>Assurez-vous que le webhook est configuré pour se déclencher sur les événements webhook requis suivants<ul><li>Référentiel : Push</li></ul>Définition de l’authentification :<br>1. Dans le champ **Nom d’utilisateur de l’authentification de base**, saisissez `cloudmanager`.<br>2. Dans le champ **Mot de passe d’authentification de base**, saisissez le secret Webhook généré à partir de l’interface utilisateur de Cloud Manager. |

>[!ENDTABS]


### Validation des requêtes d’extraction avec des Webhooks

Une fois les Webhooks configurés correctement, Cloud Manager déclenche automatiquement les exécutions de pipeline ou les contrôles de validation de RP pour votre référentiel.

Le comportement varie en fonction du fournisseur Git que vous utilisez, comme indiqué ci-dessous.

>[!BEGINTABS]


>[!TAB GitHub Enterprise]

<!-- https://git.corp.adobe.com/pages/experience-platform/cloud-manager-repository-service/#/./git-vendors/github -->

Lorsque la vérification est créée, elle ressemble à la capture d’écran ci-dessous. La principale différence avec `GitHub.com` est que `GitHub.com` utilise une exécution de vérification, tandis que GitHub Enterprise (à l’aide de jetons d’accès personnel) génère un statut de validation :

![Statut d’engagement pour indiquer le processus de validation PR sur GitHub Enterprise](/help/implementing/cloud-manager/managing-code/assets/repository-webhook-github-pr-validation.png)


>[!TAB  GitLab ]

<!-- https://git.corp.adobe.com/pages/experience-platform/cloud-manager-repository-service/#/./git-vendors/gitlab -->

Les interactions GitLab reposent uniquement sur des commentaires. Lorsque la validation commence, un commentaire est ajouté. Une fois la validation terminée (qu’elle ait réussi ou échoué), le commentaire initial est supprimé et remplacé par un nouveau commentaire contenant les résultats de la validation ou les détails de l’erreur.

Lorsque la validation de la qualité du code est en cours d’exécution :

![Lorsque la validation de la qualité du code est en cours d’exécution](/help/implementing/cloud-manager/managing-code/assets/repository-webhook-gitlab1.png)

Lorsque la validation de la qualité à froid est terminée :

![Lorsque la validation de la qualité à froid est terminée](/help/implementing/cloud-manager/managing-code/assets/repository-webhook-gitlab2.png)

Lorsque la validation de la qualité du code échoue avec une erreur :

![Lorsque la validation de la qualité du code échoue avec une erreur](/help/implementing/cloud-manager/managing-code/assets/repository-webhook-gitlab3.png)

Lorsque la validation de la qualité du code échoue en raison de problèmes client :

![Lorsque la validation de la qualité du code échoue en raison de problèmes client](/help/implementing/cloud-manager/managing-code/assets/repository-webhook-gitlab4.png)


>[!TAB Bitbucket]

<!-- https://git.corp.adobe.com/pages/experience-platform/cloud-manager-repository-service/#/./git-vendors/bitbucket -->

Lorsque la validation de la qualité du code est en cours d’exécution :

![Statut pendant l’exécution de la validation de la qualité du code](/help/implementing/cloud-manager/managing-code/assets/repository-webhook-bitbucket1.png)

Utilise le statut de validation pour le suivi de la progression de la validation PR. Dans le cas suivant, la capture d’écran montre ce qui se produit lorsqu’une validation de qualité du code échoue en raison d’un problème client. Un commentaire est ajouté avec des informations détaillées sur les erreurs, et une vérification de validation est créée, qui affiche l’échec (visible à droite) :

![Statut de validation de la demande d’extraction pour Bitbucket](/help/implementing/cloud-manager/managing-code/assets/repository-webhook-bitbucket2.png)



>[!ENDTABS]


## Résolution des problèmes webhook

* Assurez-vous que l’URL du Webhook comprend une clé API valide.
* Vérifiez que les événements webhook sont correctement configurés dans les paramètres de votre fournisseur Git.
* Si la validation PR ou les déclencheurs de pipeline ne fonctionnent pas, vérifiez que le secret Webhook est à jour dans Cloud Manager et votre fournisseur Git.


