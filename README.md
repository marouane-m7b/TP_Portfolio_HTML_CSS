# 📁 README — Portfolio Marouane Mahboub

| | |
|---|---|
| **Module** | Technologies Web et Web Sémantique |
| **Formation** | Master SDIA |
| **Professeure** | Mme Oumayma AGHERAI |
| **Mini Projet** | N°1 — Création d'un portfolio Web (HTML + CSS) |
| **Étudiant** | Marouane Mahboub |

---

> Documentation technique du code HTML/CSS du portfolio personnel.

---

## 📂 Structure des fichiers

```
portfolio/
├── index.html       → Structure et contenu de la page
├── style.css        → Mise en forme et design
└── assets/          → Images du projet
```

---

## 🧱 index.html — Explication section par section

---

### `<head>` — En-tête du document

```html
<link rel="stylesheet" href="style.css">
<link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700&family=Rajdhani:wght@400;500;600;700&display=swap" rel="stylesheet">
```

- On importe **style.css** pour appliquer le design.
- On importe deux polices Google Fonts :
  - **Orbitron** → utilisée pour les titres (effet tech/futuriste)
  - **Rajdhani** → utilisée pour le corps du texte (lisible, moderne)

---

### `<header>` — Barre de navigation fixe

```html
<header>
    <nav class="container">
        <div class="logo">M7B</div>
        <ul class="nav-links">
            <li><a href="#home">Home</a></li>
            ...
        </ul>
    </nav>
</header>
```

- Le `<header>` est **fixe en haut** (`position: fixed` dans le CSS).
- La `<nav>` utilise **Flexbox** (`display: flex; justify-content: space-between`) pour placer le logo à gauche et les liens à droite.
- Les liens utilisent des **ancres** (`href="#section"`) pour naviguer dans la page sans rechargement.
- Un **backdrop-filter: blur(10px)** donne l'effet de verre dépoli sur la barre.

---

### `#home` — Section Hero (présentation principale)

```html
<section id="home" class="hero container">
    <div class="hero-content"> ... </div>
    <div class="hero-image"> ... </div>
</section>
```

- La section hero utilise **Flexbox** (`display: flex; align-items: center; justify-content: space-between`) pour mettre le texte à gauche et la photo à droite.
- `min-height: 100vh` → occupe toute la hauteur de l'écran.
- La photo est dans un `.img-wrapper` avec `border-radius: 50%` → forme **circulaire**, avec une bordure cyan et un `box-shadow` lumineux.
- Les deux boutons `.btn-primary` et `.btn-outline` sont dans un `div.hero-btns` en **Flexbox** avec `gap: 20px`.

---

### `#about` — Section À propos

```html
<section id="about" class="section bg-alt">
    <div class="about-text-center"> ... </div>
    <div class="stats-centered"> ... </div>
</section>
```

- `.about-text-center` est centré avec `text-align: center` et `margin: 0 auto`.
- `.stats-centered` utilise **Flexbox** (`display: flex; justify-content: center; flex-wrap: wrap; gap: 30px`) pour afficher les 4 chiffres clés côte à côte.
- Chaque `.stat-box` est une carte avec une bordure subtile qui s'anime au hover.

---

### `#skills` — Section Compétences

```html
<div class="skills-grid">
    <div class="skill-card"> ... </div>
    ...
</div>
```

- `.skills-grid` utilise **CSS Grid** (`display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr))`) → les cartes s'adaptent automatiquement à la largeur de l'écran.
- Chaque `.skill-card` a un effet `transform: translateY(-10px)` au hover pour donner l'impression de "soulèvement".

---

### `#projects` — Section Projets

```html
<div class="projects-grid">
    <article class="project-card"> ... </article>
    ...
</div>
```

- `.projects-grid` utilise également **CSS Grid** avec `minmax(320px, 1fr)`.
- Chaque `.project-card` est un `<article>` sémantique (bonne pratique HTML5).
- L'image occupe `width: 100%; height: 220px; object-fit: cover` → elle remplit l'espace sans se déformer.

---

### `#experience` — Section Parcours (Timeline)

```html
<div class="timeline">
    <div class="timeline-item"> ... </div>
    ...
</div>
```

