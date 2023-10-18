---
title: Configurations et l’explorateur de configurations
description: Découvrez les configurations Adobe Experience Manager (AEM) et comment elles gèrent les paramètres de l’espace de travail dans AEM.
exl-id: 0ade04df-03a9-4976-a4b7-c01b4748474d
source-git-commit: 78ead5f15c2613d9c3bed3025b43423a66805c59
workflow-type: tm+mt
source-wordcount: '1493'
ht-degree: 60%

---

# Configurations et explorateur de configurations {#configuration-browser}

Les configurations Adobe Experience Manager (AEM) permettent de gérer les paramètres dans AEM et servent d’espaces de travail.

## Qu’est-ce qu’une configuration ?  {#what-is-a-configuration}

Une configuration peut être considérée sous deux angles différents.

* [Un administrateur](#configurations-administrator) utilise des configurations comme espaces de travail dans AEM afin de définir et de gérer des groupes de paramètres.
* [Un développeur](#configurations-developer) utilise le mécanisme de configuration sous-jacent qui implémente des configurations pour conserver et rechercher des paramètres dans AEM.

En résumé, du point de vue d’un administrateur, les configurations sont la manière dont vous créez des espaces de travail pour gérer les paramètres dans AEM, tandis que le développeur doit comprendre comment AEM utilise et gère ces configurations dans le référentiel.

Quelle que soit votre perspective, les configurations répondent à deux objectifs principaux dans AEM :

* Les configurations activent certaines fonctionnalités pour certains groupes d’utilisateurs.
* Les configurations définissent les droits d’accès pour ces fonctionnalités.

## Configurations en tant qu’administrateur {#configurations-administrator}

L’administrateur ou administratrice AEM et les auteurs et autrices peuvent considérer les configurations comme des espaces de travail. Ces espaces de travail peuvent être utilisés pour rassembler des groupes de paramètres et leur contenu associé à des fins d’organisation en implémentant des droits d’accès pour ces fonctionnalités.

Des configurations peuvent être créées pour de nombreuses fonctionnalités différentes dans AEM.

* [Segments Context Hub](/help/sites-cloud/authoring/personalization/contexthub-segmentation.md)
* [Modèles de fragment de contenu](/help/sites-cloud/administering/content-fragments/content-fragment-models.md)
* [Modèles modifiables](/help/sites-cloud/authoring/features/templates.md)
* diverses configurations de cloud

### Exemple {#administrator-example}

Par exemple, un administrateur ou une administratrice peut créer deux configurations pour les modèles modifiables.

* WKND-General
* WKND-Magazine

L’administrateur peut alors créer des modèles de page généraux à l’aide de la configuration WKND-General, puis des modèles spécifiques au magazine sous WKND-Magazine.

L’administrateur peut alors associer le WKND-General à tout le contenu du site WKND. Cependant, la configuration WKND-Magazine ne serait associée qu’au site du magazine.

En procédant comme suit :

* Lorsqu’un auteur de contenu crée une page pour le magazine, il peut choisir parmi des modèles généraux (WKND-Général) ou des modèles de magazine (WKND-Magazine).
* Lorsqu’un auteur de contenu crée une page pour une autre partie du site qui n’est pas le magazine, il peut uniquement choisir parmi les modèles généraux (WKND-General).

Des configurations similaires sont possibles non seulement pour les modèles modifiables, mais également pour les configurations de cloud, les segments ContextHub et les modèles de fragments de contenu.

### Utilisation de l’explorateur de configurations {#using-configuration-browser}

L’explorateur de configurations permet à un administrateur de créer, gérer et configurer facilement des droits d’accès aux configurations dans AEM.

>[!NOTE]
>
>Il n’est possible de créer des configurations à l’aide de l’explorateur de configurations que si votre utilisateur dispose des `admin` droits. Telle `admin` des droits sont également requis pour attribuer des droits d’accès à la configuration ou pour modifier une configuration.

#### Création d’une configuration {#creating-a-configuration}

Il est simple de créer une configuration dans AEM à l’aide du navigateur de configuration.

1. Connectez-vous à AEM as a Cloud Service et dans le menu principal, sélectionnez **Outils** -> **Général** -> **Explorateur de configurations**.
1. Appuyez ou cliquez sur **Créer**.
1. Indiquez un **Titre** et un **Nom** pour votre configuration.

   ![Création d’une configuration](assets/configuration-create.png)

   * Le **Titre** doit être descriptif.
   * Le **nom** deviendra celui du nœud dans le référentiel.
      * Il sera généré automatiquement en fonction du titre et ajusté selon les [conventions de nommage AEM](naming-conventions.md).
      * Il peut être adapté si nécessaire.
1. Vérifiez le type de configurations que vous souhaitez autoriser.
   * [Segments Context Hub](/help/sites-cloud/authoring/personalization/contexthub-segmentation.md)
   * [Modèles de fragment de contenu](/help/sites-cloud/administering/content-fragments/content-fragment-models.md)
   * [Modèles modifiables](/help/sites-cloud/authoring/features/templates.md)
   * diverses configurations de cloud
1. Appuyez ou cliquez sur **Créer**.

>[!TIP]
>
>Les configurations peuvent être imbriquées.

#### Modification des configurations et de leurs droits d’accès {#access-rights}

Si vous considérez les configurations comme des espaces de travail, les droits d’accès peuvent être définis sur ces configurations afin de définir qui peut ou non accéder à ces espaces de travail.

1. Connectez-vous à AEM as a Cloud Service et dans le menu principal, sélectionnez **Outils** -> **Général** -> **Explorateur de configurations**.
1. Sélectionnez la configuration à modifier, puis cliquez sur **Propriétés** dans la barre d’outils.
1. Sélectionnez les fonctionnalités supplémentaires que vous souhaitez ajouter à la configuration.

   >[!NOTE]
   >
   >Il n’est pas possible de désélectionner une fonction une fois la configuration créée.

1. Utilisez le bouton **Autorisations en vigueur** pour afficher une matrice des rôles et les autorisations actuellement accordées aux configurations.
   ![Fenêtre d’autorisations effectives](assets/configuration-effective-permissions.png)
1. Pour attribuer de nouvelles autorisations, saisissez le nom de l’utilisateur ou du groupe dans le champ **Sélectionner un utilisateur ou un groupe** de la section **Ajouter de nouvelles autorisations**.
   * Le champ **Sélectionner un utilisateur ou un groupe** peut être renseigné par saisie semi-automatique en fonction des utilisateurs et des rôles existants.
1. Sélectionnez l’utilisateur ou le rôle approprié dans les résultats de saisie semi-automatique.
   * Vous pouvez sélectionner plusieurs utilisateurs ou rôles.
1. Vérifiez les options d’accès qu’un ou plusieurs utilisateurs ou rôles sélectionnés doivent posséder, puis cliquez sur **Ajouter**.
   ![Ajout de droits d’accès à une configuration](assets/configuration-edit.png)
1. Répétez les étapes pour sélectionner des utilisateurs ou des rôles et attribuer des droits d’accès supplémentaires si nécessaire.
1. Appuyez ou cliquez sur **Enregistrer et fermer** une fois terminé.

## Configurations en tant que développeur {#configurations-developer}

En tant que développeur, il est important de savoir comment AEM as a Cloud Service fonctionne avec les configurations et traite la résolution de configurations.

### Séparation de la configuration et du contenu {#separation-of-config-and-content}

Bien que l’[administrateur et les utilisateurs puissent considérer les configurations comme des espaces de travail](#configurations-administrator) pour gérer différents paramètres et contenus, il est important de comprendre que les configurations et le contenu sont stockés et gérés séparément par AEM dans le référentiel.

* `/content` abrite tout le contenu.
* `/conf` abrite l’ensemble de la configuration.

Le contenu référence sa configuration associée au moyen d’une `cq:conf` . AEM effectue une recherche en fonction du contenu et de son contexte `cq:conf` pour trouver la configuration appropriée.

### Exemple {#developer-example}

Dans cet exemple, supposons que vous ayez du code d’application concernant les paramètres de la gestion des actifs numériques.

```java
Conf conf = resource.adaptTo(Conf.class);
ValueMap imageServerSettings = conf.getItem("dam/imageserver");
String bgkcolor = imageServerSettings.get("bgkcolor", "FFFFFF");
```

Le point de départ de toute recherche de configuration est une ressource de contenu située quelque part sous `/content`. Il peut s’agir d’une page, d’un composant à l’intérieur d’une page, d’une ressource ou d’un dossier DAM. Il s’agit du contenu réel pour lequel vous recherchez la configuration appropriée qui s’applique dans ce contexte.

Maintenant, avec la variable `Conf` vous pouvez récupérer l’élément de configuration spécifique qui vous intéresse. Dans ce cas, la variable `dam/imageserver`, qui est un ensemble de paramètres liés à la variable `imageserver`. L’appel `getItem` renvoie une `ValueMap`. Vous pouvez ensuite lire un `bgkcolor` et indiquez une valeur par défaut &quot;FFFFF&quot; si la propriété (ou l’élément de configuration complet) n’est pas présente.

Examinons maintenant le contenu JCR correspondant :

```text
/content/dam/wknd
    + jcr:content
      - cq:conf = "/conf/wknd"
    + image.png [dam:Asset]

/conf/wknd
    + settings
      + dam
        + imageserver [cq:Page]
          + jcr:content
            - bgkcolor = "FF0000"
```

Dans cet exemple, vous pouvez supposer ici un dossier DAM spécifique à WKND et une configuration correspondante. Démarrage dans ce dossier `/content/dam/wknd`, vous pouvez constater qu’il existe une propriété string nommée `cq:conf` qui référence la configuration qui s’applique à la sous-arborescence. La propriété est définie sur la propriété `jcr:content` d’un dossier de ressources ou d’une page. Ces liens `conf` sont explicites. Il est donc facile de les suivre en regardant simplement le contenu dans CRXDE.

Saut à l&#39;intérieur `/conf`, suivez la référence et vérifiez qu’il existe une `/conf/wknd` noeud . Il s’agit d’une configuration. Sa recherche est transparente par rapport au code de l’application. L’exemple de code n’a jamais de référence dédiée. Il est masqué derrière l’objet `Conf`. La configuration qui s’applique est contrôlée par le contenu JCR.

Vous constatez que la configuration contient un nom fixe `settings` qui contient les éléments réels, y compris le noeud `dam/imageserver` vous avez besoin dans ce cas. Un tel élément peut être considéré comme un &quot;document de paramètres&quot; et est représenté par un `cq:Page` inclusion d’un `jcr:content` contenant le contenu réel.

Enfin, la propriété s’affiche `bgkcolor` que cet exemple de code nécessite. La variable `ValueMap` tu reviens de `getItem` est basé sur le `jcr:content` noeud .

### Résolution de la configuration {#configuration-resolution}

L’exemple de base ci-dessus montrait une configuration unique. Cependant, il existe de nombreux cas où vous souhaitez avoir différentes configurations, telles qu’une configuration globale par défaut, une configuration différente pour chaque marque et peut-être une configuration spécifique pour vos sous-projets.

Pour prendre en charge cette recherche de configuration, AEM dispose d’un mécanisme d’héritage et de secours dans l’ordre de préférence suivant :

1. `/conf/<siteconfig>/<parentconfig>/<myconfig>`
   * Configuration spécifique référencée à partir de `cq:conf` quelque part dans `/content`
   * La hiérarchie est arbitraire et peut être conçue tout comme la structure de votre site. Ce n’est pas au code de l’application de le savoir
   * Modifiable au moment de l’exécution par les utilisateurs disposant de privilèges de configuration
1. `/conf/<siteconfig>/<parentconfig>`
   * Parcourir les parents pour les configurations de repli
   * Modifiable au moment de l’exécution par les utilisateurs disposant de privilèges de configuration
1. `/conf/<siteconfig>`
   * Parcourir les parents pour les configurations de repli
   * Modifiable au moment de l’exécution par les utilisateurs disposant de privilèges de configuration
1. `/conf/global`
   * Paramètres globaux du système
   * Valeurs par défaut globales de votre installation
   * Défini par un rôle `admin`
   * Modifiable au moment de l’exécution par les utilisateurs disposant de privilèges de configuration
1. `/apps`
   * Valeurs par défaut de l’application
   * Corrigé par le déploiement des applications
   * Lecture seule au moment de l’exécution
1. `/libs`
   * Paramètres par défaut du produit AEM
   * Uniquement modifiable par Adobe, accès au projet non autorisé
   * Corrigé par le déploiement des applications
   * Lecture seule au moment de l’exécution

### Utilisation des configurations {#using-configurations}

Les configurations dans AEM reposent sur les configurations basées sur le contexte Sling. Les lots Sling fournissent une API de service qui peut être utilisée pour obtenir des configurations basées sur le contexte. Les configurations basées sur le contexte sont des configurations qui sont liées à une ressource de contenu ou à une arborescence de ressources, comme [décrit dans l’exemple précédent](#developer-example).

Pour plus d’informations sur les configurations basées sur le contexte, des exemples et leur utilisation, [consultez la documentation Sling](https://sling.apache.org/documentation/bundles/context-aware-configuration/context-aware-configuration.html).

### Console Web ConfMgr {#confmgr-web-console}

À des fins de débogage et de test, une console Web **ConfMgr** dans `https://<host>:<port>/system/console/conf` peut afficher des configurations pour un chemin/élément donné.

![ConfMgr](assets/configuration-confmgr.png)

Indiquez simplement :

* **Content Path** (Chemin d’accès au contenu)
* **Item** (Élément)
* **User** (Utilisateur)

Cliquez sur **Résoudre** vous pouvez ainsi voir quelles configurations sont résolues et obtenir des exemples de code qui aident à résoudre ces configurations.

### Console Web de configuration basée sur le contexte {#context-aware-web-console}

À des fins de débogage et de test, une console Web de **configuration basée sur le contexte** dans `https://<host>:<port>/system/console/slingcaconfig` permet d’interroger des configurations basées sur le contexte dans le référentiel et d’afficher leurs propriétés.

![Console Web de configuration basée sur le contexte](assets/configuration-context-aware-console.png)

Indiquez simplement :

* **Content Path** (Chemin d’accès au contenu)
* **Config Name** (Nom de configuration)

Cliquez sur **Résoudre** vous pouvez ainsi récupérer les chemins de contexte et les propriétés associés pour la configuration sélectionnée.
