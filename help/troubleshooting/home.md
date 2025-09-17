---
title: Dépannage dans AEM Assets et Forms
description: Résolvez les problèmes courants d’AEM Assets et de Forms à l’aide des liens d’article pour des domaines clés tels que les chargements, les métadonnées, la recherche, la diffusion, la création de formulaires, l’envoi et l’intégration.
hidefromtoc: true
hide: true
source-git-commit: 5074e777c68c51955b9ad8f055e04067163b9596
workflow-type: tm+mt
source-wordcount: '798'
ht-degree: 2%

---


# Résolution des problèmes liés à AEM Assets et Forms {#troubleshoot-aem-assets-forms}

AEM as a Cloud Service offre des solutions complètes de gestion des ressources numériques grâce à AEM Assets et de puissantes fonctionnalités de création de formulaires grâce à AEM Forms. Les deux services fournissent des solutions PaaS natives au cloud avec des fonctionnalités intelligentes de nouvelle génération, telles que l&#39;IA/ML, le tout dans un système toujours à jour, toujours disponible et sans cesse en apprentissage.

Cependant, les environnements d’entreprise complexes peuvent rencontrer divers défis techniques dans différents domaines.

Ce guide de dépannage complet fournit des approches de diagnostic systématiques, des solutions catégorisées et des chemins de résolution détaillés pour AEM Assets et Forms. Chaque section comprend des guides de référence rapide, des méthodologies de dépannage détaillées et des liens vers des ressources étendues pour vous aider à résoudre efficacement les problèmes et à optimiser votre environnement AEM Cloud Service.

## Dépannage d’AEM Assets {#aem-assets-troubleshooting}

AEM Assets rationalise la gestion, l’organisation et la diffusion des ressources numériques dans les différentes expériences. Cependant, des problèmes peuvent survenir et affecter le chargement, les métadonnées, les intégrations ou la diffusion des ressources. Cet article fournit des étapes de dépannage pour vous aider à diagnostiquer et à résoudre les problèmes courants d’AEM Assets. En suivant les instructions fournies ici, vous pouvez restaurer les workflows efficacement et vous assurer que les ressources restent accessibles, précises et prêtes à être utilisées sur l’ensemble des canaux.

### Traitement et rendus des ressources {#asset-processing-renditions-issues}

<table>
  <tbody>
  <tr>
    <td><strong>Chargement et traitement</strong></td>
    <td><strong>Rendus</strong></td>
    <td><strong>PDF et extraction de texte</strong></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/fr/docs/experience-cloud-kcs/kbarticles/ka-26610">Échec du traitement des ressources pour les fichiers MP4 volumineux dans AEM as a Cloud Service</a></td>
    <td><a href="https://experienceleague.adobe.com/fr/docs/experience-cloud-kcs/kbarticles/ka-26639">Rendus DAM ne correspondant pas aux fichiers d’origine</a></td>
    <td><a href="https://experienceleague.adobe.com/fr/docs/experience-cloud-kcs/kbarticles/ka-26785">AEM tronque le texte extrait des PDF volumineux après 100 000 jetons</a></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/fr/docs/experience-cloud-kcs/kbarticles/ka-23916">Le fichier TIFF avec les chargements par compression ZIP ne génère aucun rendu</a></td>
    <td><a href="https://experienceleague.adobe.com/fr/docs/experience-cloud-kcs/kbarticles/ka-26233">Images n’affichant pas les rendus de miniature dans AEM as a Cloud Service</a></td>
    <td><a href="https://experienceleague.adobe.com/fr/docs/experience-cloud-kcs/kbarticles/ka-25518">Limites de l’extraction de texte pour les PDF volumineux dans AEM as a Cloud Service</a></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/fr/docs/experience-cloud-kcs/kbarticles/ka-21865">Échec du glisser-déposer d’un dossier de ressources vers l’interface utilisateur web d’AEM Assets</a></td>
    <td></td>
    <td><a href="https://experienceleague.adobe.com/fr/docs/experience-cloud-kcs/kbarticles/ka-26528">Le problème de rotation des ressources rend les rotations suivantes invisibles.</a></td>
  </tr>
  <tr>
  <td><a href="https://experienceleague.adobe.com/fr/docs/experience-cloud-kcs/kbarticles/ka-26450">Augmentation de la limite de chargement de ressources en une seule partie pour l’intégration de l’API Photoshop Firefly</a></td>
  <td></td>
  <td></td>
  </tr>
  </tbody>
