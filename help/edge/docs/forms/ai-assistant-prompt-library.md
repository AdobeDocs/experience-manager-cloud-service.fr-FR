---
title: Assistant AEM Forms AI - Bibliothèque d’invites
description: Collection de modèles d’invite éprouvés et d’exemples pour créer des formulaires avec l’aide de l’IA dans l’interface utilisateur de gestion de Forms, l’éditeur de Forms adaptatif et l’éditeur universel.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
role: Admin, Architect, Developer
source-git-commit: d3ade6ee9216b44b55d6808d8acffe83f1e263c9
workflow-type: tm+mt
source-wordcount: '1613'
ht-degree: 0%

---



# Assistant AEM Forms AI - Bibliothèque d’invites

Collection de modèles d’invite réutilisables et d’exemples pour les scénarios courants de création de formulaires. Considérez-les comme des modèles que vous pouvez adapter à vos besoins spécifiques. Chaque section couvre un cas d’utilisation particulier avec des conseils sur son utilisation et des exemples éprouvés.

>[!NOTE]
>
> L’assistant AI pour AEM Forms est disponible dans le cadre du programme destiné aux utilisateurs et utilisatrices précoces. Envoyez un e-mail à mailto:aem-forms-ea@adobe.com à partir de votre adresse professionnelle pour demander l’accès.

>[!IMPORTANT]
>
> **Documentation sujette à modification** : cette bibliothèque d’invites est en cours de test par rapport au produit et est sujette à des mises à jour et des révisions. Les invites, les exemples et les bonnes pratiques peuvent changer à mesure que l&#39;assistant AI pour AEM Forms continue d&#39;évoluer pendant le programme des utilisateurs et utilisatrices précoces.

## Bonnes pratiques pour des résultats optimaux

Pour tirer le meilleur parti de l’assistant d’IA, tenez compte des conseils suivants :

### Démarrer Simple, Créer Progressivement

Commencez par des commandes plus petites et spécifiques (par exemple, « Ajouter une entrée de texte pour « Prénom ») plutôt que par des requêtes à plusieurs étapes trop complexes. Cette approche permet d’assurer la précision et facilite la résolution des problèmes si quelque chose ne fonctionne pas comme prévu.

**Exemple de démarrage simple :**

```
Add a text input field for "First Name" with placeholder "Enter your first name"
```

**Ensuite, Créer Incrémentiellement :**

```
Make @firstName mandatory and add validation message "First name is mandatory"
```

### Utiliser la terminologie AEM Forms

Utilisez des termes tels que « panneau », « champ de saisie de texte », « groupe de cases à cocher », « action d’envoi », « règle », etc., pour une meilleure compréhension par l’assistant. Cela permet de s’assurer que l’IA interprète correctement vos requêtes dans le contexte d’AEM Forms.

**Termes privilégiés :**

- « champ de saisie de texte » au lieu de « zone de texte »
- « checkbox group » au lieu de « checkboxes »
- « liste déroulante » au lieu de « sélectionner la liste »
- « panel » au lieu de « section » ou « conteneur »
- « action envoyer » au lieu de « envoi du formulaire »
- « règle » au lieu de « logique » ou « condition »

### Référencez les champs clairement

Lors de la configuration de champs existants, utilisez la notation @fieldName (par exemple, « Rendre le @firstName obligatoire »). Cela permet à l’IA d’identifier exactement le champ auquel vous faites référence, en particulier dans les formulaires complexes comportant de nombreux champs.

**Exemples :**

- `Make @email mandatory with real-time validation`
- `Show @spouseInfo panel when @maritalStatus equals "Married"`
- `Set @country default value to "United States"`

### Consulter toujours les plans

Examinez toujours attentivement les plans pour les modifications proposées par l’assistant dans l’éditeur universel avant de cliquer sur « Appliquer ». L’IA vous montrera ce qu’elle prévoit de faire, prenez le temps de vérifier que cela correspond à vos attentes.

### Validation manuelle

Une fois que l’assistant a apporté des modifications, prévisualisez et testez toujours votre formulaire pour vous assurer qu’il se comporte et s’affiche comme prévu. L’IA est un outil puissant, mais la validation finale est essentielle pour garantir la qualité.

