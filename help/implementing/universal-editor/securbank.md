---
title: Exemple d’application SecurBank pour l’éditeur universel
description: Découvrez l’éditeur universel avec une expérience pratique en utilisant l’application SecurBank, conçue pour présenter la puissance, la flexibilité et la convivialité de l’éditeur universel pour accélérer la création de contenu.
exl-id: 97e1395f-b51e-4cee-b1d0-2466a08f96af
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '902'
ht-degree: 1%

---

# Exemple d’application SecurBank pour l’éditeur universel {#securbank}

Découvrez l’éditeur universel avec une expérience pratique en utilisant l’application SecurBank, conçue pour présenter la puissance, la flexibilité et la convivialité de l’éditeur universel pour accélérer la création de contenu.

## Conditions préalables {#prerequisites}

* Vous devez être affecté au **AEM Administrator** [ ](/help/journey-onboarding/assign-profiles-aem.md) pour installer l’application SecurBank.
* [Node.js](https://nodejs.org) version 20 ou supérieure doit être installé pour le développement local.

## Installation de SecurBank {#installation}

L’installation de l’application SecurBank est simple, mais comme elle touche de nombreux domaines d’AEM as a Cloud Service, plusieurs étapes sont impliquées. Vous trouverez ci-dessous un aperçu des principales étapes.

1. [Créez un programme sandbox dans Cloud Manager.](#create-sandbox-program)
1. [Cloner le référentiel git du programme et effectuer la mise à jour avec le contenu du projet AEM SecurBank.](#clone-and-update)
1. [Exécutez le pipeline pour déployer le projet AEM SecurBank.](#run-pipeline)
1. [Récupérez les informations d’identification Cloud Manager pour le développement d’applications web locales.](#retrieve-credentials)
1. [Téléchargez et configurez l’application Web SecurBank.](#download-web-app)
1. [Exécutez l’application web SecurBank.](#run-web-app)

Les sections suivantes décrivent les différentes tâches requises.

### Créez un programme sandbox dans Cloud Manager. {#create-sandbox-program}

Vous aurez besoin d’un nouveau programme Cloud Manager où vous pourrez installer SecurBank.

1. Se connecter à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionner l’organisation appropriée

1. Créez un nouveau programme d’environnement de test pour l’application SecurBank.

   * Utilisez les options par défaut lors de la sélection de **Solutions et modules complémentaires**.
   * Pour plus d’informations sur la création d’un programme Sandbox, consultez le document [Création de programmes Sandbox.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md)

### Cloner le référentiel git du programme et effectuer la mise à jour avec le contenu du projet AEM SecurBank. {#clone-and-update}

1. Une fois le programme créé, ouvrez-le et, dans l’onglet **Référentiels**, appuyez ou cliquez sur le bouton **Accéder aux informations de référentiel** pour ouvrir la boîte de dialogue **Informations de référentiel** et afficher les informations d’identification nécessaires pour accéder au référentiel git pour l’environnement de test.

   * Pour plus d&#39;informations sur l&#39;accès à vos informations de référentiel, consultez le document [Accès aux référentiels.](/help/implementing/cloud-manager/managing-code/accessing-repos.md)

1. À l’aide des informations d’identification de la boîte de dialogue **Repository Info**, clonez le référentiel sur votre ordinateur local.

1. Recherchez le dossier du clone local, ouvrez-le et supprimez tout le contenu, à l’exception des fichiers masqués/dot.

1. Récupérez le dernier code de projet AEM SecurBank à partir de GitHub à l’adresse [`https://github.com/Adobe-Marketing-Cloud/summit-2024-l425-securbank`](https://github.com/Adobe-Marketing-Cloud/summit-2024-l425-securbank) en cliquant sur **Code**, puis sur **Télécharger ZIP** dans la liste déroulante.

1. Décompressez le contenu du fichier zip sur votre système de fichiers local et déplacez-le dans le dossier désormais vide du clone local du programme sandbox.

1. À l’aide du terminal, passez au dossier du projet cloné, validez tout le contenu et poussez-le sur git.

   1. `git add --all`
   1. `git commit -m "Adding SecurBank app code"`
   1. `git push`

### Exécutez le pipeline pour déployer le projet AEM SecurBank. {#run-pipeline}

Une fois que le projet AEM pour SecurBank a été validé dans le référentiel sandbox, il peut être déployé avec un pipeline.

1. Revenez à l’onglet **Aperçu** de votre programme d’environnement de test dans Cloud Manager et exécutez le pipeline de non-production de pile complète.

   * Décochez toutes les options pour l’exécution du pipeline.
   * Pour plus d’informations sur l’exécution des pipelines, consultez le document [Gestion des pipelines.](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#running-pipelines)

### Récupérez les informations d’identification Cloud Manager pour le développement d’applications web locales. {#retrieve-credentials}

Avant d’exécuter l’application SecurBank, vous aurez besoin des informations d’identification Cloud Manager pour vous connecter à Cloud Manager.

1. Pendant l’exécution du pipeline, revenez à l’onglet **Overview** dans Cloud Manager, appuyez ou cliquez sur le bouton représentant des points de suspension en regard du nom de l’environnement et sélectionnez **Developer Console**.

1. Dans Developer Console, sélectionnez l’onglet **Intégrations** , puis l’onglet **Jeton local** et appuyez ou cliquez sur **Obtenir un jeton de développement local**.

1. Un fichier JSON est généré avec le jeton d’accès. Copiez uniquement le jeton lui-même (le JSON restant n’est pas nécessaire) à un emplacement sécurisé afin de l’utiliser à une étape ultérieure avant de fermer Developer Console et de revenir à Cloud Manager.

1. De retour dans Cloud Manager, dans l’onglet **Overview**, cliquez avec le bouton droit de la souris sur l’URL de l’environnement pour la copier et l’enregistrer à un emplacement sécurisé en vue de l’utiliser à une étape ultérieure.

### Téléchargez et configurez l’application Web SecurBank. {#download-web-app}

Vous pouvez maintenant télécharger et configurer l’application Web SecurBank.

1. Récupérez le dernier code d’application SecurBank à partir de GitHub à l’adresse [`https://github.com/Adobe-Marketing-Cloud/summit-2024-l425/tree/ue-z-final-with-events`](https://github.com/Adobe-Marketing-Cloud/summit-2024-l425/tree/ue-z-final-with-events) en cliquant sur **Code**, puis sur **Télécharger le ZIP** dans la liste déroulante.

1. Décompressez le contenu du fichier zip sur votre système de fichiers local.

1. Démarrez votre éditeur de code préféré et ouvrez le fichier d’environnement masqué dans le projet d’application SecurBank à l’adresse `summit-2024-l425-ue-z-final-with-events/react-app/.env`.

1. Apportez les modifications suivantes au fichier `.env` et enregistrez les modifications.

   * Pour `REACT_APP_HOST_URI`, collez la valeur de l’URL copiée précédemment de votre environnement.
   * Pour `REACT_APP_DEV_TOKEN`, collez la valeur du jeton de développement local copié précédemment.

### Exécutez l’application web SecurBank. {#run-web-app}

Avec tous les éléments configurés à la fois dans Cloud Manager et localement, vous pouvez exécuter l’application Web SecurBank.

1. Sur la ligne de commande de votre ordinateur local, accédez au dossier `react-app` du projet d’application SecurBank que vous avez téléchargé et décompressé.

1. Dans votre dossier `react-app`, installez l’application SecurBank avec la commande `node -i`.

1. Une fois installée, démarrez l’application SecurBank avec la commande `npm start`.

1. Si l’installation et le démarrage ont réussi, vous verrez :

* Sortie suivante dans le terminal.

  ```text
  Compiled successfully!
  
  You can now view securbank in the browser.
  
    Local:            https://localhost:3000
    On Your Network:  https://192.168.1.15:3000
  
  Note that the development build is not optimized.
  To create a production build, use npm run build.
  
  webpack compiled successfully
  ```

   * Et une fenêtre de navigateur s’ouvre sur l’URL `https://localhost:3000`.

      * Notez qu’il s’agit d’un certificat à des fins de développement et, par conséquent, aucun certificat valide n’est fourni. Par conséquent, vous devrez peut-être informer votre navigateur pour lui permettre d’accéder à la page.

Félicitations. Vous devriez maintenant voir l’application SecurBank s’exécuter correctement dans votre navigateur.

Si le contenu n’apparaît pas encore, vérifiez que le pipeline **Déployer vers Dev** que vous avez exécuté a réussi.

![Application SecurBank dans le navigateur](assets/securbank.png)
