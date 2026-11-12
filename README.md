# Watercolor-Bingo-Rain-Ver.1.7---artifact-e4ca0b34-dd80-4c9e-8166-628d8d96c77f-4
Watercolor Bingo Rain Ver.1.7 - artifact-e4ca0b34-dd80-4c9e-8166-628d8d96c77f-4
## v1.7 — Melt & Keys

**Release tag:** `v1.7`
**Type:** Feature + polish

---

### ✨ Highlights

- **Removed the wax-melt effect.** Balls now dissolve cleanly into the water — fade,
  blur and a slight spread — instead of squashing and dripping. The transition is
  also ~2× faster.
- **New `I` key toggles the control panel** on and off.
- **`F` now does fullscreen only** (it used to also hide the UI).

### 🔧 Fixes

- **Critical:** a stray comment swallowed an `if` statement's opening brace, which
  threw a syntax error and killed the whole script — the page rendered as a black
  screen. Fixed.
- Bounce friction was trapped behind a comment and never applied.
- Resting balls never picked up rolling friction, so they slid off-screen forever.

### 🛡️ Quality of life

- Added an **on-screen error banner** so any future JS error is visible instead of
  silently producing a blank canvas.
- Added a **"running" status badge** plus a live FPS readout at the top of the panel.
- Background base lightened (`#04070e` → `#070d1a`) so the dark theme reads better.

### ⌨️ Keyboard

| Key | Action |
|---|---|
| `F` | Fullscreen |
| `I` | Show / hide the control panel |
| `P` | Pause |
| `Space` | Burst |
| `R` | Reset |

### ⚠️ Breaking changes

None for users. For anyone who forked **before v1.7**, note two API changes:

- `toggleUI()` → renamed to **`togglePanel()`**
- `waxDrip()` and the `wax` flag on droplet particles were **removed**

### 📦 Upgrade
<div align="center">

# 🎨⚽ → 💧 Watercolor Bingo Rain

**An interactive canvas artwork where soccer balls burst, bounce like a bingo drum,
dissolve into slow undulating water, and get rained on — all painted over a living
watercolor wash.**

`v1.7` · Zero dependencies · Pure HTML5 Canvas · ~1 file, ~900 lines

