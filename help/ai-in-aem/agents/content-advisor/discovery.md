---
title: Agent de découverte de contenu
description: Découvrez comment utiliser l’agent de découverte de contenu pour diffuser du contenu AEM pertinent à la demande par le biais d’invites naturelles et conversationnelles afin d’offrir une expérience de découverte rationalisée et sans clic.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Developer
exl-id: 676300cd-b799-4c53-a58e-043e58a2cbc5
source-git-commit: d4b216294791958c29a4cca736bc041a7bf4ad0c
workflow-type: tm+mt
source-wordcount: '2375'
ht-degree: 1%

---


# Agent de découverte de contenu {#discovery-agent}

Dans le cadre d’AEM [Agent du gestionnaire de contenu](/help/ai-in-aem/agents/content-advisor/overview.md) l’agent de découverte de contenu fournit du contenu AEM à la demande par le biais d’invites de conversation naturelles pour une expérience de découverte rationalisée et sans clic. Il effectue des recherches intelligentes dans Assets, les fragments de contenu, les pages AEM Sites et les Forms adaptatifs pour fournir des ressources pertinentes telles que des images, des vidéos, des documents PDF, des articles et des modèles de formulaire. Le langage naturel vous permet de rechercher du contenu sans créer de requêtes complexes ni appliquer de filtres dans l’interface d’AEM Assets. En fonction de votre invite, l’agent renvoie les résultats traités, ainsi que les métadonnées de ressource et les URL de diffusion, prêts à être incorporés dans d’autres applications.

Voici quelques-uns des principaux avantages de l’agent de découverte de contenu :

* **Découverte de contenu unifié** : accédez à tous les types de contenu AEM, tels que les images, les vidéos, les documents PDF, les articles, les pages et les formulaires, à partir d’une seule interface de conversation.

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

L’agent de découverte de contenu fournit les compétences suivantes :

* **Découverte de contenu en langage naturel**

  L’agent de découverte de contenu permet aux utilisateurs et utilisatrices de rechercher des ressources, des fragments de contenu, des formulaires adaptatifs et des pages AEM Sites pertinents dans Adobe Experience Manager (AEM) à l’aide d’invites en langage naturel simple (aucune requête de recherche complexe requise).

