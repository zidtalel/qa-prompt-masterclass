# 📺 Guide de Préparation - Démo Live Section 1
## Génération de Scénarios Gherkin avec GitHub Copilot

> **Objectif** : Préparer une démonstration en live (5 min) montrant comment générer une suite complète de scénarios de test Gherkin avec GitHub Copilot.

---

## 🎯 Vue d'Ensemble de la Démo

### **Durée** : ~5 minutes
- ⏱️ Introduction : 1 min
- ⏱️ Génération avec IA : 3 min (dont 30 sec de génération)
- ⏱️ Analyse du résultat : 1 min

### **Objectif Pédagogique**
Montrer aux participants comment le **prompting structuré** (les 5 composantes) permet de générer 8-10 scénarios de test Gherkin en quelques secondes, vs 30-45 minutes manuellement.

---

## 🛠️ Prérequis Techniques

### **Environnement à Préparer AVANT la formation**

#### 1️⃣ **GitHub Copilot Chat**
- ✅ GitHub Copilot activé dans VS Code ou accessible via navigateur
- ✅ VS Code Extension : "GitHub Copilot Chat" installée
- ✅ Connexion GitHub active

#### 2️⃣ **Fichier de Destination** (optionnel)
```bash
# Créer un fichier vide pour copier les scénarios générés
touch scenarios-temps-passe.feature
```

#### 3️⃣ **Le Prompt Préparé**
Avoir le prompt accessible (soit dans un fichier texte, soit sur la page Section 1 HTML).

---

## 📋 Le Prompt à Utiliser

Voici le prompt complet à copier/coller dans GitHub Copilot Chat :

```
**Rôle** : Tu es expert de l'application Redmine et tu es un **Testeur Fonctionnel BDD** expérimenté dans la rédaction de scénarios Gherkin. Ton objectif est de fournir une couverture de test exhaustive.

**Tâche** : Écrit tous les scénarios de test (incluant Succès, Échecs et Limites) pour la User Story suivante.

**Contexte** :
Titre : Enregistrer le temps passé sur une demande dans un projet.
En tant que développeur ou membre de l'équipe projet,
Je veux enregistrer le temps que j'ai consacré à une demande (bug, évolution, support, etc.),
Afin de permettre le suivi précis de la charge de travail, la planification, et l'analyse des efforts par projet et par type d'activité.

**Exemple de Format Souhaité** :
Scénario: Le temps passé est enregistré avec succès
  Étant donné que l'utilisateur est sur la page de saisie du temps passé
  Et que la demande 1234 est ouverte et fait partie du Projet Alpha
  Quand il saisit 4 heures pour la demande 1234 avec l'activité 'Développement'
  Et qu'il ajoute un commentaire pertinent
  Alors le temps passé est enregistré et le solde des heures est mis à jour.

**Contraintes** : 
1. **Couverture :** Inclure au moins un scénario de **Succès** et tous les scénarios d'**Échec/Validation** basés sur les contraintes ci-dessous.
2. Tous les champs sont obligatoires (scénario d'échec si un champ est vide).
3. La demande saisie doit faire partie du projet sélectionné (scénario d'échec si la demande est d'un autre projet).
4. La date ne peut pas être une date future (scénario d'échec si la date est demain).
5. Le nombre d'heures ne peut pas dépasser 8 par jour (scénario d'échec si 8.1 heures sont saisies).
6. Le commentaire est sur 1024 caractères max (scénario d'échec si 1025 caractères sont saisis).
   Le champs Activités est type liste de valeurs. Elle contient les valeurs suivantes : Developpement, Design, Test, Support, Analyse.
7. Respecte strictement le format Gherkin de l'exemple ci-dessus pour tous les scénarios.

**Format** : Une liste complète de scénarios Gherkin prêts à intégrer dans Xray/Jira.
```

---

## 🎬 Flux de la Démo En Live

### **Avant le Démarrage (2 min de préparation)**

1. ✅ VS Code ouvert (ou navigateur avec GitHub Copilot)
2. ✅ GitHub Copilot Chat visible
3. ✅ Le prompt copié et prêt à coller
4. ✅ Diapos/notes de présentation prêtes
5. ✅ Page Section 1 HTML ouverte pour montrer le prompt aux participants

### **Pendant la Démo (5 min)**

