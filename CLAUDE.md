# Project Guidelines

## Main working file
**Always edit `index.html` only.**  
`probebacwe.html` has been deleted — it no longer exists.

## Repository structure
- `index.html` — sole source of truth, GitHub Pages entry point
- `Pathway Intermediates_CI.png` — Pathway Intermediates logo
- `og-image.png` — Open Graph social preview image
- `probebac-we-logo.png` — ProBe-Bac WE logo (watermark + top banner)
- `probebac-we-logo2.png` — ProBe-Bac WE logo (top banner right)

## Deployment
GitHub Pages deploys from the `main` branch root.  
**The live site URL is:** `https://pathway-bd.github.io/Probe-bac_WE/`

---

## Rules to prevent repeated mistakes

### 1. Always branch from `origin/main`
**Never** create a feature branch from another feature branch.  
Always run:
```
git checkout -b claude/<branch-name> origin/main
```
Branching from a feature branch causes squash-merges to produce empty diffs (no-op), meaning the change never lands on main even though the PR shows as merged.

### 2. Verify the change is actually on `main` after every merge
After every merge, immediately run:
```
git fetch origin main && git show origin/main:index.html | grep "<key string>"
```
Confirm the expected content is present before reporting the task as done. Do not trust the PR merge status alone.

### 3. `index.html` is the only file that matters for the live site
GitHub Pages serves `index.html` from the root of `main`.  
Editing any other HTML file has zero effect on the live site.  
Always confirm you are editing `index.html`, never another file.

### 4. Default values to preserve
These values must remain set in `index.html` and must not be accidentally reverted:
- **WE Concentration (ppm):** `value="50"` and `getVal('pbPpm', 50)`
- **Water:Feed Ratio (음수량):** `value="2"` and `getVal('pbWFRatio', 2)`
