---
title: Comment importer une politique de marque
description: Utilisation de l’agent de gouvernance Adobe pour importer une politique de marque
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Architect, Developer
source-git-commit: 94d671ebbd5aeb5992fdbc9d779ffbca51f82585
workflow-type: tm+mt
source-wordcount: '949'
ht-degree: 0%

---


# Comment importer une politique de marque {#how-to-import-a-brand-policy}

## Vue d’ensemble {#overview}

Une politique de marque définit les règles, normes et contraintes qui garantissent que tout le contenu produit ou mis à jour par Adobe Experience Manager reste cohérent avec l’identité de marque d’une entreprise. Cela inclut généralement le ton de la voix, la terminologie, les directives visuelles et les règles éditoriales.

L’agent de gouvernance utilise les politiques de marque comme source de vérité pour analyser les pages existantes et guider la génération de contenu. Les clients peuvent fournir leurs propres politiques de marque d’origine, que l’agent de gouvernance convertit automatiquement en contrôles de politiques lisibles par l’IA. Ces contrôles sont ensuite utilisés pour valider le contenu et fournir à l’agent de production un framework fiable et exécutable pour générer ou mettre à jour des pages qui restent alignées sur la marque.

## Qu’est-ce qu’une politique de marque dans l’agent de gouvernance ? {#what-is-a-brand-policy-in-the-governance-agent}

Dans le contexte de l’agent de gouvernance, une politique de marque est une représentation structurée de vos règles de marque qui peuvent être comprises et appliquées par l’IA. Plutôt que d’exiger des clients qu’ils réécrivent leurs directives dans un format technique, l’agent de gouvernance accepte les politiques de marque dans leur forme originale (par exemple, les documents, les directives ou les descriptions de règle).

Une fois importée, la politique est transformée en un ensemble de contrôles de politique d’IA qui peuvent :

* Analyse des pages existantes pour détecter les incohérences de marque
* Signaler les écarts par rapport au ton, à la terminologie ou aux règles obligatoires
* Fournir des conseils clairs aux agents en aval
* S’assurer que le contenu généré ou mis à jour reste conforme à la marque dès la conception

Cette approche permet aux équipes de réutiliser leur documentation de marque existante tout en bénéficiant d’une gouvernance automatisée et d’une production de contenu évolutive.

## Utilisation des politiques de marque {#how-brand-policies-are-used}

Après l’importation d’une politique de marque :

* L’agent de gouvernance interprète et normalise la politique en contrôles IA applicables
* Les pages peuvent être analysées par rapport à la politique afin d’identifier les lacunes ou les violations
* L’agent de production utilise ces contrôles comme contraintes lors de la génération ou de la mise à jour du contenu
* La conformité de la marque devient cohérente, reproductible et auditable sur l’ensemble des sites et des équipes


## Importer une politique de marque {#import-a-brand-policy}

Pour importer une marque dans l’agent de gouvernance :

1. Créez une marque, en donnant un nom et un domaine principal. Pour ce faire, cliquez sur le bouton **Contexte de gouvernance** sur le volet de navigation de gauche de l’accueil d’Experience Manager, puis appuyez sur le bouton **+ Ajouter une marque**, comme illustré ci-dessous :

   ![Ajouter une nouvelle marque](/help/ai-in-aem/agents/governance/assets/add_brand.png){width="70%"}

1. Définissez le nom de la marque et une description dans la fenêtre suivante

   ![Nommer la marque](/help/ai-in-aem/agents/governance/assets/add_brand_dialogue.png){width="60%"}

1. Les nouvelles marques sont créées à l’état de brouillon. Assurez-vous de changer votre marque nouvellement créée en statut Actif, en cliquant sur la carte de votre marque, en appuyant sur la modification (crayon) dans le coin supérieur droit de l&#39;écran, définissez le **Statut** sur **Actif** dans la fenêtre suivante, puis cliquez sur **Enregistrer les modifications**. Vous devez activer les marques en les définissant sur Actif avant de pouvoir les utiliser.

   ![Définir le statut de la marque sur Actif](/help/ai-in-aem/agents/governance/assets/set_brand_active.png){width="60%"}