**Liste de contrôle de validation :**

- Tester la fonctionnalité de formulaire en mode d’aperçu
- Vérifier que la logique conditionnelle fonctionne correctement
- Vérifier la réactivité mobile
- Tester un envoi de formulaire
- Validation des fonctionnalités d’accessibilité

### Itérer et affiner

Si la première invite ne donne pas le résultat exact, essayez de reformuler ou de ventiler la requête en plus petites étapes. L’IA apprend du contexte, de sorte que fournir des détails plus spécifiques améliore souvent les résultats.

**Exemple d’itération :**

1. Première tentative : « Rendre le formulaire compatible avec les appareils mobiles »
2. Affiné : « Optimisez la disposition des formulaires pour les écrans mobiles de moins de 768 pixels avec une disposition à une seule colonne et des cibles tactiles plus grandes »

### Fournir un retour d’informations

Utilisez le mécanisme de retour d&#39;informations intégré pour aider l&#39;assistant à apprendre et à s&#39;améliorer. Vos commentaires contribuent à rendre l’IA meilleure pour tous.


## Exemples de développement incrémentiel

Ces exemples montrent comment créer des formulaires pas à pas, en commençant par simple et en ajoutant progressivement de la complexité :

### Exemple 1 : création incrémentielle d’un formulaire de contact

**Étape 1 - Démarrage simple :**

```
Create a basic contact form with name, email, and message fields
```

**Étape 2 - Ajouter la validation :**

```
Make @name and @email mandatory fields with appropriate validation
```

**Étape 3 - Améliorer l’expérience utilisateur :**

```
Add placeholder text: @name "Your full name", @email "your.email@company.com", @message "Tell us how we can help"
```

**Étape 4 - Ajout de fonctionnalités avancées :**

```
Add a dropdown @inquiryType with options: "General Question", "Support Request", "Sales Inquiry", "Partnership"
```

**Étape 5 - Implémenter Une Logique Conditionnelle :**

```
Show @urgencyLevel dropdown (Low, Medium, High) only when @inquiryType equals "Support Request"
```

### Exemple 2 : création incrémentielle d’un formulaire d’enregistrement

**Étape 1 - Structure de base :**

```
Create a user registration form with personal information panel
```

**Étape 2 - Ajouter des champs principaux :**

```
Add text input fields: @firstName, @lastName, @email, @phone to the personal information panel
```

**Étape 3 - Ajouter la validation :**

```
Make @firstName, @lastName, and @email mandatory with real-time validation
```

**Étape 4 - Ajout des informations de compte :**

```
Create a new panel "Account Information" with @username and @password fields
```

**Étape 5 - Amélioration de la sécurité :**

```
Add password confirmation field @confirmPassword with validation to match @password
```

**Étape 6 - Ajouter des préférences :**

```
Create "Preferences" panel with @newsletter checkbox and @communicationMethod radio group (Email, SMS, Phone)
```

Cette approche incrémentielle vous permet d’effectuer les opérations suivantes :

- Intercepter les problèmes avant qu’ils ne se multiplient
- Tester minutieusement chaque fonctionnalité
- Effectuer des ajustements en fonction des commentaires de l’utilisateur
- Mieux contrôler le processus de développement

## Démarrer un nouveau Forms

**Utilisation :** au début d’un projet de formulaire. Cette invite aide l’IA à comprendre vos besoins et à créer la structure de base.

**Utilisation :** Commencez par la structure de base et les exigences principales. Spécifiez le type de formulaire, l’audience cible et l’objectif principal. Ajoutez de la complexité dans les invites suivantes.

**Exemple d’invite - Démarrage simple :**

```
Create a **customer onboarding form** for new bank account applications with:

**Purpose:** Collect personal information for account setup
**Target Users:** New customers applying for checking/savings accounts
**Basic Structure:** Single panel with essential fields
**Core Fields:** Name, email, phone, account type selection

Start with a simple layout that we can enhance step by step.
```

**Ensuite, Créer Incrémentiellement :**

```
Add an address panel to @customerOnboardingForm with street address, city, state, and zip code fields
```

```
Add employment information panel with @employer, @jobTitle, and @annualIncome fields
```

