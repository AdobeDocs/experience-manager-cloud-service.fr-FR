---
title: Gestion de projets de traduction
description: Découvrez comment créer et gérer des projets de traduction humaine et automatique dans AEM.
feature: Copie de la langue
role: Administrator
exl-id: dc2f3958-72b5-4ae3-a224-93d8b258bc80
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '3827'
ht-degree: 37%

---

# Gestion des projets de traduction {#managing-translation-projects}

Les projets de traduction permettent de gérer la traduction du contenu d’AEM. Un projet de traduction est un type d’AEM [projet](/help/sites-cloud/authoring/projects/overview.md) qui contient des ressources qui doivent être traduites dans d’autres langues. Ces ressources sont les pages et les actifs des [copies de langue](preparation.md) créées à partir du gabarit de langue.

Lorsque des ressources sont ajoutées à un projet de traduction, une tâche de traduction est créée pour ces ressources. Les tâches comportent les commandes et les informations sur le statut utilisées pour gérer les processus de traduction humaine et automatique exécutés sur les ressources.

Les projets de traduction sont des éléments dont l’exécution est longue, définis par langue et par méthode/fournisseur de traduction afin d’être en phase avec la gouvernance organisationnelle en matière d’internationalisation. Ils doivent être lancés en une seule fois, lors de la traduction initiale ou manuellement, et restent actifs pendant toute la durée des activités de mise à jour du contenu et de la traduction.

Les projets et les tâches de traduction sont créés avec des processus de préparation de la traduction. Ces processus possèdent trois options pour la traduction initiale (Créer et traduire) et les mises à jour (Mettre à jour une traduction) :

