# Beyond the Shopfront

A branching interactive story about how globalisation is affecting small and medium enterprises (SMEs) in Singapore — built for our Social Studies Issue Investigation, Stage 3.

**Play it here:** _https://glorifiedace.github.io/SSII-Stage-3/_

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

### Why we made this, and for who

We picked our audience first: people who don't know much about what SME owners are actually dealing with day to day — mainly classmates and teachers. A written report tells people that globalisation is a double-edged sword. We wanted them to feel that instead, by putting them in the position of having to make the same calls a shop owner would.

That's why we went with a branching story instead of a slide deck or essay. There's no single right choice in the story — same as in real life for these business owners — and each ending is tied back to something specific from our research, so the story doesn't drift away from what we actually found.

## What's in it

Animated characters (drawn as SVGs, not image files), hand-built backgrounds, dialogue that changes each character's expression, camera pans and zooms, background music and sound effects generated in the browser, and a few branch points that lead to different endings.

It's plain HTML/CSS/JS — no frameworks, no build step, nothing to install.

## Project structure

```
globalisation-story/
├── index.html                # entry point
├── src/
│   ├── data/
│   │   └── story.js           # all the story content — scenes, dialogue, choices, endings
│   ├── characters/
│   │   └── characters.js      # character SVGs
│   ├── scenes/
│   │   └── backgrounds.js     # background SVGs
│   ├── engine/
│   │   ├── engine.js           # runs the story — scene switching, choices, rendering
│   │   ├── camera.js           # handles the pan/zoom camera moves
│   │   └── audio.js            # music + sound effects (Web Audio API, no sound files)
│   └── styles/
│       └── styles.css          # everything visual
└── README.md
```

## Running it on your own computer

```bash
git clone <this-repo-url>
cd globalisation-story
python3 -m http.server 8000
```

Then open `http://localhost:8000` in a browser. (Double-clicking `index.html` sometimes works too, but some browsers block local JS modules that way, so the server is the safer bet.)

## Putting it on GitHub Pages

1. Push everything to GitHub, with `index.html` sitting at the root of the repo.
2. Go to **Settings → Pages**.
3. Under **Source**, choose "Deploy from a branch," set branch to `main` and folder to `/ (root)`.
4. Wait a minute or two — GitHub will give you a link once it's built.

If it shows the README instead of the actual site, it usually means `index.html` isn't at the root, or Pages is pointed at the wrong branch — check Settings → Pages again.

## Changing or adding to the story later

Everything you'd want to edit lives outside `src/engine/` — you shouldn't need to touch the engine itself.

**New scene or branch:** add an entry to `src/data/story.js` with a unique `id`, then point another scene's `next` (or a `choices[].next`) at it.

**New character:** add an entry to `CHARACTERS` in `src/characters/characters.js`, reusing the existing template with different colours.

**New background:** add an entry to `BACKGROUNDS` in `src/scenes/backgrounds.js`.

**New music or sound:** edit `src/engine/audio.js` — add to `MOODS` for a new music mood, or `SFX` for a new sound effect.

## How this ties back to our research

The shop and characters are made up, but every ending in the story comes from something we actually found in Stage 2:

- SMEs make up over 99% of enterprises in Singapore and about 45% of GDP, with a trade-to-GDP ratio consistently above 300% — this is why the issue matters at a national scale, not just to individual shop owners.
- Globalisation opens up new markets, but it also brings in more competition from overseas sellers and MNCs (Sources 1, 2; interviews with Mr Wang, Mr Tan).
- Going digital has stopped being optional for SMEs and become something closer to a requirement (Sources 2, 5, 6).
- Government schemes help, but they don't usually fix the deeper problem, especially around financing (Sources 4, 12, 13, 14).
- 60,000 businesses in Singapore closed in 2025, the highest number in 8 years (Source 11) — this is what the "Closing Down" ending is based on.

Full sources and our interview write-ups are in the Stage 2 submission, not repeated here.

## How this meets the rubric

**Explanation:** every ending comes with a short line connecting it to a specific piece of our research or an interview, so it's clear the story isn't just made up for its own sake — it's showing what we actually found, and staying focused on the investigation throughout.

**Creativity:** instead of a poster or a slideshow, we built something people can actually interact with — original characters, original artwork, a branching plot with several different outcomes, and a bit of sound and animation to go with it.

## Credits

Made by Group 7, 4i1, for the SS II Issue Investigation.
