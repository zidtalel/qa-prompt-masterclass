# 📋 PRD - Formation QA & IA Générative

**Product Requirements Document** - Spécifications détaillées

---

## 1. Vue d'Ensemble

**Produit** : Formation en ligne (pages web) sur l'IA générative appliquée au QA

**Objectif** : Transférer des compétences en prompting et intégration d'IA aux professionnels QA du domaine financier

**Public** : 16 participants divisés en deux groupes de 8 chacun (50% testeurs manuels, 50% scripteurs). Chaque groupe aura une session de formation complète de 3h30.

**Domaine** : Développpement logiciel dans le domaine de la Finance

**Plateforme** : GitHub Pages (hébergement gratuit, version control intégré)

---

## 2. Spécifications Fonctionnelles par Section

### 2.1 Section I : Le Paysage de l'IA Générative en QA

#### Contenu à Couvrir

| Thème | Détails | Durée |
|-------|---------|-------|
| **État de l'art 2025** | Modèles actuels, capacités, limitations | 5 min |
| **Défis du QA moderne** | Vitesse, couverture, maintenance, coûts | 5 min |
| **Types d'IA pertinentes** | Génération, analyse, prédiction, classification | 5 min |
| **Cas d'usage finance** | 3-4 exemples concrets (virement, authentification, calcul) | 5 min |
| **Éthique & Risques** | Biais, hallucinations, coûts, sécurité données | 5 min |

#### Livrables

- [ ] Page HTML : `section-1/index.html` (overview + navigation)
- [ ] Slides interactives : `section-1/slides.html` (format reveal.js ou similaire)
- [ ] Ressources : `section-1/ressources.md` (liens, références, articles)
- [ ] Démo 1 : Copilot génère 3 cas de test financiers (live)
- [ ] Démo 2 : Comparaison prompt basique vs optimisé

#### Critères d'Acceptation

- ✓ Page responsive (mobile + desktop)
- ✓ Temps de chargement < 2s
- ✓ Tous les liens externes fonctionnels
- ✓ Démos enregistrées (fallback si live échoue)

---

### 2.2 Section II : L'Art du Prompting (NOYAU - 90 min)

#### Module 2.1 : Fondamentaux du Prompting (20 min)

**Concepts** :
1. Structure d'une requête optimale
   - Contexte clair
   - Instruction précise
   - Format attendu
   - Exemple (si applicable)

2. Few-shot vs Zero-shot
   - Quand utiliser chaque approche
   - Exemples financiers

3. Chain-of-Thought (CoT)
   - Faire "penser" l'IA étape par étape
   - Amélioration des résultats

4. Persona Engineering
   - Donner un rôle à l'IA
   - Ex: "Tu es un expert en QA financier avec 15 ans d'expérience"

**Exercice 2.1.1** :
- Fichier : `section-2/exercices/2-1-1-prompting-basics.md`
- Task : Rédiger 3 versions d'un prompt pour générer des cas de test d'un virement
  - V1 : Basique ("Génère des cas de test")
  - V2 : Intermédiaire (+ contexte, format)
  - V3 : Optimisée (CoT, format structuré, constraints)
- Template fourni avec structure vide
- Solution proposée avec annotations
- Temps : 10 min d'exercice + 5 min de partage

**Livrables** :
- [ ] Page HTML module : `section-2/module-1.html`
- [ ] Fichier exercice : `section-2/exercices/2-1-1-prompting-basics.md`
- [ ] Template complété : `section-2/exercices/2-1-1-template.txt`
- [ ] Solution commentée : `section-2/exercices/2-1-1-solution.md`

---

#### Module 2.2 : Prompting pour la Génération de Tests (30 min)

**Concepts** :
1. Générer des cas de test structurés
   - Cas positifs / négatifs
   - Cas limites / edge cases
   - Données financières valides (IBAN, montants, etc.)

2. Générer des scripts automatisés
   - Cypress : page object model, assertions
   - TestComplete : identification d'objets, actions

