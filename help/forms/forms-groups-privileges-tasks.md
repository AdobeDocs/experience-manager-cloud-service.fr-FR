---
title: Quels groupes d’utilisateurs sont prêts à l’emploi dans AEM Forms as a Cloud Service ?
description: Liste des groupes d’utilisateurs prêts à l’emploi et des autorisations attribuées à chaque groupe
role: Admin, Developer, User
feature: Adaptive Forms
exl-id: bd66ce92-14d9-47fe-b5d3-022e3e468d25
source-git-commit: 8f39bffd07e3b4e88bfa200fec51572e952ac837
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 62%

---

# Groupes et autorisations {#aem-forms-on-osgi-groups-and-privileges}

| Version | Lien de l’article |
| -------- | ---------------------------- |
| AEM 6.5 | [Cliquez ici](https://experienceleague.adobe.com/docs/experience-manager-65/forms/manage-administer-aem-forms/forms-groups-privileges-tasks.html?lang=fr) |
| AEM as a Cloud Service | Cet article |

Vous pouvez [créer des groupes](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/aem-users-groups-and-permissions.html?lang=fr#accessing) et affecter des politiques et des [utilisateurs](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/aem-users-groups-and-permissions.html?lang=fr#accessing) aux groupes. Ces politiques contrôlent les autorisations des utilisateurs qui font partie du groupe.

Une fois que vous avez configuré [!DNL AEM Forms] as a Cloud Service, les groupes répertoriés dans le tableau ci-dessous, tels que [!DNL forms-users] et forms-power-user, sont automatiquement disponibles pour l’affectation :

<table>
 <tbody>
  <tr>
   <td>Groupe</td> 
   <td>Autorisations</td> 
  </tr>
  <tr>
   <td>[!DNL forms-users] <sup>[1]</sup></td> 
   <td>
    <ul> 
     <li>Créer, prévisualiser, publier et soumettre des formulaires adaptatifs</li> 
    <!-- <li>Create, preview, and publish interactive communications and document fragments</li> -->
     <li>Charger les ressources vers une instance AEM</li> 
     <li>Créer des thèmes</li> 
    </ul> </td> 
  </tr>
  <!-- <tr>
   <td>[!DNL forms-power-user]</td> 
   <td>
    <ul> 
     <li>Create, preview, publish, and submit Adaptive Forms</li> 
     <li>Create, preview, and publish interactive communications and document fragments</li> 
     <li>Create scripts for Adaptive Forms using code editor</li> 
     <li>Upload assets including scripts</li> 
     <li>Create themes</li> 
     <li>Import packages containing XDP</li> 
    </ul> </td> 
  </tr>
 <tr>
   <td>forms-submission-reviewers</td> 
   <td>
    <ul> 
     <li>Review submissions</li> 
     <li>Approve or reject submissions</li> 
    </ul> </td> 
  </tr> -->
  <tr>
   <td>[!DNL template-authors] <sup>[2]</sup></td> 
   <td>
    <ul> 
     <li>Création et prévisualisation de modèles de formulaires adaptatifs <!-- or interactive communications --></li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><p>[!DNL fdm-authors]</p> </td> 
   <td>
    <ul> 
     <li>Création et modification dʼun modèle de données de formulaire</li> 
    </ul> </td> 
  </tr>
  <!-- <tr>
   <td>cm-agent-users</td> 
   <td>
    <ul> 
     <li>Access Correspondence Management letters or interactive communications using Agent UI</li> 
    </ul> </td> 
  </tr> --> 
  <!-- <tr>
   <td><p>workflow-editors</p> </td> 
   <td>
    <ul> -->
    <!-- <li>Create an inbox application</li>  -->
    <!-- <li>Create a workflow model</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>[!DNL workflow-users]</td> 
   <td>
    <ul> 
     <li>Use AEM inbox applications<br /> -->
     <!-- 
     <strong>Note: </strong>You must have cm-agent-users and [!DNL workflow-users] group assignments to access Interactive Communications Agent UI in AEM inbox.</li>  -->
    </ul> </td> 
  </tr>
  <tr>
   <td>[!DNL fd-administrators]</td> 
   <td>
    <ul> 
     <!-- <li>Configure PDF Generator</li> --> 
     <!-- <li>Configure Watched folder</li> -->
     <li>Gestion des applications de workflow</li> 
    </ul> </td> 
  </tr>
 </tbody>
</table>

## Applicabilité et cas d’utilisation

### Assurance

## AEM Forms est-il de niveau entreprise pour les opérations d’assurance ?

Oui. AEM Forms fournit des fonctionnalités d’entreprise telles que le contrôle d’accès en fonction du rôle, les pistes d’audit, l’orchestration des workflows, la génération de documents et la flexibilité de déploiement, qui sont requises pour des opérations d’assurance à grande échelle.

## Voir également

* [Intégration à un environnement Cloud Service](/help/forms/setup-forms-cloud-service.md)
* [Configurer un environnement de développement local](/help/forms/setup-local-development-environment.md)
* [Migration d’AEM 6.5 Forms vers Cloud Service](/help/forms/migrate-to-forms-as-a-cloud-service.md)
* [Création d’un formulaire adaptatif autonome](/help/forms/creating-adaptive-form-core-components.md)
* [Ajout d’un formulaire adaptatif à une page AEM Sites](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md)

<!--

>[!MORELIKETHIS]
>
>* [Use AEM Forms workflow for business process automation](/help/forms/aem-forms-workflow.md)

-->
