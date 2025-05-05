---
title: Comment télécharger et installer Forms Designer pour créer des modèles de documents d’enregistrement ?
description: Utilisez Forms Designer pour créer des modèles XDP et de PDF Form qui servent de modèle pour un document d’enregistrement.
keywords: Installation de Designer, installation de Forms Designer, configuration requise pour l’installation de Forms Designer
feature: Adaptive Forms, Forms Designer
role: Admin, Developer, User
exl-id: d6f1cb21-c48b-406d-8d47-482d7a1b4cc3
source-git-commit: 527c9944929c28a0ef7f3e617ef6185bfed0d536
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 68%

---

# Téléchargement et installation de Forms Designer {#installing-and-configuring-designer}

| Version | Lien de l’article |
| -------- | ---------------------------- |
| AEM as a Cloud Service | Cet article |
| AEM 6.5 | [Cliquez ici](https://experienceleague.adobe.com/docs/experience-manager-65/forms/install-aem-forms/jee-installation/installing-configuring-designer.html?lang=fr) |

Designer est un outil de conception de formulaires graphiques de type pointer-cliquer qui simplifie la création de modèles de formulaires XDP et PDF. Vous pouvez concevoir un modèle de formulaire, définir sa logique et respecter des exigences légales strictes. Un formulaire XDP et PDF servent de modèle de document d’enregistrement dans un formulaire adaptatif. Ces modèles de formulaires sont différents des [modèles de formulaire adaptatif](template-editor.md).

## Conditions préalables {#pre-requisites}

Pour installer la dernière version d’AEM Forms Designer 64 bits ou 32 bits, vous avez besoin des logiciels et du matériel minimal suivants pour installer et configurer Designer :

+++ Designer 64 bits (recommandé)

* [!DNL Microsoft® Windows® 2016 Server] ou [!DNL Microsoft® Windows® 2019 Server], et [!DNL Microsoft® Windows® 10]
* 2 Go de RAM au minimum
* 20 Go d’espace disque
* Mémoire graphique - 128 Mo de GPU (256 Mo est recommandé)
* 2,35 Go d’espace disponible sur le disque dur
* Résolution d’écran de 1 024 x 768 pixels ou plus
* Accélération matérielle de la vidéo (facultatif)
* Acrobat Pro DC, Acrobat Standard DC ou Adobe Acrobat Reader DC.
* Droits d’administrateur pour l’installation de Designer.
* [!DNL Microsoft® Visual C++ 2019] (VC 14.28 ou version ultérieure) Exécution 64 bits

+++

+++ Designer 32 bits

* [!DNL Microsoft® Windows® 2016 Server], [!DNL Microsoft® Windows® 2019 Server] ou [!DNL Microsoft® Windows® 10]
* 1 Go de RAM pour un système d’exploitation 32 bits ou 2 Go de RAM pour un système d’exploitation 64 bits
* 16 Go d’espace disque pour un système d’exploitation 32 bits ou 20 Go d’espace disque pour un système d’exploitation 64 bits
* Mémoire graphique – 128 Mo de GPU (256 Mo recommandé)
* 2,35 Go d’espace disponible sur le disque dur
* Résolution d’écran de 1 024 x 768 pixels ou plus
* Accélération matérielle de la vidéo (facultatif)
* Acrobat Pro DC, Acrobat Standard DC ou Adobe Acrobat Reader DC.
* Droits d’administrateur pour l’installation de Designer.
* Microsoft® Visual C++ 2019 (VC 14.28 ou version ultérieure) Runtime 32 bits

+++

## Installation de Designer {#install-designer}

>[!NOTE]
>
> Avant d’installer la version 64 bits de Forms Designer, désinstallez la version 32 bits de Designer.

Pour installer Designer, procédez comme suit :

1. Téléchargez Designer à partir de [Distribution logicielle](https://experience.adobe.com/downloads).
1. Double-cliquez sur setup.exe pour exécuter le programme d’installation.
1. Continuez et fournissez vos détails sur l’écran Personnalisation.
1. Si vous acceptez les termes du contrat de licence, appuyez sur **[!UICONTROL Suivant]** pour continuer.
1. (Facultatif) Modifiez le chemin d’installation par défaut, si vous voulez installer Designer à l’emplacement de votre choix. Cliquez sur **[!UICONTROL Suivant]**.
1. Cliquez sur **[!UICONTROL Précédent]** pour modifier les préférences. Pour installer Designer, cliquez sur **[!UICONTROL Installer]**.
1. Cliquez sur **[!UICONTROL Terminer]** à la fin de l’installation.

## Voir également {#see-also}

* [Utiliser des polices personnalisées](/help/forms/use-custom-fonts.md)
* [Création d’un formulaire adaptatif autonome basé sur des composants principaux](/help/forms/creating-adaptive-form-core-components.md)
* [Créer ou ajouter un formulaire adaptatif à une page AEM Sites](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md)
* [Utilisation de Forms Designer pour créer des modèles de document d’enregistrement et des fragments de formulaire](/help/forms/use-forms-designer.md)


<!--

>[!MORELIKETHIS]
>
>* [Use Forms Designer to create Document of Record (DoR) templates and form fragments](/help/forms/use-forms-designer.md)

-->