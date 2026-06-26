---
title: Vérifier et annoter une communication interactive
description: Découvrez comment les réviseurs et réviseuses peuvent épingler leurs commentaires directement dans les composants de la zone de travail de communication interactive et comment les auteurs et autrices peuvent les suivre et les résoudre sans quitter l’éditeur de communication interactive.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
badgeSaas: label="AEM Forms" type="Positive" tooltip="Application pour AEM Forms."
exl-id: review-annotate-interactive-communication
source-git-commit: b11e1b28aabba9e03553dc9e9394bff111facfee
workflow-type: tm+mt
source-wordcount: '709'
ht-degree: 2%

---


# Vérifier et annoter une communication interactive

La révision d’une communication interactive implique généralement le partage de captures d’écran, la composition d’e-mails ou la tenue de conversations secondaires, dont aucune ne peut être liée au champ ou à la section exacts en cours de discussion. Les annotations résolvent ce problème en donnant aux réviseurs et aux réviseuses une vue dédiée et en lecture seule de la communication interactive où ils ou elles peuvent cliquer sur n’importe quel composant et laisser un commentaire épinglé à cet endroit précis sur la zone de travail.

Tous les réviseurs et réviseuses partagent la même vue d’annotation, de sorte que les commentaires soient visibles par tous et toutes au même endroit. Les annotations n’existent que pendant le processus de création et de révision et n’apparaissent jamais sur les sorties publiées ou visibles par le client ou la cliente.

| Qui | Avantage |
|-----|---------|
| **Réviseur** | Donnez des commentaires précis et contextuels sans modifier la communication interactive ni risquer des modifications accidentelles. |
| **Auteur (concepteur/propriétaire de la communication interactive)** | Recevez des commentaires exploitables liés à des composants spécifiques, avec un moyen clair de suivre et de fermer chaque élément de révision. |

## Avant de commencer

Les réviseurs et les auteurs doivent chacun être affectés aux groupes de réviseurs et d’auteurs prêts à l’emploi appropriés avant de pouvoir accéder à la zone de travail d’annotation ou au workflow de résolution.

>[!NOTE]
>
> Confirmez les noms exacts des groupes pour votre environnement avec votre administrateur AEM avant d’attribuer l’accès.

## Ajouter une annotation

Effectuez les étapes suivantes en tant que réviseur/réviseuse.

1. Accédez à **Forms et documents** sélectionnez la communication interactive à vérifier, puis cliquez sur **Annoter** dans la barre d’outils.

   ![Annoter 1](/help/forms/interactive-communication/assets/add-annotate1.png)

   La lecture seule **vue Annotations** s’ouvre avec la communication interactive affichée sur la zone de travail.

   ![Annoter 2](/help/forms/interactive-communication/assets/add-annotate2.png)

1. Pour joindre un commentaire à un composant spécifique, cliquez sur ce composant sur la zone de travail.

   ![Annoter 3](/help/forms/interactive-communication/assets/add-annotate3.png)

1. Saisissez vos commentaires dans la zone de commentaire, puis cliquez sur le bouton bleu Publication pour enregistrer le commentaire.

   ![Annoter 4](/help/forms/interactive-communication/assets/add-annotate4.png)

1. Répétez les étapes 2 et 3 pour chaque composant qui nécessite des commentaires.

   Par exemple, cliquez sur le bloc d’adresse de la banque et ajoutez **Mettre à jour l’adresse**, puis cliquez sur la cellule **Marque et modèle** dans le tableau Détails du véhicule et ajoutez **Mettre à jour le modèle de voiture**.

1. Lorsque vous avez terminé d’ajouter des commentaires, cliquez sur **Soumettre vos commentaires**.

   ![Annoter 5](/help/forms/interactive-communication/assets/add-annotate5.png)

   Un message de réussite confirme l’envoi de vos commentaires. Chaque commentaire s’affiche en tant qu’épingle d’annotation à l’emplacement que vous avez sélectionné, et tous les autres réviseurs peuvent le voir immédiatement.

## Vérifier les annotations

Effectuez les étapes suivantes en tant qu’auteur.

