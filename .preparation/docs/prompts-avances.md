# 📌 Prompts Avancés - Librairie de Référence QA

> **Utilisation** : Copiez-collez les prompts ci-dessous dans GitHub Copilot, adaptez le contexte à votre projet, et exécutez. Chaque prompt est classé par cas d'usage et outil.

---

## 📋 Table des Matières

1. [GitHub Copilot - Setup API (Redmine)](#github-copilot---setup-api-redmine)
2. [GitHub Copilot - Tests Cypress](#github-copilot---tests-cypress)
3. [GitHub Copilot - Teardown API](#github-copilot---teardown-api)
4. [GitHub Copilot - Maintenance & Sélecteurs](#github-copilot---maintenance--sélecteurs)
5. [Jira/Xray - Génération Gherkin](#jiraxray---génération-gherkin)
6. [Jira/Xray - Conditions Limites](#jiraxray---conditions-limites)
7. [Locus - Analyse de Logs](#locus---analyse-de-logs)
8. [Chain-of-Thought (CoT) Avancé](#chain-of-thought-cot-avancé)
9. [Persona Prompting](#persona-prompting)
10. [Few-Shot Prompting](#few-shot-prompting)

---

## GitHub Copilot - Setup API (Redmine)

### **Prompt Avancé 1 : Création de Projet (API)**

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
- Utilise Authorization si nécessaire

**Format** : Le code TypeScript de la fonction complète, prêt à l'emploi.
```

**Cas d'usage** : Générer le code de setup pour un test complet (Arrange).

---

### **Prompt Avancé 2 : Test UI E2E Cypress**

```markdown
**Rôle** : Tu es un testeur Cypress E2E spécialisé en finance.

**Tâche** : Écris un scénario de test Cypress complet pour modifier la description d'un projet Redmine existant.

**Contexte** : 
- Le projet a été créé à l'étape précédente
- L'ID du projet est connu (ex: test-modify)
- Nous utilisons le Page Object Model (POM)
- Les sélecteurs doivent utiliser l'attribut data-test-id

**Étapes à couvrir** : 
1. Naviguer vers la page `projects/test-modify/settings`
2. Attendre le chargement du formulaire
3. Trouver le champ Description (hypothèse : textarea#project_description)
4. Entrer la nouvelle valeur : 'Nouvelle description testée par IA'
5. Cliquer sur le bouton Enregistrer (data-test-id="btn-save-project")
6. Vérifier que le message de succès s'affiche (data-test-id="success-message")

**Contraintes** :
- Gère les timeouts et les attentes asynchrones
- Ajoute un cy.wait() si nécessaire (mais préfère cy.get().should())
- Le test doit être isolé et idempotent

**Format** : Le bloc `it()` complet, avec les imports nécessaires.
```

**Cas d'usage** : Générer le test UI central (Act + Assert).

---

### **Prompt Avancé 3 : Teardown API**

```markdown
**Rôle** : Ingénieur DevOps spécialisé en nettoyage de données.

**Tâche** : Crée une fonction asynchrone nommée `deleteProjectAPI(projectId)` 
qui utilise `cy.request('DELETE', ...)` pour supprimer le projet Redmine.

**Contexte** : 
- L'API de suppression de Redmine utilise le endpoint `/projects/{project_id}.json`
- La méthode HTTP est DELETE
- L'authentification se fait via header `X-Redmine-API-Key`
- Nous utilisons Cypress avec TypeScript

**Contraintes** : 
- La fonction doit être robuste
- Elle doit vérifier le code de statut HTTP 204 (No Content) ou 200 (OK)
- Elle doit gérer les erreurs (ex: projet inexistant)
- Elle doit être appelée dans `afterEach()` pour garantir le nettoyage

**Format** : Le code TypeScript de la fonction complète, avec gestion d'erreurs.
```

**Cas d'usage** : Générer le code de nettoyage (Teardown).

---

## GitHub Copilot - Tests Cypress

### **Prompt Avancé 4 : Génération de Fonction Page Object**

```markdown
**Rôle** : Développeur TypeScript avec expertise Cypress Page Object Model.

**Tâche** : Ajoute une nouvelle méthode `verifyTotal()` à la classe `PanierPage` 
qui prend un argument de type `number` et vérifie si le total affiché est égal à cet argument.

**Contexte** :
```typescript
class PanierPage {
  visit() {
    cy.visit('/panier');
  }
  
  addProductToCart(productId: string, quantity: number) {
    cy.get(`[data-test-id="product-${productId}"]`).click();
    cy.get('[data-test-id="quantity-input"]').clear().type(quantity.toString());
    cy.get('[data-test-id="add-to-cart"]').click();
  }
  
  // À compléter :
  verifyTotal(expectedTotal: number) {
    // ...
  }
}
```

**Contraintes** :
- Le sélecteur du total est `[data-test-id="total-amount"]`
- Le texte contient le symbole monétaire € (ex: "150,00 €")
- Fais un parsing pour extraire le montant
- Utilise `cy.should()` pour l'assertion
- La méthode doit retourner `this` pour le chainement

**Format** : Uniquement le code de la méthode, avec commentaires explicatifs.
```

**Cas d'usage** : Générer des fonctions utilitaires réutilisables pour le POM.

---

### **Prompt Avancé 5 : Débogage de Flakiness**

```markdown
**Rôle** : Débogueur Test Automation spécialisé en Cypress.

**Tâche** : Identifie la ligne exacte du code de test à modifier et propose DEUX solutions 
pour résoudre le Timeout ci-dessous. L'une avec `cy.wait()` et l'autre avec une attente 
conditionnelle (meilleure pratique).

**Contexte** : 
```
AssertionError: Timed out retrying after 4000ms: 
Expected to find element: [data-test-id="btn-valider-panier"], 
but never found it.

Because this element was required to complete the action: click().

The previous command was: cy.get('[data-test-id="btn-ajouter-produit"]').click()

The application appears to be stalled.
Attempting to click on a button that is hidden or disabled due to asynchronous operation.
```

**Code actuel** :
```typescript
it('Ajout produit au panier', () => {
  cy.visit('/produits');
  cy.get('[data-test-id="btn-ajouter-produit"]').click();
  cy.get('[data-test-id="btn-valider-panier"]').click();
});
```

**Contraintes** :
- Explique pourquoi le problème occur (attente asynchrone)
- Solution 1 : Avec `cy.wait()` - aide-moi à trouver le bon endpoint à attendre
- Solution 2 : Avec `cy.get().should()` - approche recommandée
- Les deux solutions doivent être complètes et prêtes à l'emploi

**Format** : Deux blocs de code TypeScript avec annotations.
```

**Cas d'usage** : Debugger les tests flaky avec l'aide de l'IA.

---

## GitHub Copilot - Maintenance & Sélecteurs

### **Prompt Avancé 6 : Robustesse des Sélecteurs**

```markdown
**Rôle** : Expert QA en stabilité des sélecteurs Cypress.

**Tâche** : Évalue la robustesse de ces 3 sélecteurs Cypress et propose des améliorations :

1. `cy.get('button').first()` (sélectionner le premier bouton)
2. `cy.get('.btn-primary')` (classe CSS)
3. `cy.get('[data-test-id="submit-payment"]')` (attribut data-test-id)

**Contexte** :
- Le projet respecte la convention data-test-id pour la sélection
- L'interface UI change régulièrement (refactoring CSS)
- Les tests doivent rester stables pendant 6 mois minimum

**Contraintes** :
- Classe chaque sélecteur par score de robustesse (1-5)
- Explique les risques de chaque approche
- Recommande la meilleure option avec justification

**Format** : Un tableau Markdown comparatif avec scores et explications.
```

**Cas d'usage** : Former les QA à la sélection robuste des éléments UI.

---

## Jira/Xray - Génération Gherkin

### **Prompt Avancé 7 : Transformation User Story → Gherkin**

```markdown
**Rôle** : Analyste QA expert en Behaviour Driven Development (BDD).

**Tâche** : Transforme le texte de la User Story Jira ci-dessous en 5 scénarios de test 
complets au format Gherkin.

**Contexte** : 
La Story doit couvrir les cas suivants :
1. Cas positif (Succès)
2. Erreur de validation (montant invalide)
3. Cas limite - Montant zéro
4. Cas limite - Montant très grand (>999,999.99€)
5. Cas d'erreur - Compte invalide

**User Story Jira** :
```
Titre : Enregistrer le temps passé sur une demande dans un projet

En tant que développeur ou membre de l'équipe projet,
Je veux enregistrer le temps que j'ai consacré à une demande 
(bug, évolution, support, etc.),
Afin de permettre le suivi précis de la charge de travail, 
la planification, et l'analyse des efforts par projet et par type d'activité.

Critères d'acceptation :
- Le temps passé doit être en heures (format : XX.XX, ex: 2.5)
- La date ne peut pas être une date future
- Le temps max par jour est 8 heures
- Le commentaire est limité à 1024 caractères
- La demande saisie doit appartenir au projet sélectionné
```

**Contraintes** :
- Format Gherkin strict : Scénario, Étant donné, Quand, Alors
- Utilise des données réalistes (contexte financier)
- Chaque scénario doit être indépendant et testable
- Ajoute les balises @tag appropriées (ex: @validationTemps, @limiteFonctionnelle)

**Format** : Le code Gherkin complet, prêt à copier/coller dans Xray ou un fichier .feature.
```

**Cas d'usage** : Générer rapidement les cas de test structurés pour Xray.

---

### **Prompt Avancé 8 : Identification de Conditions Limites**

```markdown
**Rôle** : Testeur d'Exploration en Test aux Limites (Boundary Testing).

**Tâche** : À partir de la User Story ci-dessous, liste 10 valeurs d'entrée ou scénarios 
de conditions aux limites (Boundary Conditions) qui pourraient faire échouer la validation 
du champ 'Temps passé'.

**Contexte** :
Champ : "Temps passé" (Durée en heures)
- Format attendu : Nombre décimal positif (XX.XX)
- Limite inférieure : 0 heures
- Limite supérieure : 8 heures par jour
- Précision : maximum 2 décimales
- Domaine métier : Finance/RH

**Contraintes** :
- Classe les cas en 3 catégories : Valide Nominale, Limite, Invalide
- Pour chaque cas, explique pourquoi c'est une condition limite
- Propose le résultat attendu pour chaque cas

**Format** : Un tableau Markdown avec colonnes :
| Cas # | Valeur de Test | Catégorie | Raison | Résultat Attendu |
```

**Cas d'usage** : Identifier les cas de test "sombres" non évidents.

---

## Locus - Analyse de Logs

### **Prompt Avancé 9 : Analyse d'Incident avec Chain-of-Thought**

```markdown
**Rôle** : Analyste DevOps Senior, spécialisé en interprétation de logs Redmine.

**Tâche** : Analyse le log d'incident ci-dessous ET décris TON RAISONNEMENT ÉTAPE PAR ÉTAPE 
(Chain-of-Thought).

**Contexte** : 
Le client a reçu une erreur 500 après avoir tenté de modifier la description d'un projet 
via l'UI (déclenchant une requête PATCH /projects/test-modify.json).

**Log Complet** :
```
[2025-11-02T14:35:12.601Z] INFO [a9f3b2d1] - Request received: PATCH /projects/test-modify.json from 192.168.1.10
[2025-11-02T14:35:12.650Z] INFO [a9f3b2d1] - User 'qa-tester' authorized successfully. Starting project update.
[2025-11-02T14:35:12.755Z] INFO [a9f3b2d1] - Database query: UPDATE projects SET description = 'Nouvelle description testée par IA' WHERE identifier = 'test-modify'
[2025-11-02T14:35:12.789Z] ERROR [a9f3b2d1] - **ConstraintViolationException: Column 'updated_on' cannot be NULL.** Transaction rollback initiated.
[2025-11-02T14:35:12.805Z] WARN [a9f3b2d1] - Could not commit transaction. Retrying logic failed.
[2025-11-02T14:35:12.850Z] ERROR [a9f3b2d1] - **HTTP 500 Internal Server Error sent to client.** Cause: Transaction failed due to backend database constraint.
[2025-11-02T14:35:12.899Z] INFO [a9f3b2d1] - Response time: 298ms.
```

**Contraintes** :
1. DÉCRIS TON RAISONNEMENT ÉTAPE PAR ÉTAPE pour déterminer la cause
2. Isole et liste les deux lignes de log les plus critiques (ERROR ou WARN)
3. Fournis la cause racine en termes de base de données
4. Propose une action de remédiation pour l'équipe de développement

**Format** : Un rapport Markdown structuré avec sections claires.
```

**Cas d'usage** : Debugger les incidents en production rapidement.

---

## Chain-of-Thought (CoT) Avancé

### **Prompt Avancé 10 : CoT pour Validation Financière**

```markdown
**Rôle** : Ingénieur QA spécialisé en validation de données financières.

**Tâche** : Valide le virement international ci-dessous et explique TON RAISONNEMENT 
ÉTAPE PAR ÉTAPE pour confirmer la validité.

**Contexte** :
Virement international SEPA :
- Montant : 1,500.50€
- Devise : EUR
- Date : 2025-11-16
- IBAN Débiteur : FR14 2004 1010 0505 0001 3M02 606
- IBAN Créditeur : DE89 3704 0044 0532 0130 00
- BIC Créditeur : DEUTDEDE
- Motif : Paiement facture INV-2025-0512

**Contraintes** :
1. Valide chaque champ selon les normes ISO (13616 pour IBAN, 9362 pour BIC)
2. Vérifie la cohérence devise/montant
3. Vérifie les contraintes métier (ex: pas de montant future, montant > 0)
4. Décris chaque étape de validation

**Format** : Un rapport de validation structuré avec ✅/❌ pour chaque étape.
```

**Cas d'usage** : Valider les données financières complexes avec IA.

---

## Persona Prompting

### **Prompt Avancé 11 : Persona - QA Senior Redmine**

```markdown
**Rôle** : Tu es un QA Senior avec 8 ans d'expérience en automatisation Redmine.
Tu as une expertise reconnue en Cypress et en tests E2E.
Tu respectes les bonnes pratiques : DRY, POM, data-driven testing.
Tu rédiges du code maintenable et documenté.

**Tâche** : Génère une suite de test E2E pour le flux complet de modification d'un projet.

**Contexte** :
- Application : Redmine
- Framework : Cypress avec TypeScript
- Durée du projet : 6 mois (tests doivent être maintenables à long terme)
- Équipe : 3 QA + 2 développeurs

**Contraintes** :
- Code production-ready
- Doit respecter le Page Object Model
- Doit utiliser des sélecteurs data-test-id
- Doit inclure la gestion des erreurs et timeouts
- Doit être documenté avec des commentaires clairs

**Format** : Suite complète, prête à merger dans le CI/CD.
```

**Cas d'usage** : Générer du code de qualité élevée en donnant un rôle à l'IA.

---

## Few-Shot Prompting

### **Prompt Avancé 12 : Few-Shot - Format Gherkin Cohérent**

```markdown
**Rôle** : Analyste QA expert en rédaction BDD/Gherkin.

**Tâche** : Écris 5 scénarios de test pour la User Story suivante, 
en respectant EXACTEMENT le format de l'exemple donné ci-dessous.

**Exemple de Format Attendu** :
```gherkin
@validationIBAN
Scénario : Validation d'IBAN français valide
  Étant donné que l'utilisateur est sur la page de saisie de virement
  Et qu'il a saisi l'IBAN "FR14 2004 1010 0505 0001 3M02 606"
  Quand il clique sur le bouton "Valider IBAN"
  Alors le système affiche le message "IBAN valide"
  Et le bouton "Continuer" devient actif
```

**User Story** :
```
Titre : Validation des montants de virement

Critères d'acceptation :
- Montant minimum : 0.01€
- Montant maximum : 999,999.99€
- Format : XX,XX ou XXXXX,XX
- Devise : EUR obligatoire
```

**Contraintes** :
- Respecte EXACTEMENT le format de l'exemple
- Inclut @tag appropriées
- Couvre les cas : Succès, Montant zéro, Montant >limite, Format invalide, Devise invalide

**Format** : Uniquement le code Gherkin, sans explications additionnelles.
```

**Cas d'usage** : Générer des scénarios cohérents en format standard.

---

## Techniques Avancées de Prompting

### **Prompt Avancé 13 : Prompt Chaining - Générer Test Complet**

```markdown
**Instruction Maître** : Nous allons générer un test Cypress E2E complet via 3 étapes enchaînées.

**Étape 1 - Setup** (Exécute d'abord) :
"Rôle: API QA. Tâche: Génère la fonction createProjectAPI() pour Cypress. 
Retourne: Bloc de code TypeScript."

**Étape 2 - Test Principal** (Après Étape 1) :
"Rôle: Testeur E2E. Tâche: Génère le test de modification de description. 
Contexte: Le projet est créé par l'étape 1. 
Utilise le résultat de l'étape 1 comme référence."

**Étape 3 - Teardown** (Après Étape 2) :
"Rôle: DevOps. Tâche: Génère la fonction deleteProjectAPI(). 
Contexte: Nettoyer le projet créé à l'étape 1."

**Format Final** : Un fichier complet avec les 3 étapes intégrées.
```

**Cas d'usage** : Générer des tests complexes en les décomposant en sous-prompts.

---

### **Prompt Avancé 14 : RAG (Retrieval-Augmented Generation) - Contexte Spécifique**

```markdown
**Rôle** : Ingénieur QA Redmine utilisant le contexte du projet.

**Tâche** : Génère un test de modification de projet en utilisant le contexte fourni.

**Contexte Projet** (à adapter) :
```yaml
Application: Redmine v4.2
Framework: Cypress v13.0
TypeScript: Oui
BaseURL: https://redmine.staging.example.com
API_KEY: *** (déjà configurée)
Conventions:
  - Sélecteurs: data-test-id obligatoire
  - Nommage: snake_case pour les fonctions
  - POM: Structure Pages/ et Specs/
  - Timeout: 5000ms par défaut
```

**Contraintes** :
- Respecte les conventions du projet listées ci-dessus
- Utilise les sélecteurs définis dans la Page Object
- Respecte le timeout configuré

**Format** : Code prêt à l'emploi dans le projet.
```

**Cas d'usage** : Générer du code adapté au contexte réel du projet.

---

## 🎯 Guide d'Utilisation

### Comment Utiliser Ces Prompts ?

1. **Copier le prompt complet** (y compris Rôle + Tâche + Contexte + Contraintes + Format)
2. **Adapter le contexte** à votre projet (URLs, noms, identifiants)
3. **Coller dans GitHub Copilot Chat**
4. **Exécuter et itérer** si le résultat ne convient pas

### Prompts Essentiels (Top 5)

| Priorité | Prompt | Utilisation |
|----------|--------|------------|
| 🔴 Critique | #2 Test UI Cypress | Générer tous les tests UI |
| 🔴 Critique | #7 Gherkin Jira | Générer les cas de test structurés |
| 🟠 Important | #1 Setup API | Générer les préconditions |
| 🟠 Important | #9 Analyse Logs CoT | Debugger les incidents |
| 🟡 Utile | #6 Robustesse Sélecteurs | Valider la qualité des tests |

---

## 📝 Résumé des Cas d'Usage

| Cas d'Usage | Prompt # | Outil | Temps Typique |
|------------|----------|------|---------------|
| Créer une fonction API | 1, 3 | Copilot | 2-3 min |
| Écrire un test UI | 2, 4 | Copilot | 5-10 min |
| Générer cas de test Gherkin | 7, 12 | Copilot / Xray | 5-10 min |
| Identifier conditions limites | 8 | Copilot | 3-5 min |
| Debugger test flaky | 5 | Copilot | 5-10 min |
| Analyser incident production | 9 | Copilot / Locus | 10-15 min |
| Valider données financières | 10 | Copilot | 2-3 min |
| Evaluer robustesse sélecteurs | 6 | Copilot | 5 min |

---

**Version** : 1.0 | **Date** : 16 Nov 2025 | **Auteur** : Formation QA-IA  
**Mise à jour** : Basée sur contenu détaillé du plan de formation
