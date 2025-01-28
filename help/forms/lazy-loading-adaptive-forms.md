---
title: Comment améliorer les performances des formulaires volumineux avec le chargement différé ?
description: Découvrez comment améliorer les performances des formulaires volumineux avec le chargement différé. Le chargement différé améliore considérablement les performances des formulaires adaptatifs volumineux et complexes en différant l’initialisation et le chargement des fragments des formulaires jusqu’à ce qu’ils soient visibles.
feature: Adaptive Forms, Foundation Components
role: User, Developer
level: Intermediate
exl-id: 0cd38edb-2201-4ca6-8b84-6b5b7f76bd90
source-git-commit: b5340c23f0a2496f0528530bdd072871f0d70d62
workflow-type: tm+mt
source-wordcount: '1063'
ht-degree: 88%

---

# Amélioration des performances des formulaires volumineux avec le chargement différé{#improve-performance-of-large-forms-with-lazy-loading}

>[!NOTE]
>
> Adobe recommande d’utiliser la capture de données moderne et extensible [composants principaux](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=fr) pour [créer un nouveau Forms adaptatif](/help/forms/creating-adaptive-form-core-components.md) ou [ajouter un Forms adaptatif aux pages AEM Sites](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md). Ces composants représentent une avancée significative dans la création de formulaires adaptatifs, ce qui garantit des expériences utilisateur impressionnantes. Cet article décrit une ancienne approche de création de Forms adaptatif à l’aide de composants de base.

| Version | Lien de l’article |
| -------- | ---------------------------- |
| AEM 6.5 | [Cliquez ici](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/lazy-loading-adaptive-forms.html) |
| AEM as a Cloud Service | Cet article |


## Introduction au chargement différé {#introduction-to-lazy-loading}

Lorsque les formulaires sont volumineux et complexes et qu’ils contiennent des centaines, voire des milliers de champs, le délai de réponse expérimenté par les utilisateurs est long pour le rendu du formulaire au moment de l’exécution. Pour réduire le temps de réponse, le Forms adaptatif permet de diviser les formulaires en fragments logiques et de les configurer de manière à différer l’initialisation ou le chargement des fragments jusqu’à ce que le fragment soit visible. Il s’agit du chargement différé. En outre, les fragments configurés pour un chargement différé sont déchargés lorsque l’utilisateur accède à d’autres sections du formulaire et ne sont donc plus visibles.

Découvrons d’abord les exigences et les étapes préparatoires avant de configurer le chargement différé.

## Préparation à la configuration du chargement différé {#preparing-to-configure-lazy-loading}

Avant de configurer le chargement différé des fragments d’un formulaire adaptatif, il est essentiel de définir des stratégies afin de créer des fragments, d’identifier les valeurs utilisées dans les scripts ou référencées dans d’autres fragments, ou encore de définir des règles de contrôle de la visibilité des champs des fragments chargés.

* **Identifier et créer des fragments**
Vous pouvez configurer les fragments de formulaires adaptatifs uniquement pour le chargement différé. Un fragment est un segment autonome qui réside en dehors d’un formulaire adaptatif et peut être réutilisé dans des formulaires. Ainsi, la première étape de création d’un chargement différé consiste à identifier les sections logiques d’un formulaire et à les convertir en fragments. Vous pouvez créer un fragment à partir de zéro ou enregistrer un panneau de formulaire existant comme fragment.

  <!--For more information about creating fragments, see [Adaptive Form Fragments](adaptive-form-fragments.md).-->

