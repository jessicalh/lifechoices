# Life Choices — A Fable

A fable-isation of [lifechoices](https://github.com/jessicalh/lifechoices), the
Opus 4.5-era coin flip experiment. Same green felt table, same physics ritual,
same single HTML file, same refusal to be production code. The cast changed.

The original flipped Tux against Daffy Duck under the motto *Tempus
Cuniculorum* — "Rabbit Season," the best short Latin a duck could commission.
This edition takes that rabbit seriously. The coin is now struck from Aesop:

- **Obverse (heads):** the Tortoise, walking. Motto: **FESTINA LENTE** —
  *make haste, slowly.*
- **Reverse (tails):** the Hare, mid-leap, already late. Motto: **TEMPUS
  FUGIT** — *time flies.* The rabbit finally got promoted to a full coin face;
  it remains rabbit season forever.
- **Edge:** still possible in principle, still ruled out in practice by the
  air currents. Should one occur anyway: *the moral is unclear.*

Tap to flip. The coin decides. A tally at the top keeps the long-run record of
your life choices (click it to reset, as one does).

## What stayed

- One `index.html`, no build step, no framework, no shame.
- The green felt with pinstripes, the quarter's real dimensions (24.26 mm
  across, 1.75 mm thick, 5.67 g, cupronickel), the camera that chases the coin
  and then leans in for the verdict.
- The big documented `CONFIG` object. Every number you might want to fiddle
  with is still in one place.
- The Known Behavior that coins cannot balance on edge, because a small
  simulated breeze exists specifically to prevent moral ambiguity.
- LoFi mode, debug mode, mobile support.

## What changed

- **three.js r128 → r160 (ES modules)** with ACES filmic tone mapping and
  image-based lighting (PMREM room environment), which is what makes the
  metal read as metal.
- **cannon.js 0.6.2 → cannon-es 0.20**, the maintained fork. The coin is a
  proper Y-aligned cylinder body now, no compensating quaternion.
- **The coin dies are drawn once.** One palette-driven canvas painter renders
  both the color art and the grayscale relief, so the embossing height map
  registers exactly with the artwork instead of being a hand-kept copy. The
  rim legends are set on arcs, like a coin, with a raised rim.
- **Sound**, synthesized in WebAudio at runtime — a slightly inharmonic
  metallic ring on each bounce (scaled by impact) over a felt thud, and a
  little swoosh at launch. No audio files. Mute button provided.
- **A tally** (🐢 / 🐇), persisted in localStorage.

## URL modes

| Mode | What it does |
|---|---|
| `?debug` | Camera controls, flip/force/spin sliders, info panels |
| `?faces` | Proof sheet of the four coin dies (color + relief), no WebGL needed |
| `?autoflip` | Flips once on load, for headless smoke-testing |
| `?montecarlo=N` | Runs N full flips through the real physics world synchronously and reports the distribution |

The last run of `?montecarlo=100` on this machine: 48 tortoise, 52 hare,
0 edge, 0 timeouts. The coin is fair. (Persi Diaconis estimates real
hand-flipped coins land same-side-up about 51% of the time; this coin fully
randomizes its launch every flip, so it does not inherit that bias. The tally
is there if you'd like to audit it.)

## Running it

Open `index.html` in a browser. The libraries are pinned CDN ES modules
(jsDelivr), so the first run needs an internet connection; no local server is
required.

## Browser requirements

- WebGL and ES modules (any modern browser)
- Touch events for mobile interaction
