---
title: Enregistrer un formulaire HTML5 en tant que brouillon
description: Enregistrez un formulaire HTML5 comme brouillon et reprenez le remplissage du formulaire ultérieurement.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
discoiquuid: 445e24af-cd1a-414d-bd01-9feb6631bbef
feature: HTML5 Forms,Mobile Forms
exl-id: a9879445-d626-4279-8a95-a9009294b483
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
hide: true
hidefromtoc: true
source-git-commit: 81a6c2b942df0e72a0b7d359f29c615a44640396
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 84%

---


# Enregistrer un formulaire HTML5 en tant que brouillon {#saving-an-html-form-as-a-draft}

<span class="preview"> La fonctionnalité Forms d’HTML5 est proposée dans le cadre du programme d’accès anticipé. Pour demander l’accès, envoyez un e-mail à l’adresse aem-forms-ea@adobe.com à partir de votre ID d’e-mail officiel (professionnel).
</span>

Vous pouvez enregistrer un formulaire HTML5 comme brouillon et reprendre le remplissage du formulaire ultérieurement. Le portail Formulaires permet aux utilisateurs et aux utilisatrices d’enregistrer et de restaurer un formulaire HTML5. Pour activer la fonctionnalité d’enregistrement en tant que brouillon, ajoutez les configurations suivantes au nœud de profil :

## Profil personnalisé permettant d’activer la fonctionnalité Enregistrer en tant que brouillon {#custom-profile-to-allow-save-as-draft-feature}

En standard, AEM Forms fournit un profil **Enregistrer en tant que brouillon**. Vous pouvez effectuer le rendu d’un formulaire avec le profil Enregistrer en tant que brouillon pour activer la fonctionnalité de brouillon pour un formulaire HTML5. Vous pouvez spécifier le profil de rendu HTML pour un formulaire dans **Forms Manager**.

Pour activer la fonctionnalité Enregistrer en tant que brouillon et l’appliquer à votre [profil personnalisé](/help/forms/custom-profile.md) existant, ajoutez les configurations suivantes à votre nœud de profil :

<table>
 <tbody>
  <tr>
   <td><strong>Nom de la propriété</strong></td>
   <td><strong>Type</strong></td>
   <td><strong>Valeur</strong></td>
   <td><strong>Description</strong></td>
  </tr>
  <tr>
   <td>mfAllowFPDraft</td>
   <td>Chaîne</td>
   <td>true</td>
   <td><p>Active la fonctionnalité Enregistrer en tant que brouillon</p> <p>pour ce profil.</p> </td>
  </tr>
  <tr>
   <td>mfAllowAttachments</td>
   <td>Chaîne</td>
   <td>true</td>
   <td><p>Autorise le chargement de pièces jointes</p> <p>avec ce profil.</p> </td>
  </tr>
 </tbody>
</table>

## Stockage et liste des brouillons {#drafts-storage-and-listing}

Après l’activation de la fonctionnalité Enregistrer en tant que brouillon pour un formulaire, lorsque le formulaire est enregistré, il est répertorié dans le composant Drafts and Submission. Vous pouvez extraire le formulaire enregistré et commencer son remplissage depuis le composant Drafts and Submissions.

Pour activer les listes de formulaires du composant Brouillons et Envois, ajoutez la propriété suivante au nœud de profil :

<table>
 <tbody>
  <tr>
   <td><strong>Nom de la propriété</strong></td>
   <td><strong>Type</strong></td>
   <td><strong>Valeur</strong></td>
   <td><strong>Description</strong></td>
  </tr>
  <tr>
   <td>fp.enablePortalSubmit</td>
   <td>Chaîne</td>
   <td>true</td>
   <td>Pour que les brouillons et les formulaires soient répertoriés dans le <br /> composant Brouillons et envois du portail Formulaires après envoi</td>
  </tr>
 </tbody>
</table>

Par défaut, AEM Forms stocke les données d’utilisateur associées au brouillon et à l’envoi d’un formulaire dans le nœud /content/forms/fp de l’instance de publication. Vous pouvez ajouter votre fournisseur personnalisé de stockage. Pour plus de détails, consultez [Stockage personnalisé pour le composant Drafts and Submissions](https://experienceleague.adobe.com/fr/docs/experience-manager-65/content/forms/use-forms-portal/adding-custom-storage-provider-forms).
