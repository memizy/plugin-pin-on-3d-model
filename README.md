<div align="center">

# 🧊 3D Pin-on-Model Viewer
**Official Memizy Plugin for Interactive 3D Questions**

![Version](https://img.shields.io/badge/Plugin-v1.0.0-blue?style=for-the-badge)
![Tech Stack](https://img.shields.io/badge/Three.js-WebGL-black?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-success?style=for-the-badge)

<br>

A generic, high-performance 3D viewer plugin for the [Memizy Ecosystem](https://github.com/memizy/memizy). It dynamically loads any 3D model (`.glb` / `.gltf`) and allows users to interactively answer questions by finding and clicking on specific 3D meshes.

</div>

---

## 💡 What it does

Instead of traditional text-based multiple-choice questions, this plugin handles the OQSE **`pin-on-model`** item type. 

It receives a question and a 3D model asset from the Memizy host application. The user must then orbit the 3D camera, find the correct part of the model (e.g., a specific bone, a car engine part, or a geographical region on a globe), and click on it.



### Supported Use Cases:
* 🦴 **Medicine & Anatomy:** Identifying bones, organs, and muscles.
* ⚙️ **Engineering:** Finding specific components in a complex CAD assembly.
* 🌍 **Geography:** Selecting countries or regions on a 3D globe.

---

## 🧩 OQSE Integration

This plugin declares the following capabilities in its `oqse-manifest.json`:
* **Types supported:** `pin-on-model`
* **Actions:** `render`

### How it works under the hood:
1. The Memizy app sends the `pin-on-model` item data via the `window.postMessage` SDK.
2. The plugin reads the `targetAsset` field and dynamically loads the `.glb` file.
3. It sets up a `THREE.Raycaster` to detect user clicks.
4. It compares the clicked mesh's name with the `targetName` defined in the item's `hotspots` array.
5. It returns the score (1.0 for correct, 0.0 for incorrect) back to the host app.

---

## 🛠️ Development Setup

This plugin is built as an independent Vue 3 / Vite application using `three.js`.

```bash
# 1. Install dependencies
npm install

# 2. Run the development server
npm run dev

```

### Architecture

* Uses the **Base URL + Manifest** architecture.
* Build the project using `npm run build` to generate the `dist/` folder.
* Host the `dist/` folder on GitHub Pages or any static hosting service.

---

## ⚖️ License

Released under the [MIT License](https://www.google.com/search?q=LICENSE). Built with `three.js`.

<div align="center">
<i>Maintained with ❤️ by the Memizy Team.</i>
</div>