**Phase 1 : Introduction (1 min)**
```
"Aujourd'hui, vous allez voir comment l'IA peut générer une suite complète 
de scénarios de test en quelques secondes.

Contexte : Une User Story Redmine sur l'enregistrement du temps passé.
Contraintes : 7 règles de validation à respecter.
Résultat attendu : 8-10 scénarios Gherkin complets.

Temps manuel estimé : 30-45 minutes.
Temps avec IA : ~30 secondes."
```

**Phase 2 : Préparation du Prompt (30 sec)**
1. Montrer la page Section 1 HTML
2. Cliquer sur "Afficher le Prompt Complet"
3. 💡 Souligner les 5 composantes visuellement :
   - 🔵 Rôle : "Expert Redmine + Testeur BDD"
   - 🟢 Tâche : "Écrire tous les scénarios (Succès, Échecs, Limites)"
   - 🟡 Contexte : "User Story + Exemple de format"
   - 🔴 Contraintes : "7 règles précises"
   - 🟣 Format : "Gherkin pour Xray/Jira"

**Phase 3 : Génération avec GitHub Copilot (2 min)**
1. Copier le prompt complet
2. Coller dans GitHub Copilot Chat
3. ⏱️ Attendre 20-30 secondes
4. 🎯 Observer la génération en temps réel
5. 📌 Montrer les scénarios générés (scroll pour montrer tous les scénarios)

**Phase 4 : Analyse du Résultat (1.5 min)**
```
"Regardez ce qui vient d'être généré :

✅ 1 scénario de succès
❌ 6-8 scénarios d'échec/validation :
   - Champ vide (demande, date, heures, activité, commentaire)
   - Demande d'un autre projet
   - Date future
   - Heures > 8 par jour
   - Commentaire > 1024 caractères

Chaque scénario respecte le format Gherkin strict.
Prêt pour Xray/Jira sans modification.

Temps total : ~30 secondes vs 30-45 minutes manuellement.
Gain : 90%."
```

**Phase 5 : Message Clé (30 sec)**
```
"Pourquoi ça marche si bien ?

Parce que le prompt contient les 5 composantes essentielles :
✓ Rôle spécialisé
✓ Tâche claire et exhaustive
✓ Contexte métier (User Story + Exemple)
✓ Contraintes précises (7 règles)
✓ Format attendu (Gherkin)

C'est exactement ce qu'on va maîtriser en Section II.
Vous allez apprendre à construire des prompts aussi puissants."
```

---

## 📊 Points Clés à Souligner Pendant la Démo

### **Point 1️⃣ : Couverture Exhaustive Automatique**
```
"L'IA a généré TOUS les scénarios d'échec possibles.
Manuellement, on oublie souvent des cas limites.
Ici, les 7 contraintes sont traduites en scénarios complets."
```

### **Point 2️⃣ : Format Professionnel**
```
"Chaque scénario suit le format Gherkin strict :
- Étant donné (Given)
- Quand (When)
- Alors (Then)

Directement intégrable dans Xray/Jira.
Aucun reformatage nécessaire."
```

### **Point 3️⃣ : Gain de Temps Massif**
- Sans IA : 30-45 min (analyser contraintes → identifier cas → rédiger → valider)
- Avec IA : 30 secondes (copier prompt → générer → valider)
- **Gain : 90%** du temps → libéré pour l'analyse métier approfondie

### **Point 4️⃣ : Les 5 Composantes Travaillent**
```
Montrer le tableau sur la page HTML :

🔵 Rôle : "Expert Redmine + Testeur BDD" → expertise spécialisée
🟢 Tâche : "Tous les scénarios" → couverture exhaustive
🟡 Contexte : "User Story + Exemple" → compréhension métier
🔴 Contraintes : "7 règles" → validation complète
🟣 Format : "Gherkin pour Xray" → intégration directe
```

---

## ⚠️ Gestion des Imprévus

### **Scénario 1 : GitHub Copilot Chat lent**
- **Technique** : Préparer à l'avance les scénarios générés
- **Fallback** : Montrer le résultat pré-généré
- **Message** : "Parfois l'IA prend 30 secondes, parfois 10 secondes. Normal."

### **Scénario 2 : Scénarios incomplets générés**
- **Réaction** : "Parfait ! Vous voyez que l'IA peut aussi rater.  
  C'est pourquoi on valide toujours le résultat."