3. Générer des données de test
   - Données financières réalistes
   - Formats valides (IBAN ISO 13616, etc.)
   - Volumétrie

**Exemple Concret 1 : Test d'un virement international**

Prompt Optimisé (Example) :
```
Tu es un expert en QA financier avec 10 ans d'expérience.
Je dois créer des cas de test pour un flux de virement international.

Contexte:
- Montant min: 0.01€, max: 1M€
- Devises supportées: EUR, GBP, USD, CHF
- Délai de traitement: 1-5 jours ouvrés
- Validation: IBAN source/destination, montant, devise

Génère 5 cas de test (positifs et négatifs) au format:
[
  {
    "id": "TEST_001",
    "titre": "...",
    "pré-conditions": "...",
    "étapes": ["step 1", "step 2", ...],
    "résultat attendu": "...",
    "type": "positif|négatif|limite"
  }
]

Inclus au moins 2 tests de limites (montant min/max) et 1 test d'erreur.
```

**Exercices de ce module** :

**Exercice 2.2.1 : Générer cas de test structuré**
- Fichier : `section-2/exercices/2-2-1-generate-testcases.md`
- Task : Générer 5 cas de test pour un scénario financier donné (authentification 2FA)
- Template : Prompt partiellement complété, participant le finit
- Livrable : JSON des cas de test
- Temps : 8 min d'exercice + 2 min de présentation

**Exercice 2.2.2 : Générer script Cypress**
- Fichier : `section-2/exercices/2-2-2-cypress-script.md`
- Task : Générer un script Cypress pour 3 scénarios (connexion, paiement, déconnexion)
- Public cible : Scripteurs uniquement
- Template : Fichier Cypress vide avec structure
- Livrable : Script `.js` complété
- Temps : 10 min

**Exercice 2.2.3 : Générer données de test financières**
- Fichier : `section-2/exercices/2-2-3-test-data.md`
- Task : Générer 50 IBANs valides, montants de test, données de paiement
- Validations attendues : Format IBAN correct, montants réalistes
- Livrable : CSV avec données
- Temps : 7 min

**Livrables** :
- [ ] Page HTML module : `section-2/module-2.html`
- [ ] 3 fichiers d'exercice (comme ci-dessus)
- [ ] Templates + solutions
- [ ] Exemples annotés de prompts "avant/après"

---

#### Module 2.3 : Prompting pour l'Analyse et le Debugging (20 min)

**Concepts** :
1. Analyser un test qui échoue
   - Extraire informations du log d'erreur
   - Identifier patterns de défaillance

2. Déboguer avec l'IA
   - Copilot + Explain code
   - Chat pour diagnostiquer

3. Proposer des corrections
   - Refactoring du code
   - Correction du prompt

**Exercice 2.3.1 : Analyser & Corriger**
- Fichier : `section-2/exercices/2-3-1-debugging.md`
- Task : On fournit un script Cypress qui échoue (e.g., timing issue, mauvais sélecteur)
- Instruction : Utiliser Copilot pour analyser le problème et proposer une correction
- Code fourni : Script défaillant pré-écrit
- Livrable : Script corrigé + explication
- Temps : 10 min

**Livrables** :
- [ ] Page HTML module : `section-2/module-3.html`
- [ ] Fichier exercice + code de test défaillant
- [ ] Solution avec explications

---

#### Module 2.4 : Techniques Avancées (20 min)

**Concepts** :
1. Prompt Chaining
   - Décomposer en sous-prompts
   - Chainer les résultats

2. System Prompt Customization
   - Configurer le comportement de Copilot
   - Configurations optimales pour QA

3. RAG (Retrieval-Augmented Generation)
   - Fournir du contexte externe
   - Ex: spécifications métier, normes financières

4. Itération & Feedback
   - Affiner le prompt basé sur résultats
   - Boucle d'amélioration continue

