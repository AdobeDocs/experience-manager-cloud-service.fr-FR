---
title: Navigateur de référentiel
seo-title: Repository Browser
description: Le navigateur de référentiel fournit une vue en lecture seule dans le référentiel pour tous les environnements sur les niveaux de création, de publication et de prévisualisation.
seo-description: The repository browser provides a read-only view into the repository for all environments on author, publish, and preview tiers.
exl-id: 22473a97-8f7b-4014-b885-1233116aeda6
feature: Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '871'
ht-degree: 78%

---

# Navigateur de référentiel {#repository-browser}

>[!NOTE]
>
>Le navigateur de référentiel est disponible dans les versions 6582 et ultérieures d’AEM.

>[!INFO]
>
>Vous pouvez également regarder [ce clip](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/repository-browser.html?lang=fr) pour profiter d’une vidéo de présentation rapide sur l’utilisation du navigateur de référentiel pour déboguer AEM as a Cloud Service.

## Présentation {#introduction}

Le navigateur de référentiels est un outil de développement qui fournit une vue en lecture seule dans le référentiel pour tous les environnements sur les niveaux de création, de publication et d’aperçu. Il est conçu pour faciliter l’affichage de la structure de contenu afin de consulter ou de déboguer plus facilement du contenu.

Accessible à partir du [Developer Console AEM as a Cloud Service](/help/implementing/developing/introduction/development-guidelines.md#crxde-lite-and-developer-console), il peut être utilisé pour parcourir le référentiel d’une instance de création ou de publication pour un environnement sélectionné.

### Conditions préalables d’accès {#access-prerequisites}

Ces conditions suivantes doivent être remplies pour accéder au Developer Console AEM as a Cloud Service ou au navigateur de référentiel

Pour accéder au Developer Console AEM as a Cloud Service, voir Accès à [Developer Console](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/developer-console#developer-console-access).

Pour accéder au navigateur de référentiel, les conditions requises sont les mêmes que pour AEM as a Cloud Service Developer Console (spécifié ci-dessus). Pour afficher le contenu du navigateur de référentiel pour une instance particulière :

* Instances d’auteur : les utilisateurs disposant du profil de produit Utilisateurs AEM pour l’**instance d’auteur** peuvent afficher le navigateur de référentiel avec un accès en lecture minimal ; les autorisations de l’utilisateur sont respectées lors de la navigation dans le référentiel. Les utilisateurs disposant du profil produit Administrateurs AEM peuvent afficher le navigateur de référentiel avec un accès en lecture complet.

* Instances de publication : les utilisateurs disposant du profil de produit Utilisateurs AEM pour l’**instance de publication** peuvent afficher le navigateur de référentiel avec un accès en lecture minimal. Sans cet ensemble de profils de produit, les utilisateurs navigueront en tant qu’utilisateurs anonymes et certains chemins n’apparaîtront pas en raison d’autorisations limitées.

Pour plus d’informations sur la configuration des autorisations des utilisateurs, consultez la [Documentation de Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/requirements/users-and-roles.html?lang=fr).

### Lancement du navigateur de référentiel {#launching-the-repository-browser}

Le navigateur de référentiel peut être lancé en suivant les étapes ci-dessous.

1. Dans Cloud Manager, cliquez sur les trois points de l’environnement de votre choix, puis sélectionnez la **Developer Console**

   ![repobrowser1](/help/implementing/developing/tools/assets/repobrowser1.png)

1. Cliquez ensuite sur l’onglet **Navigateur de référentiel**.
1. Sélectionnez une capsule à créer, à publier ou à prévisualiser en cliquant sur la liste déroulante **Capsule**.

   ![repobrowser2](/help/implementing/developing/tools/assets/repobrowser2.png)

1. Lancez le navigateur de référentiels en cliquant sur le lien **Ouvrir le navigateur de référentiels** plus bas. Le navigateur correspondant à une instance représentative (capsule) pour le niveau sélectionné est lancé. Notez que vous ne pouvez pas contrôler la capsule spécifique pour le niveau lancé.

## Fonctions {#features}

### Navigation dans la hiérarchie {#navigate-the-hierarchy}

Vous pouvez utiliser le volet de navigation de gauche pour naviguer dans la hiérarchie du contenu. Cliquez sur chaque dossier ou nœud pour afficher ses enfants. La structure de dossiers reflète l’arborescence de ressources Sling, qui est un super-ensemble de l’arborescence de nœuds JCR.

![repobrowser3](/help/implementing/developing/tools/assets/repobrowser3.png)

Vous pouvez également accéder directement à un chemin d’accès en le saisissant dans le champ **Chemin d’accès**, comme illustré ci-dessous. Ce chemin est également développé dans l’affichage hiérarchique du contenu sur la gauche.

![repobrowser14](/help/implementing/developing/tools/assets/repobrowser14.png)

Lorsque vous cliquez sur un dossier sur la gauche, le champ Chemin d’accès est automatiquement renseigné avec son emplacement. Cette fonctionnalité est utile pour copier et coller la valeur en vue d’une utilisation ultérieure.

De plus, lorsque vous cliquez sur un dossier, l’URL est modifiée dynamiquement afin d’inclure le chemin d’accès à ce dossier. Cette fonctionnalité permet d’ajouter les URL aux signets.

Pour la publication, par défaut, le navigateur de référentiel affiche uniquement le contenu public, de sorte que certains dossiers comme `/conf` ou `/home` ne sont pas visibles.

Pour rendre ces emplacements visibles, procédez comme suit.

1. Cliquez sur les trois points de l’environnement de votre choix et sélectionnez **Gérer l’accès**.

   ![repobrowser7](/help/implementing/developing/tools/assets/repobrowser7.png)

1. Recherchez votre instance de publication, puis cliquez dessus

   ![repobrowser8](/help/implementing/developing/tools/assets/repobrowser8.png)

1. Créez un profil de produit pour les administrateurs et les administratrices de publication. Dans l’exemple ci-dessous, il s’appelle **DEV - AEM Administrators Publish**.

   ![repobrowser9](/help/implementing/developing/tools/assets/repobrowser9.png)

1. Ajoutez les utilisateurs appropriés, correspondant à ceux qui doivent pouvoir naviguer dans le navigateur de référentiel de publication avec un accès complet, au nouveau profil de produit.

   ![repobrowser10](/help/implementing/developing/tools/assets/repobrowser10.png)

1. Patientez quelques minutes, puis ouvrez la console **Création AEM**.
1. Ajoutez le groupe correspondant au nouveau profil de produit en tant que membre du groupe d’administration en cliquant sur **Outils - Sécurité - Groupes en mode de création**, puis cliquez sur le groupe **administration**. Ajoutez ensuite le groupe comme illustré ci-dessous.

   ![repobrowser11](/help/implementing/developing/tools/assets/repobrowser11.png)

1. Activez le groupe **Administrateurs** et le nouveau groupe **DEV - AEM Administrators Publish** afin qu’ils soient disponibles pour la publication.

   ![repobrowser12](/help/implementing/developing/tools/assets/repobrowser12.png)

1. De bonnes pratiques de sécurité demandent que vous supprimiez le nouveau groupe **DEV - AEM Administrators Publish** du groupe d’administration en mode de **création** afin que le nouveau groupe reste isolé pour la publication

   ![repobrowser13](/help/implementing/developing/tools/assets/repobrowser13.png)

1. Lors de l’accès au navigateur de référentiel pour une instance de publication, tous les dossiers sont visibles, y compris `/home` et `/conf`.

### Affichage des propriétés JCR {#view-jcr-properties}

Cliquez sur un nœud pour afficher ses propriétés JCR dans le volet de droite du navigateur. Vous trouverez ci-dessous un exemple de nœud `experience-fragments`.

![repobrowser4](/help/implementing/developing/tools/assets/repobrowser41.png)

### Afficher le contenu {#view-content}

Vous pouvez utiliser le navigateur de référentiels pour voir le contenu. Cliquez sur une ressource dans le volet de navigation pour ouvrir un aperçu dans la partie droite du navigateur, sous un onglet nommé en fonction de la ressource correspondante.

![repobrowser6](/help/implementing/developing/tools/assets/repobrowser61.png)

L’aperçu est disponible pour les types d’image suivants :

* apng
* avif
* gif
* jpeg
* png
* svg+xml
* webp
* bmp
* x-icon
* tiff

Ainsi que pour les types MIME textuels suivants :

* `"text/*"`
* `'application/javascript'`
* `'application/json'`
* `'application/x-sh'`

### Téléchargement de contenu {#download-content}

Vous pouvez également utiliser le navigateur de référentiel pour télécharger du contenu. Dans l’exemple ci-dessous, vous pouvez appuyer sur le lien **Télécharger** pour télécharger le `jcr:data` associée au nœud sélectionné. Cette fonctionnalité est disponible pour toutes les propriétés binaires en accédant au nœud contenant la définition de la propriété.

![repobrowser5](/help/implementing/developing/tools/assets/repobrowser52.png)
