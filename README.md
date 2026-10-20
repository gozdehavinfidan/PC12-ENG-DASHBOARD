# PC12 Project Dashboard

Team dashboard of the PC12 project (automated morphological analysis of PC12 cells, ENG401):
live status, Gantt chart, task board, presentation plan, risks and the decision index.

**Live:** https://gozdehavinfidan.github.io/PC12-ENG-DASHBOARD/

**Local:** double-click `docs/index.html`. No install, no server, no build step.

## Related repositories

| Repository | What it holds |
|---|---|
| **PC12-ENG-DASHBOARD** (this one, public) | the dashboard website only |
| [PC12-arch](https://github.com/gozdehavinfidan/PC12-arch) (private) | ML code, experiments, reports, presentations, knowledge base and decision log |
| [camex-desktop-app](https://github.com/gozdehavinfidan/camex-desktop-app) (private) | CAMEX, the offline desktop app |

## Updating the board from the site

The site can write. Marking a task done, joining a task, adding a task or a note each appends one line
to `docs/data.txt`. On every load the page rebuilds the state from `docs/data.js` (the baseline) plus the
events in `docs/data.txt`, so changes survive a refresh.

To save, click **Enter token & save** and paste a GitHub fine-grained token
(GitHub → Settings → Developer settings → Fine-grained tokens) limited to this repository with
**Contents: Read and write**. The token is kept in memory only while the tab is open; it is never stored
or committed. Without a token, use **Copy lines** and paste them into `docs/data.txt` in the GitHub web
editor.

## Layout

```
docs/                      # published by GitHub Pages (branch main, folder /docs)
├── index.html             # page shell; loads data.js, then app.js
├── app.js                 # rendering and interaction (plain script, works from file:// too)
├── data.js                # baseline: weeks, work packages, tasks, decisions index
├── data.txt               # append-only event log written by the site
├── styles.css
├── assets/                # fonts (OFL) and a profile photo
└── presentations/         # weekly presentation decks shown on the board (W<n>.html)
gantt-chart.xlsx           # course Gantt chart the work packages mirror
```

## Editing by hand

- Change `docs/data.js`, `docs/app.js` or `docs/styles.css` → bump the `?v=N` number in
  `docs/index.html`, otherwise browsers and the Pages CDN keep serving the old file.
- `docs/data.txt` is append-only: add lines, never edit or delete old ones (renamed task ids are mapped
  in `data.js` instead).
- The reasoning behind every design choice is in the decision log of PC12-arch
  (`docs/knowledge-base/decisions.md`; the dashboard data model is D7 and D11).

## What must never be committed

This repository is public. `.gitignore` is a whitelist: only `docs/`, this README, the Gantt chart and the
git config files are tracked, so private material in the local folder (TÜSEB application, thesis, slides,
microscopy) is ignored by default.
