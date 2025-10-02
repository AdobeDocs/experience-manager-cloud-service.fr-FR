---
title: Évaluation de l’intégrité des environnements de production et d’évaluation
description: Découvrez comment utiliser l’évaluation de l’intégrité Cloud Manager. Vous pouvez analyser les environnements AEM, exécuter et réviser des rapports, afficher les détails des problèmes, exporter des PDF et gérer les exécutions précédentes.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 5f9d53958076b77cd333a042003c83853594db87
workflow-type: tm+mt
source-wordcount: '1406'
ht-degree: 8%

---


# Évaluation de l’intégrité {#about-health-assessment}

L’évaluation de l’intégrité est une analyse automatisée et non intrusive des environnements de production et d’évaluation dans Cloud Manager, au sein d’AEM as a Cloud Service. Il évalue le contenu, le code et les configurations afin de détecter les antimodèles et les écarts par rapport aux bonnes pratiques, ce qui améliore la sécurité et les performances.

Le service d’évaluation de l’intégrité effectue les opérations suivantes :

* Analyse les environnements et met en évidence les goulots d’étranglement, les inefficacités et les risques.
* Analyse les structures de contenu, telles que les plans directeurs, les Live Copies et les configurations client.
* Détecte les dépendances obsolètes, y compris AEM SDK et les bibliothèques tierces.
* Signale les problèmes de qualité du code, tels que des annotations incorrectes et des modèles inefficaces.
* fournit des conseils pratiques dans les tableaux de bord (par exemple, le Centre de maintenance) ;
* Prend des mesures correctives proactives pour améliorer les performances du système.

Chaque exécution répertorie les problèmes par gravité, fournit des liens vers des conseils et des correctifs recommandés et prend en charge une exportation PDF du rapport. Vous pouvez utiliser la vue **Dernier rapport** pour l’état actuel et **Rapports précédents** pour comparer les exécutions.

