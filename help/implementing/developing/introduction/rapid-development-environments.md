---
title: Environnements de développement rapide
description: Découvrez comment tirer parti des environnements de développement rapide pour des itérations de développement rapides sur un environnement cloud.
hidefromtoc: true
source-git-commit: 983901387d059a98942b4f7c533770a55dd4ff4a
workflow-type: tm+mt
source-wordcount: '2114'
ht-degree: 7%

---


# Environnements de développement rapide {#rapid-development-environments}

>[!AVAILABILITY]
>
>Cette fonctionnalité n’est pas encore disponible.

Pour déployer des modifications, les environnements de développement cloud actuels nécessitent l’utilisation d’un processus qui utilise des règles de sécurité et de qualité de code étendues appelées pipeline CI/CD. Dans les cas où des modifications rapides et itératives sont nécessaires, Adobe a introduit des environnements de développement rapide (RDE).

Les RDE permettent aux développeurs de déployer et de passer rapidement en revue les modifications, ce qui réduit le temps nécessaire au test des fonctionnalités dont il est prouvé qu’elles fonctionnent dans un environnement de développement local.

Une fois les modifications testées dans un RDE, elles peuvent être déployées dans un environnement de développement cloud classique via le pipeline Cloud Manager.

## Présentation {#introduction}

Les RDE peuvent être utilisés pour les configurations de code, de contenu et Apache ou Dispatcher. Contrairement aux environnements de développement cloud standard, les développeurs peuvent utiliser des outils de ligne de commande locaux pour synchroniser le code créé localement avec un RDE.

Chaque programme est configuré avec un RDE. Dans le cas de comptes Sandbox, ils seront mis en veille après quelques heures de non-utilisation.

En règle générale, un RDE est utilisé par un seul développeur à la fois, pour tester et déboguer une fonctionnalité spécifique. Une fois la session de développement terminée, le RDE peut être réinitialisé à l’état par défaut pour l’utilisation suivante.

<!-- Temporarily hiding this. See CQDOC-19795 for more details

Additional RDEs may be purchased for Production programs -->

## Activation de RDE dans un programme {#enabling-rde-in-a-program}

Suivez ces étapes pour utiliser Cloud Manager afin de créer un RDE pour votre programme.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Cliquez sur le programme auquel vous souhaitez ajouter un RDE pour en afficher les détails.

   * Les RDE peuvent être ajoutés aux deux [programmes sandbox](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md) et [programmes de production.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-production-programs.md)

1. Dans la page **Aperçu du programme**, cliquez sur **Ajouter un environnement** dans la carte **Environnements** pour ajouter un environnement.

   ![Carte Environnements](/help/implementing/cloud-manager/assets/no-environments.png)

   * L’option **Ajouter un environnement** est également disponible dans l’onglet **Environnements**.

      ![Onglet Environnements](/help/implementing/cloud-manager/assets/environments-tab.png)

   * L’option **Ajouter un environnement** peut être désactivée en raison d’un niveau d’autorisation insuffisant ou de ressources sous licence.

1. Dans la boîte de dialogue **Ajouter un environnement** qui s’affiche :

   * Sélectionner **Développement rapide** sous le **Sélection du type d’environnement** en-tête.
      * Le nombre d’environnements disponibles/utilisés est indiqué entre parenthèses derrière le type d’environnement.
   * Fournissez une **Nom** pour l’environnement.
   * Fournissez un **Description** pour l’environnement.
   * Sélectionnez une **Région Cloud**.

   ![Boîte de dialogue Ajouter un environnement](/help/implementing/cloud-manager/assets/add-environment-wizard.png)

1. Cliquez sur **Enregistrer** pour ajouter l’environnement spécifié.

L’écran **Aperçu** affiche désormais votre nouvel environnement dans la carte **Environnements.**

Pour plus d’informations sur l’utilisation de Cloud Manager pour créer des environnements, gérer les personnes qui y ont accès et affecter des domaines personnalisés, voir [la documentation de Cloud Manager.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md)

## Installation des outils de ligne de commande RDE {#installing-the-rde-command-line-tools}

Une fois que vous avez ajouté un RDE pour votre programme à l’aide de Cloud Manager, vous pouvez interagir avec celui-ci en configurant les outils de ligne de commande, comme décrit dans les étapes suivantes :

