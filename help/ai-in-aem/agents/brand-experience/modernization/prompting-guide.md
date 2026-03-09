---
title: Guide de l’invite pour l’agent de modernisation d’expérience
description: Ce guide fournit des conseils pour une invite efficace de l’agent de modernisation de l’expérience et décrit ce que font ses compétences.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Architect, Developer
source-git-commit: e2a9c55644c0d9542f6a299f0df30a3dfd4a55de
workflow-type: tm+mt
source-wordcount: '2696'
ht-degree: 0%

---


# Guide de l’invite pour l’agent de modernisation d’expérience {#prompting-guide}

L’agent de modernisation de l’expérience sélectionne automatiquement les compétences appropriées en fonction des requêtes en langage naturel. Ce guide fournit des conseils pour une invite efficace et décrit ce que font les compétences.

## Conseils généraux {#general-tips}

### Certaines compétences dépendent des résultats d’autres compétences. {#dependency}

* L’importation en bloc nécessitant l’infrastructure d’importation créée par la migration de page, migrez au moins une page avant d’exécuter l’importation en bloc.
* Comme le bloc CSS fait référence aux jetons de conception globaux, effectuez la conception à l’échelle du site avant de mettre en forme des blocs individuels.

### L’IA suit des workflows structurés et pose des questions pour clarifier les choses lorsqu’elle a besoin d’informations supplémentaires. {#workflows}

* Faites confiance au processus et répondez à ces questions au fur et à mesure qu’elles se présentent.
* N’essayez pas de charger au premier plan toutes les exigences dans l’invite initiale.

### Créez des fichiers Markdown dans le projet pour documenter les règles, directives, décisions de conception ou contraintes spécifiques au projet. {#markdown-files}

* Ces fichiers Markdown (par exemple, INSTRUCTIONS.md, CONTEXT.md) peuvent inclure des conventions de dénomination de fichiers, des règles de mappage de contenu ou des directives relatives à la marque.
* Lors du démarrage d’une nouvelle conversation, demandez à l’agent de « se préchauffer en lisant la documentation du projet » afin de charger ce contexte avant de poursuivre les tâches.

### La fenêtre contextuelle de l’agent n’est pas infinie. {#limited-window}

* Au fil de longues conversations, les instructions antérieures peuvent être compactées ou oubliées.
* Si l’agent semble avoir perdu le contexte, rappelez-lui les points clés ou effacez la conversation et recommencez à zéro avec une invite de préchauffage pour lire la documentation du projet.

### Utilisez des invites itératives pour affiner les résultats. {#iterate}

* Si quelque chose ne semble pas correct (par exemple, une mauvaise couleur d’arrière-plan sur un bloc), demandez à l’agent de résoudre le problème spécifique plutôt que de recommencer.

## Compétences en création et migration de site {#site-migration}

L’agent de modernisation de site offre de nombreuses compétences pour créer de nouveaux sites Edge Delivery Services et migrer des sites web existants. Tout nouveau site Edge Delivery ou projet de migration doit tirer parti de ces compétences.

### Migration d’un site ou d’une page vers AEM {#migrate-a-site}

Utilisez cette invite lors de la migration de contenu d’un site web existant vers Edge Delivery Services.

#### Exemples d’invites {#example-migrate}

* « Migrer cette page : `https://example.com/about`
* « Migrer ces pages : URL1, URL2, URL3 »

#### Ce qu’il faut savoir {#wtk-migrate}

* La migration suit un workflow en sept étapes :
   1. L’agent gratte la page source.
   1. Il identifie la structure de la section.
   1. Il effectue une analyse de création.
   1. Il mappe le contenu pour bloquer les variantes.
   1. Cela génère du markdown.
   1. Cela crée une infrastructure d&#39;importation.
   1. Il prévisualise le résultat.
* L’agent analyse les pages à l’aide d’une hiérarchie à deux niveaux :
   * Il identifie d&#39;abord les limites des sections (changements d&#39;arrière-plan, décalages d&#39;espacement)
   * Il identifie ensuite les séquences de contenu dans chaque section.
