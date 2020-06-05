---
title: Configurez l’éditeur de texte enrichi pour créer du contenu dans Adobe Experience Manager en tant que service Cloud.
description: Configurez l’éditeur de texte enrichi pour créer du contenu dans Adobe Experience Manager en tant que service Cloud.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 165dc4af656ce1bc431d2f921775ebda4cf4de9f
workflow-type: tm+mt
source-wordcount: '2078'
ht-degree: 52%

---


# Configuration de l’éditeur de texte enrichi {#configure-the-rich-text-editor}

L’Editeur de texte enrichi (RTE) offre aux auteurs un large éventail de fonctionnalités pour modifier le contenu de texte. Les icônes, les boîtes de dialogue de sélection, la barre d’outils et les menus sont fournis pour une expérience WYSIWYG de la modification de texte. Les administrateurs configurent le RTE pour activer, désactiver et étendre les fonctionnalités disponibles dans les composants de création. Pour savoir comment utiliser les fonctions d’éditeur de texte enrichi pour la création, voir [Utilisation de l’éditeur de texte enrichi pour la création](rich-text-editor.md). Découvrez comment les auteurs [utilisent RTE pour créer](/help/sites-cloud/authoring/fundamentals/rich-text-editor.md) du contenu Web.

Les concepts et les étapes de configuration de l’ETC sont répertoriés ci-dessous.

