# Kismet OS Rollout - Template

A beautiful, modern single-page site template with glass morphism design, animations, and interactive elements.

## 🚀 Quick Start

### Option 1: Use as GitHub Template

1. Click **"Use this template"** on GitHub (or fork the repository)
2. Clone your new repository
3. Add your assets to `/assets/` folder
4. Customize `index.html` with your content
5. Push to GitHub and enable Pages

### Option 2: Clone & Customize

```bash
git clone https://github.com/YOUR_USERNAME/kismet-template.git
cd kismet-template
# Add your assets to /assets/
# Customize index.html
git add -A
git commit -m "Initial customization"
git push
```

## 📁 Structure

```
gp/
├── index.html          # Main site file
├── assets/
│   ├── logo.webp       # Your logo
│   ├── overview.mp4     # Optional video overview
│   └── [other assets]  # Images, icons, etc.
├── README.md           # This file
└── AGENTS.md           # Design guidelines
```

## 🎨 Customization

1. **Logo**: Replace `assets/logo.webp` with your logo
2. **Colors**: Edit CSS variables in `index.html` (search for `:root`)
3. **Content**: Update text, prompts, and sections in `index.html`
4. **Video**: Add `assets/overview.mp4` for the minimal video player

## 🌐 Deploy

### GitHub Pages

1. Go to repository **Settings** → **Pages**
2. Source: **Deploy from a branch**
3. Branch: `main` / `root`
4. Your site will be live at: `https://YOUR_USERNAME.github.io/REPO_NAME/`

### Manual Setup

```bash
git remote add origin git@github.com:USER/REPO.git
git push -u origin main
```

## 📚 Documentation

See `AGENTS.md` for detailed design guidelines and best practices.

## ✨ Features

- 🎭 Glass morphism design
- ✨ Smooth animations & transitions
- 📱 Fully responsive
- 🎥 Minimal video/audio player
- 📋 Interactive prompt vault
- 🎨 Customizable color scheme
