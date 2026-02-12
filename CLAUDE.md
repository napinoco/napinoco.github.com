# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a personal academic website for Naoki Ito, built using MkDocs to generate static HTML from Markdown content. The site showcases academic achievements, publications, and career information in both English and Japanese.

## Repository Structure

```
├── .github/
│   └── workflows/
│       ├── deploy-src.yml    # Production deployment workflow
│       └── pr-preview.yml    # PR preview deployment workflow
├── docs/                     # Source markdown files
│   ├── index.md             # Main CV page (English)
│   ├── achievement-ja.md    # Japanese achievements page
│   ├── custom.css          # Custom styling
│   └── papers/             # Research papers directory
├── site/                    # Generated HTML output (MkDocs build)
├── mkdocs.yml              # MkDocs configuration
└── readme.txt              # Deployment notes
```

## Branch Structure

- **src**: Main development branch (source code)
- **master**: Production deployment branch (generated HTML)

## Development Commands

### Prerequisites
- Python 3.x
- MkDocs (install with `pip install mkdocs`)

### Common Commands
- **Build site**: `mkdocs build`
- **Serve locally**: `mkdocs serve` (accessible at http://127.0.0.1:8000)
- **Deploy to GitHub Pages**: `mkdocs gh-deploy --remote-branch master`

### Content Management
- Main content files are in `docs/` directory
- Edit `docs/index.md` for the main CV/homepage
- Edit `docs/achievement-ja.md` for Japanese content
- Custom CSS is in `docs/custom.css`

## Deployment Workflow

### Production Deployment (Automated)
The site automatically deploys to GitHub Pages via GitHub Actions:
- **Trigger**: Push to `src` branch or merged PR
- **Workflow**: `.github/workflows/deploy-src.yml`
- **Target**: `master` branch
- **URL**: https://napinoco.github.io/napinoco.github.com/

### PR Preview Build (Automated)
Pull requests to the `src` branch automatically build preview sites:
- **Trigger**: PR opened or updated
- **Workflow**: `.github/workflows/pr-preview.yml`
- **Output**: GitHub Actions Artifact (zip file)
- **Access**: Download from Actions tab → Workflow run → Artifacts section
- **Usage**: Extract zip and open `index.html` in browser
- **Retention**: Artifacts are kept for 30 days

### Manual Deployment (Legacy)
Based on readme.txt, manual deployment can still be done:
1. Making content changes in `docs/` directory
2. Running `mkdocs gh-deploy --remote-branch master` to deploy to GitHub Pages
3. The `site/` directory contains the generated output but should not be manually edited

## Configuration Notes

- Site uses the default MkDocs theme
- Pages are defined in `mkdocs.yml` with two main sections: CV (index.md) and "In Japan" (achievement-ja.md)
- Custom CSS is loaded via the `extra_css` configuration
- Site name is set to "Naoki Ito"

## Content Architecture

The website follows a bilingual structure:
- **English content** (index.md): Full academic CV with employment, education, publications, talks, and awards
- **Japanese content** (achievement-ja.md): Focused on domestic research activities, presentations, and awards in Japan
- Both pages cross-reference each other for comprehensive information

## Important Notes

- This is a static documentation site - no backend or database
- All content changes should be made in the `docs/` directory markdown files
- The `site/` directory is auto-generated and should not be edited directly
- Deployment targets the `master` branch for GitHub Pages hosting