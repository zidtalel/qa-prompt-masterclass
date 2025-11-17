# 📂 Dossier `.preparation/` - Guide de Navigation

> **Dossier isolé de préparation** : Tous les documents pour construire la formation.

## 🎯 Démarrage Rapide

### Je suis un **Animateur** 📺
👉 Commencer par : **`INSTRUCTIONS.md`**
- Contient la structure complète de la formation
- Sections I-IV **entièrement détaillées**
- Timing précis et exercices numérotés
- Livrables clairement énumérés

Ensuite :
- `prompts-avances.md` - Pour tester les 14 prompts
- `ressources.md` - Pour les cas d'usage pratiques

### Je suis un **Participant** 👥
👉 Commencer par : **`ressources.md`**
- Cas d'usage détaillés par outil (Section III)
- Exercices pratiques avec timing
- 14 prompts prêts à copier/coller

Ensuite :
- `prompts-avances.md` - Pour tous les prompts avec explications
- `contexte-financier.md` - Pour comprendre le domaine

### Je suis un **Décideur** 💼
👉 Commencer par : **`SYNTHESE-EXECUTIVE.md`** (10 min)
- Vue d'ensemble complète
- Coûts, ressources, timeline
- ROI estimé

Sinon : **`SYNTHESE-EXECUTIVE.md`** → **`INDEX.md`** → autres ressources

---

## 📑 Fichiers Principaux (14 fichiers)

### 📖 **Documentation Stratégique** (7 fichiers ~ 60 KB)

| Fichier | Audience | Objectif | Priorité |
|---------|----------|----------|----------|
| **INSTRUCTIONS.md** (33 KB) | Animateur | ⭐ Structure complète formation (Sections I-IV détaillées, 20+ exercices) | **LIRE D'ABORD** |
| **PRD.md** (21 KB) | PM/Animateur | Spécifications détaillées des livrables | Important |
| **SYNTHESE-EXECUTIVE.md** (6.5 KB) | Décideurs | Résumé 10 min (objectif, coûts, timeline) | Optionnel |
| **INDEX.md** (5.6 KB) | Tous | Entrée par rôle (participants, animateur, PM) | Navigation |
| **00-RESUME-COMPLET.md** (7.6 KB) | Tous | Overview exhaustif de tous les fichiers | Référence |
| **FINAL-SUMMARY.md** (8.4 KB) | Tous | Résumé historique creation (session précédente) | Référence |
| **README.md** | Vous êtes ici | Guide de navigation du dossier | 👈 Vous êtes ici |

---

### 📚 **Ressources Pédagogiques** (3 fichiers ~ 51 KB)

| Fichier | Contenu | Utilisation | Créé |
|---------|---------|-------------|------|
| **prompts-avances.md** ⭐ (19.5 KB) | **14 prompts prêts à l'emploi** pour Redmine/Cypress/Xray/Locus | Copier/coller dans Copilot Chat. Table des matières navigable. | 16 Nov ✨ |
| **ressources.md** ⭐ (20.6 KB) | Infrastructure, contexte, **7 cas d'usage détaillés**, **exercice intégré 30-40 min** | Participants Section III + démos pratiques. **Lire avant la formation** | 16 Nov ✨ |
| **contexte-financier.md** (11.3 KB) | Standards IBAN/BIC/ISO 13616, montants, données test réalistes | Référence métier (domaine Finance) | Existant |

---

### 📋 **Planification & Projet** (2 fichiers ~ 19 KB)

| Fichier | Contenu | Utilisation |
|---------|---------|-------------|
| **timeline.md** (8.8 KB) | Calendar 34 jours : 5 phases, jalons, ressources | Planning production (Phase 1-5) |
| **checklist-deploiement.md** (9.6 KB) | Validation complète : pré-déploiement, tests, formation day | Checklist go-live |

---

### 🏗️ **Architecture & Structure** (1 fichier ~ 11 KB)

| Fichier | Contenu | Utilisation |
|---------|---------|-------------|
| **STRUCTURE-DOCS-PUBLIC.md** (11 KB) | Architecture `/docs/` pour GitHub Pages (répertoires, fichiers HTML, assets) | Concevoir structure web (Phase 3) |

---

## 📊 Vue d'Ensemble Globale

