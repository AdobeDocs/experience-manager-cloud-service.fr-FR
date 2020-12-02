---
title: Vérification de l'état du nom de domaine
description: Vérification de l'état du nom de domaine
translation-type: tm+mt
source-git-commit: 5cd22d8af20bb947e4cdab448cf8f20c6596bb2e
workflow-type: tm+mt
source-wordcount: '810'
ht-degree: 0%

---


# Vérification du statut du nom de domaine {#check-status}

Vous pouvez déterminer si votre nom de domaine a bien été vérifié en cliquant sur l’icône État du nom de domaine dans le tableau Environnements de la page Paramètres de domaine.

>[!NOTE]
>Cloud Manager déclenche automatiquement une vérification TXT lorsque vous sélectionnez Enregistrer à l’étape de vérification de l’assistant Ajouter un domaine personnalisé. Pour les vérifications suivantes, vous devez sélectionner activement l’icône &quot;vérifier à nouveau&quot; en regard de l’état. INSÉRER UNE IMAGE

Cloud Manager vérifie la propriété du domaine via la valeur TXT et affiche l’un des messages d’état suivants :

* **La valeur**
FailedTXT de vérification de domaine est manquante ou est détectée avec des erreurs. Suivez les instructions et réessayez. Une fois prêt, vous devez sélectionner l’icône &quot;Vérifier à nouveau&quot; en regard de l’état.

* **Vérification du domaine en**
coursVérification en cours. Cet état s’affiche généralement après avoir sélectionné l’icône &quot;Vérifier à nouveau&quot; en regard de l’état.

* **Vérification vérifiée, la vérification**
FailedTXT du déploiement a réussi. Cependant, le déploiement du CDN a échoué. Un représentant d&#39;Adobe sera automatiquement averti.

* **Domaine vérifié et**
déployéCet état indique que votre nom de domaine personnalisé est prêt à être utilisé. Remarque : A ce stade, votre nom de domaine personnalisé est prêt à être testé et pointé vers le nom de domaine Cloud Manager. Accédez à Configuration des paramètres DNS INSERT LINK pour savoir comment procéder.

* ****
DeletingLa suppression du nom de domaine personnalisé est en cours.

* **Échec de la suppression**
Échec de la suppression du nom de domaine personnalisé. Vous devez réessayer. Accédez à Supprimer le nom de domaine personnalisé pour en savoir plus sur la rubrique.


## Configuration des paramètres DNS {#configure-dns}

Une fois votre nom de domaine personnalisé vérifié et déployé, vous êtes prêt à mettre à jour les enregistrements DNS de votre nom de domaine personnalisé avec votre fournisseur DNS. Cela permet à votre site de servir les visiteurs. Cette activité est donc généralement effectuée avant le lancement.

>[!NOTE]
>Vous ou la personne appropriée de votre organisation devez être en mesure de vous connecter ou de contacter votre fournisseur DNS (la société à laquelle vous avez acheté le domaine) et d&#39;effectuer des mises à jour dans vos paramètres DNS.

Pour ce faire, vous devez déterminer si vous devez configurer vos paramètres DNS sur un enregistrement `CNAME` ou Apex pointant votre nom de domaine personnalisé vers le nom de domaine Cloud Manager. Un enregistrement `CNAME` ou A, une fois configuré, achemine tout le trafic Internet du domaine vers l’endroit où il pointe. Si cet emplacement n&#39;est pas configuré pour desservir le trafic, il y aura une panne. S’il n’a pas été testé, il se peut qu’il y ait des erreurs dans le contenu. C’est pourquoi cette étape est toujours effectuée une fois les tests terminés et que le client est prêt pour l’activation.

### Enregistrement CNAME {#cname-record}

Les sections suivantes vous aideront à déterminer quel type d&#39;enregistrement convient à votre configuration DNS.

Un enregistrement Nom canonique ou `CNAME` est un type d&#39;enregistrement DNS qui mappe un nom d&#39;alias à un nom de domaine canonique ou vrai. Les enregistrements CNAME sont généralement utilisés pour mapper un sous-domaine tel que `www.example.com` au domaine hébergeant le contenu de ce sous-domaine.

Connectez-vous à votre serveur d’enregistrement de domaine et créez un enregistrement CNAME pour pointer votre nom de domaine personnalisé vers la cible, comme indiqué ci-dessous :

| CNAME | Point de nom de domaine personnalisé vers la Cible |
|--- |--- |
| www.customdomain.com | cdn.adobeaemcloud.com |

### Enregistrement APEX {#apex-record}

Un domaine apex est un domaine personnalisé qui ne contient pas de sous-domaine, tel que example.com. Un domaine apex est configuré avec un enregistrement `A`, `ALIAS` ou `ANAME` via votre fournisseur DNS. Les domaines Apex doivent pointer vers des adresses IP spécifiques.

Ajoutez tous les enregistrements A suivants aux paramètres DNS de votre domaine via votre fournisseur de domaine :

* `A RECORD`

* `A record for domain @ pointing to IP 151.101.3.10`

* `A record for domain @ pointing to IP 151.101.67.10`

* `A record for domain @ pointing to IP 151.101.131.10`

* `A record for domain @ pointing to IP 151.101.195.10`

## Vérification du statut de l&#39;enregistrement DNS {#check-status-dns-record}

Vous pouvez déterminer si votre nom de domaine est correctement résolu sur votre AEM en tant que site Web Cloud Service en cliquant sur l’icône État de l’enregistrement DNS dans le tableau de la page Environnements de la page Paramètres de domaine. Cloud Manager effectue une recherche DNS pour votre nom de domaine et affiche l’un des messages d’état suivants :

>[!NOTE]
>Cloud Manager déclenche automatiquement une recherche DNS lorsque votre nom de domaine personnalisé est vérifié et déployé pour la première fois. Pour les tentatives suivantes, vous devez sélectionner activement l&#39;icône **résoudre de nouveau** en regard de l&#39;état. INSÉRER UNE IMAGE

* **L&#39;état DNS non**
détectéL&#39;état DNS ne sera pas détecté tant que votre nom de domaine personnalisé n&#39;aura pas été vérifié et déployé avec succès. Cet état est également observé lorsque votre nom de domaine personnalisé est en cours de suppression.

* **Résolution DNS**
incorrectementCeci indique que la configuration des enregistrements DNS n&#39;a pas encore été résolue/pointée ou est erronée. Un représentant d&#39;Adobe sera automatiquement averti.

   >[!NOTE]
   >Vous devez configurer `CNAME` ou `A-record` en suivant les instructions correspondantes. Accédez à Configuration des paramètres DNS INSERT LINK pour en savoir plus sur la rubrique. Une fois prêt, vous devez sélectionner l’icône &quot;Résoudre&quot; en regard de l’état.

* **Résolution DNS en cours de**
progressionRésolution est en cours. Cet état s’affiche généralement après avoir sélectionné l’icône &quot;Résoudre&quot; en regard de l’état.

* **Résolution DNS**
CorrectementVos paramètres DNS sont correctement configurés. Votre site sert des visiteurs.
