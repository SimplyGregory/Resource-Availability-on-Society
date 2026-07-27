# Resource Availability on Society 🏝️

An interactive, browser-based evolutionary simulation exploring how resource scarcity shapes whether aggression or cooperation comes to dominate a society - a hawk–dove genetic algorithm rendered as a 2.5D island.

<img alt="Image" src="./Example.png" align="right" width="440" />

[![Language](https://img.shields.io/badge/Language-JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black)](#)
[![3D](https://img.shields.io/badge/3D-Three.js-000000?style=flat-square&logo=threedotjs&logoColor=white)](https://threejs.org/)
[![Platform](https://img.shields.io/badge/Platform-Web-4285F4?style=flat-square&logo=googlechrome&logoColor=white)](#)
[![Build](https://img.shields.io/badge/Build-None%20(static)-2EA44F?style=flat-square)](#)

---

## About This Project
<hr />

- `index.html` is the entire application - simulation, 3D scene, control panel, and live graph in one self-contained file.
- `libs/` holds a self-hosted copy of **Three.js (r0.169.0)** and **OrbitControls** - no CDN required.
- `fonts/` holds self-hosted web fonts (EB Garamond, IBM Plex Sans/Mono) so the page needs zero external requests.
- `assets/` holds the PNG artwork (animals, bushes, food, homes) loaded onto the island.

**Research question:** *To what extent does resource scarcity determine whether aggression or cooperation dominates in a GA-based simulation?*

## How It Works
<hr />

Every animal carries one heritable trait - an **aggression gene** (0–1) - which is simply its probability of picking a fight on any given day.

- Each morning an animal rolls a role: **hawk** (fights) or **dove** (shares), weighted by its gene.
- Food is scattered on the island; animals forage. Two doves at a fruit **share** it; two hawks **fight** (and risk injury); a hawk meeting a dove usually **steals** it.
- End of day: `0 food → dies`, `1 → survives`, `2 → survives and reproduces` (asexual clone with a small mutation).
- Fighting injuries are **worse when underfed**, which is what couples scarcity to selection.

Over many days the **average gene** rises or falls - the gold line on the graph is the answer to the research question.

## Running It
<hr />

The app uses ES modules, which browsers block over `file://`. Serve it over HTTP instead:

```
python -m http.server 8000
```

Then open **http://localhost:8000**. To deploy, upload the whole folder to any static host (GitHub Pages, Netlify, S3, itch.io) - no build step.

## Controls
<hr />

- **Play / Step / Reset** to run, advance one day, or restart.
- **Food each morning** is the main variable - the scarcity dial.
- Advanced sliders (**injury cost, aggressor backfire, fighting destroys food, sharing risk, mutation, hunger cost**) tune the rules.
- The **graph** plots population (blue = doves, red = hawks) and the mean aggression gene (gold, 0–1).

## Contact
<hr />

- YouTube: https://www.youtube.com/@ModSpidr
- Portfolio: https://gregorybridges.dev
- Email: contact@gregorybridges.dev
