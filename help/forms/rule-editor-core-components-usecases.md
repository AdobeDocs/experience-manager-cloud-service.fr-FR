---
title: Cet article décrit divers cas d’utilisation d’un éditeur de règles dans un formulaire adaptatif basé sur les composants principaux.
description: Cet article décrit divers cas d’utilisation d’un éditeur de règles dans un formulaire adaptatif basé sur des composants principaux.
feature: Adaptive Forms, Core Components
role: User, Developer
level: Beginner, Intermediate
exl-id: 8191e113-f768-4b1e-a191-e3c722f19054
source-git-commit: e10451553692b6ad957421783e176409b36b642b
workflow-type: tm+mt
source-wordcount: '1561'
ht-degree: 42%

---

# Différents cas d’utilisation de l’éditeur de règles

Cet article fournit des exemples détaillés d’éditeur de règles pour un formulaire adaptatif basé sur des composants principaux, ce qui fournit des informations sur sa mise en œuvre correcte pour différents scénarios. L’éditeur de règles permet aux développeurs et développeuses de définir et de gérer la logique contrôlant le comportement des formulaires.
Examinons à présent les différentes mises en œuvre d’un éditeur de règles.

## Définir le focus sur un autre panneau sur le bouton cliquer si le premier panneau est valide

<span class="preview"> Il s’agit d’une fonctionnalité de version préliminaire accessible par le biais de notre [canal de version préliminaire](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html?lang=fr#new-features). </span>

L’éditeur de règles vous permet de valider des mises en page de panneau, telles que des onglets horizontaux, verticaux, des accordéons ou un clic sur un bouton de l’assistant, puis de définir la sélection sur un objet de formulaire dans un autre panneau. Vous pouvez utiliser cette fonctionnalité pour améliorer la navigation dans les formulaires et l’expérience utilisateur.

Imaginez un formulaire de demande à plusieurs étapes utilisant une disposition Assistant. Vous devez terminer le panneau `Personal Information` avant de passer à `Employment Details`. Lorsque vous cliquez sur le bouton `Next`, l’éditeur de règles valide le panneau `Personal Information`. Si tous les champs obligatoires sont remplis correctement, le formulaire déplace automatiquement le focus vers le panneau `Employment Details`. Dans le cas contraire, un message d’erreur s’affiche, invitant les utilisateurs à renseigner les champs manquants.

Vous pouvez créer une règle sur le bouton `Next` pour valider le premier panneau :

![Règle pour le bouton Suivant](/help/forms/assets/next-rule.png){width=50%}

Lorsque vous cliquez sur le bouton **Suivant**, le panneau **Informations personnelles** est validé. Si les informations saisies sont correctes, le focus se déplace vers le panneau **Sécurité du compte**. Dans le cas contraire, un message d’erreur vous invite à renseigner les informations manquantes.

>[!VIDEO](https://video.tv.adobe.com/v/3457767)


## Navigation dans les panneaux à l’aide du bouton

L’éditeur de règles vous permet d’ajouter des boutons de navigation à vos dispositions de panneau, tels que des onglets horizontaux, verticaux, accordéons ou assistants. Ces boutons améliorent l’expérience de l’utilisateur en simplifiant les transitions entre les différents panneaux d’un formulaire, en déplaçant la sélection vers le panneau sélectionné.

Imaginez que vous interagissiez avec la section des paramètres de profil d’une application, où la navigation est facilitée par des boutons plutôt que par des onglets. Lorsque vous accédez aux paramètres du profil depuis le tableau de bord principal, vous rencontrez une série de panneaux dédiés à différents aspects de leur profil : **Informations personnelles**, **Sécurité du compte** et **Préférences de notification**.

Chaque panneau contient des champs et des options pertinents pour mettre à jour des informations spécifiques. Les boutons de navigation, tels que `Next` et `Back`, bien en évidence vous permettent de vous déplacer entre ces panneaux. Cliquez sur `Next` pour faire passer l’utilisateur au panneau **Sécurité du compte**, puis sur `Back` pour revenir au panneau **Informations personnelles**. Cette méthode de navigation assure une transition transparente entre les sections sans perdre de contexte, offrant ainsi une expérience utilisateur fluide et intuitive. L’utilisation des boutons de navigation simplifie le processus de gestion des paramètres de profil, ce qui rend l’interaction plus organisée et plus conviviale.

Vous pouvez utiliser la règle `Navigate among the panels` pour créer des règles de navigation pour les boutons qui permettent de basculer entre différents panneaux.  Sélectionnez l’attribut `Shift focus to the next item` pour déplacer le focus vers le panneau suivant dans la disposition.

![Règle du panneau suivant](/help/forms/assets/rule-editor-navigate-in-panel-next.png){width=50%}

Lorsque vous cliquez sur le bouton `Next`, le focus se déplace vers le panneau suivant de la mise en page.

![Naviguer dans le panneau à l’aide du bouton Suivant](/help/forms/assets/navigate-in-panel.gif)

De même, vous pouvez créer une règle pour le bouton `Previous` afin de déplacer le focus vers le panneau précédent.

![Règle du panneau précédent](/help/forms/assets/rule-editor-navigate-in-panel-previous.png){width=50%}

## Simplifiez les calculs complexes dans les panneaux répétables avec des fonctions

L’éditeur de règles vous permet d’utiliser des fonctions prêtes à l’emploi telles que Somme, Min, Max et Jointure directement sur les champs des panneaux répétables. Vous pouvez également transmettre une valeur de champ de panneau répétable à la fonction qui accepte le tableau numérique, le tableau de chaîne, le tableau booléen, etc. Cela débloque une automatisation puissante, ce qui vous permet d’implémenter une logique commerciale complexe sans code personnalisé.

Imaginez un formulaire avec un panneau répétable, où chaque instance de panneau collecte des informations sur la valeur déclarée des ressources.

![Formulaire reproductible](/help/forms/assets/ootb-function-support-repeatable-panel-form.png)

Vous pouvez utiliser la fonction `Sum` pour calculer automatiquement la valeur totale des ressources sur tous les panneaux, ce qui élimine la nécessité de calculs manuels et réduit le risque d’erreurs.

![Prise en charge des champs de panneau répétables dans les fonctions prêtes à l’emploi](/help/forms/assets/ootb-function-support-repeatable-panel.png)

Lorsque vous remplissez un formulaire en ajoutant des instances pour déclarer les valeurs des ressources, le bouton `Calculate Asset Value` calcule la somme totale de toutes les valeurs des ressources déclarées et affiche le résultat dans `assetvalue` zone de texte.

![Prise en charge des champs de panneau répétables dans les fonctions prêtes à l’emploi](/help/forms/assets/ootb-function-support-repeatable-panel-form-preview.png)

>[!NOTE]
>
> Si la valeur du champ du panneau répétable est transmise à une fonction qui n’accepte pas de tableau, la valeur du champ de la dernière instance du panneau répétable est transmise à la fonction.

Ce n&#39;est qu&#39;un exemple ! Explorez les [fonctions](#b-form-objects-and-functions-br) disponibles pour simplifier les workflows et améliorer la précision des données dans vos formulaires.

## Expressions imbriquées {#nestedexpressions}

L’éditeur de règles vous permet d’utiliser plusieurs opérateurs ET et OU afin de créer des règles imbriquées. Vous pouvez mélanger plusieurs opérateurs ET et OU dans les règles.

Voici un exemple de règle imbriquée qui affiche un message à l’utilisateur concernant l’éligibilité pour un droit de garde lorsque les conditions requises sont remplies.

![Expression complexe](assets/complexexpression.png)

Vous pouvez également faire glisser et déposer des conditions dans une règle pour la modifier. Appuyez et passez le curseur sur la poignée (![handle](assets/drag-handle.svg)) avant une condition. Une fois le pointeur affiché sous forme de main comme illustré ci-dessous, faites glisser la condition et déposez-la n’importe où dans la règle. La structure de la règle change.

![Glisser-déposer](assets/drag-and-drop.png)

## Conditions d’expression de date {#dateexpression}

L’éditeur de règles vous permet d’utiliser des comparaisons de dates afin de créer des conditions.

Voici un exemple de condition qui affiche un objet de texte statique si le prêt hypothécaire sur la maison est déjà utilisé, ce que l’utilisateur indique en remplissant le champ de date.

Lorsque la date du prêt hypothécaire de la propriété indiquée par l’utilisateur est déjà dépassée, le formulaire adaptatif affiche une remarque concernant le calcul des revenus. La règle ci-dessous compare la date indiquée par l’utilisateur à la date actuelle et si la date indiquée par l’utilisateur est antérieure à la date actuelle, le formulaire affiche le message texte (appelé « Revenu »).

![Condition d’expression de date](assets/dateexpressioncondition.png)

Lorsque la date remplie est antérieure à la date actuelle, le formulaire affiche le message texte (Revenu), comme suit :

![Condition d’expression de date remplie](assets/dateexpressionconditionmet.png)

## Conditions de comparaison des nombres {#number-comparison-conditions}

L’éditeur de règles vous permet de créer des conditions qui comparent deux nombres.

Voici un exemple de condition, qui contient un objet de texte statique si le demandeur habite à l’adresse actuelle depuis moins de 36 mois.

![Condition de comparaison des nombres](assets/numbercomparisoncondition.png)

Lorsque l’utilisateur indique qu’il habite à l’adresse résidentielle actuelle depuis moins de 36 mois, le formulaire affiche une notification indiquant qu’un justificatif de domicile supplémentaire peut être demandé.

![Plus de justificatif demandé](assets/additionalproofrequested.png)

<!-- ## Impact of rule editor on existing scripts {#impact-of-rule-editor-on-existing-scripts}

In [!DNL Experience Manager Forms] versions prior to [!DNL Experience Manager 6.1 Forms] feature pack 1, form authors and developers used to write expressions in the Scripts tab of the Edit component dialog to add dynamic behavior to Adaptive Forms. The Scripts tab is now replaced by the rule editor.

Any scripts or expressions that you must have written in the Scripts tab are available in the rule editor. While you cannot view or edit them in visual editor, if you are a part of the forms-power-users group you can edit scripts in code editor. -->

### Appeler service de modèle de données de formulaire {#invoke}

Imaginons un service web `GetInterestRates` prenant le montant du prêt, la durée et la cote de solvabilité du demandeur ou de la demandeuse comme valeurs d’entrée et renvoyant un plan de prêt incluant le montant des mensualités et le taux d’intérêt. Vous créez un modèle de données de formulaire à l’aide du service web comme source de données. Vous ajoutez des objets de modèle de données et un service `get` au modèle de formulaire. Le service s’affiche sur l’onglet Services du modèle de données de formulaire. Ensuite, créez un formulaire adaptatif incluant des champs des objets de modèle de données pour capturer les données saisies par l’utilisateur pour le montant et la durée du prêt et la cote de solvabilité. Ajoutez un bouton qui demande au service Web d’extraire les détails du plan. La sortie est renseignée dans les champs appropriés.

La règle ci-dessous indique comment configurer l’action Appel du service pour accomplir l’exemple de scénario.

![Exemple-invoke-services](assets/example-invoke-services.png)

>[!NOTE]
>
>Si l’entrée est de type tableau, les champs qui prennent en charge les tableaux sont visibles dans la section déroulante Sortie.

### Déclenchement de plusieurs actions à l’aide de la règle Lorsque {#triggering-multiple-actions-using-the-when-rule}

Dans un formulaire de demande de prêt, vous voulez savoir si la personne demandant le prêt est un client ou une cliente existante ou non. En fonction des informations fournies par l’utilisateur, le champ ID du client doit s’afficher ou être masqué. En outre, vous souhaitez placer le focus sur le champ d’ID de client ou cliente si l’utilisateur ou l’utilisatrice est un client ou une cliente existant. Le formulaire de demande de prêt est composé des éléments suivants :

* Un bouton radio,**[!UICONTROL Êtes-vous déjà client(e) chez Geometrixx ?]**, qui propose les options [!UICONTROL Oui] et [!UICONTROL Non]. La valeur Oui est **0** ; la valeur Non est **1**.

* Un champ de texte, **[!UICONTROL ID de client Geometrixx]**, pour indiquer l’ID du client/de la cliente.

Lorsque vous entrez une règle Lorsque sur le bouton radio pour implémenter ce comportement, la règle s’affiche comme suit dans l’éditeur de règles visuel.

![When-rule-example](assets/when-rule-example.png)

Dans l’exemple de règle, l’instruction suivante dans la section Lorsque est la condition qui, si elle renvoie True, exécute les actions spécifiées dans la section Alors.

<!-- The rule appears as follows in the code editor.

![when-rule-example-code](assets/when-rule-example-code.png) 

Rule in the code editor -->

### Utilisation d’une sortie de fonction dans une règle {#using-a-function-output-in-a-rule}

Dans un formulaire de bon de commande, le tableau ci-dessous permet aux utilisateurs de saisir leurs commandes. Dans le tableau ci-dessous :

* La première ligne est répétable, de sorte que les utilisateurs et utilisatrices puissent commander plusieurs produits et spécifier différentes quantités. Son nom d’élément est `Row1`.
* Le titre de la cellule dans la colonne Quantité de produit de la ligne répétable est Quantité. Le nom de l’élément pour cette cellule est `productquantity`.
* La deuxième ligne du tableau est non répétable et le titre de la cellule dans la colonne Quantité de produit sur cette ligne est Quantité totale.

![Example-function-table](assets/example-function-table.png)

**A.** Ligne 1 **B.** Quantité **C.** Quantité totale

Maintenant, vous souhaitez ajouter des quantités spécifiées dans la colonne Quantité de produit pour tous les produits et afficher la somme dans la cellule Quantité totale. Vous pouvez obtenir ce résultat en saisissant une règle Définir la valeur de dans la cellule Quantité totale, comme indiqué ci-dessous.

![Example-function-output](assets/example-function-output.png)

### Validation d’une valeur de champ à l’aide d’une expression {#validating-a-field-value-using-expression}

Dans le formulaire de bon de commande expliqué dans l’exemple précédent, vous souhaitez empêcher l’utilisateur de commander plusieurs quantités d’un produit dont le prix est supérieur à 10000. À cet effet, vous pouvez créer une règle Valider, comme indiqué ci-dessous.

![Example-validate](assets/example-validate.png)

## Voir également

{{see-also-rule-editor}}
