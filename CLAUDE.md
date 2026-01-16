# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Working Principles

### 1. Realistic & Objective Thinking
- Avoid exaggeration; think and answer realistically and objectively
- Focus on facts and evidence-based reasoning

### 2. Step-by-Step Reasoning
- Always think step by step
- Break down the logic behind every answer
- Show the reasoning process clearly

### 3. Honesty About Uncertainty
- If the context is unclear → explicitly state it and ask clarifying questions
- If you do not know the answer → admit it instead of guessing or making up information
- Never fabricate information

### 4. Critical Perspective
- Critique user's assumptions and point out potential risks
- Self-critique: check your own answer for potential biases or logical fallacies before responding
- Challenge ideas constructively

## Project Overview

Academic portfolio website for **Ju O Kim**, hosted on GitHub Pages. Features:
- 3 SCI publication pages with detailed figures
- 7 AI/ML project showcases with 5 images each (35 total)
- Research focus: signal processing, sensor fusion, deep learning, XAI

Originally forked from Jon Barron's template, fully customized.

## Architecture

Pure static site with no build process:
- **Frontend**: HTML5 with inline CSS and vanilla JavaScript
- **Hosting**: GitHub Pages (master branch auto-deploys)
- **No dependencies**: No package.json, no build tools, no frameworks
- **Project pages**: Bootstrap 3.3.5 with custom CSS

## File Structure

```
/
├── index.html              # Main portfolio page
├── stylesheet.css          # Global styles (Lato font)
├── CLAUDE.md               # This file
├── README.md               # Repository readme
├── CNAME                   # GitHub Pages domain
│
├── images/                 # All visual assets (~285 files)
│   ├── KimJuO.jpg          # Profile photo
│   ├── favicon/            # Favicon assets
│   ├── [publication]_*.jpg # Publication thumbnails
│   ├── [project]_*.jpg     # Project thumbnails (7)
│   └── [Project]_[1-5].png # Project detail images (35)
│
├── data/                   # BibTeX files and CV
│   ├── Kim*.bib            # Publication citations
│   └── CV_JuO_Kim.pdf      # Curriculum Vitae
│
├── electronics2025/        # SCI Publication #1
├── sensors2020/            # SCI Publication #2
├── springer2024/           # SCI Publication #3
│
└── projects/               # 7 AI/ML Project Pages
    ├── visionforge/        # PCB Defect Detection
    ├── apex-ml/            # AutoML Pipeline
    ├── nerf-factory/       # Neural Radiance Fields
    ├── avs/                # Acoustic Vision System
    ├── its-xai/            # Explainable AI for ITS
    ├── digital-twin/       # Factory Digital Twin
    └── thn-scheduler/      # Production Scheduling
```

## Project Pages Structure

Each project in `projects/` follows this structure:
```
projects/{project-name}/
├── index.html              # Project page content
├── css/
│   ├── app.css             # Custom styles
│   └── bootstrap.min.css   # Bootstrap framework
├── img/
│   └── paper_icon.png      # Icon asset
└── images/                 # Project-specific images
```

### 7 Projects Overview

| Project | Focus | Key Technologies |
|---------|-------|------------------|
| **VisionForge** | PCB Defect Detection | YOLOv8, OpenCV |
| **APEX-ML** | AutoML Pipeline | Optuna, XGBoost, Ensemble |
| **NeRF Factory** | 3D Reconstruction | Instant-NGP, COLMAP |
| **AVS** | Sound Localization | AST, Beamforming |
| **ITS-XAI** | Traffic Prediction | SHAP, LIME, XGBoost |
| **Digital Twin** | Factory Simulation | FastAPI, SimPy, React |
| **THN Scheduler** | Production Scheduling | ALNS, Gantt Charts |

## Image Naming Convention

### Thumbnails (main index.html)
- `images/visionforge.jpg`, `apex_ml.jpg`, `nerf_factory.jpg`, etc.

### Project Detail Images (35 total)
- Pattern: `images/{Project}_{1-5}.png`
- Examples:
  - `Vision_Forge_1.png` through `Vision_Forge_5.png`
  - `APEX_1.png` through `APEX_5.png`
  - `Nerf_1.png` through `Nerf_5.png`

## Publication Entry Pattern

Each paper in `index.html` follows a two-column table row:

**Left cell (20%)**: Interactive hover teaser
```html
<div class="one">
  <div class="two" id='UNIQUEID_image'>
    <img src='images/overlay.jpg' width=100%>
  </div>
  <img src='images/base.jpg' width=100%>
</div>
```

**Right cell (80%)**: Publication metadata
- Title with `class="papertitle"`
- Authors with `<strong>` for Ju O Kim
- Journal/conference, year
- Links: project page, paper, bibtex

## JavaScript Hover Effect

```javascript
function UNIQUEID_start() {
  document.getElementById('UNIQUEID_image').style.opacity = "1";
}
function UNIQUEID_stop() {
  document.getElementById('UNIQUEID_image').style.opacity = "0";
}
UNIQUEID_stop()
```

## Testing & Deployment

- **Test**: Open `index.html` in browser (no server required)
- **Deploy**: Push to `master` branch (GitHub Pages auto-deploys)

## Common Tasks

### Adding a Publication
1. Add images to `images/` (base + overlay for hover)
2. Add BibTeX to `data/Kim{JOURNAL}{YEAR}.bib`
3. Insert `<tr>` at top of publications table
4. Create project page folder if needed

### Adding a Project
1. Copy structure from `projects/visionforge/`
2. Add 5 detail images: `images/{Project}_1.png` to `_5.png`
3. Add thumbnail: `images/{project}.jpg`
4. Update `projects/{name}/index.html`
5. Add entry to main `index.html` Projects section

### Updating Project Images
1. Replace images in `images/` folder
2. Clear browser cache to see changes
3. Verify paths in project `index.html` (use `../../images/`)
