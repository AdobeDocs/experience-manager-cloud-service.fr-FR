---
title: Résolution des erreurs 403 interdites lors de l’envoi du formulaire Edge Delivery Services
description: Découvrez comment diagnostiquer et résoudre les erreurs 403 Interdit lors de l’envoi de formulaires de Edge Delivery Services au service de publication AEM. Ce guide couvre les causes courantes, notamment les problèmes de CORS, de règles Dispatcher et de filtre de référent.
feature: Edge Delivery Services
role: Admin, Developer
exl-id: f397e059-f1b3-4afa-bd38-8f5fc591bb22
source-git-commit: d457bf9af377176222c2b96816fbbc4265e6b167
workflow-type: tm+mt
source-wordcount: '1118'
ht-degree: 3%

---

# Résolution des erreurs 403 interdites lors de l’envoi du formulaire Edge Delivery Services {#troubleshooting-403-forbidden-edge-delivery}

Lors de l’envoi de formulaires de Edge Delivery Services au service de publication AEM, vous pouvez rencontrer une erreur **403 Interdit**. Cette erreur indique que le serveur refuse de traiter la demande, généralement en raison de configurations de sécurité. Cet article vous aide à identifier et à résoudre les causes les plus courantes de ce problème.

## Description du problème

Les utilisateurs rencontrent une erreur **403 Interdit** lors de l’envoi de formulaires de Edge Delivery Services au service de publication AEM. L’erreur s’affiche comme suit :

- Code d’état HTTP : 403
- Message d’erreur : « Interdit » ou « Accès refusé »
- L’envoi du formulaire échoue sans atteindre le servlet d’envoi AEM

Ce problème se produit généralement dans les intégrations Edge Delivery Services où les formulaires hébergés sur des domaines Edge (`.aem.live`, `.aem.page`, `.hlx.page`, `.hlx.live`) tentent d’envoyer des données aux instances de publication AEM.

>[!IMPORTANT]
>
>Avec les configurations sans réponse, plusieurs sites peuvent être hébergés à l’aide du même référentiel. Chaque domaine de site doit être ajouté individuellement aux places sur la liste autorisée pour que les envois de formulaire fonctionnent correctement.
>
>**Exemple :**
>
>- Référentiel : `https://github.com/adobe/abc`
>- Site 1 : `main--abc--adobe.aem.live`
>- Site 2 : `main--abc1--adobe.aem.live`
>
>Les deux domaines ont besoin d’entrées de place sur la liste autorisée distinctes pour que l’envoi du formulaire fonctionne à partir des deux sites.

## Causes courantes et solutions

Une erreur 403 Interdit lors de l’envoi d’un formulaire Edge Delivery Services peut avoir plusieurs causes. Procédez comme suit pour résoudre les problèmes :

### &#x200B;1. Problèmes de partage des ressources entre origines multiples (CORS)

**Symptômes :**

- La console du navigateur affiche les messages d’erreur CORS
- L’onglet Réseau affiche la requête en cours de blocage avant d’atteindre le serveur
- Messages d’erreur mentionnant « Demande cross-origin bloquée »

**Diagnostic :**

1. Ouvrir les outils de développement du navigateur (F12)
2. Recherchez les messages d’erreur CORS dans l’onglet Console .
3. Recherchez des messages comme : `Access to fetch at 'https://publish-xxx.adobeaemcloud.com' from origin 'https://main--repo--owner.aem.live' has been blocked by CORS policy`

**Solution :**
Configurez les paramètres CORS dans AEM pour autoriser les requêtes provenant de vos domaines de site Edge Delivery spécifiques :

```apache
# Developer Localhost
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(http://localhost(:\d+)?$)#" CORSTrusted=true

# Edge Delivery Sites - Add each site domain individually
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://main--abc--adobe\.aem\.live$)#" CORSTrusted=true
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://main--abc1--adobe\.aem\.live$)#" CORSTrusted=true

# Legacy Franklin domains (if still in use)
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://.*\.hlx\.page$)#" CORSTrusted=true  
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://.*\.hlx\.live$)#" CORSTrusted=true
```

>[!NOTE]
>
>Remplacez `main--abc--adobe.aem.live` et `main--abc1--adobe.aem.live` par vos domaines de site réels. Chaque site hébergé à partir du même référentiel nécessite une entrée de configuration CORS distincte.

Pour la configuration CORS détaillée, reportez-vous au [Guide de configuration CORS](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/getting-started-with-aem-headless/deployments/configurations/cors).

### &#x200B;2. Règles Dispatcher

**Symptômes :**

- Une erreur 403 se produit sans messages CORS dans la console du navigateur
- La demande atteint le serveur mais est bloquée par Dispatcher
- Une erreur se produit avant d’atteindre la couche d’application AEM.