```
Add file upload field @identityDocuments for identity verification (Accept: .pdf,.jpg,.png)
```

**Autres invites de démarrage simples :**

```
Create a basic **event registration form** with name, email, and event selection fields
```

```
Build a simple **contact form** with name, email, and message fields
```

```
Design a basic **feedback survey** with rating scale and comments field
```

## Structure et disposition du formulaire

**Utilisation :** lorsque vous devez organiser des formulaires complexes ou améliorer l’expérience utilisateur grâce à une meilleure conception de la disposition.

**Utilisation :** Concentrez-vous sur le parcours utilisateur et le regroupement logique des informations. Spécifiez les préférences de disposition et les modèles de navigation.

**Exemple d’invite - Structure de formulaire à plusieurs étapes :**

```
Convert this single-page form into a **3-step wizard** with:

**Step 1: Personal Information**
- Name, email, phone, address fields
- Progress indicator showing "Step 1 of 3"
- "Next" button (validate mandatory fields before proceeding)

**Step 2: Preferences & Requirements** 
- Service selection (checkbox group)
- Budget range (dropdown)
- Timeline preferences (radio group)
- Special requirements (text input field)

**Step 3: Review & Submit**
- Summary of all entered information
- Edit links to go back to specific steps
- Terms and conditions checkbox
- Submit button with confirmation

Include "Previous" and "Next" buttons, allow users to jump between completed steps, save progress automatically.
```

**Invites d’optimisation de la mise en page :**

```
Reorganize this form using a **wizard layout** for desktop and single column for mobile. 
```

```
Convert this long form into an **accordion layout** where users can expand/collapse sections.
```

```
Create a **vertical tabbed interface** for this form with tabs for: Basic Info, Contact Details, Preferences, and Review.
```

## Gestion et validation des champs

**Utilisation :** lorsque vous devez ajouter, modifier ou améliorer des champs de formulaire avec des règles et des comportements de validation spécifiques.

**Utilisation :** être précis sur les types de champs, les exigences de validation et les attentes en matière d’expérience utilisateur. Référencez des champs existants à l’aide de la syntaxe @fieldName.

**Exemple d’invite - Amélioration du champ :**

```
Enhance the form fields with these specific requirements:

**Email Field (@email):**
- Make mandatory with real-time validation
- Show green checkmark when valid format entered
- Display helpful error message: "Please enter a valid email address"
- Add placeholder: "your.email@company.com"

**Phone Number (@phone):**
- Type: tel for mobile optimization
- Make mandatory for business customers, optional for personal
- Add placeholder: "Enter your phone number"

**Date of Birth (@dateOfBirth):**
- Type: date with date picker
- Validate age is 18+ for account opening
- Show error if under 18: "Must be 18 or older to open account"

**File Upload (@documents):**
- Accept: .pdf,.doc,.docx
- Multiple: true for multiple document upload
- Show upload progress and file names after upload
```

**Invites Spécifiques Au Champ :**

```
Add a **file upload field** for resume with these specs: Accept only PDF/DOC/DOCX files, allow multiple files, show upload progress, display file names after upload.
```

```
Create a **dropdown field** for country selection with all countries listed. Set default value based on user's location if available.
```

```
Build a **repeatable panel** for work experience where users can add/remove multiple jobs. Each entry needs: company, title, start date, end date, description.
```

## Logique et règles conditionnelles

**Utilisation :** lorsque vous avez besoin d’un comportement de formulaire dynamique basé sur des entrées utilisateur ou des règles métier.

**Utilisation :** définissez clairement les conditions et les actions qui en résultent. Utilisez des références de champ spécifiques et des opérateurs logiques.

**Exemple d’invite - Logique conditionnelle complexe :**

```
Implement these conditional rules for the application form:

**Business vs Personal Account Logic:**
- If @accountType equals "Business", show:
  - Business name field (mandatory)
  - Tax ID field (mandatory)
  - Business address section
  - Number of employees dropdown
- If @accountType equals "Personal", hide all business fields

**Income-Based Requirements:**
- If @annualIncome is less than 25000:
  - Show additional verification section
  - Make co-signer information mandatory
  - Display message: "Additional documentation may be required"
- If @annualIncome is greater than 100000:
  - Show premium services options
  - Enable priority processing checkbox

**Age-Based Validation:**
- If @age is under 18:
  - Show parent/guardian information section
  - Make parent signature upload mandatory
  - Change submit button text to "Submit for Review"
- If @age is 65 or older:
  - Show senior discount options
  - Add accessibility preferences section
```

