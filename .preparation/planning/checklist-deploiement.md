# ✅ Checklist de Déploiement - Formation QA & IA

## Phase Pré-Déploiement (J-5 à J-1)

### Validation Contenu

- [ ] Tous les 4 fichiers INSTRUCTIONS.md validés par stakeholder
- [ ] PRD complet et signé off
- [ ] Tous les exemples de code testés et exécutables
- [ ] Contexte métier financier pertinent et à jour
- [ ] Ressources et liens externes vérifiés (pas de 404)
- [ ] Spelling & grammaire vérifiés (relecture)

### Validation Exercices

- [ ] 4 sections × 4-5 exercices chacun = 16+ exercices
- [ ] Chaque exercice : instructions claires + template + solution
- [ ] Solutions testées et validées
- [ ] Durées estimées réalistes (testées avec utilisateurs réels)
- [ ] Données de test appropriées (IBANs valides, montants réalistes, etc.)
- [ ] Exercices compatible tous niveaux (manuel + scripteur)

### Validation Structure Web

- [ ] Architecture de dossiers crée : `docs/section-{1..4}/`
- [ ] Fichiers HTML générés pour chaque page
- [ ] Navigation entre pages testée
- [ ] Responsive design testé (desktop + mobile)
- [ ] CSS globaux appliqués
- [ ] Images/assets optimisées (< 100KB/image)

---

## Phase Déploiement Initial (J)

### Configuration GitHub

- [ ] Repository créé (public) : `zidtalel/qa-prompt-masterclass`
- [ ] README.md complet dans root
- [ ] `.gitignore` configuré (node_modules, .env, etc.)
- [ ] Branche `gh-pages` OU `/docs` configurée
- [ ] Branch protection activée (pour `main`)

### Activation GitHub Pages

- [ ] GitHub Pages activé dans Settings
- [ ] Source : `Branch: main` OU `/docs`
- [ ] CNAME configuré (si domaine personnalisé)
- [ ] URL générée : `https://zidtalel.github.io/qa-prompt-masterclass/`
- [ ] SSL automatique validé (cadenas vert)

### Upload des Fichiers

- [ ] Tous les fichiers `.html` uploadés dans `/docs`
- [ ] Tous les fichiers `.css` dans `/docs/assets/css/`
- [ ] Tous les fichiers `.js` dans `/docs/assets/js/`
- [ ] Tous les images dans `/docs/assets/img/`
- [ ] Fichiers markdown uploadés (ou convertis en HTML)
- [ ] Exercice templates uploadés dans `/docs/exercices/`

### Build & Publication

- [ ] Git commit : `git add .`
- [ ] Git commit message descriptif
- [ ] Git push : `git push origin main`
- [ ] Attendre 2-3 min pour build GitHub Pages
- [ ] Vérifier URL est accessible

---

## Phase Test Pré-Formation (J+1 à J+3)

### Tests Fonctionnels - Desktop

#### Tests Navigation
- [ ] Page d'accueil charge correctement
- [ ] Menu de navigation visible et fonctionnel
- [ ] Tous les liens internes fonctionnent (pas de 404)
- [ ] Lien vers section 1 : OK
- [ ] Lien vers section 2 : OK
- [ ] Lien vers section 3 : OK
- [ ] Lien vers section 4 : OK
- [ ] Retour au home depuis chaque section : OK
- [ ] Footer : liens sociaux + GitHub repo : OK

#### Tests Contenu
- [ ] Tous les textes affichés correctement (sans caractères cassés)
- [ ] Tous les prompts affichés avec syntax highlighting
- [ ] Tous les fichiers téléchargeables : OK
- [ ] Bouton "Copier" sur les prompts : OK
- [ ] Liens vers GitHub pour cloner : OK
- [ ] Vidéos (si embed) : player visible + playable

#### Tests Exercices
- [ ] Fichiers template accessibles depuis liens
- [ ] Fichiers solutions accessibles pour animateur
- [ ] Énoncés exercice clairs et complets
- [ ] Points de validation listés
- [ ] Durées estimées visibles

### Tests Responsivité Mobile

- [ ] Tester sur breakpoints : 320px, 768px, 1024px, 1440px
- [ ] Navigation adapte sur mobile (menu burger ?)
- [ ] Texte readable sans scroll horizontal
- [ ] Boutons cliquables (taille >= 44px)
- [ ] Images scale correctement
- [ ] Pas de texte cassé ou overflow

### Tests Performance

- [ ] Lighthouse Score >= 85 (performance + accessibility)
- [ ] Temps de chargement page d'accueil < 2s
- [ ] Temps de chargement section pages < 3s
- [ ] Images optimisées (<100KB)
- [ ] CSS/JS minifiés (si besoin)
- [ ] Pas d'erreurs console (F12)

### Tests Accessibilité

- [ ] Contraste texte/fond >= 4.5:1 (WCAG AA)
- [ ] Tous les images ont alt text
- [ ] Tous les liens ont label descriptif
- [ ] Navigabilité au clavier : TAB working
- [ ] Pas de flash/animation excessive

### Tests Compatibilité Navigateurs

- [ ] Chrome (dernière version) : OK
- [ ] Firefox (dernière version) : OK
- [ ] Safari (Mac) : OK
- [ ] Edge (si applicable) : OK
- [ ] Pas d'erreurs JavaScript

---

## Phase Pré-Formation (J-2 jours)

### Communication Participants

