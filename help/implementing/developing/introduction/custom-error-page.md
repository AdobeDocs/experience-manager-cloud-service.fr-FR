---
title: Pages d’erreur personnalisées
description: aem est fourni avec un gestionnaire d’erreurs standard pour la gestion des erreurs HTTP, qui peut être personnalisé.
translation-type: tm+mt
source-git-commit: d7e9bdee83f1b85436185ca57420ee178268cb33
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 50%

---


# Personnalisation des pages d’erreur {#customizing-error-pages}

aem est fourni avec un gestionnaire d’erreurs standard pour la gestion des erreurs HTTP ; par exemple, en affichant :

![Message d’erreur standard](assets/error-message-standard.png)

Pour répondre aux erreurs, AEM fournit un script `404.jsp` sous `/libs/sling/servlet/errorhandler`.

>[!TIP]
>
>Comme AEM est basé sur Apache Sling, des informations complémentaires sont disponibles [dans la documentation relative à la gestion des erreurs Apache.](https://sling.apache.org/documentation/the-sling-engine/errorhandling.html)

>[!NOTE]
>
>Sur une instance de création, le [Filtre de débogage de la gestion du contenu web CQ](/help/implementing/deploying/configuring-osgi.md) est activé par défaut. Cela donne toujours comme résultat le code de réponse 200. Le gestionnaire d’erreurs par défaut répond en écrivant la trace de pile complète sur la réponse.
>
>Sur une instance de publication, le filtre de débogage de la gestion du contenu web CQ est **toujours** désactivé (même s’il est configuré comme étant activé).

## Comment personnaliser les pages affichées par le gestionnaire d&#39;erreurs {#how-to-customize-pages-shown-by-the-error-handler}

Vous pouvez développer vos propres scripts afin de personnaliser les pages affichées par le gestionnaire d’erreurs lors de la détection d’une erreur. Pour ce faire, vous utiliserez [AEM mécanisme d’incrustation standard](/help/implementing/developing/introduction/overlays.md) afin que vos pages personnalisées soient créées sous `/apps` et que les pages par défaut sous `/libs` soient superposées.

1. Dans le référentiel, copiez le(s) script(s) par défaut :

   * de `/libs/sling/servlet/errorhandler/`
   * vers `/apps/sling/servlet/errorhandler/`

   Le chemin de destination n&#39;existe pas par défaut. Vous devez donc le créer lors de cette opération pour la première fois.

1. Accédez à `/apps/sling/servlet/errorhandler`. Ici, vous pouvez effectuer l’une des opérations suivantes :

   * Modifier le script existant approprié pour fournir les informations requises. Ou
   * Créer un script, et le modifier, pour le code requis.

1. Enregistrez les modifications et effectuez un test.

>[!CAUTION]
>
>Le script `404.jsp` a été spécialement conçu pour répondre à l&#39;authentification AEM ; en particulier, pour permettre la connexion au système en cas de ces erreurs.
>
>Par conséquent, le remplacement de ce script devrait être effectué avec beaucoup de soin.

### Personnalisation de la réponse aux erreurs HTTP 500 {#customizing-the-response-to-http-errors}

L&#39;erreur interne du serveur HTTP [500 ](https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html) indique une erreur côté serveur telle que le serveur qui a rencontré une condition inattendue l&#39;empêchant de satisfaire la demande.

Lorsque le traitement des requêtes génère une exception, la structure Apache Sling (sur laquelle AEM est basé) :

* Consigne l&#39;exception
* Et revient dans le corps de la réponse :
   * Code de réponse HTTP 500
   * Suivi de la pile d&#39;exceptions

La [personnalisation des pages affichées par le gestionnaire d’erreurs](#how-to-customize-pages-shown-by-the-error-handler) permet de créer un script `500.jsp`. Cependant, elle n&#39;est utilisée que si `HttpServletResponse.sendError(500)` est exécuté explicitement ; c&#39;est-à-dire à partir d&#39;un attrapeur d&#39;exceptions.

Dans le cas contraire, le code de réponse est défini sur , mais le script `500.jsp`500.  n’est pas exécuté.

Pour gérer les erreurs de type 500, le nom de fichier du script de gestionnaire d’erreurs doit être identique à la classe d’exception (ou superclasse). Pour gérer toutes ces exceptions, vous pouvez créer un script `/apps/sling/servlet/errorhandler/Throwable.jsp` ou `/apps/sling/servlet/errorhandler/Exception.jsp`.

>[!CAUTION]
>
>Sur une instance de création, le [Filtre de débogage de la gestion du contenu web CQ](/help/implementing/deploying/configuring-osgi.md) est activé par défaut. Cela donne toujours comme résultat le code de réponse 200. Le gestionnaire d’erreurs par défaut répond en écrivant la trace de pile complète sur la réponse.
>
>Des réponses avec le code 500 sont nécessaires pour un gestionnaire d’erreurs personnalisé. Par conséquent, le [filtre de débogage de la gestion du contenu web CQ doit être désactivé.](/help/implementing/deploying/configuring-osgi.md) Cela garantit le renvoi du code de réponse 500 qui, à son tour, déclenche le gestionnaire d’erreurs Sling approprié.
>
>Sur une instance de publication, le filtre de débogage de la gestion du contenu web CQ est **toujours** désactivé (même s’il est configuré comme étant activé).
