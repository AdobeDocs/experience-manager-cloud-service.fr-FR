---
title: Notes de mise à jour de la version 2023.10.0 d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la version 2023.10.0 d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: 81a6cbd2-7101-429b-8572-2650c5bea963
source-git-commit: 02ad83eb9fa9ed3bf06cf7fe0ef10fd9577f66a9
workflow-type: tm+mt
source-wordcount: '918'
ht-degree: 90%

---

# Notes de mise à jour de la version 2023.10.0 d’[!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section suivante concerne les notes de mise à jour de la version 2023.10.0 d’[!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>À partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes, telles que 2021 ou 2022.
>
>Consultez la section [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=fr) pour en savoir plus sur les activations de fonctionnalités à venir pour [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Voir [Mises à jour récentes de la documentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=fr) pour plus d’informations sur les mises à jour de la documentation qui ne sont pas directement liées à une version.

## Date de publication {#release-date}

La date de publication de la version actuelle de [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2023.10.0) est le 26 octobre 2023. La prochaine version des fonctionnalités (2023.11.0) est prévue pour le 30 novembre 2023.

## Notes de mise à jour de la maintenance {#maintenance}

Vous trouverez les dernières notes de mise à jour de maintenance [ici](/help/release-notes/maintenance/latest.md).

## Vidéo de mise à jour {#release-video}

Regardez la vidéo de vue d’ensemble de la version d’octobre 2023 pour un résumé des fonctionnalités ajoutées dans la version 2023.10.0 :

>[!VIDEO](https://video.tv.adobe.com/v/3425186/?quality=12)

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Nouvelles fonctionnalités {#assets-features}

**Module complémentaire AEM Assets pour Adobe Express**: Experience Manager Assets fournit désormais un module complémentaire pour l’Adobe Express. Le module complémentaire vous permet d’accéder directement aux ressources stockées dans Experience Manager Assets à partir de l’interface utilisateur d’Adobe Express. Vous pouvez placer du contenu géré dans AEM Assets dans la zone de travail d’Express, puis enregistrer du contenu nouveau ou modifié dans un référentiel AEM Assets. Le module complémentaire offre les avantages clés suivants :

* Réutilisation accrue du contenu en modifiant et en enregistrant de nouvelles ressources dans AEM.

* Réduction du temps et des efforts en général pour créer de nouvelles ressources ou créer de nouvelles versions des ressources existantes.

  ![Inclusion de ressources à partir du module complémentaire Assets.](/help/assets/assets/aem-assets-add-on-include-assets.png)

### Nouvelles fonctionnalités de la vue Assets {#assets-view-features}

* **Import en bloc de ressources à partir de la source de données OneDrive** : les administrateurs et administratrices peuvent désormais [importer un grand nombre de ressources de OneDrive vers AEM Assets](/help/assets/bulk-import-assets-view.md#onedrive-developer-application). La liste mise à jour des sources de données prises en charge pour l’import en bloc comprend Azure, AWS, Google Cloud, Dropbox et OneDrive.

  ![Affectation d’un formulaire de métadonnées à un dossier.](/help/assets/assets/bulk-import-source-details-onedrive.png)

* **Prise en charge des droits inter-organisations pour les bibliothèques** : Experience Manager Assets vous permet désormais de configurer l’accès aux bibliothèques Creative Cloud dans une autre organisation IMS. Cela permet d’accéder plus facilement aux derniers workflows inter-produits entre Creative Cloud et Experience Manager et réduit le temps et les efforts pour les personnes responsables de la création.

### Fonctionnalités de pré-version disponibles dans [!DNL Experience Manager Assets] {#prerelease-features-assets}

* **Dynamic Media**: [Prise en charge du suivi multilégende et audio pour les vidéos dans Dynamic Media](/help/assets/dynamic-media/video.md#about-msma): vous pouvez désormais ajouter facilement plusieurs sous-titres et plusieurs pistes audio à une vidéo principale. Cette fonctionnalité signifie que vos vidéos sont accessibles à une audience mondiale. Vous pouvez personnaliser une seule vidéo principale publiée pour une audience mondiale dans plusieurs langues et respecter les directives d’accessibilité pour différentes régions géographiques. Les auteurs peuvent également gérer les sous-titres et les pistes audio à partir d’un seul onglet de l’interface utilisateur.

  ![Onglet Sous-titres et suivi audio de la page Propriétés d’une ressource vidéo sélectionnée.](/help/release-notes/assets/msma-aem-cs.png)*Onglet Sous-titres et suivi audio de la page Propriétés d’une ressource vidéo sélectionnée.*

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Nouvelles fonctionnalités de [!DNL Experience Manager Forms] {#forms-features}

* **[Propriétés personnalisées pour les formulaires adaptatifs](/help/forms/template-editor-core-components.md#add-a-custom-group-name-in-the-policy-of-template-editor)** : vous pouvez associer des attributs personnalisés (paires clé-valeur) à un modèle de formulaire ou à un composant de formulaires adaptatifs pour permettre aux personnes qui développent des formulaires de fournir des comportements de formulaire dynamiques qui s’adaptent en fonction des valeurs de ces attributs personnalisés. Par exemple, les développeurs et développeuses peuvent concevoir différents rendus d’un composant de formulaires découplés sur des plateformes mobiles, de bureau ou web, en fonction des valeurs des attributs personnalisés, améliorant ainsi considérablement l’expérience client sur un large éventail d’appareils.

* **Thèmes et modèles** : lancez le processus de création de formulaires grâce à nos nouveaux thèmes et modèles, conçus pour permettre aux personnes chargées de la création de formulaires de s’épanouir, qu’elles soient novices ou expérimentées. Créés en toute simplicité à l’aide des composants principaux des formulaires adaptatifs, ces thèmes et modèles soigneusement choisis vous permettent de commencer rapidement à créer des formulaires pour des cas d’utilisation courants.

  ![Modèles prêts à l’emploi.](/help/forms/assets/form-templates-ootb.png)


### Programme d’adoption précoce {#forms-early-adopter}

* **[Protégez vos documents avec les API DocAssurance (qui font partie des API de communication)](/help/forms/aem-forms-cloud-service-communications-introduction.md#document-assurance-doc-assurance)** : les API DocAssurance vous permettent de protéger les informations sensibles en signant et en chiffrant les documents. Grâce au chiffrement, le contenu d’un document est transformé en un format illisible, ce qui garantit que seules les personnes autorisées peuvent y accéder. Cette couche renforcée de protection protège non seulement les données précieuses des yeux non autorisés, mais offre également une certaine tranquillité d’esprit. Les API Signature permettent à votre entreprise de garantir la sécurité et la confidentialité des documents Adobe PDF qu’elle diffuse et reçoit. Ce service utilise les signatures numériques et la certification pour s’assurer que seules les personnes destinataires prévues peuvent modifier les documents.

  Vous pouvez écrire à `aem-forms-ea@adobe.com` depuis votre adresse e-mail officielle pour rejoindre le programme d’adoption précoce et demander l’accès à la fonctionnalité.

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### Règles de filtre de trafic, y compris les règles WAF {#traffic-filter-rules-waf}

[Filtrez le trafic sur le réseau CDN géré par Adobe](/help/security/traffic-filter-rules-including-waf.md) en déclarant des règles correspondant au trafic du site web par des propriétés, y compris l’URL, l’adresse IP et l’agent utilisateur, ou en définissant des limites de taux de trafic personnalisées pour se protéger des attaques DoS. La clientèle peut également acquérir sous licence un ensemble de règles WAF (Web Application Firewall) avancées afin d’obtenir une protection supplémentaire contre les menaces de sites web complexes.

Nous vous encourageons à vous familiariser avec les règles de filtrage du trafic en [suivant un tutoriel](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/security/traffic-filter-and-waf-rules/overview.html?lang=fr). Il vous guide tout au long des étapes nécessaires pour configurer un nouveau pipeline de configuration Cloud Manager, déclarer des règles dans un fichier de configuration et analyser les journaux de réseau CDN à la recherche de trafic malveillant.

Les règles de filtrage du trafic sont désormais disponibles dans les environnements de développement, avec un déploiement progressif dans les environnements d’évaluation et de production en novembre. Vous pouvez demander un accès anticipé à l’évaluation et la production en envoyant un courrier électronique à **aemcs-waf-adopter@adobe.com**.

Les règles de filtrage du trafic WAF avancées peuvent être autorisées au cours de l’année via les offres Sécurité renforcée ou Protection WAF-DDoS.

## Cloud Manager {#cloud-manager}

Vous trouverez la liste complète des versions mensuelles de Cloud Manager [ici](/help/implementing/cloud-manager/release-notes/current.md).

## Outils de migration {#migration-tools}

Vous trouverez une liste complète des versions des outils de migration [ici](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