- [ ] Email envoyé aux participants avec :
  - [ ] URL formation : `https://zidtalel.github.io/qa-prompt-masterclass/`
  - [ ] Checklist prérequis
  - [ ] Guide setup local (clone, npm install)
  - [ ] Support contact (email, Teams)
  - [ ] Horaires formation

### Préparation Animateur

- [ ] Tous les fichiers d'exercices imprimés ou sur second écran
- [ ] Solutions préparées et testées
- [ ] Démos enregistrées (fallback pour live)
- [ ] Durées formation validées (3h30-4h)
- [ ] Transitions entre sections préparées
- [ ] Pause identifiée (après section II ou III)

### Validation Technique Finale

- [ ] Vérifier GitHub Pages toujours accessible
- [ ] Tester tous les liens externes (Firebase, CodePen, etc.)
- [ ] Vérifier les démos vidéo playable
- [ ] Tester les sandbox (CodePen/Replit)
- [ ] Vérifier accès aux ressources externes (docs Cypress, etc.)

### Validation Setup Participants

- [ ] Tester qu'on peut cloner le dépôt sans erreurs
- [ ] Vérifier npm install fonctionne
- [ ] Tester Cypress launch : `npx cypress open`
- [ ] Vérifier GitHub Copilot suggestions working
- [ ] Tester accès Jira/Xray (comptes de test)

---

## Jour de Formation (J)

### 30 min Avant

- [ ] Tous les participants connectés à WiFi
- [ ] Site formation chargé chez animateur
- [ ] Projector/écran testé et focalisé
- [ ] Audio testé (micro, haut-parleurs)
- [ ] GitHub Copilot ready (authentifié)
- [ ] Démos locales (VS Code, Cypress) ready
- [ ] Backup: vidéos démos sur disque local
- [ ] Chat/Teams open pour support

### Démarrage Formation

- [ ] Diapo de bienvenue affichée
- [ ] Tous les participants ont URL
- [ ] Brève intro (5 min)
- [ ] Vérifier tous les outils fonctionnent (test rapide)
- [ ] Q&A avant de commencer

### Pendant Formation

- [ ] Monitor exercices (partage écran participants)
- [ ] Support temps réel si blocage
- [ ] Durée par section respectée
- [ ] Pause à mi-parcours
- [ ] Feedback continu

### Après Formation

- [ ] Questionnaire satisfation collecté
- [ ] Fichiers exercices des participants sauvegardés
- [ ] Thank you message envoyé
- [ ] Ressources post-formation partagées
- [ ] GitHub access maintenu 30 jours (au minimum)

---

## Post-Formation (J+7)

### Collecte de Feedback

- [ ] Analyser questionnaire satisfaction
- [ ] Collecter issues GitHub (si participants reportent)
- [ ] Identier améliorations pour prochaine session

### Maintenance

- [ ] Archive les données participant (RGPD compliant)
- [ ] Mettre à jour les ressources externes cassées
- [ ] Documenter lessons learned
- [ ] Valider que site reste accessible

---

## Checklist Sécurité & Conformité

### Sécurité

- [ ] Pas de données sensibles dans les exemples
- [ ] IBANs/BICs utilisés : fictifs mais format valide
- [ ] Numéros cartes : format valide uniquement (pas vrai)
- [ ] Pas de credentials dans les fichiers (`.env` non commité)
- [ ] HTTPS activé sur GitHub Pages (cadenas vert)

### RGPD & Données

- [ ] Participation volontaire documentée
- [ ] Données participant traitées conformément RGPD
- [ ] Droit d'oubli respecté (suppression après formation)
- [ ] Pas de cookies tracking (sauf essentiels)

---

## Livrables de Fin

### Pour les Participants

- [ ] ✓ Site formation accessible 24/7
- [ ] ✓ Tous les exercices + solutions téléchargeables
- [ ] ✓ Tous les prompts "copy-paste" ready
- [ ] ✓ Tous les templates (Cypress, TestComplete, Xray)
- [ ] ✓ Contexte métier (glossaire, exemples, standards)
- [ ] ✓ GitHub repo cloneable (pour continuer)

### Pour l'Équipe

- [ ] ✓ Documentation complète (INSTRUCTIONS.md + PRD.md)
- [ ] ✓ Timeline + ressources (pour la prochaine session)
- [ ] ✓ Feedback analysis + améliorations
- [ ] ✓ Recordings (si applicable)

---

## Critères de Succès - Formation

| Critère | Cible | Réel |
|---------|-------|------|
| Accessibilité site | 100% | __% |
| Score satisfaction | 4/5 | __/5 |
| Exercices complétés | 80%+ | __% |
| Prompts utilisables générés | 1+ par participant | __ |
| Retour participants (email) | 50%+ | __% |

---

## Escalades & Contacts

| Problème | Contact | Fallback |
|----------|---------|----------|
| Site inaccessible | GitHub Support | Slack/Mattermost |
| Démo live échoue | Animateur | Vidéo pré-enregistrée |
| Participant sans Copilot | Support IT | Accès temporaire |
| Jira/Xray down | Admin Jira | Démo simulée en local |

---

## Post-Formation (Optionnel)

### Sessions de Suivi

- [ ] Webinaire "1 mois après" (optional)
- [ ] Partage des meilleurs prompts générés
- [ ] Updates si nouvelles versions Copilot/outils

### Evolution

- [ ] Collecter suggestions pour v2.0
- [ ] Ajouter cas d'usage IA plus avancés
- [ ] Intégrer retours utilisateurs

---

**Version** : 1.0 | **Date** : 16 Nov 2025 | **Statut** : Pré-déploiement