Consultez également la section [&#x200B; Modèles d’évaluation de l’intégrité &#x200B;](#ha-patterns) pour obtenir des détails sur les définitions de règle et les mesures correctives.

## Accéder à la page Évaluation de l’intégrité {#access-health-assessment}

1. Connectez-vous à Cloud Manager à l’adresse [experiency.adobe.com](https://experience.adobe.com).
1. Dans la section **Accès rapide**, cliquez sur **Experience Manager**.
1. Dans le panneau de gauche, cliquez sur **Cloud Manager**.
1. Sélectionnez l’organisation de votre choix. L’image ci-dessous est fournie à titre d’illustration. Sélectionnez le nom de votre organisation.

   ![Sélection d’une organisation dans Cloud Manager](/help/implementing/cloud-manager/reports/assets/ha-org.png)

1. Sur la console **Mes programmes**, cliquez sur le programme pour lequel vous souhaitez afficher son rapport.

1. Effectuez l’une des opérations suivantes :
   * Dans la vignette **Environnements**, à droite du nom d’un environnement, cliquez sur ![icône représentant des points de suspension ou icône plus](https://spectrum.adobe.com/static/icons/ui_18/More.svg), puis choisissez **Évaluation de l’intégrité** dans le menu.

     ![Sélection de l’évaluation de l’intégrité dans le menu représentant des points de suspension de la carte Environnements](/help/implementing/cloud-manager/reports/assets/ha-myprograms-environments-card.png)

   * Dans le menu de gauche, sous **Services**, cliquez sur ![Icône Données](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Data_18_N.svg) **Environnements**. Sur la page Environnements, à droite d’un nom d’environnement, cliquez sur ![icône représentant des points de suspension ou icône plus](https://spectrum.adobe.com/static/icons/ui_18/More.svg), puis choisissez **Évaluation de l’intégrité** dans le menu.

     ![Sélection de l’évaluation de l’intégrité dans le menu représentant des points de suspension de la page Environnements](/help/implementing/cloud-manager/reports/assets/ha-environments-page.png)

## Exécution d’un nouveau rapport pour un environnement sélectionné {#run-report}

1. [Accédez à la page Évaluation de l’intégrité](#access-health-assessment).
1. Dans le coin supérieur droit de la page **Évaluation de l’intégrité**, confirmez l’environnement cible que vous êtes sur le point d’évaluer.

   Si l’environnement est incorrect, cliquez sur ![Chevron du menu déroulant ou du menu déroulant pour sélectionner un autre environnement](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ChevronDown_18_N.svg) afin de choisir l’environnement correct dans la liste.

1. Cliquez sur **Exécuter le rapport**.

   ![Cliquez sur le bouton Générer un nouveau rapport sur la page Évaluation de l’intégrité](/help/implementing/cloud-manager/reports/assets/ha-run-report.png)

   Tandis qu’un rapport s’exécute pour l’environnement sélectionné, la fonction **Exécuter le rapport** reste désactivée jusqu’à ce qu’elle se termine.

   ![Rapport en cours d’exécution](/help/implementing/cloud-manager/reports/assets/ha-running-report.png)

   Une fois le rapport terminé, il apparaît sur la page **Évaluation de l’intégrité**, dans la section **Dernier rapport**.

## Afficher le dernier rapport {#view-latest-report}

* Sur la page **Évaluation de l’intégrité**, consultez la section **Dernier rapport** pour obtenir les informations suivantes :

   * Résultats de la dernière exécution.
   * Date et heure d’exécution.
   * Nombre total d&#39;événements.
   * Points forts des principaux problèmes critiques.
   * Actions : **[Afficher les détails](#view-report-details)** ou **[Télécharger PDF](#download-pdf-report)** de tous les problèmes.

  ![Page d’évaluation la plus récente après la génération d’un nouveau rapport pour un environnement sélectionné](/help/implementing/cloud-manager/reports/assets/ha-latest-report-page.png)

### Afficher les derniers détails du rapport {#view-report-details}

* Sur la page **Évaluation de l’intégrité**, à droite du titre **Dernier rapport**, cliquez sur ![icône représentant des points de suspension ou icône plus](https://spectrum.adobe.com/static/icons/ui_18/More.svg), puis sur **Afficher les détails** ou **Télécharger**.

  L’option **Afficher les détails** vous indique ce qui suit :

   * Liste complète des problèmes.
   * Possibilité d’afficher les résultats et les descriptions des problèmes.
   * Possibilité d’afficher la documentation comportant des correctifs potentiels.

     ![Description des événements et recherche](/help/implementing/cloud-manager/reports/assets/ha-issue-descriptions-and-findings.png)

   * L’option **Télécharger** vous permet de télécharger des rapports d’événement individuels dans PDF.

     ![Télécharger le PDF des rapports d’événements individuels](/help/implementing/cloud-manager/reports/assets/ha-details-page-doc-links.png)


### Télécharger le PDF de l’intégralité du rapport {#download-pdf-report}

* Dans le coin supérieur droit de la page du rapport, cliquez sur **Télécharger**.

  Un fichier ZIP contenant des fichiers PDF pour tous les problèmes détectés dans ce rapport est généré.

  ![Télécharger le PDF de tous les problèmes rencontrés dans un rapport](/help/implementing/cloud-manager/reports/assets/ha-download-pdf.png)


## Consulter les rapports précédents {#review-past-reports}

Sur la page **Évaluation de l’intégrité**, consultez la section **Rapports précédents** pour obtenir les informations suivantes :

* Affichez les détails de tout rapport précédent.
* Affichez la date de chaque exécution.
* Téléchargez un PDF pour n’importe quel rapport.
* Triez par date, nombre d’événements ou environnement.

![Consulter les rapports précédents](/help/implementing/cloud-manager/reports/assets/ha-past-reports.png)

* À droite de l’en-tête **Rapports précédents**, cliquez sur ![Chevron du menu déroulant ou du menu déroulant pour sélectionner un autre environnement](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ChevronDown_18_N.svg) afin de trier les rapports précédents par date.
* À l’extrémité droite d’un rapport, cliquez sur ![icône représentant des points de suspension ou icône plus](https://spectrum.adobe.com/static/icons/ui_18/More.svg), puis sur **Afficher les détails** ou **Télécharger**.


## Modèles d’évaluation de l’intégrité {#ha-patterns}

Vous trouverez ci-dessous la liste complète des antimodèles et des problèmes détectés par l’évaluation de l’intégrité dans AEM as a Cloud Service. Le tableau regroupe les éléments en trois types : Analyse de contenu, Analyse de code et anti-modèles de l’optimiseur de Cloud Service, avec une explication pour chacun d’eux.

| Nom du motif | Catégorie | Type | Description | Impact | Correction automatique ? |
| --- | --- | --- | --- | --- | --- |
| Groupes AEM personnalisés avec ajouts directs d’utilisateurs | Sécurité | Analyse de contenu | Les utilisateurs sont ajoutés directement aux groupes AEM au lieu d’ajouter des groupes IMS en tant que membres. | La gestion des autorisations et la gouvernance de la sécurité peuvent devenir complexes. [Prise en charge IMS](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/security/ims-support) | Non |
| Nœud de contenu JCR manquant dans les pages | Structure du référentiel | Analyse de contenu | Nœud `jcr:content` manquant dans la page. | Limites fonctionnelles dans Experience Manager as a Cloud Service. [Détection de motifs - ACV](https://experienceleague.adobe.com/fr/docs/experience-manager-pattern-detection/table-of-contents/acv) | Non |
| Type de ressource Sling manquant dans les pages | Structure du référentiel | Analyse de contenu | `sling:resourceType` manquant dans la page. | Limites fonctionnelles dans Experience Manager as a Cloud Service. [Détection de motifs - ACV](https://experienceleague.adobe.com/fr/docs/experience-manager-pattern-detection/table-of-contents/acv) | Non |
| Pages avec nombre de nœuds excessif | Performance | Analyse de contenu | Les pages contiennent un grand nombre de nœuds dans leur structure. | Temps de chargement de page lent et mauvaise expérience utilisateur. [Détection de motifs - PCX](https://experienceleague.adobe.com/fr/docs/experience-manager-pattern-detection/table-of-contents/pcx) | Non |
| Instances de workflow en cours d’exécution excessive | Performance | Analyse de contenu | Trop d’instances de workflows en cours d’exécution. | Dégradation des performances globales du système. [Tâches de maintenance](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/operations/maintenance) | Non |
| Instances de workflow terminées et non purgées | Performance | Analyse de contenu | Les anciennes instances de workflow terminées ne sont pas purgées. | Réduction de l&#39;efficacité du système et augmentation des coûts de stockage. [Tâches de maintenance](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/operations/maintenance) | Non |
| Statistiques d’utilisation des fragments de contenu | Statistiques | Analyse de contenu | Effectue le suivi du nombre de fragments de contenu utilisés. | S/O | S/O |
| Statistiques d’utilisation du modèle de fragment de contenu | Statistiques | Analyse de contenu | Effectue le suivi du nombre de modèles de fragment de contenu utilisés. | S/O | S/O |
| MSM - Grand nombre de plans directeurs | Statistiques | Analyse de contenu | Effectue le suivi du nombre de plans directeurs. | Cela peut rendre la gestion plus complexe et la gouvernance du contenu plus difficile. | S/O |
| Pages MSM par plan directeur | Statistiques | Analyse de contenu | Suit le nombre de pages par plan directeur. | Cela peut rendre la gestion plus complexe et la gouvernance du contenu plus difficile. | S/O |
| Live Copies excessives de MSM | Statistiques | Analyse de contenu | Suit le nombre de Live Copies. | Cela peut entraîner des problèmes de performances lors des déploiements et compliquer la synchronisation du contenu. | S/O |
| Nombre excessif de Live Copies MSM par plan directeur | Statistiques | Analyse de contenu | Suit le nombre de Live Copies par plan directeur. | Cela peut entraîner des problèmes de performances lors des déploiements et compliquer la synchronisation du contenu. | S/O |
| Nombre d’Assets | Statistiques | Analyse de contenu | Effectue le suivi du nombre de ressources. | S/O | S/O |
| Nombre de sites | Statistiques | Analyse de contenu | Effectue le suivi du nombre de sites. | S/O | S/O |
| Nombre de Forms | Statistiques | Analyse de contenu | Effectue le suivi du nombre de formulaires. | S/O | S/O |
| Fragments de formulaire | Statistiques | Analyse de contenu | Effectue le suivi du nombre de fragments de formulaire. | S/O | S/O |
| Communications d’interaction | Statistiques | Analyse de contenu | Effectue le suivi du nombre d’interactions de communication de formulaire. | S/O | S/O |
| FDM | Statistiques | Analyse de contenu | Effectue le suivi du nombre de modèles de données de formulaire. | S/O | S/O |
| Dépendances obsolètes | Dépendances | Analyse du code | Met en évidence les dépendances obsolètes dans le référentiel client. | Incompatibilité avec les nouvelles versions d’AEM ; vulnérabilités de sécurité potentielles. | Non |
| Incompatibilité de versions entre AEM SDK | Dépendances | Analyse du code | Versions antérieures à (n-2) par rapport à la version de l’environnement Cloud Manager. | Cela peut entraîner des erreurs de version dans Cloud Manager et des problèmes dans les environnements de développement locaux. | Non |
| Dépendance de base Mockito obsolète | Dépendances | Analyse du code | Les versions inférieures à 4.x.x sont considérées comme obsolètes pour AEM as a Cloud Service. | Cela peut entraîner des erreurs de version dans Cloud Manager et des problèmes dans les environnements de développement locaux. | Non |
| Annotations non prises en charge | Dépendances | Analyse du code | Annotations non prises en charge dans le référentiel Cloud Manager du client. | Pannes d’application potentielles et baisse des performances. | Non |
| Annotation @Inject dans les modèles Sling | Dépendances | Analyse du code | Annotation `@Inject` obsolète. | Performances d&#39;application réduites en raison de la surcharge de résolution d&#39;injection. | Non |
| Requêtes HTTP sortantes | Performance | Anti-motifs de Cloud Service Optimizer | Utilisation problématique dans le contexte de la demande, délais d’expiration élevés ou connexion impossible. | Dégradation des performances globales du système et pannes possibles. | Oui |
| Requêtes lentes | Performance | Anti-motifs de Cloud Service Optimizer | Requêtes lentes dans le code client. | Performances système dégradées et délais d’expiration potentiels. | Oui |

### Catégories {#ha-patterns-categories}

| Catégorie | Description |
| --- | --- |
| Sécurité | Modèles liés aux pratiques de sécurité, à la gestion des utilisateurs et au contrôle d’accès. |
| Performance | Modèles qui affectent les performances des applications et du système. |
| Structure du référentiel | Modèles liés à l’organisation et à la structure du référentiel JCR. |
| Dépendances | Modèles liés aux dépendances de code et à la gestion des versions. |
| Statistiques | Modèles qui représentent des statistiques et des mesures d’utilisation. |



