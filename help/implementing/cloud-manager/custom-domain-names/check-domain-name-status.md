---
title: Vérification de l'état du nom de domaine
description: Vérification de l'état du nom de domaine
translation-type: tm+mt
source-git-commit: 91b06bcd96fe8a37c3fb20ef90e1684f6d19183f
workflow-type: tm+mt
source-wordcount: '519'
ht-degree: 0%

---


# Vérification de l&#39;état du nom de domaine {#check-status}

Vous pouvez déterminer si votre nom de domaine a bien été vérifié en cliquant sur l’icône État du nom de domaine dans le tableau Environnements de la page Paramètres de domaine.

>[!NOTE]
>Cloud Manager déclenche automatiquement une vérification TXT lorsque vous sélectionnez Enregistrer à l’étape de vérification de l’assistant Ajouter un domaine personnalisé. Pour les vérifications suivantes, vous devez sélectionner activement l’icône &quot;vérifier à nouveau&quot; en regard de l’état. INSÉRER UNE IMAGE

Cloud Manager vérifie la propriété du domaine via la valeur TXT et affiche l’un des messages d’état suivants :

* **La valeur TXT Echec** de vérification du domaine est manquante ou est détectée avec des erreurs. Suivez les instructions et réessayez. Une fois prêt, vous devez sélectionner l’icône &quot;Vérifier à nouveau&quot; en regard de l’état.

* **Vérification du domaine en cours** Vérification en cours. Cet état s’affiche généralement après avoir sélectionné l’icône &quot;Vérifier à nouveau&quot; en regard de l’état.

* **Vérification vérifiée, la vérification TXT du déploiement ayant échoué**. Cependant, le déploiement du CDN a échoué. Un représentant d&#39;Adobe sera automatiquement averti.

* **Domaine vérifié et déployé** Cet état indique que votre nom de domaine personnalisé est prêt à être utilisé. Remarque : A ce stade, votre nom de domaine personnalisé est prêt à être testé et pointé vers le nom de domaine Cloud Manager. Accédez à Configuration des paramètres DNS INSERT LINK pour savoir comment procéder.

* **Suppression** de la suppression du nom de domaine personnalisé en cours.

* **Échec** de la suppressionÉchec de la suppression du nom de domaine personnalisé. Vous devez réessayer. Accédez à Supprimer le nom de domaine personnalisé pour en savoir plus sur la rubrique.


## Configuration des paramètres DNS {#configure-dns}

Une fois votre nom de domaine personnalisé vérifié et déployé, vous êtes prêt à mettre à jour les enregistrements DNS de votre nom de domaine personnalisé avec votre fournisseur DNS. Cela permet à votre site de servir les visiteurs. Cette activité est donc généralement effectuée avant le lancement.

>[!NOTE]
>Vous ou la personne appropriée de votre organisation devez être en mesure de vous connecter ou de contacter votre fournisseur DNS (la société à laquelle vous avez acheté le domaine) et d&#39;effectuer des mises à jour dans vos paramètres DNS.

Pour ce faire, vous devez déterminer si vous devez configurer vos paramètres DNS sur un enregistrement `CNAME` ou Apex pointant votre nom de domaine personnalisé vers le nom de domaine de Cloud Manager. Un enregistrement `CNAME` ou A, une fois configuré, achemine tout le trafic Internet du domaine vers l’endroit où il pointe. Si cet emplacement n&#39;est pas configuré pour desservir le trafic, il y aura une panne. S’il n’a pas été testé, il se peut qu’il y ait des erreurs dans le contenu. C’est pourquoi cette étape est toujours effectuée une fois les tests terminés et que le client est prêt pour l’activation.

### Enregistrement CNAME {#cname-record}

Les sections suivantes vous aideront à déterminer quel type d&#39;enregistrement convient à votre configuration DNS.

Un nom ou un `CNAME` enregistrement canonique est un type d’enregistrement DNS qui mappe un nom d’alias à un nom de domaine vrai ou canonique. Les enregistrements CNAME sont généralement utilisés pour mapper un sous-domaine, par exemple `www.example.com` au domaine hébergeant le contenu de ce sous-domaine.

Connectez-vous à votre serveur d’enregistrement de domaine et créez un enregistrement CNAME pour pointer votre nom de domaine personnalisé vers la cible, comme indiqué ci-dessous :

| CNAME | Point de nom de domaine personnalisé vers la Cible |
|--- |--- |
| www.customdomain.com | cdn.adobeaemcloud.com |
