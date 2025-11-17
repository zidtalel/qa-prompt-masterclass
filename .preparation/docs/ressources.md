# 🛠️ Ressources & Setup - Formation QA & IA

## Infrastructure Participant

### Logiciels à Installer

| Outil | Version Min | Statut | Notes |
|-------|------------|--------|-------|
| GitHub Copilot | Latest | **OBLIGATOIRE** | Outil principal, accès participant |
| Visual Studio Code | 1.85+ | **OBLIGATOIRE** | IDE, extension Copilot |
| Node.js | 18+ | **OBLIGATOIRE** | Pour Cypress |
| Git | 2.42+ | **OBLIGATOIRE** | Clone du dépôt |
| Cypress | 13+ | Recommandé | Framework automation (local) |
| TestComplete | Licence actuelle | Recommandé | Tool automation (local) |
| Jira/Xray | Cloud/On-prem | Recommandé | Accès test accounts |

### Configuration Prérequis

#### GitHub Copilot
```bash
# 1. Installer extension VS Code
# Marketplace > "GitHub Copilot" by GitHub

# 2. Authentifier
# Ctrl+Shift+P > "GitHub Copilot: Sign in"

# 3. Vérifier l'activation
# Commencer à taper dans un fichier.js, Copilot doit suggérer
```

#### Node.js & Cypress
```bash
# 1. Installer Node.js depuis https://nodejs.org/ (LTS)

# 2. Vérifier installation
node --version  # v18.x.x ou supérieur

# 3. Créer dossier de travail
mkdir qa-ai-formation
cd qa-ai-formation

# 4. Initialiser npm
npm init -y

# 5. Installer Cypress
npm install --save-dev cypress

# 6. Ouvrir Cypress
npx cypress open
```

#### Cloner le Dépôt
```bash
git clone https://github.com/zidtalel/qa-prompt-masterclass.git
cd qa-prompt-masterclass

# Créer une branche personnelle (optionnel)
git checkout -b mes-exercices-[NOM]
```

---

## Contexte Métier - Domaine Financier

### Glossaire & Standards

#### IBAN (International Bank Account Number)

**Format** : `CC + Clé (2 digits) + Identifiant national (jusqu'à 30 chars)`

**Exemples** :
- `FR14 2004 1010 0505 0001 3M02 606` (France)
- `DE89 3704 0044 0532 0130 00` (Allemagne)
- `IT60 X054 2811 1010 0000 0123 456` (Italie)
- `ES91 2100 0418 4502 0005 1332` (Espagne)

**Validation** : Clé de contrôle IBAN (mod 97)

**Référence** : ISO 13616

---

#### BIC (Business Identifier Code)

**Format** : `AAAA + CC + LL + [BBB]` (8 ou 11 caractères)

**Exemples** :
- `SOGEDEFF` (Société Générale, France)
- `BNPADEFF` (BNP Paribas, France)
- `COBADEFF` (Commerzbank, Allemagne)

---

#### Montants Financiers

**Limites de test** :
- Minimum : 0.01€
- Maximum : 1,000,000€ (limite bancaire typique)
- Devises testées : EUR, GBP, USD, CHF

**Cas de test** :
```
Valides : 10.50, 1000.00, 999999.99
Invalides : 0.00, -50.00, 1000000.01
Limites : 0.01 (min), 999999.99 (max proche)
Arrondis : 10.5, 10.555 (2 décimales)
```

---

#### Authentification 2FA

**Types** :
1. **SMS OTP** : Code 6-8 digits, valide 5-10 min
2. **Email OTP** : Lien + code, valide 15-30 min
3. **Biométrique** : Empreinte, faciale
4. **Questions de sécurité** : Réponses pré-enregistrées

**Cas de test** :
- Code expiré
- Code incorrect
- Plusieurs tentatives
- Changement d'appareil
- Rate limiting

---

#### Conformité & Régulations

**PCI DSS (Payment Card Industry Data Security Standard)** :
- Jamais stocker PAN en clair (Primary Account Number)
- Tokenization requise
- Encryption en transit + au repos

**AML (Anti-Money Laundering)** :
- KYC validation (Know Your Customer)
- Limite transactions suspectes
- Reporting obligatoire

**GDPR** :
- Consentement explicite
- Droit à l'oubli (delete data)
- Data privacy by design

**Références** :
- PCI DSS v3.2.1 : https://www.pcisecuritystandards.org/
- GDPR : https://gdpr-info.eu/

---

### Données de Test Valides

#### IBANs Générés (Fictifs mais Valides)

