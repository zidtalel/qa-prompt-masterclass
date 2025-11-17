# 📖 Structure du Contenu Public (GitHub Pages)

**IMPORTANT** : Ce fichier documente comment structurer le dossier `/docs` (contenu pour les participants).

> ⚠️ **Ce dossier reste dans `.preparation/`** pour traçabilité. Le vrai dossier `/docs` sera créé lors de la phase web design (J22-J26).

---

## Vue d'Ensemble de l'Architecture

```
/docs (racine - hébergée sur GitHub Pages)
├── index.html                   # Landing page + nav principale
├── README.md                    # Infos pour participants
├── style.css                    # CSS global
│
├── section-1/                   # Le Paysage IA (25 min)
│   ├── index.html              # Overview section
│   ├── slides.html             # Slides interactives
│   └── ressources.md           # Articles, liens externes
│
├── section-2/                   # Art du Prompting (90 min - NOYAU)
│   ├── index.html              # Overview + navigation modules
│   ├── module-1.html           # Fondamentaux
│   ├── module-2.html           # Génération Tests
│   ├── module-3.html           # Debugging
│   ├── module-4.html           # Techniques Avancées
│   └── exercices.md            # Liens tous les exercices
│
├── section-3/                   # Outillage QA (50 min)
│   ├── index.html              # Overview
│   ├── copilot-ide.html        # Module 3.1
│   ├── xray-jira.html          # Module 3.2
│   ├── testcomplete.html       # Module 3.3
│   ├── cypress.html            # Module 3.4
│   └── exercices.md            # Liens exercices
│
├── section-4/                   # Pouvoirs Avancés (30 min)
│   ├── index.html              # Overview
│   ├── analyse-impact.html     # Module 4.1
│   ├── documentation.html      # Module 4.2
│   ├── collaboration.html      # Module 4.3
│   ├── perspectives.html       # Module 4.4
│   └── ressources.md           # Veille, références
│
├── exercices/                   # Répertoire centralité des exercices
│   ├── section-2/
│   │   ├── 2-1-1-template.txt
│   │   ├── 2-1-1-solution.md
│   │   ├── 2-2-1-template.json
│   │   ├── 2-2-1-solution.json
│   │   ├── 2-2-2-template.js
│   │   ├── 2-2-2-solution.js
│   │   ├── 2-2-3-template.csv
│   │   ├── 2-2-3-solution.csv
│   │   ├── 2-3-1-broken-code.js
│   │   ├── 2-3-1-solution.md
│   │   ├── 2-4-1-chaining-template.md
│   │   └── 2-4-1-solution.md
│   ├── section-3/
│   │   ├── 3-1-1-template.js
│   │   ├── 3-1-1-solution.js
│   │   ├── 3-2-1-template.md
│   │   ├── 3-2-1-solution.json
│   │   ├── 3-3-1-template.tc
│   │   ├── 3-3-1-solution.tc
│   │   ├── 3-4-1-template.js
│   │   └── 3-4-1-solution.js
│   └── section-4/
│       ├── 4-1-1-template.md
│       ├── 4-1-1-solution.md
│       ├── 4-2-1-template.md
│       └── 4-2-1-solution.md
│
├── assets/
│   ├── css/
│   │   ├── style.css           # Styles globaux
│   │   ├── highlights.css      # Code syntax highlighting
│   │   └── responsive.css      # Mobile-first
│   ├── js/
│   │   ├── main.js            # Scripts globaux
│   │   ├── copy-to-clipboard.js # Bouton copier
│   │   └── analytics.js       # Optionnel: tracking
│   ├── img/
│   │   ├── logo.svg
│   │   ├── banner-section-1.jpg
│   │   ├── banner-section-2.jpg
│   │   ├── banner-section-3.jpg
│   │   ├── banner-section-4.jpg
│   │   ├── icons/
│   │   │   ├── copilot.svg
│   │   │   ├── cypress.svg
│   │   │   ├── testcomplete.svg
│   │   │   ├── jira.svg
│   │   │   └── xray.svg
│   │   └── demo-screenshots/
│   │       ├── copilot-demo-1.png
│   │       ├── cypress-demo-1.png
│   │       └── [etc]
│   └── video/
│       ├── demo-1-intro.mp4
│       ├── demo-2-prompting.mp4
│       ├── demo-3-copilot-ide.mp4
│       ├── demo-4-cypress.mp4
│       └── demo-5-xray.mp4
│
├── _config.yml                 # Configuration GitHub Pages
├── CNAME                       # Si domaine personnalisé
└── .nojekyll                   # Pour assets custom

```