**Diagnostic :**

1. Vérifiez si l’URL de la requête correspond à une règle de filtrage Dispatcher
2. Consultez la configuration de Dispatcher pour connaître les règles de `/filter` susceptibles de bloquer les requêtes POST
3. Vérifiez que le point d’entrée d’envoi de formulaire est autorisé dans la configuration Dispatcher

**Solution :**
Mettez à jour la configuration de Dispatcher pour autoriser les demandes d’envoi de formulaire :

1. Assurez-vous que les requêtes POST aux points d’entrée d’envoi de formulaire sont autorisées.
2. Ajout de règles de filtrage appropriées pour les domaines Edge Delivery
3. Vérifiez que le chemin d’accès du servlet d’envoi n’est pas bloqué.

Exemple de configuration de filtre Dispatcher :

```apache
/filter {
  # Allow POST requests to form submission servlet
  /0100 { /type "allow" /method "POST" /url "/content/forms/af/*" }
  /0101 { /type "allow" /method "POST" /url "/adobe/forms/af/submit/*" }
  /0102 { /type "allow" /method "POST" /url "/content/forms/portal/submit/adaptiveform" }
}
```

### &#x200B;3. Problèmes De Filtre Référent

**Symptômes :**

- Erreur 403 sans problème CORS dans la console du navigateur
- La demande atteint AEM mais est rejetée par le filtre référent Sling.
- Une erreur se produit au niveau de la couche applicative AEM.

**Diagnostic :**
Consultez les journaux d’erreurs AEM pour connaître les messages de rejet de filtrage des référents :

1. [Accès aux journaux d’AEM Cloud Service via Cloud Manager](/help/implementing/cloud-manager/manage-logs.md)
2. Recherchez les entrées dans les `aemerror.log` contenant :
   - « Filtre référent rejeté »
   - « org.apache.sling.security.impl.ReferrerFilter »
   - Messages indiquant les échecs de validation du référent

**Exemple d’entrée de journal :**

```
[ERROR] org.apache.sling.security.impl.ReferrerFilter Referrer filter rejected request with referrer 'https://main--abc--adobe.aem.live' for POST /content/forms/af/submit
```

**Solution :**
Configurez le filtrage des référents pour autoriser vos domaines de site Edge Delivery spécifiques :

1. Créez ou mettez à jour le fichier de configuration OSGi : `org.apache.sling.security.impl.ReferrerFilter.cfg.json`

2. Ajoutez la configuration suivante à vos domaines de site spécifiques :

   ```json
   {
     "allow.empty": false,
     "allow.hosts": [
       "main--abc--adobe.aem.live",
       "main--abc1--adobe.aem.live"
     ],
     "allow.hosts.regexp": [
       "https://.*\\.aem\\.live:443",
       "https://.*\\.aem\\.page:443",
       "https://.*\\.hlx\\.page:443",
       "https://.*\\.hlx\\.live:443"
     ],
     "filter.methods": [
       "POST",
       "PUT",
       "DELETE",
       "COPY",
       "MOVE"
     ],
     "exclude.agents.regexp": [
       ""
     ]
   }
   ```

3. Déploiement de la configuration via Cloud Manager

>[!IMPORTANT]
>
>**Pour les configurations sans réponse :** vous devez ajouter chaque domaine de site individuellement au tableau `allow.hosts`. L’utilisation de modèles d’expression régulière uniquement peut ne pas suffire pour tous les scénarios. Incluez des domaines spécifiques et des modèles d’expression régulière pour une couverture complète.

>[!WARNING]
>
>Le filtre de référent AEM n’est pas une configuration d’usine OSGi, ce qui signifie qu’une seule configuration à la fois est active sur un service AEM. Dans la mesure du possible, évitez d’ajouter des configurations de filtre de référent personnalisées, car elles remplacent les configurations natives AEM et peuvent altérer la fonctionnalité du produit.

## Étapes de diagnostic

Pour identifier la cause spécifique de votre erreur 403, procédez comme suit :

### Étape 1 : vérifier la console du navigateur

1. Ouvrir les outils de développement du navigateur (F12)
2. Accédez à l’onglet Console .
3. Tenter l’envoi du formulaire
4. Rechercher les messages d’erreur liés à CORS

**Si des erreurs CORS sont présentes :** Suivez la solution CORS ci-dessus.
**Si aucune erreur CORS n’est détectée** Passez à l’étape 2.

### Étape 2 : vérifier l’onglet Réseau

1. Ouvrir les outils de développement du navigateur (F12)
2. Accédez à l’onglet Réseau .
3. Tenter l’envoi du formulaire
4. Vérifier les détails de la requête ayant échoué
5. Examiner les en-têtes et le statut des réponses

