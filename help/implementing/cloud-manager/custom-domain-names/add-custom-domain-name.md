---
title: Ajouter un nom de domaine personnalisé
description: Ajouter un nom de domaine personnalisé
translation-type: tm+mt
source-git-commit: 27e96d66d93f2fa0e67e607c75f37efda17a13b7
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 0%

---


# Ajouter un nom de domaine personnalisé {#adding-cdn}

Un utilisateur doit être un propriétaire d’entreprise ou un gestionnaire de déploiement pour pouvoir ajouter un nom de domaine personnalisé dans Cloud Manager.

## Points importants {#important-considerations}

* Avant d’ajouter un nom de domaine personnalisé, un certificat SSL valide contenant le nom de domaine personnalisé doit être installé sur votre Programme. Consultez [Ajouter un certificat SSL](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) pour en savoir plus.

* Un seul nom de domaine peut être ajouté à la fois. Les utilisateurs peuvent toutefois ajouter des caractères génériques, par exemple `*.wknd.com` en tant que nom de domaine, ce qui permet d’héberger plusieurs sous-domaines avec un enregistrement TXT unique.

* Chaque Environnement de Cloud Manager peut héberger jusqu’à 100 domaines personnalisés par environnement.

* Le même nom de domaine ne peut pas être utilisé sur plusieurs environnements.

## Ajouter un nom de domaine personnalisé à partir de la page Paramètres de domaine {#adding-cdn-settings}

Suivez les étapes ci-dessous pour ajouter un nom de domaine personnalisé à partir de la page Paramètres de domaine :

1. Accédez à l’écran **Environnements** à partir de la page **Aperçu**.

1. Cliquez sur **Paramètres de domaine** dans le menu de navigation de gauche.

   ![](/help/implementing/cloud-manager/assets/cdn/cdn-create.png)

1. Cliquez sur le bouton **Ajouter le domaine** pour ouvrir la boîte de dialogue **Ajouter le nom de domaine**.

   ![](/help/implementing/cloud-manager/assets/cdn/cdn-create2.png)

1. Entrez le nom de domaine personnalisé dans **Nom de domaine**.

   >[!NOTE]
   >Vous ne devez pas inclure d&#39;espaces `http://`, `https://` lors de la saisie dans votre domaine.

1. Sélectionnez l’**Environnement** dont le service de publication sera associé au nom de domaine.

1. Sélectionnez **Domain SSL Certificate** dans la liste déroulante et sélectionnez **Continuer**.

1. **La boîte de dialogue Ajouter le** nom de domaine s’affiche. Vous accédez alors à l’écran Vérification du nom de domaine pour votre Environnement. Consultez [Ajouter un enregistrement TXT](/help/implementing/cloud-manager/custom-domain-names/add-text-record.md) pour en savoir plus.
Suivez les instructions fournies pour prouver la propriété du domaine de votre environnement.

1. Cliquez sur **Créer**.
1. Le déploiement CDN nécessite un certificat SSL valide et une vérification TXT réussie. Ceci est indiqué par l’état **Vérifié et déployé**.
Accédez à [Vérification de l’état du nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) pour en savoir plus sur les différents états et sur la manière de résoudre le problème.

   >[!NOTE]
   >Le BAT DNS peut prendre jusqu&#39;à quelques heures pour reconnaître, en raison des retards de propagation DNS. Cloud Manager vérifie la propriété et met à jour l’état visible dans le tableau Paramètres de domaine. Pour plus d’informations, voir Vérification de l’état du nom de domaine.

## Ajouter un nom de domaine personnalisé à partir de la page des Environnements {#adding-cdn-environments}

1. Accédez à la page Détails des Environnements pour l’environnement d’intérêt.

   ![](/help/implementing/cloud-manager/assets/cdn/cdn-create4.png)

1. Utilisez les champs d’entrée situés en haut du tableau Noms de domaine pour envoyer le nom de domaine personnalisé et sélectionnez le certificat SSL dans la liste déroulante. Cliquez sur **+ Ajoute**.

   ![](/help/implementing/cloud-manager/assets/cdn/cdn-create3.png)

1. Vérifiez les champs de la boîte de dialogue **Ajouter le nom de domaine** et cliquez sur **Continuer**.

   ![](/help/implementing/cloud-manager/assets/cdn/cdn-create5.png)

   >[!NOTE]
   >N’incluez pas d’espaces `http://`, `https://` lors de la saisie dans votre domaine.

1. L’écran Vérification du nom de domaine de votre Environnement s’affiche.

   ![](/help/implementing/cloud-manager/assets/cdn/cdn-create6.png)

   Consultez [Vérification de domaine](/help/implementing/cloud-manager/custom-domain-names/add-text-record.md) pour en savoir plus. Suivez les instructions fournies pour prouver la propriété du domaine de votre environnement.

1. Cliquez sur **Créer**.

1. Le déploiement des noms de domaine personnalisés requiert un certificat SSL valide et une vérification TXT réussie. Ceci est indiqué par l’état **Vérifié et déployé**.

A ce stade, votre nom de domaine personnalisé est prêt pour le test et un `CNAME` pour pointer vers celui-ci. Consultez [État du nom de domaine](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) pour en savoir plus sur les différents états et sur la façon de s&#39;y attaquer.

>[!NOTE]
>Le BAT DNS peut prendre jusqu&#39;à quelques heures pour reconnaître, en raison des retards de propagation DNS. Cloud Manager vérifie la propriété et met à jour l’état visible dans le tableau Paramètres de domaine. Consultez la section Vérification de l’état du nom de domaine pour en savoir plus.
