---
title: Notes de mise à jour de la version 2022.4.0 d’ [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour de la version 2022.4.0 d’ [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: 6c86838a-cabf-4770-b1ae-618af70193a2
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '569'
ht-degree: 87%

---

# Notes de mise à jour 2022.4.0 pour [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section suivante décrit les notes de mise à jour des fonctionnalités de la version 2022.4.0 de [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>À partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes ; par exemple, celles de 2020, 2021 et ainsi de suite.

>[!NOTE]
>
>Voir [Mises à jour récentes de la documentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=fr) pour plus d’informations sur les mises à jour de la documentation qui ne sont pas directement liées à une version.

## Date de publication {#release-date}

La date de publication de la version actuelle (2022.4.0) d’[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] est le 5 mai 2022.
La prochaine version (2022.5.0) est prévue pour le 9 juin 2022.

## Vidéo de mise à jour {#release-video}

Consultez la vidéo [Aperçu de la version d’avril 2022](https://video.tv.adobe.com/v/342612?quality=12) pour obtenir un résumé des fonctionnalités ajoutées dans la version 2022.4.0.

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Nouvelles fonctionnalités de [!DNL Sites] {#sites-features}

* Les types de données de modèle de contenu peuvent désormais être définis comme [traduisible](/help/assets/content-fragments/content-fragments-models.md#properties) à l’aide d’une simple case à cocher dans l’éditeur de modèles de contenu. En outre, les règles et configurations de traduction AEM sont automatiquement mises à jour.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Nouvelles fonctionnalités de [!DNL Assets] {#assets-features}

* Vous pouvez désormais [trier les balises](/help/assets/organize-assets.md#use-tags-to-organize-assets) dans la fenêtre du sélecteur de balises, par ordre croissant ou décroissant, en fonction du nom de la balise, de la date de création ou de la date de modification.


## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Nouveautés de [!DNL Forms] {#what-is-new-forms}

* **Communications - Prise en charge des API de manipulation de documents dans le SDK Forms as a Cloud Service** : les [API de manipulation de documents](/help/forms/aem-forms-cloud-service-communications.md) vous aident à combiner, réorganiser et valider des documents PDF. Vous pouvez désormais utiliser les API Communications - Génération de documents dans un environnement de développement local à l’aide du SDK AEM Forms as a Cloud Service.

* **Utilisation de fichiers XCI personnalisés pour générer un document d’enregistrement** : vous pouvez désormais [utiliser un fichier XCI personnalisé pour définir différentes propriétés d’un document d’enregistrement](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#use-a-custom-xci-file). Il remplace le XCI maître par les modifications personnalisées. Il offre un meilleur contrôle sur la génération des documents d’enregistrement, ce qui accroît les possibilités de personnalisation et de personnalisation.

* **Utilisation d’un CAPTCHA invisible dans un formulaire adaptatif** : vous pouvez paramétrer le [CAPTCHA invisible pour qu’il ne présente le test CAPTCHA qu’en cas d’activité suspecte](/help/forms/captcha-adaptive-forms.md). Si aucune activité suspecte n’est détectée, le test CAPTCHA ne s’affiche pas. Il permet d’évaluer le remplissage du formulaire par un humain sans exiger de case à cocher, de réduire les efforts de personnalisation et d’améliorer l’expérience de l’utilisateur final.

* **Configurations du modèle de données de formulaire** : vous pouvez désormais [réutiliser des configurations de modèle de données de formulaire dans les environnements](/help/forms/create-form-data-models.md#runmode-specific-context-aware-config), en simplifiant les intégrations de données et en réduisant les coûts informatiques.


## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### Analyseurs de build de SDK {#sdk-build-analyzers}

Le plug-in Build Analyzer Maven du SDK AEM as a Cloud Service détecte des problèmes dans un projet Maven, y compris les dépendances manquantes. Il permet aux développeurs d’identifier des problèmes au cours du développement local, bien avant leur déploiement dans les environnements cloud avec Cloud Manager.

Un nouvel analyseur a été ajouté récemment :

* `content-packages-validation` : valide une syntaxe et une structure de contenu correctement formées pour les modules installés lors du déploiement.

Il est vivement recommandé de mettre à jour votre projet Maven avec la dernière version de l’analyseur ou d’inclure l’analyseur si vous ne l’avez pas encore fait. Pour plus d’informations, voir la documentation [ici](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin.html?lang=fr).

## Couche de sécurité [!DNL Experience Manager] as a [!DNL Cloud Service] {#foundation-security}

### Dépréciation de TLS 1.0 et 1.1

À compter du 30 juin 2022, l’as a Cloud Service Experience Manager devra disposer d’une communication réseau plus sécurisée et d’un échange de données avec les systèmes utilisateurs. AEM a l’intention d’utiliser exclusivement le protocole TLS (Transport Layer Security), 1.2. Les anciennes versions de TLS 1.0 et 1.1 sont désormais obsolètes.

Si vous continuez à utiliser des versions antérieures à TLS 1.0 et 1.1, vous risquez de perdre l’accès à Experience Manager as a Cloud Service.

## Cloud Manager {#cloud-manager}

Vous trouverez la liste complète des versions mensuelles de Cloud Manager [ici](/help/implementing/cloud-manager/release-notes/current.md).

## Outils de migration {#migration-tools}

Vous trouverez une liste complète des versions des outils de migration [ici](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
