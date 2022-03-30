---
title: Explorateur de référentiels
seo-title: Repository Browser
description: L’explorateur de référentiel fournit une vue en lecture seule dans le référentiel pour tous les environnements sur les niveaux d’auteur, de publication et d’aperçu.
seo-description: The repository browser provides a read-only view into the repository for all environments on author, publish, and preview tiers.
exl-id: 22473a97-8f7b-4014-b885-1233116aeda6
source-git-commit: db70857458722f870dad37ac2bee6a19ef54171e
workflow-type: tm+mt
source-wordcount: '814'
ht-degree: 3%

---

# Explorateur de référentiels {#repository-browser}

>[!NOTE]
>
>Le navigateur de référentiel est disponible sur AEM versions 6582 et ultérieures.

>[!INFO]
>
>Vous pouvez également regarder [ce clip](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/repository-browser.html) pour une présentation vidéo rapide sur l’utilisation du navigateur de référentiel pour déboguer AEM as a Cloud Service.

## Présentation {#introduction}

L’explorateur de référentiel est un outil de développement qui fournit une vue en lecture seule du référentiel pour tous les environnements sur les niveaux de création, de publication et d’aperçu. Il est conçu pour faciliter l’affichage de la structure de contenu afin de faciliter l’affichage ou le débogage du contenu.

Accessible à partir de Developer Console, elle peut être utilisée pour parcourir le référentiel d’une instance d’auteur ou de publication pour un environnement sélectionné.

### Conditions préalables d’accès {#access-prerequisites}

Ces conditions suivantes doivent être remplies pour accéder au navigateur Developer Console ou Repository

Pour accéder à Developer Console :

* Pour les programmes de production, les utilisateurs doivent avoir la variable **Cloud Manager - Rôle de développeur** dans le Admin Console
* Pour les programmes Sandbox, il est disponible pour tout utilisateur disposant d’un profil de produit qui lui donne accès à AEM as a Cloud Service.

Pour accéder à l’explorateur de référentiel :

* Les utilisateurs doivent avoir la variable **Cloud Manager - Développeur** Rôle dans le Admin Console pour afficher les instances de création et de publication.
* En outre, pour l’auteur, les utilisateurs disposant du profil produit des utilisateurs AEM peuvent afficher le navigateur du référentiel avec un accès en lecture minimal ; les autorisations de l’utilisateur sont respectées lors de la navigation dans le référentiel. Les utilisateurs disposant du profil produit Administrateurs AEM peuvent afficher le navigateur de référentiel avec un accès en lecture complet.

Pour plus d’informations sur la configuration des autorisations utilisateur, voir [Documentation de Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/requirements/setting-up-users-and-roles.html?lang=fr).

### Lancement de l’explorateur de référentiels {#launching-the-repository-browser}

Le navigateur de référentiel peut être lancé en suivant les étapes ci-dessous.

1. Dans Cloud Manager, cliquez sur les trois points en regard de l’environnement de votre choix, puis sélectionnez **Developer Console**

   ![repobrowser1](/help/implementing/developing/tools/assets/repobrowser1.png)

1. Cliquez ensuite sur le **Explorateur de référentiels** tab
1. Sélectionnez une capsule correspondant à l’auteur, à la publication ou à la prévisualisation en cliquant sur le bouton **Capsule** liste déroulante

   ![repobrowser2](/help/implementing/developing/tools/assets/repobrowser2.png)

1. Lancez l’explorateur de référentiel en cliquant sur la **Ouvrir l’explorateur de référentiels** plus bas. Le navigateur correspondant à une instance représentative (pod) pour le niveau sélectionné est ainsi lancé. Le navigateur correspondant à une instance représentative (pod) pour le niveau sélectionné est ainsi lancé. Notez que vous ne pouvez pas contrôler la capsule spécifique pour ce niveau lancé.

## Fonctions {#features}

### Navigation dans la hiérarchie {#navigate-the-hierarchy}

