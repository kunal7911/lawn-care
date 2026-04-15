# Lawn Tracker 2026 — Project Memory

## Owner
- **Name:** Kunal
- **Email:** kunal7911@yahoo.com
- **GitHub:** kunal7911
- **App URL:** https://kunal7911.github.io/lawn-care/

---

## Purpose
Build and maintain a personal lawn care tracker web app for Kunal's 2026 lawn care season. The app replaces a static Excel spreadsheet with an interactive, mobile-friendly tracker that syncs across devices.

---

## Lawn Profile
- **Location:** Concord, NC
- **USDA Zone:** 7b
- **Grass Type:** Tall Fescue (cool-season)
- **Soil:** Red clay — acidic pH 5.5–6.2, compacts easily, poor drainage
- **Front Yard:** West-facing — yellows in cool spring due to afternoon sun on cold soil
- **Key Challenge:** Tall Fescue struggles in hot NC summers; Brown Patch fungus is the #1 risk

### Known Completed Steps (as of April 2026)
- ✅ Step 1 — Scotts Halts pre-emergent applied (Feb 19, 2026)
- ✅ Step 2 — Mesotrione (Tenacity) spot treatment (early March 2026)

---

## App Overview

### Tech Stack
- **Single file:** `index.html` — no build process, no dependencies to install
- **Framework:** React 18.2.0 via CDN (unpkg)
- **Transpiler:** Babel Standalone 7.23.10 via CDN
- **Styling:** CSS custom properties (no Tailwind)
- **Storage:** Browser localStorage (per-device)
- **Cloud Sync:** GitHub Gist REST API (cross-device sync)
- **Hosting:** GitHub Pages (free)

### File Location
- **Local:** `/Users/zylummac/Documents/Claudeprojects/Claudecode/lawn-care/index.html`
- **Git Remote:** `https://github.com/kunal7911/lawn-care.git`
- **Branch:** `main`

### localStorage Keys
| Key | Purpose |
|-----|---------|
| `lawnTasks26` | Array of 16 task objects with completion state |
| `mowLogs26` | Array of mow log entries |
| `lawnGhToken` | GitHub personal access token (Gist sync) |
| `lawnGistId` | ID of the synced Gist |
| `lawnLastSynced` | ISO timestamp of last successful sync |

---

## App Structure (6 → now 5 Tabs)

| Tab | Description |
|-----|-------------|
| **Home** | Dashboard — progress %, next task, days since last mow, overdue alerts |
| **Plan** | 16-step task list — tap to expand, check off when done |
| **Mow Log** | Log each mow with deck height, previous height, notes |
| **Products** | 12 products with cost, where to buy, seasonal filters |
| **Tools** | Mesotrione calculator, temp guide, disease guide, GitHub Gist sync setup |

> **Ask AI tab was intentionally removed** — Kunal already has a paid Claude subscription and doesn't want to pay separately for an API key.

---

## GitHub Gist Sync — How It Works
1. User enters a GitHub Personal Access Token (gist scope only) in Tools → ☁ GitHub Sync
2. On first connect, app scans user's Gists for an existing `lawn-tracker-data.json` file
3. If found → loads that Gist (correct behaviour for second device)
4. If not found → creates a new private Gist
5. Auto-saves to Gist 3 seconds after any change (debounced)
6. Sync status badge shown in every screen header

### Key Gist Functions
- `gistFindExisting(token)` — scans up to 200 Gists for existing lawn tracker file
- `gistCreate(token, data)` — creates new private Gist
- `gistRead(token, gistId)` — reads and validates data from Gist
- `gistUpdate(token, gistId, data)` — writes updated data to Gist

---

## Security Decisions
- **CSP meta tag** — restricts API calls to `api.github.com` only
- **CDN versions pinned** — React 18.2.0, Babel 7.23.10 (no auto-updates)
- **Token validation** — GitHub tokens validated by prefix (`ghp_`, `github_pat_`, etc.)
- **No API keys in source** — all keys stored in localStorage only, never in the HTML file
- **Public repo is safe** — the HTML file contains zero secrets
- **Anthropic API removed** — no Claude API calls in the app, CSP updated accordingly

---

## The 16-Step 2026 Lawn Plan

