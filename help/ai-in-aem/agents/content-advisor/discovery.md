---
title: Tâche de découverte de contenu
description: Découvrez comment utiliser la tâche de découverte de contenu pour diffuser du contenu AEM pertinent à la demande par le biais d’invites naturelles et conversationnelles afin d’offrir une expérience de découverte rationalisée et sans clic.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Architect, Developer
exl-id: 676300cd-b799-4c53-a58e-043e58a2cbc5
source-git-commit: 157c5e442194931c7a34499bb6153141325393ca
workflow-type: tm+mt
source-wordcount: '1313'
ht-degree: 1%

---


# Tâche de découverte de contenu {#discovery-job}

Dans le cadre d’AEM [Agent du gestionnaire de contenu](/help/ai-in-aem/agents/content-advisor/overview.md) la tâche de découverte de contenu fournit du contenu AEM à la demande par le biais d’invites naturelles et conversationnelles pour une expérience de découverte rationalisée et sans clic. Il effectue des recherches intelligentes dans Assets, les fragments de contenu et les Forms adaptatifs pour fournir des ressources pertinentes telles que des images, des vidéos, des documents PDF, des articles et des modèles de formulaire. Le langage naturel vous permet de rechercher du contenu sans créer de requêtes complexes ni appliquer de filtres dans l’interface d’AEM Assets. En fonction de votre invite, la tâche renvoie les résultats traités, ainsi que les métadonnées de ressource et les URL de diffusion, prêts à être incorporés dans d’autres applications.

Voici quelques-uns des principaux avantages de la tâche de découverte de contenu :

* **Découverte de contenu unifié** : accédez à tous les types de contenu AEM, tels que les images, les vidéos, les documents, les articles et les formulaires PDF, à partir d’une seule interface de conversation.

* **Planification rapide des campagnes** : collectez rapidement des visuels et des formulaires pour les campagnes marketing sur les canaux e-mail, web et sociaux.

* **Productivité améliorée** : réduisez le temps passé à parcourir les référentiels ou à filtrer les métadonnées par le biais d’une recherche automatisée basée sur l’intention.

* **Utilisation cohérente du contenu** : permet de réutiliser les ressources et fragments approuvés, en préservant la cohérence de la marque sur l’ensemble des canaux.