```
FR: FR1420041010050500013M02606
DE: DE89370400440532013000
IT: IT60X0542811101000000123456
ES: ES9121004184502000051332
BE: BE68539007547034
NL: NL91ABNA0417164300
```

#### Numéros de Carte (Format Valide - Ne PAS utiliser en production)

```
Visa: 4532 1488 0343 6467
MasterCard: 5425 2334 3010 9903
Amex: 3782 822463 10005
```

#### Montants de Test Recommandés

```json
{
  "montants_valides": [0.01, 10.50, 100.00, 999999.99],
  "montants_limites": [0.001, 1000000.01],
  "montants_tests": [1.00, 50.00, 500.00],
  "devises": ["EUR", "GBP", "USD", "CHF"]
}
```

---

## Templates de Ressources

### Template 1 : Script Cypress

**Fichier** : `exercices/templates/cypress-template.js`

```javascript
// Cypress Test Template - Payment Flow

describe('Payment Flow - Virement Bancaire', () => {
  
  beforeEach(() => {
    cy.visit('https://app-test.finance.local')
    cy.login('user@test.com', 'password')
  })

  it('Should complete payment successfully', () => {
    // Données de test
    const payment = {
      recipient: 'John Doe',
      iban: 'FR1420041010050500013M02606',
      amount: 100.00,
      currency: 'EUR'
    }

    // Actions
    cy.get('[data-testid="new-payment"]').click()
    cy.get('input[name="recipient"]').type(payment.recipient)
    cy.get('input[name="iban"]').type(payment.iban)
    cy.get('input[name="amount"]').type(payment.amount)

    // Assertions
    cy.get('[data-testid="confirm-btn"]').click()
    cy.get('[data-testid="success-message"]')
      .should('be.visible')
      .should('contain', 'Virement effectué')
  })

  afterEach(() => {
    cy.logout()
  })
})
```

---

### Template 2 : Cas de Test Xray (JSON)

**Fichier** : `exercices/templates/xray-testcases.json`

```json
{
  "testcases": [
    {
      "id": "TEST_PAYMENT_001",
      "name": "Virement simple - Montant standard",
      "objective": "Valider qu'un virement standard complète avec succès",
      "type": "Manual",
      "status": "Draft",
      "preconditions": [
        "Utilisateur authentifié",
        "Solde suffisant",
        "IBAN destination valide"
      ],
      "testSteps": [
        {
          "action": "Naviguer vers 'Nouveau Virement'",
          "data": "",
          "expectedResult": "Page de saisie du virement affichée"
        },
        {
          "action": "Saisir bénéficiaire: John Doe",
          "data": "Recipient: John Doe",
          "expectedResult": "Texte accepté"
        },
        {
          "action": "Saisir montant: 100 EUR",
          "data": "Amount: 100.00, Currency: EUR",
          "expectedResult": "Montant validé"
        },
        {
          "action": "Cliquer 'Confirmer'",
          "data": "",
          "expectedResult": "Virement traité, confirmation affichée"
        }
      ],
      "priority": "High",
      "labels": ["payment", "finance", "core"]
    },
    {
      "id": "TEST_PAYMENT_002",
      "name": "Virement - Montant dépassant limite",
      "objective": "Valider le rejet d'un montant > limite",
      "type": "Manual",
      "testSteps": [
        {
          "action": "Tenter saisir montant: 2000000 EUR",
          "data": "Amount: 2000000",
          "expectedResult": "Erreur: Montant dépasse la limite (1M€)"
        }
      ],
      "priority": "High",
      "labels": ["payment", "validation", "error-handling"]
    }
  ]
}
```

---

### Template 3 : Données de Test CSV

**Fichier** : `exercices/templates/test-data.csv`

```csv
scenario_id,recipient_name,recipient_iban,amount_eur,currency,expected_result,notes
TEST_001,John Doe,FR1420041010050500013M02606,100.00,EUR,SUCCESS,Virement standard
TEST_002,Jane Smith,DE89370400440532013000,500.00,EUR,SUCCESS,Virement international
TEST_003,Invalid IBAN,XX99INVALID00000000,50.00,EUR,ERROR,Validation IBAN
TEST_004,Small Amount,FR1420041010050500013M02606,0.01,EUR,SUCCESS,Montant minimum
TEST_005,Large Amount,FR1420041010050500013M02606,999999.99,EUR,SUCCESS,Montant max
TEST_006,Over Limit,FR1420041010050500013M02606,1000000.01,EUR,ERROR,Dépassement limite
```

---

## Documentation & Guides

### Guides à Consulter