1. Accédez à **Forms et documents**, sélectionnez la communication interactive et cliquez sur **Modifier** pour l’ouvrir dans l’éditeur de communication interactive.

   ![Résoudre 1](/help/forms/interactive-communication/assets/add-annotate6.png)

1. Sélectionnez un composant qui affiche une épingle d’annotation du réviseur.

   Par exemple, sélectionnez le bloc d’adresse de la banque. Dans le panneau **Propriétés**, développez la section **Commentaires** pour afficher l’annotation jointe. Le commentaire du réviseur **mettre à jour l’adresse** s’affiche ici.

   ![Résoudre 2](/help/forms/interactive-communication/assets/add-annotate7.png)

1. Passez en revue chaque commentaire et apportez les modifications nécessaires à la conception.

   Par exemple, mettez à jour le texte de l’adresse bancaire comme demandé par le réviseur ou la réviseuse.

   ![Résoudre 3](/help/forms/interactive-communication/assets/add-annotate8.png)

1. Une fois que vous avez commenté, cliquez sur **Résoudre** dans la section **Commentaires**.

1. Répétez les étapes 2 à 4 pour chaque annotation restante.

   Par exemple, sélectionnez la cellule **Marque et modèle** dans le tableau Détails du véhicule, mettez à jour la valeur sur **Creta SX(O)** comme demandé dans le commentaire **Mettre à jour le modèle de voiture** et marquez-la comme **Résolue**.

   ![Résoudre 4](/help/forms/interactive-communication/assets/add-annotate9.png)

1. Cliquez sur **Enregistrer**.

   ![Résoudre 5](/help/forms/interactive-communication/assets/add-annotate10.png)

   Une épingle d’annotation résolue passe d’ouverte à fermée (grise), distinguant les éléments de révision terminés de ceux toujours en attente. Le commentaire résolu reste visible dans l’historique, de sorte que le journal de révision complet est conservé.

## Considérations

- Les réviseurs et les auteurs doivent être affectés aux groupes prêts à l’emploi appropriés. Les configurations de groupe personnalisées ne sont pas prises en charge.

- Si vous réduisez la taille d’un composant après avoir placé une annotation sur celui-ci, l’épingle reste à la position initiale au lieu de se déplacer avec la limite du composant.

- Les annotations sur les fragments d’un document ne sont pas prises en charge.

- Les annotations sur le composant **Tableau** ne sont pas encore prises en charge.

## Questions fréquentes

**Comment joindre un commentaire à un champ spécifique plutôt qu’à une zone générale ?**
Cliquez directement sur le composant dans la zone de travail de l’annotation. L’épingle est associée à ce composant et s’affiche pour tous les réviseurs dans la même vue d’annotation.

**Comment un auteur ou une autrice sait-il quels composants ont des annotations ouvertes ?**
Les épingles d’annotation sont visibles directement sur la zone de travail dans l’éditeur de communication interactive. La sélection d’un composant affiche tous les commentaires associés dans le panneau Propriétés .

**Les annotations apparaissent-elles dans la sortie PDF publiée ?**
Non. Les annotations font uniquement partie du workflow de création et de révision. Ils ne sont jamais inclus dans les sorties publiées ou orientées client.

**Quelle est la différence entre une annotation et un commentaire ?**
Une annotation est une épingle positionnée liée à un composant spécifique sur la zone de travail, visible dans la vue d’annotation en lecture seule. Un commentaire est une note générale jointe à la communication interactive dans son ensemble, ajoutée à partir du panneau Commentaires dans l’éditeur. Voir [Contrôle de version et commentaires](/help/forms/interactive-communication/versioning-and-commenting-in-interactive-communication-editor.md) pour plus d’informations sur les commentaires.

## Voir également

- [Créer une communication interactive](/help/forms/interactive-communication/create-interactive-communication.md)
- [Verrouillage de modèle dans l’éditeur de communication interactive](/help/forms/interactive-communication/enable-template-lock.md)
- [Contrôle de version et commentaires dans l’éditeur de communication interactive](/help/forms/interactive-communication/versioning-and-commenting-in-interactive-communication-editor.md)

