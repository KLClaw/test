# 🧠 AI Agent Workspace Skills: Web App Hub

This document defines the core architecture, design patterns, security rules, and engineering checklists for any AI developer agent working in this repository. 

AI agents should read this file with `IsSkillFile: true` upon entering the workspace to align immediately with the existing systems, design rules, and constraints.

---

## 🏗️ Architecture & Stack Constraints

All applications in this workspace are **100% client-side micro-apps** hosted via GitHub Pages.

1. **Tech Stack Limits**:
   * **Core**: Strict HTML5, CSS3, and Vanilla JavaScript.
   * **No Bundlers / Compilers**: Absolutely no webpack, vite, typescript, or Node.js compilers should be set up inside directories unless explicitly requested. Everything must execute directly in a standard browser.
   * **Dependencies**: Keep them minimal. If external libraries are necessary (e.g., PDF manipulation), load them via reliable, secure CDNs (like `cdnjs` or `unpkg`).
2. **Folder Isolation**:
   * Each app resides in its own isolated subfolder (e.g., `/password-generator/`).
   * The app entry point must be `index.html` inside that directory.
   * Global styles should be inherited from the parent directory: `<link rel="stylesheet" href="../styles.css">`.
3. **The Hub Manifest**:
   * The file [apps.json](../apps.json) acts as the single source of truth registering all micro-applications.
   * When creating a new app, it must be appended to the JSON array in `apps.json` with appropriate metadata (`name`, `path`, `icon`, `description`).

---

## 🎨 Premium UI & Design Guidelines

Web applications in this hub must look premium, modern, and engaging. Avoid simple, generic, default designs.

* **Color Palette**: Utilize the HSL CSS variables defined in [styles.css](../styles.css) (e.g. `--primary-color`, `--bg-color`, etc.).
* **Typography**: Maintain consistent, modern, sans-serif layouts. Use monospaced fonts (`Courier New`, `monospace`) strictly for credentials or system outputs.
* **Responsive Layouts**: Design card containers (`.card`) to fit neatly on mobile screens and dynamically align on desktops.
* **Component Styling**:
  * **Sliders**: Never use default browser range sliders. Style the range track and webkit thumbs with interactive scale adjustments on hover.
  * **Checkboxes & Toggles**: Create card-like interactive grid boxes that highlight/glow when checked rather than presenting basic HTML checkboxes.
  * **Buttons**: Give interactive states to all buttons with subtle focus rings and transition-based micro-animations.
* **Copy Feedback**: Integrate responsive tooltips or toast bubbles (using CSS transitions) that appear when items are copied to the clipboard.

---

## 🔒 Security & Performance Best Practices

* **Cryptographic CSPRNG**:
  * For security-critical generators (e.g., passwords, pin codes, secure keys), **NEVER** use `Math.random()`.
  * **ALWAYS** use `window.crypto.getRandomValues(array)` for cryptographically secure pseudo-random number generation.
  * When drawing from mixed pools, implement secure Fisher-Yates array shuffles utilizing browser-native random bytes.
* **Privacy & State**:
  * Do not store highly secure secrets, generated passwords, or sensitive PII in `localStorage` or `sessionStorage` unless explicitly requested.
  * Clear memory references when fields are reset or updated.
* **Performance**:
  * Avoid heavy assets. Use CSS animations instead of large GIFs or videos.
  * If images are required, keep them lightweight and optimized.

---

## 📋 The App Creation Checklist

Follow this workflow whenever a user requests a new application:

- [ ] **Step 1: Manifest Registration**
  Append the app's metadata into [apps.json](../apps.json).
- [ ] **Step 2: Subfolder Structure**
  Create a self-contained folder `/new-app-name` at the root directory.
- [ ] **Step 3: Styling Scaffold**
  Link the shared stylesheet (`../styles.css`) and add a scoped `<style>` block in `index.html` for specialized layouts.
- [ ] **Step 4: CSPRNG Integrity**
  If the utility is cryptography or security-related, write strong validation checks and utilize the `window.crypto` API.
- [ ] **Step 5: Visual Excellence**
  Add micro-animations, synchronized controls, and hover-state overlays.
- [ ] **Step 6: User Walkthrough**
  Expose clear directions for manual verification and test parameters.