**Invites Spécifiques Aux Règles :**

```
Create a **visibility rule** that shows @spouseInformation panel only when @maritalStatus equals "Married" or "Domestic Partnership".
```

```
Add **progressive disclosure** where additional questions appear based on previous answers. Start with basic info, then show relevant follow-ups.
```

```
Implement **smart defaults** where @country selection auto-sets related fields. Allow manual override.
```

## Intégration et envoi de données

**Utilisation :** lorsque vous devez connecter des formulaires à des systèmes principaux, des bases de données ou des services externes.

**Utilisation :** commencez par la configuration de base de l’envoi, puis ajoutez des intégrations supplémentaires de manière incrémentielle. Spécifiez le type d’intégration, les exigences en matière de format de données et les préférences de gestion des erreurs.

**Exemple d’invite - Commencer par l’envoi de base :**

```
Configure basic form submission for @applicationForm:

**Primary Submission:**
- Send form data to REST endpoint: `/api/v1/applications`
- Format data as JSON
- Show success message: "Application submitted successfully"
- Show error message if submission fails: "Submission failed, please try again"
```

**Ajoutez Ensuite Des Actions Secondaire De Manière Incrémentielle :**

```
Add email notification to @applicationForm: Send confirmation email to @email address with application reference number
```

```
Add CRM integration to @applicationForm: Create new lead record with @firstName, @lastName, @email, and set Status to "New Application"
```

**Exemple d’invite - Envoi multicanal avancé :**

```
Configure form submission with multiple data destinations:

**Primary Submission:**
- Send form data to REST endpoint: `/api/v1/applications`
- Include authentication header with API key
- Format data as JSON with nested objects for address and employment
- Handle success response (201) by showing thank you message

**Secondary Actions:**
- Send notification email to applicant at @email address
- Copy application data to tracking system
- Trigger workflow for approval process
- Create record in CRM with lead status "New Application"

**Error Handling:**
- If primary submission fails, save data locally and retry
- Show user-friendly error message: "Submission temporarily unavailable"
- Provide option to download form data as backup
- Send alert email to admin team about failed submission

**Success Flow:**
- Redirect to confirmation page with application reference number
- Send confirmation email with next steps
- Display estimated processing timeline
```

**Invites Spécifiques À L’Intégration :**

```
Connect this form to **CRM system** to create new leads. Map @firstName to FirstName, @email to Email, set LeadSource to "Web Form", and Status to "New".
```

```
Set up **workflow trigger** when form is submitted. Pass all form data and trigger approval workflow with manager notification.
```

```
Configure **database integration** to save form submissions as records. Create new folder for each submission with uploaded documents.
```

## Importation et conversion de conception

**Utilisation :** lorsque vous disposez de conceptions de formulaire existantes (PDF, Figma, images) qui doivent être converties en formulaires AEM fonctionnels.

**Utilisation :** fournissez un contexte clair sur la conception de la source et indiquez les modifications ou améliorations nécessaires.

**Exemple d’invite - Conversion de formulaire PDF :**

```
Convert this uploaded **PDF application form** into a functional AEM adaptive form:

**Source Analysis:**
- Analyze the PDF layout and identify all form fields
- Preserve the visual hierarchy and grouping
- Maintain the professional appearance and branding

**Field Mapping:**
- Convert PDF text fields to adaptive form text inputs
- Transform checkboxes to checkbox components
- Convert dropdown lists to AEM dropdown components
- Map signature areas to digital signature fields

**Enhancements:**
- Add real-time validation that wasn't possible in PDF
- Implement conditional logic for dependent fields
- Make the form responsive for mobile devices
- Add progress saving capability
- Include accessibility improvements (ARIA labels, keyboard navigation)

**Styling:**
- Match the original color scheme and fonts
- Maintain professional business appearance
- Ensure consistent spacing and alignment
- Add subtle animations for better user experience

Preserve all original field labels and help text, but improve the user experience with modern form interactions.
```

