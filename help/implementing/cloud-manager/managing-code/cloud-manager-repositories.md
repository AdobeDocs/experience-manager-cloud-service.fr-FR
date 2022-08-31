---
title: Référentiels Cloud Manager
description: Découvrez comment créer, afficher et supprimer vos référentiels Git dans Cloud Manager.
exl-id: 6e1cf636-78f5-4270-9a21-38b4d5e5a0b0
source-git-commit: 430179bf13c1fff077c515eed0676430e9e7f341
workflow-type: tm+mt
source-wordcount: '582'
ht-degree: 30%

---


# Référentiels Cloud Manager {#cloud-manager-repos}

Découvrez comment créer, afficher et supprimer vos référentiels Git dans Cloud Manager.

>[!NOTE]
>
>Il existe une limite de 300 référentiels pour tous les programmes d’une société ou d’une organisation IMS donnée.

## Ajout et gestion de référentiels {#add-manage-repos}

Suivez ces étapes pour afficher et gérer les référentiels dans Cloud Manager.

1. Sur la page **Aperçu du programme**, cliquez sur l’onglet **Référentiels** et accédez à la page **Référentiels**.

1. Cliquez sur **Ajouter un référentiel** pour démarrer l’assistant.

   ![Bouton Ajouter un référentiel](/help/implementing/cloud-manager/assets/repos/create-repo2.png)

1. Saisissez le nom et la description requis, puis cliquez sur **Enregistrer**.

   ![Boîte de dialogue Ajouter un référentiel](/help/implementing/cloud-manager/assets/repos/repo-1.png)

Lorsque l’assistant se ferme, votre nouveau référentiel s’affiche dans le tableau.

Vous pouvez sélectionner le référentiel dans le tableau, cliquer sur le bouton représentant des points de suspension et sélectionner **Copier l’URL du référentiel**, **Afficher et mettre à jour** ou **Supprimer**.

![Options du référentiel](/help/implementing/cloud-manager/assets/repos/create-repo3.png)

Vous pouvez également sélectionner les référentiels créés dans Cloud Manager lors de l’ajout ou de la modification de pipelines. Reportez-vous au document [Pipelines CI-CD](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) pour en savoir plus.

Il existe un référentiel Principal ou une branche pour un pipeline donné. Avec [prise en charge des sous-modules git](#git-submodule-support), de nombreuses branches secondaires peuvent être incluses au moment de la création.

>[!NOTE]
>
>Un utilisateur doit disposer du rôle **Responsable de déploiement** ou **Propriétaire de l’entreprise** pour pouvoir ajouter un référentiel.

## Suppression d’un référentiel {#delete-repo}

La suppression d’un référentiel entraînera les éléments suivants :

* Le nom du référentiel supprimé sera inutilisable pour de nouveaux référentiels qui pourraient être créés ultérieurement.
   * Message d’erreur `Repository name should be unique within organization.` s’affiche dans de tels cas.
* Rendre le référentiel supprimé indisponible dans Cloud Manager et indisponible pour la liaison à un pipeline.

Pour supprimer un référentiel dans Cloud Manager, procédez comme suit.

1. Sur la page **Aperçu du programme**, cliquez sur l’onglet **Référentiels** et accédez à la page **Référentiels**.

1. Sélectionnez le référentiel, cliquez sur le bouton représentant des points de suspension, puis sélectionnez **Supprimer** pour supprimer le référentiel.

   ![Supprimer le référentiel](/help/implementing/cloud-manager/assets/repos/delete-repo.png)

## Prise en charge des sous-modules Git {#git-submodule-support}

Les sous-modules Git peuvent être utilisés pour fusionner le contenu de plusieurs branches dans des référentiels Git au moment de la création.

Lorsque le processus de création de Cloud Manager s’exécute, une fois le référentiel configuré pour le pipeline cloné et la branche configurée extraite, si la branche contient un fichier `.gitmodules` dans le répertoire racine, la commande est exécutée.

La commande suivante extrait chaque sous-module dans le répertoire approprié.

```
$ git submodule update --init
```

Cette technique constitue une alternative potentielle à la solution décrite dans le document. [Utilisation de plusieurs référentiels Git source](/help/implementing/cloud-manager/managing-code/working-with-multiple-source-git-repositories.md) pour les organisations qui maîtrisent l’utilisation des sous-modules git et qui ne souhaitent pas gérer de processus de fusion externe.

Par exemple, supposons qu’il existe trois référentiels, chacun contenant une seule branche nommée `main`. Dans le référentiel Principal, c’est-à-dire celui configuré dans les pipelines, la variable `main` comporte une branche `pom.xml` déclarant les projets contenus dans les deux autres référentiels.

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

Cela se traduit par une `.gitmodules` semblable à ce qui suit.

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

Vous trouverez plus d’informations sur les sous-modules git dans la section [Guide de référence Git.](https://git-scm.com/book/fr/v2/Git-Tools-Submodules)

### Restrictions et recommandations {#limitations-recommendations}

Lors de l’utilisation de sous-modules git, veuillez tenir compte des limitations suivantes.

* L’URL git doit être exactement conforme à la syntaxe décrite dans la section précédente.
* Seuls les sous-modules situés à la racine de la branche sont pris en charge.
* Pour des raisons de sécurité, n’incorporez pas les informations d’identification dans les URL Git.
* Sauf si nécessaire, il est vivement recommandé d’utiliser des sous-modules superficiels.
   * Pour ce faire, exécutez `git config -f .gitmodules submodule.<submodule path>.shallow true` pour chaque sous-module.
* Les références de sous-module Git sont stockées vers des validations git spécifiques. Par conséquent, lorsque des modifications sont apportées au référentiel de sous-module, la validation référencée doit être mise à jour.
   * Par exemple, en utilisant `git submodule update --remote`
