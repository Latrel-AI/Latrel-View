# Latrel Privacy-First Architecture Visualizer

> A local-first infrastructure visualizer. Map your cloud architecture using JSON with zero data leaving your machine.

![Version](https://img.shields.io/badge/version-1.1.0-blue) ![License](https://img.shields.io/badge/license-MIT%20(with%20Attribution)-green) ![No Backend](https://img.shields.io/badge/backend-none-brightgreen) ![Single File](https://img.shields.io/badge/deployment-single_file-brightgreen)


## Why This Exists

Most diagramming tools require manual drag-and-drop or send your proprietary architecture to their servers. We built this to let you define infrastructure as a simple JSON array and render it instantly in your browser. 

**No servers. No accounts. No telemetry.** Originally built as an internal tool for [Latrel.ai](https://latrel.ai), now open-sourced. 
> **Want to see our main product?** [Join the Latrel.ai Beta Waitlist](https://latrel.ai/beta).

## Features

- **JSON-as-Code:** Define nodes, databases, parent-clusters, and edges using a simple JSON array.
- **Smart Edge Routing:** Features a custom-built dynamic orthogonal (Taxi) routing engine that prevents overlapping and backward-piercing arrows.
- **Auto-Layout:** Instantly organize messy JSON into clean hierarchies using the integrated Dagre engine.
- **Robust Editor:** Full support for Undo/Redo, box-selection, and 24px Snap-to-Grid dragging.
- **Custom Painter:** Recolor individual nodes to map specific services to specific teams.
- **Export & Share:** Export your canvas to ultra-high-resolution PNGs, SVGs or save the coordinate-mapped JSON.
- **Offline Capable:** Everything is auto-saved to your browser's `localStorage`.


## Privacy Guarantee

Everything stays locally in your browser. Your architecture JSON is never sent to a backend, logged, or visible to Latrel. (Note: The app fetches open-source rendering libraries from public CDNs on load, but no user data is attached).


## Known Limitations

- Taxi Routing Fallbacks: Looping edges and parent-connected edges automatically revert to Bezier curves to avoid canvas engine rendering bugs.

- Hierarchy Scale Caps: Bounding box constraints in the ELK engine may cause child nodes to overflow parent boxes if structures are nested deeper than 3 levels.

- Dagre Sprawl on Compounds: The Dagre layout is optimized for flat paths and can cause layout sprawl or intersecting lines when handling complex compound nodes.

- Single-Threaded Processing: All layout calculations run completely client-side, which will temporarily freeze the browser UI thread on massive datasets (500+ items).

- Strict Schema Reliance: The validation loop enforces hard node checks; a single missing or mistyped node ID reference will completely halt canvas execution.

## Issues Fixed

- Custom Arrow & Routing Mechanics: Resolved critical directional orthogonal Taxi routing calculations and secured custom Bezier fallback overrides for complex paths.

- Text Overflow Visual Bugs: Eliminated text container overflow issues within nodes.

- Dynamic Node Gap Implementation: Added automatic layout spacing calculations based on edge label lengths to prevent text overlaps between layers.

- Detached UI & Layout Pipelines: Extracted the core dark/light interface toggle into a separate top-bar action button, removing interface themes from the diagram rendering configurations.

- Layout Engine Initialization: Cleaned script load order overhead and eliminated duplicate script inclusions that were accidentally wiping out the active elk layout definitions.


## About Latrel

[Latrel.ai](https://latrel.ai) is an AI-native analysis automation platform that transforms raw organizational data into structured, sovereign intelligence.

Traditional BI tools treat AI as an added capability. Latrel is built around it — designed from the ground up so the AI functions as the tenant's dedicated data analyst, while the user retains full governance over data, logic, and context.

The platform delivers Analytical Latitude by decoupling complex reasoning from pay-per-thought constraints, enabling deep-dive investigations at scale. Its local-first hybrid architecture keeps core logic and organizational metadata private, persistent, and entirely under the user's control — independent of third-party uptime, pricing, or data policies.


## Contributing & Forking

Issues and PRs are welcome. Please ensure any new features do not require a build step (keep it plain HTML/CSS/JS).

> **Note on Forking:** This project uses a custom MIT license that requires UI Attribution. If you fork and host this tool, you must keep the "Powered by Latrel" link visible in the user interface.


## License

MIT (with UI Attribution Requirement) © 2026 [Latrel.ai](https://latrel.ai)