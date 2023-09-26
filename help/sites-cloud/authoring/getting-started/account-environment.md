---
title: Configuration de votre environnement de compte
description: Adobe Experience Manager (AEM) vous permet de configurer votre compte et certains aspects de l’environnement de création.
exl-id: 1b948f0b-85b9-478a-8b7e-61495c1d57b6
source-git-commit: 78ead5f15c2613d9c3bed3025b43423a66805c59
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 46%

---

# Configuration de votre environnement de compte {#configuring-your-account-environment}

Adobe Experience Manager (AEM) vous permet de configurer votre compte et certains aspects de l’environnement de création.

Grâce à l’option [Utilisateur](#user-settings) dans l’[en-tête](/help/sites-cloud/authoring/getting-started/basic-handling.md#the-header) et à la boîte de dialogue associée [Mes préférences](#my-preferences), vous pouvez modifier vos options utilisateur.

Accédez tout d’abord à l’option [Utilisateur](#user-settings) dans l’en-tête.

## Paramètres utilisateur {#user-settings}

La variable **Utilisateur** La boîte de dialogue paramètres vous donne accès aux options suivantes :

* Se faire passer pour
   * La fonction Se faire passer pour permet à un utilisateur de travailler au nom d’un autre. <!--With the [Impersonate as](/help/sites-administering/security.md#impersonating-another-user) functionality, a user can work on behalf of another user.-->
* Profil
   * Il offre un lien pratique vers vos paramètres utilisateur. <!--Offers a convenient link to your [user settings](/help/sites-administering/security.md))-->
* [Mes préférences](#my-preferences)
   * Spécifiez les différents paramètres uniques à votre utilisateur.

![Paramètres utilisateur](/help/sites-cloud/authoring/assets/user-settings.png)

### Mes préférences {#my-preferences}

La variable **Mes préférences** La boîte de dialogue est accessible à l’aide de la fonction [Utilisateur](#user-settings) dans l’en-tête.

Chaque utilisateur peut définir ses propriétés préférées.

![Mes préférences](/help/sites-cloud/authoring/assets/user-preferences.png)

* **Langue**

  Cette option définit la langue à utiliser pour l’interface utilisateur de l’environnement de création. Sélectionnez la langue souhaitée dans la liste disponible.

* **Gestion des fenêtres**

  Cela définit le comportement ou l’ouverture des fenêtres. Vous avez le choix entre :

   * **Fenêtres multiples** (Par défaut)

      * Les pages s’ouvrent dans une nouvelle fenêtre.

   * **Une seule fenêtre**

      * Les pages s’ouvrent dans la fenêtre active.

* **Afficher les actions de bureau pour Assets**

  Cette option nécessite l’utilisation de l’appli de bureau AEM.

* **Couleur de l’annotation**

  Cette option définit la couleur par défaut utilisée lors de la création d’annotations.

   * Cliquez sur le bloc de couleur pour ouvrir le sélecteur d’échantillon afin de sélectionner une couleur.
   * Vous pouvez également saisir le code hexadécimal de la couleur désirée dans le champ.

* **Présentation de la date relative**

  Pour améliorer la lisibilité, AEM effectue le rendu des dates au cours des sept derniers jours sous forme de dates relatives (par exemple, il y a trois jours) et des dates plus anciennes sous forme de dates exactes (par exemple, 20 mars 2017).

  Cette option définit la manière dont les dates sont affichées dans le système. Les options suivantes sont disponibles :

   * **Toujours afficher la date exacte** : la date exacte est toujours affichée (ce n’est jamais une date relative).
   * **1 jour** : la date relative s’affiche pour les dates correspondant au jour même ; dans le cas contraire, une date exacte est affichée.
   * **7 jours (par défaut)** : la date relative s’affiche pour les dates parmi les sept derniers jours ; dans le cas contraire, une date exacte est affichée.
   * **1 mois** : la date relative s’affiche pour les dates correspondant au dernier mois ; dans le cas contraire, une date exacte est affichée.
   * **1 an** : la date relative s’affiche pour les dates correspondant à la dernière année ; dans le cas contraire, une date exacte est affichée.
   * **Toujours afficher la date relative** : les dates exactes ne sont jamais affichées, seules les dates relatives le sont.

* **Activer les raccourcis**

  AEM prend en charge divers raccourcis clavier qui rendent la création plus efficace.

   * [Raccourcis clavier lors de la modification de pages](/help/sites-cloud/authoring/fundamentals/keyboard-shortcuts.md)
   * [Raccourcis clavier pour les consoles](/help/sites-cloud/authoring/getting-started/keyboard-shortcuts.md)

  Cette option active les raccourcis clavier. Par défaut, elles sont activées, mais peuvent être désactivées, par exemple si un utilisateur a certaines exigences d’accessibilité.

* **Activer la page d’accueil des ressources**

  Cette option n’est disponible que si l’administrateur système a activé l’expérience de page d’accueil des ressources pour l’ensemble de l’entreprise.

* **Configuration Stock**

  Cette option vous permet de définir la configuration Adobe Stock souhaitée. Elle n’est disponible que si l’administrateur système a activé [Intégration d’Adobe Stock](/help/assets/aem-assets-adobe-stock.md).