</table>

### Dynamic Media {#dynamic-media-issues}

<table>
  <tbody>
  <tr>
    <td><strong>Vidéo</strong></td>
    <td><strong>Visionneuses à 360° et recadrage intelligent</strong></td>
    <td><strong>Diffusion et paramètres</strong></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/fr/docs/experience-cloud-kcs/kbarticles/ka-26533">Correction des problèmes de chargement, de traitement et de rendu vidéo dans AEM</a></td>
    <td><a href="https://experienceleague.adobe.com/fr/docs/experience-cloud-kcs/kbarticles/ka-26715">Visionneuses à 360° bloquées en statut de traitement</a></td>
    <td><a href="https://experienceleague.adobe.com/fr/docs/experience-cloud-kcs/kbarticles/ka-17628">Modification de l’URL Dynamic Media pour les ressources</a></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/fr/docs/experience-cloud-kcs/kbarticles/ka-26677">Incohérence des miniatures vidéo entre les vues Dynamic Media et Carte DAM</a></td>
    <td><a href="https://experienceleague.adobe.com/fr/docs/experience-cloud-kcs/kbarticles/ka-26873">Rendus de recadrage intelligent non générés dans AEM as a Cloud Service</a></td>
    <td><a href="https://experienceleague.adobe.com/fr/docs/experience-cloud-kcs/kbarticles/ka-26367">Problème d’image rompue avec le recadrage intelligent dans AEM 6.5</a></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/fr/docs/experience-cloud-kcs/kbarticles/ka-26610">Échec du traitement des ressources dans AEM Dynamic Media</a></td>
    <td><a href="https://experienceleague.adobe.com/fr/docs/experience-cloud-kcs/kbarticles/ka-26637">Problème de couleur d’arrière-plan pour les rendus TIFF</a></td>
    <td><a href="https://experienceleague.adobe.com/fr/docs/experience-cloud-kcs/kbarticles/ka-25294">La page Paramètres généraux de Dynamic Media ne s’ouvre pas</a></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/fr/docs/experience-cloud-kcs/kbarticles/ka-26197">Résolution de problèmes audio dans les fichiers vidéo avec Dynamic Media</a></td>
    <td><a href="https://experienceleague.adobe.com/fr/docs/experience-cloud-kcs/kbarticles/ka-25885">Échec de la synchronisation des ressources dans Dynamic Media</a></td>
    <td><a href="https://experienceleague.adobe.com/fr/docs/experience-cloud-kcs/kbarticles/ka-26461">Résoudre les incohérences de nom des ressources dans les environnements</a></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/fr/docs/experience-cloud-kcs/kbarticles/ka-26871">Le lecteur vidéo Dynamic Media ne fonctionne pas dans les environnements inférieurs</a></td>
    <td><a href="https://experienceleague.adobe.com/fr/docs/experience-cloud-kcs/kbarticles/ka-25471">Recommandations d’utilisateur pour la synchronisation Dynamic Media</a></td>
    <td><a href="https://experienceleague.adobe.com/fr/docs/experience-cloud-kcs/kbarticles/ka-26902">Exporter des ressources et des métadonnées à partir de Dynamic Media à l’aide de l’API</a></td>
  </tr>
  </tbody>
</table>

### Métadonnées, balisage et partage {#metadata-tagging-sharing-issues}

