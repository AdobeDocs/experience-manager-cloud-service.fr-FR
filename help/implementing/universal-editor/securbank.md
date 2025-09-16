---
title: Exemple d’application SecurBank pour l’éditeur universel
description: Découvrez l’éditeur universel et son expérience pratique en utilisant l’application SecurBank, conçue pour présenter la puissance, la flexibilité et la convivialité de l’éditeur universel afin d’accélérer la création de contenu.
exl-id: 97e1395f-b51e-4cee-b1d0-2466a08f96af
feature: Developing
role: Admin, Architect, Developer
source-git-commit: c4dcb1cecb756f746ecb856fcfd65d73833a5ee0
workflow-type: ht
source-wordcount: '902'
ht-degree: 100%

---

# Exemple d’application SecurBank pour l’éditeur universel {#securbank}

Découvrez l’éditeur universel et son expérience pratique en utilisant l’application SecurBank, conçue pour présenter la puissance, la flexibilité et la convivialité de l’éditeur universel afin d’accélérer la création de contenu.

## Conditions préalables {#prerequisites}

* Vous devez disposer d’une affectation au [profil de produit](/help/journey-onboarding/assign-profiles-aem.md) **administrateur ou administratrice AEM** pour installer l’application SecurBank.
* La version 20 ou ultérieure de [Node.js](https://nodejs.org) doit être installée pour le développement local.

## Installation de SecurBank {#installation}

L’installation de l’application SecurBank est simple, mais plusieurs étapes sont nécessaires car elle touche de nombreux domaines d’AEM as a Cloud Service. Voici un aperçu des principales étapes.

1. [Créez un programme sandbox dans Cloud Manager](#create-sandbox-program).
1. [Clonez le référentiel Git du programme et mettez-le à jour avec le contenu du projet SecurBank AEM](#clone-and-update).
1. [Exécutez le pipeline pour déployer le projet SecurBank AEM](#run-pipeline).
1. [Récupérez les informations d’identification Cloud Manager pour le développement local d’applications web](#retrieve-credentials).
1. [Téléchargez et configurez l’application web SecurBank](#download-web-app).
1. [Exécutez l’application web SecurBank](#run-web-app).

Les sections suivantes décrivent en détail les différentes tâches requises.

### Créez un programme sandbox dans Cloud Manager. {#create-sandbox-program}

Vous aurez besoin d’un nouveau programme Cloud Manager dans lequel installer SecurBank.

1. Se connecter à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionner l’organisation appropriée

1. Créez un nouveau programme sandbox pour l’application SecurBank.

   * Utilisez les options par défaut lorsque vous sélectionnez **Solutions et modules complémentaires**.
   * Pour plus d’informations sur la création d’un programme sandbox, consultez le document [Création de programmes sandbox](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md).

### Clonez le référentiel Git du programme et mettez-le à jour avec le contenu du projet SecurBank AEM. {#clone-and-update}

1. Une fois le programme créé, ouvrez-le et, dans l’onglet **Référentiels**, appuyez ou cliquez sur le bouton **Accéder aux informations sur le référentiel** pour ouvrir la boîte de dialogue **Informations du référentiel** et afficher les informations d’identification nécessaires pour accéder au référentiel Git pour l’environnement sandbox.

   * Pour plus d’informations sur l’accès aux informations de votre référentiel, consultez le document [Accès aux référentiels](/help/implementing/cloud-manager/managing-code/accessing-repos.md).

1. À l’aide des informations d’identification de la boîte de dialogue **Informations du référentiel**, clonez le référentiel sur votre ordinateur local.

1. Recherchez le dossier du clone local, ouvrez-le et supprimez tout le contenu, à l’exception des fichiers masqués (qui commencent par un point).

1. Récupérez le dernier code de projet SecurBank AEM sur GitHub sur [`https://github.com/Adobe-Marketing-Cloud/summit-2024-l425-securbank`](https://github.com/Adobe-Marketing-Cloud/summit-2024-l425-securbank) en cliquant sur **Code** puis sur **Télécharger le fichier ZIP** dans la liste déroulante.

1. Décompressez le contenu du fichier ZIP sur votre système de fichiers local et déplacez-le vers le dossier dorénavant vide du clone local du programme sandbox.

1. À l’aide du terminal, basculez vers le dossier du projet cloné, validez tout le contenu et envoyez-le vers Git.

   1. `git add --all`
   1. `git commit -m "Adding SecurBank app code"`
   1. `git push`

### Exécutez le pipeline pour déployer le projet SecurBank AEM. {#run-pipeline}

Une fois le projet AEM pour SecurBank validé dans le référentiel sandbox, il peut être déployé avec un pipeline.

1. Revenez à l’onglet **Aperçu** de votre programme sandbox dans Cloud Manager et exécutez le pipeline hors production full stack.

   * Décochez toutes les options d’exécution du pipeline.
   * Pour plus d’informations sur l’exécution des pipelines, consultez le document [Gestion des pipelines](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#running-pipelines).

### Récupérez les informations d’identification Cloud Manager pour le développement local d’applications web. {#retrieve-credentials}

Avant de pouvoir exécuter l’application SecurBank, vous aurez besoin des informations d’identification Cloud Manager pour connecter l’application à Cloud Manager.

1. Pendant l’exécution du pipeline, revenez à l’onglet **Aperçu** dans Cloud Manager, appuyez ou cliquez sur le bouton à trois points à côté du nom de l’environnement et sélectionnez **Developer Console**.

1. Dans Developer Console, sélectionnez l’onglet **Intégrations** puis l’onglet **Jeton local** et appuyez ou cliquez sur **Obtenir le jeton de développement local**.

1. Un fichier JSON est généré avec le jeton d’accès. Copiez uniquement le jeton lui-même (le fichier JSON restant n’est pas nécessaire) vers un emplacement sécurisé en vue d’une utilisation à une étape ultérieure avant de fermer la Developer Console et de revenir à Cloud Manager.

1. De retour dans Cloud Manager, dans l’onglet **Aperçu**, cliquez avec le bouton droit sur l’URL de l’environnement pour la copier et l’enregistrer à un emplacement sécurisé en vue d’une utilisation à une étape ultérieure.

### Téléchargez et configurez l’application web SecurBank. {#download-web-app}

Vous pouvez maintenant télécharger et configurer l’application web SecurBank.

1. Récupérez le dernier code de l’application SecurBank sur GitHub à l’adresse [`https://github.com/Adobe-Marketing-Cloud/summit-2024-l425/tree/ue-z-final-with-events`](https://github.com/Adobe-Marketing-Cloud/summit-2024-l425/tree/ue-z-final-with-events) en cliquant sur **Code** puis sur **Télécharger le fichier ZIP** dans la liste déroulante.

1. Décompressez le contenu du fichier ZIP sur le système de fichiers local.

1. Démarrez l’éditeur de code de votre choix et ouvrez le fichier d’environnement masqué dans le projet de l’application SecurBank à l’adresse `summit-2024-l425-ue-z-final-with-events/react-app/.env`.

1. Apportez les modifications suivantes au fichier `.env` et enregistrez-les.

   * Pour `REACT_APP_HOST_URI`, collez la valeur de l’URL de l’environnement précédemment copiée.
   * Pour `REACT_APP_DEV_TOKEN`, collez la valeur du jeton de développement local précédemment copié.

### Exécutez l’application web SecurBank. {#run-web-app}

Une fois la configuration effectuée dans Cloud Manager et en local, exécutez l’application web SecurBank.

1. Sur la ligne de commande de votre ordinateur local, accédez au dossier `react-app` du projet d’application SecurBank que vous avez téléchargé et décompressé.

1. Dans votre dossier `react-app`, installez l’application SecurBank avec la commande `node -i`.

1. Une fois installée, lancez l&#39;application SecurBank avec la commande `npm start`.

1. Si l’installation et le démarrage ont réussi, vous verrez :

* La sortie suivante dans le terminal.

  ```text
  Compiled successfully!
  
  You can now view securbank in the browser.
  
    Local:            https://localhost:3000
    On Your Network:  https://192.168.1.15:3000
  
  Note that the development build is not optimized.
  To create a production build, use npm run build.
  
  webpack compiled successfully
  ```

   * Et une fenêtre de navigateur ouverte sur l’URL `https://localhost:3000`.

      * Notez qu’il s’agit d’un élément à des fins de développement et, par conséquent, aucun certificat valide n’est fourni. Par conséquent, vous devrez peut-être informer votre navigateur pour lui permettre d’accéder à la page.

Félicitations. Vous devriez maintenant voir l’application SecurBank s’exécuter correctement dans votre navigateur.

Si le contenu n’apparaît pas encore, assurez-vous que le pipeline **Déployer vers l’environnement de développement** que vous avez exécuté est terminé.

![Application SecurBank dans le navigateur](assets/securbank.png)

{{ue-headless-auth}}

