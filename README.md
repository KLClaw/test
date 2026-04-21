# 🚀 Web App Hub

A lightweight, highly scalable collection of client-side micro-applications hosted via GitHub Pages. This repository serves as a central dashboard (Hub) that dynamically loads and displays various specialized tools within a single, unified interface.

## 🏗️ Architecture Overview

The project follows a "Manifest-Driven" architecture. This allows the main Hub to remain lightweight while supporting an unlimited number of independent applications.

*   **The Hub (`index.html`)**: The central entry point. It fetches the `apps.json` manifest and dynamically generates a dashboard of application cards.
*   **The Manifest (`apps.json`)**: A single source of truth that contains the metadata (name, icon, description, and path) for every app in the ecosystem.
*   **The Apps (`/app-name/index.html`)**: Each application lives in its own isolated directory, containing its unique logic and assets.
*   **Global Design System (`styles.css`)**: A shared stylesheet that ensures visual consistency (typography, cards, buttons, and layouts) across all applications in the Hub.

## 🛠️ Tech Stack

All applications are built to be **100% client-side**, making them incredibly fast, private, and easy to deploy:
*   **Frontend**: HTML5, CSS3, and Vanilla JavaScript.
*   **Deployment**: GitHub Pages.
*   **Dependencies**: Minimal; most apps use lightweight CDNs (e._g., `pdf-lib` for PDF manipulation).

## 📂 Repository Structure

```text
.
├── index.html          # The main Web App Hub dashboard
├── apps.json           # The manifest containing all registered apps
├── styles.css          # Global design system and shared components
├── nric-validator/     # Application: Singapore NRIC/FIN Checker
│   └── index.html      # App logic and UI
└── pdf-merger/         # Application: Client-side PDF Merger
    └── index.html      # App logic and UI
```

---
*Maintained as a personal collection of specialized web tools.*
