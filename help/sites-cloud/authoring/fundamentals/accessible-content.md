---
title: Création de contenu accessible pour Adobe Experience Manager en tant que service Cloud (conformité WCAG 2.1)
description: Instructions pour rendre les contenus web plus accessibles aux personnes en situation de handicap
translation-type: tm+mt
source-git-commit: 921334705578626ac0ea75765496d4f379bb00fc

---


# Création d’un contenu accessible (conformité WCAG 2.1) {#creating-accessible-content-wcag-conformance}

Le [Web Content Accessibility Guidelines (WCAG) 2.1](https://www.w3.org/TR/WCAG/), élaboré par [un groupe de travail du World Wide Wec Consortium](https://www.w3.org/Consortium/activities#Accessibility_Guidelines_Working_Group), comprend un ensemble de lignes directrices et de critères de réussite indépendants de la technologie pour aider à rendre le contenu Web accessible aux personnes handicapées et utilisable par elles.

En introduction, le consortium fournit une série de sections et de  de soutien :

* [Nouvelles fonctionnalités de WCAG 2.1](https://www.w3.org/TR/WCAG/#new-features-in-wcag-2-1)
* [Conformité à WCAG 2.1](https://www.w3.org/WAI/WCAG21/quickref/)
* [Présentation de WCAG 2.1](https://www.w3.org/WAI/WCAG21/Understanding/)
* [Techniques relatives à WCAG 2.1](https://www.w3.org/WAI/WCAG21/Techniques/)
* [Le WCAG](https://www.w3.org/WAI/standards-guidelines/wcag/docs/)

En outre, voir :
* Our [Quick Guide to WCAG 2.1](/help/onboarding/accessibility/quick-guide-wcag.md) for further details

<!-- 
>* [Configuring the Rich Text Editor for producing accessible conten](/help/sites-administering/rte-accessible-content.md)
-->

Les lignes directrices sont classées selon trois niveaux de conformité : Niveau A (le plus faible), Niveau A et Niveau AAA (le plus élevé). En bref, les niveaux sont définis comme suit :

* **Niveau A :** votre site atteint un niveau minimum d’accessibilité. Pour atteindre ce niveau, tous les critères de réussite de niveau A sont satisfaits.
* **Niveau AA :** il s’agit d’un idéal d’accessibilité à atteindre : votre site est accessible par la plupart des personnes dans la plupart des situations à l’aide de la plupart des technologies. Pour atteindre ce niveau, tous les critères de réussite des niveaux A et AA doivent être satisfaits.
* **Niveau AAA :** votre site atteint un très haut niveau d’accessibilité. Pour atteindre ce niveau, tous les critères de réussite des niveaux A, AA et AAA sont satisfaits.

Lors de la création de votre site, vous devez déterminer à quel niveau général il doit se conformer.

La section suivante présente les [règles WCAG 2.1](https://www.w3.org/TR/WCAG/#wcag-2-layers-of-guidance) ainsi que les critères de réussite associés liés aux [niveaux de conformité](https://www.w3.org/TR/WCAG/#conformance-to-wcag-2-1) A et AA.

>[!NOTE]
>
>Il n’est pas possible, pour certains types de contenu, de satisfaire à tous les critères de réussite du niveau de conformité AAA ; celui-ci n’est donc pas recommandé à titre de politique générale.

>[!NOTE]
>
>Dans ce document, nous utilisons :
>
>* The short names for the [WCAG 2.1 Guidelines](https://www.w3.org/TR/WCAG/#wcag-2-layers-of-guidance).
>* The numbering used in the [WCAG 2.1 Guidelines](https://www.w3.org/TR/WCAG/#wcag-2-layers-of-guidance) to aid cross-referencing with the WCAG website.
>



## Principe 1 : perceptible    {#principle-perceivable}

[Principe 1 : perceptible – Les informations et les composants de l’interface utilisateur doivent être présentés aux utilisateurs sous des formes qu’ils peuvent percevoir.](https://www.w3.org/TR/WCAG/#perceivable)

### Équivalents textuels (1.1)    {#text-alternatives}

[Règle 1.1 – Les équivalents textuels : proposer des équivalents textuels à tout contenu non textuel qui pourra alors être présenté sous d’autres formes selon les besoins de l’utilisateur : grands caractères, braille, synthèse vocale, symboles ou langage simplifié.](https://www.w3.org/TR/WCAG/#text-alternatives)

### Contenu non textuel (1.1.1)    {#non-text-content}

* Critère de réussite 1.1.1
* Niveau A
* Contenu non textuel : tout contenu non textuel présenté à l’utilisateur possède un texte secondaire qui remplit une fonction équivalente sauf dans les situations énumérées ci-dessous.

#### Objectif – Contenu non textuel (1.1.1) {#purpose-non-text-content}

Le contenu d’une page web peut être proposé dans différents formats non textuels (photos, vidéos, animations, tableaux et graphiques). Les personnes aveugles ou malvoyantes ne sont pas en mesure de voir le contenu non textuel, mais elles peuvent accéder au contenu textuel en le faisant lire par un lecteur d’écran ou sous forme tactile dans un appareil d’affichage en braille. Ainsi, en proposant des équivalents textuels pour le contenu graphique, les personnes qui ne voient pas le contenu graphique peuvent accéder à une version équivalente des informations véhiculées par le contenu.

Autre avantage utile : les équivalents textuels permettent aux moteurs de recherche d’indexer le contenu non textuel.

#### Comment procéder – Contenu non textuel (1.1.1)    {#how-to-meet-non-text-content}

Pour les images statiques, la règle de base consiste à fournir un équivalent textuel, appelé texte secondaire. Vous pouvez pour ce faire utiliser le champ **Texte secondaire** :

>[!NOTE]
>
>Certains composants prêts à l’emploi, tels que **Carrousel** et **Diaporama**, ne permettent pas d’ajouter des descriptions d’images sous forme de texte de remplacement. Lors de l’implémentation de ces versions pour votre instance AEM, votre équipe de développement devra configurer ces composants pour prendre en charge l’attribut `alt` afin que les auteurs puissent l’ajouter au contenu (voir Ajout de la prise en charge d’éléments et d’attributs HTML supplémentaires).

<!--
>Some out-of-the-box components, such as **Carousel** and **Slideshow** do not provide a means for adding alternate text descriptions to images. When implementing versions of these for your AEM instance, your development team will need to configure such components to support the `alt` attribute so that authors can add it to the content (see [Adding Support for Additional HTML Elements and Attributes](/help/sites-administering/rte-accessible-content.md#adding-support-for-additional-html-elements-and-attributes)).
-->

Dans AEM, le champ **Texte secondaire** doit être renseigné par défaut. Si votre image est purement décorative et que le texte secondaire est dénué de sens, l’option **L’image est décorative** peut être sélectionnée.

#### Création d’un texte secondaire adapté {#creating-good-text-alternatives}

Il existe diverses formes de contenu non textuel. Par conséquent, la valeur du texte secondaire dépend du rôle du graphique dans la page web. Voici quelques-unes des règles de base à respecter :

* Les textes secondaires doivent être succincts, tout en communiquant clairement l’information essentielle du contenu non textuel.
* Il est préférable d’éviter les descriptions trop longues (plus de 100 caractères). Si un texte secondaire doit être plus détaillé :
   * donnez une brève description dans le texte secondaire ;
   * proposez une description plus longue dans le texte ailleurs sur la même page ou dans une page web distincte. Renvoyez vers cette description individuelle en transformant l’image en lien ou en plaçant un lien textuel près de l’image.
* Le texte secondaire ne doit pas répliquer le contenu fourni sous forme de texte à proximité sur la même page. N’oubliez pas que nombre d’images sont des illustrations de points déjà traités dans le texte d’une page ; il existe peut-être déjà un texte secondaire.
* Si le contenu non textuel est un lien vers une autre page ou un autre document et qu’il n’existe pas de texte faisant partie dudit lien, le texte secondaire de l’image doit indiquer la destination du lien, et non décrire l’image.
* Si le contenu non textuel est contenu dans un bouton et qu’il n’existe pas de texte faisant partie dudit bouton, le texte secondaire de l’image doit indiquer la fonction du bouton, et non décrire l’image.
* Il est tout à fait acceptable de spécifier un texte secondaire vide (nul) pour une image, à condition toutefois que l’image n’ait pas besoin de texte secondaire (s’il s’agit par exemple d’une image purement décorative) ou si le texte secondaire figure déjà dans le texte de la page.

<!--
The [W3C draft: HTML5 Techniques for providing useful text alternatives](https://dev.w3.org/html5/alt-techniques/) has more details and examples of appropriate alternative text provision for images of different types.
-->

Voici quelques-uns des types spécifiques de contenu non textuel auquel un texte secondaire doit être associé :

* Photos illustratives : il s’agit de photos de personnes, d’objets ou de lieux. Pensez au rôle de la photo sur la page ; il est probable qu’un texte équivalent approprié soit `Photo of [object]`, mais cela peut dépendre du texte environnant.
* Icônes : Certains petits pictogrammes (images) communiquent parfois des informations spécifiques. Ils doivent être utilisés de manière uniforme sur une page et un site. Toutes les instances de l’icône sur une page ou un site doivent avoir le même texte secondaire bref et succinct, sauf si cela duplique de manière superflue le texte adjacent.
* Tableaux et graphiques : ils représentent généralement des données numériques. Pour proposer un texte secondaire, vous pouvez par exemple inclure un bref résumé des principales tendances affichées dans le graphique ou diagramme. Si nécessaire, fournissez une description plus détaillée du texte dans le champ **Description** de l’onglet des propriétés d’image **Avancées**. En outre, vous pouvez fournir les données sources sous forme tabulaire ailleurs dans la page ou le site.
* Cartes, diagrammes, organigrammes : pour les graphiques communiquant des données spatiales (qui illustrent par exemple les relations entre les objets ou un workflow), veillez à ce que le message clé soit fourni dans un format textuel. Pour les cartes, il est souvent difficile de fournir un équivalent textuel complet. Si toutefois la carte est fournie pour aider le destinataire du document à se rendre à un endroit particulier, le texte secondaire de l’image de la carte peut indiquer brièvement *Carte de X*, puis spécifier un itinéraire vers ce lieu dans le texte ailleurs sur la page ou dans le champ **Description** dans l’onglet **Avancé** du composant **Image**.
* CAPTCHA :
L’acronyme anglais CAPTCHA (*Completely Automated Public Turing test to tell Computers and Humans Apart*) désigne un test servant à déterminer si le contenu est consulté par une personne plutôt que par un ordinateur. Ce contrôle de sécurité utilisé sur les pages web pour distinguer les humains des logiciels malveillants peut constituer un obstacle à l’accessibilité. Il s’agit d’images obligeant les utilisateurs à décrire ce qu’ils voient pour pouvoir réussir le test de sécurité. Il n’est évidemment pas possible de fournir un équivalent textuel pour l’image. Vous devez par conséquent envisager des alternatives non graphiques.
Le W3C émet plusieurs suggestions, comme celles énumérées ci-dessous. Chacune de ces approches a ses propres avantages et inconvénients.
   * Énigmes logiques
   * Utilisation d’une sortie audio plutôt que d’images
   * Comptes d’utilisateur limités et filtres de courrier indésirable
* Images d’arrière-plan : elles impliquent l’utilisation de feuilles de style en cascade CSS (Cascading Style Sheet) plutôt que de code HTML. Il n’est donc pas possible de spécifier une valeur de texte secondaire. Par conséquent, les images d’arrière-plan ne doivent pas communiquer d’informations textuelles importantes. Sinon, ces informations doivent aussi être spécifiées dans le texte de la page. Cependant, il est important qu’un arrière-plan alternatif s’affiche si l’image ne peut pas s’afficher.

>[!NOTE]
>
>Le niveau de contraste entre l’arrière-plan et le texte au premier plan doit être suffisant. Ceci est décrit de manière plus détaillée à la section [Contraste (minimum) (1.4.3)](#contrast-minimum).

#### En savoir plus – Contenu non textuel (1.1.1)    {#more-information-non-text-content}

* [Compréhension du critère de réussite 1.1.1](https://www.w3.org/WAI/WCAG21/Understanding/non-text-content.html)
* [Comment remplir le critère de réussite 1.1.1](https://www.w3.org/WAI/WCAG21/quickref/#non-text-content)
* [Explication des CAPTCHA et alternatives par le W3C](https://www.w3.org/TR/turingtest/)

<!--
* [W3C: HTML5 Techniques for providing useful text alternatives (draft)](https://dev.w3.org/html5/alt-techniques/)
-->

### Média temporel (1.2)    {#time-based-media}

[Règle 1.2 – Média temporel : proposer des versions de remplacement aux médias temporels.](https://www.w3.org/TR/WCAG/#time-based-media)

Cette section traite du contenu web *temporel*, notamment le contenu que l’utilisateur peut lire (contenu vidéo, audio et animé, par exemple) et qui peut être pré-enregistré ou en direct.

### Audio-only and Video-only (Prerecorded) (1.2.1) {#audio-only-and-video-only-prerecorded}

* Critère de réussite 1.2.1
* Niveau A
* Contenu seulement audio ou vidéo (pré-enregistré) : pour des médias pré-enregistrés seulement audio et pré-enregistrés seulement vidéo, sauf si l’audio ou la vidéo est un média de remplacement pour un texte et qu’ils sont clairement identifiés comme tels, ce qui suit s’applique :
   * Contenu pré-enregistré seulement audio : fournir une version de remplacement pour un média temporel, présentant une information équivalente au contenu seulement audio.
   * Contenu pré-enregistré seulement vidéo : fournir, soit une version de remplacement pour un média temporel, soit une piste audio (présentant une information équivalente) pour un contenu pré-enregistré seulement vidéo.

#### Purpose - Audio-only and Video-only (Prerecorded) (1.2.1) {#purpose-audio-only-and-video-only-prerecorded}

Les personnes suivantes peuvent éprouver des problèmes à accéder au contenu vidéo et audio :

* Les personnes malvoyantes lorsqu’il n’y a aucune piste audio ou si la piste audio ne suffit pas à les informer de ce qui se passe dans la vidéo ou l’animation.
* Les personnes malentendantes ou sourdes, qui ne peuvent pas écouter la piste audio.
* Les personnes qui peuvent écouter la piste audio, mais qui ne la comprennent pas (si par exemple elle est dans une langue qu’elles ne comprennent pas).

Les personnes qui utilisent des navigateurs ou des périphériques qui ne prennent pas en charge la lecture du contenu dans des formats multimédias spécifiques (Adobe Flash par exemple) peuvent aussi ne pas avoir accès au contenu vidéo ou audio.

En proposant ces informations dans un autre format (texte par exemple, ou audio pour un contenu vidéo sans audio), elles seront accessibles par les personnes qui ne sont pas en mesure d’accéder au contenu original.

#### How to Meet - Audio-only and Video-only (Prerecorded) (1.2.1) {#how-to-meet-audio-only-and-video-only-prerecorded}

* Si le contenu est un contenu audio pré-enregistré sans vidéo (podcast par exemple) :
   * Fournissez un lien immédiatement avant ou après le contenu vers une transcription textuelle du contenu audio.
La transcription doit être une page HTML avec un équivalent textuel de tout le contenu non parlé important et parlé, et indiquer en outre qui parle, avec les expressions vocales et une description du décor et de tout autre contenu audio significatif.
* Si le contenu est une animation ou une vidéo pré-enregistrée sans audio :
   * Fournissez un lien immédiatement avant ou après le contenu vers une description textuelle équivalente des informations communiquées par la vidéo.
   * Ou fournissez une audio-description équivalente dans un format audio fréquemment utilisé (MP3 par exemple).

>[!NOTE]
>
>Si le contenu audio ou vidéo est fourni comme alternative au contenu qui existe déjà dans un autre format sur une page web, il n’est pas nécessaire d’adhérer aux exigences ci-dessus. Si, par exemple, une vidéo illustre une liste d’instructions textuelles, il n’est pas nécessaire d’ajouter un équivalent puisque les instructions textuelles agissent comme équivalent de la vidéo.

L’ajout de contenu multimédia (Flash notamment) dans vos pages web AEM revient à ajouter une image. Toutefois, puisque le contenu multimédia représente bien davantage qu’une image fixe, il existe différents paramètres et options pour contrôler la lecture du multimédia.

>[!NOTE]
>
>Si vous utilisez un contenu multimédia informatif, vous devez également créer des liens vers les équivalents. Par exemple, pour inclure une transcription textuelle, créez une page HTML où afficher la transcription, puis ajoutez un lien en regard ou en dessous du contenu audio.

#### More Information - Audio-only and Video-only (Prerecorded) (1.2.1) {#more-information-audio-only-and-video-only-prerecorded}

* [Compréhension du critère de réussite 1.2.1](https://www.w3.org/WAI/WCAG21/Understanding/audio-only-and-video-only-prerecorded.html)
* [Comment remplir le critère de réussite 1.2.1](https://www.w3.org/WAI/WCAG21/quickref/#audio-only-and-video-only-prerecorded)

### Légendes (préenregistrées) (1.2.2) {#captions-prerecorded}

* Critère de réussite 1.2.2
* Niveau A
* Sous-titres (pré-enregistrés) : fournir des sous-titres pour tout contenu audio pré-enregistré dans un média synchronisé, excepté lorsque le média est un média de remplacement pour un texte et qu’il est clairement identifié comme tel.

#### Objet - Légendes (préenregistrées) (1.2.2) {#purpose-captions-prerecorded}

Les personnes sourdes ou malentendantes n’auront pas accès au contenu audio, ou y auront accès avec de grandes difficultés. Les sous-titres sont des équivalents textuels au contenu audio parlé et non parlé ; ils s’affichent à l’écran au moment approprié durant la vidéo. Ils permettent aux personnes qui ne peuvent pas écouter le contenu audio de comprendre ce qui se passe.

>[!NOTE]
>
>Les sous-titres ne sont pas obligatoires s’il existe déjà des équivalents textuels ou non textuels adaptés (qui fournissent directement des informations équivalentes) sur la même page que la vidéo ou l’animation.

#### How to Meet - Captions (Prerecorded) (1.2.2) {#how-to-meet-captions-prerecorded}

Les sous-titres peuvent être :

* Ouvrir : toujours visible lors de la lecture de la vidéo
* Non intégrés : les sous-titres peuvent être activés ou désactivés par l’utilisateur.

Ajoutez des sous-titres non intégrés chaque fois que cela est possible, car les utilisateurs peuvent ainsi décider s’ils souhaitent les afficher.

Pour les sous-titres non intégrés, vous devez créer et fournir un fichier de sous-titrage synchronisé dans un format approprié ([SMIL](https://www.w3.org/AudioVideo/) par exemple) avec le fichier vidéo (la procédure à suivre pour ce faire ne fait pas l’objet de ce guide, mais vous trouverez des liens vers des didacticiels sous [En savoir plus – Sous-titres (pré-enregistrés) (1.2.2)](#more-information-captions-pre-recorded)). Pensez à inclure une note avisant les utilisateurs que des sous-titres sont disponibles pour la vidéo.

Si vous devez utiliser des sous-titres intégrés, incorporez le texte à la piste vidéo. Pour ce faire, utilisez des applications de montage vidéo qui permettent de superposer du texte sur la vidéo.

#### More Information - Captions (PreRecorded) (1.2.2) {#more-information-captions-prerecorded}

* [Compréhension du critère de réussite 1.2.2](https://www.w3.org/WAI/WCAG21/Understanding/captions-prerecorded.html) :
* [Comment remplir le critère de réussite 1.2.2](https://www.w3.org/WAI/WCAG21/quickref/#captions-prerecorded)

<!--
* [W3C: Synchronized Multimedia](https://www.w3.org/AudioVideo/)
* [Captions, Transcripts, and Audio Descriptions - by WebAIM](https://webaim.org/techniques/captions/)
-->

### Audio Description or Media Alternative (Prerecorded) (1.2.3) {#audio-description-or-media-alternative-prerecorded}

* Critère de réussite 1.2.3
* Niveau A
* Audio-description ou version de remplacement pour un média temporel (pré-enregistré) : fournir une version de remplacement pour un média temporel ou une audio-description du contenu vidéo pré-enregistré pour un média synchronisé, excepté quand le média est un média de remplacement pour un texte et qu’il est clairement identifié comme tel.

#### Purpose - Audio Description or Media Alternative (Prerecorded) (1.2.3) {#purpose-audio-description-or-media-alternative-prerecorded}

Les personnes aveugles ou malvoyantes ne pourront pas accéder au contenu si les informations dans une vidéo ou une animation sont fournies sous forme visuelle seulement ou si la piste audio ne fournit pas suffisamment d’informations pour comprendre ce qui se passe visuellement.

#### How to Meet - Audio Description or Media Alternative (Prerecorded) (1.2.3) {#how-to-meet-audio-description-or-media-alternative-prerecorded}

Deux approches peuvent être adoptées pour remplir ce critère de réussite. Les deux sont acceptables :

1. Inclure une audio-description supplémentaire pour le contenu vidéo. Vous pouvez y parvenir de trois façons :
   * Durant les pauses dans le dialogue existant, fournissez des informations sur les modifications dans la scène qui ne sont pas présentées dans la piste audio existante.
   * Fournissez une nouvelle piste audio supplémentaire et facultative contenant la piste audio originale, mais aussi des informations audio supplémentaires sur les modifications dans la scène.
      * Les utilisateurs peuvent ainsi permuter entre la piste audio existante (qui ne contient *pas* de description audio) et la nouvelle piste audio (qui *comprend* une description audio).
      * De cette façon, les utilisateurs qui n’ont pas besoin de la description supplémentaire ne sont pas interrompus.
   * Créez une deuxième version du contenu vidéo afin d’y inclure des audio-descriptions plus détaillées. Ceci réduit les difficultés associées à la spécification d’audio-descriptions détaillées dans les intervalles au sein du dialogue existant, en interrompant temporairement l’audio et la vidéo à des points appropriés. Vous pouvez ainsi ajouter une audio-description beaucoup plus longue avant que l’action ne recommence. Comme dans l’exemple précédent, il est préférable de proposer une piste audio supplémentaire facultative afin d’éviter toute interruption pour les utilisateurs qui n’ont pas besoin du contenu supplémentaire.
1. Fournissez une transcription textuelle qui est un équivalent textuel adapté des éléments audio et visuels de la vidéo ou de l’animation. Il peut s’agir, si cela est approprié, d’une indication précisant qui parle, d’une description du décor ou d’expressions vocales. Selon sa durée, vous pouvez placer la transcription sur la même page que la vidéo ou animation, ou sur une autre page ; dans le deuxième cas, fournissez un lien vers la transcription près de la vidéo ou de l’animation.

Les détails exacts de la création de vidéos avec description audio ne sont pas compris dans ce guide. La création de descriptions vidéo et audio peut prendre du temps, mais d’autres produits Adobe peuvent vous aider à accomplir ces tâches. Si vous créez du contenu dans Adobe Flash Professional, vous devez également créer un script pour inviter l’utilisateur à télécharger le plug-in approprié et fournir un texte secondaire via l’élément `<noscript>`.

#### More Information - Audio Description or Media Alternative (Prerecorded) (1.2.3) {#more-information-audio-description-or-media-alternative-prerecorded}

* [Compréhension du critère de réussite 1.2.3](https://www.w3.org/WAI/WCAG21/Understanding/audio-description-or-media-alternative-prerecorded.html) :
* [Comment remplir le critère de réussite 1.2.3](https://www.w3.org/WAI/WCAG21/quickref/#audio-description-or-media-alternative-prerecorded)
* [Adobe Encore](https://www.adobe.com/products/encore.html)

### Sous-titres (en direct) (1.2.4)        {#captions-live}

* Critère de réussite 1.2.4
* Niveau AA
* Sous-titres (en direct) : fournir des sous-titres pour tout contenu audio en direct, sous forme de média synchronisé.

#### Objectif – Sous-titres (en direct) (1.2.4)    {#purpose-captions-live}

Ce critère de réussite est identique aux [Sous-titres (pré-enregistrés)](#captions-pre-recorded), du fait qu’il résout les obstacles à l’accessibilité pour les personnes sourdes ou malentendantes ; toutefois, ce critère de réussite traite des présentations en direct du type webcasts.

#### Comment procéder – Sous-titres (en direct) (1.2.4) {#how-to-meet-captions-live}

Follow the guidance provided for [Captions (Prerecorded)](#captions-prerecorded) above. However, due to the live nature of the media, caption provision has to be created as quickly as possible and in response to what is happening. Therefore, you should consider using real time captioning or speech-to-text tools.

Ce document ne vise pas à fournir des instructions détaillées à ce sujet, mais vous trouverez des renseignements utiles en suivant les liens ci-après :

* [WebAIM : Real Time Captioning (sous-titrage en temps réel ; en anglais)](https://www.webaim.org/techniques/captions/realtime.php)

<!--
* [AccessIT (University of Washington): Can captions be generated automatically using speech recognition?](https://www.washington.edu/accessit/articles?1209)
-->

#### En savoir plus – Sous-titres (en direct) (1.2.4)    {#more-information-captions-live}

* [Compréhension du critère de réussite 1.2.4](https://www.w3.org/WAI/WCAG21/Understanding/captions-live.html)
* [Comment remplir le critère de réussite 1.2.4](https://www.w3.org/WAI/WCAG21/quickref/#captions-live)

### Description audio (préenregistrée) (1.2.5) {#audio-description-prerecorded}

* Critère de réussite 1.2.5
* Niveau AA
* Audio-description (pré-enregistrée) : fournir une audio-description pour tout contenu vidéo pré-enregistré, sous forme de média synchronisé.

#### Purpose - Audio Description (Prerecorded) (1.2.5) {#purpose-audio-description-prerecorded}

This success criterion is identical to [Audio Description or Media Alternative (Prerecorded)](#audio-description-or-media-alternative-prerecorded), except that authors must provide a much more detailed audio description to conform to Level AA.

#### How to Meet - Audio Description (Prerecorded) (1.2.5) {#how-to-meet-audio-description-prerecorded}

Follow the guidance provided for [Audio Description or Media Alternative (Prerecorded)](#audio-description-or-media-alternative-prerecorded).

#### More Information - Audio Description (Prerecorded) (1.2.5) {#more-information-audio-description-prerecorded}

* [Compréhension du critère de réussite 1.2.5](https://www.w3.org/WAI/WCAG21/Understanding/audio-description-prerecorded.html)
* [Comment remplir le critère de réussite 1.2.5](https://www.w3.org/WAI/WCAG21/quickref/#audio-description-prerecorded)

### Adaptable (1.3)    {#adaptable}

[Règle 1.3 – Adaptable : créer un contenu qui puisse être présenté de différentes manières sans perte d’information ni de structure (par exemple avec une mise en page simplifiée).](https://www.w3.org/TR/WCAG/#adaptable)

Cette règle couvre les exigences nécessaires pour aider les personnes qui :

* peuvent ne pas être en mesure d’accéder aux informations présentées par un auteur dans une mise en page web colorée, à plusieurs colonnes et bidimensionnelle standard ;

* utilisent peut-être un contenu audio uniquement ou un affichage visuel de remplacement, par exemple un contraste élevé ou une grande taille de texte.

### Informations et relations (1.3.1)        {#info-and-relationships}

* Critère de réussite 1.3.1
* Niveau A
* Informations et relations : l’information, la structure et les relations véhiculées par la présentation peuvent être déterminées par un programme informatique ou sont disponibles sous forme de texte.

#### Objectif – Informations et relations (1.3.1)    {#purpose-info-and-relationships}

Nombre des technologies d’assistance auxquelles ont recours les personnes en situation de handicap ont recours à des informations structurelles pour afficher ou restituer efficacement le contenu. Ces informations structurelles peuvent se présenter sous forme de titres de page, de titres de lignes et de colonnes de tableau et de types de liste. Par exemple, un utilisateur peut recourir à un lecteur d’écran pour parcourir une page d’un titre à un autre. Si, toutefois, le contenu d’une page semble avoir une structure de style visuel uniquement, plutôt qu’un code HTML sous-jacent, aucune information structurelle n’est disponible pour les technologies d’assistance, ce qui limite leur capacité à faciliter la navigation.

Ce critère de réussite vise à garantir que de telles informations structurelles sont fournies dans le code HTML, de sorte que les navigateurs et les technologies d’assistance puissent accéder à l’information et l’exploiter.

#### Comment procéder – Informations et relations (1.3.1)    {#how-to-meet-info-and-relationships}

AEM facilite la construction de pages web à l’aide des éléments HTML appropriés. Ouvrez le contenu de la page dans l’éditeur de texte enrichi (un composant Texte) et, à l’aide du menu **Paraformat** (symbole du paragraphe), spécifiez l’élément structurel approprié (paragraphe, en-tête, etc.).

Veillez à ce que vos pages web aient la structure appropriée comme suit :

* **Utilisation des en-têtes :** tant que les fonctionnalités d’accessibilité du RTE sont activées, AEM offre 3 niveaux d’en-tête de page. Vous pouvez les utiliser pour identifier les sections et sous-sections de contenu. En-tête 1 est le plus haut niveau d’en-tête, En-tête 3 le plus bas. L’administrateur système peut configurer le système pour autoriser l’utilisation d’un plus grand nombre de niveaux d’en-tête.
* **Texte mis en évidence** : utilisez l’élément `<strong>` ou `<em>` pour indiquer la mise en évidence. N’utilisez pas d’en-têtes pour mettre le texte en évidence au sein des paragraphes.
   * Surlignez le texte à mettre en évidence.
   * Cliquez sur l’icône **B** (pour `<strong>`) ou **I** (pour `<em>`) du panneau **Propriétés** (HTML doit être sélectionné).

      >[!NOTE]
      >
      >Dans une installation AEM standard, l’éditeur de texte enrichi est configuré pour utiliser :
      >
      >* `<b>` pour `<strong>`
      >* `<i>` pour `<em>`
      >
      >Ils sont identiques dans la pratique, mais `<strong>` et `<em>` sont préférables, car il s’agit de code HTML correct sémantiquement. Votre équipe de développement peut configurer l’éditeur de texte enrichi pour qu’il utilise `<strong>` et `<em>` (au lieu de `<b>` et `<i>`) lors du développement de votre instance de projet.


* **Listes** : vous pouvez spécifier trois différents types de listes en HTML :
   * L’élément `<ul>` est utilisé pour les listes *non triées* (à puces). Les éléments de liste individuels sont identifiés à l’aide de l’élément `<li>`. Dans l’éditeur de texte enrichi, utilisez l’icône **Liste à puces**.
   * L’élément `<ol>` est utilisé pour les listes *numérotées*. Les éléments de liste individuels sont identifiés à l’aide de l’élément `<li>`. Dans l’éditeur de texte enrichi, cliquez sur l’icône **Liste numérotée**.
   Pour modifier un contenu existant en un type de liste particulier, sélectionnez-le, puis choisissez le type de liste approprié. Comme dans l’exemple précédent illustrant la saisie du texte du paragraphe, les éléments de liste appropriés sont automatiquement ajoutés au fichier HTML.

   En mode Plein écran, les icônes **Liste à puces** et **Liste numérotée** sont visibles. Lorsque vous n’êtes pas en mode Plein écran, les deux options sont disponibles derrière l’icône **Listes** unique.
* **Utiliser des tableaux** : les tableaux de données doivent être identifiés à l’aide des éléments de tableau HTML :
   * un élément `<table>` ;
   * un élément `<tr>` pour chaque ligne du tableau ;
   * un élément `<th>` pour chaque en-tête de ligne et de colonne ;
   * un élément `<td>` pour chaque cellule de données.
   En outre, les tableaux accessibles utilisent les éléments et attributs suivants :

   * L’élément `<caption>` sert à fournir une légende visible pour le tableau. Les légendes apparaissent par défaut centrées au-dessus du tableau, mais peuvent être positionnées de manière appropriée à l’aide de CSS. La légende est associée au tableau par programmation, ce qui en fait une méthode utile pour fournir une introduction au contenu.
   * L’élément `<summary>` aide les utilisateurs non voyants à comprendre plus facilement les informations présentées dans un tableau, en fournissant une synthèse de ce qu’un utilisateur voyant peut voir. Cela s’avère particulièrement utile lorsque des mises en page de tableau complexes ou non conventionnelles sont utilisées (cet attribut n’est pas affiché dans le navigateur, il est uniquement lu pour les technologies d’assistance).
   * L’attribut `scope` de l’élément `<th>` sert à indiquer si une cellule représente un en-tête pour une ligne ou une colonne particulière. Une approche similaire consiste à utiliser les attributs header et id dans des tableaux complexes, où les cellules de données peuvent être associées à un ou plusieurs en-têtes.
   >[!NOTE]
   >
   >Par défaut, ces éléments et attributs ne sont pas directement disponibles, mais l’administrateur du système peut ajouter la prise en charge de ces valeurs dans la boîte de dialogue **Propriétés du tableau** (voir Ajout de la prise en charge des éléments et attributs HTML supplémentaires).

<!-- removed link syntax for ExL - Bob Bringhurst
>By default, these elements and attributes are not directly available, though it is possible for the system administrator to add support for these values in the **Table properties** dialog box (see Adding Support for Additional HTML Elements and Attributes /help/sites-administering/rte-accessible-content.md#adding-support-for-additional-html-elements-and-attributes).
-->

Pour ouvrir la boîte de dialogue **Tableau** dans laquelle vous pouvez sélectionner l’onglet **Propriétés** du tableau :

* Définissez une **légende** appropriée.
* Idéalement, supprimez toutes les valeurs par défaut pour **Largeur**, **Hauteur**, **Bordure**, **Marge intérieure des cellules** et **Espacement des cellules**. En effet, ces propriétés peuvent être définies dans une feuille de style globale.

Vous pouvez ensuite utiliser les **propriétés de cellule** pour définir si la cellule est une cellule de données ou d’en-tête :

* **Tableaux de données complexes** : dans certains cas, lorsqu’il existe des tableaux complexes comportant deux niveaux d’en-tête ou plus, les propriétés de tableau de base peuvent ne pas suffire à fournir toutes les informations structurelles nécessaires. Pour ce type de tableaux complexes, il est nécessaire de créer des relations directes entre les en-têtes et leurs cellules associées à l’aide des attributs **header** et **id**. Par exemple, dans le tableau ci-dessous, les attributs header et id correspondent pour créer une association de programmation pour les utilisateurs de technologies d’assistance.

   >[!NOTE]
   >
   >L’attribut id n’est pas disponible dans une installation prête à l’emploi. Il peut être activé en configurant les règles HTML et le sérialiseur dans l’éditeur de texte enrichi.

```xml
 <table>
    <tr>
      <th rowspan="2" id="h">Homework</th>
      <th colspan="3" id="e">Exams</th>
      <th colspan="3" id="p">Projects</th>
    </tr>
    <tr>
      <th id="e1" headers="e">1</th>
      <th id="e2" headers="e">2</th>
      <th id="ef" headers="e">Final</th>
      <th id="p1" headers="p">1</th>
      <th id="p2" headers="p">2</th>
      <th id="pf" headers="p">Final</th>
    </tr>
    <tr>
     <td headers="h">15%</td>
     <td headers="e e1">15%</td>
     <td headers="e e2">15%</td>
     <td headers="e ef">20%</td>
     <td headers="p p1">10%</td>
     <td headers="p p2">10%</td>
     <td headers="p pf">15%</td>
    </tr>
   </table>
```

Pour y parvenir dans AEM, vous devez ajouter la balise directement en mode d’édition de la source.

>[!NOTE]
>
>Cette fonctionnalité n’est pas immédiatement disponible dans une installation standard. Vous devez configurer les règles HTML et le sérialiseur dans l’éditeur de texte enrichi.

#### En savoir plus – Informations et relations (1.3.1) {#more-information-info-and-relationships}

* [Compréhension du critère de réussite 1.3.1](https://www.w3.org/WAI/WCAG21/Understanding/info-and-relationships.html)
* [Comment remplir le critère de réussite 1.3.1](https://www.w3.org/WAI/WCAG21/quickref/#info-and-relationships)

### Séquence significative (1.3.2) {#meaningful-sequence}

* Critère de réussite 1.3.2
* Niveau A
* Séquence significative : Lorsque la séquence dans laquelle le contenu est présenté affecte sa signification, une séquence de lecture correcte peut être déterminée par programmation.

#### Objet - Séquence significative (1.3.2) {#purpose-meaningful-sequence}

Ce critère de réussite vise à permettre à un agent utilisateur de proposer une autre présentation du contenu tout en préservant l’ordre de lecture nécessaire pour comprendre la signification. Il est important de pouvoir déterminer par programmation au moins une séquence du contenu qui a du sens. Le contenu qui ne répond pas à ce critère de réussite peut embrouiller ou désorienter les utilisateurs lorsque la technologie d’assistance lit le contenu dans le mauvais ordre, ou lorsque des feuilles de style ou d’autres modifications de mise en forme sont appliquées.

#### Comment se rencontrer - Séquence significative (1.3.2) {#how-to-meet-meaningful-sequence}

Suivez les lignes directrices sous [Comment répondre aux critères de réussite 1.3.2](https://www.w3.org/WAI/WCAG21/quickref/#meaningful-sequence).

#### Plus d&#39;informations - Séquence significative (1.3.2) {#more-information-meaningful-sequence}

* [Compréhension du critère de réussite 1.3.2](https://www.w3.org/WAI/WCAG21/Understanding/meaningful-sequence.html)
* [Comment remplir le critère de réussite 1.3.2](https://www.w3.org/WAI/WCAG21/quickref/#meaningful-sequence)

### Caractéristiques sensorielles (1.3.3)        {#sensory-characteristics}

* Critère de réussite 1.3.3
* Niveau A
* Caractéristiques sensorielles : les instructions données pour la compréhension et l’utilisation du contenu ne doivent pas reposer uniquement sur les caractéristiques sensorielles des éléments comme la forme, la taille, l’emplacement visuel, l’orientation ou le son.

#### Objectif – Caractéristiques sensorielles (1.3.3)    {#purpose-sensory-characteristics}

Les concepteurs concentrent généralement leurs efforts sur le côté visuel (couleur, forme, style du texte ou position absolue ou relative d’un élément du contenu) de la présentation des informations. Même s’il peut s’agir de techniques de conception très efficaces pour véhiculer l’information, les personnes aveugles ou malvoyantes peuvent ne pas être en mesure d’accéder à l’information nécessitant une identification visuelle des attributs (position, couleur ou forme, par exemple).

De même, les informations qui impliquent de distinguer différents sons (contenu verbalisé par un homme ou une femme, par exemple) présentent un obstacle à l’accessibilité pour les personnes malentendantes si elles ne sont pas reproduites dans un équivalent textuel du contenu audio.

>[!NOTE]
>
>Pour connaître les conditions requises en rapport avec les alternatives aux couleurs, voir [Utilisation de la couleur](#use-of-color).

#### Comment procéder – Caractéristiques sensorielles (1.3.3)    {#how-to-meet-sensory-characteristics}

Veillez à ce que les informations qui reposent sur des caractéristiques visuelles du contenu de la page soient également présentées dans un autre format.

* Ne vous fiez pas à la seule position visuelle pour transmettre une information. Si, par exemple, vous souhaitez renvoyer les utilisateurs à un menu sur le côté droit de la page pour accéder à d’autres informations, ne renvoyez pas au *menu à droite* ; nommez plutôt le menu (par exemple au moyen d’un titre) et faites référence à ce nom dans le texte.
* Ne vous fiez pas au style de texte (gras ou italique par exemple) comme seul moyen de transmettre l’information.

>[!NOTE]
>
>L’utilisation de termes descriptifs est acceptable s’ils ont une signification dans un contexte non visuel. Par exemple, les termes *ci-dessus* et *ci-dessous* sont généralement acceptables, puisqu’ils impliquent respectivement le contenu juste avant ou après un élément de contenu particulier ; ils resteront donc significatifs si le contenu est lu à haute voix.

#### En savoir plus – Caractéristiques sensorielles (1.3.3) {#more-information-sensory-characteristics}

* [Compréhension du critère de réussite 1.3.3](https://www.w3.org/WAI/WCAG21/Understanding/sensory-characteristics.html)
* [Comment remplir le critère de réussite 1.3.3](https://www.w3.org/WAI/WCAG21/quickref/#sensory-characteristics)

### Distinguable (1.4)    {#distinguishable}

[Règle 1.4 – Distinguable : faciliter la perception visuelle et auditive du contenu par l’utilisateur, notamment en séparant le premier plan de l’arrière-plan.](https://www.w3.org/TR/WCAG/#distinguishable)

### Utilisation de la couleur (1.4.1)        {#use-of-color}

* Critère de réussite 1.4.1
* Niveau A
* Utilisation de la couleur : la couleur n’est pas utilisée comme la seule façon de véhiculer de l’information, d’indiquer une action, de solliciter une réponse ou de distinguer un élément visuel.

>[!NOTE]
>
>Ce critère de réussite traite spécifiquement de la perception des couleurs. Les autres formes de perception sont traitées à la règle [Adaptable (1.3)](#adaptable), comme l’accès à la couleur par programme informatique et les autres formes de codage de la présentation visuelle.

#### Objectif – Utilisation de la couleur (1.4.1)    {#purpose-use-of-color}

La couleur est un moyen évidemment efficace d’améliorer l’aspect esthétique des pages web ; elle est également utile pour véhiculer l’information. Toutefois, en raison de différentes déficiences visuelles (de la cécité au daltonisme), certaines personnes ne sont pas capables de distinguer certaines couleurs. Par conséquent, le codage en couleurs ne constitue pas un moyen fiable de véhiculer l’information.

Par exemple, une personne qui ne distingue pas le vert du rouge ne sera pas en mesure de distinguer différentes nuances de ces couleurs. Si elle voit ces couleurs comme une troisième couleur (marron par exemple), elle ne sera pas non plus en mesure de distinguer le rouge du vert et du marron.

En outre, les personnes qui utilisent des navigateurs qui ne reconnaissent que le texte, des périphériques d’affichage monochromes ou un imprimé en noir et blanc de la page ne verront pas les couleurs.

#### Comment procéder – Utilisation de la couleur (1.4.1)    {#how-to-meet-use-of-color}

Si la couleur sert à véhiculer l’information, veillez à ce que cette information soit accessible sans recourir à la couleur.

Par exemple, assurez-vous que les informations fournies par couleur sont également fournies explicitement dans le texte.

Si la couleur est utilisée comme indice pour fournir des informations, vous devez fournir un indice visuel supplémentaire, tel que la modification du style (gras ou italique, par exemple) ou de la police. Cela aide les personnes malvoyantes ou ne percevant pas bien les couleurs à identifier l’information. Cependant, il ne peut pas être entièrement fiable, car il n’aidera pas les personnes qui ne peuvent pas voir du tout la page.

#### En savoir plus – Utilisation de la couleur (1.4.1) {#more-information-use-of-color}

* [Compréhension du critère de réussite 1.4.1](https://www.w3.org/WAI/WCAG21/Understanding/use-of-color.html)
* [Comment remplir le critère de réussite 1.4.1](https://www.w3.org/WAI/WCAG21/quickref/#use-of-color)

<!-- [Guidance on meeting a 3:1 contrast ratio, containing a list of “web safe” colors](https://www.w3.org/TR/2008/NOTE-WCAG20-TECHS-20081211/working-examples/G183/link-contrast.html)
-->

### Contrôle audio (1.4.2) {#audio-control}

* Critère de réussite 1.4.2
* Niveau A
* Contrôle audio : Si un fichier audio d&#39;une page Web est lu automatiquement pendant plus de 3 secondes, soit un mécanisme est disponible pour interrompre ou arrêter le fichier audio, soit un mécanisme est disponible pour contrôler le volume audio indépendamment du niveau de volume global du système.

#### Objet - Contrôle audio (1.4.2) {#purpose-audio-control}

Les personnes qui utilisent un logiciel de lecture d’écran peuvent avoir du mal à entendre la sortie vocale si d’autres fichiers audio sont en cours de lecture en même temps. Cette difficulté est exacerbée lorsque la sortie vocale du lecteur d’écran est basée sur un logiciel (comme la plupart le sont aujourd’hui) et est contrôlée par le même contrôle du volume que le son. Par conséquent, il est important que l’utilisateur puisse désactiver le son d’arrière-plan. Remarque : Le contrôle du volume permet de réduire son volume à zéro.

#### Procédures - Contrôle audio (1.4.2) {#how-to-meet-audio-control}

Suivez les lignes directrices sous [Comment répondre aux critères de réussite 1.4.2](https://www.w3.org/WAI/WCAG21/quickref/#audio-control).

#### Plus d&#39;informations - Contrôle audio (1.4.2) {#more-information-audio-control}

* [Compréhension du critère de réussite 1.4.2](https://www.w3.org/WAI/WCAG21/Understanding/audio-control.html)
* [Comment remplir le critère de réussite 1.4.2](https://www.w3.org/WAI/WCAG21/quickref/#audio-control)

### Contraste (minimum) (1.4.3)    {#contrast-minimum}

* Critère de réussite 1.4.3
* Niveau AA
* Contraste (minimum) : la présentation visuelle du texte et du texte sous forme d’image a un rapport de contraste d’au moins 4,5:1, sauf dans les cas suivants :
   * Texte agrandi : le texte agrandi et le texte agrandi sous forme d’image ont un rapport de contraste d’au moins 3:1.
   * Texte décoratif : aucune exigence de contraste pour le texte ou le texte sous forme d’image qui fait partie d’un composant d’interface utilisateur inactif, qui est purement décoratif, qui est invisible pour tous ou qui est une partie d’une image contenant un autre contenu significatif.
   * Logotypes : aucune exigence de contraste pour le texte faisant partie d’un logo ou d’un nom de marque.

#### Objectif – Contraste (minimum) (1.4.3)    {#purpose-contrast-minimum}

Les personnes avec certaines déficiences visuelles peuvent ne pas être en mesure de distinguer certaines paires de couleurs à faible contraste. Elles peuvent être confrontées à des obstacles à l’accessibilité si :

* Le texte est faiblement contrasté avec sa couleur d’arrière-plan.
* Le codage en couleurs du texte (par exemple entre le texte du lien et le texte en dehors du lien) joue un rôle pour distinguer l’information.

>[!NOTE]
>
>Le texte simplement décoratif est exclu de ce critère de réussite.

#### Comment procéder – Contraste (minimum) (1.4.3)    {#how-to-meet-contrast-minimum}

Veillez à ce que le texte soit suffisamment contrasté par rapport à son arrière-plan. Les rapports de contraste dépendent de la taille et du style du texte en question :

* Pour le texte de moins de 18 points (ou 14 points en gras), le rapport de contraste entre le texte/les images de texte et l’arrière-plan doit être d’au moins 4.5:1.
* Pour le texte de 18 points (ou 14 points en gras) au moins, le rapport de contraste doit être d’au moins 3:1.
* Si un arrière-plan a un motif, l’arrière-plan autour du texte doit être ombré, de sorte que le rapport de 4,5:1 ou 3:1 soit préservé.

Pour vérifier les rapports de contraste, utilisez un outil de contraste des couleurs, tel que l’[analyseur de contraste des couleurs du groupe Paciello](https://www.paciellogroup.com/resources/contrast-analyser.html) ou l’[outil de vérification du contraste des couleurs de webAIM](https://www.webaim.org/resources/contrastchecker/), afin de vérifier les paires de couleurs et de signaler les éventuels problèmes de contraste.

Par ailleurs, si l’aspect de votre page n’est pas un souci majeur, vous avez la possibilité de ne spécifier aucune couleur de texte de premier plan ou d’arrière-plan. Dans ce cas, il n’est pas nécessaire de vérifier le contraste, puisque le navigateur de l’utilisateur déterminera les couleurs du texte et de l’arrière-plan.

S’il n’est pas possible d’obtenir les niveaux de contraste recommandés, vous devez fournir un lien vers une version équivalente alternative de la page (qui ne présente aucun problème de contraste des couleurs) ou permettre à l’utilisateur de régler le contraste du jeu de couleurs de la page selon ses besoins.

#### En savoir plus – Contraste (minimum) (1.4.3)    {#more-information-contrast-minimum}

* [Compréhension du critère de réussite 1.4.3](https://www.w3.org/WAI/WCAG21/Understanding/contrast-minimum.html)
* [Comment remplir le critère de réussite 1.4.3](https://www.w3.org/WAI/WCAG21/quickref/#contrast-minimum)

### Redimensionner le texte (1.4.4) {#resize-text}

* Critère de réussite 1.4.4
* Niveau A
* Redimensionner le texte : A l’exception des légendes et des images de texte, le texte peut être redimensionné sans assistance technique jusqu’à 200 % sans perte de contenu ou de fonctionnalité.

#### Objet - Redimensionner le texte (1.4.4) {#purpose-resize-text}

Le but de ce critère de réussite est de s’assurer que le texte rendu visuellement, y compris les contrôles basés sur le texte (caractères de texte qui ont été affichés pour être visibles [et caractères de texte qui sont encore sous forme de données telles que ASCII]), puisse être mis à l’échelle avec succès afin qu’il puisse être lu directement par les personnes ayant des déficiences visuelles légères, sans avoir à recourir à une technologie d’assistance telle qu’agrandisseur. Les utilisateurs peuvent bénéficier de la mise à l&#39;échelle de tout le contenu de la page Web, mais le texte est essentiel.

#### Procédures à suivre - Redimensionner le texte (1.4.4) {#how-to-meet-resize-text}

Suivez les lignes directrices sous [Comment répondre aux critères de réussite 1.4.4](https://www.w3.org/WAI/WCAG21/quickref/#resize-text).

#### Plus d&#39;informations - Redimensionner le texte (1.4.4) {#more-information-resize-text}

* [Compréhension du critère de réussite 1.4.4](https://www.w3.org/WAI/WCAG21/Understanding/resize-text.html)
* [Comment remplir le critère de réussite 1.4.4](https://www.w3.org/WAI/WCAG21/quickref/#resize-text)

### Texte sous forme d’image (1.4.5)    {#images-of-text}

* Critère de réussite 1.4.5
* Niveau AA
* Texte sous forme d’image : si les technologies utilisées peuvent réaliser la présentation visuelle, du texte est utilisé pour véhiculer l’information plutôt que du texte sous forme d’image sauf dans les cas suivants :
   * Personnalisable : le texte sous forme d’image peut être personnalisé visuellement selon les exigences de l’utilisateur.
   * Essentielle : une présentation spécifique du texte est essentielle à l’information véhiculée.

>[!NOTE]
>
>Les logotypes (le texte qui fait partie d’un logo ou d’un nom de marque) sont considérés comme essentiels.

#### Objectif – Texte sous forme d’image (1.4.5)    {#purpose-images-of-text}

Le texte sous forme d’image est souvent utilisé lorsqu’un style particulier de texte est nécessaire, tel un logotype ou si le texte a été généré à partir d’une autre source (par exemple la copie numérisée d’un document papier). Toutefois, par rapport au texte présenté en code HTML ou stylisé à l’aide d’une feuille de style CSS, il n’est pas possible de modifier la taille ou l’aspect du texte sous forme d’image, ce qui peut être nécessaire pour les personnes malvoyantes ou ayant des difficultés de lecture.

#### Comment procéder – Texte sous forme d’image (1.4.5)    {#how-to-meet-images-of-text}

Si des images de texte doivent être utilisées, utilisez CSS pour remplacer les images de texte par du texte équivalent en HTML afin que le texte soit disponible de manière personnalisable. Pour un exemple sur la manière d’y parvenir, reportez-vous à [C30: Using CSS to replace text with images of text and providing user interface controls to switch](https://www.w3.org/TR/2008/NOTE-WCAG20-TECHS-20081211/C30).

#### En savoir plus – Texte sous forme d’image (1.4.5) {#more-information-images-of-text}

* [Compréhension du critère de réussite 1.4.5](https://www.w3.org/WAI/WCAG21/Understanding/images-of-text.html)
* [Comment remplir le critère de réussite 1.4.5](https://www.w3.org/WAI/WCAG21/quickref/#images-of-text)

## Principe 2 : utilisable    {#principle-operable}

[Principe 2 : utilisable – Les composants de l’interface utilisateur et de navigation doivent être utilisables.](https://www.w3.org/TR/WCAG/#operable)

### Clavier accessible (2.1) {#keyboard-accessible}

[Ligne directrice 2.1 Clavier accessible : Rendre toutes les fonctionnalités disponibles à partir d’un clavier.](https://www.w3.org/TR/WCAG/#keyboard-accessible)

Il s’agit de veiller à ce que les utilisateurs puissent accéder à toutes les fonctionnalités à l’aide d’un clavier.

### Clavier (2.1.1) {#keyboard}

* Critère de réussite 2.1.1
* Niveau A
* Clavier : Toutes les fonctionnalités du contenu sont exploitables par le biais d’une interface clavier sans nécessiter de temps spécifique pour les frappes de touches individuelles, sauf lorsque la fonction sous-jacente nécessite une entrée qui dépend du chemin d’accès du mouvement de l’utilisateur et pas seulement des points de fin.

#### Objet - Clavier (2.1.1) {#purpose-keyboard}

Ce critère de réussite vise à garantir que, dans la mesure du possible, le contenu peut être exploité par le biais d’un clavier ou d’une interface de clavier (de sorte qu’un autre clavier puisse être utilisé). Lorsque le contenu peut être exploité par le biais d’un clavier ou d’un autre clavier, il est exploitable par des personnes sans vision (qui ne peuvent pas utiliser des appareils tels que des souris qui nécessitent une coordination visuelle), ainsi que par des personnes qui doivent utiliser d’autres claviers ou des périphériques d’entrée qui agissent comme des émulateurs de clavier. Les émulateurs de clavier comprennent des logiciels d&#39;entrée vocale, des logiciels de prise en charge, des claviers à l&#39;écran, des logiciels de numérisation et diverses technologies d&#39;assistance et des claviers alternatifs. Les personnes à faible vision peuvent également avoir des difficultés à suivre un pointeur et trouver l&#39;utilisation du logiciel beaucoup plus facile (ou seulement possible) s&#39;ils peuvent le contrôler à partir du clavier.

#### Comment se rencontrer - Clavier (2.1.1) {#how-to-meet-keyboard}

Suivez les lignes directrices sous [Comment répondre aux critères de réussite 2.1.1](https://www.w3.org/WAI/WCAG21/quickref/#keyboard).

#### Plus d&#39;informations - Clavier (2.1.1) {#more-information-keyboard}

* [Compréhension du critère de réussite 2.1.1](https://www.w3.org/WAI/WCAG21/Understanding/no-keyboard-trap.html)
* [Comment remplir le critère de réussite 2.1.1](https://www.w3.org/WAI/WCAG21/quickref/#keyboard)

### Pas de recouvrement clavier (2.1.2) {#no-keyboard-trap}

* Critère de réussite 2.1.2
* Niveau A
* Pas de recouvrement clavier : Si la sélection du clavier peut être déplacée vers un composant de la page à l’aide d’une interface de clavier, la sélection peut être déplacée de ce composant à l’aide d’une interface de clavier uniquement. Si elle nécessite plus que des touches de direction ou de tabulation non modifiées ou d’autres méthodes de sortie standard, l’utilisateur est informé de la méthode de déplacement de la sélection.

#### Objet - Pas de recouvrement clavier (2.1.2) {#purpose-no-keyboard-trap}

Ce critère de réussite vise à s’assurer que le contenu ne *piège* pas la cible d’action du clavier dans les sous-sections du contenu d’une page Web. Il s’agit d’un problème courant lorsque plusieurs formats sont combinés dans une page et générés à l’aide de modules externes ou d’applications intégrées.

Il peut arriver que la fonctionnalité de la page Web limite la cible d&#39;action à une sous-section du contenu, tant que l&#39;utilisateur sait comment quitter cet état et *décapiter* la cible d&#39;action.

#### Manière de se rencontrer - Aucun recouvrement clavier (2.1.2) {#how-to-meet-no-keyboard-trap}

Suivez les lignes directrices sous [Comment répondre aux critères de réussite 2.1.2](https://www.w3.org/WAI/WCAG21/quickref/#no-keyboard-trap).

#### Plus d&#39;informations - Aucun recouvrement clavier (2.1.2) {#more-information-no-keyboard-trap}

* [Compréhension du critère de réussite 2.1.2](https://www.w3.org/WAI/WCAG21/Understanding/no-keyboard-trap.html)
* [Comment remplir le critère de réussite 2.1.2](https://www.w3.org/WAI/WCAG21/quickref/#no-keyboard-trap)

### Temps suffisant (2.2) {#enough-time}

[Ligne directrice 2.2 Assez de temps : Donnez aux utilisateurs suffisamment de temps pour lire et utiliser le contenu.](https://www.w3.org/TR/WCAG/#enough-time)

Il s’agit de veiller à ce que les utilisateurs disposent de suffisamment de temps pour lire et agir.

### Minutage ajustable (2.2.1) {#timing-adjustable}

* Critère de réussite 2.2.1
* Niveau A
* Clavier : Donnez aux utilisateurs suffisamment de temps pour lire et utiliser le contenu.

#### Objectif - Délai ajustable (2.2.1) {#purpose-timing-adjustable}

Le but de ce critère de réussite est de s&#39;assurer que les utilisateurs ayant une déficience ont le temps d&#39;interagir avec le contenu Web dans la mesure du possible. Les personnes ayant des déficiences comme la cécité, la faible vision, les troubles de la dextérité et les limitations cognitives peuvent avoir besoin de plus de temps pour lire le contenu ou pour remplir des fonctions comme remplir des formulaires en ligne. Si les fonctions Web dépendent du temps, il sera difficile pour certains utilisateurs d&#39;exécuter l&#39;action requise avant qu&#39;une limite de temps ne se produise. Cela peut rendre le service inaccessible pour eux. La conception de fonctions qui ne dépendent pas du temps aidera les personnes handicapées à accomplir ces fonctions. L’offre d’options permettant de désactiver les délais, de personnaliser les délais ou de demander plus de temps avant qu’une limite ne se produise aide les utilisateurs qui ont besoin de plus de temps que prévu pour terminer leur . Ces options sont répertoriées dans l’ordre qui sera le plus utile pour l’utilisateur. La désactivation des délais est préférable à la personnalisation des délais, ce qui est préférable à la demande de davantage de temps avant qu’une limite ne se produise.

#### Comment se conformer - Délai ajustable (2.2.1) {#how-to-meet-timing-adjustable}

Suivez les lignes directrices sous [Comment répondre aux critères de réussite 2.2.1](https://www.w3.org/WAI/WCAG21/quickref/#timing-adjustable).

#### Plus d&#39;informations - Minutage ajustable (2.2.1) {#more-information-timing-adjustable}

* [Compréhension du critère de réussite 2.2.1](https://www.w3.org/WAI/WCAG21/Understanding/timing-adjustable.html)
* [Comment remplir le critère de réussite 2.2.1](https://www.w3.org/WAI/WCAG21/quickref/#timing-adjustable)

### Mettre en pause, arrêter, masquer (2.2.2)        {#pause-stop-hide}

* Critère de réussite 2.2.2
* Niveau A
* Mettre en pause, arrêter, masquer : pour toute information en mouvement, clignotante, défilante ou mise à jour automatiquement, tous les points suivants sont vrais :
   * déplacement, clignotement, défilement : pour toute information en mouvement, clignotante ou défilante qui (a) démarre automatiquement, (b) dure plus de cinq secondes et (c) est présentée conjointement avec un autre contenu, il y a un mécanisme à la disposition de l’utilisateur pour la mettre en pause, l’arrêter ou la masquer, à moins que le mouvement, le clignotement ou le défilement s’avère un élément essentiel au bon déroulement de l’activité ; et
   * mise à jour automatique : pour toute information mise à jour automatiquement qui (a) démarre automatiquement et (b) est présentée conjointement avec un autre contenu, il y a un mécanisme à la disposition de l’utilisateur pour la mettre en pause, l’arrêter ou pour en contrôler la fréquence des mises à jour à moins que la mise à jour automatique s’avère essentielle au bon déroulement de l’activité.

Remarques :

1. Pour les exigences relatives au contenu scintillant ou flashant, se référer à la règle Ne pas concevoir de contenu susceptible de provoquer des crises (2.3).
1. Puisque tout contenu ne satisfaisant pas ce critère de réussite peut interférer avec la capacité de l’utilisateur à exploiter la page entière, tout le contenu présent dans la page web (qu’il soit utilisé pour satisfaire d’autres critères de réussite ou non) doit satisfaire ce critère de réussite. Voir [Exigence de conformité 5 : Non-interférence](https://www.w3.org/TR/WCAG20/#cc5).
1. Il n’est pas exigé que le contenu mis à jour périodiquement par logiciel ou diffusé en flux à l’agent utilisateur conserve ou présente l’information générée ou reçue entre la mise en pause et la reprise de la présentation, puisque cela peut ne pas être techniquement possible et s’avérer trompeur dans beaucoup de situations.
1. Une animation survenant dans une phase de pré-chargement ou dans une situation similaire peut être considérée comme essentielle si aucune interaction n’est permise à tous les utilisateurs durant cette phase et si l’absence d’indication de progression est susceptible de perturber les utilisateurs ou de leur faire croire que le contenu est figé ou défectueux.

#### Objectif – Mettre en pause, arrêter, masquer (2.2.2)    {#purpose-pause-stop-hide}

Certains utilisateurs peuvent être distraits par le contenu en mouvement et avoir du mal à se concentrer sur d’autres parties de la page. En outre, un tel contenu peut s’avérer difficile à lire par les personnes qui ont du mal à suivre le texte en mouvement.

#### Comment procéder – Mettre en pause, arrêter, masquer (2.2.2)    {#how-to-meet-pause-stop-hide}

Selon la nature du contenu, appliquez une ou plusieurs des suggestions ci-après lorsque vous créez des pages web qui contiennent du mouvement, flashant ou clignotant :

* Fournissez un moyen de mettre en pause le contenu défilant afin que l’utilisateur dispose de suffisamment de temps pour le lire. Par exemple, des téléscripteurs de nouvelles ou du texte automatiquement mis à jour.
* Veillez à ce que le contenu qui clignote s’arrête de clignoter après cinq secondes.
* Utilisez des technologies appropriées pour afficher le contenu clignotant pouvant être désactivé par le navigateur. Par exemple, des fichiers GIF (Graphics Interchange Format) ou APNG (Animated Portable Network Graphics).
* Fournissez un contrôle de formulaire sur la page web permettant à l’utilisateur de désactiver tout le contenu clignotant sur la page.
* Si aucune des solutions ci-dessus n’est possible, fournissez un lien vers une page avec tout le contenu mais sans aucun clignotement.

#### En savoir plus – Mettre en pause, arrêter, masquer (2.2.2)    {#more-information-pause-stop-hide}

* [Compréhension du critère de réussite 2.2.2](https://www.w3.org/WAI/WCAG21/Understanding/pause-stop-hide.html)
* [Comment remplir le critère de réussite 2.2.2](https://www.w3.org/WAI/WCAG21/quickref/#pause-stop-hide)

### Saisies et réactions physiques (2.3) {#seizures-and-physcial-reactions}

[Ligne directrice 2.3 Saisies : Ne concevez pas le contenu d’une manière connue pour provoquer des crises ou des réactions physiques.](https://www.w3.org/TR/WCAG/#seizures-and-physical-reactions)

### Pas plus de trois flashs ou sous le seuil critique (2.3.1)    {#three-flashes-or-below-threshold}

* Critère de réussite 2.3.1
* Niveau A
* Pas plus de trois flashs ou sous le seuil critique : une page web doit être exempte de tout élément qui flashe plus de trois fois dans n’importe quel intervalle d’une seconde ou ce flash doit se situer sous le seuil de flash générique et le seuil de flash rouge.

>[!NOTE]
>
>Puisque tout contenu ne satisfaisant pas ce critère de réussite peut interférer avec la capacité de l’utilisateur à exploiter la page entière, tout le contenu présent dans la page web (qu’il soit utilisé pour satisfaire d’autres critères de réussite ou non) doit satisfaire ce critère de réussite. Voir [Exigence de conformité 5 : Non-interférence](https://www.w3.org/TR/WCAG/#cc5).

#### Objectif – Pas plus de trois flashs ou sous le seuil critique (2.3.1) {#purpose-three-flashes-or-below-threshold}

Il arrive que le contenu qui flashe provoque des crises de photosensibilité. En appliquant ce critère de réussite, les utilisateurs concernés peuvent accéder au contenu et en prendre connaissance sans inquiétude quant au contenu qui flashe.

#### Comment procéder – Pas plus de trois flashs ou sous le seuil critique (2.3.1)    {#how-to-meet-three-flashes-or-below-threshold}

Veillez à ce que les techniques ci-après soient appliquées :

* Veillez à ce que les composants ne flashent pas plus de trois fois dans n’importe quel intervalle d’une seconde.
* S’il n’est pas possible de remplir la condition ci-dessus, présentez le contenu qui clignote dans un *petit espace sécurisé* en pixels à l’écran. Cet espace est calculé selon une formule complexe, abordée dans la section [G176: Keeping the flashing area small enough](https://www.w3.org/TR/2008/NOTE-WCAG20-TECHS-20081211/G176) (faire en sorte que la zone qui clignote soit suffisamment petite ; en anglais). Cette technique doit être appliquée uniquement si le contenu qui clignote est *absolument* nécessaire.

#### En savoir plus – Pas plus de trois flashs ou sous le seuil critique (2.3.1) {#more-information-three-flashes-or-below-threshold}

* [Compréhension du critère de réussite 2.3.1](https://www.w3.org/WAI/WCAG21/Understanding/three-flashes-or-below-threshold.html)
* [Comment remplir le critère de réussite 2.3.1](https://www.w3.org/WAI/WCAG21/quickref/#three-flashes-or-below-threshold)

### Navigable (2.4) {#navigable}

[Ligne directrice 2.4 Navigable : Fournissez des moyens d’aider les utilisateurs à naviguer, à rechercher du contenu et à déterminer où ils se trouvent.](https://www.w3.org/TR/WCAG/#navigable)

Cela permet de s’assurer que le contenu est facile et facile à parcourir pour les utilisateurs.

### Blocs de contournement (2.4.1) {#bypass-blocks}

* Critère de réussite 2.4.1
* Niveau A
* Ignorer les blocs : Un mécanisme est disponible pour contourner les blocs de contenu répétés sur plusieurs pages Web.

#### Objectif - Blocs de contournement (2.4.1) {#purpose-bypass-blocks}

Ce critère de réussite vise à permettre aux personnes qui naviguent de manière séquentielle dans le contenu d&#39;accéder plus directement au contenu principal de la page Web. Les pages Web et les applications comportent souvent du contenu qui s&#39;affiche sur d&#39;autres pages ou écrans. Les exemples de blocs de contenu répétés incluent, entre autres, les liens de navigation, les graphiques de titre et les cadres publicitaires. Les petites sections répétées, telles que les mots individuels, les expressions ou les liens uniques, ne sont pas considérées comme des blocs aux fins de cette disposition.

#### Comment se rencontrer - Blocs de contournement (2.4.1) {#how-to-meet-bypass-blocks}

Suivez les lignes directrices sous [Comment répondre aux critères de réussite 2.4.1](https://www.w3.org/WAI/WCAG21/quickref/#bypass-blocks).

#### Plus d&#39;informations - Blocs de contournement (2.4.1) {#more-information-bypass-blocks}

* [Compréhension du critère de réussite 2.4.1](https://www.w3.org/WAI/WCAG21/Understanding/bypass-blocks.html)
* [Comment remplir le critère de réussite 2.4.1](https://www.w3.org/WAI/WCAG21/quickref/#bypass-blocks)

### Titre de page (2.4.2)        {#page-titled}

* Critère de réussite 2.4.2
* Niveau A
* Titre de page : les pages web présentent un titre qui décrit leur sujet ou leur but.

#### Objectif – Titre de page (2.4.2)    {#purpose-page-titled}

Ce critère de réussite aide quiconque, en situation de handicap ou non, à identifier rapidement le contenu d’une page web sans avoir à lire la page entière. Ceci s’avère particulièrement utile lorsque plusieurs pages web sont ouvertes dans des onglets de navigateur, puisque le titre de la page s’affiche dans l’onglet et est donc facile à trouver.

#### Comment procéder – Titre de page (2.4.2)    {#how-to-meet-page-titled}

Si une page HTML est créée dans AEM, vous pouvez en spécifier le titre. Veillez à ce qu’il décrive adéquatement le contenu de la page, de sorte que les visiteurs puissent rapidement identifier si le contenu est réellement adapté à leurs besoins.

Vous pouvez également changer le titre d’une page que vous modifiez en sélectionnant : **Informations sur la page** - **Propriétés.**

#### En savoir plus – Titre de page (2.4.2) {#more-information-page-titled}

* [Compréhension du critère de réussite 2.4.2](https://www.w3.org/WAI/WCAG21/Understanding/page-titled.html)
* [Comment remplir le critère de réussite 2.4.2](https://www.w3.org/WAI/WCAG21/quickref/#page-titled)

### Ordre de mise au point (2.4.3) {#focus-order}

* Critère de réussite 2.4.3
* Niveau A
* Ordre de mise au point : Si une page Web peut être naviguée de manière séquentielle et que les séquences de navigation affectent la signification ou le fonctionnement, les composants pouvant être ciblés reçoivent la cible d&#39;action dans un ordre qui préserve la signification et l&#39;opérabilité.

#### Objectif - Ordre de mise au point (2.4.3) {#purpose-focus-order}

Le but de ce critère de réussite est de s’assurer que lorsque les utilisateurs naviguent de manière séquentielle dans le contenu, ils rencontrent des informations dans un ordre compatible avec la signification du contenu et peuvent être manipulés à partir du clavier. Cela réduit la confusion en permettant aux utilisateurs de former un modèle mental cohérent du contenu. Il peut y avoir différents ordres qui reflètent les relations logiques dans le contenu. Par exemple, le fait de passer d’un composant à l’autre d’un tableau, ligne par ligne ou colonne par colonne, reflète les relations logiques dans le contenu. Chaque commande peut satisfaire à ce critère de réussite.

#### Comment se conformer - Ordre de mise au point (2.4.3) {#how-to-meet-focus-order}

Suivez les lignes directrices sous [Comment répondre aux critères de réussite 2.4.3](https://www.w3.org/WAI/WCAG21/quickref/#focus-order).

#### Plus d&#39;informations - Ordre de mise au point (2.4.3) {#more-information-focus-order}

* [Compréhension du critère de réussite 2.4.3](https://www.w3.org/WAI/WCAG21/Understanding/focus-order.html)
* [Comment remplir le critère de réussite 2.4.3](https://www.w3.org/WAI/WCAG21/quickref/#focus-order)

### Fonction du lien (selon le contexte) (2.4.4)        {#link-purpose-in-context}

* Critère de réussite 2.4.4
* Niveau A
* Fonction du lien (selon le contexte) : la fonction de chaque lien est déterminée par le texte du lien seul ou par le texte du lien associé à un contexte du lien déterminé par un programme informatique, sauf si la fonction du lien est ambiguë pour tout utilisateur.

#### Objectif – Fonction du lien (selon le contexte) (2.4.4)    {#purpose-link-purpose-in-context}

Pour tous les utilisateurs, en situation de handicap ou non, il est essentiel d’indiquer clairement la destination d’un lien par l’intermédiaire d’un texte de lien approprié. Les utilisateurs peuvent ainsi décider s’ils souhaitent suivre ce lien. Pour les utilisateurs voyants, un texte de lien significatif est extrêmement utile s’il existe plusieurs liens sur une page (en particulier si la page contient énormément de texte), car il indique clairement la fonctionnalité de la page cible. D’un autre côté, les utilisateurs de technologies d’assistance peuvent générer une liste de tous les liens sur une seule page, et ainsi comprendre plus facilement le texte du lien hors contexte.

#### Comment procéder – Fonction du lien (selon le contexte) (2.4.4)    {#how-to-meet-link-purpose-in-context}

Avant tout, veillez à ce que l’objectif d’un lien soit clairement décrit dans le texte du lien.

* Mauvais exemple :
   * Texte : Pour plus de détails sur nos cours du soir de l’automne 2010, cliquez ici.
   * Motif : le lien est ambigu et n’indique pas clairement sa destination.
* Bon exemple :
   * Texte : Cours du soir de l’automne 2010 – Détails.
   * Motif : il est possible d’améliorer le texte du lien en adaptant légèrement le texte et sa position.

Les liens doivent être formulés de manière cohérente sur toutes les pages, en particulier pour les barres de navigation. Si, par exemple, un lien vers une page spécifique est nommé **Publications** sur une page, il doit être nommé de la même façon sur toutes les autres pages.

Au moment de la rédaction toutefois, certains problèmes peuvent se présenter quant à l’utilisation des titres :

* Habituellement, seuls les utilisateurs d’une souris ont accès au texte contenu dans l’attribut de titre, sous forme d’info-bulle contextuelle ; ce texte n’est pas accessible par clavier.
* Les lecteurs d’écran peuvent lire à haute voix les attributs de titre, mais cette fonctionnalité peut ne pas être activée par défaut ; les utilisateurs peuvent donc ne pas savoir qu’il existe un attribut de titre.
* Il est difficile de modifier l’aspect du texte d’un titre, ce qui signifie qu’il peut être difficile ou impossible de le lire pour certains utilisateurs.

Par conséquent, même si vous pouvez utiliser l’attribut de titre pour fournir plus de contexte sur un lien, vous devez connaître ses limites et ne pas l’utiliser comme alternative à un texte de lien approprié.

Si le lien est composé d’une image, veillez à ce que le texte secondaire de l’image décrive la destination du lien. Si, par exemple, une image de bibliothèque est définie comme lien vers les publications d’une personne, le texte secondaire doit indiquer **Publications de Jean Dupont** et non **Bibliothèque**.

Par ailleurs, si l’ancre du lien contient du texte qui décrit l’objet du lien en sus de l’image (et par conséquent que le texte apparaît le long de l’image), utilisez un attribut alt vide pour l’image :

```xml
<a href="publications.html">
<img src = "bookshelf.jpg" alt = "" />
John Smith’s publications
</a>
```

>[!NOTE]
>
>L’extrait de code ci-dessus est une illustration ; il est recommandé d’utiliser le composant **Image**.

Il est conseillé de spécifier un texte du lien qui identifie l’objet du lien sans avoir besoin de contexte supplémentaire ; toutefois, cela n’est pas toujours possible. Des liens sans contexte peuvent être utilisés dans les cas suivants (vous trouverez des exemples HTML dans la section [Comment remplir le critère de réussite 2.4.4](https://www.w3.org/WAI/WCAG21/quickref/#link-purpose-in-context)) :

* Si le texte du lien fait partie d’une liste de liens étroitement liés et si l’élément de liste encadrant le lien fournit suffisamment de contexte.
* Si l’objet d’un lien peut être clairement identifié dans le texte du paragraphe *précédent* (et non suivant).
* si le lien est contenu dans un tableau de données et par conséquent que l’objet du lien peut être clairement identifié dans les titres associés.
* si une liste de liens est contenue dans un jeu de titres et que le titre lui-même fournit suffisamment de contexte.
* si une liste de liens est contenue dans un lien imbriqué et que la liste parente elle-même au-dessus du lien imbriqué fournit suffisamment de contexte.

Dans certains cas, s’il existe plusieurs liens sur une page (chacun d’eux fournit la destination d’un lien avec des détails complexes mais nécessaires), il peut être nécessaire de fournir une version alternative de la page web qui affiche exactement le même contenu, mais où le texte du lien n’est pas aussi détaillé.

Toutefois, il est possible d’utiliser des scripts de sorte qu’un texte minimal soit fourni avec le lien lui-même, mais, à l’activation d’une commande appropriée placée vers le haut de la page, que le texte du lien soit *développé* afin d’afficher davantage de détails. Une approche similaire consiste à utiliser une feuille de style CSS afin de *masquer* le lien complet pour les utilisateurs voyants, tout en l’affichant dans son intégralité pour les utilisateurs d’un lecteur d’écran. Cela ne fait pas partie du sujet de ce document ; toutefois, vous en apprendrez davantage dans la section [En savoir plus – Fonction du lien (selon le contexte) (2.4.4)](#more-information-link-purpose-in-context).

#### En savoir plus – Fonction du lien (selon le contexte) (2.4.4) {#more-information-link-purpose-in-context}

* [Compréhension du critère de réussite 2.4.4](https://www.w3.org/WAI/WCAG21/Understanding/link-purpose-in-context.html)
* [Comment remplir le critère de réussite 2.4.4](https://www.w3.org/WAI/WCAG21/quickref/#link-purpose-in-context)

<!--
* [C7: Using CSS to hide a portion of the link text](https://www.w3.org/TR/2008/NOTE-WCAG20-TECHS-20081211/C7)
-->

### Méthodes multiples (2.4.5) {#multiple-ways}

* Critère de réussite 2.4.5
* Niveau AA
* Plusieurs manières : Il existe plusieurs manières de localiser une page Web dans un ensemble de pages Web, sauf lorsque la page Web est le résultat d&#39;un processus ou une étape d&#39;un processus.

#### Objectif - Plusieurs façons (2.4.5) {#purpose-multiple-ways}

Ce critère de réussite vise à permettre aux utilisateurs de localiser le contenu de la manière la plus adaptée à leurs besoins. Les utilisateurs peuvent trouver une technique plus facile à utiliser ou plus compréhensible qu’une autre.

Même les petits sites devraient fournir aux utilisateurs un certain moyen d&#39;orientation. Pour un site de trois ou quatre pages, avec toutes les pages liées à partir du , il peut suffire de fournir simplement des liens à partir et vers le  du, où les liens sur l&#39; peuvent aussi servir de carte du site.

#### Comment se rencontrer - Plusieurs façons (2.4.5) {#how-to-meet-multiple-ways}

Suivez les lignes directrices sous [Comment répondre aux critères de réussite 2.4.5](https://www.w3.org/WAI/WCAG21/quickref/#multiple-ways).

#### Plus d&#39;informations - Plusieurs manières (2.4.5) {#more-information-multiple-ways}

* [Compréhension du critère de réussite 2.4.5](https://www.w3.org/WAI/WCAG21/Understanding/multiple-ways.html)
* [Comment remplir le critère de réussite 2.4.5](https://www.w3.org/WAI/WCAG21/quickref/#multiple-ways)

### Titres et étiquettes (2.4.6) {#headings-and-labels}

* Critère de réussite 2.4.6
* Niveau AA
* En-têtes et étiquettes : Les titres et les libellés décrivent la rubrique ou l’objectif.

#### But - En-têtes et étiquettes (2.4.6) {#purpose-headings-and-labels}

Ce critère de réussite vise à aider les utilisateurs à comprendre quelles informations sont contenues dans les pages Web et comment ces informations sont organisées. Lorsque les en-têtes sont clairs et descriptifs, les utilisateurs peuvent trouver plus facilement les informations qu’ils recherchent et ils peuvent comprendre plus facilement les relations entre les différentes parties du contenu. Les étiquettes descriptives aident les utilisateurs à identifier des composants spécifiques dans le contenu.

#### Manière de se rencontrer - Titres et étiquettes (2.4.6) {#how-to-meet-headings-and-labels}

Suivez les lignes directrices sous [Comment répondre aux critères de réussite 2.4.6](https://www.w3.org/WAI/WCAG21/quickref/#headings-and-labels).

#### Plus d&#39;informations - En-têtes et étiquettes (2.4.6) {#more-information-headings-and-labels}

* [Compréhension du critère de réussite 2.4.6](https://www.w3.org/WAI/WCAG21/Understanding/headings-and-labels.html)
* [Comment remplir le critère de réussite 2.4.6](https://www.w3.org/WAI/WCAG21/quickref/#headings-and-labels)

### Focus visible (2.4.7) {#focus-visible}

* Critère de réussite 2.4.7
* Niveau AA
* Ciblage visible : Toute interface utilisateur fonctionnant au clavier dispose d’un mode de fonctionnement dans lequel l’indicateur de focus du clavier est visible.

#### Objectif - Concentration visible (2.4.7) {#purpose-focus-visible}

L’objectif de ce critère de réussite est d’aider une personne à savoir quel élément a la cible d’action du clavier.

Il doit être possible pour une personne de savoir quel élément parmi plusieurs éléments a la cible d’action du clavier. S’il n’y a qu’un seul contrôle activé sur le clavier à l’écran, le critère de réussite est satisfait car la conception visuelle ne présente qu’un seul élément utilisable sur le clavier.

Lorsque le critère de réussite indique &quot;mode de fonctionnement&quot;, il s’agit de tenir compte des plateformes qui ne présentent pas toujours un indicateur de ciblage. Dans la plupart des cas, il n&#39;existe qu&#39;un seul mode de fonctionnement, ce critère de réussite s&#39;applique donc.

#### Manière de se rencontrer - Concentration visible (2.4.7) {#how-to-meet-focus-visible}

Suivez les lignes directrices sous [Comment répondre aux critères de réussite 2.4.7](https://www.w3.org/WAI/WCAG21/quickref/#focus-visible).

#### Plus d&#39;informations - Concentration visible (2.4.7) {#more-information-focus-visible}

* [Compréhension du critère de réussite 2.4.7](https://www.w3.org/WAI/WCAG21/Understanding/focus-visible.html)
* [Comment remplir le critère de réussite 2.4.7](https://www.w3.org/WAI/WCAG21/quickref/#focus-visible)

## Principe 3 : compréhensible    {#principle-understandable}

[Principe 3 : compréhensible – Les informations et l’utilisation de l’interface utilisateur doivent être compréhensibles.](https://www.w3.org/TR/WCAG/#understandable)

### Rendre le contenu textuel lisible et compréhensible (3.1)    {#make-text-content-readable-and-understandable}

[Règle 3.1 – Lisible : rendre le contenu textuel lisible et compréhensible (3.1)](https://www.w3.org/TR/WCAG/#readable)

### Langue de la page (3.1.1)    {#language-of-page}

* Critère de réussite 3.1.1
* Niveau A
* Langue de la page : la langue par défaut de chaque page web peut être déterminée par un programme informatique.

#### Objectif – Langue de la page (3.1.1)    {#purpose-language-of-page}

Ce critère de réussite garantit que ce texte et tout autre contenu linguistique est correctement restitué. Pour les utilisateurs de lecteur d’écran, il garantit que le contenu est correctement prononcé, tandis que les navigateurs visuels sont plus susceptibles d’afficher correctement certains jeux de caractères.

#### Comment procéder – Langue de la page (3.1.1)    {#how-to-meet-language-of-page}

Pour que ce critère de réussite soit satisfait, la langue par défaut d’une page web peut être identifiée à l’aide de l’attribut `lang` dans l’élément `<html>` en haut de la page. Par exemple :

* Si une page est écrite en anglais (Royaume-Uni), l’élément `<html>` doit être :
   `<html lang = “en-gb”>`

* En revanche, pour une page à restituer en anglais (États-Unis), l’attribut doit être défini comme suit :
   `<html lang = “en-us”>`

Dans AEM, la langue par défaut de la page est définie lors de sa création, mais peut également être modifiée lors de son édition, en sélectionnant : **Sidekick** - onglet **Page** - **Propriétés de la page…** - onglet **Avancé**.

#### En savoir plus – Langue de la page (3.1.1) {#more-information-language-of-page}

* [Compréhension du critère de réussite 3.1.1](https://www.w3.org/WAI/WCAG21/Understanding/language-of-page.html)
* [Comment remplir le critère de réussite 3.1.1](https://www.w3.org/WAI/WCAG21/quickref/#language-of-page)
* Les codes reposent sur la norme ISO 639-1. Vous trouverez une liste de codes plus complète pour chaque langue sur le site [W3Schools.com](https://www.w3schools.com/tags/ref_language_codes.asp).

### Langue d’un passage (3.1.2)        {#language-of-parts}

* Critère de réussite 3.1.2
* Niveau AA
* Langue d’un passage : la langue de chaque passage ou expression du contenu peut être déterminée par un programme informatique sauf pour un nom propre, pour un terme technique, pour un mot dont la langue est indéterminée ou pour un mot ou une expression faisant partie du langage courant de la langue utilisée dans le contexte immédiat.

#### Objectif – Langue d’un passage (3.1.2)    {#purpose-language-of-parts}

Ce critère de réussite vise le même objectif que le critère de réussite [Langue de la page](#language-of-page), mais il s’applique aux pages web avec du contenu en plusieurs langues sur une seule page (par exemple, en raison de citations ou de mots empruntés peu courants).

Si une page applique ce critère de réussite, alors :

* Le logiciel de transition en braille peut insérer des caractères accentués.
* Les lecteurs d’écran peuvent prononcer correctement les mots qui sont dans une autre langue que la langue par défaut.
* Les outils de traduction du type Google Translate peuvent correctement traduire les mots d’une langue à une autre.

#### Comment procéder – Langue d’un passage (3.1.2)    {#how-to-meet-language-of-parts}

L’attribut `lang` peut être utilisé pour identifier les modifications dans la langue du contenu. Par exemple, une citation en allemand (code ISO 639-1 &quot;de&quot;) peut s’afficher comme suit :

```xml
<blockquote cite = "John F. Kennedy" lang = "de">
     <p>Ich bin ein Berliner</p>
 </blockquote>
```

>[!NOTE]
>
>Les attributs blockquote ne sont pas pris en charge dans une instance prête à l’emploi. Il est toutefois possible de développer un composant personnalisé pour prendre cette fonction en charge.

De même, le navigateur peut restituer correctement un mot ou une expression emprunté peu courant si l’élément `span` est utilisé comme suit :

```xml
<p>The only French phrase I know is <span lang = “fr”>je ne sais quoi</code>.</p>
```

>[!NOTE]
>
>Il n’est pas nécessaire d’adhérer à ce critère de réussite pour les noms ou villes dans différentes langues ou lors de l’utilisation de mots ou d’expressions empruntés qui sont devenus courants dans la langue par défaut (tel que *diktat* en français).

Pour ajouter l’élément span, avec un langage approprié, vous pouvez modifier manuellement votre balisage HTML en mode d’édition source de l’éditeur de texte enrichi afin qu’il se lise comme ci-dessus. Vous pouvez également inclure l’attribut `lang` dans l’éditeur de texte enrichi par un administrateur système (voir Ajout de la prise en charge d’éléments et d’attributs HTML supplémentaires).
<!--
To add the span element, with an appropriate language, you can manually edit your HTML markup in the source edit mode of the RTE so that it reads as above. Alternatively the `lang` attribute can be included in the RTE by a system administrator (see [Adding Support for Additional HTML Elements and Attributes](/help/sites-administering/rte-accessible-content.md#adding-support-for-additional-html-elements-and-attributes)).
-->

#### En savoir plus – Langue d’un passage (3.1.2) {#more-information-language-of-parts}

* [Compréhension du critère de réussite 3.1.2](https://www.w3.org/WAI/WCAG21/Understanding/language-of-parts.html)
* [Comment remplir le critère de réussite 3.1.2](https://www.w3.org/WAI/WCAG21/quickref/#language-of-parts)

### Prévisible (3.2) {#predictable}

[Ligne directrice 3.2 Prévisible : Rendre les pages Web visibles et fonctionner de manière prévisible.](https://www.w3.org/TR/WCAG/#predictable)

Il s&#39;agit de s&#39;assurer que les pages Web sont cohérentes dans leur apparence et leur fonctionnement.

### Activé (3.2.1) {#on-focus}

* Critère de réussite 3.2.1
* Niveau A
* Au centre des préoccupations : Lorsqu’un composant d’interface utilisateur reçoit le focus, il ne déclenche pas de changement de contexte.

#### Objectif - Concentration (3.2.1) {#purpose-on-focus}

Ce critère de réussite vise à garantir que la fonctionnalité est prévisible lorsque les parcourent un . Tout composant capable de déclencher un  lorsqu’il reçoit le focus ne doit pas modifier le contexte. Voici quelques exemples de changement de contexte lorsqu’un composant est ciblé :

* les formulaires envoyés automatiquement lorsqu’un composant reçoit le focus ;
* de nouvelles fenêtres lancées lorsqu’un composant est activé ;
* le focus est remplacé par un autre composant lorsque ce composant reçoit le focus ;

La cible d&#39;action peut être déplacée vers un contrôle soit par le clavier (par exemple, en appuyant sur une commande), soit par la souris (par exemple, en cliquant sur un champ de texte). Le déplacement de la souris sur un contrôle ne déplace pas la cible d’action, sauf si un script met en oeuvre ce comportement. Notez que pour certains types de contrôles, cliquer sur un contrôle peut aussi activer le contrôle (p. ex. bouton), ce qui peut, à son tour, déclencher un changement de contexte.

#### Comment se rencontrer - Au point ciblé (3.2.1) {#how-to-meet-on-focus}

Suivez les lignes directrices sous [Comment répondre aux critères de réussite 3.2.1](https://www.w3.org/WAI/WCAG21/quickref/#on-focus).

#### Plus d&#39;informations - Au point (3.2.1) {#more-information-on-focus}

* [Compréhension du critère de réussite 3.2.1](https://www.w3.org/WAI/WCAG21/Understanding/on-focus.html)
* [Comment remplir le critère de réussite 3.2.1](https://www.w3.org/WAI/WCAG21/quickref/#on-focus)

### En entrée (3.2.2) {#on-input}

* Critère de réussite 3.2.2
* Niveau A
* En entrée : La modification du paramètre d’un composant d’interface utilisateur n’entraîne pas automatiquement un changement de contexte, sauf si l’utilisateur a été informé du comportement avant d’utiliser le composant.

#### Objectif - À l&#39;entrée (3.2.2) {#purpose-on-input}

Ce critère de réussite vise à garantir que la saisie de données ou la sélection d’un contrôle de formulaire a des effets prévisibles. La modification du paramètre d’un composant d’interface utilisateur modifie un aspect du contrôle qui persiste lorsque l’utilisateur n’interagit plus avec lui. Ainsi, la vérification d’une case à cocher, la saisie de texte dans un champ de texte ou la modification de l’option sélectionnée dans un contrôle  de modifie son paramètre, mais l’activation d’un lien ou d’un bouton ne change pas. Les changements dans le contexte peuvent embrouiller les utilisateurs qui ne perçoivent pas facilement le changement ou qui sont facilement distraits par les changements. Les changements de contexte ne sont appropriés que lorsqu’il est clair qu’un tel changement se produira en réponse à l’action de l’utilisateur.

#### Comment se rencontrer - À l&#39;entrée (3.2.2) {#how-to-meet-on-input}

Suivez les lignes directrices sous [Comment répondre aux critères de réussite 3.2.2](https://www.w3.org/WAI/WCAG21/quickref/#on-input).

#### Plus d&#39;informations - À l&#39;entrée (3.2.2) {#more-information-on-input}

* [Compréhension du critère de réussite 3.2.2](https://www.w3.org/WAI/WCAG21/Understanding/on-input.html)
* [Comment remplir le critère de réussite 3.2.2](https://www.w3.org/WAI/WCAG21/quickref/#on-input)

### Navigation cohérente (3.2.3) {#consistent-navigation}

* Critère de réussite 3.2.3
* Niveau AA
* Navigation cohérente : Les mécanismes de navigation qui sont répétés sur plusieurs pages Web d&#39;un ensemble de pages Web se produisent dans le même ordre relatif chaque fois qu&#39;elles sont répétées, sauf si l&#39;utilisateur est à l&#39;origine d&#39;une modification.

#### Objectif - Navigation cohérente (3.2.3) {#purpose-consistent-navigation}

Ce critère de réussite vise à encourager l&#39;utilisation d&#39;une présentation et d&#39;une mise en page cohérentes pour les utilisateurs qui interagissent avec du contenu répété dans un ensemble de pages Web et qui ont besoin de localiser plusieurs fois des informations ou des fonctionnalités spécifiques. Les personnes à faible vision qui utilisent un agrandissement de l’écran pour afficher une petite partie de l’écran à la fois utilisent souvent des repères visuels et des limites de page pour localiser rapidement le contenu répété. La présentation de contenu répété dans le même ordre est également importante pour les utilisateurs visuels qui utilisent la mémoire spatiale ou des repères visuels dans la conception pour localiser le contenu répété.

Il est important de noter que l&#39;utilisation de l&#39;expression &quot;même ordre&quot; dans cette section ne signifie pas que les menus de sous-navigation ne peuvent pas être utilisés ou que des blocs de navigation secondaire ou de structure de page ne peuvent pas être utilisés. Ce critère de réussite vise plutôt à aider les utilisateurs qui interagissent avec du contenu répété sur plusieurs pages Web à prévoir l’emplacement du contenu qu’ils recherchent et à le trouver plus rapidement lorsqu’ils le retrouveront.

Les utilisateurs peuvent modifier l’ordre en utilisant des agents utilisateur adaptatifs ou en définissant des préférences de sorte que les informations soient présentées de la manière la plus utile pour eux.

#### Comment se conformer - Navigation cohérente (3.2.3) {#how-to-meet-consistent-navigation}

Suivez les lignes directrices sous [Comment répondre aux critères de réussite 3.2.3](https://www.w3.org/WAI/WCAG21/quickref/#consistent-navigation).

#### Plus d&#39;informations - Navigation cohérente (3.2.3) {#more-information-consistent-navigation}

* [Compréhension du critère de réussite 3.2.3](https://www.w3.org/WAI/WCAG21/Understanding/consistent-navigation.html)
* [Comment remplir le critère de réussite 3.2.3](https://www.w3.org/WAI/WCAG21/quickref/#consistent-navigation)

### Identification cohérente (3.2.4) {#consistent-identification}

* Critère de réussite 3.2.4
* Niveau A
* Identification cohérente : Les composants qui ont la même fonctionnalité dans un ensemble de pages Web sont identifiés de manière cohérente.

#### But - Identification cohérente (3.2.4) {#purpose-consistent-identification}

Ce critère de réussite vise à assurer l&#39;identification cohérente des composants fonctionnels qui apparaissent à plusieurs reprises dans un ensemble de pages Web. Une stratégie utilisée par les utilisateurs de lecteurs d&#39;écran lors de l&#39;exploitation d&#39;un site Web consiste à s&#39;appuyer fortement sur leur connaissance des fonctions qui peuvent apparaître sur différentes pages Web. Si des fonctions identiques ont des étiquettes différentes (ou, plus généralement, un nom accessible différent) sur différentes pages Web, le site sera beaucoup plus difficile à utiliser. Cela peut aussi dérouter et augmenter la charge cognitive pour les personnes avec des limitations cognitives. Par conséquent, un étiquetage cohérent aidera.

Cette cohérence s&#39;étend aux variantes textuelles. Si des icônes ou d’autres éléments non textuels ont la même fonctionnalité, leurs alternatives textuelles doivent être cohérentes.

S’il existe deux composants sur une page Web qui ont tous deux la même fonctionnalité qu’un composant sur une autre page dans un ensemble de pages Web, les trois composants doivent être cohérents. Par conséquent, les deux sur la même page seront cohérents.

Bien qu’il soit souhaitable et recommandé d’être toujours cohérent dans une seule page Web, la version 3.2.4 ne traite que la cohérence dans un ensemble de pages Web où un élément est répété sur plusieurs pages du jeu.

#### Comment se conformer - Identification cohérente (3.2.4) {#how-to-meet-consistent-identification}

Suivez les lignes directrices sous [Comment répondre aux critères de réussite 3.2.4](https://www.w3.org/WAI/WCAG21/quickref/#consistent-identification).

#### Plus d&#39;informations - Identification cohérente (3.2.4) {#more-information-consistent-identification}

* [Compréhension du critère de réussite 3.2.4](https://www.w3.org/WAI/WCAG21/Understanding/consistent-identification.html)
* [Comment remplir le critère de réussite 3.2.4](https://www.w3.org/WAI/WCAG21/quickref/#consistent-identification)

### Assistance en entrée (3.3) {#input-assistance}

[Règle 3.3 – Assistance à la saisie : aider l’utilisateur à éviter et à corriger les erreurs de saisie (3.3)](https://www.w3.org/TR/WCAG/#input-assistance)

### Identification des erreurs (3.3.1) {#error-identification}

* Critère de réussite 3.3.1
* Niveau A
* Identification de l&#39;erreur : Si une erreur d’entrée est automatiquement détectée, l’élément en erreur est identifié et l’erreur est décrite à l’utilisateur dans le texte.

#### Objectif - Identification des erreurs (3.3.1) {#purpose-error-identification}

Ce critère de réussite a pour but de s’assurer que les utilisateurs sont conscients qu’une erreur s’est produite et peuvent déterminer ce qui ne va pas. Le message d’erreur doit être aussi précis que possible. En cas d’échec de l’envoi du formulaire, le fait de réafficher le formulaire et d’indiquer les champs en erreur est insuffisant pour que certains utilisateurs puissent percevoir qu’une erreur s’est produite. Les utilisateurs de lecteurs d’écran, par exemple, ne sauront pas qu’une erreur s’est produite tant qu’ils n’ont pas rencontré l’un des indicateurs. Ils peuvent abandonner complètement le formulaire avant de rencontrer l’indicateur d’erreur, pensant que la page n’est tout simplement pas fonctionnelle. Selon la définition de WCAG 2.0, une &quot;erreur d’entrée&quot; est une information fournie par l’utilisateur qui n’est pas acceptée. Cela inclut :

les informations requises par la page Web mais omises par l’utilisateur, ou les informations fournies par l’utilisateur mais qui ne sont pas conformes au format de données requis ou aux valeurs autorisées.
Par exemple :

* l’utilisateur ne saisit pas l’abréviation appropriée dans l’état, la province, la région, etc. field;
* l’utilisateur entre une abréviation d’état qui n’est pas un état valide ;
* l&#39;utilisateur saisit un code postal inexistant;
* l&#39;utilisateur entre dans une date de naissance de deux ans à l&#39;avenir;
* l&#39;utilisateur entre des caractères alphabétiques ou des parenthèses dans le champ de son numéro de téléphone qui n&#39;accepte que les chiffres;
* l&#39;utilisateur saisit une offre inférieure à l&#39;offre précédente ou à l&#39;augmentation d&#39;offre minimale.

#### Comment répondre - Identification des erreurs (3.3.1) {#how-to-meet-error-identification}

Suivez les lignes directrices sous [Comment répondre aux critères de réussite 3.3.1](https://www.w3.org/WAI/WCAG21/quickref/#error-identification).

#### Plus d&#39;informations - Identification des erreurs (3.3.1) {#more-information-error-identification}

* [Compréhension du critère de réussite 3.3.1](https://www.w3.org/WAI/WCAG21/Understanding/error-identification.html)
* [Comment remplir le critère de réussite 3.3.1](https://www.w3.org/WAI/WCAG21/quickref/#error-identification)

### Étiquettes ou instructions (3.3.2)    {#labels-or-instructions}

* Critère de réussite 3.3.2
* Niveau A
* Étiquettes ou instructions : des étiquettes sont présentées ou des instructions sont fournies quand un contenu requiert une saisie utilisateur.

#### Objectif – Étiquettes ou instructions (3.3.2)    {#purpose-labels-or-instructions}

La fourniture d’instructions pour aider les utilisateurs à remplir des formulaires est l’un des éléments essentiels pour rendre une interface conviviale. Ceci s’avère particulièrement utile pour les personnes ayant des déficiences visuelles ou cognitives qui risquent autrement d’avoir du mal à comprendre la mise en page d’un formulaire et le tri des données à fournir dans un champ particulier du formulaire.

Dans AEM, une étiquette est ajoutée par défaut lorsque vous ajoutez un composant de formulaire, tel que **Champ de texte**, à la page. Ce titre par défaut dépend du type de composant. Vous pouvez ajouter votre propre titre pour ce champ dans l’onglet **Titre et texte** de la boîte de dialogue d’édition. Veillez à ce que les étiquettes aident les utilisateurs à comprendre les données associées à chaque composant de formulaire.

Utilisez ce champ **Titre** pour les éléments de champ, car il fournit une étiquette accessible par les technologies d’assistance. Le simple fait d’écrire une étiquette dans le texte en regard du champ ne suffit pas.

Pour certains composants, il est également possible de masquer visuellement les étiquettes en cochant la case **Masquer le titre**. Les étiquettes masquées de cette façon restent accessibles aux technologies d’assistance, mais ne s’affichent pas à l’écran. Si cette approche est adaptée à certaines situations, il est généralement préférable d’inclure une étiquette visuelle chaque fois que cela est possible, car certains utilisateurs qui ne regardent qu’une très petite portion de l’écran (un champ à la fois) ont besoin des étiquettes pour identifier correctement le champ.

#### Boutons Image {#image-buttons}

Lorsque des boutons d’image sont utilisés (par exemple, le composant **Bouton Image**), le champ **Titre** de l’onglet **Titre et texte** de la boîte de dialogue Modifier fournit en fait le texte secondaire de l’image, plutôt que le libellé. Ainsi, dans l’exemple ci-dessous, l’image avec le texte `Submit` comporte le texte secondaire `Submit`, ajouté à l’aide du champ **Titre** dans la boîte de dialogue de modification.

#### Groupes de champs de formulaire {#groups-of-form-fields}

Lorsqu’il existe un groupe de commandes associées, comme **Groupe de cases d’option**, il peut être nécessaire de donner un titre au groupe, ainsi qu’aux commandes individuelles. Lors de l’ajout d’un jeu de cases d’option dans AEM, le champ **Titre** fournit le titre de ce groupe et des titres individuels sont spécifiés alors que les cases d’option (**Éléments**) sont créées.

Cependant, il n’existe aucune association par programmation entre le titre du groupe et les boutons radio eux-mêmes. Les éditeurs de modèles doivent placer le titre dans les balises `fieldset` et `legend` nécessaires afin de créer cette association. Pour ce faire, il suffit de modifier le code source de la page. Un administrateur système peut également ajouter la prise en charge de ces éléments afin qu’ils apparaissent dans la boîte de dialogue **Propriétés du champ** (voir Ajout de la prise en charge d’éléments et d’attributs HTML supplémentaires).

<!--
However, there is no programmatic association between the group title and the radio buttons themselves. Template editors would need to wrap the title in the necessary `fieldset` and `legend` tags to create this association and this can only be done by editing the page source code. Alternatively, a system administrator can add support for these elements so that they appear in the **Field Properties** dialog (see [Adding Support for Additional HTML Elements and Attributes](/help/sites-administering/rte-accessible-content.md#adding-support-for-additional-html-elements-and-attributes)).
-->

#### Considérations supplémentaires pour les formulaires {#additional-considerations-for-forms}

Si les données doivent être saisies dans un format spécifique, précisez-le dans le texte du libellé. Par exemple, si une date doit être saisie au format `DD-MM-YYYY`, indiquez-le spécifiquement dans le libellé. Cela signifie que lorsque les utilisateurs de lecteurs d’écran rencontrent le champ, le libellé est automatiquement annoncé, ainsi que les informations supplémentaires sur le format.

Si la saisie d’un champ de formulaire est obligatoire, indiquez-le en utilisant le mot « obligatoire » dans le libellé. AEM ajoute un astérisque lorsqu’un champ est obligatoire, mais il serait idéal d’inclure le mot `required` dans le libellé lui-même (dans le champ **Titre** de la boîte de dialogue de modification).

Le positionnement des libellés est également important, car ils permettent de localiser les champs appropriés. Cela est tout particulièrement important lorsque l’utilisateur est confronté à un formulaire complexe. Suivez les conventions ci-dessous :

* Cases à cocher ou cases d’option :
Les libellés sont positionnés immédiatement à droite du champ.
* Tous les autres composants de formulaire (par ex., zones de texte, zones de liste modifiable) :
Les libellés sont positionnés immédiatement au-dessus ou à gauche du champ.

Dans les formulaires simples avec des fonctionnalités très limitées, un bouton `Submit` approprié peut servir de libellé pour le champ adjacent (par exemple `Search`). Cela s’avère utile dans les cas où il peut être difficile de trouver de l’espace pour le texte du libellé.

#### En savoir plus – Étiquettes ou instructions (3.3.2) {#more-information-labels-or-instructions}

* [Compréhension du critère de réussite 3.3.2](https://www.w3.org/WAI/WCAG21/Understanding/labels-or-instructions.html)
* [Comment remplir le critère de réussite 3.3.2](https://www.w3.org/WAI/WCAG21/quickref/#labels-or-instructions)

### Suggestion d’erreur (3.3.3) {#error-suggestion}

* Critère de réussite 3.3.3
* Niveau AA
* Clavier : Si une erreur d’entrée est automatiquement détectée et que des suggestions de correction sont connues, les suggestions sont alors fournies à l’utilisateur, à moins qu’elles ne compromettent la sécurité ou l’objectif du contenu.

#### Objectif - Suggestion d&#39;erreur (3.3.3) {#purpose-error-suggestion}

Le but de ce critère de réussite est de s’assurer que les utilisateurs reçoivent les suggestions appropriées pour corriger une erreur d’entrée si possible. La définition WCAG 2.0 de &quot;erreur d’entrée&quot; indique que c’est &quot;l’information fournie par l’utilisateur qui n’est pas acceptée&quot; par le système. Parmi les informations non acceptées, citons les informations requises mais omises par l’utilisateur et les informations fournies par l’utilisateur, mais qui ne respectent pas le format de données requis ou les valeurs autorisées.

Critère de réussite 3.3.1 prévoit la notification des erreurs. Cependant, les personnes ayant des limitations cognitives peuvent avoir du mal à comprendre comment corriger les erreurs. Les personnes ayant des déficiences visuelles peuvent ne pas être en mesure de trouver exactement comment corriger l&#39;erreur. En cas d’échec de l’envoi d’un formulaire, les utilisateurs peuvent abandonner le formulaire parce qu’ils peuvent ne pas savoir comment corriger l’erreur même s’ils savent qu’elle s’est produite.

L’auteur du contenu peut fournir la description de l’erreur ou l’agent utilisateur peut fournir la description de l’erreur en fonction d’informations spécifiques à la technologie et déterminées par programme.

#### Comment répondre - Suggestion d&#39;erreur (3.3.3) {#how-to-meet-error-suggestion}

Suivez les lignes directrices sous [Comment répondre aux critères de réussite 3.3.3](https://www.w3.org/WAI/WCAG21/quickref/#error-suggestion).

#### Plus d&#39;informations - Suggestion d&#39;erreur (3.3.3) {#more-information-error-suggestion}

* [Compréhension du critère de réussite 3.3.3](https://www.w3.org/WAI/WCAG21/Understanding/error-suggestion.html)
* [Comment remplir le critère de réussite 3.3.3](https://www.w3.org/WAI/WCAG21/quickref/#error-suggestion)

### Prévention des erreurs (juridique, financière, données) (3.3.4) {#error-prevention-legal-financial-data}

* Critère de réussite 3.3.4
* Niveau AA
* Prévention des erreurs (juridique, financier, données) : Pour les pages Web qui génèrent des engagements légaux ou des transactions financières pour l&#39;utilisateur, qui modifient ou suppriment des données contrôlables par l&#39;utilisateur dans les systèmes de données   ou qui envoient des réponses de test de l&#39;utilisateur, au moins l&#39;une des conditions suivantes est vraie :

   * ReversibleSubmissions est réversible.
   * CheckedData saisi par l’utilisateur est analysé pour détecter les erreurs d’entrée et l’utilisateur a la possibilité de les corriger.
   * ConfirméUn mécanisme est disponible pour examiner, confirmer et corriger les informations avant de finaliser l&#39;envoi.

#### Objectif - Prévention des erreurs (juridique, financière, données) (3.3.4) {#purpose-error-prevention-legal-financial-data}

Ce critère de réussite a pour but d’aider les utilisateurs ayant une déficience à éviter les conséquences graves d’une erreur lorsqu’ils exécutent une action qui ne peut pas être annulée. Par exemple, l&#39;achat de billets d&#39;avion non remboursables ou la soumission d&#39;une commande d&#39;achat d&#39;actions dans un compte de courtage sont des transactions financières avec de graves conséquences. Si un utilisateur a commis une erreur à la date du voyage en avion, il pourrait se retrouver avec un billet pour le mauvais jour qui ne peut pas être échangé. Si l&#39;utilisateur a commis une erreur sur le nombre d&#39;actions à acheter, il pourrait acheter plus d&#39;actions que prévu. Ces deux types d&#39;erreurs impliquent des transactions qui se produisent immédiatement et qui ne peuvent être modifiées par la suite, et qui peuvent être très coûteuses. De même, il peut s’agir d’une erreur irrécupérable si les utilisateurs modifient ou suppriment involontairement les données stockées dans une base de données à laquelle ils ont par la suite besoin d’accéder, par exemple l’intégralité de leur de voyage dans un site Web de services de voyage. Lorsqu&#39;il s&#39;agit de la modification ou de la suppression de données &quot;contrôlables par l&#39;utilisateur&quot;, l&#39;intention est d&#39;empêcher la perte massive de données, comme la suppression d&#39;un fichier ou d&#39;un enregistrement. Il n&#39;est pas dans l&#39;intention d&#39;exiger une confirmation pour chaque commande d&#39;enregistrement ou la simple création ou modification de , d&#39;enregistrements ou d&#39;autres données.

Les utilisateurs handicapés sont plus susceptibles de commettre des erreurs. Les personnes ayant une déficience de lecture peuvent transposer des chiffres et des lettres, et les personnes ayant une déficience motrice peuvent toucher des clés par erreur. La possibilité d’inverser les actions permet aux utilisateurs de corriger une erreur qui pourrait avoir de graves conséquences. La possibilité de vérifier et de corriger les informations donne à l’utilisateur la possibilité de détecter une erreur avant de prendre une action qui a de graves conséquences.

Les données contrôlables par l’utilisateur sont des données visibles par l’utilisateur que l’utilisateur peut modifier et/ou supprimer par le biais d’une action intentionnelle. Par exemple, l’utilisateur qui contrôle ces données met à jour le numéro de téléphone et l’adresse du compte de l’utilisateur ou supprime un enregistrement des factures passées d’un site Web. Il ne fait pas référence à des éléments tels que les journaux Internet et les données de surveillance des moteurs de recherche que l&#39;utilisateur ne peut pas  ou utiliser directement.

#### Procédures - Prévention des erreurs (juridique, financier, données) (3.3.4) {#how-to-meet-error-prevention-legal-financial-data}

Suivez les lignes directrices sous [Comment répondre aux critères de réussite 3.3.4](https://www.w3.org/WAI/WCAG21/quickref/#error-prevention-legal-financial-data).

#### Plus d&#39;informations - Prévention des erreurs (juridique, financier, données) (3.3.4) {#more-information-error-prevention-legal-financial-data}

* [Compréhension du critère de réussite 3.3.4](https://www.w3.org/WAI/WCAG21/Understanding/error-prevention-legal-financial-data.html)
* [Comment remplir le critère de réussite 3.3.4](https://www.w3.org/WAI/WCAG21/quickref/#error-prevention-legal-financial-data)

## Principe 4 : Robuste {#principle-robust}

[Principe 4 : Robuste - Le contenu doit être suffisamment robuste pour pouvoir être interprété par un large éventail d&#39;agents utilisateurs, y compris les technologies d&#39;assistance.](https://www.w3.org/TR/WCAG/#robust)

### Compatible (4.1) {#compatible}

[Ligne directrice 4.1 Compatible : Optimiser la compatibilité avec les agents utilisateurs actuels et futurs, y compris les technologies d’assistance.](https://www.w3.org/TR/WCAG/#compatible)

Optimiser la compatibilité avec les agents utilisateurs actuels et futurs, y compris les technologies d’assistance.

### Analyse (4.1.1) {#parsing}

* Critère de réussite 4.1.1
* Niveau A
* Analyse : Dans le contenu implémenté à l’aide des langages de balisage, les éléments ont des balises de fin et de complètes, les éléments sont imbriqués selon leurs spécifications, les éléments ne contiennent pas d’attributs de et les identifiants sont uniques, sauf lorsque les spécifications autorisent ces fonctionnalités.

#### Objectif - Analyse (4.1.1) {#purpose-parsing}

Ce critère de réussite vise à garantir que les agents utilisateurs, y compris les technologies d’assistance, puissent interpréter et analyser le contenu avec précision. Si le contenu ne peut pas être analysé dans une structure de données, différents agents utilisateur peuvent le présenter différemment ou être totalement incapables de l’analyser. Certains agents d’utilisateur utilisent des &quot;techniques de réparation&quot; pour rendre le contenu mal codé.

Comme les techniques de réparation varient d’un agent utilisateur à l’autre, les auteurs ne peuvent pas présumer que le contenu sera analysé avec précision dans une structure de données ou qu’il sera rendu correctement par des agents utilisateurs spécialisés, y compris les technologies d’assistance, à moins que le contenu ne soit créé selon les règles définies dans la grammaire formelle de cette technologie. Dans les langages de balisage, les erreurs dans la syntaxe des éléments et des attributs et l’échec de la fourniture de balises de /fin correctement imbriquées entraînent des erreurs qui empêchent les agents utilisateur d’analyser le contenu de manière fiable. Par conséquent, le critère de réussite exige que le contenu puisse être analysé en utilisant uniquement les règles de la grammaire formelle.

#### Comment se rencontrer - Analyse (4.1.1) {#how-to-meet-parsing}

Suivez les lignes directrices sous [Comment répondre aux critères de réussite 4.1.1](https://www.w3.org/WAI/WCAG21/quickref/#parsing).

#### Plus d&#39;informations - Analyse (4.1.1) {#more-information-parsing}

* [Compréhension du critère de réussite 4.1.1](https://www.w3.org/WAI/WCAG21/Understanding/parsing.html)
* [Comment remplir le critère de réussite 4.1.1](https://www.w3.org/WAI/WCAG21/quickref/#parsing)

### Nom, rôle, valeur (4.1.2) {#name-role-value}

* Critère de réussite 4.1.2
* Niveau A
* Nom, Rôle, Valeur : Pour tous les composants de l’interface utilisateur (y compris, mais sans s’y limiter, les composants suivants : éléments de formulaire, liens et composants générés par les scripts), le nom et le rôle peuvent être déterminés par programmation ; les états, propriétés et valeurs qui peuvent être définis par l’utilisateur peuvent être définis par programmation ; et les agents utilisateurs peuvent être informés des modifications apportées à ces éléments, y compris les technologies d’assistance.

#### Objet - Nom, rôle, valeur (4.1.2) {#purpose-ame-role-value}

Ce critère de réussite vise à garantir que les technologies d’assistance (AT) peuvent recueillir des informations sur le contenu, l’activer (ou le définir) et rester à jour sur l’état des contrôles de l’interface utilisateur.

Lorsque des contrôles standard de technologies accessibles sont utilisés, ce processus est simple. Si les éléments de l&#39;interface utilisateur sont utilisés conformément aux spécifications, les conditions de cette disposition seront remplies. (Voir les exemples du critère de réussite 4.1.2 ci-dessous)

Toutefois, si des contrôles personnalisés sont créés ou si des éléments d’interface sont programmés (dans le code ou le script) pour avoir un rôle et/ou une fonction différents de ceux d’habitude, des mesures supplémentaires doivent être prises pour s’assurer que les contrôles fournissent des informations importantes aux technologies d’assistance et se permettent d’être contrôlés par des technologies d’assistance.

L’état particulièrement important d’un contrôle d’interface utilisateur est de savoir s’il a ou non la cible d’action. L’état d’intérêt d’un contrôle peut être déterminé par programmation, et des notifications sur le changement d’orientation sont envoyées aux agents utilisateurs et à la technologie d’assistance. D’autres exemples d’état de contrôle de l’interface utilisateur indiquent si une case à cocher ou un bouton radio a été sélectionné ou si une arborescence réductible ou un noeud  est développé ou réduit.

#### Comment se rencontrer - Nom, Rôle, Valeur (4.1.2) {#how-to-meet-ame-role-value}

Suivez les lignes directrices sous [Comment répondre aux critères de réussite 4.1.2](https://www.w3.org/WAI/WCAG21/quickref/#name-role-value).

#### Plus d&#39;informations - Nom, Rôle, Valeur (4.1.2) {#more-information-ame-role-value}

* [Compréhension du critère de réussite 4.1.2](https://www.w3.org/WAI/WCAG21/Understanding/name-role-value.html)
* [Comment remplir le critère de réussite 4.1.2](https://www.w3.org/WAI/WCAG21/quickref/#name-role-value)
