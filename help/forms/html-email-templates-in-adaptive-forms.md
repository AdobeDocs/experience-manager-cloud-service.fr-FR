---
title: HTML des modèles d’e-mail dans le Forms adaptatif sur Forms as a Cloud Service
description: Découvrez comment utiliser des modèles d’e-mail avec des formulaires adaptatifs.
feature: Adaptive Forms, Core Components
role: User, Developer
hide: true
hidefromtoc: true
source-git-commit: 9d5950793f5b3e3c3d6229b9de9d5c020a164dd7
workflow-type: tm+mt
source-wordcount: '776'
ht-degree: 4%

---

# Modèles d’e-mail dans Adaptive Forms

Le Forms adaptatif permet d’utiliser des modèles d’e-mail en texte brut et HTML. Les modèles d’e-mail d’HTML vous permettent d’envoyer des e-mails riches, personnalisés et visuellement attrayants lorsqu’un formulaire est envoyé. Ces e-mails peuvent être personnalisés avec des données de formulaire et améliorés à l’aide de différentes balises d’e-mail, telles que des images et des liens. Avec le Forms adaptatif, vous pouvez charger un fichier contenant un modèle HTML ou utiliser un éditeur de texte brut pour créer ces modèles.

![HTML de modèles d’e-mail](/help/forms/assets/html-email.png)

Cet article vous aide à configurer et à utiliser des modèles d’e-mail dans le Forms adaptatif. À la fin, vous pourrez :

