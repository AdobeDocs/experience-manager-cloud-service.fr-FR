---
title: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
mini-toc-levels: 1
source-git-commit: 6d343e539be05a13bb2a3eaeba1da5656dc54f1a
workflow-type: tm+mt
source-wordcount: '626'
ht-degree: 23%

---


# Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section suivante concerne les notes de mise à jour générales de la version actuelle (la plus récente) d’[!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>À partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes ; par exemple, celles de 2020, 2021 et ainsi de suite.

>[!NOTE]
>
>Voir [Mises à jour récentes de la documentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=fr) pour plus d’informations sur les mises à jour de la documentation qui ne sont pas directement liées à une version.

## Date de publication {#release-date}

La date de publication de [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] la version actuelle (2022.8.0) est le 1er septembre 2022.
La prochaine version (2022.10.0) est prévue pour le 27 octobre 2022.

## Vidéo de mise à jour {#release-video}

Regardez la vidéo Aperçu de la version d’août 2022 pour un résumé des fonctionnalités ajoutées dans la version 2022.8.0 :

>[!VIDEO](https://video.tv.adobe.com/v/346608/?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Nouvelles fonctionnalités de [!DNL Sites] {#sites-features}

* Le composant Email permet de créer du contenu dans AEM qui est ensuite diffusé par Campaign Classic sous la forme d’emails. Le composant principal Email :
   * est basé sur la variable [Composant WCM principal](https://github.com/adobe/aem-core-wcm-components) qui prend en charge les modèles modifiables et le système de style.
   * fournit 10 composants prêts à l’emploi optimisés pour la production (page, conteneur, titre, texte, image, bouton, teaser, fragment d’expérience, fragment de contenu, segmentation).
   * permet une personnalisation et une segmentation avancées grâce au [insertion de variables Campaign](https://github.com/adobe/aem-core-email-components/wiki/RTE-Personalization) sur la plupart des champs de boîte de dialogue et à la variable [Composant Segmentation](https://github.com/adobe/aem-core-email-components/wiki/Segmentation-component-(Technical-Documentation)).
   * fournit une sortie de HTML optimale pour les emails grâce au [Styles CSS inliner](https://github.com/adobe/aem-core-email-components/wiki/HTML-Inliner:-Technical-documentation), la variable [Attribut HTML inliner](https://github.com/adobe/aem-core-email-components/wiki/HTML-Inliner:-Technical-documentation), et la variable [assainisseur de HTMLs](https://github.com/adobe/aem-core-email-components/wiki/HTML-sanitizing:-Technical-documentation).
   * permet de créer des emails n’importe où.

### Nouvelles fonctionnalités disponibles dans le canal de version préliminaire [!DNL Sites] {#prerelease-features-sites}

* Le [Console de fragments de contenu](/help/sites-cloud/administering/content-fragments/content-fragments-console.md) permet aux utilisateurs d’afficher le nombre total de copies de langue associées à un fragment de contenu. Un accès en 1 clic a été fourni pour afficher toutes les copies de langue. Les utilisateurs peuvent également filtrer l’affichage du tableau en fonction des paramètres régionaux qui les intéressent.

![Langues de fragments de contenu](/help/release-notes/assets/cfconsole-languages.png)

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Nouvelles fonctionnalités de [!DNL Assets] {#features-assets}

* Vous pouvez maintenant configurer Adobe Experience Manager Assets sur [restreindre le type de ressources que les utilisateurs peuvent charger en fonction du type MIME ;](/help/assets/configure-asset-upload-restrictions.md).

   ![Restrictions de chargement des ressources](/help/assets/assets/asset-upload-restrictions.png)

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Nouvelles fonctionnalités disponibles dans le canal de version préliminaire [!DNL Forms] {#prerelease-features-forms}

* [Assistant de Forms adaptatif](/help/forms/creating-adaptive-form.md): AEM Forms fournit un assistant convivial destiné à l’entreprise afin de créer rapidement un Forms adaptatif. L’assistant dispose d’une navigation rapide par onglets pour sélectionner facilement un modèle, un style, des champs et des options d’envoi préconfigurés afin de créer un formulaire adaptatif. Cette version apporte les améliorations suivantes à l’assistant :

   * Sélectionnez ou désélectionnez des champs : L’assistant vous permet de créer un formulaire adaptatif basé sur des schémas de modèle de données de formulaire et JSON. Vous pouvez désormais sélectionner un sous-ensemble de champs dans un schéma à inclure dans un formulaire adaptatif. Les champs sélectionnés sont convertis en composants de capture de données de formulaire adaptatif correspondants pour créer rapidement les formulaires adaptatifs souhaités.

   * Utiliser des modèles statiques : Les clients qui ont déjà investi dans des modèles statiques hérités peuvent continuer leur parcours d’adoption du cloud en utilisant des modèles statiques dans l’assistant pour créer des formulaires adaptatifs. Les clients disposent ainsi d’un temps supplémentaire pour migrer les anciens modèles statiques vers des modèles modifiables modernes.

* [Suppression des champs masqués d’un document d’enregistrement (DE) lors du traitement côté serveur](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md): Vous pouvez générer le document du PDF d’enregistrement pour les utilisateurs finaux contenant uniquement les champs qui leur ont été visibles lors de l’expérience de capture de données. Lors de l’envoi du formulaire, le serveur valide les champs qui ont été masqués à l’utilisateur final en fonction des données envoyées et exclut du document d’enregistrement par souci de cohérence.

## Module complémentaire CIF {#cloud-services-cif}

### Nouveautés {#what-is-new-cif}

* Association des pages d’AEM aux produits et aux catégories via AEM propriétés de page plus aperçu dans le cockpit du produit
   ![association de page du cockpit du produit](/help/assets/CIF/product_cockpit_page_association.png)

## Cloud Manager {#cloud-manager}

Vous trouverez la liste complète des versions mensuelles de Cloud Manager [ici](/help/implementing/cloud-manager/release-notes-cloud-manager/release-notes-cm-current.md).

## Outils de migration {#migration-tools}

Vous trouverez une liste complète des versions des outils de migration [ici](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