Vous pouvez utiliser le volet de navigation de gauche pour vous ingérer dans la hiérarchie du contenu. Cliquez sur chaque dossier ou noeud pour afficher ses enfants. La structure de dossiers reflète l’arborescence de ressources Sling, qui est un super-ensemble de l’arborescence de noeuds JCR.

![repobrowser3](/help/implementing/developing/tools/assets/repobrowser3.png)

Pour la publication, par défaut, l’explorateur de référentiel affiche uniquement le contenu public, de sorte que certains dossiers comme `/conf` ou `/home` ne sera pas visible.

Pour rendre ces emplacements visibles, vous devez suivre la procédure ci-dessous.

1. Cliquez sur les trois points en regard de l’environnement de votre choix et sélectionnez **Gérer l’accès**

   ![repobrowser7](/help/implementing/developing/tools/assets/repobrowser7.png)

1. Recherchez votre instance de publication, puis cliquez dessus.

   ![repobrowser8](/help/implementing/developing/tools/assets/repobrowser8.png)

1. Créez un profil de produit pour les administrateurs de publication. Dans l’exemple ci-dessous, il est appelé **DEV - Publication des administrateurs AEM**

   ![repobrowser9](/help/implementing/developing/tools/assets/repobrowser9.png)

1. Ajoutez les utilisateurs appropriés, correspondant à ceux qui doivent pouvoir naviguer dans le navigateur du référentiel de publication avec un accès complet, au nouveau profil de produit.

   ![repobrowser10](/help/implementing/developing/tools/assets/repobrowser10.png)

1. Patientez quelques minutes, puis ouvrez le **Auteur AEM** console
1. Ajoutez le groupe correspondant au nouveau profil de produit en tant que membre du groupe administrateurs . Pour ce faire, cliquez sur **Outils - Sécurité - Groupes sur l’auteur**, puis cliquez sur le bouton **administrateurs** groupe. Ajoutez ensuite le groupe comme illustré ci-dessous.

   ![repobrowser11](/help/implementing/developing/tools/assets/repobrowser11.png)

1. Activez la variable **administrateurs** et le nouveau **DEV - Publication des administrateurs AEM** groupe afin qu’ils soient disponibles lors de la publication ;

   ![repobrowser12](/help/implementing/developing/tools/assets/repobrowser12.png)

1. En tant que bonne pratique de sécurité, supprimez la nouvelle **DEV - Publication des administrateurs AEM** du groupe administrateurs sur **author** le nouveau groupe est donc isolé pour la publication.

   ![repobrowser13](/help/implementing/developing/tools/assets/repobrowser13.png)

1. Lors de l’accès au navigateur de référentiel pour une instance de publication, tous les dossiers sont visibles, y compris `/home` et `/conf`.

### Afficher les propriétés JCR {#view-jcr-properties}

Cliquez sur un noeud pour afficher ses propriétés JCR dans le volet de droite du navigateur de navigation. Vous trouverez ci-dessous un exemple de la fonction `experience-fragments` noeud .

![repobrowser4](/help/implementing/developing/tools/assets/repobrowser41.png)

### Afficher le contenu {#view-content}

Vous pouvez utiliser l’explorateur de référentiel pour afficher le contenu en cliquant sur une ressource dans le volet de navigation. Un aperçu s’ouvre alors sur le côté droit du navigateur, sous un onglet nommé en fonction de la ressource correspondante.

![repobrowser6](/help/implementing/developing/tools/assets/repobrowser61.png)

L’aperçu est actuellement disponible pour les types d’image dans la liste ci-dessous :

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

Et pour les types MIME textuels suivants :

* `"text/*"`
* `'application/javascript'`
* `'application/json'`
* `'application/x-sh'`

### Télécharger le contenu {#download-content}

Vous pouvez également utiliser l’explorateur de référentiel pour télécharger du contenu. Dans l’exemple ci-dessous, vous pouvez appuyer sur la touche **télécharger** lien pour télécharger le `jcr:data` associée au noeud sélectionné. Cette fonctionnalité est disponible pour toutes les propriétés binaires en accédant au noeud contenant la définition de propriété.

![repobrowser5](/help/implementing/developing/tools/assets/repobrowser52.png)