**Invites d’importation de conception :**

```
Import this **design mockup** and convert it into an adaptive form. Maintain the exact visual design but add proper validation and mobile responsiveness.
```

```
Analyze this **image of a paper form** and recreate it digitally. Improve the layout for better mobile experience while keeping all mandatory fields.
```

```
Convert this **existing HTML form** to AEM adaptive form format. Preserve all functionality but add AEM-specific features like rules and themes.
```

## Optimisation et réactivité pour mobiles

**Quand utiliser :** quand les formulaires doivent fonctionner de manière transparente sur tous les types d’appareils et toutes les tailles d’écran.

**Utilisation :** commencez par une optimisation mobile de base, puis améliorez-la à l’aide de fonctionnalités avancées. Mettez l’accent sur l’approche mobile d’abord et spécifiez progressivement les comportements de point d’arrêt.

**Exemple d’invite - Commencer par l’optimisation mobile de base :**

```
Make @contactForm mobile-friendly with:

**Basic Mobile Layout:**
- Single column layout for all form sections
- Larger touch targets for buttons and inputs
- Responsive design that works on phones and tablets
```

**Ajoutez Ensuite Des Fonctionnalités Mobiles Avancées :**

```
Enhance @contactForm mobile experience with:
- Sticky submit button at bottom of screen
- Touch-friendly date pickers
- Swipe gestures for multi-step navigation
```

**Exemple d’invite - Optimisation complète de la priorité des appareils mobiles :**

```
Optimize this form for **mobile-first responsive design**:

**Mobile Layout (320px - 768px):**
- Single column layout for all form sections
- Larger touch targets (minimum 44px height)
- Simplified navigation with collapsible sections
- Sticky submit button at bottom of screen
- Auto-zoom disabled on input focus

**Tablet Layout (768px - 1024px):**
- Two-column layout for shorter fields (name, email)
- Single column for complex fields (address, comments)
- Side navigation for multi-step forms
- Optimized for both portrait and landscape

**Desktop Layout (1024px+):**
- Multi-column layouts where appropriate
- Horizontal form sections for related fields
- Sidebar navigation for long forms
- Hover states and advanced interactions

**Touch Optimization:**
- Larger checkbox and radio button targets
- Swipe gestures for multi-step navigation
- Pull-to-refresh for saved drafts
- Touch-friendly date/time pickers

**Performance:**
- Lazy load non-critical form sections
- Optimize images and icons for mobile
- Minimize JavaScript for faster loading
- Progressive enhancement approach
```

**Invites simples spécifiques à Mobile :**

```
Make @checkoutForm mobile-optimized with large buttons and one-thumb navigation
```

```
Add touch-friendly controls to @surveyForm for tablet users
```

```
Enable offline functionality for @applicationForm with local data saving
```

## Accessibilité et conformité

**Utilisation :** lorsque les formulaires doivent respecter les normes d’accessibilité (WCAG 2.1 AA) ou des exigences de conformité.

**Utilisation :** spécifiez les exigences d’accessibilité et les normes de conformité qui doivent être respectées.

**Exemple d’invite - Implémentation de l’accessibilité :**

```
Make this form **WCAG 2.1 AA compliant** with these accessibility features:

**Keyboard Navigation:**
- Logical tab order through all form elements
- Skip links to main content and form sections
- Keyboard shortcuts for common actions
- Focus indicators clearly visible on all interactive elements

**Screen Reader Support:**
- Proper ARIA labels for all form fields
- Descriptive error messages announced to screen readers
- Form section headings with proper hierarchy (h1, h2, h3)
- Progress announcements for multi-step forms

**Visual Accessibility:**
- Color contrast ratio minimum 4.5:1 for text
- Don't rely solely on color to convey information
- Text size minimum 16px for body text
- Scalable up to 200% without horizontal scrolling

**Motor Accessibility:**
- Large click targets (minimum 44x44px)
- Generous spacing between interactive elements
- No time limits or provide extension options
- Alternative input methods support

**Cognitive Accessibility:**
- Clear, simple language in all instructions
- Consistent navigation and layout patterns
- Error prevention and clear error recovery
- Help text and examples for complex fields

**Testing Requirements:**
- Test with screen readers (NVDA, JAWS, VoiceOver)
- Verify keyboard-only navigation
- Check color contrast with automated tools
- Validate HTML for semantic correctness
```

