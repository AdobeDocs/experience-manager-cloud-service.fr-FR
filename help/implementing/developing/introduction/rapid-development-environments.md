---
title: Environnements de développement rapide
description: Découvrez comment utiliser les environnements de développement rapide pour des itérations de développement rapides dans un environnement cloud.
exl-id: 1e9824f2-d28a-46de-b7b3-9fe2789d9c68
feature: Developing
role: Admin, Architect, Developer
source-git-commit: eb87467b1cd3338a409c2aeded74b3bb38d2e58c
workflow-type: tm+mt
source-wordcount: '5446'
ht-degree: 24%

---

# Environnements de développement rapide {#rapid-development-environments}

Pour déployer des modifications, les environnements de développement cloud actuels nécessitent l’utilisation d’un processus qui utilise des règles de sécurité et de qualité de code étendues appelées pipeline CI/CD. Dans les cas où des modifications rapides et itératives sont nécessaires, Adobe a introduit des environnements de développement rapide (RDE).

Les RDE permettent aux développeurs et développeuses de déployer et d’examiner rapidement les modifications, ce qui réduit le temps nécessaire pour tester les fonctionnalités qui fonctionnent dans un environnement de développement local.

Une fois les modifications testées dans un RDE, elles peuvent être déployées dans un environnement de développement cloud standard via le pipeline Cloud Manager.

Les environnements de développement et de développement rapide doivent se limiter au développement, à l’analyse des erreurs et aux tests fonctionnels. Ils ne sont pas conçus pour traiter des charges de travail élevées ou de grandes quantités de contenu.

>[!NOTE]
> Les environnements de développement rapide doivent se limiter au développement, à l’analyse des erreurs et aux tests fonctionnels. Ils ne sont pas conçus pour traiter des charges de travail élevées ou de grandes quantités de contenu.

