---
title: Dépannage dans AEM Assets
description: Résolvez les problèmes courants d’AEM Assets à l’aide des liens d’article pour les domaines clés d’AEM Assets, tels que les chargements, les métadonnées, la recherche, la diffusion, etc.
hidefromtoc: true
hide: true
source-git-commit: 60667c265cf480521fe0c0d646c2665540f110d0
workflow-type: tm+mt
source-wordcount: '588'
ht-degree: 0%

---


# Dépannage dans AEM Assets {#troubleshoot-aem-assets}

AEM Assets as a Cloud Service offre une solution PaaS native cloud permettant aux entreprises non seulement d’effectuer leurs opérations de gestion des ressources numériques et Dynamic Media, mais aussi d’utiliser des fonctionnalités intelligentes de nouvelle génération, telles que l’IA/ML. Le tout depuis un système qui est toujours à jour, toujours disponible et qui apprend en permanence.

Cependant, des problèmes peuvent survenir et avoir une incidence sur le chargement des ressources, les métadonnées, la recherche ou la diffusion, ainsi que d’autres domaines clés d’AEM Assets. Cet article fournit des étapes de dépannage pour vous aider à diagnostiquer et à résoudre ces problèmes courants d’AEM Assets.

<table>
  <tbody>
  <tr>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27140">Rendus manquants dans le fichier ZIP de téléchargement de ressources dans AEM</a> </td>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26616">Fragments de contenu non inclus dans la licence AEM Assets</a> </td>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26928">Commentaires limités dans la vue Assets malgré l’accès en lecture</a> </td> 
    </tr>
    <tr>
    <td>Visionneuses à 360° <a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26715">(Dynamic Media) bloquées en statut de traitement dans AEM Dynamic Media</a> </td>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26639">Les rendus de la gestion des ressources numériques (DAM) ne correspondent pas aux fichiers d’origine dans AEM</a> </td>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26873">Rendus de recadrage intelligent non générés dans AEMaaCS</a> </td> 
    </tr>
    <tr>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26533">(Dynamic Media) Correction des problèmes de chargement, de traitement et de rendu vidéo dans AEM</a> </td>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26922">(Asset Link) Adobe Asset Link conserve les liens dans un état inaccessible lors de l’utilisation d’InDesign</a> </td>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26677">Incohérence des miniatures vidéo entre le mode Dynamic Media et la vue Carte de gestion des ressources numériques dans AEMaaCS</a> </td> 
    </tr>
    <tr>
  <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26610">Échec du traitement des ressources pour les fichiers MP4 volumineux dans AEM as a Cloud Service</a></td>
  <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26871">(Dynamic Media) Le lecteur vidéo Dynamic Media ne fonctionne pas dans les environnements inférieurs</a></td>
  <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26103">(Dynamic Media avec OpenAPI) Activer l’accès restreint d’Assets à Dynamic Media avec des API ouvertes basées sur des groupes d’utilisateurs IMS</a></td>
</tr>
<tr>
  <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-23916">Lorsqu’un fichier Tiff avec compression ZIP est chargé dans AEM Assets, aucun rendu n’est généré</a></td>
  <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26785">AEM tronque le texte extrait des PDF volumineux après 100 000 jetons</a></td>
  <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-17628">(Dynamic Media) Modification de l’URL Dynamic Media pour DM Assets</a></td>
</tr>
<tr>
  <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26655">Résolution des problèmes de visibilité des schémas de métadonnées pour les utilisateurs non-administrateurs dans AEMaaCS</a></td>
  <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26637">(Dynamic Media) Problème de changement de couleur d’arrière-plan pour les rendus d’image TIFF dans Dynamic Media</a></td>
  <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26528">Le problème de rotation des ressources AEMaaCS rend les rotations suivantes invisibles.</a></td>
</tr>
<tr>
  <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26367">(Dynamic Media) Résolution d’un problème d’image rompue avec le recadrage intelligent dans Adobe Experience Manager 6.5 Dynamic Media</a></td>
  <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26450">Augmentation de la limite de chargement de ressources en une seule partie pour l’intégration de l’API Photoshop Firefly</a></td>
  <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26461">(Dynamic Media) Résoudre les incohérences de nom de ressource Dynamic Media dans les environnements AEM pour les fichiers PDF</a></td>
</tr>
<tr>
  <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26233">Certaines images n’affichent pas les rendus de miniature dans Adobe Experience Manager (AEM) as a Cloud Service - Ressource</a></td>
  <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25294">(Dynamic Media) La page Paramètres généraux de Dynamic Media ne s’ouvre pas</a></td>
  <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26197">(Dynamic Media) Résolution de problèmes audio dans les fichiers vidéo avec Dynamic Media dans AEM</a></td>
</tr>
<tr>
  <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25925">Balisage automatique des ressources nouvellement chargées dans AEM as a Cloud Service</a></td>
  <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25889">La fonctionnalité de balises intelligentes ne fonctionne pas après la migration de JWT vers OAuth dans AEM</a></td>
  <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25903">Résoudre les problèmes de liens partagés dans AEM Managed Services</a></td>
</tr>
<tr>
  <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25607">(Dynamic Media) Échec du traitement des ressources dans AEM Dynamic Media</a></td>
  <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25885">(Dynamic Media) Échec de synchronisation des ressources dans Adobe Experience Manager (AEM) Dynamic Media</a></td>
  <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25829">Mise à jour des miniatures personnalisées pour les ressources vidéo dans AEM as a Cloud Service</a></td>
</tr>
<tr>
  <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25828">Incohérence des métadonnées d’image dans Adobe Experience Manager (AEM) Assets</a></td>
  <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-21865">Échec du glisser-déposer d’un dossier de ressources vers l’interface utilisateur web d’AEM Assets</a></td>
  <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25525">(Dynamic Media) Résolution de problèmes de traitement des ressources dans AEM as a Cloud Service</a></td>
</tr>
<tr>
  <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25518">Limites de l’extraction de texte pour les PDF volumineux dans Adobe Experience Manager as a Cloud Service</a></td>
  <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25562">(Asset Link) Résolution des problèmes de connexion aux liens des ressources de Adobe Experience Manager (AEM) dans InDesign</a></td>
  <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25506">(Asset Link) Erreur réseau du plug-in Adobe Asset Link : le serveur est inatteignable</a></td>
</tr>
<tr>
  <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25471">(Dynamic Media) Recommandations d’utilisateur pour la synchronisation Dynamic Media</a></td>
  <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26902">(Dynamic Media) Exporter des ressources et des métadonnées depuis Dynamic Media à l’aide de l’API</a></td>
  <td></td>
</tr>

</tbody>
  <table>


