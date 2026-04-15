# 🌿 Lawn Tracker 2026

A personal lawn care tracker for Kunal's 2026 season — built as a single-file React app, no install required.

**Live App:** [https://kunal7911.github.io/lawn-care/](https://kunal7911.github.io/lawn-care/)

---

## Features
- 16-step 2026 lawn care plan (Tall Fescue, Zone 7b, Concord NC)
- Mow log with deck height tracking
- Products list with costs and seasonal filters
- Disease guide (Brown Patch, Gray Leaf Spot, Pythium Blight, Dollar Spot)
- Mesotrione calculator and temperature guide
- GitHub Gist sync for cross-device data (phone ↔ Mac)

## Tech Stack
- React 18.2.0 (CDN, no build step)
- Browser localStorage + GitHub Gist API for sync
- Hosted on GitHub Pages

## Sync Setup
To sync data across devices, go to the **Tools tab → GitHub Sync** and enter a GitHub Personal Access Token with `gist` scope only.