>[!NOTE]
> Contactez les développeurs et développeuses du RDE sur Adobe [canal Discord](https://discord.com/channels/1131492224371277874/1245304281184079872). N’hésitez pas à poser des questions ou à donner votre avis sur les sujets liés au RDE.

>[!VIDEO](https://video.tv.adobe.com/v/3415582/?quality=12&learn=on)


Vous pouvez visionner d’autres vidéos présentant [comment le configurer](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/developing/rde/how-to-setup), [comment l’utiliser](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/developing/rde/how-to-use), et montrant [le cycle de vie du développement](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/developing/rde/development-life-cycle) à l’aide du RDE.

## Présentation {#introduction}

Les RDE peuvent être utilisés pour les configurations de code, de contenu et Apache ou Dispatcher. Contrairement aux environnements de développement cloud standard, les développeurs peuvent utiliser des outils de ligne de commande locaux pour synchroniser le code créé localement avec un RDE.

Chaque programme est configuré avec un RDE. S’il existe des comptes Sandbox, ils sont mis en veille après quelques heures d’inutilisation.

Lors de leur création, les RDE sont définis sur la dernière version de Adobe Experience Manager (AEM) disponible. Une réinitialisation du RDE, qui peut être effectuée à l’aide de Cloud Manager, enchaîne le RDE et le définit sur la dernière version d’AEM disponible.

En règle générale, un RDE est utilisé par un seul développeur à la fois, à des fins de test et de débogage d’une fonctionnalité spécifique. Une fois la session de développement terminée, le RDE peut être réinitialisé à son état par défaut pour une utilisation ultérieure.

D’autres RDE peuvent être mis sous licence pour des programmes de production (hors sandbox).

## Activer le RDE dans un programme {#enabling-rde-in-a-program}

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Cliquez sur le programme auquel vous souhaitez ajouter un RDE pour en afficher les détails.

   * Les RDE peuvent être ajoutés aux [programmes sandbox](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md) et aux [programmes de production](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-production-programs.md).

1. Sur la page **Aperçu du programme**, sur la carte **Environnements**, cliquez sur **Ajouter un environnement**.

   ![Carte Environnements](/help/implementing/cloud-manager/assets/no-environments.png)

   * L’option **Ajouter un environnement** est également disponible dans l’onglet **Environnements**.

     ![Onglet Environnements](/help/implementing/cloud-manager/assets/environments-tab.png)

   * L’option **Ajouter un environnement** peut être désactivée en raison d’un niveau d’autorisation insuffisant ou de ressources sous licence.

1. Dans la boîte de dialogue **Ajouter un environnement**, procédez comme suit :

   * Sélectionnez **Développement rapide** sous l’en-tête **Sélectionner le type d’environnement**.
      * Le nombre d’environnements disponibles/utilisés est indiqué entre parenthèses derrière le type d’environnement.
   * Attribuez un **Nom** à l’environnement.
   * Ajoutez une **Description** de l’environnement (facultatif).
   * Sélectionnez une **Région Cloud**.

   ![Boîte de dialogue Ajouter un environnement](/help/implementing/cloud-manager/assets/add-environment-wizard.png)

1. Cliquez sur **Enregistrer** pour ajouter l’environnement spécifié.

L’écran **Aperçu** affiche désormais votre nouvel environnement dans la carte **Environnements**.

Lors de la création, les RDE sont définis sur la dernière version d’AEM disponible. Une réinitialisation du RDE, qui peut également être effectuée à l’aide de Cloud Manager, enchaîne le RDE et le définit sur la dernière version d’AEM disponible.

Pour plus d’informations sur l’utilisation de Cloud Manager pour créer des environnements, gérer leur accès et attribuer des domaines personnalisés, consultez [Programmes et types de programmes](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md) dans la documentation de Cloud Manager.

## Installation des outils de ligne de commande du RDE {#installing-the-rde-command-line-tools}

Après avoir ajouté un RDE pour votre programme à l’aide de Cloud Manager, vous pouvez interagir avec celui-ci en configurant les outils de ligne de commande comme indiqué ci-dessous :

>[!IMPORTANT]
>
>Assurez-vous que vous avez installé la version 20 de [Node et NPM](https://nodejs.org/en/download/) pour que l’interface de ligne de commande d’Adobe I/O (AIO) et les modules externes connexes fonctionnent correctement.


1. Installez les outils de l’interface de ligne de commande AIO conformément à cette [procédure](https://developer.adobe.com/app-builder/docs/guides/runtime_guides/tools/cli-install).
1. Installez le plug-in RDE AEM pour les outils de l’interface de ligne de commande AIO :

   ```
   aio plugins:install @adobe/aio-cli-plugin-aem-rde
   aio plugins:update
   ```

1. Connectez-vous à l’aide du client Adobe I/O (AIO).

   ```
   aio login
   ```

   Les informations de connexion (jeton) sont stockées dans la configuration d’API globale et ne prennent donc en charge qu’une seule connexion et organisation. Si vous souhaitez utiliser plusieurs RDE nécessitant des connexions ou des organisations différentes, suivez l’exemple ci-dessous pour introduire des contextes.

   <details><summary>Suivez cet exemple pour configurer un contexte local pour l’une de vos connexions RDE</summary>
   Pour stocker les informations de connexion localement dans un fichier `.aio` dans le répertoire actuel dans un contexte spécifique, procédez comme suit. Un contexte est également un moyen astucieux de configurer un environnement ou un script CI/CD.  Pour utiliser cette fonctionnalité, veillez à utiliser au moins la version 10.3.1 d’aio-cli. Mettez-le à jour à l’aide de « npm install -g @adobe/aio-cli ».

   Créez maintenant un contexte appelé m`ycontext` que vous définissez comme contexte par défaut à l’aide du plug-in d’authentification avant d’appeler la commande de connexion.

   ```
   aio config set --json -l "ims.contexts.mycontext" "{ cli.bare-output: false }"
   aio auth ctx -s mycontext
   aio login --no-open
   ```

   >[!NOTE]
   > La commande login avec l&#39;option `--no-open` génère une URL dans le terminal au lieu d&#39;ouvrir votre navigateur par défaut. Vous pouvez le copier et l’ouvrir dans la fenêtre **incognito** de votre navigateur. Cette fonctionnalité garantit que la session en cours dans la fenêtre principale du navigateur n’est pas affectée, ce qui vous permet de vous connecter avec le compte et l’organisation spécifiques requis pour votre tâche.

   La première commande crée une configuration de contexte de connexion, appelée `mycontext`, dans votre fichier de configuration de `.aio` local (le fichier est créé si nécessaire). La deuxième commande définit le `mycontext` de contexte sur le contexte « actif », c’est-à-dire la valeur par défaut.

   Une fois cette configuration en place, la commande login stocke automatiquement les jetons de connexion dans le `mycontext` contextuel, le maintenant ainsi en local.

   Plusieurs contextes peuvent être gérés en conservant les configurations locales dans plusieurs dossiers. Il est également possible de configurer plusieurs contextes dans un seul fichier de configuration et de basculer entre eux en modifiant le contexte « actuel ».
   </details>

1. Configurez le plug-in RDE pour utiliser votre organisation, votre programme et votre environnement. La commande de configuration ci-dessous fournit de manière interactive à l’utilisateur une liste des programmes de son organisation et affiche les environnements RDE de ce programme parmi lesquels choisir.

   ```
   aio aem:rde:setup
   ```

   Vous pouvez ignorer l’étape de configuration si vous utilisez un environnement basé sur des scripts. Dans ce cas, incluez les valeurs d’organisation, de programme et d’environnement directement dans chaque commande. [Voir la section Commandes RDE ci-dessous pour plus d’informations](#rde-cli-commands).

### Configuration interactive {#installing-the-rde-command-line-tools-interactive}

La commande setup demande si la configuration fournie doit être stockée localement ou globalement.

```
Setup the CLI configuration necessary to use the RDE commands.
? Do you want to store the information you enter in this setup procedure locally? (y/N)
```

Choisir `no` à

* stockez l’organisation, le programme et l’environnement globalement dans votre configuration aio.
* utilisez un seul RDE uniquement.

Choisissez `yes` pour effectuer les opérations suivantes :

* Stocker localement l&#39;organisation, le programme et l&#39;environnement dans le répertoire courant, dans un fichier `.aio`. Cette approche est pratique si vous souhaitez valider le fichier dans le contrôle de version afin que d’autres personnes clonant le référentiel Git puissent l’utiliser.
* être en mesure de travailler avec de nombreux RDE, de sorte que le passage à un autre répertoire utilise cette configuration à la place.
* Utilisez la configuration dans un contexte de programmation comme un script, qui peut la référencer.


Une fois la configuration locale ou globale sélectionnée, la commande de configuration tente de lire l’identifiant de votre organisation à partir de votre connexion actuelle, puis de lire les programmes de l’organisation. Si l’organisation est introuvable, vous pouvez la saisir manuellement avec quelques conseils.

```
Selected only organization: XYXYXYXYXYXYXYXXYY
retrieving programs of your organization ...
```

Une fois les programmes récupérés, l’utilisateur peut effectuer une sélection dans la liste et également saisir du texte à filtrer. Lorsque le programme est sélectionné, une liste d’environnements de RDE s’affiche. S’il n’existe qu’un seul programme, qu’un seul environnement RDE disponible ou les deux, il est sélectionné automatiquement.

Pour afficher le contexte d’environnement actuel, exécutez la commande suivante :

```aio aem rde setup --show```

La commande répond avec un résultat similaire à celui-ci :

```Current configuration: cm-p1-e1: programName - environmentName (organization: ...@AdobeOrg)```

### Procédure de paramétrage manuel dans un environnement non interactif {#manual-setup}

Dans les environnements où aucun utilisateur ne peut exécuter de manière interactive la commande de configuration (tels que CI/CD ou scripts), une configuration manuelle est requise. Vous pouvez définir les paramètres de l’organisation, du programme et de l’environnement à l’aide des étapes ci-dessous.


<details>
  <summary>Développez pour trouver des détails sur la configuration manuelle .</summary>

1. Configurez votre ID d’organisation et remplacez la chaîne alphanumérique par votre propre ID d’organisation.

   `aio config:set cloudmanager_orgid 4E03EQC05D34GL1A0B49421C@AdobeOrg`

   * Vous pouvez rechercher votre propre ID d’organisation à l’aide de la méthode décrite dans la section [Afficher votre ID d’organisation](https://experienceleague.adobe.com/en/docs/core-services/interface/administration/organizations#concept_EA8AEE5B02CF46ACBDAD6A8508646255).

1. Configurez ensuite votre ID de programme :

   `aio config:set cloudmanager_programid 12345`

1. Configurez ensuite l’identifiant d’environnement auquel le RDE va être associé :

   `aio config:set cloudmanager_environmentid 123456`

1. Après avoir configuré le plug-in, connectez-vous en procédant comme suit :

   `aio login`

   Ces étapes nécessitent que vous soyez membre du profil de produit Cloud Manager **Développeur - Cloud Service**. Voir [&#x200B; Affecter des membres de l’équipe à des profils de produit Cloud Manager - Attribuer le profil de produit Développeur &#x200B;](/help/journey-onboarding/assign-profiles-cloud-manager.md#assign-developer) pour plus d’informations.

Pour plus d’informations et des démonstrations, regardez le tutoriel vidéo [comment configurer un RDE (06:24)](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/developing/rde/how-to-setup).
</details>

## Utilisation du RDE lors du développement d’une nouvelle fonctionnalité {#using-rde-while-developing-a-new-feature}

Pour développer une nouvelle fonctionnalité, Adobe recommande le workflow suivant :

* Lorsqu’un jalon intermédiaire est atteint et validé localement avec AEM as a Cloud Service SDK, validez le code dans une branche de fonctionnalité Git. La branche ne doit pas encore faire partie de la ligne principale, bien que la validation de Git soit facultative. Ce qui constitue un « jalon intermédiaire » varie en fonction des habitudes de l’équipe. Par exemple, quelques nouvelles lignes de code, une demi-journée de travail ou l’achèvement d’une sous-fonctionnalité.

* Réinitialisez le RDE s’il a été utilisé par une autre fonctionnalité et si vous souhaitez le [réinitialiser à un état par défaut](#reset-rde). <!-- Alexandru: hiding for now, do not delete This can be done by way of [Cloud Manager](#reset-the-rde-cloud-manager) or by way of the [command line](#reset-the-rde-command-line). -->La réinitialisation prend quelques minutes et supprime tout le contenu et le code existants. Vous pouvez utiliser la commande de statut RDE pour confirmer que le RDE est prêt. Le RDE revient avec la version la plus récente d’AEM.

  >[!IMPORTANT]
  >
  >Si vos environnements d’évaluation et de production ne reçoivent pas les mises à jour de version automatique d’AEM et se trouvent derrière la dernière version, le RDE peut exécuter une autre version d’AEM. Par conséquent, le comportement du code dans le RDE peut ne pas correspondre à son fonctionnement dans l’évaluation et la production. Dans ce cas, il est important d’effectuer des tests approfondis du code lors de l’évaluation avant de le déployer en production.


* À l’aide de l’interface de ligne de commande RDE, synchronisez le code local avec le RDE. Vous pouvez installer différents types de fichiers, notamment :

   * Packages de contenu
   * Lots spécifiques
   * Fichiers de configuration OSGi
   * Fichiers de contenu
   * Fichiers ZIP contenant des configurations Apache/Dispatcher

  Il est également possible de référencer un module de contenu distant. Voir [&#x200B; Outils de ligne de commande RDE](/help/implementing/developing/introduction/rapid-development-environments.md#rde-cli-commands) pour plus d’informations. Vous pouvez utiliser la commande Statut pour vérifier que le déploiement a réussi. Vous pouvez éventuellement utiliser le gestionnaire de modules pour installer des modules de contenu.

* Testez le code dans l’outil RDE. Les URL de création et de publication sont disponibles dans Cloud Manager.

* Si le code ne se comporte pas comme prévu, utilisez des techniques de débogage standard pour comprendre le problème et effectuez les modifications nécessaires. Sans valider les modifications du code dans Git (puisqu’elles n’ont pas été validées), utilisez l’interface de ligne de commande locale pour synchroniser le code avec l’outil RDE. Continuez ainsi jusqu’à ce que le problème soit résolu.

* Une fois que le code se comporte comme prévu, validez le code sur la branche de la fonctionnalité Git.

* Le code synchronisé avec l’outil RDE n’utilise pas de pipeline Cloud Manager. Vous devez donc maintenant utiliser un pipeline hors production Cloud Manager pour déployer la branche de fonctionnalité Git dans l’environnement de développement cloud. Ce processus confirme que le code passe les points de contrôle qualité de Cloud Manager et vous permet d’être sûr que le code sera déployé ultérieurement à l’aide du pipeline de production Cloud Manager.

* Répétez les étapes ci-dessus pour chaque jalon intermédiaire jusqu’à ce que tout le code de la fonctionnalité soit prêt et s’exécute correctement dans l’environnement de l’outil RDE et l’environnement de développement cloud.

* Déployez le code en production au moyen du pipeline de production Cloud Manager.

## Utilisation du RDE pour déboguer une fonctionnalité existante {#use-rde-to-debug-an-existing-feature}

Le workflow est similaire au développement d’une nouvelle fonctionnalité. La différence est que le code synchronisé avec l’outil RDE reflète le libellé Git de ce qui a été envoyé à l’environnement où le problème s’est produit. Ce workflow permet d’assurer la cohérence lors de l’examen ou de la reproduction du problème. En outre, il peut s’avérer utile de déployer du contenu correspondant à l’environnement en amont. Cette approche peut être réalisée en exportant et en important des packages de contenu.

## Collaboration de plusieurs développeurs sur le même RDE {#multiple-developers-collaborating-on-the-same-rde}

Un outil RDE prend en charge un seul projet à la fois. Comme le code est synchronisé entre un environnement de développement local et l’environnement du RDE, il est plus naturel pour un développeur de l’utiliser seul à un moment donné.

Cependant, avec une coordination étroite, il est possible pour plusieurs développeurs de valider une fonctionnalité spécifique ou de déboguer un problème spécifique. La solution est que chaque développeur conserve ses projets locaux synchronisés de sorte que les modifications de code apportées par un développeur particulier soient absorbées par les autres développeurs. Dans le cas contraire, un développeur risque de remplacer par inadvertance le code de l’autre. La stratégie recommandée est que chaque développeur valide ses modifications dans une branche Git partagée avant la synchronisation avec l’outil RDE, de sorte que les autres développeurs extraient les modifications avant d’apporter les leurs.

## Outils de ligne de commande RDE Commandes {#rde-cli-commands}

### Aide/Informations générales {#help}

* Pour obtenir une liste des commandes, saisissez :

  `aio aem:rde`

* Pour obtenir une aide détaillée sur une commande, saisissez :

  `aio aem rde <command> --help`

### Indicateurs globaux {#global-flags}

* Pour une sortie moins détaillée, utilisez l’indicateur calme :

  `aio aem rde <command> --quiet`

  Cet indicateur supprime certains éléments, tels que les éléments à 360° et les barres de progression, et limite le besoin de saisie de l&#39;utilisateur.

* Pour JSON au lieu de la sortie du journal de la console, utilisez l’indicateur json :

  `aio aem rde <command> --json`

  Cet indicateur renvoie un JSON valide lors de la suppression de toute sortie de console. Voir les exemples JSON plus bas.

* Pour éviter de configurer les informations de connexion au RDE à l’aide de la commande de configuration ou de toute création de configuration aio, utilisez les trois indicateurs pour l’organisation, le programme et l’environnement :

  `aio aem rde <command> --organizationId=<value> --programId=<value> --environmentId=<value>`

  Nécessite l’exécution d’une ```aio login```.

### Déployer sur l’outil RDE {#deploying-to-rde}

Cette section explique comment utiliser l’interface de ligne de commande du RDE pour déployer, installer ou mettre à jour diverses ressources. Ces ressources comprennent les éléments suivants :

* Packages de contenu
* Configurations OSGi
* Lots
* Fichiers de contenu
* Configurations Apache ou Dispatcher

Le modèle d’utilisation général est le suivant : `aio aem:rde:install <artifact>`.

Vous trouverez quelques exemples ci-dessous :

#### Déployer un package de contenu {#deploy-content-package}

`aio aem:rde:install sample.demo.ui.apps.all-1.0.0-SNAPSHOT.zip`

La réponse pour un déploiement réussi ressemble à ce qui suit :

```
...
#1: deploy completed for content-package sample.demo.ui.apps.all-1.0.0-SNAPSHOT.zip on author,publish - done by 9E072FC75D54FE1A2B49431C@AdobeID at 2022-09-13T11:32:06.229Z
```

Vous pouvez éventuellement référencer un référentiel distant :

`aio aem:rde:install -t content-package "https://repo1.maven.org/maven2/com/adobe/aem/guides/aem-guides-wknd.all/2.1.0/aem-guides-wknd.all-2.1.0.zip"`

Par défaut, les artefacts sont déployés sur les niveaux de création et de publication, mais l’indicateur `-s` peut être utilisé pour cibler un niveau spécifique.

Tout package AEM peut être déployé, par exemple des packages comportant du code, du contenu ou un [package conteneur](/help/implementing/developing/introduction/aem-project-content-package-structure.md#container-packages) (également appelé package « all »).

>[!IMPORTANT]
>
>L’installation du package de contenu ci-dessus ne déploie pas la configuration Dispatcher pour le projet WKND. Déployez-le séparément en suivant les étapes de « déploiement d’une configuration Apache/Dispatcher ».

#### Déploiement d’une configuration OSGI {#deploy-OSGI-config}

`aio aem:rde:install com.adobe.granite.demo.MyServlet.cfg.json`

Où la réponse pour un déploiement réussi ressemble à ce qui suit :

```
...
#2: deploy completed for osgi-config com.adobe.granite.demo.MyServlet.cfg.json on author,publish - done by 9E0725C05D54FE1A0B49431C@AdobeID at 2022-09-13T11:54:36.390Z
```

#### Déploiement d’un lot {#deploy-bundle}

Pour déployer un lot, utilisez :

`aio aem:rde:install ~/.m2/repository/org/apache/felix/org.apache.felix.gogo.jline/1.1.8/org.apache.felix.gogo.jline-1.1.8.jar`

Où la réponse pour un déploiement réussi ressemble à ce qui suit :

```
...
#3: deploy staged for osgi-bundle org.apache.felix.gogo.jline-1.1.8.jar on author,publish - done by 9E0725C05D53BE1A0B49431C@AdobeID at 2022-09-14T07:54:28.882Z
```

#### Déployer un fichier de contenu {#deploy-content-file}

Pour déployer un fichier de contenu, saisissez la commande suivante :

`aio aem:rde:install world.txt -p /apps/hello.txt`

Où la réponse pour un déploiement réussi ressemble à ce qui suit :

```
..
#4: deploy completed for content-file world.txt on author,publish - done by 9E0729C05C54FE1A0B49431C@AdobeID at 2022-09-14T07:49:30.644Z
```

#### Déploiement d’une configuration Apache/Dispatcher {#deploy-apache-config}

Pour ce type de configuration, l’ensemble de la structure de dossiers doit se présenter sous la forme d’un fichier zip.

Dans le module `dispatcher` d’un projet AEM, vous pouvez compresser la configuration Dispatcher en exécutant la commande maven suivante :

`mvn clean package`

Ou à l’aide de la commande de compression ci-dessous à partir du répertoire `src` du module `dispatcher` :

`zip -y -r dispatcher.zip .`

Déployez ensuite la configuration à l’aide de la commande suivante :

`aio aem:rde:install target/aem-guides-wknd.dispatcher.cloud-X.X.X-SNAPSHOT.zip`

>[!TIP]
>
>La commande ci-dessus suppose que vous déployez les configurations Dispatcher du projet [WKND](https://github.com/adobe/aem-guides-wknd). Veillez à remplacer le `X.X.X` par le numéro de version du projet WKND correspondant ou votre numéro de version spécifique au projet lors du déploiement de la configuration Dispatcher de votre projet.

>[!NOTE]
>
>Le RDE prend en charge la configuration Dispatcher Dispatcher en « mode flexible », mais pas en « mode hérité ». Consultez la [documentation de Dispatcher](/help/implementing/dispatcher/disp-overview.md#validation-debug) pour plus d’informations sur ces deux modes. Vous pouvez également consulter la documentation relative à la [migration vers le mode flexible](/help/implementing/dispatcher/validation-debug.md#migrating), si vous ne l’avez pas déjà fait.

Un déploiement réussi génère une réponse qui ressemble à ce qui suit :

```
..
#5 deploy completed for dispatcher-config dispatcher.zip on author,publish - done by 9E0735C05T54FE1A0B49431C@AdobeID at 2022-10-03T10:26:31.286Z
Logs:
  Cloud manager validator 2.0.49
  2022/10/03 10:26:37 No issues found
  Syntax OK
```

Le code déployé sur le RDE n’entre pas dans le cadre d’un pipeline Cloud Manager et de ses points de contrôle qualité associés. Cependant, le code fait l’objet d’une analyse qui signale les erreurs, comme illustré dans l’exemple de code ci-dessous :

```
$ aio aem:rde:install ~/.m2/repository/org/apache/felix/org.apache.felix.gogo.jline/1.1.8/org.apache.felix.gogo.jline-1.1.8.jar
...
#19: deploy staged for osgi-bundle org.apache.felix.gogo.jline-1.1.8.jar on author,publish - done by 9E0725C05D74FR1A0B49431C@AdobeID at 2022-09-14T07:54:28.882Z
Logs:
The analyser found the following errors for author :
[requirements-capabilities] com.adobe.aem.temp:org.apache.felix.gogo.jline:1.1.8: Artifact com.adobe.aem.temp:org.apache.felix.gogo.jline:1.1.8 requires [org.apache.felix.gogo.jline/1.1.8] org.apache.felix.gogo; filter:="(&(org.apache.felix.gogo=command.implementation)(version>=1.0.0)(!(version>=2.0.0)))"; effective:=active in start level 20 but no artifact is providing a matching capability in this start level.
[api-regions-exportsimports] com.adobe.aem.temp:org.apache.felix.gogo.jline:1.1.8: Bundle org.apache.felix.gogo.jline:1.1.8 is importing package(s) [org.jline.builtins, org.jline.utils, org.apache.felix.service.command, org.apache.felix.service.threadio, org.jline.terminal, org.jline.reader, org.apache.felix.gogo.runtime, org.jline.reader.impl] in start level 20 but no bundle is exporting these for that start level.
The analyser found the following errors for publish :
[requirements-capabilities] com.adobe.aem.temp:org.apache.felix.gogo.jline:1.1.8: Artifact com.adobe.aem.temp:org.apache.felix.gogo.jline:1.1.8 requires [org.apache.felix.gogo.jline/1.1.8] org.apache.felix.gogo; filter:="(&(org.apache.felix.gogo=command.implementation)(version>=1.0.0)(!(version>=2.0.0)))"; effective:=active in start level 20 but no artifact is providing a matching capability in this start level.
[api-regions-exportsimports] com.adobe.aem.temp:org.apache.felix.gogo.jline:1.1.8: Bundle org.apache.felix.gogo.jline:1.1.8 is importing package(s) [org.jline.builtins, org.jline.utils, org.apache.felix.service.command, org.apache.felix.service.threadio, org.jline.terminal, org.jline.reader, org.apache.felix.gogo.runtime, org.jline.reader.impl] in start level 20 but no bundle is exporting these for that start level.
```

L’exemple de code ci-dessus illustre le comportement si un lot n’est pas résolu. Dans ce cas, il est « intermédiaire » et n’est installé que si ses exigences (importations manquantes, dans ce cas) sont satisfaites par l’installation d’un autre code.

#### Déployer la configuration liée au pipeline (configurations yaml) {#deploy-config-pipeline}

Les configurations spécifiques à un environnement (un ou plusieurs fichiers yaml) décrites dans l’article [Utilisation de pipelines de configuration](/help/operations/config-pipeline.md) peuvent être déployées comme suit :

`aio aem:rde:install -t env-config ./my-config-folder`
Où `my-config-folder` est le dossier parent contenant vos configurations yaml.

Il est également possible d’installer un fichier zip contenant l’arborescence de dossiers de configuration :

`aio aem:rde:install -t env-config config.zip`

Notez que le tableau envTypes du fichier yaml inclut la valeur `rde`, comme dans l’exemple ci-dessous :

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["rde"]
```

### Déployer du code front-end en fonction des thèmes du site et des modèles de site. {#deploying-themes-to-rde}

Les RDE prennent en charge le code front-end créé avec des [thèmes de site](/help/sites-cloud/administering/site-creation/site-themes.md) et [modèles de site](/help/sites-cloud/administering/site-creation/site-templates.md). Au lieu d’utiliser le Cloud Manager [Pipeline front-end](/help/sites-cloud/administering/site-creation/enable-front-end-pipeline.md) comme d’autres types d’environnements, les RDE déploient les packages front-end à l’aide d’une directive de ligne de commande.

Comme d’habitude, créez votre package front-end à l’aide de npm :

`npm run build`

Il génère un dossier `dist/`, de sorte que votre dossier de packages front-end contienne un fichier `package.json` et `dist` dossier :

```
ls ./path-to-frontend-pkg-folder/
...
dist
package.json
```

Maintenant, vous êtes prêt à déployer le package front-end sur le RDE en pointant vers le dossier de packages front-end de la manière suivante :

```
aio aem:rde:install -t frontend ./path-to-frontend-pkg-folder/
...
#1: deploy completed for frontend frontend-pipeline.zip on author,publish - done by ... at 2024-01-18T15:33:22.898Z
Logs:
> Deployed artifact wknd-1.0.0-1705592008-26e7ec1a
> with workspace hash 692021864642a20d6d298044a927d66c0d9cf2adf42d4cca0c800a378ac3f8d3
```

Vous pouvez également compresser le fichier `package.json` et `dist` dossier , puis déployer ce fichier compressé :

`zip -r frontend-pkg.zip ./path-to-frontend-pkg-folder/dist ./path-to-frontend-pkg-folder/package.json`

```
aio aem:rde:install -t frontend frontend-pkg.zip
...
#1: deploy completed for frontend frontend-pipeline.zip on author,publish - done by ... at 2024-01-18T15:33:22.898Z
Logs:
> Deployed artifact wknd-1.0.0-1705592008-26e7ec1a
> with workspace hash 692021864642a20d6d298044a927d66c0d9cf2adf42d4cca0c800a378ac3f8d3
```

>[!NOTE]
>
>Les noms des fichiers dans le package front-end doivent respecter les conventions de dénomination suivantes :
>
> * `dist` dossier , pour le dossier du package de sortie de génération npm
> * `package.json`, pour le package de dépendances npm

>[!TIP]
>
>Si vous avez créé votre RDE avant avril 2023 et que vous rencontrez le `UNEXPECTED_API_ERROR` lors de l’utilisation de la fonctionnalité front-end pour la première fois, cela peut être dû à une configuration obsolète. Pour résoudre ce problème, supprimez l’environnement et créez-en un.

### Vérifier le statut du RDE {#checking-rde-status}

Vous pouvez utiliser l’interface de ligne de commande du RDE pour vérifier si l’environnement est prêt à être déployé et pour consulter les déploiements effectués à l’aide du plug-in du RDE.

Exécutant les éléments suivants :

`aio aem:rde:status`

Renvoie avec les éléments suivants :

```
Info for cm-p12345-e987654
Environment: Ready
- Bundles Author:
 com.adobe.granite.sample.demo-1.0.0.SNAPSHOT
- Bundles Publish:
 com.adobe.granite.sample.demo-1.0.0.SNAPSHOT
- Configurations Author:
 com.adobe.granite.demo.MyServlet
- Configurations Publish:
 com.adobe.granite.demo.MyServlet
```

Si la commande renvoie une note sur le déploiement des instances, vous pouvez continuer et effectuer la prochaine mise à jour, mais la dernière ne sera peut-être pas encore visible sur l’instance.

### Afficher l’historique de déploiement {#show-deployment-history}

Vous pouvez vérifier l’historique des déploiements effectués sur le RDE en exécutant la commande suivante :

`aio aem:rde:history`

Qui renvoie une réponse sous la forme :

`#1: deploy completed for content-package aem-guides-wknd.all-2.1.0.zip on author,publish - done by 029039A55D4DE16A0A494025@AdobeID at 2022-09-12T14:41:55.393Z`

### Supprimer du RDE {#deleting-from-rde}

Vous pouvez utiliser l’outil d’interface de ligne de commande pour supprimer des configurations et des lots déployés précédemment dans le RDE. Utilisez la commande `status` pour obtenir une liste des éléments pouvant être supprimés, qui inclut les `bsn` des lots et des `pid` des configurations à référencer dans la commande de suppression.

Par exemple, si `com.adobe.granite.demo.MyServlet.cfg.json` a été installé, la référence `bsn` est juste `com.adobe.granite.demo.MyServlet`, sans le suffixe **cfg.json**.

La suppression des modules ou fichiers de contenu n’est pas prise en charge. Pour les supprimer, réinitialisez le RDE, qui revient à son état par défaut.

Consultez l’exemple ci-dessous pour plus de détails :

```
aio aem:rde:delete com.adobe.granite.csrf.impl.CSRFFilter
#13: delete completed for osgi-config com.adobe.granite.csrf.impl.CSRFFilter on author - done by karl at 2022-09-12T22:01:01.955Z
#14: delete completed for osgi-config com.adobe.granite.csrf.impl.CSRFFilter on publish - done by karl at 2022-09-12T22:01:12.979Z
```

Pour plus d’informations et des démonstrations, consultez le tutoriel vidéo [utilisation des commandes RDE (10:01)](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/developing/rde/how-to-use).


## Déploiement sur un RDE à partir de fournisseurs Git externes {#deploy-to-rde}

>[!NOTE]
>
>Cette fonctionnalité est disponible via le programme Beta. Si vous souhaitez tester cette nouvelle fonctionnalité et partager vos commentaires, envoyez un e-mail à [CloudManager_BYOG@adobe.com](mailto:cloudmanager_byog@adobe.com) à partir de l’adresse e-mail associée à votre Adobe ID. Veillez à inclure la plateforme Git à utiliser et indiquez si vous utilisez une structure de référentiel privée/publique ou d’entreprise.

Cloud Manager prend en charge le déploiement de code vers un RDE directement à partir de fournisseurs Git externes lors de l’utilisation de la configuration [Bring Your Own Git (BYOG)](/help/implementing/cloud-manager/managing-code/external-repositories.md).

Le déploiement des RDE à partir d’un référentiel Git externe nécessite les éléments suivants :

* Utilisation d’un référentiel Git externe intégré à Cloud Manager (configuration BYOG).
* Un ou plusieurs environnements RDE doivent être configurés pour votre projet.
* Si vous utilisez `github.com`, vous devez vérifier et accepter l’installation de l’application GitHub mise à jour pour accorder les nouvelles autorisations requises.

**Notes d’utilisation**

* Le déploiement vers le RDE est actuellement pris en charge uniquement pour le contenu AEM et les packages Dispatcher.
* Le déploiement d’autres types de packages (par exemple, les packages d’application AEM complets) n’est pas encore pris en charge.
* Actuellement, la réinitialisation d’un environnement RDE à l’aide d’un commentaire n’est pas prise en charge. Vous devez plutôt utiliser la commande de réinitialisation de l’interface de ligne de commande AIO existante, comme [décrit ici](/help/implementing/developing/introduction/rapid-development-environments.md#reset-the-rde-command-line).

**Fonctionnement**

1. **Message de validation de la qualité du code.**

   Lorsqu’une requête de tirage (PR) déclenche l’exécution d’un pipeline de qualité du code, les résultats de validation indiquent si le déploiement peut passer à un environnement RDE.

   Aspect sur GitHub Enterprise :
   ![Message de validation de la qualité du code sur GitHub Enterprise](/help/implementing/developing/introduction/assets/rde-gitlab-code-quality-validation-message.png)

   Aspect sur GitLab :
   ![&#x200B; Message de validation de la qualité du code sur GitLab](/help/implementing/developing/introduction/assets/rde-gitlab-code-quality-validation-message.png)

   Comment cela se présente-t-il sur Bitbucket :
   ![&#x200B; Message de validation de la qualité du code sur Bitbucket &#x200B;](/help/implementing/developing/introduction/assets/rde-bitbucket-code-quality-validation-message.png)

1. **Déclencher le déploiement à l’aide d’un commentaire.**

   Pour lancer le déploiement, ajoutez un commentaire au PR au format suivant : `deploy on rde-environment-<envName>`

   ![Déclencher le déploiement à l’aide d’un commentaire](/help/implementing/developing/introduction/assets/rde-trigger-deployment-using-comment.png)

   Le `<envName>` doit correspondre au nom d’un environnement RDE existant. Si le nom est introuvable, un commentaire est renvoyé indiquant que l’environnement n’est pas valide.

   Si le statut de l’environnement n’est pas prêt, vous obtenez le commentaire suivant :

   ![Environnement non prêt à être déployé](/help/implementing/developing/introduction/assets/rde-environment-not-ready.png)

1. **Vérification de l’environnement et déploiement des artefacts.**

   Si le RDE est prêt, Cloud Manager publie un nouveau chèque dans le PR.

   Aspect sur GitHub Enterprise :

   ![Statut de l’environnement sur GitHub](/help/implementing/developing/introduction/assets/rde-github-environment-status-is-ready.png)

   Aspect sur GitLab :

   ![Statut de l’environnement sur GitLab](/help/implementing/developing/introduction/assets/rde-gitlab-deployment-1.png)

   Comment cela se présente-t-il sur Bitbucket :

   ![Statut de l’environnement sur Bitbucket](/help/implementing/developing/introduction/assets/rde-bitbucket-deployment-1.png)

1. **Message de déploiement réussi.**

   Une fois le déploiement terminé, Cloud Manager publie un message de réussite résumant les artefacts déployés dans l’environnement cible.

   Aspect sur GitHub Enterprise :

   ![Statut de déploiement de l’environnement sur GitHub](/help/implementing/developing/introduction/assets/rde-github-environment-deployed-artifacts.png)

   Aspect sur GitLab :

   ![Statut de déploiement de l’environnement sur GitLab](/help/implementing/developing/introduction/assets/rde-gitlab-deployment-2.png)

   Comment cela se présente-t-il sur Bitbucket :

   ![&#x200B; Statut de déploiement de l’environnement sur Bitbucket &#x200B;](/help/implementing/developing/introduction/assets/rde-bitbucket-deployment-2.png)




## Journaux {#rde-logging}

Comme pour les autres types d’environnements, les niveaux de journal peuvent être définis en modifiant les configurations OSGi. Toutefois, comme décrit ci-dessus, le modèle de déploiement des RDE implique une ligne de commande plutôt qu’un déploiement Cloud Manager. Consultez la [documentation de journalisation](/help/implementing/developing/introduction/logging.md) pour plus d’informations sur l’affichage, le téléchargement et l’interprétation des journaux.

L’interface de ligne de commande du RDE dispose également de sa propre commande de journal, utilisée pour configurer rapidement les classes et les packages consignés, ainsi que le niveau de journal auquel ils se trouvent. Ces configurations peuvent être considérées comme éphémères, car elles ne modifient pas les propriétés OSGI dans le contrôle de version. Cette fonctionnalité se concentre sur l’affichage des dernières lignes en temps réel, plutôt que sur la recherche de journaux provenant d’un passé lointain.

L’exemple suivant illustre comment suivre le niveau de création, avec un package défini sur un niveau de journalisation de débogage et deux packages (séparés par des espaces) définis sur un niveau de débogage d’informations. La sortie qui comprend un package **auth** est mise en surbrillance.

`aio aem:rde:logs --target=author --debug=org.apache.sling --info=org.apache.sling.commons.threads.impl org.apache.sling.jcr.resource.internal.helper.jcr -H .auth.`

>[!TIP]
>
>Si le `RDECLI:UNEXPECTED_API_ERROR` d’erreur s’affiche lors de la lecture des commandes de journaux pour le service de création, réinitialisez votre environnement et réessayez. Cette erreur est générée si votre dernière opération de réinitialisation a eu lieu avant la fin du mois de mai 2024.
>
>```
>aio aem:rde:reset
>```

Voir `aio aem:rde:logs --help` pour l’ensemble des options de ligne de commande.

Les fonctionnalités incluent les éléments suivants :

* Déclarer des niveaux de journal par niveau de package ou de classe
* Personnaliser le format de sortie du journal
* jusqu’à quatre configurations de journal actuelles, chacune dans son propre terminal
* mise en surbrillance de journaux spécifiques

Notez que les journaux sont stockés en mémoire sur le RDE et que ces journaux sont recyclés et donc ignorés s’ils ne sont pas en échec ou si le réseau est trop lent.


## Réinitialiser le RDE {#reset-rde}

La réinitialisation du RDE supprime tout le code personnalisé, les configurations et le contenu des instances de création et de publication. La réinitialisation du RDE s’avère utile lorsque vous avez terminé de tester une fonctionnalité et que vous souhaitez rétablir l’environnement à son état par défaut avant de tester une autre.

Une réinitialisation définit le RDE sur la dernière version d’AEM disponible.

Vous pouvez réinitialiser le RDE à l’aide de [Cloud Manager](#reset-the-rde-cloud-manager) ou de la [ligne de commande](#reset-the-rde-command-line). La réinitialisation prend quelques minutes et tout le contenu et le code existants sont supprimés du RDE.

>[!NOTE]
>
>Assurez-vous que le rôle de développeur Cloud Manager vous est attribué avant d’utiliser la fonction de réinitialisation. Dans le cas contraire, l’action de réinitialisation échoue avec une erreur.

### Réinitialisez le RDE à l’aide de la ligne de commande {#reset-the-rde-command-line}

Vous pouvez réinitialiser le RDE et le rétablir à son état par défaut en exécutant les opérations suivantes :

`aio aem:rde:reset`

Ce processus prend généralement quelques minutes et signale les ```Environment reset.``` en cas de réussite ou de ```Failed to reset the environment.``` d’erreurs. Pour une sortie structurée, consultez le chapitre sur ```--json``` sortie ci-dessous.

Utilisez la commande [status](#checking-rde-status) pour vérifier quand l’environnement est à nouveau prêt.

### Réinitialiser le RDE dans Cloud Manager {#reset-the-rde-cloud-manager}

Vous pouvez utiliser Cloud Manager pour réinitialiser votre RDE en procédant comme suit :

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Cliquez sur le programme pour lequel vous souhaitez réinitialiser le RDE.

1. Dans la page **Aperçu**, cliquez sur l’onglet **Environnements** dans la partie supérieure de l’écran.

   ![Onglet Environnements](/help/implementing/cloud-manager/assets/environments-tab2.png)

   * Vous pouvez également cliquer sur le bouton **Tout afficher** dans la vignette **Environnements** pour accéder directement à l’onglet **Environnements**.

     ![Option Tout afficher](/help/implementing/cloud-manager/assets/environment-showall.png)

1. La fenêtre **Environnements** s’affiche et répertorie tous les environnements du programme.

   ![Onglet Environnements.](/help/implementing/cloud-manager/assets/environments-tab-populated.png)

1. Cliquez sur le bouton représentant des points de suspension du RDE à réinitialiser, puis sélectionnez **Réinitialiser**.

   ![Affichage des détails de l’environnement.](/help/implementing/cloud-manager/assets/rde-reset.png)

1. Confirmez votre choix en cliquant sur **Réinitialiser** dans la boîte de dialogue.

   ![Confirmer la réinitialisation](/help/implementing/cloud-manager/assets/rde-reset-confirm.png)

1. Cloud Manager confirme par une notification de bannière que le processus de réinitialisation a démarré.

   ![Notification sous forme de bannière confirmant la réinitialisation](/help/implementing/cloud-manager/assets/rde-reset-banner.png)

Une fois la réinitialisation du RDE lancée, quelques minutes sont généralement nécessaires pour terminer et restaurer l’environnement à son état par défaut. Vous pouvez consulter le statut de réinitialisation à tout moment dans la colonne **Statut** de la vignette ou de la fenêtre **Environnements**.

![Statut de la réinitialisation du RDE](/help/implementing/cloud-manager/assets/rde-reset-status-environments-card.png)

Vous pouvez également réinitialiser le RDE à l’aide du bouton représentant des points de suspension directement à partir de la vignette **Environnements** de la page **Aperçu**.

![Réinitialiser le RDE à partir de la vignette Environnements](/help/implementing/cloud-manager/assets/rde-reset-environments-card.png)

Pour plus d’informations sur la gestion de vos environnements à l’aide de Cloud Manager, consultez [la documentation de Cloud Manager](/help/implementing/cloud-manager/manage-environments.md).

## Commandes qui prennent en charge la sortie JSON {#json-commands}

La plupart des commandes prennent en charge l’indicateur de ```--json``` global qui supprime la sortie de console et renvoie un fichier json valide à traiter dans les scripts. Vous trouverez ci-dessous quelques commandes prises en charge, avec des exemples de sortie json.

### Statut {#status}

<details>
  <summary>Développer pour voir des exemples de statut</summary>

#### Un RDE épuré {#clean-rde}

```$ aio aem rde status --json```

```json
{
  "programId": "myProgram",
  "environmentId": "myEnv",
  "status": "Modification in progress | Deployment in progress | Upload in progress | Ready (instances are currently deploying) | Ready",
  "author": {
    "osgiBundles": [],
    "osgiConfigs": []
  },
  "publish": {
    "osgiBundles": [],
    "osgiConfigs": []
  }
}
```

#### Un RDE avec des lots installés {#rde-installed-bundles}

```$ aio aem rde status --json```

```json
{
  "programId": "myProgram",
  "environmentId": "myEnv",
  "status": "Ready",
  "author": {
    "osgiBundles": [
      {
        "id": "author_osgi-bundle_com.adobe.granite.hotdev.demo",
        "updateId": "80",
        "service": "author",
        "type": "osgi-bundle",
        "metadata": {
          "name": "hotdev.demo.ui.apps.all-1.0.0-SNAPSHOT.zip",
          "bundleSymbolicName": "com.adobe.granite.hotdev.demo",
          "bundleName": "HotDev Bundle",
          "bundleVersion": "1.0.0.SNAPSHOT"
        }
      }
    ],
    "osgiConfigs": [
      {
        "id": "publish_osgi-config_com.adobe.granite.demo.MyServlet",
        "updateId": "80",
        "service": "publish",
        "type": "osgi-config",
        "metadata": {
          "name": "hotdev.demo.ui.apps.all-1.0.0-SNAPSHOT.zip",
          "configPid": "com.adobe.granite.demo.MyServlet"
        }
      }
    ]
  },
  "publish": {
    "osgiBundles": [
      {
        "id": "author_osgi-bundle_com.adobe.granite.hotdev.demo",
        "updateId": "80",
        "service": "author",
        "type": "osgi-bundle",
        "metadata": {
          "name": "hotdev.demo.ui.apps.all-1.0.0-SNAPSHOT.zip",
          "bundleSymbolicName": "com.adobe.granite.hotdev.demo",
          "bundleName": "HotDev Bundle",
          "bundleVersion": "1.0.0.SNAPSHOT"
        }
      }
    ],
    "osgiConfigs": [
      {
        "id": "publish_osgi-config_com.adobe.granite.demo.MyServlet",
        "updateId": "80",
        "service": "publish",
        "type": "osgi-config",
        "metadata": {
          "name": "hotdev.demo.ui.apps.all-1.0.0-SNAPSHOT.zip",
          "configPid": "com.adobe.granite.demo.MyServlet"
        }
      }
    ]
  }
}
```

</details>

### Installer {#install}

<details>
  <summary>Développez pour afficher des exemples d’installation.</summary>

```$ aio aem rde install ~/Downloads/hotdev.demo.ui.apps.all-1.0.0-SNAPSHOT.zip --json```

```json
{
  "programId": "myProgram",
  "environmentId": "myEnv",
  "items": [
    {
      "updateId": "4",
      "info": "deploy",
      "action": "deploy",
      "metadata": {
        "name": "hotdev.demo.ui.apps.all-1.0.0-SNAPSHOT.zip"
      },
      "services": [
        "author",
        "publish"
      ],
      "status": "completed",
      "timestamps": {
        "received": "2024-05-21T12:30:44.578Z",
        "processed": "2024-05-21T12:31:07.886468Z"
      },
      "user": "userId",
      "type": "content-package",
      "hash": "2ad73507",
      "logs": [
        "No logs available for this update."
      ]
    }
  ]
}
```

</details>

### Supprimer {#delete}

<details>
  <summary>Développer pour voir les exemples de suppression</summary>

```$ aio aem rde delete com.adobe.granite.hotdev.demo-1.0.0.SNAPSHOT --json```

```json
{
  "programId": "myProgram",
  "environmentId": "myEnv",
  "items": [
    {
      "updateId": "84",
      "info": "delete author_osgi-bundle_com.adobe.granite.hotdev.demo",
      "action": "delete",
      "metadata": {},
      "services": [
        "author"
      ],
      "status": "completed",
      "timestamps": {
        "received": "2024-05-21T11:49:16.889Z",
        "processed": "2024-05-21T11:49:18.188420Z"
      },
      "user": "userId",
      "type": "osgi-bundle",
      "deletedArtifact": {
        "id": "author_osgi-bundle_com.adobe.granite.hotdev.demo",
        "metadata": {
          "name": "hotdev.demo.ui.apps.all-1.0.0-SNAPSHOT.zip",
          "bundleSymbolicName": "com.adobe.granite.hotdev.demo",
          "bundleName": "HotDev Bundle",
          "bundleVersion": "1.0.0.SNAPSHOT"
        },
        "service": "author",
        "type": "osgi-bundle",
        "updateId": "83"
      },
      "hash": "636f6d2e",
      "logs": [
        "No logs available for this update."
      ]
    },
    {
      "updateId": "85",
      "info": "delete publish_osgi-bundle_com.adobe.granite.hotdev.demo",
      "action": "delete",
      "metadata": {},
      "services": [
        "publish"
      ],
      "status": "completed",
      "timestamps": {
        "received": "2024-05-21T11:49:23.857Z",
        "processed": "2024-05-21T11:49:25.237930Z"
      },
      "user": "userId",
      "type": "osgi-bundle",
      "deletedArtifact": {
        "id": "publish_osgi-bundle_com.adobe.granite.hotdev.demo",
        "metadata": {
          "name": "hotdev.demo.ui.apps.all-1.0.0-SNAPSHOT.zip",
          "bundleSymbolicName": "com.adobe.granite.hotdev.demo",
          "bundleName": "HotDev Bundle",
          "bundleVersion": "1.0.0.SNAPSHOT"
        },
        "service": "publish",
        "type": "osgi-bundle",
        "updateId": "83"
      },
      "hash": "636f6d2e",
      "logs": [
        "No logs available for this update."
      ]
    }
  ]
}
```

</details>

### Historique {#history}

<details>
  <summary>Développer pour voir les exemples d’historique</summary>

```$ aio aem rde history --json```

```json
{
  "programId": "myProgram",
  "environmentId": "myEnv",
  "status": "Ready",
  "items": [
    {
      "updateId": "112",
      "info": "delete publish_osgi-bundle_com.adobe.granite.hotdev.demo",
      "action": "delete",
      "metadata": {},
      "services": [
        "publish"
      ],
      "status": "completed",
      "timestamps": {
        "received": "2024-05-21T12:53:07.934Z",
        "processed": "2024-05-21T12:53:09.118766Z"
      },
      "user": "userId",
      "type": "osgi-bundle",
      "deletedArtifact": {
        "id": "publish_osgi-bundle_com.adobe.granite.hotdev.demo",
        "metadata": {
          "name": "hotdev.demo.ui.apps.all-1.0.0-SNAPSHOT.zip",
          "bundleSymbolicName": "com.adobe.granite.hotdev.demo",
          "bundleName": "HotDev Bundle",
          "bundleVersion": "1.0.0.SNAPSHOT"
        },
        "service": "publish",
        "type": "osgi-bundle",
        "updateId": "110"
      },
      "hash": "636f6d2e"
    },
    {
      "updateId": "111",
      "info": "delete author_osgi-bundle_com.adobe.granite.hotdev.demo",
      "action": "delete",
      "metadata": {},
      "services": [
        "author"
      ],
      "status": "completed",
      "timestamps": {
        "received": "2024-05-21T12:53:00.824Z",
        "processed": "2024-05-21T12:53:02.101560Z"
      },
      "user": "userId",
      "type": "osgi-bundle",
      "deletedArtifact": {
        "id": "author_osgi-bundle_com.adobe.granite.hotdev.demo",
        "metadata": {
          "name": "hotdev.demo.ui.apps.all-1.0.0-SNAPSHOT.zip",
          "bundleSymbolicName": "com.adobe.granite.hotdev.demo",
          "bundleName": "HotDev Bundle",
          "bundleVersion": "1.0.0.SNAPSHOT"
        },
        "service": "author",
        "type": "osgi-bundle",
        "updateId": "110"
      },
      "hash": "636f6d2e"
    },
    {
      "updateId": "110",
      "info": "deploy",
      "action": "deploy",
      "metadata": {
        "name": "hotdev.demo.ui.apps.all-1.0.0-SNAPSHOT.zip"
      },
      "services": [
        "author",
        "publish"
      ],
      "status": "completed",
      "timestamps": {
        "received": "2024-05-21T12:52:12.123Z",
        "processed": "2024-05-21T12:52:31.026147Z"
      },
      "user": "userId",
      "type": "content-package",
      "hash": "2ad73507"
    }
  ]
}
```

</details>

### Réinitialiser {#reset}

<details>
  <summary>Développez pour voir les exemples Réinitialiser .</summary>

#### Au feu et à l&#39;oubli, sans attendre {#fire-no-wait}

```$ aio aem rde reset --no-wait --json```

```json
{
  "programId": "myProgram",
  "environmentId": "myEnv",
  "status": "resetting"
}
```

#### Attendez la fin de l’opération. La réinitialisation a réussi. {#wait-success}

```$ aio aem rde reset --json```

```json
{
  "programId": "myProgram",
  "environmentId": "myEnv",
  "status": "reset"
}
```

#### Attente de fin, échec de la réinitialisation {#wait-failed}

```$ aio aem rde reset --json```

```json
{
  "programId": "myProgram",
  "environmentId": "myEnv",
  "status": "reset_failed"
}
```

</details>

### Redémarrer {#restart}

<details>
  <summary>Développer pour voir des exemples de redémarrage</summary>

```$ aio aem rde restart --json```

```json
{
  "programId": "myProgram",
  "environmentId": "myEnv",
  "status": "restarted"
}
```

</details>

## Modes d’exécution {#runmodes}

La configuration OSGI spécifique au RDE peut être appliquée en utilisant des suffixes sur le nom du dossier, comme dans les exemples ci-dessous :

* `config.rde`
* `config.author.rde`
* `config.publish.rde`

Consultez la [documentation sur le mode d’exécution](/help/implementing/deploying/overview.md#runmodes) pour obtenir des informations générales sur les modes d’exécution.

>[!NOTE]
>
>La configuration OSGi du RDE est unique dans la mesure où elle hérite des valeurs de toutes les propriétés OSGi déclarées par le mode d’exécution `dev` du bundle.

Les RDE sont différents des autres environnements dans lesquels le contenu peut être installé dans un dossier `install.rde` (ou `install.author.rde` ou `install.publish.rde`) sous `/apps`. Cette fonctionnalité vous permet de valider le contenu sur Git et de le diffuser dans le RDE à l’aide de l’outil de ligne de commande.

## Renseigner avec du contenu {#populating-content}

Lorsqu’un RDE est réinitialisé, tout le contenu est supprimé. Par conséquent, si vous le souhaitez, une action explicite doit être entreprise pour ajouter du contenu. Une bonne pratique consiste à assembler un ensemble de contenu à utiliser comme contenu de test pour valider ou déboguer des fonctionnalités dans le RDE. Il existe plusieurs stratégies possibles pour renseigner le RDE avec ce contenu :

1. Synchronisez explicitement le package de contenu avec le RDE à l’aide de l’outil de ligne de commande

1. Placez et validez l’exemple de contenu dans git dans un dossier `install.rde` sous `/apps`, puis synchronisez le package de contenu global avec le RDE à l’aide de l’outil de ligne de commande.

1. Utilisez l’[outil de copie de contenu](/help/implementing/developing/tools/content-copy.md) pour copier un jeu de contenu défini à partir d’environnements de production, d’évaluation ou de développement, ou encore d’un autre RDE.

1. Utiliser le gestionnaire de modules

La taille maximale autorisée est de 1 Go lors de la synchronisation de packages de contenu.


## En quoi les RDE diffèrent-ils des environnements de développement cloud ? {#how-are-rds-different-from-cloud-development-environments}

Bien que le RDE soit à de nombreux égards similaire à un environnement de développement cloud, il existe quelques différences architecturales mineures pour permettre une synchronisation rapide du code. Le mécanisme de transfert du code vers le RDE est différent : pour les RDE, le code est synchronisé à partir d’un environnement de développement local, tandis que pour les environnements de développement cloud, le code est déployé au moyen de Cloud Manager.

Pour ces raisons, il est recommandé, après la validation du code dans un environnement RDE, de déployer le code dans un environnement de développement cloud à l’aide du pipeline hors production. La dernière étape consiste à tester le code avant de le déployer avec le pipeline de production.

Notez également les points suivants :

* Les RDE n’incluent pas de niveau d’aperçu
* Les RDE ne prennent actuellement pas en charge le canal de version préliminaire.


## De combien de RDE ai-je besoin ? {#how-many-rds-do-i-need}

Un RDE est disponible pour chaque solution sous licence et Adobe propose également des RDE supplémentaires pouvant être mis sous licence pour les programmes de production (hors sandbox).

Le nombre de RDE requis dépend de la composition et des processus d’une organisation. Le modèle le plus flexible est celui où une entreprise achète un RDE dédié pour chacun de ses développeurs et développeuses AEM Cloud Service. Dans ce modèle, chaque développeur ou développeuse peut tester son code sur le RDE sans se coordonner avec les autres membres de l’équipe pour déterminer si un environnement de RDE est disponible.

À l’opposé, une équipe ne disposant que d’un seul RDE peut s’appuyer sur une coordination interne pour décider quel développeur utilise l’environnement à un moment donné. Cette approche fonctionne bien lorsqu’un développeur ou une développeuse atteint un jalon de fonctionnalité et doit valider son travail dans un environnement cloud avec la possibilité d’apporter des modifications rapides.

Un modèle intermédiaire est un modèle où une organisation achète plusieurs RDE, de sorte qu’il y a une plus grande probabilité qu’un RDE inutilisé soit disponible. Une stratégie pourrait consister à allouer un RDE par équipe Scrum ou fonction majeure. Des processus internes peuvent être utilisés pour coordonner l’utilisation des environnements.

## En quoi un RDE d’AEM Forms Cloud Service est-il différent des autres environnements ? {#how-are-forms-rds-different-from-cloud-development-environments}

Les développeurs Forms peuvent utiliser l’environnement de développement rapide AEM Forms Cloud Service pour développer rapidement des Forms adaptatifs, des workflows et des personnalisations telles que la personnalisation des composants principaux, les intégrations à des systèmes tiers, etc. L’environnement de développement rapide (RDE) d’AEM Forms Cloud Service ne prend pas en charge les API de communication. Il ne prend pas non plus en charge les fonctionnalités qui nécessitent un document d’enregistrement, comme la génération d’un document d’enregistrement lors de l’envoi d’un formulaire adaptatif. Les fonctionnalités d’AEM Forms répertoriées ci-dessous ne sont pas disponibles dans un environnement de développement rapide (RDE) :

* Configuration d’un document d’enregistrement pour un formulaire adaptatif
* Génération d’un document d’enregistrement lors de l’envoi d’un formulaire adaptatif ou avec une étape de workflow
* Envoyer un document d’enregistrement en tant que pièce jointe avec l’action Envoyer par e-mail ou l’étape E-mail dans un workflow
* Utilisation d’Adobe Sign dans un formulaire adaptatif ou dans une étape de workflow
* API de communication

>[!NOTE]
>
> Il n’existe aucune différence entre l’interface utilisateur de l’environnement de développement rapide (RDE) et d’autres environnements Cloud Service pour Forms. Toutes les options liées au document d’enregistrement, comme la sélection d’un modèle de document d’enregistrement pour un formulaire adaptatif, apparaissent toujours dans l’interface utilisateur. Ces environnements ne disposent d’aucune API de communication ni de fonctionnalités de document d’enregistrement pour tester ces options. Ainsi, si vous choisissez une option qui nécessite des fonctionnalités d’API de communication ou de document d’enregistrement, le système n’effectue pas l’action. Un message d’erreur s’affiche à la place.

## Tutoriel sur le RDE

Pour en savoir plus sur le RDE dans AEM as a Cloud Service, consultez le tutoriel vidéo qui explique [comment le configurer et l’utiliser, ainsi que le cycle de vie du développement (01:25)](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/cloud-service/developing/rde/overview).

## Résolution des problèmes {#troubleshooting}

### Résolution des problèmes liés au RDE (#rde-troublehooting)

#### Comment obtenir la dernière version d’AEM pour un RDE existant {#get-latest-aem-version}

Lors de leur création, les RDE sont définis sur la dernière version de Adobe Experience Manager (AEM) disponible. Une [réinitialisation du RDE](#reset-rde), qui peut être effectuée à l’aide de Cloud Manager ou de la commande `aio aem:rde:reset`, enchaîne le RDE et le définit sur la dernière version d’AEM disponible.

### Dépannage du plug-in RDE aio {#aio-rde-plugin-troubleshooting}

#### Erreurs concernant les autorisations insuffisantes {#insufficient-permissions}

Pour utiliser le plug-in RDE, vous devez être membre du profil de produit Cloud Manager **Développeur - Cloud Service**. Voir [&#x200B; Affecter des membres de l’équipe à des profils de produit Cloud Manager - Attribuer le profil de produit Développeur &#x200B;](/help/journey-onboarding/assign-profiles-cloud-manager.md#assign-developer) pour plus d’informations.

Vous pouvez également vérifier que vous disposez de ce rôle de développeur si vous vous connectez à Developer Console à l’aide de la commande suivante :

`aio cloudmanager:environment:open-developer-console`

>[!TIP]
>
>Si l’erreur `Warning: cloudmanager:* is not a aio command.` s’affiche, vous devez installer le [aio-cli-plugin-cloudmanager](https://github.com/adobe/aio-cli-plugin-cloudmanager) en exécutant la commande suivante :
>
>```
>aio plugins:install @adobe/aio-cli-plugin-cloudmanager
>```

Vérifiez que la connexion a bien été établie en exécutant les opérations suivantes :

`aio cloudmanager:list-programs`

Ce processus répertorie tous les programmes de votre organisation configurée et confirme que le rôle approprié vous a été attribué.

#### Utiliser des `aio-cli-plugin-cloudmanager` de contexte obsolètes {#aio-rde-plugin-troubleshooting-deprecatedcontext}

En raison de l’historique du `aio-cli-plugin-aem-rde`, le nom de contexte `aio-cli-plugin-cloudmanager` a été utilisé pendant un certain temps. Le plug-in RDE utilise désormais la méthode IMS pour gérer les informations contextuelles, ce qui vous permet de stocker le contexte globalement ou localement. Vous pouvez également configurer un contexte par défaut à appliquer automatiquement à tous les appels AIO. Le contexte par défaut configuré est stocké localement et permet aux développeurs de suivre et d’utiliser des contextes individuels et leurs informations dans un dossier. Pour plus d’informations, lisez [l’exemple de configuration d’un contexte local](/help/implementing/developing/introduction/rapid-development-environments.md#installing-the-rde-command-line-tools) ci-dessus.

Les développeurs et développeuses qui utilisent les deux plug-ins, le `aio-cli-plugin-cloudmanager` et le `aio-cli-plugin-aem-rde`, et qui souhaitent conserver toutes les informations dans le même contexte ont deux options à leur disposition :

##### Continuer à utiliser les `aio-cli-plugin-cloudmanager` contextuelles

Le contexte peut toujours être utilisé. Un avertissement d’obsolescence s’affiche dans le plug-in du RDE. Cet avertissement peut être ignoré en utilisant le mode ```--quiet```. Les versions plus récentes du plug-in RDE n’offrent plus la possibilité de lire le `aio-cli-plugin-cloudmanager` contextuel. Pour continuer à l’utiliser, configurez simplement le contexte par défaut sur `aio-cli-plugin-cloudmanager`. Voir [l’exemple de configuration d’un contexte local](/help/implementing/developing/introduction/rapid-development-environments.md#installing-the-rde-command-line-tools) ci-dessus.

##### Utilisez un autre nom de contexte pour le module externe Cloud Manager

Les plug-ins Cloud Manager proposent un paramètre permettant de définir un contexte à utiliser. Il ne prend pas encore en charge la configuration du contexte par défaut IMS. Pour ce faire, configurez le plug-in RDE à l’aide de [l’exemple pour configurer un contexte local](/help/implementing/developing/introduction/rapid-development-environments.md#installing-the-rde-command-line-tools) et indiquez au plug-in Cloud Manager d’utiliser des `myContext` comme ```--imsContextName=myContext``` dans chaque appel à celui-ci.
