
<img width="1920" height="1080" alt="Screenshot (556) (1)" src="https://github.com/user-attachments/assets/542f57a2-fd10-4157-a765-00b8d4b0baf1" />


<div align="center">

# 🎨⚽ → 💧 Watercolor Bingo Rain

**An interactive canvas artwork where soccer balls burst, bounce like a bingo drum,
dissolve into slow undulating water, and dance to whatever your computer is playing.**

`v2.7` · Zero dependencies · Pure HTML5 Canvas · one file, no build step · MIT

[![](https://img.shields.io/badge/HTML5-Canvas-42a5f5?style=flat-square&logo=html5)](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API)
[![](https://img.shields.io/badge/JavaScript-ES6-f7df1e?style=flat-square&logo=javascript)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
[![](https://img.shields.io/badge/Web_Audio-API-9ddf6c?style=flat-square)](https://developer.mozilla.org/en-US/docs/Web/API/Web_Audio_API)
[![](https://img.shields.io/badge/Dependencies-0-success?style=flat-square)](#-project-structure)
[![](https://img.shields.io/badge/License-MIT-9ddf6c?style=flat-square)](#-license)
[![](https://img.shields.io/badge/Version-v2.7-6fd3ff?style=flat-square)](#-the-story-so-far)

</div>

---

## 📸 Preview

> Your screen recording / GIF goes here.
>
> `![preview](assets/preview.gif)`
>
> *Watercolor Bingo Rain v2.7 — balls bursting and dissolving into a painterly lake, rain
> falling, and the whole surface pulsing with the beat of whatever is playing on your computer.*

**Then and now** — the lake in the v2.5 reference look, and the v2.7 rebuild that brought it
back (with better paint):

| v2.5 — the reference look | v2.7 — painterly sheets |
|---|---|
| `![v2.5 lake](assets/lake-v2.5.png)` | `![v2.7 lake](assets/lake-v2.7.png)` |

---

## 🎯 What is this?

A generative, real-time **visualisation** in a single HTML file — part generative art, part
physics toy, part stress test for the browser's 2D canvas, and **audio-reactive**.

| Layer | What it does |
| --- | --- |
| 🎨 **Watercolor background** | Nine slow "washes" and thirty drifting "pigment blooms" render into a tiny **5.5 %-resolution buffer**, then upscale with bilinear smoothing. The pigment **pools at the edges** of each blob (via gradient-stop engineering) and its **hue rotates continuously**, so the palette never settles. |
| ⚽ **Balls** | Balls burst in groups of **30 → 50 → 30 → 50** every 3–7 seconds, roll in from the screen edges, bounce with real restitution, **jostle against each other** into a bingo-drum pile, settle, then **dissolve into water**. |
| 💧 **Water** | Each melted ball leaves a **pigment sheet** with its own colour, tempo and silhouette. Sheets never merge; the oldest fade. A single slow swell paints the **body of water** beneath them. |
| 🌧️ **Weather + audio** | **Big rain drops** fall, splash and send out **slow-fading expanding ripples**. **System audio** drives the wave height, and **kick drums spawn expanding rings across the lake**. |

### ✨ Highlights

- ⚽ **Bingo-style physics** — restitution, rolling friction, rolling spin, and pairwise
  ball-vs-ball separation so balls pile up like real ones in a drum.
- 🧪 **Watercolour pigment simulation** — edge pooling, hue drift, additive/multiply
  blending, paper grain, and a cursor that paints live into the wash.
- 💧 **Painterly sheets** — six watercolor passes per bloom (reflection, bloom, translucent body,
  wet edge, sparkle, pigment rim) over a coherent lake.
- 🔊 **Whole-system audio** — capture **everything your computer is playing** (all tabs,
  videos, music, games) with one button and no extension.
- 🥁 **Beat detection** — a **ratio** threshold against the signal's own median, so it fires at
  any source level; bass onsets trigger expanding rings and a kick in the wave.
- 🌧️ **Big rain** — teardrop drops with motion trails, highlights, splashes and ripples.
- 🎛️ **Live control panel** — bursts, water, sound, processing, weather, look and performance.
- 🚨 **Built-in error trap + integrity self-check** — any JS error surfaces as an on-screen
  banner, and a damaged copy names exactly what it lost.
- ⌨️ **Full keyboard control** — `F` fullscreen, `I` panel, `P` pause, `Space` burst.

---

## 🚀 Quick start

```bash
git clone https://github.com/<you>/watercolor-bingo-rain.git
cd watercolor-bingo-rain
xdg-open Watercolor_Bingo_Rain_v2.7.html   # macOS: open … | Windows: start …
```

No build step. No server. No `npm install`. **It just runs.**

### Local server (recommended for audio)

```bash
python -m http.server 8000
# → http://localhost:8000
```

> 🎵 **Audio capture needs a secure context.** `https://` (GitHub Pages) or `localhost` are
> required — screen/audio capture is blocked on `file://` in several browsers.

### GitHub Pages

1. Push the repo.
2. **Settings → Pages → Source:** `Deploy from a branch` **→** `main` **/** `/ (root)`.
3. Live at `https://<you>.github.io/watercolor-bingo-rain/`.

---

## 🔊 Capturing sound — the exact steps

### 🥁 System audio (recommended)

Captures **every sound your computer is making**: music, video, games, other tabs, other apps.

1. Open the artwork, press <kbd>I</kbd>.
2. Click **🔊 Capture system audio**.
3. In Chrome's share dialog choose:

| Select | You capture |
| --- | --- |
| 🖥️ **Entire Screen** | 🔊 **All system audio** — every app, every tab, every video. **This is the one you want.** |
| 🪟 **Window** | Only that one application. |
| 📑 **Tab** | Only that one page. *(Video stutters on it.)* |

4. **Turn on the audio** in the same dialog:
   - **Windows 11 / macOS 15** — a **"Share audio"** tab; choose **"Share system audio"**.
   - **Windows 10 / other versions** — a **"Share audio" toggle checkbox**. **Tick it.**
5. Click **Share**, then play your music. The HUD reads
   `source: system · gap 0% · level 68% · amp 57px · BEAT`.
6. <kbd>F</kbd> for fullscreen, <kbd>I</kbd> to hide the panel.

> ⚠️ **Without "Share audio" you get video with no sound.**

### 🎤 Microphone

Click **🎤 Use microphone** and allow access. Use **headphones**. On Windows set
**Settings → System → Sound → Communications → "Do nothing"** — the default ducks other audio,
which sounds exactly like a stutter.

---

## 🎮 Controls

### Keyboard

| Key | Action |
| --- | --- |
| <kbd>F</kbd> | Toggle **fullscreen** |
| <kbd>I</kbd> | Toggle the **control panel** |
| <kbd>P</kbd> | **Pause** / resume |
| <kbd>Space</kbd> | **Burst** immediately |
| <kbd>R</kbd> | **Reset** — clear balls, sheets and ripples |
| **Click** | Spawn a ball (near an edge → from that edge) |
| **Move mouse** | Paints live pigment into the background wash |

### Control panel

| Section | Control | Range | Default |
| --- | --- | --- | --- |
| **Scene** | Pause · Burst now · Clear | — | — |
| **Bursts** | Balls per burst | 0 – 90 | 30 |
| | Alternate 30 → 50 → 30 → 50 | on / off | **on** |
| | Gap min / max | 0.5 – 12 / 14 s | 3 s / 7 s |
| **Water** | Wave speed | 0 – 6× | 1.2× |
| | Wave height | 0 – 6× | 1× |
| | Extra high wave height (×2.2) | on / off | off |
| | Softer wave crests | on / off | **on** |
| | Spread (how fast sheets open) | 0 – 3× | 1× |
| **Sound** | 🔊 Capture system audio · 🎤 Use microphone · Sound input enabled | — | off |
| | Sensitivity / gain | 0.1 – 5.00× | 1.00× |
| | Audio wave height | 0 – 100 % | 45 % |
| | Smoothing (release) | 0.05 – 6 s | 0.35 s |
| | Sustain through gaps | 0 – 8 s | 3 s |
| | Beat rings on the lake · Beat sensitivity | on/off · 0.4 – 3× | on · 1× |
| **Processing** | Analysis window (buffer) | 64 – 8192 ms | 336 ms |
| | Gap-fill level from buffer | on / off | **on** |
| **Weather** | Big rain drops / sec | 0 – 24 | 7 |
| **Look** | Background flow · Cursor paints · Paper (light) theme | on / off | on · on · off |
| **Performance** | 30 FPS · 60 FPS · Max | buttons | **60 FPS** |

---

## 📖 The story so far

*A single-file artwork that kept refusing to be "done" — and each refusal taught something.*

### Act I — first light (v1.0 → v1.7)

**v1.0 — first light.** Falling soccer balls, pentagon sprites, ground collision, puddles with
two-sine wave surfaces, a static watercolor background.

**v1.4** — ripples and splashes on impact; puddles that merge.
**v1.5** — the burst system: 30 balls every 3–7 seconds.
**v1.6** — alternating **30 / 50** bursts, a pause control, sliders for ball count and wave speed.
**v1.7 — melt & keys.** Removed the wax-melt effect (balls now dissolve cleanly), made `F` toggle
fullscreen only and moved the panel to `I`, added ball-vs-ball separation, edge spawns, big rain
drops, and — after two embarrassing bugs — an **on-screen error banner**.

### Act II — making it listen (v1.1717a → v2.0)

**v1.1717a — audio reactive.** Audio drove the wave height (up to half the screen), with
auto-gain normalisation, an attack/release envelope, hue modulation and a live level meter.
**v1.1717b — gain control.** A sensitivity slider (0.1× – 5×); the HUD now shows the post-gain level.

**v2.0 — system audio.** The unlock: **one button captures everything the computer is playing**,
through Chrome's share dialog. Beat detection arrived with it (bass onsets → expanding rings).
The **Tab Audio Bridge extension and six DSP workarounds were deleted** — they had been treating
a symptom.

### Act III — making the beat detector honest (v2.1 → v2.3)

**v2.1** — beats never appeared, because an *absolute* bass threshold cannot fire when the bass
is sustained. Replaced with **spectral-flux onset detection**, a second analyser with
`smoothingTimeConstant = 0`, an adaptive threshold and two detectors.

**v2.2** — and then one huge kick **deafened** the detector, because `mean + k·stddev` let a
single spike inflate the threshold to ~27× the real flux. Replaced with **median + MAD** (robust
statistics), flux computed in the float-dB domain, a mid/high detector for snares and hats, and
dB floors so quiet passages don't false-trigger.

**v2.3 — the audio maths.** Two more honesty fixes: the auto-gain had a **hidden absolute
floor** (`Math.max(avg, 0.004)`) that halved every quiet source, and the beat threshold was
still an absolute number. Auto-gain became a **pure ratio** with a peak hold, and the threshold
became **2.2 ÷ sensitivity** measured against the signal's own running median. *Every threshold
in this project is now a ratio.*

### Act IV — the performance wall (v2.4 → v2.5)

**v2.4** — the last build verified end-to-end. It ran at **~7.7 fps** and the beat detector was
still dormant. Diagnosis, not guesswork:

- the background was blitted **twice** at high-quality smoothing (a 70×28 px buffer resampled
  twice to 1.5 M pixels — the single biggest frame cost);
- gradients were allocated per puddle, per raindrop and per vignette **every frame**;
- the fps readout was computed from the **clamped** `dt`, so it could never show below 20;
- the ring buffer silently dropped samples whenever a frame exceeded the analyser window.

**v2.5 — the render & performance batch.** `FFT_SIZE` 4096 → 8192; **one** low-quality
background blit; a **cached offscreen vignette** (rebuilt on resize and theme change); solid
rain trails instead of per-drop gradients; a **dropped-sample counter**; **raw-delta fps**; a
**real gap-episode counter** (`events=` used to be permanently 0); and an analysis-window slider
step of 16 so 336 ms is actually reachable.

It also merged puddles into **one lake** and capped wave amplitude by lake width. Both were
defensible optimisations — and together they **flattened the water into a few smooth cyan
humps**, which is exactly what v2.7 had to undo.

### Act V — the delivery saga (v2.6)

**v2.6** added the **performance panel** — 30 / 60 / Max FPS, with a display-target readout and
audio analysis running independently at 60 Hz — and a larger, calmer lake.

Then came the uncomfortable part: **five failed deliveries in a row.** A 70 KB file pasted
through chat arrived blank, once. Not broken — *absent*, with no error banner, because the
document never reached the browser. The lesson was expensive and simple:

> **Past ~1,000 lines, ship a patch, never the file.**

Every build after that was a **patch script**: idempotent, self-verifying, ASCII-only, refusing
to write when an anchor doesn't match, and printing a SHA-256. Delivery became measurable.

### Act VI — painting the water again (v2.7)

The request was simple — *"make the waves more like the old screenshots"* — and the diagnosis
was three specific edits (capped amplitude, nearby-puddle merging, averaged hues) plus one
structural insight: **wave frequency is per-pool, not per-pixel**, so a narrow pool shows one
or two lobes (a spike) while a wide lake shows one or two lobes (a hump). Narrow pools are the
entire trick.

**v2.7 rebuilds the lake as painterly pigment sheets:**

```js
// asymmetric bell envelope: soft shoulders, one dominant side
var c = (p.skew > 0.5) ? 0.44 : 0.56;
var e = (u < c) ? Math.pow(u / c, 1.30) : Math.pow((1 - u) / (1 - c), 1.85);
e = e * e * (3 - 2 * e);

// three octaves on irrational ratios -> the crest never repeats
var s1 = Math.sin(u * 6.2832 * p.freq            + sp + p.phase);
var s2 = Math.sin(u * 6.2832 * p.freq * 2.618    + sp * 0.72 + p.phase2);
var s3 = Math.sin(u * 6.2832 * p.freq * 6.13 - sp * 1.27 + p.phase * 0.61);
var shape = 0.30 + 0.70 * (s1 * 0.60 + s2 * 0.27 + s3 * 0.13);

// music: the sheet breathes, the beat kicks it, the pigment shifts hue
var stat = p.amp * S.waveAmp * S.boost * (0.45 + 0.55 * p.grow);
var mus  = S.audioPx * p.react * 0.55 * WGAIN;
var a    = (stat * 0.55 + mus) * e * (1 + AU.beat * 0.16 * p.react);
return p.y - a * shape;
```

Each sheet is painted in **six passes** — reflection, bloom, translucent gradient body, **wet
edge**, sparkle on the peaks, pigment rim pooled at the bottom. Sheets **never merge**; they fade
with age, the newest 44 survive, and a new `drawLakeBase()` paints the **body of water** beneath
them so the lake still reads as one lake. Peak heights follow a heavy-tailed distribution
(`Math.pow(Math.random(), 2.2)`), so a few dominant peaks carry the composition.

### Act VII — a broken copy that can say what it lost

One paste lost a brace. The artwork's scope closed early, the boot code fell outside it, and the
page died with `ReferenceError: AU is not defined`.

The fix was not a repair — it was **architecture**:

```js
window.S = S;    // published globally
window.AU = AU;  // so a damaged copy can never lose them
```

plus an **integrity self-check** that verifies fifteen markers in the document's own source and
prints *"THIS COPY IS INCOMPLETE — Missing from the file: …"* instead of a cryptic error.

**The project now runs on three rules:**

1. **Measure, don't guess.** Every diagnosis came from a number — brace counts, byte offsets,
   `rawMs`, `norm`, `ratio`, dropped samples.
2. **Patch, never whole files.**
3. **Verify the artifact, not the intention.** Build stamp, live diagnostics, a machine marker
   audit, and one in-browser line a mangled copy cannot fake:
   `[WBR] build v2.7 ready | controls wired: 33  OK all present`.

---

## ⚙️ How it works

### The watercolor background

Pigment gradients are expensive, so the background renders into an **offscreen buffer at 5.5 %
resolution** and upscales:

```js
var BG_SCALE = 0.055;                       // 0.075 = crisper, 0.04 = dreamier
bgC.width  = Math.round(W * BG_SCALE);
bgC.height = Math.round(H * BG_SCALE);
```

Each blob is a radial gradient with a deliberately **non-monotonic alpha profile** — the bump at
`0.86` is what makes it read as **watercolour** rather than a neon glow, because real pigment
migrates to the drying edge of a wash:

```js
grd.addColorStop(0.00, hsla(hue, sat, lit, a));               // core
grd.addColorStop(0.38, hsla(hue + 6, sat, lit, a * 0.55));     // body
grd.addColorStop(0.70, hsla(h2, sat - 6, lit - 4, a * 0.20));  // thin edge
grd.addColorStop(0.86, hsla(h2, sat, lit - 3, a * 0.30));      // <- edge pooling
grd.addColorStop(1.00, hsla(h2, sat, lit, 0));                 // falloff
```

### The balls

Every ball is drawn once into an **offscreen sprite canvas**, cached by
`hue | saturation | lightness | radius-bucket`, then blitted with rotation — no gradient or path
work happens per frame. The geometry is a real pentagon layout.

### The physics

```js
b.vy += GRAV * dt;              // gravity
b.vy  = -b.vy * 0.52;           // restitution
b.vx *= 0.80;                   // horizontal friction
b.vx *= Math.pow(0.18, dt);     // rolling friction once resting
b.vr  = b.vx / b.r * 0.9;       // rolling spin from velocity
```

Ball-vs-ball separation is an O(n²) pass — cheap at 80 balls, and it produces the satisfying
**jumbled bingo heap**.

### The audio chain

```
capture ─▶ Float32 RMS (2048-sample fast window + a long 336 ms ring)
         ─▶ rolling-average auto-gain (pure ratio, no absolute floor)
         ─▶ relative gap gate ─▶ user sensitivity ─▶ attack/release envelope
         ─▶ AU.level ─▶ S.audioPx ─▶ the lake breathes
         └─▶ float-dB spectral flux ─▶ ratio to its own median ─▶ beat ─▶ rings + hue shift
```

```js
AU.ref  = Math.max(AU.avg, 1e-6);          // pure ratio - any source level works
AU.norm = Math.min(1.8, AU.rms / AU.ref);
AU.gate = Math.max(AU.floor * 2.0, AU.avg * 0.05, 1e-6);   // relative gap gate
```

### Beat detection — spectral flux with a **ratio** threshold

```js
var bassRef = Math.max(bs.m, 0.05);        // median of recent bass flux
AU.ratioB  = AU.bassFlux / bassRef;        // ratio, not an absolute number
AU.thrB    = 2.2 / S.beatSens;              // sensitivity divides the threshold
if (AU.sinceGap > 2 && bs.m > 0.30) {      // needs real signal behind it
  if (AU.ratioB > AU.thrB) { hit = true; strength = 1; }
}
```

A ratio threshold is **level-independent**: identical behaviour whether the source is a whisper
or a stadium, and one huge kick can never deafen the detector.

### Keeping the audio alive

Browsers suspend an `AudioContext` with no path to `destination` — that is what broke sound on
fullscreen. A near-silent gain node gives the context a permanent output:

```js
AU.silent = AU.ctx.createGain();
AU.silent.gain.value = 0.0001;      // inaudible, but keeps the graph alive
AU.silent.connect(AU.ctx.destination);
```

The engine re-arms on `fullscreenchange`, `visibilitychange` and `focus`, and a **"Reconnect
sound"** button appears if it is ever suspended anyway.

---

## 🎨 Customising it

Everything lives in one `S` object near the top of the script:

```js
var S = {
  theme: 'deep', bgFlow: true, cursorPaint: true,
  waveAmp: 1.0, waveSpeed: 1.2, spread: 1.0,
  softCrests: true, extraTall: false, boost: 1,
  audioPx: 0, sensitivity: 1.0, audioHeight: 0.45, release: 0.35,
  gapHold: 3.0, beats: true, beatSens: 1.0,
  ringMs: 336, gapFill: true,
  ballsPerBurst: 30, alternate: true, gapMin: 3, gapMax: 7, rain: 7,
  paused: false, uiHidden: false,
  fpsMode: '60', fpsTarget: 60
};
```

### The art knobs (one line each)

| Want… | Change |
| --- | --- |
| Taller / shorter peaks | `p.amp=rr*(0.85+heavy*2.35)` |
| More or fewer dominant peaks | `heavy=Math.pow(Math.random(),2.2)` — ↑ calmer, ↓ spikier |
| Wider blooms | `var width=rr*(2.6+Math.random()*1.8)*(0.85+heavy*0.55)` |
| Smoother / jagged crest | the octave weights `s1*0.60+s2*0.27+s3*0.13` |
| Softer / harder shoulders | `Math.pow(u/c,1.30)` and `Math.pow((1-u)/(1-c),1.85)` |
| More / fewer sheets at once | `while(waters.length>44)` |
| Stronger / subtler lake | `drawLakeBase()` — `Math.sin(u*6.2832*1.6+t*0.18)*6` |
| More colour movement | `var hu=((p.hue+AU.beat*16+AU.level*6)%360+360)%360;` |
| Crisper background | `var BG_SCALE=0.055;` → `0.075` |

**Live knob, no reload:** type `WAVE_GAIN = 0.45` (calmer) or `1.0` (wilder) in the console.

**Ball palette:** `var BALL_HUES = [4,22,40,58,86,110,140,166,186,199,206,216,232,252,270,288,304,320,338];`
**Every ball random:** `var rnd = Math.random() < 0.35;` — raise `0.35` for more.
**Gravity:** `var GRAV = 1750;` (solid) or `900` (floaty). **Horizon:** `groundBase = H * 0.865;`

---

## 📁 Project structure

```
watercolor-bingo-rain/
├── Watercolor_Bingo_Rain_v2.7.html   # the artwork (HTML + CSS + JS, one file)
├── README.md                          # you're reading it
├── LICENSE                            # MIT
├── assets/
│   ├── preview.gif                    # screen recording
│   ├── lake-v2.5.png                  # the reference look
│   └── lake-v2.7.png                  # the painterly rebuild
└── tools/
    ├── build-v2.7.ps1                 # applies the wave engine to a v2.6 file
    ├── fix-v2.7.ps1                   # verifies / hardens / fingerprints any copy
    ├── audit_wbr.py                   # structural audit of any copy
    └── style_only.css                 # the stylesheet in isolation
```

---

## 🧩 Architecture

```
┌──────────────────────────────────────────────────────────────┐
│ requestAnimationFrame loop (display target 30 / 60 / max)      │
│                                                              │
│ audio at a FIXED 60 Hz (independent of the display rate)      │
│   └── sampleAudio(dt)                                        │
│         ├── Float32 RMS + long ring → relative gap gate       │
│         ├── pure-ratio auto-gain → AU.level → S.audioPx       │
│         └── float-dB spectral flux → ratio to median → beats │
│                                                              │
│ update(dt, t)                                                │
│   ├── balls    gravity · bounce · roll · separate · melt     │
│   ├── sheets   grow · drift · age · fade · cull (never merge)│
│   ├── droplets ballistic splash particles                     │
│   ├── rain     big drops → splash + ripple                   │
│   └── ripples  expand + fade                                 │
│                                                              │
│ render()                                                     │
│   ├── background  5.5 % buffer → one low-quality upscale     │
│   ├── ground      wavy horizon + pigment dabs                │
│   ├── lake base   one slow full-width swell                  │
│   ├── sheets      six watercolor passes each                 │
│   ├── ripples     additive expanding ellipses                │
│   ├── beats       bright expanding rings on the lake         │
│   ├── rain        teardrops with trails                      │
│   ├── balls       cached sprites, dissolve blend             │
│   ├── droplets    spray                                       │
│   └── grain + cached vignette                                 │
└──────────────────────────────────────────────────────────────┘
```

---

## 📦 Release history

| Version | Name | What changed |
| --- | --- | --- |
| **v2.7** | **Painterly Sheets** | The lake is painted, not plotted: pigment sheets with bell-envelope crests, three irrational octaves, heavy-tailed heights, six watercolor passes each, a coherent lake base beneath them. `window.S` / `window.AU` published globally + an integrity self-check. Performance controls unchanged. |
| **v2.6** | Performance Controls | 30 / 60 / Max FPS with a display-target readout; audio analysis runs independently at 60 Hz. |
| **v2.5** | Render & Performance | `FFT_SIZE` 8192; **one** low-quality background blit; cached offscreen vignette; solid rain trails; raw-delta fps; dropped-sample counter; real gap-episode counter; analysis-window step 16. *Also merged puddles into one lake and capped amplitude by lake width — superseded by v2.7's sheets.* |
| **v2.4** | Stability baseline | The last build verified end-to-end. |
| **v2.3** | Audio Maths | Pure-ratio auto-gain + peak hold; ratio-based beat threshold; ratio diagnostics. |
| **v2.2** | Robust Beat Detection | Median + MAD instead of mean + stddev; float-dB flux; a mid/high detector; dB floors. |
| **v2.1** | Beat Detection Fix | Spectral-flux onset detection; second analyser; adaptive threshold; two detectors; a sensitivity slider. |
| **v2.0** | System Audio | One button captures everything the computer is playing; beat detection; the Tab Audio Bridge and six DSP workarounds **deleted**. |
| **v1.1717b** | Gain Control | Sensitivity slider; the HUD shows the post-gain level. |
| **v1.1717a** | Audio Reactive | Audio drives the wave height; auto-gain; attack/release; hue modulation; level meter. |
| **v1.7.1** | Anchored & Calmer | Puddles re-anchor on resize; live resolution badge; softer crests; extra-high wave height. |
| **v1.7** | Melt & Keys | Wax-melt removed; `F` = fullscreen only, panel on `I`; ball separation, edge spawns, big rain; the error banner. |
| **v1.6** | — | Alternating 30/50 bursts, pause, sliders. |
| **v1.5** | — | The burst system. |
| **v1.4** | — | Ripples, splashes, merging puddles. |
| **v1.0** | First light | Falling balls, pentagon sprites, ground collision, two-sine puddles. |

---

## 🐛 Notable bugs (and what they taught us)

| # | Bug | Cause | Lesson |
| --- | --- | --- | --- |
| 1 | **Entire script dead — black screen** | a trailing `//` comment swallowed an `if` statement's **opening brace** → parse error → the whole `<script>` was rejected, while the static HTML still rendered | a **comment on the same line as code** is a silent syntax bomb — and *"does it run?"* is a different question from *"does it parse?"* |
| 2 | **Balls never lost horizontal energy** | `b.vx *= .80;` sat *after* a `//` on the same line | same root cause; the symptom pointed at physics, the bug was in formatting |
| 3 | **Resting balls slid off-screen** | `restT` only incremented inside `if (vy > 0)` | state machines need an explicit **resting flag** |
| 4 | **A band of water floating mid-screen** | puddles stored the ground height they were born at; on resize the ground moved | anything anchored to a moving reference needs a **re-anchor pass** |
| 5 | **Sound died on fullscreen** | the `AudioContext` had no path to `destination`, so Chrome could suspend it mid-transition | give the context a **permanent silent output path** and re-arm on `fullscreenchange` |
| 6 | **Audio stuttered on video** | Chrome's tab capture feeds audio in bursts and video decode starves it | **fix the source, not the symptom** — whole-system capture bypasses the renderer, and every workaround became deletable |
| 7 | **Beat rings never appeared** | an absolute bass threshold can't fire when the bass is sustained | detect **change** (spectral flux), not level |
| 8 | **Beats deafened after a big kick** | `mean + k·stddev` pushed the threshold to ~27× the real flux | use **robust statistics** (median + MAD) |
| 9 | **`AU is not defined` after a copy-paste** | a lost brace closed the artwork's scope early, so the boot code could not see the state objects | **publish the state globally** and let the file **say what it lost** |
| 10 | **The lake looked generic** | amplitude capped by lake width + nearby-puddle merging + averaged hues | every one of those was a *deliberate* optimisation; together they flattened the art |

> **The through-line:** each of these was invisible to *"does it run?"* and obvious to
> *"does it look right?"* — which is why the on-screen error banner, the live fps badge and the
> integrity self-check all exist.

---

## 🛠 Troubleshooting

| Symptom | Cause / fix |
| --- | --- |
| **Blank page** | Saved as UTF-16 or as `.txt`. Re-save as **UTF-8**, type **All Files**, filename ending `.html`. |
| **`ReferenceError: AU is not defined`** | A brace was lost while copying. Run `tools/fix-v2.7.ps1` — it restores the global state and re-verifies the file. |
| **"THIS COPY IS INCOMPLETE"** | The banner lists exactly which markers are missing. Re-copy that part, or rebuild from the canonical file. |
| **No sound** | Tick **"Share audio"** in the picker and choose **Entire Screen**. |
| **"VERY QUIET SOURCE"** | Captured level below 0.004 — raise the system volume or capture another source. |
| **Audio stutters** | Use **Entire Screen**, not **Tab**. On Windows: Sound → Communications → "Do nothing". |
| **Beat rings never appear** | The diagnostics should show `ratio > 2.20` on a kick; lower **Beat sensitivity** to 0.6 if marginal. |
| **Low fps** | **Balls per burst** 30, lower `BG_SCALE`, or the **30 FPS** target — the audio analysis still runs at 60 Hz. |

---

## ⚠️ Known limitations

- **The lake is composed, not simulated** — sheets are painted shapes; there is no fluid solver
  and sheets deliberately do not merge.
- **Ripples and beat rings are drawn on the lake base**, so they read as one water plane.
- **The background is upscaled from a 5.5 % buffer**, so it is soft by design — raise
  `BG_SCALE` for a crisper wash.
- **The `ctx.filter = 'blur()'` dissolve** needs a modern browser; without it the dissolve still
  works, just without the blur.
- **Audio capture requires a secure context** (`https://` or `localhost`).
- **DRM-protected content** captures as silence — a platform restriction.
- **Tab capture stutters on video** — use *Entire Screen*.
- Mobile touch spawns balls, but the panel needs a wide viewport.

---

## 🛠 Browser support

| Browser | Support |
| --- | --- |
| Chrome / Edge 90+ | ✅ Full, incl. system audio capture |
| Firefox 90+ | ✅ Full (some builds offer tab audio only) |
| Safari 15+ | ⚠️ Works; no system audio in the share dialog — use 🎤 Microphone |
| Mobile Safari / Chrome | ✅ Works, panel needs space |

Uses only `Canvas 2D`, `requestAnimationFrame`, `Pointer Events`, the **Web Audio API**,
`MediaDevices` (`getDisplayMedia` / `getUserMedia`) and the **Fullscreen API**.

---

## 🚧 Roadmap

**Art**
- [ ] Tune the sheets to the v2.5 reference look — one-line changes, shipped as patches
- [ ] Sharpen the background (`BG_SCALE` 0.055 → 0.075)
- [ ] Beat-reactive colour on the sheet body
- [ ] Per-lake ripples that displace individual sheets
- [ ] A "flood" mode where the ground rises and the balls float
- [ ] Palette presets (ocean / sunset / monochrome)

**Engineering**
- [ ] Cache the per-sheet gradient allocation if fps demands it
- [ ] Optional WebGL renderer for thousands of sheets
- [ ] Export a frame as PNG
- [ ] Touch-friendly control panel layout
- [ ] Accessibility: reduced-motion mode and a photosensitivity-safe flash limit

**Process**
- [ ] Keep the artifact + its SHA-256 as the fingerprint of every release
- [ ] Continue to ship patches, never retyped whole files

---

## 🤝 Contributing

1. Fork the repo and create a branch: `git checkout -b feature/your-idea`
2. Keep it **dependency-free** and inside a single HTML file if you can.
3. Test in **at least two browsers** and check the console prints
   `[WBR] build v2.7 ready | controls wired: 33  OK all present`.
4. Open a Pull Request with a short description and, ideally, a GIF.

**Good areas to contribute:** new backgrounds, new paint effects, wave shaping, beat-detection
tuning, mobile layout, accessibility.

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
<sub>Made with 🎨, ⚽, 💧 and 🔊 — v2.7</sub>
</div>



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


