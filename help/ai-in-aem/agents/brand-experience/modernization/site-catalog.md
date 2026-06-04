---
title: Compétence du catalogue de sites
description: Découvrez comment la compétence de catalogue de sites de l’agent de modernisation d’expérience effectue une analyse automatisée d’un site web existant afin de prendre en charge la planification de la migration vers Edge Delivery Services.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Developer
source-git-commit: f035a0fdbc4fe275e2af4665ba6f25292924af0f
workflow-type: tm+mt
source-wordcount: '776'
ht-degree: 0%

---


# Compétence du catalogue de sites {#site-catalog-skill}

Découvrez comment la compétence de catalogue de sites de l’agent de modernisation d’expérience effectue une analyse automatisée d’un site web existant afin de prendre en charge la planification de la migration vers Edge Delivery Services.

## Vue d’ensemble {#overview}

Les compétences en matière de catalogue de sites permettent de découvrir chaque page du site, d’identifier les modèles de page et de bloquer les variantes utilisées, de capturer des captures d’écran de chacune d’elles et de générer un lot de rapports interactifs HTML que vous pouvez parcourir dans l’onglet Aperçu de la console ou télécharger et ouvrir localement.

Les compétences vous aident ainsi que votre migration d’un projet existant vers Edge Delivery Services de la manière suivante :

* **Démarrer un projet de migration** — Exécutez les compétences avant de commencer à comprendre l’échelle du site, y compris le nombre de pages, les modèles, les variantes de bloc et les paramètres régionaux. Il établit l’inventaire de base dont dépend chaque décision en aval.
* **Estimation et planification de l’effort** — Obtenez des mesures quantifiées pour soutenir les propositions, la planification du sprint et les ressources.
* **Préparation de l’importation en bloc** — Utilisez des `template-catalog.json` pour identifier les pages partageant la même disposition et planifiez des importations en bloc modèle par modèle.
* **Rapports des parties prenantes** — Partagez le bundle de rapports interactifs HTML avec les chefs de projet, les architectes et les parties prenantes de l’entreprise.

## Appeler {#invoking}

[Dans la console de modernisation de l’expérience](/help/ai-in-aem/agents/brand-experience/modernization/console.md) utilisez un langage naturel pour demander à l’agent de cataloguer un site. Voici des exemples d’invites.

* `scope site https://www.example.com`
* `site scope https://www.example.com`
* `analyze https://www.example.com`
* `find templates on https://www.example.com`
* `discover templates on https://www.example.com`
* `catalog site https://www.example.com`
* `how many page types are there on https://www.example.com`
* `what are the layouts on https://www.example.com`
* `analyze site structure of https://www.example.com`

Vous remarquerez que le workflow de la compétence comporte quatre phases qui s’exécutent en séquence :

1. Analyser
1. Modèles
1. Réglage
1. Catalogage en bloc

Vous pouvez relire n’importe quelle phase et l’agent efface les sorties de cette phase ainsi que toutes les sorties en aval, puis reprend à partir de ce moment. Voici quelques exemples d’invites de relecture de phases.

* `Repeat analyzing` / `Redo page analysis` / `Rerun analyze pages`
* `Repeat templating` / `Redo the template discovery step` / `Restart the templating step`
* `Repeat tuning` / `Rerun tune templates` / `Redo template tuning`
* `Repeat block cataloging` / `Restart catalog block variants`

Lors de la relecture d’une phase, les phases antérieures sont conservées.

## Sortie {#output}

Lorsque la compétence termine son catalogage du site, vous recevez trois types différents de sortie.

1. **Résumé d’achèvement dans le chat** y compris les totaux (pages, modèles, variantes de bloc avec répartition EDS-mapped par rapport à répartition personnalisée), la répartition par paramètres régionaux, le pourcentage de couverture et le statut global du rapport (complet/incomplet/en échec)
1. **Groupe de rapports HTML interactifs** comme principal livrable, enregistré dans `catalog/template-catalog-report-bundle.zip`
   * Le lot contient des `template-catalog-report.html`, ainsi que toutes les captures d’écran et ressources référencées.
   * Vous pouvez télécharger le lot et l’afficher localement ou le partager.
   * Vous pouvez également demander à l’agent de `Move template-catalog-report-bundle.zip to the /content folder to render it in the preview tab. Update all references as needed.` pour afficher le rapport dans la console.
1. **Artefacts JSON structurés** en `catalog/` pour les compétences en aval et l’utilisation par programmation, y compris `summary.json`, `template-catalog.json`, `block-catalog.json`, `urls-all.json`, `urls-grouped.json`, `urls-checklist.json`, `.pages/`, `.blocks/`

