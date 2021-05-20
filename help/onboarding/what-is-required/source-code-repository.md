---
title: Référentiel de code source - Cloud Services
description: Référentiel de code source - Cloud Services
source-git-commit: 23349f3350631f61f80b54b69104e5a19841272f
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 23%

---


# Référentiel de code source {#source-code-repository}

Le programme Cloud Manager est fourni avec son propre référentiel Git.

Pour qu’un utilisateur puisse accéder au référentiel Git de Cloud Manager, il doit utiliser un client Git avec un outil de ligne de commande, un client Git visuel autonome ou l’IDE de l’utilisateur tel qu’Eclipse, IntelliJ, NetBeans.

Une fois qu’un client Git est configuré, vous pouvez gérer votre référentiel Git à partir de l’interface utilisateur de Cloud Manager. Pour en savoir plus sur la gestion de Git à l’aide de l’interface utilisateur de Cloud Manager, voir [Accès à Git](/help/implementing/cloud-manager/accessing-git.md).

Pour commencer à développer l’application AEM Cloud, une copie locale du code de l’application doit être effectuée en l’extrayant du référentiel Cloud Manager vers un emplacement sur l’ordinateur local où il souhaite créer son référentiel.

```java
$ git clone {URL}
```

>[!NOTE]
>
>Un utilisateur peut extraire une copie de son code et effectuer des modifications dans le référentiel de code local. Une fois prêt, l’utilisateur peut valider les modifications de code dans le référentiel de code distant dans Cloud Manager.