**Invites Spécifiques À La Conformité :**

```
Ensure this **healthcare form meets HIPAA requirements** with proper data encryption, audit logging, and privacy controls.
```

```
Make this **financial form PCI DSS compliant** with secure payment field handling and data protection measures.
```

```
Create a **government form meeting Section 508 standards** with full accessibility and plain language requirements.
```

## Assurance de test et de qualité

**Utilisation :** lorsque vous devez valider les fonctionnalités de formulaire, l’expérience utilisateur et les performances techniques.

**Utilisation :** spécifiez les scénarios de test, les cas Edge et les critères de qualité qui doivent être vérifiés.

**Exemple d’invite - Test complet du formulaire :**

```
Create a **comprehensive testing plan** for this application form:

**Functional Testing:**
- Test all field validations with valid and invalid data
- Verify conditional logic shows/hides fields correctly
- Test file upload with various file types and sizes
- Validate calculation fields update correctly
- Test form submission with complete and incomplete data

**User Experience Testing:**
- Test form completion time (target: under 10 minutes)
- Verify error messages are helpful and actionable
- Test progress saving and restoration
- Validate mobile touch interactions
- Check form accessibility with assistive technologies

**Edge Case Testing:**
- Test with extremely long text inputs
- Verify behavior with special characters and emojis
- Test with slow internet connections
- Validate offline functionality if applicable
- Test browser back/forward button behavior

**Performance Testing:**
- Measure form load time (target: under 3 seconds)
- Test with large file uploads
- Verify memory usage with long form sessions
- Test concurrent user submissions
- Validate database performance under load

**Security Testing:**
- Test input sanitization and XSS prevention
- Verify CSRF protection is working
- Test file upload security restrictions
- Validate data encryption in transit and at rest
- Check authentication and authorization controls

**Cross-Browser Testing:**
- Test on Chrome, Firefox, Safari, Edge
- Verify mobile browsers (iOS Safari, Chrome Mobile)
- Test on different operating systems
- Validate older browser fallbacks
- Check print functionality across browsers
```

**Invites Spécifiques Au Test :**

```
Create **automated test scripts** for this form's critical user paths: successful submission, validation errors, and conditional logic.
```

```
Design a **user acceptance testing plan** with realistic scenarios and success criteria for business stakeholders.
```

```
Set up **performance monitoring** to track form completion rates, abandonment points, and submission success rates.
```

## Fonctionnalités et intégrations avancées

**Utilisation :** lorsque vous avez besoin de fonctionnalités de formulaire sophistiquées telles que l’assistance d’IA, des workflows avancés ou des intégrations complexes.

**Utilisation :** définissez clairement les exigences en matière de fonctionnalités avancées et d’intégration.

**Exemple d’invite - Formulaire optimisé par l’IA :**

```
Add **AI-powered features** to enhance this application form:

**Smart Auto-Complete:**
- Use AI to suggest company names as user types
- Auto-populate address fields from partial input
- Suggest job titles based on industry selection
- Provide intelligent form completion suggestions

**Dynamic Question Generation:**
- Generate follow-up questions based on previous answers
- Adapt form complexity to user's experience level
- Show relevant optional fields based on user profile
- Personalize form sections for different user types

**Intelligent Validation:**
- Use AI to detect potentially incorrect information
- Suggest corrections for common data entry errors
- Validate business information against public databases
- Flag suspicious or inconsistent responses

**Content Optimization:**
- A/B test different form layouts automatically
- Optimize field order based on completion patterns
- Adjust form length based on user engagement
- Personalize help text based on user behavior

**Predictive Analytics:**
- Predict likelihood of form completion
- Identify users who might need assistance
- Suggest optimal times for form completion reminders
- Analyze drop-off points and suggest improvements

**Natural Language Processing:**
- Allow voice input for text fields
- Convert speech to text for accessibility
- Analyze open-text responses for sentiment
- Extract structured data from unstructured input
```

**Invites d’intégration avancées :**

```
Integrate with **CRM system** to pre-populate known customer data, update records in real-time, and trigger automated follow-up sequences.
```

