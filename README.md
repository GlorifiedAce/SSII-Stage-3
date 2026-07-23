# Beyond the Shopfront

An interactive, animated branching story exploring how globalisation affects the sustainability of small and medium enterprises (SMEs) in Singapore's business and trade sector.

Built as the Stage 3 showcase product for a Social Studies Issue Investigation (SS II) project.

**Play it:** _add your Netlify link here once deployed_

---

## About this project

**Sub-inquiry question:** How does globalisation affect the sustainability of Small and Medium Enterprises (SMEs) in the business and trade sector?

**Class:** 4i1 · **Group:** 7

| Name | Index No. |
|---|---|
| Song Meng Xin * (leader) | 25 |
| Low Jit Yoke Edric | 21 |
| Wang Zhiyuan | 29 |
| Zheng Shengbai | 32 |

### Why this product, and for whom

- **Target audience:** peers and teachers unfamiliar with the day-to-day pressures facing local SME owners — people more likely to engage with a short interactive story than a written report.
- **Mode of presentation:** a browser-based interactive story rather than a slide deck or essay, so the audience *makes the same decisions* a real SME owner has to make, rather than just reading about them.
- **Why it fits the findings:** our secondary research and interviews kept surfacing the same idea — globalisation is a double-edged sword, and there is no single "correct" response for an SME. Branching choices let the audience feel that ambiguity directly, instead of being told about it.

Every ending in the story is annotated with the specific finding from our research or interviews that it dramatises, so the fictional narrative always ties back to real evidence. See [Grounding the story in our research](#grounding-the-story-in-our-research) below.

---

## What it is

A small web app: a cast of animated 2D characters, hand-built SVG backgrounds, dialogue with mood-based expressions, camera pans/zooms, light sound design, and 2–3 branching choices at key decision points that lead to different scenes and endings.

- Runs entirely in the browser — no backend, no build step required to view it.
- Fully static, so it deploys to Netlify (or GitHub Pages) as-is.
- Content (story text, characters, backgrounds) is separated from the rendering engine, so new scenes/branches can be added without touching any animation code.

## Project structure

```
globalisation-story/
├── index.html              # entry point — loads the engine and mounts the story
├── src/
│   ├── data/
│   │   └── story.js         # ALL story content: scenes, dialogue, choices, endings
│   ├── characters/
│   │   └── characters.js    # character SVGs (one function per character)
│   ├── scenes/
│   │   └── backgrounds.js   # background SVGs (one function per location)
│   ├── engine/
│   │   ├── engine.js         # scene graph walker, choice handling, state
│   │   ├── camera.js         # pan/zoom tween logic
│   │   └── audio.js          # sound effect + music cue playback
│   └── styles/
│       └── styles.css        # layout, character animation, UI, mood classes
├── assets/
│   └── sfx/                 # short sound effect files (click, page-turn, chime, etc.)
├── netlify.toml              # deployment config
└── README.md
```

> **Note:** this repository is being built incrementally. If a folder above is empty or missing on your clone, it means that part hasn't been generated yet — check the commit history / project board for progress.

## Running it locally

No build tools or installs are required — it's plain HTML/CSS/JS.

```bash
git clone <this-repo-url>
cd globalisation-story
python3 -m http.server 8000
# then open http://localhost:8000 in your browser
```

(Opening `index.html` directly by double-clicking also works in most browsers, but a local server avoids browser restrictions on loading local JS modules.)

## Deploying to Netlify

1. Push this repo to GitHub.
2. In Netlify: **Add new site → Import an existing project → choose this repo**.
3. Build settings: leave **Build command** blank, set **Publish directory** to the project root (`/`).
4. Deploy. Netlify will give you a live URL — add it to the top of this README.

Alternatively, drag-and-drop the whole project folder into Netlify's "Deploys" page for a one-off manual deploy.

## Adding new content

The project is organised so that **story content, characters, and backgrounds are independent of the engine** — you should rarely need to touch `src/engine/` at all.

**Add a new scene or branch**
Open `src/data/story.js` and add a new scene object with a unique `id`. Point an existing scene's `choices[].next` (or `next`) at your new scene's `id`. The engine walks this automatically — no other file needs to change.

**Add a new character**
Open `src/characters/characters.js` and add a new entry to `CHARACTERS`, reusing the shared `personSVG()` template with a new palette. Reference the character's key in a scene's `actors` array.

**Add a new background**
Open `src/scenes/backgrounds.js` and add a new `key: () => \`<svg>...\`` entry to `BACKGROUNDS`. Reference the key as a scene's `background`.

**Add a new sound effect or music cue**
Drop the audio file into `assets/sfx/`, then reference its name in `src/engine/audio.js`'s cue map, and use that cue name in a scene's `music` field or dialogue line.

## Grounding the story in our research

The story is fictional (a shop called "Lim Trading" and its owner, Mei), but every plot beat and ending is drawn directly from our Stage 2 findings:

- SMEs make up over 99% of enterprises in Singapore and about 45% of GDP, with a trade-to-GDP ratio consistently exceeding 300% — establishing why this issue matters at a national scale.
- Globalisation is a double-edged sword: it opens new markets while intensifying competition from overseas sellers and MNCs (Sources 1, 2; interviews with Mr Wang, Mr Tan).
- Digital adoption has shifted from optional to essential for SME survival (Sources 2, 5, 6).
- Government support schemes exist but often don't resolve deeper structural issues, particularly around financing (Sources 4, 12, 13, 14).
- 60,000 Singapore businesses closed in 2025 — the highest figure in 8 years (Source 11) — which directly informs the story's "Closing Down" ending.

Full citations and analysis are in our Stage 2 submission (secondary research + interview write-ups), not reproduced here.

## Rubric alignment

This product is designed to speak to both grading criteria:

- **Explanation:** each ending in-app is paired with a short note connecting it back to a specific research finding or interview insight, so the reasoning is explicit rather than left implicit in the story alone.
- **Creativity:** an original interactive narrative with custom-illustrated characters/backgrounds and multiple branching paths, rather than a conventional poster, slideshow, or report.

## Credits

Story, code, and illustrations created by Group 7 (4i1) for the SS II Issue Investigation, Stage 2/3.
