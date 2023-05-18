---
title: Environnements de développement rapide
description: Découvrez comment tirer parti des environnements de développement rapide pour réaliser des itérations de développement rapides sur un environnement cloud.
exl-id: 1e9824f2-d28a-46de-b7b3-9fe2789d9c68
source-git-commit: 5bfa5a1df940b8903acd08f4c3cb7443adb897d8
workflow-type: tm+mt
source-wordcount: '3325'
ht-degree: 97%

---

# Environnements de développement rapide {#rapid-development-environments}

Afin de déployer les modifications, les environnements de développement cloud actuels nécessitent l’utilisation d’un processus qui utilise des règles de sécurité et de qualité du code, appelé pipeline CI/CD. Dans les cas où des modifications rapides et itératives sont nécessaires, Adobe a introduit des environnements de développement rapide (RDE).

Les RDE permettent aux développeurs de déployer et d’examiner rapidement les modifications, afin de réduire la durée des tests des fonctionnalités éprouvées dans un environnement de développement local.

Une fois les modifications testées dans un RDE, elles peuvent être déployées dans un environnement de développement cloud standard via le pipeline Cloud Manager.

>[!VIDEO](https://video.tv.adobe.com/v/3415582/?quality=12&learn=on)


Vous pouvez visionner d’autres vidéos présentant [comment le configurer](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/developing/rde/how-to-setup.html), [comment l’utiliser](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/developing/rde/how-to-use.html), et montrant le [cycle de vie du développement](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/developing/rde/development-life-cycle.html) à l’aide du RDE.

## Présentation {#introduction}

Les RDE peuvent être utilisés pour les configurations de code, de contenu et Apache ou Dispatcher. Contrairement aux environnements de développement cloud standard, les développeurs peuvent utiliser des outils de ligne de commande locaux pour synchroniser le code créé localement avec un RDE.

Chaque programme est configuré avec un RDE. Notez que les comptes sandbox seront mis en veille après quelques heures d’inactivité.

Lors de la création, les RDE sont définis sur la dernière version d’AEM disponible. Une réinitialisation du RDE, qui peut être effectuée à l’aide de Cloud Manager, enchaîne le RDE et le définit sur la dernière version d’AEM disponible.

En règle générale, un RDE est utilisé par un seul développeur à la fois, à des fins de test et de débogage d’une fonctionnalité spécifique. Une fois la session de développement terminée, le RDE peut être réinitialisé à son état par défaut pour une utilisation ultérieure.

D’autres RDE peuvent être mis sous licence pour des programmes de production (hors sandbox).

## Activation du RDE dans un programme {#enabling-rde-in-a-program}

Pour créer un RDE pour votre programme à l’aide de Cloud Manager, procédez comme suit.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Cliquez sur le programme pour lequel vous souhaitez ajouter un RDE afin d’afficher ses détails.

   * Les RDE peuvent être ajoutés aux [programmes sandbox](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md) et aux [programmes de production.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-production-programs.md)

1. Dans la page **Aperçu du programme**, cliquez sur **Ajouter un environnement** dans la carte **Environnements** pour ajouter un environnement.

   ![Carte Environnements](/help/implementing/cloud-manager/assets/no-environments.png)

   * L’option **Ajouter un environnement** est également disponible dans l’onglet **Environnements**.

      ![Onglet Environnements](/help/implementing/cloud-manager/assets/environments-tab.png)

   * L’option **Ajouter un environnement** peut être désactivée en raison d’un niveau d’autorisation insuffisant ou de ressources sous licence.

1. Dans la boîte de dialogue **Ajouter un environnement** qui s’affiche :

   * Sélectionnez **Développement rapide** sous l’en-tête **Sélectionner le type d’environnement**.
      * Le nombre d’environnements disponibles/utilisés est indiqué entre parenthèses derrière le type d’environnement.
   * Attribuez un **Nom** à l’environnement.
   * Ajoutez une **Description** de l’environnement (facultatif).
   * Sélectionnez une **Région Cloud**.

   ![Boîte de dialogue Ajouter un environnement](/help/implementing/cloud-manager/assets/add-environment-wizard.png)

1. Cliquez sur **Enregistrer** pour ajouter l’environnement spécifié.

L’écran **Aperçu** affiche désormais votre nouvel environnement dans la carte **Environnements**.

Lors de la création, les RDE sont définis sur la dernière version d’AEM disponible. Une réinitialisation du RDE, qui peut également être effectuée à l’aide de Cloud Manager, enchaîne le RDE et le définit sur la dernière version d’AEM disponible.

Pour plus d’informations sur l’utilisation de Cloud Manager pour créer des environnements, gérer leur accès et attribuer des domaines personnalisés, consultez [la documentation de Cloud Manager.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md)

## Installation des outils de ligne de commande RDE {#installing-the-rde-command-line-tools}

Une fois que vous avez ajouté un RDE pour votre programme à l’aide de Cloud Manager, vous pouvez interagir avec celui-ci en configurant les outils de ligne de commande comme indiqué ci-dessous :

>[!IMPORTANT]
>
>Assurez-vous que vous disposez des dernières versions de [Node et de NPM](https://nodejs.org/en/download/) pour que l’interface de ligne de commande d’Adobe I/O et les modules externes connexes fonctionnent correctement.


1. Installez les outils de l’interface de ligne de commande Adobe I/O en suivant la procédure décrite [ici](https://developer.adobe.com/runtime/docs/guides/tools/cli_install/).
1. Installez le plug-in Cloud Manager pour les outils de l’interface de ligne de commande Adobe I/O et configurez-le comme décrit [ici](https://github.com/adobe/aio-cli-plugin-cloudmanager).
1. Installez le plug-in AEM pour les outils de l’interface de ligne de commande Adobe I/O du RDE en exécutant les commandes suivantes :

   ```
   aio plugins:install @adobe/aio-cli-plugin-aem-rde
   aio plugins:update
   ```

1. Configurez le plug-in Cloud Manager pour votre ID d’organisation comme suit :

   `aio config:set cloudmanager_orgid 4E03EQC05D34GL1A0B49421C@AdobeOrg`

   et remplacez la chaîne alphanumérique par votre propre ID d’organisation. Vous le trouverez à l’aide de la stratégie décrite [ici](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=fr#concept_EA8AEE5B02CF46ACBDAD6A8508646255).

1. Configurez ensuite votre ID de programme :

   `aio config:set cloudmanager_programid 12345`

1. L’étape suivante consiste à configurer l’ID d’environnement auquel le RDE va être associé :

   `aio config:set cloudmanager_environmentid 123456`

1. Une fois la configuration du plug-in terminée, connectez-vous à l’aide de la commande suivante :

   `aio login`

   La réponse lors d’une connexion réussie doit ressembler à la sortie ci-dessous, mais vous pouvez ignorer les valeurs affichées.

   ```
   ...
   You are currently in:
   1. Org: <no org selected>
   2. Project: <no project selected>
   3. Workspace: <no workspace selected>
   ```

   Notez que cette étape nécessite que vous soyez membre de Cloud Manager **Développeur - Cloud Service** Profil du produit. Consultez [cette page](/help/journey-onboarding/assign-profiles-cloud-manager.md#assign-developer) pour plus de détails.

   Vous pouvez également vérifier que vous disposez de ce rôle de développeur si vous pouvez vous connecter à Developer Console à l’aide de la commande suivante :

   `aio cloudmanager:environment:open-developer-console`

   >[!TIP]
   >
   >Si vous rencontrez l’erreur `Warning: cloudmanager:list-programs is not a aio command.`, vous devez installer [aio-cli-plugin-cloudmanager](https://github.com/adobe/aio-cli-plugin-cloudmanager) en exécutant la commande ci-dessous :
   >
   >
   ```
   >aio plugins:install @adobe/aio-cli-plugin-cloudmanager
   >```

1. Vérifiez la réussite de la connexion en exécutant

   `aio cloudmanager:list-programs`

   Cette opération affiche la liste de tous les programmes de votre organisation configurée.


Pour plus d’informations et des démonstrations, consultez le tutoriel vidéo [configuration d’un RDE](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/developing/rde/how-to-setup.html).

## Utilisation du RDE lors du développement d’une nouvelle fonctionnalité {#using-rde-while-developing-a-new-feature}

Pour développer une nouvelle fonctionnalité, Adobe recommande le workflow suivant :

* Lorsqu’un jalon intermédiaire est atteint et validé localement avec le SDK AEM as a Cloud Service, le code doit être validé dans une branche de fonctionnalité Git qui ne fait pas encore partie de la ligne principale, bien que la validation de ce dernier soit facultative. Ce qui constitue un « jalon intermédiaire » varie en fonction des habitudes de l’équipe. Par exemple, quelques nouvelles lignes de code, une demi-journée de travail ou l’achèvement d’une sous-fonctionnalité.

* Réinitialisez le RDE s’il a été utilisé par une autre fonctionnalité et si vous souhaitez le [réinitialiser à un état par défaut](#reset-rde). <!-- Alexandru: hiding for now, please don't delete This can be done via [Cloud Manager](#reset-the-rde-cloud-manager) or via the [command line](#reset-the-rde-command-line). -->La réinitialisation prend quelques minutes et supprime tout le contenu et le code existants. Vous pouvez utiliser la commande de statut RDE pour confirmer que le RDE est prêt. Le RDE reviendra avec la version la plus récente d’AEM.

   >[!IMPORTANT]
   >
   > Si vos environnements d’évaluation et de production ne reçoivent pas les actualisations de mise à jour d’AEM automatique et sont très en retard par rapport à la version d’AEM la plus récente, gardez à l’esprit que le code qui s’exécute sur le RDE peut ne pas correspondre à la façon dont le code fonctionnera sur l’évaluation et la production. Dans ce cas, il est particulièrement important d’effectuer des tests approfondis du code lors de l’évaluation avant de le déployer en production.


* À l’aide de l’interface de ligne de commande RDE, synchronisez le code local avec le RDE. Les options incluent l’installation d’un package de contenu, d’une offre groupée spécifique, d’un fichier de configuration OSGI, d’un fichier de contenu et d’un fichier zip d’une configuration Apache/Dispatcher. Il est également possible de référencer un package de contenu distant. Consultez la section [Outils de ligne de commande RDE](#rde-cli-commands) pour plus d’informations. Vous pouvez utiliser la commande Statut pour vérifier que le déploiement a réussi. Vous pouvez éventuellement utiliser le gestionnaire de modules pour installer des packages de contenu.

* Testez le code dans l’outil RDE. Les URL de création et de publication sont disponibles dans Cloud Manager.

* Si le code ne se comporte pas comme prévu, utilisez des techniques de débogage standard pour comprendre le problème et effectuez les modifications nécessaires. Sans valider les modifications du code dans Git (puisqu’elles n’ont pas été validées), utilisez l’interface de ligne de commande locale pour synchroniser le code avec l’outil RDE. Continuez ainsi jusqu’à ce que le problème soit résolu.

* Une fois que le code se comporte comme prévu, validez le code sur la branche de la fonctionnalité Git.

* Le code synchronisé avec l’outil RDE n’utilise pas de pipeline Cloud Manager. Vous devez donc maintenant utiliser un pipeline Cloud Manager hors production pour déployer la branche de fonctionnalité Git dans l’environnement de développement cloud. Cela permet de confirmer que le code passe les points de contrôle qualité de Cloud Manager et vous permet d’être sûr que le code sera déployé ultérieurement à l’aide du pipeline de production Cloud Manager.

* Répétez les étapes ci-dessus pour chaque jalon intermédiaire jusqu’à ce que tout le code de la fonctionnalité soit prêt et s’exécute correctement dans l’environnement de l’outil RDE et l’environnement de développement cloud.

* Déployez le code en production via le pipeline de production Cloud Manager.

## Utilisation de l’outil RDE pour déboguer une fonctionnalité existante {#use-rde-to-debug-an-existing-feature}

Le workflow est similaire au développement d’une nouvelle fonctionnalité. La différence est que le code synchronisé avec l’outil RDE reflète le libellé Git avec tout ce qui a été envoyé à l’environnement où le problème a été détecté. En outre, il peut s’avérer utile de déployer du contenu correspondant à l’environnement en amont. Pour ce faire, vous pouvez exporter et importer des packages de contenu.

## Collaboration de plusieurs développeurs sur le même outil RDE {#multiple-developers-collaborating-on-the-same-rde}

Un outil RDE prend en charge un seul projet à la fois. Comme le code est synchronisé entre un environnement de développement local et l’environnement du RDE, il est plus naturel pour un développeur de l’utiliser seul à un moment donné.

Cependant, avec une coordination étroite, il est possible pour plusieurs développeurs de valider une fonctionnalité spécifique ou de déboguer un problème spécifique. La solution est que chaque développeur conserve ses projets locaux synchronisés de sorte que les modifications de code effectuées par un développeur particulier soient absorbées par les autres développeurs, sinon un développeur risque de remplacer par inadvertance le code de l’autre. La stratégie recommandée est que chaque développeur valide ses modifications dans une branche Git partagée avant la synchronisation avec l’outil RDE, de sorte que les autres développeurs extraient les modifications avant d’apporter les leurs.

## Commandes des outils de ligne de commande de l’outil RDE {#rde-cli-commands}

### Aide/Informations générales {#help}

* Pour obtenir une liste des commandes, saisissez :

   `aio aem:rde`

* Pour obtenir une aide détaillée sur une commande, saisissez :

   `aio aem rde <command> --help`

### Déploiement sur l’outil RDE {#deploying-to-rde}

Cette section décrit l’utilisation de l’interface de ligne de commande de l’outil RDE pour le déploiement, l’installation ou la mise à jour de lots, de configurations OSGI, de packages de contenu, de fichiers de contenu individuels et de configurations Apache ou Dispatcher.

Le modèle d’utilisation général est le suivant : `aio aem:rde:install <artifact>`.

Vous trouverez quelques exemples ci-dessous :

<u>Déploiement d’un package de contenu</u>

`aio aem:rde:install sample.demo.ui.apps.all-1.0.0-SNAPSHOT.zip`

La réponse pour un déploiement réussi ressemble à ce qui suit :

```
...
#1: deploy completed for content-package sample.demo.ui.apps.all-1.0.0-SNAPSHOT.zip on author,publish - done by 9E072FC75D54FE1A2B49431C@AdobeID at 2022-09-13T11:32:06.229Z
```

Vous pouvez éventuellement référencer un référentiel distant :

`aio aem:rde:install -t content-package "https://repo1.maven.org/maven2/com/adobe/aem/guides/aem-guides-wknd.all/2.1.0/aem-guides-wknd.all-2.1.0.zip"`

Par défaut, les artefacts sont déployés sur les deux niveaux Création et Publication, mais l’indicateur « -s » peut être utilisé pour cibler un niveau spécifique.

Tout module AEM peut être déployé, par exemple des modules comportant du code, du contenu ou un [module conteneur](/help/implementing/developing/introduction/aem-project-content-package-structure.md#container-packages) (également appelé package &quot;all&quot;).

>[!IMPORTANT]
>
>La configuration du Dispatcher pour le projet WKND n’est pas déployée via l’installation du package de contenu ci-dessus. Vous devrez le déployer séparément, en suivant les étapes de « déploiement d’une configuration Apache/Dispatcher ».

<u>Déploiement d’une configuration OSGi</u>

`aio aem:rde:install com.adobe.granite.demo.MyServlet.cfg.json`

où la réponse d’un déploiement réussi ressemble à ce qui suit :

```
...
#2: deploy completed for osgi-config com.adobe.granite.demo.MyServlet.cfg.json on author,publish - done by 9E0725C05D54FE1A0B49431C@AdobeID at 2022-09-13T11:54:36.390Z
```

<u>Déploiement d’un lot</u>

Pour déployer un lot, utilisez :

`aio aem:rde:install ~/.m2/repository/org/apache/felix/org.apache.felix.gogo.jline/1.1.8/org.apache.felix.gogo.jline-1.1.8.jar`

où la réponse d’un déploiement réussi ressemble à ce qui suit :

```
...
#3: deploy staged for osgi-bundle org.apache.felix.gogo.jline-1.1.8.jar on author,publish - done by 9E0725C05D53BE1A0B49431C@AdobeID at 2022-09-14T07:54:28.882Z
```

<u>Déployer un fichier de contenu</u>

Pour déployer un fichier de contenu, saisissez la commande suivante :

`aio aem:rde:install world.txt -p /apps/hello.txt`

où la réponse d’un déploiement réussi ressemble à ce qui suit :

```
..
#4: deploy completed for content-file world.txt on author,publish - done by 9E0729C05C54FE1A0B49431C@AdobeID at 2022-09-14T07:49:30.644Z
```

<u>Déploiement d’une configuration Apache/Dispatcher</u>

Pour ce type de configuration, l’ensemble de la structure de dossiers doit se présenter sous la forme d’un fichier zip.

Dans le module `dispatcher` d’un projet AEM, vous pouvez compresser la configuration du Dispatcher en exécutant la commande maven suivante :

`mvn clean package`

ou à l’aide de la commande de compression ci-dessous à partir du répertoire `src` du module `dispatcher` :

`zip -y -r dispatcher.zip .`

déployez ensuite la configuration à l’aide de la commande suivante :

`aio aem:rde:install target/aem-guides-wknd.dispatcher.cloud-X.X.X-SNAPSHOT.zip`

>[!TIP]
>
>La commande ci-dessus suppose que vous déployez les configurations du Dispatcher du projet [WKND](https://github.com/adobe/aem-guides-wknd). Veillez à remplacer le `X.X.X` avec le numéro de version du projet WKND correspondant ou votre numéro de version spécifique au projet lors du déploiement de la configuration du Dispatcher de votre projet.

>[!NOTE]
>
>RDE prend en charge la configuration Dispatcher &quot;mode flexible&quot;, mais pas &quot;mode hérité&quot;. Voir [documentation du dispatcher](/help/implementing/dispatcher/disp-overview.md#validation-debug) pour plus d’informations sur les deux modes. Vous pouvez également consulter la documentation relative à la [migration vers le mode flexible](/help/implementing/dispatcher/validation-debug.md#migrating), si vous ne l’avez pas déjà fait.

Un déploiement réussi génère une réponse qui ressemble à ce qui suit :

```
..
#5 deploy completed for dispatcher-config dispatcher.zip on author,publish - done by 9E0735C05T54FE1A0B49431C@AdobeID at 2022-10-03T10:26:31.286Z
Logs:
  Cloud manager validator 2.0.49
  2022/10/03 10:26:37 No issues found
  Syntax OK
```

Le code déployé sur le RDE n’entre pas dans le cadre d’un pipeline Cloud Manager et de ses points de contrôle qualité associés. Cependant, il subit une analyse qui signalera les erreurs, comme illustré dans l’exemple de code ci-dessous :

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

L’exemple de code ci-dessus illustre le comportement si un lot ne se résout pas. Ce dernier est alors « En attente » et ne sera installé que si ses exigences (importations manquantes, dans ce cas) sont satisfaites par l’installation d’un autre code.

### Vérification du statut du RDE {#checking-rde-status}

Vous pouvez utiliser l’interface de ligne de commande du RDE pour vérifier si l’environnement est prêt à être déployé et pour consulter les déploiements effectués à l’aide du plug-in du RDE.

En cours :

`aio aem:rde:status`

renvoie :

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

qui renvoie une réponse sous la forme :

`#1: deploy completed for content-package aem-guides-wknd.all-2.1.0.zip on author,publish - done by 029039A55D4DE16A0A494025@AdobeID at 2022-09-12T14:41:55.393Z`

### Suppression du RDE {#deleting-from-rde}

Vous pouvez supprimer des configurations et des lots déployés précédemment sur le RDE via l’outil d’interface de ligne de commande. Utilisez la commande `status` pour obtenir une liste des éléments pouvant être supprimés, qui comprend `bsn` pour les lots et `pid` pour les configurations à référencer dans la commande de suppression.

Par exemple, si `com.adobe.granite.demo.MyServlet.cfg.json` a été installé, la référence `bsn` est juste `com.adobe.granite.demo.MyServlet`, sans le suffixe **cfg.json**.

La suppression des packages ou fichiers de contenu n’est pas prise en charge. Pour les supprimer, le RDE doit être réinitialisé à son état par défaut.

Consultez l’exemple ci-dessous pour plus de détails :

```
aio aem:rde:delete com.adobe.granite.csrf.impl.CSRFFilter
#13: delete completed for osgi-config com.adobe.granite.csrf.impl.CSRFFilter on author - done by karl at 2022-09-12T22:01:01.955Z
#14: delete completed for osgi-config com.adobe.granite.csrf.impl.CSRFFilter on publish - done by karl at 2022-09-12T22:01:12.979Z
```

Pour plus d’informations et des démonstrations, consultez le tutoriel vidéo [Utilisation des commandes RDE](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/developing/rde/how-to-use.html).

## Réinitialiser {#reset-rde}

La réinitialisation du RDE supprime tout le code personnalisé, les configurations et le contenu des instances de création et de publication. Cette opération peut s’avérer utile, par exemple, si le RDE a été utilisé pour tester une fonctionnalité spécifique et que vous souhaitez réinitialiser l’environnement à son état par défaut afin de tester une autre fonctionnalité.

Une réinitialisation définit le RDE sur la version d’AEM la plus récente disponible.

<!-- Alexandru: hiding for now, please don't delete

Resetting can be done via [Cloud Manager](#reset-the-rde-cloud-manager) or via the [command line](#reset-the-rde-command-line). Resetting takes a few minutes and all existing content and code will be deleted from the RDE.

>[NOTE!]
>
>You must be assigned the Cloud Manager Developer role in order to be able to use the reset feature. If not, a reset action will result in an error.

### Reset the RDE via Command Line {#reset-the-rde-command-line}

You can reset the RDE and return it to a default state by running:

`aio aem:rde:reset`

This usually takes a few minutes. Use the [status command](#checking-rde-status) to check when the environment is ready again.

### Reset the RDE in Cloud Manager {#reset-the-rde-cloud-manager} -->

Vous pouvez utiliser Cloud Manager pour réinitialiser votre RDE en procédant comme suit :

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Cliquez sur le programme pour lequel vous souhaitez réinitialiser le RDE.

1. Dans la page **Aperçu**, cliquez sur l’onglet **Environnements** dans la partie supérieure de l’écran.

   ![Onglet Environnements](/help/implementing/cloud-manager/assets/environments-tab2.png)

   * Vous pouvez également cliquer sur le bouton **Tout afficher** dans la carte **Environnements** pour accéder directement à l’onglet **Environnements**.

      ![Option Tout afficher](/help/implementing/cloud-manager/assets/environment-showall.png)

1. La fenêtre **Environnements** s’affiche et répertorie tous les environnements du programme.

   ![Onglet Environnements.](/help/implementing/cloud-manager/assets/environments-tab-populated.png)

1. Cliquez sur le bouton représentant des points de suspension en regard du RDE à réinitialiser, puis sélectionnez **Réinitialiser**.

   ![Affichage des détails de l’environnement.](/help/implementing/cloud-manager/assets/rde-reset.png)

1. Confirmez votre choix en cliquant sur **Réinitialiser** dans la boîte de dialogue.

   ![Confirmer la réinitialisation](/help/implementing/cloud-manager/assets/rde-reset-confirm.png)

1. Cloud Manager affiche une notification sous forme de bannière pour avertir que le processus de réinitialisation a démarré.

   ![Notification sous forme de bannière confirmant la réinitialisation](/help/implementing/cloud-manager/assets/rde-reset-banner.png)

Le processus de réinitialisation du RDE dure généralement quelques minutes avant que l’environnement ne retrouve son état par défaut. Vous pouvez consulter le statut de la réinitialisation à tout moment dans la colonne **Statut** de la vignette **Environnements** ou dans la fenêtre **Environnements**.

![Statut de la réinitialisation du RDE](/help/implementing/cloud-manager/assets/rde-reset-status-environments-card.png)

Vous pouvez également réinitialiser le RDE à l’aide du bouton représentant des points de suspension directement à partir de la vignette **Environnements** de la page **Aperçu**.

![Réinitialiser le RDE à partir de la vignette Environnements](/help/implementing/cloud-manager/assets/rde-reset-environments-card.png)

Pour plus d’informations sur la gestion de vos environnements à l’aide de Cloud Manager, consultez [la documentation de Cloud Manager.](/help/implementing/cloud-manager/manage-environments.md)

## Modes d’exécution {#runmodes}

La configuration OSGi spécifique au RDE peut être appliquée en utilisant des suffixes sur le nom du dossier, tel qu’indiqué dans les exemples suivants :

* `config.rde`
* `config.author.rde`
* `config.publish.rde`

Voir la [documentation sur les modes d’exécution](/help/implementing/deploying/overview.md#runmodes) pour obtenir des informations générales sur les modes d’exécution.

>[!NOTE]
>
>La configuration OSGi du RDE est unique dans la mesure où elle hérite des valeurs de toutes les propriétés OSGi déclarées par le mode d’exécution `dev` du bundle.

Les RDE sont différents des autres environnements dans lesquels le contenu peut être installé dans un dossier install.rde (ou install.author.rde ou install.publish.rde) sous /apps. Cela vous permet de valider le contenu sur git et de le diffuser dans le RDE à l’aide de l’outil de ligne de commande.

## Ajout de contenu {#populating-content}

Lorsqu’un RDE est réinitialisé, tout le contenu est supprimé. Par conséquent, si vous le souhaitez, une action explicite doit être entreprise pour ajouter du contenu. Une bonne pratique consiste à assembler un ensemble de contenu à utiliser comme contenu de test pour valider ou déboguer des fonctionnalités dans le RDE. Il existe plusieurs stratégies possibles pour renseigner le RDE avec ce contenu :

1. Synchronisez explicitement le package de contenu avec le RDE à l’aide de l’outil de ligne de commande

1. Placez et validez l’exemple de contenu dans git dans un dossier install.rde sous /apps, puis synchronisez le package de contenu global avec le RDE à l’aide de l’outil de ligne de commande.

1. Utilisez la variable [outil de copie de contenu](/help/implementing/developing/tools/content-copy.md) pour copier un jeu de contenu défini à partir d’environnements de production, d’évaluation ou de développement ou d’un autre RDE.

1. Utiliser le gestionnaire de modules

Notez la limite de 1 Go lors de la synchronisation de packages de contenu.

## Journalisation {#logging}

Les niveaux de journal peuvent être définis en modifiant les configurations OSGi. Pour plus d’informations, consultez la [documentation](/help/implementing/developing/introduction/logging.md).

## En quoi les RDE diffèrent-ils des environnements de développement cloud ? {#how-are-rds-different-from-cloud-development-environments}

Bien que le RDE et l’environnement de développement cloud partagent de nombreuses similitudes, ils diffèrent légèrement au niveau de leur architecture afin de permettre une synchronisation rapide du code. Le mécanisme de transfert du code vers le RDE est différent : la synchronisation du code s’effectue à partir d’un environnement de développement local pour les RDE et via Cloud Manager pour les environnements de développement cloud.

Pour ces raisons, il est recommandé, après la validation du code dans un environnement RDE, de déployer le code dans un environnement de développement cloud à l’aide du pipeline hors production. La dernière étape consiste à tester le code avant de le déployer avec le pipeline de production.

Notez également les points suivants :

* Les RDE n’incluent pas de niveau d’aperçu
* Les RDE ne prennent actuellement pas en charge l’affichage et le débogage du code frontal déployé à l’aide du pipeline front-end de Cloud Manager.
* Les RDE ne prennent actuellement pas en charge le canal de version préliminaire.


## De combien de RDE ai-je besoin ? {#how-many-rds-do-i-need}

Un RDE est disponible pour chaque solution sous licence et Adobe propose également des RDE supplémentaires pouvant être mis sous licence pour les programmes de production (hors sandbox).

Le nombre de RDE requis dépend de la composition et des processus d’une organisation. Le modèle le plus flexible est celui où une entreprise achète un RDE dédié pour chacun de ses développeurs et développeuses AEM Cloud Service. Dans ce modèle, chaque développeur ou développeuse peut tester son code sur le RDE sans se coordonner avec les autres membres de l’équipe pour déterminer si un environnement de RDE est disponible.

À l’autre extrême, une équipe disposant d’un seul RDE peut utiliser des processus internes pour coordonner les développeurs t les développeuses pouvant utiliser l’environnement à un moment donné. Ceci peut se produire chaque fois qu’un développeur ou une développeuse atteint un jalon de fonctionnalité intermédiaire et est prêt à effectuer une validation dans un environnement Cloud où il ou elle peut rapidement apporter les modifications dont il a besoin.

Un modèle intermédiaire est un modèle où une organisation achète un certain nombre de RDE, de sorte qu’il y a une plus grande probabilité qu’un RDE inutilisé soit disponible. Une stratégie pourrait consister à allouer un RDE par équipe Scrum ou fonction majeure. Des processus internes peuvent être utilisés pour coordonner l’utilisation des environnements.

## En quoi un environnement de développement rapide (RDE) de Cloud Service d’AEM Forms diffère-t-il des autres environnements ? {#how-are-forms-rds-different-from-cloud-development-environments}

Les développeurs et développeuses Forms peuvent utiliser un environnement de développement rapide de Cloud Service d’AEM Forms pour développer rapidement des personnalisations, des workflows et des formulaires adaptatifs tels que la personnalisation des composants principaux, les intégrations à des systèmes tiers, etc. L’environnement de développement rapide (RDE) de Cloud Service d’AEM Forms ne prend pas en charge les API de communication, ainsi que les caractéristiques et fonctionnalités nécessitant un document d’enregistrement, comme la génération d’un document d’enregistrement lors de l’envoi d’un formulaire adaptatif. Les fonctionnalités d’AEM Forms répertoriées ci-dessous ne sont pas disponibles dans un environnement de développement rapide (RDE) :

* Configuration d’un document d’enregistrement pour un formulaire adaptatif
* Génération d’un document d’enregistrement lors de l’envoi d’un formulaire adaptatif ou avec une étape de workflow
* Envoyer un document d’enregistrement en tant que pièce jointe avec l’action Envoyer par e-mail ou l’étape E-mail dans un workflow
* Utilisation d’Adobe Sign dans un formulaire adaptatif ou dans une étape de workflow
* API de communication

>[!NOTE]
>
> Il n’existe aucune différence entre l’interface utilisateur de l’environnement de développement rapide (RDE) et d’autres environnements Cloud Service pour Forms. Toutes les options liées au document d’enregistrement, comme la sélection d’un modèle de document d’enregistrement pour un formulaire adaptatif, apparaissent toujours dans l’interface utilisateur. Ces environnements ne disposent d’aucune API de communication ni de fonctionnalités de document d’enregistrement pour tester ces options. Ainsi, lorsque vous choisissez une option nécessitant des fonctionnalités d’API de communication ou de document d’enregistrement, aucune action n’est effectuée et un message d’erreur s’affiche ou est renvoyé.

## Tutoriel sur le RDE

Pour en savoir plus sur le RDE dans AEM as a Cloud Service, reportez-vous au [tutoriel vidéo qui explique comment le configurer et comment l’utiliser et qui montre le cycle de vie du développement](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/developing/rde/overview.html).
