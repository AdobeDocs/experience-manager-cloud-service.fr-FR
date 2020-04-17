---
title: Gestion des versions du projet Maven
description: Gestion des versions du projet Maven - Cloud Services
translation-type: ht
source-git-commit: cedc14b0d71431988238d6cb4256936a5ceb759b

---


# Gestion des versions du projet Maven {#maven-project-version-handling}


## Comprendre la gestion des versions du projet Maven {#understanding-project-version}

Pour les déploiements dans l’environnement intermédiaire et dans l’environnement de production, Cloud Manager génère une version incrémentée unique.

Cette version est affichée sur la page des détails d’exécution du pipeline, ainsi que sur la page d’activité. Lorsqu’une génération est exécutée, le projet Maven est mis à jour pour utiliser cette version et une balise est créée dans le référentiel Git avec cette version comme nom.

Si la version originale du projet répond à certains critères, la version mise à jour du projet Maven fusionne la version originale du projet et la version générée par Cloud Manager. Toutefois, la balise utilise toujours la version générée. Pour que cette fusion se produise, la version originale du projet doit être formée avec exactement trois segments de version, par exemple 1.0.0 ou 1.2.3, mais pas 1.0 ou 1, et la version originale ne doit pas se terminer par -SNAPSHOT.

Si la version d’origine ne répond pas à ces critères, la version générée sera ajoutée à la version d’origine en tant que segment de nouvelle version. La version générée sera également légèrement modifiée pour inclure un tri et une gestion corrects des versions. Par exemple, en supposant une version générée de 2019.926.121356.0000020490 :

| **Version** | **version dans pom.xml** | **Commentaire** |
|---|---|---|
| 1.0.0 | 1.0.0.2019_0926_121356_0000020490 | Version originale correctement formée |
| 1.0.0-SNAPSHOT | 2019.926.121356.0000020490 | Version Snapshot, écrasée |
| 1 | 2019.926.121356.0000020490 | Version incomplète, écrasée |

>[!NOTE]
>
>Que la version d’origine ait été incorporée ou non dans la version initialisée de Cloud Manager, la version d’origine est disponible sous la forme d’une propriété Maven nommée *cloudManagerOriginalVersion.*