<table>
  <tbody>
  <tr>
    <td><strong>Métadonnées</strong></td>
    <td><strong>Balises intelligentes</strong></td>
    <td><strong>Accès et partage</strong></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/fr/docs/experience-cloud-kcs/kbarticles/ka-25828">Incohérence des métadonnées d’image dans AEM Assets</a></td>
    <td><a href="https://experienceleague.adobe.com/fr/docs/experience-cloud-kcs/kbarticles/ka-25925">Balisage automatique des ressources nouvellement chargées</a></td>
    <td><a href="https://experienceleague.adobe.com/fr/docs/experience-cloud-kcs/kbarticles/ka-26928">Commentaires limités dans la vue Assets malgré l’accès en lecture</a></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/fr/docs/experience-cloud-kcs/kbarticles/ka-26655">Résolution des problèmes de visibilité des schémas de métadonnées pour les utilisateurs non-administrateurs</a></td>
    <td><a href="https://experienceleague.adobe.com/fr/docs/experience-cloud-kcs/kbarticles/ka-25889">Les balises intelligentes ne fonctionnent pas après la migration de JWT vers OAuth</a></td>
    <td><a href="https://experienceleague.adobe.com/fr/docs/experience-cloud-kcs/kbarticles/ka-25903">Résoudre les problèmes de liens partagés dans AEM Managed Services</a></td>
  </tr>

</tbody>
</table>

### Intégrations et accès {#integrations-access}

<table>
  <tbody>
    <tr>
      <td><strong>Asset Link</strong></td>
      <td><strong>Licences et personnalisations</strong></td>
    </tr>
    <tr>
      <td><a href="https://experienceleague.adobe.com/fr/docs/experience-cloud-kcs/kbarticles/ka-26922">Adobe Asset Link laisse les liens inaccessibles dans InDesign</a></td>
      <td>
        <a href="https://experienceleague.adobe.com/fr/docs/experience-cloud-kcs/kbarticles/ka-26616">Fragments de contenu non inclus dans la licence AEM Assets</a><br>
        </td>
    </tr>
    <tr>
      <td><a href="https://experienceleague.adobe.com/fr/docs/experience-cloud-kcs/kbarticles/ka-25562">Résolution des problèmes de connexion à AEM Asset Link dans InDesign</a></td>
      <td><a href="https://experienceleague.adobe.com/fr/docs/experience-cloud-kcs/kbarticles/ka-25525">Résolution des problèmes de traitement des ressources dans AEM as a Cloud Service</a></td>
    </tr>
    <tr>
      <td><a href="https://experienceleague.adobe.com/fr/docs/experience-cloud-kcs/kbarticles/ka-25506">Erreur réseau du plug-in Adobe Asset Link : serveur inatteignable</a></td>
      <td><a href="https://experienceleague.adobe.com/fr/docs/experience-cloud-kcs/kbarticles/ka-25829">Mise à jour des miniatures personnalisées pour les ressources vidéo dans AEM as a Cloud Service</a>
      </td>
    </tr>
  </tbody>
</table>




## Dépannage d’AEM Forms {#aem-forms-troubleshooting}

AEM Forms as a Cloud Service offre de puissantes fonctionnalités de création et de gestion de formulaires. Cependant, vous pouvez rencontrer des problèmes lors de l’installation, de la configuration, de la création de formulaires ou des processus d’envoi. Cette section fournit des conseils de dépannage complets pour les problèmes courants d’AEM Forms.

### Problèmes d’installation et de configuration

<table>
  <tbody>
  <tr>
    <td><strong>Installation et configuration</strong></td>
    <td><strong>Problèmes de création de formulaire</strong></td>
    <td><strong>Performances et mise en cache</strong></td>
  </tr>
  <tr>
    <td><a href="/help/forms/troubleshooting-installation-and-configuration.md">Option Forms non disponible dans la navigation</a></td>
    <td><a href="/help/forms/form-creation-failing.md">La création du formulaire échoue après la publication du modèle</a></td>
    <td><a href="/help/forms/troubleshooting-caching-performance.md">Problèmes de mise en cache du Forms adaptatif</a></td>
  </tr>
  <tr>
    <td><a href="/help/forms/troubleshooting-installation-and-configuration.md#build-pipeline-fails">Échecs de création de pipeline</a></td>
    <td><a href="/help/forms/form-creation-failing.md#cause-form-creation-fails">Problèmes de séquence de publication des modèles</a></td>
    <td><a href="/help/forms/troubleshooting-caching-performance.md#images-videos-not-invalidated">Problèmes d’invalidation du cache de Dispatcher</a></td>
  </tr>
  <tr>
    <td><a href="/help/forms/troubleshooting-installation-and-configuration.md#bundles-inactive-state">Problèmes d’activation des lots</a></td>
    <td><a href="/help/forms/known-issues.md">Limites connues de création de formulaires</a></td>
    <td><a href="/help/forms/troubleshooting-caching-performance.md#cdn-caching-stops-working-after-300-seconds">Échecs de mise en cache CDN</a></td>
  </tr>
  </tbody>