```
.preparation/ (14 fichiers, ~141 KB)
│
├── 📖 DOCUMENTATION STRATÉGIQUE (7 fichiers)
│   ├── INSTRUCTIONS.md ⭐⭐⭐ (LIRE D'ABORD)
│   ├── PRD.md
│   ├── SYNTHESE-EXECUTIVE.md
│   ├── INDEX.md
│   ├── 00-RESUME-COMPLET.md
│   ├── FINAL-SUMMARY.md
│   └── README.md (vous êtes ici)
│
├── 📚 RESSOURCES PÉDAGOGIQUES (3 fichiers)
│   ├── prompts-avances.md ⭐ (14 prompts prêts)
│   ├── ressources.md ⭐ (Cas d'usage + exercices)
│   └── contexte-financier.md (Domaine Finance)
│
├── 📋 PLANNING (2 fichiers)
│   ├── timeline.md (34 jours production)
│   └── checklist-deploiement.md (Validation)
│
└── 🏗️ ARCHITECTURE (1 fichier)
    └── STRUCTURE-DOCS-PUBLIC.md (GitHub Pages)
```

---

## 🆕 Mise à Jour Récente (16 Nov 2025)

### **Source** : Intégration du plan détaillé "Plan de Formation IA.md"

#### Fichiers Modifiés
✅ **INSTRUCTIONS.md** - Sections I-IV enrichies (33 KB, **+50% contenu**)
- Section I : "IA comme accélérateur" + démo Waouh
- Section II : Anatomie du prompt + 3 techniques avancées
- Section III : Cas d'usage par outil (Redmine, Cypress, Xray, TestComplete)
- Section IV : **COMPLÈTEMENT DOCUMENTÉE** (injection contexte, Mutant Testing, etc.)

✅ **ressources.md** - Cas d'usage détaillés + exercice intégré (20.6 KB, **+300 lignes**)
- 7 cas d'usage détaillés (Redmine, Cypress, Xray, TestComplete)
- Exercice intégré : test E2E complet 30-40 min

#### Fichiers Créés
✨ **prompts-avances.md** - 14 prompts prêts à l'emploi (19.5 KB, **NOUVEAU**)
- Prompts 1-3 : Setup/Test/Teardown Redmine
- Prompts 4-7 : Cypress & Jira/Xray
- Prompts 8-12 : Techniques avancées
- Prompts 13-14 : Chaining & RAG

✨ **MISE-A-JOUR-SYNTHESE.md** - Détail complet des changements (11.7 KB, **NOUVEAU**)
- Interconnexions entre fichiers
- Metrics avant/après intégration
- Prochaines étapes recommandées

#### Impact Global
- 📈 **Couverture** : Section I-IV → **100% documentées** (avant ~50%)
- 🎯 **Cas d'usage** : 0 → **7 détaillés** (pratiques réelles)
- 💾 **Prompts** : 0 → **14 spécifiques** prêts à copier/coller
- ⏱️ **Exercices** : ~8 génériques → **20+ numérotés et détaillés**

👉 **Lire `MISE-A-JOUR-SYNTHESE.md`** pour comprendre tous les changements

---

## ✅ Checklist d'Utilisation

### Avant Démarrage (Jour -7)

