---
title: Référentiels Cloud Manager
description: Découvrez comment créer, afficher et supprimer vos référentiels Git dans Cloud Manager.
exl-id: 6e1cf636-78f5-4270-9a21-38b4d5e5a0b0
source-git-commit: af8ab1f741c658dcb47bdf0d37e403fcb180631a
workflow-type: tm+mt
source-wordcount: '588'
ht-degree: 96%

---


# Référentiels Cloud Manager {#cloud-manager-repos}

Découvrez comment créer, afficher et supprimer vos référentiels Git dans Cloud Manager.

>[!NOTE]
>
>Les référentiels sont limités à 300 pour tous les programmes d’une société ou d’une organisation IMS donnée.

## Ajouter et gérer des référentiels {#add-manage-repos}

Suivez ces étapes pour afficher et gérer les référentiels dans Cloud Manager.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Dans la **Aperçu du programme** page, appuyez ou cliquez sur **Référentiels** pour basculer vers l’onglet **Référentiels** page.

1. Cliquez sur **Ajouter un référentiel**.

   ![Bouton Ajouter un référentiel](/help/implementing/cloud-manager/assets/repos/create-repo2.png)

1. Saisissez le nom et la description demandés, puis cliquez sur **Enregistrer**.

   ![Boîte de dialogue Ajouter un référentiel](/help/implementing/cloud-manager/assets/repos/repo-1.png)

Lorsque l’assistant se ferme, votre nouveau référentiel s’affiche dans le tableau.

Vous pouvez sélectionner le référentiel dans le tableau, puis cliquer sur le bouton représentant des points de suspension et sélectionner **Copier l’URL du référentiel**, **Afficher et mettre à jour** ou **Supprimer**.

![Options du référentiel](/help/implementing/cloud-manager/assets/repos/create-repo3.png)

Vous pouvez également sélectionner les référentiels créés dans Cloud Manager lors de l’ajout ou de la modification de pipelines. Consultez [Pipelines CI-CD](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) pour en savoir plus.

Il existe un référentiel principal unique ou une branche pour chaque pipeline donné. Grâce à la [prise en charge des sous-modules Git](#git-submodule-support), de nombreuses branches secondaires peuvent être incluses au moment de la création.

>[!NOTE]
>
>Un utilisateur ou une utilisatrice doit disposer du rôle **Responsable de déploiement** ou **Propriétaire de l’entreprise** pour pouvoir ajouter un référentiel.

## Supprimer un référentiel {#delete-repo}

La suppression d’un référentiel entraînera les éléments suivants :

* Le nom du référentiel supprimé sera inutilisable pour de nouveaux référentiels qui pourraient être créés ultérieurement.
   * Le message d’erreur `Repository name should be unique within organization.` s’affiche dans de tels cas.
* Le référentiel supprimé sera indisponible dans Cloud Manager et ne pourra donc pas être lié à un pipeline.

Pour supprimer un référentiel dans Cloud Manager, procédez comme suit.

1. Sur la page **Présentation du programme**, cliquez sur l’onglet **Référentiels** et accédez à la page **Référentiels**.

1. Sélectionnez le référentiel, cliquez sur le bouton représentant des points de suspension, puis sélectionnez **Supprimer** pour supprimer le référentiel.

   ![Supprimer le référentiel](/help/implementing/cloud-manager/assets/repos/delete-repo.png)

## Prise en charge des sous-modules Git {#git-submodule-support}

Les sous-modules Git peuvent être utilisés pour fusionner le contenu de plusieurs branches dans des référentiels Git au moment de la création.

Lorsque le processus de création de Cloud Manager s’exécute, une fois le référentiel configuré pour le pipeline cloné et la branche configurée extraite, si la branche contient un fichier `.gitmodules` dans le répertoire racine, la commande est exécutée.

La commande suivante extrait chaque sous-module dans le répertoire approprié.

```
$ git submodule update --init
```

Cette technique constitue une alternative potentielle à la solution décrite dans le document [Utiliser plusieurs référentiels Git sources](/help/implementing/cloud-manager/managing-code/working-with-multiple-source-git-repositories.md) pour les organisations qui maîtrisent l’utilisation des sous-modules Git et qui ne souhaitent pas gérer de processus de fusion externe.

Par exemple, supposons qu’il existe trois référentiels, chacun contenant une seule branche nommée `main`. Dans le référentiel principal, c’est-à-dire celui qui est configuré dans les pipelines, la branche `main` contient un fichier `pom.xml` qui déclare les projets contenus dans les deux autres référentiels.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="https://maven.apache.org/POM/4.0.0" xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="https://maven.apache.org/POM/4.0.0 https://maven.apache.org/maven-v4_0_0.xsd">
    <modelVersion>4.0.0</modelVersion>
   
    <groupId>customer.group.id</groupId>
    <artifactId>customer-reactor</artifactId>
    <version>0.0.1-SNAPSHOT</version>
    <packaging>pom</packaging>
   
    <modules>
        <module>project-a</module>
        <module>project-b</module>
    </modules>
   
</project>
```

Vous pouvez ensuite ajouter des sous-modules pour les deux autres référentiels.

```shell
$ git submodule add -b main https://git.cloudmanager.adobe.com/ProgramName/projectA/ project-a
$ git submodule add -b main https://git.cloudmanager.adobe.com/ProgramName/projectB/ project-b
```

Vous obtenez un fichier `.gitmodules` similaire au fichier suivant.

```text
[submodule "project-a"]
    path = project-a
    url = https://git.cloudmanager.adobe.com/ProgramName/projectA/
    branch = main
[submodule "project-b"]
    path = project-b
    url = https://git.cloudmanager.adobe.com/ProgramName/projectB/
    branch = main
```

Pour plus d’informations sur les sous-modules Git, consultez le [Manuel de référence Git](https://git-scm.com/book/fr/v2/Git-Tools-Submodules).

### Restrictions et recommandations {#limitations-recommendations}

Lors de l’utilisation de sous-modules Git, tenez compte des limitations suivantes.

* L’URL Git doit se trouver exactement dans la syntaxe décrite dans la section précédente.
* Seuls les sous-modules situés à la racine de la branche sont pris en charge.
* Pour des raisons de sécurité, n’incorporez pas d’informations d’identification dans les URL Git.
* Sauf si nécessaire, il est vivement recommandé d’utiliser des sous-modules superficiels.
   * Pour ce faire, exécutez `git config -f .gitmodules submodule.<submodule path>.shallow true` pour chaque sous-module.
* Les références des sous-modules Git sont stockées vers des validations Git spécifiques. Par conséquent, lorsque des modifications sont apportées au référentiel de sous-module, la validation référencée doit être mise à jour.
   * Par exemple, en utilisant `git submodule update --remote`
