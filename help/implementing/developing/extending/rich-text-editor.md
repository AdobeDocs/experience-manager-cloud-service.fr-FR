---
title: Configurez l’éditeur de texte enrichi pour créer du contenu dans [!DNL Adobe Experience Manager] as a Cloud Service.
description: Configurez l’éditeur de texte enrichi pour créer du contenu dans [!DNL Adobe Experience Manager] as a Cloud Service.
contentOwner: AG
exl-id: 1f0ff800-5e95-429a-97f2-221db0668170
feature: Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1892'
ht-degree: 96%

---


# Configuration de l’éditeur de texte enrichi {#configure-the-rich-text-editor}

L’éditeur de texte enrichi met à la disposition des auteurs de nombreuses fonctionnalités pour modifier leur contenu textuel. Les icônes, les boîtes de dialogue de sélection, la barre d’outils et les menus apportent une expérience WYSIWYG de la modification des textes. Les administrateurs configurent l’éditeur de texte enrichi pour activer, désactiver et étendre les fonctions disponibles dans les composants de création. Découvrez comment les auteurs [utilisent l’éditeur de texte enrichi pour créer](/help/sites-cloud/authoring/page-editor/rich-text-editor.md) du contenu web.

Les concepts et les étapes de configuration de l’éditeur de texte enrichi sont répertoriés ci-dessous.