**Exemple** :
```
Prompt 1 : Génère une liste de cas de test pour un virement
↓
Résultat : 10 cas

Prompt 2 : Parmi ces cas, lesquels couvrent la conformité PCI-DSS ?
↓
Résultat : Analyse

Prompt 3 : Génère des cas de test SUPPLÉMENTAIRES pour les gaps de conformité
↓
Résultat : 5 cas additionnels
```

**Exercice 2.4.1 : Prompt Chaining**
- Fichier : `section-2/exercices/2-4-1-chaining.md`
- Task : Construire une séquence de 3 prompts pour générer une suite de tests complète
- Livrable : Les 3 prompts + résultats finaux
- Temps : 12 min

**Livrables** :
- [ ] Page HTML module : `section-2/module-4.html`
- [ ] Fichier exercice chaining
- [ ] Ressources : guide des techniques avancées

---

### 2.3 Section III : Outillage QA + IA (50 min)

#### Module 3.1 : GitHub Copilot dans l'IDE (15 min)

**Objectives** :
- Utiliser Copilot pour autocompléter du code QA
- Générer des fonctions réutilisables
- Patterns optimaux

**Démo** :
- Live : Générer une fonction `generatePaymentData()` en Cypress
- Live : Autocomplétion sur un script TestComplete

**Exercice 3.1.1 : Compléter avec Copilot**
- Fichier : `section-3/exercices/3-1-1-copilot-ide.md`
- Code fourni : Fichier JavaScript avec fonction partiellement écrite
- Task : Utiliser Copilot Autocomplete pour compléter
- Temps : 8 min

**Livrables** :
- [ ] Page HTML : `section-3/copilot-ide.html`
- [ ] Code exemple commenté
- [ ] Exercice + solution

---

#### Module 3.2 : Xray & Jira + IA (15 min)

**Objectives** :
- Générer des cas de test au format Xray
- Créer des scénarios à partir de User Stories Jira
- Automatiser la documentation

**Workflows** :

Workflow 1 : Jira Story → Cas Xray
```
US: "En tant que client bancaire, je veux virer de l'argent à l'international"
        ↓
[Copilot] Génère 5 cas de test structurés
        ↓
Format Xray (JSON/CSV)
        ↓
Import dans Xray via API
```

**Exercice 3.2.1 : De la US au cas de test Xray**
- Fichier : `section-3/exercices/3-2-1-jira-xray.md`
- Donné : 2 User Stories Jira en texte
- Task : Générer les cas de test + formater pour Xray
- Temps : 12 min

**Livrables** :
- [ ] Page HTML : `section-3/xray-jira.html`
- [ ] Guide d'intégration Jira-Xray-Copilot
- [ ] Templates Xray JSON
- [ ] Exercice + solution

---

#### Module 3.3 : TestComplete + IA (10 min)

**Objectives** :
- Générer scripts TestComplete robustes
- Gestion des locators avec IA
- Maintenance du code

**Démo** :
- Générer un script pour tester la page de login 2FA

**Exercice 3.3.1 : Script TestComplete**
- Fichier : `section-3/exercices/3-3-1-testcomplete.md`
- Scénario : Test d'une transaction financière dans une app bancaire
- Temps : 8 min

**Livrables** :
- [ ] Page HTML : `section-3/testcomplete.html`
- [ ] Templates TestComplete
- [ ] Patterns robustes avec IA
- [ ] Exercice + solution

---

#### Module 3.4 : Cypress + IA (10 min)

**Objectives** :
- Patterns Cypress optimisés
- Page Object Model generation
- Gestion des états async

**Exercice 3.4.1 : Page Object Model**
- Fichier : `section-3/exercices/3-4-1-cypress.md`
- Task : Générer un POM pour une page de virement bancaire
- Temps : 8 min

**Livrables** :
- [ ] Page HTML : `section-3/cypress.html`
- [ ] Templates Cypress (POM, helpers)
- [ ] Best practices Cypress + Copilot
- [ ] Exercice + solution