| Document | Lien | Domaine |
|----------|------|---------|
| GitHub Copilot Best Practices | https://docs.github.com/en/copilot | Dev Tools |
| Cypress Documentation | https://docs.cypress.io | Testing |
| TestComplete Docs | https://smartbear.com/testcomplete/docs/ | Testing |
| Xray REST API | https://docs.getxray.app/display/XRAYAPI/ | Test Mgmt |
| IBAN Standards | https://en.wikipedia.org/wiki/International_Bank_Account_Number | Finance |
| PCI DSS | https://www.pcisecuritystandards.org/ | Security |

---

### Librairies & Frameworks

#### NPM Packages Utiles

```json
{
  "devDependencies": {
    "cypress": "^13.0.0",
    "cypress-plugin-api": "^2.0.0",
    "faker": "^6.0.0",
    "@faker-js/faker": "^8.0.0",
    "jest": "^29.0.0",
    "eslint": "^8.0.0",
    "prettier": "^3.0.0"
  }
}
```

#### Commandes Utiles

```bash
# Générer données de test
npm install @faker-js/faker

# Utilisation :
import { faker } from '@faker-js/faker'
const iban = faker.finance.iban()
const amount = faker.finance.amount(0.01, 1000000, 2)

# Cypress - Ouvrir l'interface
npx cypress open

# Cypress - Exécuter en headless
npx cypress run
```

---

## Environnements de Test

### Environnement Local

```bash
# Setup
git clone ...
npm install
npm run dev

# Cypress local
npx cypress open

# URL locale
http://localhost:3000
```

### Environnement Test (Si fourni)

```
Base URL: https://app-test.finance.local
Test Account: user@test.com
Password: [Fourni lors de la formation]
Credentials: Utilisateur de test avec permissions complètes
```

---

## Outils en Ligne (Pas d'Installation)

### Pour la Formation

- **GitHub** : https://github.com (version control + repo contenu)
- **GitHub Pages** : Hébergement gratuit (site formation)
- **CodePen** : https://codepen.io (démos interactives)
- **Replit** : https://replit.com (code sandbox)

### Outils de Support

- **Lucidchart** : Diagrammes + flow
- **Miro** : Collaboration temps réel
- **Notion** : Documentation partagée

---

## Support & Troubleshooting

### Problème 1 : GitHub Copilot ne suggère pas

**Solution** :
1. Vérifier extension installée (Extensions > GitHub Copilot)
2. Vérifier authentification (Ctrl+Shift+P > Sign In)
3. Redémarrer VS Code
4. Vérifier fichier `.js` ou `.py` (Copilot préfère certains langages)

---

### Problème 2 : Cypress n'ouvre pas

**Solution** :
```bash
# Vérifier Node
node --version

# Vérifier installation Cypress
npx cypress --version

# Réinstaller si nécessaire
npm uninstall cypress
npm install --save-dev cypress

# Ouvrir avec détails
npx cypress open --env DEBUG=cypress:*
```

---

### Problème 3 : Accès Jira/Xray

**Solution** :
- Demander accès administrateur
- Vérifier IP whitelisting
- Tester avec un autre navigateur
- Contacter support IT

---

## Checklist Prérequis (À Faire AVANT Formation)

### 48h Avant

- [ ] Installer VS Code
- [ ] Installer Node.js
- [ ] Installer GitHub Copilot (extension)
- [ ] Authentifier Copilot
- [ ] Cloner le dépôt
- [ ] Installer Cypress localement
- [ ] Tester Cypress : `npx cypress open`

### 24h Avant

- [ ] Accès Jira/Xray testé
- [ ] TestComplete accessible
- [ ] Tester le site de formation : https://zidtalel.github.io/qa-prompt-masterclass/
- [ ] Préparer un dossier vide pour les exercices

### Jour de la Formation

- [ ] Vérifier WiFi stable
- [ ] Vérifier batterie laptop (100%)
- [ ] Ouvrir URL formation
- [ ] Avoir GitHub open en onglet
- [ ] Avoir Copilot ready

---

## FAQ Support

**Q: Je peux partager les prompts générés ?**
A: Oui ! Une des objectives est de créer une "prompts library" partagée. Les committer sur GitHub.

**Q: Puis-je continuer après la formation ?**
A: Absolument ! Le dépôt reste accessible. Les ressources et exemples sont réutilisables.

**Q: Copilot coûte-t-il ?**
A: $10/mois (perso) ou via une license entreprise. À vérifier avec votre organisation.

**Q: Comment rester à jour après ?**
A: Suivre les ressources listées ci-dessus + faire veille technologique régulière.

---

## 🎯 Cas d'Usage Détaillés par Outil

### Section III Module 3.1 : GitHub Copilot & Redmine