1. [Créer un projet](#creating-translation-projects-using-the-references-panel)
1. [Ajouter à un projet existant](#adding-pages-to-a-translation-project)
1. [Structure de contenu uniquement](#creating-the-structure-of-a-language-copy)

AEM détecte si un projet de traduction est créé pour la traduction initiale du contenu ou pour mettre à jour des copies de langue déjà traduites. Lorsque vous créez un projet de traduction pour une page et que vous indiquez les copies de langue pour lesquelles vous effectuez une traduction, AEM détecte si la page source existe déjà dans les copies de langue ciblées :

* **La copie de langue n’inclut pas la page :** AEM traite cette situation comme la traduction initiale. La page est copiée immédiatement dans la copie de langue et incorporée au projet. Lorsque la page traduite est importée dans AEM, AEM la copie directement dans la copie de langue.
* **La copie de langue comprend déjà la page :** AEM traite cette situation comme une traduction mise à jour. Un lancement est créé, et une copie de la page est ajoutée au lancement et incorporée au projet. Les lancements permettent de réviser les traductions mises à jour avant de les valider dans la copie de langue :

   * Lorsque la page traduite est importée dans AEM, elle remplace la page correspondante dans le lancement.
   * La page traduite ne remplace la copie de langue que lorsque le lancement est converti.

Par exemple, la racine de langue `/content/wknd/fr` est créée pour la traduction française de la langue principale `/content/wknd/en`. Il n’y a pas d’autres pages dans la copie de langue française.

* Un projet de traduction est créé pour la page `/content/wknd/en/products` et toutes les pages enfants, ciblant la copie en français. Comme la copie de langue n’inclut pas la page `/content/wknd/fr/products`, AEM copie immédiatement la page `/content/wknd/en/products` et toutes les pages enfants dans la copie de langue française. Les copies sont également incluses dans le projet de traduction.
* Un projet de traduction est créé pour la page `/content/wknd/en` et toutes les pages enfants, ciblant la copie en français. Comme la copie de langue inclut la page qui correspond à la page `/content/wknd/en` (la racine de langue), AEM copie la page `/content/wknd/en` et toutes les pages enfants et les ajoute à un lancement. Les copies sont également incluses dans le projet de traduction.

## Traduction à partir de la console Sites {#performing-initial-translations-and-updating-existing-translations}

Les projets de traduction peuvent être créés ou mis à jour directement à partir de la console Sites.

### Création de projets de traduction à l’aide du panneau Références {#creating-translation-projects-using-the-references-panel}

Créez des projets de traduction afin de pouvoir exécuter et gérer le processus pour traduire les ressources de votre gabarit de langue. Lorsque vous créez des projets, vous spécifiez la page du gabarit de langue que vous traduisez et les copies de langue pour lesquelles vous effectuez la traduction :

* La configuration du cloud de la structure d’intégration de traduction associée à la page sélectionnée détermine de nombreuses propriétés des projets de traduction, comme le processus de traduction à utiliser.
* Un projet est créé pour chaque copie de langue sélectionnée.
* Une copie de la page sélectionnée et des ressources associées est créée et ajoutée à chaque projet. Ces copies sont ensuite envoyées au fournisseur de traduction pour être traduites.

Vous pouvez spécifier que les pages enfants de la page sélectionnée soient elles aussi sélectionnées. Dans ce cas, les copies des pages enfants sont également ajoutées à chaque projet afin d’être traduites. Lorsque des pages enfants sont associées à différentes configurations de structure d’intégration de traduction, AEM crée des projets supplémentaires.

Vous pouvez également [créer manuellement des projets de traduction](#creating-a-translation-project-using-the-projects-console).

>[!NOTE]
>
>Pour créer un projet, votre compte doit être membre du groupe `project-administrators` .

### Traductions initiales et mise à jour de traductions {#initial-and-updating}

Le panneau Références indique si vous mettez à jour les copies de langue existantes ou si vous créez la première version des copies de langue. Lorsqu’il existe une copie de langue pour la page sélectionnée, l’onglet Mettre à jour les copies de langue s’affiche pour permettre d’accéder aux commandes liées au projet.

![Mise à jour des copies de langue](../assets/update-language-copies.png)

Après la traduction, vous pouvez [réviser la traduction](#reviewing-and-promoting-updated-content) avant de remplacer la copie de langue. Lorsqu’il n’existe pas copie de langue pour la page sélectionnée, l’onglet Créer et traduire s’affiche pour permettre d’accéder aux commandes liées au projet.

![Créer et traduire](../assets/create-and-translate.png) 

### Création de projets de traduction pour une nouvelle copie de langue {#create-translation-projects-for-a-new-language-copy}

1. Utilisez la console Sites pour sélectionner la page que vous ajoutez aux projets de traduction.

1. À l’aide de la barre d’outils, ouvrez le rail **Références** .

   ![Références](../assets/references.png)

1. Sélectionnez **Copies de langue**, puis sélectionnez les copies de langue pour lesquelles vous traduisez les pages source.
1. Cliquez ou appuyez sur **Créer et traduire**, puis configurez la tâche de traduction :

   * Utilisez la liste déroulante **Langues** pour sélectionner une copie de langue pour laquelle vous souhaitez traduire. Sélectionnez d’autres langues, au besoin. Les langues qui figurent dans la liste correspondent aux [racines de langue que vous avez créées](preparation.md#creating-a-language-root).
      * La sélection de plusieurs langues crée un projet avec une tâche de traduction pour chaque langue.
   * Pour traduire la page que vous avez sélectionnée et toutes les pages enfants, sélectionnez **Sélectionner toutes les sous-pages**. Pour ne traduire que la page sélectionnée, désélectionnez cette option.
   * Pour **Projet**, sélectionnez **Créer un(s) projet(s) de traduction**.
   * Si vous le souhaitez pour **Principal du projet**, sélectionnez un projet à partir duquel hériter des rôles utilisateur et des autorisations.
   * Dans **Titre**, saisissez un nom pour le projet.

   ![Créer un projet de traduction](../assets/create-translation-project.png)

1. Cliquez ou appuyez sur **Créer**.

### Création de projets de traduction pour une copie de langue existante {#create-translation-projects-for-an-existing-language-copy}

1. Utilisez la console Sites pour sélectionner la page que vous ajoutez aux projets de traduction.

1. À l’aide de la barre d’outils, ouvrez le rail **Références** .

   ![Références](../assets/references.png)

1. Sélectionnez **Copies de langue**, puis sélectionnez les copies de langue pour lesquelles vous traduisez les pages source.
1. Cliquez ou appuyez sur **Mettre à jour les copies de langue**, puis configurez la tâche de traduction :

   * Pour traduire la page que vous avez sélectionnée et toutes les pages enfants, sélectionnez **Sélectionner toutes les sous-pages**. Pour ne traduire que la page sélectionnée, désélectionnez cette option.
   * Pour **Projet**, sélectionnez **Créer un(s) projet(s) de traduction**.
   * Si vous le souhaitez pour **Principal du projet**, sélectionnez un projet à partir duquel hériter des rôles utilisateur et des autorisations.
   * Dans **Titre**, saisissez un nom pour le projet.

   ![Créer un projet pour mettre à jour les copies de langue](../assets/create-update-language-copies-project.png)

1. Cliquez ou appuyez sur **Créer**.

### Ajout de pages à un projet de traduction {#adding-pages-to-a-translation-project}

Après avoir créé un projet de traduction, vous pouvez utiliser le rail **Ressources** pour ajouter des pages au projet. Il est utile d’ajouter des pages lorsque vous incorporez des pages de différentes branches dans le même projet.

Lorsque vous ajoutez des pages à un projet de traduction, les pages sont incorporées à une nouvelle tâche de traduction. Vous pouvez également [ajouter des pages à une tâche existante](#adding-pages-assets-to-a-translation-job).

Comme lors de la création d’un projet, lorsque vous ajoutez des pages, des copies des pages sont ajoutées à un lancement, si nécessaire, afin d’éviter de remplacer des copies de langue. (Voir [Création de projets de traduction pour une copie de langue existante](#performing-initial-translations-and-updating-existing-translations).)

1. Utilisez la console Sites pour sélectionner la page que vous ajoutez au projet de traduction.

1. À l’aide de la barre d’outils, ouvrez le rail **Références** .

   ![Références](../assets/references.png)

1. Sélectionnez **Copies de langue**, puis sélectionnez les copies de langue pour lesquelles vous traduisez les pages source.

   ![Mise à jour des copies de langue à partir du rail de références](../assets/update-language-copies-references.png)

1. Cliquez ou appuyez sur **Mettre à jour les copies de langue**, puis configurez les propriétés :

   * Pour traduire la page que vous avez sélectionnée et toutes les pages enfants, sélectionnez **Sélectionner toutes les sous-pages**. Pour ne traduire que la page sélectionnée, désélectionnez cette option.
   * Pour **Projet**, sélectionnez **Ajouter au projet de traduction existant**.
   * Sélectionnez le projet dans **Projet de traduction existant**.

   >[!NOTE]
   >
   >La langue cible définie dans le projet de traduction doit correspondre au chemin d’accès de la copie de langue comme indiqué dans le rail de références.

1. Cliquez ou appuyez sur **Mettre à jour**.

### Création de la structure d’une copie de langue {#creating-the-structure-of-a-language-copy}

Il est possible de créer uniquement la structure de la copie de langue, ce qui permet de copier le contenu et les modifications structurelles dans le gabarit de langue vers des copies de langue (non traduites). Il n’est pas lié à une tâche ou à un projet de traduction. Vous pouvez l’utiliser pour préserver la synchronisation des gabarits de langue, même sans traduction.

Remplissez la copie de langue afin qu’elle contienne le contenu de la langue principale que vous traduisez. Avant de renseigner votre copie de langue, [vous devez avoir créé la racine de langue](preparation.md#creating-a-language-root) de la copie de langue.

1. Utilisez la console Sites pour sélectionner la racine de langue de la langue principale que vous utilisez comme source.
1. Ouvrez le rail Références en cliquant ou en appuyant sur **Références** dans la barre d’outils.

   ![Références](../assets/references.png)

1. Sélectionnez **Copies de langue**, puis sélectionnez les copies de langue à renseigner.

   ![Sélection de copies de langue](../assets/language-copy-structure-select.png)

1. Cliquez ou appuyez sur **Mettre à jour les copies de langue** pour afficher les outils de traduction et configurer les propriétés :

   * Sélectionnez l’option **Sélectionner toutes les sous-pages**.
   * Pour **Projet**, sélectionnez **Créer uniquement la structure**.

   ![Structure uniquement](../assets/language-copy-structure-only.png)

1. Cliquez ou appuyez sur **Mettre à jour**.

### Mise à jour de la mémoire de traduction {#updating-translation-memory}

Les modifications manuelles du contenu traduit peuvent être synchronisées à nouveau dans le système de gestion de traduction (TMS) pour entraîner sa mémoire de traduction.

1. Dans la console Sites, après avoir mis à jour le contenu textuel dans une page traduite, sélectionnez **Mettre à jour la mémoire de traduction**.
1. Un mode Liste affiche côte à côte une comparaison de la source et de la traduction pour chaque composant de texte qui a été modifié. Sélectionnez les mises à jour de traduction qui doivent être synchronisées avec la mémoire de traduction, puis sélectionnez **Mettre à jour la mémoire**.

![Comparaison des modifications pour la mémoire de traduction](../assets/update-translation-memory-compare.png)

AEM enverra les chaînes sélectionnées vers le système de gestion de traduction.

### Vérification du statut de traduction d’une page {#check-translation-status}

Une propriété peut être sélectionnée dans la vue de liste de la console Sites qui indique si une page a été traduite, est en traduction ou n’a pas encore été traduite.

1. Dans la console du site, passez en [mode Liste.](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources)
1. Appuyez ou cliquez sur **Paramètres d’affichage** dans la liste déroulante des vues.
1. Dans la boîte de dialogue, vérifiez la propriété **Traduite** et appuyez ou cliquez sur **Mettre à jour**.

La console Sites affiche désormais la colonne **Traduit** indiquant l’état de traduction des pages répertoriées.

![Etat de traduction en mode Liste](../assets/translation-status-list-view.png)

## Gestion des projets de traduction à partir de la console de projets

De nombreuses tâches de traduction et options avancées sont accessibles dans la console Projets.

### Présentation de la console Projets

Les projets de traduction d’ AEM utilisent la [console de projets d’AEM standard.](/help/sites-cloud/authoring/projects/overview.md) Si vous ne connaissez pas AEM projets, consultez cette documentation.

Comme tout autre projet, un projet de traduction est constitué de mosaïques qui présentent un aperçu des tâches du projet.

![Projet de traduction](../assets/translation-project.png)

* **Résumé**  - Aperçu du projet
* **Tâches**  - Une ou plusieurs tâches de traduction
* **Équipe**  : utilisateurs collaborant sur le projet de traduction
* **Tâches**  : éléments qui doivent être remplis dans le cadre de l’effort de traduction.

Utilisez les commandes et les boutons de points de suspension en haut et en bas des mosaïques (respectivement) pour accéder aux commandes et aux options des différentes mosaïques.

![Bouton Commandes](../assets/context.png)

![Bouton Ellipsis](../assets/ellipsis.png)

### Création d’un projet de traduction à l’aide de la console Projets {#creating-a-translation-project-using-the-projects-console}

Vous pouvez créer manuellement un projet de traduction si vous préférez utiliser la console Projets au lieu de la console Sites.

>[!NOTE]
>
>Pour créer un projet, votre compte doit être membre du groupe `project-administrators` .

Lorsque vous créez manuellement un projet de traduction, vous devez fournir des valeurs pour les propriétés associées à la traduction ci-dessous en complément des [propriétés de base](/help/sites-cloud/authoring/projects/managing.md#creating-a-project) :

* **Nom** : nom du projet
* **Langue source** : langue du contenu source
* **Langue cible :**  langue ou langues dans lesquelles le contenu est traduit.
   * Si plusieurs langues sont sélectionnées, une tâche est créée pour chaque langue du projet.
* **Méthode de conversion**** : sélectionnez Traduction humaine pour indiquer que la traduction doit être effectuée manuellement.**

1. Dans la barre d’outils de la console Projets, cliquez ou appuyez sur **Créer**.
1. Sélectionnez le modèle **Projet de traduction** , puis cliquez ou appuyez sur **Suivant**.
1. Saisissez les valeurs de l’onglet des propriétés **De base** .
1. Cliquez ou appuyez sur **Avancé** et indiquez des valeurs pour les propriétés liées à la traduction.
1. Cliquez ou appuyez sur **Créer**. Dans la boîte de confirmation, cliquez ou appuyez sur **Terminé** pour revenir à la console Projets, ou cliquez ou appuyez sur **Ouvrir le projet** pour ouvrir et commencer à gérer le projet.

### Ajout de pages et de ressources à une tâche de traduction {#adding-pages-assets-to-a-translation-job}

Vous pouvez ajouter des pages, des ressources ou des balises à la tâche de traduction de votre projet de traduction. Pour ajouter des pages ou des ressources :

1. Au bas de la mosaïque de la tâche de traduction de votre projet de traduction, cliquez ou appuyez sur les points de suspension.

   ![Mosaïque de tâche de traduction](../assets/translation-job.png)

1. Dans la fenêtre suivante, cliquez ou appuyez sur le bouton **Ajouter** dans la barre d’outils, puis sélectionnez **Ressources/Pages**.

   ![Ajouter des pages](../assets/add-to-project.png)

1. Dans la fenêtre modale, sélectionnez l’élément le plus en haut de la branche à ajouter, puis cliquez ou appuyez sur l’icône en forme de coche. La sélection multiple est activée dans cette fenêtre.

   ![Sélectionner des pages](../assets/select-pages.png)

1. Vous pouvez également choisir l’icône de recherche pour rechercher des pages ou des ressources à ajouter à la tâche de traduction.

   ![Recherche de contenu](../assets/search-for-content.png)

1. Une fois la sélection effectuée, appuyez ou cliquez sur **Sélectionner**. Vos pages et/ou ressources sont ajoutées à la tâche de traduction.

>[!TIP]
>
>Cette méthode ajoute des pages/ressources et leurs enfants au projet. Sélectionnez **Ressource/Page (sans enfants)** si vous souhaitez uniquement ajouter les parents.

### Ajout de balises à une tâche de traduction {#adding-tags-to-a-translation-job}

Vous pouvez ajouter des balises à un projet de traduction comme [la manière dont vous ajoutez des ressources et des pages à un projet.](#adding-pages-assets-to-a-translation-job) Sélectionnez simplement  **** Balises sous le  **** menu Ajouter , puis procédez comme suit.

### Affichage des détails d’un projet de traduction {#seeing-translation-project-details}

Les propriétés du projet de traduction sont accessibles à partir du bouton représentant des points de suspension de la mosaïque Résumé du projet. Outre les [informations génériques sur le projet](/help/sites-cloud/authoring/projects/overview.md#project-info), les propriétés du projet de traduction contiennent des informations spécifiques à la traduction.

Dans votre projet de traduction, cliquez ou appuyez sur les points de suspension en bas de la mosaïque Résumé de traduction. La plupart des propriétés spécifiques au projet se trouvent dans l’onglet **Avancé**.

* **Langue source :** langue des pages en cours de traduction.
* **Langue cible :**  langue ou langues dans lesquelles les pages sont traduites.
* **Configuration du cloud :** configuration du cloud pour le connecteur du service de traduction utilisé pour le projet.
* **Méthode de traduction :** processus de traduction, traduction  **humaine** ou  **traduction automatique**
* **Fournisseur de traduction :** fournisseur de services de traduction qui effectue la traduction
* **Catégorie de contenu :**  (traduction automatique) catégorie de contenu utilisée pour la traduction.
* **Informations d’identification du fournisseur de traduction :**  informations d’identification pour se connecter au fournisseur
* **Promouvoir automatiquement les lancements de traduction :** après réception du contenu traduit, les lancements de traduction sont automatiquement promus.
   * **Supprimer le lancement après la promotion :** si les lancements de traduction sont automatiquement promus, supprimez le lancement après la promotion.
* **Approuver automatiquement les traductions :** après réception du contenu traduit, les tâches de traduction sont automatiquement approuvées.
* **Répéter la traduction :**  configurez l’exécution récurrente d’un projet de traduction en sélectionnant la fréquence à laquelle le projet va créer et exécuter automatiquement des tâches de traduction.

Lorsqu’un projet est créé à l’aide du rail de références d’une page, ces propriétés sont automatiquement configurées en fonction des propriétés de la page source.

![Propriétés du projet de traduction](../assets/translation-project-properties.png)

### Suivi du statut d’une tâche de traduction {#monitoring-the-status-of-a-translation-job}

La mosaïque de tâche de traduction d’un projet de traduction indique l’état d’une tâche de traduction, ainsi que le nombre de pages et de ressources de la tâche.

![Tâche de traduction](../assets/translation-job.png)

Le tableau ci-dessous décrit les différents statuts qu’une tâche ou un élément de la tâche peut avoir :

| État | Description |
|---|---|
| **Draft** | La tâche de traduction n’a pas été lancée. Les tâches de traduction sont à l’état **Version préliminaire**** lors de leur création. |
| **Envoyé** | Les fichiers de la tâche de traduction ont cet état lorsqu’ils ont été envoyés avec succès au service de traduction. Cet état peut se produire après l’émission de la commande **Portée de la requête** ou **Démarrer**. |
| **Portée demandée** | Pour le processus de traduction humaine, les fichiers de la tâche ont été envoyés au fournisseur de traduction pour la définition de la portée. Cet état s’affiche une fois la commande **Portée de la requête** lancée. |
| **Portée terminée** | Le fournisseur a défini la portée de la tâche de traduction. |
| **Engagé pour la traduction** | Le propriétaire du projet a accepté la portée. Ce statut indique que le fournisseur de traduction doit commencer à traduire les fichiers de la tâche. |
| **Traduction en cours** | Pour une tâche, la traduction d’un ou de plusieurs fichiers de la tâche n’est pas encore terminée. Pour un élément de la tâche, l’élément est en cours de traduction. |
| **Traduit** | Pour une tâche, la traduction de tous les fichiers de la tâche est terminée. Pour un élément de la tâche, l’élément est traduit. |
| **Prêt pour la révision** | L’élément de la tâche est traduit et le fichier a été importé dans AEM. |
| **Terminé** | Le propriétaire du projet a indiqué que le contrat de traduction est terminé. |
| **Annuler** | Indique que le fournisseur de traduction doit arrêter de travailler sur une tâche de traduction. |
| **Mise à jour d’erreur** | Une erreur s’est produite lors du transfert de fichiers entre AEM et le service de traduction. |
| **État inconnu** | Une erreur inconnue s’est produite. |

Pour afficher le statut des différents fichiers de la tâche, cliquez ou appuyez sur le bouton de sélection de la mosaïque.

### Définition du délai des tâches de traduction {#setting-the-due-date-of-translation-jobs}

Spécifiez la date à laquelle le fournisseur de traduction doit renvoyer les fichiers traduits. La définition du délai ne fonctionne correctement que lorsque le fournisseur de traduction auquel vous faites appel prend en charge cette fonctionnalité.

1. Cliquez ou appuyez sur les points de suspension en bas de la mosaïque Résumé de traduction.

   ![Mosaïque Résumé de traduction](../assets/translation-summary-tile.png)

1. Dans l’onglet **Simple** , utilisez le sélecteur de date de la propriété **Date d’échéance** pour sélectionner la date d’échéance.

   ![Propriétés du projet de traduction](../assets/translation-project-properties-basic.png)

1. Cliquez ou appuyez sur **Enregistrer et fermer**.

### Définition de la portée d’une tâche de traduction {#scoping-a-translation-job}

Définissez la portée de la tâche de traduction afin que le prestataire de services de traduction vous fournisse une estimation du coût de la traduction. Lorsque vous définissez la portée d’une tâche, les fichiers source sont envoyés au fournisseur de traduction, qui compare le texte à son pool de traductions stockées (mémoire de traduction). En règle générale, la portée est le nombre de mots à traduire.

Pour plus d’informations sur les résultats de la définition de la portée, contactez le fournisseur de traduction.

>[!NOTE]
>
>L’application de plage est facultative et ne s’applique qu’à la traduction humaine. Vous pouvez commencer une tâche de traduction sans définir la portée.

Lorsque vous définissez la portée d’une tâche de traduction, le statut de la tâche est **Portée demandée**. Lorsque le fournisseur de traduction renvoie la définition de la portée, le statut devient **Portée terminée**. Une fois l’application de plage terminée, vous pouvez utiliser la commande **Afficher la portée** pour consulter les résultats de l’application de plage.

La définition de la portée ne fonctionne correctement que lorsque le fournisseur de traduction auquel vous faites appel prend en charge cette fonctionnalité.

1. Dans la console Projets, ouvrez votre projet de traduction.
1. Sur le titre de la tâche de traduction, appuyez ou cliquez sur le menu Commandes, puis appuyez ou cliquez sur **Portée de la requête**.
1. Lorsque l’état de la tâche passe à **Portée terminée**, cliquez ou appuyez sur le menu Commandes, puis cliquez ou appuyez sur **Afficher la portée**.

### Démarrage des tâches de traduction {#starting-translation-jobs}

Commencez une tâche de traduction pour traduire les pages source dans la langue cible. La traduction est effectuée en fonction des valeurs de propriété de la mosaïque Résumé de traduction.

Vous pouvez démarrer une tâche individuelle dans le projet.

1. Dans la console Projets, ouvrez le projet de traduction.
1. Sur la mosaïque de la tâche de traduction, cliquez ou appuyez sur le menu Commandes, puis cliquez ou appuyez sur **Démarrer**.
1. Dans la boîte de dialogue d’action qui confirme le début de la traduction, cliquez ou appuyez sur **Fermer**.

Une fois la tâche de traduction lancée, la mosaïque de la tâche de traduction affiche la traduction à l’état **En cours** .

Vous pouvez également lancer toutes les tâches de traduction d’un projet.

1. Dans la console du projet, sélectionnez le projet de traduction.
1. Dans la barre d’outils, appuyez ou cliquez sur **Démarrer la tâche de traduction**.
1. Dans la boîte de dialogue, passez en revue la liste des tâches qui seront démarrées, puis confirmez avec **Démarrer** ou abandonnez avec **Annuler**.

### Annulation d’une tâche de traduction {#canceling-a-translation-job}

Annulez une tâche de traduction pour suspendre le processus de traduction et empêcher le fournisseur de traduction d’effectuer d’autres traductions. Vous pouvez annuler une tâche lorsque la tâche possède le statut **Engagé pour traduction** ou **Traduction en cours**.

1. Dans la console Projets, ouvrez le projet de traduction.
1. Sur la mosaïque de la tâche de traduction, cliquez ou appuyez sur le menu Commandes, puis cliquez ou appuyez sur **Annuler**.
1. Dans la boîte de dialogue d’action qui confirme l’annulation de la traduction, cliquez ou appuyez sur **OK**.

### Processus d’acceptation et de rejet {#accept-reject-workflow}

Lorsque le contenu revient après la traduction et est à l’état **Prêt pour la révision** , vous pouvez passer à la tâche de traduction et accepter/rejeter le contenu.

Si vous sélectionnez **Rejeter la traduction**, vous avez la possibilité d’ajouter un commentaire.

Le rejet du contenu le renvoie au fournisseur de traduction où il pourra voir le commentaire.

### Fin et archivage des tâches de traduction {#completing-and-archiving-translation-jobs}

Effectuez une tâche de traduction après avoir révisé les fichiers traduits du fournisseur.

1. Dans la console Projets, ouvrez le projet de traduction.
1. Sur la mosaïque de la tâche de traduction, cliquez ou appuyez sur le menu Commandes, puis cliquez ou appuyez sur **Terminer**.
1. La tâche a désormais le statut **Complète**.

Pour les workflows de traduction humaine, la réalisation d’une traduction indique au fournisseur que le contrat de traduction a été rempli et qu’il doit enregistrer la traduction dans sa mémoire de traduction.

Archivez une tâche de traduction une fois qu’elle est terminée et que vous n’avez plus besoin de consulter les détails du statut de cette tâche.

1. Dans la console Projets, ouvrez le projet de traduction.
1. Sur la mosaïque de la tâche de traduction, cliquez ou appuyez sur le menu Commandes, puis cliquez ou appuyez sur **Archiver**.

Lorsque vous archivez la tâche, la mosaïque de la tâche de traduction est supprimée du projet.

## Révision et utilisation du contenu traduit {#reviewing-and-promoting-updated-content}

Vous pouvez utiliser la console Sites pour examiner le contenu, comparer des copies de langue et activer le contenu.

### Conversion de contenu mis à jour {#promoting-updated-content}

Lorsque le contenu est traduit pour une copie de langue existante, révisez les traductions, apportez-y des modifications, si nécessaire, puis convertissez les traductions pour les déplacer vers la copie de langue. Vous pouvez consulter les fichiers traduits lorsque la tâche de traduction affiche l’état **Prêt pour la révision** .

![Traitement prêt pour la révision](../assets/job-ready-for-review.png)

1. Sélectionnez la page dans le gabarit de langue, cliquez ou appuyez sur **Références**, puis cliquez ou appuyez sur **Copies de langue**.
1. Cliquez ou appuyez sur la copie de langue à réviser.

   ![Copie de langue prête à être examinée](../assets/language-copy-ready-for-review.png)

1. Cliquez ou appuyez sur **Launch** pour afficher les commandes liées au lancement.

   ![Lancement](../assets/language-copy-launch.png)

1. Pour ouvrir la copie de lancement de la page afin de réviser et modifier le contenu, cliquez sur **Ouvrir la page**.
1. Après avoir examiné le contenu et apporté les modifications nécessaires, cliquez sur **Convertir** pour promouvoir la copie de lancement.
1. Sur la page **Convertir le lancement** , spécifiez les pages à convertir, puis cliquez ou appuyez sur **Convertir**.

### Comparaison des copies de langue {#comparing-language-copies}

Pour comparer des copies de langue au gabarit de langue :

1. Dans la console Sites, accédez à la copie de langue à comparer.
1. Ouvrez le rail [Références.](/help/sites-cloud/authoring/getting-started/basic-handling.md#references)
1. Sous l’en-tête **Copies**, sélectionnez **Copies de langue.**
1. Sélectionnez votre copie de langue spécifique, puis cliquez sur **Comparer au Principal** ou **Comparer au précédent**, le cas échéant.

   ![Comparaison de copies de langue](../assets/language-copy-compare.png)

1. Les deux pages (de lancement et source) s’ouvrent côte à côte.
   * Pour des informations complètes sur l’utilisation de cette fonction, consultez [Différence entre les pages](/help/sites-cloud/authoring/features/page-diff.md).

## Importation et exportation de tâches de traduction {#import-export}

Bien qu’AEM propose un certain nombre de solutions et d’interfaces de traduction, il est également possible d’importer et d’exporter des informations de tâche de traduction manuellement.

### Exportation d’une tâche de traduction {#exporting-a-translation-job}

Vous pouvez télécharger le contenu d’une tâche de traduction, par exemple, pour l’envoyer à un fournisseur de traduction qui n’est pas intégré à AEM par le biais d’un connecteur ou pour réviser le contenu.

1. Dans le menu déroulant de la mosaïque de la tâche de traduction, cliquez ou appuyez sur **Exporter**.
1. Dans la boîte de dialogue, cliquez ou appuyez sur **Télécharger le fichier exporté** et, si nécessaire, utilisez la boîte de dialogue du navigateur Web pour enregistrer le fichier.
1. Dans la boîte de dialogue, cliquez ou appuyez sur **Fermer**.

### Importation d’une tâche de traduction {#importing-a-translation-job}

Vous pouvez importer du contenu traduit dans AEM, par exemple, lorsque votre fournisseur de traduction vous l’envoie, car il n’est pas intégré à AEM par le biais d’un connecteur.

1. Dans le menu déroulant de la mosaïque de la tâche de traduction, cliquez ou appuyez sur **Importer**.
1. Utilisez la boîte de dialogue du navigateur web pour sélectionner le fichier à importer.
1. Dans la boîte de dialogue, cliquez ou appuyez sur **Fermer**.