---

### 2.4 Section IV : Avancés (30 min)

#### Module 4.1 : Analyse d'Impact (10 min)

**Concept** : Prédire l'impact d'une modification de code/règle métier

**Cas d'usage** :
- Changement d'une règle de calcul d'intérêt → quels tests relancer ?
- Modification du workflow de paiement → couverture affectée ?

**Exercice 4.1.1 : Risk Analysis**
- Fichier : `section-4/exercices/4-1-1-impact-analysis.md`
- Donné : Description d'un changement de code
- Task : Utiliser Copilot pour identifier les tests impactés
- Temps : 8 min

**Livrables** :
- [ ] Page HTML : `section-4/analyse-impact.html`
- [ ] Guide d'analyse d'impact
- [ ] Exercice + solution

---

#### Module 4.2 : Génération de Documentation (10 min)

**Concepts** :
- Générer doc de test automatiquement
- Générer des rapports
- Knowledge base auto-maintenue

**Exercice 4.2.1 : Doc Automatique**
- Fichier : `section-4/exercices/4-2-1-documentation.md`
- Task : Générer la doc complète d'une suite de tests
- Temps : 8 min

**Livrables** :
- [ ] Page HTML : `section-4/documentation.html`
- [ ] Templates de documentation
- [ ] Exercice + solution

---

#### Module 4.3 : Collaboration d'Équipe (5 min)

**Concepts** :
- Partager les prompts optimisés
- Prompts library en version control
- Bonnes pratiques d'équipe

**Livrable** :
- [ ] Guide : `section-4/collaboration.html`

---

#### Module 4.4 : Perspectives (5 min)

**Topics** :
- Agents autonomes
- Future de l'IA en QA
- Ressources de veille

**Livrable** :
- [ ] Page HTML : `section-4/perspectives.html`

---

## 3. Spécifications Web

### Architecture générale

```
docs/
├── index.html           # Landing page + navigation
├── style.css            # Global styles
├── section-1/index.html
├── section-2/
│   ├── index.html       # Overview
│   ├── module-1.html    # Fondamentaux
│   ├── module-2.html    # Génération
│   ├── module-3.html    # Debugging
│   ├── module-4.html    # Avancés
│   └── exercices/       # Liens vers fichiers exercice
├── section-3/
│   ├── copilot-ide.html
│   ├── xray-jira.html
│   ├── testcomplete.html
│   └── cypress.html
└── section-4/
    ├── analyse-impact.html
    ├── documentation.html
    ├── collaboration.html
    └── perspectives.html
```

### Critères d'Interface

- [ ] Design responsive (mobile-first)
- [ ] Navigation claire et intuitive
- [ ] Temps de chargement < 2s par page
- [ ] Compatibilité navigateurs modernes (Chrome, Firefox, Edge, Safari)
- [ ] Accessibilité WCAG 2.1 AA
- [ ] Code syntax highlighting pour tous les exemples
- [ ] Lien "Copier" pour tous les prompts/code
- [ ] Lien direct vers les fichiers d'exercice sur GitHub

### Contenu Interactif

- [ ] Démos vidéo enregistrées (fallback live)
- [ ] Code sandbox (CodePen/Replit intégré)
- [ ] Links vers GitHub repo (pour cloner)
- [ ] CTAs pour les exercices (boutons clairs)

---

## 4. Spécifications Contenu Métier

### Contexte Financier à Intégrer

**Domaines couverts** :

1. **Virement Bancaire**
   - Format IBAN (ISO 13616) : XX99XXXX...
   - BIC (Business Identifier Code)
   - Montants : 0.01€ à 1M€
   - Délais : 1-5 jours ouvrés

2. **Authentification 2FA**
   - SMS OTP (Time-based)
   - Biométrie
   - Questions de sécurité
   - Temps d'expiration (5-15 min)

3. **Calcul d'Intérêts**
   - Formules composées
   - Taux annuels
   - Méthodes de calcul (ACT/ACT, 30/360, etc.)