---

## Détails par Section

### Section 1 : Paysage IA

**Fichier** : `section-1/index.html`

```html
<!-- Structure type -->
<section>
  <h1>Le Paysage de l'IA Générative en QA</h1>
  
  <!-- Durée, objectifs -->
  <div class="meta">
    <span>📍 25 minutes</span>
    <span>📊 Niveau: Débutant</span>
  </div>
  
  <!-- Contenu principal -->
  <article class="module">
    <h2>État de l'Art 2025</h2>
    <p>Modèles actuels... [contenu]</p>
    
    <!-- Démo vidéo -->
    <div class="demo">
      <video src="assets/video/demo-1-intro.mp4"></video>
    </div>
  </article>
  
  <!-- Navigation suivant -->
  <a href="section-2" class="btn-primary">Vers Section 2 →</a>
</section>
```

---

### Section 2 : Prompting (NOYAU)

**Fichier** : `section-2/module-1.html` (exemple Module 2.1)

```html
<div class="module module-2-1">
  <h1>Module 2.1 : Fondamentaux du Prompting</h1>
  
  <!-- Navigation modules -->
  <nav class="module-nav">
    <a href="module-1.html" class="active">2.1</a>
    <a href="module-2.html">2.2</a>
    <a href="module-3.html">2.3</a>
    <a href="module-4.html">2.4</a>
  </nav>
  
  <!-- Contenu -->
  <section class="content">
    <h2>1. Structure d'une Bonne Requête</h2>
    
    <!-- Prompt exemple -->
    <div class="prompt-box">
      <pre><code class="language-prompt">
Tu es un expert en QA financier...
[code du prompt]
      </code></pre>
      <button class="copy-btn">Copier</button>
    </div>
    
    <!-- Exercice -->
    <div class="exercise">
      <h3>✍️ Exercice 2.1.1 : Rédiger 3 versions d'un prompt</h3>
      <p>Task: Générer des cas de test pour un virement...</p>
      <a href="../exercices/section-2/2-1-1-template.txt" class="download">
        📥 Télécharger template
      </a>
      <details>
        <summary>Voir la solution</summary>
        <pre><code>[solution]</code></pre>
      </details>
    </div>
  </section>
  
  <!-- Navigation -->
  <nav class="nav-footer">
    <a href="index.html" class="btn-back">← Retour</a>
    <a href="module-2.html" class="btn-next">Suivant →</a>
  </nav>
</div>
```

---

### Section 3 : Outillage QA

**Fichier** : `section-3/cypress.html` (exemple Module 3.4)

```html
<div class="module module-3-4">
  <h1>Module 3.4 : Cypress + IA</h1>
  
  <!-- Démo live -->
  <div class="demo-live">
    <video src="assets/video/demo-4-cypress.mp4" controls></video>
    <p>Démo : Générer un Page Object Model avec Copilot</p>
  </div>
  
  <!-- Code exemple -->
  <section class="code-example">
    <h2>Template Cypress Optimisé</h2>
    <pre><code class="language-javascript">
describe('Payment - Page Object Model', () => {
  // [code]
})
    </code></pre>
    <button class="copy-btn">Copier</button>
  </section>
  
  <!-- Exercice -->
  <div class="exercise">
    <h3>✍️ Exercice 3.4.1 : Générer un POM</h3>
    <a href="../exercices/section-3/3-4-1-template.js">Fichier template</a>
  </div>
</div>
```

