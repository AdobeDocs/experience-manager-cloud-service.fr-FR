---
title: Ajout de référentiels privés dans Cloud Manager
description: Découvrez comment configurer Cloud Manager pour utiliser vos propres référentiels GitHub privés.
source-git-commit: 7f598a623c3003b20a074c31749382df7f5f5ca6
workflow-type: tm+mt
source-wordcount: '836'
ht-degree: 48%

---


# Ajout de référentiels privés dans Cloud Manager {#private-repositories}

En configurant Cloud Manager pour qu’il fonctionne avec vos propres référentiels GitHub privés, vous pouvez valider votre code directement dans votre référentiel GitHub via Cloud Manager, rendant ainsi inutile la synchronisation cohérente de votre code avec le référentiel Adobe.

>[!NOTE]
>
>Cette fonctionnalité est réservée au GitHub public. La prise en charge du GitHub auto-hébergé n’est pas disponible.

## Configuration {#configuration}

La configuration se compose de deux étapes principales :

1. [Ajout d’un référentiel](#add-repo)
1. [Validation de la propriété du référentiel privé](#validate-ownership)

### Ajouter un référentiel {#add-repo}

1. Dans Cloud Manager, à partir du **Aperçu du programme** , sélectionnez **Référentiels** pour basculer vers l’onglet **Référentiels** page et clic **Ajouter un référentiel**.

1. Dans la boîte de dialogue **Ajouter un référentiel**, sélectionnez **Référentiel privé** comme type de référentiel.

1. Fournir des détails de votre référentiel

   * **Nom du référentiel** : un nom expressif.
   * **URL du référentiel** : l’URL du référentiel, qui doit se terminer par `.git`.
   * **Description** (facultatif) : une description plus longue du référentiel selon les besoins.

   ![Ajout de votre propre référentiel.](/help/implementing/cloud-manager/assets/repos/add-own-github.png)

1. Sélectionnez **Enregistrer**.

>[!TIP]
>
>Pour plus d’informations sur la gestion des référentiels dans Cloud Manager, voir [Référentiels Cloud Manager](/help/implementing/cloud-manager/managing-code/managing-repositories.md).

### Valider la propriété du référentiel privé {#validate-ownership}

Cloud Manager connaît désormais votre référentiel GitHub, mais il doit toujours y accéder. Pour accorder l’accès, vous devez installer l’application GitHub d’Adobe et vérifier que vous êtes propriétaire du référentiel spécifié.

1. Après avoir ajouté votre propre référentiel, la variable **Validation de la propriété du référentiel privé** s’ouvre.

   ![Validation de la propriété du référentiel privé.](/help/implementing/cloud-manager/assets/repos/private-repo-validate.png)

1. Cloud Manager utilise une application GitHub pour interagir de manière sécurisée avec votre référentiel.
   * Une personne propriétaire de votre organisation GitHub doit installer l’application qui se trouve à l’adresse `https://github.com/apps/cloud-manager-for-aem` et accordez l’accès au référentiel.
   * Consultez la documentation de GitHub pour plus d’informations sur la manière dont cela est effectué.

1. Pour renforcer la sécurité, vous devez créer un fichier secret dans la branche par défaut de votre référentiel. Sélectionner **Générer**.

1. Confirmez la génération du fichier secret en appuyant ou en cliquant sur **Confirmer**.

   ![Confirmation de la génération du secret.](/help/implementing/cloud-manager/assets/repos/confirm-generation.png)

1. De retour dans la fenêtre **Validation de la propriété du référentiel privé**, Cloud Manager a généré le contenu du fichier privé dans le champ **Contenu du fichier secret**. Copiez le contenu de ce champ.

   * Le contenu du fichier secret ne s’affichera qu’une seule fois. Si vous ne copiez pas le contenu avant de fermer cette fenêtre, régénérez le secret.

   ![Copie du contenu du fichier secret.](/help/implementing/cloud-manager/assets/repos/new-secret.png)

1. Créez un fichier dans la branche par défaut de votre référentiel GitHub appelé `.well-known/adobe/cloud-manager-challenge`, collez le contenu du fichier secret dans ce fichier et enregistrez-le.

1. Une fois l’application installée et le fichier secret présent dans le référentiel, vous pouvez sélectionner **Valider** dans le **Validation de la propriété du référentiel privé** boîte de dialogue.

L’application peut être installée et un fichier secret peut être créé dans n’importe quel ordre. Toutefois, vous devez effectuer les deux étapes avant de pouvoir valider.

Jusqu’à la validation, le référentiel est répertorié avec une icône rouge indiquant qu’il n’est pas encore validé et qu’il ne peut pas encore être utilisé.

![Référentiel non validé.](/help/implementing/cloud-manager/assets/repos/unvalidated-repo.png)

La variable **Type** identifie facilement les référentiels fournis par l’Adobe (**Adobe**) et vos propres référentiels GitHub (**GitHub**).

Si vous devez revenir au référentiel à une date ultérieure pour terminer la validation, sur la page **Référentiels** , sélectionnez le bouton représentant des points de suspension dans la ligne représentant le référentiel GitHub que vous venez d’ajouter, puis sélectionnez **Validation de propriété** dans le menu déroulant.

## Utilisation de référentiels privés avec Cloud Manager {#using}

Une fois le référentiel GitHub validé dans Cloud Manager, l’intégration est terminée et vous pouvez utiliser le référentiel avec Cloud Manager.

1. Lorsque vous créez une demande d’extraction, une vérification GitHub démarre automatiquement.

   ![Vérifications GitHub.](/help/implementing/cloud-manager/assets/repos/github-checks.png)

1. Un [pipeline de qualité de code de pile pleine](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) est créé automatiquement pour chaque demande d’extraction. Ce pipeline démarre à chaque mise à jour de demande d’extraction.

1. La vérification GitHub reste à l’état d’exécution jusqu’à ce que les vérifications de la qualité du code soient terminées. Les résultats de la qualité du code sont ensuite propagés à la vérification GitHub.

   ![Vérifications de la qualité du code GitHub.](/help/implementing/cloud-manager/assets/repos/github-code-quality.png)

Lorsque la demande d’extraction est fermée ou fusionnée, le pipeline de qualité de code de pile pleine créé est automatiquement supprimé.

>[!TIP]
>
>Voir le document [Annotations de vérification GitHub](github-annotations.md) pour plus d’informations sur les informations fournies via GitHub lors de l’exécution des vérifications de requête de tirage.

>[!TIP]
>
>Vous pouvez contrôler les pipelines créés automatiquement pour valider chaque demande d’extraction dans un référentiel privé. Consultez le document [Configuration de la vérification GitHub pour les référentiels privés](github-check-config.md) pour plus d’informations.

## Association de référentiels privés à des pipelines {#pipelines}

Les référentiels privés validés peuvent être associés à [pipelines full-stack et frontend.](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md)

>[!NOTE]
>
>Les pipelines de niveau web et de configuration ne sont pas pris en charge par les référentiels privés.

## Limites {#limitations}

Certaines limites s’appliquent lors de l’utilisation de référentiels privés avec Cloud Manager.

* Vous ne pouvez pas suspendre la validation de la requête de tirage à l’aide de la vérification GitHub de Cloud Manager.
   * Si le référentiel GitHub est validé dans Cloud Manager, Cloud Manager tente toujours de valider les demandes d’extraction créées pour ce référentiel.
* Si l’application GitHub d’Adobe est supprimée de votre organisation GitHub, la fonctionnalité de validation des demandes d’extraction est supprimée pour tous les référentiels.
* Les pipelines de niveau web et de configuration ne sont pas pris en charge par les référentiels privés.
* Aucune balise git ne sera créée et transmise lors de l’utilisation de référentiels privés sur des pipelines de pile complète de production.
* Les pipelines qui utilisent des référentiels privés et le déclencheur de version on-commit ne sont pas démarrés automatiquement lorsqu’une nouvelle validation est poussée dans la branche sélectionnée.
* [Fonctionnalité de réutilisation des artefacts](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/setting-up-project.md#build-artifact-reuse) ne s’applique pas aux référentiels privés.