#### **Cas d'Usage 1 : Générer Setup API (createProjectAPI)**

**Contexte** : Nous testons Redmine. Nous devons créer un projet via l'API avant de tester son modification.

**Prompt** (copier/coller dans Copilot) :

```markdown
**Rôle** : Tu es un ingénieur QA Redmine automatisant en TypeScript.

**Tâche** : Crée une fonction utilitaire asynchrone nommée `createProjectAPI()` 
qui utilise `cy.request('POST', '/projects.json', ...)` pour créer un projet Redmine.

**Contexte** : 
- Nous utilisons Cypress avec TypeScript
- L'API Redmine est à `https://redmine.example.com`
- L'authentification se fait via un header `X-Redmine-API-Key`

**Contraintes** : 
- Le projet doit s'appeler 'Projet à Modifier - QA'
- Son identifiant doit être 'test-modify'
- Le JSON doit être intégré à la fonction
- La fonction doit retourner l'ID du projet créé pour usage ultérieur

**Format** : Le code TypeScript de la fonction complète, prêt à l'emploi.
```

**Résultat attendu** : Une fonction prête à copier/coller dans vos tests.

---

#### **Cas d'Usage 2 : Générer Test UI E2E (Modification de Description)**

**Contexte** : Modifier la description du projet créé et vérifier le succès.

**Prompt** :

```markdown
**Rôle** : Tu es un testeur Cypress E2E spécialisé en finance.

**Tâche** : Écris un scénario de test Cypress complet pour modifier 
la description d'un projet Redmine existant.

**Contexte** : 
- Le projet a été créé à l'étape précédente
- L'ID du projet est 'test-modify'
- Nous utilisons le Page Object Model (POM)
- Les sélecteurs doivent utiliser l'attribut data-test-id

**Étapes à couvrir** : 
1. Naviguer vers `projects/test-modify/settings`
2. Attendre le chargement du formulaire
3. Remplir le champ Description : 'Nouvelle description testée par IA'
4. Cliquer sur le bouton Enregistrer
5. Vérifier que le message de succès s'affiche

**Format** : Le bloc `it()` complet, avec imports nécessaires.
```

---

#### **Cas d'Usage 3 : Générer Teardown (deleteProjectAPI)**

**Contexte** : Nettoyer le projet créé pour éviter les interférences entre tests.

**Prompt** :

```markdown
**Rôle** : Ingénieur DevOps spécialisé en nettoyage de données.

**Tâche** : Crée une fonction asynchrone nommée `deleteProjectAPI(projectId)` 
qui utilise `cy.request('DELETE', ...)` pour supprimer le projet Redmine.

**Contexte** : L'API de suppression de Redmine utilise `/projects/{project_id}.json`

**Contraintes** : 
- Vérifier un code de statut HTTP 204 ou 200
- Gérer les erreurs (projet inexistant, etc.)
- Appelable dans `afterEach()`

**Format** : Code TypeScript complet, avec gestion d'erreurs.
```

---

### Section III Module 3.2 : Jira/Xray & Gherkin

#### **Cas d'Usage 4 : User Story → Scénarios Gherkin**

**Contexte** : Une User Story Jira → Nous voulons générer les cas de test Xray automatiquement.

**Prompt** :

```markdown
**Rôle** : Analyste QA expert en BDD.

**Tâche** : Transforme la User Story ci-dessous en 5 scénarios de test 
complets au format Gherkin.

**Contexte** : 
La Story doit couvrir les cas : 
- Succès (montant valide)
- Erreur de validation (montant invalide)
- Cas limite - Montant zéro
- Cas limite - Montant > 999,999.99€
- Cas d'erreur - Compte invalide

**User Story** :
```
Titre : Enregistrer le temps passé sur une demande dans un projet

En tant que développeur,
Je veux enregistrer le temps que j'ai consacré à une demande,
Afin de permettre le suivi précis de la charge de travail.

Critères d'acceptation :
- Temps en heures (format XX.XX)
- Max 8 heures par jour
- Date ne peut pas être future
- Commentaire max 1024 caractères
```

**Format** : Gherkin pur (Feature, Scénario, Étant donné, Quand, Alors).
```

**Résultat** : Copier/coller directement dans Xray.

---

#### **Cas d'Usage 5 : Identification de Conditions Limites**

**Contexte** : Identifier les cas de test "sombres" pour la validation de montant.

**Prompt** :

```markdown
**Rôle** : Testeur d'Exploration en Boundary Testing.

**Tâche** : Identifie 10 valeurs d'entrée qui pourraient faire échouer 
la validation du champ "Montant".