```
Connect to **payment gateway** for secure transaction processing with PCI compliance, fraud detection, and multiple payment methods.
```

```
Implement **blockchain verification** for document authenticity, immutable audit trails, and decentralized identity verification.
```

## Dépannage et optimisation

**Utilisation :** lorsque les formulaires présentent des problèmes de performances, des problèmes d’expérience utilisateur ou des difficultés techniques.

**Utilisation :** Décrivez clairement le problème et le résultat souhaité.

**Exemple d’invite - Optimisation des performances :**

```
Optimize this form for **better performance and user experience**:

**Current Issues:**
- Form takes 8+ seconds to load on mobile
- Users are abandoning at the address section (60% drop-off)
- File uploads frequently fail or timeout
- Validation errors are confusing users

**Performance Improvements:**
- Implement lazy loading for non-critical form sections
- Optimize images and reduce bundle size
- Add progressive loading indicators
- Cache frequently used data (country lists, etc.)
- Minimize JavaScript execution time

**User Experience Fixes:**
- Simplify the address section with auto-complete
- Add inline validation with helpful error messages
- Implement smart defaults based on user location
- Add progress saving every 30 seconds
- Provide clear instructions for each section

**Technical Optimizations:**
- Implement chunked file uploads with resume capability
- Add client-side validation before server submission
- Optimize database queries for faster responses
- Implement proper error handling and retry logic
- Add comprehensive logging for debugging

**Monitoring & Analytics:**
- Set up form analytics to track user behavior
- Monitor completion rates by section
- Track error rates and types
- Measure performance metrics continuously
- A/B test improvements with real users
```

**Résolution des problèmes liés aux invites :**

```
**Debug this form submission error:** Users report getting "500 Internal Server Error" when submitting. Check validation logic, server endpoints, and data formatting.
```

```
**Fix mobile layout issues:** Form fields are overlapping on iPhone screens and submit button is not visible. Ensure proper responsive design.
```

```
**Resolve validation conflicts:** Some users can't submit even with valid data. Review validation rules for conflicts and edge cases.
```

## Bonnes Pratiques Spécifiques À Un Environnement

### Interface utilisateur de gestion de Forms

**Utilisation :** pour la création et la gestion de formulaires de haut niveau.

```
In Forms Management UI, create a new **customer survey template** that can be reused across different departments. Include standard branding, common field types, and configurable sections.
```

### Éditeur de Forms adaptatif

**Utilisation :** pour une configuration de formulaire détaillée et la création de règles complexes.

```
In the Adaptive Forms Editor, configure **advanced business rules** for this loan application: calculate debt-to-income ratio, determine eligibility, and show appropriate next steps.
```

### Éditeur universel

**Utilisation :** pour les formulaires Edge Delivery Services avec modification visuelle.

```
In Universal Editor, create a **responsive contact form** for the company website. Ensure it matches the site design and integrates with the existing content management workflow.
```

## Guide rapide de référence des commandes

| Commande | Meilleur cas d’utilisation | Exemple |
|---------|---------------|---------|
| `/create-form` | Démarrer de nouveaux formulaires | `/create-form employee onboarding with personal info and benefits selection` |
| `/add-form` | Ajout de formulaires à des pages | `/add-form newsletter signup with email and preferences` |
| `/update-layout` | Modification de la structure d’un formulaire | `/update-layout wizard with 4 steps: info, preferences, review, confirm` |
| `/update-field` | Modification des propriétés des champs | `/update-field @email to be mandatory with real-time validation` |
| `/create-rule` | Ajout d’un comportement dynamique | `/create-rule show @spouseInfo if @maritalStatus equals "Married"` |
| `/create-panel` | Organisation des sections de formulaire | `/create-panel Employment Details with job title, company, salary fields` |
| `/add-panel` | Conversion de conceptions | `/add-panel from uploaded form image with field recognition` |
| `/configure-submit` | Configuration de la gestion des données | `/configure-submit to CRM and send confirmation email` |
| `/help` | Obtention d’assistance | `/help how to implement multi-step validation?` |

## Référence des propriétés de composant prises en charge

### Propriétés universelles (tous les composants)