- **Show & Tell** : Relancer avec une reformulation légère du prompt

### **Scénario 3 : Format Gherkin incorrect**
- **Pédagogique** : "L'exemple de format dans le prompt est crucial.  
  Sans lui, l'IA pourrait générer un format différent."
- **Demo** : Montrer l'importance de la composante "Format"

---

## 🎁 Ressources pour les Participants

Vous pouvez fournir après la démo :

1. **Le Prompt Complet** (Markdown ou PDF)
   - Accessible sur la page Section 1 HTML
   - Participants peuvent le copier directement

2. **Les Scénarios Générés** (fichier .feature)
   - Exemple concret de résultat
   - Montre la qualité attendue

3. **Cheat Sheet : Anatomie du Prompt**
   - Les 5 composantes expliquées
   - Exemples pour chaque composante

---

## 📝 Checklist Avant la Démo

- [ ] GitHub Copilot Chat actif et testé
- [ ] Le prompt copié et accessible
- [ ] Page Section 1 HTML ouverte
- [ ] Diapos/notes de présentation prêtes
- [ ] Microphone/son testé
- [ ] Écran partagé configuré (si session virtuelle)
- [ ] Fallback prêt : scénarios pré-générés en cas de problème

---

## 💡 Conseils Pro

1. **Pratiquez 2 fois avant la formation**
   - Maîtrisez le timing (5 min chrono)
   - Testez que Copilot génère bien les scénarios

2. **Gardez le Fallback**
   - Sauvegardez les scénarios générés lors de votre test
   - En cas d'erreur : montrer le résultat pré-généré

3. **Engagez les Participants**
   - "Combien pensent que l'IA peut générer 8 scénarios en 30 secondes ?"
   - "Observez comment les 5 composantes guident l'IA"
   - "Chronométrez avec moi : 30 secondes top chrono !"

4. **Transition Fluide vers Section II**
   - "Vous voyez la puissance ? Maintenant apprenons la technique"
   - "Les 5 composantes : c'est ça qu'on va maîtriser dans 10 minutes"
   - "Prochaine étape : vous allez VOUS générer vos propres tests"

---

## 🚀 Après la Démo

**Engagement des participants** :
- Demander : "Des questions sur ce qu'on vient de voir ?"
- "Le prompt est disponible sur la page Section 1, vous pouvez le tester"
- "Prêts pour la Section II ? C'est là qu'on apprend à construire ces prompts !"

**Message de Clôture** :
```
"Ce que vous venez de voir en 5 minutes aurait pris 30-45 minutes manuellement.

Mais ce n'est pas de la magie. C'est de la technique.
Et cette technique, on va la maîtriser ensemble en Section II.

Vous allez apprendre à :
✓ Identifier les 5 composantes
✓ Structurer vos prompts
✓ Obtenir des résultats de cette qualité
✓ L'appliquer à VOS cas d'usage

Prêts ? C'est parti pour l'Art du Prompting !"
```

---

## 📈 Avantages de cette Démo vs Démo Cypress

| Critère | Démo Gherkin | Démo Cypress (ancienne) |
|---------|--------------|-------------------------|
| **Préparation** | 2 min | 15-20 min |
| **Prérequis** | Copilot Chat uniquement | VS Code + Cypress + Redmine |
| **Durée** | 5 min | 10 min |
| **Complexité** | Simple | Complexe (3 étapes) |
| **Risque technique** | Faible | Élevé (Redmine, réseau) |
| **Impact visuel** | 8-10 scénarios instantanés | Code généré progressivement |
| **Pédagogie** | Focus sur les 5 composantes | Focus sur le code technique |
| **Transférabilité** | Tous (testeurs manuels + automation) | Principalement automation |

---

Bon courage ! 🎬✨



---

## 🎯 Vue d'Ensemble de la Démo

### **Durée** : ~10 minutes
- ⏱️ Étape 1 (Setup API) : 3 min
- ⏱️ Étape 2 (Test UI) : 4 min
- ⏱️ Étape 3 (Teardown) : 3 min

### **Objectif Pédagogique**
Montrer aux participants comment le **prompting avancé** (les 5 composantes) permet de générer du code de qualité en quelques minutes.

---

## 🛠️ Prérequis Techniques