</table>

### Problèmes d’envoi et d’intégration de formulaire

<table>
  <tbody>
  <tr>
    <td><strong>Edge Delivery Services</strong></td>
    <td><strong>Actions Envoyer personnalisées</strong></td>
    <td><strong>Problèmes d’intégration</strong></td>
  </tr>
  <tr>
    <td><a href="/help/forms/troubleshooting-403-forbidden-edge-delivery-form-submission.md">403 Erreurs interdites lors de l’envoi du formulaire</a></td>
    <td><a href="/help/forms/custom-submit-action-troubleshooting.md">Erreurs 502 dans les actions d’envoi personnalisées</a></td>
    <td><a href="https://experienceleague.adobe.com/fr/docs/experience-cloud-kcs/kbarticles/ka-27434">Échec de redirection DRM-SAML</a></td>
  </tr>
  <tr>
    <td><a href="/help/forms/troubleshooting-403-forbidden-edge-delivery-form-submission.md#cors-issues">Problèmes de configuration CORS</a></td>
    <td><a href="/help/forms/custom-submit-action-troubleshooting.md#resolution">Gestion des exceptions non gérée</a></td>
    <td><a href="https://experienceleague.adobe.com/fr/docs/experience-cloud-kcs/kbarticles/ka-27075">Bouton Envoyer désactivé dans AEM Sites</a></td>
  </tr>
  <tr>
    <td><a href="/help/forms/troubleshooting-403-forbidden-edge-delivery-form-submission.md#referrer-filter-issues">Configuration du filtre Référent</a></td>
    <td><a href="/help/forms/custom-submit-action-for-adaptive-forms-based-on-core-components.md">Bonnes pratiques relatives aux actions personnalisées</a></td>
    <td><a href="https://experienceleague.adobe.com/fr/docs/experience-cloud-kcs/kbarticles/ka-26532">Visibilité des champs masqués après les mises à niveau</a></td>
  </tr>
  </tbody>
</table>

### Designer et problèmes de développement

<table>
  <tbody>
  <tr>
    <td><strong>AEM Forms Designer</strong></td>
    <td><strong>Environnement de développement</strong></td>
    <td><strong>Version et compatibilité</strong></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/fr/docs/experience-cloud-kcs/kbarticles/ka-26558">Designer 6.5 ne s’ouvre pas après la mise à niveau</a></td>
    <td><a href="https://experienceleague.adobe.com/fr/docs/experience-cloud-kcs/kbarticles/ka-27089">Les services de localisation ne commencent pas par JDK 8/11.</a></td>
    <td><a href="https://experienceleague.adobe.com/fr/docs/experience-cloud-kcs/kbarticles/ka-26862">Problèmes d’affichage de la version du package AEM Forms (AEMFD)</a></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/fr/docs/experience-cloud-kcs/kbarticles/ka-21018">Erreurs PDF Generator JPEG 2000</a></td>
    <td><a href="https://experienceleague.adobe.com/fr/docs/experience-cloud-kcs/kbarticles/ka-22689">Configuration du chemin du journal JBoss</a></td>
    <td><a href="https://experienceleague.adobe.com/fr/docs/experience-cloud-kcs/kbarticles/ka-26846">Numéros de version incorrects sous Windows</a></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/fr/docs/experience-cloud-kcs/kbarticles/ka-27406">Bouton manquant dans la sortie PDF</a></td>
    <td><a href="https://experienceleague.adobe.com/fr/docs/experience-cloud-kcs/kbarticles/ka-18084">Erreurs de mise à niveau de Configuration Manager</a></td>
    <td><a href="https://experienceleague.adobe.com/fr/docs/experience-cloud-kcs/kbarticles/ka-17339">Solution de contournement de la corruption d’index</a></td>
  </tr>
  </tbody>
</table>



