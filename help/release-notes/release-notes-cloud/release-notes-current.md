---
title: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
source-git-commit: 6b38601e9bd29c71e5f70b46d2fa55a928851adc
workflow-type: tm+mt
source-wordcount: '1049'
ht-degree: 41%

---

# Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section suivante concerne les notes de mise à jour techniques de la version actuelle (la plus récente) d’[!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>À partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes ; par exemple, celles de 2021, 2022 et ainsi de suite.
>
>Consultez la section [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=fr) pour en savoir plus sur les activations de fonctionnalités à venir pour [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Voir [Mises à jour récentes de la documentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=fr) pour plus d’informations sur les mises à jour de la documentation qui ne sont pas directement liées à une version.

## Date de publication {#release-date}

La date de publication de [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] la version actuelle des fonctionnalités (2023.4.0) est le 7 juin 2023. La prochaine version de la fonctionnalité (2023.6.0) est prévue pour le 29 juin 2023.

## Vidéo de mise à jour {#release-video}

Consultez la vidéo Aperçu de la version d’avril 2023 pour obtenir un résumé des fonctionnalités ajoutées dans la version 2023.4.0:

>[!VIDEO](https://video.tv.adobe.com/v/3418681/?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Nouvelles fonctionnalités de [!DNL Experience Manager Sites] {#sites-features}

* Exportez des fragments de contenu d’AEM as a Cloud Service vers Adobe Target en tant qu’offres JSON.
* La prise en charge de la pagination et du tri GraphQL, ainsi que des améliorations de la mise en cache interne, permettent désormais d’accroître les performances des applications clientes découplées lors de la récupération de jeux de contenu volumineux d’AEM à l’aide de requêtes et de filtres GraphQL complexes.

### Nouvelles fonctionnalités d’ [!DNL Experience Manager Sites] premise {#prerelease-sites}

* Les fragments de contenu et leurs références peuvent désormais être publiés dans la [Service d’aperçu AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-environments.html?lang=en#access-preview-service) en utilisant la variable [Console de fragments de contenu](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/content-fragments/content-fragments-console.html?lang=en), permettant aux utilisateurs de prévisualiser l’expérience finale sur une application d’aperçu découplée avant la mise en ligne.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Nouvelles fonctionnalités de [!DNL Assets] {#assets-features}

* Ajout de la prise en charge des images WebP pour extraire automatiquement les métadonnées, générer des miniatures et des rendus personnalisés. La fonctionnalité de balises intelligentes est désormais prise en charge pour ces fichiers. Les fonctionnalités Dynamic Media ne sont pas prises en charge pour WebP en tant que format d’entrée.

* [Améliorations de l’expérience de recherche](/help/assets/search-assets.md#aftersearch) - Vous pouvez désormais effectuer rapidement les opérations suivantes sur les ressources qui s’affichent dans les résultats de recherche :

   * Créer un workflow
   * Créer une version
   * Lier ou dissocier des ressources

      Vous n’avez pas besoin d’accéder à l’emplacement de la ressource et d’afficher ses propriétés pour effectuer ces opérations.

* Améliorations de la convivialité des facettes de recherche de couleurs : le champ d’entrée pour les valeurs de couleur est désormais modifiable et les résultats de recherche ne sont mis à jour que lorsque vous quittez le sélecteur de couleurs.

* Prise en charge du nouveau protocole (DASH, Dynamic Adaptive Streaming over HTTP) pour le streaming adaptatif dans les diffusions vidéo Dynamic Media (avec CMAF activé) :
   * Le streaming adaptatif (DASH/HLS) garantit une meilleure expérience de visionnage des vidéos à l’utilisateur ou l’utilisatrice final.
   * Largement adopté dans le secteur, DASH est le protocole standard international pour le streaming à débit adaptatif de vidéos
   * Disponible dans toutes les régions, à activer via un ticket d’assistance

* Dynamic Media _Instantané_ - Testez des images de test ou des URL Dynamic Media pour voir la sortie de différents modificateurs d’image et les optimisations de l’imagerie dynamique pour la taille de fichier (avec diffusion WebP et AVIF), la bande passante réseau et le rapport pixel du périphérique. Voir [Instantané Dynamic Media](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/images/dynamic-media-snapshot.html).

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Nouvelles fonctionnalités disponibles dans [!DNL Forms] {#new-features-available-in-channel}

* **[Envois de formulaires adaptatifs à Microsoft SharePoint et Microsoft OneDrive](/help/forms/configuring-submit-actions.md)** : améliorez l’agilité des utilisateurs et utilisatrices professionnels pour ouvrir rapidement de nouveaux formulaires et stockez les données envoyées dans les outils quotidiens qu’ils et elles utilisent comme les sites Microsoft SharePoint ou les dossiers OneDrive.

### Fonctionnalités de la version préliminaire de [!DNL Forms] {#prerelease-features-forms}

* [Amélioration de l’intégration et de la conformité de Adobe Acrobat Sign](/help/forms/adobe-sign-integration-adaptive-forms.md): AEM Forms s’intègre désormais à Adobe Acrobat Sign for Government, offrant un niveau avancé de conformité et de sécurité pour les signatures électroniques avec des envois de formulaires adaptatifs pour les comptes associés aux administrations (ministères et agences gouvernementales).

   L’intégration à Adobe Acrobat Sign for Government permet à nos partenaires et clients gouvernementaux d’utiliser des signatures électroniques dans Adaptive Forms pour certains secteurs d’activité les plus critiques et les plus sensibles. Cette couche supplémentaire de sécurité garantit que toutes les signatures électroniques sont entièrement conformes à la conformité FedRAMP Modérate, offrant ainsi à nos clients gouvernementaux une certaine tranquillité d’esprit.

* [Forms adaptatif dans l’éditeur AEM Sites](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md): Vous pouvez désormais utiliser l’éditeur AEM Sites pour créer et ajouter rapidement plusieurs formulaires aux pages de vos sites. Cette fonctionnalité permet aux auteurs de contenu de créer des expériences de capture de données transparentes dans les pages Sites à l’aide de la puissance des composants de formulaires adaptatifs, notamment le comportement dynamique, les validations, l’intégration de données, la génération d’un document d’enregistrement et l’automatisation des processus d’entreprise. Vous pouvez :

   * Créez un formulaire adaptatif en faisant glisser les composants de formulaire vers le composant de conteneur de Forms adaptatif dans l’éditeur AEM Sites ou les fragments d’expérience.
   * Utilisez l’assistant de Forms adaptatif de l’éditeur AEM Sites pour créer des formulaires indépendants de toute page Sites, ce qui vous permet de réutiliser ces formulaires sur plusieurs pages.
   * Ajoutez plusieurs formulaires à une page Sites, en rationalisant l’expérience utilisateur et en offrant une plus grande flexibilité.

      >[!VIDEO](https://video.tv.adobe.com/v/3419284?quality=12&learn=on)

* Amélioration de la gestion des erreurs avec les gestionnaires d’erreurs personnalisés dans l’éditeur de règles : Vous pouvez désormais appeler une fonction personnalisée (à l’aide de la bibliothèque cliente) en réponse à une erreur renvoyée par un service externe et fournir une réponse personnalisée aux utilisateurs finaux ou prendre des mesures spécifiques pour les erreurs renvoyées par un service. Par exemple, vous pouvez appeler un workflow personnalisé dans le serveur principal pour des codes d’erreur spécifiques ou informer le client que le service est hors service.

   Cela permet d’améliorer votre fonctionnalité globale de gestion des erreurs en introduisant des réponses d’erreur basées sur des normes, qui sont rétrocompatibles avec les gestionnaires d’erreurs prêts à l’emploi, avec une plus grande flexibilité et un meilleur contrôle.

## Programme des formulaires adaptatifs découplés destiné aux utilisateurs et utilisatrices précoces {#forms-early-adopter}

Utilisez les formulaires adaptatifs découplés pour permettre à vos développeurs et développeuses de créer, publier et gérer des formulaires interactifs accessibles via des API, plutôt que par le biais d’une interface utilisateur graphique classique. Les formulaires adaptatifs découplés vous aident à :

* créer des formulaires multicanaux de haute qualité dans le langage de programmation de votre choix ;
* intégrer nativement les formulaires à vos applications de bureau et mobiles, à vos sites web et à vos applications de chat ;
* réutiliser vos composants d’IU propriétaires avec des applications de formulaires ;
* tirer profit de la puissance d’Adobe Experience Manager Forms.

Vous pouvez envoyer un courrier électronique à `aem-forms-headless@adobe.com` à partir de votre ID de courrier électronique officiel pour rejoindre le programme des premiers adopteurs.

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### Nouveautés {#what-is-new-foundation}

* Autres régions de publication : Les clients de Sites peuvent acquérir sous licence jusqu’à trois régions de publication, en plus de la région Principale. Le trafic est acheminé vers des fermes de publication supplémentaires, ce qui entraîne une diminution de la latence pour certaines requêtes, ainsi qu’une plus grande résilience contre les pannes régionales. Contactez votre gestionnaire de compte Adobe pour plus d’informations sur les licences [Autres régions de publication](/help/operations/additional-publish-regions.md) pour vos programmes.

## Notes de mise à jour de la maintenance {#maintenance}

Vous trouverez les dernières notes de mise à jour de maintenance [ici](/help/release-notes/maintenance/latest.md).

## Cloud Manager {#cloud-manager}

Vous trouverez la liste complète des versions mensuelles de Cloud Manager [ici.](/help/implementing/cloud-manager/release-notes/current.md)

## Outils de migration {#migration-tools}

Vous trouverez une liste complète des versions des outils de migration [ici](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
