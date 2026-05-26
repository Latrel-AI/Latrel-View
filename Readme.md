# Latrel Private Architecture Visualizer

> A privacy-first, JSON-driven infrastructure visualizer. Your architecture stays in your browser.

![Version](https://img.shields.io/badge/version-1.0.0-blue) ![License](https://img.shields.io/badge/license-MIT%20(with%20Attribution)-green) ![No Backend](https://img.shields.io/badge/backend-none-brightgreen) ![Single File](https://img.shields.io/badge/deployment-single_file-brightgreen)

---

## Why This Exists

Most diagramming tools require you to manually draw boxes, or worse, they force you to send your proprietary cloud architecture to a third-party server to be parsed.

Latrel's Architecture Visualizer solves both problems. You define your infrastructure as a simple JSON array, and the visualizer maps it instantly. **No servers. No accounts. No telemetry.** Your infrastructure blueprint never leaves your local machine.

This is part of how [Latrel.ai](https://latrel.ai) builds tools: **Productivity that doesn't compromise your data privacy.**

---

## Features

- **JSON-as-Code:** Define nodes, databases, parent-clusters, and edges using a simple JSON array.
- **Smart Edge Routing:** Features a custom-built dynamic orthogonal (Taxi) routing engine that prevents overlapping and backward-piercing arrows.
- **Auto-Layout:** Instantly organize messy JSON into clean hierarchies using the integrated Dagre engine.
- **Robust Editor:** Full support for Undo/Redo, box-selection, and 24px Snap-to-Grid dragging.
- **Custom Painter:** Recolor individual nodes to map specific services to specific teams.
- **Export & Share:** Export your canvas to ultra-high-resolution PNGs or save the coordinate-mapped JSON.
- **Offline Capable:** Everything is auto-saved to your browser's `localStorage`.

---

## Usage & Deployment

Because this is a Single-File Web App, deployment is frictionless:

1. Download or clone this repo.
2. Open `index.html` in any web browser.
3. Paste your JSON array into the sidebar.

**To host this for your team:**
Simply upload the `index.html` file to GitHub Pages, Vercel, Netlify, or an AWS S3 bucket. There is no `npm install`, no Webpack and no server required.

---

## JSON Syntax Guide

The engine reads a flat JSON array of Cytoscape.js-formatted objects.

### 1. Basic Nodes

Nodes require an `id`. You can optionally provide a `label`, a `color` and a `type`.

```json
{ 
  "data": { 
    "id": "api", 
    "label": "API Gateway", 
    "color": "#4f46e5" 
  } 
}
```

> **Tip:** Set `"type": "db"` to render the node as a database barrel shape.

### 2. Edges (Connections)

Edges require a `source` and `target` matching your node IDs.

```json
{ 
  "data": { 
    "source": "api", 
    "target": "db", 
    "label": "queries data",
    "dashed": true 
  } 
}
```

### 3. Compound Nodes (Groupings / Clusters)

To put nodes inside a larger bounding box (like a VPC or a Kubernetes Cluster), define the parent node, then assign the `parent` property to the child nodes.

```json
[
  { "data": { "id": "aws", "label": "AWS Cloud" } },
  { "data": { "id": "ec2", "label": "Web Server", "parent": "aws" } }
]
```

---

## Keyboard Controls & Shortcuts

| Action | Shortcut / Input |
|---|---|
| Box Select | `Ctrl + Click & Drag` |
| Add to Selection | `Ctrl + Click Node` |
| Select All | `Ctrl + A` |
| Undo | `Ctrl + Z` |
| Redo | `Ctrl + Y` (or `Ctrl + Shift + Z`) |
| Pan Canvas | `Click & Drag` empty space |
| Zoom | Scroll Wheel / Trackpad |

---

## Privacy Guarantee

| What happens to your architecture JSON | Answer |
|---|---|
| Sent to a backend server | ❌ Never |
| Stored in the cloud | ❌ Never |
| Logged or tracked | ❌ Never |
| Visible to Latrel | ❌ Never |
| Stays locally in your browser | ✅ Always |

> **Note:** The app fetches open-source rendering libraries (Cytoscape.js, Dagre, Phosphor Icons) from public CDNs on initial load, but zero user data or diagram metadata is attached to these requests.

---

## Known Limitations

- Compound (Parent) nodes and looping edges bypass the orthogonal "Taxi" routing and fall back to smooth Bezier curves to prevent rendering bugs in the Cytoscape engine.
- Highly nested compound nodes (more than 3 levels deep) may experience padding issues during Auto-Arrange.

---

## About Latrel

[Latrel.ai](https://latrel.ai) is an AI-native analysis automation platform that transforms raw organizational data into structured, sovereign intelligence.

Traditional BI tools treat AI as an added capability. Latrel is built around it — designed from the ground up so the AI functions as the tenant's dedicated data analyst, while the user retains full governance over data, logic, and context.

The platform delivers Analytical Latitude by decoupling complex reasoning from pay-per-thought constraints, enabling deep-dive investigations at scale. Its local-first hybrid architecture keeps core logic and organizational metadata private, persistent, and entirely under the user's control — independent of third-party uptime, pricing, or data policies.

---

## Contributing & Forking

Issues and PRs are welcome. Please ensure any new features do not require a build step (keep it plain HTML/CSS/JS).

> **Note on Forking:** This project uses a custom MIT license that requires UI Attribution. If you fork and host this tool, you must keep the "Powered by Latrel" link visible in the user interface.

---

## License

MIT (with UI Attribution Requirement) © 2026 [Latrel.ai](https://latrel.ai)