| Comprendre les concepts de RTE | Activer les fonctionnalités requises | Configurer des fonctionnalités individuelles |
|---|---|---|
| [Comprendre l&#39;interface](#understand-rte-ui) | [Comprendre et définir des emplacements de configuration](#understand-the-configuration-paths-and-locations) | [Configuration des modules externes](#enable-rte-functionalities-by-activating-plug-ins) |
| [Types de modes de modification](#editingmodes) | [Activation des modules externes](/help/implementing/developing/extending/configure-rich-text-editor-plug-ins.md#activateplugin) | [Définition des propriétés des fonctions](#aboutplugins) |
| [À propos des modules externes](#aboutplugins) | [Configuration des barres d’outils RTE](#dialogfullscreen) | [Configuration des modes de collage](/help/implementing/developing/extending/configure-rich-text-editor-plug-ins.md#textstyles) |

## Comprendre l’interface utilisateur disponible pour les auteurs {#understand-rte-ui}

L’interface RTE offre une conception [](/help/sites-cloud/authoring/features/responsive-layout.md) réactive pour l’environnement de création. L&#39;interface est conçue pour être utilisée sur les périphériques tactiles et de bureau.

![Barre d’outils Editeur de texte enrichi](assets/rte-toolbar-full-screen-mode.png)

*Figure : Barre d’outils de l’éditeur de texte enrichi avec toutes les options disponibles activées.*

La barre d’outils fournit les options de l’expérience de création WYSIWYG. Les administrateurs d’Experience Manager peuvent configurer les options disponibles dans la barre d’outils de l’interface. Un ensemble complet d’options de modification est disponible par défaut dans Experience Manager. Les développeurs peuvent personnaliser Experience Manager pour ajouter d’autres options d’édition.

## Différents modes de modification {#editingmodes}

Les auteurs peuvent créer et modifier du contenu textuel dans Experience Manager à l’aide des différents modes de composants. Les options de la barre d’outils pour la création et la mise en forme du contenu, et l’expérience utilisateur des composants compatibles avec l’éditeur de texte enrichi dans différents modes de modification, varient en fonction des configurations d’éditeur de texte enrichi.

| Mode de modification | Zone de modification | Fonctions dont l’activation est recommandée |
|--- |--- |--- |
| En ligne | Modification en ligne pour des modifications rapides et mineures ; mettez en forme sans ouvrir une zone de dialogue | Fonctions minimales d’éditeur de texte enrichi |
| Éditeur de texte enrichi en plein écran | Couvre la page entière | Toutes les fonctions requises d’éditeur de texte enrichi |
| Boîte de dialogue | Boîte de dialogue située en haut du contenu de page sans couvrir la page entière | Activation judicieuse des fonctionnalités |
| Boîte de dialogue plein écran | Identique au mode plein écran ; contient des champs de la boîte de dialogue à côté de l’éditeur de texte enrichi | Toutes les fonctions requises d’éditeur de texte enrichi |

>[!NOTE]
>
>La fonction d’édition source n’est pas disponible en mode d’édition intégré. Vous ne pouvez pas faire glisser les images en mode plein écran. Toutes les autres fonctions sont utilisables dans tous les modes.

### Modification en ligne {#inline-editing}

Une fois ouvert (avec un doublon-clic lent), le contenu peut être modifié dans la page. Une barre d’outils compacte avec des options très basiques est présentée.

![Modification en ligne avec les options de base dans la barre d’outils](assets/inline-editing-mode-basic-options.png)

*Figure : Modification en ligne avec les options de base dans la barre d’outils.*

### Modification en plein écran {#full-screen-editing}

Les composants d’Experience Manager peuvent être ouverts dans une vue en plein écran qui masque le contenu de la page et occupe l’écran disponible. Considérez la modification en plein écran comme une version détaillée de la modification en ligne, car elle offre le plus grand nombre d’options de modification. It can be opened by clicking ![rte_fullscreen](assets/rte_fullscreen.png), from the compact toolbar when using the inline editing mode.

En mode de boîte de dialogue plein écran, outre une barre d’outils détaillée d’éditeur de texte enrichi, les options et les composants disponibles dans une boîte de dialogue sont également disponibles. Il s’applique seulement aux boîtes de dialogue qui contiennent l’éditeur de texte enrichi à côté d’autres composants.

![Barre d’outils RTE détaillée lors de la modification en mode plein écran](assets/rte-toolbar-full-screen-mode.png)

*Figure : Barre d’outils RTE détaillée lors de la modification en mode plein écran.*

### Modification dans une boîte de dialogue {#dialog-editing}

Lorsque vous double-cliquez sur un composant, une boîte de dialogue apparaît pour modifier le contenu. La boîte de dialogue s’ouvre dans la partie supérieure de la page existante. Dans quelques scénarios spécifiques, la boîte de dialogue s’affiche comme fenêtre contextuelle. Par exemple, lorsqu’un composant Texte fait partie d’une colonne dans une mise en page à plusieurs colonnes et que la zone disponible pour la boîte de dialogue est moindre.

![Mode de modification de la boîte de dialogue](assets/dialog_editing_modetouchui.png)

*Figure : Mode de modification de la boîte de dialogue.*

## À propos des modules externes d’éditeur de texte enrichi et des fonctions associées {#aboutplugins}

Cette fonctionnalité est mise à disposition par le biais d’une série de modules externes, comportant chacun :

* Une `features` propriété qui est

   * Utilisé pour activer ou désactiver les fonctionnalités de base de ce module externe.
   * Configuré selon une procédure normalisée.

* Le cas échéant, propriétés et options supplémentaires nécessitant une configuration spécialisée.

Les fonctions de base d’éditeur de texte enrichi sont activées, ou désactivées, par la valeur de la propriété `features` sur un nœud spécifique au module externe approprié.

Le tableau ci-dessous répertorie les modules externes actuels et indique les informations suivantes :

* Les ID des modules externes avec un lien vers la documentation des API. L’ID est utilisé comme nom de nœud lors de l’[activation d’un module externe](/help/implementing/developing/extending/configure-rich-text-editor-plug-ins.md#activateplugin).
* Les valeurs admises pour la propriété `features`.
* Une description de la fonctionnalité fournie par le module externe.

| ID du module externe | features | Description |
|--- |--- |--- |
| edit | cut copy paste-default paste-plaintext paste-wordhtml | [Couper, copier et les trois modes de collage](/help/implementing/developing/extending/configure-rich-text-editor-plug-ins.md#textstyles). |
| [findreplace](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.FindReplacePlugin) | find replace | Rechercher et remplacer. |
| [format](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.FormatPlugin) | bold italic underline | [Mise en forme textuelle de base](configure-rich-text-editor-plug-ins.md#textstyles). |
| [image](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.ImagePlugin) | image | Prise en charge des images de base (faites glisser le curseur depuis le contenu ou l’outil de recherche de contenu). Selon le navigateur, la prise en charge présente différents comportements pour les auteurs |
| [keys](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.KeyPlugin) |  | Pour définir cette valeur, voir [taille de tabulation](configure-rich-text-editor-plug-ins.md#tabsize). |
| [justify](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.JustifyPlugin) | justifyleft justifycenter justifyright | Alignement de paragraphe. |
| [links](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.LinkPlugin) | modifylink unlink anchor | [Liens hypertextes et ancres](configure-rich-text-editor-plug-ins.md#linkstyles). |
| [lists](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.ListPlugin) | ordered unordered indent outdent | This plug-in controls both [indentation and lists](configure-rich-text-editor-plug-ins.md#indentmargin); including nested lists. |
| [misctools](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.MiscToolsPlugin) | specialchars sourceedit | Miscellaneous tools allow authors to enter [special characters](configure-rich-text-editor-plug-ins.md#spchar) or edit the HTML source. Also, you can add a whole [range of special characters](configure-rich-text-editor-plug-ins.md#definerangechar) if you want to define your own list. |
| Paraformat | paraformat | The default paragraph formats are Paragraph, Heading 1, Heading 2, and Heading 3 (`<p>`, `<h1>`, `<h2>`, and `<h3>`). Vous pouvez [ajouter davantage de formats de paragraphe](configure-rich-text-editor-plug-ins.md#paraformats) ou prolonger la liste. |
| spellcheck | checktext | [Vérificateur orthographique sensible à la langue](configure-rich-text-editor-plug-ins.md#adddict). |
| styles | styles | Prise en charge de la mise en forme à l’aide d’une classe CSS. [Ajoutez de nouveaux styles](configure-rich-text-editor-plug-ins.md#textstyles) de texte si vous souhaitez ajouter (ou étendre) votre propre plage de styles à utiliser avec du texte. |
| subsuperscript | subscript superscript | Extensions aux formats de base, ajout de sous-scripts et de super-scripts. |
| table | table removetable insertrow removerow insertcolumn removecolumn cellprops mergecells splitcell selectrow selectcolumns | See [configure table styles](configure-rich-text-editor-plug-ins.md#tablestyles), if you want to add your own styles for either entire tables or individual cells. |
| undo | undo redo | History size of [undo and redo](configure-rich-text-editor-plug-ins.md#undohistory) operations. |

>[!NOTE]
>
>Le module externe Plein écran n’est pas pris en charge en mode de boîte de dialogue. Use of the `dialogFullScreen` setting to configure the toolbar for full screen mode.

## Présentation des chemins et des emplacements de configuration {#understand-the-configuration-paths-and-locations}

[Mode de modification d’éditeur de texte enrichi (et de l’IU)](#editingmodes) que vous fournissez pour que les auteurs déterminent l’emplacement des informations de configuration lorsque vous [activez les modules externes d’éditeur de texte enrichi](configure-rich-text-editor-plug-ins.md#activateplugin) :

* Mode intégré : `cq:editConfig/cq:inplaceEditing`
* Mode Plein écran: `cq:editConfig/cq:inplaceEditing`
* Mode boîte de dialogue : `cq:dialog`
* Mode de dialogue plein écran : `cq:dialog`

>[!NOTE]
>
>Do not name the node under `cq:inplaceEditing` as `config`. On `cq:inplaceEditing` node, define the following properties:
>
>* **Nom**: `configPath`
>* **Type**: `String`
>* **Valeur** : chemin du nœud qui contient la configuration proprement dite.

>
>
Ne donnez pas le nom `config` au nœud de configuration de l’éditeur de texte enrichi (RTE). Otherwise, the RTE configurations take effect for only the administrators and not for the users in the group `content-author`.

Configurez les propriétés suivantes qui s’appliquent en mode d’édition Boîte de dialogue :

* `useFixedInlineToolbar`: Définissez cette propriété booléenne définie sur le noeud RTE (un avec sling:resourceType= `cq/gui/components/authoring/dialog/richtext`) sur `True`, pour que la barre d’outils RTE soit fixe plutôt que flottante.

    Lorsque cette propriété est définie sur true, la modification en texte démarre par défaut sur l’événement « foundation-contentloaded ».

   Pour éviter cette situation, définissez la propriété `customStart``True` sur et déclenchez l’événement « rte-start » pour commencer la modification avec l’éditeur de texte enrichi. Lorsque cette propriété est définie sur true, le comportement par défaut (l’éditeur de texte enrichi démarre en cas de clic) ne fonctionne pas.

* `customStart` : configurez cette propriété booléenne définie sur le nœud de l’éditeur de texte enrichi sur `True` pour contrôler à quel moment démarrer l’éditeur de texte enrichi en déclenchant l’événement `rte-start`.

* `rte-start` : déclenchez cet événement sur l’élément `contenteditable-div` d’éditeur de texte enrichi lorsque vous commencez la modification avec l’éditeur de texte enrichi. Cette option ne fonctionne que si `customStart` a été défini sur true.

Lorsque RTE est utilisé dans la boîte de dialogue tactile, définissez la propriété `useFixedInlineToolbar` pour `true` éviter les problèmes.

## Activation des fonctionnalités d’éditeur de texte enrichi en activant des modules externes {#enable-rte-functionalities-by-activating-plug-ins}

Les fonctionnalités d’éditeur de texte enrichi sont rendues disponibles par l’intermédiaire d’une série de modules externes, chacun avec sa propriété features. Vous pouvez configurer la propriété features afin d’activer ou de désactiver une ou plusieurs fonctions de chaque module externe.

Pour consulter des configurations détaillées des modules externes de l’éditeur de texte enrichi, voir [Activation et configuration des modules externes de l’éditeur de texte enrichi](configure-rich-text-editor-plug-ins.md).

<!-- TBD ENGREVIEW: To confirm if the sample works in CS or not?
**Sample**: Download [this sample configuration](/help/sites-administering/assets/rte-sample-all-features-enabled-10.zip) that illustrates how to configure RTE. In this package all the features are enabled. -->

The [Core Components text component](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/components/text.html#the-text-component-and-the-rich-text-editor) allows template editors to configure many RTE plugins using the user interface as content policies, eliminating the need for technical configuration. Les stratégies de contenu peuvent fonctionner avec les configurations d’interface utilisateur de l’éditeur de texte enrichi décrites dans ce document. For more information, see [create page templates](/help/sites-cloud/authoring/features/templates.md) and the [Core Components developer documentation](https://docs.adobe.com/content/help/fr-FR/experience-manager-core-components/using/developing/developing.html).

>À titre de référence, les composants Texte par défaut (fournis dans le cadre d’une installation standard) se trouvent sous :
>
>* `/libs/wcm/foundation/components/text`
>* `/libs/foundation/components/text`

>
>
Pour créer votre propre composant textuel, copiez le composant ci-dessus au lieu de modifier ces composants.

## Configuration de la barre d’outils de l’éditeur de texte enrichi {#dialogfullscreen}

Experience Manager vous permet de configurer l’interface de l’éditeur de texte enrichi différemment selon les différents modes de modification. Les paramètres par défaut sont fournis ci-dessous. Vous pouvez remplacer ces paramètres par défaut en fonction de vos besoins. Vous personnalisez uniquement les fonctions de barre d’outils que vous souhaitez fournir à vos auteurs. Vous n’avez pas besoin de définir toutes les configurations de barre d’outils.

Pour configurer la barre d’outils pour `dialogFullScreen`, utilisez l’exemple de configuration suivant.

```java
<uiSettings jcr:primaryType="nt:unstructured">
  <cui jcr:primaryType="nt:unstructured">
    <inline
      jcr:primaryType="nt:unstructured"
      toolbar="[format#bold,format#italic,format#underline,#justify,#lists,links#modifylink,links#unlink,#paraformat]">
      <popovers jcr:primaryType="nt:unstructured">
        <justify
          jcr:primaryType="nt:unstructured"
          items="[justify#justifyleft,justify#justifycenter,justify#justifyright,justify#justifyjustify]"
          ref="justify"/>
        <lists
          jcr:primaryType="nt:unstructured"
          items="[lists#unordered,lists#ordered,lists#outdent,lists#indent]"
          ref="lists"/>
        <paraformat
          jcr:primaryType="nt:unstructured"
          items="paraformat:getFormats:paraformat-pulldown"
          ref="paraformat"/>
      </popovers>
    </inline>
    <dialogFullScreen
      jcr:primaryType="nt:unstructured"
      toolbar="[format#bold,format#italic,format#underline,justify#justifyleft,justify#justifycenter,justify#justifyright,justify#justifyjustify,lists#unordered,lists#ordered,lists#outdent,lists#indent,links#modifylink,links#unlink,table#createoredit,#paraformat,image#imageProps]">
      <popovers jcr:primaryType="nt:unstructured">
        <paraformat
          jcr:primaryType="nt:unstructured"
          items="paraformat:getFormats:paraformat-pulldown"
          ref="paraformat"/>
      </popovers>
    </dialogFullScreen>
    <tableEditOptions
      jcr:primaryType="nt:unstructured"
      toolbar="[table#insertcolumn-before,table#insertcolumn-after,table#removecolumn,-,table#insertrow-before,table#insertrow-after,table#removerow,-,table#mergecells-right,table#mergecells-down,table#mergecells,table#splitcell-horizontal,table#splitcell-vertical,-,table#selectrow,table#selectcolumn,-,table#ensureparagraph,-,table#modifytableandcell,table#removetable,-,undo#undo,undo#redo,-,table#exitTableEditing,-]">
    </tableEditOptions>
  </cui>
</uiSettings>
```

Différents paramètres d’IU sont utilisés pour les modes en ligne et plein écran. La propriété toolbar est utilisée pour spécifier les boutons de la barre d’outils.

For example, if the button is itself a feature (for example, `Bold`), it is specified as `PluginName#FeatureName` (for example, `links#modifylink`).

If the button is a popover (containing some features of a plug-in), it is specified as `#PluginName` (for example, `#format`).

Separators (`|`) between a group of buttons can be specified with `-`.

Le nœud pop-up sous le mode en ligne ou plein écran contient la liste des éléments contextuels utilisés. Chaque nœud enfant sous le nœud « popovers » (éléments contextuels) est nommé en fonction du module externe (format, par exemple). Il possède des « éléments » de propriété contenant la liste des fonctions du module externe (format#bold, par exemple).

## Paramètres de l’interface utilisateur de l’éditeur de texte enrichi et stratégies de contenu {#rtecontentpolicies}

Les administrateurs peuvent contrôler les options de l’éditeur de texte enrichi à l’aide de stratégies de contenu, au lieu de procéder à la configuration en suivant les instructions ci-dessus, par exemple. Les stratégies de contenu définissent les propriétés de conception d’un composant lorsqu’il est utilisé dans le cadre d’un [modèle modifiable](/help/sites-cloud/authoring/features/templates.md). Par exemple, si un composant textuel qui utilise l’éditeur de texte enrichi est employé avec un modèle modifiable, la stratégie de contenu peut définir que l’option Gras doit être disponible, au même titre que quelques options de mise en forme de paragraphe. Les stratégies de contenu sont réutilisables et peuvent être appliquées à plusieurs modèles.

Les options disponibles dans l’éditeur texte enrichi sont transmises depuis les configurations de l’interface utilisateur en amont vers les stratégies de contenu.

* Les paramètres de configuration de l’interface utilisateur définissent les options disponibles pour les stratégies de contenu.
* Si la configuration de l&#39;interface utilisateur de l&#39;ETC a été supprimée ou n&#39;active pas un élément, la stratégie de contenu ne peut pas le configurer.
* Un auteur n’a accès à une fonctionnalité de ce type que si elle est mise à sa disposition par les configurations de l’interface utilisateur et les stratégies de contenu.

Pour consulter un exemple, reportez-vous à la [documentation du composant principal Texte](https://docs.adobe.com/help/fr/experience-manager-core-components/using/components/text.html#the-text-component-and-the-rich-text-editor).

## Personnalisation de l’association entre les commandes et les icônes de la barre d’outils {#iconstoolbar}

Vous pouvez personnaliser l’association entre les icônes de Coral affichées dans la barre d’outils de l’éditeur de texte enrichi et les commandes disponibles. Vous ne pouvez utiliser que les icônes de Coral.

1. Create a node named `icons` under `uiSettings/cui`.

1. Sous ce nœud, créez des nœuds pour les différentes icônes.
1. Sur chacun des noeuds d’icône individuels, spécifiez une icône Coral et une commande pour mapper à l’icône.

Vous trouverez, ci-dessous, un exemple de fragment de code pour associer la commande Gras à l’icône Coral intitulée `textItalic`.

```java
<text jcr:primaryType="nt:unstructured" sling:resourceType="cq/gui/components/authoring/dialog/richtext" name="./text" useFixedInlineToolbar="{Boolean}true">
    <rtePlugins jcr:primaryType="nt:unstructured">
        <format jcr:primaryType="nt:unstructured" features="bold,italic"/>
    </rtePlugins>
    <uiSettings jcr:primaryType="nt:unstructured">
        <cui jcr:primaryType="nt:unstructured">
            <inline jcr:primaryType="nt:unstructured"
                toolbar="[format#bold,format#italic,format#underline,links#modifylink,links#unlink]">
            </inline>
            <icons jcr:primaryType="nt:unstructured">
                <bold jcr:primaryType="nt:unstructured"
                    command="format#bold"
                    icon="textItalic"/>
            </icons>
        </cui>
    </uiSettings>
</text>
```

## Limitations connues {#known-limitations}

La fonctionnalité RTE d’Experience Manager présente les limites suivantes :

* Les fonctionnalités RTE sont uniquement prises en charge dans les boîtes de dialogue des composants d’Experience Manager. RTE n’est pas pris en charge sur les assistants ou les formulaires Foundation.

* Experience Manager ne fonctionne pas sur les périphériques hybrides. <!-- TBD: Check. This is not mentioned in Known Issue /help/release-notes/known-issues.md-->

* Do not name the RTE configuration node `config`. Otherwise, the RTE configuration takes effect for only the administrators and not for the users in the group `content-author`.

* RTE ne prend pas en charge l’incorporation de contenu dans un cadre intégré ou un iframe.

## Best practices and tips {#best-practices-and-tips}

* Pour une boîte de dialogue flottante, activez uniquement les modules externes sans fenêtre contextuelle. Les plug-ins sans fenêtre contextuelle sont de taille plus petite et conviennent mieux à une boîte de dialogue flottante.
* Enable the plug-ins with larger pop-up, such as the `Paste` plug-in, only in the full-screen dialog mode or in full-screen mode. Les modules externes avec une grande fenêtre contextuelle nécessitent davantage d’espace sur l’écran pour offrir une expérience de création optimale.
* Si vous employez des modules externes personnalisés pour l’éditeur de texte enrichi CoralUI , utilisez la bibliothèque `rte.coralui3`3.

>[!MORELIKETHIS]
>
>* [Configuration des modules externes d’éditeur de texte enrichi](configure-rich-text-editor-plug-ins.md)
>* [Utilisation de l’éditeur de texte enrichi pour la création](/help/sites-cloud/authoring/fundamentals/rich-text-editor.md)
>* [Configuration de l’éditeur de texte enrichi pour les sites accessibles](rte-accessible-content.md)
>* [Extrait d’un tutoriel pour créer un composant multichamp composite](https://experience-aem.blogspot.com/2019/05/aem-65-touchui-composite-multifield-with-coral3-rte-rich-text.html)

