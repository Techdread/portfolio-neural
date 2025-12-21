# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Neural Pathways is an educational portfolio showcasing interactive Three.js visualizations of neural network mathematics and ML/AI concepts. The project teaches linear algebra, calculus, and deep learning fundamentals through visual, interactive demonstrations.

## Development Setup

This is a static site with no build system. Use any local HTTP server to develop:
- VS Code Live Server (configured on port 5501 in `.vscode/settings.json`)
- `npx serve public` or `python -m http.server 8000` from the `public/` directory

## Project Structure

```
portfolio-neural/
├── public/                    # Static site root (deploy this folder)
│   ├── index.html            # Landing page with curriculum grid
│   ├── css/style.css         # Global styles with neural color palette
│   ├── topics/               # Educational content pages (42 topics)
│   │   └── {id}-{topic}.html # e.g., a1-vector-operations.html
│   └── viz/                  # Standalone Three.js visualizations
│       ├── A*.html           # Linear Algebra (Category A)
│       ├── B*.html           # Calculus (Category B)
│       ├── C*.html           # Neural Network Operations (Category C)
│       ├── category-d/       # Optimization visualizations
│       └── category-e/       # Architecture visualizations
├── prompts/                  # LLM prompts for generating content
│   └── category-{a-i}*.md   # Prompts per category
├── PROGRESS.md              # Topic completion status tracker
└── threejs-neural-viz-portfolio-ideas.md  # Project spec & build order
```

## Architecture

**Two-layer content system:**
1. **Topic pages** (`public/topics/`) - Educational HTML pages with explanations, styled with Tailwind CSS
2. **Visualization pages** (`public/viz/`) - Standalone Three.js interactive demos, often embedded in topic pages via iframe

**Tech stack per visualization:**
- Three.js (CDN via import maps, typically v0.160+)
- Tailwind CSS (CDN)
- MathJax for mathematical notation
- No build step, no bundler - each HTML file is self-contained

## Naming Conventions

- Topic IDs follow pattern: `{Letter}{Number}` (e.g., A1, B3, C2)
- Categories: A=Linear Algebra, B=Calculus, C=Neural Ops, D=Optimization, E=Architecture, F=Training, G=Playgrounds, H=Advanced, I=Probability
- File naming: `{id}-{kebab-case-name}.html` in topics, `{ID}-{PascalCase-name}.html` in viz

## CSS Variables (from style.css)

Key color tokens for consistent theming:
- `--neural-primary: #6366f1` (indigo)
- `--synapse-active: #22d3ee` (cyan)
- Category colors: `--cat-a` through `--cat-i` for color-coding modules

## When Creating New Visualizations

1. Each visualization is a self-contained HTML file using ES modules
2. Import Three.js via import map:
   ```html
   <script type="importmap">
   { "imports": { "three": "https://cdn.jsdelivr.net/npm/three@0.160.0/build/three.module.js", "three/addons/": "https://cdn.jsdelivr.net/npm/three@0.160.0/examples/jsm/" } }
   </script>
   ```
3. Use OrbitControls for camera interaction
4. Target 60fps, use dark background (#111827 or similar)
5. Include responsive handling for window resize
6. Use CSS2DRenderer for in-scene labels when needed

## Prompts for Content Generation

The `prompts/` folder contains structured LLM prompts for generating:
- Educational explanations (1500-2000 words per topic)
- Three.js visualization code (production quality)

When generating new content, reference these prompts for consistent quality and format.