4. **Conformité**
   - PCI DSS (sécurité paiements)
   - AML (Anti-Money Laundering)
   - GDPR
   - KYC (Know Your Customer)

5. **Gestion de Portefeuille**
   - Actifs (actions, obligations, crypto)
   - Valorisation
   - Rendements

**Ressources à créer** :
- [ ] `contexte-financier.md` : Glossaire & explications
- [ ] `donnees-test-valides.md` : IBANs valides, numéros de compte, etc.

---

## 5. Fichiers Exercice - Spécifications

### Structure par Exercice

```
section-2/exercices/
├── 2-1-1-prompting-basics.md
├── 2-1-1-template.txt        # Template vide
├── 2-1-1-solution.md         # Solution annotée
├── 2-2-1-generate-testcases.md
├── 2-2-1-template.json
├── 2-2-1-solution.json
└── [etc...]
```

### Format Standard d'un Exercice

**Fichier** : `exercice.md`

```markdown
# Exercice X.X.X : Titre

## Objectives
- Objective 1
- Objective 2

## Contexte
[Description du contexte, situation]

## Task
[Instruction claire et précise]

## Ressources
- File template : `path/to/template.ext`
- Example prompt : [code block]
- Docs : [links]

## Durée Estimée
8-10 min

## Points de Validation
- [ ] Point 1
- [ ] Point 2

## Prochaines Étapes
[Si le temps, points bonus]
```

### Critères d'Acceptation pour chaque Exercice

- [ ] Instructions claires (non ambiguës)
- [ ] Template fourni
- [ ] Solution avec annotations
- [ ] Temps estimé réaliste
- [ ] Résultat validable facilement
- [ ] Contexte financier pertinent

---

## 6. Données de Test & Exemples Métier

### IBANs Valides (pour tests)

```
Exemples à générer :
- FR14 2004 1010 0505 0001 3M02 606
- DE89 3704 0044 0532 0130 00
- IT60 X054 2811 1010 0000 0123 456
- ES91 2100 0418 4502 0005 1332
```

### Montants de Test Financiers

```
Valides : 0.01, 10.50, 1000.00, 999999.99
Limites : 0.00 (négatif), 1000000.01 (max dépassé)
Formats : EUR, GBP, USD, CHF
```

### Données de Paiement de Test

```
Cartes de crédit fictives (format valide) : 4532 1488 0343 6467
Codes BIC : SOGEDEFF, BNPADEFF
Dates d'expiration : 12/25, 06/28
```

---

## 7. Démos Interactives

### Démo 1 : Génération de Cas de Test (Section I)

**Setup** :
- Animateur ouvre GitHub Copilot
- Tape un prompt basique : "Génère un cas de test pour un virement"

**Résultat** :
- Copilot génère un cas simple

**Puis** :
- Animateur utilise un prompt optimisé (avec contexte, format, contraintes)
- Comparaison : résultat beaucoup meilleur

**Durée** : 3-5 min

---

### Démo 2 : Génération de Script Cypress (Section III)

**Setup** :
- Ouvre Cypress boilerplate vide
- Utilise Copilot pour compléter

**Résultat** :
- Script de test pour login + paiement

**Durée** : 5 min

---

### Démo 3 : Analyse d'Erreur (Section II.3)

**Setup** :
- Montre un test défaillant avec stacktrace
- Copilot analyse et propose correction

**Durée** : 3 min

---

## 8. Spécifications de Déploiement

### Plateforme

- **Hébergement** : GitHub Pages
- **URL** : `https://zidtalel.github.io/qa-prompt-masterclass/`
- **Branche** : `gh-pages` ou `/docs`

### Processus Déploiement

1. Commit tous les fichiers HTML/CSS/JS
2. Push vers `main` ou `gh-pages`
3. GitHub Pages build automatiquement
4. URL accessible en 2-3 min

### Customisation Pré-Formation

