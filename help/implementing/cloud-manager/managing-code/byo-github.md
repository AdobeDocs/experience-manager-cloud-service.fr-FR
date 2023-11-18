---
title: Utilisation de vos propres référentiels GitHub dans Cloud Manager
description: Découvrez comment configurer Cloud Manager pour utiliser vos propres référentiels GitHub.
feature: Release Information
source-git-commit: bc3c054e781789aa2a2b94f77b0616caec15e2ff
workflow-type: tm+mt
source-wordcount: '721'
ht-degree: 1%

---


# Utilisation de vos propres référentiels GitHub dans Cloud Manager {#byo-github}

En configurant Cloud Manager pour qu’il fonctionne avec vos propres référentiels GitHub, vous pouvez valider votre code directement dans votre référentiel GitHub via Cloud Manager, rendant ainsi inutile la synchronisation cohérente de votre code avec le référentiel Adobe.

>[!NOTE]
>
>Cette fonctionnalité n’est disponible que pour [le programme d&#39;adoption précoce.](/help/implementing/cloud-manager/release-notes/current.md#early-adoption)

## Configuration {#configuration}

La configuration se compose de deux étapes principales :

1. [Ajouter un référentiel](#add-repo)
1. [Validation de la propriété du référentiel privé](#validate-ownership)

### Ajouter un référentiel {#add-repo}

1. Dans Cloud Manager, à partir du **Aperçu du programme** , sélectionnez **Référentiels** pour basculer vers l’onglet **Référentiels** page et clic **Ajouter un référentiel**.

1. Dans le **Ajouter un référentiel** boîte de dialogue, sélectionnez **Référentiel privé** comme type de référentiel.

1. Fournir les détails de votre référentiel

   * **Nom du référentiel** - Un nom expressif
   * **URL du référentiel** : URL du référentiel, qui doit se terminer par `.git`
   * **Description** (facultatif) - Une description plus longue du référentiel selon les besoins.

   ![Ajouter son propre référentiel](/help/implementing/cloud-manager/assets/repos/add-own-github.png)

1. Sélectionnez **Enregistrer**.

>[!TIP]
>
>Pour plus d’informations sur la gestion des référentiels dans Cloud Manager, voir [Référentiels Cloud Manager](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md).

### Validation de la propriété du référentiel privé {#validate-ownership}

Cloud Manager connaît désormais votre référentiel GitHub, mais il doit toujours y accéder. Pour accorder l’accès, vous devez installer l’application GitHub Adobe et vérifier que vous êtes propriétaire du référentiel spécifié.

1. Après avoir ajouté votre propre référentiel, la variable **Validation de la propriété du référentiel privé** s’ouvre.

   ![Validation de la propriété du référentiel privé](/help/implementing/cloud-manager/assets/repos/private-repo-validate.png)

1. Cloud Manager utilise une application GitHub pour interagir de manière sécurisée avec votre référentiel.
   * Un propriétaire de votre organisation GitHub doit installer l’application située à l’adresse `https://github.com/apps/cloud-manager-for-aem-stage` et accordez l’accès au référentiel.
   * Consultez la documentation de GitHub pour plus d’informations sur la manière dont cela est effectué.

1. Pour améliorer la sécurité, vous devez créer un fichier secret dans la branche par défaut de votre référentiel. Sélectionner **Générer**.

1. Confirmez la génération du fichier secret en appuyant ou en cliquant **Confirmer**.

   ![Confirmer la génération du secret](/help/implementing/cloud-manager/assets/repos/confirm-generation.png)

1. De retour dans le **Validation de la propriété du référentiel privé** , Cloud Manager a généré le contenu du fichier privé dans la variable **Contenu du fichier secret** champ . Copiez le contenu de ce champ.

   * Le contenu du fichier secret ne s&#39;affichera qu&#39;une seule fois. Si vous ne copiez pas le contenu avant de fermer cette fenêtre, régénérez le secret.

   ![Copie du contenu du fichier secret](/help/implementing/cloud-manager/assets/repos/new-secret.png)

1. Créez un fichier dans la branche par défaut de votre référentiel GitHub appelé `.well-known/adobe/cloud-manager-challenge` et collez le contenu du fichier secret dans ce fichier et enregistrez-le.

1. Une fois l’application installée et le fichier secret présent dans le référentiel, vous pouvez sélectionner **Valider** dans le **Validation de la propriété du référentiel privé** boîte de dialogue.

L’application peut être installée et un fichier secret peut être créé dans n’importe quel ordre. Toutefois, vous devez effectuer les deux étapes avant de pouvoir valider.

Jusqu’à la validation, le référentiel est répertorié avec une icône rouge indiquant qu’il n’est pas encore validé et qu’il ne peut pas encore être utilisé.

![Référentiel non validé](/help/implementing/cloud-manager/assets/repos/unvalidated-repo.png)

La variable **Type** identifie facilement les référentiels fournis par l’Adobe (**Adobe**) et vos propres référentiels GitHub (**GitHub**).

Si vous devez revenir au référentiel à une date ultérieure pour terminer la validation, sur la page **Référentiels** , sélectionnez le bouton représentant des points de suspension dans la ligne représentant le référentiel GitHub que vous venez d’ajouter, puis sélectionnez **Validation de propriété** dans le menu déroulant.

## Utilisation de vos propres référentiels GitHub avec Cloud Manager {#using}

Une fois le référentiel GitHub validé dans Cloud Manager, l’intégration est terminée et vous pouvez utiliser le référentiel avec Cloud Manager.

1. Lorsque vous créez une requête de tirage, une vérification GitHub démarre automatiquement.

   ![Vérifications GitHub](/help/implementing/cloud-manager/assets/repos/github-checks.png)

1. Pour chaque requête d’extraction, une [pipeline de qualité de code de pile complet](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) sera créé automatiquement. Ce pipeline est démarré à chaque mise à jour de requête de tirage.

1. La vérification GitHub reste en cours d’exécution jusqu’à ce que les contrôles de qualité du code soient terminés. Les résultats de qualité du code seront ensuite propagés au contrôle GitHub.

   ![Vérifications de qualité du code GitHub](/help/implementing/cloud-manager/assets/repos/github-code-quality.png)

Lorsque la requête de tirage est fermée ou fusionnée, le pipeline de qualité de code de pile complet créé est automatiquement supprimé.

## Limites {#limitations}

Limites lors de l’utilisation de vos propres référentiels GitHub avec Cloud Manager.

* Vous ne pouvez pas utiliser les référentiels GitHub comme source directe de référentiel pour les pipelines que vous gérez.
   * Cette fonctionnalité est prévue.
* Vous ne pouvez pas suspendre la validation de la requête de tirage à l’aide de la vérification GitHub du gestionnaire de cloud.
   * Si le référentiel GitHub est validé dans Cloud Manager, Cloud Manager tente toujours de valider les demandes d’extraction créées pour ce référentiel.
Si l’application GitHub Adobe est supprimée de votre organisation GitHub, la fonctionnalité de validation des demandes d’extraction est supprimée pour tous les référentiels.
