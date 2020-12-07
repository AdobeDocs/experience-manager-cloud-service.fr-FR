---
title: Ajouter un nom de domaine personnalisé
description: Ajouter un nom de domaine personnalisé
translation-type: tm+mt
source-git-commit: 6571c11cedbc0d81fbdfd8072a39b1327bdba10b
workflow-type: tm+mt
source-wordcount: '530'
ht-degree: 0%

---


# Ajouter un nom de domaine personnalisé {#adding-cdn}

Un utilisateur doit être un propriétaire d’entreprise ou un gestionnaire de déploiement pour pouvoir ajouter un nom de domaine personnalisé dans Cloud Manager.

>[!NOTE]
>Avant d’ajouter un nom de domaine personnalisé, un certificat SSL valide contenant le nom de domaine personnalisé doit être installé sur votre Programme. Consultez la section Installation d’un certificat SSL pour en savoir plus.

Un seul nom de domaine peut être ajouté à la fois. Les utilisateurs peuvent toutefois ajouter des caractères génériques, par exemple `*.wknd.com` en tant que nom de domaine, ce qui permet d’héberger plusieurs sous-domaines avec un enregistrement TXT unique.
Chaque Environnement de Cloud Manager peut héberger jusqu’à 50 domaines personnalisés par environnement.
Le même nom de domaine ne peut pas être utilisé sur plusieurs environnements.

## Ajouter un nom de domaine personnalisé à partir de la page Paramètres de domaine {#adding-cdn-settings}

Suivez les étapes ci-dessous pour ajouter un nom de domaine personnalisé à partir de la page Paramètres de domaine :

1. Accédez à la page Paramètres de domaine à partir de la **page Environnements**

1. Sélectionnez **Ajouter le nom de domaine personnalisé** pour lancer l&#39;assistant d&#39;ajout de nom de domaine personnalisé.

1. Entrez le nom de domaine personnalisé.

   >[!NOTE]
   >Vous ne devez pas inclure d&#39;espaces `http://`, `https://` lors de la saisie dans votre domaine.

1. Sélectionnez l’Environnement dont le service de publication sera associé au nom de domaine.

1. Sélectionnez le certificat SSL dans la liste déroulante et sélectionnez Continuer.

1. Vous accédez alors à l’écran Vérification du nom de domaine pour votre Environnement. Consultez Ajouter un enregistrement TXT pour en savoir plus.

   >[!NOTE]
   >Suivez les instructions fournies pour prouver la propriété du domaine de votre environnement.

1. Sélectionnez Continuer.
1. Le déploiement CDN nécessite un certificat SSL valide et une vérification TXT réussie. Ceci est indiqué par l’état **Vérifié et déployé**.
1. Accédez à Vérifier l’état du nom de domaine personnalisé pour en savoir plus sur les différents états et sur la façon de s’adresser.

   >[!NOTE]
   >Le BAT DNS peut prendre jusqu&#39;à quelques heures pour reconnaître, en raison des retards de propagation DNS. Cloud Manager vérifie la propriété et met à jour l’état visible dans le tableau Paramètres de domaine. Pour plus d’informations, voir Vérification de l’état du nom de domaine.

## Ajouter un nom de domaine personnalisé à partir de la page des Environnements {#adding-cdn-environments}

1. Accédez à la page Détails de l’Environnement pour l’environnement d’intérêt.
1. Utilisez les champs d’entrée situés en haut du tableau Noms de domaine pour envoyer le nom de domaine personnalisé, le certificat SSL. Sélectionnez ensuite Ajouter.
1. L&#39;Assistant Ajouter un nom de domaine personnalisé s&#39;ouvre alors avec le nom d&#39;Environnement pré-renseigné.
1. Entrez le nom de domaine personnalisé. Remarque : N’incluez pas d’espaces `http://`, `https://` lors de la saisie dans votre domaine. Sélectionnez Continuer.
1. Vous accédez alors à l’écran Vérification du nom de domaine pour votre Environnement. Consultez la section Vérification du domaine (Ajouter l’enregistrement TXT) pour en savoir plus.

   >[!NOTE]
   >Suivez les instructions fournies pour prouver la propriété du domaine de votre environnement.

1. Sélectionnez Continuer.
1. Le déploiement CDN nécessite un certificat SSL valide et une vérification TXT réussie. Ceci est indiqué par l’état **Vérifié et déployé**.

A ce stade, votre nom de domaine personnalisé est prêt pour le test et un `CNAME` pour pointer vers celui-ci. Reportez-vous à la section Etat du nom de domaine pour en savoir plus sur les différents états et sur la façon de traiter.

>[!NOTE]
>Le BAT DNS peut prendre jusqu&#39;à quelques heures pour reconnaître, en raison des retards de propagation DNS. Cloud Manager vérifie la propriété et met à jour l’état visible dans le tableau Paramètres de domaine. Consultez la section Vérification de l’état du nom de domaine pour en savoir plus.