- [ ] URL générée et testée
- [ ] Accès email envoyé aux participants
- [ ] Test de tous les liens
- [ ] Test des vidéos/démos
- [ ] Vérification accessibilité

---

## 9. Ressources & Dépendances

### Outils Requérant Accès Préalable

- [ ] GitHub Copilot (tous les participants)
- [ ] TestComplete (group de scripteurs)
- [ ] Jira + Xray (accès test accounts)
- [ ] Cypress (installé localement via npm)

### Bibliothèques Front-end (optionnel)

- Reveal.js (pour slides interactives)
- Highlight.js (pour syntax highlighting)
- Bootstrap 5 (pour responsive design)

### Dépôt Git

- Repository public : `zidtalel/qa-prompt-masterclass`
- Branch `main` : code de formation
- Branch `gh-pages` : contenu web déployé
- Issues/Discussions : support pendant/après

---

## 10. Critères de Succès

### Métriques de Formation

- [ ] 80% des participants completent tous les exercices
- [ ] Score satisfaction >= 4/5
- [ ] 95% des liens/démos fonctionnent
- [ ] Participants génèrent au moins 1 prompt utilisable

### Critères Techniques

- [ ] Site responsive + accessible
- [ ] Tous les démos live-enregistrées (fallback)
- [ ] Tous les fichiers d'exercice clonables
- [ ] Tests unitaires sur solutions (optionnel)

### Critères Pédagogiques

- [ ] Participants comprennent les 3 piliers : prompting, outils, avancés
- [ ] Participants peuvent rédiger un prompt efficace
- [ ] Participants peuvent générer un test utilisable
- [ ] Participants connaissent les ressources pour continuer

---

## 11. Ressources de Référence

### Documentation & Articles

| Ressource | URL | Note |
|-----------|-----|------|
| GitHub Copilot Docs | https://docs.github.com/en/copilot | Officiel |
| OpenAI Prompting Guide | https://platform.openai.com/docs/guides/gpt-best-practices | Techniques prompting |
| Cypress Docs | https://docs.cypress.io | Framework test |
| TestComplete | https://smartbear.com/testcomplete/ | Automation tool |

### Contexte Métier

- Normes IBAN ISO 13616
- Spéifications PCI DSS v3.2.1
- GDPR Compliance checklist

---

## 12. Timeline Production (Estimé)

| Étape | Durée | Dates |
|-------|-------|-------|
| Finaliser PRD | 3j | J0-J3 |
| Rédiger contenu sections | 5j | J4-J8 |
| Créer exercices + solutions | 5j | J9-J13 |
| Concevoir web design | 3j | J14-J16 |
| Développer pages HTML | 5j | J17-J21 |
| Tester end-to-end | 3j | J22-J24 |
| Ajustements/Feedback | 2j | J25-J26 |
| Déployer | 1j | J27 |

**Total** : ~4 semaines

---

## 13. Annexes

### A. Checklist Pré-Formation (Participants)

- [ ] Accès GitHub Copilot activé
- [ ] VS Code installé
- [ ] Node.js 18+ installé
- [ ] Cypress installé localement : `npm install cypress`
- [ ] Accès Jira/Xray testé
- [ ] TestComplete accessible
- [ ] Git configuré (user.name, user.email)
- [ ] Dépôt cloneable testé

### B. Démo Recording Checklist

- [ ] Micro clairement audible
- [ ] Écran en 1080p minimum
- [ ] Cursor visible
- [ ] Pas de données sensibles
- [ ] Duration < 5 min par démo
- [ ] Format: MP4 ou WebM

### C. Feedback Post-Formation

**Questionnaire** (5 min) :
- Clarity des concepts (1-5)
- Pertinence des exercices (1-5)
- Confiance d'appliquer (1-5)
- Ressources suffisantes (oui/non)
- Suggestionss amélioration (open-ended)

---

**Version** : 1.0 | **Date** : 16 Nov 2025 | **Statut** : Draft
