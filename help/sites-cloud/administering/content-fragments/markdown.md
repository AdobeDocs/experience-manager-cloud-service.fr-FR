---
title: Markdown
description: Découvrez comment l’éditeur de fragment de contenu utilise la syntaxe Markdown pour vous permettre de créer facilement du contenu pour la création de pages et la diffusion headless.
feature: Content Fragments
role: User
exl-id: 6fbf8128-3b7f-4eda-bbbd-3336578d2586
solution: Experience Manager Sites
source-git-commit: 278242e0be1da5c64abfa5d9ac174013688ff422
workflow-type: tm+mt
source-wordcount: '559'
ht-degree: 79%

---

# Markdown {#markdown}

Lors de la [création](/help/sites-cloud/administering/content-fragments/authoring.md#edit-multi-line-text-fields-plaintext-markdown) de fragments de contenu, des [champs de texte multiligne](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#data-types) peuvent être définis avec le **Type par défaut** de **Markdown**. L’éditeur de fragment de contenu utilise la syntaxe *markdown* pour vous permettre d’écrire facilement du contenu pour la création de pages et la diffusion headless :

![Champ de texte multiligne Markdown dans l’éditeur](/help/sites-cloud/administering/content-fragments/assets/cf-markdown-field-edit.png)

Vous pouvez définir :

* [Notation d’en-tête](/help/sites-cloud/administering/content-fragments/markdown.md#heading-notation)
* [Paragraphes et sauts de ligne](/help/sites-cloud/administering/content-fragments/markdown.md#paragraphs-and-line-breaks)
* [Liens](/help/sites-cloud/administering/content-fragments/markdown.md#links)
* [Images](/help/sites-cloud/administering/content-fragments/markdown.md#images)
* [Blocs de citations](/help/sites-cloud/administering/content-fragments/markdown.md#block-quotes)
* [Listes](/help/sites-cloud/administering/content-fragments/markdown.md#lists)
* [Accent](/help/sites-cloud/administering/content-fragments/markdown.md#emphasis)
* [Blocs de code](/help/sites-cloud/administering/content-fragments/markdown.md#code-blocks)
* [Échappements par barre oblique inverse](/help/sites-cloud/administering/content-fragments/markdown.md#backslash-escapes)

## Notation d’en-tête {#heading-notation}

Pour créer un en-tête en plaçant un hashtag (#) devant le titre, Une balise de hachage (#) indique un H1, deux balises de hachage (##) pour un H2, etc. Vous pouvez utiliser jusqu’à six hashtags. Par exemple :

    `## This is an H2`

    `### This is an H3`

    `###### This is a H6`

Si vous le souhaitez, vous pouvez créer une balise H1 en soulignant le texte par des signes égal et créer une balise H2 en soulignant le texte par des signes moins. Par exemple :

    `This is an H1`

    `=============`

    `This is an H2`

    `-------------`

## Paragraphes et sauts de ligne {#paragraphs-and-line-breaks}

Un paragraphe est simplement une ou plusieurs lignes consécutives de texte séparées par une ou plusieurs lignes vierges. Une ligne vierge est une ligne ne contenant rien d’autre que des espaces ou des tabulations. Les paragraphes normaux ne doivent pas être mis en retrait avec des espaces ou des tabulations.

Un saut de ligne est créé en terminant une ligne par deux espaces ou plus puis un retour.

## Liens {#links}

Vous pouvez créer des liens intégrés et de référence.

Dans les deux styles, le texte du lien est délimité par des crochets `[]`.

Voici des exemples de liens intégrés :

    `This is [an example](https://example.com/ "Title") inline link.`

    `This is [an example (non-standard) of an email link](emailto:myaddress@mydomain.info)`

    `[This link](https://example.net/) has no title attribute.`

Les liens de référence présentent la syntaxe suivante :

    `Hey you should [checkout][0] this [cool thing][wiki] that I [made][].`

    `[0]: https://www.google.ca`

    `[wiki]: https://www.wikipedia.org`

    `[made]: https://www.stackoverflow.com`

## Images {#images}

La syntaxe des images est similaire à celle des liens. Vous pouvez créer des images intégrées et référencées.

Par exemple, les images intégrées présentent la syntaxe suivante :

    `![Alt text](/path/to/img.jpg)`

    `![Alt text](/path/to/img.jpg "Optional title")`

La syntaxe comprend :

* Un point d’exclamation : !;
* suivi d’un ensemble de crochets, contenant le texte d’attribut alternatif de l’image ;
* suivi d’un ensemble de parenthèses, contenant l’URL ou le chemin d’accès de l’image, et un attribut de titre facultatif inclus dans des guillemets doubles ou simples.

Les images de style de référence présentent la syntaxe suivante :

    `![Alt text][id]`

Où « id » est le nom d’une référence d’image définie. Les références d’image sont définies à l’aide d’une syntaxe identique à celle des références de lien :

    `[id]: url/to/image "Optional title attribute"`

## Blocs de citations {#block-quotes}

Vous pouvez transformer un texte en citation en ajoutant le symbole > avant le texte. Par exemple :

    `>This is block quotes`

    `>asdhfjlkasdhlf`

    `>asdfahsdlfasdfj`

Vous pouvez avoir des blocs de citation imbriqués. Par exemple :

    `> This is the first level of quoting.`

    `>`

        `>> This is nested blockquote.`

    `>`

    `> Back to the first level.`

## Listes {#lists}

Vous pouvez créer des listes ordonnées et non ordonnées.

Pour créer une liste non ordonnée, insérez le symbole * avant les éléments de la liste. Par exemple :

    `* item in list`

    `* item in list`

    `* item in list`

Pour créer une liste ordonnée, ajoutez les nombres, suivis d’un point, avant chaque élément de la liste. Par exemple :

    `1. First item in list.`

    `2. Second item in list.`

    `3. Third item in list.`

## Accent {#emphasis}

Vous pouvez ajouter un style italique ou gras à votre texte.

Vous pouvez ajouter l’italique comme suit :

    `*single asterisks*`

    `_single underscores_`

    `Keyboard shortcut: Ctrl-I (Cmd-I)`

Vous pouvez mettre du texte en gras comme suit :

    `**double asterisks**`

    `__double underscores__`

    `Keyboard shortcut: Ctrl-B (Cmd-B)`

Pour désigner une plage de code, entourez-la de guillemets obliques (&grave;). Contrairement à un bloc de code préformaté, une plage de code indique du code dans un paragraphe normal.

Par exemple :

    ``Use the `printf()` function.``

## Blocs de code {#code-blocks}

Les blocs de code sont généralement utilisés pour illustrer le code source. Vous pouvez créer des blocs de code en mettant le code en retrait avec une tabulation ou un minimum de 4 espaces. Par exemple :

    `This is a normal paragraph.`

        `This is a code block.`

## Échappements par barre oblique inverse {#backslash-escapes}

Vous pouvez utiliser des barres obliques inverses pour générer des caractères littéraux qui ont également une signification spéciale dans la syntaxe de mise en forme. Par exemple, si vous souhaitez entourer un mot d’astérisques littéraux (au lieu d’une balise HTML &lt;em>), vous pouvez utiliser des barres obliques inverses avant les astérisques, comme suit :

    `\\*literal asterisks\\*`

Les échappements par barre oblique inverse sont disponibles pour les caractères suivants :

    ` \ backslash`

    `` ` backtick``

    ` * asterisk`

    ` _ underscore`

    ` {} curly braces`

    ` [] square brackets`

    ` () parentheses`

    ` # hash mark`

    ` + plus sign`

    ` - minus sign (hyphen)`

    ` . dot`
