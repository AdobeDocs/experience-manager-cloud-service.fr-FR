---
title: Différences de fonctionnalités entre formulaires HTML5 et formulaires PDF
description: Découvrez les différences de fonctionnalités entre les formulaires HTML5 et les formulaires PDF.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
docset: aem65
feature: HTML5 Forms,Mobile Forms
exl-id: 3150f95f-7150-4eee-b5a9-121422dec2a1
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: 22aeedaaf4171ad295199a989e659b6bf5ce9834
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 94%

---

# Différences de fonctionnalités entre formulaires HTML5 et formulaires PDF {#feature-differentiation-between-html-forms-and-pdf-forms}

<span class="preview"> La fonctionnalité Forms d’HTML5 est proposée dans le cadre du programme d’accès anticipé. Pour demander l’accès, envoyez un e-mail à l’adresse aem-forms-ea@adobe.com à partir de votre ID d’e-mail officiel (professionnel).
</span>

Le tableau suivant indique les fonctionnalités prises en charge par les formulaires HTML5 et les formulaires PDF :

<table>
 <tbody>
  <tr>
   <th>Fonctionnalité</th>
   <th>Formulaires HTML5</th>
   <th>PDF</th>
  </tr>
  <tr>
   <td>Codes-barres<br /> </td>
   <td>Non disponible au niveau de l’interface utilisateur. </td>
   <td>Pris en charge</td>
  </tr>
  <tr>
   <td>Champ de signature<br /> </td>
   <td>Les <strong>signatures numériques</strong> ne sont pas prises en charge mais le nouveau champ <strong>Signature tactile</strong> a été ajouté pour les signatures apposées. Il est possible de griffonner sa signature sur le formulaire en utilisant le champ <strong>Signature tactile</strong>. La signature est enregistrée sur le formulaire en tant qu’image. Vous pouvez enregistrer des informations de géolocalisation dans le champ <strong>Signature tactile</strong>.</td>
   <td>Champ de signature disponible pour les <strong>Signatures numériques</strong>.</td>
  </tr>
  <tr>
   <td>Fusion de données</td>
   <td>Pris en charge</td>
   <td>Pris en charge</td>
  </tr>
  <tr>
   <td>Images</td>
   <td>Le schéma URI des données sert à afficher des images. Toutes les versions modernes des navigateurs prennent en charge ce schéma, mais il existe des différences dans la gamme de formats d’image pris en charge par chaque navigateur.<br /> </td>
   <td>Les formats .gif, .png, .jpeg, .bmp et .tiff sont pris en charge.</td>
  </tr>
  <tr>
   <td>Pagination<br /> </td>
   <td><p>Un formulaire HTML5 est divisé en panneaux et en cadres pour lui donner une apparence similaire aux formulaires PDF. La taille de la page est calculée dynamiquement. Si vous supprimez ou marquez comme masqué tout le contenu d’une page dans un formulaire HTML5, la page vierge est masquée. Aucun espace vide (espace) n’est affiché entre les pages au-dessus et en dessous de la page vierge.</p> <p>Si la fusion de données ou les scripts ajoutent du contenu à une page, la longueur de la page s’agrandit pour s’adapter au nouveau contenu. Aucune nouvelle page n’est ajoutée au formulaire pour s’adapter au nouveau contenu. </p> <p><strong>Remarque :</strong> si vous supprimez ou marquez comme masqué tout le contenu d’une page de formulaire HTML5, la page vierge (espace) reste visible entre la première et la deuxième page mais pas entre les autres pages.</p> </td>
   <td>La pagination des documents PDF dépend du contenu des données fusionnées ou du contenu de l’utilisateur : le nombre de pages est augmenté/réduit en conséquence.</td>
  </tr>
  <tr>
   <td>En-têtes/pieds de page </td>
   <td>Pris en charge. <br /> <br /> Les formulaires mobiles HTML5 ne prenant pas en charge les sauts de page, les en-têtes et les pieds de page n’apparaissent qu’une seule fois. Vous pouvez toutefois les configurer dans la disposition pour qu’ils apparaissent à plusieurs endroits dans l’aperçu des formulaires mobiles.<br /> </td>
   <td>Pris en charge.</td>
  </tr>
  <tr>
   <td>Widgets personnalisés</td>
   <td>Vous pouvez personnaliser les widgets pour améliorer l’expérience client sur les appareils mobiles.<br /> </td>
   <td>Tous les widgets sont verrouillés et aucun widget personnalisé ne peut être ajouté.<br /> </td>
  </tr>
  <tr>
   <td>API de script XFA</td>
   <td>Prend en charge les éléments de scripts XFA les plus fréquemment utilisés. Pour obtenir une liste détaillée des éléments pris en charge, consultez <a href="/help/forms/scripting-support.md">Prise en charge des scripts</a>.</td>
   <td>Prend en charge tous les éléments de script XFA.</td>
  </tr>
  <tr>
   <td>API des scripts Acrobat </td>
   <td>Les formulaires HTML5 prennent en charge la plupart des API couramment utilisées. Pour plus d’informations, consultez la section <a href="/help/forms/scripting-support.md">Prise en charge des scripts</a>.</td>
   <td>Si le fichier PDF est ouvert dans Acrobat ou Reader, il prend également en charge toutes les API de script fournies par Acrobat.</td>
  </tr>
  <tr>
   <td>Prise en charge des langues écrites de droite à gauche </td>
   <td>Pris en charge</td>
   <td>Pris en charge</td>
  </tr>
 </tbody>
</table>

<!--Follow the best practices to enable a form template for HTML5 renditions and ensure that the behavior and appearance of HTML5 forms and XFA-based PDF is consistent. For detailed list of best practices, see [Best practices to design an HTML5 form.](/help/forms/using/best-practices-design-html5-forms.md)-->
