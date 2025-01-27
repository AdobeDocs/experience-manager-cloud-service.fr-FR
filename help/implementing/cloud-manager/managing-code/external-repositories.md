---
title: Ajout de référentiels externes dans Cloud Manager (adoption précoce)
description: Découvrez comment ajouter un référentiel externe dans Cloud Manager. Cloud Manager prend en charge l’intégration avec les référentiels GitHub, GitLab et Bitbucket.
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
exl-id: aebda813-2eb0-4c67-8353-6f8c7c72656c
source-git-commit: befb092169e2278a9e84c183d342003ef325c71e
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 91%

---

# Ajout de référentiels externes dans Cloud Manager {#external-repositories}

Découvrez comment ajouter un référentiel externe dans Cloud Manager. Cloud Manager prend en charge l’intégration avec les référentiels GitHub, GitLab et Bitbucket.

>[!NOTE]
>
>Cette fonctionnalité n’est disponible que dans le cadre du programme d’adoption précoce. Pour plus d’informations et pour vous inscrire en tant qu’utilisateur ou utilisatrice précoce, consultez [Apporter votre propre Git - désormais avec prise en charge de GitLab et Bitbucket](/help/implementing/cloud-manager/release-notes/2024/2024-10-0.md#gitlab-bitbucket).

## Configuration d’un référentiel externe

La configuration d’un référentiel externe dans Cloud Manager se compose de trois étapes :

1. [Ajoutez un référentiel externe](#add-external-repo) à un programme sélectionné.
1. Fournissez un jeton d’accès au référentiel externe.
1. Validez la propriété du référentiel GitHub privé.


## Ajout d’un référentiel externe {#add-ext-repo}

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Sur la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez le programme auquel vous souhaitez lier un référentiel externe.

1. Dans le menu latéral, sous **Services**, sélectionnez ![icône Dossier](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Folder_18_N.svg) **Référentiels**.

   ![Page Référentiels](/help/implementing/cloud-manager/managing-code/assets/repositories-tab.png)

1. Dans le coin supérieur droit de la page **Référentiels**, cliquez sur **Ajouter un référentiel**.

1. Dans la boîte de dialogue **Ajouter un référentiel**, sélectionnez **Référentiel privé** pour lier un référentiel Git externe à votre programme.

   ![Ajout de votre propre référentiel](/help/implementing/cloud-manager/managing-code/assets/repositories-private-repo-type.png)

1. Dans chaque champ respectif, fournissez les détails suivants sur votre référentiel :

   | Champ | Description |
   | --- | --- |
   | **Nom du référentiel** | Obligatoire. Nom expressif pour votre nouveau référentiel. |
   | **URL du référentiel** | Obligatoire. URL du référentiel.<br><br> Si vous utilisez un référentiel hébergé par GitHub, le chemin d’accès doit se terminer par `.git`.<br>Par exemple, *`https://github.com/org-name/repo-name.git`* (le chemin d’accès de l’URL est fourni à titre d’illustration uniquement).<br><br>Si vous utilisez un référentiel externe, il doit utiliser le format de chemin d’accès d’URL suivant :<br>`https://git-vendor-name.com/org-name/repo-name.git`<br> ou <br>`https://self-hosted-domain/org-name/repo-name.git`<br> et correspondre à votre fournisseur Git. |
   | S **Select Repository Type** | Obligatoire. Sélectionnez le type de référentiel que vous utilisez : **GitHub**, **GitLab** ou **BitBucket**. Si le chemin d’accès de l’URL du référentiel ci-dessus inclut le nom du fournisseur Git, tel que GitLab ou Bitbucket, le type de référentiel est déjà présélectionné. |
   | **Description** | Facultatif. Description détaillée du référentiel. |

1. Sélectionnez **Enregistrer** pour ajouter le référentiel.

1. Dans la boîte de dialogue **Validation de la propriété du référentiel privé**, fournissez un jeton d’accès pour valider la propriété du référentiel externe afin que vous puissiez y accéder.

   ![Sélection d’un jeton d’accès existant pour un référentiel](/help/implementing/cloud-manager/managing-code/assets/repositories-exisiting-access-token.png)
   *Sélection d’un jeton d’accès existant pour un référentiel BitBucket.*

   | Type de jeton | Description |
   | --- | --- |
   | **Utilisation d’un jeton d’accès existant** | Si vous avez déjà fourni un jeton d’accès au référentiel pour votre organisation et que vous avez accès à plusieurs référentiels, vous pouvez sélectionner un jeton existant. Utilisez la liste déroulante **Nom du jeton** pour choisir le jeton que vous souhaitez appliquer au référentiel. Sinon, ajoutez un nouveau jeton d’accès. |
   | **Ajout d’un nouveau jeton d’accès** | **Type de référentiel : GitHub**<br>• Dans le champ de texte **Nom du jeton**, saisissez un nom pour le jeton d’accès que vous créez.<br>• Créez un jeton d’accès personnel en suivant les instructions de la [documentation GitHub](https://docs.github.com/fr/enterprise-server@3.14/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens).<br>• Autorisations requises : <br> • `Read access to metadata`.<br> • `Read and write access to code and pull requests`.<br>• Dans le champ **Jeton d’accès**, collez le jeton que vous venez de créer. |
   |  | **Type de référentiel : GitLab**<br>• Dans le champ de texte **Nom du jeton**, saisissez un nom pour le jeton d’accès que vous créez.<br>• Créez un jeton d’accès personnel en suivant les instructions de la [documentation GitLab](https://docs.gitlab.com/ee/user/profile/personal_access_tokens.html).<br>• Autorisations requises :<br> • `api`<br> • `read_api`<br> • `read_repository`<br> • `write_repository`<br>• Dans le champ **Jeton d’accès**, collez le jeton que vous venez de créer. |
   |  | **Type de référentiel : Bitbucket**<br>• Dans le champ de texte **Nom du jeton**, saisissez un nom pour le jeton d’accès que vous créez.<br>• Créez un jeton d’accès au référentiel à l’aide de la [documentation Bitbucket](https://support.atlassian.com/bitbucket-cloud/docs/create-a-repository-access-token/).<br>• Autorisations requises :<br> • `Read and write access to code and pull requests`. |

   >[!NOTE]
   >
   >La fonctionnalité **Ajouter un nouveau jeton d’accès** est actuellement en phase d’adoption précoce. Des fonctionnalités supplémentaires sont en cours de planification. Par conséquent, les autorisations requises pour les jetons d’accès peuvent changer. De plus, l’interface d’utilisation pour la gestion des jetons peut être mise à jour avec des fonctionnalités telles que la gestion des dates d’expiration des jetons. Ainsi que des vérifications automatisées pour garantir que les jetons associés aux référentiels restent valides.

1. Cliquez sur **Valider**.

Après validation, le référentiel externe est prêt à l’emploi et peut être connecté à un pipeline.

## Liaison d’un référentiel externe validé à un pipeline {#validate-ext-repo}

1. Ajoutez ou modifiez un pipeline :
   * [Ajout d’un pipeline de production](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md)
   * [Ajout de pipelines hors production](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md)
   * [Modification d’un pipeline](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#editing-pipelines)

   ![Référentiel de code source du pipeline et branche Git](/help/implementing/cloud-manager/managing-code/assets/pipeline-repo-gitbranch.png)
   *Boîte de dialogue Ajout d’un pipeline hors production avec référentiel sélectionné et branche Git*

1. Pour spécifier l’emplacement du **code source** lors de l’ajout ou de la modification d’un pipeline, sélectionnez le référentiel externe de votre choix dans la liste déroulante **Référentiel**.

1. Dans la liste déroulante **Branche Git**, sélectionnez la branche comme source du pipeline.

1. Cliquez sur **Enregistrer**.


>[!TIP]
>
>Pour plus d’informations sur la gestion des référentiels dans Cloud Manager, consultez le document [Référentiels Cloud Manager](/help/implementing/cloud-manager/managing-code/managing-repositories.md).


## Limites

Les référentiels externes ne peuvent pas être liés aux pipelines de configuration.

<!-- THIS BULLET REMOVED AS PER https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2024.12.0+Release. THEY CAN NOW START AUTOMATICALLY>
* Pipelines using external repositories (excluding GitHub-hosted repositories) and the **Deployment Trigger** option [!UICONTROL **On Git Changes**], triggers are not automatically started. They must be manually started. -->
