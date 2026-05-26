# Security Policy

## Privacy Architecture

Latrel Private Architecture Visualizer is built on a single principle: **your infrastructure blueprint belongs to you.**

- **No backend** — there is no server. Your JSON schema and network architecture are never transmitted anywhere.
- **`localStorage` only** — your layout, node positions and color preferences are saved locally in your own browser.
- **Client-side rendering** — everything is processed directly on your machine using Cytoscape.js. 

**Transparency Note on External Requests:**
Unlike fully air-gapped tools, this visualizer *does* make initial GET requests to fetch its open-source libraries from public CDNs (Cytoscape, Dagre, Phosphor Icons, Fontshare). However, **no user data, JSON payloads, or diagram metadata are ever sent in these requests.**

You can independently verify all of this:
1. Open `index.html` in a browser.
2. Open DevTools → Network tab.
3. Paste any complex JSON architecture.
4. Observe: zero outbound network requests after the initial page load.

---

## Reporting a Vulnerability

Open a GitHub issue labelled `security`. Please include:
- Description of the vulnerability
- Steps to reproduce
- Potential impact

## License

MIT (with UI Attribution) © 2026 [Latrel](https://latrel.ai)