- La timeline est créée avec un simple `border-left: 2px solid cyan` sur le conteneur `.timeline`.
- Chaque `.timeline-item` a un **pseudo-élément `::before`** qui dessine le **cercle** sur la ligne :
```css
.timeline-item::before {
    content: '';
    position: absolute;
    left: -41px;
    width: 20px;
    height: 20px;
    border-radius: 50%;
    background: var(--accent-primary);
}
```
- Aucune librairie externe — juste du CSS pur.

---

### `#awards` — Section Récompenses

```html
<div class="awards-grid">
    <div class="award-item"> ... </div>
    ...
</div>
```

- `.awards-grid` utilise **CSS Grid** avec `minmax(260px, 1fr)`.
- Chaque `.award-item` est centré avec `text-align: center` et un emoji comme icône visuelle.

---

### `#contact` — Section Contact

```html
<div class="contact-wrapper">
    <div class="contact-info"> ... </div>
    <form class="contact-form"> ... </form>
</div>
```

- `.contact-wrapper` utilise **Flexbox** (`display: flex; gap: 60px`) → les infos de contact à gauche, le formulaire à droite.
- Le formulaire a `display: flex; flex-direction: column; gap: 15px` → les champs sont empilés verticalement.
- Les inputs ont un fond foncé (`background: var(--bg-secondary)`) pour correspondre au thème sombre.

---

### `<footer>` — Pied de page

```html
<footer>
    <div class="container footer-content">
        <p>&copy; 2026 Marouane Mahboub. All rights reserved.</p>
        <div class="footer-socials">
            <a href="...">GitHub</a>
            <a href="...">LinkedIn</a>
            <a href="...">Instagram</a>
        </div>
    </div>
</footer>
```

- Le `<footer>` a un `border-top` pour le séparer visuellement du reste.
- `.footer-content` utilise **Flexbox** pour aligner le copyright et les liens sociaux côte à côte.
- `background-color: var(--bg-secondary)` → légèrement plus clair que le fond principal pour le distinguer.

---

## 🎨 style.css — Explication des choix CSS

---

### Variables CSS (`:root`)

```css
:root {
    --bg-primary: #0f172a;
    --bg-secondary: #1e293b;
    --accent-primary: #22d3ee;
    --accent-secondary: #0ea5e9;
    --text-primary: #f8fafc;
    --text-secondary: #94a3b8;
}
```

- Toutes les couleurs sont définies en **variables CSS** → facile à modifier globalement.
- Palette **dark theme** (bleu nuit + cyan).

---

### Typographie

```css
h1, h2, h3, .logo {
    font-family: 'Orbitron', sans-serif;
    text-transform: uppercase;
    letter-spacing: 2px;
}
```

- Les titres utilisent **Orbitron** avec `text-transform: uppercase` → identité visuelle tech.
- Le corps utilise **Rajdhani** → plus lisible pour les paragraphes.

---

### Système de Layout

| Technique | Où utilisé |
|-----------|------------|
| **Flexbox** | Header, Hero, Stats, Contact, Footer |
| **CSS Grid** | Skills, Projects, Awards |
| **Position absolute** | Points de la timeline, pseudo-éléments |

---

### Responsive Design

```css
@media (max-width: 992px) {
    .hero { flex-direction: column-reverse; }
}

@media (max-width: 768px) {
    .nav-links { display: none; }
}
```

- À `992px` → le Hero passe en **colonne** (photo en haut, texte en bas).
- À `768px` → la navigation est **masquée** (à améliorer avec un menu burger).
- Les grids passent en `1 colonne` grâce à `auto-fit` et `minmax`.

---

### Effets visuels

- **Hover** : `transform: translateY(-5px / -10px)` sur les cartes → effet flottant.
- **Transitions** : `transition: all 0.3s ease` → animation douce sur tous les éléments.
- **Glow** : `box-shadow: 0 0 30px rgba(34, 211, 238, 0.3)` sur la photo de profil.
- **Glassmorphism** : `backdrop-filter: blur(10px)` sur le header.

---

*README rédigé pour le portfolio de Marouane Mahboub — 2026*
