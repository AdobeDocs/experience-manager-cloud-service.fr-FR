---
title: Requêtes persistantes GraphQL - Activation de la mise en cache dans Dispatcher
description: Dispatcher est une couche de mise en cache et de sécurité pour les environnements de publication Adobe Experience Manager. Vous pouvez activer la mise en cache des requêtes persistantes dans AEM sans affichage.
feature: Dispatcher, GraphQL API
exl-id: 30a97e56-6699-41c4-a4eb-fc6236667f8f
source-git-commit: ea5b404e83c11f0057342bff22ba45e6b0ead124
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 8%

---

# Requêtes persistantes GraphQL - Activation de la mise en cache dans Dispatcher {#graphql-persisted-queries-enabling-caching-dispatcher}

>[!CAUTION]
>
>Si la mise en cache dans Dispatcher est activée, la fonction [Filtre CORS](/help/headless/deployment/cross-origin-resource-sharing.md) n’est pas nécessaire. Cette section peut donc être ignorée.

La mise en cache des requêtes persistantes n’est pas activée par défaut dans Dispatcher. L’activation par défaut n’est pas possible, car les clients qui utilisent le partage de ressources cross-origin (CORS) avec plusieurs origines doivent examiner et éventuellement mettre à jour leur configuration Dispatcher.

>[!NOTE]
>
>Dispatcher ne met pas en cache la variable `Vary` en-tête .
>
>La mise en cache d’autres en-têtes liés à CORS peut être activée dans Dispatcher, mais peut s’avérer insuffisante en cas d’origines CORS multiples.

>[!NOTE]
>
>Pour obtenir une documentation détaillée à propos du Dispatcher, veuillez consulter le [Guide du Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=fr).

## Activation de la mise en cache des requêtes persistantes {#enable-caching-persisted-queries}

Pour activer la mise en cache des requêtes persistantes, définissez la variable Dispatcher . `CACHE_GRAPHQL_PERSISTED_QUERIES`:

1. Ajout de la variable au fichier de Dispatcher `global.vars`:

   ```xml
   Define CACHE_GRAPHQL_PERSISTED_QUERIES
   ```

>[!NOTE]
>
>Lorsque la mise en cache de Dispatcher est activée pour les requêtes persistantes à l’aide de `Define CACHE_GRAPHQL_PERSISTED_QUERIES` an `ETag` L’en-tête est ajouté à la réponse par Dispatcher.
>
>Par défaut, la variable `ETag` header est configuré avec la directive suivante :
>
>```
>FileETag MTime Size 
>```
>
>Cependant, ce paramètre peut entraîner des problèmes lorsqu’il est utilisé pour les réponses de requête persistantes, car il ne tient pas compte des petites modifications apportées à la réponse.
>
>Pour atteindre un individu `ETag` calculs sur *each* réponse unique : `FileETag Digest` doit être utilisé dans la configuration du dispatcher :
>
>```xml
><Directory />    
>   ...    
>   FileETag Digest
></Directory> 
>```

