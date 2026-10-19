# ☁️ Mizzle: Baby's First Portfolio

> “Small weather, big hugs.”

A portfolio website for **Mizzle**, an original baby raincloud and Junior Weather Weaver. Built for the [haX.baby "Baby's First Website"](https://hax.baby/first-website) 48-hour hackathon (17–19 Oct 2026), **Track 2: Your Own Baby**.

**Live demo:** https://mizzle-puddlewick.vercel.app
**Built by:** Abhishek

---

## Character sheet

| | |
|---|---|
| **Name** | Mizzle |
| **What they are** | A baby raincloud, cream-white with berry cheeks. Curious, shy, easily delighted. Voice: a soft "plink-plink", with a thunder hiccup when too happy. |
| **What they do** | Junior Weather Weaver at the Puddlewick Weather Workshop: lullaby rain, puddle postcards, umbrella routes. |
| **Their story** | Sneezed out of a grumpy thundercloud over the town of Puddlewick, then learned from Mrs. Tulip that one small drop can fix a whole day. |
| **Tagline** | "Small weather, big hugs." |

## Showcase projects

1. **The Drizzle Lab:** a raindrop music box (8 pentatonic notes, keys 1–8) and a looping rain ambience, synthesized live with the Web Audio API.
2. **Puddle Postcards:** three 3D flip cards (CSS `rotateY`, keyboard accessible).
3. **Umbrella Routes:** an SVG path drawn and followed by a cloud marker, synced to scroll with `getPointAtLength()`.

## Features

| Brief item | Implementation |
|---|---|
| Character reacts to visitor | Pupils follow the pointer; idle wander when there is no pointer (touch fallback) |
| Scroll-driven story | 4 scenes (each under 150 words) revealed with `IntersectionObserver` |
| Tier 3: 3D / WebGL | Three.js cloud in a sticky canvas beside the story; its size, rotation, rain and rainbow are driven by scroll progress; eyes follow the pointer |
| Day/night mood toggle | Swaps the CSS custom-property palette and Mizzle's expression (sleepy lids, "z Z"); saved in `localStorage` |
| Responsive layout | Mobile-first CSS grid, breakpoint at 720px |
| Hidden Easter egg | Boop Mizzle's nose 5 times 🤫 |
| Tier 2: Web Audio | Oscillator music box plus filtered-noise rain, with a mute switch |
| Tier 2: SVG route | `stroke-dashoffset` animation synced to scroll progress |
| Tier 3: visitor memory | Returning-visitor greeting via `localStorage` |
| Side quest: sparkle trail | Throttled pointer-move particles |
| Side quest: click sounds + mute | Soft blips on buttons and links; mute state persisted |
| Side quest: odometer | Counts the raindrops you make in the Drizzle Lab |
| Side quest: wish wall | Leave a wish; stored locally (see Limitations) |

## Tech

Plain **HTML + CSS + JavaScript** in a single `index.html`, plus **Three.js r128** (cdnjs). No framework, no build step.

```
mizzle-puddlewick/
├── index.html   # markup, CSS, JS and the Three.js scene, all in one file
└── README.md
```

External requests: Google Fonts (Fredoka, Fraunces) and Three.js from cdnjs. If WebGL or the CDN is unavailable, the 3D canvas is skipped and the rest of the site still works.

## Run locally

```bash
git clone https://github.com/YOUR-USERNAME/mizzle-puddlewick.git
cd mizzle-puddlewick
# open index.html directly, or serve it:
npx serve .
```

## Deploy

- **Vercel / Netlify:** import the repo, framework "Other", no build command, output directory `.`
- **GitHub Pages:** Settings → Pages → deploy from `main`, folder `/ (root)`

## Accessibility and performance

- Visible, persistent **mute toggle**; sound only starts after a user gesture
- `prefers-reduced-motion` disables animations and the sparkle trail
- Keyboard support for keys, flip cards, nose, and toggles; skip link; ARIA labels and `aria-pressed` states
- The 3D canvas is `aria-hidden` (the story text carries the content) and the pixel ratio is capped at 2

## Limitations

- The wish wall, odometer, and visit counter use `localStorage`, so they are **per browser**, not shared between visitors. A shared guestbook would need a backend (e.g. Supabase or Firebase).

## Credits

- Mizzle and all artwork: original, drawn in inline SVG, CSS and Three.js primitives (no existing IP)
- Audio: synthesized at runtime with the Web Audio API (no samples)
- 3D: [Three.js](https://threejs.org/) r128 (MIT)
- Fonts: [Fredoka](https://fonts.google.com/specimen/Fredoka) and [Fraunces](https://fonts.google.com/specimen/Fraunces) via Google Fonts (SIL OFL)
- Scene icons: system emoji
- Built with AI assistance (Claude) for the haX.baby hackathon, as permitted by the rules

## Hackathon

Made during the 48-hour sprint, 17–19 October 2026. See the commit history for the build timeline.