### **Environnement à Préparer AVANT la formation**

#### 1️⃣ **VS Code avec Cypress**
```bash
# Créer un projet de démonstration
mkdir demo-qa-cypress
cd demo-qa-cypress
npm init -y
npm install cypress --save-dev
npx cypress open
```

#### 2️⃣ **GitHub Copilot Chat**
- ✅ GitHub Copilot activé dans VS Code
- ✅ VS Code Extension : "GitHub Copilot Chat"
- ✅ Accès à Copilot Chat (icon chat sur la gauche)

#### 3️⃣ **Redmine Local (ou Mock)**
```bash
# Option A : Docker Redmine
docker run -d -p 3000:3000 redmine:5.0

# Option B : Utiliser Redmine de demo
# https://demo.redmine.org (accès public)

# Option C : Mock local
# Vous pouvez créer un mock simple avec JSON Server
npm install -g json-server
# ... configurer un mock API
```

#### 4️⃣ **Structure du Projet Cypress**
```
demo-qa-cypress/
├── cypress/
│   ├── e2e/
│   │   └── demo.spec.ts          ← À GÉNÉRER EN LIVE
│   ├── support/
│   │   └── commands.ts
│   └── fixtures/
├── cypress.config.ts
├── package.json
└── tsconfig.json
```

---

## 📋 Les 3 Prompts à Préparer

### **Prompt #1 : Setup API (3 min)**

Copier ce texte dans GitHub Copilot Chat :

```
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

**Attendu** : Copilot génère une fonction complète pour créer le projet.

---

### **Prompt #2 : Test UI E2E (4 min)**

Copier ce texte dans GitHub Copilot Chat :

```
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

**Attendu** : Copilot génère le bloc de test complet.

---

### **Prompt #3 : Teardown API (3 min)**

Copier ce texte dans GitHub Copilot Chat :

