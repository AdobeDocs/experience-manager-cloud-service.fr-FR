---
title: Copier et coller dans l’éditeur de communication interactive
description: La fonctionnalité Copier et coller dans l’éditeur de communication interactive d’AEM Forms permet aux auteurs de dupliquer une communication interactive existante et de la réutiliser dans un autre dossier ou emplacement.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
hide: true
index: false
hidefromtoc: true
exl-id: 127abe2a-d8cf-4488-959f-f7316a8ddc3e
source-git-commit: cdaceaabb8eeeec931b1897e1161f408606540b9
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 3%

---

# Copier et coller dans l’éditeur de communication interactive

>[!NOTE]
>
> La fonctionnalité de communication interactive est disponible dans le cadre du programme destiné aux utilisateurs et utilisatrices précoces. Envoyez un e-mail à `aem-forms-ea@adobe.com` à partir de votre adresse professionnelle pour demander l’accès.

La fonctionnalité Copier et coller de l’éditeur de communication interactive (IC) permet aux auteurs de dupliquer une communication interactive existante et de la réutiliser dans un autre dossier ou emplacement. Cette fonctionnalité permet aux équipes de travailler efficacement en activant plusieurs variantes d’un CI sans modifier la version d’origine.

En créant une copie, les auteurs peuvent apporter en toute sécurité des modifications à différents cas d’utilisation, clients ou scénarios commerciaux tout en préservant la communication interactive source.

## Éléments copiés

Lorsque vous copiez une communication interactive, les éléments suivants sont dupliqués dans le nouvel IC :

- Disposition et structure

- Composants et fragments

- Liaisons et règles de données

- Configurations de style et de marque

- Vous pouvez ensuite modifier chacun de ces éléments indépendamment dans l’IC copié.

## Copier une communication interactive

![Rechercher document IC](/help/forms/interactive-communication/assets/copy-in-ic.png)

Pour copier une communication interactive, procédez comme suit :

- Accédez à Forms et documents dans l’interface d’AEM.

- Recherchez la communication interactive à copier.

- Sélectionnez l’ID.

- Dans la barre d’outils ou le menu contextuel, choisissez Copier.

- Accédez au dossier ou à l’emplacement cible.

- Sélectionnez Coller pour créer un doublon de la communication interactive.

- Un nouvel IC est créé avec la même configuration que l&#39;original.

## Modifier et réutiliser la communication interactive copiée

![Rechercher document IC](/help/forms/interactive-communication/assets/paste-in-ic.png)

Après avoir collé la communication interactive :

- Ouvrez l’ID copié dans l’éditeur de communication interactive.

- Mettez à jour le contenu, les règles, les mappages de données ou la disposition selon les besoins.

- Enregistrez et publiez l’ID une fois prêt.

- Les modifications apportées à l’ID copié n’affectent pas la communication interactive d’origine.

## Bonnes pratiques

- Conservez l’IC d’origine comme version de base ou principale.

- Renommez les CI copiées pour refléter clairement leur objectif ou variation.

- Utilisez des opérations de copier-coller en combinaison avec le contrôle de version et les commentaires pour une meilleure traçabilité.

- Vérifiez les liaisons de données et les canaux de sortie après les avoir copiés pour vous assurer qu’ils sont corrects.

La fonctionnalité Copier et coller de la communication interactive simplifie la réutilisation et la personnalisation en permettant aux auteurs de dupliquer les IC existants et de les modifier indépendamment. Il permet un développement plus rapide, une expérimentation plus sûre et une diffusion de communication cohérente, sans risquer de modifier la communication interactive d’origine.