1. Une fois la marque créée, créez un domaine principal dans la fenêtre suivante en cliquant sur le lien **Domaines** sur la gauche :

   ![Configuration d’un domaine pour la marque](/help/ai-in-aem/agents/governance/assets/add_domain.png)

   >[!IMPORTANT]
   >
   >Tout comme les nouvelles marques, les nouveaux domaines sont créés avec un statut Brouillon par défaut. Pour modifier ce paramètre, accédez à votre marque, cliquez sur **Domaines**, puis modifiez votre domaine à l’aide de l’icône en forme de crayon et définissez son statut sur **Actif**.

1. Après avoir configuré le domaine principal, vous pouvez charger votre document de politique de marque en accédant à **Politiques** dans le coin supérieur gauche de la fenêtre, puis en appuyant sur le bouton **+ Ajouter une politique**.

   ![Ajout d’une politique à partir de la carte de marque](/help/ai-in-aem/agents/governance/assets/add_policy_treeview.png)

   >[!NOTE]
   >
   >Vous pouvez également ajouter des politiques en passant à l’onglet **Politiques** et en appuyant sur le lien **+ Ajouter une politique**.

1. Dans la fenêtre suivante, appuyez sur **Charger des PDF** et sélectionnez le ou les documents de stratégie de marque au format PDF

   ![Chargez votre document de politique de marque](/help/ai-in-aem/agents/governance/assets/upload_brand_policy_document.png){width="70%"}

   L’agent de gouvernance analyse les directives de votre politique de marque en utilisant un langage naturel et extrait les contrôles obtenus à partir du document pour les traduire en tâches réelles. Une fois le document traité, vous pouvez afficher un résumé de l’importation, comprenant le nombre de contrôles et le statut de la politique, comme illustré ci-dessous :

   ![Fenêtre de présentation du statut de la politique de marque](/help/ai-in-aem/agents/governance/assets/policy_status.png)

1. Une fois votre marque créée et votre document de politique téléchargé, vous pouvez obtenir une vue détaillée par marque en accédant à l&#39;onglet **Marques** et en cliquant sur la vignette d&#39;une marque. Il s’agit de la vue que vous souhaitez utiliser pour créer des catégories de chèques, en appuyant sur les trois points en regard d’une catégorie existante, puis en sélectionnant **+ Ajouter une catégorie**, comme illustré dans la capture d’écran ci-dessous :

   ![Ajouter une catégorie &#x200B;](/help/ai-in-aem/agents/governance/assets/add_category.png)

   Vous pouvez également utiliser cette vue pour créer, modifier et supprimer des contrôles. Les étapes ci-dessous vous donneront des détails à ce sujet.

1. Pour obtenir une vue plus granulaire de chaque vérification individuelle, vous pouvez passer à l’onglet **Vérifications** et afficher une liste de chaque vérification individuelle extraite de vos documents de référence. Vous pouvez filtrer les contrôles en fonction de la marque ou du statut :

   ![Voir vérifications de marque individuelles](/help/ai-in-aem/agents/governance/assets/see_brand_checks.png)

   De plus, vous pouvez afficher des détails supplémentaires sur chaque vérification individuelle en cliquant sur les trois points (**...**) à gauche de la vérification et en appuyant sur **Afficher les détails**. Une nouvelle fenêtre s’ouvre, contenant plus d’informations sur la vérification :

   ![Afficher les détails des contrôles individuels](/help/ai-in-aem/agents/governance/assets/view_check_details.png)

   Vous pouvez également supprimer des contrôles en appuyant sur **Supprimer** à partir du même emplacement du menu, ou les modifier en appuyant sur **Modifier** :

   ![Modification d’une vérification](/help/ai-in-aem/agents/governance/assets/edit_check.png)

1. Vous pouvez ajouter manuellement une vérification en appuyant sur **Ajouter une vérification** dans le coin supérieur gauche de la fenêtre Vérifications :

   ![Ajout d’une vérification](/help/ai-in-aem/agents/governance/assets/add_check.png)

   Dans l’écran suivant, vous pouvez configurer des détails tels que :

   * Nom du chèque
   * La règle, décrite en langage naturel
   * La catégorie
   * Portée(s) à laquelle(lesquelles) elle s’applique

   ![Configuration des détails de vérification](/help/ai-in-aem/agents/governance/assets/add_check_window.png)

1. Enfin, pour obtenir la liste des domaines et des marques auxquelles ils sont associés, vous pouvez appuyer sur l’onglet **Domaines**. Cette section vous permet d’ajouter, de supprimer ou de modifier des domaines dans votre liste.

