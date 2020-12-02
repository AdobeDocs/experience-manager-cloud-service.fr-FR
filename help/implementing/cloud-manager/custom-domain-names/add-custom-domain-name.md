---
title: Ajouter un nom de domaine personnalisé
description: Ajouter un nom de domaine personnalisé
translation-type: tm+mt
source-git-commit: b6b1ef8f97413dc8bf9b1fa7f355a02bdaeebfd8
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 0%

---


# Ajouter un nom de domaine personnalisé {#adding-cdn}

Un utilisateur doit être un propriétaire d’entreprise ou un gestionnaire de déploiement pour pouvoir ajouter un nom de domaine personnalisé dans Cloud Manager.

>[!NOTE]
>Avant d’ajouter un nom de domaine personnalisé, un certificat SSL valide contenant le nom de domaine personnalisé doit être installé sur votre Programme. Voir Installation d’un certificat SSL (INSERT LINK) pour en savoir plus.

Un seul nom de domaine peut être ajouté à la fois. Les utilisateurs peuvent toutefois ajouter des caractères génériques, par exemple `*.wknd.com` en tant que nom de domaine, ce qui permet d’héberger plusieurs sous-domaines avec un enregistrement TXT unique.
Chaque Environnement de Cloud Manager peut héberger jusqu’à 50 domaines personnalisés par environnement.
Le même nom de domaine ne peut pas être utilisé sur plusieurs environnements.

## Ajouter un nom de domaine personnalisé à partir de la page Paramètres de domaine {#adding-cdn-settings}

Suivez les étapes ci-dessous pour ajouter un nom de domaine personnalisé à partir de la page Paramètres de domaine :

1. De la page Environnements, accédez à la page Paramètres de domaine.

1. Sélectionner un nom de domaine personnalisé Ajouté
L&#39;assistant d&#39;ajout de noms de domaine personnalisé INSERT IMAGE sera lancé

1. Entrez le nom de domaine personnalisé. Remarque : N’incluez pas &quot;http://&#39;&quot;, &quot;https://&#39;&quot; ou d’espaces lorsque vous entrez dans votre domaine.

1. Sélectionnez l’Environnement dont le service de publication sera associé au nom de domaine.

1. Sélectionnez le certificat SSL dans la liste déroulante et sélectionnez Continuer.

1. Vous accédez alors à l’écran Vérification du nom de domaine pour votre Environnement. Pour en savoir plus, Ajoutez Enregistrement TXT. INSÉRER UNE IMAGE

Suivez les instructions fournies pour prouver la propriété de domaine de votre environnement :

1. Sélectionnez Continuer.
1. Le déploiement CDN nécessite un certificat SSL valide et une vérification TXT réussie. Ceci est indiqué par l’état &quot;Vérifié et déployé&quot;.  INSÉRER UNE IMAGE
1. Accédez à Vérifier l&#39;état du nom de domaine personnalisé INSERTION LIEN pour en savoir plus sur les différents états et sur la façon de s&#39;adresser.

>[!NOTE]
>Le BAT DNS peut prendre jusqu&#39;à quelques heures pour reconnaître, en raison des retards de propagation DNS. Cloud Manager vérifie la propriété et met à jour l’état visible dans le tableau Paramètres de domaine. Pour en savoir plus, consultez Vérifier l&#39;état du nom de domaine INSÉRER LE LIEN.

## Ajouter un nom de domaine personnalisé à partir de la page des Environnements {#adding-cdn-environments}

1. Accédez à la page Détails de l’Environnement pour l’environnement d’intérêt.
1. Utilisez les champs d’entrée situés en haut du tableau Noms de domaine pour envoyer le nom de domaine personnalisé, le certificat SSL. Sélectionnez ensuite Ajouter.
1. L&#39;Assistant Ajouter un nom de domaine personnalisé s&#39;ouvre alors avec le nom d&#39;Environnement pré-renseigné.
1. Entrez le nom de domaine personnalisé. Remarque : N’incluez pas d’espaces `http://`, `https://` lors de la saisie dans votre domaine. Sélectionnez Continuer.
1. Vous accédez alors à l’écran Vérification du nom de domaine pour votre Environnement. Pour en savoir plus, consultez la section Vérification du domaine (Ajouter l’enregistrement TXT). INSÉRER UNE IMAGE

Suivez les instructions fournies pour prouver la propriété de domaine de votre environnement :

1. Sélectionnez Continuer.
1. Le déploiement CDN nécessite un certificat SSL valide et une vérification TXT réussie. Ceci est indiqué par l’état &quot;Vérifié et déployé&quot;.

A ce stade, votre nom de domaine personnalisé est prêt pour le test et un `CNAME` pour pointer vers celui-ci. Accédez à l’état du nom de domaine pour en savoir plus sur les différents états et sur la manière de traiter.

>[!NOTE]
>Le BAT DNS peut prendre jusqu&#39;à quelques heures pour reconnaître, en raison des retards de propagation DNS. Cloud Manager vérifie la propriété et met à jour l’état visible dans le tableau Paramètres de domaine. Pour en savoir plus, consultez Vérifier l&#39;état du nom de domaine INSÉRER LE LIEN.