---

### Section 4 : Avancés

Structure similaire aux autres sections, avec focus sur perspectives et ressources futures.

---

## Fichiers Exercice - Convention de Nommage

**Pattern** : `[SECTION]-[MODULE]-[NUMERO]-[TYPE]`

Examples:
- `2-1-1-template.txt` → Section 2, Module 1, Exercice 1, Template
- `2-2-2-solution.js` → Section 2, Module 2, Exercice 2, Solution
- `3-4-1-broken-code.js` → Section 3, Module 4, Exercice 1, Code défaillant

---

## Ressources Statiques

### Images à Générer

- Banners pour chaque section (1920x400px)
- Icons pour outils (SVG, 64x64px)
- Screenshots des démos
- Logos (Copilot, Cypress, TestComplete, Jira/Xray)

### Vidéos à Enregistrer

| Démo | Durée | Contenu |
|------|-------|---------|
| demo-1-intro.mp4 | 2 min | Overview IA en QA |
| demo-2-prompting.mp4 | 3 min | Prompt basique vs optimisé |
| demo-3-copilot-ide.mp4 | 3 min | Copilot IDE en action |
| demo-4-cypress.mp4 | 4 min | Générer script Cypress |
| demo-5-xray.mp4 | 3 min | Générer cas test Xray |

---

## Configuration GitHub Pages

### Fichier `_config.yml`

```yaml
title: Formation QA & IA Générative
description: Du Prompting Avancé à l'Automatisation Intelligente
theme: jekyll-theme-minimal  # ou cayman, etc.
baseurl: /qa-prompt-masterclass
url: https://zidtalel.github.io
```

### Fichier `.nojekyll`

Créer fichier vide pour éviter processing Jekyll.

---

## CSS Global - Structure

**Fichier** : `assets/css/style.css`

```css
/* Variables */
:root {
  --primary: #0366d6;
  --secondary: #6f42c1;
  --success: #28a745;
  --danger: #dc3545;
  --font-main: 'Segoe UI', Tahoma, Geneva, Verdana;
  --spacing: 1rem;
}

/* Layout responsive */
@media (max-width: 768px) {
  .container { padding: 0.5rem; }
  h1 { font-size: 1.5rem; }
}

/* Composants exercices */
.exercise {
  background: #f6f8fa;
  border-left: 4px solid var(--primary);
  padding: var(--spacing);
}

/* Prompts */
.prompt-box {
  background: #0d1117;
  color: #c9d1d9;
  border-radius: 4px;
  position: relative;
}

.copy-btn {
  position: absolute;
  top: 8px;
  right: 8px;
}
```

---

## JavaScript - Fonctionnalités

### Copy to Clipboard

```javascript
// assets/js/copy-to-clipboard.js
document.querySelectorAll('.copy-btn').forEach(btn => {
  btn.addEventListener('click', function() {
    const code = this.previousElementSibling.textContent;
    navigator.clipboard.writeText(code).then(() => {
      this.textContent = '✓ Copié !';
      setTimeout(() => { this.textContent = 'Copier'; }, 2000);
    });
  });
});
```

---

## Checklist Contenu `/docs`

- [ ] Tous les HTML créés & validés
- [ ] CSS global appliqué & responsive
- [ ] Syntax highlighting (Highlight.js) intégré
- [ ] Tous les images optimisées (<100KB)
- [ ] Tous les vidéos (MP4, < 50MB chacun)
- [ ] Tous les liens fonctionnels (pas de 404)
- [ ] Navigation cohérente (breadcrumbs, footer)
- [ ] Mobile-first design testé
- [ ] Accessibilité WCAG AA validée
- [ ] Performance Lighthouse >= 85

---

**Version** : 1.0 | **Date** : 16 Nov 2025

