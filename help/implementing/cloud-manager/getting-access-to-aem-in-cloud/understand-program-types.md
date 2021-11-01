---
title: Présentation du programme et des types de programmes
description: Présentation du programme et des types de programmes – Cloud Services
exl-id: 507df619-a5b5-419a-9e38-db77541425a2
source-git-commit: 7e51fb98c76a5913ef237aca3b66c73a8263f4ff
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 100%

---

# Présentation des programmes et des types de programmes {#understanding-programs}

Dans Cloud Manager, l’entité cliente se trouve tout en haut de l’écran et peut comporter plusieurs programmes. Chaque programme ne peut contenir qu’un environnement de production mais peut compter plusieurs environnements autres que de production.

Le diagramme suivant présente la hiérarchie des entités dans Cloud Manager.

![image](assets/program-types1.png)

## Référentiel de code source {#source-code-repository}

Le programme Cloud Manager est fourni avec son propre référentiel Git.

Pour qu’un utilisateur puisse accéder au référentiel Git de Cloud Manager, il doit utiliser un client Git avec un outil de ligne de commande, un client Git visuel autonome ou l’IDE de l’utilisateur tel qu’Eclipse, IntelliJ ou NetBeans.

Une fois le client Git configuré, vous pouvez gérer votre référentiel Git à partir de l’interface utilisateur de Cloud Manager. Pour en savoir plus sur la gestion de Git à l’aide de l’interface utilisateur de Cloud Manager, voir la section [Accès à Git](/help/implementing/cloud-manager/managing-code/accessing-repos.md).

Pour commencer à développer l’application AEM Cloud, une copie locale du code de l’application doit être effectuée en l’extrayant du référentiel Cloud Manager vers un emplacement de l’ordinateur local où l’utilisateur souhaite créer son référentiel.

```java
$ git clone {URL}
```

>[!NOTE]
>Un utilisateur peut extraire une copie de son code et effectuer des modifications dans le référentiel de code local. Une fois prêt, l’utilisateur peut valider les modifications de code dans le référentiel de code distant dans Cloud Manager.

## Types de programme {#program-types}

Un utilisateur peut créer un programme **Sandbox** ou de **Production**.

* Un *Programme de production* est créé pour activer dans le futur le trafic actif au moment approprié.
Consultez [Présentation des programmes de production](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/production-programs/introduction-production-programs.html?lang=fr) pour plus d’informations.


* Un *programme Sandbox* est généralement créé pour les besoins de formation, à des fins de démonstration, d’activation, de preuve de concept ou de documentation. Ces programmes ne sont pas destinés à gérer un trafic réel et comporteront des restrictions absentes d’un programme de production. Ils incluront Sites et Assets et seront pourvus automatiquement d’une branche Git comprenant un exemple de code, un environnement de développement et un pipeline non productif.
Consultez [Présentation des programmes Sandbox](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/sandbox-programs/introduction-sandbox-programs.html?lang=fr) pour plus d’informations.
