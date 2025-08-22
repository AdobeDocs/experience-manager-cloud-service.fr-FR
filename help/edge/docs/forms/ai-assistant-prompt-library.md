---
title: Forms Experience Builder - Bibliothèque d’invites
description: Collection de modèles de prompts et d’exemples éprouvés pour créer des formulaires avec l’aide de l’IA dans l’interface d’utilisation de gestion de Forms, l’éditeur de formulaires adaptatifs et l’éditeur universel.
feature: Edge Delivery Services
hide: true
index: false
hidefromtoc: true
role: Admin, Architect, Developer
exl-id: 333d42e0-625f-432e-a61b-5d49bf08765a
source-git-commit: 8be2b09200af58c701721b3e8537ea5e6cc3e4a2
workflow-type: tm+mt
source-wordcount: '1338'
ht-degree: 28%

---

# Forms Experience Builder - Bibliothèque d’invites

Collection de modèles d’invite réutilisables et d’exemples optimisés pour Forms Experience Builder. Cette bibliothèque rationalisée se concentre sur les deux méthodes de création principales : Créer en partant de zéro et Importer et convertir, avec une prise en charge améliorée des champs intelligents optimisés par LLM et la cohérence de la marque.

>[!NOTE]
>
> Forms Experience Builder est disponible dans le cadre du programme destiné aux utilisateurs et utilisatrices précoces. Envoyez un e-mail de votre adresse professionnelle à `aem-forms-ea@adobe.com` pour demander l’accès.

>[!IMPORTANT]
>
> **Documentation sujette à modification** : cette bibliothèque de prompts est en cours de test produit. Elle est sujette à des mises à jour et des révisions. Les invites, les exemples et les bonnes pratiques peuvent changer à mesure que Forms Experience Builder continue d’évoluer pendant le programme destiné aux utilisateurs et utilisatrices précoces.

## Utilisation de cette bibliothèque d&#39;invites