| Comprendre les concepts de l’éditeur de texte enrichi | Activer les fonctionnalités requises | Configurer des fonctionnalités individuelles |
|---|---|---|
| [Présentation de l’interface](#understand-rte-ui) | [Présentation et définition des emplacements de configuration](#understand-the-configuration-paths-and-locations) | [Configuration des modules externes](#enable-rte-functionalities-by-activating-plug-ins) |
| [Types de modes de modification](#editingmodes) | [Activation des modules externes](/help/implementing/developing/extending/configure-rich-text-editor-plug-ins.md#activateplugin) | [Définition des propriétés des fonctions](#aboutplugins) |
| [À propos des modules externes](#aboutplugins) | [Configuration des barres d’outils de l’éditeur de texte enrichi](#dialogfullscreen) | [Configuration des modes de collage](/help/implementing/developing/extending/configure-rich-text-editor-plug-ins.md#textstyles) |

>[!NOTE]
>
>L’éditeur de texte enrichi décrit dans ce document décrit celui qui est disponible dans l’éditeur de page. Si vous utilisez l’éditeur universel moderne, consultez le document [Configuration de l’éditeur universel](/help/implementing/universal-editor/configure-rte.md) pour plus d’informations.

## Présentation de l’interface utilisateur disponible pour les auteurs {#understand-rte-ui}

L’interface de l’éditeur de texte enrichi s’appuie sur une approche de [responsive design](/help/sites-cloud/authoring/page-editor/responsive-layout.md) pour l’environnement de création. Elle est conçue pour être utilisée sur les appareils tactiles et de bureau.

![Barre d’outils de l’éditeur de texte enrichi](assets/rte-toolbar-full-screen-mode.png)

*Figure : Barre d’outils de l’éditeur de texte enrichi avec toutes les options disponibles activées.*

La barre d’outils contient les options nécessaires pour une expérience de création WYSIWYG. Les administrateurs d’[!DNL Experience Manager] peuvent configurer les options disponibles dans la barre d’outils de l’interface. Un ensemble complet d’options de modification est disponible par défaut dans [!DNL Experience Manager]. Les développeurs peuvent personnaliser [!DNL Experience Manager] pour ajouter d’autres options de modification.

## Différents modes de modification {#editingmodes}

Les auteurs peuvent créer et modifier du contenu textuel dans [!DNL Experience Manager] en utilisant les différents modes des composants. Les options de la barre d’outils dédiées à la création et à la mise en forme de contenu, ainsi que l’expérience utilisateur des composants compatibles avec l’éditeur de texte enrichi dans les différents modes de modification, varient selon les configurations de l’éditeur de texte enrichi.

| Mode de modification | Zone de modification | Fonctions dont l’activation est recommandée |
|--- |--- |--- |
| En ligne | Modification en ligne pour des modifications rapides et mineures ; mettez en forme sans ouvrir une boîte de dialogue. | Fonctions minimales d’éditeur de texte enrichi. |
| Éditeur de texte enrichi en plein écran | Couvre toute la page. | Toutes les fonctions requises d’éditeur de texte enrichi. |
| Boîte de dialogue | Boîte de dialogue située en haut du contenu de page sans couvrir la page entière. | Activation judicieuse des fonctionnalités. |
| Boîte de dialogue plein écran | Identique au mode plein écran ; contient des champs de la boîte de dialogue avec l’éditeur de texte enrichi. | Toutes les fonctions requises d’éditeur de texte enrichi. |

>[!NOTE]
>
>La fonction de modification de source n’est pas disponible dans le mode de modification en ligne. Vous ne pouvez pas faire glisser les images en mode plein écran. Toutes les autres fonctions sont utilisables dans tous les modes.

### Modification en ligne {#inline-editing}

Pour modifier le contenu d’une page, ouvrez-le en double-cliquant lentement dessus. Une barre d’outils compacte avec des options de base est présentée.

![Modification en ligne avec les options de base dans la barre d’outils](assets/inline-editing-mode-basic-options.png)

*Figure : Modification en ligne avec les options de base dans la barre d’outils.*

### Modification en plein écran {#full-screen-editing}

Les composants [!DNL Experience Manager] peuvent être ouverts dans une vue plein écran qui masque le contenu de la page et occupe l’écran disponible. Considérez la modification en plein écran comme une version détaillée de la modification en ligne, car elle offre le plus grand nombre d’options de modification. Vous pouvez l’ouvrir en cliquant sur ![Icône d’ouverture de RTE en plein écran](assets/rte_fullscreen.png), dans la barre d’outils compacte lorsque vous utilisez le mode de modification en ligne.

Dans le mode de boîte de dialogue plein écran, outre une barre d’outils détaillée d’éditeur de texte enrichi, les options et les composants disponibles dans une boîte de dialogue sont également disponibles. Il s’applique seulement aux boîtes de dialogue qui contiennent l’éditeur de texte enrichi à côté d’autres composants.

![Barre d’outils détaillée de l’éditeur de texte enrichi au cours d’une modification en mode plein écran](assets/rte-toolbar-full-screen-mode.png)

*Figure : Barre d’outils détaillée de l’éditeur de texte enrichi au cours d’une modification en mode plein écran.*

### Modification dans une boîte de dialogue {#dialog-editing}

Lorsqu’un composant fait l’objet d’un double clic, une boîte de dialogue s’ouvre permettant de modifier le contenu. La boîte de dialogue s’affiche en haut de la page existante. Dans certains scénarios spécifiques, la boîte de dialogue s’ouvre sous la forme d’une fenêtre pop-up. C’est notamment le cas lorsqu’un composant Texte fait partie d’une colonne dans une disposition à plusieurs colonnes et que la zone disponible pour la boîte de dialogue est moindre.

![Mode de modification dans une boîte de dialogue](assets/dialog_editing_modetouchui.png)

*Figure : Mode de modification dans une boîte de dialogue.*

## À propos des modules externes de l’éditeur de texte enrichi et des fonctions associées {#aboutplugins}

Cette fonctionnalité est mise à disposition par le biais d’une série de modules externes, comportant chacun :

* une propriété `features` qui est :

   * utilisée afin d’activer ou désactiver une fonctionnalité de base pour ce module externe ;
   * configurée selon une procédure normalisée.

* Le cas échéant, des propriétés et options supplémentaires nécessitant une configuration spécialisée.

Les fonctions de base d’éditeur de texte enrichi sont activées, ou désactivées, par la valeur de la propriété `features` sur un nœud spécifique au module externe approprié.

Le tableau suivant répertorie les plug-ins actuels et présente les informations suivantes :

* Les ID de plug-in avec un lien vers la documentation de l’API. L’ID est utilisé comme nom de nœud lors de l’[activation d’un plug-in](/help/implementing/developing/extending/configure-rich-text-editor-plug-ins.md#activateplugin).
* Les valeurs admises pour la propriété `features`.
* Une description de la fonctionnalité fournie par le module externe.

| ID du module externe | features | Description |
|--- |--- |--- |
| edit | `cut`, `copy`, `paste-default`, `paste-plaintext`, `paste-wordhtml` | [Couper, copier et les trois modes de collage](/help/implementing/developing/extending/configure-rich-text-editor-plug-ins.md#textstyles). |
| findreplace | `find`, `replace` | Rechercher et remplacer. |
| format | `bold`, `italic`, `underline` | [Mise en forme de texte de base](configure-rich-text-editor-plug-ins.md#textstyles). |
| image | `image` | Prise en charge de base des images (faire glisser à partir du contenu ou de l’outil de recherche de contenu). Selon le navigateur, la prise en charge présente différents comportements pour les auteurs |
| keys | - | Pour définir cette valeur, consultez la [taille des onglets](configure-rich-text-editor-plug-ins.md#tabsize). |
| justify | `justifyleft`, `justifycenter`, `justifyright` | Alignement des paragraphes. |
| links | `modifylink`, `unlink`, `anchor` | [Hyperliens et ancres](configure-rich-text-editor-plug-ins.md#linkstyles). |
| lists | `ordered`, `unordered`, `indent`, `outdent` | Ce plug-in contrôle à la fois la [mise en retrait et les listes](configure-rich-text-editor-plug-ins.md#indentmargin), y compris les listes imbriquées. |
| misctools | `specialchars`, `sourceedit` | Divers outils permettent aux auteurs de saisir des [caractères spéciaux](configure-rich-text-editor-plug-ins.md#spchar) ou de modifier la source HTML. En outre, vous pouvez ajouter une [gamme de caractères spéciaux](configure-rich-text-editor-plug-ins.md#definerangechar) si vous voulez définir votre propre liste. |
| Paraformat | `paraformat` | Les formats de paragraphe par défaut sont : Paragraphe, En-tête 1, En-tête 2 et En-tête 3 (`<p>`, `<h1>`, `<h2>` et `<h3>`). Vous pouvez [ajouter d’autres formats de paragraphe](configure-rich-text-editor-plug-ins.md#paraformats) ou allonger la liste. |
| spellcheck | `checktext` | [Vérificateur orthographique prenant en compte la langue](configure-rich-text-editor-plug-ins.md#adddict). |
| styles | `styles` | Prise en charge de l’application d’un style en utilisant une classe CSS. [Ajoutez de nouveaux styles de texte](configure-rich-text-editor-plug-ins.md#textstyles) si vous voulez ajouter (ou étendre) votre propre gamme de styles utilisables avec du texte. |
| subsuperscript | `subscript`, `superscript` | Extensions des formats de base, en ajoutant l’indice et l’exposant. |
| table | `table`, `removetable`, `insertrow`, `removerow`, `insertcolumn`, `removecolumn`, `cellprops`, `mergecells`, `splitcell`, `selectrow`, `selectcolumns` | Voir [Configuration des styles de tableau](configure-rich-text-editor-plug-ins.md#tablestyles) afin d’ajouter vos propres styles pour des tableaux entiers ou des cellules individuelles. |
| undo | `undo`, `redo` | Taille de l’historique des opérations [d’annulation et de rétablissement](configure-rich-text-editor-plug-ins.md#undohistory). |

>[!NOTE]
>
>Le module externe Plein écran n’est pas pris en charge en mode de boîte de dialogue. Utilisation du paramètre `dialogFullScreen` pour configurer la barre d’outils en mode plein écran.

## Présentation des chemins et des emplacements de configuration {#understand-the-configuration-paths-and-locations}

[Mode de modification d’éditeur de texte enrichi et de l’interface](#editingmodes) que vous fournissez pour que les auteurs déterminent l’emplacement des informations de configuration lorsque vous [activez les modules externes d’éditeur de texte enrichi](configure-rich-text-editor-plug-ins.md#activateplugin). Les emplacements sont les suivants :

* Mode en ligne : `cq:editConfig/cq:inplaceEditing`.
* Mode Plein écran : `cq:editConfig/cq:inplaceEditing`.
* Mode Boîte de dialogue : `cq:dialog`.
* Mode Boîte de dialogue plein écran : `cq:dialog`.

>[!NOTE]
>
>Ne donnez pas le nom `cq:inplaceEditing` au nœud sous `config`. Sur le nœud `cq:inplaceEditing`, définissez les propriétés suivantes :
>
>* **Nom** : `configPath`
>* **Type** : `String`
>* **Valeur** : chemin du nœud qui contient la configuration proprement dite.
>
>Ne donnez pas le nom `config` au nœud de configuration de l’éditeur de texte enrichi (RTE). Autrement, les configurations de l’éditeur de texte enrichi prennent effet seulement pour les administrateurs et non pour les utilisateurs du groupe `content-author`.

Configurez les propriétés suivantes qui s’appliquent uniquement au mode de modification dans la boîte de dialogue :

* `useFixedInlineToolbar` : vous pouvez faire en sorte que la barre d’outils de l’éditeur de texte enrichi soit fixe plutôt que flottante. Définissez cette propriété booléenne définie sur le nœud de l’éditeur de texte enrichi avec sling:resourceType= `cq/gui/components/authoring/dialog/richtext` sur `True`. Lorsque cette propriété est définie sur `True`, la modification de texte enrichi est lancée sur l’événement `foundation-contentloaded`. Pour éviter cela, définissez la propriété `customStart` sur `True` et déclenchez l’événement `rte-start` afin de commencer la modification avec l’éditeur de texte enrichi. Lorsque cette propriété est définie sur `true`, l’éditeur de texte enrichi ne démarre pas sur un clic et il s’agit du comportement par défaut.

* `customStart` : configurez cette propriété booléenne définie sur le nœud de l’éditeur de texte enrichi sur `True` pour contrôler à quel moment démarrer l’éditeur de texte enrichi en déclenchant l’événement `rte-start`.

* `rte-start` : déclenchez cet événement sur l’élément `contenteditable-div` d’éditeur de texte enrichi lorsque vous commencez la modification avec l’éditeur de texte enrichi. Cette option ne fonctionne que si `customStart` a été défini sur `true`.

Lorsque l’éditeur de texte enrichi est utilisé dans la boîte de dialogue tactile, définissez la propriété `useFixedInlineToolbar` sur `true` pour éviter les problèmes.

## Activation des fonctionnalités d’éditeur de texte enrichi en activant des modules externes {#enable-rte-functionalities-by-activating-plug-ins}

Les fonctionnalités d’éditeur de texte enrichi sont rendues disponibles par l’intermédiaire d’une série de modules externes, chacun avec sa propriété features. Vous pouvez configurer la propriété features pour activer ou désactiver les différentes fonctionnalités de chaque plug-in.

Pour obtenir des configurations détaillées des plug-ins d’éditeur de texte enrichi, voir [Comment activer et configurer les plug-ins d’éditeur de texte enrichi](configure-rich-text-editor-plug-ins.md).

<!-- TBD ENGREVIEW: To confirm if the sample works in CS or not?
**Sample**: Download [this sample configuration](/help/sites-administering/assets/rte-sample-all-features-enabled-10.zip) that illustrates how to configure RTE. In this package all the features are enabled. -->

Le [composant Texte des composants principaux](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/text.html?lang=fr#the-text-component-and-the-rich-text-editor) permet aux éditeurs de modèle de configurer de nombreux modules externes de l’éditeur de texte enrichi en tant que politiques de contenu dans l’interface utilisateur, rendant ainsi inutile toute configuration technique. Les politiques de contenu peuvent fonctionner avec les configurations d’interface utilisateur de l’éditeur de texte enrichi décrites dans ce document. Pour plus d’informations, voir [Création de modèles de page](/help/sites-cloud/authoring/page-editor/templates.md) ainsi que la [Documentation relative au développement des composants principaux](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/developing.html?lang=fr).

>À titre de référence, les composants Texte par défaut (fournis dans le cadre d’une installation standard) se trouvent sous :
>
>* `/libs/wcm/foundation/components/text`
>* `/libs/foundation/components/text`
>
>Pour créer votre propre composant textuel, copiez le composant ci-dessus au lieu de modifier ces composants.

## Configuration de la barre d’outils de l’éditeur de texte enrichi {#dialogfullscreen}

[!DNL Experience Manager] vous permet de configurer différemment l’interface de l’éditeur de texte enrichi pour les différents modes de modification. Les paramètres par défaut sont fournis ci-dessous. Vous pouvez remplacer ces paramètres par défaut en fonction de vos besoins. Vous personnalisez uniquement les fonctionnalités de la barre d’outils que vous souhaitez fournir à vos auteurs. Vous n’avez pas besoin de définir toutes les configurations de barre d’outils.

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

Différents paramètres d’interface utilisateur sont utilisés pour le mode en ligne et le mode plein écran. La propriété toolbar spécifie l’option de la barre d’outils.

Par exemple, si l’option est elle-même une fonctionnalité (par exemple, `Bold`), elle est spécifiée sous la forme `PluginName#FeatureName` (par exemple, `links#modifylink`).

Si l’option est un élément contextuel (contenant certaines fonctionnalités d’un module externe), il est spécifié sous la forme `#PluginName` (par exemple, `#format`).

Les séparateurs (`|`) dans un groupe d’options peuvent être spécifiés par le signe `-`.

Le nœud pop-up sous le mode en ligne ou plein écran contient la liste des éléments contextuels utilisés. Chaque nœud enfant sous le nœud `popovers` (éléments contextuels) est nommé en fonction du module externe (format, par exemple). Il possède des « éléments » de propriété contenant la liste des fonctions du module externe (format#bold, par exemple).

## Paramètres de l’interface utilisateur de l’éditeur de texte enrichi et politiques de contenu {#rtecontentpolicies}

L’administration peut contrôler les options de l’éditeur de texte enrichi à l’aide de politiques de contenu, par exemple au lieu d’effectuer la configuration décrite ci-dessus. Les politiques de contenu définissent les propriétés de conception d’un composant lorsqu’il est utilisé dans le cadre d’un [modèle modifiable](/help/sites-cloud/authoring/page-editor/templates.md). Par exemple, si un composant de texte qui utilise l’éditeur de texte enrichi est utilisé avec un modèle modifiable, la politique de contenu peut définir que l’option gras est disponible, à l’instar de quelques options de mise en forme de paragraphe. Les politiques de contenu sont réutilisables et peuvent être appliquées à plusieurs modèles.

Les options disponibles dans l’éditeur de texte enrichi sont transmises depuis les configurations de l’interface utilisateur en amont vers les politiques de contenu.

* Les paramètres de configuration de l’interface utilisateur définissent les options disponibles pour les politiques de contenu.
* Si un élément a été supprimé ou n’est pas activé par la configuration d’interface utilisateur de l’éditeur de texte enrichi, la politique de contenu ne peut pas le configurer.
* Un auteur n’a accès à une fonctionnalité de ce type que si elle est mise à sa disposition par les configurations de l’interface utilisateur et les politiques de contenu.

Pour consulter un exemple, reportez-vous à la [documentation du composant principal Texte](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/text.html?lang=fr#the-text-component-and-the-rich-text-editor).

## Personnalisation de l’association entre les commandes et les icônes de la barre d’outils {#iconstoolbar}

Vous pouvez personnaliser l’association entre les icônes Coral affichées dans la barre d’outils de l’éditeur de texte enrichi et les commandes disponibles. Vous ne pouvez utiliser que les icônes Coral.

1. Créez un nœud intitulé `icons` sous `uiSettings/cui`.

1. Sous ce nœud, créez des nœuds pour les différentes icônes.
1. Sur chacun des nœuds d’icône, spécifiez une icône Coral et une commande à laquelle elle doit être associée.

Vous trouverez, ci-dessous, un exemple de fragment de code pour associer la commande `Bold` à l’icône Coral nommée `textItalic`.

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

Les fonctionnalités de l’éditeur de texte enrichi de [!DNL Experience Manager] présentent les limites suivantes :

* Les fonctionnalités de l’éditeur de texte enrichi sont prises en charge uniquement dans les boîtes de dialogue des composants [!DNL Experience Manager]. L’éditeur de texte enrichi n’est pas pris en charge dans les assistants ni les formulaires Foundation.

* [!DNL Experience Manager] ne fonctionne pas sur les appareils hybrides. <!-- TBD: Check. This is not mentioned in Known Issue /help/release-notes/known-issues.md-->

* Ne donnez pas le nom `config` au nœud de configuration de l’éditeur de texte enrichi (RTE). Autrement, les configurations de l’éditeur de texte enrichi prennent effet seulement pour les administrateurs et non pour les utilisateurs du groupe `content-author`.

* L’éditeur de texte enrichi ne prend pas en charge l’incorporation de contenus dans un cadre en ligne (iframe).

## Bonnes pratiques et astuces {#best-practices-and-tips}

* Pour une boîte de dialogue flottante, n’activez que les modules externes sans boîte de dialogue pop-up. Les plug-ins sans pop-up sont plus petits et sont les mieux adaptés aux boîtes de dialogue flottantes.
* Activez les plug-ins avec un pop-up plus grand, comme le plug-in `Paste`, uniquement en mode Boîte de dialogue plein écran ou en mode Plein écran. Les plug-ins possédant un grand pop-up nécessitent davantage d’espace sur l’écran pour offrir une expérience de création optimale.
* Si vous employez des modules externes personnalisés pour l’éditeur de texte enrichi CoralUI3, utilisez la bibliothèque `rte.coralui3`.

>[!MORELIKETHIS]
>
>* [Configuration des modules externes d’éditeur de texte enrichi](configure-rich-text-editor-plug-ins.md)
>* [Utilisation de l’éditeur de texte enrichi pour la création](/help/sites-cloud/authoring/page-editor/rich-text-editor.md)
>* [Configuration de l’éditeur de texte enrichi pour les sites accessibles](rte-accessible-content.md)