### Contenu du dossier de catalogue {#contents}

Les artefacts JSON structurés sont stockés dans `catalog/` par la compétence .

| File | Description |
|---|---|
| `template-catalog-report-bundle.zip` | Rapport HTML interactif groupé (livrable principal) |
| `summary.json` | Mesures de cumul et [statut du rapport](#status) |
| `template-catalog.json` | Tous les modèles uniques avec les URL qui les utilisent (utilisés pour les imports en bloc) |
| `block-catalog.json` | Toutes les variantes de bloc avec des références de métadonnées et de capture d’écran |
| `urls-all.json` | Chaque URL découverte |
| `urls-grouped.json` | URL regroupées par motif et paramètre régional |
| `urls-sample.json` | URL représentatives échantillonnées pour l’analyse |
| `urls-checklist.json` | Statut de l’analyse par URL |
| `catalog.log` | Log d’exécution |
| `.pages/<page-slug>/page-catalog.json` | Sortie d’analyse au niveau de la page |
| `.pages/<page-slug>/full-page.jpg` | Capture d’écran pleine page |
| `.pages/<page-slug>/blocks/<block-name>.jpg` | Captures d’écran par bloc |
| `.pages/_global/header.json + header.jpg` | Analyse de l’en-tête global et capture d’écran |
| `.pages/_global/footer.json + footer.jpg` | Analyse globale des pieds de page et capture d’écran |
| `.blocks/<variantId>/metadata.json` | Bloquer les métadonnées de variante |
| `.blocks/<variantId>/screenshots/<name>.jpg` | Bloquer les captures d’écran de variantes |

### Statuts des rapports {#status}

Le champ `status` dans [`summary.json`](#contents) peut être :

| État | Signification |
|---|---|
| `complete` | Toutes les pages ont été analysées avec succès (ou le taux d’échec était de 10 % ou moins). |
| `incomplete` | Plus de 10 % des pages ont échoué ou la détection des blocs s’est bloquée sur plus de 50 % des pages. Les sorties sont toujours utilisables, mais partielles. |
| `failed` | Aucune page n’a été analysée. |

## Échantillonnage pour les grands sites {#sampling}

Par défaut, la compétence limite l’analyse approfondie de la page à 1 000 URL. Pour les sites contenant jusqu’à 1 000 URL incluses, chaque page est analysée.

Pour les sites comportant plus de 1 000 URL, l’agent se met en pause et demande comment procéder :

* Augmentez la limite d’échantillonnage (jusqu’à un maximum de 4 000 URL).
* Analyser uniquement un groupe spécifique (par exemple uniquement `/products/*` ou `/blog/*`)
* Analysez toutes les URL et exécutez le site complet sans échantillonnage

La découverte d’URL couvre toujours l’ensemble du site, quelle que soit la limite d’échantillon. Seule la phase d’analyse approfondie par page est limitée.

Pour remplacer et analyser chaque page, indiquez à l’agent :

* `analyze all URLs`
* `analyze everything`
* `analyze every page`
* `run the full site`

## Workflow d’importation en bloc {#bulk-import}

Les compétences de catalogue de sites font partie de l’approche recommandée pour migrer un site complet.

1. Exécutez les compétences du catalogue de sites pour obtenir le catalogue de modèles complet et le catalogue global.
1. Ouvrez [l’offre groupée de rapports HTML](#output) pour examiner visuellement les modèles identifiés par l’agent.
1. Pour chaque modèle, importez manuellement les pages représentatives (répertoriées dans [`template-catalog.json`](#output)) et affinez l’importation jusqu’à ce que la sortie soit correcte.
1. Importez en bloc les pages restantes pour ce modèle à l’aide de la liste d’URL de `template-catalog.json`.
1. Répétez l’opération pour chaque modèle jusqu’à ce que le site complet soit migré.

## Limites {#limitations}

La compétence de catalogue de sites présente les limites suivantes.

* **Sites publics uniquement** — La cible doit être accessible au public (pas d&#39;authentification, de VPN ou de pare-feu).
* **Le contenu dynamique n’est pas pris en charge** — Le contenu nécessitant l’interaction de l’utilisateur pour apparaître dans le DOM peut ne pas être capturé.
* **Limite de 1 000 URL par défaut** - La phase d’analyse approfondie est par défaut limitée à 1 000 URL, [qui peuvent être remplacées](#sampling) et à un maximum de 4 000 URL.