* **Identifier et marquer les valeurs globales**
Les transactions Forms utilisent des éléments dynamiques pour capturer les données appropriées depuis les utilisateurs et les traiter afin de simplifier l’expérience de remplissage. Par exemple, votre formulaire contient le champ A dans le fragment X dont la valeur détermine la validité du champ B dans un autre fragment. Dans ce cas, si le fragment X est marqué pour un chargement différé, la valeur du champ A doit être disponible pour valider le champ B, même si le fragment X n’est pas chargé. Pour obtenir ce résultat, vous pouvez marquer le champ A comme étant global, ce qui permet de s’assurer que sa valeur est disponible pour la validation du champ B lorsque le fragment X n’est pas chargé.

  Pour plus d’informations sur la façon de créer une valeur de champ global, voir [Configuration du chargement différé](lazy-loading-adaptive-forms.md#p-configuring-lazy-loading-p).

* **Règles d’écriture pour le contrôle de la visibilité des champs**
Les formulaires incluent certains champs et sections qui ne s’appliquent pas à tous les utilisateurs et dans tous les cas. Les équipes de création et de développement utilisent la visibilité ou les règles afficher-masquer pour contrôler leur visibilité en fonction des entrées de l’utilisateur ou de l’utilisatrice. Par exemple, le champ Adresse du bureau n’est pas affiché pour les utilisateurs ou utilisatrices qui saisissent Sans emploi dans le champ Emploi. Pour plus d’informations sur les règles d’écriture, voir [Utilisation de l’éditeur de règles](rule-editor.md).

  Vous pouvez utiliser les règles de visibilité dans les fragments chargés de manière différée de sorte que les champs conditionnels soient affichés uniquement lorsqu’ils sont obligatoires. En outre, marquez le champ conditionnel comme étant global pour vous y référer dans l’expression de visibilité du fragment chargé en différé.

## Configuration du chargement différé {#configuring-lazy-loading}

Suivez les étapes ci-après pour activer le chargement différé sur un fragment de formulaire adaptatif :

1. Ouvrez le formulaire adaptatif en mode création contenant le fragment que vous souhaitez activer pour le chargement différé.
1. Sélectionnez le fragment de formulaire adaptatif et sélectionnez ![configurer](assets/configure-icon.svg).
1. Dans la barre latérale, activez **[!UICONTROL Chargement différé du fragment]** et sélectionnez **Terminé**.

   ![Activation du chargement différé du fragment de formulaire adaptatif](assets/lazy-loading-fragment.png)

   Le fragment est désormais activé pour le chargement différé.

Vous pouvez marquer les valeurs des objets du fragment chargé en différé comme globales, de manière à pouvoir les utiliser dans des scripts lorsque le fragment contenant n’est pas chargé. Procédez comme suit :

1. Ouvrez le fragment de formulaire adaptatif en mode création.
1. Sélectionnez le champ dont vous souhaitez marquer la valeur comme globale, puis sélectionnez ![configurer](assets/configure-icon.svg).
1. Dans la barre latérale, activez **[!UICONTROL Utiliser la valeur pendant le chargement différé]**.

   ![Champ de chargement différé dans la barre latérale](assets/enable-lazy-loading.png)

   Cette valeur est maintenant marquée comme globale et peut être utilisée dans les scripts même lorsque le fragment contenant est déchargé.

## Éléments à prendre en compte et bonnes pratiques pour la configuration du chargement différé {#considerations-and-best-practices-for-configuring-lazy-loading}

Voici certaines restrictions, recommandations et aspects importants à garder à l’esprit lorsque vous travaillez avec le chargement différé :

* Adobe recommande d’utiliser le Forms adaptatif basé sur un schéma XSD plutôt que le Forms adaptatif basé sur XFA pour configurer le chargement différé des formulaires volumineux. Le gain de performances en raison de l’implémentation du chargement différé dans les formulaires adaptatifs basés sur XFA est moins important que dans les formulaires adaptatifs XSD.
* Ne configurez pas le chargement différé sur les fragments d’un formulaire adaptatif qui utilisent **[!UICONTROL Réactif -tout sur une page sans disposition de navigation]** pour le panneau racine. En raison de la configuration de la disposition réactive, tous les fragments se chargent simultanément dans un formulaire adaptatif. Vous risqueriez également de causer une baisse des performances.
* Il est recommandé de ne pas configurer le chargement différé sur des fragments du premier panneau s’affichant au chargement du formulaire adaptatif.
* Le chargement différé est pris en charge jusqu’à deux niveaux dans la hiérarchie de fragment.
* Assurez-vous que les champs signalés comme étant globaux sont uniques sur un formulaire adaptatif.
* Pensez à créer des règles de visibilité pour les fragments qui doivent s’afficher ou être masqués en fonction d’une condition. Par exemple, vous pouvez afficher ou masquer le fragment Conjoint(e) selon la valeur État civil spécifiée par l’utilisateur.
* Les composants des pièces jointes et des conditions générales ne sont pas pris en charge dans les fragments chargés en différé.

### Script des bonnes pratiques pour la configuration du chargement différé {#scripting-best-practices-for-configuring-lazy-loading}

Voici des aspects importants à garder à l’esprit lors du développement des scripts pour les panneaux de chargement différé :

* Assurez-vous que les scripts initialize et calculate utilisés sur les champs d’un fragment à chargement différé sont idempotents par nature. Les scripts idempotents sont ceux qui ont le même effet, même après plusieurs exécutions.
* Utilisez plutôt la propriété disponible globalement des champs pour modifier la valeur des champs situés dans un panneau de chargement différé à la disposition de tous les autres panneaux d’un formulaire.
* Ne transférez pas la valeur de référence d’un champ dans un panneau différé, peu importe que le champ soit ou non marqué globalement sur tous les fragments.
* Utilisez la fonction de réinitialisation des panneaux pour réinitialiser tout élément visible sur le panneau à l’aide de l’expression de clic suivante.\
  guideBridge.resolveNode(guideBridge.getFocus({&quot;focusOption&quot;: &quot;navigablePanel&quot;})).resetData()


## Voir également {#see-also}

{{see-also}}