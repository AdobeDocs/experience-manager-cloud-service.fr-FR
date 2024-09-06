---
title: Prise en charge des sous-modules Git
description: Découvrez comment vous pouvez utiliser des sous-modules Git pour fusionner le contenu de plusieurs branches dans des référentiels Git lors de la création.
exl-id: fa5b0f49-4b87-4f39-ad50-7e62094d85f4
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 5d6d3374f2dd95728b2d3ed0cf6fab4092f73568
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 90%

---

# Prise en charge des sous-modules Git pour les référentiels Adobe {#git-submodule-support}

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

Vous trouverez plus d’informations sur les sous-modules Git dans le [Manuel de référence Git](https://git-scm.com/book/fr/v2/Git-Tools-Submodules).

### Restrictions et recommandations {#limitations-recommendations}

Lors de l’utilisation de sous-modules git avec des référentiels gérés par Adobe, tenez compte des limites suivantes.

* L’URL Git doit se trouver exactement dans la syntaxe décrite dans la section précédente.
* Seuls les sous-modules situés à la racine de la branche sont pris en charge.
* Pour des raisons de sécurité, n’incorporez pas d’informations d’identification dans les URL Git.
* Sauf si nécessaire, il est vivement recommandé d’utiliser des sous-modules superficiels.
   * Pour ce faire, exécutez `git config -f .gitmodules submodule.<submodule path>.shallow true` pour chaque sous-module.
* Les références des sous-modules Git sont stockées vers des validations Git spécifiques. Par conséquent, lorsque des modifications sont apportées au référentiel de sous-module, la validation référencée doit être mise à jour.
   * Par exemple, en utilisant `git submodule update --remote`

## Prise en charge des sous-modules Git pour les référentiels privés {#private-repositories}

La prise en charge des sous-modules Git pour les [référentiels privés](private-repositories.md) est largement similaire à celle des référentiels Adobe.

Cependant, après avoir configuré votre fichier `pom.xml` et exécuté les commandes `git submodule`, vous devez ajouter un fichier `.gitmodules` dans le répertoire racine du référentiel de l’agrégateur pour que Cloud Manager détecte la configuration du sous-module.

![fichier .gitmodules](assets/gitmodules.png)

![Agrégateur](assets/aggregator.png)

### Restrictions et recommandations {#limitations-recommendations-private-repos}

Lors de l’utilisation de sous-modules Git avec des référentiels privés, tenez compte des restrictions suivantes.

* Les URL Git des sous-modules peuvent être au format HTTPS ou SSH, mais elles doivent diriger vers un référentiel github.com
   * L’ajout d’un sous-module de référentiel d’Adobe à un référentiel d’agrégateur GitHub ou vice-versa ne fonctionnera pas.
* Les sous-modules GitHub doivent être accessibles pour l’application GitHub Adobe.
* [Les limites d’utilisation des sous-modules Git avec des référentiels gérés par Adobe](#limitations-recommendations) s’appliquent également.