1. Installez les outils de l’interface de ligne de commande d’Adobe I/O en suivant la procédure [here](https://developer.adobe.com/runtime/docs/guides/tools/cli_install/).
1. Installez le module externe de gestion de cloud des outils de l’interface de ligne de commande d’Adobe I/O et configurez-le comme décrit [here](https://github.com/adobe/aio-cli-plugin-cloudmanager).
1. Installez les outils de l’interface de ligne de commande d’Adobe I/O AEM le module externe RDE en exécutant les commandes suivantes :

   ```
   aio plugins:install @adobe/aio-cli-plugin-aem-rde
   aio plugins:update
   ```

1. Configurez le module externe cloud Manager pour l’ID d’organisation :

   `aio config:set cloudmanager_orgid 4E03EQC05D34GL1A0B49421C@AdobeOrg`

   et remplacez la chaîne alphanumérique par votre propre ID d’organisation, qui peut être recherchée à l’aide de la stratégie. [here](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html#concept_EA8AEE5B02CF46ACBDAD6A8508646255).

1. Configurez ensuite votre ID de programme :

   `aio config:set cloudmanager_programid 12345`

1. Ensuite, configurez l’ID d’environnement auquel le RDE sera associé :

   `aio config:set cloudmanager_environmentid 123456`

1. Une fois la configuration du module externe terminée, connectez-vous en procédant comme suit :

   `aio login`

   La réponse lors d’une connexion réussie doit ressembler à la sortie ci-dessous, mais vous pouvez ignorer les valeurs affichées.

   ```
   ...
   You are currently in:
   1. Org: <no org selected>
   2. Project: <no project selected>
   3. Workspace: <no workspace selected>
   ```

1. Vérifiez que la connexion s’est bien déroulée en exécutant

   `aio cloudmanager:list-programs`

   Cela devrait répertorier tous les programmes sous votre organisation configurée.

   Notez que ce qui précède nécessite que vous soyez membre de Cloud Manager. **Développeur - Cloud Service** Profil du produit. Consultez [cette page](/help/journey-onboarding/assign-profiles-cloud-manager.md#assign-developer) pour plus de détails.

   Vous pouvez également vérifier que vous disposez de ce rôle de développeur si vous pouvez vous connecter à la console de développement en exécutant cette commande :

   `aio cloudmanager:environment:open-developer-console`

## Utilisation de RDE lors du développement d’une nouvelle fonctionnalité {#using-rde-while-developing-a-new-feature}

Adobe recommande le processus suivant pour développer une nouvelle fonctionnalité :

* Lorsqu’un jalon intermédiaire est atteint et validé localement avec le SDK as a Cloud Service AEM, le code doit être validé dans une branche de fonctionnalité Git qui ne fait pas encore partie de la ligne principale, bien que la validation de ce dernier soit facultative. Ce qui constitue un &quot;jalon intermédiaire&quot; varie en fonction des habitudes de l’équipe. Par exemple, quelques nouvelles lignes de code, une demi-journée de travail ou l’achèvement d’une sous-fonctionnalité.

* Réinitialisez le RDE s’il a été utilisé par une autre fonctionnalité et si vous souhaitez [la réinitialiser à un état par défaut](#reset-rde). <!-- Alexandru: hiding for now, please don't delete This can be done via [Cloud Manager](#reset-the-rde-cloud-manager) or via the [command line](#reset-the-rde-command-line). -->La réinitialisation prend quelques minutes et tout le contenu et le code existants seront supprimés. Vous pouvez utiliser la commande d’état RDE pour confirmer que le RDE est prêt.

* À l’aide de l’interface de ligne de commande RDE, synchronisez le code local avec le RDE. Les options incluent l’installation d’un module de contenu, d’un lot spécifique, d’un fichier de configuration OSGI, d’un fichier de contenu et d’un fichier zip d’une configuration Apache/Dispatcher. Il est également possible de référencer un module de contenu distant. Voir [Outils de ligne de commande RDE](#rde-cli-commands) pour plus d’informations. Vous pouvez utiliser la commande status pour vérifier que le déploiement a réussi. Vous pouvez éventuellement utiliser le gestionnaire de modules pour installer des modules de contenu.

* Testez le code dans l’éditeur de texte enrichi. Les URL de création et de publication sont disponibles dans Cloud Manager.

* Si le code ne se comporte pas comme prévu, utilisez des techniques de débogage standard pour comprendre le problème et apportez les modifications appropriées. Sans valider les modifications du code dans git (puisqu’elles n’ont pas été validées), utilisez l’interface de ligne de commande locale pour synchroniser le code avec l’éditeur de texte enrichi. Continuez à itérer jusqu’à ce que le problème soit résolu.

* Une fois que le code se comporte comme prévu, validez le code sur la branche de la fonctionnalité git.

* Le code synchronisé avec RDE n’utilise pas de pipeline Cloud Manager. Vous devez donc maintenant utiliser un pipeline hors production Cloud Manager pour déployer la branche de fonctionnalités Git dans l’environnement de développement Cloud. Cela confirme que le code passe les points de contrôle qualité de Cloud Manager et vous permet d’être sûr que le code sera déployé ultérieurement avec succès à l’aide du pipeline de production Cloud Manager.

* Répétez les étapes ci-dessus pour chaque jalon intermédiaire jusqu’à ce que tout le code de la fonctionnalité soit prêt et s’exécute correctement dans l’environnement de développement RDE et cloud.

* Déployez le code en production via le pipeline de production Cloud Manager.

## Utilisation de RDE pour déboguer une fonction existante {#use-rde-to-debug-an-existing-feature}

Le workflow est similaire au développement d’une nouvelle fonctionnalité. La différence est que le code synchronisé avec RDE reflète le libellé Git de tout ce qui a été envoyé à l’environnement où le problème a été détecté. En outre, il peut s’avérer utile de déployer du contenu correspondant à l’environnement en amont. Pour ce faire, vous pouvez exporter et importer des packages de contenu.

## Collaboration de plusieurs développeurs sur le même RDE {#multiple-developers-collaborating-on-the-same-rde}

Un RDE prend en charge un seul projet à la fois. Comme le code est synchronisé d’un environnement de développement local à l’environnement RDE, il est plus naturel pour un développeur de l’utiliser seul à un moment donné.

Cependant, avec une coordination étroite, il est possible pour plusieurs développeurs de valider une fonctionnalité spécifique ou de déboguer un problème spécifique. La clé est que chaque développeur conserve ses projets locaux synchronisés de sorte que les modifications de code effectuées par un développeur particulier soient absorbées par les autres développeurs, sinon un développeur risque de remplacer par inadvertance le code de l’autre. La stratégie recommandée est que chaque développeur valide ses modifications dans une branche git partagée avant la synchronisation avec l’éditeur de texte enrichi, de sorte que les autres développeurs extraient les modifications avant d’apporter leurs propres modifications.

## Commandes des outils de ligne de commande RDE {#rde-cli-commands}

### Aide/Informations générales {#help}

* Pour obtenir une liste des commandes, saisissez :

   `aio aem:rde`

* Pour obtenir une aide détaillée sur une commande, saisissez :

   `aio aem rde <command> --help`

### Déploiement sur RDE {#deploying-to-rde}

Cette section décrit l’utilisation de l’interface de ligne de commande RDE pour le déploiement, l’installation ou la mise à jour de lots, de configurations OSGI, de packages de contenu, de fichiers de contenu individuels et de configurations Apache ou Dispatcher.

Le modèle d’utilisation général est le suivant : `aio aem:rde:install <artifact>`.

Vous trouverez ci-dessous quelques exemples :

<u>Déploiement d’un module de contenu</u>

`aio aem:rde:install sample.demo.ui.apps.all-1.0.0-SNAPSHOT.zip`

La réponse pour un déploiement réussi ressemble à ce qui suit :

```
...
#1: deploy completed for content-package sample.demo.ui.apps.all-1.0.0-SNAPSHOT.zip on author,publish - done by 9E072FC75D54FE1A2B49431C@AdobeID at 2022-09-13T11:32:06.229Z
```

Vous pouvez éventuellement référencer un référentiel distant :

`aio aem:rde:install 'https://repo1.maven.org/maven2/com/adobe/aem/guides/aem-guides-wknd.all/2.1.0/aem-guides-wknd.all-2.1.0.zip'`

<u>Déploiement d’une configuration OSGI</u>

`aio aem:rde:install com.adobe.granite.demo.MyServlet.cfg.json`

où la réponse pour un déploiement réussi ressemble à ce qui suit :

```
...
#2: deploy completed for osgi-config com.adobe.granite.demo.MyServlet.cfg.json on author,publish - done by 9E0725C05D54FE1A0B49431C@AdobeID at 2022-09-13T11:54:36.390Z
```

<u>Déploiement d’un lot</u>

Pour déployer un lot, utilisez :

`aio aem:rde:install ~/.m2/repository/org/apache/felix/org.apache.felix.gogo.jline/1.1.8/org.apache.felix.gogo.jline-1.1.8.jar`

où la réponse pour un déploiement réussi ressemble à ce qui suit :

```
...
#3: deploy staged for osgi-bundle org.apache.felix.gogo.jline-1.1.8.jar on author,publish - done by 9E0725C05D53BE1A0B49431C@AdobeID at 2022-09-14T07:54:28.882Z
```

<u>Déploiement d’un fichier de contenu</u>

Pour déployer un fichier de contenu, utilisez :

`aio aem:rde:install world.txt -p /apps/hello.txt`

où la réponse pour un déploiement réussi ressemble à ce qui suit :

```
..
#4: deploy completed for content-file world.txt on author,publish - done by 9E0729C05C54FE1A0B49431C@AdobeID at 2022-09-14T07:49:30.644Z
```

<u>Déploiement d’une configuration Apache/Dispatcher</u>

L’ensemble de la structure de dossiers doit se présenter sous la forme d’un fichier zip pour ce type de configuration. Vous pouvez le zipper en exécutant cette commande à partir de la racine d’un dossier de configuration du Dispatcher :

`zip -y -r dispatcher.zip`

déployez ensuite la configuration par cette commande :

`aio aem:rde:install -t dispatcher-config dispatcher-wknd-2.1.0.zip`

Un déploiement réussi génère une réponse qui ressemble à ce qui suit :

```
..
#5 deploy completed for dispatcher-config dispatcher.zip on author,publish - done by 9E0735C05T54FE1A0B49431C@AdobeID at 2022-10-03T10:26:31.286Z
Logs:
  Cloud manager validator 2.0.49
  2022/10/03 10:26:37 No issues found
  Syntax OK
```

Le code déployé sur RDE ne fait pas l’objet d’un pipeline Cloud Manager et de ses points de contrôle qualité associés. Cependant, le code fait l’objet d’une analyse qui signalera les erreurs, comme illustré dans l’exemple de code ci-dessous :

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

L’exemple de code ci-dessus illustre le comportement si un lot ne se résout pas, auquel cas il est &quot;intermédiaire&quot; et ne sera installé que si ses exigences (importations manquantes, dans ce cas) sont satisfaites par l’installation d’un autre code.

### Vérification du statut du RDE {#checking-rde-status}

Vous pouvez utiliser l’interface de ligne de commande de RDE pour vérifier si l’environnement est prêt à être déployé, comme les déploiements effectués via le module externe de RDE.

En cours :

`aio aem:rde:status`

renverra :

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

Si la commande renvoie une note sur le déploiement des instances, vous pouvez continuer et effectuer la mise à jour suivante, mais votre dernière peut ne pas encore être visible sur l’instance.

### Afficher l’historique de déploiement {#show-deployment-history}

Vous pouvez vérifier l’historique des déploiements effectués sur le RDE en exécutant :

`aio aem:rde:history`

qui renvoie une réponse sous la forme :

`#1: deploy completed for content-package aem-guides-wknd.all-2.1.0.zip on author,publish - done by 029039A55D4DE16A0A494025@AdobeID at 2022-09-12T14:41:55.393Z`

### Suppression de RDE {#deleting-from-rde}

Vous pouvez supprimer des configurations et des lots qui ont été déployés précédemment sur RDE via l’outil d’interface de ligne de commande. Utilisez la variable `status` pour une liste de ce qui peut être supprimé, qui inclut la commande `bsn` pour les lots et `pid` pour les configurations à référencer dans la commande de suppression.

Par exemple, si `com.adobe.granite.demo.MyServlet.cfg.json` a été installé, la variable `bsn` est juste `com.adobe.granite.demo.MyServlet`, sans la variable **cfg.json** suffixe.

La suppression des packages de contenu ou des fichiers de contenu n’est pas prise en charge. Pour les supprimer, le RDE doit être réinitialisé, ce qui le renverra à un état par défaut.

Voir l’exemple ci-dessous pour plus de détails :

```
aio aem:rde:delete com.adobe.granite.csrf.impl.CSRFFilter
#13: delete completed for osgi-config com.adobe.granite.csrf.impl.CSRFFilter on author - done by karl at 2022-09-12T22:01:01.955Z
#14: delete completed for osgi-config com.adobe.granite.csrf.impl.CSRFFilter on publish - done by karl at 2022-09-12T22:01:12.979Z
```

## Réinitialiser {#reset-rde}

La réinitialisation de l’éditeur de texte enrichi supprime tout le code personnalisé, les configurations et le contenu des instances d’auteur et de publication. Cela peut s’avérer utile, par exemple, si le RDE a été utilisé pour tester une fonctionnalité spécifique et que vous souhaitez la réinitialiser à un état par défaut afin de tester une autre fonctionnalité.

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

Vous pouvez utiliser Cloud Manager pour réinitialiser votre RDE en procédant comme suit :

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Cliquez sur le programme pour lequel vous souhaitez réinitialiser le RDE.

1. Dans la page **Aperçu**, cliquez sur l’onglet **Environnements** dans la partie supérieure de l’écran.

   ![Onglet Environnements](/help/implementing/cloud-manager/assets/environments-tab2.png)

   * Vous pouvez également cliquer sur le bouton **Tout afficher** dans la carte **Environnements** pour accéder directement à l’onglet **Environnements**.

      ![Option Tout afficher](/help/implementing/cloud-manager/assets/environment-showall.png)

1. Le **Environnements** s’ouvre et répertorie tous les environnements du programme.

   ![Onglet Environnements](/help/implementing/cloud-manager/assets/environments-tab-populated.png)

1. Cliquez sur le bouton représentant des points de suspension de l’éditeur de texte enrichi que vous souhaitez réinitialiser, puis sélectionnez **Réinitialiser**.

   ![Affichage des détails de l’environnement](/help/implementing/cloud-manager/assets/rde-reset.png)

1. Confirmez que vous souhaitez réinitialiser le RDE en cliquant sur **Réinitialiser** dans la boîte de dialogue.

   ![Confirmer la réinitialisation](/help/implementing/cloud-manager/assets/rde-reset-confirm.png)

1. Cloud Manager confirme par une bannière que le processus de réinitialisation a démarré.

   ![Réinitialiser la notification de bannière](/help/implementing/cloud-manager/assets/rde-reset-banner.png)

Une fois le processus de réinitialisation de RDE démarré, l’exécution prend généralement quelques minutes, puis l’environnement retrouve son état par défaut. L’état du processus de réinitialisation peut être affiché à tout moment dans la variable **État** de la colonne **Environnements** ou dans la variable **Environnements** fenêtre.

![État de réinitialisation RDE](/help/implementing/cloud-manager/assets/rde-reset-status-environments-card.png)

Vous pouvez également réinitialiser l’éditeur de texte enrichi à l’aide du bouton représentant des points de suspension directement à partir du **Environnements** sur la carte **Présentation** page.

![Réinitialisation de RDE à partir de la carte Environnements](/help/implementing/cloud-manager/assets/rde-reset-environments-card.png)

Pour plus d’informations sur l’utilisation de Cloud Manager pour gérer vos environnements, voir [la documentation de Cloud Manager.](/help/implementing/cloud-manager/manage-environments.md)

## Journalisation {#logging}

Les niveaux de journal peuvent être définis en modifiant les configurations OSGi. Vérifiez les [documentation](/help/implementing/developing/introduction/logging.md) pour plus d’informations.

## En quoi les RDE diffèrent-ils des environnements de développement cloud ? {#how-are-rds-different-from-cloud-development-environments}

Bien que le RDE soit à de nombreux égards similaire à un environnement de développement cloud, il existe des différences architecturales mineures afin de permettre une synchronisation rapide du code. Le mécanisme de transfert de code vers RDE est différent : pour les RDE, un synchronise le code d’un environnement de développement local, tandis que pour les environnements de développement Cloud, un déploie le code via Cloud Manager.

Pour ces raisons, il est recommandé, après avoir validé le code dans un environnement RDE, de déployer le code dans un environnement de développement Cloud à l’aide du pipeline hors production. Enfin, testez le code avant de le déployer avec le pipeline de production.

<!-- Temporarily hiding this. See CQDOC-19795 for more details

## How many RDEs do I need? {#how-many-rds-do-i-need}

The purchase of additional RDEs for Production programs will be possible beginning with late January.

The number of RDEs needed depends on the make-up and processes of an organization. The most flexible model is where an organization purchases a dedicated RDE for each one of their AEM CS developers. In this model, each developer can test their code on the RDE without needing to coordinate with other team members around whether an RDE environment is available.

At the other extreme, a team with a single RDE may use internal processes to coordinate which developer can use the environment at a given time. This can possibly be whenever a developer has hit an intermediate feature milestone and is ready to validate in a Cloud environment where they can quickly make the changes they need.

An intermediate model is one where an organization purchases a number of RDEs that will create a situation in which not every developer will have a dedicated environment, but there is a greater likelihood of an unused RDE being available. One strategy could be to allocate an RDE per scrum team or major feature. Internal processes may be used to coordinate usage of the environments. -->