- [ ] **Lire** `INSTRUCTIONS.md` (vue d'ensemble 30 min)
- [ ] **Consulter** `MISE-A-JOUR-SYNTHESE.md` (changements 15 min)
- [ ] **Valider** les 14 prompts dans `prompts-avances.md` avec votre Copilot
- [ ] **Adapter** les exemples Redmine à votre version/instance
- [ ] **Tester** les cas d'usage de `ressources.md` (Section III)

### Pendant Préparation (Jour 0-30)

- [ ] **Suivre** `timeline.md` pour les jalons
- [ ] **Créer** les pages HTML basées sur `INSTRUCTIONS.md`
- [ ] **Organiser** ressources par section dans `/docs/section-X/`
- [ ] **Préparer** les démos en direct (ou pré-enregistrer comme fallback)
- [ ] **Créer** les fichiers d'exercices (templates vides pour participants)

### Avant Formation (Jour -1)

- [ ] **Valider** tous les liens (internes + externes)
- [ ] **Tester** tous les exercices end-to-end
- [ ] **Vérifier** accès (Jira, Xray, TestComplete, GitHub Copilot)
- [ ] **Utiliser** `checklist-deploiement.md` pour validation finale
- [ ] **Préparer** les démos enregistrées (fallback si live échoue)

---

## 🔗 Flux de Lecture Recommandé

### Pour Animateur
```
INSTRUCTIONS.md (structure)
    ↓
prompts-avances.md (tester les prompts)
    ↓
ressources.md (cas d'usage + exercices)
    ↓
contexte-financier.md (domaine métier)
    ↓
timeline.md (planning production)
    ↓
STRUCTURE-DOCS-PUBLIC.md (architecture web)
```

### Pour Participant
```
ressources.md (setup + cas d'usage)
    ↓
prompts-avances.md (tous les prompts)
    ↓
contexte-financier.md (domaine métier)
    ↓
INSTRUCTIONS.md (si besoin de détails)
```

### Pour Décideur
```
SYNTHESE-EXECUTIVE.md (10 min)
    ↓
timeline.md (timeline + ressources)
    ↓
PRD.md (spécifications)
```

---

## 📚 Cas d'Usage Clés Documentés

### Section III - Ressources.md

| Cas # | Contexte | Outil | Prompt # | Temps |
|-------|----------|------|----------|-------|
| 1 | Créer projet Redmine via API | Copilot | 1 | 2-3 min |
| 2 | Test UI E2E modification projet | Copilot | 2 | 5-10 min |
| 3 | Nettoyer projet après test (API) | Copilot | 3 | 2-3 min |
| 4 | User Story Jira → Gherkin | Copilot/Xray | 7 | 5-10 min |
| 5 | Identifier conditions limites | Copilot | 8 | 3-5 min |
| 6 | Script TestComplete pour 2FA | Copilot | 6 | 10-15 min |
| 7 | Page Object Model Cypress | Copilot | 4 | 5-10 min |

### Exercice Intégré (30-40 min)

**Test E2E Complet** : Assembler Setup + Test + Teardown

```typescript
// transfert.spec.ts
describe('Redmine - Gestion de Projet', () => {
  let projectId: number;
  
  before(() => {
    // createProjectAPI() - Cas #1
  });
  
  it('Modifier la description du projet', () => {
    // Test UI E2E - Cas #2
  });
  
  after(() => {
    // deleteProjectAPI(projectId) - Cas #3
  });
});
```

---

## 💡 Tips Pratiques

### Pour l'Animateur ✓
1. **Tester les prompts** AVANT la formation (vérifier sortie Copilot)
2. **Adapter les URLs** Redmine à votre instance
3. **Pré-enregistrer** les démos comme fallback si live échoue
4. **Imprimer les prompts** pour partage participants
5. **Créer une Prompts Library** équipe après la formation

### Pour les Participants ✓
1. **Copier/coller** les prompts depuis `prompts-avances.md` (numérotés)
2. **Adapter le contexte** (URLs, versions, conventions)
3. **Sauvegarder** les prompts qui fonctionnent
4. **Tester** les cas d'usage dans votre environnement
5. **Partager** les prompts optimisés avec l'équipe

---

## 🎯 Objectifs par Fichier

| Fichier | Objectif Principal | Critère de Succès |
|---------|-------------------|-------------------|
| INSTRUCTIONS.md | Guider la construction de la formation | Tous modules clairs + timing respecté |
| prompts-avances.md | Fournir prompts prêts à l'emploi | 14 prompts testés + numérés |
| ressources.md | Support pratique pendant formation | Cas d'usage fonctionnels + exercice réussi |
| PRD.md | Spécifier tous les livrables | Specs validées + critères d'acceptation |
| contexte-financier.md | Contextualiser dans finance | Exemples réalistes + données valides |
| timeline.md | Planifier production en 34 jours | Jalons atteints + ressources allouées |
| STRUCTURE-DOCS-PUBLIC.md | Définir architecture GitHub Pages | Pages responsive + navigation fluide |
| checklist-deploiement.md | Valider go-live | Tous items cochés + 0 blockers |

---

## 🚀 Prochaine Étape

### Vous êtes Prêt !

✅ **14 fichiers de préparation créés** (~141 KB)  
✅ **Sections I-IV entièrement documentées**  
✅ **14 prompts avancés prêts à l'emploi**  
✅ **7 cas d'usage détaillés + exercice intégré**  
✅ **Timeline 34 jours + checklist déploiement**

### Maintenant :

1. **👉 Lire `INSTRUCTIONS.md`** (30-45 min)
2. Tester les prompts de `prompts-avances.md` (1 heure)
3. Créer les pages HTML `/docs/` suivant `STRUCTURE-DOCS-PUBLIC.md`
4. Suivre `timeline.md` pour production

---

**Version** : 2.0 | **Date** : 16 Nov 2025  
**Statut** : ✅ **Préparation Complète - Prêt pour Production**

**Questions ?** Consulter `SYNTHESE-EXECUTIVE.md` ou `MISE-A-JOUR-SYNTHESE.md`
