---
title: Ajout d’un référentiel GitHub privé dans Cloud Manager
description: Découvrez comment configurer Cloud Manager pour utiliser vos propres référentiels GitHub privés.
exl-id: 5232bbf5-17a5-4567-add7-cffde531abda
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: 2ea076c42a6406548bf48cd246227fc8ddb3a080
workflow-type: tm+mt
source-wordcount: '998'
ht-degree: 35%

---

# Ajout d’un référentiel cloud GitHub privé dans Cloud Manager {#private-repositories}

En configurant Cloud Manager pour l’intégration à votre cloud GitHub privé (référentiels hébergés sur `github.com`), vous pouvez valider votre code directement dans GitHub à l’aide de Cloud Manager. Cette configuration supprime l’exigence de synchroniser régulièrement votre code avec le référentiel Adobe.

>[!NOTE]
>
>Vous pouvez également ajouter les types de référentiel suivants avec des Webhooks :
>
>* Référentiels GitHub Enterprise Server (version auto-hébergée de GitHub) .
>* Référentiels GitLab (versions `gitlab.com` et auto-hébergées de GitLab).
>* Référentiels Bitbucket (`bitbucket.org` et Bitbucket Server, la version auto-hébergée de BitBucket).
>* Référentiels DevOps d’Azure ([dev.azure.com](https://azure.microsoft.com/en-us/products/devops/?nav=min) et versions auto-hébergées d’Azure DevOps).
>
>Voir [Ajouter des référentiels externes dans Cloud Manager](/help/implementing/cloud-manager/managing-code/external-repositories.md).

<!-- CONSIDER ADDING MORE DETAIL... THE WHY. Some key points about this capability include the following:

* **Direct Integration**: With this setup, you can directly link your private GitHub repositories to Cloud Manager, allowing for seamless code validation, deployment, and CI/CD (Continuous Integration/Continuous Deployment) pipelines without needing to maintain a separate sync process with Adobe's default Git repository.

* **Customization and Autonomy**: Companies often prefer managing their own source code repositories for security, control, and integration purposes. "Build your own GitHub" allows organizations to maintain their internal development processes while leveraging the full functionality of Cloud Manager for building, testing, and deploying AEM (Adobe Experience Manager) applications.

* **Simplified Workflow**: It reduces the overhead of synchronizing code between multiple repositories by allowing Cloud Manager to access the organization's private repository directly, making the development cycle faster and more efficient.

* **CI/CD Pipelines**: Teams can still benefit from Adobe Cloud Manager's automated build, test, and deployment processes, as the integration allows the CI/CD pipelines to pull code from the organization's own GitHub repository.

In essence, a "Build your own GitHub" in Adobe Cloud Manager empowers teams to manage their own GitHub repositories while still using the robust deployment and validation capabilities of Cloud Manager.

>[!NOTE]
>
>This feature is exclusive to public GitHub. Support for self-hosted GitHub is not available. -->

## Configuration {#configuration}

La configuration d’un référentiel cloud GitHub privé dans Cloud Manager se compose de deux étapes :

1. [Ajoutez un référentiel cloud GitHub privé](#add-repo) à un programme sélectionné.
1. Ensuite, [vérifiez la propriété du référentiel cloud GitHub privé](#validate-ownership).



### Ajouter un référentiel cloud GitHub privé à un programme {#add-repo}

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Sur la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez le programme auquel vous souhaitez lier un référentiel Git privé.

1. Dans le menu latéral, sous **Services**, sélectionnez ![icône Dossier](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Folder_18_N.svg) **Référentiels**.

   ![Page Référentiels](/help/implementing/cloud-manager/managing-code/assets/repositories-tab.png)

1. Dans le coin supérieur droit de la page **Référentiels**, cliquez sur **Ajouter un référentiel**.

1. Dans la boîte de dialogue **Ajouter un référentiel**, sélectionnez **Référentiel privé** comme type de référentiel.

   ![Ajout de votre propre référentiel](/help/implementing/cloud-manager/assets/repos/add-own-github.png)

1. Dans chaque champ respectif, fournissez les détails suivants sur votre référentiel :

   | Champ | Description |
   | --- | --- |
   | Nom du référentiel | Nom expressif pour votre nouveau référentiel. |
   | URL du référentiel | URL du référentiel privé, qui doit se terminer par `.git`.<br>Par exemple, *`https://github.com/org-name/repo-name.git`* (le chemin d’accès de l’URL est fourni à titre d’illustration uniquement). |
   | Description (facultative) | Description détaillée du référentiel. |

1. Sélectionnez **Enregistrer**.
Vous pouvez désormais [valider la propriété du référentiel privé](#validate-ownership).

>[!TIP]
>
>Pour plus d’informations sur la gestion des référentiels dans Cloud Manager, consultez le document [Référentiels Cloud Manager](/help/implementing/cloud-manager/managing-code/managing-repositories.md).


### Validation de la propriété d’un référentiel GitHub privé {#validate-ownership}

Cloud Manager connaît désormais votre référentiel GitHub, mais il doit toujours y accéder. Pour accorder l’accès, vous devez installer l’application GitHub d’Adobe et vérifier que vous êtes propriétaire du référentiel spécifié.

**Pour valider la propriété d’un référentiel GitHub privé, procédez comme suit**

1. Après avoir ajouté votre propre référentiel, suivez les étapes restantes de la boîte de dialogue **Validation de la propriété du référentiel privé**.

   ![Validation de la propriété du référentiel privé.](/help/implementing/cloud-manager/assets/repos/private-repo-validate.png)

   |  | Description |
   | --- | --- |
   | **Étape 1 : application GitHub** | Cloud Manager utilise une application GitHub pour interagir en toute sécurité avec votre référentiel privé.<br>· Un propriétaire de votre organisation GitHub doit installer l’application située à l’adresse `https://github.com/apps/cloud-manager-for-aem` et accorder l’accès au référentiel.<br>· Pour plus d’informations sur l’installation et l’octroi de l’accès, consultez la documentation de GitHub . |
   | **Étape 2 : Fichier Secret** | Pour améliorer la sécurité, vous devez créer un fichier secret dans la branche par défaut de votre référentiel.<br>· Cliquez sur **Générer**, puis sur **Confirmer**. Cloud Manager génère le contenu du fichier privé dans le champ de texte **Contenu du fichier secret**.<br>· Cliquez sur ![Icône Copier](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg) pour copier le contenu de ce champ. Le contenu du fichier secret ne s’affichera qu’une seule fois. Si vous ne copiez pas le contenu avant de fermer cette boîte de dialogue, régénérez le secret. |

1. Créez un fichier dans la branche par défaut de votre référentiel GitHub appelé :

   `.well-known/adobe/cloud-manager-challenge`

1. Collez le contenu du fichier secret dans le nouveau fichier que vous venez de créer, puis enregistrez-le.

   Une fois l’application installée et le fichier secret existant dans le référentiel, poursuivez l’étape.

1. Dans la boîte de dialogue **Validation de la propriété du référentiel privé**, cliquez sur **Valider**.

L’application peut être installée et un fichier secret peut être créé dans n’importe quel ordre. Toutefois, vous devez effectuer les deux étapes avant de pouvoir valider.

Jusqu’à la validation, le référentiel est répertorié avec une icône rouge indiquant qu’il n’est pas encore validé et qu’il ne peut pas encore être utilisé.

![Référentiel non validé.](/help/implementing/cloud-manager/assets/repos/unvalidated-repo.png)

La colonne **Type** du tableau de la page **Référentiels** identifie les référentiels fournis par Adobe (**Adobe**) et vos propres référentiels privés (**GitHub**).

Si vous devez revenir au référentiel ultérieurement pour terminer la validation, sur la page **Référentiels**, cliquez sur ![icône Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) dans la ligne représentant le référentiel GitHub que vous venez d’ajouter. Dans la liste déroulante, sélectionnez **Validation de la propriété**.



## Utiliser des référentiels cloud GitHub privés avec Cloud Manager {#using}

Une fois le référentiel GitHub validé dans Cloud Manager, l’intégration est terminée. Vous pouvez utiliser le référentiel avec Cloud Manager.

**Pour utiliser des référentiels cloud GitHub privés avec Cloud Manager :**

1. Lorsque vous créez une demande d’extraction, une vérification GitHub démarre automatiquement.

   ![Vérifications GitHub](/help/implementing/cloud-manager/assets/repos/github-checks.png)

1. Un [pipeline de qualité de code de pile pleine](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) est créé automatiquement pour chaque demande d’extraction. Ce pipeline démarre à chaque mise à jour de demande d’extraction.

1. La vérification GitHub reste en cours d’exécution jusqu’à ce que la vérification de qualité du code soit terminée. Les résultats de la qualité du code sont ensuite propagés à la vérification GitHub.

   ![Vérifications de la qualité du code GitHub.](/help/implementing/cloud-manager/assets/repos/github-code-quality.png)

Lorsque la demande d’extraction est fusionnée ou fermée, le pipeline de qualité du code de pile complète créé est automatiquement supprimé.

>[!TIP]
>
>Consultez [Annotations de vérification GitHub](github-annotations.md) pour plus d’informations sur les informations fournies par le biais de GitHub lorsque les vérifications de requête d’extraction sont exécutées.

>[!TIP]
>
>Vous pouvez contrôler les pipelines créés automatiquement pour valider chaque requête d’extraction dans un référentiel privé. Consultez le document [Configuration de la vérification GitHub pour les référentiels privés](github-check-config.md) pour plus d’informations.



## Associer des référentiels cloud GitHub privés à des pipelines {#pipelines}

Les référentiels privés validés peuvent être associés à des [pipelines full-stack et front-end.](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md).



## Limites {#limitations}

Certaines limites s’appliquent lors de l’utilisation de référentiels privés avec Cloud Manager.

* Aucune balise Git ne sera créée et transmise lors de l’utilisation de référentiels privés sur des pipelines de pile pleine de production.
* Si l’application Adobe GitHub est supprimée de votre organisation GitHub, la fonction de validation des demandes d’extraction est supprimée pour tous les référentiels.
* Les pipelines qui utilisent des référentiels cloud GitHub privés et le déclencheur de build « on-commit » ne sont pas démarrés automatiquement lorsqu’une nouvelle validation est poussée dans la branche sélectionnée.
* La [fonctionnalité de réutilisation des artefacts](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/setting-up-project.md#build-artifact-reuse) ne s’applique pas aux référentiels privés.
* Vous ne pouvez pas suspendre la validation de la demande d’extraction à l’aide de la vérification GitHub à partir de Cloud Manager. Si le référentiel GitHub est validé dans Cloud Manager, Cloud Manager tente toujours de valider les demandes d’extraction créées pour ce référentiel.
* Si votre organisation GitHub applique des restrictions IP, ouvrez un dossier de support pour obtenir la liste des adresses IP qui doivent être autorisées.
