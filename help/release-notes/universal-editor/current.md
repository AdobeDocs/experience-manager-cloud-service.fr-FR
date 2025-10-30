---
title: Notes de mise à jour de l’éditeur universel version 2025.10.30
description: Il s’agit des notes de mise à jour de la version 2025.10.30 de l’éditeur universel.
feature: Release Information
role: Admin
exl-id: d16ed78d-d5a3-45bf-a415-5951e60b53f9
source-git-commit: e3e571bef450ddc09eb30ab7d73b144ea521a87b
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 58%

---


# Notes de mise à jour de l’éditeur universel version 2025.10.30 {#release-notes}

Voici les notes de mise à jour de la version du 30 octobre 2025 de l’éditeur universel.

>[!TIP]
>
>Si vous souhaitez tester les fonctionnalités de l’éditeur universel **à venir** avant leur publication, reportez-vous aux [Notes de mise à jour de l’aperçu de l’éditeur universel.](/help/release-notes/universal-editor/preview.md)

>[!TIP]
>
>Consultez [cette page](/help/release-notes/release-notes-cloud/release-notes-current.md) pour obtenir les notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service.

## Nouveautés {#what-is-new}

* [Le nouvel éditeur de texte enrichi](#new-rte) peut désormais insérer des images.
   * Cette fonctionnalité est désactivée en OtB et doit être explicitement activée via une [&#x200B; définition de filtre &#x200B;](/help/implementing/universal-editor/configure-rte.md#toolbar).

## Fonctionnalités d’adoption précoce {#early-adopter}

Si vous souhaitez tester ces nouvelles fonctionnalités à venir et partager vos commentaires, envoyez un e-mail à la personne responsable du succès client d’Adobe de votre équipe à partir de l’adresse e-mail associée à votre Adobe ID.

### Nouvel éditeur de texte enrichi {#new-rte}

Le nouvel éditeur de texte enrichi ProseMirror, qui présente un sélecteur de page dans la boîte de dialogue du lien, est désormais disponible dans le panneau de droite. [Cet éditeur de texte enrichi offre des options de configuration flexibles.](/help/implementing/universal-editor/configure-rte.md)

## Autres améliorations {#other-improvements}

* L’événement de mise à jour est désormais informé si l’action a été annulée.
* `No results` chaîne dépend désormais des paramètres régionaux du navigateur dans les balises de l’éditeur universel.
* Correction d’un saut de ligne supplémentaire dans le bouton de publication de l’éditeur universel.
* Le nettoyage a été effectué sur l’API de correctif.
* Le bouton Sélectionner le contenu est désormais visible dans Safari.
* La version RPM a été corrigée.
* Mise à jour CORS pour éviter de mettre à jour à nouveau le texte modifié après l’enregistrement.