* [Configuration d’un modèle d’HTML pour un formulaire adaptatif](#configure-an-html-template-for-an-adaptive-form)
* [Configuration d’un modèle d’e-mail en texte brut pour un formulaire adaptatif](#configure-a-plain-text-template-for-an-adaptive-form)
* [Utiliser des données de formulaire dans vos modèles d’e-mail](#use-form-data-in-your-email-templates)


Voici un aperçu rapide des étapes impliquées :

1. Ouvrez le formulaire adaptatif pour le modifier.
1. Configurez l’action d’envoi [ Envoyer un e-mail ](/help/forms/configure-submit-action-send-email.md).
1. Sélectionnez ou chargez un modèle d’HTML ou saisissez manuellement le modèle d’e-mail.
1. Testez la configuration de votre e-mail.

## Configuration d’un modèle d’HTML pour un formulaire adaptatif

Vous pouvez configurer un formulaire adaptatif pour envoyer un e-mail lors de l’envoi à l’aide de l’action d’envoi [**Envoyer un e-mail**. ](/help/forms/configure-submit-action-send-email.md) L’action propose deux méthodes pour configurer un modèle d’HTML :

### Option 1 : sélectionner un fichier contenant le modèle d’HTML

Avant de poursuivre, assurez-vous d’avoir chargé le modèle HTML dans votre environnement AEM Forms.

1. Ouvrez le formulaire adaptatif pour le modifier.
1. Accédez au **Explorateur de contenu**, sélectionnez le **Conteneur de guide** et appuyez sur l’icône de propriétés. Une boîte de dialogue avec le titre `Adaptive Form Container` s’affiche.
1. Accédez à l’onglet **Envoi** et sélectionnez l’action d’envoi **Envoyer un e-mail**.
1. Activez l’option **Utiliser un modèle externe**.
1. Activez l’option **Utiliser un modèle d’HTML**.
1. Cliquez sur l’icône de dossier pour l’option Chemin d’accès au modèle externe et recherchez et sélectionnez votre modèle d’HTML.
1. Cliquez sur Terminé pour enregistrer la configuration.

Votre modèle HTML est maintenant configuré pour le formulaire adaptatif.

### Option 2 : saisir ou coller manuellement un modèle HTML

1. Ouvrez le formulaire adaptatif pour le modifier.
1. Accédez au **Explorateur de contenu**, sélectionnez le **Conteneur de guide** et appuyez sur l’icône de propriétés. Une boîte de dialogue avec le titre `Adaptive Form Container` s’affiche.
1. Accédez à l’onglet **Envoi** et sélectionnez l’action d’envoi **Envoyer un e-mail**.
1. Activez l’option **Utiliser un modèle externe**.
1. Activez l’option **Utiliser un modèle d’HTML**.
1. Saisissez ou collez votre code d’HTML directement dans la zone **Modèle d’e-mail** fournie.


## Configuration d’un modèle de texte brut pour un formulaire adaptatif

Vous pouvez configurer un formulaire adaptatif pour envoyer un e-mail lors de l’envoi à l’aide de l’action d’envoi [**Envoyer un e-mail**. ](/help/forms/configure-submit-action-send-email.md) L’action propose deux méthodes pour configurer un modèle de texte brut :

### Option 1 : sélectionner un fichier contenant le modèle

Avant de poursuivre, assurez-vous d’avoir chargé le modèle HTML dans votre environnement AEM Forms.

1. Ouvrez le formulaire adaptatif pour le modifier.
1. Accédez au **Explorateur de contenu**, sélectionnez le **Conteneur de guide** et appuyez sur l’icône de propriétés. Une boîte de dialogue avec le titre `Adaptive Form Container` s’affiche.
1. Accédez à l’onglet **Envoi** et sélectionnez l’action d’envoi **Envoyer un e-mail**.
1. Activez l’option **Utiliser un modèle externe**.
1. Cliquez sur l’icône de dossier de l’option **Chemin d’accès au modèle externe** et recherchez votre modèle de texte brut.
1. Cliquez sur Terminé pour enregistrer la configuration.

Votre modèle est maintenant configuré pour le formulaire adaptatif.

### Option 2 : saisir ou coller manuellement un modèle HTML

1. Ouvrez le formulaire adaptatif pour le modifier.
1. Accédez au **Explorateur de contenu**, sélectionnez le **Conteneur de guide** et appuyez sur l’icône de propriétés. Une boîte de dialogue avec le titre `Adaptive Form Container` s’affiche.
1. Accédez à l’onglet **Envoi** et sélectionnez l’action d’envoi **Envoyer un e-mail**.
1. Saisissez ou collez votre code de modèle en texte brut directement dans la zone **Modèle d’e-mail** fournie.

## Utilisation de données de formulaire dans vos modèles d’e-mail

Vous pouvez inclure des données de formulaire dans vos modèles d’e-mail à l’aide d’espaces réservés. Ces espaces réservés sont remplacés dynamiquement par des valeurs de champ de formulaire réelles lorsque l’e-mail est envoyé. Par exemple :

* ${name} : valeur du champ nommé « name ».
* ${email} : valeur du champ nommé « email ».
* ${message} : valeur du champ nommé « message ».

### Exemple de modèle d’e-mail d’HTML

Voici un exemple de modèle d’e-mail HTML qui utilise des espaces réservés de données de formulaire :

```HTML
    <!DOCTYPE html>
    <html>
    <head>
        <title>Form Submission</title>
        <style>
            body {
                font-family: Arial, sans-serif;
                line-height: 1.6;
                color: #333;
            }
            h2 {
                color: #0056b3;
            }
        </style>
    </head>
    <body>
        <h2>Thank You for Your Submission</h2>
        <p>Dear ${name},</p>
        <p>We have received your submission with the following details:</p>
        <ul>
            <li><strong>Email:</strong> ${email}</li>
            <li><strong>Phone Number:</strong> ${phone_number}</li>
            <li><strong>Message:</strong> ${message}</li>
        </ul>
        <p>We will get back to you soon!</p>
        <p>Best regards,</p>
        <p>Your Team</p>
    </body>
    </html>
```

### Exemple de modèle d’e-mail en texte brut

Voici un exemple de modèle d’e-mail en texte brut :

```TXT
    
    Subject: Thank You for Your Submission
    
    Dear ${name},
    
    We have received your submission with the following details:
    
    - Email: ${email}
    - Phone Number: ${phone_number}
    - Message: ${message}
    
    We will get back to you soon!
    
    Best regards,
    Your Team
```

Remplacez les espaces réservés (${name}, ${email}, etc.) par les noms de champ de formulaire correspondants dans votre formulaire adaptatif.

## Bonnes pratiques relatives aux modèles d’e-mail HTML

* Assurez-vous que vos styles sont intégrés pour une meilleure compatibilité avec les clients de messagerie.
* Rendez votre modèle réactif pour une meilleure expérience sur les appareils mobiles.
* Utilisez des outils tels que Litmus ou Email on Acid pour prévisualiser votre e-mail sur différents clients de messagerie.
* Assurez-vous que les noms des espaces réservés correspondent exactement aux noms des champs du formulaire.
* Recherchez les balises manquantes ou incorrectes dans votre modèle d’HTML.
* Vérifiez que l’action d’envoi [ Envoyer un e-mail ](/help/forms/configure-submit-action-send-email.md) est correctement configurée.