**Contexte** :
- Format attendu : Nombre décimal positif (XX.XX)
- Limite min : 0€
- Limite max : 999,999.99€
- Domaine : Virements bancaires

**Cas à identifier** :
- Valide nominale
- Limites
- Invalides

**Format** : Tableau Markdown : Cas # | Valeur | Catégorie | Raison | Résultat attendu
```

**Résultat** : Liste de 10 cas pour renforcer la couverture de test.

---

### Section III Module 3.3 : TestComplete Patterns

#### **Cas d'Usage 6 : Générer Script TestComplete pour 2FA**

**Contexte** : Test du flux d'authentification 2FA sur Redmine.

**Prompt** :

```markdown
**Rôle** : Ingénieur TestComplete spécialisé en flux d'authentification.

**Tâche** : Génère un script TestComplete pour le flux 2FA complet :
1. Saisir username/password
2. Attendre SMS
3. Saisir OTP
4. Vérifier succès

**Contexte** :
- Redmine avec 2FA activée
- TestComplete v14+
- Objets UI utilisent des propriétés testID

**Contraintes** :
- Gère les timeouts
- Logging des étapes
- Nettoyage en fin

**Format** : Script TestComplete complet, prêt à exécuter.
```

---

### Section III Module 3.4 : Cypress Page Object Model

#### **Cas d'Usage 7 : Générer POM Cypress pour Redmine**

**Contexte** : Créer une Page Object réutilisable pour la page de virement.

**Prompt** :

```markdown
**Rôle** : Ingénieur Cypress avec 5 ans d'expérience POM.

**Tâche** : Génère une classe TypeScript `TransferPage` pour Redmine
avec les méthodes :
- visit()
- enterAmount(montant)
- selectAccount(account)
- submitTransfer()
- verifySuccessMessage()

**Contexte** :
- Les sélecteurs utilisent data-test-id
- Page Object Model pattern
- Retourner `this` pour chainement

**Format** : Classe TypeScript complète, prête à importer.
```

---

## 📊 Tableau de Synthèse - Cas d'Usage & Temps

| Module | Cas d'Usage | Prompt # | Outil | Temps |
|--------|-----------|----------|------|--------|
| 3.1 | Setup API | 1 | Copilot | 2-3 min |
| 3.1 | Test UI E2E | 2 | Copilot | 5-10 min |
| 3.1 | Teardown API | 3 | Copilot | 2-3 min |
| 3.2 | Gherkin from Story | 4 | Copilot/Xray | 5-10 min |
| 3.2 | Boundary Conditions | 5 | Copilot | 3-5 min |
| 3.3 | TestComplete 2FA | 6 | Copilot | 10-15 min |
| 3.4 | Cypress POM | 7 | Copilot | 5-10 min |

---

## 🎓 Exercice d'Application (Section III - 50 min)

### Exercice Intégré : Test E2E Complet

**Objectif** : Générer un test E2E **complet** (Arrange-Act-Assert) pour un virement Redmine.

**Durée** : 30-40 min

**Étapes** :

1. **Setup (5 min)** : Exécuter Cas d'Usage 1 → Copier la fonction `createProjectAPI()`
2. **Test Principal (10 min)** : Exécuter Cas d'Usage 2 → Générer le test de modification
3. **Teardown (5 min)** : Exécuter Cas d'Usage 3 → Copier `deleteProjectAPI()`
4. **Intégration (10 min)** : Assembler les 3 parties dans un fichier `.spec.ts` complet
5. **Validation (5 min)** : Exécuter le test et vérifier qu'il passe

**Fichier attendu** :

```typescript
// transfert.spec.ts
describe('Redmine - Gestion de Projet', () => {
  let projectId: number;
  
  before(() => {
    // ici : createProjectAPI()
  });
  
  it('Modifier la description du projet', () => {
    // ici : test de modification
  });
  
  after(() => {
    // ici : deleteProjectAPI(projectId)
  });
});
```

---

## 📝 Résumé : Transition Théorie → Pratique

| Phase | Durée | Activité | Output |
|-------|-------|----------|---------|
| Section I | 25 min | Compréhension du contexte IA | Comprendre limites + potentiel |
| Section II | 90 min | Maîtriser techniques prompting | 5+ prompts testés + librairie |
| Section III | 50 min | Intégration avec outils | 1 test E2E complet généré |
| Section IV | 30 min | Cas avancés + perspectives | Vision d'équipe sur IA + QA |

---

**Version** : 2.0 | **Date** : 16 Nov 2025 | **Mise à jour** : Ajout cas d'usage détaillés Redmine

