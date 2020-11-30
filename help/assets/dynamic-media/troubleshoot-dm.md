---
title: Résolution des problèmes liés à Dynamic Media
description: Résolution des problèmes liés à Dynamic Media.
translation-type: tm+mt
source-git-commit: a0b4f04aaafbaef86728c8bd23cc026f43c72dde
workflow-type: tm+mt
source-wordcount: '995'
ht-degree: 100%

---


# Résolution des problèmes liés à Dynamic Media {#troubleshooting-dynamic-media-scene-mode}

La rubrique suivante décrit la résolution des problèmes liés à Dynamic Media.

## Nouvelle configuration Dynamic Media {#new-dm-config}

Voir [Résolution des problèmes liés à une nouvelle configuration Dynamic Media.](/help/assets/dynamic-media/config-dm.md#troubleshoot-dm-config)

## Général (toutes les ressources) {#general-all-assets}

Vous trouverez ci-après quelques astuces et conseils généraux concernant toutes les ressources.

### Propriétés de l’état de synchronisation des ressources  {#asset-synchronization-status-properties}

Vous pouvez passer en revue les propriétés de ressource suivantes dans CRXDE Lite pour vérifier que la synchronisation de la ressource depuis AEM vers Dynamic Media s’est déroulée correctement :

| **Propriété** | **Exemple** | **Description** |
|---|---|---|
| `<object_node>/jcr:content/metadata/dam:scene7ID` | **`a|364266`** | Indicateur général indiquant que le nœud est lié à Dynamic Media. |
| `<object_node>/jcr:content/metadata/dam:scene7FileStatus` | **PublishComplete** ou texte d’erreur | Statut du téléchargement de la ressource vers Dynamic Media. |
| `<object_node>/jcr:content/metadata/dam:scene7File` | **myCompany/myAssetID** | Doit être renseigné pour générer des URL vers la ressource distante de Dynamic Media. |
| `<object_node>/jcr:content/dam:lastSyncStatus` | **succès** ou **échec :`<error text>`** | Statut de synchronisation des visionneuses (visionneuses à 360°, visionneuses d’images, etc.), des paramètres prédéfinis d’image, des paramètres prédéfinis de visionneuse, des mises à jour de zone cliquable pour une ressource ou des images ayant été modifiées. |

### Journalisation de la synchronisation {#synchronization-logging}

Les erreurs et problèmes de synchronisation sont consignés dans le fichier `error.log` (répertoire de serveur AEM `/crx-quickstart/logs/`). La journalisation est suffisante pour déterminer la cause de la plupart des problèmes. Vous pouvez toutefois augmenter le niveau de journalisation sur DEBUG sur le module `com.adobe.cq.dam.ips` via la console Sling ([https://localhost:4502/system/console/slinglog](https://localhost:4502/system/console/slinglog)) pour collecter davantage d’informations.

### Gestion de version {#version-control}

Lors du remplacement d’une ressource Dynamic Media (nom et emplacement identiques), vous avez la possibilité de conserver les deux ressources ou de remplacer/créer une version :

* Si vous conservez les deux, une nouvelle ressource est créée avec un nom unique pour l’URL de ressource publiée. Par exemple, `image.jpg` est la ressource d’origine et `image1.jpg` est la ressource qui vient d’être chargée.

* La création d’une version n’est pas prise en charge dans Dynamic Media. La nouvelle version remplace la ressource existante lors de la diffusion.

## Images et visionneuses  {#images-and-sets}

Si des problèmes surviennent avec les images et les visionneuses, reportez-vous aux conseils de dépannage ci-dessous.

<table>
 <tbody>
  <tr>
   <td><strong>Problème</strong></td>
   <td><strong>Débogage</strong></td>
   <td><strong>Solution</strong></td>
  </tr>
  <tr>
   <td>Impossible d’accéder au bouton Copier le code intégré/l’URL dans la vue détaillée de la ressource</td>
   <td>
    <ol>
     <li><p>Accédez à CRX/DE :</p>
      <ul>
       <li>Vérifiez si le paramètre prédéfini dans le JCR <code>/etc/dam/presets/viewer/&lt;preset&gt; has lastReplicationAction</code> est défini. Remarque : cet emplacement s’applique si vous avez effectué la mise à niveau d’AEM 6.x vers la version 6.4 et si vous avez choisi de ne pas utiliser la migration. Dans le cas contraire, l’emplacement est <code>/conf/global/settings/dam/dm/presets/viewer</code>.</li>
       <li>Vérifiez que la ressource dans le JCR présente <code>dam:scene7FileStatus</code><strong> </strong>sous Métadonnées défini sur <code>PublishComplete</code>.</li>
      </ul> </li>
    </ol> </td>
   <td><p>Actualisez la page/accédez à une autre page et revenez sur la page (le code JSP de rail latéral doit être recompilé)</p> <p>Si cela ne fonctionne pas :</p>
    <ul>
     <li>Publiez la ressource.</li>
     <li>Rechargez la ressource et publiez-la.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>La zone réactive de carrousel se déplace après un basculement entre des diapositives.</td>
   <td><p>Vérifiez que toutes les diapositives ont la même taille.</p> </td>
   <td><p>Utilisez uniquement des images de taille identique pour le carrousel.</p> </td>
  </tr>
  <tr>
   <td>L’aperçu de l’image ne s’affiche pas avec la visionneuse Dynamic Media.</td>
   <td><p>Vérifiez que la ressource contient <code>dam:scene7File</code> dans les propriétés de métadonnées (CRXDE Lite).</p> </td>
   <td><p>Vérifiez que le traitement de toutes les ressources est terminé.</p> </td>
  </tr>
  <tr>
   <td>La ressource téléchargée n’apparaît pas dans le sélecteur de ressources.</td>
   <td><p>Vérifiez que la ressource présente la propriété <code>jcr:content</code> &gt; <strong><code>dam:assetState</code></strong> = <code>processed</code> (CRXDE Lite)</p> </td>
   <td><p>Vérifiez que le traitement de toutes les ressources est terminé.</p> </td>
  </tr>
  <tr>
   <td>La bannière en mode Carte affiche <strong>Nouveau</strong> lorsque la ressource n’a pas commencé le traitement.</td>
   <td>Vérifiez que la ressource <code>jcr:content</code> &gt; <code>dam:assetState</code> = if <code>unprocessed</code> n’a pas été sélectionnée par le workflow.</td>
   <td>Attendez que la ressource soit sélectionnée par le workflow.</td>
  </tr>
  <tr>
   <td>Les images ou les visionneuses n’affichent pas l’URL ou le code intégré de la visionneuse.</td>
   <td>Vérifiez que le paramètre prédéfini de visionneuse a été publié.</td>
   <td><p>Accédez à <strong>Outils</strong> &gt; <strong>Ressources</strong> &gt; <strong>Paramètres prédéfinis de la visionneuse</strong> et publiez le paramètre prédéfini de la visionneuse.</p> </td>
  </tr>
 </tbody>
</table>

## Vidéo {#video}

Si vous êtes confronté à des problèmes au niveau de la vidéo, reportez-vous aux conseils de dépannage ci-dessous.

<table>
 <tbody>
  <tr>
   <td><strong>Problème</strong></td>
   <td><strong>Débogage</strong></td>
   <td><strong>Solution</strong></td>
  </tr>
  <tr>
   <td>L’aperçu de la vidéo ne peut pas être affiché.</td>
   <td>
    <ul>
     <li>Vérifiez que le dossier est associé à un profil vidéo (dans le cas d’un format de fichier non pris en charge). En l’absence de prise en charge, seule une image est affichée.</li>
     <li>Le profil vidéo doit contenir plusieurs paramètres prédéfinis de codage pour générer un ensemble AVS (les codages uniques sont considérés comme du contenu vidéo pour les fichiers MP4 ; dans le cas des fichiers non pris en charge, ils sont considérés comme étant non traités).</li>
     <li>Vérifiez que le traitement de la vidéo est terminé en confirmant <code>dam:scene7FileAvs</code> de <code>dam:scene7File</code> dans les métadonnées.</li>
    </ul> </td>
   <td>
    <ol>
     <li>Attribuez un profil vidéo au dossier.</li>
     <li>Modifiez le profil vidéo de sorte qu’il inclue plusieurs paramètres de codage prédéfinis.</li>
     <li>Attendez que le traitement de la vidéo soit terminé.</li>
     <li>Rechargez la vidéo et assurez-vous que le workflow Vidéo de codage de média dynamique n’est pas en cours d’exécution.<br/> </li>
     <li>Rechargez la vidéo.</li>
    </ol> </td>
  </tr>
  <tr>
   <td>La vidéo n’est pas codée.</td>
   <td>
    <ul>
     <li>Vérifiez que le service cloud Dynamic Media est configuré.</li>
     <li>Vérifiez qu’un profil vidéo est associé au dossier de transfert.</li>
    </ul> </td>
   <td>
    <ol>
     <li>Vérifiez que la configuration de Dynamic Media sous Cloud Services est correctement effectuée.</li>
     <li>Vérifiez que le dossier contient un profil vidéo. Vérifiez également le profil vidéo.</li>
    </ol> </td>
  </tr>
  <tr>
   <td>Le traitement vidéo prend trop de temps.</td>
   <td><p>Pour déterminer si le codage vidéo est toujours en cours ou s’il est passé à l’état d’échec :</p>
    <ul>
     <li>Vérifiez l’état de la vidéo <code>https://localhost:4502/crx/de/index.jsp#/content/dam/folder/videomp4/jcr%3Acontent</code> &gt; <code>dam:assetState</code></li>
    </ul> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Absence de rendu vidéo</td>
   <td><p>Lorsque la vidéo est téléchargée, mais qu’il n’y a aucun rendu codé :</p>
    <ul>
     <li>Vérifiez qu’un profil vidéo est attribué au dossier.</li>
     <li>Vérifiez que le traitement de la vidéo est terminé en confirmant <code>dam:scene7FileAvs</code> dans les métadonnées.</li>
    </ul> </td>
   <td>
    <ol>
     <li>Attribuez un profil vidéo au dossier.</li>
     <li>Attendez que le traitement de la vidéo soit terminé.<br /> </li>
    </ol> </td>
  </tr>
 </tbody>
</table>

## Visionneuses {#viewers}

Si vous rencontrez des problèmes avec les visionneuses, reportez-vous aux conseils de dépannage ci-dessous.

<table>
 <tbody>
  <tr>
   <td><strong>Problème</strong></td>
   <td><strong>Débogage</strong></td>
   <td><strong>Solution</strong></td>
  </tr>
  <tr>
   <td>Les paramètres prédéfinis de la visionneuse ne sont pas publiés.</td>
   <td><p>Accédez à la page de diagnostic du gestionnaire d’échantillons : <code>https://localhost:4502/libs/dam/gui/content/s7dam/samplemanager/samplemanager.html</code></p> <p>Observez les valeurs calculées. Dans le cadre d’un fonctionnement correct, vous devriez voir :</p> <p><code>_DMSAMPLE status: 0 unsyced assets - activation not necessary
       _OOTB status: 0 unsyced assets - 0 unactivated assets</code></p> <p><strong>Remarque</strong> : Environ 10 minutes peuvent être nécessaires après la configuration des paramètres cloud de Dynamic Media pour que les ressources de visionneuse se synchronisent.</p> <p>S’il reste des ressources non activées, cliquez sur l’un des boutons <strong>Répertorier toutes les ressources non activées</strong> pour afficher des informations détaillées.</p> </td>
   <td>
    <ol>
     <li>Accédez à la liste des paramètres prédéfinis de la visionneuse dans les outils d’administration : <code>https://localhost:4502/libs/dam/gui/content/s7dam/samplemanager/samplemanager.html</code></li>
     <li>Sélectionnez tous les paramètres prédéfinis de visionneuse, puis cliquez sur <strong>Publier</strong>.</li>
     <li>Revenez au gestionnaire d’échantillons et notez que le nombre de ressources non activées est maintenant égal à zéro.</li>
    </ol> </td>
  </tr>
  <tr>
   <td>Le paramètre prédéfini de visionneuse retourne 404 à partir de l’aperçu des détails de ressource ou de la copie d’URL/de code intégré.</td>
   <td><p>Dans CRXDE Lite, procédez comme suit :</p>
    <ol>
     <li>Accédez au dossier <code>&lt;sync-folder&gt;/_CSS/_OOTB</code> dans votre dossier de synchronisation Dynamic Media (par exemple, <code>/content/dam/_CSS/_OOTB</code>),</li>
     <li>Recherchez le nœud de métadonnées de la ressource qui pose problème (par exemple, <code>&lt;sync-folder&gt;/_CSS/_OOTB/CarouselDotsLeftButton_dark_sprite.png/jcr:content/metadata/</code>).</li>
     <li>Vérifiez que les propriétés <code>dam:scene7*</code> sont présentes. Si la ressource a été correctement synchronisée et publiée, <code>dam:scene7FileStatus</code> est défini sur <strong>PublishComplete</strong>.</li>
     <li>Essayez de demander l’illustration directement à partir de Dynamic Media en concaténant les valeurs des propriétés suivantes et des littéraux de chaîne.
      <ul>
       <li><code>dam:scene7Domain</code></li>
       <li><code>"is/content"</code></li>
       <li><code>dam:scene7Folder</code></li>
       <li><code>&lt;asset-name&gt;</code></li>
       <li>Exemple : <code>https://&lt;server&gt;/is/content/myfolder/_CSS/_OOTB/CarouselDotsLeftButton_dark_sprite.png</code></li>
      </ul> </li>
    </ol> </td>
   <td><p>Si les exemples de ressources ou l’illustration du paramètre prédéfini de la visionneuse n’ont pas été synchronisés ou publiés, redémarrez le processus de copie/synchronisation entier :</p>
    <ol>
     <li>Accédez à <code>/libs/dam/gui/content/s7dam/samplemanager/samplemanager.html</code>.
     </li>
     <li>Sélectionnez les actions suivantes dans l’ordre :
      <ol>
       <li>Supprimer les dossiers de synchronisation.</li>
       <li>Supprimer le dossier Paramètre prédéfini (sous <code>/conf</code>).
       <li>Déclencher la tâche asynchrone de configuration de DM.</li>
      </ol> </li>
     <li>Attendez la notification d’une synchronisation réussie dans votre boîte de réception AEM.
     </li>
    </ol> </td>
  </tr>
 </tbody>
</table>