* **Découverte de ressources basées sur des métadonnées**

  L’agent de découverte de contenu utilise des invites en langage naturel pour rechercher des ressources en fonction des métadonnées disponibles pour les ressources dans AEM. Les utilisateurs peuvent découvrir des ressources à l’aide de métadonnées telles que les balises, les ID de messagerie de l’auteur ou de l’éditeur, les dates de publication ou de modification, le type MIME, le type de ressource, le statut, les propriétés de métadonnées personnalisées définies dans les formulaires de métadonnées dans la vue Assets ou la vue Administration, etc. Voir [Cas d’utilisation courants et exemples d’invites](#use-cases-prompts) pour en obtenir la liste complète.

  Vous pouvez également combiner plusieurs filtres de métadonnées dans une seule invite pour affiner les résultats de recherche.

* **Découverte de contenu basé sur des dossiers :**\
  L’agent de découverte de contenu peut identifier les ressources en interprétant les invites de langage naturel qui font référence aux noms de dossier dans AEM. Les utilisateurs peuvent simplement mentionner le dossier dans leur invite, sans avoir à parcourir manuellement le référentiel, ce qui réduit considérablement le nombre de clics nécessaires pour localiser le contenu approprié.

## Personnes {#personas-content-discovery}

### Responsables de campagne {#campaign-managers}

L’agent de découverte de contenu permet aux responsables de campagne d’identifier et de réutiliser rapidement du contenu fiable et hautement performant à des fins d’idéation.

### Marketeurs de canaux {#channel-marketers}

L’agent de découverte de contenu permet aux spécialistes du marketing des canaux de rechercher efficacement les ressources appropriées afin de créer des expériences multicanaux cohérentes.

### Bibliothécaires DAM {#dam-librarians}

Les bibliothécaires de la gestion des ressources numériques peuvent signaler les ressources qui ne respectent pas les normes de métadonnées définies par l’organisation, ce qui permet une gouvernance cohérente et garantit que les ressources restent complètes et prêtes à être utilisées sur l’ensemble des canaux.

### Agences et partenaires {#agencies-partners}

Les agences et les partenaires peuvent facilement rechercher des ressources approuvées par la marque dans Content Hub et les réutiliser pour accélérer le travail créatif tout en restant conformes aux normes de la marque.

## Accès {#access}

Vous pouvez accéder à l’agent de découverte de contenu dans AEM via l’assistant d’IA. Connectez-vous à [`experience.adobe.com`](https://experience.adobe.com) et commencez à interagir avec l’assistant AI en spécifiant votre invite en langage naturel à l’aide de la zone de recherche :

![Accéder à l’agent de découverte de contenu](/help/ai-in-aem/agents/content-advisor/assets/access-discovery-agent.png)

Pour plus d’informations sur le point d’entrée MCP permettant d’accéder à l’agent de découverte de contenu, contactez l’assistance Adobe.

## Cas d’utilisation courants et exemples d’invites {#use-cases-prompts}

### Ressources {#discovery-agent-use-cases-assets}

**Découverte de ressources basées sur des métadonnées**

L’agent de découverte de contenu utilise des invites en langage naturel pour rechercher des ressources en fonction des métadonnées disponibles pour les ressources dans AEM. Les utilisateurs peuvent découvrir des ressources à l’aide des propriétés de métadonnées suivantes : balises, créé par ID d’e-mail, modifié par ID d’e-mail, publié par ID d’e-mail, date de création, date de modification, date de publication, type MIME, type de ressource, statut, format de fichier, taille de fichier, largeur d’image, hauteur d’image et plusieurs filtres de métadonnées dans une seule invite.

L’agent de découverte de contenu recherche également les propriétés personnalisées disponibles dans les schémas de métadonnées dans la vue Administration et les formulaires de métadonnées dans la vue Assets. Vous pouvez modifier vos invites en conséquence pour rechercher des valeurs disponibles dans ces propriétés de ressource personnalisées.

>[!NOTE]
>
>Pour améliorer les performances de découverte, indexez les propriétés de métadonnées personnalisées pertinentes. Les propriétés indexées permettent à l’agent de récupérer plus rapidement le contenu correspondant lorsque les utilisateurs incluent ces propriétés dans leurs invites.


Exemples d’invites :

* **Recherche basée sur les balises** : affiche les images balisées `office` dans le dossier `WKND`.
* **Recherche en fonction du format de fichier, du type de ressource, de l’état de la ressource et de l’ID de publication par e-mail** : affiche les images au format `.PNG` qui sont `approved` et `published by <user email ID>`.
* **Recherche en fonction du format de fichier, du type de ressource, de l’état de la ressource et de l’ID de ressource créé par e-mail** : afficher les vidéos au format `.mp4` qui sont approuvées et `created by <user email ID>`.
* **Recherche en fonction du format de fichier, du type de ressource, du statut de la ressource et de la date de création** : affiche les images au format `.PNG` créées après le 1er janvier 2025 et `published by <user email ID>`
* **Recherche basée sur le type MIME, la date de création et l’ID de publication par e-mail** : affiche les `image/jpeg` créées après `January 1, 2025` et `published by <user email ID>`.

* **Rechercher des ressources présentant des métadonnées manquantes** : l’option Afficher les ressources créées au cours des 90 derniers jours avec des `<Name of metadata property including custom properties>` est vide.

* **Rechercher des ressources en utilisant la taille de fichier, la largeur d’image et la hauteur d’image** : affichez les images de plus de 5 Mo avec une largeur supérieure à 2 000 pixels et une hauteur supérieure à 1 200 pixels.

**Prise en charge du langage naturel pour les métadonnées personnalisées**

L’agent de découverte de contenu prend en charge l’interrogation de propriétés de métadonnées personnalisées définies dans des schémas de métadonnées. Vous pouvez référencer des valeurs de métadonnées directement dans vos invites sans avoir à les spécifier à l’aide d’un format clé-valeur strict. L’agent interprète l’intention et associe automatiquement les champs de métadonnées pertinents.

Exemples d’invites :

* **La recherche de ressources avec une valeur de propriété n’est pas définie** : recherchez les ressources dont le nom de campagne n’est pas défini (la propriété doit être indexée pour obtenir les résultats appropriés).

* **Recherche de ressources dont la valeur de propriété est définie** : recherchez les ressources dont le nom de campagne est défini (la propriété doit être indexée pour obtenir les résultats appropriés).

* **Recherche de ressources dont la valeur de propriété est définie sur X** : recherchez-moi les ressources dont le nom de campagne est Jour de café.

* **Recherche de ressources dont la valeur de propriété est définie sur un ensemble de valeurs X, Y** : recherchez les ressources dont le nom de campagne est Jour-café ainsi que celles dont le nom de campagne est Jour-thé.

* **Affichage de la valeur d’un champ de propriété spécifique** : Obtenir des ressources Coffee m’affiche également le nom de campagne de ces ressources.

* **Rechercher des ressources qui correspondent à une condition de propriété basée sur la date** : obtenez-moi les ressources dont la licence n’a pas expiré.












**Découverte de contenu basé sur des dossiers :**\
L’agent de découverte de contenu peut identifier les ressources en interprétant les invites en langage naturel qui font référence aux noms de dossier dans AEM. Les utilisateurs peuvent simplement mentionner le dossier dans leur invite, sans avoir à parcourir manuellement le référentiel, ce qui réduit considérablement le nombre de clics nécessaires pour localiser le contenu approprié.

Exemples d’invites :

* Existe-t-il des fichiers svg dans le dossier `WKND` ?
* Afficher les ressources modifiées après la `Nov 1 2025` dans le dossier `WKND`.
* Répertorier `lifestyle` images dans le dossier `WKND`.

**Questions supplémentaires pour permettre la découverte de contenu basé sur des dossiers**

Lorsqu’un nom de dossier est inclus dans une invite (sans le chemin d’accès complet à la ressource), l’agent de découverte de contenu recherche d’abord un dossier correspondant au `/content/dam/<folder-name>` de chemin racine.

Si aucun dossier correspondant n’est trouvé au niveau racine, l’agent suggère d’autres chemins de dossier où le nom de dossier spécifié existe dans le référentiel. Cela permet aux utilisateurs d’identifier rapidement l’emplacement correct sans avoir à parcourir manuellement la structure des dossiers.

Par exemple, le chemin `/content/dam/<folder-name>` est introuvable. Tu voulais dire un de ceux-là ?

* Option 1

* Option 2

**Découverte de ressources basée sur le format**

L’agent de découverte de contenu peut identifier les ressources qui répondent à des exigences de qualité spécifiques, telles que le format de fichier, ce qui permet aux utilisateurs de localiser rapidement les visuels de produit prêts pour une diffusion de haute qualité et une réutilisation sur plusieurs canaux.

Exemple d’invite :

Recherchez les images PNG d’emballage de produit.

**Découverte de contenu basée sur l’orientation**

L’agent de découverte de contenu peut filtrer les ressources en reconnaissant les attributs visuels, tels que la présence de personnes et l’orientation d’une image. Cela permet aux utilisateurs et aux utilisatrices de réduire rapidement le contenu aux visuels les plus pertinents sans appliquer manuellement plusieurs filtres dans AEM.

Exemple d’invite :

Afficher les ressources avec une personne en orientation paysage

**Développement des résultats de recherche**

L’agent de découverte de contenu renvoie les 20 résultats les plus pertinents par type de contenu pour une invite. Si d’autres résultats correspondants sont disponibles, les utilisateurs peuvent demander l’ensemble suivant en saisissant une invite de relance, telle que `show me more`. L’agent récupère ensuite le jeu de résultats suivant de la recherche d’origine, ce qui permet aux utilisateurs et utilisatrices d’explorer progressivement des jeux de résultats plus volumineux sans affiner l’invite.

**Recherche de ressources similaires**

L’agent de découverte de contenu permet aux utilisateurs de trouver des ressources similaires à un résultat spécifique renvoyé dans les résultats de recherche. Une fois que l’agent a affiché les meilleurs résultats pour une invite, vous pouvez demander des ressources similaires en référençant la position d’un élément dans la liste de résultats. Par exemple, une invite telle que `find assets similar to the 3rd result` demande à l’agent d’identifier et de renvoyer d’autres ressources pertinentes liées à cet élément. Cela permet aux utilisateurs de découvrir rapidement le contenu associé sans créer d’invite de recherche.

**Tri des résultats de recherche**

L’agent de découverte de contenu permet aux utilisateurs et utilisatrices de trier les résultats de recherche directement dans leurs invites de langage naturel. Les utilisateurs et utilisatrices peuvent spécifier des critères de tri tels que la date de modification, la date de création ou le nom de la ressource, et choisir un ordre croissant ou décroissant.

Exemples d’invites :

* Recherchez des images de montagne triées par date de modification dans l’ordre décroissant (affiche d’abord les ressources modifiées le plus récemment).

* Afficher les images de montagne triées par nom dans l’ordre croissant (affiche les noms d’image commençant par la lettre A suivie de B, etc.).

**Détection d’environnement contextuelle**

Dans la vue Administration, l’agent de découverte de contenu détecte automatiquement l’environnement de création et l’utilise pour résoudre les invites, sans que vous ayez à spécifier explicitement l’URL de création.

### Pages AEM Sites {#content-discovery-agent-aem-sites-pages}

L’agent de découverte de contenu permet aux utilisateurs de localiser rapidement les pages AEM Sites appropriées en interprétant les invites en langage naturel qui font référence aux rubriques de la page, aux campagnes ou à d’autres mots-clés contextuels. L’agent effectue une recherche en texte intégral en fonction des mots-clés de l’invite pour identifier les pages correspondantes dans le référentiel AEM, ce qui élimine la nécessité de parcourir manuellement la structure Sites.

Exemples d’invites :

* Recherchez toutes les pages AEM Sites pour la campagne d’été.

* Recherchez des pages AEM Sites avec un thème Café .

### Fragments de contenu {#discovery-agent-use-cases-content-fragments}

L’agent de découverte de contenu permet aux utilisateurs et utilisatrices de localiser rapidement les fragments de contenu appropriés en interprétant les références en langage naturel aux noms de campagne, aux marques de produit, au statut de publication et à l’activité de création récente. Il permet aux équipes de faire apparaître les fragments prêts pour la campagne et d’afficher le contenu spécifique à la marque, le tout sans avoir à parcourir manuellement les dossiers ou à appliquer plusieurs filtres dans AEM.

Exemples d’invites :

* Afficher les fragments de contenu pour la création de la campagne d’offres WKND.

* Affichez le fragment de contenu pour la boisson amérique.

* Afficher tous les fragments de contenu publiés pour les boissons WKND.

* Répertoriez tous les fragments de contenu créés au cours des 2 dernières semaines.

### Formulaires {#discovery-agent-use-cases-forms}

L’agent de découverte de contenu vous permet de trouver rapidement des formulaires adaptatifs à l’aide d’invites en langage naturel. Il effectue une recherche dans le contenu et les métadonnées du formulaire pour trouver des correspondances en fonction des mots-clés de vos invites. Cela signifie que vous pouvez découvrir des formulaires pertinents même si vos termes de recherche ne figurent pas dans le titre ou la description du formulaire.

Exemples d’invites :

* Montrez-moi tous les formulaires de demande de prêt.
* Recherchez les formulaires de demande d’un agent.
* Rechercher des formulaires de contact.
* Je recherche des formulaires d’intégration des employés.
* Afficher les formulaires de demande de carte de crédit.

Remarque : la découverte de formulaires prend actuellement en charge les formulaires Edge Delivery Services uniquement et la recherche basée sur les balises n’est pas disponible pour les formulaires pour le moment.

## Résultats de la recherche {#discovery-agent-search-results}

### Assets {#discovery-agent-search-results-assets}

L’agent de découverte de contenu renvoie les meilleurs résultats pour chaque requête, triés par pertinence afin de s’assurer que les correspondances exactes apparaissent en premier. L’agent combine des requêtes basées sur les métadonnées avec une recherche sémantique pour assembler un ensemble ciblé de correspondances probables, puis utilise un LLM pour les classer en fonction de l’intention de l’utilisateur. Cette approche mixte fournit des résultats précis et contextuels sans dépendre entièrement d’une correspondance directe des mots-clés.

Chaque résultat s’affiche sous la forme d’une carte de ressource, qui indique le nom, l’aperçu et les métadonnées clés de la ressource, telles que la description et le format. Vous pouvez cliquer sur l’icône Infos sur une carte pour afficher des propriétés de ressource supplémentaires.

Utilisez l’option **Afficher le tableau** pour afficher les résultats sous forme de tableau. Cliquez sur **Afficher tous les résultats** pour afficher l’ensemble complet des 20 ressources récupérées dans le volet de droite.

Chaque résultat inclut également des métadonnées clés sur la ressource telles que le chemin d’accès, la taille, la date de création et le créateur ou la créatrice, la date de modification, ainsi que l’utilisateur ou l’utilisatrice qui a modifié la ressource, le format et la description. Si une ressource est à l’état approuvé, les résultats incluent également [Dynamic Media avec l’URL OpenAPI](/help/assets/dynamic-media-open-apis-overview.md). Vous pouvez cliquer sur le chemin d’accès à la ressource pour accéder facilement à son emplacement dans AEM.

![Recherche de ressources à l’aide de l’agent de découverte de contenu](/help/ai-in-aem/agents/content-advisor/assets/search-results-content-discovery-agent.png)

Vous pouvez utiliser ces détails de ressource pour évaluer rapidement si une ressource répond aux exigences sans accéder à chaque ressource pour afficher ces détails.

>[!NOTE]
>
>Le champ [&#x200B; URL Dynamic Media &#x200B;](/help/assets/dynamic-media/dynamic-media.md) s’affiche dans les résultats de recherche uniquement si la ressource est publiée et que vous disposez d’une licence Dynamic Media valide. De même, le champ [Dynamic Media avec URL OpenAPI](/help/assets/dynamic-media-open-apis-overview.md) s’affiche uniquement si vous disposez d’une licence Dynamic Media valide et que Dynamic Media avec OpenAPI est activé pour votre instance AEM as a Cloud Service.

### Fragments de contenu {#discovery-agent-search-results-content-fragments}

L’agent de découverte de contenu fournit des fonctionnalités de recherche de texte intégral pour les fragments de contenu, renvoyant les meilleurs résultats qui correspondent le mieux à l’invite spécifiée. Chaque résultat comprend le nom du fragment de contenu avec les champs de métadonnées clés tels que le chemin du fragment de contenu, le créateur, la date de création, les variations, le dernier modificateur et les champs de date de dernière modification.

![Rechercher des fragments de contenu à l’aide de l’agent de découverte de contenu](/help/ai-in-aem/agents/content-advisor/assets/search-content-fragments-discovery-agent.png)

Vous pouvez cliquer sur le chemin d’accès du fragment de contenu pour accéder facilement à l’emplacement du fragment de contenu dans AEM.

## Bonnes pratiques relatives à la promotion {#prompting-best-practices-discovery-agent}

Spécifiez des détails concis dans vos invites en langage naturel afin que l&#39;agent puisse renvoyer des résultats précis et pertinents. Plus vous décrivez clairement ce que vous recherchez, plus l’agent peut affiner et réduire la sortie. Par exemple, vous pouvez effectuer les actions suivantes :

* Définissez des métadonnées de ressources telles que les balises, les noms de dossier, les dates de création, le statut de publication, les noms d’auteur dans vos invites pour filtrer les ressources.

* Utilisez des métadonnées spécifiques à votre entreprise, telles que les catégories (chaussures de course, appareils électroniques), les saisons (automne, printemps), les événements (vendredi noir, lancement de produit) et les canaux (web, e-mail, impression) pour filtrer davantage le contenu.

## Restrictions {#limitations-discovery-agent}

* Le Content Discovery Agent prend uniquement en charge les invites basées sur les dimensions pour les types de format image et SVG. Par exemple, `Find images wider than 1080px`.

* Les administrateurs Content Hub peuvent accéder à l’agent de découverte de contenu à l’aide du portail Content Hub. Toutefois, les résultats sont récupérés uniquement à partir de l’instance d’auteur AEM. Les utilisateurs de Content Hub Limited ne peuvent actuellement pas bénéficier des avantages de l’agent de découverte de contenu (bientôt disponible).

* La fonctionnalité Rechercher des similitudes fonctionne uniquement pour les images avec des améliorations de balises intelligentes [Smart Tags](/help/assets/ai-generated-metadata-assets-view.md).