| Step | Window | Type | Task | Status |
|------|--------|------|------|--------|
| 1 | Feb 1–28 | Pre-Emergent | Scotts Halts crabgrass preventer | ✅ Done (Feb 19) |
| 2 | Mar 1–15 | Weed Control | Mesotrione spot spray | ✅ Done (Mar 2026) |
| 3 | Mar 15–Apr 15 | Mowing | Begin regular mowing at 3.5" | — |
| 4 | Apr 1–30 | Soil Test | Send soil samples (front + back) | — |
| 5 | Apr 15–30 | Fertilizer | **Light spring fertilizer — low nitrogen (Scotts Turf Builder, half rate). NO Weed & Feed.** | — |
| 6 | May 1–15 | Weed Control | Mesotrione second round if needed | — |
| 7 | May 15–Jun 1 | Mowing | Raise to 4.0" for summer | — |
| 8 | Jun 1–15 | Disease Prev | Apply Scotts DiseaseEx preventively | — |
| 9 | Jun–Aug | Mowing | Maintain 4.0", never remove more than 1/3 | — |
| 10 | Jul–Aug | Disease Watch | Monitor for Brown Patch (night temps >70°F + humidity) | — |
| 11 | Aug 15–Sep 1 | Prep | Scalp to 3.0" before aeration | — |
| 12 | Sep 1–15 | Aeration | Core aerate entire lawn | — |
| 13 | Sep 1–15 | Overseeding | Overseed with Tall Fescue blend | — |
| 14 | Sep 15–Oct | Fertilizer | Starter fertilizer after overseeding | — |
| 15 | Oct–Nov | Fertilizer | Fall fertilizer (higher nitrogen) | — |
| 16 | Nov–Dec | Winterizer | Apply winterizer fertilizer | — |

### Important Lawn Rules
- **Never use Weed & Feed on Tall Fescue** — pushes excessive growth before summer stress, herbicide can damage grass as temps rise. Use separate fertilizer + targeted Mesotrione spot spray instead.
- **1/3 mowing rule** — never cut more than 1/3 of blade height at once
- **Step 12 scalp height** — 3.0" (not 2.5") before aeration
- **Brown Patch trigger** — apply fungicide when night temps consistently exceed 70°F with high humidity, don't wait for visible symptoms
- **Mesotrione in September** — NO surfactant during overseeding window, it kills germinating seedlings

---

## Products List (12 items)
1. Scotts Halts Crabgrass Preventer — Step 1
2. Mesotrione (Tenacity) — Steps 2, 6
3. Surfactant — Steps 2, 6 (NOT Step 13)
4. Blue Dye marker — Steps 2, 6
5. **Scotts Turf Builder (plain, no weed control)** — Step 5 *(replaced Weed & Feed)*
6. Scotts DiseaseEx — Steps 8, 10
7. Core Aerator (rental) — Step 12
8. Tall Fescue Seed blend — Step 13
9. Starter Fertilizer — Step 14
10. Fall Fertilizer — Step 15
11. Winterizer — Step 16
12. Soil Test Kit — Step 4

---

## Design — iOS Lawn Journal Style
- **Theme:** Dark green + earthy tones
- **Font:** SF Pro / system font
- **Primary colors:** `--green-900: #0f2318` through `--green-300: #6dcf9a`
- **Earth tones:** `--earth: #7c5c3a`, `--tan: #c9a97a`, `--cream: #faf7f2`
- **Bottom nav:** iOS-style fixed bottom navigation, 5 tabs
- **Cards:** `border-radius: 16px`, subtle shadow
- **Sync badge:** Shown in header of every screen

---

## Disease Guide (in Tools tab)
Four diseases most relevant to Tall Fescue in Concord NC — each with SVG visual, triggers, symptoms, treatment, prevention, extension link:
1. **Brown Patch** (Rhizoctonia solani) — HIGH risk, Jun–Sep, night temps >70°F
2. **Gray Leaf Spot** — Moderate risk, Jul–Aug, very hot + humid
3. **Pythium Blight** — Moderate risk, Jul–Aug, waterlogged soil
4. **Dollar Spot** — Low-Moderate risk, May–Jun and Sep–Oct

---

## VS Code / Git Workflow
- Repo initialized at `/Users/zylummac/Documents/Claudeprojects/Claudecode/lawn-care`
- Remote: `https://github.com/kunal7911/lawn-care.git`
- Branch: `main`
- GitHub Pages serves `index.html` from root of `main` branch
- **First push:** Kunal needs to run from Terminal:
  ```bash
  cd ~/Documents/Claudeprojects/Claudecode/lawn-care
  rm .git/index.lock
  git add .
  git commit -m "Initial commit — Lawn Tracker 2026"
  git push -u origin main
  ```
  Use GitHub token (same one as Gist) as password when prompted.
- **After that:** VS Code Source Control panel → type message → Commit → Sync Changes

---

## Conversation History Summary
- Started from an Excel file ("Lawn Care Schedule Expansion.xlsx") generated by a prior chatbot
- Verified and corrected the 16-step plan for Tall Fescue Zone 7b
- Built single-file React app with iOS-style UI
- Added: Disease Guide, Products tab, GitHub Gist sync, security audit
- Removed: Ask AI tab (Kunal has paid Claude subscription)
- Fixed bugs: overlapping UI elements, Gist creating new sync per device (now auto-detects existing)
- Replaced Step 5 Weed & Feed with correct low-nitrogen separate fertilizer approach

---

*Last updated: April 15, 2026*