>[!VIDEO](https://video.tv.adobe.com/v/3479983)

>[!IMPORTANT]
>
>Les réponses générées par l&#39;IA peuvent être inexactes ou trompeuses. Assurez-vous de vérifier les correctifs et les réponses suggérés.
>
>Consultez également les [instructions d’utilisation de l’IA générative de Adobe Experience Cloud.](https://www.adobe.com/fr/legal/licenses-terms/adobe-dx-gen-ai-user-guidelines.html)

## Compétences {#skills-discovery-agent}

La tâche de découverte de contenu fournit les compétences suivantes :

* **Découverte de contenu en langage naturel**\
  La tâche de découverte de contenu permet aux utilisateurs et utilisatrices de rechercher des ressources, des fragments de contenu et des formulaires adaptatifs pertinents dans Adobe Experience Manager (AEM) à l’aide d’invites simples en langage naturel, sans nécessiter de requêtes de recherche complexes.

* **Découverte de ressources basée sur les balises**

  La tâche de découverte de contenu utilise des invites en langage naturel pour rechercher des ressources associées à des balises spécifiques dans le référentiel AEM, ce qui permet aux utilisateurs d&#39;accéder rapidement au contenu, organisé ou non selon la taxonomie de l&#39;organisation.

* **Découverte de contenu basé sur des dossiers :**\
  La tâche de découverte de contenu peut identifier des ressources en interprétant des invites en langage naturel qui font référence à des noms de dossier dans AEM. Les utilisateurs peuvent simplement mentionner le dossier dans leur invite, sans avoir à parcourir manuellement le référentiel, ce qui réduit considérablement le nombre de clics nécessaires pour localiser le contenu approprié.

## Personnes {#personas-content-discovery}

### Responsables de campagne {#campaign-managers}

La tâche de découverte de contenu permet aux responsables de campagne d’identifier et de réutiliser rapidement du contenu fiable et hautement performant à des fins d’idéation.

### Marketeurs de canaux {#channel-marketers}

La tâche de découverte de contenu permet aux spécialistes du marketing des canaux de rechercher efficacement les ressources appropriées afin de créer des expériences multicanaux cohérentes.

### Bibliothécaires DAM {#dam-librarians}

Les bibliothécaires de la gestion des ressources numériques peuvent signaler les ressources qui ne respectent pas les normes de métadonnées définies par l’organisation, ce qui permet une gouvernance cohérente et garantit que les ressources restent complètes et prêtes à être utilisées sur l’ensemble des canaux.

### Agences et partenaires {#agencies-partners}

Les agences et les partenaires peuvent facilement rechercher des ressources approuvées par la marque dans Content Hub et les réutiliser pour accélérer le travail créatif tout en restant conformes aux normes de la marque.

## Accès {#access}

Vous pouvez accéder au traitement de découverte de contenu dans AEM via l’assistant d’IA. Connectez-vous à [`experience.adobe.com`](https://experience.adobe.com) et commencez à interagir avec l’assistant AI en spécifiant votre invite en langage naturel à l’aide de la zone de recherche :

![Accéder à la tâche de découverte de contenu](/help/ai-in-aem/agents/content-advisor/assets/access-discovery-agent.png)

Pour plus d’informations sur le point d’entrée MCP permettant d’accéder au traitement de découverte de contenu, contactez l’assistance Adobe.

## Cas d’utilisation courants et exemples d’invites {#use-cases-prompts}

### Assets {#discovery-agent-use-cases-assets}

**Découverte de ressources basée sur les balises**

La tâche de découverte de contenu utilise des invites en langage naturel pour rechercher des ressources associées à des balises spécifiques dans le référentiel AEM, ce qui permet aux utilisateurs d&#39;accéder rapidement au contenu organisé en fonction de la taxonomie de leur entreprise.

Exemple d’invite :

Afficher les images balisées `office` dans le dossier `WKND`.

**Découverte de contenu basé sur des dossiers :**\
La tâche de découverte de contenu peut identifier des ressources en interprétant des invites en langage naturel qui font référence à des noms de dossier dans AEM. Les utilisateurs peuvent simplement mentionner le dossier dans leur invite, sans avoir à parcourir manuellement le référentiel, ce qui réduit considérablement le nombre de clics nécessaires pour localiser le contenu approprié.

Exemples d’invites :

* Existe-t-il des fichiers svg dans le dossier `WKND` ?
* Afficher les ressources modifiées après la `Nov 1 2025` dans le dossier `WKND`.
* Répertorier `lifestyle` images dans le dossier `WKND`.

**Découverte de ressources basée sur le format**

La tâche de découverte de contenu peut identifier les ressources qui répondent à des exigences de qualité spécifiques, telles que le format de fichier, ce qui permet aux utilisateurs de localiser rapidement les visuels de produit prêts pour une diffusion de haute qualité et une réutilisation sur plusieurs canaux.

Exemple d’invite :

Recherchez les images PNG d’emballage de produit.

**Découverte de contenu basée sur l’orientation**

La tâche de découverte de contenu peut filtrer les ressources en reconnaissant les attributs visuels, tels que la présence de personnes et l’orientation d’une image. Cela permet aux utilisateurs et aux utilisatrices de réduire rapidement le contenu aux visuels les plus pertinents sans appliquer manuellement plusieurs filtres dans AEM.

Exemple d’invite :

Afficher les ressources avec une personne en orientation paysage

### Fragments de contenu {#discovery-job-use-cases-content-fragments}

La tâche de découverte de contenu permet aux utilisateurs et utilisatrices de localiser rapidement les fragments de contenu appropriés en interprétant les références en langage naturel aux noms de campagne, aux marques de produit, au statut de publication et à l’activité de création récente. Il permet aux équipes de faire apparaître les fragments prêts pour la campagne et d’afficher le contenu spécifique à la marque, le tout sans avoir à parcourir manuellement les dossiers ou à appliquer plusieurs filtres dans AEM.

Exemples d’invites :

* Afficher les fragments de contenu pour la création de la campagne d’offres WKND.

* Affichez le fragment de contenu pour la boisson amérique.

* Afficher tous les fragments de contenu publiés pour les boissons WKND.

* Répertoriez tous les fragments de contenu créés au cours des 2 dernières semaines.

### Formulaires {#discovery-job-use-cases-forms}

La tâche de découverte de contenu vous permet de trouver rapidement des formulaires adaptatifs à l’aide d’invites en langage naturel. Il effectue une recherche dans le contenu et les métadonnées du formulaire pour trouver des correspondances en fonction des mots-clés de vos invites. Cela signifie que vous pouvez découvrir des formulaires pertinents même si vos termes de recherche ne figurent pas dans le titre ou la description du formulaire.

Exemples d’invites :

* Montrez-moi tous les formulaires de demande de prêt.
* Recherchez les formulaires à remplir pour postuler à un emploi.
* Rechercher des formulaires de contact.
* Je recherche des formulaires d’intégration des employés.
* Afficher les formulaires de demande de carte de crédit.

Remarque : la découverte de formulaires prend actuellement en charge les formulaires Edge Delivery Services uniquement et la recherche basée sur les balises n’est pas disponible pour les formulaires pour le moment.

## Résultats de la recherche {#discovery-job-search-results}

### Assets {#discovery-job-search-results-assets}

La tâche de découverte de contenu renvoie les meilleurs résultats pour chaque requête, triés par pertinence afin de s’assurer que les correspondances exactes apparaissent en premier. Le traitement associe des requêtes basées sur les métadonnées à une recherche sémantique afin d’assembler un ensemble ciblé de correspondances probables, puis utilise un LLM pour les classer en fonction de l’intention de l’utilisateur. Cette approche mixte fournit des résultats précis et contextuels sans dépendre entièrement d’une correspondance directe des mots-clés.

Chaque résultat inclut le nom de la ressource ainsi que les métadonnées clés de la ressource telles que le chemin d’accès, le créateur, la date de création, le titre, la description, le format, le dernier modificateur, la date de dernière modification, la taille du fichier, les dimensions, l’[URL de Dynamic Media](/help/assets/dynamic-media/dynamic-media.md) et les balises associées. Si une ressource est à l’état approuvé, les résultats incluent également [Dynamic Media avec l’URL OpenAPI](/help/assets/dynamic-media-open-apis-overview.md).

Vous pouvez cliquer sur le chemin d’accès à la ressource pour accéder facilement à son emplacement dans AEM.

![Recherche de ressources à l’aide de la tâche de découverte de contenu](/help/ai-in-aem/agents/content-advisor/assets/search-results-discovery-agent.png)

Vous pouvez utiliser ces détails de ressource pour évaluer rapidement si une ressource répond aux exigences sans accéder à chaque ressource pour afficher ces détails.

>[!NOTE]
>
>Le champ [ URL Dynamic Media ](/help/assets/dynamic-media/dynamic-media.md) s’affiche dans les résultats de recherche uniquement si la ressource est publiée et que vous disposez d’une licence Dynamic Media valide. De même, le champ [Dynamic Media avec URL OpenAPI](/help/assets/dynamic-media-open-apis-overview.md) s’affiche uniquement si vous disposez d’une licence Dynamic Media valide et que Dynamic Media avec OpenAPI est activé pour votre instance AEM as a Cloud Service.

### Fragments de contenu {#discovery-agent-search-results-content-fragments}

La tâche de découverte de contenu fournit des fonctionnalités de recherche en texte intégral pour les fragments de contenu, renvoyant les meilleurs résultats qui correspondent le mieux à l’invite spécifiée. Chaque résultat comprend le nom du fragment de contenu avec les champs de métadonnées clés tels que le chemin du fragment de contenu, le créateur, la date de création, les variations, le dernier modificateur et les champs de date de dernière modification.

![Rechercher des fragments de contenu à l’aide de la tâche de découverte de contenu](/help/ai-in-aem/agents/content-advisor/assets/search-content-fragments-discovery-agent.png)

Vous pouvez cliquer sur le chemin d’accès du fragment de contenu pour accéder facilement à l’emplacement du fragment de contenu dans AEM.

## Bonnes pratiques relatives à la promotion {#prompting-best-practices-discovery-job}

Spécifiez des détails concis dans vos invites de langage naturel afin que la tâche puisse renvoyer des résultats précis et pertinents. Plus vous décrivez clairement ce que vous recherchez, plus la tâche peut affiner et réduire la sortie. Par exemple, vous pouvez effectuer les actions suivantes :

* Définissez des métadonnées de ressources telles que les balises, les noms de dossier, les dates de création, le statut de publication, les noms d’auteur dans vos invites pour filtrer les ressources.

* Utilisez des métadonnées spécifiques à votre entreprise, telles que les catégories (chaussures de course, appareils électroniques), les saisons (automne, printemps), les événements (vendredi noir, lancement de produit) et les canaux (web, e-mail, impression) pour filtrer davantage le contenu.

## Limites {#limitations-discovery-job}

La tâche de découverte de contenu prend uniquement en charge les invites basées sur les dimensions pour les types d’image et de format SVG. Par exemple, `Find images wider than 1080px`.