* La création d’une analyse suit [le modèle de David](https://www.aem.live/docs/davidsmodel).
   * pour chaque séquence de contenu, il vérifie d’abord « Un auteur peut-il le créer en saisissant normalement ? »
   * Le contenu par défaut (titres, paragraphes, listes, images intégrées) est préférable aux blocs.
* L’agent tente de réutiliser des blocs existants de la bibliothèque de blocs du référentiel avant d’en créer de nouveaux.
   * Lorsque le contenu ne peut pas être mappé à un bloc existant, il crée des variantes de bloc.
   * Vous pouvez demander des modifications, demander de nouvelles variantes ou ajuster les mappages de manière interactive.
* Les variantes de bloc sont suivies avec des métadonnées.
   * Lors de la migration de plusieurs pages, l’agent charge d’abord les variantes personnalisées existantes et les réutilise lors de la mise en forme des correspondances (seuil de similarité de 70 % en fonction de l’objectif, des couleurs, de la typographie, de l’espacement et de la disposition).
* L’en-tête, la navigation et le pied de page sont exclus de la migration. Ils sont gérés par des compétences dédiées.
* Chaque migration crée une infrastructure d’importation (modèles de page, analyseurs de blocs, transformateurs) pour les futures importations en bloc.

### Importation en bloc {#bulk-import}

Utilisez cette invite pour importer de nombreuses pages du même modèle après avoir terminé une [migration initiale d’une seule page](#migrate-a-site).

#### Exemples d’invites {#example-prompts-bulk-import}

* « Exécutez l’import en bloc sur ces pages : URL1, URL2, URL3. »
* « Exécuter l’importation en bloc sur toutes les pages de produits. »
* « Importez en bloc ces pages de blog : URL1, URL2. »

#### Ce qu’il faut savoir {#wtk-bulk-import}

* L’importation en bloc dépend de l’infrastructure d’importation créée lors d’une migration précédente sur une seule page.
   * Cela inclut les modèles de page (structure de section), les transformateurs (nettoyage DOM à l’échelle du site) et les analyseurs (conversion d’HTML en tableau spécifique au bloc).
* Vous devez migrer au moins une page représentative par modèle avant de pouvoir exécuter l’importation en bloc.
* L’importation en bloc réutilise la structure et les mappages établis lors de la migration sur une seule page.
   * Il ne déduit pas de modèles à partir de zéro.
* Les transformateurs fonctionnent sur l’ensemble du DOM avant et après l’analyse. Les analyseurs fonctionnent au niveau du bloc individuel.
* Tous les analyseurs sont validés avant que l’importation en bloc puisse se poursuivre.
* Un modèle correspond à une configuration d’importation en bloc.
   * Le mélange de modèles dans une seule exécution n’est pas pris en charge.

#### Workflow standard {#typical-workflow}

Le workflow recommandé est itératif : validez d’abord un petit ensemble, puis augmentez-le.

1. **Commencez par effectuer une migration sur une seule page.** - Migrez une page représentative pour le modèle que vous prévoyez d’importer en bloc.
   * Cela crée l’infrastructure d’importation requise.
1. **Exécutez l’importation en bloc sur un petit ensemble de pages.** - Demandez à l’agent d’exécuter l’import en bloc et de fournir une liste courte d’URL qui suivent le même modèle.
1. **Examinez et affinez les résultats.** - Inspectez les pages importées.
   * Si quelque chose semble incorrect, demandez à l’agent d’ajuster les analyseurs, les transformateurs ou la logique d’importation.
1. **Agrandir.** - Lorsque les résultats semblent corrects, fournissez la liste complète des URL.
   * L’agent réutilisera la même logique d’importation et exécutera l’importation en bloc à grande échelle.

### Grattage de pages web {#scraping-webpages}

Utilisez cette invite pour extraire du contenu, des métadonnées et des images à partir d’une URL source à des fins d’analyse ou de migration.

#### Exemples d’invites {#example-scraping}

* « Extraire cette page pour analyse : `https://example.com` »
* « Extraire le contenu de `https://example.com/product` »

#### Ce qu’il faut savoir {#wtk-scraping}

* Cette invite est généralement appelée automatiquement comme première étape de la migration de la page.
* Le contenu masqué via CSS est également capturé s’il est présent dans le DOM.
* Les images chargées en différé et le contenu rendu côté client sont gérés en faisant défiler la page dans Chromium découplé et en laissant les scripts s’exécuter.
* Les images WebP/AVIF/SVG sont converties en PNG à des fins de compatibilité.
* Les métadonnées sont extraites, notamment le titre, la description, les balises Open Graph, les données structurées JSON-ID et l’URL canonique.
* Les images dans DOM sont corrigées.
   * background-image est converti en img.
   * Les éléments d&#39;image sont dépliés
   * srcset est résolu en src
   * Les URL relatives sont converties en URL absolues.
   * Le SVG intégré en est converti en fichiers img.
* Les chemins d’accès aux documents assainis sont générés (en minuscules sans extension `.html`).
* Les résultats suivants sont produits :
   * `screenshot.png`
   * `cleaned.html` (aucun script/style)
   * `metadata.json`
   * Dossier `images/` avec copies locales
* Les utilisateurs peuvent poser des questions sur les dimensions des captures d’écran et demander des tailles d’appareil spécifiques (mobile, bureau) pour l’extraction de contenu.
* L’extraction de contenu à plusieurs points d’arrêt augmente le temps de traitement.

### Migration de la conception {#design-migration}

Utilisez cette invite pour extraire et appliquer une conception visuelle d’un site source à Edge Delivery Services.

#### Exemples d’invites {#example-design}

* « Migrer la conception depuis `https://example.com` »
* « Extraction de jetons de conception »
* « Donner un style au bloc des héros »

#### Ce qu’il faut savoir {#wtk-design}

* La migration de conception comporte deux phases :
   1. La phase 1 (à l’échelle du site) extrait les éléments suivants pour les `styles/styles.css` :
      * Palette de couleurs globale et couleurs d’accentuation
      * Système de typographie (polices, tailles, poids)
      * Système d&#39;espacement (marge intérieure, marges, espaces)
      * Arrière-plans de section (clair, sombre, coloré)
      * Styles des composants de base (boutons, liens, images)
      * Sorties vers
   1. La phase 2 migre les styles de blocs individuels et crée un CSS spécifique au bloc dans `/blocks/{name}/{name}.css`.
* Le style de bloc (phase 2) nécessite que la conception à l’échelle du site (phase 1) soit terminée en premier.
   * Le système de conception global fournit des propriétés personnalisées CSS qui bloquent la référence.
* Temps estimé :
   * Phase 1 : 5-10 minutes
   * Phase 2 : 10 à 15 minutes
* Les requêtes ambiguës effectuent par défaut la migration complète (les deux phases).

### Bloquer la critique {#block-critique}

Utilisez cette invite pour valider et affiner les blocs migrés individuels et garantir la précision visuelle par rapport au site web d’origine.

#### Exemples d’invites {#example-block-critique}

* « Bloc de héros critique »
* « Valider le bloc de cartes personnalisées »

#### Ce qu’il faut savoir {#wtk-block-critique}

* La critique de bloc compare un bloc migré à sa source d’origine et applique de manière itérative des correctifs CSS jusqu’à ce qu’une similarité visuelle de 85 % soit atteinte ou que trois itérations soient terminées.
* La compétence nécessite que le bloc ait d’abord été créé par la migration de la page.
* Une critique de bloc suit un workflow en six étapes :
   1. Il capture le bloc d’origine de la page source à l’aide d’un sélecteur XPath.
   1. Il initialise la session critique.
   1. Il inspecte le bloc d’origine (captures d’écran, styles, HTML).
   1. Il inspecte le bloc migré.
   1. Il compare les éléments et génère un score de similarité avec les correctifs CSS.
   1. Il applique des correctifs et procède à de nouvelles inspections jusqu’à ce que l’objectif de 85 % soit atteint.
* Chaque itération affiche un rapport critique complet avec toutes les différences, applique tous les correctifs CSS (hiérarchisés par impact visuel), vérifie dans l’aperçu, inspecte à nouveau et affiche les mesures d’amélioration.
* Utilisez la critique de bloc une fois la [migration de conception](#design-migration) terminée.

### Critique de page {#page-critique}

Utilisez cette invite pour valider des pages entières migrées pour une fidélité visuelle pleine page par rapport au site web d’origine.

#### Exemples d’invites {#example-page-critique}

* « Critique de la page À propos de »
* « Valider la page migrée par rapport à `https://example.com/about` »

#### Ce qu’il faut savoir {#wtk-page-critique}

* La critique de page effectue une comparaison visuelle sur toute la page entre la page d’origine et la page migrée, en itérant jusqu’à ce qu’une cible de similarité de 85 % ou trois itérations soient atteintes.
* Une critique de page comporte un workflow en cinq étapes :
   1. Il initialise une session critique.
   1. Il inspecte tous les éléments de la page d’origine.
   1. Il inspecte tous les éléments de la page migrée.
   1. Il compare et génère un score de similarité avec les correctifs CSS prioritaires.
   1. Il applique des correctifs et procède à de nouvelles inspections jusqu’à ce que l’objectif de 85 % soit atteint.
* Une critique de page nécessite l’URL de la page source et le chemin migré (par exemple, « /about ») comme entrée.
* Utilisez la critique de page lors de la validation de la fidélité globale de la page ou de la validation de plusieurs blocs simultanément.
* [Utilisez la critique de bloc](#block-critique) pour une validation ciblée sur des composants spécifiques.
* Le workflow suivant est recommandé :
   1. Migrer une page.
   1. Appliquez une conception.
   1. Exécuter une critique de bloc sur les blocs de clés
   1. Exécutez la critique de page pour une validation complète.

### Migration en blocs Figma {#figma-block-migration}

Utilisez cette invite pour migrer un bloc de la conception Figma vers Edge Delivery Services.

Pour utiliser cette invite, vous devez configurer les détails de vos données Figma dans [la console de modernisation de l’expérience](/help/ai-in-aem/agents/brand-experience/modernization/console.md).

#### Exemples d’invites {#example-figma}

* « Migrer le `https://figma.com/design/{fileKey}?node-id={nodeId}` de bloc vers Edge Delivery Services »
* « Migrer des `{blockName}` de `https://figma.com/file/{fileKey}` vers Edge Delivery Services »

#### Ce qu’il faut savoir {#wtk-figma}

* Cette compétence migre un bloc à la fois, et non des pages entières ou des fichiers Figma complets.
* Pour de meilleurs résultats :
   * Sélectionnez le bloc spécifique à migrer dans Figma et copiez son lien (avec `node-id`) ou son nom.
   * Fournissez le paramètre `node-id` dans l’URL pour cibler le bloc exact.
* Lorsque vous exécutez cette compétence, les étapes suivantes sont automatiquement exécutées dans l’environnement hébergé :
   1. **Découverte de structure en blocs** — L&#39;agent lit le nœud Figma pour comprendre les couches et les composants.
   1. **Extraction de style globale** : l’agent extrait les couleurs, la typographie et l’espacement dans les `styles/styles.css` en tant que propriétés personnalisées CSS (jetons de conception).
   1. **Création de style spécifique au bloc** — L’agent crée des propriétés personnalisées CSS supplémentaires spécifiques au bloc en cours de migration.
   1. **Mappage à des blocs existants** — L&#39;agent identifie le bloc correspondant le plus proche dans la bibliothèque de blocs de votre projet et crée une variante personnalisée.
   1. **Génération CSS** — L’agent écrit des styles qui font référence aux propriétés personnalisées CSS extraites, assurant ainsi la cohérence de la conception.
   1. **Téléchargement des ressources** — L&#39;agent enregistre les images et les icônes de Figma dans l&#39;espace de travail de l&#39;environnement hébergé.
   1. **Génération de contenu Edge Delivery Services** — L&#39;agent crée le fichier Markdown en suivant la structure du bloc EDS
   1. **Validation de la sortie** — L&#39;agent prévisualise le résultat et effectue une comparaison visuelle avec la conception Figma d&#39;origine.
* La compétence lit d’abord les métadonnées (étape 1) pour comprendre la structure, puis extrait le contexte de conception détaillé (étapes 2 à 5).
   * Cette approche progressive permet d’éviter les problèmes liés aux fichiers Figma volumineux ou complexes.
* Cette compétence adopte une approche qui privilégie les styles.
   * Tous les styles sont extraits en tant que propriétés personnalisées CSS (jetons de conception) avant l’écriture d’un CSS.
   * Cela garantit que le bloc migré reste cohérent avec votre système de conception.
* L’invite nécessite l’URL Figma (avec les `fileKey` `node-id` et facultatifs) ou une clé de fichier Figma directement en entrée.

### Configuration de la navigation {#navigation-setup}

Utilisez cette invite pour configurer ou migrer la navigation du site.

#### Exemples d’invites {#example-navigation}

* « Configurer la navigation à partir de `https://example.com` »
* « Correction du menu de navigation »

#### Ce qu’il faut savoir {#wtk-navigation}

* La navigation dans Edge Delivery Services applique une structure à trois sections (appliquée par `header.js`) :
   1. **Marque** (section 1) : logo et lien de marque principal
   1. **Sections** (section 2) : menu de navigation principal avec listes déroulantes facultatives
   1. **Outils** (section 3) : liens d’utilitaires (abonnement, connexion, panier)
* Le contenu de navigation réside en `nav.md` dans le répertoire racine.
* Les sections sont séparées par des marqueurs (`---`).
* Les éléments en gras (`**Text**`) avec des listes imbriquées créent des listes déroulantes.
* Les liens dans la navigation peuvent s’afficher sous forme de boutons en raison du comportement d’encapsulation automatique de la création de documents.
   * Le bloc d’en-tête comprend du code pour supprimer les classes de bouton des liens de navigation.

## Bloquer les fonctionnalités de développement {#block-development-capabilities}

Ces invites sont utilisées pour créer et faire évoluer les blocs, offrant ainsi une valeur continue au-delà de la création ou de la migration initiale du site.

### Bloquer le développement {#block-development}

Utilisez cette invite pour créer de nouveaux blocs ou modifier des blocs existants.

#### Exemples d’invites {#example-block-development}

* « Créer un bloc de témoignages »
* « Ajouter une variante d’arrière-plan vidéo au bloc principal »

#### Ce qu’il faut savoir {#wtk-block-development}

* L’agent suit le développement piloté par le contenu (CDD), un processus obligatoire pour tous les développements Edge Delivery Services.
   * Il pose des questions sur les modèles de contenu et teste le contenu avant d’écrire du code.
* La philosophie du CDD est que les besoins de l’auteur passent avant ceux du développeur.
   * Les modèles de contenu doivent être intuitifs pour les auteurs, même si cela signifie un code de décoration plus complexe.
* La création du contenu de test fournit d’abord :
   * Fonctionnalité de test immédiat
   * Liens de validation des RP pour les contrôles PSI
   * Documentation dynamique pour les auteurs
   * Découverte de cas Edge dans lesquels les approches code-first ne fonctionnent pas
* L’agent recherche des blocs similaires dans les [Collection de blocs](https://www.aem.live/developer/block-collection) et [Partie de bloc](https://www.aem.live/developer/block-party/) avant l’implémentation, afin de trouver des modèles et du code réutilisable.
* Ignorer le CDD uniquement pour les ajustements triviaux de CSS uniquement (mais toujours identifier le contenu du test pour la validation).

### Modélisation de contenu {#content-modeling}

Utilisez cette invite pour concevoir la structure du tableau que les auteurs utilisent lors de la création de contenu en bloc.

#### Exemples d’invites {#example-modeling}

* « Conception d’un modèle de contenu pour un bloc de témoignages »
* « Quel est le meilleur modèle de contenu pour ce carrousel ? »

#### Ce qu’il faut savoir {#wtk-modeling}

* Edge Delivery Services comporte quatre types de modèles canoniques :
   * **Autonome :** éléments visuels/narratifs distincts (héros, citation)
      * Tableau unique avec contenu en blocs
   * **Collection :** Répétition de contenu semi-structuré (cartes, carrousel)
      * Tableau avec motif de lignes répétées
   * **Configuration :** contenu dynamique ou piloté par API où les commandes de configuration s’affichent (liste de blogs, résultats de recherche)
      * Tableau avec lignes de configuration clé-valeur.
   * **Bloqué automatiquement :** structures complexes que les auteurs créent en tant que sections/contenu par défaut, puis sont transformées (onglets, incorporations de YouTube).
* Il existe une limite de quatre cellules par ligne.
   * Regroupez les éléments associés dans des cellules.
* Préférez les variantes de bloc aux cellules de configuration pour les différences de style.
* [Suivez la loi de Postel](https://en.wikipedia.org/wiki/Robustness_principle) : soyez flexible en matière de structure d’entrée.
   * Un bloc de premier plan doit fonctionner, que le contenu se trouve dans une cellule, fractionné sur deux cellules ou dans des lignes distinctes.
* Cette compétence est généralement appelée automatiquement par le développement piloté par le contenu lors de la création du bloc.

### Recherche de blocs de référence {#reference-blocks}

Utilisez cette invite pour rechercher des implémentations existantes à utiliser comme points de départ.

#### Exemples d’invites {#example-reference}

* « Rechercher des blocs similaires à une table des prix »
* « Quels blocs sont disponibles pour les témoignages ? »
* « Rechercher des parties de bloc pour une implémentation d’onglets »

#### Ce qu’il faut savoir {#wtk-reference}

* La [collection de blocs](https://www.aem.live/developer/block-collection) est gérée et contrôlée par Adobe pour garantir de bonnes pratiques, une excellente modélisation de contenu, des performances élevées et l’accessibilité.
   * Elle est limitée aux blocs fréquemment nécessaires. Commencez ici.
* Le [Block Party](https://www.aem.live/developer/block-party/) est axé sur la communauté et offre une plus grande variété, y compris des approches expérimentales.
   * Il comprend également des modules externes Sidekick, des outils de création (webpack, vite, sass) et des intégrations.
   * À utiliser lorsque la collection de blocs n’a pas ce dont vous avez besoin.
* Pensez aux autres noms lors de la recherche
   * FAQ = accordéon
   * Galerie = carrousel/diaporama
   * Navigation = menu/en-tête
* La partie bloc renvoie uniquement les entrées approuvées/traitées.

### Recherche de documentation {#searching-documentation}

Utilisez cette invite pour obtenir des informations sur les fonctionnalités de Edge Delivery Services ou des conseils d’implémentation.

#### Exemples d’invites {#example-documentation}

* « Comment mettre en œuvre le chargement différé dans Edge Delivery Services ? »
* « Recherche de métadonnées de section dans la documentation »

#### Ce qu’il faut savoir {#wtk-documentation}

* Elle effectue une recherche spécifique dans la documentation [aem.live](https://aem.live) (documents et articles de blog).
* Utilisez des mots-clés spécifiques (« décoration de bloc », « plug-in sidekick », « métadonnées ») plutôt que des termes génériques (« aem », « site web », « comment créer »).
* Pour les exemples de code et les implémentations de référence, utilisez plutôt « rechercher des blocs de référence ».
* Les dix premiers résultats les plus pertinents renvoyés par défaut.

### Tests {#testing}

Utilisez cette invite pour valider les modifications de code avant d’ouvrir une demande d’extraction.

#### Exemples d’invites {#example-testing}

* « Tester le nouveau bloc de cartes »
* « Exécuter les tests avant d’ouvrir une requête de tirage »

#### Ce qu’il faut savoir {#wtk-testing}

* Les tests suivent une philosophie de type « valeur par rapport au coût », selon laquelle vous créez et conservez des tests lorsque leur valeur dépasse le coût.
   * Les **tests de gardien** (tests unitaires) concernent les utilitaires lourds en logique, le traitement des données et les intégrations d’API. Ces éléments sont rapides, faciles à gérer et interceptent les régressions dans le code réutilisé.
   * Les **tests de suppression** (tests de navigateur) sont destinés aux transformations DOM et à la validation visuelle. Utilisez pour valider l’implémentation, capturer des captures d’écran pour la révision PR, puis ignorez.
* Les tests de suppression sont `test/tmp/` et testent le contenu dans `drafts/tmp/` (tous deux ignorés).
* Avant d’ouvrir une requête de tirage, assurez-vous que :
   * Succès des tests existants
   * Les tests unitaires sont écrits pour une nouvelle logique
   * Validation du navigateur terminée
   * Toutes les variantes sont testées
   * Le comportement réactif est vérifié.
   * Liaison de passes

### Débogage {#debugging}

Utilisez cette invite pour résoudre les problèmes liés aux blocs, aux images, aux feuilles CSS ou à la prévisualisation.

#### Exemples d’invites {#example-debugging}

* « Déboguer pourquoi les images s’affichent comme environ :error »
* « Correction du bloc principal dont le rendu n’est pas effectué »
* « Pourquoi mes modifications ne s’affichent-elles pas dans l’aperçu ? »

#### Ce qu’il faut savoir {#wtk-debugging}

* Les problèmes courants ont des schémas connus :
   * **Images montrant « about:error »** : appel `createOptimizedPicture` généralement manquant dans le bloc JS, ou appelé avant la restructuration de DOM
   * **Blocs non rendus** : vérifiez le format du nom du bloc dans Markdown et vérifiez que le bloc contient à la fois des fichiers `.js` et `.css` en `blocks/`.
   * **Le fichier CSS ne se charge pas** : vérifiez les chemins d’accès aux fichiers, l’existence du fichier CSS et l’onglet Réseau dans le navigateur.
   * **Les modifications n’apparaissent pas** : la synchronisation du code prend entre 3 et 5 secondes. Essayez une actualisation complète (Ctrl + Maj + R).
* L’agent vérifie systématiquement chaque couche :
   1. Fichiers Source
   1. Sortie générée
   1. Code du bloc
   1. Console du navigateur
* L’agent a la possibilité de vérifier les aperçus locaux à l’`http://localhost:3000`.