[![](https://img.shields.io/badge/HTML5-Canvas-42a5f5?style=flat-square&logo=html5)](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API)
[![](https://img.shields.io/badge/JavaScript-ES6-f7df1e?style=flat-square&logo=javascript)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
[![](https://img.shields.io/badge/Dependencies-0-success?style=flat-square)](#dependencies)
[![](https://img.shields.io/badge/License-MIT-9ddf6c?style=flat-square)](LICENSE)

</div>

---

## 📸 Preview

> Add your screen recording / GIF here.
>
> `![preview](assets/preview.gif)`

---

## 🎯 What is this?

A generative, real-time **visualisation** built as a single HTML file — part generative
art, part physics toy, part stress test for the browser's 2D canvas.

The scene has three layers that all feed each other:

| Layer | What it does |
|---|---|
| 🎨 **Watercolor background** | Nine slow "washes" and thirty drifting "pigment blooms" render into a tiny 5.5 %-resolution buffer, then upscale with bilinear smoothing. The pigment **pools at the edges** of each blob (via gradient stop engineering) and its **hue rotates continuously**, so the palette never settles. |
| ⚽ **Balls** | Balls burst in groups of **30 → 50 → 30 → 50** every 3–7 seconds, roll in from the screen edges, bounce with real restitution, **jostle against each other** into a bingo-drum pile, settle, then **dissolve into water**. |
| 💧 **Water + weather** | Puddles grow, **merge into lakes**, and undulate with layered sine waves. **Big rain drops** fall, splash, and send out **slow-fading expanding ripples** across the surface. |

### ✨ Highlights

- ⚽ **Bingo-style physics** — restitution, rolling friction, rolling spin, and pairwise
  ball-vs-ball separation so balls pile up like real ones in a drum.
- 🧪 **Watercolour pigment simulation** — edge pooling, hue drift, additive/multiply
  blending, paper grain, and a cursor that paints live into the wash.
- 💧 **Self-merging water** — puddles detect overlap and fuse into wider lakes with
  averaged hue.
- 🌧️ **Big rain** — teardrop drops with motion trails, highlights, splashes and ripples.
- 🔄 **Alternating 30/50 bursts** on a randomised 3–7 s gap.
- 🎛️ **Live control panel** — bursts, wave speed/height, spread, rain rate, theme.
- ⌨️ **Full keyboard control** — `F` fullscreen, `I` toggle panel, `P` pause, `Space` burst.
- 🚨 **Built-in error trap** — any JS error surfaces as an on-screen banner instead of
  a silent black screen.

---

## 🚀 Quick start

### Option1 — just open it

```bash
git clone https://github.com/<you>/watercolor-bingo-rain.git
cd watercolor-bingo-rain
xdg-open index.html     # macOS: open index.html  |  Windows: start index.html
```

No build step. No server. No `npm install`. **It just runs.**

### Option 2 — GitHub Pages

1. Push the repo to GitHub.
2. **Settings → Pages → Source: `Deploy from a branch` → `main` / `/ (root)`**.
3. Your artwork is live at `https://<you>.github.io/watercolor-bingo-rain/`.

### Option 3 — local server (optional)

```bash
python -m http.server 8000
# → http://localhost:8000
```

---

## 🎮 Controls

### Keyboard

| Key | Action |
|---|---|
| <kbd>F</kbd> | Toggle **fullscreen** |
| <kbd>I</kbd> | Toggle the **control panel** on / off |
| <kbd>P</kbd> | **Pause** / resume the animation |
| <kbd>Space</kbd> | Trigger a **burst** immediately |
| <kbd>R</kbd> | **Reset** — clear all balls, water and ripples |
| **Click** | Spawn a ball (clicking near an edge spawns it *from* that edge) |
| **Move mouse** | Paints live pigment into the background wash |

### Control panel

| Section | Control | Range | Default |
|---|---|---|---|
| **Scene** | Pause · Burst now · Clear | — | — |
| **Bursts** | Balls per burst | 0 – 90 | 30 |
| | Alternate 30 → 50 → 30 → 50 | on / off | **on** |
| | Gap min / max | 0.5 – 14 s | 3 s / 7 s |
| **Water** | Wave speed | 0 – 6× | 1.2× |
| | Wave height | 0 – 2.5× | 1× |
| | Spread (how fast lakes grow) | 0 – 3× | 1× |
| **Weather** | Big rain drops / sec | 0 – 24 | 7 |
| **Look** | Background flow | on / off | on |
| | Cursor paints | on / off | on |
| | Paper (light) theme | on / off | off |

---

## ⚙️ How it works

### 1. The watercolor background

Painting fluid pigment with canvas gradients is normally expensive, so the background is
rendered into an **offscreen buffer at 5.5 % resolution** and then upscaled:

```js
const BG_SCALE = 0.055;                 // buffer is 5.5% of screen size
bgC = document.createElement('canvas');
bgC.width = Math.round(W * BG_SCALE);
bgC.height = Math.round(H * BG_SCALE);
```

Upscaling a tiny canvas with `imageSmoothingEnabled` gives free, buttery blur. Each
pigment blob is a radial gradient with a deliberately **non-monotonic alpha profile**:

```js
grd.addColorStop(0.00, `hsla(${hue},${sat}%,${lit}%,${a})`);        // core
grd.addColorStop(0.38, `hsla(${hue},${sat}%,${lit}%,${a*0.55})`);    // body
grd.addColorStop(0.70, `hsla(${h2},${sat}%,${lit}%,${a*0.20})`);     // thin edge
grd.addColorStop(0.86, `hsla(${h2},${sat}%,${lit}%,${a*0.30})`);     // ← edge pooling!
grd.addColorStop(1.00, `hsla(${h2},${sat}%,${lit}%,0)`);            // falloff
```

The bump at `0.86` is what makes it read as **watercolour** rather than a neon glow —
real pigment migrates to the drying edge of a wash.

Blobs are composited with `lighter` (dark theme) or `multiply` (paper theme) so
**overlapping washes mix** instead of just stacking. Hue rotates over time, so the
palette is never static.

### 2. The soccer balls

Every ball is drawn once into an **offscreen sprite canvas** and cached by
`hue | saturation | lightness | radius-bucket`, then blitted with rotation:

```js
const key = `${hue}|${sat}|${lit}|${rb}`;   // rb = radius rounded to 3px
```

This keeps a busy frame at ~80 balls cheap — no gradient or path work happens per
frame, only `drawImage`.

The ball geometry is a real pentagon layout: one centre pentagon, five rim pentagons
(clipped by the ball edge), and seam lines joining the vertices.

### 3. The physics

```js
b.vy += GRAV * dt;             // gravity
b.vy = -b.vy * 0.52;           // restitution on bounce
b.vx *= 0.80;                  // horizontal friction on impact
b.vx *= Math.pow(0.18, dt);    // rolling friction once resting
b.vr  = b.vx / b.r * 0.9;      // rolling spin derived from velocity
```

Ball-vs-ball separation is an O(n²) pass — cheap at 80 balls, and it produces the
satisfying **jumbled bingo heap** instead of balls overlapping each other.

### 4. Water, merging and waves

Every puddle renders its surface as a **sum of two sine waves** sampled along the
top edge, so the surface genuinely moves up and down:

```js
function waveY(p, u, t) {
  const a = p.h * 0.5 * S.waveAmp;
  const sp = t * p.speed * S.waveSpeed;
  return p.y - p.h * 0.5
    + Math.sin(u * 6.2832 * p.freq + sp + p.phase) * a
    + Math.sin(u * 6.2832 * p.freq * 1.73 - sp * 0.78 + p.phase * 1.3) * a * 0.42;
}
```

Puddles that overlap **fuse**: the union of their x-ranges becomes a new, wider lake
with an averaged hue — which is how the scene gradually becomes one body of water.

### 5. Ripples

A ripple is an expanding ellipse with an ease-out radius curve and a quadratic
alpha fade, so it lingers long after it stops growing:

```js
const e   = 1 - Math.pow(1 - k, 2.4);            // radius easing
const rr  = r.r0 + (r.r1 - r.r0) * e;
alpha = r.alpha * (1 - k) * (1 - k) * 0.9;   // slow fade
```

Ripples are spawned by **ball impacts**, **full absorption into water**, and **raindrop
strikes**.

---

## 🎨 Customising it

Everything lives in one `S` object near the top of the script:

```js
const S = {
  theme: 'deep',      // 'deep' | 'paper'
  bgFlow: true,       // animate the pigment
  waveAmp: 1.0,       // wave height
  waveSpeed: 1.2,     // wave speed
  spread: 1.0,        // how fast lakes grow
  ballsPerBurst: 30,
  alternate: true,    // 30 -> 50 -> 30 -> 50
  gapMin: 3, gapMax: 7,
  rain: 7,            // drops per second
  paused: false
};
```

**Change the ball palette:**

```js
const BALL_HUES = [4,22,40,58,86,110,140,166,186,199,206,216,232,252,270,288,304,320,338];
// └─ curated set └─ or set to a single hue, e.g. [200]
```

**Make every ball a different random colour** (already supported for 35 % of spawns —
raise the probability in `spawnBall`):

```js
const useRandomHue = Math.random() < 0.35;   // ← change 0.35
```

**Change gravity / bounce feel:**

```js
const GRAV = 1750;   // heavierconst GRAV = 900;    // floatier, more bingo-drum-like
```

**Change the horizon:**

```js
groundBase = H * 0.865;   // fraction of screen height
```

**Change the background resolution** (lower = softer and cheaper, higher = crisper):

```js
const BG_SCALE = 0.055;   // try 0.03 for a dreamier wash
```

**Change the dissolve speed** — how long a ball takes to become water:

```js
b.melt += dt / 1.1;   // 1.1 seconds — try dt / 2.5 for a slower fade
```

---

## 📁 Project structure

```
watercolor-bingo-rain/
├── index.html          # the entire artwork (HTML + CSS + JS, single file)
├── README.md           # you're reading it
├── LICENSE             # MIT
└── assets/
    └── preview.gif     # screen recording for the README hero image
```

---

## 🧩 Architecture```
┌─────────────────────────────────────────────────────────────┐
│  requestAnimationFrame loop (dt-clamped to 50 ms)           │
│                                                             │
│  update(dt, t)                                             │
│   ├── balls      gravity · bounce · roll · separate · melt │
│   ├── water      grow · drift · merge                       │
│   ├── droplets ballistic splash particles │
│   ├── rain       big drops → splash + ripple                │
│   └── ripples    expand + fade                              │
│                                                             │
│  render()                                                   │
│   ├── background offscreen 5.5% buffer → upscale           │
│   ├── ground      wavy horizon + pigment dabs │
│   ├── water       layered-sine surfaces + crest highlights │
│   ├── ripples     additive expanding ellipses                │
│   ├── rain        teardrops with trails                     │
│   ├── balls       cached sprites, dissolve blend │
│   ├── droplets    spray │
│   └── grain + vignette │
└─────────────────────────────────────────────────────────────┘
```

---

## 🧭 Changelog

### v1.7 — *current*
- ✨ **Removed the wax-melt effect** — balls now dissolve cleanly into water  (fade + blur + spread) instead of squashing and dripping.
- ⌨️ **`F` now toggles fullscreen only**; the control panel moved to **`I`**.
- 🐛 **Fixed a critical syntax error** where a trailing comment swallowed an `if`
  statement's opening brace, killing the entire script and rendering a black screen.
- 🐛 **Fixed missing bounce friction** (it was trapped behind a comment).
- 🐛 **Fixed resting balls never applying rolling friction**, so they slid off-screen.
- 🚨 Added an **on-screen error banner** and a **"running" status badge**.
- ✨ Added **ball-vs-ball separation** for a proper bingo-drum pile.
- ✨ Added **edge spawns** — balls roll in from the left and right edges.
- ✨ Added **big rain drops** with trails, splashes and ripples.
- ✨ Added **wave speed** control and **rain rate** control.

### v1.6
- Alternating **30 / 50 ball bursts** on a randomised 3–7 s gap.
- **Pause** control and `P` shortcut.
- **Ball count** and **wave speed** sliders.
- Slower, wider-spreading watercolor background.

### v1.5
- First **burst system** (30 balls every 3–7 s).
- `F` = fullscreen + hide UI.
- Ball sizes and hues widened; some spawns near screen edges.

### v1.4
- Ripples and splashes on impact.
- Merging puddles.

### v1.0 — *first light*
- Falling soccer balls, circle-texture-style sprites, ground collision.
- Puddles with two-sine wave surfaces.
- Static watercolor background.

---

## ⚠️ Known limitations

- **Very wide screens** can dip below 60 fps because every puddle re-renders its wave
  path each frame. Lowering `BG_SCALE` or the ball count helps.
- **Ripples are drawn flat on the ground line**, not on the surface of individual
  lakes, so they read as a single water plane rather than per-lake waves.
- **Puddles merge by x-overlap**, not by true fluid simulation — a puddle that drifts
  past another will fuse with it even if the shapes didn't really touch.
- The `ctx.filter = 'blur()'` dissolve needs a reasonably modern browser; without it
  the dissolve still works, just without the blur.
- Mobile touch works for spawning, but the control panel needs a wide viewport.

---

## 🛠 Browser support

| Browser | Support |
|---|---|
| Chrome / Edge 90+ | ✅ Full |
| Firefox 90+ | ✅ Full |
| Safari 15+ | ✅ Full (blur may be soft) |
| Mobile Safari / Chrome | ✅ Works, panel needs space |

Uses only `Canvas 2D`, `requestAnimationFrame`, `Pointer Events` and `Fullscreen API`.

---

## 🚧 Roadmap

- [ ] True per-lake ripple interaction (waves that displace the surface)
- [ ] Optional WebGL/WebGPU renderer for thousands of puddles
- [ ] A "lake" mode where the ground floods and balls float
- [ ] Palette presets (ocean / sunset / monochrome)
- [ ] Export frame as PNG
- [ ] Touch-friendly control panel layout

---

## 🤝 Contributing

Contributions are welcome — especially visual experiments!

1. Fork the repo and create a branch: `git checkout -b feature/your-idea`
2. Keep it **dependency-free** and inside a single `index.html` if you can.
3. Please test in **at least two browsers** and check the console is clean.
4. Open a Pull Request with a short description and, ideally, a GIF.

**Good areas to contribute:** new backgrounds, new particle effects, better wave
physics, mobile layout, accessibility (a reduced-motion mode would be welcome).

---

## 📄 License

MIT — see [LICENSE](LICENSE).

```
MIT License

Copyright (c) 2026 <your name>

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

---

## 🙏 Acknowledgements

- Inspired by **bingo-ball drums** and by the way **watercolour washes bloom** on wet paper.
- Built as a playful exploration of what a single `<canvas>` can do with nothing but gradients.
- Dedicated to everyone who has ever watched a paint drop spread.

<div align="center">
<sub>Made with 🎨, ⚽ and 💧 — v1.7</sub>
</div>


Replace `index.html` with the new one — there is no build step and no dependencies.

<div align="center">

# 🎨⚽ → 💧 Watercolor Bingo Rain

**An interactive canvas artwork where soccer balls burst, bounce like a bingo drum,
dissolve into slow undulating water, and get rained on — all painted over a living
watercolor wash that reacts to your music.**

`v1.1717b` · Zero dependencies · Pure HTML5 Canvas · one file, no build step

[![](https://img.shields.io/badge/HTML5-Canvas-42a5f5?style=flat-square&logo=html5)](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API)
[![](https://img.shields.io/badge/JavaScript-ES6-f7df1e?style=flat-square&logo=javascript)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
[![](https://img.shields.io/badge/Web_Audio-API-9ddf6c?style=flat-square)](https://developer.mozilla.org/en-US/docs/Web/API/Web_Audio_API)
[![](https://img.shields.io/badge/Dependencies-0-success?style=flat-square)](#dependencies)
[![](https://img.shields.io/badge/License-MIT-9ddf6c?style=flat-square)](LICENSE)
[![](https://img.shields.io/badge/Version-v1.1717b-6fd3ff?style=flat-square)](#-release-history)

</div>

---

## 📸 Preview

> Your screen recording / GIF goes here.
>
> `![preview](assets/preview.gif)`
>
> *Watercolor Bingo Rain v1.1717b — balls bursting and dissolving into a lake while rain
> falls and the water surges with the music.*

---

## 🎯 What is this?

A generative, real-time **visualisation** in a single HTML file — part generative art, part
physics toy, part stress test for the browser's 2D canvas, and now **audio-reactive**.

Four layers, all feeding each other:

| Layer | What it does |
| --- | --- |
| 🎨 **Watercolor background** | Nine slow "washes" and thirty drifting "pigment blooms" render into a tiny **5.5 %-resolution buffer**, then upscale with bilinear smoothing. The pigment **pools at the edges** of each blob (via gradient-stop engineering) and its **hue rotates continuously**, so the palette never settles. |
| ⚽ **Balls** | Balls burst in groups of **30 → 50 → 30 → 50** every 3–7 seconds, roll in from the screen edges, bounce with real restitution, **jostle against each other** into a bingo-drum pile, settle, then **dissolve into water**. |
| 💧 **Water** | Puddles grow, **merge into lakes**, and undulate with layered sine waves. |
| 🌧️ **Weather + audio** | **Big rain drops** fall, splash and send out **slow-fading expanding ripples**. Browser audio input drives the **wave height** — peaks reach **half the screen height** at full level. |

### ✨ Highlights

- ⚽ **Bingo-style physics** — restitution, rolling friction, velocity-derived rolling spin,
  and pairwise ball-vs-ball separation so balls pile up like real ones in a drum.
- 🧪 **Watercolour pigment simulation** — edge pooling, hue drift, additive/multiply
  blending, paper grain, and a cursor that paints live into the wash.
- 💧 **Self-merging water** — puddles detect overlap and fuse into wider lakes with
  averaged hue.
- 🎵 **Audio-reactive water** — mic or shared-tab audio drives wave height, wave speed and
  water colour, with **auto-gain normalisation** and an attack/release envelope.
- 🎚️ **Sensitivity / gain** — 0.1×–5.00× control over the whole audio response.
- 🌧️ **Big rain** — teardrop drops with motion trails, highlights, splashes and ripples.
- 🔄 **Alternating 30/50 bursts** on a randomised 3–7 s gap.
- 🎛️ **Live control panel** — bursts, wave speed/height/softness, spread, rain, sound, theme.
- ⌨️ **Full keyboard control** — `F` fullscreen, `I` panel, `P` pause, `Space` burst.
- 🚨 **Built-in error trap** — any JS error surfaces as an on-screen banner instead of
  a silent black screen.

---

## 🚀 Quick start

### Option 1 — just open it

```bash
git clone https://github.com/<you>/watercolor-bingo-rain.git
cd watercolor-bingo-rain
xdg-open index.html     # macOS: open index.html  |  Windows: start index.html
```

No build step. No server. No `npm install`. **It just runs.**

### Option 2 — GitHub Pages

1. Push the repo to GitHub.
2. **Settings → Pages → Source:** `Deploy from a branch` **→** `main` **/** `/ (root)`.
3. Live at `https://<you>.github.io/watercolor-bingo-rain/`.

### Option 3 — local server (recommended for the audio features)

```bash
python -m http.server 8000
# → http://localhost:8000
```

> 🎵 **Audio capture needs a secure context.** `https://` (GitHub Pages) or `localhost`
> are required for tab-audio capture, and some browsers refuse microphone access on
> `file://`. If the sound panel says *"needs https:// or a local server"*, this is why.

---

## 🎮 Controls

### Keyboard

| Key | Action |
| --- | --- |
| <kbd>F</kbd> | Toggle **fullscreen** |
| <kbd>I</kbd> | Toggle the **control panel** on / off |
| <kbd>P</kbd> | **Pause** / resume the animation |
| <kbd>Space</kbd> | Trigger a **burst** immediately |
| <kbd>R</kbd> | **Reset** — clear all balls, water and ripples |
| **Click** | Spawn a ball (clicking near an edge spawns it *from* that edge) |
| **Move mouse** | Paints live pigment into the background wash |

### Control panel

| Section | Control | Range | Default |
| --- | --- | --- | --- |
| **Scene** | Pause · Burst now · Clear | — | — |
| **Bursts** | Balls per burst | 0 – 90 | 30 |
| | Alternate 30 → 50 → 30 → 50 | on / off | **on** |
| | Gap min | 0.5 – 12 s | 3 s |
| | Gap max | 0.5 – 14 s | 7 s |
| **Water** | Wave speed | 0 – 6× | 1.2× |
| | Wave height | 0 – 6× | 1× |
| | Extra high wave height (×2.2) | on / off | off |
| | Softer wave crests | on / off | **on** |
| | Spread (how fast lakes grow) | 0 – 3× | 1× |
| **Sound** | Sound input — drives wave height | on / off | off |
| | Sensitivity / gain | 0.1 – 5.00× | 1.00× |
| | ♪ Capture tab audio | button | — |
| | Input level | live readout | — |
| **Weather** | Big rain drops / sec | 0 – 24 | 7 |
| **Look** | Background flow | on / off | on |
| | Cursor paints | on / off | on |
| | Paper (light) theme | on / off | off |

---

## 🎵 The audio system

### Why there are two input modes

A web page **cannot read the audio of another tab** directly — browsers sandbox that for
security. So there are two real options, and **both** are implemented:

| Mode | How it works | Gets you |
| --- | --- | --- |
| 🎤 **Microphone** (checkbox) | Captures your mic, so it hears **whatever is playing out loud** — including music from another tab, as long as your speakers are on | "Whatever music is playing" ✓ |
| ♪ **Capture tab audio** (button) | `getDisplayMedia` — you pick the tab and tick **"Share tab audio"**, and that tab's sound is analysed **directly and perfectly** | Exact other-tab audio ✓ (Chrome/Edge) |

> The **analyser is never connected to the destination**, so there is no feedback loop
> or echo. The tab-capture button keeps Chrome's "sharing" indicator visible — that's
> Chrome holding the stream open, not a bug.

### The signal chain

```
capture ──▶ time-domain RMS ──▶ auto-gain normalise ──▶ × sensitivity │
 fast attack / slow release envelope
 │
                    ┌─────────────────────┬───────────────┴────────────┐
                    ▼                     ▼                            ▼
            wave amplitude wave speed                  water hue (→½ screen height)      (→ ×2.1)                   (→ +16°)
```

```js
// auto-gain: normalise against a decaying peak so quiet music still works
AU.peak = Math.max(AU.raw, AU.peak * 0.995);
const norm = AU.peak > 0.03 ? AU.raw / AU.peak : 0;

// user gain — applied AFTER auto-gain, otherwise the normaliser cancels it out
const gained = clamp(norm * S.sensitivity, 0, 1);

// envelope: fast attack, slow release
const k = gained > AU.level ? 0.5 : 0.07;
AU.level += (gained - AU.level) * k;

// final drive: full level = wave peaks at half the screen height
S.audioPx = AU.level * (H * 0.5);
```

| Sensitivity | Result |
| --- | --- |
| **0.10×** | Barely-there shimmer, only the loudest hits register |
| **1.00×** (default) | Balanced — the full range of the music maps to the wave |
| **2.00–3.00×** | Aggressive — the water hits the half-screen cap on every chorus |
| **5.00×** | Pinned at maximum height (clamped) |

The HUD **level meter shows the post-gain level**, so you can tune by eye without
leaving the visuals.

---

## ⚙️ How it works

### 1. The watercolor background

Painting fluid pigment with canvas gradients is normally expensive, so the background is
rendered into an **offscreen buffer at 5.5 % resolution** and then upscaled:

```js
const BG_SCALE = 0.055;                 // buffer is 5.5% of screen size
bgC = document.createElement('canvas');
bgC.width  = Math.round(W * BG_SCALE);
bgC.height = Math.round(H * BG_SCALE);
```

Upscaling a tiny canvas with `imageSmoothingEnabled` gives free, buttery blur. Each
pigment blob is a radial gradient with a deliberately **non-monotonic alpha profile**:

```js
grd.addColorStop(0.00, `hsla(${hue},${sat}%,${lit}%,${a})`);        // core
grd.addColorStop(0.38, `hsla(${hue},${sat}%,${lit}%,${a*0.55})`);    // body
grd.addColorStop(0.70, `hsla(${h2},${sat}%,${lit}%,${a*0.20})`);     // thin edge
grd.addColorStop(0.86, `hsla(${h2},${sat}%,${lit}%,${a*0.30})`);     // ← edge pooling!
grd.addColorStop(1.00, `hsla(${h2},${sat}%,${lit}%,0)`);            // falloff
```

The bump at `0.86` is what makes it read as **watercolour** rather than a neon glow —
real pigment migrates to the drying edge of a wash.

Blobs are composited with `lighter` (dark theme) or `multiply` (paper theme) so
**overlapping washes mix** instead of just stacking. Hue rotates over time, so the
palette is never static.

### 2. The soccer balls

Every ball is drawn once into an **offscreen sprite canvas** and cached by
`hue | saturation | lightness | radius-bucket`, then blitted with rotation:

```js
const key = `${hue}|${sat}|${lit}|${rb}`;   // rb = radius rounded to 3px
```

This keeps a busy frame at ~80 balls cheap — no gradient or path work happens per
frame, only `drawImage`.

The ball geometry is a real pentagon layout: one centre pentagon, five rim pentagons
(clipped by the ball edge), and seam lines joining the vertices.

### 3. The physics

```js
b.vy += GRAV * dt;             // gravity
b.vy = -b.vy * 0.52;           // restitution on bounce
b.vx *= 0.80;                  // horizontal friction on impact
b.vx *= Math.pow(0.18, dt);    // rolling friction once resting
b.vr  = b.vx / b.r * 0.9;      // rolling spin derived from velocity
```

Ball-vs-ball separation is an O(n²) pass — cheap at 80 balls, and it produces the
satisfying **jumbled bingo heap** instead of balls overlapping each other.

### 4. Water, merging and waves

Every puddle renders its surface as a **sum of two sine waves** sampled along the
top edge, so the surface genuinely moves up and down:

```js
function waveY(p, u, t) {
  const scale = 0.35 + 0.65 * Math.min(1, p.h / 18);   // bigger pools react more
  const base  = p.h * 0.5 * S.waveAmp * S.boost;
  const a     = Math.min(H * 0.5, base + S.audioPx * scale);
  const sp    = t * p.speed * S.waveSpeed * (1 + AU.level * 1.1);
  const soft  = S.softCrests;
  const f     = soft ? p.freq * 0.62 : p.freq;         // softer = wider swells
  const h2    = soft ? 0.20 : 0.42; // softer = weaker harmonic
  return p.y - p.h * 0.5
    + Math.sin(u * 6.2832 * f + sp + p.phase) * a
    + Math.sin(u * 6.2832 * f * 1.73 - sp * 0.78 + p.phase * 1.3) * a * h2;
}
```

Puddles that overlap **fuse**: the union of their x-ranges becomes a new, wider lake
with an averaged hue — which is how the scene gradually becomes one body of water.

### 5. Ripples

A ripple is an expanding ellipse with an ease-out radius curve and a quadratic
alpha fade, so it lingers long after it stops growing:

```js
const e   = 1 - Math.pow(1 - k, 2.4);            // radius easing
const rr  = r.r0 + (r.r1 - r.r0) * e;
alpha = r.alpha * (1 - k) * (1 - k) * 0.9;       // slow fade
```

Ripples are spawned by **ball impacts**, **full absorption into water**, and **raindrop
strikes**.

### 6. Resize handling

Puddles store the ground height they were born at, so a window resize used to leave
them **floating in mid-screen**. A re-anchor pass fixes it:

```js
function reanchor(){
  for(const p of waters) p.y = groundY(p.x);
  for(const d of drops) d.y = Math.min(d.y, groundY(d.x) - 2);
  ripples.length = 0;
  rain.length = 0;
}
```

---

## 🎨 Customising it

Everything lives in one `S` object near the top of the script:

```js
const S = {
  theme: 'deep',       // 'deep' | 'paper'
  bgFlow: true,        // animate the pigment
  waveAmp: 1.0,        // wave height
  waveSpeed: 1.2,      // wave speed
  spread: 1.0,         // how fast lakes grow
  softCrests: true,    // calmer, wider swells
  extraTall: false,    // ×2.2 wave amplitude  boost: 1
  audioPx: 0,          // audio-driven extra amplitude (px)
  sensitivity: 1.0,    // audio gain multiplier
  ballsPerBurst: 30,
  alternate: true,     // 30 -> 50 -> 30 -> 50
  gapMin: 3, gapMax: 7,
  rain: 7,             // drops per second
  paused: false
};
```

**Ball palette:**

```js
const BALL_HUES = [4,22,40,58,86,110,140,166,186,199,206,216,232,252,270,288,304,320,338];
// or a single hue, e.g. [200]
```

**Every ball a different random colour** (already true for 35 % of spawns — raise it in
`spawnBall`):

```js
const useRandomHue = Math.random() < 0.35;   // ← change 0.35
```

**Gravity / bounce feel** — heavier and more solid:

```js
const GRAV = 1750;
```

…or floatier and more bingo-drum-like:

```js
const GRAV = 900;
```

**Horizon:**

```js
groundBase = H * 0.865;   // fraction of screen height
```

**Background resolution** (lower = softer and cheaper, higher = crisper):

```js
const BG_SCALE = 0.055;   // try 0.03 for a dreamier wash
```

**Dissolve speed** — how long a ball takes to become water:

```js
b.melt += dt / 1.1;   // 1.1 seconds — try dt / 2.5 for a slower fade
```

**Audio drive depth** — how much the music moves the water:

```js
const sp = t * p.speed * S.waveSpeed * (1 + AU.level * 1.1);  // wave speed
const hu = (p.hue + AU.level * 16) % 360;                    // colour drift
```

---

## 📁 Project structure

```
watercolor-bingo-rain/
├── index.html          # the entire artwork (HTML + CSS + JS, single file)
├── README.md           # you're reading it
├── LICENSE             # MIT
└── assets/
    └── preview.gif     # screen recording for the README hero image
```

---

## 🧩 Architecture

```
┌─────────────────────────────────────────────────────────────┐
│  requestAnimationFrame loop (dt-clamped to 50 ms)           │
│                                                             │
│  sampleAudio()                                              │
│   ├── getByteTimeDomainData → RMS                          │
│   ├── auto-gain normalise (÷ decaying peak)                 │
│   ├── × sensitivity                                         │
│   └── attack / release envelope  → AU.level → S.audioPx     │
│                                                             │
│  update(dt, t)                                             │
│   ├── balls      gravity · bounce · roll · separate · melt │
│   ├── water      grow · drift · merge                       │
│   ├── droplets ballistic splash particles                 │
│   ├── rain       big drops → splash + ripple                │
│   └── ripples    expand + fade                              │
│                                                             │
│  render()                                                   │
│   ├── background  offscreen 5.5% buffer → upscale           │
│   ├── ground      wavy horizon + pigment dabs               │
│   ├── water       layered-sine surfaces + crest highlights  │
│   ├── ripples     additive expanding ellipses               │
│   ├── rain        teardrops with trails                     │
│   ├── balls       cached sprites, dissolve blend            │
│   ├── droplets    spray                                      │
│   └── grain + vignette                                       │
└─────────────────────────────────────────────────────────────┘
```

---

## 📦 Release history

### v1.1717b — *current* · "Gain Control"

- ✨ **Sensitivity / gain slider** for the audio input (**0.1× – 5.00×**, default 1.00×).
  Scales the whole audio response *after* auto-gain normalisation, so it works
  regardless of source volume.
- ✨ The HUD **level meter now shows the post-gain level**, so the slider's effect is
  visible in real time.

### v1.1717a — "Audio Reactive"

- ✨ **Sound-reactive water.** Browser audio input drives the wave height — peaks scale
  up to **half the screen height** at full level.
- ✨ **Two input sources:** 🎤 microphone, and ♪ **capture tab audio** via
  `getDisplayMedia` for perfect other-tab audio (Chrome/Edge).
- ✨ **Auto-gain normalisation** so quiet music still modulates fully.
- ✨ **Fast attack / slow release envelope** — the water snaps on the beat, settles on
  the decay.
- ✨ The music also **speeds up the waves** (up to ×2.1) and **shifts the water colour**
  (up to +16° hue).
- ✨ **Live audio level meter** in the HUD + status readout in the panel.
- ✨ **Sound input toggle** that releases the microphone when switched off.

### v1.7.1 — "Anchored & Calmer"

- 🐛 **Puddles now re-anchor to the ground on window resize** — previously pools created
  before a resize stayed pinned to the old horizon and floated in mid-screen.
- 🐛 **The status badge now shows the live resolution** instead of the value captured at
  page load.
- ✨ **"Softer wave crests"** toggle (default **on**) — fewer, wider swells and a weaker
  second harmonic, so the surface reads as calm water rather than a spiky mountain range.
- ✨ **"Extra high wave height"** toggle — ×2.2 amplitude on top of the slider.
- ✨ **Wave height slider range widened** from 0–2.5× to 0–6× (up to 13.2× with the boost).
- 🛡️ Wave amplitude clamped to 150 px so extreme settings can't leave the screen.

### v1.7 — "Melt & Keys"

- ✨ **Removed the wax-melt effect.** Balls dissolve cleanly into the water (fade + blur
  + spread) instead of squashing and dripping. ~2× faster.
- ⌨️ **`F` now toggles fullscreen only**; the control panel moved to **`I`**.
- 🐛 **Fixed a critical syntax error** where a trailing comment swallowed an `if`
  statement's opening brace, killing the entire script and rendering a black screen.
- 🐛 **Fixed missing bounce friction** (it was trapped behind a comment).
- 🐛 **Fixed resting balls never applying rolling friction**, so they slid off-screen.
- 🚨 Added an **on-screen error banner** and a **"running" status badge**.
- ✨ Added **ball-vs-ball separation** for a proper bingo-drum pile.
- ✨ Added **edge spawns** — balls roll in from the left and right edges.
- ✨ Added **big rain drops** with trails, splashes and ripples.
- ✨ Added **wave speed** and **rain rate** controls.

### v1.6

- Alternating **30 / 50 ball bursts** on a randomised 3–7 s gap.
- **Pause** control and `P` shortcut.
- **Ball count** and **wave speed** sliders.
- Slower, wider-spreading watercolor background.

### v1.5

- First **burst system** (30 balls every 3–7 s).
- `F` = fullscreen + hide UI.
- Ball sizes and hues widened; some spawns near screen edges.

### v1.4

- Ripples and splashes on impact.
- Merging puddles.

### v1.0 — *first light*

- Falling soccer balls, pentagon-sprite rendering, ground collision.
- Puddles with two-sine wave surfaces.
- Static watercolor background.

---

## 🐛 Notable bugs (and what they taught us)

This project shipped a few genuinely instructive bugs. They're listed because they'remore interesting than the features:

| # | Bug | Cause | Lesson |
| --- | --- | --- | --- |
| 1 | **Entire script dead — black screen** | A trailing `//` comment swallowed an `if` statement's **opening brace**, leaving an unmatched `}` → parse error → the whole `<script>` was rejected. The UI still rendered because it was static HTML, which made it look like a rendering problem. | A **comment on the same line as code** is a silent syntax bomb. Fixed by putting code on its own line — and by adding a global `window.onerror` banner so this can never fail silently again. |
| 2 | **Balls never lost horizontal energy** | `b.vx *= .80;` sat *after* a `//` on the same line, so it was commented out. | Same root cause as #1 — the visual symptom (balls sliding forever) pointed at physics, but the bug was in the source formatting. |
| 3 | **Resting balls slid off-screen** | `restT` only incremented inside the `if (vy > 0)` branch, so once a ball stopped bouncing, rolling friction never applied. | State machines need an explicit **resting flag**, not a counter hidden inside another branch. |
| 4 | **A band of water floating mid-screen** | Puddles store the ground height they were born at; on resize the ground moved but the puddles didn't. | Any object anchored to a moving reference needs a **re-anchor pass** on resize. |

> **The through-line:** every one of these was invisible to "does it run?" and obvious to
> "does it look right?" — which is exactly the argument for keeping the on-screen error
> banner and the live FPS badge.

---

## ⚠️ Known limitations

- **Very wide screens** can dip below 60 fps because every puddle re-renders its wave
  path each frame. Lowering `BG_SCALE` or the ball count helps.
- **Ripples are drawn flat on the ground line**, not on the surface of individual
  lakes, so they read as a single water plane rather than per-lake waves.
- **Puddles merge by x-overlap**, not by true fluid simulation — a puddle that drifts
  past another will fuse with it even if the shapes didn't really touch.
- The `ctx.filter = 'blur()'` dissolve needs a reasonably modern browser; without it
  the dissolve still works, just without the blur.
- **Audio requires a secure context** (`https://` or `localhost`); some browsers refuse
  microphone access from `file://`.
- **A page cannot read another tab's audio** directly — use the ♪ tab-capture button, or
  let the microphone hear it.
- Mobile touch works for spawning, but the control panel needs a wide viewport.

---

## 🛠 Browser support

| Browser | Support |
| --- | --- |
| Chrome / Edge 90+ | ✅ Full, incl. tab-audio capture |
| Firefox 90+ | ✅ Full (mic only) |
| Safari 15+ | ✅ Full (blur may be soft; tab capture limited) |
| Mobile Safari / Chrome | ✅ Works, panel needs space |

Uses only `Canvas 2D`, `requestAnimationFrame`, `Pointer Events`, the **Web Audio API**,
`MediaDevices` and the **Fullscreen API**.

---

## 🚧 Roadmap

- [ ] **Beat detection** — a bright expanding ring across the lake on every kick drum
- [ ] True per-lake ripple interaction (waves that displace the surface)
- [ ] Optional WebGL/WebGPU renderer for thousands of puddles
- [ ] A "lake" mode where the ground floods and balls float
- [ ] Palette presets (ocean / sunset / monochrome)
- [ ] Export frame as PNG
- [ ] Touch-friendly control panel layout
- [ ] Accessibility: a reduced-motion mode and a photosensitivity-safe flash limit

---

## 🤝 Contributing

Contributions are welcome — especially visual experiments!

1. Fork the repo and create a branch: `git checkout -b feature/your-idea`
2. Keep it **dependency-free** and inside a single `index.html` if you can.
3. Please test in **at least two browsers** and check the console is clean.
4. Open a Pull Request with a short description and, ideally, a GIF.

**Good areas to contribute:** new backgrounds, new particle effects, better wave physics,
beat detection, mobile layout, accessibility (a reduced-motion mode would be welcome).

---

## 📄 License

MIT — see [LICENSE](LICENSE).

```
MIT License

Copyright (c) 2026 <your name>

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

---

## 🙏 Acknowledgements

- Inspired by **bingo-ball drums** and by the way **watercolour washes bloom** on wet paper.
- Built as a playful exploration of what a single `<canvas>` can do with nothing but gradients.
- Dedicated to everyone who has ever watched a paint drop spread.

<div align="center">
<sub>Made with 🎨, ⚽, 💧 and 🎵 — v1.1717b</sub>
</div>