**Si la demande n’atteint pas le serveur :** il s’agit probablement d’un problème Dispatcher.
**Si la requête atteint le serveur mais échoue :** probablement un problème de filtrage des référents.

### Étape 3 : vérifier les journaux AEM

1. Accéder à Cloud Manager
2. Accédez à Environnements → votre environnement → Journaux .
3. Télécharger ou afficher des `aemerror.log`
4. Rechercher des entrées autour du moment d’envoi du formulaire
5. Recherchez le filtre Référent ou les messages liés à la sécurité.

## Prévention et bonnes pratiques

### &#x200B;1. Configuration Appropriée Pendant La Configuration

- Configurez les paramètres CORS, Dispatcher et Filtre de référent lors de la configuration initiale de Edge Delivery Services
- placer sur la liste autorisée **Pour chaque nouveau site :** Ajouter le domaine spécifique à tous les (CORS, filtrage des référents)
- Tester les envois de formulaire dans l’environnement de développement avant la mise en ligne

### &#x200B;2. Configurations Spécifiques À Un Environnement

- Utiliser différentes configurations pour les environnements de développement, d’évaluation et de production
- Inclure des domaines localhost pour les tests de développement local
- **Documenter tous les domaines de site** qui ont besoin d&#39;un accès de liste autorisée pour votre référentiel

### &#x200B;3. Surveillance et consignation

- Configurer la surveillance des journaux pour les rejets de filtrage des référents
- Implémenter une gestion des erreurs appropriée dans le code d’envoi du formulaire
- Utiliser les outils de développement du navigateur pendant le test

### &#x200B;4. Documentation et connaissances de l’équipe

- **Tenir à jour un registre** de tous les domaines de site utilisant le même référentiel
- Former l’équipe de développement aux étapes de dépannage
- Tenir à jour une liste de contrôle pour la configuration des formulaires Edge Delivery Services
- **Mettre à jour les listes autorisées** chaque fois que de nouveaux sites sont créés à partir de référentiels existants

## Gestion des domaines de site pour les configurations Reponses

Avec les architectures Helix-5 et Repoless, suivez ces instructions :

### Lors De La Création De Sites

1. **Identifier le domaine du site** (par exemple, `main--newsite--adobe.aem.live`)
2. **Mettez à jour la configuration CORS** pour inclure le nouveau domaine
3. **Mettez à jour le filtre Référent** pour inclure le nouveau domaine dans `allow.hosts`
4. **Tester l’envoi du formulaire** à partir du nouveau site
5. **Documentez le nouveau domaine** dans le registre de votre site

### Modèles de dénomination de domaine

- Modèle standard : `{branch}--{site}--{owner}.aem.live`
- Chaque site obtient un domaine unique même lors du partage du même référentiel
- Les domaines `.aem.live` et `.aem.page` peuvent être utilisés

### Gestion de la configuration

- Utiliser des entrées de domaine spécifiques dans `allow.hosts` pour une meilleure sécurité
- Compléter avec des modèles d’expression régulière pour une couverture plus large
- Vérifier et mettre à jour régulièrement les places sur la liste autorisée à mesure que des sites sont ajoutés ou supprimés

## Ressources supplémentaires

- [Configuration du filtre Référent avec AEM Headless](/help/headless/deployment/referrer-filter.md)
- [ Guide de configuration CORS ](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/getting-started-with-aem-headless/deployments/configurations/cors)
- [Comprendre le partage de ressources entre origines multiples (CORS)](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/foundation/security/understand-cross-origin-resource-sharing)
- [Documentation de Edge Delivery Services Forms](/help/edge/docs/forms/universal-editor/publish-forms.md)

## Rubriques connexes

- [Configuration des actions Envoyer](/help/forms/configuring-submit-actions.md)
- [Service d’envoi de formulaires](/help/forms/forms-submission-service.md)
- [Vue d’ensemble d’Edge Delivery Services](/help/edge/overview.md)


**Besoin d’aide supplémentaire ?** Si vous continuez à rencontrer des problèmes après avoir suivi ces étapes de dépannage, contactez le service clientèle d’Adobe avec :

- Vos messages d’erreur spécifiques
- Détails de l’environnement AEM Cloud Service
- **Tous les domaines de site Edge Delivery Services** qui nécessitent un accès pour l’envoi de formulaire
- Entrées de journal pertinentes à partir du moment de l’erreur

**Besoin d’aide supplémentaire ?** Si vous continuez à rencontrer des problèmes après avoir suivi ces étapes de dépannage, contactez le service clientèle d’Adobe avec :

- Vos messages d’erreur spécifiques
- Détails de l’environnement AEM Cloud Service
- Informations sur le domaine Edge Delivery Services
- Entrées de journal pertinentes à partir du moment de l’erreur