Cette bibliothèque fournit des modèles d’invite réutilisables pour les scénarios courants de création de formulaires. Pour connaître les bonnes pratiques complètes, consultez le [Guide de prise en main de Forms Experience Builder](forms-ai-assistant-getting-started.md#best-practices).

### Conseils rapides pour cette bibliothèque

- **Commencez par des exemples** - Utilisez les invites fournies comme modèles et adaptez-les selon vos besoins
- **Deux méthodes de création** - Choisissez Créer en partant de zéro ou Importer et convertir .
- **Soyez précis** - Ajoutez vos propres détails aux exemples génériques.
- **Tester minutieusement** - Toujours valider les résultats dans votre environnement spécifique

### Modèles et styles de marque

**Préparez les ressources de marque à l’avance pour une création de formulaire cohérente :**

- **Modèles de marque** - Créez des modèles de formulaire normalisés avec les couleurs, les polices et les modèles de disposition de votre entreprise
- **Instructions de style** - Définissez un style de champ, des conceptions de bouton et des normes d’espacement cohérents
- **Bibliothèque de composants** - Créez des composants de formulaire réutilisables qui correspondent à votre identité de marque.
- **Visual Assets** - Préparez les logos, les icônes et les éléments d’arrière-plan pour l’intégration des formulaires

**Exemple d’invite de modèle de marque :**

```
Create a brand template for financial services forms with:
- Corporate blue (#003366) and silver (#C0C0C0) color scheme
- Open Sans font family for all text
- 16px minimum font size for accessibility
- Consistent 24px spacing between sections
- Corporate logo in header with proper sizing
- Professional button styling with hover effects
```

>[!NOTE]
>
>**Composants personnalisés** : renseignez-vous auprès de votre équipe de développement sur l’utilisation de composants spécifiques à une organisation et leur compatibilité avec Forms Experience Builder avant d’implémenter des éléments de marque personnalisés.

>[!NOTE]
>
> Cette bibliothèque d’invites a été mise à jour pour prendre en compte les fonctionnalités simplifiées de Forms Experience Builder. Certaines fonctionnalités avancées d’intégration et de test présentées dans les exemples peuvent nécessiter une configuration supplémentaire.



## Exemples de développement incrémentiel

Ces exemples montrent comment créer des formulaires pas à pas, en commençant par simplement et en procédant pas à pas :

### Exemple 1 : création pas à pas d’un formulaire de contact

**Étape 1 : démarrer simplement :**

```
Create a basic contact form with name, email, and message fields
```

**Étape 2 : ajouter la validation :**

```
Make @name and @email mandatory fields with appropriate validation
```

**Étape 3 : améliorer l’expérience d’utilisation :**

```
Add placeholder text: @name "Your full name", @email "your.email@company.com", @message "Tell us how we can help"
```

**Étape 4 : ajouter des fonctionnalités avancées :**

```
Add a dropdown @inquiryType with options: "General Question", "Support Request", "Sales Inquiry", "Partnership"
```

**Étape 5 : implémenter une logique conditionnelle :**

```
Show @urgencyLevel dropdown (Low, Medium, High) only when @inquiryType equals "Support Request"
```

### Exemple 2 : création pas à pas d’un formulaire d’enregistrement

**Étape 1 : structure de base :**

```
Create a user registration form with personal information panel
```

**Étape 2 - Ajouter les champs obligatoires :**

```
Add fields for @firstName, @lastName, @email, @phoneNumber with appropriate validation
```

**Étape 3 - Ajouter une logique commerciale :**

```
Create a rule: if @age is under 18, show parent/guardian information section
```

**Étape 4 - Amélioration avec les préférences :**

```
Add a preferences panel with @newsletterSubscription, @marketingConsent, @termsAccepted
```

**Étape 5 - Ajouter le téléchargement de fichier :**

```
Include a file upload field for @profilePicture with size limit of 5MB
```

## Création et gestion de formulaires

**Utilisation :** lorsque vous devez créer de nouveaux formulaires ou modifier des formulaires existants.

**Utilisation :** choisissez l’une des deux approches suivantes : Créer en partant de zéro ou Importer et convertir (voir [Guide de prise en main](/help/edge/docs/forms/forms-ai-assistant-getting-started.md)).

**Exemple d’invite - Création simple de formulaire :**

```
Create a customer feedback form with:
- Product rating (1-5 stars)
- Comment field for detailed feedback
- Customer email (optional)
- Submit to email notification
```

**Exemple d’invite - Création de formulaire complexe :**

```
Create a comprehensive employee onboarding form with:

**Personal Information Section:**
- Full name (first, middle, last)
- Date of birth with age validation
- Contact information (email, phone, address)
- Emergency contact details

**Employment Details:**
- Position and department selection
- Start date with business day validation
- Salary information with confidentiality notice
- Reporting structure

**Document Upload:**
- Resume/CV upload (PDF, DOC, DOCX)
- ID verification documents
- Tax forms and banking information
- Signed employment agreement

**Preferences:**
- Benefits selection with cost calculator
- Work schedule preferences
- Training requirements
- Equipment needs

**Validation Rules:**
- Email format validation
- Phone number format validation
- Age must be 18 or older
- All required documents must be uploaded
- Terms and conditions must be accepted

**Submit Actions:**
- Send confirmation email to new employee
- Notify HR department
- Create employee record in HR system
- Schedule orientation meeting
```

**Invites de gestion des formulaires :**

```
Import this PDF application form and convert it to an adaptive form with enhanced validation
```

```
Update the existing contact form to include social media handles and preferred contact method
```

```
Reorganize the registration form into a 3-step wizard: personal info, preferences, confirmation
```

## Gestion et configuration des champs

**Utilisation :** lorsque vous devez ajouter, modifier ou configurer des champs de formulaire.

**Utilisation :** être précis sur les types de champs, les règles de validation et les exigences en matière d’expérience utilisateur.

**Exemple d’invite - Ajout d’un champ de base :**

```
Add a text input field for "Company Name" with placeholder "Enter your company name"
```

**Exemple d’invite - Configuration avancée des champs :**

```
Add a comprehensive address section with:

**Street Address:**
- Address line 1 (required, max 100 characters)
- Address line 2 (optional, max 100 characters)
- City (required, dropdown with common cities)
- State/Province (required, dropdown)
- Postal code (required, format validation)
- Country (required, default to "United States")

**Validation Rules:**
- Postal code must match state selection
- Address line 1 cannot be empty
- City must be a valid city for selected state

**User Experience:**
- Auto-complete for address fields
- Clear labels and help text
- Mobile-friendly input fields
- Accessibility compliance
```

**Invites de configuration de champ :**

```
Make @email field required with real-time validation and custom error message
```

```
Add a dropdown for @country with options for USA, Canada, UK, Germany, France, and "Other"
```

```
Configure @phoneNumber field with format (XXX) XXX-XXXX and validation
```

```
Add a file upload field for @resume with PDF and DOC restrictions, max 5MB
```

## Champs intelligents améliorés par LLM

**Quand l’utiliser :** quand vous avez besoin de champs avec des options préremplies qui exploitent la base de connaissances de l’IA.

**Utilisation :** permet de demander des champs qui nécessitent des jeux de données complets. L’IA peut renseigner automatiquement les options à l’aide de ses connaissances intégrées.

### Champs géographiques et de localisation

**Aéroports et transports :**

```
Add a dropdown for departure airports with all major international airports
Add arrival airport field with IATA codes and full names
Create a field for nearest airport to user location
Add a selection of train stations for European cities
```

**Régions administratives :**

```
Add a complete list of US states with abbreviations
Create a country dropdown with ISO codes and full names
Add a field for major world cities with time zones
Include a dropdown of Canadian provinces and territories
Add a field for UK counties and postal areas
```

### Données relatives aux entreprises et au secteur

**Classifications d’entreprise :**

```
Add a field for industry classification with NAICS codes
Create a dropdown of business entity types (LLC, Corporation, Partnership, etc.)
Add a field for company size categories (startup, SME, enterprise)
Include department selection for large organizations
Add a field for professional service types
```

**Classifications professionnelles :**

```
Add a field for job titles with common industry roles
Create a dropdown of professional certifications by field
Include education levels with degree types
Add a field for years of experience ranges
Create a selection for programming languages and frameworks
```

### Normes et réglementation

**Financier et juridique :**

```
Add a field for currency codes with symbols and exchange rates
Create a dropdown of tax ID types by country
Include a field for legal document types
Add payment method options with security features
Create a selection for banking institutions by country
```

**Normes techniques :**

```
Add a dropdown of file format types with extensions
Include network protocol options
Add a field for database types and versions
Create a selection for API authentication methods
```

### Soins de santé et médical

**Classifications médicales :**

```
Add a field for medical specialties
Create a dropdown of common medications with generic names
Include a field for insurance provider types
Add a selection for medical emergency contact relationships
Create a field for dietary restrictions and allergies
```

### Intelligence temporelle et calendaire

**Champs de date et d’heure :**

```
Add a field for business hours with time zone handling
Create a dropdown of public holidays by country
Include seasonal options with date ranges
Add a field for conference room booking with availability
Create a selection for recurring meeting patterns
```

### Catégories de produits et de services

**Classifications e-commerce :**

```
Add a field for product categories with subcategories
Create a dropdown of shipping methods with delivery estimates
Include a field for return policy options
Add a selection for customer priority levels
Create a field for subscription billing cycles
```

**Exemples d’invites de champ dynamique :**

```
"Add a departure airport field with all major airports worldwide including IATA codes and city names"
```

```
"Create a comprehensive industry field using standard NAICS classification with technology subcategories"
```

```
"Include a professional certification dropdown that adapts based on the selected job field"
```

```
"Add an international phone number field that formats based on the selected country"
```

```
"Create a university selection field with major institutions organized by country and ranking"
```

## Création de règles et logique commerciale

**Utilisation :** lorsque vous devez implémenter une logique conditionnelle, des règles de validation ou des processus d’entreprise.

**Utilisation :** Décrivez clairement la logique commerciale, en spécifiant les conditions et les actions.

**Exemple d’invite - Logique conditionnelle simple :**

```
Create a rule that shows @spouseInformation panel only when @maritalStatus equals "Married"
```

**Exemple d’invite - Règles métier complexes :**

```
Implement comprehensive loan application validation:

**Income Validation:**
- If @annualIncome is less than 30000:
  - Show warning message: "Income may be insufficient for requested loan amount"
  - Require additional income documentation
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

**Prompts spécifiques aux règles :**

```
Create a **visibility rule** that shows @spouseInformation panel only when @maritalStatus equals "Married" or "Domestic Partnership"
```

```
Add **progressive disclosure** where additional questions appear based on previous answers. Start with basic info, then show relevant follow-ups
```

```
Implement **smart defaults** where @country selection auto-sets related fields. Allow manual override
```

## Intégration et envoi de données

**Opportunité d’utilisation :** lorsque vous devez connecter des formulaires à des systèmes principaux, des bases de données ou des services externes.

**Méthode d’utilisation :** commencer par la configuration de base de l’envoi, puis ajouter des intégrations supplémentaires de manière incrémentielle. Spécifiez le type d’intégration, les exigences en matière de format de données et les préférences de gestion des erreurs.

**Exemple de prompt : commencer par l’envoi de base :**

```
Configure basic form submission for @applicationForm:

**Primary Submission:**
- Send form data to REST endpoint: `/api/v1/applications`
- Format data as JSON
- Show success message: "Application submitted successfully"
- Show error message if submission fails: "Submission failed, please try again"
```

**Ajoutez ensuite des actions secondaire pas à pas :**

```
Add email notification to @applicationForm: Send confirmation email to @email address with application reference number
```

```
Add CRM integration to @applicationForm: Create new lead record with @firstName, @lastName, @email, and set Status to "New Application"
```

**Exemple d’invite - Envoi multicanal standard :**

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

**Prompts spécifiques à l’Intégration :**

```
Connect this form to **CRM system** to create new leads. Map @firstName to FirstName, @email to Email, set LeadSource to "Web Form", and Status to "New"
```

```
Set up **workflow trigger** when form is submitted. Pass all form data and trigger approval workflow with manager notification
```

```
Configure **database integration** to save form submissions as records. Create new folder for each submission with uploaded documents
```

## Importer et convertir un Forms existant

**Utilisation :** lorsque vous disposez de formulaires, documents ou conceptions existants à transformer en formulaires AEM modernes.

**Utilisation :** chargez votre fichier source et décrivez les exigences de conversion (voir [ Guide d’importation](/help/edge/docs/forms/forms-ai-assistant-getting-started.md)).

**Exemple de prompt : conversion de formulaire PDF :**

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

Preserve all original field labels and help text, but improve the user experience with modern form interactions
```

**Prompts d’import de conception :**

```
Import this **design mockup** and convert it into an adaptive form. Maintain the exact visual design but add proper validation and mobile responsiveness
```

```
Analyze this **image of a paper form** and recreate it digitally. Improve the layout for better mobile experience while keeping all mandatory fields
```

```
Convert this **existing HTML form** to AEM adaptive form format. Preserve all functionality but add AEM-specific features like rules and themes
```

## Optimisation et réactivité pour mobiles

**Opportunité d’utilisation :** quand les formulaires doivent fonctionner de manière transparente sur tous les types d’appareils et toutes les tailles d’écran.

**Méthode d’utilisation :** commencer par une optimisation mobile de base, puis l’améliorer à l’aide de fonctionnalités avancées. Mettez l’accent sur l’approche mobile d’abord et spécifiez pas à pas les comportements des points d’arrêt.

**Exemple de prompt : commencer par l’optimisation mobile de base :**

```
Make @contactForm mobile-friendly with:

**Basic Mobile Layout:**
- Single column layout for all form sections
- Larger touch targets for buttons and inputs
- Responsive design that works on phones and tablets
```

**Ajoutez ensuite des fonctionnalités mobiles avancées :**

```
Enhance @contactForm mobile experience with:
- Sticky submit button at bottom of screen
- Touch-friendly date pickers
- Swipe gestures for multi-step navigation
```

**Exemple de prompt : optimisation complète de la priorité des appareils mobiles :**

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
```

**Invites Spécifiques Aux Appareils Mobiles :**

```
Make this form **touch-friendly** with larger buttons and simplified navigation for mobile users
```

```
Optimize form for **tablet users** with appropriate field sizes and navigation patterns
```

```
Add **swipe gestures** for multi-step form navigation on mobile devices
```

## Accessibilité et conformité

**Utilisation :** lorsque les formulaires doivent respecter les normes d’accessibilité (WCAG) ou des exigences de conformité.

**Utilisation :** spécifiez le niveau de conformité requis et les fonctionnalités d’accessibilité spécifiques nécessaires.

**Exemple d’invite - Accessibilité de base :**

```
Make @contactForm accessible with:

**Basic Accessibility:**
- Proper ARIA labels for all form fields
- Keyboard navigation support
- High contrast color scheme
- Screen reader compatibility
- Focus indicators for all interactive elements
```

**Exemple d’invite - Accessibilité avancée :**

```
Implement comprehensive accessibility for @applicationForm:

**WCAG 2.1 AA Compliance:**
- Semantic HTML structure with proper headings
- ARIA landmarks and roles for navigation
- Color contrast ratio of at least 4.5:1
- Keyboard-only navigation support
- Screen reader announcements for dynamic content

**Form-Specific Accessibility:**
- Error messages announced to screen readers
- Field validation with clear error descriptions
- Progress indicators for multi-step forms
- Skip navigation links for keyboard users
- Alternative text for all images and icons

**User Experience:**
- Clear focus indicators on all interactive elements
- Logical tab order through form fields
- Descriptive link text and button labels
- Help text available for complex fields
- Timeout warnings for session expiration
```

**Invites Spécifiques À L’Accessibilité :**

```
Add **screen reader support** to this form with proper ARIA labels and announcements
```

```
Implement **keyboard navigation** for all form interactions and navigation elements
```

```
Ensure **color contrast** meets WCAG AA standards for all text and interactive elements
```

## Optimisation des performances

**Quand l’utiliser :** quand les formulaires doivent se charger rapidement et fonctionner correctement dans diverses conditions.

**Utilisation :** spécifiez les exigences de performances et les stratégies d’optimisation.

**Exemple d’invite - Performances de base :**

```
Optimize @contactForm for performance:

**Loading Optimization:**
- Lazy load non-critical form sections
- Minimize initial bundle size
- Optimize images and assets
- Enable caching for static resources
```

**Exemple d’invite - Performances avancées :**

```
Implement comprehensive performance optimization for @applicationForm:

**Loading Performance:**
- Progressive loading of form sections
- Optimize images with WebP format
- Minimize JavaScript bundle size
- Enable gzip compression for all assets

**Runtime Performance:**
- Debounce validation calls to reduce API requests
- Optimize conditional logic execution
- Cache frequently used data
- Implement virtual scrolling for long lists

**User Experience:**
- Show loading indicators for async operations
- Provide offline capability for form data
- Auto-save form progress every 30 seconds
- Optimize form submission with retry logic

**Monitoring:**
- Track form load times and user interactions
- Monitor validation performance
- Measure submission success rates
- Alert on performance degradation
```

**Invites Spécifiques Aux Performances :**

```
Optimize form **loading speed** by implementing progressive loading and asset optimization
```

```
Add **auto-save functionality** to prevent data loss during form completion
```

```
Implement **offline support** so users can complete forms without internet connection
```

## Tests et assurance qualité

**Quand l’utiliser :** quand les formulaires ont besoin d’être testés de manière exhaustive pour garantir leur fiabilité et la satisfaction des utilisateurs.

**Utilisation :** spécifiez les scénarios de test, les exigences de validation et les mesures de qualité.

**Exemple d’invite - Tests de base :**

```
Add comprehensive testing for @contactForm:

**Functional Testing:**
- Test all form field validations
- Verify submit functionality works correctly
- Test error handling and user feedback
- Validate conditional logic and rules
```

**Exemple d’invite - Tests avancés :**

```
Implement comprehensive testing strategy for @applicationForm:

**Functional Testing:**
- Unit tests for all validation rules
- Integration tests for submit actions
- End-to-end testing for complete user flows
- Cross-browser compatibility testing

**User Experience Testing:**
- Usability testing with target user groups
- Accessibility testing with screen readers
- Mobile device testing on various screen sizes
- Performance testing under load conditions

**Quality Assurance:**
- Automated testing for regression prevention
- Manual testing for edge cases and scenarios
- Security testing for data protection
- Compliance testing for regulatory requirements

**Monitoring:**
- Track form completion rates and abandonment
- Monitor error rates and user feedback
- Measure performance metrics and load times
- Analyze user behavior and interaction patterns
```

**Prompts spécifique au test :**

```
Add **automated testing** for all form validations and submit functionality
```

```
Implement **user acceptance testing** scenarios for complete form workflows
```

```
Set up **performance monitoring** to track form load times and user interactions
```

## Résolution des problèmes

Solutions rapides aux problèmes courants de Forms Experience Builder :

| Problème | Quick Fix |
|-------|-----------|
| Formulaire non envoyé | Vérifier la configuration et les règles de validation de l’action d’envoi |
| Erreurs de validation non affichées | Vérifier les paramètres de validation des champs et l’emplacement des messages d’erreur |
| Problèmes de disposition mobile | Vérifier les paramètres de Responsive Design et le dimensionnement des champs |
| Les champs ne s’affichent pas | Vérifier la logique conditionnelle et les règles de visibilité |
| Échecs d’import | Vérifier la compatibilité des formats de fichiers et les limites de taille |
| Erreurs d’intégration | Valider les points d’entrée d’API et les informations d’authentification |
| Problèmes de performances | Optimiser le nombre de champs et supprimer les validations inutiles |
| Problèmes d’accessibilité | Vérifier les libellés de champ, les attributs ARIA et l’ordre de tabulation |

**Invite du mode de débogage :**

```
Enable debug mode to identify issues with form submission and field validation
```

**Invite d’analyse des erreurs :**

```
Analyze form errors: check validation rules, API responses, and user input patterns
```

## Analyses et informations avancées

**Utilisation :** lorsque vous devez comprendre les performances des formulaires et le comportement des utilisateurs.

**Utilisation :** spécifiez les exigences et les informations d’analyse nécessaires.

**Exemple d’invite - Analyses de base :**

```
Add analytics to @contactForm:

**Basic Metrics:**
- Form completion rates
- Field abandonment rates
- Submit success/failure rates
- User session duration
```

**Exemple d’invite - Analyses avancées :**

```
Implement comprehensive analytics for @applicationForm:

**User Behavior Analytics:**
- Track field completion rates and abandonment
- Monitor user session duration and patterns
- Analyze form navigation and user flow
- Identify bottlenecks and friction points

**Performance Analytics:**
- Measure form load times and performance
- Track API response times and failures
- Monitor validation rule effectiveness
- Analyze submission success rates

**Business Intelligence:**
- Generate reports on form effectiveness
- Track conversion rates and ROI
- Monitor user satisfaction and feedback
- Identify opportunities for optimization

**Predictive Analytics:**
- Predict form completion likelihood
- Identify users likely to abandon
- Recommend form improvements
- Optimize user experience based on data
```

**Invites spécifiques à Analytics :**

```
Add **conversion tracking** to measure form completion rates and user behavior
```

```
Implement **A/B testing** to compare different form designs and optimize performance
```

```
Create **analytics dashboard** to monitor form performance and user insights
```

## Sécurité et protection des données

**Utilisation :** lorsque les formulaires gèrent des données sensibles et nécessitent des mesures de sécurité.

**Utilisation :** spécifiez les exigences de sécurité et les mesures de protection des données.

**Exemple d’invite - Sécurité de base :**

```
Add security measures to @contactForm:

**Basic Security:**
- HTTPS encryption for all data transmission
- Input validation and sanitization
- CSRF protection for form submissions
- Secure session management
```

**Exemple d’invite - Sécurité avancée :**

```
Implement comprehensive security for @applicationForm:

**Data Protection:**
- End-to-end encryption for sensitive data
- PII data masking and anonymization
- Secure file upload with virus scanning
- Data retention and deletion policies

**Access Control:**
- Role-based access control for form data
- Multi-factor authentication for admin access
- Audit logging for all data access
- Secure API authentication and authorization

**Compliance:**
- GDPR compliance for data handling
- HIPAA compliance for health information
- PCI DSS compliance for payment data
- SOC 2 compliance for data security

**Monitoring:**
- Real-time security monitoring and alerts
- Intrusion detection and prevention
- Data breach notification systems
- Regular security audits and assessments
```

**Invites spécifiques à la sécurité :**

```
Implement **data encryption** for sensitive form submissions and user information
```

```
Add **access control** to restrict form data access based on user roles and permissions
```

```
Set up **security monitoring** to detect and prevent unauthorized access to form data
```

## Référence des commandes

### Commandes Essentielles

| Commande | Meilleurs cas d’utilisation | Exemple |
|---------|---------------|---------|
| `/create-form` | Démarrage de nouveaux formulaires | `/create-form employee onboarding with personal info and benefits selection` |
| `/add-form` | Ajout de formulaires aux pages | `/add-form newsletter signup with email and preferences` |
| `/update-layout` | Modification de la structure d’un formulaire | `/update-layout wizard with 4 steps: info, preferences, review, confirm` |
| `/update-field` | Modification des propriétés des champs | `/update-field @email to be mandatory with real-time validation` |
| `/create-rule` | Ajout d’un comportement dynamique | `/create-rule show @spouseInfo if @maritalStatus equals "Married"` |
| `/create-panel` | Organisation des sections de formulaire | `/create-panel Employment Details with job title, company, salary fields` |
| `/add-panel` | Conversion de conceptions | `/add-panel from uploaded form image with field recognition` |
| `/configure-submit` | Configuration de la gestion de données | `/configure-submit to CRM and send confirmation email` |
| `/help` | Obtention d’assistance | `/help how to implement multi-step validation?` |

### Références de champ

Utilisez la syntaxe `@fieldName` pour référencer les champs existants dans vos invites :

- `@email` - Champ d’e-mail de référence
- `@firstName` - Champ de prénom de référence
- `@maritalStatus` - Champ État civil de référence

### Types de composant

**Composants d’entrée :**

- `text`, `email`, `number`, `tel`, `date`, `checkbox`, `radio`, `dropdown`, `file`, `textarea`

**Composants de conteneur :**

- `fieldset`, `panel`, `repeatable`, `wizard`

### Propriétés du composant

**Propriétés universelles (tous les composants) :**

- **Type** : type de composant
- **Nom** : identifiant du champ pour l’envoi du formulaire
- **Libellé** : texte d’affichage du champ
- **Description** : texte d’aide pour le champ
- **Visible** : booléen pour la visibilité initiale
- **Obligatoire** : valeur booléenne pour les champs obligatoires

**Propriétés du champ de saisie :**

- **Valeur** : valeur par défaut/initiale
- **Espace réservé** : texte d’indice pour les champs de saisie
- **Min.** : valeur minimale (pour les nombres/dates)
- **Max.** : valeur maximale (pour les nombres/dates)

**Propriétés de chargement de fichier :**

- **Accepter** : types de fichiers (.pdf, .doc, .docx, .jpg, .png, etc.)
- **Multiple** : valeur booléenne pour la sélection de plusieurs fichiers

**Propriétés du contrôle Selection :**

- **Options** : choix des listes déroulantes (liste séparée par des virgules)
- **Coché** : sélection par défaut des cases à cocher/cases d’option

**Propriétés du conteneur :**

- **Fieldset** : regroupement des champs associés
- **Répétable** : valeur booléenne pour les sections répétables

**Propriétés avancées :**

- **Expression visible** : formule de visibilité conditionnelle (=formule)
- **Expression de valeur** : formule pour les valeurs calculées (=formule)

### Commandes d’intégration

**Actions Envoyer :**

- Notifications par e-mail
- Envois de l’API REST
- Stockage dans le cloud (Azure, SharePoint)
- Automatisation des workflows (Power Automate, Workfront Fusion)
- Plateformes marketing (Marketo)
- Intégrations CRM

### Instructions relatives à la syntaxe de l&#39;invite

- **Références de champ** : utilisez des `@fieldName` pour les champs existants
- **Commandes** : utilisez des `/command` pour des actions spécifiques
- **Langage naturel** : décrivez les exigences de manière claire et spécifique.

### Liste de contrôle de validation

Pour obtenir des bonnes pratiques et des instructions de validation complètes, consultez le [Guide de prise en main de Forms Experience Builder](forms-ai-assistant-getting-started.md#best-practices).

*Cette bibliothèque d’invites est continuellement mise à jour en fonction des commentaires des utilisateurs et des nouvelles fonctionnalités de Forms Experience Builder. Pour consulter les derniers exemples et fonctionnalités, consultez la [documentation d’AEM Forms](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/home.html?lang=fr).*
