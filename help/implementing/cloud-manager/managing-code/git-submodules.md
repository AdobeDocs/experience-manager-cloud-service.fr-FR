---
title: Prise en charge des sous-modules Git
description: Découvrez comment vous pouvez utiliser des sous-modules Git pour fusionner le contenu de plusieurs branches dans des référentiels Git lors de la création.
exl-id: fa5b0f49-4b87-4f39-ad50-7e62094d85f4
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 8a53bef8bdf592869c895cbaca1e79034e52f856
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 24%

---

# Prise en charge des sous-modules Git pour les référentiels Adobe {#git-submodule-support}

Les sous-modules Git peuvent être utilisés pour fusionner le contenu de plusieurs branches dans des référentiels Git au moment de la création.

Lorsque le processus de création Cloud Manager s’exécute, il clone le référentiel du pipeline et extrait la branche. Si un fichier `.gitmodules` existe dans le répertoire racine de la branche, la commande correspondante est exécutée.

La commande suivante extrait chaque sous-module dans le répertoire approprié.

```
$ git submodule update --init
```

Cette technique offre une alternative à la solution décrite dans [Utilisation de plusieurs référentiels Git Source](/help/implementing/cloud-manager/managing-code/working-with-multiple-source-git-repositories.md). Il est idéal pour les organisations qui maîtrisent les sous-modules Git et qui préfèrent ne pas gérer de processus de fusion externe.

Supposons, par exemple, qu’il existe trois référentiels. Chaque référentiel contient une branche unique nommée `main`. Dans le référentiel principal, c’est-à-dire celui qui est configuré dans les pipelines, la branche `main` contient un fichier `pom.xml` qui déclare les projets contenus dans les deux autres référentiels :

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

Vous pouvez ensuite ajouter des sous-modules pour les deux autres référentiels :

```shell
$ git submodule add -b main https://git.cloudmanager.adobe.com/ProgramName/projectA/ project-a
$ git submodule add -b main https://git.cloudmanager.adobe.com/ProgramName/projectB/ project-b
```

Le résultat est un fichier `.gitmodules` similaire au fichier suivant :

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

Consultez également le [Manuel de référence Git](https://git-scm.com/book/fr/v2/Git-Tools-Submodules) pour plus d’informations sur les sous-modules Git.

## Notes d’utilisation des référentiels Adobe {#usage-notes-recommendations-adobe-repos}

* L’URL Git doit se trouver exactement dans la syntaxe décrite dans la section précédente.
* Seuls les sous-modules situés à la racine de la branche sont pris en charge.
* Pour des raisons de sécurité, n’incorporez pas les informations d’identification dans les URL Git.
* Sauf indication contraire, Adobe vous recommande d’utiliser des sous-modules superficiels en exécutant les opérations suivantes :
  `git config -f .gitmodules submodule.<submodule path>.shallow true` pour chaque sous-module.
* Les références des sous-modules Git sont stockées vers des validations Git spécifiques. Par conséquent, lorsque des modifications sont apportées au référentiel de sous-module, la validation référencée doit être mise à jour.
Par exemple, en utilisant ce qui suit :

  `git submodule update --remote`

## Prise en charge des sous-modules Git pour les référentiels privés {#private-repositories}

La prise en charge des sous-modules Git dans les [référentiels privés](private-repositories.md) est généralement similaire à leur utilisation avec les référentiels Adobe.

Cependant, après avoir configuré votre fichier `pom.xml` et exécuté les commandes `git submodule`, vous devez ajouter un fichier `.gitmodules` au répertoire racine du référentiel d’agrégation pour que Cloud Manager reconnaisse la configuration de sous-module.

![fichier .gitmodules](assets/gitmodules.png)

![Agrégateur](assets/aggregator.png)

### Remarques sur l’utilisation {#usage-notes-recommendations-private-repos}

* Les URL Git de sous-module peuvent être au format HTTPS ou SSH, mais doivent pointer vers un référentiel GitHub.com. L’ajout d’un sous-module de référentiel Adobe à un référentiel agrégateur GitHub ou inversement n’est pas pris en charge.
* Les sous-modules GitHub doivent être accessibles par le biais de l’application GitHub Adobe.
* [Les limites d’utilisation des sous-modules Git avec des référentiels gérés par Adobe](#usage-notes-recommendations-adobe-repos) s’appliquent également.