```
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

**Attendu** : Copilot génère la fonction de teardown robuste.

---

## 🎬 Flux de la Démo En Live

### **Avant le Démarrage (5 min de préparation)**

1. ✅ VS Code ouvert avec le projet Cypress visible
2. ✅ GitHub Copilot Chat ouvert sur la gauche
3. ✅ Redmine (ou mock) accessible et testé
4. ✅ Navigateur avec la page Redmine visible en parallèle
5. ✅ Diapos/notes prêtes à côté

### **Pendant la Démo (10 min)**

**Phase 1 : Introduction (1 min)**
```
"Vous allez voir en direct comment l'IA génère du code de qualité.
En 3 étapes : Setup → Test → Teardown.
Chaque étape utilise un prompt bien structuré.
Les prompts sont affichés sur la page Section 1 que vous consultez."
```

**Phase 2 : Étape 1 - Setup API (3 min)**
1. Ouvrir GitHub Copilot Chat
2. Copier/Coller le **Prompt #1** dans le chat
3. 💡 Souligner les 5 composantes (Rôle, Tâche, Contexte, Contraintes, Format)
4. Observer la génération du code
5. 📌 Copier le code généré dans `cypress/e2e/setup.ts`

**Phase 3 : Étape 2 - Test UI (4 min)**
1. Copier/Coller le **Prompt #2** dans GitHub Copilot Chat
2. 💡 Souligner comment le contexte précédent aide l'IA
3. Observer la génération du test complet
4. 📌 Montrer le Page Object Model appliqué
5. Souligner les sélecteurs `data-test-id` standardisés
6. Copier le code dans `cypress/e2e/test.ts`

**Phase 4 : Étape 3 - Teardown (3 min)**
1. Copier/Coller le **Prompt #3** dans GitHub Copilot Chat
2. 💡 Souligner la gestion d'erreurs générée
3. Observer le code robuste
4. 📌 Montrer l'intégrité du cycle Setup → Test → Teardown
5. Copier le code dans `cypress/e2e/teardown.ts`

**Phase 5 : Conclusion (1 min)**
```
"Vous avez vu 3 tests générés en ~10 minutes.
Chaque test aurait pris 15-20 min à écrire manuellement.
La clé ? Les prompts bien structurés (5 composantes).
C'est exactement ce qu'on va maîtriser en Section II."
```

---

## 📊 Points Clés à Souligner Pendant la Démo

### **Point 1️⃣ : Les 5 Composantes Travaillent**
- ✅ **Rôle** : "Testeur Cypress E2E spécialisé en finance" → code spécialisé
- ✅ **Tâche** : Précise et claire → IA sait quoi générer
- ✅ **Contexte** : Redmine, TypeScript, POM → IA s'adapte
- ✅ **Contraintes** : data-test-id, robustesse → qualité du code
- ✅ **Format** : "Bloc it() complet" → intégration directe

### **Point 2️⃣ : Pas de Magie, du Travail d'Équipe**
```
"L'IA n'est pas magique. C'est nous qui guidons l'IA avec le prompt.
Plus le prompt est bon, meilleur est le résultat.
C'est ce qu'on appelle 'Prompt Engineering'."
```

### **Point 3️⃣ : Impact Réel**
- Sans IA : 45-60 min pour les 3 tests
- Avec IA + bon prompt : 10 min (+ validation)
- **Gain : 80%** du temps → libéré pour la stratégie

### **Point 4️⃣ : Les Limites Existent**
```
"L'IA peut aussi halluciner (inventer des sélecteurs).
D'où l'importance de la validation et du contexte bien structuré.
Vous verrez ça en pratique en Section III."
```

---

## ⚠️ Gestion des Imprévus

### **Scénario 1 : Redmine non accessible**
- **Fallback** : Utiliser des mock URLs (https://mock-redmine.local)
- **Solution** : Montrer juste le code généré, pas l'exécution

### **Scénario 2 : Copilot Chat qui "rate" la génération**
- **Technique** : Relancer le prompt ou reformuler légèrement
- **Pédagogique** : "Vous voyez ? Même l'IA a des limites. D'où l'importance du prompt."

### **Scénario 3 : Code généré incorrect**
- **Réaction** : "Normal. L'IA propose, nous validons et corrigeons. C'est du pair programming."
- **Show & Tell** : Montrer comment corriger en quelques secondes

---

## 🎁 Ressources pour les Participants

Vous pouvez fournir :

1. **Fichier projet Cypress complet** (zippé)
   - `cypress/e2e/setup.ts` (généré en live)
   - `cypress/e2e/test.ts` (généré en live)
   - `cypress/e2e/teardown.ts` (généré en live)
   - `cypress.config.ts` (déjà configuré)

2. **Cheat Sheet des 3 Prompts**
   - Format : PDF ou Markdown
   - À partager après la formation

3. **Lien vers Section 1 HTML**
   - Les 3 prompts sont déroulants sur la page
   - Participants peuvent les consulter pendant la formation

---

## 📝 Checklist Avant la Démo

- [ ] VS Code ouvert avec le projet Cypress
- [ ] GitHub Copilot Chat actif et testé
- [ ] Redmine (ou mock) accessible
- [ ] Les 3 prompts copiés/accessibles
- [ ] Terminal prêt pour `npm test` si besoin
- [ ] Diapos/notes de présentation prêtes
- [ ] Navigateur avec démo.redmine.org ou local
- [ ] Écran partitionné : Code + Redmine en parallèle
- [ ] Microphone/son testé pour la demo
- [ ] Caméra testée si session vidéo

---

## 💡 Conseils Pro

1. **Pratiquez 2-3 fois avant la formation**
   - Maîtrisez le timing (10 min chrono)
   - Soyez à l'aise avec GitHub Copilot Chat

2. **Gardez des sauvegardes**
   - Sauvegardez les 3 codes générés avant la démo
   - Fallback en cas d'erreur : montrer les fichiers pré-générés

3. **Engagez les participants**
   - "Qui pense que l'IA peut générer du code de test ?"
   - "Observez les 5 composantes du prompt"
   - "Notez le gain de temps"

4. **Transition fluide vers Section II**
   - "Maintenant que vous voyez la magie, apprenons la science"
   - "Les 5 composantes du prompt : c'est ça qu'on va maîtriser"
   - "Vous vous demanderez comment vous aviez codé avant"

---

## 🚀 Après la Démo

**Engagement des participants** :
- Demander : "Des questions sur ce qu'on vient de voir ?"
- "Vous avez tous 10 min pour regarder les prompts sur la page Section 1"
- "Prêts pour la Section II ? Là, ce sera **vous** qui allez générer le code !"

---

Bon courage ! 🎬✨

