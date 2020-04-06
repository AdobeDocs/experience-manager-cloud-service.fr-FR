---
title: Traitement des ressources à l’aide des workflows et des gestionnaires de médias
description: En savoir plus sur les différents gestionnaires de médias et sur la façon de les utiliser dans les workflows afin d’effectuer des tâches sur les ressources.
contentOwner: AG
translation-type: tm+mt
source-git-commit: f2e257ff880ca2009c3ad6c8aadd055f28309289

---


# Traitement des ressources à l’aide des workflows et des gestionnaires de médias {#processing-assets-using-media-handlers-and-workflows}

Adobe Experience Manager (AEM) Assets s’accompagne d’un ensemble de workflows et de gestionnaires de médias par défaut destinés au traitement des ressources. Le workflow définit les tâches générales à exécuter sur les ressources, puis délègue les tâches spécifiques aux gestionnaires de médias, par exemple la génération de miniatures ou l’extraction de métadonnées.

Vous pouvez définir un workflow qui doit s’exécuter automatiquement lorsqu’une ressource d’un type particulier est chargée sur le serveur. Les étapes de traitement sont définies sous la forme d’une série de gestionnaires de médias AEM Assets. AEM fournit certains [gestionnaires intégrés](#default-media-handlers) et des gestionnaires supplémentaires peuvent être [conçus et personnalisés](#creating-a-new-media-handler) ou définis en déléguant le processus à un [outil de ligne de commande](#command-line-based-media-handler).

Les gestionnaires de médias sont des services d’AEM Assets qui effectuent des actions spécifiques sur les ressources. Par exemple, lorsqu’un fichier audio MP3 est chargé dans AEM, un workflow déclenche un gestionnaire MP3 qui extrait les métadonnées et génère une miniature. Les gestionnaires de médias sont généralement utilisés conjointement avec des workflows. La plupart des types MIME courants sont pris en charge dans AEM. Il est possible d’effectuer des tâches spécifiques sur les ressources en étendant/créant des processus, en étendant/créant des gestionnaires de médias ou en désactivant/activant des gestionnaires de médias.

>[!NOTE]
>
>Reportez-vous à la page [Formats pris en charge par Assets](file-format-support.md) pour une description de tous les formats pris en charge par AEM Assets, ainsi que des fonctionnalités prises en charge pour chaque format.

## Gestionnaires de médias par défaut {#default-media-handlers}

Les gestionnaires de médias suivants sont disponibles dans AEM Assets et gèrent les types MIME les plus courants :

<!-- TBD: Apply correct formatting once table is moved to MD.
-->

<table>
 <tbody>
  <tr>
   <td>Nom du gestionnaire</td>
   <td>Nom du service (dans la console système)</td>
   <td>Types MIME pris en charge</td>
  </tr>
  <tr>
   <td>TextHandler</td>
   <td><p>com.day.cq.dam.core.impl.handler.TextHandler</p> </td>
   <td>text/plain</td>
  </tr>
  <tr>
   <td>PdfHandler</td>
   <td><p>com.day.cq.dam.handler.standard.pdf.PdfHandler</p> </td>
   <td><p>application/pdf<br /> application/illustrator</p> </td>
  </tr>
  <tr>
   <td>JpegHandler</td>
   <td><p>com.day.cq.dam.core.impl.handler.JpegHandler</p> </td>
   <td>image/jpeg</td>
  </tr>
  <tr>
   <td>Mp3Handler</td>
   <td><p>com.day.cq.dam.handler.standard.mp3.Mp3Handler</p> </td>
   <td><p>audio/mpeg</p> </td>
  </tr>
  <tr>
   <td>ZipHandler</td>
   <td><p>com.day.cq.dam.handler.standard.zip.ZipHandler</p> </td>
   <td><p>application/java-archive</p> <p>application/zip</p> </td>
  </tr>
  <tr>
   <td>PictHandler</td>
   <td><p>com.day.cq.dam.handler.standard.pict.PictHandler</p> </td>
   <td><p>image/pict</p> </td>
  </tr>
  <tr>
   <td>StandardImageHandler</td>
   <td><p>com.day.cq.dam.core.impl.handler.StandardImageHandler</p> </td>
   <td><p>image/gif</p> <p>image/png</p> <p>application/photoshop</p> <p>image/jpeg</p> <p>image/tiff</p> <p>image/x-ms-bmp</p> <p>image/bmp</p> </td>
  </tr>
  <tr>
   <td>MSOfficeHandler</td>
   <td>com.day.cq.dam.handler.standard.msoffice.MSOfficeHandler</td>
   <td>application/msword<br /> </td>
  </tr>
  <tr>
   <td>MSPowerPointHandler</td>
   <td>com.day.cq.dam.handler.standard.msoffice.MSPowerPointHandler</td>
   <td>application/vnd.ms-powerpoint<br /> </td>
  </tr>
  <tr>
   <td>OpenOfficeHandler</td>
   <td>com.day.cq.dam.handler.standard.ooxml.OpenOfficeHandler</td>
   <td>application/vnd.openxmlformats-officedocument.wordprocessingml.document<br /> application/vnd.openxmlformats-officedocument.spreadsheetml.sheet<br /> application/vnd.openxmlformats-officedocument.presentationml.presentation<br /> <br /> </td>
  </tr>
  <tr>
   <td>EPubHandler</td>
   <td>com.day.cq.dam.handler.standard.epub.EPubHandler</td>
   <td>application/epub+zip</td>
  </tr>
  <tr>
   <td>GenericAssetHandler</td>
   <td><p>com.day.cq.dam.core.impl.handler.GenericAssetHandler</p> </td>
   <td>Solution de secours au cas où aucun autre gestionnaire n’aurait été trouvé pour extraire des données d’une ressource</td>
  </tr>
 </tbody>
</table>

Tous les gestionnaires effectuent les tâches suivantes :

* extraction de toutes les métadonnées disponibles dans la ressource.
* création d’une miniature à partir de la ressource.

Il est possible d’afficher les gestionnaires de médias actifs :

1. Dans votre navigateur, accédez à la page suivante : `http://localhost:4502/system/console/components`.
1. Cliquez sur le lien `com.day.cq.dam.core.impl.store.AssetStoreImpl`.
1. Une liste comportant tous les gestionnaires de médias actifs est affichée.

## Utilisation des gestionnaires de médias dans les workflows afin d’effectuer des tâches sur les ressources {#using-media-handlers-in-workflows-to-perform-tasks-on-assets}

Les gestionnaires de médias sont des services généralement utilisés conjointement avec des processus.

AEM comporte des processus par défaut pour le traitement des ressources. Pour les afficher, ouvrez la console de workflow et cliquez sur l’onglet **[!UICONTROL Modèles]** : les titres de workflow commençant par AEM Assets concernent des ressources.

Les workflows existants peuvent être étendus et de nouveaux workflows peuvent être créés pour gérer les ressources en fonction d’exigences spécifiques.

L’exemple suivant indique comment développer le workflow de **[!UICONTROL synchronisation AEM Assets]**, de sorte que des sous-ressources soient générées pour toutes les ressources, à l’exception des documents PDF.

### Désactivation/activation d’un gestionnaire de médias {#disabling-enabling-a-media-handler}

Les gestionnaires de médias peuvent être désactivés ou activés par le biais de la console de gestion web Apache Felix. Lorsque le gestionnaire de médias est désactivé, ses tâches ne sont pas réalisées sur les ressources.

Pour activer/désactiver un gestionnaire de médias :

1. Dans votre navigateur, accédez à la page suivante : `https://<host>:<port>/system/console/components`.
1. Cliquez sur **[!UICONTROL Désactiver]** en regard du nom du gestionnaire de médias. Par exemple : `com.day.cq.dam.handler.standard.mp3.Mp3Handler`.
1. Actualisez la page : une icône s’affiche en regard du gestionnaire de médias pour indiquer qu’il est désactivé.
1. Pour activer le gestionnaire de médias, cliquez sur le bouton **[!UICONTROL Activer]** en regard de son nom.

### Création d’un gestionnaire de médias {#creating-a-new-media-handler}

Pour prendre en charge un nouveau type de médias ou exécuter des tâches spécifiques sur une ressource, il est nécessaire de créer un gestionnaire de médias. Cette section décrit la procédure à suivre.

#### Classes et interfaces importantes   {#important-classes-and-interfaces}

La meilleure façon de démarrer une implémentation est d’hériter d’une implémentation abstraite fournie qui prend en charge l’essentiel du traitement et qui fournit un comportement par défaut raisonnable : à savoir la classe `com.day.cq.dam.core.AbstractAssetHandler`.

Cette classe fournit déjà un descripteur de service abstrait. Donc, si vous héritez de cette classe et que vous utilisez le plug-in maven-sling-plugin, assurez-vous que vous avez défini l’indicateur inherit sur `true`.

Implémentez les méthodes suivantes :

* `extractMetadata()` : extraction de toutes les métadonnées disponibles.
* `getThumbnailImage()` : création d’une miniature à partir de la ressource transmise.
* `getMimeTypes()` : renvoi des types MIME de la ressource.

Voici un exemple de modèle :

`package my.own.stuff; /** * @scr.component inherit="true" * @scr.service */ public class MyMediaHandler extends com.day.cq.dam.core.AbstractAssetHandler { // implement the relevant parts } `

L’interface et les classes sont les suivantes :

* `com.day.cq.dam.api.handler.AssetHandler` interface : Cette interface décrit le service qui ajoute la prise en charge de types MIME spécifiques. L’ajout d’un nouveau type MIME nécessite l’implémentation de cette interface. L’interface contient des méthodes pour importer et exporter les documents spécifiques, pour créer des miniatures et extraire des métadonnées.
* `com.day.cq.dam.core.AbstractAssetHandler` : cette classe sert de base pour toutes les autres implémentations de gestionnaires de ressources et fournit des fonctionnalités communes.
* Classe `com.day.cq.dam.core.AbstractSubAssetHandler` :
   * Cette classe sert de base pour toutes les autres implémentations de gestionnaires de ressources et fournit des fonctionnalités communes, ainsi que la fonctionnalité commune d’extraction de sous-ressources.
   * La meilleure façon de démarrer une implémentation est d’hériter d’une implémentation abstraite fournie qui prend en charge l’essentiel du traitement et qui fournit un comportement par défaut raisonnable : à savoir la classe com.day.cq.dam.core.AbstractAssetHandler.
   * Cette classe fournit déjà un descripteur de service abstrait. Donc, si vous héritez de cette classe et que vous utilisez le plug-in maven-sling-plugin, assurez-vous que vous avez défini l’indicateur inherit sur true.

Les méthodes suivantes doivent être implémentées :

* `extractMetadata()` : cette méthode extrait toutes les métadonnées disponibles.
* `getThumbnailImage()` : cette méthode crée une miniature de la ressource transmise.
* `getMimeTypes()`: cette méthode renvoie le ou les types MIME de ressource.

Voici un exemple de modèle :

package my.own.stuff; /&amp;ast;&amp;ast; &amp;ast; @scr.component inherit=&quot;true&quot; &amp;ast; @scr.service &amp;ast;/ public class MyMediaHandler extends com.day.cq.dam.core.AbstractAssetHandler { // implement the relevant parts }

L’interface et les classes sont les suivantes :

* `com.day.cq.dam.api.handler.AssetHandler` interface : Cette interface décrit le service qui ajoute la prise en charge de types MIME spécifiques. L’ajout d’un nouveau type MIME nécessite l’implémentation de cette interface. L’interface contient des méthodes pour importer et exporter les documents spécifiques, pour créer des miniatures et extraire des métadonnées.
* `com.day.cq.dam.core.AbstractAssetHandler` : cette classe sert de base pour toutes les autres implémentations de gestionnaires de ressources et fournit des fonctionnalités communes.
* `com.day.cq.dam.core.AbstractSubAssetHandler` : cette classe sert de base pour toutes les autres implémentations de gestionnaires de ressources et fournit des fonctionnalités communes, ainsi que la fonctionnalité commune d’extraction de sous-ressources.

<!--
#### Example: create a specific Text Handler {#example-create-a-specific-text-handler}

In this section, you will create a specific Text Handler that generates thumbnails with a watermark.

Proceed as follows:

Refer to [Development Tools](../sites-developing/dev-tools.md) to install and set up Eclipse with a Maven plugin and for setting up the dependencies that are needed for the Maven project.

After you perform the following procedure, when you upload a txt file into AEM, the file's metadata are extracted and two thumbnails with a watermark are generated.

1. In Eclipse, create `myBundle` Maven project:

    1. In the Menu bar, click **[!UICONTROL File > New > Other]**.
    1. In the dialog, expand the Maven folder, select Maven Project and click **[!UICONTROL Next]**.
    1. Check the Create a simple project box and the Use default Workspace locations box, then click **[!UICONTROL Next]**.
    1. Define the Maven project:

        * Group Id: com.day.cq5.myhandler
        * Artifact Id: myBundle
        * Name: My AEM bundle
        * Description: This is my AEM bundle

    1. Click **[!UICONTROL Finish]**.

1. Set the Java Compiler to version 1.5:

    1. Right-click the `myBundle` project, select Properties.
    1. Select Java Compiler and set following properties to 1.5:

        * Compiler compliance level
        * Generated .class files compatibility
        * Source compatibility

    1. Click **[!UICONTROL OK]**. In the dialog window, click Yes.

1. Replace the code in the pom.xml file with the following code:

1. Create the package `com.day.cq5.myhandler` that contains the Java classes under `myBundle/src/main/java`:

    1. Under myBundle, right-click `src/main/java`, select New, then Package.
    1. Name it `com.day.cq5.myhandler` and click Finish.

1. Create the Java class `MyHandler`:

    1. In Eclipse, under `myBundle/src/main/java`, right-click the `com.day.cq5.myhandler` package, select New, then Class.
    1. In the dialog window, name the Java Class MyHandler and click Finish. Eclipse creates and opens the file MyHandler.java.
    1. In `MyHandler.java` replace the existing code with the following and then save the changes:

   ```java
   package com.day.cq5.myhandler;
   import java.awt.Color;
   import java.awt.Rectangle;
   import java.awt.image.BufferedImage;
   import java.io.IOException;
   import java.io.InputStream;
   import java.io.InputStreamReader;
   import javax.jcr.Node;
   import javax.jcr.RepositoryException;
   import javax.jcr.Session;
   import org.apache.commons.io.IOUtils;
   import org.slf4j.Logger;
   import org.slf4j.LoggerFactory;
   import com.day.cq.dam.api.metadata.ExtractedMetadata;
   import com.day.cq.dam.core.AbstractAssetHandler;
   import com.day.image.Font;
   import com.day.image.Layer;
   import com.day.cq.wcm.foundation.ImageHelper;

   /**
    * The <code>MyHandler</code> can extract text files
    * @scr.component inherit="true" immediate="true" metatype="false"
    * @scr.service
    *
    **/

   public class MyHandler extends AbstractAssetHandler {
    /** * Logger instance for this class. */
    private static final Logger log = LoggerFactory.getLogger(MyHandler.class);
    /** * Music icon margin */
    private static final int MARGIN = 10;
    /** * @see com.day.cq.dam.api.handler.AssetHandler#getMimeTypes() */
    public String[] getMimeTypes() {
     return new String[] {"text/plain"};
    }

    public ExtractedMetadata extractMetadata(Node asset) {
     ExtractedMetadata extractedMetadata = new ExtractedMetadata();
     InputStream data = getInputStream(asset);
     try {
      // read text data
      InputStreamReader reader = new InputStreamReader(data);
      char[] buffer = new char[4096];
      String text = "";
      while (reader.read(buffer) != -1) {
       text += new String(buffer);
      }
      reader.close();
      long wordCount = this.wordCount(text);
      extractedMetadata.setProperty("text", text);
      extractedMetadata.setMetaDataProperty("Word Count",wordCount);
      setMimetype(extractedMetadata, asset);
     } catch (Throwable t) {
      log.error("handling error: " + t.toString(), t);
     } finally {
      IOUtils.closeQuietly(data);
     }
     return extractedMetadata; }
    // ----------------------< helpers >----------------------------------------
    protected BufferedImage getThumbnailImage(Node node) {
     ExtractedMetadata metadata = extractMetadata(node);
     final String text = (String) metadata.getProperty("text");
     // create text layer
     final Layer layer = new Layer(500, 600, Color.WHITE);
     layer.setPaint(Color.black);
     Font font = new Font("Arial", 12);
     String displayText = this.getDisplayText(text, 600, 12);
     if(displayText!=null && displayText.length() > 0) {
      // commons-gfx Font class would throw IllegalArgumentException on empty or null text
      layer.drawText(10, 10, 500, 600, displayText, font, Font.ALIGN_LEFT, 0, 0);
     }
     // create watermark and merge with text layer
     Layer watermarkLayer;
     try {
      final Session session = node.getSession();
      watermarkLayer = ImageHelper.createLayer(session, "/content/dam/geometrixx/icons/certificate.png");
      watermarkLayer.setX(MARGIN);
      watermarkLayer.setY(MARGIN);
      layer.merge(watermarkLayer);
     } catch (RepositoryException e) {
      // TODO Auto-generated catch block
      e.printStackTrace();
     } catch (IOException e) {
      // TODO Auto-generated catch block
      e.printStackTrace(); }
     layer.crop(new Rectangle(510, 600));
     return layer.getImage(); }
    // ---------------< private >-----------------------------------------------
    /**
     * This method cuts lines if the text file is too long..
     * * @param text
     * * text to check
     * * @param height
     * * text box height (px)
     * * @param fontheight
     * * font height (px)
     * * @return the text which will fit into the box
     */
    private String getDisplayText(String text, int height, int fontheight) {
     String trimmedText = text.trim();
     int numOfLines = height / fontheight;
     String lines[] = trimmedText.split("\n");
     if (lines.length <= numOfLines) {
      return trimmedText;
     } else {
      String cuttetText = "";
      for (int i = 0; i < numOfLines; i++) {
       cuttetText += lines[i] + "\n";
      }
      return cuttetText;
     }
    }
    /**
     * * This method counts the number of words in a string
     * * @param text the String whose words would like to be counted
     * * @return the number of words in the string
     * */
    private long wordCount(String text) {
     // We need to keep track of the last character, if we have two white spaces in a row we dont want to double count
     // The starting of the document is always a whitespace
     boolean prevWhiteSpace = true;
     boolean currentWhiteSpace = true;
     char c; long numwords = 0;
     int j = text.length();
     int i = 0;
     while (i < j) {
      c = text.charAt(i++);
      if (c == 0) { break; }
      currentWhiteSpace = Character.isWhitespace(c);
      if (currentWhiteSpace && !prevWhiteSpace) { numwords++; }
      prevWhiteSpace = currentWhiteSpace;
     }
     // If we do not end with a white space then we need to add one extra word
     if (!currentWhiteSpace) { numwords++; }
     return numwords;
    }
   }
   ```

1. Compile the Java class and create the bundle:

    1. Right-click the myBundle project, select **[!UICONTROL Run As]**, then **[!UICONTROL Maven Install]**.
    1. The bundle `myBundle-0.0.1-SNAPSHOT.jar` (containing the compiled class) is created under `myBundle/target`.

1. In CRX Explorer, create a new node under `/apps/myApp`. Name = `install`, Type = `nt:folder`.
1. Copy the bundle `myBundle-0.0.1-SNAPSHOT.jar` and store it under `/apps/myApp/install` (for example with WebDAV). The new text handler is now active in AEM.
1. In your browser, open the Apache Felix Web Management Console. Select the Components tab and disable the default text handler `com.day.cq.dam.core.impl.handler.TextHandler`.

-->

## Gestionnaire de médias en ligne de commande {#command-line-based-media-handler}

AEM vous permet d’exécuter n’importe quel outil de ligne de commande dans un workflow pour convertir des ressources (comme ImageMagick) et ajouter le nouveau rendu à la ressource. Vous avez uniquement besoin d’installer l’outil de ligne de commande sur le disque hébergeant le serveur AEM, puis d’ajouter une étape au workflow et de la configurer. Le processus appelé, `CommandLineProcess`, permet également d’effectuer un filtrage en fonction de types MIME spécifiques et de créer plusieurs miniatures sur la base du nouveau rendu.

Les conversions suivantes peuvent être automatiquement exécutées et stockées dans AEM Assets :

* Transformation EPS et AI à l’aide d’[ImageMagick](https://www.imagemagick.org/script/index.php) et de [Ghostscript](https://www.ghostscript.com/)
* Transcodage vidéo FLV à l’aide de [FFmpeg](https://ffmpeg.org/)
* Encodage MP3 à l’aide de [LAME](http://lame.sourceforge.net/)
* Traitement audio à l’aide de [SOX](http://sox.sourceforge.net/)

>[!NOTE]
>
>Sur les systèmes autres que Windows, l’outil FFMpeg renvoie une erreur lors de la génération de rendus pour une ressource vidéo dont le nom de fichier contient une apostrophe (’). Si le nom de votre fichier vidéo comprend une apostrophe, supprimez-la avant de charger le fichier dans AEM.

Le processus `CommandLineProcess` effectue les opérations suivantes par ordre d’apparition dans la liste :

* le fichier selon des types MIME spécifiques, le cas échéant.
* Crée un répertoire temporaire sur le disque hébergeant le serveur AEM.
* Diffuse le fichier d’origine vers le répertoire temporaire.
* Exécute la commande définie par les arguments de l’étape. La commande est exécutée dans le répertoire temporaire avec les autorisations de l’utilisateur exécutant AEM.
* Renvoie le résultat dans le dossier de rendu du serveur AEM.
* Supprime le répertoire temporaire.
* Crée des miniatures basées sur ces rendus, si spécifié. Le nombre et les dimensions des miniatures sont définis par les arguments de l’étape.

### Exemple utilisant ImageMagick   {#an-example-using-imagemagick}

L’exemple suivant montre comment configurer l’étape de processus de ligne de commande de sorte qu’à chaque fois qu’une ressource de type MIME gif ou tiff est ajoutée à /content/dam sur le serveur AEM, une image inversée de l’original est créée avec trois miniatures supplémentaires (140x100, 48x48 et 10x250).

Pour ce faire, vous utiliserez ImageMagick. ImageMagick est une suite logicielle gratuite permettant de créer, modifier et composer des images bitmap, généralement à partir de la ligne de commande.

Installez d’abord ImageMagick sur le disque hébergeant le serveur AEM :

1. Installez ImageMagick : reportez-vous à la [documentation d’ImageMagick](https://www.imagemagick.org/script/download.php).
1. Configurez l’outil afin de pouvoir exécuter convert sur la ligne de commande.
1. Pour vérifier si cet outil est installé correctement, exécutez la commande `convert -h` sur la ligne de commande.

   L’écran d’aide qui s’affiche alors répertorie toutes les options possibles de l’outil convert.

   >[!NOTE]
   >
   >Dans certaines versions de Windows (Windows SE, par exemple), il se peut que la commande convert ne s’exécute pas, car elle est en conflit avec l’utilitaire de conversion natif de Windows. Dans ce cas, indiquez le chemin complet de l’utilitaire ImageMagick utilisé pour convertir les fichiers image en miniatures. Par exemple, `"C:\Program Files\ImageMagick-6.8.9-Q16\convert.exe" -define jpeg:size=319x319 ${filename} -thumbnail 319x319 cq5dam.thumbnail.319.319.png`.

1. Pour vérifier si l’outil fonctionne correctement, ajoutez une image .jpg dans le répertoire de travail et exécutez la commande de conversion `<image-name>.jpg -flip <image-name>-flipped.jpg` sur la ligne de commande.

   Une image inversée est ajoutée au répertoire.

Ajoutez ensuite l’étape de processus de ligne de commande au workflow **[!UICONTROL Ressources de mise à jour de gestion des actifs numériques]** :

1. Accédez à la console **[!UICONTROL Workflow]**.
1. Dans l’onglet **[!UICONTROL Modèles]**, modifiez le modèle **[!UICONTROL Ressources de mise à jour de gestion des actifs numériques]**.
1. Modifiez les paramètres de l’étape **[!UICONTROL Rendu Web]** comme suit :

   **Arguments** :

   `mime:image/gif,mime:image/tiff,tn:140:100,tn:48:48,tn:10:250,cmd:convert ${directory}/${filename} -flip ${directory}/${basename}.flipped.jpg`

1. Enregistrez le workflow.

Pour tester le workflow modifié, ajoutez une ressource à `/content/dam`.

1. Dans le système de fichiers, sélectionnez une image.tiff. Renommez-la `myImage.tiff` et copiez-la dans `/content/dam` en utilisant, par exemple, WebDAV.
1. Accédez à la console **[!UICONTROL CQ5 DAM]**, par exemple `http://localhost:4502/libs/wcm/core/content/damadmin.html`.
1. Ouvrez la ressource **[!UICONTROL myImage.tiff]** et vérifiez que l’image inversée et les trois miniatures ont bien été créées.

#### Configuration de l’étape du processus CommandLineProcess {#configuring-the-commandlineprocess-process-step}

Cette section décrit la procédure à suivre pour définir les **Arguments du processus** de **CommandLineProcess**.

Les valeurs des **Arguments du processus** doivent être séparées par une virgule et ne doivent pas commencer par un espace.

<table>
 <tbody>
  <tr>
   <td> Argument-Format</td>
   <td>Description</td>
  </tr>
  <tr>
   <td> mime:&lt;mime-type&gt;</td>
   <td><p>Argument facultatif. Le processus est appliqué si le fichier a le même type MIME que celui de l’argument.</p> <p>Plusieurs types MIME peuvent être définis.</p> </td>
  </tr>
  <tr>
   <td> tn:&lt;width&gt;:&lt;height&gt;</td>
   <td><p>Argument facultatif. Le processus crée une miniature avec les dimensions définies dans l’argument.</p> <p>Plusieurs miniatures peuvent être définies.<br /> </p> </td>
  </tr>
  <tr>
   <td> cmd: &lt;command&gt;</td>
   <td><p>Définit la commande qui sera exécutée. La syntaxe dépend de l’outil de ligne de commande.</p> <p>Une seule commande peut être définie.</p> <p>Les variables suivantes permettent de créer la commande :<br/></p> <p><code>${filename}</code>: name of the input file, for example `original.jpg`<br/><code>${file}</code>: full path name of the input file, for example, `/tmp/cqdam0816.tmp/original.jpg`<br/><code>${directory}</code>: directory of the input file, for example `/tmp/cqdam0816.tmp`.<br/> <code>${basename}</code>: nom du fichier d’entrée sans son extension, par exemple original<br/><code>${extension}</code>: extension du fichier d’entrée, par exemple JPG<br/></p></td>
  </tr>
 </tbody>
</table>

Par exemple, si ImageMagick est installé sur le disque hébergeant le serveur AEM et que vous créez une étape de processus en utilisant **CommandLineProcess** en tant qu’implémentation et les valeurs suivantes en tant qu’**arguments de processus** :

`mime:image/gif,mime:image/tiff,tn:140:100,tn:48:48,tn:10:250,cmd:convert ${directory}/${filename} -flip ${directory}/${basename}.flipped.jpg`

alors, lors de l’exécution du workflow, l’étape s’applique uniquement aux ressources dont les types MIME sont image/gif ou mime:image/tiff, elle crée une image inversée de l’original, la convertit en .jpg et génère trois miniatures aux dimensions suivantes : 140x100, 48x48 et 10x250.

Utilisez les **Arguments de processus** suivants pour créer les trois miniatures standards à l’aide d’ImageMagick :

`mime:image/tiff,mime:image/png,mime:image/bmp,mime:image/gif,mime:image/jpeg,cmd:convert ${filename} -define jpeg:size=319x319 -thumbnail "319x319>" -background transparent -gravity center -extent 319x319 -write png:cq5dam.thumbnail.319.319.png -thumbnail "140x100>" -background transparent -gravity center -extent 140x100 -write cq5dam.thumbnail.140.100.png -thumbnail "48x48>" -background transparent -gravity center -extent 48x48 cq5dam.thumbnail.48.48.png`

Utilisez les **Arguments de processus** suivants pour créer le rendu web à l’aide d’ImageMagick :

`mime:image/tiff,mime:image/png,mime:image/bmp,mime:image/gif,mime:image/jpeg,cmd:convert ${filename} -define jpeg:size=1280x1280 -thumbnail "1280x1280>" cq5dam.web.1280.1280.jpeg`

>[!NOTE]
>
>L’étape **CommandLineProcess** s’applique uniquement aux ressources (nœuds du type `dam:Asset`) ou aux descendants d’une ressource.
