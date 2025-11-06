---
title: Pages d’erreur personnalisées
description: AEM s’accompagne d’un outil standard destiné à la gestion des erreurs HTTP, qui peut être personnalisé.
exl-id: b74c65d1-8ef5-4ad4-8255-8187f3b1d84c
feature: Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 91%

---

# Personnalisation des pages d’erreur {#customizing-error-pages}

AEM s’accompagne d’un outil standard destiné à la gestion des erreurs HTTP, en affichant, par exemple :

![Message d’erreur standard](assets/error-message-standard.png)

Pour répondre aux erreurs, AEM fournit un script `404.jsp` sous `/libs/sling/servlet/errorhandler`.

>[!TIP]
>
>AEM étant basé sur Apache Sling, des informations supplémentaires sont disponibles [dans la documentation sur le traitement des erreurs Apache](https://sling.apache.org/documentation/the-sling-engine/errorhandling.html).

>[!NOTE]
>
>Sur une instance de création, le [filtre de débogage de la gestion du contenu web CQ](/help/implementing/deploying/configuring-osgi.md) est activé par défaut. Le code de réponse est toujours 200. Le gestionnaire d’erreurs par défaut répond en écrivant la trace de la pile complète à la réponse.
>
>Sur une instance de publication, le filtre de débogage de la gestion du contenu web CQ est **toujours** désactivé (même s’il est configuré comme étant activé).

>[!NOTE]
>
>Pour plus d’informations sur la gestion des erreurs avec le Dispatcher, voir [Configuration des pages d’erreur du réseau CDN](/help/implementing/dispatcher/cdn-error-pages.md).

## Méthode de personnalisation des pages affichées par le gestionnaire d’erreurs {#how-to-customize-pages-shown-by-the-error-handler}

Vous pouvez développer vos propres scripts afin de personnaliser les pages affichées par le gestionnaire d’erreurs lors de la détection d’une erreur. Vous utiliserez pour cela le [mécanisme de recouvrement standard d’AEM &#x200B;](/help/implementing/developing/introduction/overlays.md) afin que vos pages personnalisées soient créées sous `/apps` et recouvrent les pages par défaut sous `/libs`.

1. Dans le référentiel, copiez le ou les scripts par défaut :

   * de `/libs/sling/servlet/errorhandler/`
   * vers `/apps/sling/servlet/errorhandler/`

   Le chemin de destination n’existe pas par défaut. Vous devez donc le créer lorsque vous effectuez cette opération pour la première fois.

1. Accédez à `/apps/sling/servlet/errorhandler`. Ici, vous pouvez effectuer l’une des opérations suivantes :

   * Modifier le script existant approprié pour fournir les informations requises Ou
   * Créer un script, et le modifier, pour le code requis

1. Enregistrez les modifications et effectuez un test.

>[!CAUTION]
>
>Le script `404.jsp` a été spécialement conçu pour permettre l’authentification AEM, et en particulier la connexion au système si ces erreurs surviennent.
>
>Le remplacement de ce script doit donc être effectué avec précaution.

### Personnalisation de la réponse aux erreurs HTTP 500 {#customizing-the-response-to-http-errors}

[500 – Erreur interne du serveur](https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html) HTTP indique une erreur côté serveur, par exemple que le serveur a rencontré une condition inattendue l’empêchant de satisfaire la demande.

Lorsque le traitement des demandes provoque une exception, la structure Apache Sling (sur laquelle AEM est basé) :

* Consigne l’exception
* Et renvoie dans le corps de la réponse :
   * Le code de réponse HTTP 500
   * La trace de la pile d’exception

La [personnalisation des pages affichées par le gestionnaire d’erreurs](#how-to-customize-pages-shown-by-the-error-handler) permet de créer un script `500.jsp`. Cependant, il n’est utilisé que si `HttpServletResponse.sendError(500)` est exécuté de manière explicite ; c’est-à-dire à partir d’un détecteur d’exceptions.

Dans le cas contraire, le code de réponse est défini sur 500, mais le script `500.jsp` n’est pas exécuté.

Pour gérer les erreurs de type 500, le nom de fichier du script de gestionnaire d’erreurs doit être identique à la classe d’exception (ou superclasse). Pour gérer toutes ces exceptions, vous pouvez créer un script `/apps/sling/servlet/errorhandler/Throwable.jsp` ou `/apps/sling/servlet/errorhandler/Exception.jsp`.

>[!NOTE]
>
>Dans AEM as a Cloud Service, le réseau CDN diffuse une page d’erreur générique lorsqu’une erreur 5XX est reçue du serveur principal. Pour permettre au back-end de transmettre la réponse, vous devez ajouter l’en-tête suivant à la réponse : `x-aem-error-pass: true`.
>Cela ne fonctionne que pour les réponses provenant d’AEM ou de la couche Apache/Dispatcher. D’autres erreurs inattendues provenant des couches d’infrastructure intermédiaires afficheront toujours la page d’erreur générique.

>[!CAUTION]
>
>Sur une instance de création, le [filtre de débogage de la gestion du contenu web CQ](/help/implementing/deploying/configuring-osgi.md) est activé par défaut. Le code de réponse est toujours 200. Le gestionnaire d’erreurs par défaut répond en écrivant la trace de la pile complète à la réponse.
>
>Des réponses avec le code 500 sont nécessaires pour un gestionnaire d’erreurs personnalisé. Par conséquent, le [filtre de débogage de la gestion du contenu web CQ doit être désactivé](/help/implementing/deploying/configuring-osgi.md). Cela garantit le renvoi du code de réponse 500 qui, à son tour, déclenche le gestionnaire d’erreurs Sling approprié.
>
>Sur une instance de publication, le filtre de débogage de la gestion du contenu Web CQ est **toujours** désactivé (même s’il est configuré comme étant activé).