>[!NOTE]
>
>Pour que la variable [Exigences de Dispatcher pour les documents pouvant être mis en cache](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/troubleshooting/dispatcher-faq.html#how-does-the-dispatcher-return-documents%3F), Dispatcher ajoute le suffixe `.json` à toutes les URL de requête conservées, de sorte que le résultat puisse être mis en cache.
>
>Ce suffixe est ajouté par une règle de réécriture, une fois la mise en cache de requête persistante activée.

## Configuration CORS dans Dispatcher {#cors-configuration-in-dispatcher}

Les clients qui utilisent des requêtes CORS doivent peut-être passer en revue et mettre à jour leur configuration CORS dans Dispatcher.

* La variable `Origin` L’en-tête ne doit pas être transmis à AEM publication via Dispatcher :
   * Vérifiez les `clientheaders.any` fichier .
* Au lieu de cela, les demandes CORS doivent être évaluées pour les origines autorisées au niveau de Dispatcher. Cette approche garantit également que les en-têtes liés à CORS sont correctement définis, à un seul endroit, dans tous les cas.
   * Une telle configuration doit être ajoutée à la variable `vhost` fichier . Vous trouverez ci-dessous un exemple de configuration. Pour plus de simplicité, seule la partie relative à CORS a été fournie. Vous pouvez l’adapter à vos cas d’utilisation spécifiques.

  ```xml
  <VirtualHost *:80>
     ServerName "publish"
  
     # ...
  
     <IfModule mod_headers.c>
         Header add X-Vhost "publish"
  
          ################## Start of the CORS specific configuration ##################
  
          SetEnvIfExpr "req_novary('Origin') == ''"  CORSType=none CORSProcessing=false
          SetEnvIfExpr "req_novary('Origin') != ''"  CORSType=cors CORSProcessing=true CORSTrusted=false
  
          SetEnvIfExpr "req_novary('Access-Control-Request-Method') == '' && %{REQUEST_METHOD} == 'OPTIONS' && req_novary('Origin') != ''  " CORSType=invalidpreflight CORSProcessing=false
          SetEnvIfExpr "req_novary('Access-Control-Request-Method') != '' && %{REQUEST_METHOD} == 'OPTIONS' && req_novary('Origin') != ''  " CORSType=preflight CORSProcessing=true CORSTrusted=false
          SetEnvIfExpr "req_novary('Origin') -strcmatch 'https://%{HTTP_HOST}*'"  CORSType=samedomain CORSProcessing=false
  
          # For requests that require CORS processing, check if the Origin can be trusted
          SetEnvIfExpr "%{HTTP_HOST} =~ /(.*)/ " ParsedHost=$1
  
          ################## Adapt the regex to match CORS origin for your environment
          SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://.*.your-domain.tld(:\d+)?$)#" CORSTrusted=true
  
          # Extract the Origin header 
          SetEnvIfNoCase ^Origin$ ^https://(.*)$ CORSTrustedOrigin=https://$1
  
          # Flush If already set
          Header unset Access-Control-Allow-Origin
          Header unset Access-Control-Allow-Credentials
  
          # Trusted
          Header always set Access-Control-Allow-Credentials "true" "expr=reqenv('CORSTrusted') == 'true'"
          Header always set Access-Control-Allow-Origin "%{CORSTrustedOrigin}e" "expr=reqenv('CORSTrusted') == 'true'"
          Header always set Access-Control-Allow-Methods "GET" "expr=reqenv('CORSTrusted') == 'true'"
          Header always set Access-Control-Max-Age 1800 "expr=reqenv('CORSTrusted') == 'true'"
          Header always set Access-Control-Allow-Headers "Origin, Accept, X-Requested-With, Content-Type, Access-Control-Request-Method, Access-Control-Request-Headers" "expr=reqenv('CORSTrusted') == 'true'"
  
          # Non-CORS or Not Trusted
          Header unset Access-Control-Allow-Credentials "expr=reqenv('CORSProcessing') == 'false' || reqenv('CORSTrusted') == 'false'"
          Header unset Access-Control-Allow-Origin "expr=reqenv('CORSProcessing') == 'false' || reqenv('CORSTrusted') == 'false'"
          Header unset Access-Control-Allow-Methods "expr=reqenv('CORSProcessing') == 'false' || reqenv('CORSTrusted') == 'false'"
          Header unset Access-Control-Max-Age "expr=reqenv('CORSProcessing') == 'false' || reqenv('CORSTrusted') == 'false'"
  
          # Always vary on origin, even if its not there.
          Header merge Vary Origin
  
          # CORS - send 204 for CORS requests which are not trusted
          RewriteCond expr "reqenv('CORSProcessing') == 'true' && reqenv('CORSTrusted') == 'false'"
          RewriteRule "^(.*)" - [R=204,L]
  
          ################## End of the CORS specific configuration ##################
  
     </IfModule>
  
     <Directory />
  
         # ...
  
     </Directory>
  
     # ...
  
  </VirtualHost>
  ```