- **Type** : type de composant (texte, e-mail, numéro, téléphone, date, case à cocher, radio, liste déroulante, fichier, etc.).
- **Name** : identifiant du champ pour l&#39;envoi du formulaire
- **Libellé** : texte d’affichage du champ.
- **Description** : texte d’aide pour le champ
- **Visible** : booléen pour la visibilité initiale
- **Obligatoire** : valeur booléenne pour les champs obligatoires.

### Propriétés du champ de saisie

- **Value** : valeur par défaut/initiale
- **Espace réservé** : texte d’indice pour les champs de saisie
- **Min** : valeur minimale (pour les nombres/dates)
- **Max** : valeur maximale (pour les nombres/dates)

### Propriétés de chargement de fichier

- **Accepter** : types de fichiers (.pdf, .doc, .docx, .jpg, .png, etc.)
- **Multiple** : valeur booléenne pour la sélection de plusieurs fichiers

### Propriétés du contrôle de sélection

- **Options** : choix des listes déroulantes (liste séparée par des virgules)
- **Coché** : sélection par défaut des cases à cocher/cases d’option

### Propriétés du conteneur

- **Fieldset** : regroupement des champs associés
- **Répétable** : booléen pour les sections répétables

### Propriétés avancées

- **Expression visible** : formule de visibilité conditionnelle (=formule)
- **Expression de valeur** : formule pour les valeurs calculées (=formule)

## Résumé des bonnes pratiques

### Directives techniques

- **Utiliser uniquement les propriétés prises en charge** de la spécification officielle des composants AEM Forms
- **Respectez la syntaxe correcte** pour les références de champ (@fieldName) et les expressions (=formule)
- **Test incrémentiel** après chaque modification pour détecter les problèmes au plus tôt.
- **Planifiez l’accessibilité** dès le début, et non après coup
- **Tenir compte des utilisateurs mobiles** dans chaque décision de conception
- **Documenter des règles complexes** pour la maintenance future et la collaboration d’équipe

### Approche stratégique

- **Commencez par les besoins des utilisateurs** - Concentrez-vous sur ce que les utilisateurs doivent accomplir, et pas seulement sur les fonctionnalités techniques.
- **Conception pour achèvement** - Réduisez la friction et la charge cognitive dans la conception de formulaire.
- **Planifier le flux de données** précocement - réfléchissez à la manière dont les données seront traitées, stockées et utilisées
- **Créer à grande échelle** : concevez des formulaires capables de gérer la croissance attendue du volume d’utilisateurs et de données
- **Implémenter une amélioration progressive** - Assurez-vous que les fonctionnalités de base fonctionnent, puis ajoutez des fonctionnalités avancées

### Pièges courants à éviter

- **Requêtes initiales trop complexes** - Divisez les tâches volumineuses en étapes plus petites et plus faciles à gérer
- **Utilisation de propriétés non prises en charge** non incluses dans la spécification AEM Forms
- **Expérience mobile ignorée** jusque tard dans le processus de développement
- **Test utilisateur ignoré** avec des scénarios réels et des cas de périphérie
- **En supposant que l’IA comprenne le contexte** sans fournir d’instructions claires et spécifiques
- **Oublier les exigences d’accessibilité** de conformité
- **Pas de validation des modifications** avant de passer à l’étape suivante

### Approche de la qualité dans Assurance

1. **Aperçu fréquent** - Vérifiez votre travail en mode aperçu après chaque modification importante
2. **Test des cas de périphérie** - Essayez des entrées inhabituelles, du texte long, des caractères spéciaux.
3. **Validation sur plusieurs appareils** - Test sur mobile, tablette et bureau
4. **Vérifier l’accessibilité** - Vérifier la compatibilité entre le clavier et le lecteur d’écran
5. **Test de performance** - Assurez-vous que les formulaires se chargent rapidement et répondent correctement
6. **Test d’acceptation utilisateur** - Demandez à de vrais utilisateurs de tester le formulaire avant le déploiement


*Cette bibliothèque d’invites est continuellement mise à jour en fonction des commentaires des utilisateurs et des nouvelles fonctionnalités de l’assistant d’IA. Pour consulter les derniers exemples et fonctionnalités, consultez la [documentation d’AEM Forms](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/home.html?lang=fr).*
