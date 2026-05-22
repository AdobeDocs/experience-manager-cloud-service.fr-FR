---
title: Notes de mise à jour de la version 2022.8.0 d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la version 2022.8.0 d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: 0eff8100-5990-4553-8373-445fb7e6fb27
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '677'
ht-degree: 58%

---

# Notes de mise à jour de la version 2022.8.0 d’[!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section ci-dessous présente les notes de mise à jour des fonctionnalités de la version 2022.8.0 d’[!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>À partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes ; par exemple, celles de 2020, 2021 et ainsi de suite.

>[!NOTE]
>
>Voir [Mises à jour récentes de la documentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=fr) pour plus d’informations sur les mises à jour de la documentation qui ne sont pas directement liées à une version.

## Date de publication {#release-date}

La date de publication de la version actuelle (2022.8.0) d’[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] est le vendredi 1 septembre 2022.
La prochaine version (2022.10.0) est prévue pour le 10 novembre 2022.

## Vidéo de mise à jour {#release-video}

Consultez la vidéo Vue d’ensemble de la version d’août 2022 pour un résumé des fonctionnalités ajoutées dans la version 2022.8.0 :

>[!VIDEO](https://video.tv.adobe.com/v/346608/?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Nouvelles fonctionnalités de [!DNL Sites] {#sites-features}

* Le composant E-mail permet de créer du contenu dans AEM qui est ensuite diffusé par e-mail via Campaign Classic. Le composant E-mail principal :
   * est basé sur le [composant WCM principal](https://github.com/adobe/aem-core-wcm-components) qui prend en charge les modèles modifiables et le système de style.
   * fournit 10 composants prêts pour la production et optimisés pour les e-mails (Page, Conteneur, Titre, Texte, Image, Bouton, Teaser, Fragment d’expérience, Fragment de contenu, Segmentation).
   * personnalisation et segmentation avancées grâce à l’[insertion de variables Campaign](https://github.com/adobe/aem-core-email-components/wiki/RTE-Personalization) sur la plupart des champs de boîte de dialogue et au [composant Segmentation](https://github.com/adobe/aem-core-email-components/wiki/Segmentation-component-(Technical-Documentation)) flexible.
   * fournit une sortie HTML optimale adaptée aux e-mails, grâce à l’intégrateur de styles [CSS](https://github.com/adobe/aem-core-email-components/wiki/HTML-Inliner:-Technical-documentation), l’intégrateur d’attributs [HTML](https://github.com/adobe/aem-core-email-components/wiki/HTML-Inliner:-Technical-documentation) et l’[assainisseur HTML](https://github.com/adobe/aem-core-email-components/wiki/HTML-sanitizing:-Technical-documentation).
   * permet la création d’e-mails n’importe où.

### Nouvelles fonctionnalités disponibles dans le canal de version préliminaire [!DNL Sites] {#prerelease-features-sites}

* La [&#x200B; Console de fragments de contenu &#x200B;](/help/sites-cloud/administering/content-fragments/managing.md#content-fragments-console) permet aux utilisateurs d’afficher le nombre total de copies de langue associées à un fragment de contenu. En un seul clic, vous pouvez désormais afficher toutes les copies de langue. Les utilisateurs et utilisatrices peuvent également filtrer la vue du tableau en fonction des paramètres régionaux de leur choix.

![Langues de fragments de contenu](/help/release-notes/assets/cfconsole-languages.png)

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Nouvelles fonctionnalités de [!DNL Assets] {#features-assets}

* Vous pouvez désormais configurer Adobe Experience Manager Assets pour [&#x200B; restreindre le type de ressources que les utilisateurs peuvent charger en fonction du type MIME &#x200B;](/help/assets/configure-asset-upload-restrictions.md).

  ![Restrictions de téléchargement des ressources](/help/assets/assets/asset-upload-restrictions.png)

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Nouvelles fonctionnalités disponibles dans le canal de version préliminaire [!DNL Forms] {#prerelease-features-forms}

* [Assistant de formulaires adaptatifs](/help/forms/creating-adaptive-form.md) : AEM Forms offre un assistant convivial pour l’utilisateur professionnel afin de créer rapidement des formulaires adaptatifs. L’assistant fournit une navigation rapide par onglets pour sélectionner facilement un modèle, un style, des champs et des options d’envoi préconfigurés afin de créer un formulaire adaptatif. Dans cette nouvelle version, l’assistant bénéficie des améliorations suivantes :

   * Sélectionner ou désélectionner des champs : l’assistant vous permet de créer un formulaire adaptatif basé sur des schémas de modèles JSON et de données de formulaire. Vous pouvez désormais sélectionner un sous-ensemble de champs dans un schéma à inclure dans un formulaire adaptatif. Les champs sélectionnés sont convertis en composants de capture de données correspondants dans le formulaire adaptatif afin de créer rapidement les formulaires adaptatifs souhaités.

   * Utilisation de modèles statiques : les client(e)s qui utilisent toujours les modèles statiques hérités peuvent poursuivre leur migration vers le cloud en utilisant des modèles statiques dans l’assistant pour créer des formulaires adaptatifs. Les client(e)s disposent ainsi de temps supplémentaire pour migrer des anciens modèles statiques vers des modèles modifiables modernes.

* [Suppression des champs masqués d’un document d’enregistrement (DoR) lors du traitement serveur](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md) : vous pouvez générer le document d’enregistrement au format PDF à destination des utilisateurs et utilisatrices finaux contenant uniquement les champs qui leur étaient visibles lors de l’expérience de capture de données. Lors de l’envoi du formulaire, le serveur valide les champs qui étaient masqués à l’utilisateur en fonction des données envoyées et les exclut du document d’enregistrement par souci de cohérence.

## Module complémentaire CIF {#cloud-services-cif}

### Nouveautés {#what-is-new-cif}

* Association des pages AEM aux produits et aux catégories à l’aide des propriétés de page AEM et aperçu dans le cockpit de produits
  ![Association de page du cockpit de produits](/help/assets/CIF/product_cockpit_page_association.png)

## Cloud Manager {#cloud-manager}

Vous trouverez la liste complète des versions mensuelles de Cloud Manager [ici](/help/implementing/cloud-manager/release-notes/current.md).

## Outils de migration {#migration-tools}

Vous trouverez une liste complète des versions des outils de migration [ici](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
